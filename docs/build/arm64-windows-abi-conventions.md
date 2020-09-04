---
title: Übersicht über ARM64-ABI-Konventionen
ms.date: 03/27/2019
ms.openlocfilehash: bfe55513ffd24175dbe62efc6d5afcfd82f71e4c
ms.sourcegitcommit: 7f378314c5692d897ead10b7f6c96d4cb2abd266
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88972672"
---
# <a name="overview-of-arm64-abi-conventions"></a>Übersicht über ARM64-ABI-Konventionen

Die grundlegende ABI (Application Binary Interface, Binärschnittstelle) für Windows folgt beim Kompilieren und Ausführen auf ARM-Prozessoren im 64-Bit-Modus (ARMv8 oder höhere Architekturen) größtenteils der AArch64-Standard-ARM-EABI. In diesem Artikel werden einige der in der EABI dokumentierten Hauptannahmen und Änderungen erläutert. Weitere Informationen zur 32-Bit-ABI finden Sie unter [Übersicht über ARM32-ABI-Konventionen](overview-of-arm-abi-conventions.md). Weitere Informationen zur Standard-ARM-EABI finden Sie unter [Application Binary Interface (ABI) für die ARM-Architektur](http://infocenter.arm.com/help/index.jsp?topic=/com.arm.doc.subset.swdev.abi/index.html) (externer Link).

## <a name="definitions"></a>Definitionen

Bei der Einführung der 64-Bit-Unterstützung wurden von ARM verschiedene Begriffe definiert:

- **AArch32**: Hierbei handelt es sich um die alte von ARM definierte 32-Bit-Anweisungsset-Architektur (Instruction Set Architecture, ISA), einschließlich der Ausführung im Thumb-Modus.
- **AArch64**: Hierbei handelt es sich um die neue von ARM definierte 64-Bit-Anweisungsset-Architektur (Instruction Set Architecture, ISA).
- **ARMv7**: Hierbei handelt es sich um die Spezifikation der ARM-Hardware der „7. Generation“, zu der nur Unterstützung für AArch32 gehört. Diese ARM-Hardwareversion ist die erste Version, die Windows für ARM unterstützt hat.
- **ARMv8**: Hierbei handelt es sich um die Spezifikation der ARM-Hardware der „8. Generation“, zu der Unterstützung für AArch32 und AArch64 gehört.

Windows verwendet auch die folgenden Begriffe:

- **ARM**: Dieser Begriff bezieht sich auf die 32-Bit-ARM-Architektur (AArch32), die manchmal auch als WoA (Windows on ARM) bezeichnet wird.
- **ARM32**: Dieser Begriff ist identisch zu ARM (siehe oben). In diesem Dokument wird er der Deutlichkeit halber verwendet.
- **ARM64**: Dieser Begriff bezieht sich auf die 64-Bit-ARM-Architektur (AArch64). Begriffe wie „WoA64“ werden nicht verwendet.

Schließlich wird bei Bezugnahme auf Datentypen auf die folgenden Definitionen von ARM verwiesen:

- **Short-Vector**: Hierbei handelt es sich um einen Datentyp, der direkt in SIMD dargestellt werden kann, ein Vektor mit 8 Byte oder 16 Byte an Elementen. Je nach Größe, 8 oder 16 Byte, wird angepasst, wo die einzelnen Elemente 1, 2, 4 oder 8 Byte aufweisen können.
- **HFA (Homogeneous Floating-Point Aggregate, homogenes Gleitkommaaggregat)** : Hierbei handelt es sich um einen Datentyp mit zwei bis vier identischen Gleitkommamembern, entweder Gleitkommazahlen oder Werte mit doppelter Genauigkeit.
- **HVA (Homogeneous Short-Vector Aggregate, Homogenes Short-Vector-Aggregat)** : Hierbei handelt es sich um einen Datentyp mit zwei bis vier identischen Short-Vector-Membern.

## <a name="base-requirements"></a>Basisanforderungen

Die ARM64-Version von Windows hat als Voraussetzung, dass sie immer unter einer ARMv8-Architektur oder einer höheren Version ausgeführt wird. Sowohl die Gleitkomma- als auch die NEON-Unterstützung müssen als Voraussetzung in der Hardware gegeben sein.

Die ARMv8-Spezifikation beschreibt neue optionale Kryptografie- und CRC-Hilfsprogramm-Opcodes sowohl für AArch32 als auch für AArch64. Die Unterstützung dafür ist aktuell optional, wird jedoch empfohlen. Damit diese Opcodes genutzt werden können, sollten Apps zunächst Runtimeüberprüfungen durchführen, ob sie überhaupt vorhanden sind.

## <a name="endianness"></a>Endianness

Wie bei der ARM32-Version von Windows wird Windows bei ARM64 im Little-Endian-Modus ausgeführt. Den Endian-Modus zu ändern ist schwierig, wenn keine Unterstützung für den Kernel-Modus in AArch64 vorhanden ist. Die Änderung zu erzwingen ist also einfacher.

## <a name="alignment"></a>Ausrichtung

Wenn Windows mit ARM64 ausgeführt wird, kann die CPU-Hardware falsch ausgerichteten Zugriff transparent verarbeiten. Dank einer auf AArch32 basierenden Verbesserung funktioniert diese Unterstützung nun auch für alle Integerzugriffe (einschließlich Mehrwortzugriffe) und für Gleitkommazugriffe.

Der Zugriff auf nicht zwischengespeicherten (Geräte)-Arbeitsspeicher muss jedoch weiterhin ausgerichtet werden. Wenn Code falsch ausgerichtete Daten aus nicht zwischengespeichertem Arbeitsspeicher lesen oder schreiben kann, muss sichergestellt sein, dass alle Zugriffe ausgerichtet werden.

Standardlayoutausrichtung für lokale Variablen:

| Größe in Byte | Ausrichtung in Byte |
| - | - |
| 1 | 1 |
| 2 | 2 |
| 3, 4 | 4 |
| > 4 | 8 |

Standardlayoutausrichtung für globale und statische Variablen:

| Größe in Byte | Ausrichtung in Byte |
| - | - |
| 1 | 1 |
| 2–7 | 4 |
| 8–63 | 8 |
| >= 64 | 16 |

## <a name="integer-registers"></a>Ganzzahlregister

Die AArch64-Architektur unterstützt 32 Integerregister:

| Register | Volatil? | Rolle |
| - | - | - |
| x0 | Volatil | Parameter-/Scratch-Register 1, Ergebnisregister |
| x1-x7 | Volatil | Parameter-/Scratch-Register 2–8 |
| x8-x15 | Volatil | Scratch-Register |
| x16–x17 | Volatil | Intra-Procedure-Call-Scratch-Register |
| x18 | Nicht volatil | Plattformregister: im Kernel-Modus, verweist auf KPCR für den aktuellen Prozessor, verweist im Benutzermodus auf TEB |
| x19–x28 | Nicht volatil | Scratch-Register |
| x29/fp | Nicht volatil | Frame-Pointer |
| x30/lr | Nicht volatil | Verknüpfungsregister |

Auf jeden Register kann als vollständiger 64-Bit-Wert (über x0–x30) oder als 32-Bit-Wert (über w0–w30) zugegriffen werden. 32-Bit-Vorgänge führen eine Vorzeichenerweiterung um 0 für ihr Ergebnis auf 64 Bit durch.

Im Abschnitt zur Übergabe von Parametern finden Sie weitere Informationen zur Verwendung von Parameterregistern.

Im Gegensatz zu AArch32 handelt es sich beim Programmzähler (PC) und beim Stapelzeiger (SP) nicht um indizierte Register. Es gelten Einschränkungen, wie auf sie zugegriffen werden kann. Beachten Sie außerdem, dass es kein x31-Register gibt. Diese Codierung wird für spezielle Zwecke verwendet.

Der Spapelzeiger (x29) ist für die Kompatibilität mit schnellem Stackwalk erforderlich, das von ETW und anderen Diensten verwendet wird. Er muss auf das vorherige Paar {x29, x30} auf dem Stapel zeigen.

## <a name="floating-pointsimd-registers"></a>Gleitkomma-/SIMD-Register

Die AArch64-Architektur unterstützt auch 32 Gleitkomma-/SIMD-Register, die unten zusammengefasst sind:

| Register | Volatil? | Rolle |
| - | - | - |
| v0 | Volatil | Parameter-/Scratch-Register 1, Ergebnisregister |
| v1–v7 | Volatil | Parameter-/Scratch-Register 2–8 |
| v8–v15 | Nicht volatil | Scratch-Register (nur die unteren 64 Bit sind nicht flüchtig) |
| v16–v31 | Volatil | Scratch-Register |

Auf jeden Register kann als vollständiger 128-Bit-Wert (über v0–v31 oder q0–q31) zugegriffen werden. Der Zugriff als 64-Bit-Wert (über d0–d31), als 32-Bit-Wert (über s0–s31), als 16-Bit-Wert (über h0–h31) oder als 8-Bit-Wert (über b0–b31) ist möglich. Zugriffe, die kleiner als 128 Bit sind, greifen nur auf die unteren Bit des vollständigen 128-Bit-Registers zu. Die verbleibenden Bit werden nicht tangiert, sofern dies nicht anders angegeben wurde. (AArch64 unterscheidet sich von AArch32, wo kleinere Register auf größere Register gepackt wurden).

Das Floating Point Control Register (FPCR) hat verschiedene Anforderungen für die unterschiedlichen darin enthaltenen Bitfelder:

| Bits | Bedeutung | Volatil? | Rolle |
| - | - | - | - |
| 26 | AHP | Nicht flüchtig | Alternative Steuerung mit halber Genauigkeit |
| 25 | DN | Nicht flüchtig | Standardmäßige NaN-Modussteuerung |
| 24 | FZ | Nicht volatil | Flush-to-Zero-Modussteuerung |
| 23-22 | RMode | Nicht volatil | Steuerung des Rundungsmodus |
| 15,12–8 | IDE, IXE usw. | Nicht flüchtig | Ausnahme-Trap-Aktivierungsbit, muss immer 0 sein. |

## <a name="system-registers"></a>Systemregister

Wie AArch32 stehen bei der AArch64-Spezifikation drei vom System gesteuerte „Thread-ID“-Register zur Verfügung:

| Register | Rolle |
| - | - |
| TPIDR_EL0 | Reserviert. |
| TPIDRRO_EL0 | Enthält die CPU-Zahl des aktuellen Prozessors. |
| TPIDR_EL1 | Verweist auf die KPCR-Struktur für den aktuellen Prozessor. |

## <a name="floating-point-exceptions"></a>Gleitkommaausnahmen

Die Unterstützung für IEEE-Gleitkommaausnahmen ist für AArch64-Systeme optional. Bei Prozessorvarianten mit Hardware-Gleitkommaausnahmen fängt der Windows-Kernel stumm die Ausnahmen ab und deaktiviert sie implizit im FPSCR-Register. Dadurch wird ein normalisiertes Verhalten zwischen Prozessorvarianten sichergestellt. Andernfalls könnte Code, der auf einer Plattform ohne Ausnahmeunterstützung entwickelt wurde, unerwartete Ausnahmen akzeptieren, wenn er auf einer Plattform mit Unterstützung ausgeführt wird.

## <a name="parameter-passing"></a>Parameterübergabe

Bei nicht-variadischen Funktionen folgt die Windows-ABI den Regeln, die von ARM für die Parameterübergabe angegeben wurden. Diese Regeln werden direkt dem Standard für Prozeduraufrufe für die AArch64-Architektur entnommen:

### <a name="stage-a--initialization"></a>Stufe A – Initialisierung

Diese Stufe wird genau einmal ausgeführt, bevor die Verarbeitung der Argumente beginnt.

1. Die nächste Registerzahl mit allgemeinem Zweck (Next General-Purpose Register Number, NGRN) wird auf null festgelegt.

1. Die nächste SIMD- und Gleitkommaregisterzahl (Next SIMD and Floating-point Register Number, NSRN) wird auf null festgelegt.

1. Die nächste gestapelte Argumentadresse (Next Stacked Argument Address, NSAA) wird auf den aktuellen SP-Wert festgelegt.

### <a name="stage-b--pre-padding-and-extension-of-arguments"></a>Stufe B – Vorab-Auffüllung und Erweiterung von Argumenten

Auf jedes Argument in der Liste wird die erste übereinstimmende Regel aus der folgenden Liste angewendet. Wenn keine Regel übereinstimmt, wird das Argument unverändert übernommen.

1. Wenn das Argument ein zusammengesetzter Typ ist, dessen Größe nicht statisch vom Aufrufer und dem Aufgerufenen bestimmt werden kann, wird das Argument in den Arbeitsspeicher kopiert und durch einen Verweis auf die Kopie ersetzt. (In C/C++ gibt es solche Typen nicht, sie existieren jedoch in anderen Sprachen oder Spracherweiterungen.)

1. Wenn der Argumenttyp HFA oder HVA ist, wird das Argument unverändert verwendet.

1. Wenn es sich beim Argumenttyp um einen zusammengesetzten Typ handelt, der größer als 16 Byte ist, wird das Argument in dem vom Aufrufer zugeordneten Arbeitsspeicher kopiert, und das Argument wird durch einen Zeiger auf die Kopie ersetzt.

1. Wenn es sich beim Argumenttyp um einen zusammengesetzten Typ handelt, wird die Größe des Arguments auf das nächste Vielfache von 8 Byte aufgerundet.

### <a name="stage-c--assignment-of-arguments-to-registers-and-stack"></a>Stufe C – Zuweisung von Argumenten zu Registern und zum Stapel

Auf jedes Argument in der Liste werden die folgenden Regeln abwechselnd angewendet, bis das Argument zugeordnet wurde. Wenn ein Argument einem Register zugewiesen wird, weisen alle nicht verwendeten Bit im Register einen nicht angegebenen Wert auf. Wenn ein Argument einem Stapelplatz zugewiesen wird, weisen alle nicht verwendeten Byte für die Vorab-Auffüllung einen nicht angegebenen Wert auf.

1. Wenn es sich beim Argument um einen Gleitkommawert mit halber, einfacher, doppelter oder vierfacher Genauigkeit oder einen Short-Vector-Typ handelt und die NSRN geringer als 8 ist, wird das Argument den Bit des Registers v\[NSRN] mit der geringsten Bedeutung zugewiesen. Die NSRN wird um eins inkrementiert. Das Argument wurde nun zugeordnet.

1. Wenn es sich beim Argument um HFA oder HVA handelt und es eine ausreichende Anzahl nicht zugewiesener SIMD- und Gleitkommaregister (NSRN + die Anzahl der Member ≤ 8) gibt, wird das Argument SIMD- und Gleitkommaregistern zugeordnet, und zwar immer ein Register pro HFA- oder HVA-Member. Die NSRN wird um die Anzahl der verwendeten Register inkrementiert. Das Argument wurde nun zugeordnet.

1. Wenn es sich beim Argument um HFA oder HVA handelt, wird NSRN auf 8 festgelegt. Die Größe des Arguments wird auf das nächste Vielfache von 8 Byte aufgerundet.

1. Wenn es sich beim Argument um HFA, HVA oder einen Gleitkommawerttyp mit vierfacher Genauigkeit oder Short-Vector-Typ handelt, wird die NSAA auf 8 oder auf die natürliche Ausrichtung des Typs des Arguments aufgerundet, je nachdem, welcher Wert größer ist.

1. Wenn es sich beim Argument um einen Gleitkommatyp mit halber oder einfacher Genauigkeit handelt, wird die Größe des Arguments auf 8 Byte festgelegt. Der Effekt ist, wie wenn das Argument auf die Bit eines 64-Bit-Registers mit der geringsten Bedeutung kopiert worden wäre und die verbleibenden Bit mit nicht angegebenen Werten aufgefüllt worden wären.

1. Wenn es sich beim Argument um HFA, HVA, Gleitkomma mit einfacher, doppelter oder vierfacher Genauigkeit oder einen Short-Vector-Typ handelt, wird das Argument in den Arbeitsspeicher der angepassten NSAA kopiert. Die NSAA wird um die Größe des Arguments inkrementiert. Das Argument wurde nun zugeordnet.

1. Wenn es sich beim Argument um ein Integral oder Zeigertyp handelt, die Größe des Arguments geringer oder gleich 8 Byte sind und die NGRN niedriger als 8 ist, wird das Argument auf die Bit in x\[NGRN] mit der geringsten Bedeutung kopiert. Die NGRN wird um eins inkrementiert. Das Argument wurde nun zugeordnet.

1. Wenn das Argument eine Ausrichtung von 16 hat, wird die NGRN auf die nächste gerade Zahl aufgerundet.

1. Wenn das Argument einen integralen Typ aufweist, die Größe des Arguments gleich 16 und die NGRN niedriger als 7 ist, wird das Argument in x\[NGRN] und x\[NGRN+1] kopiert. x\[NGRN] muss die niedrigeren adressierten Doppelwörter der Arbeitsspeicherdarstellung des Arguments enthalten. Die NGRN wird um zwei inkrementiert. Das Argument wurde nun zugeordnet.

1. Wenn es sich beim Argument um einen zusammengesetzten Typ handelt und die Größe des Arguments in Doppelwörtern 8 minus NGRN nicht übersteigt, wird das Argument in zusammenhängende Register mit allgemeinem Zweck kopiert. Begonnen wird dabei mit x\[NGRN]. Das Argument wird übergeben, wie wenn es in die Register aus einer mit Doppelwörtern ausgerichteten Adresse geladen worden wäre. Dabei wird eine angemessene Sequenz an LDR-Anweisungen verwendet, die zusammenhängende Register aus dem Arbeitsspeicher laden. Die Inhalte nicht verwendeter Teile des Registers werden von diesem Standard nicht angegeben. Die NGRN wird um die Anzahl der verwendeten Register inkrementiert. Das Argument wurde nun zugeordnet.

1. Die NGRN wird auf 8 festgelegt.

1. Die NSAA wird auf 8 aufgerundet oder auf die natürliche Ausrichtung des Typs des Arguments, je nachdem, welcher Wert größer ist.

1. Wenn es sich beim Argument um einen zusammengesetzten Typ handelt, wird das Argument in den Arbeitsspeicher der angepassten NSAA kopiert. Die NSAA wird um die Größe des Arguments inkrementiert. Das Argument wurde nun zugeordnet.

1. Wenn die Größe des Arguments geringer als 8 Byte ist, wird die Größe des Arguments auf 8 Byte festgelegt. Der Effekt ist, wie wenn das Argument auf die Bit eines 64-Bit-Registers mit der geringsten Bedeutung kopiert worden wäre und die verbleibenden Bit mit nicht angegebenen Werten aufgefüllt worden wären.

1. Das Argument wird in den Arbeitsspeicher der angepassten NSAA kopiert. Die NSAA wird um die Größe des Arguments inkrementiert. Das Argument wurde nun zugeordnet.

### <a name="addendum-variadic-functions"></a>Nachtrag: Variadische Funktionen

Funktionen, die eine variable Anzahl von Argumenten verwenden, werden anders wie die obigen verarbeitet:

1. Alle Bestandteile werden gleich behandelt. HFAs oder HVAs werden nicht gesondert behandelt.

1. SIMD- und Gleitkommaregister werden nicht verwendet.

Im Prinzip ist die Behandlung identisch damit, die Regeln C.12–C.15 zu befolgen, um Argumente einem imaginären Stapel zuzuweisen. Die ersten 64 Byte des Stapels werden dabei in x0–x7 geladen. Alle verbleibenden Stapelargumente werden normal platziert.

## <a name="return-values"></a>Rückgabewerte

Integrale Werte werden in x0 zurückgegeben.

Gleitkommawerte werden je nach Eignung in s0, d0 oder v0 zurückgegeben.

HFA- und HVA-Werte werden je nach Eignung in s0–s3, d0–d3 oder v0–v3 zurückgegeben.

Nach Wert zurückgegebene Typen werden anders verarbeitet, je nachdem, ob sie bestimmte Eigenschaften aufweisen und ob es sich bei der Funktion um einen nicht statische Memberfunktion handelt. Typen, die alle der folgenden Eigenschaften aufweisen, d. h.

- sie werden von der Definition des C++14-Standards *aggregiert*, d. h., sie haben keine von Benutzern bereitgestellten Konstruktoren, keine privaten oder geschützten, nicht statischen Datenmember, keine Basisklassen und keine virtuellen Funktionen,
- sie weisen einen trivialen Zuweisungsoperator für Kopien auf, und
- sie haben einen trivialen Destruktor,

und sie werden von Nicht-Memberfunktionen oder statischen Memberfunktionen mit folgendem Rückgabeformat zurückgegeben:

- Typen mit weniger oder gleich 8 Byte werden in x0 zurückgegeben.
- Typen mit weniger oder gleich 16 Byte werden in x0 und x1 zurückgegeben. x0 enthält dabei die niedrigeren 8 Byte.
- Bei Typen, die größer als 16 Byte sind, muss der Aufrufer einen Arbeitsspeicherblock reservieren, der groß genug ist, sowie eine Ausrichtung, um die Ergebnisse speichern zu können. Die Adresse des Arbeitsspeicherblocks muss als zusätzliches Argument der Funkion in x8 übergeben werden. Der Aufgerufene kann den Ergebnisarbeitsspeicherblock jederzeit während der Ausführung der Subroutine ändern. Der Aufgerufene muss den in x8 gespeicherten Wert nicht aufbewahren.

Alle anderen Typen verwenden diese Konvention:

- Der Aufrufer muss einen Arbeitsspeicherblock reservieren, der groß genug ist, sowie eine Ausrichtung, um die Ergebnisse speichern zu können. Die Adresse des Arbeitsspeicherblocks muss als zusätzliches Argument der Funkion in x0 übergeben werden, oder x1, wenn „$this“ in x0 übergeben wird. Der Aufgerufene kann den Ergebnisarbeitsspeicherblock jederzeit während der Ausführung der Subroutine ändern. Der Aufgerufene gibt die Adresse des Arbeitsspeicherblocks in x0 zurück.

## <a name="stack"></a>Stapel

Gemäß der ARM-ABI muss der Stapel jederzeit eine 16-Byte-Ausrichtung aufweisen. AArch64 enthält ein Hardwarefeature, das Stapelausrichtungsfehler generiert, wenn der SP keine 16-Byte-Ausrichtung aufweist und ein Lade- oder Speichervorgang im Zusammenhang mit dem SP ausgeführt wird. Bei der Ausführung von Windows ist dieses Feature jederzeit aktiviert.

Funktionen, die 4.000 oder einen höheren Wert für den Stapel zuweisen, müssen sicherstellen, dass jede Seite vor der letzten Seite in der richtigen Reihenfolge verwendet wird. Dadurch wird sichergestellt, dass kein Code die Schutzseiten „überspringt“, die Windows zur Erweiterung des Stapels verwendet. In der Regel ist dafür das `__chkstk`-Hilfsprogramm zuständig, das eine benutzerdefinierte Aufrufkonvention aufweist, die die gesamte Stapelzuteilung geteilt durch 16 in x15 übergibt.

## <a name="red-zone"></a>Red Zone

Dieser 16-Byte-Bereich direkt unter dem aktuellen Stapelzeiger ist für die Analyse und das dynamische Patching reserviert. Dadurch kann sorgfältig generierter Code eingefügt werden, in dem zwei Register bei [sp, #-16] gespeichert werden und der sie vorübergehend für beliebige Zwecke verwendet. Der Windows-Kernel stellt sicher, dass diese 16 Byte nicht überschrieben werden, wenn eine Ausnahme oder ein Interrupt im Benutzermodus und im Kernel-Modus auftreten.

## <a name="kernel-stack"></a>Kernelstapel

Der standardmäßige Stapel im Kernel-Modus unter Windows besteht aus sechs Seiten (24.000). Beachten Sie insbesondere Funktionen mit großen Stapelpuffern im Kernel-Modus. Ein Interruptvorgang zum falschen Zeitpunkt könnte einen zu geringen Toleranzbereich aufweisen und eine Stapelpanikfehlerüberprüfung erstellen.

## <a name="stack-walking"></a>Stackwalk

Windows-Code wird mit aktivierten Rahmenzeigern kompiliert ([/Oy-](reference/oy-frame-pointer-omission.md)), um einen schnellen Stackwalk zu ermöglichen. Im Allgemeinen verweist x29 (fp) auf den nächsten Link in der Kette, bei dem es sich um ein {fp, lr}-Paar handelt, das den Zeiger zum vorherigen Rahmen im Stapel und die Rückgabeadresse spezifiziert. Für Drittanbietercode sollten Rahmenzeiger ebenfalls aktiviert werden, um eine verbesserte Profilerstellung und Ablaufverfolgung zu ermöglichen.

## <a name="exception-unwinding"></a>Ausnahmeentladung

Die Stapelentladung während der Ausnahmebehandlung wird durch den Einsatz von Entladecodes aktiviert. Bei den Entladecodes handelt es sich um Bytesequenzen, die im Abschnitt .xdata der ausführbaren Datei gespeichert sind. Sie beschreiben den Vorgang des Prolog- und Epilogcodes der Funktion auf abstrakte Weise, sodass die Effekte eines Funktionsprologs als Vorbereitung für die Entladung im Stapelrahmen des Aufrufers rückgängig gemacht werden. Weitere Informationen zu Entladungscodes finden Sie unter [ARM64-Ausnahmebehandlung](arm64-exception-handling.md).

Die ARM-EABI gibt ein Ausnahmeentladungsmodell an, das Entladecodes verwendet. Diese Spezifikation ist jedoch nicht ausreichend zum Entladen unter Windows, wobei Fälle behandelt werden müssen, in denen der Computer sich in der Mitte des Prologs oder Epilogs einer Funktion befindet.

Dynamisch generierter Code sollte mit dynamischen Funktionstabellen über `RtlAddFunctionTable` und dazugehörigen Funktionen beschrieben werden, sodass der generierte Code bei der Ausnahmebehandlung beteiligt werden kann.

## <a name="cycle-counter"></a>Zykluszähler

Alle ARMv8-CPUs müssen ein Zykluszählerregister unterstützen, ein 64-Bit-Register, das Windows so konfiguriert, das es auf jeder Ausnahmeebene gelesen werden kann, einschließlich des Benutzermodus. Der Zugriff erfolgt über das spezielle PMCCNTR_EL0-Register, mithilfe des MSR-Opcodes im Assemblycode oder der systeminternen `_ReadStatusReg`-Funktion im C-/C++-Code.

Der Zykluszähler hier ist ein echter Zykluszähler, keine Wanduhrzeit. Die Zählhäufigkeit variiert mit der Prozessorfrequenz. Wenn Sie der Meinung sind, die Häufigkeit des Zykluszählers kennen zu müssen, sollten sie ihn nicht verwenden. Stattdessen sollten Sie die Gesamtbetrachtungszeit messen. Dafür können Sie `QueryPerformanceCounter` verwenden.

## <a name="see-also"></a>Siehe auch

[Häufig auftretende ARM-Migrationsprobleme bei Visual C++](common-visual-cpp-arm-migration-issues.md)<br/>
[ARM64-Ausnahmebehandlung](arm64-exception-handling.md)
