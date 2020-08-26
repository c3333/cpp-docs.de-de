---
title: Tasks.vs.json-Schemareferenz (C++)
ms.date: 08/20/2019
helpviewer_keywords:
- tasks.vs.json file [C++]
ms.assetid: abd1985e-3717-4338-9e80-869db5435175
ms.openlocfilehash: a2aea1b64d5a6c62604c680bf1a4a26478b7b52a
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88844989"
---
# <a name="tasksvsjson-schema-reference-c"></a>Tasks.vs.json-Schemareferenz (C++)

Fügen Sie eine *tasks.vs.json*-Datei hinzu, damit Visual Studio weiß, wie Ihr Quellcode in einem „Ordner öffnen“-Projekt erstellt werden soll. Sie können in dieser Datei eine beliebige Aufgabe definieren und diesen dann über das Kontextmenü des **Projektmappen-Explorers** aufrufen. CMake-Projekte verwenden diese Datei in der Regel nicht, da alle Buildbefehle in *CMakeLists.txt* angegeben sind. Bei anderen Buildsystemen als CMake können Sie in *tasks.vs.json* Ihre Buildbefehle angeben und Buildskripts aufrufen. Allgemeine Informationen zur Verwendung von *tasks.vs.json* finden Sie unter [Anpassen von Build- und Debugtasks für die Open Folder-Entwicklung](/visualstudio/ide/customize-build-and-debug-tasks-in-visual-studio).

Eine Aufgabe hat eine `type`-Eigenschaft, die einen von vier Werten aufweisen kann: `default`, `launch`, `remote` oder `msbuild`. Die meisten Aufgaben sollten `launch` verwenden, es sei denn, eine Remoteverbindung ist erforderlich.

## <a name="default-properties"></a>Standardeigenschaften

Die Standardeigenschaften sind für alle Aufgabentypen verfügbar:

|Eigenschaft|type|BESCHREIBUNG|
|-|-|-|
|`taskLabel`|string| (Erforderlich.) Gibt die in der Benutzeroberfläche verwendete Aufgabenbezeichnung an.|
|`appliesTo`|string| (Erforderlich.) Gibt an, für welche Dateien der Befehl ausgeführt werden kann. Die Verwendung von Platzhaltern wird unterstützt, z. B. „ *“, „* .cpp“, „/*.txt“.|
|`contextType`|string| Zulässige Werte sind: „custom“, „build“, „clean“ und „rebuild“. Bestimmt, wo im Kontextmenü die Aufgabe angezeigt wird. Der Standardwert ist „custom“.|
|`output`|string| Gibt ein Ausgabetag für Ihren Task an.|
|`inheritEnvironments`|array| Gibt mehrere Umgebungsvariablen an, die aus mehreren Quellen geerbt werden. Sie können Variablen in Dateien wie *CMakeSettings.json* oder *CppProperties.json* definieren und sie für den Aufgabenkontext verfügbar machen. **Visual Studio 16.4:** Geben Sie Umgebungsvariablen pro Aufgabe an. Verwenden Sie dazu die `env.VARIABLE_NAME`-Syntax. Wenn Sie die Festlegung einer Variable aufheben möchten, legen Sie sie auf „null“ fest.|
|`passEnvVars`|boolean| Gibt an, ob zusätzliche Umgebungsvariablen für den Aufgabenkontext eingeschlossen werden sollen oder nicht. Diese Variablen unterscheiden sich von denen, die mithilfe der `envVars`-Eigenschaft definiert werden. Der Standardwert ist „True“.|

## <a name="launch-properties"></a>Starteigenschaften

Wenn der Aufgabentyp `launch` ist, sind die folgenden Eigenschaften verfügbar:

|Eigenschaft|type|BESCHREIBUNG|
|-|-|-|
|`command`|string| Gibt den vollständigen Pfad des Prozesses oder Skripts für den Start an.|
|`args`|array| Gibt eine durch Kommas getrennte Liste an Argumenten an, die an den Befehl übergeben werden.|
|`launchOption`|string| Zulässige Werte: „None“, „ContinueOnError“, „IgnoreError“. Gibt an, wie der Befehl fortgesetzt werden soll, wenn Fehler auftreten.|
|`workingDirectory`|string| Gibt das Verzeichnis an, in dem der Befehl ausgeführt wird. Standardwert: Das aktuelle Arbeitsverzeichnis des Projekts.|
|`customLaunchCommand`|string| Gibt eine globale Bereichsanpassung an, die angewendet werden soll, bevor der Befehl ausgeführt wird. Dies ist hilfreich, wenn Umgebungsvariablen wie %PATH% festgelegt werden sollen.|
|`customLaunchCommandArgs`|string| Gibt Argumente für customLaunchCommand an. (Erfordert `customLaunchCommand`.)|
 `env`| Gibt eine Schlüssel-Wert-Liste benutzerdefinierter Umgebungsvariablen an. Beispiel: „myEnv“: „myVal“.|
|`commands`|array| Gibt eine Liste von Befehlen an, die in Reihenfolge aufgerufen werden sollen.|

### <a name="example"></a>Beispiel

Die folgenden Aufgaben rufen *make.exe* auf, wenn eine Makefile im Ordner bereitgestellt wird und die `Mingw64`-Umgebung in *CppProperties.json* definiert wurde. Sehen Sie sich dazu die [CppProperties.json-Schemareferenz](cppproperties-schema-reference.md#user_defined_environments) an:

```json
 {
  "version": "0.2.1",
  "tasks": [
    {
      "taskLabel": "gcc make",
      "appliesTo": "*.cpp",
      "type": "launch",
      "contextType": "custom",
      "inheritEnvironments": [
        "Mingw64"
      ],
      "command": "make"
    },
    {
      "taskLabel": "gcc clean",
      "appliesTo": "*.cpp",
      "type": "launch",
      "contextType": "custom",
      "inheritEnvironments": [
        "Mingw64"
      ],
      "command": "make",
      "args": ["clean"]
    }
  ]
}
```

Die Aufgaben können im Kontextmenü aufgerufen werden, wenn Sie mit der rechten Maustaste auf eine *CPP*-Datei im **Projektmappen-Explorer** klicken.

## <a name="remote-properties"></a>Remoteeigenschaften

Remoteaufgaben sind möglich, wenn Sie die Workload „Linux Entwicklung mit C++“ installieren und eine Verbindung zu einem Remotecomputer hinzufügen, indem Sie den Verbindungs-Manager in Visual Studio verwenden. Eine Remoteaufgabe führt Befehle auf einem Remotesystem aus und kann auch Dateien dorthin kopieren.

Wenn der Aufgabentyp `remote` ist, sind die folgenden Eigenschaften verfügbar:

|Eigenschaft|type|BESCHREIBUNG|
|-|-|-|
|`remoteMachineName`|string|Der Name des Remotecomputers. Dieser muss einem Computername im **Verbindungs-Manager** entsprechen.|
|`command`|string|Der Befehl, um den Remotecomputer zu senden. Standardmäßig werden Befehle im $HOME-Verzeichnis auf dem Remotesystem ausgeführt.|
|`remoteWorkingDirectory`|string|Das aktuelle Arbeitsverzeichnis auf dem Remotecomputer.|
|`localCopyDirectory`|string|Das lokale Verzeichnis, das auf den Remotecomputer kopiert werden soll. Der Standardwert ist das aktuelle Arbeitsverzeichnis.|
|`remoteCopyDirectory`|string|Das Verzeichnis auf dem Remotecomputer, in das `localCopyDirectory` kopiert wird.|
|`remoteCopyMethod`|string| Die Methode, die für den Kopiervorgang verwendet wird. Zulässige Werte sind: „none“, „sftp“, „rsync“. „rsync“ wird für große Projekte empfohlen.|
|`remoteCopySourcesOutputVerbosity`|string| Zulässige Werte: „Normal“, „Verbose“, „Diagnostic“.|
|`rsyncCommandArgs`|string|Der Standard ist „-t --delete“.|
|`remoteCopyExclusionList`|array|Durch Kommas getrennte Liste von Dateien in `localCopyDirectory`, die bei Kopiervorgängen ausgeschlossen werden sollen.|

### <a name="example"></a>Beispiel

Die folgende Aufgabe wird im Kontextmenü angezeigt, wenn Sie mit der rechten Maustaste auf *main.cpp* im **Projektmappen-Explorer** klicken. Die Aufgabe hängt von einem Remotecomputer namens `ubuntu` im **Verbindungs-Manager** ab. Die Aufgabe kopiert den aktuellen Ordner in Visual Studio in das `sample`-Verzeichnis auf dem Remotecomputer und ruft dann g++ ab, um das Programm zu erstellen.

```json
{
  "version": "0.2.1",
  "tasks": [
    {
      "taskLabel": "Build",
      "appliesTo": "main.cpp",
      "type": "remote",
      "contextType": "build",
      "command": "g++ main.cpp",
      "remoteMachineName": "ubuntu",
      "remoteCopyDirectory": "~/sample",
      "remoteCopyMethod": "sftp",
      "remoteWorkingDirectory": "~/sample/hello",
      "remoteCopySourcesOutputVerbosity": "Verbose"
    }
  ]
}
```

## <a name="msbuild-properties"></a>MSBuild-Eigenschaften

Wenn der Aufgabentyp `msbuild` ist, sind die folgenden Eigenschaften verfügbar:

|Eigenschaft|type|BESCHREIBUNG|
|-|-|-|
|`verbosity`|string| Gibt die verbosityAllowed-Werte für die MSBuild-Projektbuildausgabe an: „Quiet“, „Minimal“, „Normal“, „Detailed“, „Diagnostic“.|
|`toolsVersion`|string| Gibt die Toolsetversion an, mit der das Projekt erstellt werden soll, z. B. „2.0“, „3.5“, „4.0“, „Current“. Der Standardwert ist „Current“.|
|`globalProperties`|Objekt|Gibt eine Schlüssel-Wert-Liste der globalen Eigenschaften an, die in das Projekt übergeben werden sollen, z. B. „Configuration“:„Release“.|
|`properties`|Objekt| Gibt eine Schlüssel-Wert-Liste zusätzlicher nur für das Projekt geltender Eigenschaften an.|
|`targets`|array| Gibt die Liste der Ziele an, die im Projekt der Reihe nach aufgerufen werden sollen. Das Standardziel des Projekts wird verwendet, wenn keines angegeben ist.|
