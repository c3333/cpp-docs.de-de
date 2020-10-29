---
title: /OpenMP (OpenMP-Unterstützung aktivieren)
ms.date: 04/15/2019
f1_keywords:
- /openmp
- VC.Project.VCCLCompilerTool.OpenMP
helpviewer_keywords:
- /openmp compiler option [C++]
- -openmp compiler option [C++]
ms.assetid: 9082b175-18d3-4378-86a7-c0eb95664e13
ms.openlocfilehash: 6bd1ffcd9b21bfe22ed9424ee77edf43100abf6c
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "92921229"
---
# <a name="openmp-enable-openmp-support"></a>/OpenMP (OpenMP-Unterstützung aktivieren)

Bewirkt, dass der Compiler [`#pragma omp`](../../preprocessor/omp.md) Direktiven zur Unterstützung von OpenMP verarbeitet.

## <a name="syntax"></a>Syntax

::: moniker range=">= msvc-160"

> **/OpenMP** \[ **:**__experimentell__ ]

::: moniker-end

::: moniker range="<= msvc-150"

> **/OpenMP**

::: moniker-end

## <a name="remarks"></a>Hinweise

`#pragma omp` wird verwendet, um [Direktiven](../../parallel/openmp/reference/openmp-directives.md) und [Klauseln](../../parallel/openmp/reference/openmp-clauses.md)anzugeben. Wenn **/OpenMP** nicht in einer Kompilierung angegeben ist, ignoriert der Compiler OpenMP-Klauseln und-Direktiven. [OpenMP-Funktions](../../parallel/openmp/reference/openmp-functions.md) Aufrufe werden vom Compiler verarbeitet, auch wenn **/OpenMP** nicht angegeben ist.

::: moniker range=">= msvc-160"

Der C++-Compiler unterstützt derzeit den OpenMP 2,0-Standard. Visual Studio 2019 bietet jedoch jetzt auch SIMD-Funktionen. Kompilieren Sie mit der Option **/OpenMP: experimental** , um SIMD zu verwenden. Diese Option ermöglicht sowohl die üblichen OpenMP-Features als auch zusätzliche OpenMP SIMD-Funktionen, die bei Verwendung des **/OpenMP** -Schalters nicht verfügbar sind.

::: moniker-end

Anwendungen, die mit **/OpenMP** und **/CLR** kompiliert werden, können nur in einem einzelnen Anwendungs Domänen Prozess ausgeführt werden. Mehrere Anwendungs Domänen werden nicht unterstützt. Das heißt, wenn der Modulkonstruktor ( `.cctor` ) ausgeführt wird, erkennt er, ob der Prozess mit **/OpenMP** kompiliert wird und ob die app in eine nicht standardmäßige Laufzeit geladen wird. Weitere Informationen finden Sie unter [AppDomain](../../cpp/appdomain.md), [/CLR (Common Language Runtime-Kompilierung)](clr-common-language-runtime-compilation.md)und [Initialisierung gemischter](../../dotnet/initialization-of-mixed-assemblies.md)Assemblys.

Wenn Sie versuchen, eine mit " **/OpenMP** " und " **/CLR** " kompilierte app in eine nicht standardmäßige Anwendungsdomäne zu laden, wird eine- <xref:System.TypeInitializationException> Ausnahme außerhalb des Debuggers ausgelöst, und `OpenMPWithMultipleAppdomainsException` im Debugger wird eine-Ausnahme ausgelöst.

Diese Ausnahmen können auch in den folgenden Situationen ausgelöst werden:

- Wenn Ihre Anwendung mit **/CLR** , aber nicht mit **/OpenMP** kompiliert wird, wird Sie in eine nicht standardmäßige Anwendungsdomäne geladen, wobei der Prozess eine mit **/OpenMP** kompilierte app enthält.

- Wenn Sie Ihre **/CLR** -APP an ein-Hilfsprogramm übergeben, z. b. [regasm.exe](/dotnet/framework/tools/regasm-exe-assembly-registration-tool), das die Zielassemblys in eine nicht standardmäßige Anwendungsdomäne lädt.

Die Code Zugriffssicherheit des Common Language Runtime funktioniert nicht in den OpenMP-Regionen. Wenn Sie ein Attribut für die CLR-Code Zugriffssicherheit außerhalb eines parallelen Bereichs anwenden, ist es im parallelen Bereich nicht wirksam.

Microsoft empfiehlt nicht, **/OpenMP** -apps zu schreiben, die teilweise vertrauenswürdige Aufrufer zulassen. Verwenden Sie weder noch die Attribute für die <xref:System.Security.AllowPartiallyTrustedCallersAttribute> CLR-Code Zugriffssicherheit.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>So legen Sie diese Compileroption in der Visual Studio-Entwicklungsumgebung fest

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** des Projekts. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Erweitern Sie die **Eigenschaften Seite Konfigurations Eigenschaften**  >  **C/C++-**  >  **Sprache** .

1. Ändern Sie die Eigenschaft **OpenMP-Unterstützung** .

### <a name="to-set-this-compiler-option-programmatically"></a>So legen Sie diese Compileroption programmgesteuert fest

- Siehe <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.OpenMP%2A>.

## <a name="example"></a>Beispiel

Im folgenden Beispiel werden einige der Auswirkungen des Thread Pool Starts und die Verwendung des Thread Pools nach dem Starten veranschaulicht. Bei einem x64-, Single Core-und Dual-Prozessor benötigt der Thread Pool ungefähr 16 ms, um zu starten. Danach fallen für den Thread Pool wenig zusätzliche Kosten an.

Wenn Sie mit **/OpenMP** kompilieren, wird der zweite test2-Befehl nie länger ausgeführt, als wenn Sie mit **/OpenMP-** kompilieren, da kein Thread Pool Start vorhanden ist. Bei einer Million Iterationen ist die **/OpenMP** -Version schneller als die **/OpenMP-** -Version für den zweiten test2-Rückruf. Bei 25 Iterationen registrieren sowohl die **/OpenMP-** -als auch die **/OpenMP** -Version weniger als die Zeit Granularität.

Wenn Sie nur eine Schleife in Ihrer Anwendung haben und Sie in weniger als 15 MS ausgeführt wird (entsprechend dem ungefähren mehr Aufwand auf dem Computer), ist **/OpenMP** möglicherweise nicht geeignet. Wenn Sie höher ist, sollten Sie die Verwendung von **/OpenMP** in Erwägung gezogen.

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
[MSVC-CompilerCommand-Line Syntax](compiler-command-line-syntax.md) \
[OpenMP in MSVC](../../parallel/openmp/openmp-in-visual-cpp.md)
