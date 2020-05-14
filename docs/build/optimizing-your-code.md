---
title: Codeoptimierung
ms.date: 05/06/2019
helpviewer_keywords:
- performance, optimizing code
- optimization
- cl.exe compiler, performance
- optimization, C++ code
- code, optimizing
- performance, compiler
ms.openlocfilehash: 00356cf50ca8e50c80e8a1142adf654816490c9b
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "80078494"
---
# <a name="optimizing-your-code"></a>Codeoptimierung

Durch die Optimierung einer ausführbaren Datei können Sie einen Kompromiss zwischen einer hohen Ausführungsgeschwindigkeit und einer geringen Codegröße erzielen. In diesem Thema werden einige der Mechanismen erläutert, die Visual Studio bereitstellt, um Ihnen die Optimierung von Code zu erleichtern.

## <a name="language-features"></a>Sprachfunktionen

In den folgenden Themen werden einige der Optimierungsfeatures in der Programmiersprache C/C++ beschrieben.

[Pragmas und Schlüsselwörter für die Optimierung](optimization-pragmas-and-keywords.md) \
Eine Liste von Schlüsselwörtern und Pragmas, die Sie im Code verwenden können, um die Leistung zu verbessern.

[Compileroptionen (nach Kategorie sortiert)](reference/compiler-options-listed-by-category.md) \
Eine Liste von **/O**-Compileroptionen, die sich speziell auf die Ausführungsgeschwindigkeit oder Codegröße auswirken.

[Rvalue-Verweisdeklarator: &&](../cpp/rvalue-reference-declarator-amp-amp.md) \
Rvalue-Verweise unterstützen die Implementierung von *Move-Semantik*. Wenn die Move-Semantik zum Implementieren von Vorlagenbibliotheken verwendet wird, kann sich die Leistung von Anwendungen, die diese Vorlagen verwenden, erheblich verbessern.

### <a name="the-optimize-pragma"></a>Das optimize-Pragma

Wenn ein optimierter Codeabschnitt zu Fehlern oder einer Verlangsamung führt, können Sie das [optimize](../preprocessor/optimize.md)-Pragma verwenden, um die Optimierung für diesen Abschnitt zu deaktivieren.

Schließen Sie den Code, wie hier gezeigt, zwischen zwei Pragmas ein:

```cpp
#pragma optimize("", off)
// some code here
#pragma optimize("", on)
```

## <a name="programming-practices"></a>Programmierverfahren

Beim Kompilieren des Codes mit Optimierung werden möglicherweise zusätzliche Warnmeldungen angezeigt. Dieses Verhalten wird erwartet, da einige Warnungen nur mit optimiertem Code in Zusammenhang stehen. Viele Optimierungsprobleme lassen sich vermeiden, wenn Sie diese Warnungen beachten.

Wenn Sie ein Programm hinsichtlich der Geschwindigkeit optimieren, kann dies paradoxerweise dazu führen, dass Code langsamer ausgeführt wird. Dies liegt daran, dass einige Optimierungen für die Geschwindigkeit zu mehr Code führen. Beispielsweise entfällt durch das Inlining von Funktionen der Mehraufwand von Funktionsaufrufen. Durch das Inlining von zu viel Code kann das Programm jedoch so groß werden, dass die Anzahl der Seitenfehler des virtuellen Arbeitsspeichers zunimmt. Daher kann die durch das Eliminieren von Funktionsaufrufen gewonnene Geschwindigkeit bei der Speicherauslagerung verloren gehen.

In den folgenden Themen werden gute Programmierverfahren erläutert.

[Tipps zum Verbessern von zeitkritischem Code](tips-for-improving-time-critical-code.md) \
Durch bessere Codierungstechniken wird eine bessere Leistung erzielt. In diesem Thema werden Codierungstechniken vorgeschlagen, mit deren Hilfe sichergestellt werden kann, dass die zeitkritischen Teile des Codes zufriedenstellend funktionieren.

[Bewährte Methoden für die Optimierung](optimization-best-practices.md) \
Dieses Thema enthält allgemeine Richtlinien für eine bestmögliche Optimierung Ihrer Anwendung.

## <a name="debugging-optimized-code"></a>Debuggen von optimiertem Code

Da sich durch die Optimierung der vom Compiler erstellte Code möglicherweise ändert, empfiehlt es sich, die Anwendung zu debuggen, ihre Leistung zu messen und dann den Code zu optimieren.

Die folgenden Themen enthalten Informationen zum Debuggen von Releasebuilds.

- [Debuggen in Visual Studio](/visualstudio/debugger/debugging-in-visual-studio)

- [How to: Debuggen von optimiertem Code](/visualstudio/debugger/how-to-debug-optimized-code)

- [Warum Gleitkommazahlen an Genauigkeit verlieren können](why-floating-point-numbers-may-lose-precision.md)

Die folgenden Themen enthalten Informationen dazu, wie Sie das Erstellen, Laden und Ausführen Ihres Codes optimieren.

- [Erhöhen des Compilerdurchsatzes](improving-compiler-throughput.md)

- [Bei Verwendung eines Funktionsnamens ohne „()“ wird kein Code generiert](using-function-name-without-parens-produces-no-code.md)

- [Optimieren der Inlineassembly](../assembler/inline/optimizing-inline-assembly.md)

- [Festlegen der Compileroptimierung für ein ATL-Projekt](../atl/reference/specifying-compiler-optimization-for-an-atl-project.md)

- [Welche Optimierungstechniken sollten verwendet werden, um die Leistung der Clientanwendung beim Laden zu verbessern?](../build/dll-frequently-asked-questions.md#mfc_optimization)

## <a name="in-this-section"></a>In diesem Abschnitt

[Pragmas und Schlüsselwörter für die Optimierung](optimization-pragmas-and-keywords.md) \
[Erhöhen des Compilerdurchsatzes](improving-compiler-throughput.md) \
[Warum Gleitkommazahlen an Genauigkeit verlieren können](why-floating-point-numbers-may-lose-precision.md) \
[IEEE-Gleitkommadarstellung](ieee-floating-point-representation.md) \
[Tipps zum Verbessern von zeitkritischem Code](tips-for-improving-time-critical-code.md) \
[Bei Verwendung eines Funktionsnamens ohne "()" wird kein Code generiert](using-function-name-without-parens-produces-no-code.md) \
[Bewährte Methoden für die Optimierung](optimization-best-practices.md) \
[Profilgesteuerte Optimierungen](profile-guided-optimizations.md) \
[Umgebungsvariablen für profilgesteuerte Optimierungen](environment-variables-for-profile-guided-optimizations.md) \
[PgoAutoSweep](pgoautosweep.md) \
[pgomgr](pgomgr.md) \
[pgosweep](pgosweep.md) \
[How to: Zusammenführen mehrerer PGO-Profile in einem einzigen Profil](how-to-merge-multiple-pgo-profiles-into-a-single-profile.md)

## <a name="see-also"></a>Siehe auch

[Referenz zur C/C++-Erstellung](reference/c-cpp-building-reference.md)
