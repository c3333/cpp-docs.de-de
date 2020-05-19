---
title: Erstellen und Konfigurieren eines Linux CMake-Projekts in Visual Studio
description: Hier erfahren Sie, wie Sie ein Linux CMake-Projekt in Visual Studio erstellen, konfigurieren, bearbeiten und kompilieren.
ms.date: 05/03/2020
ms.assetid: f8707b32-f90d-494d-ae0b-1d44425fdc25
ms.openlocfilehash: c12e32801c992f6ba3675327b9ae537890202a4c
ms.sourcegitcommit: 8a01ae145bc65f5bc90d6e47b4a1bdf47b073ee7
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82765759"
---
# <a name="create-and-configure-a-linux-cmake-project"></a>Erstellen und Konfigurieren eines Linux-CMake-Projekts

::: moniker range="vs-2015"

Die Unterstützung für Linux ist in Visual Studio 2017 und höher verfügbar. Wenn die Dokumentation für diese Versionen angezeigt werden soll, legen Sie das Steuerelement für die Auswahl der **Version** von Visual Studio für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich am Anfang des Inhaltsverzeichnisses auf dieser Seite.

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="before-you-begin"></a>Vorbereitungen

Stellen Sie zuerst sicher, dass die Workload **Linux-Entwicklung mit C++** mit der CMake-Komponente installiert ist. Weitere Informationen finden Sie unter [Install the C++ Linux workload in Visual Studio (Installieren der C++-Workload unter Linux in Visual Studio)](download-install-and-setup-the-linux-development-workload.md).

Stellen Sie sicher, dass Folgendes auf dem Linux-System installiert ist:

- gcc
- gdb
- rsync
- zip
- ninja-build

::: moniker-end

::: moniker range="vs-2019"

Für die Unterstützung von CMake-Projekten unter Linux ist eine aktuelle Version von CMake auf dem Zielcomputer erforderlich. Die vom Standardpaket-Manager einer Distribution bereitgestellte Version ist häufig nicht ausreichend aktuell, um alle für Visual Studio erforderlichen Features zu unterstützen. Visual Studio 2019 erkennt, ob eine aktuelle Version von CMake auf dem Linux-System installiert ist. Wenn keine gefunden werden kann, zeigt Visual Studio über dem Editorbereich eine Infoleiste an. Dort haben Sie die Möglichkeit, CMake von [https://github.com/Microsoft/CMake/releases](https://github.com/Microsoft/CMake/releases) herunterzuladen und zu installieren.

Die CMake-Unterstützung in Visual Studio erfordert die Servermodusunterstützung, die in CMake 3.8 eingeführt wurde. In Visual Studio 2019 wird Version 3.14 oder höher empfohlen.

::: moniker-end

::: moniker range="vs-2017"

Die CMake-Unterstützung in Visual Studio erfordert die Servermodusunterstützung, die in CMake 3.8 eingeführt wurde. Laden Sie für eine von Microsoft bereitgestellte CMake-Variante unter [https://github.com/Microsoft/CMake/releases](https://github.com/Microsoft/CMake/releases) die aktuellsten vordefinierten Binärdateien herunter.

Die Binärdateien werden unter `~/.vs/cmake` installiert. Nach dem Bereitstellen der Binärdateien wird Ihr Projekt automatisch neu generiert. Wenn die vom Feld `cmakeExecutable` in *CMakeSettings.json* angegebene CMake-Version ungültig ist (Version nicht vorhanden oder ungültig) und die vorab erstellten Binärdateien vorhanden sind, ignoriert Visual Studio `cmakeExecutable` und verwendet die vorab erstellten Binärdateien.

:::moniker-end

::: moniker range="vs-2019"

## <a name="create-a-new-linux-cmake-project"></a>Erstellen eines neuen CMake-Projekts unter Linux

So erstellen Sie ein neues Linux CMake-Projekt in Visual Studio 2019

1. Wählen Sie in Visual Studio **Datei > Neues Projekt** aus, oder drücken Sie **STRG + UMSCHALT + N**.
1. Legen Sie **Sprache** auf **C++** fest, und suchen Sie nach „CMake“. Klicken Sie dann auf **Weiter**. Geben Sie einen **Namen** und einen **Speicherort** an, und klicken Sie auf **Erstellen**.

Visual Studio erstellt eine minimale Datei namens *CMakeLists.txt* mit nur dem Namen der ausführbaren Datei und der mindestens erforderlichen CMake-Version. Sie können diese Datei jedoch manuell nach Belieben bearbeiten. Visual Studio wird Ihre Änderungen in keinem Fall überschreiben. Sie können CMake-Befehlszeilenargumente und Umgebungsvariablen in dieser Datei angeben. Klicken Sie mit der rechten Maustaste auf die Datei *CMakeLists.txt* im **Projektmappen-Explorer**, und wählen Sie **CMake Settings for Project** (Einstellungen für CMake-Projekt) aus. Klicken Sie zum Angeben von Optionen für das Debuggen mit der rechten Maustaste auf den Projektknoten, und wählen Sie **Debug- und Starteinstellungen**.

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="open-a-cmake-project-folder"></a>Öffnen eines CMake-Projektordners

Wenn Sie einen Ordner öffnen, der ein bereits vorhandenes CMake-Projekt enthält, verwendet Visual Studio Variablen im CMake-Cache, um IntelliSense und Builds automatisch zu konfigurieren. Lokale Konfigurations- und Debugeinstellungen werden in JSON-Dateien gespeichert. Sie können diese Dateien optional für andere Personen freigeben, die Visual Studio verwenden.

Visual Studio ändert die *CMakeLists.txt*-Dateien nicht. Sie bleiben unverändert, damit andere Personen, die am selben Projekt arbeiten, weiterhin ihre vorhandenen Tools verwenden können. Visual Studio generiert den Cache neu, wenn Sie Änderungen an *CMakeLists.txt* oder in einigen Fällen an *CMakeSettings.json* speichern. Wenn Sie aber eine Konfiguration des Typs **Vorhandener Cache** nutzen, ändert Visual Studio den Cache nicht.

Allgemeine Informationen zur Unterstützung von CMake in Visual Studio finden Sie unter [CMake-Projekte in Visual Studio](../build/cmake-projects-in-visual-studio.md). Diesen Artikel sollten Sie lesen, bevor Sie hier fortfahren.

Klicken Sie zum Starten im Hauptmenü auf **Datei** > **Öffnen** > **Ordner**, oder geben Sie `devenv.exe <foldername>` in einem Fenster mit einer [Developer-Eingabeaufforderung](../build/building-on-the-command-line.md) ein. Der Ordner, den Sie öffnen, sollte eine Datei *CMakeLists.txt* sowie Ihren Quellcode enthalten.

Das folgende Beispiel zeigt eine einfache *CMakeLists.txt*-Datei und eine CPP-Datei:

```cpp
// hello.cpp

#include <iostream>

int main(int argc, char* argv[])
{
    std::cout << "Hello from Linux CMake" << std::endl;
}
```

*CMakeLists.txt:*

```txt
cmake_minimum_required(VERSION 3.8)
project (hello-cmake)
add_executable(hello-cmake hello.cpp)
```

## <a name="choose-a-linux-target"></a>Auswählen eines Linux-Ziels

Sobald Sie den Ordner öffnen, analysiert Visual Studio die Datei *CMakeLists.txt* und gibt das Windows-Ziel **x86-Debug** an. Ändern Sie die Projekteinstellungen auf **Linux-Debug** oder **Linux-Release**, um auf ein Linux-Remotesystem abzuzielen. (Siehe [Konfigurieren von CMake-Einstellungen für Linux](#configure_cmake_linux) weiter unten.)

::: moniker-end

::: moniker range="vs-2019"

Klicken Sie auf der Hauptsymbolleiste in der Dropdownliste „Konfiguration“ auf **Konfigurationen verwalten**, um „Windows-Subsystem für Linux“ als Ziel festzulegen. Klicken Sie dann auf die Schaltfläche **Konfiguration hinzufügen**, und wählen Sie **WSL-Debug** oder **WSL-Release** aus, wenn GCC verwendet wird. Verwenden Sie bei Nutzung des Clang/LLVM-Toolsets die Clang-Varianten.

**Visual Studio 2019, Version 16.1** Wenn WSL als Ziel verwendet wird, müssen Quellen oder Header nicht kopiert werden. Dies liegt daran, dass der Compiler unter Linux direkten Zugriff auf Ihre Quelldateien im Dateisystem von Windows hat. (Bei der Windows 10-Version 1903 und höheren Versionen können Windows-Anwendungen ebenfalls direkt auf die Linux-Headerdateien zugreifen. Visual Studio nutzt diese Möglichkeit noch nicht.)

::: moniker-end

::: moniker range=">=vs-2017"

Für Remoteziele wählt Visual Studio standardmäßig das erste Remotesystem in der Liste unter **Extras** > **Optionen** > **Plattformübergreifend** > **Verbindungs-Manager** aus. Wenn keine Remoteverbindungen gefunden werden, werden Sie aufgefordert, eine Remoteverbindung zu erstellen. Weitere Informationen finden Sie unter [Herstellen einer Verbindung mit Ihrem Linux-Remotecomputer](connect-to-your-remote-linux-computer.md).

Wenn Sie ein Linux-Remoteziel angeben, wird Ihre Quelle in das Remotesystem kopiert.

Wenn Sie ein Ziel ausgewählt haben, wird CMake zum Generieren des CMake-Caches für Ihr Projekt automatisch auf dem Linux-System ausgeführt.

![Generieren des CMake-Caches unter Linux](media/cmake-linux-1.png "Generieren des CMake-Caches unter Linux")

Visual Studio kopiert automatisch Header vom Linux-Computer in ein Verzeichnis auf Ihrem lokalen Windows-Computer, um IntelliSense-Unterstützung für Header auf Linux-Remotesystemen bereitzustellen. Weitere Informationen finden Sie unter [IntelliSense für Remoteheader (Visual Studio 2017-Version 15.7 und höher)](configure-a-linux-project.md#remote_intellisense).

## <a name="debug-the-cmake-project"></a><a name="debug_cmake_project"></a> Debuggen des CMake-Projekts

Wenn Sie Ihren Code im angegebenen Zielsystem debuggen möchten, legen Sie einen Haltepunkt fest. Wählen Sie das CMake-Ziel als Startelement im Symbolleistenmenü neben den Projekteinstellungen auf. Klicken Sie dann auf **&#x23f5; Starten** in der Symbolleiste, oder drücken Sie **F5**.

Wenn Sie die Befehlszeilenargumente Ihres Programms anpassen möchten, klicken Sie oben im **Projektmappen-Explorer** auf die Schaltfläche **Switch Targets** (Ziele wechseln), und wählen Sie dann die Ansicht **Ziele** aus. Klicken Sie mit der rechten Maustaste auf das Ziel, und wählen Sie **Debug- und Starteinstellungen** aus. Durch diesen Befehl wird eine Konfigurationsdatei *launch.vs.json* geöffnet oder erstellt, die Informationen zu Ihrem Programm enthält. Fügen Sie der Datei wie im folgenden Beispiel veranschaulicht eine **sourceFilemileMapap**-Eigenschaft hinzu, um den Speicherort für Quelldateien festzulegen.

```json
"MIMode": "gdb",
"externalConsole": true,
"sourceFileMap": {
"c/Users/USER/source/repos/CMAKEPROJECTNAME": "C:\\Users\\USER\\source\\repos\\CMAKEPROJECTNAME"
},
"remoteMachineName": "${debugInfo.remoteMachineName}",
```

Um zusätzliche Argumente anzugeben, fügen Sie sie dem JSON-Array `args` hinzu. Weitere Informationen finden Sie unter [Open Folder projects for C++ (Verwenden von „Ordner öffnen“ mit Projekten in Visual C++)](../build/open-folder-projects-cpp.md) und [Configure CMake debugging sessions (Konfigurieren von CMake-Debugsitzungen)](../build/configure-cmake-debugging-sessions.md).

## <a name="configure-cmake-settings-for-linux"></a><a name="configure_cmake_linux"></a> Konfigurieren von CMake-Einstellungen für Linux

Eine *CMakeSettings.json*-Datei in einem CMake-Projekt unter Linux kann alle unter [Customize CMake settings](../build/customize-cmake-settings.md) (Anpassen von CMake-Einstellungen) aufgeführten Eigenschaften angeben sowie weitere Eigenschaften, die die Buildeinstellungen auf dem Linux-Remotecomputer steuern.

::: moniker-end

::: moniker range="vs-2019"

Öffnen Sie über die Hauptsymbolleiste die Dropdownliste **Konfiguration**, und wählen Sie die Option **Konfigurationen verwalten** aus, um die Standardeinstellungen von CMake in Visual Studio 2019 zu ändern.

![Verwalten von CMake-Konfigurationen](../build/media/vs2019-cmake-manage-configurations.png "Dropdownliste „CMake-Konfigurationen“")

Durch diesen Befehl wird der **Editor für CMake-Einstellungen** geöffnet, den Sie zum Bearbeiten der *CMakeSettings.json*-Datei im Stammprojektordner verwenden können. Sie können die Datei auch direkt öffnen, indem Sie im Editor auf **JSON bearbeiten** klicken. Weitere Informationen finden Sie unter [Anpassen von CMake-Einstellungen](../build/customize-cmake-settings.md).

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

::: moniker range="vs-2017"

Wenn Sie die Standard-CMake-Einstellungen in Visual Studio 2017 ändern möchten, klicken Sie im Hauptmenü auf **CMake** > **Change CMake Settings** > **CMakeLists.txt** (CMake > CMake-Einstellungen ändern > CMakeLists.txt). Alternativ können Sie auch mit der rechten Maustaste im **Projektmappen-Explorer** auf *CMakeSettings.txt* klicken und die Option **Change CMake Settings** (CMake-Einstellungen ändern) auswählen. Visual Studio erstellt dann eine neue *CMakeSettings.json*-Datei im Stammordner des Projekts. Sie können die Datei mit dem Editor für **CMake-Einstellungen** öffnen oder die Datei direkt ändern. Weitere Informationen finden Sie unter [Customize CMake settings (Anpassen von CMake-Einstellungen)](../build/customize-cmake-settings.md).

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

::: moniker range=">=vs-2017"

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
[CMake predefined configuration reference (Referenz für vordefinierte CMake-Konfigurationen)](../build/cmake-predefined-configuration-reference.md)

::: moniker-end
