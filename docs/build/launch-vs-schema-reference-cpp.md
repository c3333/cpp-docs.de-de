---
title: launch.vs.json-Schemaverweis (C++)
ms.date: 08/20/2019
helpviewer_keywords:
- launch.vs.json file [C++]
ms.openlocfilehash: ff4713642ab95a9bbc31f1a06236de459e53f9c3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323055"
---
# <a name="launchvsjson-schema-reference-c"></a>launch.vs.json-Schemaverweis (C++)

Verwenden Sie die *Datei launch.vs.json,* um Debugparameter zu konfigurieren. So erstellen Sie die Datei. Klicken Sie mit der rechten Maustaste auf eine ausführbare Datei im **Projektmappen-Explorer,** und wählen Sie **Debug- und Starteinstellungen**aus. Wählen Sie die Option aus, die dem Projekt am ehesten entspricht, und verwenden Sie dann die folgenden Eigenschaften, um die Konfiguration nach Bedarf zu ändern. Weitere Informationen zum Debuggen von CMake-Projekten finden Sie unter Konfigurieren von [CMake-Debuggingsitzungen](/cpp/build/configure-cmake-debugging-sessions).

## <a name="default-properties"></a>Standardeigenschaften

||||
|-|-|-|
|**Eigenschaft**|**Typ**|**Beschreibung**|
|`name`|Zeichenfolge|Gibt den Namen des Eintrags in der Dropdownliste Debugziel an.|
|`type`|Zeichenfolge|Gibt an, ob es sich bei dem Projekt um eine dLL oder .exe handelt (Standardwerte auf .exe)|
|`project`|Zeichenfolge|Gibt den relativen Pfad zur Projektdatei an.|
|`projectTarget`|Zeichenfolge|Gibt das optionale Ziel `project`an, das beim Erstellen aufgerufen wird. Dies `projectTarget` muss bereits vorhanden sein und mit dem Namen in der Dropdown-Liste **Debugziel** übereinstimmen.|
|`debugType`|Zeichenfolge|Gibt den Debugmodus entsprechend dem Codetyp (systemativ, verwaltet oder gemischt) an. Dies wird automatisch erkannt, es sei denn, dieser Parameter ist festgelegt. Zulässige Werte: "nativ", "verwaltet", "gemischt".|
|`inheritEnvironments`|array|Gibt einen Satz von Umgebungsvariablen an, die von mehreren Quellen geerbt wurden. Sie können einige Variablen in Dateien wie *CMakeSettings.json* oder *CppProperties.json* definieren und sie zum Debugkontext verfügbar machen.  **Visual Studio 16.4:** Geben Sie Umgebungsvariablen pro `env.VARIABLE_NAME` Ziel mithilfe der Syntax an. Um die Einstellung einer Variablen aufzuheben, setzen Sie sie auf "null".|
|`args`|array|Gibt die Befehlszeilenargumente an, die an das gestartete Programm übergeben werden.|
|`currentDir`|Zeichenfolge|Gibt den vollständigen Verzeichnispfad zum Buildziel an. Dies wird automatisch erkannt, es sei denn, dieser Parameter ist festgelegt.|
|`noDebug`|boolean|Gibt an, ob das gestartete Programm gedebuggen werden soll. Der Standardwert für `false` diesen Parameter ist, wenn nicht angegeben.|
|`stopOnEntry`|boolean|Gibt an, ob ein schnelles Öffnen des Prozesses und der Anfügen des Debuggers aufgebrochen werden soll. Der Standardwert für `false`diesen Parameter ist .|
|`remoteMachine`|Zeichenfolge|Gibt den Namen des Remotecomputers an, auf dem das Programm gestartet wird.|
|`env`|array| Gibt eine Schlüssel-Wert-Liste benutzerdefinierter Umgebungsvariablen an. env:'myEnv":"myVal".|
|`portName`|Zeichenfolge|Gibt den Namen des Ports an, wenn es an einen laufenden Prozess angefügt wird.|
|`buildConfigurations`|array| Ein Schlüssel-Wert-Paar, das den Namen des Buildmodus angibt, um die Konfigurationen anzuwenden. Zum Beispiel `Debug` `Release` oder und die Konfigurationen, die entsprechend dem ausgewählten Buildmodus verwendet werden sollen.

## <a name="c-linux-properties"></a>C++ Linux-Eigenschaften

||||
|-|-|-|
|**Eigenschaft**|**Typ**|**Beschreibung**|
|`program`|Zeichenfolge|Vollständiger Pfad zur Programmausführung auf dem Remotecomputer. Bei Verwendung von CMake kann das Makro `${debugInfo.fullTargetPath}` als Wert dieses Felds verwendet werden.|
|`processId`|integer|Optionale Prozess-ID zum Anfügen des Debuggers.|
|`sourceFileMap`|Objekt (object)|Optionale Quelldateizuordnungen, die an das Debugmodul übergeben werden. Format: `{ "\<Compiler source location>": "\<Editor source location>" }` `{ "\<Compiler source location>": { "editorPath": "\<Editor source location>", "useForBreakpoints": true } }`oder . Beispiel: `{ "/home/user/foo": "C:\\foo" }` oder `{ "/home/user/foo": { "editorPath": "c:\\foo", "useForBreakpoints": true } }`. Siehe [Quelldateizuordnungsoptionen](#source_file_map_options).|
|`additionalProperties`|Zeichenfolge|Eine der sourceFileMapOptions. (Siehe unten.)|
|`MIMode`|Zeichenfolge|Gibt den Typ des MI-fähigen Konsolendebuggers an, mit dem die MIDebugEngine eine Verbindung herstellt. Zulässige Werte sind "gdb", "lldb".|
|`args`|array|Befehlszeilenargumente, die an das Programm übergeben werden.|
|`environment`|array|Umgebungsvariablen, die der Umgebung für das Programm hinzugefügt werden sollen. Beispiel: [ - "name": "squid", "value": "clam" . ]|
|`targetArchitecture`|Zeichenfolge|Die Architektur des Debuggees. Dies wird automatisch erkannt, es sei denn, dieser Parameter ist festgelegt. Zulässige Werte sind x86, arm, arm64, mips, x64, amd64, x86_64.|
|`visualizerFile`|Zeichenfolge|.natvis-Datei, die beim Debuggen dieses Prozesses verwendet werden soll. Diese Option ist nicht kompatibel mit GDB-Formatdrucken. Siehe "showDisplayString", wenn Sie diese Einstellung verwenden.|
|`showDisplayString`|boolean|Wenn eine visualizerFile angegeben wird, aktiviert showDisplayString die Anzeigezeichenfolge. Das Aktivieren dieser Option kann zu einer langsameren Leistung beim Debuggen führen.|
|`remoteMachineName`|Zeichenfolge|Der Remote-Linux-Computer, auf dem gdb gehostet wird, und das zu debuggende Programm. Verwenden Sie den Verbindungs-Manager zum Hinzufügen neuer Linux-Computer. Bei Verwendung von CMake kann das Makro `${debugInfo.remoteMachineName}` als Wert dieses Felds verwendet werden.|
|`cwd`|Zeichenfolge|Das Arbeitsverzeichnis des Ziels auf dem Remotecomputer. Bei Verwendung von CMake kann das Makro `${debugInfo.defaultWorkingDirectory}` als Wert dieses Felds verwendet werden. Der Standardwert ist der Remotearbeitsbereichsstamm, es sei denn, er wird in der Datei *CMakeLists.txt* überschrieben.|
|`miDebuggerPath`|Zeichenfolge|Der Pfad zum MI-fähigen Debugger (z. B. gdb). Wenn nicht angegeben, wird PATH zuerst nach dem Debugger durchsucht.|
|`miDebuggerServerAddress`|Zeichenfolge|Netzwerkadresse des MI-fähigen Debuggerservers, mit dem eine Verbindung hergestellt werden soll. Beispiel: localhost:1234.|
|`setupCommands`|array|Ein oder mehrere GDB/LLDB-Befehle, die ausgeführt werden sollen, um den zugrunde liegenden Debugger einzurichten. Beispiel: `"setupCommands": [ { "text": "-enable-pretty-printing", "description": "Enable GDB pretty printing", "ignoreFailures": true }]`. Siehe [Setupbefehle starten](#launch_setup_commands).|
|`customLaunchSetupCommands`|array|Wenn diese Option angegeben wird, werden die Standardbefehle, die zum Starten eines Ziels verwendet werden, durch einige andere Befehle ersetzt. Dies kann z. B. "-target-attach" sein, um an einen Zielprozess anzuhängen. Eine leere Befehlsliste ersetzt die Startbefehle durch nichts, was nützlich sein kann, wenn dem Debugger Startoptionen als Befehlszeilenoptionen bereitgestellt werden. Beispiel: `"customLaunchSetupCommands": [ { "text": "target-run", "description": "run target", "ignoreFailures": false }]`.|
|`launchCompleteCommand`|Zeichenfolge|Der Befehl, der ausgeführt werden soll, nachdem der Debugger vollständig eingerichtet wurde, um die Ausführung des Zielprozesses zu bewirken. Zulässige Werte sind "exec-run", "exec-continue", "None". Der Standardwert ist "exec-run".|
|`debugServerPath`|Zeichenfolge|Optionaler vollständiger Pfad zum startenden Debugserver. Standardwerte auf null.|
|`debugServerArgs`|Zeichenfolge|Optionale Debugserver-Args. Standardwerte auf null.|
|`filterStderr`|boolean|Suchen Sie den Stderr-Stream nach servergestartetem Muster und log stderr zum Debuggen der Ausgabe. Der Standardwert lautet `false`.|
|`coreDumpPath`|Zeichenfolge|Optionaler vollständiger Pfad zu einer Core-Dump-Datei für das angegebene Programm. Standardwerte auf null.|
externalConsole|boolean|Wenn true, wird eine Konsole für das Debuggee gestartet. Wenn `false`, wird keine Konsole gestartet. Der Standardwert lautet `false`. HINWEIS: Diese Option wird in einigen Fällen aus technischen Gründen ignoriert.|
|`pipeTransport`|Zeichenfolge|Wenn vorhanden, weist dies den Debugger an, eine Verbindung zu einem Remotecomputer herzustellen, der eine andere ausführbare Datei als Pipe verwendet, die Die Standardeingabe/-ausgabe zwischen Visual Studio und dem MI-fähigen Debugger (z. B. gdb) weiterleitet. Zulässige Werte: eine oder mehrere [Rohrtransportoptionen](#pipe_transport_options).|

## <a name="launch-setup-commands"></a><a name="launch_setup_commands"></a>Setup-Befehle starten

Wird mit `setupCommands` der Eigenschaft verwendet:

||||
|-|-|-|
|`text`|Zeichenfolge|Der auszuführende Debuggerbefehl.|
|`description`|Zeichenfolge|Optionale Beschreibung für den Befehl.|
|`ignoreFailures`|boolean|Wenn true, sollten Fehler des Befehls ignoriert werden. Der Standardwert lautet `false`.|

## <a name="pipe-transport-options"></a><a name = "pipe_transport_options"></a>Rohrtransportoptionen

Wird mit `pipeTransport` der Eigenschaft verwendet:

||||
|-|-|-|
|`pipeCwd`|Zeichenfolge|Der vollqualifizierte Pfad zum Arbeitsverzeichnis für das Rohrprogramm.|
|`pipeProgram`|Zeichenfolge|Der vollqualifizierte auszuführende Pipe-Befehl.|
|`pipeArgs`|array|Befehlszeilenargumente, die an das Rohrprogramm übergeben werden, um die Verbindung zu konfigurieren.|
|`debuggerPath`|Zeichenfolge|Der vollständige Pfad zum Debugger auf dem Zielcomputer, z. B. /usr/bin/gdb.|
|`pipeEnv`|Objekt (object)|Umgebungsvariablen, die an das Rohrprogramm übergeben werden.|
|`quoteArgs`|boolean|Wenn einzelne Argumente Zeichen enthalten (z. B. Leerzeichen oder Registerkarten), sollten sie zitiert werden? Wenn `false`, wird der Befehl debugger nicht mehr automatisch zitiert. Der Standardwert ist `true`.|

## <a name="source-file-map-options"></a><a name="source_file_map_options"></a>Quelldateizuordnungsoptionen

Verwendung mit `sourceFileMap` der Eigenschaft:

||||
|-|-|-|
|`editorPath`|Zeichenfolge|Der Speicherort des Quellcodes, den der Editor suchen soll.|
|`useForBreakpoints`|boolean|Beim Festlegen von Haltepunkten sollte diese Quellzuordnung verwendet werden. Wenn `false`, wird nur der Dateiname und die Zeilennummer zum Festlegen von Haltepunkten verwendet. Wenn `true`, werden Haltepunkte mit dem vollständigen Pfad zur Datei- und Zeilennummer nur festgelegt, wenn diese Quellzuordnung verwendet wird. Andernfalls werden beim Festlegen von Haltepunkten nur Dateiname und Zeilennummer verwendet. Der Standardwert ist `true`.|
