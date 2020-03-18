---
title: Allgemeine Makros für MSBuild-Befehle und-Eigenschaften
ms.date: 08/02/2019
helpviewer_keywords:
- $(FrameworkSDKDir) macro
- ProjectName macro $(ProjectName)
- DevEnvDir macro $(DevEnvDir)
- $(DevEnvDir) macro
- TargetPath macro $(TargetPath)
- VSInstallDir macro $(VSInstallDir)
- $(InputFileName) macro
- $(SolutionFileName) macro
- macros [C++], build macros
- InputFileName macro $(InputFileName)
- $(VCInstallDir) macro
- $(IntDir) macro
- $(ConfigurationName) macro
- SolutionDir macro $(SolutionDir)
- $(TargetPath) macro
- $(Inherit) macro
- $(SolutionPath) macro
- WebDeployRoot macro $(WebDeployRoot)
- WebDeployPath macro $(WebDeployPath)
- StopEvaluating macro $(StopEvaluating)
- $(RootNamespace) macro
- $(WebDeployRoot) macro
- ProjectPath macro $(ProjectPath)
- $(ProjectPath) macro
- $(InputDir) macro
- SolutionName macro $(SolutionName)
- ProjectExt macro $(ProjectExt)
- $(TargetExt) macro
- $(ProjectFileName) macro
- TargetName macro $(TargetName)
- $(References) macro
- References macro $(References)
- TargetExt macro $(TargetExt)
- ProjectDir macro $(ProjectDir)
- $(TargetDir) macro
- SolutionExt macro $(SolutionExt)
- $(SolutionDir) macro
- ProjectFileName macro $(ProjectFileName)
- VCInstallDir macro $(VCInstallDir)
- $(InputExt) macro
- $(TargetFileName) macro
- $(SolutionExt) macro
- PlatformName macro $(PlatformName)
- IntDir macro $(IntDir)
- $(FrameworkVersion) macro
- $(ProjectDir) macro
- build macros [C++]
- InputPath macro $(InputPath)
- $(VSInstallDir) macro
- $(WebDeployPath) macro
- TargetFileName macro $(TargetFileName)
- NoInherit macro $(NoInherit)
- ConfigurationName macro $(ConfigurationName)
- $(ProjectExt) macro
- TargetDir macro $(TargetDir)
- InputName macro $(InputName)
- $(ProjectName) macro
- FrameworkSDKDir macro $(FrameworkSDKDir)
- $(ParentName) macro
- InputExt macro $(InputExt)
- $(SafeRootNamespace) macro
- InputDir macro $(InputDir)
- $(FxCopDir) macro
- $(RemoteMachine) macro
- Inherit macro $(Inherit)
- FrameworkVersion macro $(FrameworkVersion)
- $(StopEvaluating) macro
- $(OutDir) macro
- FrameworkDir macro $(FrameworkDir)
- SolutionFileName macro $(SolutionFileName)
- $(NoInherit) macro
- RemoteMachine macro $(RemoteMachine)
- properties [C++], build property macros
- $(TargetName) macro
- $(SolutionName) macro
- $(InputPath) macro
- ParentName macro $(ParentName)
- OutDir macro $(OutDir)
- SafeRootNamespace macro $(SafeRootNamespace)
- FxCopDir macro $(FxCopDir)
- $(InputName) macro
- RootNamespace macro $(RootNamespace)
- builds [C++], macros
- $(FrameworkDir) macro
- $(PlatformName) macro
- $(PlatformShortName) macro
- SolutionPath macro $(SolutionPath)
ms.assetid: 239bd708-2ea9-4687-b264-043f1febf98b
ms.openlocfilehash: 5038416a8df3282b426d3298c73520f78e962766
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79440172"
---
# <a name="common-macros-for-msbuild-commands-and-properties"></a>Allgemeine Makros für MSBuild-Befehle und-Eigenschaften

Abhängig von den Installationsoptionen können Sie in Visual Studio hunderte von Makros in einem Visual Studio-Projekt (basierend auf MSBuild) zur Verfügung stellen. Sie entsprechen den MSBuild-Eigenschaften, die standardmäßig festgelegt sind, oder in. Properties-oder Targets-Dateien oder in den Projekteinstellungen. Sie können diese Makros an einer beliebigen Stelle im Dialogfeld **Eigenschaftenseiten** eines Projekts verwenden, an der Zeichenfolgen akzeptiert werden. Bei diesen Makros wird keine Groß-/Kleinschreibung beachtet.

## <a name="view-the-current-properties-and-macros"></a>Anzeigen der aktuellen Eigenschaften und Makros

Wenn Sie alle momentan verfügbaren Makros anzeigen möchten, klicken Sie im Dialogfeld **Eigenschaften Seiten** unter **VC + +-Verzeichnisse**auf den Dropdown Pfeil am Ende einer Eigenschaften Zeile. Klicken Sie auf **Bearbeiten** , und wählen Sie dann im Dialogfeld bearbeiten die Schaltfläche **Makros** aus. Die aktuell für Visual Studio sichtbaren Eigenschaften und Makros werden jeweils zusammen mit dem aktuellen Wert aufgeführt. Weitere Informationen finden Sie im Abschnitt **Angeben von benutzerdefinierten Werten** der [ C++ Projekteigenschaften Seite-Referenz](property-pages-visual-cpp.md).

![Schaltfläche für VC + +-Makros](../media/vcppdir_libdir_macros.png "Makros (Menü)")

## <a name="list-of-common-macros"></a>Liste der häufig verwendeten Makros

Diese Tabelle beschreibt eine häufig verwendete Teilmenge der verfügbaren Makros. Hier sind noch viele weitere nicht aufgeführt. Wechseln Sie zum Dialogfeld **Makros** , um alle Eigenschaften und deren aktuelle Werte in Ihrem Projekt anzuzeigen. Ausführliche Informationen zum Erstellen von MSBuild-Eigenschaftsdefinitionen und wie diese als Makros in PROPS, TARGETS und VCXPROJ-Dateien verwendet werden, finden Sie unter [MSBuild-Eigenschaften](/visualstudio/msbuild/msbuild-properties).

|Makro|BESCHREIBUNG|
|-----------|-----------------|
|**$(Configuration)**|Der Name der aktuellen Projektkonfiguration, z.B. „Debug“.|
|**$(DevEnvDir)**|Das Installationsverzeichnis von Visual Studio (als „Laufwerk + Pfad“ definiert). Es enthält den nachgestellten umgekehrten Schrägstrich „\\“.|
|**$(FrameworkDir)**|Das Verzeichnis, in dem .NET Framework installiert wurde.|
|**$(FrameworkSDKDir)**|Das Verzeichnis, in dem Sie .NET Framework installiert haben. .NET Framework könnte als Teil von Visual Studio oder separat installiert worden sein.|
|**$(FrameworkVersion)**|Die Version von .NET Framework, die von Visual Studio verwendet wurde. In Kombination mit **$(FrameworkDir)** stellt dies den vollständigen Pfad zu der Version von .NET Framework dar, die von Visual Studio verwendet wurde.|
|**$(FxCopDir)**|Der Pfad zur Datei „fxcop.cmd“. Die Datei "FxCop. cmd" wird nicht mit allen Editionen von Visual Studio installiert.|
|**$(IntDir)**|Der Pfad zum Verzeichnis, das für Zwischendateien angegeben wurde. Wenn es sich um einen relativen Pfad handelt, werden zwischen Dateien an diesen Pfad angehängt, der an das Projektverzeichnis angefügt wird. Dieser Pfad sollte über einen nachgestellten Schrägstrich verfügen. Sie wird in den Wert für die Eigenschaft **zwischen Verzeichnis** aufgelöst. Verwenden Sie " **$ (OutDir)** " nicht, um diese Eigenschaft zu definieren.|
|**$(OutDir)**|Der Pfad zum Ausgabedateiverzeichnis. Wenn es sich um einen relativen Pfad handelt, werden Ausgabedateien an diesen Pfad weitergeleitet, der an das Projektverzeichnis angefügt wird. Dieser Pfad sollte über einen nachgestellten Schrägstrich verfügen. Sie wird in den Wert für die Eigenschaft **Ausgabeverzeichnis** aufgelöst. Verwenden Sie " **$ (IntDir)** " nicht, um diese Eigenschaft zu definieren.|
|**$(Platform)**|Der Name der aktuellen Projektplattform (z.B. „Win32“).|
|**$ (Platformshortname)**|Der Kurzname der aktuellen Architektur, z. b. "x86" oder "x64".|
|**$(ProjectDir)**|Das Verzeichnis des Projekts (als „Laufwerk + Pfad“ definiert). Es enthält den nachgestellten umgekehrten Schrägstrich „\\“.|
|**$(ProjectExt)**|Die Dateierweiterung des Projekts. Sie umfasst den „.“ vor der Dateierweiterung.|
|**$(ProjectFileName)**|Der Dateiname des Projekts (als „Basisname + Dateierweiterung“ definiert).|
|**$(ProjectName)**|Der Basisname des Projekts.|
|**$(ProjectPath)**|Der absolute Pfadname des Projekts (als „Laufwerk + Pfad + Basisname + Dateierweiterung“ definiert).|
|**$ (PublishDir)**|Der Ausgabe Speicherort für das Veröffentlichungsziel. schließt den nachfolgenden umgekehrten Schrägstrich '\\' ein. Der Standardwert ist der **$ (OutDir)-app. Publish\\** -Ordner.|
|**$(RemoteMachine)**|Auf der Debugeigenschaftenseite auf den Wert der **Remote Machine** -Eigenschaft festgelegt. Weitere Informationen finden Sie unter [Projekteinstellungen für eine C- oder C++-Debugkonfiguration](/visualstudio/debugger/project-settings-for-a-cpp-debug-configuration) .|
|**$(RootNameSpace)**|Der Namespace, falls vorhanden, der die Anwendung enthält.|
|**$(SolutionDir)**|Das Verzeichnis der Projektmappe (als „Laufwerk + Pfad“ definiert). Es enthält den nachgestellten umgekehrten Schrägstrich „\\“. Wird nur bei der Erstellung einer Projektmappe in der IDE definiert.|
|**$(SolutionExt)**|Die Dateierweiterung der Projektmappe. Sie umfasst den „.“ vor der Dateierweiterung. Wird nur bei der Erstellung einer Projektmappe in der IDE definiert.|
|**$(SolutionFileName)**|Der Dateiname der Projektmappe (als „Basisname + Dateierweiterung“ definiert). Wird nur bei der Erstellung einer Projektmappe in der IDE definiert.|
|**$(SolutionName)**|Der Basisname der Projektmappe. Wird nur bei der Erstellung einer Projektmappe in der IDE definiert.|
|**$(SolutionPath)**|Der absolute Pfadname der Projektmappe (als „Laufwerk + Pfad + Basisname + Dateierweiterung“ definiert). Wird nur bei der Erstellung einer Projektmappe in der IDE definiert.|
|**$(TargetDir)**|Das Verzeichnis der primären Ausgabedatei für den Build (als „Laufwerk + Pfad“ definiert). Es enthält den nachgestellten umgekehrten Schrägstrich „\\“.|
|**$(TargetExt)**|Die Dateierweiterung der primären Ausgabedatei für den Build. Sie umfasst den „.“ vor der Dateierweiterung.|
|**$(TargetFileName)**|Der Dateiname der primären Ausgabedatei für den Build (als „Basisname + Dateierweiterung“ definiert).|
|**$(TargetName)**|Der Basisname der primären Ausgabedatei für den Build.|
|**$(TargetPath)**|Der absolute Pfadname der primären Ausgabedatei für den Build (als „Laufwerk + Pfad + Basisname + Dateierweiterung“ definiert).|
|**$(VCInstallDir)**|Das Verzeichnis, das den C++-Inhalt Ihrer Visual Studio-Installation enthält. Diese Eigenschaft enthält die Version des zielsets von C++ Microsoft (MSVC), die sich möglicherweise vom Visual Studio-Host unterscheidet. Wenn Sie z. b. mit `$(PlatformToolset) = v140`aufbauen, enthält **$ (VCInstallDir)** den Pfad zur Installation von Visual Studio 2015.|
|**$(VSInstallDir)**|Das Verzeichnis, in dem Visual Studio installiert wurde. Diese Eigenschaft enthält die Version des angezielten Visual Studio-Toolsets, die sich möglicherweise vom Visual Studio-Host unterscheidet. Beim Erstellen mit `$(PlatformToolset) = v110`, enthält **$(VSInstallDir)** z. B. den Pfad zur Installation von Visual Studio 2012.|
|**$(WebDeployPath)**|Der relative Pfad vom Stamm der Webbereitstellung zum Speicherort der Projektausgaben.|
|**$(WebDeployRoot)**|Der absolute Pfad zum Speicherort von **\<localhost>** . Beispiel: „c:\inetpub\wwwroot“.|

## <a name="obsolete-macros"></a>Veraltete Makros

Das Buildsystem wurde zwischen Visual Studio 2008 und Visual Studio 2010 erheblich geändert. Viele Makros, die in früheren Projekttypen verwendet wurden, wurden durch neue ersetzt. Diese Makros werden nicht mehr verwendet oder wurden durch mindestens eine entsprechende Eigenschaft oder ein Makro für [Elementmetadatenwerte](/visualstudio/msbuild/itemmetadata-element-msbuild) ( **%(** _name_ **)** ) ersetzt. Makros, die als „Migriert“ markiert sind, können mithilfe des Migrationstools für Projekte aktualisiert werden. Wenn das Projekt, das das Makro enthält, zudem von Visual Studio 2008 oder früher zu Visual Studio 2010 migriert wird, konvertiert Visual Studio das Makro in das entsprechende aktuelle Makro. Höhere Versionen von Visual Studio können Projekte von Visual Studio 2008 und früher nicht in den neuen Projekttyp konvertieren. Sie müssen diese Projekte in zwei Schritten konvertieren. Konvertieren Sie sie zunächst in Visual Studio 2010, und konvertieren Sie das Ergebnis anschließend in ihre neuere Version von Visual Studio. Weitere Informationen finden Sie in der [Übersicht über potenzielle Probleme beim Upgrade](../../porting/overview-of-potential-upgrade-issues-visual-cpp.md).

|Makro|BESCHREIBUNG|
|-----------|-----------------|
|**$(InputDir)**|(Migriert.) Das Verzeichnis der Eingabedatei (definiert als Laufwerk + Pfad). schließt den nachfolgenden umgekehrten Schrägstrich '\\' ein. Wenn das Projekt die Eingabe darstellt, entspricht dieses Makro **$(ProjectDir)** .|
|**$(InputExt)**|(Migriert.) Die Dateierweiterung der Eingabedatei. Sie umfasst den „.“ vor der Dateierweiterung. Wenn das Projekt die Eingabe darstellt, entspricht dieses Makro **$(ProjectExt)** . Für Quelldateien entspricht dies **%(Extension)** .|
|**$(InputFileName)**|(Migriert.) Der Dateiname der Eingabedatei (als "Basisname + Dateierweiterung" definiert). Wenn das Projekt die Eingabe darstellt, entspricht dieses Makro **$(ProjectFileName)** . Für Quelldateien entspricht dies **%(Identity)** .|
|**$(InputName)**|(Migriert.) Der Basisname der Eingabedatei. Wenn das Projekt die Eingabe darstellt, entspricht dieses Makro **$(ProjectName)** . Für Quelldateien entspricht dies **%(Filename)** .|
|**$(InputPath)**|(Migriert.) Der absolute Pfadname der Eingabedatei (als "Laufwerk + Pfad + Basisname + Dateierweiterung" definiert). Wenn das Projekt die Eingabe darstellt, entspricht dieses Makro **$(ProjectPath)** . Für Quelldateien entspricht dies **%(FullPath)** .|
|**$(ParentName)**|Der Name des Elements, das dieses Projektelement enthält. Dies wird der Name des übergeordneten Ordners oder der Projektname sein.|
|**$(SafeInputName)**|Der Name der Datei als gültiger Klassenname, ohne die Dateierweiterung. Für diese Eigenschaft gibt es keine genaue Entsprechung.|
|**$(SafeParentName)**|Der Name des unmittelbar übergeordneten Elements im gültigen Namensformat. Ein Formular ist beispielsweise das übergeordnete Element einer RESX-Datei. Für diese Eigenschaft gibt es keine genaue Entsprechung.|
|**$(SafeRootNamespace)**|Der Namespacename, in dem die Projekt-Assistenten Code hinzufügen. Dieser Namespacename darf nur Zeichen enthalten, die in einem gültigen C++-Bezeichner zulässig sind. Für diese Eigenschaft gibt es keine genaue Entsprechung.|

## <a name="see-also"></a>Weitere Informationen

[Visual Studio-Projekte C++ -](../creating-and-managing-visual-cpp-projects.md)\
[Handbuch C++ zum Visual portieren und upgraden](../../porting/visual-cpp-porting-and-upgrading-guide.md)\
[Überblick über potenzielle Upgradeprobleme (Visual C++)](../../porting/overview-of-potential-upgrade-issues-visual-cpp.md)
