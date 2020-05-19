---
title: Anpassen von CMake-Buildeinstellungen in Visual Studio
ms.date: 08/20/2019
helpviewer_keywords:
- CMake build settings
ms.openlocfilehash: c6bd1404799ccc9ad6b689646cd066849d48fca8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328677"
---
# <a name="customize-cmake-build-settings"></a>Anpassen von CMake-Buildeinstellungen

::: moniker range="vs-2019"

In Visual Studio 2019 und höher können Sie mithilfe des **CMake-Einstellungs-Editors** Konfigurationen hinzufügen und ihre Einstellungen anpassen. Der Editor soll eine einfachere Alternative zur manuellen Bearbeitung der Datei *CMakeSettings.json* bieten, aber wenn Sie es vorziehen, die Datei direkt zu bearbeiten, können Sie auf den Link **JSON bearbeiten** oben rechts im Editor klicken.

Um den Editor zu öffnen, klicken Sie auf die Dropdownliste **Konfiguration** in der Hauptsymbolleiste, und wählen Sie **Konfigurationen verwalten** aus.

![Dropdownliste „CMake-Konfigurationen“](media/vs2019-cmake-manage-configurations.png)

Jetzt wird der **Einstellungs-Editor** mit den installierten Konfigurationen auf der linken Seite angezeigt.

![CMake-Einstellungs-Editor](media/cmake-settings-editor.png)

Visual Studio stellt standardmäßig eine `x64-Debug`-Konfiguration bereit. Sie können zusätzliche Konfigurationen hinzufügen, indem Sie auf das grüne Pluszeichen klicken. Die im Editor angezeigten Einstellungen unterscheiden sich möglicherweise abhängig von der ausgewählten Konfiguration.

Die Optionen, die Sie im Editor auswählen, werden in eine Datei mit dem Namen *CMakeSettings.json* geschrieben. Diese Datei stellt Befehlszeilenargumente und Umgebungsvariablen zur Verfügung, die beim Erstellen der Projekte an CMake übergeben werden. Visual Studio ändert *CMakeLists.txt* nie automatisch; mithilfe von *CMakeSettings.json* können Sie den Build über Visual Studio anpassen, ohne die CMake-Projektdateien zu bearbeiten, sodass andere in Ihrem Team sie mit Tools ihrer Wahl nutzen können.

## <a name="cmake-general-settings"></a>CMake – allgemeine Einstellungen

Die folgenden Einstellungen sind unter der Überschrift **Allgemein** verfügbar:

### <a name="configuration-name"></a>Konfigurationsname

Entspricht der Einstellung **name**. Dieser Name wird in der Dropdownliste für die C++-Konfiguration angezeigt. Sie können das `${name}`-Makro verwenden, um weitere Eigenschaftswerte wie etwa Pfade zu verfassen.

### <a name="configuration-type"></a>Konfigurationstyp

Entspricht der Einstellung **configurationType**. Definiert den Typ der Buildkonfiguration für den ausgewählten Generator. Derzeit werden die Werte "Debug", "MinSizeRel", "Release" und "RelWithDebInfo" unterstützt. Diese Einstellung ist [CMAKE_BUILD_TYPE](https://cmake.org/cmake/help/latest/variable/CMAKE_BUILD_TYPE.html) zugeordnet.

### <a name="toolset"></a>Toolset

Entspricht der Einstellung **inheritedEnvironments**. Mit dieser Einstellung wird die Compilerumgebung definiert, die zum Erstellen der ausgewählten Konfiguration verwendet wird. Die unterstützten Werte hängen von der Art der Konfiguration ab. Klicken Sie auf den Link **JSON bearbeiten** in der rechten oberen Ecke des Einstellungs-Editors, und bearbeiten Sie die Datei *CMakeSettings.json* direkt, um eine benutzerdefinierte Umgebung zu erstellen.

### <a name="cmake-toolchain-file"></a>CMake-Toolkettendatei

Hierbei handelt es sich um den Pfad zur [CMake-Toolkettendatei](https://cmake.org/cmake/help/latest/variable/CMAKE_TOOLCHAIN_FILE.html). Dieser Pfad wird an CMake als „-DCMAKE_TOOLCHAIN_FILE = \<Dateipfad>“ übergeben. In Toolkettendateien werden die Speicherorte von Compilern und Toolketten-Hilfsprogrammen sowie andere Informationen in Bezug auf die Zielplattform und Compiler angegeben. Wenn für diese Einstellung nichts angegeben ist, verwendet Visual Studio standardmäßig die [VCPKG-Toolkettendatei](https://github.com/microsoft/vcpkg/blob/master/docs/examples/installing-and-using-packages.md#cmake).

### <a name="build-root"></a>Buildstamm

Entspricht **buildRoot**. Diese Einstellung ist [CMAKE_BINARY_DIR](https://cmake.org/cmake/help/v3.15/variable/CMAKE_BINARY_DIR.html) zugeordnet und gibt an, wo der CMake-Cache erstellt werden soll. Wenn der angegebene Ordner nicht vorhanden ist, wird er erstellt.

## <a name="command-arguments"></a>Befehlsargumente

Die folgenden Einstellungen sind unter der Überschrift **Befehlsargumente** verfügbar:

### <a name="cmake-command-arguments"></a>CMake-Befehlsargumente

Entspricht **cmakeCommandArgs**. Diese Einstellung gibt zusätzliche [Befehlszeilenoptionen](https://cmake.org/cmake/help/latest/manual/cmake.1.html) an, die an CMake.exe übergeben werden.

### <a name="build-command-arguments"></a>Build-Befehlsargumente

Diese Einstellung entspricht **buildCommandArgs**. Sie gibt zusätzliche Parameter an, die an das zugrunde liegende Buildsystem übergeben werden sollen. Beispielsweise wird beim Übergeben von `-v` bei Verwendung des Ninja-Generators erzwungen, dass Ninja Befehlszeilen ausgibt.

### <a name="ctest-command-arguments"></a>CTest-Befehlsargumente

Diese Einstellung entspricht **ctestCommandArgs**. Sie gibt zusätzliche [Befehlszeilenoptionen](https://cmake.org/cmake/help/v3.15/manual/ctest.1.html) an, die beim Ausführen von Tests an CTest übergeben werden sollen.

## <a name="general-settings-for-remote-builds"></a>Allgemeine Einstellungen für Remotebuilds

Für Konfigurationen wie Linux, die Remotebuilds verwenden, sind ferner die folgenden Einstellungen verfügbar:

### <a name="rsync-command-arguments"></a>rsync-Befehlsargumente

Bei dieser Einstellung werden zusätzliche Befehlszeilenoptionen an [rsync](https://download.samba.org/pub/rsync/rsync.html) übergeben, ein schnelles und vielseitiges Tool zum Kopieren von Dateien.

## <a name="cmake-variables-and-cache"></a>CMake-Variablen und -Cache

Mithilfe dieser Einstellungen können Sie CMake-Variablen festlegen und in *CMakeSettings.json* speichern. Sie werden zur Erstellungszeit an CMake übergeben und setzen die in der Datei *CMakeLists.txt* vorhandenen Werte außer Kraft. Sie können diesen Abschnitt in der gleichen Weise verwenden, in der Sie das CMakeGUI verwenden, um eine Liste aller für die Bearbeitung verfügbaren CMake-Variablen anzuzeigen. Klicken Sie auf die Schaltfläche **Speichern und Cache generieren**, um eine Liste aller für die Bearbeitung verfügbaren CMake-Variablen anzuzeigen, einschließlich erweiterter Variablen (mithilfe des CMakeGUI). Sie können die Liste nach dem Variablennamen filtern.

Diese Einstellung entspricht **variables**. Sie enthält ein Name/Wert-Paar von CMake-Variablen, die als **-D** *_Name_=_Wert_* an CMake übergeben werden. Wenn die Buildanweisungen Ihres CMake-Projekts das direkte Hinzufügen aller Variablen zur CMake-Cachedatei festlegen, wird empfohlen, diese stattdessen hier hinzuzufügen.

## <a name="advanced-settings"></a>Erweiterte Einstellungen

### <a name="cmake-generator"></a>CMake-Generator

Diese Einstellung entspricht **generator**. Sie ist der CMake-Option **-G** zugeordnet und gibt den [CMake-Generator](https://cmake.org/cmake/help/latest/manual/cmake-generators.7.html) an, der verwendet werden soll. Diese Eigenschaft kann ebenfalls als Makro (`${generator}`) beim Erstellen anderer Eigenschaftswerte verwendet werden. Visual Studio unterstützt derzeit folgende CMake-Generatoren:

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
  
Da Ninja für schnelle Buildgeschwindigkeiten statt für Flexibilität und Funktionalität entwickelt wurde, ist dieser Generator als Standardwert festgelegt. Einige CMake-Projekte können jedoch mit Ninja keinen ordnungsgemäßen Build durchführen. In diesem Fall können Sie CMake anweisen, stattdessen ein Visual Studio-Projekt zu erstellen.

### <a name="intellisense-mode"></a>IntelliSense-Modus

Hierbei handelt es sich um den IntelliSense-Modus, der von der IntelliSense-Engine verwendet wird. Wenn kein Modus ausgewählt ist, erbt Visual Studio den Modus des angegebenen Toolsets.  

### <a name="install-directory"></a>Installationsverzeichnis

Hierbei handelt es sich um das Verzeichnis, in dem CMake Ziele installiert. Diese Einstellung ist [CMAKE_INSTALL_PREFIX](https://cmake.org/cmake/help/latest/variable/CMAKE_INSTALL_PREFIX.html) zugeordnet.

### <a name="cmake-executable"></a>Ausführbare CMake-Datei

Hier wird der vollständige Pfad zur ausführbaren CMake-Programmdatei angegeben, einschließlich des Dateinamens und der Erweiterung. Die Verwendung einer benutzerdefinierten Version von CMake mit Visual Studio ist möglich. Geben Sie für Remotebuilds den CMake-Speicherort auf dem Remotecomputer an.

Für Konfigurationen wie Linux, die Remotebuilds verwenden, sind ferner die folgenden Einstellungen verfügbar:

### <a name="remote-cmakeliststxt-root"></a>Remoteverzeichnis der Stammdatei „CMakeLists.txt“

Hierbei handelt es sich um das Verzeichnis auf dem Remotecomputer, das die Stammdatei *CMakeLists.txt* enthält.

### <a name="remote-install-root"></a>Installationsstammverzeichnis auf dem Remotesystem

Das Verzeichnis auf dem Remotecomputer, in dem CMake Zieldateien installiert. Diese Einstellung ist [CMAKE_INSTALL_PREFIX](https://cmake.org/cmake/help/latest/variable/CMAKE_INSTALL_PREFIX.html) zugeordnet.

### <a name="remote-copy-sources"></a>Quellen auf Remotesystem kopieren

Diese Einstellung gibt an, ob Quelldateien auf den Remotecomputer kopiert werden sollen, und ermöglicht Ihnen, anzugeben, ob rsync oder sftp verwendet werden soll.

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

JSON-IntelliSense unterstützt Sie beim Bearbeiten der Datei *CMakeSettings.json*:

   ![CMake: JSON-IntelliSense](media/cmake-json-intellisense.png "CMake: JSON-IntelliSense")

Der JSON-Editor informiert Sie auch, wenn Sie inkompatible Einstellungen auswählen.

Weitere Informationen zu den einzelnen Eigenschaften in der Datei finden Sie in der [CMakeSettings.json-Schemareferenz](cmakesettings-reference.md).

::: moniker-end

::: moniker range="<=vs-2017"

Visual Studio 2017 bietet verschiedene CMake-Konfigurationen, die definieren, wie „CMake.exe“ aufgerufen wird, um den CMake-Cache für ein bestimmtes Projekt zu erstellen. Klicken Sie zum Hinzufügen einer neuen Konfiguration in der Symbolleiste auf die Konfigurations-Dropdownliste, und wählen Sie **Konfigurationen verwalten...** aus:

   ![CMake: „Konfigurationen verwalten...“](media/cmake-manage-configurations.png)

Sie können aus der Liste vordefinierter Konfigurationen wählen:

   ![Vordefinierte CMake-Konfigurationen](media/cmake-configurations.png)

Wenn Sie zum ersten Mal eine Konfiguration auswählen, erstellt Visual Studio im Stammordner des Projekts eine Datei namens *CMakeSettings.json*. Diese Datei wird verwendet, um die CMake-Cachedatei erneut zu erstellen, z.B. nach einem **Bereinigungsvorgang**.

Klicken Sie zum Hinzufügen einer zusätzlichen Konfiguration mit der rechten Maustaste auf *CMakeSettings.json*, und klicken Sie auf **Konfiguration hinzufügen**.

   ![CMake: Konfiguration hinzufügen](media/cmake-add-configuration.png "CMake: Konfiguration hinzufügen")

Sie können die Datei auch mithilfe des **Editors für CMake-Einstellungen** bearbeiten. Klicken Sie mit der rechten Maustaste im **Projektmappen-Explorer** auf *CMakeSettings.json*, und klicken Sie auf **CMake-Einstellungen bearbeiten**. Alternativ können Sie oben im Editor-Fenster aus der Konfigurations-Dropdownliste **Konfigurationen verwalten...** auswählen.

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

JSON-IntelliSense unterstützt Sie beim Bearbeiten der Datei *CMakeSettings.json*:

   ![CMake: JSON-IntelliSense](media/cmake-json-intellisense.png "CMake: JSON-IntelliSense")

Weitere Informationen zu den einzelnen Eigenschaften in der Datei finden Sie in der [CMakeSettings.json-Schemareferenz](cmakesettings-reference.md).

::: moniker-end

## <a name="see-also"></a>Siehe auch

[CMake Projects in Visual Studio (CMake-Projekte in Visual Studio)](cmake-projects-in-visual-studio.md)<br/>
[Konfigurieren eines Linux CMake-Projekts](../linux/cmake-linux-project.md)<br/>
[Herstellen einer Verbindung mit Ihrem Linux-Remotecomputer](../linux/connect-to-your-remote-linux-computer.md)<br/>
[Konfigurieren von CMake-Debugsitzungen](configure-cmake-debugging-sessions.md)<br/>
[Bereitstellen, Ausführen und Debuggen Ihres Linux-Projekts](../linux/deploy-run-and-debug-your-linux-project.md)<br/>
[CMake predefined configuration reference (Referenz für vordefinierte CMake-Konfigurationen)](cmake-predefined-configuration-reference.md)
