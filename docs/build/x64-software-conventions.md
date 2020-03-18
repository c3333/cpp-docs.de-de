---
title: Softwarekonventionen bei x64-Systemen
ms.date: 12/17/2018
helpviewer_keywords:
- x64 coding conventions
- Visual C++, x64 calling conventions
ms.assetid: 750f3d97-1706-4840-b2fc-41a007329a08
ms.openlocfilehash: 11d29b6c31ccecfe5b9c51c2f9311213bd4a6732
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2020
ms.locfileid: "79422721"
---
# <a name="x64-software-conventions"></a>Softwarekonventionen bei x64-Systemen

In diesem Abschnitt wird C++ die Methode für die Aufruf Konvention für x64, die 64-Bit-Erweiterung der x86-Architektur, beschrieben.

## <a name="overview-of-x64-calling-conventions"></a>Übersicht über x64-Aufruf Konventionen

Zwei wichtige Unterschiede zwischen x86 und x64 sind die 64-Bit-Adressierungs Funktion und ein flacher Satz von 16 64-Bit-Registern für allgemeine Verwendung. Bei Verwendung des erweiterten Register Satzes verwendet x64 die [__fastcall](../cpp/fastcall.md) Aufruf Konvention und ein RISC-basiertes Modell für die Ausnahmebehandlung. Die `__fastcall` Konvention verwendet Register für die ersten vier Argumente und den Stapel Rahmen, um zusätzliche Argumente zu übergeben. Ausführliche Informationen zur x64-Aufruf Konvention, einschließlich Register Verwendung, Stapel Parameter, Rückgabewerte und Stapel Entwicklung, finden Sie unter [x64-Aufruf Konvention](x64-calling-convention.md).

## <a name="enable-optimization-for-x64"></a>Aktivieren der Optimierung für x64

Mit der folgenden Compileroption können Sie Ihre Anwendung für x64 optimieren:

- [/favor (Für Architektureigenschaften optimieren)](../build/reference/favor-optimize-for-architecture-specifics.md)

## <a name="types-and-storage"></a>Typen und Speicher

In diesem Abschnitt werden die Enumeration und Speicherung von Datentypen für die x64-Architektur beschrieben.

### <a name="scalar-types"></a>Skalare Typen

Obwohl es möglich ist, mit einer beliebigen Ausrichtung auf Daten zuzugreifen, empfiehlt es sich, die Daten auf der natürlichen oder einer mehrfach Grenze auszurichten, um Leistungseinbußen zu vermeiden. Enumerationswerte sind Konstante Integerwerte und werden als 32-Bit-Ganzzahlen behandelt. In der folgenden Tabelle werden die Typdefinition und der empfohlene Speicher für Daten anhand der folgenden Ausrichtungs Werte beschrieben:

- Byte-8 Bits

- Word-16 Bits

- Doubleword-32 Bits

- Quadword-64 Bits

- Octaword-128 Bits

|||||
|-|-|-|-|
|Skalartyp|C-Datentyp|Speichergröße (in Bytes)|Empfohlene Ausrichtung|
|**Int8**|**char**|1|Byte|
|**Uint8**|**unsigned char**|1|Byte|
|**INT16**|**short**|2|Word|
|**UInt16**|**unsigned short**|2|Word|
|**Int32**|**int**, **Long**|4|Doubleword|
|**UInt32**|**Ganzzahl ohne Vorzeichen int, Ganzzahl ohne Vorzeichen Long**|4|Doubleword|
|**Int64**|**__int64**|8|Quadword|
|**UINT64**|**__int64 ohne Vorzeichen**|8|Quadword|
|**FP32 (einfache Genauigkeit)**|**float**|4|Doubleword|
|**FP64 (doppelte Genauigkeit)**|**double**|8|Quadword|
|**Zeichner**|__\*__|8|Quadword|
|**__m64**|**Struktur __m64**|8|Quadword|
|**__m128**|**Struktur __m128**|16|Octaword|

### <a name="aggregates-and-unions"></a>Aggregate und Unions

Andere Typen, z. b. Arrays, Strukturen und Unions, haben strengere Ausrichtungs Anforderungen, die einen konsistenten Aggregat-und Union-Speicher und Datenabruf sicherstellen. Im folgenden sind die Definitionen für Array, Struktur und Union aufgeführt:

- Array

   Enthält eine geordnete Gruppe von angrenzenden Datenobjekten. Jedes-Objekt wird als- *Element*bezeichnet. Alle Elemente in einem Array haben dieselbe Größe und denselben Datentyp.

- Struktur

   Enthält eine geordnete Gruppe von Datenobjekten. Im Gegensatz zu den Elementen eines Arrays können die Datenobjekte in einer Struktur unterschiedliche Datentypen und Größen aufweisen. Jedes Datenobjekt in einer Struktur wird als *Member*bezeichnet.

- Union

   Ein-Objekt, das eine Gruppe von benannten Membern enthält. Die Elemente der benannten Menge können von einem beliebigen Typ sein. Der für eine Union zugeordnete Speicher ist gleich dem für das größte Mitglied dieser Union erforderlichen Speicher plus allen für die Ausrichtung erforderlichen Auffüll Zeichen.

Die folgende Tabelle zeigt die stark vorgeschlagene Ausrichtung für die skalaren Member von Unions und Strukturen.

||||
|-|-|-|
|Skalartyp|C-Datentyp|Erforderliche Ausrichtung|
|**Int8**|**char**|Byte|
|**Uint8**|**unsigned char**|Byte|
|**INT16**|**short**|Word|
|**UInt16**|**unsigned short**|Word|
|**Int32**|**int**, **Long**|Doubleword|
|**UInt32**|**Ganzzahl ohne Vorzeichen int, Ganzzahl ohne Vorzeichen Long**|Doubleword|
|**Int64**|**__int64**|Quadword|
|**UINT64**|**__int64 ohne Vorzeichen**|Quadword|
|**FP32 (einfache Genauigkeit)**|**float**|Doubleword|
|**FP64 (doppelte Genauigkeit)**|**double**|Quadword|
|**Zeichner**|<strong>\*</strong>|Quadword|
|**__m64**|**Struktur __m64**|Quadword|
|**__m128**|**Struktur __m128**|Octaword|

Die folgenden Aggregat Ausrichtungs Regeln gelten:

- Die Ausrichtung eines Arrays entspricht der Ausrichtung eines der Elemente des Arrays.

- Die Ausrichtung des Anfangs einer Struktur oder Union ist die maximale Ausrichtung eines einzelnen Members. Jedes Element in der Struktur oder Union muss in der richtigen Ausrichtung platziert werden, wie in der vorherigen Tabelle definiert. Dies kann abhängig vom vorherigen Member eine implizite interne Auffüll Zeichen erfordern.

- Die Struktur Größe muss ein ganzzahliges Vielfaches der Ausrichtung sein, das möglicherweise nach dem letzten Element Auffüll Zeichen erfordert. Da Strukturen und Unions in Arrays gruppiert werden können, muss jedes Array Element einer Struktur oder Union mit der richtigen Ausrichtung beginnen und enden, die zuvor festgelegt wurde.

- Es ist möglich, Daten so auszurichten, dass Sie größer als die Ausrichtungs Anforderungen sind, solange die vorherigen Regeln beibehalten werden.

- Ein einzelner Compiler kann die Verpackung einer Struktur aus Größen Gründen anpassen. Beispielsweise ermöglicht [/ZP (Strukturmember Alignment)](../build/reference/zp-struct-member-alignment.md) das Anpassen der Verpackung von Strukturen.

### <a name="examples-of-structure-alignment"></a>Beispiele für die Strukturausrichtung

In den folgenden vier Beispielen wird jeweils eine ausgerichtete Struktur oder Union deklariert, und die entsprechenden Abbildungen veranschaulichen das Layout der Struktur oder Union im Speicher. Jede Spalte in einer Abbildung stellt ein Byte des Speichers dar, und die Zahl in der Spalte zeigt die Verschiebung dieses Byte an. Der Name in der zweiten Zeile jeder Abbildung entspricht dem Namen einer Variablen in der Deklaration. Die schattierten Spalten geben den Abstand an, der zum Erreichen der angegebenen Ausrichtung erforderlich ist.

#### <a name="example-1"></a>Beispiel 1

```C
// Total size = 2 bytes, alignment = 2 bytes (word).

_declspec(align(2)) struct {
    short a;      // +0; size = 2 bytes
}
```

![AMD-Konvertierung, Beispiel 1, Struktur Layout](../build/media/vcamd_conv_ex_1_block.png "AMD-Konvertierung, Beispiel 1, Struktur Layout")

#### <a name="example-2"></a>Beispiel 2

```C
// Total size = 24 bytes, alignment = 8 bytes (quadword).

_declspec(align(8)) struct {
    int a;       // +0; size = 4 bytes
    double b;    // +8; size = 8 bytes
    short c;     // +16; size = 2 bytes
}
```

![AMD-Konvertierungs Beispiel 2 Struktur Layout](../build/media/vcamd_conv_ex_2_block.png "AMD-Konvertierungs Beispiel 2 Struktur Layout")

#### <a name="example-3"></a>Beispiel 3

```C
// Total size = 12 bytes, alignment = 4 bytes (doubleword).

_declspec(align(4)) struct {
    char a;       // +0; size = 1 byte
    short b;      // +2; size = 2 bytes
    char c;       // +4; size = 1 byte
    int d;        // +8; size = 4 bytes
}
```

![AMD-Konvertierungs Beispiel 2 Struktur Layout](../build/media/vcamd_conv_ex_3_block.png "AMD-Konvertierungs Beispiel 2 Struktur Layout")

#### <a name="example-4"></a>Beispiel 4

```C
// Total size = 8 bytes, alignment = 8 bytes (quadword).

_declspec(align(8)) union {
    char *p;      // +0; size = 8 bytes
    short s;      // +0; size = 2 bytes
    long l;       // +0; size = 4 bytes
}
```

![AMD-Konvertierung, Beispiel 4 Union layouit](../build/media/vcamd_conv_ex_4_block.png "AMD-Konvertierung, Beispiel 4 Union layouit")

### <a name="bitfields"></a>Bitfelder

Struktur Bitfelder sind auf 64 Bits beschränkt und können den Typ "signed int", "Ganzzahl ohne Vorzeichen int", "Int64" oder "Ganzzahl ohne Vorzeichen Int64" aufweisen. Bitfelder, die die Typgrenze überschreiten, überspringen Bits, um das Bitfeld an der nächsten typausrichtung auszurichten. Ganzzahlige Bitfelder können z. b. nicht einen 32-Bit-BOUNDRY-Wert überschreiten.

### <a name="conflicts-with-the-x86-compiler"></a>Konflikte mit dem x86-Compiler

Datentypen, die größer als 4 Bytes sind, werden nicht automatisch auf dem Stapel ausgerichtet, wenn Sie den x86-Compiler zum Kompilieren einer Anwendung verwenden. Da die Architektur für den x86-Compiler einen 4-Byte-ausgerichteten Stapel ist, kann alles, was größer als 4 Bytes ist (z. b. eine 64-Bit-Ganzzahl), nicht automatisch an eine 8-Byte-Adresse ausgerichtet werden.

Das Arbeiten mit nicht ausgerichteten Daten hat zwei Auswirkungen.

- Der Zugriff auf nicht ausgerichtete Speicherorte dauert möglicherweise länger als für den Zugriff auf ausgerichtete Standorte.

- Nicht ausgerichtete Standorte können nicht in Interlocked-Vorgängen verwendet werden.

Wenn Sie eine strengere Ausrichtung benötigen, verwenden Sie `__declspec(align(N))` für die Variablen Deklarationen. Dies bewirkt, dass der Compiler den Stapel dynamisch entsprechend Ihren Spezifikationen ausgleicht. Das dynamische Anpassen des Stapels zur Laufzeit kann jedoch zu einer langsameren Ausführung Ihrer Anwendung führen.

## <a name="register-usage"></a>Verwendung registrieren

Die x64-Architektur bietet 16 allgemeine Register (im folgenden als ganzzahlige Register bezeichnet) und 16 XMM/ymm-Register, die für die Gleit Komma Verwendung verfügbar sind. Volatile Register sind Scratch-Register, von denen der Aufrufer voraussetzt, dass sie während eines Aufrufs zerstört werden. Nicht volatile Register müssen ihre Werte über einen Funktionsaufruf hinweg bewahren und, sofern sie verwendet werden, vom Aufgerufenen gespeichert werden.

### <a name="register-volatility-and-preservation"></a>Registrieren von Volatilität und Beibehaltung

Die folgende Tabelle beschreibt, wie jedes Register bei Funktionsaufrufen verwendet wird:

||||
|-|-|-|
|Registrieren|Status|Verwendung|
|RAX|Volatil|Rückgabewert-Register|
|RCX|Volatil|Erstes Ganzzahl-Argument|
|RDX|Volatil|Zweites Ganzzahl-Argument|
|R8|Volatil|Drittes Ganzzahl-Argument|
|R9|Volatil|Viertes Ganzzahl-Argument|
|R10:R11|Volatil|Muss je nach Anforderung des Aufrufers bewahrt werden. Wird in syscall-/sysret-Instruktionen verwendet.|
|R12:R15|Nicht volatil|Muss vom Aufgerufenen bewahrt werden|
|RDI|Nicht volatil|Muss vom Aufgerufenen bewahrt werden|
|RSI|Nicht volatil|Muss vom Aufgerufenen bewahrt werden|
|RBX|Nicht volatil|Muss vom Aufgerufenen bewahrt werden|
|RBP|Nicht volatil|Kann als Frame-Pointer verwendet werden; muss vom Aufgerufenen bewahrt werden|
|RSP|Nicht volatil|Stack-Pointer|
|XMM0, YMM0|Volatil|Erstes FP-Argument; erstes Vektortypargument, wenn `__vectorcall` verwendet wird|
|XMM1, YMM1|Volatil|Zweites FP-Argument; zweites Argument vom Typ Vektor, wenn `__vectorcall` verwendet wird|
|XMM2, YMM2|Volatil|Drittes FP-Argument; drittes Argument vom Typ Vektor, wenn `__vectorcall` verwendet wird|
|XMM3, YMM3|Volatil|Viertes FP-Argument; viertes Argument vom Typ Vektor, wenn `__vectorcall` verwendet wird|
|XMM4, YMM4|Volatil|Muss je nach Bedarf vom Aufrufer bewahrt werden; fünftes Argument vom Typ Vektor, wenn `__vectorcall` verwendet wird|
|XMM5, YMM5|Volatil|Muss je nach Bedarf vom Aufrufer bewahrt werden; sechstes Argument vom Typ Vektor, wenn `__vectorcall` verwendet wird|
|XMM6:XMM15, YMM6:YMM15|Nicht volatil (XMM), Volatil (obere Hälfte von YMM)|Muss vom aufgerufenen beibehalten werden. YMM-Register müssen je nach Bedarf vom Aufrufer bewahrt werden.|

Bei einem Funktions-und einem Funktions Eintrag in C-Lauf Zeit Bibliotheks aufrufen und Windows-Systemaufrufen wird erwartet, dass das richtungsflag im CPU-Flags-Register gelöscht wird.

## <a name="stack-usage"></a>Stapel Verwendung

Ausführliche Informationen zu Stapel Zuordnung, Ausrichtung, Funktionstypen und Stapel Rahmen auf x64 finden Sie unter [x64-Stapel Verwendung](stack-usage.md).

## <a name="prolog-and-epilog"></a>Prolog und Epilogcode

Jede Funktion, die Stapel Speicher zuordnet, andere Funktionen aufruft, nicht flüchtige Register speichert oder die Ausnahmebehandlung verwendet, muss über einen Prolog verfügen, dessen Adress Begrenzungen in den Entladedaten, die dem jeweiligen Funktionstabellen Eintrag zugeordnet sind, und Epilogs unter beschrieben werden. jeder Exit-Vorgang zu einer Funktion. Ausführliche Informationen zum erforderlichen Prolog-und Epilogcode auf x64 finden Sie unter [x64 Prolog und Epilogcode](prolog-and-epilog.md).

## <a name="x64-exception-handling"></a>Ausnahmebehandlung bei x64-Systemen

Informationen zu den Konventionen und Datenstrukturen, die verwendet werden, um die strukturierte C++ Ausnahmebehandlung und das Verhalten der Ausnahmebehandlung in x64 zu implementieren, finden Sie unter [x64-Ausnahmebehandlung](exception-handling-x64.md).

## <a name="intrinsics-and-inline-assembly"></a>Intrinsie-und Inlineassembly

Eine der Einschränkungen für den x64-Compiler besteht darin, dass keine Unterstützung für den Inline Assembler vorhanden ist. Dies bedeutet, dass Funktionen, die nicht in C oder C++ geschrieben werden können, entweder als Unterroutinen oder als intrinsische Funktionen geschrieben werden müssen, die vom Compiler unterstützt werden. Bestimmte Funktionen sind Leistungs sensibel, andere hingegen nicht. Leistungs empfindliche Funktionen sollten als intrinsische Funktionen implementiert werden.

Die vom Compiler unterstützten systeminternen Funktionen werden in systeminternen [Compilerfunktionen](../intrinsics/compiler-intrinsics.md)beschrieben.

## <a name="image-format"></a>Bildformat

Das ausführbare x64-Bildformat ist das Format PE32 +. Ausführbare Images (sowohl DLLs als auch exe-Dateien) sind auf eine maximale Größe von 2 Gigabyte beschränkt, sodass eine relative Adressierung mit einer 32-Bit-Verschiebung verwendet werden kann, um statische Bilddaten zu adressieren. Diese Daten umfassen die Import Adress Tabelle, Zeichen folgen Konstanten, statische globale Daten usw.

## <a name="see-also"></a>Siehe auch

[Aufrufkonventionen](../cpp/calling-conventions.md)
