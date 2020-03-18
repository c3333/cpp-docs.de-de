---
title: 'Gewusst wie: Festlegen von Codeanalyseeigenschaften für C/C++-Projekte'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.propertypages.native
- VC.Project.VCCLCompilerTool.EnablePrefast
- VC.Project.VCFxCopTool.EnablePREfast
- VC.Project.VCFxCopTool.IgnoreGeneratedCode
helpviewer_keywords:
- properties, C/C++ Code Analysis
- properties, Code Analysis
- code analysis properties
- C/C++ code analysis properties
ms.assetid: 7af52097-6d44-4785-9b9f-43b7a7d447d7
ms.openlocfilehash: 0f1f5b18255c9d39c2922c5c4f049f1cbe40d37e
ms.sourcegitcommit: 7bea0420d0e476287641edeb33a9d5689a98cb98
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/17/2020
ms.locfileid: "79467201"
---
# <a name="how-to-set-code-analysis-properties-for-cc-projects"></a>Gewusst wie: Festlegen von Codeanalyseeigenschaften für C/C++-Projekte

Sie können konfigurieren, welche Regeln das Code Analysetool verwendet, um den Code in jeder Konfiguration des Projekts zu analysieren. Außerdem können Sie die Code Analyse weiterleiten, um Warnungen aus dem Code zu unterdrücken, der von einem Drittanbieter Tool generiert und Ihrem Projekt hinzugefügt wurde.

## <a name="code-analysis-property-page"></a>Code Analyse (Eigenschaften Seite)

Die Eigenschaften Seite " **Code Analyse** " enthält alle Konfigurationseinstellungen für die Code Analyse für ein MSBuild-Projekt. Um die Eigenschaften Seite Code Analyse für ein Projekt in **Projektmappen-Explorer**zu öffnen, klicken Sie mit der rechten Maustaste auf das Projekt, und klicken Sie dann auf **Eigenschaften**. Erweitern Sie als nächstes **Konfigurations Eigenschaften** , und wählen Sie die Registerkarte **Code Analyse** aus.

## <a name="project-configuration-and-platform"></a>Projekt Konfiguration und Plattform

Mithilfe der **Konfigurations** Liste und der **Platt Form** Liste am oberen Rand des Fensters können Sie unterschiedliche Code Analyse Einstellungen auf verschiedene Projekt Konfigurationen und Platt Form Kombinationen anwenden. Beispielsweise können Sie die Code Analyse weiterleiten, um einen Satz von Regeln auf das Projekt für Debugbuilds und einen anderen Satz für Releasebuilds anzuwenden.

## <a name="enabling-code-analysis"></a>Aktivieren der Code Analyse

Sie können die Code Analyse für Ihr Projekt aktivieren, indem Sie die Optionen " **Microsoft-Code Analyse aktivieren** " und " **clang-bereinigen" aktivieren** und dann konfigurieren, ob Sie auf dem Build ausgeführt werden, indem Sie **Code Analyse beim Build aktivieren**auswählen. In Kombination mit der **Konfigurations** Liste können Sie z. b. entscheiden, die Code Analyse für Debugbuilds zu deaktivieren und für Releasebuilds zu aktivieren.

Die Code Analyse soll Sie dabei unterstützen, die Qualität Ihres Codes zu verbessern und häufige Fehler zu vermeiden. Daher sollten Sie sorgfältig überlegen, ob die Code Analyse deaktiviert werden soll. Es ist in der Regel besser, Regelsätze, einzelne Regeln oder einzelne Überprüfungen zu deaktivieren, die nicht auf Ihr Projekt angewendet werden sollen.

## <a name="cmake-configuration"></a>Cmake-Konfiguration

Ändern Sie in cmake-Projekten den Wert der `enableMicrosoftCodeAnalysis`-und `enableClangTidyCodeAnalysis` Schlüssel innerhalb `CMakeSettings.json`, um die Code Analyse zu aktivieren oder zu deaktivieren. Weitere Informationen finden [Sie unter Verwenden von clang-tidy in Visual Studio](../code-quality/clang-tidy.md) .

## <a name="see-also"></a>Weitere Informationen

- [Analysieren der Qualität von verwaltetem Code](/visualstudio/code-quality/code-analysis-for-managed-code-overview)
- [Codeanalyse für C/C++-Warnungen](../code-quality/code-analysis-for-c-cpp-warnings.md)
- [Verwenden von Regelsätzen zum angeben C++ der Regeln, die ausgeführt werden sollen](using-rule-sets-to-specify-the-cpp-rules-to-run.md)
- [Verwenden von clang-tidy](../code-quality/clang-tidy.md)
