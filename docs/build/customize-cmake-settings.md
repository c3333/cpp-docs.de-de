---
title: Anpassen von CMake-Buildeinstellungen in Visual Studio
ms.date: 08/20/2019
helpviewer_keywords:
- CMake build settings
ms.openlocfilehash: f93997e498502e0e326edfc2b023af9808f86357
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "80078654"
---
# <a name="customize-cmake-build-settings"></a>Anpassen von CMake-Buildeinstellungen

::: moniker range="vs-2019"

In Visual Studio 2019 und höher können Sie mithilfe des **CMake-Einstellungs-Editors** Konfigurationen hinzufügen und ihre Einstellungen anpassen. Der Editor ist eine einfachere Alternative zum manuellen Bearbeiten der Datei " *cmakesettings. JSON* ". Wenn Sie die Datei jedoch lieber direkt bearbeiten möchten, können Sie auf den Link " **JSON bearbeiten** " in der oberen rechten Ecke des Editors klicken.

Um den Editor zu öffnen, klicken Sie auf die Dropdownliste **Konfiguration** in der Hauptsymbolleiste, und wählen Sie **Konfigurationen verwalten** aus.

![Dropdownliste „CMake-Konfigurationen“](media/vs2019-cmake-manage-configurations.png)

Jetzt wird der **Einstellungs-Editor** mit den installierten Konfigurationen auf der linken Seite angezeigt.

![CMake-Einstellungs-Editor](media/cmake-settings-editor.png)

Visual Studio bietet standardmäßig eine `x64-Debug` Konfiguration. Sie können zusätzliche Konfigurationen hinzufügen, indem Sie auf das grüne Pluszeichen klicken. Welche Einstellungen im Editor angezeigt werden, hängt davon ab, welche Konfiguration ausgewählt ist.

Die Optionen, die Sie im Editor auswählen, werden in eine Datei mit dem Namen *cmakesettings. JSON*geschrieben. Diese Datei stellt Befehlszeilenargumente und Umgebungsvariablen zur Verfügung, die beim Erstellen der Projekte an CMake übergeben werden. Visual Studio ändert " *CMakeLists. txt* " nie automatisch. mithilfe von *cmakesettings. JSON* können Sie den Build über Visual Studio anpassen, während die cmake-Projektdateien unverändert bleiben, sodass andere Benutzer in Ihrem Team Sie mit den Tools nutzen können, die Sie verwenden.

## <a name="cmake-general-settings"></a>CMake – allgemeine Einstellungen

Die folgenden Einstellungen sind unter der Überschrift **Allgemein** verfügbar:

### <a name="configuration-name"></a>Konfigurationsname

Entspricht der Einstellung **name**. Dieser Name wird in der C++ Dropdown Liste Konfiguration angezeigt. Sie können das `${name}`-Makro verwenden, um weitere Eigenschaftswerte wie etwa Pfade zu verfassen.

### <a name="configuration-type"></a>Konfigurationstyp

Entspricht der Einstellung **configurationType**. Definiert den Typ der Buildkonfiguration für den ausgewählten Generator. Derzeit werden die Werte "Debug", "MinSizeRel", "Release" und "RelWithDebInfo" unterstützt. Sie wird [CMAKE_BUILD_TYPE](https://cmake.org/cmake/help/latest/variable/CMAKE_BUILD_TYPE.html)zugeordnet.

### <a name="toolset"></a>Toolset

Entspricht der Einstellung **inheritedEnvironments**. Definiert die Compilerumgebung, die zum Erstellen der ausgewählten Konfiguration verwendet wird. Die unterstützten Werte hängen von der Art der Konfiguration ab. Um eine benutzerdefinierte Umgebung zu erstellen, wählen Sie den Link **JSON bearbeiten** in der oberen rechten Ecke des Einstellungs-Editors aus, und bearbeiten Sie die Datei " *cmakesettings. JSON* " direkt.

### <a name="cmake-toolchain-file"></a>CMake-Toolkettendatei

Der Pfad zur [cmake-Toolkette-Datei](https://cmake.org/cmake/help/latest/variable/CMAKE_TOOLCHAIN_FILE.html). Dieser Pfad wird als "-DCMAKE_TOOLCHAIN_FILE = \<filePath >" an cmake übergeben. Toolkette-Dateien geben Speicherorte von Compilern und Toolkette-Hilfsprogrammen sowie andere Informationen zu Zielplattform und Compilerinformationen an. Standardmäßig verwendet Visual Studio die [vcpkg-Toolkette-Datei](https://github.com/microsoft/vcpkg/blob/master/docs/examples/installing-and-using-packages.md#cmake) , wenn diese Einstellung nicht angegeben ist.

### <a name="build-root"></a>Buildstamm

Entspricht **buildRoot**. Wird [CMAKE_BINARY_DIR](https://cmake.org/cmake/help/v3.15/variable/CMAKE_BINARY_DIR.html)zugeordnet und gibt an, wo der cmake-Cache erstellt wird. Der angegebene Ordner wird erstellt, wenn er nicht vorhanden ist.

## <a name="command-arguments"></a>Befehlsargumente

Die folgenden Einstellungen sind unter der Überschrift **Befehlsargumente** verfügbar:

### <a name="cmake-command-arguments"></a>CMake-Befehlsargumente

Entspricht **cmakeCommandArgs**. Gibt alle zusätzlichen [Befehlszeilenoptionen](https://cmake.org/cmake/help/latest/manual/cmake.1.html) an, die an cmake. exe übergeben werden.

### <a name="build-command-arguments"></a>Build-Befehlsargumente

Entspricht **buildcommandargs**. Gibt zusätzliche Switches an, die an das zugrunde liegende Buildsystem übergeben werden. Wenn Sie z. b. `-v` bei Verwendung des Ninja-Generators übergeben, wird die Ausgabe von Befehlszeilen durch Ninja erzwungen

### <a name="ctest-command-arguments"></a>CTest-Befehlsargumente

Entspricht **ctestcommandargs**. Gibt zusätzliche [Befehlszeilenoptionen](https://cmake.org/cmake/help/v3.15/manual/ctest.1.html) an, die beim Ausführen von Tests an CTest übergeben werden.

## <a name="general-settings-for-remote-builds"></a>Allgemeine Einstellungen für Remotebuilds

Für Konfigurationen wie Linux, die Remotebuilds verwenden, sind ferner die folgenden Einstellungen verfügbar:

### <a name="rsync-command-arguments"></a>rsync-Befehlsargumente

Zusätzliche Befehlszeilenoptionen, die an [rsync](https://download.samba.org/pub/rsync/rsync.html)übermittelt werden, ein schnelles und vielseitiges Tool zum Kopieren von Dateien.

## <a name="cmake-variables-and-cache"></a>CMake-Variablen und -Cache

Diese Einstellungen ermöglichen es Ihnen, cmake-Variablen festzulegen und in " *cmakesettings. JSON*" zu speichern. Sie werden zur Buildzeit an cmake übergeben und überschreiben alle Werte in der Datei " *CMakeLists. txt* ". Sie können diesen Abschnitt in der gleichen Weise verwenden, in der Sie das CMakeGUI verwenden, um eine Liste aller für die Bearbeitung verfügbaren CMake-Variablen anzuzeigen. Klicken Sie auf die Schaltfläche **Speichern und Cache generieren**, um eine Liste aller für die Bearbeitung verfügbaren CMake-Variablen anzuzeigen, einschließlich erweiterter Variablen (mithilfe des CMakeGUI). Sie können die Liste nach Variablennamen filtern.

Entspricht **Variablen**. Enthält ein Name-Wert-Paar aus cmake-Variablen, die als **-D-** *_Name_=_Wert_* an cmake übergeben werden. Wenn Ihre cmake-projektbuildanweisungen das Hinzufügen von Variablen direkt zur cmake-Cachedatei angeben, empfiehlt es sich, Sie hier hinzuzufügen.

## <a name="advanced-settings"></a>Erweiterte Einstellungen

### <a name="cmake-generator"></a>CMake-Generator

Entspricht **Generator**. Wird dem Schalter cmake **-G** zugeordnet und gibt den zu verwendenden [cmake-Generator](https://cmake.org/cmake/help/latest/manual/cmake-generators.7.html) an. Diese Eigenschaft kann ebenfalls als Makro (`${generator}`) beim Erstellen anderer Eigenschaftswerte verwendet werden. Visual Studio unterstützt derzeit folgende CMake-Generatoren:

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
  
Da Ninja für schnelles Erstellen von Builds anstelle von Flexibilität und Funktion konzipiert ist, wird es als Standard festgelegt. Einige CMake-Projekte können jedoch mit Ninja keinen ordnungsgemäßen Build durchführen. Wenn dies der Fall ist, können Sie cmake anweisen, stattdessen ein Visual Studio-Projekt zu generieren.

### <a name="intellisense-mode"></a>IntelliSense-Modus

Der IntelliSense-Modus, der von der IntelliSense-Engine verwendet wird. Wenn kein Modus ausgewählt ist, erbt Visual Studio vom angegebenen Toolset.  

### <a name="install-directory"></a>Installationsverzeichnis

Das Verzeichnis, in dem cmake Ziele installiert. Wird [CMAKE_INSTALL_PREFIX](https://cmake.org/cmake/help/latest/variable/CMAKE_INSTALL_PREFIX.html)zugeordnet.

### <a name="cmake-executable"></a>Ausführbare CMake-Datei

Der vollständige Pfad zur ausführbaren cmake-Programmdatei, einschließlich des Datei namens und der Erweiterung. Sie können eine benutzerdefinierte Version von cmake mit Visual Studio verwenden. Geben Sie für Remotebuilds den CMake-Speicherort auf dem Remotecomputer an.

Für Konfigurationen wie Linux, die Remotebuilds verwenden, sind ferner die folgenden Einstellungen verfügbar:

### <a name="remote-cmakeliststxt-root"></a>Remoteverzeichnis der Stammdatei „CMakeLists.txt“

Das Verzeichnis auf dem Remote Computer, das die Stammdatei " *CMakeLists. txt* " enthält.

### <a name="remote-install-root"></a>Installationsstammverzeichnis auf dem Remotesystem

Das Verzeichnis auf dem Remotecomputer, in dem CMake Zieldateien installiert. Wird [CMAKE_INSTALL_PREFIX](https://cmake.org/cmake/help/latest/variable/CMAKE_INSTALL_PREFIX.html)zugeordnet.

### <a name="remote-copy-sources"></a>Quellen auf Remotesystem kopieren

Gibt an, ob Quelldateien auf den Remote Computer kopiert werden sollen, und ermöglicht Ihnen, anzugeben, ob Sie rsync oder SFTP verwenden möchten.

## <a name="directly-edit-cmakesettingsjson"></a>„CMakeSettings.json“ direkt bearbeiten

Sie können *cmakesettings. JSON* auch direkt bearbeiten, um benutzerdefinierte Konfigurationen zu erstellen. Der **Einstellungs-Editor** weist eine Schaltfläche **JSON bearbeiten** oben rechts auf, mit der die Datei zur Bearbeitung geöffnet wird.

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

Mit JSON IntelliSense können Sie die Datei " *cmakesettings. JSON* " bearbeiten:

   ![Cmake-JSON-IntelliSense](media/cmake-json-intellisense.png "Cmake-JSON-IntelliSense")

Der JSON-Editor informiert Sie auch, wenn Sie nicht kompatible Einstellungen auswählen.

Weitere Informationen zu den einzelnen Eigenschaften in der Datei finden Sie in der [CMakeSettings.json-Schemareferenz](cmakesettings-reference.md).

::: moniker-end

::: moniker range="<=vs-2017"

Visual Studio 2017 bietet verschiedene CMake-Konfigurationen, die definieren, wie „CMake.exe“ aufgerufen wird, um den CMake-Cache für ein bestimmtes Projekt zu erstellen. Klicken Sie zum Hinzufügen einer neuen Konfiguration in der Symbolleiste auf die Konfigurations-Dropdownliste, und wählen Sie **Konfigurationen verwalten...** aus:

   ![CMake: „Konfigurationen verwalten...“](media/cmake-manage-configurations.png)

Sie können aus der Liste vordefinierter Konfigurationen wählen:

   ![Vordefinierte CMake-Konfigurationen](media/cmake-configurations.png)

Wenn Sie zum ersten Mal eine Konfiguration auswählen, erstellt Visual Studio eine *cmakesettings. JSON* -Datei im Stamm Ordner Ihres Projekts. Diese Datei wird verwendet, um die CMake-Cachedatei erneut zu erstellen, z.B. nach einem **Bereinigungsvorgang**.

Klicken Sie zum Hinzufügen einer zusätzlichen Konfiguration mit der rechten Maustaste auf *cmakesettings. JSON* , und wählen Sie **Konfiguration hinzufügen**.

   ![Cmake-Konfiguration hinzufügen](media/cmake-add-configuration.png "Cmake-Konfiguration hinzufügen")

Sie können die Datei auch mithilfe des **Editors für CMake-Einstellungen** bearbeiten. Klicken Sie in **Projektmappen-Explorer** mit der rechten Maustaste auf *cmakesettings. JSON* , und wählen Sie **cmake-Einstellungen bearbeiten**aus. Alternativ können Sie oben im Editor-Fenster aus der Konfigurations-Dropdownliste **Konfigurationen verwalten...** auswählen.

Sie können *cmakesettings. JSON* auch direkt bearbeiten, um benutzerdefinierte Konfigurationen zu erstellen. Das folgende Beispiel zeigt eine Beispielkonfiguration, die Sie als Ausgangspunkt verwenden können:

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

Mit JSON IntelliSense können Sie die Datei " *cmakesettings. JSON* " bearbeiten:

   ![Cmake-JSON-IntelliSense](media/cmake-json-intellisense.png "Cmake-JSON-IntelliSense")

Weitere Informationen zu den einzelnen Eigenschaften in der Datei finden Sie in der [CMakeSettings.json-Schemareferenz](cmakesettings-reference.md).

::: moniker-end

## <a name="see-also"></a>Weitere Informationen

[CMake Projects in Visual Studio (CMake-Projekte in Visual Studio)](cmake-projects-in-visual-studio.md)<br/>
[Konfigurieren eines Linux CMake-Projekts](../linux/cmake-linux-project.md)<br/>
[Herstellen einer Verbindung mit Ihrem Linux-Remotecomputer](../linux/connect-to-your-remote-linux-computer.md)<br/>
[Konfigurieren von CMake-Debugsitzungen](configure-cmake-debugging-sessions.md)<br/>
[Bereitstellen, Ausführen und Debuggen Ihres Linux-Projekts](../linux/deploy-run-and-debug-your-linux-project.md)<br/>
[CMake predefined configuration reference (Referenz für vordefinierte CMake-Konfigurationen)](cmake-predefined-configuration-reference.md)
