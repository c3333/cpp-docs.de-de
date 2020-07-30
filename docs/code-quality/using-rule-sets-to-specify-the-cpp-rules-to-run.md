---
title: Verwenden von Regelsätzen zum Festlegen von C++-Regeln für die Ausführung
ms.date: 07/27/2020
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.rulesets.native
ms.openlocfilehash: b132400485c041b96e81736bcda04922b2cda88c
ms.sourcegitcommit: 6e55aeb538b1c39af754f82d6f7738a18f5aa031
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/29/2020
ms.locfileid: "87389817"
---
# <a name="use-rule-sets-to-specify-the-c-rules-to-run"></a>Verwenden von Regelsätzen zum Festlegen von C++-Regeln für die Ausführung

In Visual Studio können Sie einen benutzerdefinierten *Regelsatz* erstellen und ändern, um bestimmte Projektanforderungen zu erfüllen, die mit der Code Analyse verknüpft sind. Die Standardregel Sätze werden in gespeichert *`%VSINSTALLDIR%\Team Tools\Static Analysis Tools\Rule Sets`* .

**Visual Studio 2017 Version 15,7 und höher:** Sie können benutzerdefinierte Regelsätze mit einem beliebigen Text-Editor erstellen und diese in Befehlszeilenbuilds anwenden, unabhängig davon, welches Buildsystem Sie verwenden. Weitere Informationen finden Sie unter [`/analyze:ruleset`](/cpp/build/reference/analyze-code-analysis).

Ein C/C++-Projekt muss in der Visual Studio-IDE geöffnet sein, um einen benutzerdefinierten C++-Regelsatz in Visual Studio zu erstellen. Anschließend öffnen Sie einen Standardregel Satz im Regelsatz-Editor und fügen dann bestimmte Regeln hinzu bzw. entfernen Sie. Optional können Sie auch die Aktion ändern, die auftritt, wenn die Code Analyse bestimmt, dass eine Regel verletzt wurde.

Zum Erstellen eines neuen benutzerdefinierten Regelsatzes speichern Sie diesen unter einem neuen Dateinamen. Der benutzerdefinierte Regelsatz wird dem Projekt automatisch zugewiesen.

## <a name="to-create-a-custom-rule-from-a-single-existing-rule-set"></a>So erstellen Sie eine benutzerdefinierte Regel aus einem einzelnen vorhandenen Regelsatz

::: moniker range="<=vs-2017"

1. Öffnen Sie in Projektmappen-Explorer das Kontextmenü für das Projekt, und wählen Sie dann **Eigenschaften**aus.

1. Wählen Sie im Dialogfeld Eigenschaften **Seiten** die **Eigenschaften** > Seite allgemeine **Code Analyse** für die Konfiguration aus > **General** .

1. Führen Sie in der Dropdown Liste **Regelsatz** einen der folgenden Schritte aus:

   - Wählen Sie den Regelsatz aus, den Sie anpassen möchten.

     \- oder –

   - **\<Browse...>** Geben Sie einen vorhandenen Regelsatz an, der nicht in der Liste enthalten ist.

1. Wählen Sie **Öffnen** aus, um die Regeln im Regelsatz-Editor anzuzeigen.

::: moniker-end
::: moniker range=">=vs-2019"

1. Öffnen Sie in Projektmappen-Explorer das Kontextmenü für das Projekt, und wählen Sie dann **Eigenschaften**aus.

1. Wählen Sie im Dialogfeld Eigenschaften **Seiten** die **Eigenschaften Seite Konfigurations Eigenschaften** > **Code Analyse** > **Microsoft** aus.

1. Führen Sie in der Dropdown Liste **aktive Regeln** einen der folgenden Schritte aus:

   - Wählen Sie den Regelsatz aus, den Sie anpassen möchten.

     \- oder –

   - **\<Browse...>** Geben Sie einen vorhandenen Regelsatz an, der nicht in der Liste enthalten ist.

1. Wählen Sie **Öffnen** aus, um die Regeln im Regelsatz-Editor anzuzeigen.

::: moniker-end

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

- Wenn Sie das Feld ändern möchten, nach dem Regeln gruppiert werden, wählen Sie das Feld aus der Liste **Gruppieren nach** aus. Um die Regeln nicht gruppiert anzuzeigen, wählen Sie aus **\<None>** .

- Wählen Sie **Spaltenoptionen**aus, um Felder in Regel Spalten hinzuzufügen oder zu entfernen.

- Um Regeln auszublenden, die nicht für die aktuelle Projekt Mappe gelten, wählen Sie **Regeln ausblenden aus, die nicht auf die aktuelle**Projekt Mappe angewendet werden.

- Wenn Sie zwischen dem anzeigen und Ausblenden von Regeln wechseln möchten, denen die Fehler Aktion zugewiesen ist, wählen Sie **Regeln anzeigen, die Code Analysefehler generieren können**.

- Wenn Sie zwischen dem anzeigen und Ausblenden von Regeln wechseln möchten, denen die Warnungs Aktion zugewiesen ist, wählen Sie **Regeln anzeigen, die Code Analyse Warnungen generieren können**aus.

- Wenn Sie zwischen dem anzeigen und Ausblenden von Regeln wechseln möchten, denen die Aktion **keine** zugewiesen ist, wählen Sie **nicht aktivierte Regeln anzeigen**aus.

- Um dem aktuellen Regelsatz Microsoft-Standardregel Sätze hinzuzufügen oder daraus zu entfernen, wählen Sie untergeordnete **Regelsätze hinzufügen oder entfernen**aus.

## <a name="to-create-a-rule-set-in-a-text-editor"></a>So erstellen Sie einen Regelsatz in einem Text-Editor

Sie können einen benutzerdefinierten Regelsatz in einem Text-Editor erstellen, ihn an einem beliebigen Speicherort mit einer *`.ruleset`* -Erweiterung speichern und mit der- [`/analyze:ruleset`](/cpp/build/reference/analyze-code-analysis) Compileroption anwenden.

Das folgende Beispiel zeigt eine grundlegende Regel Satz Datei, die Sie als Ausgangspunkt verwenden können:

```xml
<?xml version="1.0" encoding="utf-8"?>
<RuleSet Name="New Rule Set" Description="New rules to apply." ToolsVersion="10.0">
  <Rules AnalyzerId="Microsoft.Analyzers.NativeCodeAnalysis" RuleNamespace="Microsoft.Rules.Native">
    <Rule Id="C6001" Action="Warning" />
    <Rule Id="C26494" Action="Warning" />
  </Rules>
</RuleSet>
```

## <a name="ruleset-schema"></a>RuleSet-Schema

Das folgende RuleSet-Schema beschreibt das XML-Schema einer RuleSet-Datei. Das RuleSet-Schema wird in gespeichert *`%VSINSTALLDIR%\Team Tools\Static Analysis Tools\Schemas\RuleSet.xsd`* . Sie können Sie verwenden, um eigene RuleSets Programm gesteuert zu erstellen oder um zu überprüfen, ob Ihre benutzerdefinierten RuleSets das richtige Format einhalten. Weitere Informationen finden Sie unter Gewusst [wie: Erstellen eines XML-Dokuments auf Grundlage eines XSD-Schemas](https://docs.microsoft.com/visualstudio/xml-tools/how-to-create-an-xml-document-based-on-an-xsd-schema?view=vs-2019).

```xml
<?xml version="1.0" encoding="utf-8"?>
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">

  <xs:annotation>
    <xs:documentation xml:lang="en">
            Visual Studio Code Analysis Rule Set Schema Definition Language.
            Copyright (c) Microsoft Corporation. All rights reserved.
        </xs:documentation>
  </xs:annotation>

  <!-- Every time this file changes, be sure to change the Validate method for the corresponding object in the code -->

  <xs:element name="RuleSet" type="TRuleSet">
  </xs:element>

  <xs:complexType name="TLocalization">
    <xs:all>
      <xs:element name="Name" type="TName" minOccurs="0" maxOccurs="1" />
      <xs:element name="Description" type="TDescription" minOccurs="0" maxOccurs="1" />
    </xs:all>
    <xs:attribute name="ResourceAssembly" type="TNonEmptyString" use="required" />
    <xs:attribute name="ResourceBaseName" type="TNonEmptyString" use="required" />
  </xs:complexType>

  <xs:complexType name="TRuleHintPaths">
    <xs:sequence>
      <xs:element name="Path" type="TNonEmptyString" minOccurs="0" maxOccurs="unbounded" />
    </xs:sequence>
  </xs:complexType>
  
  <xs:complexType name="TName">
    <xs:attribute name="Resource" type="TNonEmptyString" use="required" />
  </xs:complexType>

  <xs:complexType name="TDescription">
    <xs:attribute name="Resource" type="TNonEmptyString" use="required" />
  </xs:complexType>

  <xs:complexType name="TInclude">
    <xs:attribute name="Path" type="TNonEmptyString" use="required" />
    <xs:attribute name="Action" type="TIncludeAction" use="required" />
  </xs:complexType>

  <xs:complexType name="TIncludeAll">
    <xs:attribute name="Action" type="TIncludeAllAction" use="required" />
  </xs:complexType>

  <xs:complexType name="TRule">
    <xs:attribute name="Id" type="TNonEmptyString" use="required" />
    <xs:attribute name="Action" type="TRuleAction" use="required" />
  </xs:complexType>

  <xs:complexType name="TRules">
    <xs:sequence>
      <xs:element name="Rule" type="TRule" minOccurs="0" maxOccurs="unbounded" />
    </xs:sequence>
    <xs:attribute name="AnalyzerId" type="TNonEmptyString" use="required" />
    <xs:attribute name="RuleNamespace" type="TNonEmptyString" use="required" />
  </xs:complexType>

  <xs:complexType name="TRuleSet">
    <xs:sequence minOccurs="0" maxOccurs="1">
      <xs:element name="Localization" type="TLocalization" minOccurs="0" maxOccurs="1" />
      <xs:element name="RuleHintPaths" type="TRuleHintPaths" minOccurs="0" maxOccurs="1" />
      <xs:element name="IncludeAll" type="TIncludeAll" minOccurs="0" maxOccurs="1" />
      <xs:choice minOccurs="0" maxOccurs="unbounded">
        <xs:element name="Include" type="TInclude" minOccurs="0" maxOccurs="unbounded" />
        <xs:element name="Rules" type="TRules" minOccurs="0" maxOccurs="unbounded">
          <xs:unique name="UniqueRuleName">
            <xs:selector xpath="Rule" />
            <xs:field xpath="@Id" />
          </xs:unique>
        </xs:element>
      </xs:choice>
    </xs:sequence>
    <xs:attribute name="Name" type="TNonEmptyString" use="required" />
    <xs:attribute name="Description" type="xs:string" use="optional" />
    <xs:attribute name="ToolsVersion" type="TNonEmptyString" use="required" />
  </xs:complexType>

  <xs:simpleType name="TRuleAction">
    <xs:restriction base="xs:string">
      <xs:enumeration value="Error"/>
      <xs:enumeration value="Warning"/>
      <xs:enumeration value="Info"/>
      <xs:enumeration value="Hidden"/>
      <xs:enumeration value="None"/>
    </xs:restriction>
  </xs:simpleType>

  <xs:simpleType name="TIncludeAction">
    <xs:restriction base="xs:string">
      <xs:enumeration value="Error"/>
      <xs:enumeration value="Warning"/>
      <xs:enumeration value="Info"/>
      <xs:enumeration value="Hidden"/>
      <xs:enumeration value="None"/>
      <xs:enumeration value="Default"/>
    </xs:restriction>
  </xs:simpleType>

  <xs:simpleType name="TIncludeAllAction">
    <xs:restriction base="xs:string">
      <xs:enumeration value="Error"/>
      <xs:enumeration value="Warning"/>
      <xs:enumeration value="Info"/>
      <xs:enumeration value="Hidden"/>
    </xs:restriction>
  </xs:simpleType>

  <xs:simpleType name="TNonEmptyString">
    <xs:restriction base="xs:string">
      <xs:minLength value="1" />
    </xs:restriction>
  </xs:simpleType>
  
</xs:schema>

```

Details zum Schema Element:

| Schema-Element | BESCHREIBUNG |
|--------------------|--------------|
| `TLocalization` | Lokalisierungs Informationen einschließlich Name der RuleSet-Datei, Beschreibung der RuleSet-Datei, Name der Ressourcenassembly, die die lokalisierte Ressource enthält, und Basisname der lokalisierten Ressource |
| `TRuleHintPaths` | Dateipfade, die als Hinweise für die Suche nach RuleSet-Dateien verwendet werden |
| `TName` | Name der aktuellen RuleSet-Datei |
| `TDescription` | Beschreibung der aktuellen RuleSet-Datei |
| `TInclude` | Pfad zu einem eingeschlossenen RuleSet mit der Regel Aktion |
| `TIncludeAll` | Regel Aktion für alle Regeln |
| `TRule` | Regel-ID mit Regel Aktion |
| `TRules` | Sammlung von mindestens einer Regel |
| `TRuleSet` | Das RuleSet-Dateiformat, das aus Lokalisierungs Informationen, Regel Hinweis Pfaden, Informationen zu allen Informationen, Informationen zu Regeln, Informationen zum Namen, zur Beschreibung und Tools-Version besteht. |
| `TRuleAction` | Enumeration, die eine Regel Aktion beschreibt, z. b. Fehler, Warnung, Info, ausgeblendet oder keine |
| `TIncludeAction` | Enumeration, die eine Regel Aktion beschreibt, z. b. Fehler, Warnung, Info, ausgeblendet, keine oder Standard |
| `TIncludeAllAction` | Enumeration, die eine Regel Aktion beschreibt, z. b. einen Fehler, eine Warnung, eine Information oder eine verborgene |

Ein Beispiel für einen Regelsatz finden Sie unter so [Erstellen Sie einen Regelsatz in einem Text-Editor](#to-create-a-rule-set-in-a-text-editor)oder eines der standardmäßigen RuleSets, die in gespeichert sind `%VSINSTALLDIR%\Team Tools\Static Analysis Tools\Rule Sets` .
