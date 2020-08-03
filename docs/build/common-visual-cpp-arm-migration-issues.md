---
title: Häufig auftretende ARM-Migrationsprobleme bei Visual C++
ms.date: 05/06/2019
ms.assetid: 0f4c434e-0679-4331-ba0a-cc15dd435a46
ms.openlocfilehash: 889eed2b02362f33446cd9441ef84f406817b01a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224070"
---
# <a name="common-visual-c-arm-migration-issues"></a>Häufig auftretende ARM-Migrationsprobleme bei Visual C++

Bei Verwendung des Microsoft C++-Compilers (MSVC) kann derselbe C++-Quellcode in der ARM-Architektur zu anderen Ergebnissen führen als in x86- oder x64-Architekturen.

## <a name="sources-of-migration-issues"></a>Quellen für Migrationsprobleme

Viele Probleme, auf die Sie bei der Codemigration von der x86- oder x64-Architektur auf die ARM-Architektur möglicherweise stoßen, hängen mit Quellcodekonstrukten zusammen, die ein nicht definiertes, durch die Implementierung definiertes oder nicht spezifiziertes Verhalten hervorrufen können.

*Nicht definiertes Verhalten* ist ein Verhalten, das der C++-Standard nicht definiert und das durch einen Vorgang verursacht wird, der kein vernünftiges Ergebnis liefert: z. B. die Konvertierung eines Gleitkommawerts in eine ganze Zahl ohne Vorzeichen oder die Verschiebung eines Werts um eine Anzahl von Positionen, die negativ ist oder die Anzahl der Bits im höher gestuften Typ übersteigt.

*Durch die Implementierung definiertes Verhalten* ist ein Verhalten, das der C++-Standard zum Definieren und Dokumentieren des Compilers benötigt. Ein Programm kann sich sicher auf durch die Implementierung definiertes Verhalten verlassen, auch wenn dies nicht immer portierbar ist. Beispiele für durch die Implementierung definiertes Verhalten sind u. a. die Größe der integrierten Datentypen und ihre Ausrichtungsanforderungen. Ein Beispiel für einen Vorgang, der von durch die Implementierung definiertem Verhalten beeinflusst werden kann, ist der Zugriff auf die Liste der variablen Argumente.

*Nicht spezifiziertes Verhalten* ist ein Verhalten, bei dem der C++-Standard absichtlich nicht deterministisch bleibt. Obwohl das Verhalten als nicht deterministisch angesehen wird, werden bestimmte Aufrufe von nicht spezifiziertem Verhalten von der Compilerimplementierung bestimmt. Es ist jedoch nicht erforderlich, dass ein Compilerhersteller das Ergebnis im Voraus festlegt oder ein konsistentes Verhalten zwischen vergleichbaren Aufrufen garantiert. Außerdem besteht keine Dokumentationspflicht. Ein Beispiel für nicht spezifiziertes Verhalten ist die Reihenfolge, in der Unterausdrücke, die Argumente zu einem Funktionsaufruf enthalten, ausgewertet werden.

Andere Migrationsprobleme können auf Hardwareunterschiede zwischen ARM- und x86- bzw. x64-Architekturen zurückzuführen sein, die auf unterschiedliche Weise mit dem C++-Standard interagieren. Durch das Modell des starken Arbeitsspeichers der x86- und x64-Architektur erhalten beispielsweise **`volatile`** -qualifizierte Variablen einige zusätzliche Eigenschaften, die in der Vergangenheit verwendet wurden, um bestimmte Arten der Kommunikation zwischen Threads zu erleichtern. Das schwache Speichermodell der ARM-Architektur unterstützt diese Verwendung nicht, und auch der C++-Standard erfordert dies nicht.

> [!IMPORTANT]
> Auch wenn **`volatile`** einige Eigenschaften erhält, die zur Implementierung bestimmter Formen der Kommunikation zwischen Threads in x86- und x64-Architekturen verwendet werden können, reichen diese zusätzlichen Eigenschaften nicht aus, um die Kommunikation zwischen Threads allgemein zu implementieren. Der C++-Standard empfiehlt, dass eine solche Kommunikation stattdessen mithilfe geeigneter Synchronisierungsprimitiven implementiert wird.

Da verschiedene Plattformen diese Art von Verhalten unterschiedlich ausdrücken können, ist die Portierung von Software zwischen Plattformen unter Umständen schwierig und fehleranfällig, wenn sie vom Verhalten einer bestimmten Plattform abhängt. Obwohl viele dieser Verhaltensweisen beobachtet werden können und stabil erscheinen mögen, ist es zumindest nicht portierbar, sich auf sie zu verlassen, und in den Fällen von nicht definiertem oder nicht spezifiziertem Verhalten ist dies auch ein Fehler. Selbst das Verhalten, das in diesem Dokument beschrieben wird, sollte nicht als verlässlich angesehen werden und könnte sich in zukünftigen Compilern oder CPU-Implementierungen ändern.

## <a name="example-migration-issues"></a>Beispiel für Migrationsprobleme

Im restlichen Dokument wird beschrieben, wie das unterschiedliche Verhalten dieser C++-Sprachelemente auf verschiedenen Plattformen zu unterschiedlichen Ergebnissen führen kann.

### <a name="conversion-of-floating-point-to-unsigned-integer"></a>Konvertierung von Gleitkommazahlen in ganze Zahlen ohne Vorzeichen

Bei der ARM-Architektur erfolgt die Konvertierung eines Gleitkommawerts in eine 32-Bit-Ganzzahl auf den nächsten Wert, den die Ganzzahl darstellen kann, wenn der Gleitkommawert außerhalb des Bereichs liegt, den die Ganzzahl darstellen kann. Bei den x86- und x64-Architekturen wird die Konvertierung umgebrochen, wenn die ganze Zahl kein Vorzeichen hat, oder auf -2147483648 gesetzt, wenn die ganze Zahl ein Vorzeichen aufweist. Keine dieser Architekturen unterstützt direkt die Konvertierung von Gleitkommawerten in kleinere ganzzahlige Typen; stattdessen werden die Konvertierungen auf 32 Bit durchgeführt, und die Ergebnisse werden auf eine kleinere Größe gekürzt.

Für die ARM-Architektur bedeutet die Kombination von Sättigung und Kürzung, dass bei der Konvertierung in Typen ohne Vorzeichen kleinere Typen ohne Vorzeichen korrekt gesättigt werden, wenn diese eine 32-Bit-Ganzzahl sättigt, aber ein gekürztes Ergebnis für Werte erzeugt wird, die größer sind, als der kleinere Typ darstellen kann, aber zu klein, um die volle 32-Bit-Ganzzahl zu sättigen. Bei der Konvertierung werden auch 32-Bit-Ganzzahlen mit Vorzeichen korrekt gesättigt, aber das Kürzen von gesättigten, ganzen Zahlen mit Vorzeichen ergibt -1 für positiv gesättigte Werte und 0 für negativ gesättigte Werte. Die Konvertierung in eine kleinere ganze Zahl mit Vorzeichen erzeugt ein nicht vorhersagbares Ergebnis.

Bei den x86- und x64-Architekturen macht die Kombination aus Umbruchverhalten bei Konvertierungen von ganzen Zahlen ohne Vorzeichen und der expliziten Bewertung für Konvertierungen von ganzen Zahlen mit Vorzeichen bei einer Überschreitung, zusammen mit der Kürzung, die Ergebnisse für die meisten Verschiebungen unvorhersagbar, wenn sie zu groß sind.

Diese Plattformen unterscheiden sich auch darin, wie sie die Konvertierung von NaN (Not-a-Number) in ganzzahlige Typen verarbeiten. Bei ARM-Architekturen wird NaN in 0x0000000000, bei x86- und x64-Architekturen in 0x80000000 konvertiert.

Auf die Konvertierung von Gleitkommawerten kann man sich nur verlassen, wenn bekannt ist, dass der Wert innerhalb des Bereichs des ganzzahligen Typs liegt, in den er konvertiert wird.

### <a name="shift-operator---behavior"></a>Verhalten des Schiebeoperators (\<\< >>)

Bei der ARM-Architektur kann ein Wert um bis zu 255 Bit nach links oder rechts verschoben werden, bevor sich das Muster wiederholt. Bei x86- und x64-Architekturen wird das Muster bei jedem Vielfachen von 32 wiederholt, es sei denn, die Quelle des Musters ist eine 64-Bit-Variable; in diesem Fall wiederholt sich das Muster bei jedem Vielfachen von 64 für x64 und bei jedem Vielfachen von 256 für x86, wenn eine Softwareimplementierung eingesetzt wird. Zum Beispiel ist für eine 32-Bit-Variable, die einen um 32 Positionen nach links verschobenen Wert von 1 hat, bei ARM das Ergebnis 0, bei x86 ist das Ergebnis 1 und bei x64 ist das Ergebnis ebenfalls 1. Wenn die Quelle des Werts jedoch eine 64-Bit-Variable ist, dann ist das Ergebnis auf allen drei Plattformen 4294967296, und der Wert wird erst dann „umgebrochen“, wenn er um 64 Positionen bei x64 bzw. 256 Positionen bei ARM und x86 verschoben wird.

Da das Ergebnis eines Verschiebevorgangs, der die Anzahl der Bits im Quelltyp überschreitet, nicht definiert ist, muss der Compiler nicht in allen Situationen ein konsistentes Verhalten aufweisen. Wenn zum Beispiel beide Operanden einer Verschiebung zur Kompilierzeit bekannt sind, kann der Compiler das Programm optimieren, indem er mit einer internen Routine das Ergebnis der Verschiebung vorab berechnet und dann den Verschiebevorgang durch das Ergebnis ersetzt. Wenn der Betrag der Verschiebung zu groß oder negativ ist, kann das Ergebnis der internen Routine anders ausfallen als das Ergebnis desselben Verschiebeausdrucks, der von der CPU ausgeführt wird.

### <a name="variable-arguments-varargs-behavior"></a>Verhalten von variablen Argumenten (VarArgs)

Bei der ARM-Architektur unterliegen Parameter aus der Liste der variablen Argumente, die auf dem Stapel übergeben werden, der Ausrichtung. Beispielsweise wird ein 64-Bit-Parameter an einer 64-Bit-Grenze ausgerichtet. Bei x86 und x64 werden Argumente, die auf dem Stapel übergeben werden, nicht ausgerichtet und werden dicht gepackt. Dieser Unterschied kann dazu führen, dass eine variadische Funktion wie `printf` Speicheradressen liest, die bei ARM zur Auffüllung gedacht waren, wenn das erwartete Layout der Liste der variablen Argumente nicht genau übereinstimmt, auch wenn dies für eine Teilmenge einiger Werte bei der x86- oder x64-Architektur funktionieren könnte. Betrachten Sie das folgende Beispiel:

```C
// notice that a 64-bit integer is passed to the function, but '%d' is used to read it.
// on x86 and x64 this may work for small values because %d will "parse" the low-32 bits of the argument.
// on ARM the calling convention will align the 64-bit value and the code will print a random value
printf("%d\n", 1LL);
```

In diesem Fall kann der Fehler behoben werden, indem sichergestellt wird, dass die richtige Formatangabe verwendet wird, sodass die Ausrichtung des Arguments berücksichtigt wird. Dieser Code ist korrekt:

```C
// CORRECT: use %I64d for 64-bit integers
printf("%I64d\n", 1LL);
```

### <a name="argument-evaluation-order"></a>Auswertungsreihenfolge der Argumente

Da ARM-, x86- und x64-Prozessoren so unterschiedlich sind, können sie unterschiedliche Anforderungen an Compilerimplementierungen und auch unterschiedliche Möglichkeiten für Optimierungen darstellen. Aus diesem Grund und wegen anderer Faktoren wie Aufrufkonvention und Optimierungseinstellungen könnte ein Compiler Funktionsargumente in unterschiedlicher Reihenfolge für verschiedene Architekturen oder bei Änderung der anderen Faktoren auswerten. Dies kann dazu führen, dass sich das Verhalten einer App, die auf einer bestimmten Auswertungsreihenfolge beruht, unerwartet ändert.

Diese Art von Fehler kann auftreten, wenn Argumente für eine Funktion Nebeneffekte haben, die sich auf andere Argumente für die Funktion im gleichen Aufruf auswirken. Normalerweise ist diese Art von Abhängigkeit leicht zu vermeiden. Sie kann jedoch manchmal durch schwer zu erkennende Abhängigkeiten oder durch eine Überlastung des Operators verdeckt werden. Betrachten Sie dieses Codebeispiel:

```cpp
handle memory_handle;

memory_handle->acquire(*p);
```

Dies ist zwar klar definiert, aber wenn `->` und `*` überladene Operatoren sind, dann wird dieser Code in etwas übersetzt, das dem Folgenden ähnelt:

```cpp
Handle::acquire(operator->(memory_handle), operator*(p));
```

Und wenn es eine Abhängigkeit zwischen `operator->(memory_handle)` und `operator*(p)` gibt, könnte der Code auf eine bestimmte Auswertungsreihenfolge zurückgreifen, auch wenn der ursprüngliche Code so aussieht, als gäbe es keinerlei Abhängigkeit.

### <a name="volatile-keyword-default-behavior"></a>Standardverhalten des volatile-Schlüsselworts

Der MSVC-Compiler unterstützt zwei verschiedene Interpretationen des **`volatile`** -Speicherqualifizierers, die Sie mithilfe von Compilerparametern festlegen können. Der Schalter [/volatile:ms](reference/volatile-volatile-keyword-interpretation.md) wählt die erweiterte volatile Semantik von Microsoft aus, die eine feste Reihenfolge sicherstellt, wie dies traditionell für x86 und x64 aufgrund des starken Speichermodells bei diesen Architekturen der Fall war. Der Schalter [/volatile:iso](reference/volatile-volatile-keyword-interpretation.md) wählt die strikte volatile Semantik des C++-Standards aus, die keine feste Reihenfolge garantiert.

Bei der ARM-Architektur lautet der Standard **/volatile:iso**, weil ARM-Prozessoren ein wenig geordnetes Speichermodell haben und weil ARM-Software nicht auf die erweiterte Semantik von **/volatile:ms** angewiesen ist und in der Regel keine Schnittstelle zu Software haben muss, die diese benötigt. Dennoch ist es manchmal praktisch oder sogar erforderlich, ein ARM-Programm zu kompilieren, um die erweiterte Semantik zu verwenden. Beispielsweise ist es möglicherweise zu teuer, ein Programm für die Verwendung der ISO-C++-Semantik zu portieren, oder die Treibersoftware muss der herkömmlichen Semantik entsprechen, damit sie ordnungsgemäß funktioniert. In diesen Fällen können Sie den Parameter **/volatile: ms** verwenden. Zum erneuten Erstellen der traditionellen volatilen Semantik bei ARM-Zielen muss der Compiler jedoch Arbeitsspeicherabgrenzungen um alle Lese- oder Schreibvorgänge einer **`volatile`** -Variablen einfügen, um eine feste Reihenfolge zu erzwingen, was sich negativ auf die Leistung auswirken kann.

Bei den x86- und x64-Architekturen lautet der Standard **/volatile:ms**, da ein Großteil der Software, die bereits für diese Architekturen mit MSVC erstellt wurde, auf diesen Architekturen beruht. Beim Kompilieren von x86- und x64-Programmen können Sie den Schalter **/volatile:iso** festlegen, um eine unnötige Abhängigkeit von der traditionellen volatilen Semantik zu vermeiden und die Portabilität zu fördern.

## <a name="see-also"></a>Siehe auch

[Konfigurieren von Visual C++ für ARM-Prozessoren](configuring-programs-for-arm-processors-visual-cpp.md)
