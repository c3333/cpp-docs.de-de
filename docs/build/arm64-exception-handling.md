---
title: ARM64-Ausnahmebehandlung
description: Hier werden die Konventionen für die Ausnahmebehandlung erklärt, und Sie erfahren, welche Daten von Windows auf ARM64 verwendet werden.
ms.date: 11/19/2018
ms.openlocfilehash: 2304c04c5e9be31299e30bb48771f7c9777d1cd5
ms.sourcegitcommit: b9aaaebe6e7dc5a18fe26f73cc7cf5fce09262c1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/20/2020
ms.locfileid: "77504483"
---
# <a name="arm64-exception-handling"></a>ARM64-Ausnahmebehandlung

Windows auf ARM64 verwendet denselben strukturierten Mechanismus für die Ausnahmebehandlung bei asynchronen (von der Hardware generierten) und synchronen (von der Software generierten) Ausnahmen. Sprachspezifische Ausnahmehandler werden auf von Windows strukturierter Ausnahmebehandlung mithilfe von Sprachhilfsfunktionen erstellt. Dieses Dokument beschreibt die Ausnahmebehandlung in Windows auf ARM64 und die Sprachhilfen, die von Code verwendet werden, der vom Microsoft-ARM-Assembler und vom MSVC-Compiler generiert wurde.

## <a name="goals-and-motivation"></a>Ziele und Motivation

Die Datenkonventionen für die Ausnahmeentladung und diese Beschreibung dienen folgendem Zweck:

1. Die Beschreibung soll dafür ausreichen, dass Entladevorgänge generell ohne Codetests durchgeführt werden können.

   - Für die Codeanalyse muss der Code ausgelagert werden. Dadurch kann das Entladen in Fällen verhindert werden, in denen es nicht sinnvoll wäre (bei der Ablaufverfolgung, bei der Stichprobenentnahme und beim Debuggen).

   - Die Codeanalyse ist komplex. Der Compiler muss darauf achten, nur Anweisungen zu generieren, die der Entlader decodieren kann.

   - Wenn das Entladen durch die Verwendung von Entladungscodes nicht vollständig beschrieben werden kann, muss in manchen Fällen auf die Anweisungsdecodierung zurückgegriffen werden. Dadurch wird die Komplexität insgesamt erhöht, deshalb sollte diese Vorgehensweise im Idealfall vermieden werden.

1. Die Entladung innerhalb des Prologs und Epilogs soll unterstützt werden.

   - Die Entladung wird unter Windows nicht nur für die Ausnahmebehandlung verwendet. Es ist wichtig, dass der Code auch dann korrekt entladen werden kann, wenn gerade eine Prolog- oder Epilogsequenz ausgeführt wird.

1. Es soll nur eine minimale Menge an Speicherplatz in Anspruch genommen werden.

   - Die Entladungscodes dürfen nicht aggregiert werden, damit die Binärgröße nicht erheblich ansteigt.

   - Da die Entladungscodes wahrscheinlich im Arbeitsspeicher gesperrt sind, stellt ein kleiner Speicherbedarf einen minimalen Aufwand für jede geladene Binärdatei sicher.

## <a name="assumptions"></a>Annahmen

Bei der Beschreibung der Ausnahmebehandlung werden folgende Annahmen getroffen:

1. Prologe und Epiloge sind tendenziell gespiegelt. Wenn wir uns dieses allgemeine Merkmal zunutze machen, kann die Größe der Metadaten, die zum Beschreiben der Entladung erforderlich sind, erheblich reduziert werden. Innerhalb des Funktionstexts spielt es keine Rolle, ob die Prologvorgänge rückgängig gemacht oder die Epilogvorgänge vorwärts durchgeführt werden. Beides sollte zum gleichen Ergebnis führen.

1. Funktionen sind im Allgemeinen relativ klein. Einige Optimierungen für den Speicherplatz basieren auf dieser Tatsache, damit Daten möglichst effizient gepackt werden können.

1. Es gibt keinen bedingten Code in Epilogen.

1. Dediziertes Framezeigerregister: Wenn der SP (Stack Pointer, Stapelzeiger) in einem anderen Register (x29) im Prolog gespeichert wird, bleibt dieses Register in der gesamten Funktion unverändert. Das bedeutet, dass der ursprüngliche SP jederzeit wiederhergestellt werden kann.

1. Sämtliche Änderungen des Stapelzeigers müssen strikt innerhalb von Prolog und Epilog erfolgen, sofern der SP nicht in einem anderen Register gespeichert ist.

1. Das Stapelrahmenlayout ist wie im nächsten Abschnitt beschrieben organisiert.

## <a name="arm64-stack-frame-layout"></a>ARM64-Stapelrahmenlayout

![Stapelrahmenlayout](media/arm64-exception-handling-stack-frame.png "Stapelrahmenlayout")

Bei frameverketteten Funktionen können das FP- und LR-Paar (FP = Frame Pointer = Framezeiger, LR = Link Register = Linkregister) je nach angestrebter Optimierung an jeder beliebigen Position im Bereich der lokalen Variablen gespeichert werden. Das Ziel besteht darin, dass so viele lokale Variablen wie möglich durch eine einzelne Anweisung erreicht werden können, die auf dem Framezeiger (x29) oder dem Stapelzeiger (sp) basiert. Für `alloca`-Funktionen muss jedoch eine Verkettung erfolgen, und x29 muss auf das Ende des Stapels zeigen. Die Speicherbereiche für nicht flüchtige Register werden am Anfang des Bereichsstapels für die lokale Variable positioniert, um die Abdeckung des Adressierungsmodus für Registerpaare zu verbessern. Im Folgenden finden Sie Beispiele, die einige der effizientesten Prologsequenzen veranschaulichen. Der Eindeutigkeit halber und um eine bessere Cachelokalität zu erzielen wird eine aufsteigende Speicherreihenfolge für die nicht flüchtigen Register in allen kanonischen Prologen verwendet. `#framesz` steht für die Größe des gesamten Stapels (mit Ausnahme des alloca-Bereichs). `#localsz` und `#outsz` geben die lokale Bereichsgröße (einschließlich des Speicherbereichs für das \<x29, lr>-Paar) und die Größe für ausgehende Parameter an.

1. Verkettet, #localsz \<= 512

    ```asm
        stp    x19,x20,[sp,#-96]!        // pre-indexed, save in 1st FP/INT pair
        stp    d8,d9,[sp,#16]            // save in FP regs (optional)
        stp    x0,x1,[sp,#32]            // home params (optional)
        stp    x2,x3,[sp,#48]
        stp    x4,x5,[sp,#64]
        stp    x6,x7,[sp,#72]
        stp    x29,lr,[sp,#-localsz]!   // save <x29,lr> at bottom of local area
        mov    x29,sp                   // x29 points to bottom of local
        sub    sp,sp,#outsz             // (optional for #outsz != 0)
    ```

1. Verkettet, #localsz > 512

    ```asm
        stp    x19,x20,[sp,#-96]!        // pre-indexed, save in 1st FP/INT pair
        stp    d8,d9,[sp,#16]            // save in FP regs (optional)
        stp    x0,x1,[sp,#32]            // home params (optional)
        stp    x2,x3,[sp,#48]
        stp    x4,x5,[sp,#64]
        stp    x6,x7,[sp,#72]
        sub    sp,sp,#(localsz+outsz)   // allocate remaining frame
        stp    x29,lr,[sp,#outsz]       // save <x29,lr> at bottom of local area
        add    x29,sp,#outsz            // setup x29 points to bottom of local area
    ```

1. Nicht verkettete Leaf-Funktionen (lr nicht gespeichert)

    ```asm
        stp    x19,x20,[sp,#-80]!       // pre-indexed, save in 1st FP/INT reg-pair
        stp    x21,x22,[sp,#16]
        str    x23,[sp,#32]
        stp    d8,d9,[sp,#40]           // save FP regs (optional)
        stp    d10,d11,[sp,#56]
        sub    sp,sp,#(framesz-80)      // allocate the remaining local area
    ```

   Der Zugriff auf alle lokalen Variablen erfolgt auf Basis des SP. \<x29, lr> zeigt auf den vorherigen Frame. Wenn die Framegröße \<= 512 ist, kann „sub sp,...“ zur Optimierung weggelassen werden, wenn der gespeicherte Bereich der Register an das Ende des Stapels verschoben wird. Der Nachteil ist, dass das Layout dann nicht mit anderen übereinstimmt, und gespeicherte Register nehmen einen Teil des Bereichs für Registerpaare und den prä- und postindizierten Offsetadressierungsmodus ein.

1. Nicht verkettete Non-Leaf-Funktionen (lr wird im gespeicherten Integerbereich gespeichert)

    ```asm
        stp    x19,x20,[sp,#-80]!       // pre-indexed, save in 1st FP/INT reg-pair
        stp    x21,x22,[sp,#16]         // ...
        stp    x23,lr,[sp,#32]          // save last Int reg and lr
        stp    d8,d9,[sp,#48]           // save FP reg-pair (optional)
        stp    d10,d11,[sp,#64]         // ...
        sub    sp,sp,#(framesz-80)      // allocate the remaining local area
    ```

   Alternativ bei einer geraden Anzahl gespeicherter Integerregister:

    ```asm
        stp    x19,x20,[sp,#-80]!       // pre-indexed, save in 1st FP/INT reg-pair
        stp    x21,x22,[sp,#16]         // ...
        str    lr,[sp,#32]              // save lr
        stp    d8,d9,[sp,#40]           // save FP reg-pair (optional)
        stp    d10,d11,[sp,#56]         // ...
        sub    sp,sp,#(framesz-80)      // allocate the remaining local area
    ```

   Wenn nur x19 gespeichert wird:

    ```asm
        sub    sp,sp,#16                // reg save area allocation*
        stp    x19,lr,[sp]              // save x19, lr
        sub    sp,sp,#(framesz-16)      // allocate the remaining local area
    ```

   \* Die Speicherbereichzuordnung für Register wird nicht in stp gefaltet, weil ein präindizierter stp-Befehl für reg-lr nicht mit Entladungscodes dargestellt werden kann.

   Der Zugriff auf alle lokalen Variablen erfolgt auf Basis des SP. \<x29> zeigt auf den vorherigen Frame.

1. Verkettet, #framesz \<= 512, #outs = 0

    ```asm
        stp    x29,lr,[sp,#-framesz]!       // pre-indexed, save <x29,lr>
        mov    x29,sp                       // x29 points to bottom of stack
        stp    x19,x20,[sp,#(framesz-32)]   // save INT pair
        stp    d8,d9,[sp,#(framesz-16)]     // save FP pair
    ```

   Im Vergleich zum ersten obigen Prologbeispiel besteht der Vorteil darin, dass alle Registerspeicheranweisungen nach nur einer Stapelzuordnungsanweisung zur Ausführung bereit sind. Das bedeutet, dass keine Abhängigkeit vom SP vorliegt, die eine Parallelität auf Anweisungsebene verhindert.

1. Verkettet, Framegröße > 512 (optional für Funktionen ohne alloca)

    ```asm
        stp    x29,lr,[sp,#-80]!            // pre-indexed, save <x29,lr>
        stp    x19,x20,[sp,#16]             // save in INT regs
        stp    x21,x22,[sp,#32]             // ...
        stp    d8,d9,[sp,#48]               // save in FP regs
        stp    d10,d11,[sp,#64]
        mov    x29,sp                       // x29 points to top of local area
        sub    sp,sp,#(framesz-80)          // allocate the remaining local area
    ```

   Zur Optimierung kann x29 an jeder beliebigen Position im lokalen Bereich eingefügt werden, um eine bessere Abdeckung für das Registerpaar und den prä- bzw. postindizierten Offsetadressierungsmodus zu bieten. Auf lokale Variablen unterhalb von Framezeigern kann auf Basis des SP zugegriffen werden.

1. Verkettet, Framegröße > 4 KB, mit oder ohne alloca()

    ```asm
        stp    x29,lr,[sp,#-80]!            // pre-indexed, save <x29,lr>
        stp    x19,x20,[sp,#16]             // save in INT regs
        stp    x21,x22,[sp,#32]             // ...
        stp    d8,d9,[sp,#48]               // save in FP regs
        stp    d10,d11,[sp,#64]
        mov    x29,sp                       // x29 points to top of local area
        mov    x15,#(framesz/16)
        bl     __chkstk
        sub    sp,sp,x15,lsl#4              // allocate remaining frame
                                            // end of prolog
        ...
        sub    sp,sp,#alloca                // more alloca() in body
        ...
                                            // beginning of epilog
        mov    sp,x29                       // sp points to top of local area
        ldp    d10,d11,[sp,#64]
        ...
        ldp    x29,lr,[sp],#80              // post-indexed, reload <x29,lr>
    ```

## <a name="arm64-exception-handling-information"></a>Informationen zur ARM64-Ausnahmebehandlung

### <a name="pdata-records"></a>PDATA-Datensätze

Die PDATA-Datensätze sind ein geordnetes Elementarray mit fester Länge, die jede Stapelbearbeitungsfunktion in einer PE-Binärdatei beschreiben. Der Ausdruck „Stapelbearbeitung“ ist wichtig: Leaf-Funktionen, die keinen lokalen Speicher belegen und keine nicht flüchtigen Register speichern oder wiederherstellen müssen, benötigen keinen PDATA-Datensatz. Diese Datensätze sollten explizit weggelassen werden, um Speicherplatz zu sparen. Eine Entladung von einer dieser Funktionen kann die Rückgabeadresse direkt vom LR abrufen, um zur aufrufenden Funktion zu wechseln.

Jeder PDATA-Datensatz für ARM64 hat eine Länge von 8 Byte. Im allgemeinen Format für jeden Datensatz wird die 32-Bit-RVA (relative virtuelle Adresse) des Funktionsstarts im ersten Wort eingefügt. Diesem folgt ein zweites Wort, das entweder einen Zeiger auf einen XDATA-Block mit variabler Länge enthält oder ein gepacktes Wort, das die Entladesequenz einer kanonischen Funktion beschreibt.

![PDATA-Datensatzlayout](media/arm64-exception-handling-pdata-record.png "PDATA-Datensatzlayout")

Die Felder haben folgenden Zweck:

- **Function Start RVA** (RVA für Funktionsbeginn) ist der 32-Bit-RVA des Funktionsbeginns.

- **Flag** ist ein 2-Bit-Feld, das angibt, wie die verbleibenden 30 Bit des zweiten PDATA-Worts zu interpretieren sind. Wenn **Flag** den Wert 0 hat, bilden die übrigen Bits den **Exception Information RVA** (RVA für Ausnahmeinformationen), wobei die beiden niedrigsten Bits implizit 0 sind. Wenn **Flag** ungleich 0 (null) ist, bilden die übrigen Bits die Struktur **Packed Unwind Data** (Gepackte Entladedaten).

- **Exception Information RVA** (RVA für Ausnahmeinformationen) enthält die Adresse der Ausnahmeinformationsstruktur mit variabler Länge, die im XDATA-Abschnitt gespeichert wird. Diese Daten müssen 4-Bytes ausgerichtet sein.

- **Packed Unwind Data** (Gepackte Entladedaten) enthält eine komprimierte Beschreibung der Vorgänge, die für die Entladung einer Funktion nötig sind. Dabei wird von einer kanonischen Form ausgegangen. In diesem Fall ist kein .xdata-Datensatz erforderlich.

### <a name="xdata-records"></a>XDATA-Datensätze

Wenn das gepackte Entladeformat nicht zur Beschreibung der Entladung einer Funktion ausreicht, muss ein .xdata-Datensatz mit variabler Länge erstellt werden. Die Adresse dieses Datensatzes wird im zweiten Wort des .pdata-Datensatzes gespeichert. Das Format des XDATA-Datensatz setzt sich aus gepackten Wörtern mit variabler Länge zusammen:

![XDATA-Datensatzlayout](media/arm64-exception-handling-xdata-record.png "XDATA-Datensatzlayout")

Diese Daten sind in vier Abschnitte unterteilt:

1. Ein Ein- oder Zwei-Wort-Header, der die Gesamtgröße der Struktur beschreibt und wichtige Funktionsdaten enthält. Das zweite Wort ist nur vorhanden, wenn die Felder **Epilog Count** (Epiloganzahl) und **Code Words** (Codewörter) auf 0 festgelegt sind. Der Header enthält diese Bitfelder:

   a. **Function Length** (Funktionslänge) ist ein 18-Bit-Feld. Es gibt die Gesamtlänge der Funktion in Byte geteilt durch 4 an. Wenn eine Funktion größer als 1 MB ist, müssen mehrere PDATA- und XDATA-Datensätze verwendet werden, um diese zu beschreiben. Weitere Informationen finden Sie im Abschnitt [Große Funktionen](#large-functions).

   b. **Vers** (Version) ist ein 2-Bit-Feld. Es gibt die Version der restlichen XDATA-Daten an. Derzeit ist nur Version 0 definiert, sodass Werte von 1 bis 3 nicht zulässig sind.

   c. **X** ist ein 1-Bit-Feld. Es gibt das Vorhandensein (1) oder Fehlen (0) von Ausnahmedaten an.

   d. **E** ist ein 1-Bit-Feld. Es gibt an, dass die Informationen, die einen einzelnen Epilog beschreiben in den Header gepackt werden (1), sodass später keine zusätzlichen Bereichswörter mehr erforderlich sind (0).

   e. **Epilog Count** (Epiloganzahl) ist ein 5-Bit-Feld mit zwei Bedeutungen, die vom Status des **E**-Bits abhängen:

      1. Wenn **E** den Wert 0 aufweist, wird die Gesamtanzahl der in Abschnitt 2 beschriebenen Epilogbereiche angegeben. Sind über 31 Bereiche in der Funktion vorhanden, muss das Feld **Code Words** (Codewörter) auf 0 festgelegt werden, damit angegeben wird, dass ein Ausnahmewort erforderlich ist.

      2. Wenn **E** den Wert 1 aufweist, legt dieses Feld den Index des ersten Entladungscodes fest, der den einzigen vorhandenen Epilog beschreibt.

   f. **Code Words** (Codewörter) ist ein 5-Bit-Feld, das die Anzahl der 32-Bit-Wörter angibt, die für alle Entladungscodes in Abschnitt 3 benötigt werden. Sind über 31 Wörter (also mehr als 124 Entladungscodebytes) erforderlich, muss dieses Feld auf 0 festgelegt werden, damit angegeben wird, dass ein Ausnahmewort erforderlich ist.

   g. **Extended Epilog Count** (Erweiterte Epiloganzahl) und **Extended Code Words** (Erweiterte Codewörter) sind 16-Bit- bzw. 8-Bit-Felder. Sie bieten mehr Speicherplatz für das Codieren ungewöhnlich vieler Epiloge oder Entladungscodewörter. Das Erweiterungswort, das diese Felder enthält, ist nur vorhanden, wenn die Felder **Epilog Count** (Epiloganzahl) und **Code Words** (Codewörter) im ersten Headerwort den Wert 0 aufweisen.

1. Wenn **Epilog Count** (Epiloganzahl) ungleich 0 ist, folgt dem Header und dem optionalen erweiterten Header eine Liste mit Informationen zu den Epilogbereichen, die in ein Wort gepackt ist. Sie werden nach aufsteigendem Startoffset gespeichert. Jeder Bereich enthält die folgenden Bits:

   a. **Epilog Start Offset** (Startoffset des Epilogs) ist ein 18-Bit-Feld, das den Epilogoffset in Byte geteilt durch 4 enthält, der relativ zum Funktionsbeginn ist.

   b. **Res** (Reserviert) ist ein 4-Bit-Feld, das für künftige Erweiterungen reserviert ist. Sein Wert muss 0 sein.

   c. **Epilog Start Index** (Startindex des Epilogs) ist ein 10-Bit-Feld (2 Bits länger als **Extended Code Words** (Erweiterte Codewörter)). Es gibt den Byteindex des ersten Entladungscodes an, der diesen Epilog beschreibt.

1. Nach der Liste der Epilogbereichen folgt ein Bytearray, das Entladungscodes enthält. Diese werden in einem späteren Abschnitt ausführlich beschrieben. Dieses Array ist am Ende aufgefüllt bis zur nächsten vollen Wortgrenze. Entladungscodes werden in dieses Array geschrieben. Dabei wird mit demjenigen begonnen, der dem Hauptteil der Funktion am nächsten ist, und der Vorgang wird bis zum Funktionsende fortgesetzt. Die Bytes für jeden Entladungscode werden in Big-Endian-Reihenfolge gespeichert, sodass sie direkt abgerufen werden können. Dabei wird mit dem wichtigsten Byte begonnen, das den Vorgang und die Länge des restlichen Codes identifiziert.

1. Wenn das **X**-Bit im Header auf 1 festgelegt wurde, werden die Informationen zum Ausnahmehandler angezeigt. Diese bestehen aus einem einzelnen **Exception Handler RVA** (RVA für Ausnahmehandler), die die Adresse des Ausnahmehandlers bereitstellt. Dieser folgt die für den Ausnahmehandler erforderliche Datenmenge, deren Länge variiert.

Der XDATA-Datensatz ist so gestaltet, dass die ersten 8 Byte abgerufen werden und zur Berechnung der Gesamtgröße des Datensatzes verwendet werden können. Dabei wird die Länge der folgenden Ausnahmedaten variabler Länge abgezogen. Der folgende Codeausschnitt berechnet die Datensatzgröße:

```cpp
ULONG ComputeXdataSize(PULONG *Xdata)
{
    ULONG EpilogScopes;
    ULONG Size;
    ULONG UnwindWords;

    if ((Xdata[0] >> 27) != 0) {
        Size = 4;
        EpilogScopes = (Xdata[0] >> 22) & 0x1f;
        UnwindWords = (Xdata[0] >> 27) & 0x0f;
    } else {
        Size = 8;
        EpilogScopes = Xdata[1] & 0xffff;
        UnwindWords = (Xdata[1] >> 16) & 0xff;
    }

    Size += 4 * EpilogScopes;
    Size += 4 * UnwindWords;
    if (Xdata[0] & (1 << 20)) {
        Size += 4;        // exception handler RVA
    }
    return Size;
}
```

Obwohl der Prolog und jeder Epilog einen Index in den Entladungscodes besitzen, teilen sich die beiden die Tabelle. Es ist möglich (und nicht ungewöhnlich), dass sie denselben Codes gemeinsam nutzen können. Ein Beispiel finden Sie unter „Beispiel 2“ im Abschnitt [Beispiele](#examples). Compilerautoren sollten Optimierungen für insbesondere diesen Fall implementieren, denn der größtmögliche Index ist 255. Dadurch wird die Gesamtzahl der Entladungscodes für eine bestimmte Funktion begrenzt.

### <a name="unwind-codes"></a>Entladungscodes

Das Entladungscodearray ist ein Sequenzpool, der genau beschreibt, wie die Auswirkungen des Prologs rückgängig gemacht werden. Dieser wird in der Reihenfolge gespeichert, in der die Vorgänge rückgängig gemacht werden müssen. Die Entladungscodes sind quasi eine Reihe von Minianweisungen, die als eine Bytezeichenfolge codiert sind. Wenn die Ausführung beendet ist, befindet sich die Rückgabeadresse der aufrufenden Funktion im LR. Alle nicht flüchtigen Register werden darüber hinaus zu dem Zeitpunkt wiederhergestellt, zu dem die Funktion aufgerufen wurde.

Würden Ausnahmen garantiert immer nur innerhalb einer Funktion und niemals im Prolog oder Epilog auftreten, wäre nur eine Sequenz nötig. Für das Windows-Entlademodell ist jedoch erforderlich, dass Code aus einem partiell ausgeführten Prolog oder Epilog entladen werden kann. Damit diese Anforderung erfüllt wird, wurden die Entladungscodes so entwickelt, dass eine eindeutige 1:1-Zuordnung zu jedem relevanten Opcode im Prolog und Epilog vorhanden ist. Diese Konzeption hat mehrere Auswirkungen:

1. Es ist möglich, die Länge von Prolog und Epilog zu berechnen, indem die Anzahl der Entladungscodes gezählt wird.

1. Indem die Anzahl der Anweisungen nach dem Anfang eines Epilogbereichs gezählt wird, ist es möglich, die entsprechende Anzahl von Entladungscodes zu überspringen. Anschließend können Sie den Rest einer Sequenz ausführen, um die durch den Epilog partiell ausgeführte Entladung abzuschließen.

1. Indem die Anzahl der Anweisungen vor dem Ende des Prologs gezählt wird, ist es möglich, die entsprechende Anzahl von Entladungscodes zu überspringen. Anschließend können Sie den Rest der Sequenz ausführen, um nur die Teile des Prologs rückgängig zu machen, die bereits ausgeführt wurden.

Die Entladungscodes werden der folgenden Tabelle entsprechend codiert. Alle Entladungscodes sind ein Einzel- oder Doppelbytes, sofern sie nicht einen sehr großen Stapel zuordnen. Insgesamt gibt es 21 Entladungscodes. Jeder Entladungscode ordnet genau eine Anweisung im Prolog oder Epilog zu, um das Entladen partiell ausgeführter Prologe und Epiloge zu ermöglichen.

|Entladungscode|Bits und Interpretation|
|-|-|
|`alloc_s`|000xxxxx: Ein kleiner Stapel mit der Größe \< 512 (25 × 16) wird zugeordnet.|
|`save_r19r20_x`|    001zzzzz: Das Paar \<x19,x20> wird unter `[sp-#Z*8]!` gespeichert, der präindizierte Offset ist >= –248. |
|`save_fplr`|        01zzzzzz: Das Paar \<x29,lr> wird unter `[sp+#Z*8]` gespeichert, der Offset ist \<= 504. |
|`save_fplr_x`|        10zzzzzz: Das Paar \<x29, lr> wird unter `[sp-(#Z+1)*8]!` gespeichert, der präindizierte Offset ist >= –512. |
|`alloc_m`|        11000xxx'xxxxxxxx: Ein kleiner Stapel mit der Größe \< 16000(211 × 16) wird zugeordnet. |
|`save_regp`|        110010xx'xxzzzzzz: Das Paar x(19+#X) wird unter `[sp+#Z*8]` gespeichert, der Offset ist \<= 504. |
|`save_regp_x`|        110011xx'xxzzzzzz: Das Paar x(19+#X) wird unter `[sp-(#Z+1)*8]!` gespeichert, der präindizierte Offset ist >= –512. |
|`save_reg`|        110100xx'xxzzzzzz: Das Register x(19+#X) wird unter `[sp+#Z*8]` gespeichert, der Offset ist \<= 504. |
|`save_reg_x`|        1101010x'xxxzzzzz: Das Register x(19+#X) wird unter `[sp-(#Z+1)*8]!` gespeichert, der präindizierte Offset ist >= –256. |
|`save_lrpair`|         1101011x'xxzzzzzz: Das Paar \<x(19+2*#X),lr> wird unter `[sp+#Z*8]` gespeichert, der Offset ist \<= 504. |
|`save_fregp`|        1101100x'xxzzzzzz: Das Paar d(8+#X) wird unter `[sp+#Z*8]` gespeichert, der Offset ist \<= 504. |
|`save_fregp_x`|        1101101x'xxzzzzzz: Das Paar d(8+#X) wird unter `[sp-(#Z+1)*8]!` gespeichert, der präindizierte Offset ist >= –512. |
|`save_freg`|        1101110x'xxzzzzzz: Das Register d(8+#X) wird unter `[sp+#Z*8]` gespeichert, der Offset ist \<= 504. |
|`save_freg_x`|        11011110'xxxzzzzz: Das Register d(8+#X) wird unter `[sp-(#Z+1)*8]!` gespeichert, der präindizierte Offset ist >= –256. |
|`alloc_l`|         11100000'xxxxxxxx'xxxxxxxx'xxxxxxxx: Ein kleiner Stapel mit der Größe \< 256M(224 × 16) wird zugeordnet. |
|`set_fp`|        11100001: x29 wird mit `mov x29,sp` eingerichtet. |
|`add_fp`|        11100010'xxxxxxxx: x29 wird mit `add x29,sp,#x*8` eingerichtet. |
|`nop`|            11100011: Es ist kein Entladevorgang erforderlich. |
|`end`|            11100100: Ende des Entladungscodes, impliziert ret im Epilog |
|`end_c`|        11100101: Ende des Entladungscodes im aktuellen verketteten Bereich |
|`save_next`|        11100110: Das nächste nicht flüchtige Integer- oder FP-Registerpaar wird gespeichert. |
|`arithmetic(add)`|    11100111'000zxxxx: Das Cookie reg(z) wird zu lr (0=x28, 1=sp); `add lr, lr, reg(z)` hinzugefügt. |
|`arithmetic(sub)`|    11100111'001zxxxx: Subookie reg(z) von lr (0=x28, 1=sp); `sub lr, lr, reg(z)` |
|`arithmetic(eor)`|    11100111'010zxxxx: eor-Vorgang für lr mit Cookie reg(z) (0=x28, 1=sp); `eor lr, lr, reg(z)` |
|`arithmetic(rol)`|    11100111'0110xxxx: simulierter rol-Vorgang für lr mit Cookie reg (x28); xip0 = neg x28; `ror lr, xip0` |
|`arithmetic(ror)`|    11100111'100zxxxx: ror-Vorgang für lr mit Cookie reg(z) (0=x28, 1=sp); `ror lr, lr, reg(z)` |
| |            11100111: xxxz----: ----, reserviert |
| |              11101xxx: Für folgende benutzerdefinierte Stapelfälle reserviert, wird nur für ASM-Routinen generiert. |
| |              11101000: Benutzerdefinierter Stapel für MSFT_OP_TRAP_FRAME |
| |              11101001: Benutzerdefinierter Stapel für MSFT_OP_MACHINE_FRAME |
| |              11101010: Benutzerdefinierter Stapel für MSFT_OP_CONTEXT |
| |              11101100: Benutzerdefinierter Stapel für MSFT_OP_CLEAR_UNWOUND_TO_CALL |
| |              1111xxxx: reserviert |

Die Anweisungen mit großen Werten umfassen mehrere Bytes, wobei die wichtigsten Bits zuerst gespeichert sind. Mit dieser Konzeption können Sie die Gesamtgröße des Entladungscodes in Byte ermitteln, indem Sie nur das erste Byte des Codes suchen. Da jeder Entladungscode genau einer Anweisung in einem Prolog oder Epilog zugeordnet ist, können Sie die Größe des Prologs oder Epilogs berechnen. Sie können die Sequenz von Beginn bis Ende durchlaufen und eine Nachschlagetabelle oder ein ähnliches Mittel verwenden, um die Länge des entsprechenden Opcodes zu bestimmen.

Die postindizierte Offsetadressierung ist in einem Prolog nicht zulässig. Alle Offsetbereiche (#Z) entsprechen der Codierung der STP/STR-Adressierung. Eine Ausnahme ist `save_r19r20_x`, bei der 248 für alle Speicherbereiche ausreichend ist (10 Integerregister + 8 FP-Register + 8 Eingaberegister).

`save_next` muss ein Speichervorgang für ein flüchtiges Integer- oder FP-Registerpaar folgen: `save_regp`, `save_regp_x`, `save_fregp`, `save_fregp_x`, `save_r19r20_x` oder noch einmal `save_next`. Dabei wird das nächste Registerpaar im nächsten 16-Byte-Slot in aufsteigender Reihenfolge gespeichert. `save_next` verweist auf das erste FP-Registerpaar, wenn es auf den `save-next`-Befehl folgt, der das letzte Integerregisterpaar angibt.

Da die Größe der regulären Rückgabe- und Sprunganweisungen identisch ist, ist bei Endaufrufen kein separater `end`-Entladungscode erforderlich.

`end_c` ist so konzipiert, dass nicht zusammenhängende Funktionsfragmente zu Optimierungszwecken verarbeitet werden. Auf einen `end_c`-Code, der das Ende der Entladungscodes im aktuellen Bereich angibt, müssen weitere Entladungscodes folgen, auf die ein echter `end`-Code folgt. Die Entladungscodes zwischen `end_c` und `end` stellen die Prologvorgänge in der übergeordneten Region (Phantomprolog) dar.  Weitere Details und Beispiele werden im folgenden Abschnitt beschrieben.

### <a name="packed-unwind-data"></a>Gepackte Entladedaten

Bei Funktionen, deren Prologe und Epiloge der unten beschriebenen kanonischen Form entsprechen, können gepackte Entladedaten verwendet werden. Dadurch ist kein ganzer XDATA-Datensatz erforderlich, sodass der Aufwand für die Bereitstellung von Entladedaten erheblich reduziert wird. Die kanonischen Prologe und Epiloge sind so konzipiert, dass sie die allgemeinen Anforderungen einer einfachen Funktion erfüllen: Eine Funktion, die keinen Ausnahmehandler benötigt und deren Setup- und Beendigungsvorgänge in der Standardreihenfolge durchgeführt werden.

Ein PDATA-Datensatz mit gepackten Entladedaten weist folgendes Format auf:

![PDATA-Datensatz mit gepackten Entladedaten](media/arm64-exception-handling-packed-unwind-data.png "PDATA-Datensatz mit gepackten Entladedaten")

Die Felder haben folgenden Zweck:

- **Function Start RVA** (RVA für Funktionsbeginn) ist der 32-Bit-RVA des Funktionsbeginns.
- **Flag** ist wie oben beschrieben ein 2-Bit-Feld mit folgenden Bedeutungen:
  - 00 = Gepackte Entladedaten werden nicht verwendet; verbleibende Bits zeigen auf den XDATA-Datensatz.
  - 01 = Gepackte Entladedaten, die mit einem einzelnen Prolog und Epilog am Anfang und Ende des Bereichs verwendet werden.
  - 10 = Gepackte Entladedaten, die für Code ohne Prolog und Epilog verwendet werden. Diese sind zum Beschreiben separater Funktionssegmente nützlich.
  - 11 = reserviert
- **Function Length** (Funktionslänge) ist ein 11-Bit-Feld, das die Länge der gesamten Funktion in Byte geteilt durch 4 angibt. Wenn die Funktion größer als 8000 ist, muss stattdessen ein voller XDATA-Datensatz verwendet werden.
- **Frame Size** (Framegröße) ist ein 9-Bit-Feld, das die Byteanzahl des Stapels, der dieser Funktion zugeordnet ist, geteilt durch 16 angibt. Funktionen, die einen Stapel über 8000–16 Byte zuordnen, müssen einen vollständigen XDATA-Datensatz verwenden. Dazu zählen der Bereich für lokale Variablen, für ausgehende Parameter, für nicht flüchtige Integer- und FP-Register und für Basisparameter, jedoch nicht der Bereich für die dynamische Zuordnung.
- **CR** ist ein 2-Bit-Flag, das angibt, ob die Funktion zusätzliche Anweisungen für das Einrichten einer Framekette und eines Rückgabelinks enthält:
  - 00 = Nicht verkettete Funktion, das Paar \<x29, lr> wird nicht im Stapel gespeichert.
  - 01 = Nicht verkettete Funktion, \<lr> wird im Stapel gespeichert.
  - 10 = reserviert
  - 11 = Verkettete Funktion, eine Anweisung für ein Speicher-Lade-Paar wird im Prolog oder Epilog \<x29,lr> verwendet.
- **H** ist ein 1-Bit-Flag, das angibt, ob die Funktion die Integerparameterregister (x0–x7) herausgreift, indem sie am Anfang der Funktion gespeichert werden. (0 = greift Register nicht heraus, 1 = greift Register heraus)
- **RegI** ist ein 4-Bit-Feld, das die Anzahl der nicht flüchtigen Int-Register (x19–x28) angibt, die am kanonischen Stapelspeicherort gespeichert sind.
- **RegF** ist ein 3-Bit-Feld, das die Anzahl der nicht flüchtigen FP-Register (d8–d15) angibt, die am kanonischen Stapelspeicherort gespeichert sind. (RegF = 0: Es wird kein FP-Register gespeichert. RegF > 0: RegF + 1 FP-Register werden gespeichert.) Gepackte Entladedaten können nicht für Funktionen verwendet werden, bei denen nur ein FP-Register gespeichert wird.

Kanonische Prologe, die in die Kategorien 1, 2 (ohne ausgehenden Parameterbereich), 3 und 4 im obigen Abschnitt fallen, können durch das gepackte Entladeformat dargestellt werden.  Die Epiloge für kanonische Funktionen folgen einem ähnlichen Format. Es besteht jedoch der Unterschied, dass **H** keine Auswirkung hat, die `set_fp`-Anweisung ausgelassen wird und die Reihenfolge der Schritte und die Anweisungen in jedem Schritt im Epilog rückgängig gemacht werden. Der Algorithmus für gepackte XDATA-Datensätze folgt den Schritten in der folgenden Tabelle:

Schritt 0: Die Größe der einzelnen Bereiche wird vorberechnet.

Schritt 1: Die nicht flüchtigen Integerregister werden gespeichert.

Schritt 2: Dieser Schritt gilt nur für Typ 4 in den vorherigen Abschnitten. Am Ende des Integerbereichs wird lr gespeichert.

Schritt 3: Die nicht flüchtigen FP-Register werden gespeichert.

Schritt 4: Die Eingabeargumente werden im Basisparameterbereich gespeichert.

Schritt 5: Die verbleibenden Stapel werden zugewiesen, einschließlich des lokalen Bereichs, des Paars \<x29,lr> und des Bereichs für ausgehende Parameter. 5a entspricht dem kanonischen Typ 1. 5b und 5c gelten für den kanonischen Typ 2. 5d und 5e gelten für Typ 3 und Typ 4.

Schrittnummer|Flagwerte|Anzahl der Anweisungen|Opcode|Entladungscode
-|-|-|-|-
0|||`#intsz = RegI * 8;`<br/>`if (CR==01) #intsz += 8; // lr`<br/>`#fpsz = RegF * 8;`<br/>`if(RegF) #fpsz += 8;`<br/>`#savsz=((#intsz+#fpsz+8*8*H)+0xf)&~0xf)`<br/>`#locsz = #famsz - #savsz`|
1|0 < **RegI** <= 10|RegI / 2 + **RegI** % 2|`stp x19,x20,[sp,#savsz]!`<br/>`stp x21,x22,[sp,#16]`<br/>`...`|`save_regp_x`<br/>`save_regp`<br/>`...`
2|**CR**==01*|1|`str lr,[sp,#(intsz-8)]`\*|`save_reg`
3|0 < **RegF** <=7|(RegF + 1) / 2 +<br/>(RegF + 1) % 2)|`stp d8,d9,[sp,#intsz]`\*\*<br/>`stp d10,d11,[sp,#(intsz+16)]`<br/>`...`<br/>`str d(8+RegF),[sp,#(intsz+fpsz-8)]`|`save_fregp`<br/>`...`<br/>`save_freg`
4|**H** == 1|4|`stp x0,x1,[sp,#(intsz+fpsz)]`<br/>`stp x2,x3,[sp,#(intsz+fpsz+16)]`<br/>`stp x4,x5,[sp,#(intsz+fpsz+32)]`<br/>`stp x6,x7,[sp,#(intsz+fpsz+48)]`|`nop`<br/>`nop`<br/>`nop`<br/>`nop`
5a|**CR** == 11 && #locsz<br/> <= 512|2|`stp x29,lr,[sp,#-locsz]!`<br/>`mov x29,sp`\*\*\*|`save_fplr_x`<br/>`set_fp`
5 b|**CR** == 11 &&<br/>512 < #locsz <= 4080|3|`sub sp,sp,#locsz`<br/>`stp x29,lr,[sp,0]`<br/>`add x29,sp,0`|`alloc_m`<br/>`save_fplr`<br/>`set_fp`
5c|**CR** == 11 && #locsz > 4080|4|`sub sp,sp,4080`<br/>`sub sp,sp,#(locsz-4080)`<br/>`stp x29,lr,[sp,0]`<br/>`add x29,sp,0`|`alloc_m`<br/>`alloc_s`/`alloc_m`<br/>`save_fplr`<br/>`set_fp`
5d|(**CR** == 00 \|\| **CR**==01) &&<br/>#locsz <= 4080|1|`sub sp,sp,#locsz`|`alloc_s`/`alloc_m`
5e|(**CR** == 00 \|\| **CR**==01) &&<br/>#locsz > 4080|2|`sub sp,sp,4080`<br/>`sub sp,sp,#(locsz-4080)`|`alloc_m`<br/>`alloc_s`/`alloc_m`

\* Wenn **CR** == 01 und **RegI** eine ungerade Zahl ist, werden Schritt 2 und der letzte save_rep-Befehl in Schritt 1 zu einem save_regp-Befehl zusammengeführt.

\*\* Wenn **RegI** == **CR** == 0 und **RegF** != 0 ist, führt der erste stp-Befehl für die Gleitkommazahl den Prädekrementvorgang durch.

\*\*\* Im Epilog ist keine Anweisung vorhanden, die `mov x29,sp` entspricht. Gepackte Entladedaten können nicht verwendet werden, wenn eine Funktion eine Wiederherstellung von sp über x29 erfordert.

### <a name="unwinding-partial-prologs-and-epilogs"></a>Entladen partieller Prologe und Epiloge

Der häufigste Entladungsfall ist, dass eine Ausnahme oder ein Aufruf im Text der Funktion außerhalb der Prologe und Epiloge auftritt. In dieser Situation ist das Entladen ein geradliniger Prozess: Der Entlader beginnt mit der Ausführung des Codes im Entladearray (bei Index 0) und setzt diesen Vorgang fort, bis beendender Opcode ermittelt wird.

Die Entladung gestaltet sich schwieriger, wenn eine Ausnahme oder ein Interrupt auftritt, während ein Prolog oder Epilog ausgeführt wird. In diesen Fällen wird der Stapelrahmen nur teilweise konstruiert. Das Problem besteht darin, durchgeführte Aktionen genau zu bestimmen, damit diese ordnungsgemäß rückgängig gemacht werden können.

Nehmen Sie diese Prolog- und Epilogsequenz als Beispiel:

```asm
0000:    stp    x29,lr,[sp,#-256]!          // save_fplr_x  256 (pre-indexed store)
0004:    stp    d8,d9,[sp,#224]             // save_fregp 0, 224
0008:    stp    x19,x20,[sp,#240]           // save_regp 0, 240
000c:    mov    x29,sp                      // set_fp
         ...
0100:    mov    sp,x29                      // set_fp
0104:    ldp    x19,x20,[sp,#240]           // save_regp 0, 240
0108:    ldp    d8,d9,[sp,224]              // save_fregp 0, 224
010c:    ldp    x29,lr,[sp],#256            // save_fplr_x  256 (post-indexed load)
0110:    ret    lr                          // end
```

Neben jedem Opcode befindet sich der entsprechende Entladungscode, der diesen Vorgang beschreibt. Sie sehen, dass die Sequenz der Entladungscodes für den Prolog im Vergleich zu derjenigen für den Epilog gespiegelt ist (von der letzten Anweisung des Epilogs abgesehen). Dieser Fall kommt häufig vor. Deshalb gehen wir immer davon aus, dass die Entladungscodes für den Prolog in umgekehrter Reihenfolge zur Ausführung des Prologs gespeichert werden.

Für Prolog und Epilog gibt es also gemeinsamen Entladungscodes:

`set_fp`, `save_regp 0,240`, `save_fregp,0,224`, `save_fplr_x_256`, `end`

Der Epilogfall ist geradlinig, da eine normale Reihenfolge vorliegt. Wenn bei Offset 0 innerhalb des Epilogs (der bei Offset 0x100 in der Funktion beginnt) begonnen wird, wird erwartet, dass die vollständige Entladesequenz ausgeführt wird, da noch kein Bereinigung durchgeführt wurde. Wenn wir uns eine Anweisung weiter (am Offset 2 im Epilog) befinden, können wir den ersten Entladungscode überspringen. Diese Situation lässt sich verallgemeinern, indem wir annehmen, dass eine 1:1-Zuordnung zwischen Opcodes und Entladungscodes vorliegt. Dann sollten die ersten *n* Entladungscodes übersprungen und von dieser Position aus begonnen werden, um mit der Entladung von Anweisung *n* aus im Epilog zu beginnen.

Eine ähnliche Logik funktioniert für den Prolog, die Reihenfolge ist jedoch umgekehrt. Wenn wir mit der Auflösung von Offset 0 im Prolog beginnen, soll nichts ausgeführt werden. Wenn wir den Entladevorgang bei Offset 2 starten, der schon eine Anweisung weiter ist, soll die Entladesequenz einen Entladungscode vor dem Ende beginnen. Bedenken Sie, dass die Codes in umgekehrter Reihenfolge gespeichert werden. Auch das lässt sich verallgemeinern: Wenn die Entladung bei Anweisung n im Prolog beginnt, sollten zuerst n Entladungscodes vom Ende der Codeliste an ausgeführt werden.

Die Prolog- und Epilogcodes stimmen nicht immer exakt überein. Deshalb muss das Entladungscodearray möglicherweise mehrere Codesequenzen enthalten. Verwenden Sie folgende Logik, um den Offset zu bestimmen, an dem mit der Verarbeitung der Codes begonnen werden soll:

1. Wenn die Entladung im Funktionstext erfolgt, beginnen Sie mit der Ausführung der Entladungscodes bei Index 0, und fahren Sie fort, bis ein beendigender Opcode erreicht wird.

1. Wenn die Entladung in einem Epilog erfolgt, verwenden Sie den epilogspezifischen Startindex, der vom Epilogbereich als Startpunkt angegeben wird. Berechnen Sie, wie viele Bytes sich der jeweilige PC vom Beginn des Epilogs weg befindet. Durchlaufen Sie die Entladungscodes dann vorwärts, wodurch diese übersprungen werden, bis alle bereits ausgeführten Anweisungen einbezogen sind. Beginnen Sie an diesem Punkt mit der Ausführung.

1. Wenn Sie im Prolog eine Entladung durchführen, sollten Sie Index 0 als Ausgangspunkt verwenden. Berechnen Sie die Länge des Prologcodes aus der Sequenz und dann, wie viele Bytes der jeweilige PC sich vom Ende des Prologs weg befindet. Durchlaufen Sie die Entladungscodes dann vorwärts, wodurch diese übersprungen werden, bis alle noch nicht ausgeführten Anweisungen einbezogen sind. Beginnen Sie an diesem Punkt mit der Ausführung.

Diese Regeln haben zur Folge, dass Entladungscodes für den Prolog immer zuerst im Array stehen müssen. Dabei handelt es sich auch um die Codes, die für die Entladung im Text verwendet werden. Alle epilogspezifischen Codesequenzen sollten unmittelbar folgen.

### <a name="function-fragments"></a>Funktionsfragmente

Zur Codeoptimierung und aus anderen Gründen kann es von Vorteil sein, eine Funktion in Fragmente (Bereiche) aufzuteilen. Nach der Aufteilung benötigt jedes Funktionsfragment jedoch einen separaten PDATA-Datensatz (oder XDATA-Datensatz).

Für jedes getrennte sekundäre Fragment, das einen eigenen Prolog enthält, wird erwartet, dass im Prolog keine Stapelanpassung erfolgt. Sämtlicher Stapelspeicher, der für einen sekundären Bereich erforderlich ist, muss vom übergeordneten Bereich (Hostbereich) zugeordnet werden. Damit werden alle Stapelzeigerbearbeitungen strikt im ursprünglichen Prolog der Funktion gehalten.

Ein typischer Fall von Funktionsfragmenten ist die Codetrennung, bei der der Compiler einen Codebereich aus der Hostfunktion heraus verschiebt. Es gibt drei ungewöhnliche Fälle, die durch die Codetrennung verursacht werden könnten.

#### <a name="example"></a>Beispiel

- (Bereich 1: Anfang)

    ```asm
        stp     x29,lr,[sp,#-256]!      // save_fplr_x  256 (pre-indexed store)
        stp     x19,x20,[sp,#240]       // save_regp 0, 240
        mov     x29,sp                  // set_fp
        ...
    ```

- (Bereich 1: Ende)

- (Bereich 3: Anfang)

    ```asm
        ...
    ```

- (Bereich 3: Ende)

- (Bereich 2: Anfang)

    ```asm
        ...
        mov     sp,x29                  // set_fp
        ldp     x19,x20,[sp,#240]       // save_regp 0, 240
        ldp     x29,lr,[sp],#256        // save_fplr_x  256 (post-indexed load)
        ret     lr                      // end
    ```

- (Bereich 2: Ende)

1. Nur Prolog (Bereich 1: Alle Epiloge befinden sich in separaten Bereichen):

   Nur der Prolog muss beschrieben werden. Das kompakte PDATA-Format kann hierfür nicht verwendet werden. In einem vollständigen XDATA-Fall kann der Wert durch Festlegen von Epilog Count = 0 dargestellt werden. Dies wird in Bereich 1 im obigen Beispiel veranschaulicht.

   Entladungscodes: `set_fp`, `save_regp 0,240`, `save_fplr_x_256`, `end`

1. Nur Epiloge (Bereich 2: Der Prolog befindet sich in der Hostregion.):

   Es wird davon ausgegangen, dass beim Springen in diesen Bereich alle Prologcodes bereits ausgeführt wurden. Eine Teilentladung kann in Epilogen auf dieselbe Weise wie in einer normalen Funktion erfolgen. Für diese Bereichsart kann das kompakte PDATA-Format nicht verwendet werden. Im vollständigen XDATA-Datensatz kann dieser mit einem Phantomprolog codiert werden, der von einem `end_c`- und `end`-Entladungscodepaar umschlossen ist.  Der führende `end_c`-Code gibt an, dass die Größe des Prologs 0 (null) ist. Der Startindex des einzelnen Epilogs zeigt auf `set_fp`.

   Entladungscode für Bereich 2: `end_c`, `set_fp`, `save_regp 0,240`, `save_fplr_x_256`, `end`.

1. Keine Prologe oder Epiloge (Bereich 3: Prologe und alle Epiloge befinden sich in anderen Fragmenten.):

   Das kompakte PDATA-Format kann über die Einstellung Flag = 10 angewendet werden. Legen Sie bei einem vollständigen XDATA-Datensatz Epilog Count = 1 fest. Der Entladungscode ist mit dem oben aufgeführten Code für Bereich 2 identisch, aber der Startindex des Epilogs verweist auch auf `end_c`. Eine Teilentladung erfolgt in diesem Codebereich nie.

Ein weiterer komplizierterer Fall von Funktionsfragmenten ist das Shrink Wrapping. Der Compiler kann die Speicherung einiger nicht flüchtiger Register verzögern, bis er sich außerhalb des Prologs für den Funktionseinstieg befindet.

- (Bereich 1: Anfang)

    ```asm
        stp     x29,lr,[sp,#-256]!      // save_fplr_x  256 (pre-indexed store)
        stp     x19,x20,[sp,#240]       // save_regp 0, 240
        mov     x29,sp                  // set_fp
        ...
    ```

- (Bereich 2: Anfang)

    ```asm
        stp     x21,x22,[sp,#224]       // save_regp 2, 224
        ...
        ldp     x21,x22,[sp,#224]       // save_regp 2, 224
    ```

- (Bereich 2: Ende)

    ```asm
        ...
        mov     sp,x29                  // set_fp
        ldp     x19,x20,[sp,#240]       // save_regp 0, 240
        ldp     x29,lr,[sp],#256        // save_fplr_x  256 (post-indexed load)
        ret     lr                      // end
    ```

- (Bereich 1: Ende)

Im Prolog von Bereich 1 wird der Stapelspeicher im Voraus zugeordnet. Sie sehen, dass in Bereich 2 derselbe Entladungscode vorhanden ist, auch wenn dieser aus der Hostfunktion heraus verschoben wurde.

Bereich 1: `set_fp`, `save_regp 0,240`, `save_fplr_x_256`, `end`, wobei der Startindex des Epilogs wie üblich auf `set_fp` zeigt

Bereich 2: `save_regp 2, 224`, `end_c`, `set_fp`, `save_regp 0,240`, `save_fplr_x_256`, `end` Der Startindex des Epilogs zeigt auf den ersten Entladungscode, `save_regp 2, 224`.

### <a name="large-functions"></a>Große Funktionen

Fragmente lassen sich für die Beschreibung von Funktionen einsetzen, die das 1 MB-Limit übersteigen, das von den Bitfeldern im XDATA-Header vorgegeben wird. Damit eine sehr große Funktion wie diese beschrieben werden kann, muss sie in Fragmente unterteilt werden, die kleiner als 1 MB sind. Jedes Fragment sollte so angepasst werden, dass es Epiloge nicht aufteilt.

Nur das erste Fragment der Funktion enthält einen Prolog. Alle anderen sind als Fragmente ohne Prolog gekennzeichnet. Je nach Anzahl der vorhandenen Epiloge kann jedes Fragment null oder mehr Epiloge enthalten. Bedenken Sie, dass jeder Epilogbereich in einem Fragment dessen Startoffset relativ zum Start des Fragments, nicht zum Start der Funktion festlegt.

Wenn ein Fragment keinen Prolog und Epilog enthält, benötigt es dennoch einen eigenen PDATA-Datensatz und ggf. auch einen XDATA-Datensatz, um zu beschreiben, wie die Entladung im Funktionstext stattfindet.

## <a name="examples"></a>Beispiele

### <a name="example-1-frame-chained-compact-form"></a>Beispiel 1: Frameverkettet, kompaktes Format

```asm
|Foo|     PROC
|$LN19|
    str     x19,[sp,#-0x10]!        // save_reg_x
    sub     sp,sp,#0x810            // alloc_m
    stp     fp,lr,[sp]              // save_fplr
    mov     fp,sp                   // set_fp
                                    //  end of prolog
    ...

|$pdata$Foo|
    DCD     imagerel     |$LN19|
    DCD     0x416101ed
    ;Flags[SingleProEpi] functionLength[492] RegF[0] RegI[1] H[0] frameChainReturn[Chained] frameSize[2080]
```

### <a name="example-2-frame-chained-full-form-with-mirror-prolog--epilog"></a>Beispiel 2: Frameverkettet, vollständiges Format mit gespiegeltem Prolog und Epilog

```asm
|Bar|     PROC
|$LN19|
    stp     x19,x20,[sp,#-0x10]!    // save_regp_x
    stp     fp,lr,[sp,#-0x90]!      // save_fplr_x
    mov     fp,sp                   // set_fp
                                    // end of prolog
    ...
                                    // begin of epilog, a mirror sequence of Prolog
    mov     sp,fp
    ldp     fp,lr,[sp],#0x90
    ldp     x19,x20,[sp],#0x10
    ret     lr

|$pdata$Bar|
    DCD     imagerel     |$LN19|
    DCD     imagerel     |$unwind$cse2|
|$unwind$Bar|
    DCD     0x1040003d
    DCD     0x1000038
    DCD     0xe42291e1
    DCD     0xe42291e1
    ;Code Words[2], Epilog Count[1], E[0], X[0], Function Length[6660]
    ;Epilog Start Index[0], Epilog Start Offset[56]
    ;set_fp
    ;save_fplr_x
    ;save_r19r20_x
    ;end
```

Der Startindex des Epilogs [0] zeigt auf die gleiche Entladungscodesequenz im Prolog.

### <a name="example-3-variadic-unchained-function"></a>Beispiel 3: Nicht verkettete variadische Funktion

```asm
|Delegate| PROC
|$LN4|
    sub     sp,sp,#0x50
    stp     x19,lr,[sp]
    stp     x0,x1,[sp,#0x10]        // save incoming register to home area
    stp     x2,x3,[sp,#0x20]        // ...
    stp     x4,x5,[sp,#0x30]
    stp     x6,x7,[sp,#0x40]        // end of prolog
    ...
    ldp     x19,lr,[sp]             // beginning of epilog
    add     sp,sp,#0x50
    ret     lr

    AREA    |.pdata|, PDATA
|$pdata$Delegate|
    DCD     imagerel |$LN4|
    DCD     imagerel |$unwind$Delegate|

    AREA    |.xdata|, DATA
|$unwind$Delegate|
    DCD     0x18400012
    DCD     0x200000f
    DCD     0xe3e3e3e3
    DCD     0xe40500d6
    DCD     0xe40500d6
    ;Code Words[3], Epilog Count[1], E[0], X[0], Function Length[18]
    ;Epilog Start Index[4], Epilog Start Offset[15]
    ;nop        // nop for saving in home area
    ;nop        // ditto
    ;nop        // ditto
    ;nop        // ditto
    ;save_lrpair
    ;alloc_s
    ;end
```

Der Startindex des Epilogs [4] verweist auf die Mitte des Entladungscodes im Prolog (partielle Wiederverwendung des Entladungsarrays).

## <a name="see-also"></a>Siehe auch

[Übersicht über ARM64-ABI-Konventionen](arm64-windows-abi-conventions.md)<br/>
[ARM-Ausnahmebehandlung](arm-exception-handling.md)
