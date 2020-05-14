---
title: CppProperties.json-Referenz
ms.date: 08/09/2019
helpviewer_keywords:
- CppProperties.json file [C++]
ms.openlocfilehash: be6db52e1e62244e9f44db8ac86238242ab50ca0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328717"
---
# <a name="cpppropertiesjson-reference"></a>CppProperties.json-Referenz

„Ordner öffnen“-Projekte, die CMake nicht verwenden, können Projektkonfigurationseinstellungen für IntelliSense in einer *CppProperties.json*-Datei speichern. (CMake-Projekte verwenden eine [CMakeSettings.json](customize-cmake-settings.md)-Datei.) Eine Konfiguration besteht aus Name/Wert-Paaren und definiert #include-Pfade, Compileroptionen und andere Parameter. Weitere Informationen zum Hinzufügen von Konfigurationen in einem „Ordner öffnen“-Projekt finden Sie unter [„Ordner öffnen“-Projekte für C++](open-folder-projects-cpp.md). In den folgenden Abschnitten werden die verschiedenen Einstellungen zusammengefasst. Navigieren Sie für eine vollständige Beschreibung des Schemas zu *CppProperties_schema.json*, wo am Anfang des Code-Editors der vollständige Pfad angezeigt wird, wenn die *CppProperties.json*-Datei geöffnet ist.

## <a name="configuration-properties"></a>Konfigurationseigenschaften

Eine Konfiguration kann folgende Eigenschaften aufweisen:

|||
|-|-|
|`inheritEnvironments`| Hiermit wird angegeben, für welche Umgebungen diese Konfiguration gilt.|
|`name`|Dies ist der Konfigurationsname, der im Dropdownmenü für die C++-Konfiguration angezeigt wird.|
|`includePath`|Dies ist die durch Trennzeichen getrennte Ordnerliste, die im Includepfad angegeben sein sollte (entspricht bei den meisten Compilern „/I“)|
|`defines`|Die Liste der Makros, die definiert sein sollten (entspricht bei den meisten Compilern /D)|
|`compilerSwitches`|Eine oder mehrere zusätzliche Optionen, die das Verhalten von IntelliSense beeinflussen können|
|`forcedInclude`|Ein Header, der automatisch in jede Kompilierungseinheit eingefügt wird (entspricht /FI bei MSVC oder -include bei Clang)|
|`undefines`|Die Liste der Makros, die nicht definiert sind (entspricht /U bei MSVC)|
|`intelliSenseMode`|Die zu verwendende IntelliSense-Engine Sie können eine der vordefinierten, architekturspezifischen Varianten für MSVC, GCC oder Clang angeben.|
|`environments`|Dies sind die benutzerdefinierten Variablen, die sich wie Umgebungsvariablen in einer Eingabeaufforderung verhalten und auf die über das Makro „${env.\<VARIABLE>}“ zugegriffen wird.|

### <a name="intellisensemode-values"></a>intelliSenseMode-Werte

Der Code-Editor zeigt die verfügbaren Optionen an, wenn Sie mit der Eingabe beginnen:

![IntelliSense: „Ordner öffnen“](media/open-folder-intellisense-mode.png "IntelliSense: „Ordner öffnen“")

Die folgenden Werte werden unterstützt:

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

Hinweis: Die Werte `msvc-x86` und `msvc-x64` werden nur aus Legacygründen unterstützt. Verwenden Sie stattdessen die `windows-msvc-*`-Varianten.

## <a name="pre-defined-environments"></a>Vordefinierte Umgebungen

Visual Studio bietet die folgenden vordefinierten Umgebungen für Microsoft C++, die der entsprechenden Developer-Eingabeaufforderung zugeordnet sind. Wenn Sie eine dieser Umgebungen erben, können Sie auf jede Umgebungsvariable verweisen, indem Sie die globale Eigenschaft `env` mit der folgenden Makrosyntax verwenden: ${env.\<VARIABLE>}.

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

## <a name="user-defined-environments"></a><a name="user_defined_environments"></a> Benutzerdefinierte Umgebungen

Optional können Sie die `environments`-Eigenschaft verwenden, um Variablen in *CppProperties.json* entweder global oder pro Konfiguration zu definieren. Diese Variablen verhalten sich wie Umgebungsvariablen im Kontext eines „Ordner öffnen“-Projekts. Auf diese kann über die ${env.\<VARIABLE>}-Syntax von *tasks.vs.json* und *launch.vs.json* nach deren Definition zugegriffen werden. Allerdings werden sie in einer Eingabeaufforderung, die Visual Studio intern verwendet, nicht notwendigerweise als tatsächliche Umgebungsvariablen festgelegt.

**Visual Studio 2019, Version 16.4 und höher:** Konfigurationsspezifische Variablen, die in *CppProperties.json* definiert sind, werden automatisch durch Debugziele und Aufgaben abgerufen, ohne dass `inheritEnvironments` festgelegt werden muss. Debugziele werden automatisch mit der von Ihnen in *CppProperties.json* angegebenen Umgebung gestartet.

**Visual Studio 2019, Version 16.3 und früher:** Wenn Sie eine Umgebung nutzen, müssen Sie diese in der `inheritsEnvironments`-Eigenschaft angeben, auch wenn die Umgebung als Teil derselben Konfiguration definiert ist. Die `environment`-Eigenschaft gibt den Namen der Umgebung an. Das folgende Beispiel zeigt eine Beispielkonfiguration zum Aktivieren von IntelliSense für GCC in einer MSYS2-Installation. Beachten Sie, dass die Konfiguration sowohl die `mingw_64`-Umgebung definiert als auch erbt und wie die `includePath`-Eigenschaft auf die `INCLUDE`-Variable zugreifen kann.

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

Wenn Sie eine **Umgebungseigenschaft** innerhalb einer Konfiguration definieren, werden alle globalen Variablen mit demselben Namen überschrieben.

## <a name="built-in-macros"></a>Integrierte Makros

Sie können auf die folgenden integrierten Makros innerhalb von *CppProperties.json* zugreifen:

|||
|-|-|
|`${workspaceRoot}`| den vollständigen Pfad zum Arbeitsbereichordner|
|`${projectRoot}`| den vollständigen Pfad zum Ordner von *CppProperties.json*|
|`${env.vsInstallDir}`| den vollständigen Pfad zum Ordner, in dem die ausgeführte Instanz von Visual Studio installiert ist|

### <a name="example"></a>Beispiel

Wenn in Ihrem Projekt ein Includeordner sowie *windows.h* und andere allgemeine Header des Windows SDK vorhanden sind, sollten Sie die Konfigurationsdatei *CppProperties.json* mit folgenden Includeelementen aktualisieren:

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

Wenn IntelliSense nicht so angezeigt wird, wie Sie es erwarten, können Sie ein Troubleshooting durchführen, indem Sie auf **Extras** > **Optionen** > **Text-Editor** > **C/C++**  > **Erweitert** klicken und **Protokollierung aktivieren** auf **True** festlegen. Versuchen Sie für den Beginn, den **Protokolliergrad** auf 5 und die **Protokollierungsfilter** auf 8 festzulegen.

![Diagnoseprotokollierung](media/diagnostic-logging.png)

Die Ausgabe wird an das **Ausgabefenster** weitergeleitet und ist sichtbar, wenn Sie auf die Option **Ausgabe anzeigen von: Visual C++-Protokoll** klicken. Die Ausgabe enthält u. a. die Liste der tatsächlichen Includepfade, die IntelliSense versucht zu verwenden. Wenn die Pfade nicht mit denen in der Datei *CppProperties.json* übereinstimmen, versuchen Sie, den Ordner zu schließen und den Unterordner *.vs* zu löschen, der die zwischengespeicherten Browserdaten enthält.

Wenn Sie IntelliSense-Fehler beheben möchten, die von fehlenden Includepfaden verursacht wurden, öffnen Sie die **Fehlerliste**, und filtern Sie deren Ausgabe nach „Nur IntelliSense“ und dem Fehlercode E1696 „Die Datei ‚Dateiname‘ kann nicht geöffnet werden“.
