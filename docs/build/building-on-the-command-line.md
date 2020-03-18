---
title: Verwenden Sie das C++ Microsoft-Toolset von der Befehlszeile aus.
description: Verwenden Sie die Microsoft C++ Compiler Toolchain (MSVC) auf der Befehlszeile außerhalb der Visual Studio IDE.
ms.custom: conceptual
ms.date: 11/12/2019
helpviewer_keywords:
- command-line builds [C++]
- compiling source code [C++], command line
- builds [C++], command-line
- command line [C++], building from
- command line [C++], compilers
ms.assetid: 7ca9daed-a003-4162-842d-908f79058365
ms.openlocfilehash: ec30cba8e119f96efc5bca156fa565db77904520
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2020
ms.locfileid: "79422901"
---
# <a name="use-the-microsoft-c-toolset-from-the-command-line"></a>Verwenden Sie das C++ Microsoft-Toolset von der Befehlszeile aus.

Sie können mithilfe von Tools, die in Visual Studio enthalten sind, C- und C++-Anwendungen auf der Befehlszeile erstellen. Das Microsoft C++ -Compilertoolset (MSVC) kann auch als eigenständiges Paket heruntergeladen werden, das die Visual Studio-IDE nicht enthält.

## <a name="download-and-install-the-tools"></a>Herunterladen und Installieren der Tools

Wenn Sie Visual Studio und eine C++ Arbeitsauslastung installiert haben, verfügen Sie über alle Befehlszeilen Tools. Weitere Informationen zum Installieren C++ von und Visual Studio finden Sie [unter Installieren C++ von Support in Visual Studio](vscpp-step-0-installation.md). Wenn Sie nur das Befehlszeilen-Toolset wünschen, laden Sie die [Buildtools für Visual Studio](https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2019)herunter. Wenn Sie die heruntergeladene ausführbare Datei ausführen, wird die Visual Studio-Installer aktualisiert und ausgeführt. Um nur die Tools zu installieren, die C++ Sie für die Entwicklung benötigen, wählen Sie die  **C++ Arbeitsauslastung Build Tools** aus. Sie können optionale Bibliotheken und Toolsets auswählen, die unter **Installationsdetails**enthalten sein sollen. Wählen Sie zum Erstellen von Code mithilfe der Visual Studio 2015-oder 2017-Toolsets die optionalen MSVC-V140-oder MSVC v141 Build-Tools aus. Wenn Sie mit Ihrer Auswahl zufrieden sind, wählen Sie **Installieren**aus.

## <a name="how-to-use-the-command-line-tools"></a>Verwenden der Befehlszeilentools

Wenn Sie eine der C++-Workloads im Visual Studio-Installer auswählen, installiert sie das Visual Studio-*Plattformtoolset*. Ein Platt Form Toolset verfügt über alle C C++ -und-Tools für eine bestimmte Visual Studio-Version. Die Tools umfassen die C/C++ Compiler, Linker, Assemblys und andere Buildtools sowie übereinstimmende Bibliotheken. Sie können all diese Tools in der Befehlszeile verwenden. Sie werden auch intern von der Visual Studio-IDE verwendet. Es gibt separate, x86-gehostete und x64-gehostete Compiler und Tools zum Erstellen von Code für x86-, x64-, Arm-und ARM64-Ziele. Jeder Satz Tools für eine bestimmte Host- und Zielbuildarchitektur ist in einem eigenen Verzeichnis gespeichert.

Um ordnungsgemäß zu funktionieren, müssen für die Tools verschiedene spezifische Umgebungsvariablen festgelegt werden. Diese Variablen werden zum Hinzufügen der Tools zum Pfad und zum Festlegen von Include-Dateien, Bibliotheksdateien und SDK-Speicherorten verwendet. Um das Festlegen dieser Umgebungsvariablen zu vereinfachen, erstellt der Installer während der Installation angepasste *Befehlsdateien* oder Batchdateien. Sie können eine dieser Befehls Dateien ausführen, um eine bestimmte Host-und zielbuildarchitektur, Windows SDK Version und ein Platt Form Toolset festzulegen. Aus praktischer Gründen erstellt das Installationsprogramm auch Verknüpfungen im Startmenü. Mit den Tastenkombinationen starten Sie Entwickler-Eingabe Aufforderungs Fenster, indem Sie diese Befehls Dateien für bestimmte Kombinationen von Host und Ziel verwenden. Mit diesen Tastenkombinationen stellen Sie sicher, dass alle erforderlichen Umgebungsvariablen festgelegt und einsatzbereit sind.

Die erforderlichen Umgebungsvariablen sind spezifisch für Ihre Installation und die von Ihnen gewählte buildarchitektur. Sie können auch durch Produktupdates oder-Upgrades geändert werden. Daher wird empfohlen, dass Sie eine installierte Eingabe Aufforderungs Verknüpfung oder Befehlsdatei verwenden, anstatt die Umgebungsvariablen selbst festzulegen. Weitere Informationen finden Sie unter [Festlegen der Pfad-und Umgebungsvariablen für Befehlszeilenbuilds](setting-the-path-and-environment-variables-for-command-line-builds.md).

Die installierten Toolsets, Befehls Dateien und Verknüpfungen sind abhängig von Ihrem Computer Prozessor und den Optionen, die Sie während der Installation ausgewählt haben. Die x86-gehosteten Tools und Cross Tools, die x86-und x64-Code erstellen, sind immer installiert. Wenn Sie über 64-Bit-Windows verfügen, werden die x64-gehosteten Tools und Cross Tools, die x86-und x64-Code erstellen, ebenfalls installiert. Wenn Sie die optionalen C++ universelle Windows-Plattform Tools auswählen, werden die x86-und x64-Tools, die Arm-und ARM64-Code erstellen, ebenfalls installiert. Von anderen Workloads werden möglicherweise zusätzliche Tools installiert.

## <a name="developer_command_prompt_shortcuts"></a>Developer-Eingabeaufforderungsverknüpfungen

Die Eingabeaufforderungsverknüpfungen werden in einem versionsspezifischen Visual Studio-Ordner in Ihrem Startmenü gespeichert. Das Folgende ist eine Liste der grundlegenden Eingabeaufforderungsverknüpfungen und der von ihnen unterstützten Buildarchitekturen:

- **Developer-Eingabeaufforderung**: Legt die Umgebung für die Verwendung von x86-nativen 32-Bit-Tools zum Erstellen von x86-nativem 32-Bit-Code fest.
- **x86 Native Tools-Eingabeaufforderung**: Legt die Umgebung für die Verwendung von x86-nativen 32-Bit-Tools zum Erstellen von x86-nativem 32-Bit-Code fest.
- **x64 Native Tools-Eingabeaufforderung**: Legt die Umgebung für die Verwendung von x64-nativen 64-Bit-Tools zum Erstellen von x64-nativem 64-Bit-Code fest.
- **x86_x64 Cross Tools-Eingabeaufforderung**: Legt die Umgebung für die Verwendung von x86-nativen 32-Bit-Tools zum Erstellen von x64-nativem 64-Bit-Code fest.
- **x64_x86 Cross Tools-Eingabeaufforderung**: Legt die Umgebung für die Verwendung von x64-nativen 64-Bit-Tools zum Erstellen von x86-nativem 32-Bit-Code fest.

::: moniker range=">= vs-2019"

Der Startmenü Ordner und die Verknüpfungs Namen unterscheiden sich abhängig von der installierten Version von Visual Studio. Wenn Sie eins festlegen, hängt es auch vom Installations **Spitzname**ab. Nehmen Sie beispielsweise an, Sie haben Visual Studio 2019 installiert, und Sie haben den Spitznamen " *Latest*" erhalten. Die Verknüpfung für die Developer-Eingabeaufforderung heißt **Developer-Eingabeaufforderung für vs 2019 (Latest)** , in einem Ordner mit dem Namen **Visual Studio 2019**.

::: moniker-end
::: moniker range="= vs-2017"

Der Startmenü Ordner und die Verknüpfungs Namen unterscheiden sich abhängig von der installierten Version von Visual Studio. Wenn Sie eins festlegen, hängt es auch vom Installations **Spitzname**ab. Nehmen Sie beispielsweise an, Sie haben Visual Studio 2017 installiert, und Sie haben den Spitznamen " *Latest*" erhalten. Die Verknüpfung für die Developer-Eingabeaufforderung heißt **Developer-Eingabeaufforderung für vs 2017 (Latest)** , in einem Ordner mit dem Namen **Visual Studio 2017**.

::: moniker-end
::: moniker range="< vs-2017"

Der Startmenü Ordner und die Verknüpfungs Namen unterscheiden sich abhängig von der installierten Version von Visual Studio. Nehmen Sie beispielsweise an, Sie haben Visual Studio 2015 installiert. Die Verknüpfung für die Developer-Eingabeaufforderung heißt **Developer-Eingabeaufforderung für vs 2015**.

::: moniker-end

### <a name="developer_command_prompt"></a> So öffnen Sie ein Developer-Eingabeaufforderungsfenster

1. Öffnen Sie auf dem Desktop das Windows-**Startmenü**, und scrollen Sie dann nach unten, um den Ordner für Ihre Visual Studio-Version zu finden und zu öffnen, beispielsweise **Visual Studio 2019**.

1. Wählen Sie im Ordner die **Developer-Eingabeaufforderung** für Ihre Version von Visual Studio aus. Diese Verknüpfung startet ein Developer-Eingabeaufforderungsfenster, das die Standardbuildarchitektur mit x86-nativen 32-Bit-Tools zum Erstellen von x86-nativem 32-Bit-Code verwendet. Falls Sie eine andere als die Standardbuildarchitektur vorziehen, wählen Sie eine der Eingabeaufforderungen mit nativen oder kreuzkompatiblen Tools aus, um die Host- und die Zielarchitektur anzugeben.

Wenn Sie eine Entwickler Eingabeaufforderung noch schneller öffnen möchten, geben Sie im Feld Desktop Suche eine *Developer-Eingabeaufforderung* ein. Wählen Sie dann das gewünschte Ergebnis aus.

## <a name="developer_command_file_locations"></a> Speicherorte von Developer-Befehlsdateien

Wenn Sie die Buildumgebung in einem vorhandenen Eingabe Aufforderungs Fenster festlegen möchten, können Sie eine der Befehls Dateien verwenden, die vom Installationsprogramm erstellt wurden. Es wird empfohlen, dass Sie die Umgebung in einem neuen Eingabe Aufforderungs Fenster festlegen. Wir empfehlen Ihnen später nicht, Umgebungen im gleichen Befehlsfenster zu wechseln.

::: moniker range=">= vs-2019"

Der Speicherort der Befehlsdatei ist abhängig von der installierten Version von Visual Studio und den Optionen, die Sie bei der Installation getroffen haben. Für Visual Studio 2019 befindet sich der typische Installationsort auf einem 64-Bit-System in \\Programme (x86)\\Microsoft Visual Studio\\2019\\*Edition*. Die *Edition* kann Community, Professional, Enterprise, Buildtools oder ein anderer Spitzname sein, den Sie angegeben haben.

::: moniker-end
::: moniker range="= vs-2017"

Der Speicherort der Befehlsdatei ist abhängig von der installierten Version von Visual Studio und den Optionen, die Sie bei der Installation getroffen haben. Für Visual Studio 2017 befindet sich der typische Installationsort auf einem 64-Bit-System in \\Programme (x86)\\Microsoft Visual Studio\\2017\\*Edition*. Die *Edition* kann Community, Professional, Enterprise, Buildtools oder ein anderer Spitzname sein, den Sie angegeben haben.

::: moniker-end
::: moniker range="< vs-2017"

Der Speicherort der Befehlsdatei hängt von der Visual Studio-Version und dem Installationsverzeichnis ab. Für Visual Studio 2015 befindet sich der typische Installationsort in \\-Programmdateien (x86)\\Microsoft Visual Studio 14,0.

::: moniker-end

Die primäre Befehlszeile für die Developer-Eingabeaufforderung, vsdevcmd. bat, befindet sich im Unterverzeichnis Common7\\Tools. Wenn keine Parameter angegeben werden, wird die Umgebung so festgelegt, dass die x86-Native-Tools zum Erstellen von 32-Bit-x86-Code verwendet werden.

::: moniker range=">= vs-2017"

Es sind weitere Befehls Dateien zum Einrichten spezifischer buildarchitekturen verfügbar. Welche Befehls Dateien verfügbar sind, hängt von den Visual Studio-Arbeits Auslastungen und den von Ihnen installierten Optionen ab. In Visual Studio 2017 und Visual Studio 2019 finden Sie diese im VC-\\\\Build-Unterverzeichnis.

::: moniker-end
::: moniker range="< vs-2017"

Es sind weitere Befehls Dateien zum Einrichten spezifischer buildarchitekturen verfügbar. Welche Befehls Dateien verfügbar sind, hängt von den Visual Studio-Arbeits Auslastungen und den von Ihnen installierten Optionen ab. In Visual Studio 2015 befinden Sie sich in den Unterverzeichnissen VC, VC\\bin oder VC\\bin\\*Architecture* , wobei *Architecture* eine der systemeigenen oder Cross-Compiler-Optionen ist.

::: moniker-end

Diese Befehlsdateien legen Standardparameter fest und rufen „VsDevCmd.bat“ auf, um die angegebene Buildarchitekturumgebung einzurichten. Eine typische Installation kann etwa diese Befehlsdateien enthalten:

|Befehlsdatei|Host- und Zielarchitekturen|
|---|---|
|**vcvars32.bat**| Die x86-nativen 32-Bit-Tools werden zum Erstellen von 32-Bit-x86-Code verwendet.|
|**vcvars64.bat**| Die x64-nativen 64-Bit-Tools werden zum Erstellen von 64-Bit-x64-Code verwendet.|
|**vcvarsx86_amd64.bat**| Die x86-nativen 32-Bit kreuzkompatiblen Tools werden zum Erstellen von 64-Bit-x64-Code verwendet.|
|**vcvarsamd64_x86.bat**| Die x64-nativen 64-Bit kreuzkompatiblen Tools werden zum Erstellen von 32-Bit-x86-Code verwendet.|
|**vcvarsx86_arm.bat**| Die x86-nativen 32-Bit kreuzkompatiblen Tools werden zum Erstellen ARM-Code verwendet.|
|**vcvarsamd64_arm.bat**| Die x64-nativen 64-Bit kreuzkompatiblen Tools werden zum Erstellen ARM-Code verwendet.|
|**vcvarsall.bat**| Verwenden Sie Parameter, um die Optionen für Host und Ziel Architekturen, Windows SDK und Plattform anzugeben. Um eine Liste der unterstützten Optionen anzuzeigen, rufen Sie diesen Befehl mit dem Parameter **/help** auf.|

> [!CAUTION]
> Die vcvarsall.bat-Datei und andere Visual Studio-Befehlsdateien können sich von Computer zu Computer unterscheiden. Ersetzen Sie eine fehlender oder beschädigte vcvarsall.bat-Datei nicht durch eine Datei von einem anderen Computer. Führen Sie den Visual Studio-Installer erneut aus, um die fehlende Datei zu ersetzen.
>
> Die vcvarsall.bat-Datei ist auch von Version zu Version unterschiedlich. Falls die aktuelle Version von Visual Studio auf einem Computer installiert ist, der außerdem über eine frühere Version von Visual Studio verfügt, sollten Sie nicht „vcvarsall.bat“ oder eine andere Visual Studio-Befehlsdatei aus einer anderen Version im selben Eingabeaufforderungsfenster ausführen.

## <a name="use-the-developer-tools-in-an-existing-command-window"></a>Verwenden der Entwicklertools in einem vorhandenen Befehlsfenster

Die einfachste Möglichkeit, eine bestimmte Buildarchitektur in einem vorhandenen Befehlsfenster anzugeben, ist die Verwendung der Datei „vcvarsall.bat“. Verwenden Sie vcvarsall. bat, um Umgebungsvariablen festzulegen, um die Befehlszeile für die native 32-Bit-oder 64-Bit-Kompilierung zu konfigurieren. Mit Argumenten können Sie die Kreuz Kompilierung für x86-, x64-, Arm-oder ARM64-Prozessoren angeben. Sie können auf Microsoft Store-, universelle Windows-Plattform-oder Windows-Desktop Plattformen abzielen. Sie können sogar angeben, welche Windows SDK verwendet werden sollen, und die Platt Form Toolsetversion auswählen.

Bei Verwendung ohne Argumente konfiguriert vcvarsall. bat die Umgebungsvariablen für die Verwendung des aktuellen x86-Native Compilers für 32-Bit-Windows-Desktop Ziele. Sie können Argumente hinzufügen, um die Umgebung so zu konfigurieren, dass Sie eines der systemeigenen oder Cross-Compilertools verwendet. vcvarsall. bat zeigt eine Fehlermeldung an, wenn Sie eine Konfiguration angeben, die nicht installiert oder auf Ihrem Computer verfügbar ist.

### <a name="vcvarsall-syntax"></a>vcvarsall-Syntax

> **vcvarsall.bat** [*architecture*] [*platform_type*] [*winsdk_version*] [ **-vcvars_ver=** _vcversion_]

*architecture*<br/>
Dieses optionale Argument gibt die zu verwendende Host- und Zielarchitektur an. Wenn *Architektur* nicht angegeben wird, wird die standardbuildumgebung verwendet. Diese Argumente werden unterstützt:

|*architecture*|Compiler|Hostcomputerarchitektur|Buildausgabearchitektur (Zielarchitektur)|
|----------------------------|--------------|----------------------------------|-------------------------------|
|**x86**|x86-32-Bit systemeigen|x86, x64|x86|
|**x86\_amd64** oder **x86\_x64**|x64 kreuzkompatibel auf x86|x86, x64|x64|
|**x86_arm**|ARM auf x86-Cross|x86, x64|ARM|
|**x86_arm64**|ARM64 kreuzkompatibel auf x86|x86, x64|ARM64|
|**amd64** oder **x64**|x64 64-Bit nativ|x64|x64|
|**amd64\_x86** oder **x64\_x86**|x86 kreuzkompatibel auf x64|x64|x86|
|**amd64\_arm** oder **x64\_arm**|ARM kreuzkompatibel auf x64|x64|ARM|
|**amd64\_arm64** oder **x64\_arm64**|ARM64 kreuzkompatibel auf x64|x64|ARM64|

*platform_type*<br/>
Dieses optionale Argument ermöglicht Ihnen die Angabe von **store** oder **uwp** als Plattformtyp. Standardmäßig ist die Umgebung auf das Erstellen von Desktop- oder Konsolen-Apps festgelegt.

*winsdk_version*<br/>
Gibt optional die Version des zu verwendenden Windows SDK an. Standardmäßig wird das neueste installierte Windows SDK verwendet. Um die Windows SDK-Version anzugeben, können Sie eine vollständige Windows 10 SDK-Nummer, wie etwa **10.0.10240.0**, verwenden oder **8.1** angeben, wenn Sie das Windows 8.1 SDK verwenden möchten.

*vcversion*<br/>
Gibt optional das zu verwendende Visual Studio-Compilertoolset an. Standardmäßig ist die Umgebung auf die Verwendung des aktuellen Visual Studio-Compilertoolsets festgelegt.

::: moniker range=">= vs-2019"

Verwenden Sie **-vcvars_ver = 14,2 x. yyyyy** , um eine bestimmte Version des compilertoolsets von Visual Studio 2019 anzugeben.

Verwenden Sie **-vcvars_ver = 14.16** , um die neueste Version des Visual Studio 2017-compilertoolsets anzugeben.

::: moniker-end
::: moniker range="= vs-2017"

Verwenden Sie **-vcvars_ver = 14.16** , um die neueste Version des Visual Studio 2017-compilertoolsets anzugeben.

Verwenden Sie **-vcvars_ver = 14.1 x. yyyyy** , um eine bestimmte Version des compilertoolsets von Visual Studio 2017 anzugeben.

::: moniker-end

Verwenden Sie **-vcvars_ver = 14,0** , um das Visual Studio 2015-Compilertoolset anzugeben.

#### <a name="vcvarsall"></a>So richten Sie die Buildumgebung in einem vorhandenen Eingabe Aufforderungs Fenster ein

1. Verwenden Sie an der Eingabeaufforderung den CD-Befehl, um in das Visual Studio-Installationsverzeichnis zu wechseln. Verwenden Sie dann erneut CD, um in das Unterverzeichnis zu wechseln, das die konfigurationsspezifischen Befehlsdateien enthält. Verwenden Sie für Visual Studio 2019 und Visual Studio 2017 das Unterverzeichnis *VC\\-Erweiterung\\Build* . Verwenden Sie für Visual Studio 2015 das Unterverzeichnis *VC* .

1. Geben Sie den Befehl für Ihre bevorzugte Entwicklerumgebung ein. Um z. b. Arm-Code für UWP auf einer 64-Bit-Plattform zu erstellen, verwenden Sie die neueste Windows SDK und das Visual Studio-Compilertoolset, indem Sie die folgende Befehlszeile verwenden:

   `vcvarsall.bat amd64_arm uwp`

## <a name="create-your-own-command-prompt-shortcut"></a>Erstellen einer eigenen Eingabeaufforderungsverknüpfung

::: moniker range=">= vs-2019"

Öffnen Sie das Dialogfeld Eigenschaften für eine Eingabe Aufforderungs Verknüpfung für Entwickler, um das verwendete Befehls Ziel anzuzeigen. Beispielsweise ist das Ziel für die Verknüpfung **x64 Native Tools-Eingabeaufforderung für VS 2019** ähnlich wie dies hier:

`%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\VC\Auxiliary\Build\vcvars64.bat"`

::: moniker-end
::: moniker range="= vs-2017"

Öffnen Sie das Dialogfeld Eigenschaften für eine Eingabe Aufforderungs Verknüpfung für Entwickler, um das verwendete Befehls Ziel anzuzeigen. Beispielsweise ist das Ziel für das **x64 Native Tools-Eingabeaufforderung für die Verknüpfung von vs 2017** etwas ähnlich:

`%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\VC\Auxiliary\Build\vcvars64.bat"`

::: moniker-end
::: moniker range="< vs-2017"

Öffnen Sie das Dialogfeld Eigenschaften für eine Eingabe Aufforderungs Verknüpfung für Entwickler, um das verwendete Befehls Ziel anzuzeigen. Beispielsweise ist das Ziel für die **VS2015-x64 Native Tools-Eingabeaufforderung** Verknüpfung etwa wie folgt:

`%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\vcvarsall.bat" amd64`

::: moniker-end

Die architekturspezifischen Batchdateien legen den *architecture*-Parameter fest und rufen „vcvarsall.bat“ auf. Sie können dieselben Optionen an diese Batch Dateien übergeben, wie Sie es an "vcvarsall. bat" übergeben würden, oder Sie können "vcvarsall. bat" direkt direkt aufzurufen. Um Parameter für Ihre eigene Befehlsverknüpfung anzugeben, fügen Sie sie am Ende des Befehls in doppelten Anführungszeichen hinzu. Hier ist beispielsweise eine Verknüpfung zum Erstellen von Arm-Code für die UWP auf einer 64-Bit-Plattform mit den neuesten Windows SDK. Wenn Sie ein früheres Compilertoolset verwenden möchten, geben Sie die Versionsnummer an. Verwenden Sie in Ihrer Verknüpfung etwas in der Art dieses Befehlsziels:

::: moniker range=">= vs-2019"

`%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\VC\Auxiliary\Build\vcvarsall.bat" amd64_arm uwp -vcvars_ver=14.16`

::: moniker-end
::: moniker range="= vs-2017"

`%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\VC\Auxiliary\Build\vcvarsall.bat" amd64_arm uwp -vcvars_ver=14.0`

::: moniker-end
::: moniker range="< vs-2017"

`%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\vcvarsall.bat" amd64 -vcvars_ver=12.0`

::: moniker-end

Passen Sie den Pfad an das Visual Studio-Installationsverzeichnis an. Die vcvarsall.bat-Datei enthält zusätzliche Informationen über bestimmte Versionsnummern.

## <a name="command-line-tools"></a>Befehlszeilentools

Zum Erstellen eines C/C++ Projekts an einer Eingabeaufforderung stellt Visual Studio die folgenden Befehlszeilen Tools bereit:

[CL](reference/compiling-a-c-cpp-program.md)<br/>
Verwenden Sie den Compiler (cl.exe), um Quellcodedateien in Apps, Bibliotheken und DLLs zu kompilieren und zu verknüpfen.

[Link](reference/linking.md)<br/>
Verwenden Sie den Linker (link.exe), um kompilierte Objektdateien in Apps und DLLs zu verknüpfen.

[MSBuild](msbuild-visual-cpp.md)<br/>
Verwenden Sie MSBuild (msbuild.exe) und eine Projektdatei (.vcxproj), um einen Build zu konfigurieren und das Toolset indirekt aufzurufen. Dies entspricht dem Ausführen des Befehls **Build** Project oder **Build Solution** in der Visual Studio-IDE. Das Ausführen von MSBuild über die Befehlszeile ist ein erweitertes Szenario, das nicht häufig empfohlen wird.

[DEVENV](/visualstudio/ide/reference/devenv-command-line-switches)<br/>
Verwenden Sie devenv (devenv. exe) in Kombination mit einem Befehls Zeilenschalter (z. b. **/Build** oder **/Clean** ), um bestimmte Buildbefehle auszuführen, ohne die Visual Studio-IDE anzuzeigen. Im Allgemeinen wird die Verwendung von MSBuild mit der Verwendung von "tovenv" bevorzugt, da Visual Studio die Komplexität von MSBuild verarbeiten kann.

[NMAKE](reference/nmake-reference.md)<br/>
Verwenden Sie NMAKE (nmake.exe) unter Windows, um C++-Projekte auf der Grundlage eines traditionellen Makefiles zu erstellen.

Wenn Sie in der Befehlszeile erstellen, ist der Befehl F1 nicht für sofortige Hilfe verfügbar. Stattdessen können Sie eine Suchmaschine verwenden, um Informationen über Warnungen, Fehler und Meldungen abzurufen, oder Sie können die Offline-Hilfedateien verwenden. Wenn Sie die Suche in [docs.Microsoft.com](https://docs.microsoft.com/cpp/)verwenden möchten, verwenden Sie das Suchfeld am oberen Rand der Seite.

## <a name="in-this-section"></a>In diesem Abschnitt

In diesen Artikeln erfahren Sie, wie Sie apps in der Befehlszeile erstellen und wie Sie die Buildumgebung der Befehlszeile anpassen. Einige zeigen, wie Sie 64-Bit-Toolsets verwenden und x86-, x64-, Arm-und ARM64-Plattformen als Ziel verwenden. Außerdem wird die Verwendung der Befehlszeilen-Buildtools MSBuild und NMAKE beschrieben.

[Exemplarische Vorgehensweise: Kompilieren C++ eines nativen Programms in der Befehlszeile](walkthrough-compiling-a-native-cpp-program-on-the-command-line.md)<br/>
Enthält ein Beispiel, das zeigt, wie ein C++ Programm in der Befehlszeile erstellt und kompiliert wird.

[Exemplarische Vorgehensweise: Kompilieren eines C-Programms in der Befehlszeile](walkthrough-compile-a-c-program-on-the-command-line.md)<br/>
Beschreibt, wie Sie ein in der Programmiersprache C geschriebenes Programm kompilieren.

[Exemplarische Vorgehensweise: C++Kompilieren eines/CLI-Programms in der Befehlszeile](walkthrough-compiling-a-cpp-cli-program-on-the-command-line.md)<br/>
Beschreibt, wie Sie ein C++-/CLI-Programm erstellen und kompilieren, das .NET Framework verwendet.

[Exemplarische Vorgehensweise: C++Kompilieren eines/CX-Programms in der Befehlszeile](walkthrough-compiling-a-cpp-cx-program-on-the-command-line.md)<br/>
Beschreibt, wie Sie ein C++-/CX-Programm erstellen und kompilieren, das die Windows Runtime verwendet.

[Festlegen der Pfad-und Umgebungsvariablen für Befehlszeilenbuilds](setting-the-path-and-environment-variables-for-command-line-builds.md)<br/>
Festlegen von Umgebungsvariablen für die Verwendung eines 32-Bit-oder 64-Bit-Toolsets für x86-, x64-, Arm-und ARM64-Plattformen.

[NMAKE-Referenz](reference/nmake-reference.md)<br/>
Enthält Links zu Artikeln, in denen das Microsoft Program Maintenance Utility (NMAKE.EXE) beschrieben wird.

[MSBuild on the Command Line – C++ (C++: MSBuild in der Befehlszeile)](msbuild-visual-cpp.md)<br/>
Enthält Links zu Artikeln, in denen die Verwendung von msbuild.exe auf der Befehlszeile dargestellt wird.

## <a name="related-sections"></a>Verwandte Abschnitte

[/MD,/MT,/LD (Lauf Zeit Bibliothek verwenden)](reference/md-mt-ld-use-run-time-library.md)<br/>
Beschreibt die Verwendung dieser Compileroptionen für eine Debug- oder Releaselaufzeitbibliothek.

[C/C++ Compileroptionen](reference/compiler-options.md)<br/>
Enthält Links zu Artikeln, in denen die C- und C++-Compileroptionen sowie CL.exe erläutert werden.

[MSVC (Linkeroptionen)](reference/linker-options.md)<br/>
Enthält Links zu Artikeln, in denen die Linkeroptionen und LINK.EXE dargestellt werden.

[Zusätzliche MSVC-Buildtools](reference/c-cpp-build-tools.md)<br/>
Enthält Links zu den C-/C++-Buildtools, die in Visual Studio enthalten sind.

## <a name="see-also"></a>Siehe auch

[Projekte und Buildsysteme](projects-and-build-systems-cpp.md)
