---
title: /Qpar (Automatische Parallelisierung)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.EnableParallelCodeGeneration
ms.assetid: 33ecf49d-c0d5-4f34-bce3-84ff03f38918
ms.openlocfilehash: 18aaa1dc678ca2c73f9fad6c016aa40cfa95982b
ms.sourcegitcommit: 31a443c9998cf5cfbaff00fcf815b133f55b2426
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/14/2020
ms.locfileid: "86373800"
---
# <a name="qpar-auto-parallelizer"></a>/Qpar (Automatische Parallelisierung)

Ermöglicht der [automatischen parallelisierungsfunktion](../../parallel/auto-parallelization-and-auto-vectorization.md) des Compilers, Schleifen in Ihrem Code automatisch zu parallelisieren.

## <a name="syntax"></a>Syntax

```
/Qpar
```

## <a name="remarks"></a>Hinweise

Wenn der Compiler Schleifen im Code automatisch parallelisiert, wird die Berechnung auf mehrere Prozessorkerne verteilt. Eine-Schleife wird nur parallelisiert, wenn der Compiler feststellt, dass dies zulässig ist und die Parallelisierung die Leistung verbessert.

Die- `#pragma loop()` Direktiven sind verfügbar, damit der Optimierer bestimmte Schleifen parallelisieren können. Weitere Informationen finden Sie unter [Schleife](../../preprocessor/loop.md).

Informationen zum Aktivieren von Ausgabemeldungen für die automatische Parallelisierung finden Sie unter [/QPAR-Report (Auto-parallelizer Reporting Level)](qpar-report-auto-parallelizer-reporting-level.md).

### <a name="to-set-the-qpar-compiler-option-in-visual-studio"></a>So legen Sie die/QPAR-Compileroption in Visual Studio fest

1. Öffnen Sie im **Projektmappen-Explorer**das Kontextmenü für das Projekt, und wählen Sie **Eigenschaften**aus.

1. Wählen Sie im Dialogfeld **Eigenschaften Seiten** unter **C/C++** die Option **Befehlszeile**aus.

1. Geben Sie im Feld **zusätzliche Optionen** ein `/Qpar` .

### <a name="to-set-the-qpar-compiler-option-programmatically"></a>So legen Sie die/QPAR-Compileroption Programm gesteuert fest

- Verwenden Sie hierzu das Codebeispiel unter <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Weitere Informationen

[/Q-Optionen (Vorgänge auf niedriger Ebene)](q-options-low-level-operations.md)<br/>
[/QPAR-Report (Berichts Ebene für die automatische Parallelisierung)](qpar-report-auto-parallelizer-reporting-level.md)<br/>
[MSVC-Compileroptionen](compiler-options.md)<br/>
[MSVC-compilerbefehlszeilensyntax](compiler-command-line-syntax.md)<br/>
[#pragma-Schleife ()](../../preprocessor/loop.md)<br/>
[Vektorisierung in nativem Code in Visual Studio](https://docs.microsoft.com/archive/blogs/nativeconcurrency/auto-vectorizer-in-visual-studio-2012-overview)
