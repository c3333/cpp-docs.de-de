---
title: Häufig auftretende ARM-Migrationsprobleme bei Visual C++
ms.date: 05/06/2019
ms.assetid: 0f4c434e-0679-4331-ba0a-cc15dd435a46
ms.openlocfilehash: 2c29b4ffa5344b309622314970ce52c47a0ebd05
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328796"
---
# <a name="common-visual-c-arm-migration-issues"></a>Häufig auftretende ARM-Migrationsprobleme bei Visual C++

Wenn Sie den Microsoft C++-Compiler (MSVC) verwenden, kann derselbe C++-Quellcode in der ARM-Architektur andere Ergebnisse liefern als bei x86- oder x64-Architekturen.

## <a name="sources-of-migration-issues"></a>Quellen von Migrationsproblemen

Viele Probleme, die beim Migrieren von Code aus der x86- oder x64-Architektur in die ARM-Architektur auftreten können, beziehen sich auf Quellcodekonstrukte, die möglicherweise nicht definiertes, implementierungsdefiniertes oder nicht angegebenes Verhalten aufrufen.

*Undefiniertes Verhalten* ist ein Verhalten, das der C++-Standard nicht definiert, und das wird durch einen Vorgang verursacht, der kein vernünftiges Ergebnis hat: z. B. das Konvertieren eines Gleitkommawerts in eine nicht signierte ganzzahlige Datei oder das Verschieben eines Werts um eine Anzahl von Positionen, die negativ ist oder die Anzahl der Bits in ihrem heraufgestuften Typ überschreitet.

*Das von der Implementierung definierte Verhalten* ist ein Verhalten, das der C++-Standard vom Compileranbieter definieren und dokumentieren muss. Ein Programm kann sich sicher auf das von der Implementierung definierte Verhalten verlassen, auch wenn dies möglicherweise nicht portierbar ist. Beispiele für ein implementierungsdefiniertes Verhalten sind die Größe integrierter Datentypen und deren Ausrichtungsanforderungen. Ein Beispiel für einen Vorgang, der möglicherweise durch das durch die Implementierung definierte Verhalten beeinflusst wird, ist der Zugriff auf die Liste der Variablenargumente.

*Nicht angegebenes Verhalten* ist ein Verhalten, das der C++-Standard absichtlich nicht deterministisch hinterlässt. Obwohl das Verhalten als nicht deterministisch betrachtet wird, werden bestimmte Aufrufe nicht angegebenen Verhaltens von der Compilerimplementierung bestimmt. Es ist jedoch nicht erforderlich, dass ein Compileranbieter das Ergebnis vorab bestimmt oder ein konsistentes Verhalten zwischen vergleichbaren Aufrufen garantiert, und es besteht keine Dokumentation. Ein Beispiel für nicht angegebenes Verhalten ist die Reihenfolge, in der Unterausdrücke, die Argumente für einen Funktionsaufruf enthalten, ausgewertet werden.

Andere Migrationsprobleme können auf Hardwareunterschiede zwischen ARM- und x86- oder x64-Architekturen zurückgeführt werden, die unterschiedlich mit dem C++-Standard interagieren. Das starke Speichermodell der x86- und x64-Architektur gibt `volatile`beispielsweise -qualifizierten Variablen einige zusätzliche Eigenschaften, die in der Vergangenheit verwendet wurden, um bestimmte Arten der Interthreadkommunikation zu erleichtern. Das schwache Speichermodell der ARM-Architektur unterstützt diese Verwendung jedoch nicht, und der C++-Standard erfordert dies nicht.

> [!IMPORTANT]
> Obwohl `volatile` einige Eigenschaften erhalten werden, die zum Implementieren begrenzter Formen der Interthreadkommunikation auf x86 und x64 verwendet werden können, reichen diese zusätzlichen Eigenschaften nicht aus, um die Interthreadkommunikation im Allgemeinen zu implementieren. Der C++-Standard empfiehlt, eine solche Kommunikation mithilfe geeigneter Synchronisierungsprimitiven zu implementieren.

Da verschiedene Plattformen diese Art von Verhalten unterschiedlich ausdrücken können, kann die Portierung von Software zwischen Plattformen schwierig und fehleranfällig sein, wenn sie vom Verhalten einer bestimmten Plattform abhängt. Obwohl viele dieser Verhaltensweisen beobachtet werden können und stabil erscheinen können, ist es zumindest nicht portierbar, sich darauf zu verlassen, und im Falle von nicht definiertem oder nicht spezifiziertem Verhalten ist es auch ein Fehler. Selbst das in diesem Dokument zitierte Verhalten sollte nicht berücksichtigt werden und könnte sich in zukünftigen Compilern oder CPU-Implementierungen ändern.

## <a name="example-migration-issues"></a>Beispiel für Migrationsprobleme

Der Rest dieses Dokuments beschreibt, wie das unterschiedliche Verhalten dieser C++-Sprachelemente auf verschiedenen Plattformen zu unterschiedlichen Ergebnissen führen kann.

### <a name="conversion-of-floating-point-to-unsigned-integer"></a>Konvertierung des Gleitkommas in nicht signierte Ganzzahl

In der ARM-Architektur wird die Konvertierung eines Gleitkommawerts in eine 32-Bit-Ganzzahl in den nächsten Wert gesättigt, den die ganze Zahl darstellen kann, wenn der Gleitkommawert außerhalb des Bereichs liegt, den die ganze Zahl darstellen kann. Bei den x86- und x64-Architekturen wird die Konvertierung umbrochen, wenn die ganze Zahl nicht signiert ist oder auf -2147483648 festgelegt ist, wenn die ganze Zahl signiert ist. Keine dieser Architekturen unterstützt direkt die Konvertierung von Gleitkommawerten in kleinere Ganzzahltypen. Stattdessen werden die Konvertierungen in 32 Bit durchgeführt, und die Ergebnisse werden auf eine kleinere Größe abgeschnitten.

Für die ARM-Architektur bedeutet die Kombination aus Sättigung und Abschneide, dass die Konvertierung in nicht signierte Typen kleinere nicht signierte Typen korrekt sättigt, wenn sie eine 32-Bit-Ganzzahl sättigen, aber ein abgeschnittenes Ergebnis für Werte erzeugt, die größer als der kleinere Typ darstellen können, aber zu klein sind, um die vollständige 32-Bit-Ganzzahl zu sättigen. Die Konvertierung sättigt auch korrekt für 32-Bit-ganzer Code, aber das Abschneiden von gesättigten, signierten Ganzzahlen ergibt -1 für positiv gesättigte Werte und 0 für negativ gesättigte Werte. Die Konvertierung in eine kleinere signierte Ganzzahl führt zu einem abgeschnittenen Ergebnis, das unvorhersehbar ist.

Für die x86- und x64-Architekturen macht die Kombination aus Umbruchverhalten für ganzzahlige Konvertierungen und expliziter Bewertung für signierte Ganzzahlkonvertierungen beim Überlauf zusammen mit dem Abschneiden die Ergebnisse für die meisten Verschiebungen unvorhersehbar, wenn sie zu groß sind.

Diese Plattformen unterscheiden sich auch in der Art und Weise, wie sie die Konvertierung von NaN (Not-a-Number) in ganzzahlige Typen handhaben. Bei ARM konvertiert NaN in 0x0000000; auf x86 und x64 wird in 0x8000000konvertiert.

Die Gleitkommakonvertierung kann nur verwendet werden, wenn Sie wissen, dass sich der Wert innerhalb des Bereichs des Ganzzahltyps befindet, in den er konvertiert wird.

### <a name="shift-operator---behavior"></a>Shift-Operator-Verhalten ( >>)\< \<

In der ARM-Architektur kann ein Wert nach links oder rechts bis zu 255 Bit verschoben werden, bevor sich das Muster zu wiederholen beginnt. Bei x86- und x64-Architekturen wird das Muster bei jedem Vielfachen von 32 wiederholt, es sei denn, die Quelle des Musters ist eine 64-Bit-Variable. in diesem Fall wiederholt sich das Muster bei jedem Vielfachen von 64 auf x64 und jedes Vielfache von 256 auf x86, bei dem eine Softwareimplementierung verwendet wird. Zum Beispiel für eine 32-Bit-Variable, die einen Wert von 1 links verschoben durch 32 Positionen hat, auf ARM ist das Ergebnis 0, auf x86 ist das Ergebnis 1, und auf x64 ist das Ergebnis auch 1. Wenn die Quelle des Werts jedoch eine 64-Bit-Variable ist, dann ist das Ergebnis auf allen drei Plattformen 4294967296, und der Wert "umwickelt" erst, wenn er 64 Positionen auf x64 oder 256 Positionen auf ARM und x86 verschoben hat.

Da das Ergebnis eines Schichtvorgangs, der die Anzahl der Bits im Quelltyp überschreitet, nicht definiert ist, muss der Compiler in allen Situationen kein konsistentes Verhalten aufweisen. Wenn z. B. beide Operanden einer Verschiebung zur Kompilierungszeit bekannt sind, kann der Compiler das Programm optimieren, indem er eine interne Routine verwendet, um das Ergebnis der Verschiebung vorzuberechnen und dann das Ergebnis anstelle des Schichtvorgangs zu ersetzen. Wenn der Schichtbetrag zu groß oder negativ ist, kann sich das Ergebnis der internen Routine von dem Ergebnis desselben Verschiebungsausdrucks unterscheiden, der von der CPU ausgeführt wird.

### <a name="variable-arguments-varargs-behavior"></a>Verhalten von Variablenargumenten (varargs)

In der ARM-Architektur unterliegen Parameter aus der Liste der Variablenargumente, die auf dem Stapel übergeben werden, der Ausrichtung. Beispielsweise wird ein 64-Bit-Parameter an einer 64-Bit-Grenze ausgerichtet. Auf x86 und x64 unterliegen Argumente, die auf dem Stapel übergeben werden, nicht der Ausrichtung und dem festverpacken. Dieser Unterschied kann dazu führen, `printf` dass eine variadic Funktion wie das Lesen von Speicheradressen, die als Auffüllung auf ARM vorgesehen waren, wenn das erwartete Layout der Liste der Variablenargumente nicht genau übereinstimmt, obwohl es für eine Teilmenge einiger Werte auf den x86- oder x64-Architekturen funktionieren könnte. Betrachten Sie dieses Beispiel:

```C
// notice that a 64-bit integer is passed to the function, but '%d' is used to read it.
// on x86 and x64 this may work for small values because %d will "parse" the low-32 bits of the argument.
// on ARM the calling convention will align the 64-bit value and the code will print a random value
printf("%d\n", 1LL);
```

In diesem Fall kann der Fehler behoben werden, indem sichergestellt wird, dass die richtige Formatspezifikation verwendet wird, sodass die Ausrichtung des Arguments berücksichtigt wird. Dieser Code ist richtig:

```C
// CORRECT: use %I64d for 64-bit integers
printf("%I64d\n", 1LL);
```

### <a name="argument-evaluation-order"></a>Argumentauswertungsreihenfolge

Da ARM-, x86- und x64-Prozessoren so unterschiedlich sind, können sie unterschiedliche Anforderungen an Compilerimplementierungen und auch unterschiedliche Optimierungsmöglichkeiten darstellen. Aus diesem Grund kann ein Compiler zusammen mit anderen Faktoren wie Aufrufkonventions- und Optimierungseinstellungen Funktionsargumente in einer anderen Reihenfolge auf verschiedenen Architekturen auswerten oder wenn die anderen Faktoren geändert werden. Dies kann dazu führen, dass sich das Verhalten einer App, die auf einer bestimmten Auswertungsreihenfolge beruht, unerwartet ändert.

Diese Art von Fehler kann auftreten, wenn Argumente für eine Funktion Nebenwirkungen haben, die sich auf andere Argumente für die Funktion im gleichen Aufruf auswirken. Normalerweise ist diese Art von Abhängigkeit leicht zu vermeiden, aber sie kann manchmal durch Abhängigkeiten verdeckt werden, die schwer zu erkennen sind, oder durch Eine Überladung des Bedieners. Betrachten Sie dieses Codebeispiel:

```cpp
handle memory_handle;

memory_handle->acquire(*p);
```

Dies scheint klar definiert, aber wenn `->` und `*` sind überladene Operatoren, dann wird dieser Code in etwas übersetzt, das diesem ähnelt:

```cpp
Handle::acquire(operator->(memory_handle), operator*(p));
```

Und wenn eine Abhängigkeit `operator->(memory_handle)` zwischen `operator*(p)`und besteht, kann der Code auf einer bestimmten Auswertungsreihenfolge basieren, obwohl der ursprüngliche Code so aussieht, als ob keine Abhängigkeit möglich ist.

### <a name="volatile-keyword-default-behavior"></a>volatiles Schlüsselwort-Standardverhalten

Der MSVC-Compiler unterstützt zwei `volatile` unterschiedliche Interpretationen des Speicherqualifizierers, die Sie mithilfe von Compilerwechseln angeben können. Der Schalter [/volatile:ms](reference/volatile-volatile-keyword-interpretation.md) wählt die erweiterte flüchtige Semantik von Microsoft aus, die eine starke Reihenfolge garantiert, wie dies bei x86 und x64 aufgrund des starken Speichermodells auf diesen Architekturen der Fall war. Der Schalter [/volatile:iso](reference/volatile-volatile-keyword-interpretation.md) wählt die strenge flüchtige C++-Standardsemantik aus, die keine starke Reihenfolge garantiert.

In der ARM-Architektur ist die Standardeinstellung **/volatile:iso,** da ARM-Prozessoren über ein schwach geordnetes Speichermodell verfügen und weil die ARM-Software nicht über ein Vermächtnis verfügt, sich auf die erweiterte Semantik von **/volatile:ms** zu verlassen, und in der Regel keine Schnittstelle zu Software haben muss, die dies tut. Es ist jedoch manchmal noch bequem oder sogar erforderlich, ein ARM-Programm zu kompilieren, um die erweiterte Semantik zu verwenden. Beispielsweise kann es zu teuer sein, ein Programm für die Verwendung der ISO C++-Semantik zu portieren, oder die Treibersoftware muss sich an die herkömmliche Semantik halten, um ordnungsgemäß zu funktionieren. In diesen Fällen können Sie den Schalter **/volatile:ms** verwenden. Um jedoch die traditionelle flüchtige Semantik für ARM-Ziele neu zu erstellen, `volatile` muss der Compiler Speicherbarrieren um jeden Lese- oder Schreibvorgang einer Variablen einfügen, um eine starke Reihenfolge zu erzwingen, die sich negativ auf die Leistung auswirken kann.

Bei den x86- und x64-Architekturen ist die Standardeinstellung **/volatile:ms,** da ein Großteil der Software, die bereits für diese Architekturen mithilfe von MSVC erstellt wurde, auf ihnen basiert. Wenn Sie x86- und x64-Programme kompilieren, können Sie den Schalter **/volatile:iso** angeben, um unnötige Abhängigkeiten von der herkömmlichen flüchtigen Semantik zu vermeiden und die Portabilität zu fördern.

## <a name="see-also"></a>Siehe auch

[Konfigurieren von Visual C++ für ARM-Prozessoren](configuring-programs-for-arm-processors-visual-cpp.md)
