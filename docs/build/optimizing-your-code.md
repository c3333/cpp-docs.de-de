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
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "80078494"
---
# <a name="optimizing-your-code"></a>Codeoptimierung

Durch Optimieren einer ausführbaren Datei können Sie ein Gleichgewicht zwischen schneller Ausführungsgeschwindigkeit und kleiner Codegröße erzielen. In diesem Thema werden einige der Mechanismen erläutert, die Visual Studio bereitstellt, um Ihnen die Optimierung von Code zu erleichtern.

## <a name="language-features"></a>Sprachfunktionen

In den folgenden Themen werden einige der Optimierungs Features in der ProgrammierspracheC++ C/Sprache beschrieben.

[Optimierungs-Pragmas und Schlüsselwörter](optimization-pragmas-and-keywords.md) \
Eine Liste von Schlüsselwörtern und Pragmas, die Sie im Code verwenden können, um die Leistung zu verbessern.

[Compileroptionen nach Kategorien sortiert](reference/compiler-options-listed-by-category.md) \
Eine Liste von **/O** -Compileroptionen, die sich speziell auf die Ausführungsgeschwindigkeit oder die Codegröße auswirken.

[Rvalue-verweisdedeklarator: & &](../cpp/rvalue-reference-declarator-amp-amp.md) \
Rvalue-Verweise unterstützen die Implementierung der Verschiebungs *Semantik*. Wenn die Verschiebungs Semantik zum Implementieren von Vorlagen Bibliotheken verwendet wird, kann sich die Leistung von Anwendungen, die diese Vorlagen verwenden, erheblich verbessern.

### <a name="the-optimize-pragma"></a>Das Pragma "optimieren"

Wenn ein optimierter Code Abschnitt Fehler oder eine Verlangsamung verursacht, können Sie das Pragma " [optimieren](../preprocessor/optimize.md) " verwenden, um die Optimierung für diesen Abschnitt zu deaktivieren.

Schließen Sie den Code zwischen zwei Pragmas ein, wie hier gezeigt:

```cpp
#pragma optimize("", off)
// some code here
#pragma optimize("", on)
```

## <a name="programming-practices"></a>Programmierverfahren

Beim Kompilieren des Codes mit Optimierung werden möglicherweise zusätzliche Warnmeldungen angezeigt. Dieses Verhalten wird erwartet, da einige Warnungen nur mit optimiertem Code in Beziehung stehen. Sie können viele Optimierungsprobleme vermeiden, wenn Sie diese Warnungen beachten.

Wenn Sie ein Programm für die Geschwindigkeit optimieren, kann dies dazu führen, dass Code langsamer ausgeführt wird. Dies liegt daran, dass einige Optimierungen für die Geschwindigkeit die Codegröße erhöhen. Beispielsweise entfällt durch Inlining-Funktionen der mehr Aufwand von Funktionsaufrufen. Das Inlining zu viel Code kann jedoch dazu führen, dass das Programm so groß wird, dass die Anzahl der Seiten Fehler des virtuellen Speichers zunimmt. Aus diesem Grund kann die durch das Eliminieren von Funktionsaufrufen gewonnene Geschwindigkeit bei der Speicher Auslagerung verloren gehen.

In den folgenden Themen werden gute Programmierverfahren erläutert.

[Tipps zum Verbessern von Zeit kritischem Code](tips-for-improving-time-critical-code.md) \
Bessere Codierungstechniken erzielen eine bessere Leistung. In diesem Thema werden Codierungstechniken vorgeschlagen, mit deren Hilfe Sie sicherstellen können, dass die zeitkritischen Teile des Codes zufriedenstellend funktionieren.

[Bewährte Methoden](optimization-best-practices.md) für die Optimierung \
Bietet allgemeine Richtlinien zur optimalen Optimierung Ihrer Anwendung.

## <a name="debugging-optimized-code"></a>Debugging von optimiertem Code

Da durch die Optimierung der vom Compiler erstellte Code geändert werden kann, empfiehlt es sich, die Anwendung zu Debuggen und ihre Leistung zu messen und dann den Code zu optimieren.

Die folgenden Themen enthalten Informationen zum Debuggen von Releasebuilds.

- [Debuggen in Visual Studio](/visualstudio/debugger/debugging-in-visual-studio)

- [Gewusst wie: Debuggen von optimiertem Code](/visualstudio/debugger/how-to-debug-optimized-code)

- [Warum Gleitkommazahlen an Genauigkeit verlieren können](why-floating-point-numbers-may-lose-precision.md)

Die folgenden Themen enthalten Informationen dazu, wie Sie das Erstellen, laden und ausführen Ihres Codes optimieren.

- [Erhöhen des Compilerdurchsatzes](improving-compiler-throughput.md)

- [Bei Verwendung eines Funktionsnamens ohne „()“ wird kein Code generiert](using-function-name-without-parens-produces-no-code.md)

- [Optimieren der Inlineassembly](../assembler/inline/optimizing-inline-assembly.md)

- [Festlegen der Compileroptimierung für ein ATL-Projekt](../atl/reference/specifying-compiler-optimization-for-an-atl-project.md)

- [Welche Optimierungstechniken sollte ich verwenden, um die Leistung der Client Anwendung beim Laden zu verbessern?](../build/dll-frequently-asked-questions.md#mfc_optimization)

## <a name="in-this-section"></a>In diesem Abschnitt

[Optimierungs-Pragmas und Schlüsselwörter](optimization-pragmas-and-keywords.md) \
[Verbessern des Compilerdurchsatz](improving-compiler-throughput.md) \
[Warum Gleit Komma Zahlen die Genauigkeit verlieren können](why-floating-point-numbers-may-lose-precision.md) \
[IEEE-Gleit Komma Darstellung](ieee-floating-point-representation.md) \
[Tipps zum Verbessern von Zeit kritischem Code](tips-for-improving-time-critical-code.md) \
Die [Verwendung von Funktions Name ohne () erzeugt keinen Code](using-function-name-without-parens-produces-no-code.md) \
[Bewährte Methoden](optimization-best-practices.md) für die Optimierung \
[Profil gesteuerte Optimierungen](profile-guided-optimizations.md) \
[Umgebungsvariablen für Profil gesteuerte Optimierungen](environment-variables-for-profile-guided-optimizations.md) \
[PgoAutoSweep](pgoautosweep.md) - \
[pgomgr](pgomgr.md) - \
[PGOSWEEP](pgosweep.md) - \
[Vorgehensweise: Zusammenführen mehrerer PGO-Profile in einem einzigen Profil](how-to-merge-multiple-pgo-profiles-into-a-single-profile.md)

## <a name="see-also"></a>Weitere Informationen

[Referenz zur C/C++-Erstellung](reference/c-cpp-building-reference.md)
