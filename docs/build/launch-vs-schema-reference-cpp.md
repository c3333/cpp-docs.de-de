---
title: launch.vs.json-Schemareferenz (C++)
ms.date: 08/20/2019
helpviewer_keywords:
- launch.vs.json file [C++]
ms.openlocfilehash: ff4713642ab95a9bbc31f1a06236de459e53f9c3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323055"
---
# <a name="launchvsjson-schema-reference-c"></a>launch.vs.json-Schemareferenz (C++)

Verwenden Sie die Datei *launch.vs.json*, um Debugparameter zu konfigurieren. Klicken Sie zum Erstellen der Datei mit der rechten Maustaste auf eine ausführbare Datei im **Projektmappen-Explorer**, und klicken Sie auf **Debug- und Starteinstellungen**. Wählen Sie die Option aus, die Ihrem Projekt am ehesten entspricht, und verwenden Sie dann die folgenden Eigenschaften, um die Konfiguration nach Bedarf anzupassen. Weitere Informationen zum Debuggen von CMake-Projekten finden Sie unter [Konfigurieren von CMake-Debugsitzungen](/cpp/build/configure-cmake-debugging-sessions).

## <a name="default-properties"></a>Standardeigenschaften

||||
|-|-|-|
|**Property**|**Type**|**Beschreibung**|
|`name`|string|Hiermit wird der Name des Eintrags in der Dropdownliste „Debugziel“ angegeben.|
|`type`|string|Hiermit wird angegeben, ob es sich bei dem Projekt um eine DLL oder eine EXE-Datei handelt. (Standardmäßig handelt es sich um eine EXE-Datei.)|
|`project`|string|Hiermit wird der relative Pfad zur Projektdatei angegeben.|
|`projectTarget`|string|Hiermit wird das optionale Ziel angegeben, das bei der Erstellung von `project`aufgerufen wird. Das mit `projectTarget` angegebene Ziel muss bereits vorhanden sein, und der Name muss mit dem in der Dropdownliste **Debugziel** übereinstimmen.|
|`debugType`|string|Hiermit wird der Debuggingmodus für die jeweilige Art von Code angegeben (nativ, verwaltet oder gemischt). Er wird automatisch erkannt, wenn für diesen Parameter nichts festgelegt wurde. Zulässige Werte sind: „native“, „managed“ und „mixed“.|
|`inheritEnvironments`|array|Hiermit werden mehrere Umgebungsvariablen angegeben, die aus mehreren Quellen geerbt werden. Manche Variablen können Sie in Dateien wie *CMakeSettings.json* oder *CppProperties.json* definieren und für den Debugkontext verfügbar machen.  **Visual Studio 16.4:** Geben Sie Umgebungsvariablen pro Ziel an. Verwenden Sie dazu die `env.VARIABLE_NAME`-Syntax. Wenn Sie die Festlegung einer Variable aufheben möchten, legen Sie sie auf „null“ fest.|
|`args`|array|Hiermit werden die Befehlszeilenargumente angegeben, die an das gestartete Programm übergeben werden.|
|`currentDir`|string|Hiermit wird der vollständige Verzeichnispfad zum Buildziel angegeben. Er wird automatisch erkannt, wenn für diesen Parameter nichts festgelegt wurde.|
|`noDebug`|boolean|Hiermit wird angegeben, ob das gestartete Programm debuggt werden soll. Wenn nichts angegeben wird, ist der Standardwert für diesen Parameter `false`.|
|`stopOnEntry`|boolean|Hiermit wird angegeben, ob beim Starten des Prozesses eine Unterbrechung erfolgt und der Debugger angefügt wird. Der Standardwert für diesen Parameter ist `false`.|
|`remoteMachine`|string|Hiermit wird der Name des Remotecomputers angegeben, auf dem das Programm gestartet wird.|
|`env`|array| Hiermit wird eine Schlüssel-Wert-Liste benutzerdefinierter Umgebungsvariablen angegeben: env:{"myEnv":"myVal"}.|
|`portName`|string|Hiermit wird der Name des Ports beim Anfügen an einen Prozess, der ausgeführt wird, angegeben.|
|`buildConfigurations`|array| Hierbei handelt es sich um ein Schlüssel-Wert-Paar, das den Namen des Buildmodus angibt, der die Konfigurationen anwenden soll. Beispiele hierfür sind `Debug` oder `Release` sowie die Konfigurationen, die je nach ausgewähltem Buildmodus verwendet werden sollen.

## <a name="c-linux-properties"></a>C++-Linux-Eigenschaften

||||
|-|-|-|
|**Property**|**Type**|**Beschreibung**|
|`program`|string|Hierbei handelt es sich um den vollständigen Pfad zur ausführbaren Programmdatei auf dem Remotecomputer. Wenn CMake verwendet wird, kann das Makro `${debugInfo.fullTargetPath}` als Wert für dieses Feld verwendet werden.|
|`processId`|Ganze Zahl|Hierbei handelt es sich um die optionale Prozess-ID, an die der Debugger angefügt werden soll.|
|`sourceFileMap`|Objekt|Hierbei handelt es sich um optionale Quelldateizuordnungen, die an die Debug-Engine übergeben werden. Das Format lautet `{ "\<Compiler source location>": "\<Editor source location>" }` oder `{ "\<Compiler source location>": { "editorPath": "\<Editor source location>", "useForBreakpoints": true } }`. Beispiele sind `{ "/home/user/foo": "C:\\foo" }` oder `{ "/home/user/foo": { "editorPath": "c:\\foo", "useForBreakpoints": true } }`. Weitere Informationen finden Sie unter [Quelldateizuordnungsoptionen](#source_file_map_options).|
|`additionalProperties`|string|Hierbei handelt es sich um eine der sourceFileMapOptions. (Siehe unten.)|
|`MIMode`|string|Hiermit wird der Typ des MI-fähigen Konsolendebuggers angegeben, mit dem MIDebugEngine eine Verbindung herstellt. Zulässige Werte sind „gdb“ und „lldb“.|
|`args`|array|Hierbei handelt es sich um Befehlszeilenargumente, die an das Programm übergeben werden.|
|`environment`|array|Hiermit werden Umgebungsvariablen angegeben, die der Umgebung für das Programm hinzugefügt werden sollen. Beispiel: [ { "name": "squid", "value": "clam" } ]|
|`targetArchitecture`|string|Hiermit wird die Architektur der zu debuggenden Komponente angegeben. Sie wird automatisch erkannt, wenn für diesen Parameter nichts festgelegt wurde. Zulässige Werte sind „x86“, „arm“, „arm64“, „mips“, „x64“, „amd64“ und „x86_64“.|
|`visualizerFile`|string|Hiermit wird die NATVIS-Datei angegeben, die beim Debuggen dieses Prozesses verwendet werden soll. Diese Option ist nicht mit der automatischen Strukturierung und Einrückung von GDB kompatibel. Sehen Sie sich die Hinweise zu showDisplayString an, wenn Sie diese Einstellung verwenden.|
|`showDisplayString`|boolean|Wenn für visualizerFile ein Wert angegeben wird, aktiviert showDisplayString die Anzeigezeichenfolge. Wenn diese Option eingeschaltet wird, kann die Leistung beim Debuggen verlangsamt werden.|
|`remoteMachineName`|string|Hiermit wird der Linux-Remotecomputer angegeben, der gdb und das zu debuggende Programm hostet. Verwenden Sie den Verbindungs-Manager zum Hinzufügen neuer Linux-Computer. Wenn CMake verwendet wird, kann das Makro `${debugInfo.remoteMachineName}` als Wert für dieses Feld verwendet werden.|
|`cwd`|string|Hiermit wird das Arbeitsverzeichnis des Ziels auf dem Remotecomputer angegeben. Wenn CMake verwendet wird, kann das Makro `${debugInfo.defaultWorkingDirectory}` als Wert für dieses Feld verwendet werden. Der Standardwert ist der Stamm des Remotearbeitsbereichs, außer er wurde in der Datei *CMakeLists.txt* außer Kraft gesetzt.|
|`miDebuggerPath`|string|Hiermit wird der Pfad zum MI-fähigen Debugger (z. B. gdb) angegeben. Wenn nichts angegeben ist, wird erst PATH nach dem Debugger durchsucht.|
|`miDebuggerServerAddress`|string|Hiermit wird die Netzwerkadresse des MI-fähigen Debuggerservers angegeben, mit dem eine Verbindung hergestellt werden soll. Beispiel: localhost:1234|
|`setupCommands`|array|Hiermit werden ein oder mehrere GDB- oder LLDB-Befehle angegeben, die ausgeführt werden sollen, um den zugrunde liegenden Debugger einzurichten. Beispiel: `"setupCommands": [ { "text": "-enable-pretty-printing", "description": "Enable GDB pretty printing", "ignoreFailures": true }]` Weitere Informationen finden Sie unter [Startsetupbefehle](#launch_setup_commands).|
|`customLaunchSetupCommands`|array|Wenn ein Wert angegeben wird, ersetzt diese Einstellung die Standardbefehle für das Starten eines Ziels durch andere Befehle. Beispielsweise kann „-target-attach“ zum Anfügen an einen Zielprozess verwendet werden. Eine leere Befehlsliste ersetzt die Startbefehle durch nichts. Dies kann nützlich sein, wenn für den Debugger Startoptionen als Befehlszeilenoptionen bereitgestellt werden. Beispiel: `"customLaunchSetupCommands": [ { "text": "target-run", "description": "run target", "ignoreFailures": false }]`|
|`launchCompleteCommand`|string|Hiermit wird der Befehl angegeben, der ausgeführt werden soll, wenn der Debugger vollständig eingerichtet ist, damit der Zielprozess ausgeführt wird. Zulässige Werte sind „exec-run“, „exec-continue“ und „None“. Der Standardwert ist „exec-run“.|
|`debugServerPath`|string|Hiermit wird ein optionaler vollständiger Pfad zum zu startenden Debugserver angegeben. Der Standardwert ist „null“.|
|`debugServerArgs`|string|Hiermit werden optionale Debugserverargumente angegeben. Der Standardwert ist „null“.|
|`filterStderr`|boolean|Hiermit wird ein stderr-Datenstrom für ein vom Server gestartetes Muster gesucht und stderr in der Debugausgabe protokolliert. Wird standardmäßig auf `false` festgelegt.|
|`coreDumpPath`|string|Hiermit wird ein optionaler vollständiger Pfad zu einer Kern-Speicherabbilddatei für das angegebene Programm angegeben. Der Standardwert ist „null“.|
externalConsole|boolean|Wenn „true“ festgelegt ist, wird eine Konsole für die zu debuggende Komponente gestartet. Wenn `false` festgelegt ist, wird keine Konsole gestartet. Wird standardmäßig auf `false` festgelegt. HINWEIS: Diese Option wird in manchen Fällen aus technischen Gründen ignoriert.|
|`pipeTransport`|string|Falls angegeben, weist diese Option den Debugger an, eine Verbindung mit einem Remotecomputer mithilfe einer anderen ausführbaren Datei als Pipe herzustellen, die Standardeingaben/-ausgaben zwischen Visual Studio und dem MI-fähigen Debugger (z. B. gdb) weiterleitet. Zulässige Werte sind eine oder mehrere [Pipetransportoptionen](#pipe_transport_options).|

## <a name="launch-setup-commands"></a><a name="launch_setup_commands"></a> Startsetupbefehle

Folgende Optionen können mit der Eigenschaft `setupCommands` verwendet werden:

||||
|-|-|-|
|`text`|string|Hiermit wird der auszuführende Debuggerbefehl angegeben.|
|`description`|string|Hiermit wird eine optionale Beschreibung des Befehls angegeben.|
|`ignoreFailures`|boolean|Wenn „true“ festgelegt ist, sollten durch den Befehl verursachte Fehler ignoriert werden. Wird standardmäßig auf `false` festgelegt.|

## <a name="pipe-transport-options"></a><a name = "pipe_transport_options"></a> Pipetransportoptionen

Folgende Optionen können mit der Eigenschaft `pipeTransport` verwendet werden:

||||
|-|-|-|
|`pipeCwd`|string|Hiermit wird der vollqualifizierte Pfad zum Arbeitsverzeichnis für das Pipeprogramm angegeben.|
|`pipeProgram`|string|Hiermit wird der vollqualifizierte auszuführende Pipebefehl angegeben.|
|`pipeArgs`|array|Hiermit werden Befehlszeilenargumente angegeben, die zum Konfigurieren der Verbindung an das Pipeprogramm übergeben werden.|
|`debuggerPath`|string|Hiermit wird der vollständige Pfad zum Debugger auf dem Zielcomputer angegeben, z. B. „/usr/bin/gdb“.|
|`pipeEnv`|Objekt|Hiermit werden Umgebungsvariablen angegeben, die an das Pipeprogramm übergeben werden.|
|`quoteArgs`|boolean|Wenn einzelne Argumente Zeichen enthalten (z. B. Leerzeichen oder Tabstoppzeichen), sollen diese in Anführungszeichen gesetzt werden? Wenn `false` festgelegt ist, wird der Debuggerbefehl nicht mehr automatisch in Anführungszeichen eingeschlossen. Der Standardwert ist `true`.|

## <a name="source-file-map-options"></a><a name="source_file_map_options"></a> Quelldateizuordnungsoptionen

Folgende Optionen können mit der Eigenschaft `sourceFileMap` verwendet werden:

||||
|-|-|-|
|`editorPath`|string|Hiermit wird der Speicherort des Quellcodes angegeben, den der Editor sucht.|
|`useForBreakpoints`|boolean|Beim Festlegen von Breakpoints sollte diese Quellzuordnung verwendet werden. Wenn `false` festgelegt ist, werden nur der Dateiname und die Zeilennummer zum Festlegen von Breakpoints verwendet. Wenn `true` festgelegt ist, werden Breakpoints nur mit dem vollständigen Pfad zur Datei und der Zeilennummer festgelegt, wenn diese Quellzuordnung verwendet wird. Andernfalls werden beim Festlegen von Breakpoints nur Dateiname und Zeilennummer verwendet. Der Standardwert ist `true`.|
