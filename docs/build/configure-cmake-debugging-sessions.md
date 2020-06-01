---
title: Konfigurieren von CMake-Debugsitzungen in Visual Studio
description: Hier wird die Verwendung von Visual Studio zum Konfigurieren der CMake-Debuggereinstellungen beschrieben.
ms.date: 04/02/2020
helpviewer_keywords:
- CMake debugging
ms.openlocfilehash: f860d1ae78d401a9e5079e79684a053220deaa6c
ms.sourcegitcommit: 3f91111c0350c0237fddb82766c290307f20e659
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83630521"
---
# <a name="configure-cmake-debugging-sessions"></a>Konfigurieren von CMake-Debugsitzungen

::: moniker range="vs-2015"

Die native Unterstützung für CMake ist in Visual Studio 2017 und höher verfügbar. Legen Sie das Auswahlsteuerelement für die Visual Studio-**Version** für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest, um die Dokumentationen für diese Versionen anzuzeigen. Es befindet sich am Anfang des Inhaltsverzeichnisses auf dieser Seite.

::: moniker-end

::: moniker range=">=vs-2017"

Alle ausführbaren CMake-Ziele werden in der Dropdownliste **Startelement** auf der Symbolleiste **Allgemein** angezeigt. Wählen Sie eine Version aus, um eine Debugsitzung und somit den Debugger zu starten.

![Dropdownmenü für CMake-Startelement](media/cmake-startup-item-dropdown.png "Dropdownmenü für CMake-Startelement")

Sie können eine Debugsitzung auch über den Projektmappen-Explorer starten. Wechseln Sie zunächst zur Ansicht **CMake-Zielansicht** im Fenster **Projektmappen-Explorer**.

![Schaltfläche für CMake-Zielansicht](media/cmake-targets-view.png  "CMake-Menüelement „Targets View“ (Zielansicht)")

Klicken Sie dann mit der rechten Maustaste auf eine ausführbare Datei und dann auf **Debuggen**. Mit diesem Befehl wird das Debuggen des ausgewählten Ziels basierend auf der aktiven Konfiguration automatisch gestartet.

## <a name="customize-debugger-settings"></a>Anpassen von Debuggereinstellungen

Sie können die Debuggereinstellungen für alle ausführbaren CMake-Ziele im Projekt anpassen. Sie befinden sich in einer Konfigurationsdatei namens *launch.vs.json*, die sich in einem *`.vs`* -Ordner im Projektstamm befindet. Eine Startkonfigurationsdatei ist in den meisten Debugszenarios nützlich, da Sie die Details zum Debuggen konfigurieren und speichern können. Es gibt drei Einstiegspunkte für diese Datei:

- **Menü „Debuggen“:** Klicken Sie im Hauptmenü auf **Debuggen > Debug- und Starteinstellungen für ${activeDebugTarget}** , um die für das Debugziel spezifische Debugkonfiguration anzupassen. Wenn Sie kein Debugziel ausgewählt haben, ist diese Option ausgegraut.

![Einstiegspunkt über Menü „Debuggen“](media/cmake-debug-menu.png "Einstiegspunkt über Menü „Debuggen“")

- **Targets View** (Zielansicht): Navigieren Sie im Projektmappen-Explorer zu **Targets View** (Zielansicht). Klicken Sie dann mit der rechten Maustaste auf ein Debugziel und dann auf **Add Debug Configuration** (Debugkonfiguration hinzufügen), um die für das Debugziel spezifische Debugkonfiguration anzupassen.

![Einstiegspunkt „Targets View“ (Zielansicht)](media/cmake-targets-add-debug-configuration.png "Einstiegspunkt „Targets View“ (Zielansicht)")

- **Root CMakeLists.txt:** Klicken Sie mit der rechten Maustaste auf den Stamm *CMakeLists.txt* und dann auf **Add Debug Configuration** (Debugkonfiguration hinzufügen), um das Dialogfeld **Debugger auswählen** zu öffnen. Mit dem Dialogfeld können Sie *jeden beliebigen* Typ der Debugkonfiguration hinzufügen. Sie müssen das CMake-Ziel jedoch manuell angeben, um dieses über die `projectTarget`-Eigenschaft aufzurufen.

![Dialogfeld „Debugger auswählen“](media/cmake-select-a-debugger.png "Dialogfeld „Debugger auswählen“")

Sie können die *launch.vs.json*-Datei bearbeiten, um Debugkonfigurationen für eine beliebige Anzahl von CMake-Zielen zu erstellen. Wenn Sie die Datei speichern, erstellt Visual Studio im Dropdownmenü **Startelement** einen Eintrag für jede neue Konfiguration.

## <a name="reference-keys-in-cmakesettingsjson"></a>Verweisschlüssel in CMakeSettings.json

Stellen Sie in der *launch.vs.json*-Datei `cmake.` voran, um in einer *CMakeSettings.json*-Datei auf einen beliebigen Schlüssel zu verweisen. In folgendem Beispiel wird eine einfache *launch.vs.json*-Datei dargestellt, die den Wert des Schlüssels `remoteCopySources` aus der Datei *CMakeSettings.json* für die derzeit ausgewählte Konfiguration abruft:

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

Die in der *CMakeSettings.json*-Datei definierten **Umgebungsvariablen** können mithilfe der Syntax `${env.VARIABLE_NAME}` auch in „launch.vs.json“ verwendet werden. In Visual Studio 2019, Version 16.4 und höher werden Debugziele mithilfe der in der *CMakeSettings.json*-Datei angegebenen Umgebung automatisch gestartet. Sie können eine Umgebungsvariable zurücksetzen, indem Sie sie auf **Null** festlegen.

## <a name="launchvsjson-reference"></a>Launch.vs.json-Verweis

Es gibt viele *launch.vs.json*-Eigenschaften, die alle Debugszenarios unterstützen. Die folgenden Eigenschaften gelten sowohl für alle lokalen als auch für Remotedebugkonfigurationen:

- `projectTarget`: Hiermit wird das CMake-Ziel angegeben, das beim Erstellen des Projekts abgerufen werden soll. Visual Studio füllt diese Eigenschaft automatisch auf, wenn Sie *launch.vs.json* im **Menü „Debuggen“** oder in der **Targets View** (Zielansicht) eingeben. Dieser Wert muss mit dem Namen eines vorhandenen Debugziels übereinstimmen, das im Dropdownmenü **Startelement** aufgeführt wird.

- `env`: Dies sind zusätzliche Umgebungsvariablen, die mithilfe der Syntax hinzugefügt werden sollen:

  ```json
  "env": {
        "DEBUG_LOGGING_LEVEL": "trace;info",
        "ENABLE_TRACING": "true"
      }
  ```

- `args`: Dies sind Befehlszeilenargumente, die zum Debuggen an das Programm übergeben werden.

## <a name="launchvsjson-reference-for-remote-projects-and-wsl"></a>Launch.vs.json-Verweis für Remoteprojekte und WSL

In Visual 2019, Version 16.6 haben wir eine neue Debugkonfiguration von `type: cppgdb` hinzugefügt, um das Debuggen auf Remotesystemen und WSL zu vereinfachen. Alte Debugkonfigurationen von `type: cppdbg` werden weiterhin unterstützt.

### <a name="configuration-type-cppgdb"></a>Konfigurationstyp `cppgdb`

- `name`: Dies ist ein Anzeigename zum Identifizieren der Konfiguration im Dropdownmenü **Startelement**.
- `project`: Hiermit wird der relative Pfad zur Projektdatei angegeben. Normalerweise müssen Sie diesen Pfad beim Debuggen eines CMake-Projekts nicht ändern.
- `projectTarget`: Hiermit wird das CMake-Ziel angegeben, das beim Erstellen des Projekts abgerufen werden soll. Visual Studio füllt diese Eigenschaft automatisch auf, wenn Sie *launch.vs.json* im **Menü „Debuggen“** oder in der **Targets View** (Zielansicht) eingeben. Dieser Zielwert muss mit dem Namen eines vorhandenen Debugziels übereinstimmen, das im Dropdownmenü **Startelement** aufgeführt wird.
- `debuggerConfiguration`: Hiermit wird angegeben, welche Gruppe von Standarddebugwerten verwendet werden soll. In Visual Studio 2019, Version 16.6 ist `gdb` die einzige gültige Option. Visual Studio 2019, Version 16.7 oder höher, bietet ebenfalls Unterstützung für `gdbserver`.
- `args`: Dies sind die Befehlszeilenargumente, die beim Start an das zu debuggende Programm übergeben werden.
- `env`: Diese zusätzlichen Umgebungsvariablen werden an das zu debuggende Programm übergeben. Beispielsweise `{"DISPLAY": "0.0"}`.
- `processID`: Dies ist die Linux-Prozess-ID, an die angehängt werden soll. Diese wird nur beim Anhängen an einen Remoteprozess verwendet. Weitere Informationen finden Sie unter [Problembehandlung beim Anhängen an Prozesse mithilfe von gdb](https://github.com/Microsoft/MIEngine/wiki/Troubleshoot-attaching-to-processes-using-GDB).

#### <a name="additional-options-for-the-gdb-configuration"></a>Zusätzliche Optionen für die `gdb`-Konfiguration

- `program`: Wird standardmäßig auf `"${debugInfo.fullTargetPath}"` festgelegt. Dies ist der UNIX-Pfad zu der zu debuggenden Anwendung. Dieser ist nur erforderlich, wenn dieser von dem der ausführbaren Zieldatei im Build- oder Bereitstellungsspeicherort abweicht.
- `remoteMachineName`: Wird standardmäßig auf `"${debugInfo.remoteMachineName}"` festgelegt. Dies ist der Name des Remotesystems, das das zu debuggende Programm hostet. Dieser ist nur erforderlich, wenn er von dem des Buildsystems abweicht. Im [Verbindungs-Manager](../linux/connect-to-your-remote-linux-computer.md) muss ein Eintrag vorhanden sein. Drücken Sie **STRG+LEERTASTE**, um eine Liste aller vorhandenen Remoteverbindungen anzuzeigen.
- `cwd`: Wird standardmäßig auf `"${debugInfo.defaultWorkingDirectory}"` festgelegt. Dies ist der UNIX-Pfad zum Verzeichnis auf dem Remotesystem, auf dem `program` ausgeführt wird. Das Verzeichnis muss vorhanden sein.
- `gdbpath`: Wird standardmäßig auf `/usr/bin/gdb` festgelegt. Dies ist der vollständige UNIX-Pfad zu dem zum Debuggen verwendeten `gdb`-Befehl. Dieser ist nur erforderlich, wenn eine benutzerdefinierte Version von `gdb` verwendet wird.
- `preDebugCommand`: Dies ist ein Linux-Befehl, der unmittelbar vor dem Aufrufen von `gdb` ausgeführt wird. `gdb` wird nicht gestartet, bis der Befehl abgeschlossen ist. Sie können die Option verwenden, um ein Skript vor der Ausführung von `gdb` auszuführen.

#### <a name="additional-options-allowed-with-the-gdbserver-configuration-167-or-later"></a>Mit der `gdbserver`-Konfiguration (16.7 oder höher) sind weitere Optionen zulässig.

- `program`: Wird standardmäßig auf `"${debugInfo.fullTargetPath}"` festgelegt. Dies ist der UNIX-Pfad zu der zu debuggenden Anwendung. Dieser ist nur erforderlich, wenn dieser von dem der ausführbaren Zieldatei im Build- oder Bereitstellungsspeicherort abweicht.
- `remoteMachineName`:  Wird standardmäßig auf `"${debugInfo.remoteMachineName}"` festgelegt. Dies ist der Name des Remotesystems, das das zu debuggende Programm hostet. Dieser ist nur erforderlich, wenn er von dem des Buildsystems abweicht. Im [Verbindungs-Manager](../linux/connect-to-your-remote-linux-computer.md) muss ein Eintrag vorhanden sein. Drücken Sie **STRG+LEERTASTE**, um eine Liste aller vorhandenen Remoteverbindungen anzuzeigen.
- `cwd`: Wird standardmäßig auf `"${debugInfo.defaultWorkingDirectory}"` festgelegt. Dies ist der vollständige UNIX-Pfad zum Verzeichnis auf dem Remotesystem, auf dem `program` ausgeführt wird. Das Verzeichnis muss vorhanden sein.
- `gdbPath`: Wird standardmäßig auf `${debugInfo.vsInstalledGdb}` festgelegt. Dies ist der vollständige Windows-Pfad zum `gdb`-Befehl, der für das Debuggen verwendet wird. Entspricht standardmäßig `gdb` (wird mit der Linux-Entwicklung mit der C/C++-Workload installiert).
- `gdbserverPath`: Wird standardmäßig auf `usr/bin/gdbserver` festgelegt. Dies ist der vollständige UNIX-Pfad zu dem zum Debuggen verwendeten `gdbserver`-Befehl.
- `preDebugCommand`: Dies ist ein Linux-Befehl, der unmittelbar vor dem Start von `gdbserver` ausgeführt wird. `gdbserver` wird nicht gestartet, bis der Befehl abgeschlossen ist.

#### <a name="deployment-options"></a>Bereitstellungsoptionen

Verwenden Sie die folgenden Optionen, um den (in der CMakeSettings.json-Datei definierten) Buildcomputer vom Remotedebugcomputer zu trennen.

- `remoteMachineName`: Remotedebugcomputer Dieser ist nur erforderlich, wenn er von dem des Buildcomputers abweicht. Im [Verbindungs-Manager](../linux/connect-to-your-remote-linux-computer.md) muss ein Eintrag vorhanden sein. Drücken Sie **STRG+LEERTASTE**, um eine Liste aller vorhandenen Remoteverbindungen anzuzeigen.
- `disableDeploy`: Wird standardmäßig auf `false` festgelegt. Hiermit wird angegeben, ob die Build- bzw. Debugtrennung deaktiviert ist. Im Falle von `false` ermöglicht diese Option das Durchführen von Build- und Debugvorgängen auf zwei separaten Computern.
- `deployDirectory`: Dies ist der vollständige UNIX-Pfad zum Verzeichnis auf `remoteMachineName`, in das die ausführbare Datei kopiert wird.
- `deploy`: Dies ist ein Array erweiterter Bereitstellungseinstellungen. Sie müssen diese Einstellungen nur konfigurieren, wenn Sie genauere Kontrolle über den Bereitstellungsprozess wünschen. Standardmäßig werden nur die Dateien, die für den zu debuggenden Prozess erforderlich sind, auf dem Remotedebugcomputer bereitgestellt.
  - `sourceMachine`: Dies ist der Computer, von dem die Datei oder das Verzeichnis kopiert wird. Drücken Sie **STRG+LEERTASTE**, um eine Liste aller im Verbindungs-Manager gespeicherten Remoteverbindungen anzuzeigen. Wenn Sie nativ auf WSL aufbauen, wird diese Option ignoriert.
  - `targetMachine`: Dies ist der Computer, auf den die Datei oder das Verzeichnis kopiert wird. Drücken Sie **STRG+LEERTASTE**, um eine Liste aller im Verbindungs-Manager gespeicherten Remoteverbindungen anzuzeigen.
  - `sourcePath`: Dies ist der Speicherort der Datei oder des Verzeichnisses auf `sourceMachine`.
  - `targetPath`: Dies ist der Speicherort der Datei oder des Verzeichnisses auf `targetMachine`.
  - `deploymentType`: Dies ist eine Beschreibung des Bereitstellungstyps. `LocalRemote` und `RemoteRemote` werden unterstützt. `LocalRemote` bedeutet, dass von dem lokalen Dateisystem auf das Remotesystem kopiert wird, das durch `remoteMachineName` in der *launch.vs.json*-Datei angegeben wird. `RemoteRemote` bedeutet, dass von dem in der *CMakeSettings.json*-Datei angegebenen Remotebuildsystem auf das andere in der *launch.vs.json*-Datei angegebene Remotesystem kopiert wird.
  - `executable`: Hiermit wird angegeben, ob es sich bei der bereitgestellten Datei um eine ausführbare Datei handelt.

### <a name="execute-custom-gdb-commands"></a>Ausführen benutzerdefinierter `gdb`-Befehle

Visual Studio unterstützt das Ausführen von benutzerdefinierten `gdb`-Befehlen, um direkt mit dem zugrunde liegenden Debugger zu interagieren. Weitere Informationen finden Sie unter [Ausführen benutzerdefinierter ](https://github.com/microsoft/MIEngine/wiki/Executing-custom-gdb-lldb-commands)-lldb-Befehle`gdb`.

### <a name="enable-logging"></a>Protokollierung aktivieren

Aktivieren Sie die MIEngine-Protokollierung, um anzuzeigen, welche Befehle an `gdb` gesendet werden, welche Ausgabe `gdb` zurückgibt und wie lange die einzelnen Befehle dauern. [Weitere Informationen](https://github.com/microsoft/MIEngine/wiki/Logging)

### <a name="configuration-type-cppdbg"></a>Konfigurationstyp `cppdbg`

Die folgenden Optionen können beim Debuggen auf einem Remotesystem oder WSL mit dem Konfigurationstyp `cppdbg` verwendet werden. In Visual Studio 2019, Version 16.6 oder höher wird der Konfigurationstyp `cppgdb` empfohlen.

- `name`: Dies ist ein Anzeigename zum Identifizieren der Konfiguration im Dropdownmenü **Startelement**.

- `project`: Hiermit wird der relative Pfad zur Projektdatei angegeben. Normalerweise müssen Sie diesen Wert beim Debuggen eines CMake-Projekts nicht ändern.

- `projectTarget`: Hiermit wird das CMake-Ziel angegeben, das beim Erstellen des Projekts abgerufen werden soll. Visual Studio füllt diese Eigenschaft automatisch auf, wenn Sie *launch.vs.json* im **Menü „Debuggen“** oder in der **Targets View** (Zielansicht) eingeben. Dieser Wert muss mit dem Namen eines vorhandenen Debugziels übereinstimmen, das im Dropdownmenü **Startelement** aufgeführt wird.

- `args`: Dies sind die Befehlszeilenargumente, die beim Start an das zu debuggende Programm übergeben werden.

- `processID`: Dies ist die Linux-Prozess-ID, an die angehängt werden soll. Diese wird nur beim Anhängen an einen Remoteprozess verwendet. Weitere Informationen finden Sie unter [Problembehandlung beim Anhängen an Prozesse mithilfe von gdb](https://github.com/Microsoft/MIEngine/wiki/Troubleshoot-attaching-to-processes-using-GDB).

- `program`: Wird standardmäßig auf `"${debugInfo.fullTargetPath}"` festgelegt. Dies ist der UNIX-Pfad zu der zu debuggenden Anwendung. Dieser ist nur erforderlich, wenn dieser von dem der ausführbaren Zieldatei im Build- oder Bereitstellungsspeicherort abweicht.

- `remoteMachineName`:  Wird standardmäßig auf `"${debugInfo.remoteMachineName}"` festgelegt. Dies ist der Name des Remotesystems, das das zu debuggende Programm hostet. Dieser ist nur erforderlich, wenn er von dem des Buildsystems abweicht. Im [Verbindungs-Manager](../linux/connect-to-your-remote-linux-computer.md) muss ein Eintrag vorhanden sein. Drücken Sie **STRG+LEERTASTE**, um eine Liste aller vorhandenen Remoteverbindungen anzuzeigen.

- `cwd`: Wird standardmäßig auf `"${debugInfo.defaultWorkingDirectory}"` festgelegt. Dies ist der vollständige UNIX-Pfad zum Verzeichnis auf dem Remotesystem, auf dem `program` ausgeführt wird. Das Verzeichnis muss vorhanden sein.

- `environment`: Diese zusätzlichen Umgebungsvariablen werden an das zu debuggende Programm übergeben. Ein auf ein Objekt angewendeter

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

- `pipeArgs`: Dies ist ein Array von Befehlszeilenargumenten, die zum Konfigurieren der Verbindung an das Pipeprogramm übergeben werden. Das Pipeprogramm wird verwendet, um Standardeingaben und -ausgaben zwischen Visual Studio und `gdb` weiterzuleiten. Beim Debuggen von CMake-Projekten muss ein Großteil dieses Arrays **nicht angepasst werden**. `${debuggerCommand}` bildet die Ausnahme, da hiermit `gdb` auf dem Remotesystem gestartet wird. Dies kann wie folgt geändert werden:

  - Exportieren Sie den Wert der Umgebungsvariablen „DISPLAY“ auf Ihrem Linux-System. Im folgenden Beispiel lautet dieser Wert `:1`.

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

  - Führen Sie vor der Ausführung von `gdb` ein Skript aus. Stellen Sie sicher, dass die Ausführungsberechtigungen für Ihr Skript festgelegt sind.

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

- `stopOnEntry`: Dies ist ein boolescher Wert, der angibt, ob beim Starten des Prozesses eine Unterbrechung erfolgt. Der Standardwert ist false.

- `visualizerFile`: Diese [.natvis](/visualstudio/debugger/create-custom-views-of-native-objects)-Datei wird beim Debuggen dieses Prozesses verwendet. Diese Option ist nicht mit der automatischen Strukturierung und Einrückung von `gdb` kompatibel. Legen Sie auch `showDisplayString` fest, wenn Sie diese Eigenschaft festlegen.

- `showDisplayString`: Dies ist ein boolescher Wert, der die Anzeigezeichenfolge aktiviert, wenn eine `visualizerFile`-Datei angegeben wird. Wenn diese Option auf `true` festgelegt wird, kann die Leistung beim Debuggen verlangsamt werden.

- `setupCommands`: Dies sind ein oder mehrere auszuführende `gdb`-Befehle, um den zugrunde liegenden Debugger einzurichten.

- `miDebuggerPath`: Dies ist der vollständige Pfad zu `gdb`. Wenn dieser nicht angegeben ist, sucht Visual Studio zuerst nach dem Pfad für den Debugger.

- Schließlich können auch alle Bereitstellungsoptionen, die für den Konfigurationstyp `cppgdb` definiert sind, vom Konfigurationstyp `cppdbg` verwendet werden.

### <a name="debug-using-gdbserver"></a>Debuggen mithilfe von `gdbserver`

Sie können die `cppdbg`-Konfiguration zum Debuggen mithilfe von `gdbserver` konfigurieren. Weitere Details und ein Beispiel für eine Startkonfiguration finden Sie im Blogbeitrag [Debuggen von Linux-CMake-Projekten mithilfe von`gdbserver`](https://devblogs.microsoft.com/cppblog/debugging-linux-cmake-projects-with-gdbserver/) des Microsoft C++-Teams.

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="see-also"></a>Siehe auch

[CMake-Projekte in Visual Studio](cmake-projects-in-visual-studio.md)\
[Konfigurieren eines Linux CMake-Projekts](../linux/cmake-linux-project.md)\
[Herstellen einer Verbindung mit Ihrem Linux-Remotecomputer](../linux/connect-to-your-remote-linux-computer.md)\
[Anpassen von CMake-Buildeinstellungen](customize-cmake-settings.md)\
[Konfigurieren von CMake-Debugsitzungen](configure-cmake-debugging-sessions.md)\
[Bereitstellen, Ausführen und Debuggen Ihres Linux-Projekts](../linux/deploy-run-and-debug-your-linux-project.md)\
[CMake predefined configuration reference (Referenz für vordefinierte CMake-Konfigurationen)](cmake-predefined-configuration-reference.md)

::: moniker-end
