---
title: /openmp (OpenMP-Unterstützung aktivieren)
ms.date: 04/15/2019
f1_keywords:
- /openmp
- VC.Project.VCCLCompilerTool.OpenMP
helpviewer_keywords:
- /openmp compiler option [C++]
- -openmp compiler option [C++]
ms.assetid: 9082b175-18d3-4378-86a7-c0eb95664e13
ms.openlocfilehash: d3454650bfaaacd756e5cfc73df056441a39f5ac
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336194"
---
# <a name="openmp-enable-openmp-support"></a>/openmp (OpenMP-Unterstützung aktivieren)

Bewirkt, dass [`#pragma omp`](../../preprocessor/omp.md) der Compiler Direktiven zur Unterstützung von OpenMP verarbeitet.

## <a name="syntax"></a>Syntax

::: moniker range=">= vs-2019"

> **/openmp**\[**:**__experimentell__]

::: moniker-end

::: moniker range="<= vs-2017"

> **/openmp**

::: moniker-end

## <a name="remarks"></a>Bemerkungen

`#pragma omp`wird verwendet, um [Richtlinien](../../parallel/openmp/reference/openmp-directives.md) und [Klauseln](../../parallel/openmp/reference/openmp-clauses.md)anzugeben. Wenn **/openmp** in einer Kompilierung nicht angegeben ist, ignoriert der Compiler OpenMP-Klauseln und -Direktiven. [OpenMP Function-Aufrufe](../../parallel/openmp/reference/openmp-functions.md) werden vom Compiler verarbeitet, auch wenn **/openmp** nicht angegeben ist.

::: moniker range=">= vs-2019"

Der C++-Compiler unterstützt derzeit den OpenMP 2.0-Standard. Visual Studio 2019 bietet jetzt jedoch auch SIMD-Funktionalität. Um SIMD zu verwenden, kompilieren Sie mit der Option **/openmp:experimental.** Diese Option aktiviert sowohl die üblichen OpenMP-Funktionen als auch zusätzliche OpenMP-SIMD-Funktionen, die bei Verwendung des **Schalters /openmp** nicht verfügbar sind.

::: moniker-end

Anwendungen, die mit **/openmp** und **/clr** kompiliert werden, können nur in einem einzelnen Anwendungsdomänenprozess ausgeführt werden. Mehrere Anwendungsdomänen werden nicht unterstützt. Das heißt, wenn der`.cctor`Modulkonstruktor ( ) ausgeführt wird, erkennt er, ob der Prozess mit **/openmp**kompiliert wird und ob die App in eine nicht standardmäßige Laufzeit geladen wird. Weitere Informationen finden Sie unter [appdomain](../../cpp/appdomain.md), [/clr (Common Language Runtime Compilation)](clr-common-language-runtime-compilation.md)und [Initialisierung gemischter Assemblys](../../dotnet/initialization-of-mixed-assemblies.md).

Wenn Sie versuchen, eine App, die mit **/openmp** und **/clr** kompiliert wurde, in eine nicht standardmäßige Anwendungsdomäne zu laden, wird eine <xref:System.TypeInitializationException> Ausnahme außerhalb des Debuggers ausgelöst, und eine `OpenMPWithMultipleAppdomainsException` Ausnahme wird im Debugger ausgelöst.

Diese Ausnahmen können auch in den folgenden Situationen ausgelöst werden:

- Wenn Ihre Anwendung mit **/clr,** aber nicht mit **/openmp**kompiliert und in eine nicht standardmäßige Anwendungsdomäne geladen wird, enthält der Prozess eine Mit **/openmp**kompilierte App.

- Wenn Sie Ihre **/clr-App** an ein Dienstprogramm übergeben, z. B. [regasm.exe](/dotnet/framework/tools/regasm-exe-assembly-registration-tool), das seine Zielassemblys in eine nicht standardmäßige Anwendungsdomäne lädt.

Die Codezugriffssicherheit der Common Language Runtime funktioniert in OpenMP-Regionen nicht. Wenn Sie ein CLR-Codezugriffssicherheitsattribut außerhalb einer parallelen Region anwenden, ist es in der parallelen Region nicht wirksam.

Microsoft empfiehlt nicht, **/openmp-Apps** zu schreiben, die teilweise vertrauenswürdige Aufrufer zulassen. Verwenden Sie <xref:System.Security.AllowPartiallyTrustedCallersAttribute>keine oder CLR-Codezugriffssicherheitsattribute.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>So legen Sie diese Compileroption in der Visual Studio-Entwicklungsumgebung fest

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** des Projekts. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Erweitern Sie die Eigenschaftenseite **"Konfigurationseigenschaften** > **C/C++** > **Language".**

1. Ändern Sie die **OpenMP** Support-Eigenschaft.

### <a name="to-set-this-compiler-option-programmatically"></a>So legen Sie diese Compileroption programmgesteuert fest

- Siehe <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.OpenMP%2A>.

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt einige der Auswirkungen des Threadpoolstarts im Vergleich zur Verwendung des Threadpools nach dem Start. Unter der Annahme eines x64, Single-Core, Dual-Prozessor, dauert der Thread-Pool etwa 16 ms, um zu starten. Danach gibt es wenig zusätzliche Kosten für den Thread-Pool.

Wenn Sie mit **/openmp**kompilieren, wird der zweite Aufruf von test2 nie länger ausgeführt als wenn Sie mit **/openmp-** kompilieren, da kein Threadpoolstart gestartet wird. Bei einer Million Iterationen ist die **/openmp-Version** schneller als die **/openmp-Version** für den zweiten Aufruf von test2. Bei 25 Iterationen registrieren sowohl **/openmp- als** **auch /openmp-Versionen** weniger als die Uhrgranularität.

Wenn Sie nur eine Schleife in Ihrer Anwendung haben und sie in weniger als 15 ms läuft (angepasst an den ungefähren Overhead auf Ihrem Computer), ist **/openmp** möglicherweise nicht geeignet. Wenn es höher ist, sollten Sie die Verwendung von **/openmp**in Betracht ziehen.

```cpp
// cpp_compiler_options_openmp.cpp
#include <omp.h>
#include <stdio.h>
#include <stdlib.h>
#include <windows.h>

volatile DWORD dwStart;
volatile int global = 0;

double test2(int num_steps) {
   int i;
   global++;
   double x, pi, sum = 0.0, step;

   step = 1.0 / (double) num_steps;

   #pragma omp parallel for reduction(+:sum) private(x)
   for (i = 1; i <= num_steps; i++) {
      x = (i - 0.5) * step;
      sum = sum + 4.0 / (1.0 + x*x);
   }

   pi = step * sum;
   return pi;
}

int main(int argc, char* argv[]) {
   double   d;
   int n = 1000000;

   if (argc > 1)
      n = atoi(argv[1]);

   dwStart = GetTickCount();
   d = test2(n);
   printf_s("For %d steps, pi = %.15f, %d milliseconds\n", n, d, GetTickCount() - dwStart);

   dwStart = GetTickCount();
   d = test2(n);
   printf_s("For %d steps, pi = %.15f, %d milliseconds\n", n, d, GetTickCount() - dwStart);
}
```

## <a name="see-also"></a>Siehe auch

[MSVC-Compileroptionen](compiler-options.md) \
[MSVC Compiler-Befehlszeilensyntax](compiler-command-line-syntax.md) \
[OpenMP in MSVC](../../parallel/openmp/openmp-in-visual-cpp.md)
