---
title: VCXPROJ- und PROPS-Dateistruktur
description: Gibt an, wie die System. vcxproj-und. Constants-Dateien des C++ Native MSBuild-Projekts Projektinformationen speichern.
ms.date: 09/30/2020
helpviewer_keywords:
- .vcxproj file structure
ms.assetid: 14d0c552-29db-480e-80c1-7ea89d6d8e9c
ms.openlocfilehash: 562ef0c1b371d7212f31da1917d19c012e4cbb24
ms.sourcegitcommit: f7fbdc39d73e1fb3793c396fccf7a1602af7248b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2020
ms.locfileid: "91662281"
---
# <a name="vcxproj-and-props-file-structure"></a>`.vcxproj` und `.props` Dateistruktur

[MSBuild](../msbuild-visual-cpp.md) ist das Standard Projekt System in Visual Studio. Wenn Sie in Visual C++ **Datei**  >  **Neues Projekt** auswählen, erstellen Sie ein MSBuild-Projekt, dessen Einstellungen in einer XML-Projektdatei mit der Erweiterung gespeichert sind *`.vcxproj`* . In der Projektdatei können auch *`.props`* Dateien und *`.targets`* Dateien importiert werden, in denen die Einstellungen gespeichert werden können.

Es wird empfohlen, nur Projekte in der IDE zu erstellen und zu ändern *`.vcxproj`* und so die manuelle Bearbeitung so weit wie möglich zu vermeiden. In den meisten Fällen müssen Sie die Projektdatei nie manuell bearbeiten. Wenn möglich, sollten Sie die Visual Studio-Eigenschaften Seiten verwenden, um Projekteinstellungen zu ändern. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

Wenn Sie Anpassungen benötigen, die in der IDE nicht möglich sind, empfiehlt es sich, benutzerdefinierte Eigenschaften oder Ziele hinzuzufügen. Praktische Orte zum Einfügen von Anpassungen sind die *`Directory.Build.props`* -und- *`Directory.Build.targets`* Dateien, die automatisch in allen MSBuild-basierten Projekten importiert werden.

In einigen Fällen müssen Sie die *`.vcxproj`* Projektdatei oder das Eigenschaften Blatt möglicherweise manuell ändern. Es wird nicht empfohlen, Sie manuell zu bearbeiten, sofern Sie nicht über ein gutes Verständnis von MSBuild verfügen, und befolgen Sie die Richtlinien in diesem Artikel. Damit die IDE Dateien automatisch laden und aktualisieren *`.vcxproj`* kann, gelten für diese Dateien mehrere Einschränkungen, die nicht für andere MSBuild-Projektdateien gelten. Sie wurden nicht für die manuelle Bearbeitung entwickelt. Fehler können dazu führen, dass die IDE abstürzen kann oder sich auf unerwartete Weise verhält.

In diesem Artikel finden Sie grundlegende Informationen zur Struktur von *`.vcxproj`* und verwandten Dateien in diesem Artikel.

**Wichtig:**

Beachten Sie die folgenden Fakten, wenn Sie eine Datei manuell bearbeiten möchten *`.vcxproj`* :

- Die Struktur der Datei muss einer vorgeschriebenen Form folgen, die in diesem Artikel beschrieben wird.

- Das Visual Studio C++-Projekt System unterstützt derzeit keine Platzhalter oder Listen direkt in Projekt Elementen. Diese Formulare werden z. b. nicht unterstützt:

   ```xml
   <ItemGroup>
     <None Include="*.txt"/>
     <ClCompile Include="a.cpp;b.cpp"/>
   </ItemGroup>
   ```

   Weitere Informationen zur Platzhalter Unterstützung in Projekten und möglichen Problem Umgehungen finden Sie unter [ `.vcxproj` Dateien und](vcxproj-files-and-wildcards.md)Platzhalter.

- Das Visual Studio C++-Projekt System unterstützt derzeit keine Makros in Projekt Element Pfaden. Dieses Formular wird z. b. nicht unterstützt:

   ```xml
   <ItemGroup>
     <ClCompile Include="$(IntDir)\generated.cpp"/>
   </ItemGroup>
   ```

   "Nicht unterstützt" bedeutet, dass Makros nicht garantiert für alle Vorgänge in der IDE funktionieren. Makros, die ihren Wert in verschiedenen Konfigurationen nicht ändern, sollten funktionieren, werden jedoch möglicherweise nicht beibehalten, wenn ein Element in einen anderen Filter oder ein anderes Projekt verschoben wird. Makros, die ihren Wert für verschiedene Konfigurationen ändern, führen zu Problemen. Das liegt daran, dass die IDE nicht erwartet, dass sich Projekt Element Pfade für unterschiedliche Projekt Konfigurationen unterscheiden.

- Wenn Sie Projekteigenschaften im Dialogfeld **Projekteigenschaften** ordnungsgemäß hinzufügen, entfernen oder ändern möchten, muss die Datei separate Gruppen für jede Projekt Konfiguration enthalten. Die Bedingungen müssen in der folgenden Form vorliegen:

   ```xml
   Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'"
   ```

- Jede Eigenschaft muss in der Gruppe mit der richtigen Bezeichnung angegeben werden, wie in der Eigenschafts Regeldatei angegeben. Weitere Informationen finden Sie unter [Property page xml rule files (XML-Regeldateien für Eigenschaftenseiten)](property-page-xml-files.md).

## <a name="vcxproj-file-elements"></a>`.vcxproj` file-Elemente

Sie können den Inhalt einer Datei mit *`.vcxproj`* einem beliebigen Text-oder XML-Editor überprüfen. Sie können sie in Visual Studio anzeigen, indem Sie im Projektmappen-Explorer mit der rechten Maustaste auf das Projekt klicken und anschließend **Projekt entladen** > **Foo.vcxproj bearbeiten** auswählen.

Zunächst werden Sie feststellen, dass die Elemente auf oberster Ebene in einer bestimmten Reihenfolge angezeigt werden. Beispiel:

- Die meisten Eigenschaftengruppen und Elementdefinitionsgruppen werden nach dem Import für „Microsoft.Cpp.Default.props“ angezeigt.

- Alle Ziele werden am Ende der Datei importiert.

- Es gibt mehrere Eigenschaftengruppen, die jeweils eine eindeutige Bezeichnung besitzen und in einer bestimmten Reihenfolge auftreten.

Die Reihenfolge der Elemente in der Projektdatei ist äußerst wichtig, da MSBuild auf einem sequenziellen Evaluierungs Modell basiert.  Wenn die Projektdatei, einschließlich aller importierten *`.props`* Dateien und *`.targets`* , aus mehreren Definitionen einer Eigenschaft besteht, überschreibt die letzte Definition die vorangehenden Definitionen. Im folgenden Beispiel wird der Wert "xyz" während der Kompilierung festgelegt, da die MSBuild-Engine Sie während der Auswertung zuletzt findet.

```xml
  <MyProperty>abc</MyProperty>
  <MyProperty>xyz</MyProperty>
```

Der folgende Code Ausschnitt zeigt eine minimale *`.vcxproj`* Datei. Jede *`.vcxproj`* von Visual Studio generierte Datei enthält diese MSBuild-Elemente der obersten Ebene. Und Sie werden in dieser Reihenfolge angezeigt, obwohl Sie möglicherweise mehrere Kopien der einzelnen Elemente der obersten Ebene enthalten. `Label`Attribute sind beliebige Tags, die nur von Visual Studio als Signposts für die Bearbeitung verwendet werden. Sie haben keine andere Funktion.

```xml
<Project DefaultTargets="Build" ToolsVersion="4.0" xmlns='http://schemas.microsoft.com/developer/msbuild/2003'>
  <ItemGroup Label="ProjectConfigurations" />
  <PropertyGroup Label="Globals" />
  <Import Project="$(VCTargetsPath)\Microsoft.Cpp.default.props" />
  <PropertyGroup Label="Configuration" />
  <Import Project="$(VCTargetsPath)\Microsoft.Cpp.props" />
  <ImportGroup Label="ExtensionSettings" />
  <ImportGroup Label="PropertySheets" />
  <PropertyGroup Label="UserMacros" />
  <PropertyGroup />
  <ItemDefinitionGroup />
  <ItemGroup />
  <Import Project="$(VCTargetsPath)\Microsoft.Cpp.targets" />
  <ImportGroup Label="ExtensionTargets" />
</Project>
```

In den folgenden Abschnitten wird der Zweck der einzelnen Elemente beschrieben und erläutert, warum Sie auf diese Weise angeordnet sind:

### <a name="project-element"></a>Project-Element

```xml
<Project DefaultTargets="Build" ToolsVersion="4.0" xmlns='http://schemas.microsoft.com/developer/msbuild/2003' >
```

`Project` ist der Stammknoten. Sie gibt die zu verwendende MSBuild-Version und auch das Standardziel an, das ausgeführt wird, wenn diese Datei an MSBuild.exe übermittelt wird.

### <a name="projectconfigurations-itemgroup-element"></a>ItemGroup-Element „ProjectConfigurations“

```xml
<ItemGroup Label="ProjectConfigurations" />
```

`ProjectConfigurations` enthält die Beschreibung der Projektkonfiguration. Beispiele dafür sind „Debug|Win32“, „Release|Win32“ und „Debug|ARM“. Viele Projekteigenschaften sind für eine bestimmte Konfiguration spezifisch. Beispielsweise möchten Sie wahrscheinlich Optimierungs Eigenschaften für einen Releasebuild festlegen, aber nicht für einen Debugbuild.

Die `ProjectConfigurations` Element Gruppe wird zum Zeitpunkt der Erstellung nicht verwendet. Die Visual Studio-IDE erfordert, dass das Projekt geladen wird. Diese Element Gruppe kann in eine Datei verschoben *`.props`* und in die Datei importiert werden *`.vcxproj`* . Wenn Sie in diesem Fall jedoch Konfigurationen hinzufügen oder entfernen müssen, müssen Sie die Datei manuell bearbeiten *`.props`* . die IDE kann nicht verwendet werden.

### <a name="projectconfiguration-elements"></a>ProjectConfiguration-Elemente

In folgendem Codeausschnitt wird eine Projektkonfiguration dargestellt. In diesem Beispiel ist "Debug | x64" der Konfigurations Name. Der Name der Projekt Konfiguration muss das Format aufweisen `$(Configuration)|$(Platform)` . Ein `ProjectConfiguration` Knoten kann zwei Eigenschaften haben: `Configuration` und `Platform` . Diese Eigenschaften werden automatisch mit den hier angegebenen Werten festgelegt, wenn die Konfiguration aktiv ist.

```xml
<ProjectConfiguration Include="Debug|x64">
  <Configuration>Debug</Configuration>
  <Platform>x64</Platform>
</ProjectConfiguration>
```

Die IDE erwartet eine Projekt Konfiguration für eine beliebige Kombination von `Configuration` -und-Werten, die `Platform` in allen Elementen verwendet werden `ProjectConfiguration` . Häufig bedeutet dies, dass ein Projekt möglicherweise bedeutungslose Projekt Konfigurationen hat, um diese Anforderung zu erfüllen. Gehen Sie von einem Projekt mit folgenden Konfigurationen aus:

- Debug|Win32

- Retail|Win32

- Special 32-bit Optimization|Win32

Das Projekt muss dann ebenfalls diese Konfigurationen enthalten, obwohl „Special 32-bit Optimization“ für x64 nicht von Bedeutung ist:

- Debuggen|x64

- Retail|x64

- Special 32-bit Optimization|x64

Sie können die Build- und Bereitstellungsbefehle für alle Konfigurationen im **Konfigurations-Manager für Projektmappen** deaktivieren.

### <a name="globals-propertygroup-element"></a>PropertyGroup-Element „Globals“

```xml
<PropertyGroup Label="Globals" />
```

`Globals` enthält Einstellungen auf Projektebene `ProjectGuid` , z `RootNamespace` . b., und `ApplicationType` oder `ApplicationTypeRevision` . Die letzten beiden definieren häufig das Zielbetriebssystem. Ein Projekt kann nur auf ein einzelnes Betriebssystem abzielen, da Verweise und Projekt Elemente derzeit keine Bedingungen haben können. Diese Eigenschaften werden üblicherweise nicht an anderer Stelle in der Projektdatei überschrieben. Diese Gruppe ist nicht Konfigurations abhängig, und in der Regel ist nur eine `Globals` Gruppe in der Projektdatei vorhanden.

### <a name="microsoftcppdefaultprops-import-element"></a>Import-Element „Microsoft.Cpp.default.props“

```xml
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.default.props" />
```

Das Eigenschaften Blatt " **Microsoft. cpp. default.** -Eigenschaften" ist in Visual Studio verfügbar und kann nicht geändert werden. Es enthält die Standardeinstellungen für das Projekt. Die Standardwerte hängen von „ApplicationType“ ab.

### <a name="configuration-propertygroup-elements"></a>PropertyGroup-Element „Configuration“

```xml
<PropertyGroup Label="Configuration" />
```

Eine `Configuration`-Eigenschaftengruppe besitzt eine angefügte Konfigurationsbedingung (z.B. `Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'"`) und liegt in mehreren Kopien (eine pro Konfiguration) vor. Diese Eigenschaftengruppe hostet die Eigenschaften, die für eine bestimmte Konfiguration festgelegt sind. Zu den Konfigurationseigenschaften zählt „PlatformToolset“. Außerdem steuern diese das Einschließen von Systemeigenschaftenblättern in **Microsoft.Cpp.props**. Wenn Sie beispielsweise die Eigenschaft `<CharacterSet>Unicode</CharacterSet>` definieren, wird das Systemeigenschaftenblatt **microsoft.Cpp.unicodesupport.props** eingeschlossen. Wenn Sie **Microsoft. cpp.**-Eigenschaften überprüfen, sehen Sie die folgende Zeile: `<Import Condition="'$(CharacterSet)' == 'Unicode'" Project="$(VCTargetsPath)\microsoft.Cpp.unicodesupport.props" />` .

### <a name="microsoftcppprops-import-element"></a>Import-Element „Microsoft.Cpp.props“

```xml
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.props" />
```

Das Eigenschaften Blatt " **Microsoft. cpp.** Properties" (direkt oder über Importe) definiert die Standardwerte für viele Tool spezifische Eigenschaften. Beispiele hierfür sind die Optimierungs-und warnebeneneigenschaften des Compilers, die typeLibraryName-Eigenschaft des Mittelpunkts usw. Außerdem werden verschiedene System Eigenschafts Blätter importiert, die darauf basieren, welche Konfigurations Eigenschaften direkt vor dem Objekt in der Eigenschaften Gruppe definiert werden.

### <a name="extensionsettings-importgroup-element"></a>ImportGroup-Element „ExtensionSettings“

```xml
<ImportGroup Label="ExtensionSettings" />
```

Die `ExtensionSettings`-Gruppe enthält Importe für die Eigenschaftenblätter, die Teil der Buildanpassungen sind. Eine Buildanpassung wird durch bis zu drei Dateien definiert: eine *`.targets`* Datei, eine *`.props`* Datei und eine *`.xml`* Datei. Diese Import Gruppe enthält die Importe für die *`.props`* Datei.

### <a name="propertysheets-importgroup-elements"></a>ImportGroup-Element „PropertySheets“

```xml
<ImportGroup Label="PropertySheets" />
```

Die `PropertySheets`-Gruppe enthält die Importe für Benutzereigenschaftenblätter. Diese Importe sind die Eigenschaften Blätter, die Sie über die Eigenschaften-Manager Ansicht in Visual Studio hinzufügen. Die Reihenfolge, in der diese Importe aufgeführt werden, ist wichtig und wird im Eigenschaften-Manager dargestellt. Die Projektdatei enthält normalerweise mehrere Instanzen von dieser Art von Importgruppe (eine pro Projektkonfigurationen).

### <a name="usermacros-propertygroup-element"></a>PropertyGroup-Element „UserMacros“

```xml
<PropertyGroup Label="UserMacros" />
```

`UserMacros` enthält Eigenschaften, die Sie als Variablen erstellen, die zum Anpassen des Buildprozesses verwendet werden. Sie können beispielsweise ein Benutzermakro definieren, um den benutzerdefinierten Ausgabepfad als „$(CustomOutputPath)“ zu definieren und diesen dafür verwenden, andere Variablen zu definieren. Diese Eigenschaftengruppe enthält diese Eigenschaften. In Visual Studio wird diese Gruppe nicht in der Projektdatei aufgefüllt, da Visual C++ keine Benutzer Makros für Konfigurationen unterstützt. Benutzermakros werden in Eigenschaftenblättern unterstützt.

### <a name="per-configuration-propertygroup-elements"></a>PropertyGroup-Elemente pro Konfiguration

```xml
<PropertyGroup />
```

Es gibt mehrere Instanzen dieser Eigenschaftengruppe: eine pro Konfiguration für alle Projektkonfigurationen. Jeder Eigenschaftengruppe muss eine Konfigurationsbedingung angefügt sein. Wenn eine Konfiguration fehlt, funktioniert das Dialogfeld **Projekteigenschaften** nicht ordnungsgemäß. Im Gegensatz zu den zuvor aufgeführten Eigenschaften Gruppen weist diese keine Bezeichnung auf. Diese Gruppe enthält Einstellungen auf Projektkonfigurationsebene. Diese Eigenschaften gelten für alle Dateien, die Teil der angegebenen Elementgruppe sind. Elementdefinitionsmetadaten für die Buildanpassung werden hier initialisiert.

Diese PropertyGroup muss nach stehen, `<Import Project="$(VCTargetsPath)\Microsoft.Cpp.props" />` und es darf keine andere PropertyGroup vorhanden sein, ohne dass eine Bezeichnung vorhanden sein muss (andernfalls funktioniert die Bearbeitung von Projekteigenschaften nicht ordnungsgemäß).

### <a name="per-configuration-itemdefinitiongroup-elements"></a>ItemDefinitionGroup-Elemente pro Konfiguration

```xml
<ItemDefinitionGroup />
```

Enthält Elementdefinitionen. Diese Definitionen müssen die gleichen Bedingungen erfüllen wie die für die Bezeichnung weniger Konfigurations `PropertyGroup` Elemente.

### <a name="itemgroup-elements"></a>ItemGroup-Elemente

```xml
<ItemGroup />
```

`ItemGroup` -Elemente enthalten die Elemente (Quelldateien usw.) im Projekt. Bedingungen werden für Projekt Elemente (d. h. Elementtypen, die von Regeldefinitionen als Projekt Elemente behandelt werden) nicht unterstützt.

Die Metadaten sollten Konfigurations Bedingungen für jede Konfiguration aufweisen, auch wenn Sie alle identisch sind. Beispiel:

```xml
<ItemGroup>
  <ClCompile Include="stdafx.cpp">
    <TreatWarningAsError Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'">true</TreatWarningAsError>
    <TreatWarningAsError Condition="'$(Configuration)|$(Platform)'=='Debug|x64'">true</TreatWarningAsError>
  </ClCompile>
</ItemGroup>
```

Das Visual Studio C++-Projekt System unterstützt derzeit keine Platzhalter in Projekt Elementen.

```xml
<ItemGroup>
  <ClCompile Include="*.cpp"> <!--Error-->
</ItemGroup>
```

Das Visual Studio C++-Projekt System unterstützt derzeit keine Makros in Projekt Elementen.

```xml
<ItemGroup>
  <ClCompile Include="$(IntDir)\generated.cpp"> <!--not guaranteed to work in all scenarios-->
</ItemGroup>
```

Verweise werden in einem ItemGroup-Element angegeben und haben folgende Einschränkungen:

- Verweise unterstützen keine Bedingungen.

- Verweis Metadaten unterstützen keine Bedingungen.

### <a name="microsoftcpptargets-import-element"></a>Import-Element „Microsoft.Cpp.targets“

```xml
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.targets" />
```

Definiert (direkt oder durch Importe) C++ Ziele wie Build, Clean usw.

### <a name="extensiontargets-importgroup-element"></a>ImportGroup-Element „ExtensionTargets“

```xml
<ImportGroup Label="ExtensionTargets" />
```

Diese Gruppe enthält Importe für die Zieldateien der Buildanpassung.

## <a name="impact-of-incorrect-ordering"></a>Auswirkungen einer falschen Reihenfolge

Die Visual Studio-IDE hängt von der Projektdatei ab, die die zuvor beschriebene Reihenfolge aufweist. Wenn Sie beispielsweise einen Eigenschaftswert auf den Eigenschaftenseiten definieren, platziert die IDE die Eigenschaftsdefinition generell in der Eigenschaftengruppe mit der leeren Bezeichnung. Durch diese Reihenfolge wird sichergestellt, dass die in den Systemeigenschaften Blätter eingebundenen Standardwerte von benutzerdefinierten Werten überschrieben werden. Entsprechend werden die Zieldateien am Ende importiert, da Sie die zuvor definierten Eigenschaften nutzen, und da Sie in der Regel keine Eigenschaften selbst definieren. Entsprechend werden Benutzereigenschaften Blätter nach den Systemeigenschaften Blättern (in enthalten) importiert *`Microsoft.Cpp.props`* . Mit dieser Reihenfolge wird sichergestellt, dass der Benutzer alle Standardwerte überschreiben kann, die von den System Eigenschafts Tabellen

Wenn eine *`.vcxproj`* Datei nicht diesem Layout folgt, entsprechen die Buildergebnisse möglicherweise nicht Ihren Erwartungen. Wenn Sie z. b. fälschlicherweise ein Systemeigenschaften Blatt nach den vom benutzerdefinierten Eigenschaften Blättern importieren, werden die Benutzereinstellungen durch die Systemeigenschaften Blätter überschrieben.

Selbst die IDE-Entwurfszeit Umgebung hängt in gewissem Umfang von der korrekten Reihenfolge der Elemente ab. Wenn Ihre Datei z. b *`.vcxproj`* . nicht über die `PropertySheets` Import Gruppe verfügt, kann die IDE möglicherweise nicht ermitteln, wo ein neues Eigenschaften Blatt platziert werden soll, das der Benutzer in **Eigenschaften-Manager**erstellt hat. Dies könnte dazu führen, dass ein Benutzer Blatt von einem System Blatt überschrieben wird. Obwohl die Heuristik, die von IDE verwendet wird, geringfügige Inkonsistenzen im *`.vcxproj`* Datei Layout tolerieren kann, wird dringend empfohlen, dass Sie nicht von der weiter oben in diesem Artikel gezeigten Struktur abweichen.

## <a name="how-the-ide-uses-element-labels"></a>Verwendung von Elementbezeichnungen durch die IDE

Wenn Sie in der IDE die **useOfATL** -Eigenschaft auf der Eigenschaften Seite "Allgemein" festlegen, wird Sie in die Konfigurations Eigenschaften Gruppe in der Projektdatei geschrieben. Die Eigenschaft " **TargetName** " auf der gleichen Eigenschaften Seite wird in die Bezeichnung "weniger Konfiguration pro Konfiguration" geschrieben. Visual Studio sucht in der XML-Datei der Eigenschaftenseite nach Informationen dazu, wohin jede Eigenschaft geschrieben werden soll. Wenn Sie auf der Eigenschaften Seite " **Allgemein** " eine englische Version von Visual Studio 2019 Enterprise Edition haben, lautet diese Datei `%ProgramFiles(x86)%\Microsoft Visual Studio\2019\Enterprise\Common7\IDE\VC\VCTargets\1033\general.xml` . Die XML-Regeldatei der Eigenschaftenseite definiert die statischen Informationen einer Regel und deren Eigenschaften. Eine dieser Informationen ist die bevorzugte Position einer Regeleigenschaft in der Zieldatei (die Datei, in die deren Wert geschrieben wird). Die bevorzugte Position wird vom Label-Attribut in den Elementen der Projektdatei angegeben.

## <a name="property-sheet-layout"></a>Layout von Eigenschaftenblättern

Der folgende XML-Codeausschnitt stellt das minimale Layout einer Eigenschaftenblattdatei (.props) dar. Sie ähnelt einer *`.vcxproj`* Datei, und die Funktionalität der *`.props`* Elemente kann aus der vorherigen Erörterung abgeleitet werden.

```xml
<Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <ImportGroup Label="PropertySheets" />
  <PropertyGroup Label="UserMacros" />
  <PropertyGroup />
  <ItemDefinitionGroup />
  <ItemGroup />
</Project>
```

Wenn Sie ein eigenes Eigenschaften Blatt erstellen möchten, kopieren Sie eine der *`.props`* Dateien im *`VCTargets`* Ordner, und ändern Sie Sie für Ihre Zwecke. Für Visual Studio 2019 Enterprise Edition lautet der Standard *`VCTargets`* Pfad `%ProgramFiles%\Microsoft Visual Studio\2019\Enterprise\Common7\IDE\VC\VCTargets` .

## <a name="see-also"></a>Weitere Informationen

[Festlegen des C++-Compilers und der Buildeigenschaften in Visual Studio](../working-with-project-properties.md)\
[XML-Dateien der Eigenschaften Seite](property-page-xml-files.md)\
[`.vcxproj` Dateien und Platzhalter](vcxproj-files-and-wildcards.md)
