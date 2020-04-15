---
title: „Ordner öffnen“-Unterstützung für C++-Buildsysteme in Visual Studio
ms.date: 12/02/2019
helpviewer_keywords:
- Open Folder Projects in Visual Studio
ms.assetid: abd1985e-3717-4338-9e80-869db5435175
ms.openlocfilehash: 9264aa4bf77de406bdde9042ef9ec4251763f721
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320962"
---
# <a name="open-folder-support-for-c-build-systems-in-visual-studio"></a>„Ordner öffnen“-Unterstützung für C++-Buildsysteme in Visual Studio

::: moniker range="vs-2015"

Die Funktion Ordner öffnen ist in Visual Studio 2017 und höher verfügbar.

::: moniker-end

::: moniker range=">=vs-2017"

In Visual Studio 2017 und höher können Sie das Feature „Ordner öffnen“ verwenden, um einen Ordner mit Quelldateien öffnen und sofort mit dem Programmieren beginnen zu können. Dabei wird unter anderem IntelliSense, das Durchsuchen, Refactoring und Debuggen unterstützt. Während Sie Dateien bearbeiten, erstellen, verschieben und löschen, verfolgt Visual Studio die Änderungen automatisch nach und aktualisiert den IntelliSense-Index kontinuierlich. Es werden keine SLN- oder VCXPROJ-Dateien geladen. Bei Bedarf können Sie benutzerdefinierte Tasks sowie Build- und Startparameter über einfache JSON-Dateien angeben. Mit dieser Funktion können Sie jedes Buildsystem von Drittanbietern in Visual Studio integrieren. Allgemeine Informationen zu „Ordner öffnen“ finden Sie unter [Entwickeln von Code in Visual Studio ohne Projekte oder Projektmappen](/visualstudio/ide/develop-code-in-visual-studio-without-projects-or-solutions).

## <a name="cmake-and-qt"></a>CMake und Qt

CMake ist als Komponente der C++-Desktop-Workload in die Visual Studio-IDE integriert. Der Workflow für CMake ist nicht identisch mit dem in diesem Artikel beschriebenen Workflow. Wenn Sie CMake verwenden, finden Sie weitere Informationen unter [CMake-Projekte in Visual Studio](cmake-projects-in-visual-studio.md). Sie können CMake auch zum Erstellen von Qt-Projekten oder die [Qt Visual Studio-Erweiterung](https://download.qt.io/development_releases/vsaddin/) für Visual Studio 2015 oder Visual Studio 2017 verwenden.

## <a name="other-build-systems"></a>Andere Buildsysteme

Um die Visual Studio-IDE mit einem Buildsystem oder Compiler-Toolset zu verwenden, das nicht direkt aus dem Hauptmenü unterstützt wird, wählen Sie **Datei | Öffnen | Ordner** oder drücken **Sie Strg + Umschalt + Alt + O**. Navigieren Sie zu dem Ordner, der Ihre Quellcodedateien enthält. Um das Projekt zu erstellen, IntelliSense zu konfigurieren und Debugparameter festzulegen, fügen Sie drei JSON-Dateien hinzu:

| | |
|-|-|
|CppProperties.json|Geben Sie benutzerdefinierte Konfigurationsinformationen für das Durchsuchen an. Erstellen Sie diese Datei bei Bedarf im Stammordner des Projekts. (Wird in CMake-Projekten nicht verwendet.)|
|tasks.vs.json|Geben Sie benutzerdefinierte Buildbefehle an. Der Zugriff erfolgt über das Kontextmenüelement **Tasks konfigurieren** im **Projektmappen-Explorer**.|
|launch.vs.json|Geben Sie Befehlszeilenargumente für den Debugger an. Der Zugriff erfolgt über das Kontextmenüelement **Einstellungen für Debuggen und Starten** im **Projektmappen-Explorer**.|

## <a name="configure-code-navigation-with-cpppropertiesjson"></a>Konfigurieren der Codenavigation mit CppProperties.json

Damit IntelliSense und Das Browsingverhalten wie **"Zur Definition"** ordnungsgemäß funktionieren, muss Visual Studio wissen, welchen Compiler Sie verwenden, wo sich die Systemheader befinden und wo sich zusätzliche Includedateien befinden, wenn sie sich nicht direkt in dem Ordner befinden, den Sie geöffnet haben (den Arbeitsbereichsordner). Um eine Konfiguration anzugeben, können Sie in der Dropdownliste in der Hauptsymbolleiste die Option **Konfigurationen verwalten** auswählen:

![Dropdown-Liste von Konfigurationen verwalten](media/manage-configurations-dropdown.png)

Visual Studio bietet die folgenden Standardkonfigurationen:

![Standardkonfigurationen](media/default-configurations.png)

Wenn Sie z. B. **x64-Debug**auswählen, erstellt Visual Studio eine Datei mit dem Namen *CppProperties.json* in Ihrem Stammprojektordner:

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

Diese Konfiguration erbt die Umgebungsvariablen der Visual Studio [x64 Developer Command Prompt](building-on-the-command-line.md). Eine dieser Variablen `INCLUDE` ist und Sie können hier `${env.INCLUDE}` mit dem Makro darauf verweisen. Die `includePath` Eigenschaft teilt Visual Studio mit, wo sie nach allen Quellen suchen soll, die sie für IntelliSense benötigt. In diesem Fall heißt es: "Schauen Sie sich alle Verzeichnisse an, die von der Include-Umgebungsvariablen angegeben wurden, sowie in allen Verzeichnissen in der aktuellen Arbeitsordnerstruktur." Die `name` Eigenschaft ist der Name, der in der Dropdownliste angezeigt wird, und kann alles sein, was Sie mögen. Die `defines` Eigenschaft stellt Hinweise für IntelliSense bereit, wenn sie auf bedingte Kompilierungsblöcke trifft. Die `intelliSenseMode` Eigenschaft stellt einige zusätzliche Hinweise basierend auf dem Compilertyp bereit. Für MSVC, GCC und Clang stehen mehrere Optionen zur Verfügung.

> [!NOTE]
> Wenn Visual Studio Einstellungen in *CppProperties.json*zu ignorieren scheint, versuchen Sie, Ihrer `!/CppProperties.json` *.gitignore-Datei* eine Ausnahme wie folgt hinzuzufügen: .

## <a name="default-configuration-for-mingw-w64"></a>Standardkonfiguration für MinGW-w64

Wenn Sie die MinGW-W64-Konfiguration hinzufügen, sieht das JSON wie folgt aus:

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

Beachten `environments` Sie den Block. Es definiert Eigenschaften, die sich wie Umgebungsvariablen verhalten und nicht nur in der Datei *CppProperties.json,* sondern auch in den anderen Konfigurationsdateien *task.vs.json* und *launch.vs.json*verfügbar sind. Die `Mingw64` Konfiguration erbt `mingw_w64` die Umgebung `INCLUDE` und verwendet ihre `includePath`Eigenschaft, um den Wert für anzugeben. Sie können dieser Arrayeigenschaft bei Bedarf weitere Pfade hinzufügen."

Die `intelliSenseMode` Eigenschaft wird auf einen Wert festgelegt, der für GCC geeignet ist. Weitere Informationen zu all diesen Eigenschaften finden Sie unter [CppProperties-Schemareferenz](cppproperties-schema-reference.md).

Wenn alles ordnungsgemäß funktioniert, sehen Sie IntelliSense aus den GCC-Headern, wenn Sie den Mauszeiger über einen Typ bewegen:

![GCC IntelliSense](media/gcc-intellisense.png)

## <a name="enable-intellisense-diagnostics"></a>IntelliSense-Diagnose aktivieren

Wenn sie den erwarteten IntelliSense nicht sehen, können Sie die Problembehandlung beheben, indem Sie zu **Tools** > **Options** > **Text Editor** > **C/C++** > **Advanced** gehen und die **Option Protokollierung** **auf true**aktivieren festlegen. Versuchen Sie zunächst, **die Protokollierungsebene** auf 5 und die **Protokollierungsfilter** auf 8 festzulegen.

![Diagnoseprotokollierung](media/diagnostic-logging.png)

Die Ausgabe wird an das **Ausgabefenster** gepipetiert und ist sichtbar, wenn Sie **Ausgabe anzeigen von: Visual C++ Log auswählen.* Die Ausgabe enthält unter anderem die Liste der tatsächlichen Includepfade, die IntelliSense zu verwenden versucht. Wenn die Pfade nicht mit denen in *CppProperties.json*übereinstimmen, versuchen Sie, den Ordner zu schließen und den *Unterordner .vs* zu löschen, der zwischengespeicherte Browserdaten enthält.

### <a name="define-build-tasks-with-tasksvsjson"></a>Definieren von Buildtasks mit „tasks.vs.json“

Sie können Buildskripts oder andere externe Vorgänge in den Dateien automatisieren, die sich in Ihrem aktuellen Arbeitsbereich befinden, indem Sie sie direkt in der IDE als Tasks ausführen. Sie können einen neuen Task konfigurieren, indem Sie mit der rechten Maustaste auf eine Datei oder einen Ordner klicken und **Tasks konfigurieren** auswählen.

![Konfigurieren von Tasks für „Ordner öffnen“](media/configure-tasks.png)

Dadurch wird die *Datei tasks.vs.json* in dem .vs-Ordner erstellt (oder geöffnet), den Visual Studio in Ihrem Stammprojektordner erstellt. Sie können in dieser Datei einen beliebigen Task definieren und diesen dann über das Kontextmenü des **Projektmappen-Explorers** aufrufen. Um das GCC-Beispiel fortzusetzen, zeigt der folgende Ausschnitt eine vollständige *tasks.vs.json-Datei* mit einer einzigen Aufgabe an, die *g++.exe* aufruft, um ein Projekt zu erstellen. Angenommen, das Projekt enthält eine einzelne Datei namens *hello.cpp*.

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

Die JSON-Datei wird im *Unterordner .vs* abgelegt. Um diesen Ordner anzuzeigen, klicken Sie oben im **Projektmappen-Explorer**auf die Schaltfläche **Alle Dateien anzeigen** . Sie können diese Aufgabe ausführen, indem Sie mit der rechten Maustaste auf den Stammknoten im **Projektmappen-Explorer** klicken und **Build hello**auswählen. Wenn die Aufgabe abgeschlossen ist, sollte eine neue Datei angezeigt werden, *hello.exe* im **Projektmappen-Explorer**.

Sie können viele Arten von Aufgaben definieren. Das folgende Beispiel zeigt eine *tasks.vs.json-Datei,* die eine einzelne Aufgabe definiert. `taskLabel` definiert den Namen, der im Kontextmenü angezeigt wird. `appliesTo` definiert, für welche Dateien der Befehl ausgeführt werden kann. Die `command` Eigenschaft bezieht sich auf die COMSPEC-Umgebungsvariable, die den Pfad für die Konsole (*cmd.exe* unter Windows) identifiziert. Sie können ebenfalls auf Umgebungsvariablen verweisen, die in „CppProperties.json“ oder „CMakeSettings.json“ definiert sind. Die `args`-Eigenschaft gibt die Befehlszeile an, die aufgerufen werden soll. Das `${file}`-Makro ruft die ausgewählte Datei im **Projektmappen-Explorer** ab. Im folgenden Beispiel wird der Dateiname der aktuell ausgewählten CPP-Datei angezeigt.

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

Nach dem Speichern *von tasks.vs.json*können Sie mit der rechten Maustaste auf eine *beliebige CPP-Datei* im Ordner klicken, im Kontextmenü die Option **Echo-Dateiname** auswählen und den Dateinamen im Ausgabefenster anzeigen.

Weitere Informationen finden Sie unter [Tasks.vs.json schema reference (Tasks.vs.json-Schemareferenz)](tasks-vs-json-schema-reference-cpp.md).

### <a name="configure-debugging-parameters-with-launchvsjson"></a>Konfigurieren von Parametern für das Debuggen mithilfe von „launch.vs.json“

Um die Befehlszeilenargumente und Debuganweisungen Ihres Programms anzupassen, klicken Sie mit der rechten Maustaste auf die ausführbare Datei im **Projektmappen-Explorer,** und wählen Sie **Debug- und Starteinstellungen**aus. Dadurch wird eine vorhandene *launch.vs.json-Datei* geöffnet, oder wenn keine vorhanden ist, wird eine neue Datei mit einer Reihe von minimalen Starteinstellungen erstellt. Zuerst haben Sie die Wahl, welche Art von Debugsitzung Sie konfigurieren möchten. Zum Debuggen eines MinGw-w64-Projekts wählen wir **C/C++ Launch für MinGW/Cygwin (gdb)**. Dadurch wird eine Startkonfiguration für die Verwendung von *gdb.exe* mit einigen fundierten Vermutungen über Standardwerte erstellt. Einer dieser Standardwerte `MINGW_PREFIX`ist . Sie können den Literalpfad ersetzen (wie unten `MINGW_PREFIX` gezeigt) oder Sie können eine Eigenschaft in *CppProperties.json*definieren:

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

Um mit dem Debuggen zu beginnen, wählen Sie die ausführbare Datei in der Dropdown-Liste des Debuggens aus, und klicken Sie dann auf den grünen Pfeil:

![Debugger starten](media/launch-debugger-gdb.png)

Es sollte das Dialogfeld Initialisieren des **Debuggers** und dann ein externes Konsolenfenster angezeigt werden, in dem das Programm ausgeführt wird.

Weitere Informationen finden Sie unter [launch.vs.json-Schemareferenz](launch-vs-schema-reference-cpp.md).

## <a name="launching-other-executables"></a>Starten anderer ausführbarer Dateien

Sie können Starteinstellungen für jede ausführbare Datei auf Ihrem Computer definieren. Im folgenden Beispiel wird *7za* gestartet und zusätzliche Argumente `args` angegeben, indem sie dem JSON-Array hinzugefügt werden:

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
