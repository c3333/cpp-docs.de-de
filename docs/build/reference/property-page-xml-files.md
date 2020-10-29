---
title: XML-Regeldateien für Eigenschaftenseiten
description: Beschreibung der Visual Studio-IDE C++ XML-Regel Dateien und-Inhalte der Eigenschaften Seite.
ms.date: 10/14/2020
helpviewer_keywords:
- property page XML files
ms.openlocfilehash: f8aa893fa2b062da2f1d0784e5a9b1a6f2b30c95
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "92921398"
---
# <a name="property-page-xml-rule-files"></a>XML-Regeldateien für Eigenschaftenseiten

Die Projekteigenschaften Seiten in der IDE werden von XML-Dateien im Ordner Standardregeln konfiguriert. Die XML-Dateien beschreiben die Namen der Regeln, die Kategorien und die einzelnen Eigenschaften, den Datentyp, die Standardwerte und wie Sie angezeigt werden. Wenn Sie eine Eigenschaft in der IDE festlegen, wird der neue Wert in der Projektdatei gespeichert.

::: moniker range="msvc-140"

Der Pfad zum Standardordner "Rules" hängt vom Gebiets Schema und der verwendeten Version von Visual Studio ab. Bei der Developer-Eingabeaufforderung in Visual Studio 2015 oder einer früheren Version ist der Regelordner *`%ProgramFiles(x86)%\MSBuild\Microsoft.Cpp\v4.0\<version>\<locale>`* . In Visual Studio 2015 ist der Wert für `<version>` *`v140`* . `<locale>` ist eine LCID, z. B. `1033` für Englisch. Für jede installierte Edition von Visual Studio und jede Sprache gibt es einen eigenen Pfad. Beispielsweise könnte der Standardpfad für den Regelordner für Visual Studio 2015 Community Edition in englischer Sprache *`C:\Program Files (x86)\MSBuild\Microsoft.Cpp\v4.0\v140\1033\`* sein.

::: moniker-end

::: moniker range="msvc-150"

Der Pfad zum Standardordner "Rules" hängt vom Gebiets Schema und der verwendeten Version von Visual Studio ab. Bei der Developer-Eingabeaufforderung in Visual Studio 2017 ist der Regelordner *`%VSINSTALLDIR%Common7\IDE\VC\VCTargets\<locale>\`* . `<locale>` ist eine LCID, z. B. `1033` für Englisch. Bei der Developer-Eingabeaufforderung in Visual Studio 2015 oder einer früheren Version ist der Regelordner *`%ProgramFiles(x86)%\MSBuild\Microsoft.Cpp\v4.0\<version>\<locale>\`* mit *`v140`* als Wert für `<version>` in Visual Studio 2015. Für jede installierte Edition von Visual Studio und jede Sprache gibt es einen eigenen Pfad. Beispielsweise könnte der Standardpfad für den Regelordner für Visual Studio 2017 Community Edition in englischer Sprache *`C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\VC\VCTargets\1033\`* sein.

::: moniker-end

::: moniker range=">=msvc-160"

Der Pfad zum Standardordner "Rules" hängt vom Gebiets Schema und der verwendeten Version von Visual Studio ab. Bei der Developer-Eingabeaufforderung in Visual Studio 2019 oder einer höheren Version ist der Regelordner *`%VSINSTALLDIR%MSBuild\Microsoft\VC\<version>\<locale>\`* mit *`v160`* als Wert für `<version>` in Visual Studio 2019. `<locale>` ist eine LCID, z. B. `1033` für Englisch. In Visual Studio 2017 ist der Regelordner *`%VSINSTALLDIR%Common7\IDE\VC\VCTargets\<locale>\`* . Bei der Developer-Eingabeaufforderung in Visual Studio 2015 oder einer früheren Version ist der Regelordner *`%ProgramFiles(x86)%\MSBuild\Microsoft.Cpp\v4.0\<version>\<locale>\`* . Für jede installierte Edition von Visual Studio und jede Sprache gibt es einen eigenen Pfad. Beispielsweise könnte der Standardpfad für den Regelordner für Visual Studio 2019 Community Edition in englischer Sprache *`C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\MSBuild\Microsoft\VC\v160\1033\`* sein.

::: moniker-end

Sie müssen nur die internen Abläufe dieser Dateien und der Visual Studio-IDE in einigen Szenarios verstehen:

- Sie möchten eine benutzerdefinierte Eigenschaften Seite erstellen oder
- Sie möchten Ihre Projekteigenschaften ohne die Visual Studio-IDE anpassen.

## <a name="contents-of-rule-files"></a>Inhalt von Regel Dateien

Öffnen Sie zunächst die Eigenschaften Seiten für ein Projekt. Klicken Sie in **Projektmappen-Explorer** mit der rechten Maustaste auf den Projekt Knoten, und wählen Sie **Eigenschaften** aus:

![Zeigt das Dialogfeld "Visual Studio C++ Projekteigenschaften" an](../media/cpp-property-page-2017.png)

Jeder Knoten unter **Konfigurations Eigenschaften** wird als *Regel* bezeichnet. Eine Regel stellt manchmal ein einzelnes Tool wie den Compiler dar. Im allgemeinen verweist der Begriff auf etwas, das über Eigenschaften verfügt, die ausgeführt werden und eine Ausgabe verursachen können. Jede Regel wird aus einer XML-Datei im Standardregel Ordner ausgefüllt. Die hier gezeigte C/C++-Regel wird z. b. mit *"cl.xml"* aufgefüllt.

Jede Regel verfügt über eine Reihe von Eigenschaften, die in *Kategorien* unterteilt sind. Jeder unter Knoten unter einer Regel stellt eine Kategorie dar. Beispielsweise enthält der Knoten **Optimierung** unter **C/C++** alle Optimierungs bezogenen Eigenschaften des Compilertools. Die Eigenschaften und ihre Werte werden im rechten Bereich in einem Raster Format gerendert.

Sie können *`cl.xml`* in Editor oder einem beliebigen XML-Editor öffnen. Sie sehen einen Stamm Knoten mit dem Namen `Rule` . Sie definiert die gleiche Liste von Eigenschaften, die in der Benutzeroberfläche angezeigt werden, zusammen mit zusätzlichen Metadaten.

```xml
<?xml version="1.0" encoding="utf-8"?>
<!--Copyright, Microsoft Corporation, All rights reserved.-->
<Rule Name="CL" PageTemplate="tool" DisplayName="C/C++" SwitchPrefix="/" Order="10" xmlns="http://schemas.microsoft.com/build/2009/properties" xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml" xmlns:sys="clr-namespace:System;assembly=mscorlib">
  <Rule.Categories>
    <Category Name="General" DisplayName="General" />
    <Category Name="Optimization" DisplayName="Optimization" />
    <Category Name="Preprocessor" DisplayName="Preprocessor" />
    <Category Name="Code Generation" DisplayName="Code Generation" />
    <Category Name="Language" DisplayName="Language" />
    <Category Name="Precompiled Headers" DisplayName="Precompiled Headers" />
    <Category Name="Output Files" DisplayName="Output Files" />
    <Category Name="Browse Information" DisplayName="Browse Information" />
    <Category Name="Advanced" DisplayName="Advanced" />
    <Category Name="All Options" DisplayName="All Options" Subtype="Search" />
    <Category Name="Command Line" DisplayName="Command Line" Subtype="CommandLine" />
  </Rule.Categories>
  <!-- . . . -->
</Rule>
```

Es gibt eine XML-Datei für jeden Knoten unter **Konfigurations Eigenschaften** in der Benutzeroberfläche der Eigenschaften Seiten. Sie können Regeln in der Benutzeroberfläche hinzufügen oder entfernen: Dies erfolgt durch das einschließen oder Entfernen von Speicherorten in entsprechende XML-Dateien im Projekt. Beispielsweise enthält die Vorgehensweise *`Microsoft.CppBuild.targets`* (eine Ebene, die höher als der Ordner 1033 ist) Folgendes *`cl.xml`* :

```xml
<PropertyPageSchema Condition="'$(ConfigurationType)' != 'Utility'" Include="$(VCTargetsPath)$(LangID)\cl.xml"/>
```

Wenn Sie *`cl.xml`* alle Daten entfernen, verfügen Sie über dieses grundlegende Framework:

```xml
<?xml version="1.0" encoding="utf-8"?>
<Rule>
  <Rule.DataSource />
  <Rule.Categories>
    <Category />
    <!-- . . . -->
  </Rule.Categories>
  <BoolProperty />
  <EnumProperty />
  <IntProperty />
  <StringProperty />
  <StringListProperty />
</Rule>
```

Im nächsten Abschnitt werden die einzelnen Hauptelemente und einige der Metadaten beschrieben, die Sie anfügen können.

### <a name="rule-attributes"></a>Regel Attribute

Ein- **`<Rule>`** Element ist der Stamm Knoten in der XML-Datei. Sie kann über viele Attribute verfügen:

```xml
<Rule Name="CL" PageTemplate="tool" SwitchPrefix="/" Order="10"
          xmlns="http://schemas.microsoft.com/build/2009/properties"
          xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
          xmlns:sys="clr-namespace:System;assembly=mscorlib">
  <Rule.DisplayName>
    <sys:String>C/C++</sys:String>
  </Rule.DisplayName>
```

- **`Name`** : Das Name-Attribut ist eine ID für das `Rule` . Er muss in allen XML-Dateien der Eigenschaften Seite für ein Projekt eindeutig sein.

- **`PageTemplate`** : Der Wert dieses Attributs wird von der Benutzeroberfläche verwendet, um eine Sammlung von UI-Vorlagen auszuwählen. Die Vorlage „tool“ rendert die Eigenschaften in einem Standardrasterformat. Weitere integrierte Werte für dieses Attribut sind „debugger“ und „generic“. Betrachten Sie die Knoten „Debuggen“ und „Allgemein“, um zu sehen, welches Format sich für die Benutzeroberfläche ergibt, wenn Sie diese Werte festlegen. Die Benutzeroberfläche für die Seitenvorlage "Debugger" verwendet ein Dropdown Feld, um zwischen den Eigenschaften verschiedener Debugger zu wechseln. Die "generische" Vorlage zeigt verschiedene Eigenschaften Kategorien in einer Seite an, anstatt mehrere kategorieunterknoten unterhalb des `Rule` Knotens zu haben. Dieses Attribut ist nur ein Vorschlag für die Benutzeroberfläche. Die XML-Datei ist so konzipiert, dass Sie Benutzeroberflächen unabhängig ist. Eine andere Benutzeroberfläche verwendet dieses Attribut möglicherweise für andere Zwecke.

- **`SwitchPrefix`** : Das Präfix, das in der Befehlszeile für die Switches verwendet wird. Ein Wert von `"/"` würde zu Switches führen, die wie **`/ZI`** , **`/nologo`** , **`/W3`** usw. aussehen.

- **`Order`** : Ein Vorschlag an einen potenziellen Benutzeroberflächen Client im `Rule` Vergleich zu allen anderen Regeln im System.

- **`xmlns`** : Ein Standard-XML-Element. Drei Namespaces werden aufgeführt. Diese Attribute entsprechen den Namespaces für die XML-deserialisierungsklassen, das XML-Schema bzw. den System Namespace.

- **`DisplayName`** : Der Name, der auf der Benutzeroberfläche der Eigenschaften Seite für den Knoten angezeigt wird `Rule` . Dieser Wert wird lokalisiert. Wir haben `DisplayName` `Rule` `Name` `SwitchPrefix` aufgrund interner Lokalisierungs Tool Anforderungen als untergeordnetes Element von und nicht als Attribut (z. b. oder) erstellt. Aus XML-Sicht sind beide Äquivalent. Sie können deshalb ein Attribut daraus erstellen, um die Übersichtlichkeit zu verbessern, oder keine Änderung vornehmen.

- **`DataSource`** : Diese wichtige Eigenschaft weist das Projekt System an, den Eigenschafts Wert und die zugehörige Gruppierung zu lesen und zu schreiben (später erläutert). Für lauten *`cl.xml`* folgende Werte:

    ```xml
    <DataSource Persistence="ProjectFile" ItemType="ClCompile" Label="" HasConfigurationCondition="true" />
    ```

  - `Persistence="ProjectFile"` weist das Projekt System an, dass alle Eigenschaften für das `Rule` in die Projektdatei oder die Eigenschaften Blatt Datei geschrieben werden sollen (je nachdem, welcher Knoten zum Erzeugen der Eigenschaften Seiten verwendet wurde). Der andere mögliche Wert ist `"UserFile"` , wodurch der Wert in die Datei geschrieben wird *`.user`* .

  - `ItemType="ClCompile"` gibt an, dass die Eigenschaften als ItemDefinition-Metadaten oder als Elementmetadaten (nur, wenn die Eigenschaftenseiten aus einem Dateiknoten im Projektmappen-Explorer erzeugt wurden) dieses Elementtyps gespeichert werden. Wenn dieses Feld nicht festgelegt ist, wird die Eigenschaft als allgemeine Eigenschaft in eine PropertyGroup geschrieben.

  - `Label=""` gibt an, dass die Bezeichnung des übergeordneten Elements „ItemDefinitionGroup“ leer ist (jedes MSBuild-Element kann eine Bezeichnung besitzen), wenn die Eigenschaften als `ItemDefinition`-Metadaten geschrieben werden. Visual Studio 2017 und höher verwendet Gruppen mit Bezeichnung, um in der VCXPROJ-Projektdatei zu navigieren. Die Gruppen, die die meisten Eigenschaften enthalten, `Rule` haben eine leere Zeichenfolge als Bezeichnung.

  - `HasConfigurationCondition="true"` weist das Projektsystem an, eine Konfigurationsbedingung an den Wert anzufügen, damit dieser nur für die aktuelle Projektkonfiguration wirksam ist. Die Konfiguration kann an die übergeordnete Gruppe oder an den Wert angefügt werden. Öffnen Sie beispielsweise die Projektseiten über den Projektknoten, und legen Sie den Wert der Eigenschaft **Warnungen als Fehler behandeln** unter **Konfigurationseigenschaften > C/C++ > Allgemein** auf „Ja“ fest. Der folgende Wert wird in die Projektdatei geschrieben. Beachten Sie die Konfigurationsbedingung, die an das übergeordnete Element „ItemDefinitionGroup“ angefügt ist.

    ```xml
    <ItemDefinitionGroup Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'">
      <ClCompile>
        <TreatWarningAsError>true</TreatWarningAsError>
      </ClCompile>
    </ItemDefinitionGroup>
    ```

     Wenn dieser Wert auf der Eigenschaften Seite für eine bestimmte Datei (z. b.) festgelegt wird, *`stdafx.cpp`* sollte der Eigenschafts Wert unter dem `stdafx.cpp` Element in der Projektdatei geschrieben werden, wie hier gezeigt. Beachten Sie, dass die Konfigurations Bedingung direkt an die Metadaten selbst angefügt wird:

    ```xml
    <ItemGroup>
      <ClCompile Include="stdafx.cpp">
        <TreatWarningAsError Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'">true</TreatWarningAsError>
      </ClCompile>
    </ItemGroup>
    ```

  Ein anderes Attribut, das `DataSource` hier nicht aufgeführt ist, ist `PersistedName` . Sie können dieses Attribut verwenden, um eine Eigenschaft in der Projektdatei mit einem anderen Namen darzustellen. Standardmäßig ist dieses Attribut auf die der-Eigenschaft festgelegt `Name` .

  Eine einzelne Eigenschaft kann die `DataSource` des übergeordneten Elements überschreiben `Rule` . In diesem Fall unterscheidet sich der Speicherort für den Wert dieser Eigenschaft von anderen Eigenschaften im `Rule` .

- Es gibt andere Attribute von `Rule` , einschließlich `Description` und `SupportsFileBatching` , die hier nicht angezeigt werden. Der vollständige Satz von Attributen, die für einen `Rule` oder für ein beliebiges anderes Element anwendbar sind, kann durch das Durchsuchen der Dokumentation für diese Typen abgerufen werden. Alternativ können Sie die öffentlichen Eigenschaften von Typen im `Microsoft.Build.Framework.XamlTypes`-Namespace der `Microsoft.Build.Framework.dll`-Assembly überprüfen.

- **`DisplayName`** , **`PageTemplate`** und **`Order`** sind UI-bezogene Eigenschaften, die in diesem anderweitig Benutzeroberflächen unabhängigen Datenmodell vorhanden sind. Diese Eigenschaften werden meistens von allen Benutzeroberflächen verwendet, die zum Anzeigen von Eigenschaftenseiten verwendet werden. `DisplayName` und `Description` sind zwei Eigenschaften, die für fast alle Elemente in der XML-Datei vorhanden sind. Diese beiden Eigenschaften sind die einzigen, die lokalisiert werden.

### <a name="category-elements"></a>Kategorieelemente

Ein `Rule` kann mehrere- `Category` Elemente aufweisen. Die Reihenfolge, in der die Kategorien in der XML-Datei aufgelistet sind, ist ein Vorschlag für die Benutzeroberfläche, die Kategorien in derselben Reihenfolge anzuzeigen. Beispielsweise ist die Reihenfolge der Kategorien unter dem Knoten **C/C++** , den Sie in der Benutzeroberfläche sehen, identisch mit der Reihenfolge in *`cl.xml`* . Eine Beispielkategorie sieht folgendermaßen aus:

```xml
<Category Name="Optimization">
  <Category.DisplayName>
    <sys:String>Optimization</sys:String>
  </Category.DisplayName>
</Category>
```

Dieser Code Ausschnitt zeigt das `Name` -Attribut und das- `DisplayName` Attribut, die zuvor beschrieben wurden. Auch hier gibt es noch weitere Attribute, `Category` die ein aufweisen kann, die im Beispiel nicht angezeigt werden. Weitere Informationen hierzu finden Sie in der Dokumentation oder unter Untersuchen der Assemblys mithilfe von *`ildasm.exe`* .

### <a name="property-elements"></a>Eigenschaften Elemente

Der größte Teil der Regeldatei besteht aus `Property` Elementen. Sie enthalten die Liste aller Eigenschaften in einer `Rule` . Jede Eigenschaft kann einer der fünf möglichen Typen sein, die im grundlegenden Framework angezeigt werden: `BoolProperty` , `EnumProperty` , `IntProperty` , `StringProperty` und `StringListProperty` . In Ihrer Datei sind möglicherweise nur einige dieser Typen enthalten. Eine Eigenschaft verfügt über eine Reihe von Attributen, mit denen Sie ausführlich beschrieben werden kann. Die `StringProperty` wird hier beschrieben. Der Rest ist ähnlich.

```xml
<StringProperty Subtype="file" Name="ObjectFileName" Category="Output Files" Switch="Fo">
  <StringProperty.DisplayName>
    <sys:String>Object File Name</sys:String>
  </StringProperty.DisplayName>
  <StringProperty.Description>
    <sys:String>Specifies a name to override the default object file name; can be file or directory name.(/Fo[name])</sys:String>
  </StringProperty.Description>
</StringProperty>
```

Die meisten Attribute im Codeausschnitt wurden zuvor bereits beschrieben. Die neuen sind `Subtype` , `Category` und `Switch` .

- **`Subtype`** ist ein Attribut, das nur für `StringProperty` -und-Elemente verfügbar ist `StringListProperty` . Sie enthält Kontextinformationen. Der-Wert gibt beispielsweise an `file` , dass die-Eigenschaft einen Dateipfad darstellt. Visual Studio verwendet diese Kontextinformationen, um die Bearbeitungsfunktionen zu verbessern. Beispielsweise kann ein Fenster in Windows-Explorer bereitgestellt werden, mit dem der Benutzer die Datei visuell als Editor für die Eigenschaft auswählen kann.

- **`Category`** : Die Kategorie, unter der diese Eigenschaft liegt. Suchen Sie diese Eigenschaft in der Kategorie **Ausgabedateien** auf der Benutzeroberfläche.

- **`Switch`** : Wenn eine Regel ein Tool (z. b. das Compilertool) darstellt, werden die meisten `Rule` Eigenschaften bei der Buildzeit als Switches an die ausführbare Datei des Tools Der Wert dieses Attributs gibt an, welches switchliterale verwendet werden soll. Im `<StringProperty>` Beispiel wird angegeben, dass der Switch lauten soll **`Fo`** . In Kombination mit dem- `SwitchPrefix` Attribut für das übergeordnete Element `Rule` wird diese Eigenschaft als an die ausführbare Datei weitergegeben  **`/Fo"Debug\"`** . Es ist in der Befehlszeile für C/C++ auf der Eigenschaften Seite der Benutzeroberfläche sichtbar.

   Folgende weitere Eigenschaftenattribute sind vorhanden:

- **`Visible`** : Wenn Sie nicht möchten, dass Ihre Eigenschaft in den Eigenschaften Seiten angezeigt wird, Sie aber zur Buildzeit verfügbar machen möchten, legen Sie dieses Attribut auf fest `false` .

- **`ReadOnly`** : Legen Sie dieses Attribut auf fest, wenn Sie eine schreibgeschützte Ansicht für den Wert dieser Eigenschaft in den Eigenschaften Seiten bereitstellen möchten `true` .

- **`IncludeInCommandLine`** : Bei der Buildzeit benötigt ein Tool möglicherweise nicht einige seiner Eigenschaften. Legen Sie dieses Attribut auf fest, `false` um zu verhindern, dass eine bestimmte Eigenschaft übermittelt wird.
