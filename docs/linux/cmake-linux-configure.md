---
title: Konfigurieren eines CMake-Projekts für Linux in Visual Studio
description: Konfigurieren von CMake-Einstellungen für Linux in Visual Studio
ms.date: 08/08/2020
ms.openlocfilehash: 4bc6d5d82a0f1cd21e8f989eb92b431d38b2bf5c
ms.sourcegitcommit: 111ee74772d7f308d3414b5d42cbc1e90287f081
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/20/2020
ms.locfileid: "88659343"
---
# <a name="configure-a-linux-cmake-project-in-visual-studio"></a>Konfigurieren eines CMake-Projekts für Linux in Visual Studio

::: moniker range="vs-2015"
Die Unterstützung für Linux ist in Visual Studio 2017 und höher verfügbar. Wenn die Dokumentation für diese Versionen angezeigt werden soll, legen Sie die Dropdownliste **Version** über dem Inhaltsverzeichnis auf **Visual Studio 2017** oder **Visual Studio 2019** fest.
::: moniker-end

::: moniker range=">=vs-2017"
In diesem Thema wird beschrieben, wie eine Linux-Konfiguration einem CMake-Projekt hinzugefügt wird, das entweder auf ein Linux-Remotesystem oder ein Windows-Subsystem für Linux (WSL) abzielt. Dabei wird die Reihe fortgesetzt, die mit [Erstellen eines CMake-Projekts für Linux in Visual Studio](cmake-linux-project.md) begonnen hat. Wenn Sie stattdessen MSBuild verwenden, finden Sie weitere Informationen unter [Konfigurieren eines MSBuild-Projekts für Linux in Visual Studio](configure-a-linux-project.md).

## <a name="add-a-linux-configuration"></a>Hinzufügen einer Linux-Konfiguration

Eine Konfiguration dient dazu, mit dem gleichen Quellcode auf verschiedene Plattformen (Windows, WSL, Remotesystem) abzuzielen. Eine Konfiguration dient auch zum Festlegen Ihrer Compiler, zum Übergeben von Umgebungsvariablen und zum Anpassen des Aufrufs von CMake. Die Datei *CMakeSettings.json* gibt alle unter [Anpassen von CMake-Buildeinstellungen](../build/customize-cmake-settings.md) aufgeführten Eigenschaften sowie weitere Eigenschaften an, die die Buildeinstellungen auf dem Linux-Remotecomputer steuern.
::: moniker-end

::: moniker range="vs-2017"
Wenn Sie die Standard-CMake-Einstellungen in Visual Studio 2017 ändern möchten, klicken Sie im Hauptmenü auf **CMake** > **Change CMake Settings** > **CMakeLists.txt** (CMake > CMake-Einstellungen ändern > CMakeLists.txt). Alternativ können Sie auch mit der rechten Maustaste im **Projektmappen-Explorer** auf *CMakeLists.txt* klicken und die Option **CMake-Einstellungen ändern** auswählen. Visual Studio erstellt dann eine neue *CMakeSettings.json*-Datei im Stammordner des Projekts. Um Änderungen vorzunehmen, öffnen Sie die Datei, und ändern Sie sie direkt. Weitere Informationen finden Sie unter [Customize CMake settings (Anpassen von CMake-Einstellungen)](../build/customize-cmake-settings.md).

Die Standardkonfiguration für Linux-Debuggen in Visual Studio 2017 (und Visual Studio 2019, Version 16.0) sieht wie folgt aus:

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
Öffnen Sie über die Hauptsymbolleiste die Dropdownliste **Konfiguration**, und wählen Sie die Option **Konfigurationen verwalten** aus, um die Standardeinstellungen von CMake in Visual Studio 2019 zu ändern.

![Verwalten von CMake-Konfigurationen](../build/media/vs2019-cmake-manage-configurations.png "Dropdownliste „CMake-Konfigurationen“")

Durch diesen Befehl wird der **Editor für CMake-Einstellungen** geöffnet, den Sie zum Bearbeiten der Datei *CMakeSettings.json* im Stammprojektordner verwenden können. Sie können die Datei auch im JSON-Editor öffnen, indem Sie im Editor auf die Schaltfläche **JSON bearbeiten** klicken. Weitere Informationen finden Sie unter [Anpassen von CMake-Einstellungen](../build/customize-cmake-settings.md).

Die Standardkonfiguration für das Linux-Debuggen in Visual Studio 2019, Version 16.1 sieht wie folgt aus:

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

Ab Visual Studio 2019, Version 16.6 ist Ninja der Standardgenerator für Konfigurationen, die auf ein Remotesystem oder das WSL abzielen. Weitere Informationen finden Sie in diesem Beitrag im [C++-Teamblog](https://devblogs.microsoft.com/cppblog/linux-development-with-visual-studio-first-class-support-for-gdbserver-improved-build-times-with-ninja-and-updates-to-the-connection-manager/).

::: moniker-end
::: moniker range=">=vs-2017"
Weitere Informationen zu diesen Einstellungen finden Sie in der [Referenz zu CMakeSettings.json](../build/cmakesettings-reference.md).

Beim Erstellen eines Builds:
- Für Remoteziele wählt Visual Studio standardmäßig das erste Remotesystem in der Liste unter **Extras** > **Optionen** > **Plattformübergreifend** > **Verbindungs-Manager** aus.
- Wenn keine Remoteverbindungen gefunden werden, werden Sie aufgefordert, eine Remoteverbindung zu erstellen. Weitere Informationen finden Sie unter [Herstellen einer Verbindung mit Ihrem Linux-Remotecomputer](connect-to-your-remote-linux-computer.md).

## <a name="choose-a-linux-target"></a>Auswählen eines Linux-Ziels

Sobald Sie einen CMake-Projektordner öffnen, analysiert Visual Studio die Datei *CMakeLists.txt* und gibt das Windows-Ziel **x86-Debug** an. Ändern Sie die Projekteinstellungen in **Linux-Debug** oder **Linux-Release**, um auf ein Linux-Remotesystem abzuzielen.

Wenn Sie ein Linux-Remoteziel angeben, wird Ihre Quelle in das Remotesystem kopiert.

Wenn Sie ein Ziel ausgewählt haben, wird CMake zum Generieren des CMake-Caches für Ihr Projekt automatisch auf dem Linux-System ausgeführt:

![Generieren des CMake-Caches unter Linux](media/cmake-linux-1.png "Generieren des CMake-Caches unter Linux")

::: moniker-end
::: moniker range="vs-2019"

### <a name="target-windows-subsystem-for-linux"></a>Abzielen auf das Windows-Subsystem für Linux

Wenn Sie auf das Windows-Subsystem für Linux (WSL) abzielen, müssen Sie keine Remoteverbindung hinzufügen.

Um auf das WSL abzuzielen, wählen Sie auf der Hauptsymbolleiste in der Dropdownliste „Konfiguration“ **Konfigurationen verwalten** aus. Klicken Sie dann auf die Schaltfläche **Konfiguration hinzufügen**, und wählen Sie **WSL-Debug** oder **WSL-Release** aus, wenn GCC verwendet wird. Verwenden Sie bei Nutzung des Clang/LLVM-Toolsets die Clang-Varianten.

**Visual Studio 2019, Version 16.1** Wenn Sie auf die WSL zielen, muss Visual Studio keine Quelldateien kopieren und zwei synchrone Kopien Ihrer Buildstruktur pflegen, da der Compiler unter Linux direkten Zugriff auf Ihre Quelldateien im eingebundenen Windows-Dateisystem hat.
::: moniker-end
::: moniker range=">=vs-2017"

### <a name="intellisense"></a>IntelliSense

Damit IntelliSense für C++ präzise arbeitet, ist ein Zugriff auf die C++-Header erforderlich, auf die Ihre C++-Quelldateien verweisen. Visual Studio verwendet automatisch die Header, auf die von einem CMake-Projekt von Linux zu Windows verwiesen wird, um ein originalgetreues IntelliSense-Erlebnis zu bieten. Weitere Informationen finden Sie unter [IntelliSense für Remoteheader (Visual Studio 2017-Version 15.7 und höher)](configure-a-linux-project.md#remote_intellisense).

### <a name="locale-setting"></a>Einstellung des Gebietsschemas

Visual Studio-Spracheinstellungen werden nicht an Linux-Ziele weitergegeben, da Visual Studio installierte Pakete nicht verwaltet oder konfiguriert. Nachrichten, die im Ausgabefenster angezeigt werden (z. B. Buildfehler), werden mit der Sprache und dem Gebietsschema des Linux-Ziels angezeigt. Sie müssen Ihre Linux-Ziele für das gewünschte Gebietsschema konfigurieren.

## <a name="additional-settings"></a>Zusätzliche Einstellungen

Mithilfe dieser Einstellungen können Sie Befehle vor und nach dem Build und vor der CMake-Generierung auf dem Linux-System ausführen. Die Werte können ein beliebiger Befehl sein, der auf dem Remotesystem gültig ist. Die Ausgabe wird wieder zurück an Visual Studio geleitet.

```json
{
      "remotePrebuildCommand": "",
      "remotePreGenerateCommand": "",
      "remotePostbuildCommand": "",
}
```

## <a name="next-steps"></a>Nächste Schritte

[Konfigurieren von CMake-Debugsitzungen](../build/configure-cmake-debugging-sessions.md?toc=/cpp/linux/toc.json&bc=/cpp/_breadcrumb/toc.json)

## <a name="see-also"></a>Weitere Informationen

[Arbeiten mit Projekteigenschaften](../build/working-with-project-properties.md)<br/>
[Anpassen von CMake-Buildeinstellungen](../build/customize-cmake-settings.md)<br/>
[CMake predefined configuration reference (Referenz für vordefinierte CMake-Konfigurationen)](../build/cmake-predefined-configuration-reference.md)

::: moniker-end
