---
title: Verwenden von Regelsätzen zum Festlegen von C++-Regeln für die Ausführung
ms.date: 04/28/2018
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.rulesets.native
ms.openlocfilehash: 5cf0f88c6937f4c1609a29fd618af0fdadad4437
ms.sourcegitcommit: 7bea0420d0e476287641edeb33a9d5689a98cb98
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/17/2020
ms.locfileid: "79467120"
---
# <a name="use-rule-sets-to-specify-the-c-rules-to-run"></a>Verwenden von Regelsätzen zum angeben C++ der Regeln, die ausgeführt werden sollen

In Visual Studio können Sie einen benutzerdefinierten *Regelsatz* erstellen und ändern, um bestimmte Projektanforderungen zu erfüllen, die mit der Code Analyse verknüpft sind. Die Standardregel Sätze werden in `%VSINSTALLDIR%\Team Tools\Static Analysis Tools\Rule Sets`gespeichert.

**Visual Studio 2017 Version 15,7 und höher:** Sie können benutzerdefinierte Regelsätze mit einem beliebigen Text-Editor erstellen und diese in Befehlszeilenbuilds anwenden, unabhängig davon, welches Buildsystem Sie verwenden. Weitere Informationen finden Sie unter [/analyze: RuleSet](/cpp/build/reference/analyze-code-analysis).

Um einen benutzerdefinierten C++ Regelsatz in Visual Studio zu erstellen, mussC++ ein C/-Projekt in der Visual Studio-IDE geöffnet sein. Öffnen Sie dann einen Standardregel Satz im Regelsatz-Editor, und fügen Sie bestimmte Regeln hinzu bzw. entfernen Sie Sie, und ändern Sie optional die Aktion, die auftritt, wenn die Code Analyse festlegt, dass eine Regel verletzt wurde.

Zum Erstellen eines neuen benutzerdefinierten Regelsatzes speichern Sie diesen unter einem neuen Dateinamen. Der benutzerdefinierte Regelsatz wird dem Projekt automatisch zugewiesen.

## <a name="to-create-a-custom-rule-from-a-single-existing-rule-set"></a>So erstellen Sie eine benutzerdefinierte Regel aus einem einzelnen vorhandenen Regelsatz

1. Öffnen Sie im Projektmappen-Explorer das Kontextmenü für das Projekt, und wählen Sie dann **Eigenschaften**aus.

1. Wählen Sie auf der Registerkarte **Eigenschaften** die Option **Code Analyse**aus.

1. Führen Sie in der Dropdown Liste **Regelsatz** einen der folgenden Schritte aus:

   - Wählen Sie den Regelsatz aus, den Sie anpassen möchten.

     \- oder –

   - Wählen Sie **\<durchsuchen... >** , um einen vorhandenen Regelsatz anzugeben, der nicht in der Liste enthalten ist.

1. Wählen Sie **Öffnen** aus, um die Regeln im Regelsatz-Editor anzuzeigen.

## <a name="to-modify-a-rule-set-in-the-rule-set-editor"></a>So ändern Sie einen Regelsatz im Regelsatz-Editor

- Um den anzeigen amen des Regelsatzes zu ändern, wählen Sie im Menü **Ansicht** die Option **Eigenschaften Fenster**aus. Geben Sie den anzeigen Amen in das Feld **Name** ein. Der Anzeigename kann sich vom Dateinamen unterscheiden.

- Wenn Sie einem benutzerdefinierten Regelsatz alle Regeln der Gruppe hinzufügen möchten, aktivieren Sie das Kontrollkästchen für die Gruppe. Wenn Sie alle Regeln der Gruppe entfernen möchten, deaktivieren Sie das Kontrollkästchen.

- Wenn Sie dem benutzerdefinierten Regelsatz eine bestimmte Regel hinzufügen möchten, aktivieren Sie das Kontrollkästchen für die Regel. Wenn Sie die Regel aus dem Regelsatz entfernen möchten, deaktivieren Sie das zugehörige Kontrollkästchen.

- Um die Aktion zu ändern, die durchgeführt wird, wenn eine Regel in einer Code Analyse verletzt wird, wählen Sie das Feld **Aktion** für die Regel aus, und wählen Sie dann einen der folgenden Werte aus:

     **Warnung** : generiert eine Warnung.

     **Fehler** -generiert einen Fehler.

     **Info** : generiert eine Meldung.

     **Keine** : deaktiviert die Regel. Diese Aktion ist mit der Aktion identisch, die beim Entfernen der Regel aus dem Regelsatz ausgeführt wird.

## <a name="to-group-filter-or-change-the-fields-in-the-rule-set-editor-by-using-the-rule-set-editor-toolbar"></a>So gruppieren, filtern oder ändert Sie Felder auf der Symbolleiste des Regelsatz-Editors

- Um die Regeln in allen Gruppen zu erweitern, wählen Sie **Alle erweitern**aus.

- Um die Regeln in allen Gruppen zu reduzieren, wählen Sie **alle**reduzieren aus.

- Wenn Sie das Feld ändern möchten, nach dem Regeln gruppiert werden, wählen Sie das Feld aus der Liste **Gruppieren nach** aus. Wählen Sie **\<keine >** aus, um die Regeln nicht gruppiert anzuzeigen.

- Wählen Sie **Spaltenoptionen**aus, um Felder in Regel Spalten hinzuzufügen oder zu entfernen.

- Um Regeln auszublenden, die nicht für die aktuelle Projekt Mappe gelten, wählen Sie **Regeln ausblenden aus, die nicht auf die aktuelle**Projekt Mappe angewendet werden.

- Wenn Sie zwischen dem anzeigen und Ausblenden von Regeln wechseln möchten, denen die Fehler Aktion zugewiesen ist, wählen Sie **Regeln anzeigen, die Code Analysefehler generieren können**.

- Wenn Sie zwischen dem anzeigen und Ausblenden von Regeln wechseln möchten, denen die Warnungs Aktion zugewiesen ist, wählen Sie **Regeln anzeigen, die Code Analyse Warnungen generieren können**aus.

- Wenn Sie zwischen dem anzeigen und Ausblenden von Regeln wechseln möchten, denen die Aktion **keine** zugewiesen ist, wählen Sie **nicht aktivierte Regeln anzeigen**aus.

- Um dem aktuellen Regelsatz Microsoft-Standardregel Sätze hinzuzufügen oder daraus zu entfernen, wählen Sie untergeordnete **Regelsätze hinzufügen oder entfernen**aus.

## <a name="to-create-a-rule-set-in-a-text-editor"></a>So erstellen Sie einen Regelsatz in einem Text-Editor

Sie können einen benutzerdefinierten Regelsatz in einem Text-Editor erstellen, ihn an einem beliebigen Speicherort mit einer `.ruleset`-Erweiterung speichern und mit der [/analyze: RuleSet](/cpp/build/reference/analyze-code-analysis) -Compileroption anwenden.

Das folgende Beispiel zeigt eine grundlegende Regel Satz Datei, die Sie als Ausgangspunkt verwenden können:

::: moniker range="<=vs-2017"

```xml
<?xml version="1.0" encoding="utf-8"?>
<RuleSet Name="New Rule Set" Description=" " ToolsVersion="15.0">
  <Rules AnalyzerId="Microsoft.Analyzers.NativeCodeAnalysis" RuleNamespace="Microsoft.Rules.Native">
    <Rule Id="C6001" Action="Warning" />
    <Rule Id="C26494" Action="Warning" />
  </Rules>
</RuleSet>
```

::: moniker-end

::: moniker range=">=vs-2019"

```xml
<?xml version="1.0" encoding="utf-8"?>
<RuleSet Name="New Rule Set" Description=" " ToolsVersion="16.0">
  <Rules AnalyzerId="Microsoft.Analyzers.NativeCodeAnalysis" RuleNamespace="Microsoft.Rules.Native">
    <Rule Id="C6001" Action="Warning" />
    <Rule Id="C26494" Action="Warning" />
  </Rules>
</RuleSet>
```

::: moniker-end
