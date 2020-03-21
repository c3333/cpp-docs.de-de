---
title: Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio
description: Verwenden Sie die Visual Studio-IDE C++ , um Compiler-und Linkeroptionen und andere Buildeinstellungen zu ändern.
ms.date: 07/17/2019
helpviewer_keywords:
- project properties [C++], modifying
- properties [C++]
- Visual C++ projects, properties
- projects [C++], properties
ms.assetid: 9b0d6f8b-7d4e-4e61-aa75-7d14944816cd
ms.openlocfilehash: 6c05dd00324113819dd145e46bf10dfeb96a66a3
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "80078235"
---
# <a name="set-compiler-and-build-properties"></a>Festlegen von compilerund Buildeigenschaften

In der IDE werden alle Informationen, die für das Erstellen eines Projekts erforderlich sind, als *Eigenschaften* verfügbar gemacht. Zu diesen Informationen zählen unter anderem der Anwendungsname, die Erweiterung (z.B. DLL, LIB, EXE), Compileroptionen, Linkeroptionen, Debuggereinstellungen und benutzerdefinierte Buildschritte. In der Regel verwenden Sie Eigenschaften *Seiten* , um diese Eigenschaften anzuzeigen und zu ändern. Wählen Sie zum Zugreifen auf die Eigenschaften Seiten im Hauptmenü **Project** >  **_ProjectName_ -Eigenschaften** aus, oder klicken Sie mit der rechten Maustaste in **Projektmappen-Explorer** auf den Projekt Knoten, und wählen Sie **Eigenschaften**aus.

## <a name="default-properties"></a>Standardeigenschaften

Wenn Sie ein Projekt erstellen, weist das System verschiedenen Eigenschaften Werte zu. Die Standardwerte variieren in Abhängigkeit von der Art des Projekts und den Optionen, die Sie im App-Assistenten auswählen. Ein ATL-Projekt verfügt beispielsweise über Eigenschaften für MIDL-Dateien. Diese sind jedoch in einer Basiskonsolenanwendung nicht vorhanden. Die Standardeigenschaften werden im Bereich „Allgemein“ auf den Eigenschaftenseiten angezeigt:

![Visual C&#43; &#43; -Projekt Standardwerte](media/visual-c---project-defaults.png "Visual C++ Project-Standardwerte")

## <a name="applying-properties-to-build-configurations-and-target-platforms"></a>Anwenden von Eigenschaften auf Buildkonfigurationen und Zielplattformen

Einige Eigenschaften (z.B. der Anwendungsname) gelten für alle Buildvarianten, unabhängig von der Zielplattform oder davon, ob es sich um einen Debug- oder um einen Releasebuild handelt. Die meisten Eigenschaften hängen jedoch von Konfigurationen ab. Das liegt daran, dass der Compiler wissen muss, auf welcher Plattform das Programm ausgeführt wird und welche Compileroptionen verwendet werden müssen, um den richtigen Code zu generieren. Wenn Sie eine Eigenschaft festlegen, sollten Sie deshalb darauf achten, für welche Konfiguration und welche Plattform der neue Wert gelten soll. Soll sie nur für Win32-Debugbuilds oder ebenfalls für ARM- und x64-Debugbuilds gelten? Die Eigenschaft **Optimierung** ist in einer Releasekonfiguration beispielsweise standardmäßig auf **Geschwindigkeit maximieren (/O2)** festgelegt. In einer Debugkonfiguration ist sie jedoch deaktiviert.

Die Eigenschaftenseiten wurden so entwickelt, dass Sie immer sehen und bei Bedarf ändern können, für welche Konfiguration und Plattform ein Eigenschaftswert gelten soll. Die folgende Abbildung zeigt die Eigenschaftenseiten mit Informationen zur Konfiguration und zur Plattform in den Listenfeldern im oberen Bereich. Wenn die Eigenschaft **Optimierung** hier festgelegt ist, gilt diese nur für Win32-Debugbuilds. Dies ist die aktive Konfiguration (angezeigt durch die roten Pfeile).

![Visual C&#43; &#43; -Eigenschaften Seiten mit aktiver Konfiguration](media/visual-c---property-pages-showing-active-configuration.png "Visuelle C++ Eigenschaften Seiten, die eine aktive Konfiguration zeigen")

Die folgende Abbildung zeigt dieselbe Eigenschaftenseite des Projekts, allerdings wurde die Konfiguration in „Release“ geändert. Beachten Sie den geänderten Wert der Eigenschaft „Optimierung“. Beachten Sie außerdem, dass die aktive Konfiguration immer noch „Debug“ ist. Sie können hier Eigenschaften für jede Konfiguration festlegen. Diese müssen nicht der aktiven Konfiguration entsprechen.

![Visual C&#43; &#43; -Eigenschaften Seiten mit Releasekonfiguration](media/visual-c---property-pages-showing-release-config.png "Visuelle C++ Eigenschaften Seiten mit Releasekonfiguration")

## <a name="target-platforms"></a>Zielplattformen

*Zielplattform* bezieht sich auf den Gerätetyp und/oder das Betriebssystem, auf dem die ausführbare Datei ausgeführt wird. Sie können ein Projekt für mehr als eine Plattform erstellen. Die verfügbaren Zielplattformen für C++-Projekte hängen von der Art des Projekts ab. Unter anderem sind Win32, x64, ARM, Android und iOS verfügbar.     Die Zielplattform **x86**, die im **Konfigurations-Manager** angezeigt wird, entspricht **Win32** in nativen C++-Projekten. Win32 bedeutet 32-Bit-Windows, und **x64** bedeutet 64-Bit-Windows. Weitere Informationen zu diesen beiden Plattformen finden Sie unter [Ausführung von 32-Bit-Anwendungen](/windows/win32/WinProg64/running-32-bit-applications).

Der Wert **Beliebige CPU**, den Sie im **Konfigurations-Manager** für die Zielplattform sehen, hat keine Auswirkung auf native C++-Projekte. Er ist nur für C++/CLI- und andere .NET-Projekttypen relevant. Weitere Informationen finden Sie unter [/CLRIMAGETYPE (Angeben des CLR-Bildtyps)](reference/clrimagetype-specify-type-of-clr-image.md).

Weitere Informationen zum Festlegen von Eigenschaften für einen Debugbuild finden Sie unter:

- [Projekteinstellungen für eine C++-Debugkonfiguration](/visualstudio/debugger/project-settings-for-a-cpp-debug-configuration)
- [Debuggereinstellungen und -vorbereitung](/visualstudio/debugger/debugger-settings-and-preparation)
- [Vorbereitung zum Debuggen: Visual C++-Projekttypen](/visualstudio/debugger/debugging-preparation-visual-cpp-project-types)
- [Angeben von Symbol- (PDB-) und Quelldateien im Visual Studio Debugger](/visualstudio/debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger)

## <a name="c-compiler-and-linker-options"></a>C++Optionen für Compiler und Linker

C++Optionen für Compiler und Linker befinden sich unter den Knoten **C/C++**  und **Linker** im linken Bereich unter **Konfigurations Eigenschaften**. Diese übersetzen direkt in Befehlszeilenoptionen, die an den Compiler übermittelt werden. Um die Dokumentation zu einer bestimmten Option zu lesen, wählen Sie die Option im mittleren Bereich aus, und drücken Sie **F1**. Sie können auch die Dokumentation zu allen Optionen unter [MSVC-Compileroptionen](reference/compiler-options.md) und [MSVC-Linkeroptionen](reference/linker-options.md)durchsuchen.

Im Dialogfeld **Eigenschaften Seiten** werden nur die Eigenschaften Seiten angezeigt, die für das aktuelle Projekt relevant sind. Wenn das Projekt beispielsweise keine IDL-Datei enthält, wird die MIDL-Eigenschaftenseite nicht angezeigt. Weitere Informationen zu den Einstellungen auf den einzelnen Eigenschaften Seiten finden Sie unter [Eigenschaften SeitenC++()](reference/property-pages-visual-cpp.md).

## <a name="directory-and-path-values"></a>Verzeichnis-und Pfadwerte

MSBuild unterstützt die Verwendung von Kompilierzeit Konstanten, die als "Makros" bezeichnet werden, für bestimmte Zeichen folgen Werte, die Verzeichnisse und Pfade enthalten. Diese werden in den Eigenschaften Seiten verfügbar gemacht, auf die Sie mithilfe des [Eigenschaften-Editors](#property_editor)verweisen und diese ändern können.

Die folgende Abbildung zeigt die Eigenschaften Seiten für ein Visual Studio C++ -Projekt. Im linken Bereich ist die Regel **VC + +-Verzeichnisse** *rule* ausgewählt, und im rechten Bereich werden die Eigenschaften aufgelistet, die dieser Regel zugeordnet sind. Die `$(...)` Werte werden als *Makros*bezeichnet. Ein *Makro* ist eine Kompilierzeitkonstante, die auf einen benutzerdefinierten Wert oder auf einen Wert verweisen kann, der von Visual Studio oder dem MSBuild-System definiert wurde. Durch die Verwendung von Makros anstelle von hart codierten Werten, wie z. b. Verzeichnis Pfaden, können Sie Eigenschafts Einstellungen zwischen Computern und Versionen von Visual Studio einfacher freigeben, und Sie können besser sicherstellen, dass Ihre Projekteinstellungen ordnungsgemäß an der [Eigenschaften Vererbung](project-property-inheritance.md)teilnehmen.

![Projekteigenschaften Seiten](media/project_property_pages_vc.png "Project_Property_Pages_VC")

Sie können den Eigenschaften-Editor verwenden, um die Werte aller verfügbaren Makros anzuzeigen.

### <a name="predefined-macros"></a>Vordefinierte Makros

*Globale Makros*<br/>
Gilt für alle Elemente in einer Projektkonfiguration. Besitzt die Syntax `$(name)`. Ein Beispiel eines globalen Makros ist `$(VCInstallDir)`, das das Stammverzeichnis der Visual Studio-Installation speichert. Ein globales Makro entspricht einer `PropertyGroup` in MSBuild.

*Elementmakros*<br/>
Besitzt die Syntax `%(name)`. Bei einer Datei gilt ein Elementmakro nur für diese Datei – z. B. können Sie `%(AdditionalIncludeDirectories)` verwenden, um Includeverzeichnisse anzugeben, die nur für eine bestimmte Datei gelten. Diese Art des Elementmakros entspricht den `ItemGroup`-Metadaten in MSBuild. Wenn ein Elementmakro im Zusammenhang mit einer Projektkonfiguration verwendet wird, gilt es für alle Dateien eines bestimmten Typs. Beispielsweise kann die C/C++-Konfigurationseigenschaft **Präprozessordefinitionen** ein `%(PreprocessorDefinitions)`-Elementmakro verwenden, das für alle CPP-Dateien im Projekt gilt. Diese Art des Elementmakros entspricht den `ItemDefinitionGroup`-Metadaten in MSBuild. Weitere Informationen finden Sie unter [Item Definitions (Elementdefinitionen)](/visualstudio/msbuild/item-definitions).

### <a name="user-defined-macros"></a>benutzerdefinierte Makros

Sie können *benutzerdefinierte Makros* erstellen, um sie als Variablen in Projektbuilds zu verwenden. Sie können z. B. ein benutzerdefiniertes Makro erstellen, das einen Wert für einen benutzerdefinierten Buildschritt oder ein benutzerdefiniertes Buildtool bereitstellt. Ein benutzerdefiniertes Makro ist ein Name-Wert-Paar. Verwenden Sie in einer Projektdatei die Notation **$(** <em>name</em> **)** , um auf den Wert zuzugreifen.

Ein benutzerdefiniertes Makro wird in einem Eigenschaftenblatt gespeichert. Wenn das Projekt noch kein Eigenschaften Blatt enthält, können Sie eines erstellen, indem Sie die Schritte unter [freigeben oder wieder verwenden von Visual Studio-Projekteinstellungen](create-reusable-property-configurations.md)ausführen.

#### <a name="to-create-a-user-defined-macro"></a>So erstellen Sie ein benutzerdefiniertes Makro

1. Öffnen Sie das Fenster **Eigenschaften-Manager** . (Wählen Sie in der Menüleiste > **Eigenschaften-Manager** **anzeigen** oder > **anderen Windows** - > **Eigenschaften-Manager** **anzeigen** aus.) Öffnen Sie das Kontextmenü für ein Eigenschaften Blatt (der Name endet auf. User), und wählen Sie dann **Eigenschaften**aus. Das Dialogfeld **Eigenschaftenseiten** für dieses Eigenschaftenblatt wird geöffnet.

1. Klicken Sie im linken Bereich des Dialogfelds auf **Benutzermakros**. Klicken Sie im rechten Bereich auf die Schaltfläche **Makro hinzufügen**, um das Dialogfeld **Benutzermakro hinzufügen** zu öffnen.

1. Geben Sie im Dialogfeld einen Namen und einen Wert für das Makro an. Optional können Sie das Kontrollkästchen **Makro als Umgebungsvariable in Buildumgebung festlegen** aktivieren.

## <a name=""></a><a name="property_editor">Eigenschaften-Editor</a>

Mit dem Eigenschaften-Editor können Sie bestimmte Zeichenfolgeneigenschaften ändern und Makros als Werte auswählen. Um auf den Eigenschaften-Editor zuzugreifen, wählen Sie eine Eigenschaft auf einer Eigenschaftenseite aus, und klicken Sie rechts auf die Schaltfläche mit dem Pfeil nach unten. Wenn die Dropdownliste die Option **\<Bearbeiten>** enthält, können Sie auf diese klicken, um den Eigenschaften-Editor für diese Eigenschaft anzuzeigen.

![Dropdown Menü für Eigenschaften&#95;-Editor&#95;](media/property_editor_dropdown.png "Property_Editor_Dropdown")

Im Eigenschaften-Editor können Sie auf die Schaltfläche **Makros** klicken, um die verfügbaren Makros und deren aktuelle Werte anzuzeigen. Die folgende Abbildung zeigt den Eigenschaften-Editor für die Eigenschaft **Zusätzliche Includeverzeichnisse**, nachdem auf die Schaltfläche **Makros** geklickt wurde. Wenn das Kontrollkästchen **Vom übergeordneten Projekt erben oder Projektstandard** aktiviert ist und Sie einen neuen Wert hinzufügen, wird dieser an alle Werte angefügt, die derzeit vererbt werden. Wenn Sie das Kontrollkästchen deaktivieren, ersetzt der neue Wert die vererbten Werte. In den meisten Fällen bleibt das Kontrollkästchen aktiviert.

![Eigenschaften-Editor, Visual C&#43;&#43;](media/propertyeditorvc.png "PropertyEditor VC")

## <a name="add-an-include-directory-to-the-set-of-default-directories"></a>Hinzufügen eines includeverzeichnisses zum Satz von Standardverzeichnissen

Wenn Sie einem Projekt ein Includeverzeichnis hinzufügen, ist es wichtig darauf zu achten, die Standardverzeichnisse nicht zu überschreiben. Die richtige Methode, ein Verzeichnis hinzuzufügen, besteht darin, den neuen Pfad anzufügen (z.B. C:\MeinNeuesIncludeVerz\"), und dann das Makro **$(IncludePath)** an den Eigenschaftswert anzufügen.

## <a name="quickly-browse-and-search-all-properties"></a>Schnelles Durchsuchen und Durchsuchen aller Eigenschaften

Die Eigenschaftenseite **Alle Optionen** (unter dem Knoten **Konfigurationseigenschaften > C/C++** im linken Bereich des Dialogfelds **Eigenschaftenseiten**) bietet eine schnelle Möglichkeit, die Eigenschaften zu durchsuchen, die im aktuellen Kontext verfügbar sind, und nach ihnen zu suchen. Über ein spezielles Suchfeld und eine einfache Syntax können Sie Ergebnisse filtern:

Kein Präfix:<br/>
Suche nur in den Eigenschaftennamen (untergeordnete Zeichenfolge ohne Berücksichtigung der Groß-/Kleinschreibung)

'/' oder '-' :<br/>
Suche nur in den Compilerschaltern (Präfix ohne Berücksichtigung der Groß-/Kleinschreibung)

A:<br/>
Suche nur in Werten (untergeordnete Zeichenfolge ohne Berücksichtigung der Groß-/Kleinschreibung)

## <a name="set-environment-variables-for-a-build"></a>Festlegen von Umgebungsvariablen für einen Build

Der MSVC-Compiler (cl. exe) erkennt bestimmte Umgebungsvariablen, insbesondere lib, LIBPATH, Path und include. Wenn Sie die Erstellung mit der IDE vornehmen, werden die Eigenschaften, die auf der Eigenschaftenseite [VC++-Verzeichnisse](reference/vcpp-directories-property-page.md) festgelegt sind, zum Festlegen der Umgebungsvariablen verwendet. Wenn LIB-, LIBPATH- und INCLUDE-Werte bereits festgelegt wurden, beispielsweise durch eine Developer-Eingabeaufforderung, werden diese durch die Werte der entsprechenden MSBuild-Eigenschaften ersetzt. Der Build stellt dann PATH den Wert der ausführbaren Verzeichniseigenschaft VC++-Verzeichnisse voran. Sie können eine benutzerdefinierte Umgebungsvariable festlegen, indem Sie ein benutzerdefiniertes Makro erstellen und dann das Kontrollkästchen **Makro als Umgebungsvariable in Buildumgebung festlegen** aktivieren.

## <a name="set-environment-variables-for-a-debugging-session"></a>Festlegen von Umgebungsvariablen für eine Debugsitzung

Erweitern Sie im linken Bereich des Dialogfelds **Eigenschaftenseiten** die **Konfigurationseigenschaften** des Projekts, und klicken Sie auf **Debugging**.

Ändern Sie im rechten Bereich die Projekteinstellungen **Umgebung** oder **Mergeumgebung**, und klicken Sie dann auf die Schaltfläche **OK**.

## <a name="in-this-section"></a>In diesem Abschnitt

[Freigeben oder Wiederverwenden von Visual Studio-Projekteinstellungen](create-reusable-property-configurations.md)<br/>
Erstellen einer.-Eigenschaften Datei mit benutzerdefinierten Buildeinstellungen, die freigegeben oder wieder verwendet werden können.

[Vererbung von Projekteigenschaften](project-property-inheritance.md)<br/>
Beschreibt die Auswertungs Reihenfolge für die.-Eigenschaften, Targets-, vcxproj-Dateien und Umgebungsvariablen im Buildprozess.

[Ändern von Eigenschaften und Zielen ohne Änderungen an der Projektdatei](modify-project-properties-without-changing-project-file.md)<br/>
Erstellen temporärer Buildeinstellungen, ohne dass eine Projektdatei geändert werden muss.

## <a name="see-also"></a>Weitere Informationen

[Visual Studio-Projekte: C++](creating-and-managing-visual-cpp-projects.md)<br/>
[VCXPROJ- und PROPS-Dateistruktur](reference/vcxproj-file-structure.md)<br/>
[Eigenschaftenseite: XML-Dateien](reference/property-page-xml-files.md)<br/>
