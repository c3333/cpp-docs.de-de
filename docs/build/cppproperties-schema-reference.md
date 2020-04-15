---
title: CppProperties.json-Referenz
ms.date: 08/09/2019
helpviewer_keywords:
- CppProperties.json file [C++]
ms.openlocfilehash: be6db52e1e62244e9f44db8ac86238242ab50ca0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328717"
---
# <a name="cpppropertiesjson-reference"></a>CppProperties.json-Referenz

Open Folder-Projekte, die CMake nicht verwenden, können Projektkonfigurationseinstellungen für IntelliSense in einer *CppProperties.json-Datei* speichern. (CMake-Projekte verwenden eine [CMakeSettings.json-Datei.)](customize-cmake-settings.md) Eine Konfiguration besteht aus Namen/Wert-Paaren und definiert #include Pfade, Compiler-Switches und andere Parameter. Weitere Informationen zum Hinzufügen von Konfigurationen in einem Projekt für offene Ordner finden Sie unter [Open Folder-Projekte für C++.](open-folder-projects-cpp.md) In den folgenden Abschnitten werden die verschiedenen Einstellungen zusammengefasst. Navigieren Sie zu *CppProperties_schema.json*, dessen vollständiger Pfad oben im Codeeditor angegeben wird, wenn *CppProperties.json* geöffnet ist.

## <a name="configuration-properties"></a>Konfigurationseigenschaften

Eine Konfiguration kann folgende Eigenschaften aufweisen:

|||
|-|-|
|`inheritEnvironments`| Gibt an, welche Umgebungen für diese Konfiguration gelten.|
|`name`|Der Konfigurationsname, der in der Dropdown-Liste der C++-Konfiguration angezeigt wird|
|`includePath`|Eine durch Kommas getrennte Liste von Ordnern, die im Include-Pfad angegeben werden sollen (Zuordnungen zu /I für die meisten Compiler)|
|`defines`|Die Liste der Makros, die definiert sein sollten (entspricht bei den meisten Compilern /D)|
|`compilerSwitches`|Eine oder mehrere zusätzliche Optionen, die das Verhalten von IntelliSense beeinflussen können|
|`forcedInclude`|Ein Header, der automatisch in jede Kompilierungseinheit eingefügt wird (entspricht /FI bei MSVC oder -include bei Clang)|
|`undefines`|Die Liste der Makros, die nicht definiert sind (entspricht /U bei MSVC)|
|`intelliSenseMode`|Die zu verwendende IntelliSense-Engine Sie können eine der vordefinierten architekturspezifischen Varianten für MSVC, gcc oder Clang angeben.|
|`environments`|Benutzerdefinierte Sätze von Variablen, die sich wie Umgebungsvariablen in einer Eingabeaufforderung\< verhalten und auf die mit dem Befehlsaufforderung zugegriffen wird. VARIABLE>-Makro.|

### <a name="intellisensemode-values"></a>intelliSenseMode-Werte

Der Code-Editor zeigt die verfügbaren Optionen an, wenn Sie mit der Eingabe beginnen:

![Öffnen von Ordner IntelliSense](media/open-folder-intellisense-mode.png "Öffnen von Ordner IntelliSense")

Dies sind die unterstützten Werte:

- windows-msvc-x86
- windows-msvc-x64
- windows-msvc-arm
- windows-msvc-arm64
- android-clang-x86
- android-clang-x64
- android-clang-arm
- android-clang-arm64
- ios-clang-x86
- ios-clang-x64
- ios-clang-arm
- ios-clang-arm64
- windows-clang-x86
- windows-clang-x64
- windows-clang-arm
- windows-clang-arm64
- linux-gcc-x86
- linux-gcc-x64
- linux-gcc-arm

Hinweis: Die `msvc-x86` `msvc-x64` Werte werden nur aus Älterengründen unterstützt. Verwenden `windows-msvc-*` Sie stattdessen die Varianten.

## <a name="pre-defined-environments"></a>Vordefinierte Umgebungen

Visual Studio stellt die folgenden vordefinierten Umgebungen für Microsoft C++ bereit, die der entsprechenden Entwicklereingabeaufforderung zugeordnet sind. Wenn Sie eine dieser Umgebungen erben, können Sie auf eine der Umgebungsvariablen verweisen, indem Sie die globale Eigenschaft `env` mit dieser Makrosyntax verwenden:\< VARIABLE>.

|Variablenname|BESCHREIBUNG|
|-----------|-----------------|
|vsdev|Die Standardumgebung von Visual Studio|
|msvc_x86|Kompiliert mithilfe von x86-Tools für x86|
|msvc_x64|Kompiliert mithilfe von 64-Bit-Tools für AMD64|
|msvc_arm|Kompiliert mithilfe von x86-Tools für ARM|
|msvc_arm64|Kompiliert mithilfe von x86-Tools für ARM64|
|msvc_x86_x64|Kompiliert mithilfe von x86-Tools für AMD64|
|msvc_arm_x64|Kompiliert mithilfe von 64-Bit-Tools für ARM|
|msvc_arm64_x64|Kompiliert mithilfe von 64-Bit-Tools für ARM64|

Wenn die Linux-Workload installiert ist, können folgende Umgebungen verwendet werden, um Linux und WSL remote anzuzielen:

|Variablenname|BESCHREIBUNG|
|-----------|-----------------|
|linux_x86|Hiermit wird x86 Linux als Remotezielversion festgelegt.|
|linux_x64|Hiermit wird x64 Linux als Remotezielversion festgelegt.|
|linux_arm|Hiermit wird ARM Linux als Remotezielversion festgelegt.|

## <a name="user-defined-environments"></a><a name="user_defined_environments"></a>Benutzerdefinierte Umgebungen

Sie können die `environments` Eigenschaft optional verwenden, um Variablensätze in *CppProperties.json* entweder global oder pro Konfiguration zu definieren. Diese Variablen verhalten sich wie Umgebungsvariablen im Kontext eines Open Folder-Projekts\< und können mit dem Projekt .env aufgerufen werden. VARIABLE>-Syntax von *tasks.vs.json* und *launch.vs.json,* nachdem sie hier definiert wurden. Sie werden jedoch nicht unbedingt als tatsächliche Umgebungsvariablen in jeder Eingabeaufforderung festgelegt, die Visual Studio intern verwendet.

**Visual Studio 2019 Version 16.4 und höher:** Konfigurationsspezifische Variablen, die in *CppProperties.json* definiert sind, werden automatisch `inheritEnvironments`von Debugzielen und -aufgaben erfasst, ohne dass festgelegt werden muss. Debugziele werden automatisch mit der Umgebung gestartet, die Sie in *CppProperties.json*angeben.

**Visual Studio 2019 Version 16.3 und früher:** Wenn Sie eine Umgebung verwenden, müssen Sie `inheritsEnvironments` sie in der Eigenschaft angeben, auch wenn die Umgebung als Teil derselben Konfiguration definiert ist. Die `environment` Eigenschaft gibt den Namen der Umgebung an. Das folgende Beispiel zeigt eine Beispielkonfiguration zum Aktivieren von IntelliSense für GCC in einer MSYS2-Installation. Beachten Sie, wie die Konfiguration die `mingw_64` Umgebung definiert `includePath` und erbt `INCLUDE` und wie die Eigenschaft auf die Variable zugreifen kann.

```json
"configurations": [
    {

      "inheritEnvironments": [
        "mingw_64"
      ],
      "name": "Mingw64",
      "includePath ,": [
        "${env.INCLUDE}",
        "${workspaceRoot}\\**",
      ],
      "intelliSenseMode": "linux-gcc-x64",
      "environments": [
        {
          "MINGW64_ROOT": "C:\\msys64\\mingw64",
          "BIN_ROOT": "${env.MINGW64_ROOT}\\bin",
          "FLAVOR": "x86_64-w64-mingw32",
          "TOOLSET_VERSION": "9.1.0",
          "PATH": "${env.MINGW64_ROOT}\\bin;${env.MINGW64_ROOT}\\..\\usr\\local\\bin;${env.MINGW64_ROOT}\\..\\usr\\bin;${env.MINGW64_ROOT}\\..\\bin;${env.PATH}",
          "INCLUDE": "${env.MINGW64_ROOT}\\include\\c++\\${env.TOOLSET_VERSION};${env.MINGW64_ROOT}\\include\\c++\\${env.TOOLSET_VERSION}\\tr1;${env.MINGW64_ROOT}\\include\\c++\\${env.TOOLSET_VERSION}\\${env.FLAVOR};",
          "environment": "mingw_64"
        }
      ]
    }
  ]
```

Wenn Sie eine **Environments-Eigenschaft** innerhalb einer Konfiguration definieren, werden alle globalen Variablen mit demselben Namen überschrieben.

## <a name="built-in-macros"></a>Integrierte Makros

Sie haben Zugriff auf die folgenden integrierten Makros in *CppProperties.json:*

|||
|-|-|
|`${workspaceRoot}`| Der vollständige Pfad zum Arbeitsbereichsordner|
|`${projectRoot}`| Der vollständige Pfad zu dem Ordner, in dem *CppProperties.json* platziert wird|
|`${env.vsInstallDir}`| Der vollständige Pfad zu dem Ordner, in dem die ausgeführte Instanz von Visual Studio installiert ist|

### <a name="example"></a>Beispiel

Wenn Ihr Projekt über einen Include-Ordner verfügt und auch *windows.h* und andere allgemeine Header aus dem Windows SDK enthält, sollten Sie Ihre *CppProperties.json-Konfigurationsdatei* mit den folgenden Optionen aktualisieren:

```json
{
  "configurations": [
    {
      "name": "Windows",
      "includePath": [
        // local include folder
        "${workspaceRoot}\include",
        // Windows SDK and CRT headers
        "${env.WindowsSdkDir}\include\${env.WindowsSDKVersion}\ucrt",
        "${env.NETFXSDKDir}\include\um",
        "${env.WindowsSdkDir}\include\${env.WindowsSDKVersion}\um",
        "${env.WindowsSdkDir}\include\${env.WindowsSDKVersion}\shared",
        "${env.VCToolsInstallDir}\include"
      ]
    }
  ]
}
```

> [!Note]
> `%WindowsSdkDir%`und `%VCToolsInstallDir%` werden nicht als globale Umgebungsvariablen festgelegt, um sicherzustellen, dass „devenv.exe“ über eine Developer-Eingabeaufforderung ausgeführt wird, die diese Variablen definiert. (Geben Sie "developer" im Windows-Startmenü ein.)

## <a name="troubleshoot-intellisense-errors"></a>Problembehandlung für IntelliSense-Fehler

Wenn sie den erwarteten IntelliSense nicht sehen, können Sie die Problembehandlung beheben, indem Sie zu **Tools** > **Options** > **Text Editor** > **C/C++** > **Advanced** gehen und die **Option Protokollierung** **auf true**aktivieren festlegen. Versuchen Sie zunächst, **die Protokollierungsebene** auf 5 und die **Protokollierungsfilter** auf 8 festzulegen.

![Diagnoseprotokollierung](media/diagnostic-logging.png)

Die Ausgabe wird an das **Ausgabefenster** gepipetiert und ist sichtbar, wenn Sie **Ausgabe anzeigen aus: Visual C++ Log**auswählen. Die Ausgabe enthält unter anderem die Liste der tatsächlichen Includepfade, die IntelliSense zu verwenden versucht. Wenn die Pfade nicht mit denen in *CppProperties.json*übereinstimmen, versuchen Sie, den Ordner zu schließen und den *Unterordner .vs* zu löschen, der zwischengespeicherte Browserdaten enthält.

Wenn Sie IntelliSense-Fehler beheben möchten, die von fehlenden Includepfaden verursacht wurden, öffnen Sie die **Fehlerliste**, und filtern Sie deren Ausgabe nach „Nur IntelliSense“ und dem Fehlercode E1696 „Die Datei ‚Dateiname‘ kann nicht geöffnet werden“.
