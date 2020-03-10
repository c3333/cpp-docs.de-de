---
title: Erstellen und Konfigurieren eines Linux CMake-Projekts in Visual Studio
description: Hier erfahren Sie, wie Sie ein Linux CMake-Projekt in Visual Studio erstellen, konfigurieren, bearbeiten und kompilieren.
ms.date: 10/04/2019
ms.assetid: f8707b32-f90d-494d-ae0b-1d44425fdc25
ms.openlocfilehash: 9c6a60162c2dbbab8e348b27d1987d7f1001bee0
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78865648"
---
# <a name="create-and-configure-a-linux-cmake-project"></a>Erstellen und Konfigurieren eines Linux-CMake-Projekts

::: moniker range="vs-2015"

Die Unterstützung für Linux ist in Visual Studio 2017 und höher verfügbar.

::: moniker-end

::: moniker range="vs-2019"

So erstellen Sie ein neues Linux CMake-Projekt in Visual Studio 2019

1. Wählen Sie in Visual Studio **Datei > Neues Projekt** aus, oder drücken Sie **STRG + UMSCHALT + N**.
1. Legen Sie **Sprache** auf **C++** fest, und suchen Sie nach „CMake“. Klicken Sie dann auf **Weiter**. Geben Sie einen **Namen** und einen **Speicherort** an, und klicken Sie auf **Erstellen**.

Visual Studio erstellt eine minimale Datei namens „CMakeLists.txt“ mit nur dem Namen der ausführbaren Datei und der mindestens erforderlichen CMake-Version. Sie können diese Datei jedoch manuell nach Belieben bearbeiten. Visual Studio wird Ihre Änderungen in keinem Fall überschreiben. Sie können CMake-Befehlszeilenargumente und -Umgebungsvariablen angeben, indem Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf die Stammdatei „CMakeLists.txt“ klicken und **CMake-Einstellungen für Projekt** auswählen. Klicken Sie zum Angeben von Optionen für das Debuggen mit der rechten Maustaste auf den Projektknoten, und wählen Sie **Debug- und Starteinstellungen**.

::: moniker-end

Wenn Sie einen Ordner öffnen, der ein bereits vorhandenes CMake-Projekt enthält, verwendet Visual Studio Variablen im CMake-Cache, um IntelliSense und Builds automatisch zu konfigurieren. Lokale Konfigurations- und Debugeinstellungen werden in JSON-Dateien gespeichert, die optional für andere Benutzer von Visual Studio freigegeben werden können.

Visual Studio nimmt keine Änderungen an den Dateien namens „CMakeLists.txt“ vor, sodass andere, die am selben Projekt arbeiten, weiterhin dieselben Tools nutzen können. Visual Studio generiert den Cache neu, wenn Sie Änderungen an „CMakeLists.txt“ oder in einigen Fällen an „CMakeSettings.json“ speichern. Wenn Sie aber eine Konfiguration des Typs **Vorhandener Cache** nutzen, ändert Visual Studio den Cache nicht.

Allgemeine Informationen zur Unterstützung von CMake in Visual Studio finden Sie unter [CMake-Projekte in Visual Studio](../build/cmake-projects-in-visual-studio.md). Diesen Artikel sollten Sie lesen, bevor Sie hier fortfahren.

## <a name="before-you-begin"></a>Vorbereitungen

Stellen Sie zuerst sicher, dass die Workload **Linux-Entwicklung mit C++** mit der CMake-Komponente installiert ist. Weitere Informationen finden Sie unter [Install the C++ Linux workload in Visual Studio (Installieren der C++-Workload unter Linux in Visual Studio)](download-install-and-setup-the-linux-development-workload.md). 

Stellen Sie sicher, dass Folgendes auf dem Linux-System installiert ist: 

- gcc
- gdb
- rsync
- zip 

::: moniker range="vs-2019"

Für die Unterstützung von CMake-Projekten unter Linux ist eine aktuelle Version von CMake auf dem Zielcomputer erforderlich. Die vom Standardpaket-Manager einer Distribution bereitgestellte Version ist häufig nicht ausreichend aktuell, um alle für Visual Studio erforderlichen Funktionen zu unterstützen. Visual Studio 2019 erkennt, ob eine aktuelle Version von CMake auf dem Linux-System installiert ist. Wenn keine aktuelle Version gefunden wird, zeigt Visual Studio im oberen Editor-Bereich eine Informationsleiste an, auf der Sie sie über [https://github.com/Microsoft/CMake/releases](https://github.com/Microsoft/CMake/releases) installieren können.

Die CMake-Unterstützung in Visual Studio erfordert die Servermodusunterstützung, die in CMake 3.8 eingeführt wurde. In Visual Studio 2019 wird Version 3.14 oder höher empfohlen.

::: moniker-end

::: moniker range="vs-2017"

Die CMake-Unterstützung in Visual Studio erfordert die Servermodusunterstützung, die in CMake 3.8 eingeführt wurde. Laden Sie für eine von Microsoft bereitgestellte CMake-Variante unter [https://github.com/Microsoft/CMake/releases](https://github.com/Microsoft/CMake/releases) die aktuellsten vordefinierten Binärdateien herunter.

Die Binärdateien werden in `~/.vs/cmake` installiert. Nach dem Bereitstellen der Binärdateien wird Ihr Projekt automatisch neu generiert. Hinweis: Wenn die im Feld `cmakeExecutable` in `CMakeSettings.json` angegebene CMake-Version ungültig ist (Version nicht vorhanden oder ungültig) und die vorab erstellten Binärdateien vorhanden sind, ignoriert Visual Studio `cmakeExecutable` und verwendet die vorab erstellten Binärdateien.

:::moniker-end

## <a name="open-a-folder"></a>Öffnen eines Ordners

Um zu beginnen, wählen Sie **Datei** > **Öffnen** > **Ordner** aus dem Hauptmenü aus, oder geben Sie `devenv.exe <foldername>` in der Befehlszeile ein. Der Ordner, den Sie öffnen, sollte eine Datei „CMakeLists.txt“ sowie Ihren Quellcode enthalten.
Das folgende Beispiel zeigt eine einfache Datei „CMakeLists.txt“ und CPP-Datei:

```cpp
// hello.cpp

#include <iostream>

int main(int argc, char* argv[])
{
    std::cout << "Hello from Linux CMake" << std::endl;
}
```

„CMakeLists.txt“:

```cmd
cmake_minimum_required(VERSION 3.8)
project (hello-cmake)
add_executable(hello-cmake hello.cpp)
```

## <a name="choose-a-linux-target"></a>Auswählen eines Linux-Ziels

Sobald Sie den Ordner öffnen, analysiert Visual Studio die Datei „CMakeLists.txt“ und gibt das Windows-Ziel **x86-Debug** an. Ändern Sie die Projekteinstellungen auf **Linux-Debug** oder **Linux-Release**, um auf ein Linux-Remotesystem abzuzielen. (Siehe [Konfigurieren von CMake-Einstellungen für Linux](#configure_cmake_linux) weiter unten.)

::: moniker range="vs-2019"

Um „Windows-Subsystem für Linux“ als Ziel festzulegen, klicken Sie auf der Hauptsymbolleiste in der Dropdownliste „Konfiguration“ auf **Konfigurationen verwalten**. Klicken Sie dann bei Verwenden von GCC auf die Schaltfläche **Konfiguration hinzufügen**, und wählen Sie **WSL-Debug** oder **WSL-Release** aus bzw. bei Verwendung der Clang-Varianten das Clang-/LLVM-Toolset. 

**Visual Studio 2019 Version 16.1** Wenn WSL als Ziel gewählt wird, ist das Kopieren von Quellen oder Headern nicht erforderlich, da der Compiler unter Linux Direktzugriff auf das Windows-Dateisystem hat, in dem Ihre Quelldateien gespeichert sind. (Ab der Windows-Version 1903 können Windows-Anwendungen ebenfalls direkt auf die Linux-Headerdateien zugreifen, jedoch nutzt Visual Studio diese Funktion noch nicht).

::: moniker-end

Für Remoteziele wählt Visual Studio standardmäßig das erste Remotesystem in der Liste unter **Tools** > **Optionen** > **Plattformübergreifend** > **Verbindungs-Manager** aus. Wenn keine Remoteverbindungen gefunden werden, werden Sie aufgefordert, eine Remoteverbindung zu erstellen. Weitere Informationen finden Sie unter [Herstellen einer Verbindung mit Ihrem Linux-Remotecomputer](connect-to-your-remote-linux-computer.md).

Wenn Sie ein Linux-Remoteziel angeben, wird Ihre Quelle in das Remotesystem kopiert.

Wenn Sie ein Ziel ausgewählt haben, wird CMake zum Generieren des CMake-Caches für Ihr Projekt automatisch auf dem Linux-System ausgeführt. 

![Generieren des CMake-Caches unter Linux](media/cmake-linux-1.png "Generieren des CMake-Caches unter Linux")

Visual Studio kopiert automatisch Header vom Linux-Computer in ein Verzeichnis auf Ihrem lokalen Windows-Computer, um IntelliSense-Unterstützung für Header auf Linux-Remotesystemen bereitzustellen. Weitere Informationen finden Sie unter [IntelliSense für Remoteheader (Visual Studio 2017-Version 15.7 und höher)](configure-a-linux-project.md#remote_intellisense).

## <a name="debug_cmake_project"></a> Debuggen des CMake-Projekts

Legen Sie zum Debuggen Ihres Codes auf dem angegebenen Debugzielsystem einen Breakpoint fest, wählen Sie im Symbolleistenmenü neben der Projekteinstellung das CMake-Ziel als Startelement aus, und klicken Sie in der Symbolleiste auf **&#x23f5; Start** bzw. F5.

Um die Befehlszeilenargumente Ihres Programms anzupassen, klicken Sie oben im **Projektmappen-Explorer** auf die Schaltfläche **Ziele vertauschen**, und wählen Sie dann die Ansicht **Ziele**. Klicken Sie mit der rechten Maustaste auf das Ziel, und wählen Sie **Debug- und Starteinstellungen** aus. Hierdurch wird eine Konfigurationsdatei „launch.vs.json“ geöffnet oder erstellt, die Informationen zu Ihrem Programm enthält. Fügen Sie der Datei wie im folgenden Beispiel veranschaulicht eine **sourceFilemileMapap**-Eigenschaft hinzu, um den Speicherort für Quelldateien festzulegen.

```json
"MIMode": "gdb",
"externalConsole": true,
"sourceFileMap": {
"c/Users/USER/source/repos/CMAKEPROJECTNAME": "C:\\Users\\USER\\source\\repos\\CMAKEPROJECTNAME"
},
"remoteMachineName": "${debugInfo.remoteMachineName}",
```

Um zusätzliche Argumente anzugeben, fügen Sie sie dem JSON-Array `args` hinzu. Weitere Informationen finden Sie unter [Open Folder projects for C++ (Verwenden von „Ordner öffnen“ mit Projekten in Visual C++)](../build/open-folder-projects-cpp.md) und [Configure CMake debugging sessions (Konfigurieren von CMake-Debugsitzungen)](../build/configure-cmake-debugging-sessions.md).

## <a name="configure_cmake_linux"></a> Konfigurieren von CMake-Einstellungen für Linux

Eine „CMakeSettings.json“-Datei in einem CMake-Projekt unter Linux kann alle unter [Anpassen von CMake-Buildeinstellungen](../build/customize-cmake-settings.md) aufgeführten Einstellungen angeben sowie weitere Eigenschaften, die die Buildeinstellungen auf dem Linux-Remotecomputer steuern. 

::: moniker range="vs-2019"

Öffnen Sie über Hauptsymbolleiste die Dropdownliste **Konfiguration**, und wählen Sie die Option **Konfigurationen verwalten** aus, um die Standardeinstellungen von CMake in Visual Studio 2019 zu ändern. 

![Verwalten von CMake-Konfigurationen](../build/media/vs2019-cmake-manage-configurations.png "Dropdownliste „CMake-Konfigurationen“")

Dadurch wird der **Editor für CMake-Einstellungen** geöffnet, den Sie zum Bearbeiten der `CMakeSettings.json`-Datei im Stammprojektordner verwenden können. Sie können die Datei auch direkt öffnen, indem Sie im Editor auf **JSON bearbeiten** klicken. Weitere Informationen finden Sie unter [Anpassen von CMake-Einstellungen](../build/customize-cmake-settings.md).

::: moniker-end

::: moniker range="vs-2017"

Klicken Sie im Hauptmenü auf **CMake > CMake-Einstellungen ändern > CMakeLists.txt**, oder klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf die Datei „CMakeSettings.txt“, und wählen Sie dann **CMake-Einstellungen ändern** aus, um die CMake-Standardeinstellungen in Visual Studio 2017 zu ändern. Visual Studio erstellt dann eine neue `CMakeSettings.json`-Datei im Stammordner des Projekts. Sie können die Datei mit dem Editor für **CMake-Einstellungen** öffnen oder die Datei direkt ändern. Weitere Informationen finden Sie unter [Customize CMake settings (Anpassen von CMake-Einstellungen)](../build/customize-cmake-settings.md).

Das folgende Beispiel zeigt die Standardkonfiguration für Linux-Debug in Visual Studio 2017 (und Visual Studio 2019, Version 16.0) basierend auf dem vorherigen Codebeispiel:

```json
{
      "name": "Linux-Debug",
      "generator": "Unix Makefiles",
      "remoteMachineName": "${defaultRemoteMachineName}",
      "configurationType": "Debug",
      "remoteCMakeListsRoot": "/var/tmp/src/${workspaceHash}/${name}",
      "cmakeExecutable": "/usr/local/bin/cmake",
      "buildRoot": "${env.LOCALAPPDATA}\\CMakeBuilds\\${workspaceHash}\\build\\${name}",
      "installRoot": "${env.LOCALAPPDATA}\\CMakeBuilds\\${workspaceHash}\\install\\${name}",
      "remoteBuildRoot": "/var/tmp/build/${workspaceHash}/build/${name}",
      "remoteInstallRoot": "/var/tmp/build/${workspaceHash}/install/${name}",
      "remoteCopySources": true,
      "remoteCopySourcesOutputVerbosity": "Normal",
      "remoteCopySourcesConcurrentCopies": "10",
      "remoteCopySourcesMethod": "rsync",
      "remoteCopySourcesExclusionList": [".vs", ".git"],
      "rsyncCommandArgs" : "-t --delete --delete-excluded",
      "remoteCopyBuildOutput" : "false",
      "cmakeCommandArgs": "",
      "buildCommandArgs": "",
      "ctestCommandArgs": "",
      "inheritEnvironments": [ "linux-x64" ]
}
```

::: moniker-end

::: moniker range="vs-2019"

Die Standardkonfiguration für Linux-Debug in Visual Studio 2019 ab Version 16.1 ist wie hier gezeigt:

```json
{
      "name": "Linux-Debug",
      "generator": "Unix Makefiles",
      "configurationType": "Debug",
      "cmakeExecutable": "/usr/bin/cmake",
      "remoteCopySourcesExclusionList": [ ".vs", ".git", "out" ],
      "cmakeCommandArgs": "",
      "buildCommandArgs": "",
      "ctestCommandArgs": "",
      "inheritEnvironments": [ "linux_x64" ],
      "remoteMachineName": "${defaultRemoteMachineName}",
      "remoteCMakeListsRoot": "$HOME/.vs/${projectDirName}/${workspaceHash}/src",
      "remoteBuildRoot": "$HOME/.vs/${projectDirName}/${workspaceHash}/out/build/${name}",
      "remoteInstallRoot": "$HOME/.vs/${projectDirName}/${workspaceHash}/out/install/${name}",
      "remoteCopySources": true,
      "rsyncCommandArgs": "-t --delete --delete-excluded",
      "remoteCopyBuildOutput": false,
      "remoteCopySourcesMethod": "rsync",
      "addressSanitizerRuntimeFlags": "detect_leaks=0",
      "variables": []
    }
  ]
}
```
::: moniker-end

Weitere Informationen zu diesen Einstellungen finden Sie in der [Referenz zu CMakeSettings.json](../build/cmakesettings-reference.md).


## <a name="optional-settings"></a>Optionale Einstellungen

Sie können über die folgenden optionalen Einstellungen mehr Kontrolle erlangen:

```json
{
      "remotePrebuildCommand": "",
      "remotePreGenerateCommand": "",
      "remotePostbuildCommand": "",
}
```

Mithilfe dieser Optionen können Sie Befehle vor und nach dem Erstellen und vor der CMake-Generierung auf dem Linux-System ausführen. Die Werte können ein beliebiger Befehl sein, der auf dem Remotesystem gültig ist. Die Ausgabe wird wieder zurück an Visual Studio geleitet.



## <a name="see-also"></a>Siehe auch

[Arbeiten mit Projekteigenschaften](../build/working-with-project-properties.md)<br/>
[CMake Projects in Visual Studio (CMake-Projekte in Visual Studio)](../build/cmake-projects-in-visual-studio.md)<br/>
[Herstellen einer Verbindung mit Ihrem Linux-Remotecomputer](connect-to-your-remote-linux-computer.md)<br/>
[Anpassen von CMake-Buildeinstellungen](../build/customize-cmake-settings.md)<br/>
[Konfigurieren von CMake-Debugsitzungen](../build/configure-cmake-debugging-sessions.md)<br/>
[Bereitstellen, Ausführen und Debuggen Ihres Linux-Projekts](deploy-run-and-debug-your-linux-project.md)<br/>
[CMake predefined configuration reference (Referenz für vordefinierte CMake-Konfigurationen)](../build/cmake-predefined-configuration-reference.md)<br/>
