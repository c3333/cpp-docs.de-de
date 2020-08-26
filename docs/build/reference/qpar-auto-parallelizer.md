---
title: /Qpar (Automatische Parallelisierung)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.EnableParallelCodeGeneration
ms.assetid: 33ecf49d-c0d5-4f34-bce3-84ff03f38918
ms.openlocfilehash: effe1ad7799022ea85184513de1dc48c72d6bfcb
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88839438"
---
# <a name="qpar-auto-parallelizer"></a>/Qpar (Automatische Parallelisierung)

Ermöglicht der [automatischen parallelisierungsfunktion](../../parallel/auto-parallelization-and-auto-vectorization.md) des Compilers, Schleifen in Ihrem Code automatisch zu parallelisieren.

## <a name="syntax"></a>Syntax

```
/Qpar
```

## <a name="remarks"></a>Bemerkungen

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
[Vektorisierung in nativem Code in Visual Studio](/archive/blogs/nativeconcurrency/auto-vectorizer-in-visual-studio-2012-overview)
