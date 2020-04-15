---
title: Konfigurieren von CMake-Debugsitzungen in Visual Studio
description: Beschreibt die Verwendung von Visual Studio zum Konfigurieren von CMake-Debuggereinstellungen.
ms.date: 04/02/2020
helpviewer_keywords:
- CMake debugging
ms.openlocfilehash: 8364e5b3dd3316a4ed7e754a104a14373040aa6e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328855"
---
# <a name="configure-cmake-debugging-sessions"></a>Konfigurieren von CMake-Debugsitzungen

::: moniker range="vs-2015"

Native CMake-Unterstützung ist in Visual Studio 2017 und höher verfügbar. Um die Dokumentation zu diesen Versionen anzuzeigen, legen Sie das Visual **Studio-Versionsauswahlsteuerelement** für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich oben im Inhaltsverzeichnis auf dieser Seite.

::: moniker-end

::: moniker range=">=vs-2017"

Alle ausführbaren CMake-Ziele werden in der Dropdownliste **Startelement** auf der Symbolleiste **Allgemein** angezeigt. Wählen Sie eine aus, um eine Debugsitzung zu starten und den Debugger zu starten.

![CMake-Startelement-Dropdown](media/cmake-startup-item-dropdown.png "CMake-Startelement-Dropdown")

Sie können eine Debugsitzung auch im Projektmappen-Explorer starten. Wechseln Sie zunächst im **Projektmappen-Explorer** zur **CMake Targets View.**

![Schaltfläche für CMake-Zielansicht](media/cmake-targets-view.png  "CMake Targets Menüelement anzeigen")

Klicken Sie dann mit der rechten Maustaste auf eine ausführbare Datei und wählen Sie **Debug**aus. Dieser Befehl beginnt automatisch mit dem Debuggen des ausgewählten Ziels basierend auf Ihrer aktiven Konfiguration.

## <a name="customize-debugger-settings"></a>Anpassen von Debuggereinstellungen

Sie können die Debuggereinstellungen für jedes ausführbare CMake-Ziel in Ihrem Projekt anpassen. Sie befinden sich in einer Konfigurationsdatei namens *launch.vs.json*, die sich in einem *`.vs`* Ordner in Ihrem Projektstamm befindet. Eine Startkonfigurationsdatei ist in den meisten Debugszenarios nützlich, da Sie Ihre Debuginstallationsdetails konfigurieren und speichern können. Es gibt drei Einstiegspunkte für diese Datei:

- **Debugmenü:** Wählen Sie im Hauptmenü die Option **Debug-> Debug- und Starteinstellungen für "activeDebugTarget"** aus, um die Debugkonfiguration für Ihr aktives Debugziel anzupassen. Wenn Sie kein Debugziel ausgewählt haben, ist diese Option abgeblendet.

![Debugmenü-Einstiegspunkt](media/cmake-debug-menu.png "Debugmenü-Einstiegspunkt")

- **Ziele Ansicht:** Navigieren Sie im Projektmappen-Explorer zur **Zielansicht.** Klicken Sie dann mit der rechten Maustaste auf ein Debugziel, und wählen Sie **Debugkonfiguration hinzufügen** aus, um die Debugkonfiguration für das ausgewählte Ziel anzupassen.

![Ziele AnsichtSeinstiegspunkt](media/cmake-targets-add-debug-configuration.png "Ziele AnsichtSeinstiegspunkt")

- **Stamm CMakeLists.txt:** Klicken Sie mit der rechten Maustaste auf eine Stammdatei *CMakeLists.txt,* und wählen Sie **Debugkonfiguration hinzufügen** aus, um das Dialogfeld **Debugger auswählen** zu öffnen. Im Dialogfeld können Sie *jede* Art von Debugkonfiguration hinzufügen, aber Sie müssen `projectTarget` das CMake-Ziel manuell angeben, das über die Eigenschaft aufgerufen werden soll.

![Auswählen eines Debugger-Dialogfelds](media/cmake-select-a-debugger.png "Auswählen eines Debugger-Dialogfelds")

Sie können die *Datei launch.vs.json* bearbeiten, um Debugkonfigurationen für eine beliebige Anzahl von CMake-Zielen zu erstellen. Wenn Sie die Datei speichern, erstellt Visual Studio einen Eintrag für jede neue Konfiguration in der Dropdownliste **Startelement.**

## <a name="reference-keys-in-cmakesettingsjson"></a>Referenzschlüssel in CMakeSettings.json

Um auf einen beliebigen Schlüssel in einer *CMakeSettings.json-Datei* zu verweisen, stellen Sie `cmake.` ihm im *launch.vs.json*vor. Das folgende Beispiel zeigt eine einfache *launch.vs.json-Datei,* die den Wert des `remoteCopySources` Schlüssels in der Datei *CMakeSettings.json* für die aktuell ausgewählte Konfiguration abruft:

```json
{
  "version": "0.2.1",
  "defaults": {},
  "configurations": [
    {
      "type": "default",
      "project": "CMakeLists.txt",
      "projectTarget": "CMakeHelloWorld.exe (Debug\\CMakeHelloWorld.exe)",
      "name": "CMakeHelloWorld.exe (Debug\\CMakeHelloWorld.exe)",
      "args": ["${cmake.remoteCopySources}"]
    }
  ]
}
```

**Umgebungsvariablen,** die in *CMakeSettings.json* definiert sind, können auch `${env.VARIABLE_NAME}`in launch.vs.json mit der Syntax verwendet werden. In Visual Studio 2019 Version 16.4 und höher werden Debugziele automatisch mithilfe der Umgebung gestartet, die Sie in *CMakeSettings.json*angeben. Sie können die Einstellung einer Umgebungsvariablen aufheben, indem Sie sie auf **null**setzen.

## <a name="launchvsjson-reference"></a>Launch.vs.json-Referenz

Es gibt viele *launch.vs.json-Eigenschaften,* die alle Debugszenarios unterstützen. Die folgenden Eigenschaften sind allen Debugkonfigurationen gemeinsam, sowohl remote als auch lokal:

- `projectTarget`: Gibt das CMake-Ziel an, das beim Erstellen des Projekts aufgerufen werden soll. Visual Studio füllt diese Eigenschaft automatisch aus, wenn Sie *launch.vs.json* über das **Debugmenü** oder die **Zielansicht**eingeben. Dieser Wert muss mit dem Namen eines vorhandenen Debugziels übereinstimmen, das in der Dropdownliste **Startelement** aufgeführt ist.

- `env`: Zusätzliche Umgebungsvariablen, die mit der Syntax hinzugefügt werden sollen:

  ```json
  "env": {
        "DEBUG_LOGGING_LEVEL": "trace;info",
        "ENABLE_TRACING": "true"
      }
  ```

- `args`: Befehlszeilenargumente, die an das zu debuggende Programm übergeben werden.

## <a name="launchvsjson-reference-for-remote-projects-and-wsl"></a>Launch.vs.json-Referenz für Remoteprojekte und WSL

In Visual Studio 2019 Version 16.6 haben `type: cppgdb` wir eine neue Debugkonfiguration hinzugefügt, um das Debuggen auf Remotesystemen und WSL zu vereinfachen. Alte Debugkonfigurationen `type: cppdbg` von werden weiterhin unterstützt.

### <a name="configuration-type-cppgdb"></a>Konfigurationstyp`cppgdb`

- `name`: Ein Anzeigename, um die Konfiguration in der Dropdownliste **Startelement** zu identifizieren.
- `project`: Gibt den relativen Pfad zur Projektdatei an. Normalerweise müssen Sie diesen Pfad beim Debuggen eines CMake-Projekts nicht ändern.
- `projectTarget`: Gibt das CMake-Ziel an, das beim Erstellen des Projekts aufgerufen werden soll. Visual Studio füllt diese Eigenschaft automatisch aus, wenn Sie *launch.vs.json* über das **Debugmenü** oder die **Zielansicht**eingeben. Dieser Zielwert muss mit dem Namen eines vorhandenen Debugziels übereinstimmen, das in der Dropdownliste **Startelement** aufgeführt ist.
- `debuggerConfiguration`: Gibt an, welche Gruppe von Debugging-Standardwerten verwendet werden soll. In Visual Studio 2019 Version 16.6 `gdb`ist die einzige gültige Option . Frühere Versionen `gdbserver`unterstützen ebenfalls .
- `args`: Befehlszeilenargumente, die beim Start an das zu debuggende Programm übergeben werden.
- `env`: Zusätzliche Umgebungsvariablen, die an das zu debuggende Programm übergeben werden. Beispiel: `{"DISPLAY": "0.0"}`.
- `processID`: Linux-Prozess-ID, an die angefügt werden soll. Wird nur verwendet, wenn an einen Remoteprozess angefügt wird. Weitere Informationen finden Sie unter [Fehlerbehebung sanfügen an Prozesse mit GDB](https://github.com/Microsoft/MIEngine/wiki/Troubleshoot-attaching-to-processes-using-GDB).

#### <a name="additional-options-for-the-gdb-configuration"></a>Zusätzliche Optionen `gdb` für die Konfiguration

- `program`: Standardwerte `"${debugInfo.fullTargetPath}"`auf . Der Unix-Pfad zur zu debuggenden Anwendung. Nur erforderlich, wenn es sich von der ausführbaren Zieldatei am Build- oder Bereitstellungsspeicherort unterscheidet.
- `remoteMachineName`: Standardwerte `"${debugInfo.remoteMachineName}"`auf . Name des Remotesystems, auf dem das zu debugende Programm gehostet wird. Nur erforderlich, wenn es sich vom Buildsystem unterscheidet. Muss über einen vorhandenen Eintrag im [Verbindungs-Manager](../linux/connect-to-your-remote-linux-computer.md)verfügen. Drücken Sie **Strg+Leertaste,** um eine Liste aller vorhandenen Remoteverbindungen anzuzeigen.
- `cwd`: Standardwerte `"${debugInfo.defaultWorkingDirectory}"`auf . Der Unix-Pfad zum Verzeichnis auf `program` dem Remotesystem, auf dem ausgeführt wird. Das Verzeichnis muss vorhanden sein.
- `gdbpath`: Standardwerte `/usr/bin/gdb`auf . Vollständiger Unix-Pfad zum `gdb` Debuggen. Nur erforderlich, wenn eine `gdb`benutzerdefinierte Version von verwendet wird.
- `preDebugCommand`: Ein Linux-Befehl, der `gdb`unmittelbar vor dem Aufrufen ausgeführt werden soll. `gdb`wird erst gestartet, wenn der Befehl abgeschlossen ist. Sie können die Option zum Ausführen eines `gdb`Skripts vor der Ausführung von verwenden.

#### <a name="deployment-options"></a>Bereitstellungsoptionen

Verwenden Sie die folgenden Optionen, um ihren Buildcomputer (definiert in CMakeSettings.json) von Ihrem Remote-Debugcomputer zu trennen.

- `remoteMachineName`: Remote-Debug-Computer. Nur erforderlich, wenn es sich von der Buildmaschine unterscheidet. Muss über einen vorhandenen Eintrag im [Verbindungs-Manager](../linux/connect-to-your-remote-linux-computer.md)verfügen. Drücken Sie **Strg+Leertaste,** um eine Liste aller vorhandenen Remoteverbindungen anzuzeigen.
- `disableDeploy`: Standardwerte `false`auf . Gibt an, ob die Build-/Debug-Trennung deaktiviert ist. Wenn `false`diese Option das Erstellen und Debuggen auf zwei separaten Computern ermöglicht.
- `deployDirectory`: Vollständiger Unix-Pfad `remoteMachineName` zum Verzeichnis, in das die ausführbare Datei kopiert wird.
- `deploy`: Eine Reihe erweiterter Bereitstellungseinstellungen. Sie müssen diese Einstellungen nur konfigurieren, wenn Sie detailliertere Kontrolle über den Bereitstellungsprozess benötigen. Standardmäßig werden nur die Dateien bereitgestellt, die für den Prozess zum Debuggen erforderlich sind, auf dem Remotedebugcomputer bereitgestellt werden.
  - `sourceMachine`: Der Computer, von dem die Datei oder das Verzeichnis kopiert wird. Drücken Sie **Strg+Leertaste,** um eine Liste aller im Verbindungs-Manager gespeicherten Remoteverbindungen anzuzeigen. Beim erstellen nativ auf WSL wird diese Option ignoriert.
  - `targetMachine`: Der Computer, auf den die Datei oder das Verzeichnis kopiert wird. Drücken Sie **Strg+Leertaste,** um eine Liste aller im Verbindungs-Manager gespeicherten Remoteverbindungen anzuzeigen.
  - `sourcePath`: Die Datei oder `sourceMachine`der Verzeichnisspeicherort auf .
  - `targetPath`: Die Datei oder `targetMachine`der Verzeichnisspeicherort auf .
  - `deploymentType`: Eine Beschreibung des Bereitstellungstyps. `LocalRemote`und `RemoteRemote` werden unterstützt. `LocalRemote`bedeutet Das Kopieren aus dem lokalen Dateisystem auf das Remotesystem, das in `remoteMachineName` *launch.vs.json*angegeben ist. `RemoteRemote`bedeutet Das Kopieren von dem in *CMakeSettings.json* angegebenen Remotebuildsystem auf das andere Remotesystem, das in *launch.vs.json*angegeben ist.
  - `executable`: Gibt an, ob es sich bei der bereitgestellten Datei um eine ausführbare Datei handelt.

### <a name="execute-custom-gdb-commands"></a>Ausführen `gdb` benutzerdefinierter Befehle

Visual Studio unterstützt `gdb` das Ausführen benutzerdefinierter Befehle, um direkt mit dem zugrunde liegenden Debugger zu interagieren. Weitere Informationen finden Sie unter [Ausführen benutzerdefinierter `gdb` lldb-Befehle](https://github.com/microsoft/MIEngine/wiki/Executing-custom-gdb-lldb-commands).

### <a name="enable-logging"></a>Aktivieren der Protokollierung

Aktivieren Sie die MIEngine-Protokollierung, um zu sehen, welche Befehle an `gdb`gesendet werden, welche Ausgabe `gdb` zurückgegeben wird und wie lange jeder Befehl dauert. [Weitere Informationen](https://github.com/microsoft/MIEngine/wiki/Logging)

### <a name="configuration-type-cppdbg"></a>Konfigurationstyp`cppdbg`

Die folgenden Optionen können beim Debuggen auf einem Remotesystem oder WSL mithilfe des Konfigurationstyps `cppdbg` verwendet werden. In Visual Studio 2019 Version 16.6 `cppgdb` oder höher wird der Konfigurationstyp empfohlen.

- `name`: Ein Anzeigename, um die Konfiguration in der Dropdownliste **Startelement** zu identifizieren.

- `project`: Gibt den relativen Pfad zur Projektdatei an. Normalerweise müssen Sie diesen Wert beim Debuggen eines CMake-Projekts nicht ändern.

- `projectTarget`: Gibt das CMake-Ziel an, das beim Erstellen des Projekts aufgerufen werden soll. Visual Studio füllt diese Eigenschaft automatisch aus, wenn Sie *launch.vs.json* über das **Debugmenü** oder die **Zielansicht**eingeben. Dieser Wert muss mit dem Namen eines vorhandenen Debugziels übereinstimmen, das in der Dropdownliste **Startelement** aufgeführt ist.

- `args`: Befehlszeilenargumente, die beim Start an das zu debuggende Programm übergeben werden.

- `processID`: Linux-Prozess-ID, an die angefügt werden soll. Wird nur verwendet, wenn an einen Remoteprozess angefügt wird. Weitere Informationen finden Sie unter [Fehlerbehebung sanfügen an Prozesse mit GDB](https://github.com/Microsoft/MIEngine/wiki/Troubleshoot-attaching-to-processes-using-GDB).

- `program`: Standardwerte `"${debugInfo.fullTargetPath}"`auf . Der Unix-Pfad zur zu debuggenden Anwendung. Nur erforderlich, wenn es sich von der ausführbaren Zieldatei am Build- oder Bereitstellungsspeicherort unterscheidet.

- `remoteMachineName`: Standardwerte `"${debugInfo.remoteMachineName}"`auf . Name des Remotesystems, auf dem das zu debugende Programm gehostet wird. Nur erforderlich, wenn es sich vom Buildsystem unterscheidet. Muss über einen vorhandenen Eintrag im [Verbindungs-Manager](../linux/connect-to-your-remote-linux-computer.md)verfügen. Drücken Sie **Strg+Leertaste,** um eine Liste aller vorhandenen Remoteverbindungen anzuzeigen.

- `cwd`: Standardwerte `"${debugInfo.defaultWorkingDirectory}"`auf . Vollständiger Unix-Pfad zum Verzeichnis `program` auf dem Remotesystem, auf dem ausgeführt wird. Das Verzeichnis muss vorhanden sein.

- `environment`: Zusätzliche Umgebungsvariablen, die an das zu debuggende Programm übergeben werden. Beispiel:

  ```json
    "environment": [
        {
          "name": "ENV1",
          "value": "envvalue1"
        },
        {
          "name": "ENV2",
          "value": "envvalue2"
        }
      ]
  ```

- `pipeArgs`: Ein Array von Befehlszeilenargumenten, die an das Pipe-Programm übergeben werden, um die Verbindung zu konfigurieren. Das Rohrprogramm wird verwendet, um Standardein-/Ausgabe zwischen Visual Studio und `gdb`weiterzuleiten. Der größte Teil dieses Arrays muss beim Debuggen von CMake-Projekten **nicht angepasst werden.** Die Ausnahme `${debuggerCommand}`ist die `gdb` , die auf dem Remotesystem gestartet wird. Es kann geändert werden, um:

  - Exportieren Sie den Wert der Umgebungsvariablen DISPLAY auf Ihrem Linux-System. Im folgenden Beispiel ist `:1`dieser Wert .

    ```json
    "pipeArgs": [
        "/s",
        "${debugInfo.remoteMachineId}",
        "/p",
        "${debugInfo.parentProcessId}",
        "/c",
        "export DISPLAY=:1;${debuggerCommand}",
        "--tty=${debugInfo.tty}"
      ],
    ```

  - Führen Sie ein Skript `gdb`vor der Ausführung von aus. Stellen Sie sicher, dass Ausführungsberechtigungen für Ihr Skript festgelegt sind.

    ```json
    "pipeArgs": [
        "/s",
        "${debugInfo.remoteMachineId}",
        "/p",
        "${debugInfo.parentProcessId}",
        "/c",
        "/path/to/script.sh;${debuggerCommand}",
        "--tty=${debugInfo.tty}"
      ],
    ```

- `stopOnEntry`: Ein boolescher Wert, der angibt, ob die Datei nach dem Start des Prozesses zu unterbrechen ist. Die Standardeinstellung ist „false“.

- `visualizerFile`: Eine [.natvis-Datei,](/visualstudio/debugger/create-custom-views-of-native-objects) die beim Debuggen dieses Prozesses verwendet werden soll. Diese Option ist `gdb` mit dem hübschen Drucken nicht kompatibel. Legen `showDisplayString` Sie auch fest, wenn Sie diese Eigenschaft festlegen.

- `showDisplayString`: Ein boolescher Wert, `visualizerFile` der die Anzeigezeichenfolge aktiviert, wenn eine angegeben wird. Wenn Sie `true` diese Option so einstellen, kann dies zu einer langsameren Leistung beim Debuggen führen.

- `setupCommands`: Ein `gdb` oder mehrere auszuführende Befehle, um den zugrunde liegenden Debugger einzurichten.

- `miDebuggerPath`: Der vollständige `gdb`Pfad zu . Wenn nicht angegeben, durchsucht Visual Studio PATH zuerst nach dem Debugger.

- Schließlich können alle für den `cppgdb` Konfigurationstyp definierten Bereitstellungsoptionen auch vom `cppdbg` Konfigurationstyp verwendet werden.

### <a name="debug-using-gdbserver"></a>Debuggen mit`gdbserver`

Sie können `cppdbg` die Konfiguration `gdbserver`so konfigurieren, dass sie mit debugg. Weitere Details und eine Beispielstartkonfiguration finden Sie im Microsoft C++ Team Blog-Beitrag [Debugging Linux `gdbserver`CMake Projects with ](https://devblogs.microsoft.com/cppblog/debugging-linux-cmake-projects-with-gdbserver/).

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="see-also"></a>Siehe auch

[CMake-Projekte in Visual Studio](cmake-projects-in-visual-studio.md)\
[Konfigurieren eines Linux CMake-Projekts](../linux/cmake-linux-project.md)\
[Verbinden Sie sich mit Ihrem Remote-Linux-Computer](../linux/connect-to-your-remote-linux-computer.md)\
[Anpassen der CMake-Buildeinstellungen](customize-cmake-settings.md)\
[Konfigurieren von CMake-Debuggingsitzungen](configure-cmake-debugging-sessions.md)\
[Bereitstellen, Ausführen und Debuggen Ihres Linux-Projekts](../linux/deploy-run-and-debug-your-linux-project.md)\
[CMake predefined configuration reference (Referenz für vordefinierte CMake-Konfigurationen)](cmake-predefined-configuration-reference.md)

::: moniker-end
