---
title: MSBuild-Interna für C++-Projekte in Visual Studio
ms.date: 02/26/2020
helpviewer_keywords:
- MSBuild overview
ms.assetid: dd258f6f-ab51-48d9-b274-f7ba911d05ca
ms.openlocfilehash: c52434fa4b652d52baea70df705920db4ee68a5f
ms.sourcegitcommit: 65fead53d56d531d71be42216056aca5f44def11
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/19/2020
ms.locfileid: "88610846"
---
# <a name="msbuild-internals-for-c-projects"></a>MSBuild-Interna für C++-Projekte

Wenn Sie Projekteigenschaften in der IDE festlegen und dann das Projekt speichern, schreibt Visual Studio die Projekteinstellungen in die Projektdatei. Die Projektdatei enthält Einstellungen, die für Ihr Projekt eindeutig sind. Sie enthält jedoch nicht alle Einstellungen, die zum Erstellen des Projekts erforderlich sind. Die Projektdatei enthält `Import`-Elemente, die ein Netzwerk zusätzlicher *Supportdateien* beinhalten. Die Unterstützungs Dateien enthalten die restlichen Eigenschaften, Ziele und Einstellungen, die zum Erstellen des Projekts erforderlich sind.

Die meisten Ziele und Eigenschaften in den Unterstützungsdateien dienen ausschließlich der Implementierung des Buildsystems. In diesem Artikel werden nützliche Ziele und Eigenschaften erläutert, die Sie in der MSBuild-Befehlszeile angeben können. Durchsuchen Sie die Dateien in den Unterstützungsdateiverzeichnissen, um mehr Ziele und Eigenschaften zu ermitteln.

## <a name="support-file-directories"></a>Supportdateiverzeichnisse

Standardmäßig befinden sich die primären Visual Studio-Supportdateien in den folgenden Verzeichnissen. Diese Informationen sind Versions spezifisch.

### <a name="visual-studio-2019"></a>Visual Studio 2019

- % VSInstallDir% MSBuild \\ Microsoft \\ VC- \\ *Version*\\

  Enthält die primären Zieldateien (TARGETS-Format) und Eigenschaftendateien (PROPS-Format), die von den Zielen verwendet werden. Standardmäßig verweist das $ (VCTargetsPath)-Makro auf dieses Verzeichnis. Der *Versions* Platzhalter verweist auf die Visual Studio-Version: V160 for Visual Studio 2019, V150 for Visual Studio 2017.

- % VSInstallDir% MSBuild \\ \\ Plattform für \\ *version* \\ Plattformen \\ *platform* von Microsoft VC\\

  Enthält plattformspezifische Ziel- und Eigenschaftsdateien, die die Ziele und Eigenschaften im übergeordneten Verzeichnis außer Kraft setzen. Dieses Verzeichnis enthält außerdem eine DLL, die die von den Zielen in diesem Verzeichnis verwendeten Aufgaben definiert. Der Platzhalter *Plattform* steht für das ARM-, Win32- oder x64-Unterverzeichnis.

- % VSInstallDir% MSBuild \\ Microsoft \\ VC \\ *Version* \\ Platforms \\ *Plattform* \\ platformtoolsets \\ *Toolset*\\

  Enthält die Verzeichnisse, die es dem Build ermöglichen, C++-Anwendungen mit dem angegebenen *Toolset* zu generieren. Der Platzhalter *Plattform* steht für das ARM-, Win32- oder x64-Unterverzeichnis. Der *toolsetplatzhalter* stellt das toolsetunterverzeichnis dar.

### <a name="visual-studio-2017"></a>Visual Studio 2017

- % VSInstallDir% Common7 \\ IDE \\ VC \\ vctargets\\

  Enthält die primären Zieldateien (TARGETS-Format) und Eigenschaftendateien (PROPS-Format), die von den Zielen verwendet werden. Standardmäßig verweist das $ (VCTargetsPath)-Makro auf dieses Verzeichnis.

- % VSInstallDir% Common7 \\ IDE \\ VC \\ vctargets \\ Platforms \\ *Platform*\\

  Enthält plattformspezifische Ziel- und Eigenschaftsdateien, die die Ziele und Eigenschaften im übergeordneten Verzeichnis außer Kraft setzen. Dieses Verzeichnis enthält außerdem eine DLL, die die von den Zielen in diesem Verzeichnis verwendeten Aufgaben definiert. Der Platzhalter *Plattform* steht für das ARM-, Win32- oder x64-Unterverzeichnis.

- % VSInstallDir% Common7 \\ IDE \\ VC \\ vctargets \\ Platforms \\ *Platform* \\ platformtoolsets- \\ *Toolset*\\

  Enthält die Verzeichnisse, die es dem Build ermöglichen, C++-Anwendungen mit dem angegebenen *Toolset* zu generieren. Der Platzhalter *Plattform* steht für das ARM-, Win32- oder x64-Unterverzeichnis. Der *toolsetplatzhalter* stellt das toolsetunterverzeichnis dar.

### <a name="visual-studio-2015-and-earlier"></a>Visual Studio 2015 und frühere Versionen

- *Laufwerk*: \\ Programmdateien *(x86)* \\ MSBuild \\ Microsoft. cpp (x86) \\ v 4.0 \\ *Version*\\

  Enthält die primären Zieldateien (TARGETS-Format) und Eigenschaftendateien (PROPS-Format), die von den Zielen verwendet werden. Standardmäßig verweist das $ (VCTargetsPath)-Makro auf dieses Verzeichnis.

- *Laufwerk*: \\ Programme *(x86)* \\ MSBuild \\ Microsoft. cpp \\ v 4.0 \\ *Version* \\ Platforms \\ *Plattform*\\

  Enthält plattformspezifische Ziel- und Eigenschaftsdateien, die die Ziele und Eigenschaften im übergeordneten Verzeichnis außer Kraft setzen. Dieses Verzeichnis enthält außerdem eine DLL, die die von den Zielen in diesem Verzeichnis verwendeten Aufgaben definiert. Der Platzhalter *Plattform* steht für das ARM-, Win32- oder x64-Unterverzeichnis.

- *Laufwerk*: \\ Programmdateien *(x86)* \\ MSBuild \\ Microsoft. cpp \\ v 4.0 \\ *Versions* \\ Plattformen \\ *Platform* \\ platformtoolsets \\ *Toolset*\\

  Enthält die Verzeichnisse, die es dem Build ermöglichen, C++-Anwendungen mit dem angegebenen *Toolset* zu generieren. Der *Versions* Platzhalter ist v110 für Visual Studio 2012, V120 für Visual Studio 2013 und V140 für Visual Studio 2015. Der Platzhalter *Plattform* steht für das ARM-, Win32- oder x64-Unterverzeichnis. Der *toolsetplatzhalter* stellt das toolsetunterverzeichnis dar. Beispielsweise ist es V140 zum Entwickeln von Windows-apps mit dem Visual Studio 2015-Toolset. Oder v120_xp für Windows XP mithilfe des Visual Studio 2013 Toolsets erstellt werden.

- *Laufwerk*: \\ Programme *(x86)* \\ MSBuild \\ Microsoft. cpp \\ v 4.0 \\ Plattformen Platt \\ *Form Plattform* \\ platformtoolsets \\ *Toolset*\\

  Die Pfade, mit denen der Build entweder Visual Studio 2008-oder Visual Studio 2010-Anwendungen generieren kann, enthalten nicht die- *Version*. In diesen Versionen stellt der *Platt Form* Platzhalter das Unterverzeichnis Itanium, Win32 oder x64 dar. Der *Toolset*-Platzhalter stellt das Toolsetunterverzeichnis v90 oder v100 dar.

## <a name="support-files"></a>Supportdateien

Die Supportdateiverzeichnisse enthalten Dateien mit diesen Erweiterungen:

| Durchwahl | BESCHREIBUNG |
| --------- | ----------- |
| TARGETS | Enthält `Target`-XML-Elemente, die die vom Ziel ausgeführten Aufgaben angeben. Enthält auch `PropertyGroup`-, `ItemGroup`- und `ItemDefinitionGroup`-Elemente sowie benutzerdefinierte `Item`-Elemente, die zum Zuweisen von Dateien und Befehlszeilenoptionen zu Aufgabenparametern verwendet werden.<br /><br /> Weitere Informationen finden Sie unter [Zielelement (MSBuild)](/visualstudio/msbuild/target-element-msbuild). |
| PROPS | Enthält `Property Group`-XML-Elemente und benutzerdefinierte `Property`-XML-Elemente, die während eines Builds verwendete Datei- und Parametereinstellungen angeben.<br /><br /> Enthält auch `ItemDefinitionGroup`-XML-Elemente und benutzerdefinierte `Item`-XML-Elemente, die zusätzliche Einstellungen angeben. In einer Element Definitions Gruppe definierte Elemente ähneln Eigenschaften, aber von der Befehlszeile aus kann nicht darauf zugegriffen werden. Visual Studio-Projektdateien verwenden häufig Elemente statt Eigenschaften, um Einstellungen darzustellen.<br /><br /> Weitere Informationen finden Sie unter [ItemGroup-Element (MSBuild)](/visualstudio/msbuild/itemgroup-element-msbuild), [ItemDefinitionGroup-Element (MSBuild)](/visualstudio/msbuild/itemdefinitiongroup-element-msbuild)und [Item-Element (MSBuild)](/visualstudio/msbuild/item-element-msbuild). |
| .xml | Enthält XML-Elemente, die IDE-Benutzeroberflächen Elemente deklarieren und initialisieren. Beispielsweise Eigenschaften Blätter, Eigenschaften Seiten, Textfeld-Steuerelemente und ListBox-Steuerelemente.<br /><br /> Die XML-Dateien unterstützen direkt die IDE, nicht MSBuild. Die Werte von IDE-Eigenschaften werden jedoch zur Erstellung von Eigenschaften und Elementen verwendet.<br /><br /> Die meisten XML-Dateien befinden sich in einem gebietsschemaspezifischen Unterverzeichnis. Dateien für die Region "Englisch-US" befinden sich beispielsweise in "$ (vctargetspath) \\ 1033" \\ . |

## <a name="user-targets-and-properties"></a>Benutzerziele und -eigenschaften

Um MSBuild effektiv zu verwenden, ist es hilfreich zu wissen, welche Eigenschaften und Ziele nützlich und relevant sind. Die meisten Eigenschaften und Ziele helfen dabei, das Visual Studio-Buildsystem zu implementieren und sind daher für den Benutzer nicht relevant. In diesem Abschnitt werden benutzerorientierte Eigenschaften und Ziele beschrieben, die Sie kennen sollten.

### <a name="platformtoolset-property"></a>PlatformToolset-Eigenschaft

Die `PlatformToolset`-Eigenschaft bestimmt, welches MSVC-Toolset im Build verwendet wird. Standardmäßig wird das aktuelle Toolset verwendet. Wenn diese Eigenschaft festgelegt ist, wird Ihr Wert mit Literalzeichenfolgen verkettet, um den Pfad zu bilden. Dabei handelt es sich um das Verzeichnis, das die Eigenschaften-und Zieldateien enthält, die zum Erstellen eines Projekts für eine bestimmte Plattform erforderlich sind. Das Plattformtoolset muss installiert sein, um Builds mithilfe dieser Plattform-Toolsetversion zu erstellen.

Legen Sie beispielsweise die `PlatformToolset`-Eigenschaft auf `v140` fest, um zur Erstellung der Anwendung Visual Studio 2015-Tools und Bibliotheken zu verwenden:

`msbuild myProject.vcxproj /p:PlatformToolset=v140`

### <a name="preferredtoolarchitecture-property"></a>PreferredToolArchitecture-Eigenschaft

Die `PreferredToolArchitecture`-Eigenschaft bestimmt, ob der 32-Bit- oder 64-Bit-Compiler sowie die entsprechenden Tools im Build verwendet werden. Diese Eigenschaft hat keine Auswirkung auf die Architektur oder Konfiguration der Ausgabe Plattform. Standardmäßig verwendet MSBuild die x86-Version des Compilers und der Tools, wenn diese Eigenschaft nicht festgelegt ist.

Legen Sie beispielsweise die `PreferredToolArchitecture`-Eigenschaft auf `x64` fest, um den 64-Bit-Compiler und 64-Bit-Tools zum Erstellen Ihrer Anwendung zu verwenden:

`msbuild myProject.vcxproj /p:PreferredToolArchitecture=x64`

### <a name="useenv-property"></a>UseEnv-Eigenschaft

Standardmäßig setzen die plattformspezifischen Einstellungen für das aktuelle Projekt die PATH-, INCLUDE-, LIB-, LIBPATH-, CONFIGURATION- und PLATFORM-Umgebungsvariablen außer Kraft. Legen Sie die- `UseEnv` Eigenschaft auf fest, **`true`** um sicherzustellen, dass die Umgebungsvariablen nicht überschrieben werden.

`msbuild myProject.vcxproj /p:UseEnv=true`

### <a name="targets"></a>Ziele

In den Visual Studio-Supportdateien sind Hunderte von Zielen enthalten. Die meisten sind jedoch systemorientierte Ziele, die der Benutzer ignorieren kann. Die meisten System Ziele haben einen Unterstrich ( `_` ), oder Sie haben einen Namen, der mit "preparefor", "Compute", "Before", "After", "Pre" oder "Post" beginnt.

In der folgenden Tabelle sind mehrere nützliche benutzerorientierte Ziele aufgeführt.

| Target | Beschreibung |
| ------ | ----------- |
| BscMake | Führt das Microsoft-Wartungshilfsprogramm zum Durchsuchen von Informationen aus ("bscmake.exe"). |
| Entwickeln | Erstellt das Projekt.<br /><br /> Dieses Ziel ist die Standardeinstellung für ein Projekt. |
| ClCompile | Führt das MSVC-Compilertool („cl.exe“) aus. |
| Clean | Löscht temporäre und zwischengespeicherte Builddateien. |
| Lib | Führt das 32-Bit-Tool von Microsoft zur Bibliotheksverwaltung ("lib.exe") aus. |
| Link | Führt das MSVC-Linkertool („link.exe“) aus. |
| ManifestResourceCompile | Extrahiert eine Liste der Ressourcen aus einem Manifest und führt das Microsoft Windows-Ressourcencompilertool ("rc.exe") aus. |
| Midl | Führt das MIDL (Microsoft Interface Definition Language)-Compilertool ("midl.exe") aus. |
| Neu erstellen | Bereinigt und erstellt das Projekt. |
| ResourceCompile | Führt das Microsoft Windows-Ressourcencompilertool ("rc.exe") aus. |
| XdcMake | Führt das XML-Dokumentationstool ("xdcmake.exe") aus. |
| Xsd | Führt das XML-Schemadefinitionstool ("Xsd.exe") aus. *Siehe Hinweis weiter unten.* |

> [!NOTE]
> In Visual Studio 2017 und höher ist die Unterstützung von C++-Projekten für **xsd**-Dateien veraltet. Sie können **Microsoft.VisualC.CppCodeProvider** weiterhin verwenden, indem Sie die Datei **CppCodeProvider.dll** manuell dem globalen Assemblycache hinzufügen.

## <a name="see-also"></a>Siehe auch

[Referenz zu MSBuild-Aufgaben](/visualstudio/msbuild/msbuild-task-reference)\
[BSCMAKE-Aufgabe](/visualstudio/msbuild/bscmake-task)\
[CL-Aufgabe](/visualstudio/msbuild/cl-task)\
[Cppclean-Aufgabe](/visualstudio/msbuild/cppclean-task)\
[LIB-Aufgabe](/visualstudio/msbuild/lib-task)\
[Link-Aufgabe](/visualstudio/msbuild/link-task)\
[Mittel l-Aufgabe](/visualstudio/msbuild/midl-task)\
[MT-Aufgabe](/visualstudio/msbuild/mt-task)\
[RC-Aufgabe](/visualstudio/msbuild/rc-task)\
[-Aufgabe](/visualstudio/msbuild/setenv-task)\
[Vcmessage-Aufgabe](/visualstudio/msbuild/vcmessage-task)\
[XDCMake-Aufgabe](/visualstudio/msbuild/xdcmake-task)
