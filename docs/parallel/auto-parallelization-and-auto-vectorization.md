---
title: Automatische Parallelisierung und automatische Vektorisierung
ms.date: 11/04/2016
ms.assetid: ec71583a-287b-4599-8767-1d255e080fe3
ms.openlocfilehash: adc0dd9346cc2850b02e01804e26044c367f2d14
ms.sourcegitcommit: fcc3aeb271449f8be80348740cffef39ba543407
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/29/2020
ms.locfileid: "82538611"
---
# <a name="auto-parallelization-and-auto-vectorization"></a>Automatische Parallelisierung und automatische Vektorisierung

Automatische Parallelisierung und automatische Vektorisierung sind so konzipiert, dass automatische Leistungszuwachs für Schleifen im Code bereitgestellt wird.

## <a name="auto-parallelizer"></a>Automatische Parallelisierung

Der [/QPAR](../build/reference/qpar-auto-parallelizer.md) -Compilerschalter ermöglicht die *Automatische Parallelisierung* von Schleifen in Ihrem Code. Wenn Sie dieses Flag angeben, ohne den vorhandenen Code zu ändern, wertet der Compiler den Code aus und durchsucht Schleifen, die möglicherweise von einer Parallelisierung profitieren könnten. Da möglicherweise Schleifen gefunden werden, die nicht viel Arbeit ausführen und daher nicht von einer Parallelisierung profitiert würden, und da jede unnötige Parallelisierung die Erstellung eines Threadpools, zusätzliche Synchronisierung oder andere Prozesse auslösen kann, die die Leistung eher verlangsamen anstatt zu verbessern, ist der Compiler bei der Auswahl der Schleifen, die er parallelisiert, konservativ. Betrachten Sie das folgende Beispiel, in dem die Obergrenze der Schleife zur Kompilierzeit nicht bekannt ist:

```cpp
void loop_test(int u) {
   for (int i=0; i<u; ++i)
      A[i] = B[i] * C[i];
}
```

Da `u` ein kleiner Wert sein könnte, parallelisiert der Compiler diese Schleife nicht automatisch. Sie sollten sie dennoch parallelisierten, da Sie wissen, dass `u` immer groß ist. Um die automatische Parallelisierung zu aktivieren, geben Sie [#pragma-Schleife (hint_parallel (n))](../preprocessor/loop.md)an, wobei `n` die Anzahl der Threads ist, die übergreifend parallelisiert werden sollen. Im folgenden Beispiel versucht der Compiler, die Schleife über 8 Threads zu parallelisieren.

```cpp
void loop_test(int u) {
#pragma loop(hint_parallel(8))
   for (int i=0; i<u; ++i)
      A[i] = B[i] * C[i];
}
```

Wie bei allen [pragma-Direktiven](../preprocessor/pragma-directives-and-the-pragma-keyword.md)wird auch die alternative `__pragma(loop(hint_parallel(n)))` Pragma-Syntax unterstützt.

Es gibt einige Schleifen, die der Compiler nicht parallelisieren kann. Hier sehen Sie ein Beispiel:

```cpp
#pragma loop(hint_parallel(8))
for (int i=0; i<upper_bound(); ++i)
    A[i] = B[i] * C[i];
```

Die Funktion `upper_bound()` kann sich jedes Mal ändern, wenn sie aufgerufen wird. Da die Obergrenze nicht bekannt sein kann, kann der Compiler eine Diagnosemeldung ausgeben, die erklärt, warum diese Schleife nicht parallelisiert werden kann. Im folgenden Beispiel werden eine Schleife, die parallelisiert werden kann, eine Schleife, die nicht parallelisiert werden kann, die Compilersyntax, die an der Eingabeaufforderung verwendet wird, und die Compilerausgabe für jede Befehlszeilenoption dargestellt:

```cpp
int A[1000];
void test() {
#pragma loop(hint_parallel(0))
    for (int i=0; i<1000; ++i) {
        A[i] = A[i] + 1;
    }

    for (int i=1000; i<2000; ++i) {
        A[i] = A[i] + 1;
    }
}
```

Eine Kompilierung mit diesem Befehl:

`cl d:\myproject\mylooptest.cpp /O2 /Qpar /Qpar-report:1`

löst diese Ausgabe aus:

```Output
--- Analyzing function: void __cdecl test(void)
d:\myproject\mytest.cpp(4) : loop parallelized
```

Eine Kompilierung mit diesem Befehl:

`cl d:\myproject\mylooptest.cpp /O2 /Qpar /Qpar-report:2`

löst diese Ausgabe aus:

```Output
--- Analyzing function: void __cdecl test(void)
d:\myproject\mytest.cpp(4) : loop parallelized
d:\myproject\mytest.cpp(4) : loop not parallelized due to reason '1008'
```

Beachten Sie den Unterschied in der Ausgabe zwischen den zwei verschiedenen [/QPAR-Report-Optionen (Auto-parallelizer-Berichts Ebene)](../build/reference/qpar-report-auto-parallelizer-reporting-level.md) . `/Qpar-report:1` gibt Parallelisierungsmeldungen nur für Schleifen aus, die erfolgreich parallelisiert werden. `/Qpar-report:2` gibt Parallelisierungsmeldungen für die erfolgreiche und nicht ausgeführte Schleifenparallelisierungen aus.

Weitere Informationen zu Ursachen Codes und Meldungen finden Sie unter [vektorizer-und parallelizer-Meldungen](../error-messages/tool-errors/vectorizer-and-parallelizer-messages.md).

## <a name="auto-vectorizer"></a>Automatische Vektorisierung

Die automatische Vektorisierung analysiert Schleifen im Code und verwendet die Vektorregister und Anweisungen auf dem Zielcomputer, um sie, sofern möglich, auszuführen. Damit können Sie die Leistung des Codes verbessern. Der Compiler zielt auf die SSE2-, AVX-und AVX2-Anweisungen in Intel-oder AMD-Prozessoren oder auf die Neon-Anweisungen auf ARM-Prozessoren entsprechend dem [/arch](../build/reference/arch-minimum-cpu-architecture.md) -Schalter ab.

Die automatische Vektorisierung kann andere Anweisungen generieren, als die vom `/arch`-Schalter angegebenen. Diese Anweisungen sind durch eine Laufzeitüberprüfung geschützt, um sicherzustellen, dass der Code weiterhin ordnungsgemäß ausgeführt wird. Wenn Sie z. B. `/arch:SSE2` kompilieren, können SSE4.2-Anweisungen ausgegeben werden. Eine Laufzeitüberprüfung stellt sicher, dass SSE4.2 auf dem Zielprozessor verfügbar ist, und springt zu einer Nicht-SSE4.2-Version der Schleife, wenn der Prozessor diese Anweisungen nicht unterstützt.

Standardmäßig ist die automatische Vektorisierung aktiviert. Wenn Sie die Leistung des Codes unter Vektorisierung vergleichen möchten, können Sie mit [#pragma-Schleife (no_vector)](../preprocessor/loop.md) die Vektorisierung einer beliebigen Schleife deaktivieren.

```cpp
#pragma loop(no_vector)
for (int i = 0; i < 1000; ++i)
   A[i] = B[i] + C[i];
```

Wie bei allen [pragma-Direktiven](../preprocessor/pragma-directives-and-the-pragma-keyword.md)wird auch die alternative `__pragma(loop(no_vector))` Pragma-Syntax unterstützt.

Wie bei der automatischen Parallelisierung können Sie die Befehlszeilenoption [/Qvec-Report (Auto-Vectorizer Reporting Level)](../build/reference/qvec-report-auto-vectorizer-reporting-level.md) angeben, um entweder erfolgreich vektorisierte Schleifen nur –`/Qvec-report:1`– oder sowohl erfolgreiche als auch nicht erfolgreiche vektorisierte Schleifen`/Qvec-report:2`–) zu melden.

Weitere Informationen zu Ursachen Codes und Meldungen finden Sie unter [vektorizer-und parallelizer-Meldungen](../error-messages/tool-errors/vectorizer-and-parallelizer-messages.md).

Ein Beispiel, das zeigt, wie der Vektorisierung in der Praxis funktioniert, finden Sie unter [Project Austin Part 2 of 6: Page Curling](https://devblogs.microsoft.com/cppblog/project-austin-part-2-of-6-page-curling/)

## <a name="see-also"></a>Weitere Informationen

[ESE](../preprocessor/loop.md)<br/>
[Parallele Programmierung in nativem Code](/archive/blogs/nativeconcurrency)<br/>
[/Qpar (Automatische Parallelisierung)](../build/reference/qpar-auto-parallelizer.md)<br/>
[/Qpar-report (Berichtebene der automatischen Parallelisierung)](../build/reference/qpar-report-auto-parallelizer-reporting-level.md)<br/>
[/Qvec-report (Auto-Vectorizer-Berichtsebene)](../build/reference/qvec-report-auto-vectorizer-reporting-level.md)<br/>
[Vectorizer-und parallelizer-Meldungen](../error-messages/tool-errors/vectorizer-and-parallelizer-messages.md)
