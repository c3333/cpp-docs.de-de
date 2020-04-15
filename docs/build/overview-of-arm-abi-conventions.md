---
title: Übersicht über ARM-ABI-Konventionen
ms.date: 07/11/2018
ms.assetid: 23f4ae8c-3148-4657-8c47-e933a9f387de
ms.openlocfilehash: 8737f7b1cbe0651b43eb3b9990a4035b60bd01b9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320730"
---
# <a name="overview-of-arm32-abi-conventions"></a>Überblick über ARM32 ABI Conventions

Die Binärschnittstelle (ABI, Application Binary Interface) für den für Windows on ARM-Prozessoren kompilierten Code basiert auf der standardmäßigen ARM EABI. Dieser Artikel zeigt die wichtigsten Unterschiede zwischen Windows on ARM und dem Standard. Dieses Dokument behandelt den ARM32 ABI. Informationen zum ARM64 ABI finden Sie unter [Übersicht über ARM64 ABI-Konventionen](arm64-windows-abi-conventions.md). Weitere Informationen zum Standard-ARM-EABI finden Sie unter [Application Binary Interface (ABI) für die ARM-Architektur](http://infocenter.arm.com/help/index.jsp?topic=/com.arm.doc.subset.swdev.abi/index.html) (externer Link).

## <a name="base-requirements"></a>Anforderungen – einfach

Für Windows on ARM wird vorausgesetzt, dass es dauerhaft unter einer ARMv7-Architektur ausgeführt wird. Die Hardware muss eine Gleitkommaunterstützung in Form von VFPv3-D32 oder höher bieten. Das VFP muss in der Hardware sowohl ein Gleitkomma in einfacher als auch doppelter Genauigkeit unterstützen. Die Windows-Laufzeit unterstützt keine Emulation von Gleitkomma, um die Ausführung auf Nicht-VFP-Hardware zu ermöglichen.

Die Hardware muss auch Advanced SIMD Extensions (NEON)-Unterstützung für Ganzzahl- und Gleitkommaoperationen bieten. Es wird keine Laufzeitunterstützung für die Emulation geboten.

Die Unterstützung für die Division von ganzen Zahlen (UDIV/SDIV) wird wärmstens empfohlen, ist jedoch nicht erforderlich. Plattformen, die keine Unterstützung für die Division von ganzen Zahlen bieten, weisen womöglich Leistungseinbußen auf, da diese Operationen aufgefangen und unter Umständen gepatcht werden müssen.

## <a name="endianness"></a>Endianwert

Windows on ARM wird im Little-Endian-Modus ausgeführt. Sowohl der MSVC-Compiler als auch die Windows-Laufzeit erwarten jederzeit little-endian-Daten. Auch wenn die SETEND-Instruktion in der ARM-Instruktionssatz-Architektur (ISA) es sogar dem Benutzermodus-Code ermöglicht, die aktuelle Endianness zu ändern, wird davon dringend abgeraten, da es für eine Anwendung gefährlich sein kann. Wenn im Big-Endian-Modus eine Ausnahme generiert wird, ist das Verhalten unvorhersehbar und kann zu einem Anwendungsfehler im Benutzermodus oder zu einer Fehlerprüfung im Kernel-Modus führen.

## <a name="alignment"></a>Ausrichtung

Auch wenn Windows es der ARM-Hardware ermöglicht, falsch ausgerichtete Ganzzahlzugriffe transparent zu verarbeiten, können in einigen Situationen weiterhin Ausrichtungsfehler generiert werden. Befolgen Sie diese Regeln bei der Ausrichtung:

- Lade- und -Speichervorgänge von Ganzzahlen halber Wortgröße (16-Bit) und ganzer Wortgröße (32-Bit) müssen nicht ausgerichtet werden. Die Hardware verarbeitet sie effizient und transparent.

- Lade- und Speichervorgänge von Gleitkommazahlen sollten ausgerichtet werden. Der Kernel verarbeitet nicht ausgerichtete Lade- und Speichervorgänge transparent, aber mit einem maßgeblichen Mehraufwand.

- Doppelte (LDRD/STRD) und mehrfache Lade- und Speichervorgänge (LDM/STM) sollten ausgerichtet werden. Der Kernel verarbeitet die meisten transparent, aber mit einem maßgeblichen Mehraufwand.

- Alle nicht zwischengespeicherten Arbeitsspeicherzugriffe müssen ausgerichtet werden, auch für Ganzzahlzugriffe. Nicht ausgerichtete Zugriffe verursachen einen Ausrichtungsfehler.

## <a name="instruction-set"></a>Instruktionssatz

Der Instruktionssatz für Windows on ARM ist streng auf Thumb-2 beschränkt. Der gesamte Code, der auf dieser Plattform ausgeführt wird, soll erwartungsgemäß im Thumb-Modus starten und dauerhaft dort verweilen. Ein Versuch, zum alten ARM-Instruktionssatz zu wechseln, kann erfolgreich sein. In einem solchen Fall können jedoch alle etwaigen Ausnahmen oder Interrupts zu einem Anwendungsfehler im Benutzermodus oder zu einer Fehlerprüfung im Kernel-Modus führen.

Eine Nebenwirkung dieser Anforderung ist, dass für alle Codezeiger das niedrigwertigste Bit festgelegt sein muss. Auf diese Weise bleibt der Prozessor im Thumb-Modus und versucht nicht, den Zielcode als 32-Bit-ARM-Instruktionen ausführen, wenn die Codezeiger über BLX oder BX geladen und als Branchziel verwendet werden.

### <a name="it-instructions"></a>IT-Instruktionen

Der Einsatz von IT-Instruktionen in Thumb-2-Code ist mit Ausnahme der folgenden spezifischen Fälle nicht zulässig:

- Die IT-Instruktion kann nur zum Ändern einer Zielinstruktion verwendet werden.

- Bei der Zielinstruktion muss es sich um eine 16-Bit-Instruktion handeln.

- Die Zielinstruktion muss eine der folgenden sein:

   |16-Bit-OpCodes|Klasse|Beschränkungen|
   |---------------------|-----------|------------------|
   |MOV, MVN|Move|Rm != PC, Rd != PC|
   |LDR, LDR[S]B, LDR[S]H|Aus Arbeitsspeicher laden|Jedoch keine LDR-Literalformen|
   |STR, STRB, STRH|Im Arbeitsspeicher speichern||
   |ADD, ADC, RSB, SBC, SUB|Addieren oder subtrahieren|Jedoch nicht ADD/SUB SP, SP, imm7-Formen<br /><br /> Rm != PC, Rdn != PC, Rdm != PC|
   |CMP, CMN|Vergleichen|Rm != PC, Rn != PC|
   |MUL|Multiplizieren||
   |ASR, LSL, LSR, ROR|Bit-Verschiebung||
   |AND, BIC, EOR, ORR, TST|Bitweise arithmetisch||
   |BX|Verzweigung zum Register|Rm != PC|

Auch wenn aktuelle ARMv7-CPUs nicht den Einsatz von unzulässigen Instruktionsformen melden können, wird dies von zukünftigen Generationen erwartet. Wenn diese Formen erkannt werden, wird jedes Programm, das sie verwendet, unter Umständen mit einer nicht definierten Instruktionsausnahme beendet.

### <a name="sdivudiv-instructions"></a>SDIV/UDIV-Anweisungen

Die Nutzung von Divisionsinstruktionen für Ganzzahlen SDIV und UDIV wird vollständig unterstützt, sogar auf Plattformen ohne native Hardware zur Verarbeitung. Der Mehraufwand pro SDIV- oder UDIV-Division auf einem Cortex-A9-Prozessor beträgt etwa 80 Zyklen, hinzu kommt die Gesamtzeit für die Division von 20-250 Zyklen, je nach Eingaben.

## <a name="integer-registers"></a>Ganzzahl-Register

Der ARM-Prozessor unterstützt 16 Ganzzahlregister:

|Register|Volatil?|Role|
|--------------|---------------|----------|
|r0|Flüchtig|Parameter, Ergebnis, Scratch-Register 1|
|r1|Flüchtig|Parameter, Ergebnis, Scratch-Register 2|
|r2|Flüchtig|Parameter, Scratch-Register 3|
|r3|Flüchtig|Parameter, Scratch-Register 4|
|r4|Nicht volatil||
|r5|Nicht volatil||
|r6|Nicht volatil||
|r7|Nicht volatil||
|r8|Nicht volatil||
|r9|Nicht volatil||
|r10|Nicht volatil||
|r11|Nicht volatil|Frame-Pointer|
|r12|Flüchtig|Intra-Procedure-Call / Scratch-Register|
|r13 (SP)|Nicht volatil|Stack-Pointer|
|r14 (LR)|Nicht volatil|Link-Register|
|r15 (PC)|Nicht volatil|Program-Counter|

Details für die Nutzung des Parameters und der Rückgabewerteregister finden Sie im Abschnitt "Parameterübergabe" in diesem Artikel.

Windows verwendet r11 für einen schnellen Walk durch den Stack-Frame. Weitere Informationen finden Sie im Abschnitt "Stackwalk". Aufgrund dieser Anforderung muss r11 jederzeit auf den obersten Link in der Kette verweisen. Verwenden Sie r11 nicht zu allgemeinen Zwecken; Ihr Code generiert keine Stackwalks während der Analyse.

## <a name="vfp-registers"></a>VFP-Register

Windows unterstützt nur ARM-Varianten mit Unterstützung für VFPv3-D32-Coprozessoren. Das bedeutet, dass Gleitkommaregister immer vorhanden sind und für die Parameterübergabe genutzt werden können und dass der vollständige Satz aus 32 Registern zur Verfügung steht. Die VFP-Register und deren Einsatz werden in dieser Tabelle zusammengefasst:

|Einfach|Doppelt|Vierfach|Volatil?|Role|
|-------------|-------------|-----------|---------------|----------|
|s0-s3|d0-d1|q0|Flüchtig|Parameter, Ergebnis, Scratch-Register|
|s4-s7|d2-d3|q1|Flüchtig|Parameter, Scratch-Register|
|s8-s11|d4-d5|q2|Flüchtig|Parameter, Scratch-Register|
|s12-s15|d6-d7|q3|Flüchtig|Parameter, Scratch-Register|
|s16-s19|d8-d9|q4|Nicht volatil||
|s20-s23|d10-d11|q5|Nicht volatil||
|s24-s27|d12-d13|q6|Nicht volatil||
|s28-s31|d14-d15|q7|Nicht volatil||
||d16-d31|q8-q15|Flüchtig||

Die nächste Tabelle zeigt die Gleitkommastatus- und Steuerungsregister (FPSCR)-Bitfelder:

|Bits|Bedeutung|Volatil?|Role|
|----------|-------------|---------------|----------|
|31-28|NZCV|Flüchtig|Status-Flags|
|27|QC|Flüchtig|Kumulative Sättigung|
|26|AHP|Nicht volatil|Alternative-Half-Precision-Steuerung|
|25|DN|Nicht volatil|Standardmäßige NaN-Modussteuerung|
|24|FZ|Nicht volatil|Flush-to-Zero-Modussteuerung|
|23-22|RMode|Nicht volatil|Rounding-Modussteuerung|
|21-20|Stride|Nicht volatil|Vektorsprung, muss immer 0 sein|
|18-16|Len|Nicht volatil|Vektorlänge, muss immer 0 sein|
|15, 12-8|IDE, IXE usw.|Nicht volatil|Ausnahme-Trap-Aktivierungsbits, muss immer 0 sein|
|7, 4-0|IDC, IXC usw.|Flüchtig|Kumulative Ausnahme-Flags|

## <a name="floating-point-exceptions"></a>Gleitkommaausnahmen

Der Großteil an ARM-Hardware unterstützt keine IEEE-Gleitkommaausnahmen. Bei Prozessorvarianten mit Hardware-Gleitkommaausnahmen fängt der Windows-Kernel stumm die Ausnahmen ab und deaktiviert sie implizit im FPSCR-Register. Dadurch wird ein normalisiertes Verhalten zwischen Prozessorvarianten sichergestellt. Anderenfalls könnte Code, der auf einer Plattform entwickelt wurde, die keine Ausnahmenunterstützung bietet, unerwartete Ausnahmen erhalten, wenn er auf einer Plattform mit Ausnahmenunterstützung ausgeführt wird.

## <a name="parameter-passing"></a>Parameterübergabe

Bei nicht variadic-Funktionen folgt die Windows on ARM-ABI den ARM-Regeln für die Parameterübergabe, dazu gehören die VFP- und Advanced SIMD-Erweiterungen. Diese Regeln folgen dem [Prozeduraufrufstandard für die ARM-Architektur](http://infocenter.arm.com/help/topic/com.arm.doc.ihi0042c/IHI0042C_aapcs.pdf), die mit den VFP-Erweiterungen konsolidiert wird. Standardmäßig werden die ersten vier Ganzzahlargumente und bis zu acht Gleitkomma- oder Vektor-Argumente an Register übergeben, und zusätzliche Argumente werden an den Stack übergeben. Argumente werden Registern oder dem Stack mithilfe der folgenden Prozedur zugewiesen:

### <a name="stage-a-initialization"></a>Stufe A: Initialisierung

Die Initialisierung wird genau einmal durchgeführt, bevor die Argumentsverarbeitung beginnt:

1. Die Next Core Register Number (NCRN) wird auf r0 gesetzt.

1. Die VFP-Register werden als nicht zugewiesen markiert.

1. Die Next Stacked Argument Address (NSAA) wird auf die aktuelle SP gesetzt.

1. Wenn eine Funktion aufgerufen wird, die ein Ergebnis im Speicher zurückgibt, wird die Adresse für das Ergebnis in r0 platziert und die NCRN wird auf r1 gesetzt.

### <a name="stage-b-pre-padding-and-extension-of-arguments"></a>Stufe B: Vorpolsterung und Erweiterung von Argumenten

Auf jedes Argument in der Liste wird die erste übereinstimmende Regel aus der folgenden Liste angewendet:

1. Wenn das Argument ein zusammengesetzter Typ ist, dessen Größe nicht statisch vom Aufrufer und dem Aufgerufenen bestimmt werden kann, wird das Argument in den Arbeitsspeicher kopiert und durch einen Verweis auf die Kopie ersetzt.

1. Wenn das Argument ein Byte oder 16-Bit-Halbwort ist, wird es durch eine Null oder ein Symbol auf ein 32-Bit-Vollwort erweitert und als ein 4-Byte-Argument behandelt.

1. Wenn das Argument ein zusammengesetzter Typ ist, wird die Größe auf das nächste Vielfache von 4 aufgerundet.

### <a name="stage-c-assignment-of-arguments-to-registers-and-stack"></a>Stufe C: Zuordnung von Argumenten zu Registern und Stapeln

Auf jedes Argument in der Liste werden die folgenden Regeln abwechselnd angewendet, bis das Argument zugeordnet wurde:

1. Wenn das Argument ein VFP-Typ ist und es ausreichend aufeinander folgende nicht zugewiesene VFP-Register vom entsprechenden Typ gibt, wird das Argument zur Registerreihe mit der niedrigsten Nummer zugeordnet.

1. Wenn das Argument ein VFP-Typ ist, werden alle verbleibenden nicht zugewiesenen Register als nicht verfügbar markiert. Die NSAA wird nach oben angepasst, bis sie ordnungsgemäß für den Argumententyp ausgerichtet ist und das Argument in den Stack an der angepassten NSAA kopiert wird. Die NSAA wird dann um die Größe des Arguments inkrementiert.

1. Wenn das Argument eine 8-Byte-Ausrichtung benötigt, wird die NCRN auf die nächste gerade Registernummer aufgerundet.

1. Wenn die Größe des Arguments in 32-Bit-Wörtern nicht mehr als r4 minus NCRN ist, wird das Argument in Core-Register kopiert, beginnend bei der NCRN, wobei die am niedrigstwertigen Bits die niedrig nummerierten Register belegen. Die NCRN wird um die Anzahl der verwendeten Register inkrementiert.

1. Wenn die NCRN kleiner als r4 ist und die NSAA mit der SP übereinstimmt, wird das Argument in Core-Register und den Stack unterteilt. Der erste Teil des Arguments wird in die Core-Register kopiert, beginnend bei der NCRN bis hin zu einschließlich r3. Der Rest des Arguments wird in den Stack kopiert, beginnend bei der NSAA. Die NCRN wird auf r4 gesetzt, und die NSAA wird um die Größe des Arguments minus der an die Register übergegebene Anzahl inkrementiert.

1. Wenn das Argument eine 8-Byte-Ausrichtung benötigt, wird die NSAA auf die nächste 8-Byte-ausgerichtete Adresse aufgerundet.

1. Das Argument wird an der NSAA in den Arbeitsspeicher kopiert. Die NSAA wird um die Größe des Arguments inkrementiert.

Die VFP-Register werden nicht für variadic-Funktionen verwendet, und die Regeln 1 und 2 aus Stufe C werden ignoriert. Das bedeutet, dass eine variadic-Funktion mit einem optionalen Push {r0-r3} beginnen kann, um die Registerargumente vor zusätzliche vom Aufrufer übergegebene Argumente voranzustellen und um dann direkt vom Stack aus auf die gesamte Argumentenliste zuzugreifen.

Werte vom Typ Ganzzahl werden in r0 zurückgegeben, was optional auf r1 für 64-Bit-Rückgabewerte erweitert werden kann. Werte vom Typ VFP/NEON-Gleitkomma oder SIMD werden wie vorgegeben an s0, d0 oder q0 zurückgegeben.

## <a name="stack"></a>Stapel

Der Stack muss dauerhaft 4-Byte-ausgerichtet bleiben und an jeder Funktionsgrenze 8-Byte-ausgerichtet sein. Dies ist erforderlich, um die häufige Nutzung von interlocked-Operationen für 64-Bit-Stack-Variablen zu unterstützen. Die ARM EABI besagt, dass der Stack an jeder öffentlichen Schnittstelle 8-Byte-ausgerichtet ist. Aus Konsistenzgründen interpretiert die Windows on ARM ABI jede Funktionsgrenze als öffentliche Schnittstelle.

Funktionen, die einen Frame-Pointer verwenden müssen, z. B. Funktionen, die `alloca` aufrufen oder die den Stack-Pointer dynamisch ändern, müssen den Frame-Pointer in r11 im Funktionsprolog einrichten und bis zum Epilog unverändert lassen. Funktionen, die keinen Frame-Pointer erfordern, müssen alle Stack-Updates im Prolog durchführen und dann den Stack-Pointer bis zum Epilog unverändert lassen.

Funktionen, die 4 KB oder mehr im Stack zuweisen, müssen sicherstellen, dass jede Seite vor der letzten Seite in der richtigen Reihenfolge verwendet wird. Dadurch wird sichergestellt, dass kein Code die Schutzseiten "überspringen" kann, die Windows zum Erweitern des Stacks verwendet. Dies wird in der Regel mithilfe des Hilfsprogramms `__chkstk` erzielt, dem die Stack-Gesamtzuordnung in Bytes geteilt durch 4 an r4 übergeben wird und das die letzte Stackzuordnungsanzahl in Bytes wieder an r4 zurückgibt.

### <a name="red-zone"></a>Rote Zone

Dieser 8-Byte-Bereich direkt unter dem aktuellen Stack-Pointer ist für die Analyse und das dynamische Patching reserviert. Dadurch kann sorgfältig generierter Code eingefügt werden, in dem 2 Register bei [sp, #-8] gespeichert werden und der sie vorübergehend für beliebige Zwecke verwendet. Der Windows-Kernel stellt sicher, dass diese 8 Bytes nicht überschrieben werden, wenn eine Ausnahme oder ein Interrupt im Benutzermodus und im Kernel-Modus auftritt.

### <a name="kernel-stack"></a>Kernel-Stack

Der standardmäßige Stack im Kernel-Modus unter Windows besteht aus drei Seiten (12 KB). Achten Sie darauf, keine Funktionen zu erstellen, die über große Stack-Puffer im Kernel-Modus verfügen. Ein Interrupt kann mit sehr kleinem Stack-Spielraum auftreten und eine Panik-Stack-Fehlerprüfung verursachen.

## <a name="cc-specifics"></a>C/C++-Spezifikationen

Enumerationen sind 32-Bit-Ganzzahl-Typen, es sei denn mindestens ein Wert in der Enumeration erfordert einen 64-Bit-Doppelwort-Speicher. In diesem Fall wird die Enumeration auf einen 64-Bit-Ganzzahl-Typ heraufgestuft.

`wchar_t`wird als äquivalent `unsigned short`zu definiert, um die Kompatibilität mit anderen Plattformen zu erhalten.

## <a name="stack-walking"></a>Stack Walking

Windows-Code wird mit aktivierten Frame-Zeigern ([/Oy (Frame-Pointer-Omission)](reference/oy-frame-pointer-omission.md)) kompiliert, um schnelles Stack-Walking zu ermöglichen. Im Allgemeinen verweist das r11-Register auf den nächsten Link in der Kette, bei dem es sich um ein {r11, lr}-Paar handelt, das den Pointer zum vorherigen Frame im Stack und die Rückgabeadresse spezifiziert. Für eine verbesserte Profilerstellung und Ablaufverfolgung empfehlen wir, dass Ihr Code auch Frame-Pointer aktiviert.

## <a name="exception-unwinding"></a>Ausnahmeabwickeln

Die Stackentladung während der Ausnahmebehandlung wird durch den Einsatz von Entladecodes aktiviert. Bei den Entladecodes handelt es sich um Bytesequenzen, die im Abschnitt .xdata des ausführbaren Bildes gespeichert sind. Sie beschreiben die Funktionsweise des Funktionsprologs und des Epilogcodes auf abstrakte Weise, so dass die Effekte des Prologs einer Funktion rückgängig gemacht werden können, um das Abwickeln zum Stapelrahmen des Aufrufers vorzubereiten.

Die ARM EABI gibt ein Ausnahmeentladungsmodell an, das Entladecodes verwendet. Diese Spezifikation ist jedoch nicht ausreichend zum Entladen unter Windows, wobei Fälle behandelt werden müssen, in denen der Prozessor sich in der Mitte des Prologs oder Epilogs einer Funktion befindet. Weitere Informationen zu Windows auf ARM-Ausnahmedaten und Zum Entladen finden Sie unter [ARM Exception Handling](arm-exception-handling.md).

Wir empfehlen, dass dynamisch generierter Code mithilfe von dynamischen Funktionstabellen beschrieben wird, die in Aufrufen von `RtlAddFunctionTable` und zugewiesenen Funktionen angegeben sind, damit der generierte Code sich an der Ausnahmebehandlung beteiligen kann.

## <a name="cycle-counter"></a>Zykluszähler

ARM-Prozessoren mit Windows müssen einen Zyklus-Counter unterstützen. Der direkte Einsatz des Counters kann jedoch Probleme verursachen. Um diese Probleme zu vermeiden, verwendet Windows on ARM einen nicht definierten OpCode, um einen normalisierten 64-Bit-Zyklus-Counter-Wert anzufordern. Verwenden Sie aus C oder C++ den intrinsischen `__rdpmccntr64`, um den entsprechenden OpCode auszugeben; verwenden Sie aus der Assembly die `__rdpmccntr64`-Instruktion. Das Lesen des Zyklus-Counters dauert etwa 60 Zyklen auf einem Cortex-A9.

Der Counter ist ein wahrer Zyklus-Counter und keine Uhr, daher variiert die Zählerfrequenz mit der Prozessorfrequenz. Wenn Sie die verstrichene Uhrzeit messen möchten, verwenden Sie `QueryPerformanceCounter`.

## <a name="see-also"></a>Siehe auch

[Häufig auftretende ARM-Migrationsprobleme bei Visual C++](common-visual-cpp-arm-migration-issues.md)<br/>
[ARM-Ausnahmebehandlung](arm-exception-handling.md)
