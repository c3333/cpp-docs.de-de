---
title: „Ordner öffnen“-Unterstützung für C++-Buildsysteme in Visual Studio
ms.date: 12/02/2019
helpviewer_keywords:
- Open Folder Projects in Visual Studio
ms.assetid: abd1985e-3717-4338-9e80-869db5435175
ms.openlocfilehash: 73d6ff9fb9411b146082989d581ed35298b911ad
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229804"
---
# <a name="open-folder-support-for-c-build-systems-in-visual-studio"></a>„Ordner öffnen“-Unterstützung für C++-Buildsysteme in Visual Studio

::: moniker range="vs-2015"

Das Feature „Ordner öffnen“ ist in Visual Studio 2017 und höher verfügbar.

::: moniker-end

::: moniker range=">=vs-2017"

In Visual Studio 2017 und höher können Sie das Feature „Ordner öffnen“ verwenden, um einen Ordner mit Quelldateien öffnen und sofort mit dem Programmieren beginnen zu können. Dabei wird unter anderem IntelliSense, das Durchsuchen, Refactoring und Debuggen unterstützt. Während Sie Dateien bearbeiten, erstellen, verschieben und löschen, verfolgt Visual Studio die Änderungen automatisch nach und aktualisiert den IntelliSense-Index kontinuierlich. Es werden keine SLN- oder VCXPROJ-Dateien geladen. Bei Bedarf können Sie benutzerdefinierte Tasks sowie Build- und Startparameter über einfache JSON-Dateien angeben. Mit diesem Feature können Sie jedes beliebige Drittanbieterbuildsystem in Visual Studio integrieren. Allgemeine Informationen zu „Ordner öffnen“ finden Sie unter [Entwickeln von Code in Visual Studio ohne Projekte oder Projektmappen](/visualstudio/ide/develop-code-in-visual-studio-without-projects-or-solutions).

## <a name="cmake-and-qt"></a>CMake und Qt

CMake ist in die Visual Studio-IDE als Komponente der Workload für C++-Desktopentwicklung integriert. Der Workflow für CMake ist nicht identisch mit dem in diesem Artikel beschriebenen Workflow. Wenn Sie CMake verwenden, finden Sie unter [CMake-Projekte in Visual Studio](cmake-projects-in-visual-studio.md) weitere Informationen. Sie können auch CMake verwenden, um Qt-Projekten zu erstellen. Alternativ können Sie für Visual Studio 2015 oder 2017 die [Qt-Erweiterung für Visual Studio](https://download.qt.io/development_releases/vsaddin/) verwenden.

## <a name="other-build-systems"></a>Andere Buildsysteme

Wenn Sie die Visual Studio-IDE mit einem Buildsystem oder einem Compilertoolset verwenden möchten, das nicht direkt unterstützt wird, klicken Sie im Hauptmenü auf **Datei > Öffnen > Ordner**, oder drücken Sie **STRG+UMSCHALT+ALT+O**. Navigieren Sie zu dem Ordner, der Ihre Quellcodedateien enthält. Wenn Sie das Projekt erstellen, IntelliSense konfigurieren und Debugparameter festlegen möchten, fügen Sie drei JSON-Dateien hinzu:

| | |
|-|-|
|CppProperties.json|Geben Sie benutzerdefinierte Konfigurationsinformationen für das Durchsuchen an. Erstellen Sie diese Datei bei Bedarf im Stammordner des Projekts. (Wird in CMake-Projekten nicht verwendet.)|
|tasks.vs.json|Angeben von benutzerdefinierten Buildbefehlen. Der Zugriff erfolgt über das Kontextmenüelement **Tasks konfigurieren** im **Projektmappen-Explorer**.|
|launch.vs.json|Geben Sie Befehlszeilenargumente für den Debugger an. Der Zugriff erfolgt über das Kontextmenüelement **Einstellungen für Debuggen und Starten** im **Projektmappen-Explorer**.|

## <a name="configure-code-navigation-with-cpppropertiesjson"></a>Konfigurieren der Codenavigation mithilfe von CppProperties.json

Damit IntelliSense und das Verhalten von Suchen wie **Gehe zu Definition** ordnungsgemäß funktionieren, muss Visual Studio wissen, welchen Compiler Sie verwenden, wo sich die Systemheader befinden und wo weitere Includedateien zu finden sind, wenn sie sich nicht direkt in dem Ordner befinden, den Sie geöffnet haben (der Arbeitsbereichsordner). Zum Angeben einer Konfiguration können Sie im Dropdown in der Hauptsymbolleiste auf die Option **Konfigurationen verwalten** klicken:

![Dropdown „Konfigurationen verwalten“](media/manage-configurations-dropdown.png)

In Visual Studio stehen die folgenden Standardkonfigurationen zur Verfügung:

![Standardkonfigurationen](media/default-configurations.png)

Wenn Sie beispielsweise **x64-Debug** auswählen, erstellt Visual Studio eine Datei namens *CppProperties.json* im Stammprojektordner:

```json
{
  "configurations": [
    {
      "inheritEnvironments": [
        "msvc_x64"
      ],
      "name": "x64-Debug",
      "includePath": [
        "${env.INCLUDE}",
        "${workspaceRoot}\\**"
      ],
      "defines": [
        "WIN32",
        "_DEBUG",
        "UNICODE",
        "_UNICODE"
      ],
      "intelliSenseMode": "windows-msvc-x64"
    }
  ]
}
```

Diese Konfiguration erbt die Umgebungsvariablen von der [x64-Developer-Eingabeaufforderung](building-on-the-command-line.md) in Visual Studio. Eine dieser Variablen ist `INCLUDE`, und Sie können hier auf sie verweisen, indem Sie das `${env.INCLUDE}`-Makro verwenden. Über die `includePath`-Eigenschaft erfährt Visual Studio, wo nach all den Quellen gesucht werden muss, die für IntelliSense benötigt werden. In diesem Fall wird Visual Studio angewiesen, in allen Verzeichnissen zu suchen, die von der INCLUDE-Umgebungsvariable angegeben werden, sowie in allen Verzeichnissen in der aktuellen Arbeitsordnerstruktur. Bei der `name`-Eigenschaft handelt es sich um den Name, der im Dropdown angezeigt wird. Sie können einen beliebigen Namen festlegen. Die `defines`-Eigenschaft stellt Hinweise für IntelliSense bereit, wenn Blöcke für die bedingte Kompilierung auftreten. Die `intelliSenseMode`-Eigenschaft stellt basierend auf dem Typ des Compilers weitere Hinweise bereit. Für MSVC, GCC und Clang stehen verschiedene Optionen zur Verfügung.

> [!NOTE]
> Wenn Visual Studio Einstellungen in *CppProperties.json* zu ignorieren scheint, versuchen Sie, Ihrer *GITIGNORE*-Datei folgendermaßen eine Ausnahme hinzuzufügen: `!/CppProperties.json`.

## <a name="default-configuration-for-mingw-w64"></a>Standardkonfiguration für MinGW-w64

Wenn Sie die MinGW-W64-Konfiguration hinzufügen, sieht die JSON-Datei folgendermaßen aus:

```json
{
  {
      "inheritEnvironments": [
        "mingw_64"
      ],
      "name": "Mingw64",
      "includePath": [
        "${env.INCLUDE}",
        "${workspaceRoot}\\**"
      ],
      "intelliSenseMode": "linux-gcc-x64",
      "environments": [
        {
          "MINGW64_ROOT": "C:\\msys64\\mingw64",
          "BIN_ROOT": "${env.MINGW64_ROOT}\\bin",
          "FLAVOR": "x86_64-w64-mingw32",
          "TOOLSET_VERSION": "9.1.0",
          "PATH": "${env.BIN_ROOT};${env.MINGW64_ROOT}\\..\\usr\\local\\bin;${env.MINGW64_ROOT}\\..\\usr\\bin;${env.MINGW64_ROOT}\\..\\bin;${env.PATH}",
          "INCLUDE": "${env.MINGW64_ROOT}\\include\\c++\\${env.TOOLSET_VERSION};${env.MINGW64_ROOT}\\include\\c++\\${env.TOOLSET_VERSION}\\tr1;${env.MINGW64_ROOT}\\include\\c++\\${env.TOOLSET_VERSION}\\${env.FLAVOR}",
          "environment": "mingw_64"
        }
      ]
    }
}
```

Beachten Sie den `environments`-Block. Er definiert Eigenschaften, die sich wie Umgebungsvariablen verhalten und nicht nur in der *CppProperties.json*-Datei verfügbar sind, sondern auch in den Konfigurationsdateien *task.vs.json* und *launch.vs.json*. Die `Mingw64`-Konfiguration erbt die `mingw_w64`-Umgebung und verwendet die dazugehörige `INCLUDE`-Eigenschaft, um den Wert für `includePath` anzugeben. Sie können dieser Arrayeigenschaft bei Bedarf weitere Pfade hinzufügen.

Die `intelliSenseMode`-Eigenschaft wird auf einen Wert festgelegt, der für GCC geeignet ist. Weitere Informationen zu allen diesen Eigenschaften finden Sie unter [CppProperties.json-Referenz](cppproperties-schema-reference.md).

Wenn alles ordnungsgemäß funktioniert, wird IntelliSense in den GCC-Headern angezeigt, wenn Sie den Mauszeiger über einen Typ bewegen:

![GCC-IntelliSense](media/gcc-intellisense.png)

## <a name="enable-intellisense-diagnostics"></a>Aktivieren von IntelliSense-Diagnosen

Wenn IntelliSense nicht so angezeigt wird, wie Sie es erwarten, können Sie eine Problembehandlung durchführen, indem Sie auf **Extras** > **Optionen** > **Text-Editor** > **C/C++**  > **Erweitert** klicken und **Protokollierung aktivieren** auf **`true`** festlegen. Versuchen Sie für den Beginn, den **Protokolliergrad** auf 5 festzulegen und die **Protokollierungsfilter** auf 8.

![Diagnoseprotokollierung](media/diagnostic-logging.png)

Die Ausgabe wird an das **Ausgabefenster** weitergeleitet und ist sichtbar, wenn Sie die Option **Ausgabe anzeigen von: Visual C++-Protokoll* auswählen. Die Ausgabe enthält u. a. die Liste der tatsächlichen Includepfade, die IntelliSense versucht zu verwenden. Wenn die Pfade nicht mit denen in der Datei *CppProperties.json* übereinstimmen, versuchen Sie, den Ordner zu schließen und den *VS*-Unterordner zu löschen, der die zwischengespeicherten Browserdaten enthält.

### <a name="define-build-tasks-with-tasksvsjson"></a>Definieren von Buildtasks mit „tasks.vs.json“

Sie können Buildskripts oder andere externe Vorgänge in den Dateien automatisieren, die sich in Ihrem aktuellen Arbeitsbereich befinden, indem Sie sie direkt in der IDE als Tasks ausführen. Sie können einen neuen Task konfigurieren, indem Sie mit der rechten Maustaste auf eine Datei oder einen Ordner klicken und **Tasks konfigurieren** auswählen.

![Konfigurieren von Tasks für „Ordner öffnen“](media/configure-tasks.png)

Dadurch wird die *tasks.vs.json*-Datei im VS-Ordner erstellt (oder geöffnet), den Visual Studio im Stammordner des Projekts erstellt. Sie können in dieser Datei einen beliebigen Task definieren und diesen dann über das Kontextmenü des **Projektmappen-Explorers** aufrufen. Wenn das GCC-Beispiel fortgesetzt werden soll, zeigt der folgende Codeausschnitt eine vollständige *tasks.vs.json*-Datei mit einer einzelnen Aufgabe, die *g++.exe* aufruft, um ein Projekt zu erstellen. Nehmen Sie an, das Projekt enthält eine einzelne Datei namens *hello.cpp*.

```json
{
  "version": "0.2.1",
  "tasks": [
    {
      "taskLabel": "build hello",
      "appliesTo": "/",
      "type": "default",
      "command": "g++",
      "args": [
        "-g",
        "-o",
        "hello",
        "hello.cpp"
      ]
    }
  ]
}

```

Die JSON-Datei wird in den *VS*-Unterordner platziert. Wenn dieser Ordner angezeigt werden soll, klicken Sie auf die Schaltfläche **Alle Dateien anzeigen** oben im **Projektmappen-Explorer**. Sie können diese Aufgabe ausführen, indem Sie mit der rechten Maustaste auf den Stammknoten im **Projektmappen-Explorer** klicken und **build hello** auswählen. Wenn die Aufgabe abgeschlossen ist, sollte im **Projektmappen-Explorer** eine neue Datei angezeigt werden: *hello.exe*.

Sie können viele Arten von Aufgaben definieren. Das folgende Beispiel zeigt eine *tasks.vs.json-Datei*, die eine einzelne Aufgabe definiert. `taskLabel` definiert den Namen, der im Kontextmenü angezeigt wird. `appliesTo` definiert, für welche Dateien der Befehl ausgeführt werden kann. Die `command`-Eigenschaft bezieht sich auf die Umgebungsvariable COMSPEC, die den Pfad für die Konsole (*cmd.exe* unter Windows) identifiziert. Sie können ebenfalls auf Umgebungsvariablen verweisen, die in „CppProperties.json“ oder „CMakeSettings.json“ definiert sind. Die `args`-Eigenschaft gibt die Befehlszeile an, die aufgerufen werden soll. Das `${file}`-Makro ruft die ausgewählte Datei im **Projektmappen-Explorer** ab. Im folgenden Beispiel wird der Dateiname der aktuell ausgewählten CPP-Datei angezeigt.

```json
{
  "version": "0.2.1",
  "tasks": [
    {
      "taskLabel": "Echo filename",
      "appliesTo": "*.cpp",
      "type": "command",
      "command": "${env.COMSPEC}",
      "args": ["echo ${file}"]
    }
  ]
}
```

Wenn Sie *tasks.vs.json* gespeichert haben, können Sie mit der rechten Maustaste auf eine beliebige *CPP*-Datei im Ordner klicken und im Kontextmenü **Echo filename** auswählen. Anschließend wird der Dateiname im Ausgabefenster angezeigt.

Weitere Informationen finden Sie unter [Tasks.vs.json schema reference (Tasks.vs.json-Schemareferenz)](tasks-vs-json-schema-reference-cpp.md).

### <a name="configure-debugging-parameters-with-launchvsjson"></a>Konfigurieren von Parametern für das Debuggen mithilfe von „launch.vs.json“

Wenn Sie die Befehlszeilenargumente Ihres Programms und die Debuganweisungen anpassen möchten, klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf die ausführbare Datei, und wählen Sie **Debug- und Starteinstellungen** aus. Dadurch wird eine vorhandene *launch.vs.json*-Datei geöffnet, oder, falls keine vorhanden ist, wird eine neue Datei mit minimal erforderlichen Starteinstellungen erstellt. Zunächst können Sie auswählen, welche Art von Debugsitzung Sie konfigurieren möchten. Wenn Sie ein MinGw-w64-Projekt debuggen möchten, wählen Sie **C/C++ Launch for MinGW/Cygwin (gdb)** aus. Dadurch wird eine Startkonfiguration erstellt, bei der *gdb.exe* mit einigen fundierten Vermutungen zu Standardwerten verwendet werden kann. Einer dieser Standardwerte ist `MINGW_PREFIX`. Sie können den Literalpfad wie unten gezeigt ersetzen, oder Sie definieren eine `MINGW_PREFIX`-Eigenschaft in *CppProperties.json*:

```json
{
  "version": "0.2.1",
  "defaults": {},
  "configurations": [
    {
      "type": "cppdbg",
      "name": "hello.exe",
      "project": "hello.exe",
      "cwd": "${workspaceRoot}",
      "program": "${debugInfo.target}",
      "MIMode": "gdb",
      "miDebuggerPath": "c:\\msys64\\usr\\bin\\gdb.exe",
      "externalConsole": true
    }
  ]
}

```

Wählen Sie die ausführbare Datei im Debugdropdown aus, und klicken Sie dann auf den grünen Pfeil, um das Debuggen zu beginnen:

![Starten des Debuggers](media/launch-debugger-gdb.png)

Das Dialogfeld **Initializing Debugger** (Debugger wird initialisiert) sollte angezeigt werden und danach ein externes Konsolenfenster, in dem Ihr Programm ausgeführt wird.

Weitere Informationen finden Sie unter [Tasks.vs.json-Schemareferenz (C++)](launch-vs-schema-reference-cpp.md).

## <a name="launching-other-executables"></a>Starten anderer ausführbarer Dateien

Sie können Starteinstellungen für jede ausführbare Datei auf Ihrem Computer definieren. Im folgenden Beispiel wird *7za* gestartet und weitere Argumente angegeben, indem sie dem `args`-JSON-Array hinzugefügt werden:

```json
{
  "version": "0.2.1",
  "defaults": {},
  "configurations": [
    {
      "type": "default",
      "project": "CPP\\7zip\\Bundles\\Alone\\O\\7za.exe",
      "name": "7za.exe list content of helloworld.zip",
      "args": [ "l", "d:\\sources\\helloworld.zip" ]
    }
  ]
}
```

Wenn Sie diese Datei speichern, wird die neue Konfiguration in der Dropdownliste der Debugziele angezeigt, und Sie können auf diese klicken, um den Debugger zu starten. Sie können beliebig viele Debugkonfigurationen für beliebig viele ausführbare Dateien erstellen. Wenn Sie nun auf **F5** drücken, wird der Debugger gestartet. Dieser hält an jedem Breakpoint an, den Sie bereits festgelegt haben. Die bekannten Debuggerfenster und deren Funktionalitäten sind nun verfügbar.

::: moniker-end
