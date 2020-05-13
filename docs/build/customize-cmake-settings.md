---
title: Anpassen von CMake-Buildeinstellungen in Visual Studio
ms.date: 08/20/2019
helpviewer_keywords:
- CMake build settings
ms.openlocfilehash: c6bd1404799ccc9ad6b689646cd066849d48fca8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328677"
---
# <a name="customize-cmake-build-settings"></a>Anpassen von CMake-Buildeinstellungen

::: moniker range="vs-2019"

In Visual Studio 2019 und höher können Sie mithilfe des **CMake-Einstellungs-Editors** Konfigurationen hinzufügen und ihre Einstellungen anpassen. Der Editor soll eine einfachere Alternative zum manuellen Bearbeiten der *Datei CMakeSettings.json* sein, aber wenn Sie die Datei direkt bearbeiten möchten, können Sie oben rechts im Editor auf den Link **JSON bearbeiten** klicken.

Um den Editor zu öffnen, klicken Sie auf die Dropdownliste **Konfiguration** in der Hauptsymbolleiste, und wählen Sie **Konfigurationen verwalten** aus.

![Dropdownliste „CMake-Konfigurationen“](media/vs2019-cmake-manage-configurations.png)

Jetzt wird der **Einstellungs-Editor** mit den installierten Konfigurationen auf der linken Seite angezeigt.

![CMake-Einstellungs-Editor](media/cmake-settings-editor.png)

Visual Studio `x64-Debug` stellt standardmäßig eine Konfiguration bereit. Sie können zusätzliche Konfigurationen hinzufügen, indem Sie auf das grüne Pluszeichen klicken. Die Einstellungen, die im Editor angezeigt werden, können je nachdem, welche Konfiguration ausgewählt ist, variieren.

Die Optionen, die Sie im Editor auswählen, werden in eine Datei mit dem Namen *CMakeSettings.json*geschrieben. Diese Datei stellt Befehlszeilenargumente und Umgebungsvariablen zur Verfügung, die beim Erstellen der Projekte an CMake übergeben werden. Visual Studio ändert *CMakeLists.txt* nie automatisch. Mit *CMakeSettings.json* können Sie den Build über Visual Studio anpassen, während Sie die CMake-Projektdateien unberührt lassen, damit andere In ihrem Team sie mit den von ihnen verwendenden Tools verwenden können.

## <a name="cmake-general-settings"></a>CMake – allgemeine Einstellungen

Die folgenden Einstellungen sind unter der Überschrift **Allgemein** verfügbar:

### <a name="configuration-name"></a>Konfigurationsname

Entspricht der Einstellung **name**. Dieser Name wird in der Dropdownliste der C++-Konfiguration angezeigt. Sie können das `${name}`-Makro verwenden, um weitere Eigenschaftswerte wie etwa Pfade zu verfassen.

### <a name="configuration-type"></a>Konfigurationstyp

Entspricht der Einstellung **configurationType**. Definiert den Typ der Buildkonfiguration für den ausgewählten Generator. Derzeit werden die Werte "Debug", "MinSizeRel", "Release" und "RelWithDebInfo" unterstützt. Es bildet [CMAKE_BUILD_TYPE](https://cmake.org/cmake/help/latest/variable/CMAKE_BUILD_TYPE.html)ab.

### <a name="toolset"></a>Toolset

Entspricht der Einstellung **inheritedEnvironments**. Definiert die Compilerumgebung, die zum Erstellen der ausgewählten Konfiguration verwendet wird. Die unterstützten Werte hängen von der Art der Konfiguration ab. Um eine benutzerdefinierte Umgebung zu erstellen, wählen Sie den **Link JSON bearbeiten** in der oberen rechten Ecke des Einstellungs-Editors aus, und bearbeiten Sie die Datei *CMakeSettings.json* direkt.

### <a name="cmake-toolchain-file"></a>CMake-Toolkettendatei

Pfad zur [CMake-Toolchain-Datei](https://cmake.org/cmake/help/latest/variable/CMAKE_TOOLCHAIN_FILE.html). Dieser Pfad wird als "-DCMAKE_TOOLCHAIN_FILE \<= filepath>" an CMake übergeben. Toolchain-Dateien geben Speicherorte von Compilern und Toolchain-Dienstprogrammen sowie andere Zielplattform- und Compilerinformationen an. Standardmäßig verwendet Visual Studio die [toolchain-Datei vcpkg,](https://github.com/microsoft/vcpkg/blob/master/docs/examples/installing-and-using-packages.md#cmake) wenn diese Einstellung nicht angegeben ist.

### <a name="build-root"></a>Buildstamm

Entspricht **buildRoot**. Ordnet [CMAKE_BINARY_DIR](https://cmake.org/cmake/help/v3.15/variable/CMAKE_BINARY_DIR.html)zu und gibt an, wo der CMake-Cache erstellt werden soll. Der angegebene Ordner wird erstellt, wenn er nicht vorhanden ist.

## <a name="command-arguments"></a>Befehlsargumente

Die folgenden Einstellungen sind unter der Überschrift **Befehlsargumente** verfügbar:

### <a name="cmake-command-arguments"></a>CMake-Befehlsargumente

Entspricht **cmakeCommandArgs**. Gibt alle zusätzlichen [Befehlszeilenoptionen](https://cmake.org/cmake/help/latest/manual/cmake.1.html) an, die an CMake.exe übergeben werden.

### <a name="build-command-arguments"></a>Build-Befehlsargumente

Entspricht **buildCommandArgs**. Gibt zusätzliche Switches an, die an das zugrunde liegende Buildsystem übergeben werden sollen. Wenn Sie `-v` z. B. den Ninja-Generator verwenden, wird Ninja dazu zwingt, Befehlszeilen auszugeben.

### <a name="ctest-command-arguments"></a>CTest-Befehlsargumente

Entspricht **ctestCommandArgs**. Gibt zusätzliche [Befehlszeilenoptionen](https://cmake.org/cmake/help/v3.15/manual/ctest.1.html) an, die beim Ausführen von Tests an CTest übergeben werden sollen.

## <a name="general-settings-for-remote-builds"></a>Allgemeine Einstellungen für Remotebuilds

Für Konfigurationen wie Linux, die Remotebuilds verwenden, sind ferner die folgenden Einstellungen verfügbar:

### <a name="rsync-command-arguments"></a>rsync-Befehlsargumente

Zusätzliche Befehlszeilenoptionen, die an [rsync](https://download.samba.org/pub/rsync/rsync.html), ein schnelles und vielseitiges Dateikopierwerkzeug, übergeben werden.

## <a name="cmake-variables-and-cache"></a>CMake-Variablen und -Cache

Mit diesen Einstellungen können Sie CMake-Variablen festlegen und in *CMakeSettings.json*speichern. Sie werden zur Buildzeit an CMake übergeben und überschreiben alle Werte in der *Datei CMakeLists.txt.* Sie können diesen Abschnitt in der gleichen Weise verwenden, in der Sie das CMakeGUI verwenden, um eine Liste aller für die Bearbeitung verfügbaren CMake-Variablen anzuzeigen. Klicken Sie auf die Schaltfläche **Speichern und Cache generieren**, um eine Liste aller für die Bearbeitung verfügbaren CMake-Variablen anzuzeigen, einschließlich erweiterter Variablen (mithilfe des CMakeGUI). Sie können die Liste nach Variablennamen filtern.

Entspricht **Variablen**. Enthält ein Name-Wert-Paar von CMake-Variablen, die als **-D-Namenswert** * _name_=* an CMake übergeben werden. Wenn Ihre CMake-Projekterstellungsanweisungen das Hinzufügen von Variablen direkt zur CMake-Cachedatei angeben, empfehlen wir, sie stattdessen hier hinzuzufügen.

## <a name="advanced-settings"></a>Erweiterte Einstellungen

### <a name="cmake-generator"></a>CMake-Generator

Entspricht **dem Generator**. Ordnet dem CMake **-G-Schalter** zu und gibt den zu [verwendenden CMake-Generator](https://cmake.org/cmake/help/latest/manual/cmake-generators.7.html) an. Diese Eigenschaft kann ebenfalls als Makro (`${generator}`) beim Erstellen anderer Eigenschaftswerte verwendet werden. Visual Studio unterstützt derzeit folgende CMake-Generatoren:

- "Ninja"
- "Unix Makefiles"
- "Visual Studio 16 2019"
- "Visual Studio 16 2019 Win64"
- "Visual Studio 16 2019 ARM"
- "Visual Studio 15 2017"
- "Visual Studio 15 2017 Win64"
- "Visual Studio 15 2017 ARM"
- "Visual Studio 14 2015"
- "Visual Studio 14 2015 Win64"
- "Visual Studio 14 2015 ARM"
  
Da Ninja für schnelle Build-Geschwindigkeiten anstelle von Flexibilität und Funktion entwickelt wurde, ist es als Standard festgelegt. Einige CMake-Projekte können jedoch mit Ninja keinen ordnungsgemäßen Build durchführen. In diesem Fall können Sie CMake anweisen, stattdessen ein Visual Studio-Projekt zu generieren.

### <a name="intellisense-mode"></a>IntelliSense-Modus

Der IntelliSense-Modus, der von der IntelliSense-Engine verwendet wird. Wenn kein Modus ausgewählt ist, erbt Visual Studio vom angegebenen Toolset.  

### <a name="install-directory"></a>Installationsverzeichnis

Das Verzeichnis, in dem CMake Ziele installiert. Karten zu [CMAKE_INSTALL_PREFIX](https://cmake.org/cmake/help/latest/variable/CMAKE_INSTALL_PREFIX.html).

### <a name="cmake-executable"></a>Ausführbare CMake-Datei

Der vollständige Pfad zur ausführbaren Dateidatei des CMake-Programms, einschließlich Dateiname und Erweiterung. Sie können eine benutzerdefinierte Version von CMake mit Visual Studio verwenden. Geben Sie für Remotebuilds den CMake-Speicherort auf dem Remotecomputer an.

Für Konfigurationen wie Linux, die Remotebuilds verwenden, sind ferner die folgenden Einstellungen verfügbar:

### <a name="remote-cmakeliststxt-root"></a>Remoteverzeichnis der Stammdatei „CMakeLists.txt“

Das Verzeichnis auf dem Remotecomputer, das die Stammdatei *CMakeLists.txt* enthält.

### <a name="remote-install-root"></a>Installationsstammverzeichnis auf dem Remotesystem

Das Verzeichnis auf dem Remotecomputer, in dem CMake Zieldateien installiert. Karten zu [CMAKE_INSTALL_PREFIX](https://cmake.org/cmake/help/latest/variable/CMAKE_INSTALL_PREFIX.html).

### <a name="remote-copy-sources"></a>Quellen auf Remotesystem kopieren

Gibt an, ob Quelldateien auf den Remotecomputer kopiert werden sollen, und sie können angeben, ob rsync oder sftp verwendet werden soll.

## <a name="directly-edit-cmakesettingsjson"></a>„CMakeSettings.json“ direkt bearbeiten

Sie können *CMakeSettings.json* auch direkt bearbeiten, um benutzerdefinierte Konfigurationen zu erstellen. Der **Einstellungs-Editor** weist eine Schaltfläche **JSON bearbeiten** oben rechts auf, mit der die Datei zur Bearbeitung geöffnet wird.

Das folgende Beispiel zeigt eine Beispielkonfiguration, die Sie als Ausgangspunkt verwenden können:

```json
    {
      "name": "x86-Debug",
      "generator": "Ninja",
      "configurationType": "Debug",
      "inheritEnvironments": [ "msvc_x86" ],
      "buildRoot": "${env.USERPROFILE}\\CMakeBuilds\\${workspaceHash}\\build\\${name}",
      "installRoot": "${env.USERPROFILE}\\CMakeBuilds\\${workspaceHash}\\install\\${name}",
      "cmakeCommandArgs": "",
      "buildCommandArgs": "-v",
      "ctestCommandArgs": ""
    },
```

JSON IntelliSense unterstützt Sie beim Bearbeiten der *Datei CMakeSettings.json:*

   ![CMake JSON IntelliSense](media/cmake-json-intellisense.png "CMake JSON IntelliSense")

Der JSON-Editor informiert Sie auch, wenn Sie inkompatible Einstellungen auswählen.

Weitere Informationen zu den einzelnen Eigenschaften in der Datei finden Sie in der [CMakeSettings.json-Schemareferenz](cmakesettings-reference.md).

::: moniker-end

::: moniker range="<=vs-2017"

Visual Studio 2017 bietet verschiedene CMake-Konfigurationen, die definieren, wie „CMake.exe“ aufgerufen wird, um den CMake-Cache für ein bestimmtes Projekt zu erstellen. Klicken Sie zum Hinzufügen einer neuen Konfiguration in der Symbolleiste auf die Konfigurations-Dropdownliste, und wählen Sie **Konfigurationen verwalten...** aus:

   ![CMake: „Konfigurationen verwalten...“](media/cmake-manage-configurations.png)

Sie können aus der Liste vordefinierter Konfigurationen wählen:

   ![Vordefinierte CMake-Konfigurationen](media/cmake-configurations.png)

Wenn Sie zum ersten Mal eine Konfiguration auswählen, erstellt Visual Studio eine *CMakeSettings.json-Datei* im Stammordner Ihres Projekts. Diese Datei wird verwendet, um die CMake-Cachedatei erneut zu erstellen, z.B. nach einem **Bereinigungsvorgang**.

Um eine zusätzliche Konfiguration hinzuzufügen, klicken Sie mit der rechten Maustaste auf *CMakeSettings.json,* und wählen **Sie Konfiguration hinzufügen**aus.

   ![CMake Add-Konfiguration](media/cmake-add-configuration.png "CMake-Konfiguration hinzufügen")

Sie können die Datei auch mithilfe des **Editors für CMake-Einstellungen** bearbeiten. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf *CMakeSettings.json* und wählen **Sie CMake-Einstellungen bearbeiten**. Alternativ können Sie oben im Editor-Fenster aus der Konfigurations-Dropdownliste **Konfigurationen verwalten...** auswählen.

Sie können *CMakeSettings.json* auch direkt bearbeiten, um benutzerdefinierte Konfigurationen zu erstellen. Das folgende Beispiel zeigt eine Beispielkonfiguration, die Sie als Ausgangspunkt verwenden können:

```json
    {
      "name": "x86-Debug",
      "generator": "Ninja",
      "configurationType": "Debug",
      "inheritEnvironments": [ "msvc_x86" ],
      "buildRoot": "${env.USERPROFILE}\\CMakeBuilds\\${workspaceHash}\\build\\${name}",
      "installRoot": "${env.USERPROFILE}\\CMakeBuilds\\${workspaceHash}\\install\\${name}",
      "cmakeCommandArgs": "",
      "buildCommandArgs": "-v",
      "ctestCommandArgs": ""
    },
```

JSON IntelliSense unterstützt Sie beim Bearbeiten der *Datei CMakeSettings.json:*

   ![CMake JSON IntelliSense](media/cmake-json-intellisense.png "CMake JSON IntelliSense")

Weitere Informationen zu den einzelnen Eigenschaften in der Datei finden Sie in der [CMakeSettings.json-Schemareferenz](cmakesettings-reference.md).

::: moniker-end

## <a name="see-also"></a>Siehe auch

[CMake-Projekte in Visual Studio](cmake-projects-in-visual-studio.md)<br/>
[Konfigurieren eines Linux CMake-Projekts](../linux/cmake-linux-project.md)<br/>
[Herstellen einer Verbindung mit Ihrem Linux-Remotecomputer](../linux/connect-to-your-remote-linux-computer.md)<br/>
[Konfigurieren von CMake-Debugsitzungen](configure-cmake-debugging-sessions.md)<br/>
[Bereitstellen, Ausführen und Debuggen Ihres Linux-Projekts](../linux/deploy-run-and-debug-your-linux-project.md)<br/>
[CMake predefined configuration reference (Referenz für vordefinierte CMake-Konfigurationen)](cmake-predefined-configuration-reference.md)
