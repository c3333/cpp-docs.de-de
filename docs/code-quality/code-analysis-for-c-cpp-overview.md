---
title: Übersicht über die Codeanalyse für C/C++
ms.date: 04/28/2018
ms.topic: conceptual
helpviewer_keywords:
- annotations, code analysis
- build integration, code analysis
- C/C++ code analysis
- IDE, code analysis
- pragma directive, code analysis
- code analysis, C/C++
- code analysis tool
- command line, code analysis
- C++, code analysis
- check-in policies, code analysis
- '#pragma directives, code analysis'
- C, code analysis
ms.assetid: 81f0c9e8-f471-4de5-aac4-99db336a8809
ms.openlocfilehash: e5f5b75057985dc769c8f1ab84765d628dc42fcc
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/12/2020
ms.locfileid: "90040301"
---
# <a name="code-analysis-for-cc-overview"></a>Übersicht über die Codeanalyse für C/C++

Das c/C++-Code Analysetool enthält Informationen zu möglichen Fehlern in Ihrem c/C++-Quellcode. Zu den Codierungsfehlern, die das Tool am häufigsten findet, zählen Pufferüberläufe, nicht initialisierter Speicher, Dereferenzierungen von NULL-Zeigern sowie Speicher- und Ressourcenverluste. Das Tool kann auch Überprüfungen des [C++ Core Guidelines](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md)ausführen.

## <a name="ide-integrated-development-environment-integration"></a>Integration der IDE (integrierte Entwicklungsumgebung)

Das Code Analysetool ist vollständig in die Visual Studio-IDE integriert.

Während des Buildprozesses werden alle für den Quellcode generierten Warnungen in der Fehlerliste angezeigt. Sie können dadurch zu den Quellcodebestandteilen navigieren, die die Warnung ausgelöst haben, und zusätzliche Informationen zu den Gründen sowie mögliche Lösungen für die Probleme abrufen.

## <a name="command-line-support"></a>Befehlszeilen Unterstützung

Sie können das Analysetool auch über die Befehlszeile verwenden, wie im folgenden Beispiel gezeigt:

```cmd
C:\>cl /analyze Sample.cpp
```

**Visual Studio 2017 Version 15,7 und höher:** Sie können das Tool in der Befehlszeile mit jedem Buildsystem ausführen, einschließlich cmake.

## <a name="pragma-support"></a>#pragma Unterstützung

Sie können die- `#pragma` Direktive verwenden, um Warnungen als Fehler zu behandeln, Warnungen zu aktivieren oder zu deaktivieren und Warnungen für einzelne Codezeilen zu unterdrücken. Weitere Informationen finden Sie unter [Pragma-Direktiven und das __Pragma-Schlüsselwort](/cpp/preprocessor/pragma-directives-and-the-pragma-keyword).

## <a name="annotation-support"></a>Unterstützung der Anmerkung

Mithilfe von Anmerkungen wird die Codeanalyse genauer. Sie enthalten zusätzliche Informationen zu Vorabbedingungen und nachträglichen Bedingungen für Funktionsparameter und Rückgabetypen. Weitere Informationen finden Sie unter [Verwenden von Sal-Anmerkungen zum Reduzieren von C/C++-Code Fehlern](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md).

## <a name="run-analysis-tool-as-part-of-check-in-policy"></a>Ausführen des Analysetools im Rahmen einer Eincheckrichtlinie

Möglicherweise möchten Sie festlegen, dass beim Quellcode-Check-In stets bestimmte Richtlinien beachtet werden müssen. Insbesondere sollten Sie sicherstellen, dass die Analyse im Rahmen des aktuellen lokalen Builds durchgeführt wurde. Weitere Informationen zum Aktivieren einer Eincheck Richtlinie für die Code Analyse finden Sie unter [Erstellen und Verwenden von Eincheck Richtlinien für die Code Analyse](/visualstudio/code-quality/how-to-create-or-update-standard-code-analysis-check-in-policies).

## <a name="team-build-integration"></a>Team Build-Integration

Sie können die integrierten Funktionen des Buildsystems verwenden, um das Code Analysetool als Schritt des Azure devops-Buildprozesses auszuführen. Weitere Informationen finden Sie unter [Azure Pipelines](/azure/devops/pipelines/index).

## <a name="see-also"></a>Weitere Informationen

- [Schnellstart: Code Analyse für C/C++](quick-start-code-analysis-for-c-cpp.md)
- [Exemplarische Vorgehensweise: Analysieren von C/C++-Code auf Fehler](walkthrough-analyzing-c-cpp-code-for-defects.md)
- [Code Analyse für C/C++-Warnungen](code-analysis-for-c-cpp-warnings.md)
- [Verwenden der Überprüfungen für C++ Core Guidelines](using-the-cpp-core-guidelines-checkers.md)
- [C++ Core Guidelines Checker-Referenz](code-analysis-for-cpp-corecheck.md)
- [Verwenden von Regelsätzen zum Angeben der C++ Regeln, die ausgeführt werden sollen](using-rule-sets-to-specify-the-cpp-rules-to-run.md)
- [Analysieren der Treiber Qualität mithilfe von Code Analyse Tools](/windows-hardware/drivers/develop/analyzing-driver-quality-by-using-code-analysis-tools)
- [Codeanalyse für Treiberwarnungen](/windows-hardware/drivers/devtest/prefast-for-drivers-warnings)
