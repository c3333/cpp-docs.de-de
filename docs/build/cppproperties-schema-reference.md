---
title: Cppproperties. JSON-Referenz
ms.date: 08/09/2019
helpviewer_keywords:
- CppProperties.json file [C++]
ms.openlocfilehash: d59fca412a26d08f88ccbda20a2c0444cf33b1cb
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2020
ms.locfileid: "79422841"
---
# <a name="cpppropertiesjson-reference"></a>Cppproperties. JSON-Referenz

Wenn Ordner Projekte geöffnet werden, die cmake nicht verwenden, können Projekt Konfigurationseinstellungen für IntelliSense in einer *cppproperties. JSON* -Datei gespeichert werden. (Cmake-Projekte verwenden eine [cmakesettings. JSON](customize-cmake-settings.md) -Datei.) Eine Konfiguration besteht aus Name/Wert-Paaren und definiert #Include Pfade, compilerswitches und andere Parameter. Weitere Informationen zum Hinzufügen von Konfigurationen in einem geöffneten Ordner Projekt finden Sie unter [Open Folder Projects for C++ ](open-folder-projects-cpp.md) . In den folgenden Abschnitten werden die verschiedenen Einstellungen zusammengefasst. Um eine vollständige Beschreibung des Schemas zu erhalten, navigieren Sie zu " *CppProperties_schema. JSON*", dessen vollständiger Pfad oben im Code-Editor angezeigt wird, wenn " *cppproperties. JSON* " geöffnet ist.

## <a name="configuration-properties"></a>Konfigurationseigenschaften

Eine Konfiguration kann folgende Eigenschaften aufweisen:

|||
|-|-|
|`inheritEnvironments`| Gibt an, welche Umgebungen auf diese Konfiguration angewendet werden.|
|`name`|Der Konfigurations Name, der in der C++ Konfigurations-Dropdown Liste angezeigt wird.|
|`includePath`|Eine durch Trennzeichen getrennte Liste von Ordnern, die im Includepfad angegeben werden sollten (für die meisten Compiler/I zugeordnet).|
|`defines`|Die Liste der Makros, die definiert sein sollten (entspricht bei den meisten Compilern /D)|
|`compilerSwitches`|Eine oder mehrere zusätzliche Optionen, die das Verhalten von IntelliSense beeinflussen können|
|`forcedInclude`|Ein Header, der automatisch in jede Kompilierungseinheit eingefügt wird (entspricht /FI bei MSVC oder -include bei Clang)|
|`undefines`|Die Liste der Makros, die nicht definiert sind (entspricht /U bei MSVC)|
|`intelliSenseMode`|Die zu verwendende IntelliSense-Engine Sie können eine der vordefinierten architekturspezifischen Varianten für MSVC, gcc oder clang angeben.|
|`environments`|Benutzerdefinierte Variablen Sätze, die sich wie Umgebungsvariablen an einer Eingabeaufforderung Verhalten und auf die mit "$ {ERV.<VARIABLE>}" zugegriffen wird. Hilfen.|

### <a name="intellisensemode-values"></a>intellisensmode-Werte

Der Code-Editor zeigt die verfügbaren Optionen an, wenn Sie mit der typinstallation beginnen:

![IntelliSense für Ordner öffnen](media/open-folder-intellisense-mode.png "IntelliSense für Ordner öffnen")

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
- Linux-GCC-Arm

Hinweis: die Werte `msvc-x86` und `msvc-x64` werden nur aus Legacy Gründen unterstützt. Verwenden Sie stattdessen die `windows-msvc-*` Varianten.

## <a name="pre-defined-environments"></a>Vordefinierte Umgebungen

Visual Studio bietet die folgenden vordefinierten Umgebungen für Microsoft C++ , die dem entsprechenden Developer-Eingabeaufforderung zugeordnet sind. Wenn Sie eine dieser Umgebungen erben, können Sie auf jede Umgebungsvariable verweisen, indem Sie die globale Eigenschaften `env` mit der folgenden Makro Syntax verwenden: $ {env.\<Variable >}.

|Variablenname|Beschreibung|
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

|Variablenname|Beschreibung|
|-----------|-----------------|
|linux_x86|Hiermit wird x86 Linux als Remotezielversion festgelegt.|
|linux_x64|Hiermit wird x64 Linux als Remotezielversion festgelegt.|
|linux_arm|Hiermit wird ARM Linux als Remotezielversion festgelegt.|

## <a name="user_defined_environments"></a>Benutzerdefinierte Umgebungen

Optional können Sie die `environments`-Eigenschaft verwenden, um Variablen Sätze in *cppproperties. JSON* entweder global oder pro Konfiguration zu definieren. Diese Variablen verhalten sich wie Umgebungsvariablen im Kontext eines geöffneten Ordner Projekts. auf Sie kann mit der $ {ENV.\<Variable >}-Syntax aus " *Tasks. vs. JSON* " und " *Launch. vs. JSON* " zugegriffen werden, nachdem Sie hier definiert wurden. Allerdings werden Sie in einer Eingabeaufforderung, die Visual Studio intern verwendet, nicht notwendigerweise als tatsächliche Umgebungsvariablen festgelegt.

**Visual Studio 2019 Version 16,4 und höher:** Konfigurations spezifische Variablen, die in " *cppproperties. JSON* " definiert sind, werden automatisch durch debugziele und Aufgaben abgerufen, ohne dass `inheritEnvironments`festgelegt werden muss. Debugziele werden automatisch mit der Umgebung gestartet, die Sie in " *cppproperties. JSON*" angeben.

**Visual Studio 2019 Version 16,3 und früher:** Wenn Sie eine Umgebung nutzen, müssen Sie Sie in der `inheritsEnvironments`-Eigenschaft angeben, auch wenn die Umgebung als Teil derselben Konfiguration definiert ist. die `environment`-Eigenschaft gibt den Namen der Umgebung an. Das folgende Beispiel zeigt eine Beispielkonfiguration zum Aktivieren von IntelliSense für gcc in einer MSYS2-Installation. Beachten Sie, dass die Konfiguration sowohl die `mingw_64` Umgebung definiert als auch erbt und wie die `includePath`-Eigenschaft auf die `INCLUDE` Variable zugreifen kann.

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

Wenn Sie eine **Umgebungs** Eigenschaft innerhalb einer Konfiguration definieren, werden alle globalen Variablen mit demselben Namen überschrieben.

## <a name="built-in-macros"></a>Integrierte Makros

Sie haben Zugriff auf die folgenden integrierten Makros in " *cppproperties. JSON*":

|||
|-|-|
|`${workspaceRoot}`| Der vollständige Pfad zum Arbeitsbereichs Ordner.|
|`${projectRoot}`| Der vollständige Pfad zu dem Ordner, in dem " *cppproperties. JSON* " platziert wird.|
|`${env.vsInstallDir}`| Der vollständige Pfad zu dem Ordner, in dem die laufende Instanz von Visual Studio installiert ist.|

### <a name="example"></a>Beispiel

Wenn das Projekt über einen includeordner verfügt und auch *Windows. h* und andere gängige Header aus der Windows SDK enthält, sollten Sie die *cppproperties. JSON* -Konfigurationsdatei wie folgt aktualisieren:

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

Wenn die erwartete IntelliSense-Funktion nicht angezeigt wird, können Sie Probleme **beheben, indem** Sie zu Extras > **Optionen** > **Text-Editor** > **CC++ /**  > **erweitert** wechseln und **Protokollierung aktivieren** auf **wahr**festlegen. Legen Sie zunächst den **Protokolliergrad** auf 5 fest, und **Protokollieren** Sie die Filter auf 8.

![Diagnoseprotokollierung](media/diagnostic-logging.png)

Die Ausgabe wird an den **Ausgabefenster** weitergeleitet und ist sichtbar, wenn Sie **Ausgabe anzeigen von: C++ visuelles Protokoll**auswählen. Die Ausgabe enthält unter anderem die Liste der tatsächlichen Includepfade, die IntelliSense zu verwenden versucht. Wenn die Pfade nicht mit denen in " *cppproperties. JSON*" identisch sind, schließen Sie den Ordner, und löschen Sie den Unterordner " *. vs* ", der zwischengespeicherte Browserdaten enthält.

Wenn Sie IntelliSense-Fehler beheben möchten, die von fehlenden Includepfaden verursacht wurden, öffnen Sie die **Fehlerliste**, und filtern Sie deren Ausgabe nach „Nur IntelliSense“ und dem Fehlercode E1696 „Die Datei ‚Dateiname‘ kann nicht geöffnet werden“.
