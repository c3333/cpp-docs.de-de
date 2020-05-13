---
title: C++-Tools und -Features in Visual Studio-Editionen
ms.date: 05/21/2019
helpviewer_keywords:
- tools and platforms [C++]
ms.assetid: 3d88607b-9cc4-490a-8d4c-31ee7610a26f
ms.openlocfilehash: 88eb66440df023254cb806c03a00aa2d71980305
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366793"
---
# <a name="c-tools-and-features-in-visual-studio-editions"></a>C++-Tools und -Features in Visual Studio-Editionen

::: moniker range=">=vs-2019"

Die folgenden C++-Features stehen in Visual Studio 2019 zur Verfügung. Sofern nicht anders angegeben, sind alle Features in allen Editionen verfügbar: Visual Studio Community, Visual Studio Professional und Visual Studio Enterprise. Einige Features erfordern spezifische Workloads oder optionale Komponenten, die Sie mit dem Visual Studio-Installer installieren können.

## <a name="platforms"></a>Plattformen

- Windows-Desktop
- Universelle Windows-Plattform ((Tablet, PC, Xbox, IoT und HoloLens))
- Linux
- Android
- iOS

## <a name="compilers"></a>Compiler

- 32-Bit-MSVC-Compiler für x86, x64, ARM und ARM64
- 64-Bit-MSVC-Compiler für x86, x64, ARM und ARM64
- GCC-Cross-Compiler für ARM
- Clang/LLVM
  - Unter Windows: Clang/LLVM 7.0 für x86 oder x64 (gilt nur für CMake-Unterstützung). Andere Clang-Versionen können funktionieren, jedoch werden diese nicht offiziell unterstützt.
  - Unter Linux: beliebige von der Verteilung unterstützte Installation von Clang/LLVM.

## <a name="c-workloads"></a>C++-Workloads

Visual Studio enthält die folgenden Workloads für die C++-Entwicklung. Sie können eine beliebige von diesen und anderen Workloads installieren, z. B. .NET Desktopentwicklung, Python-Entwicklung, Azure-Entwicklung, Visual Studio-Extensionentwicklung und mehr.

### <a name="desktop-development-with-c"></a>Desktopentwicklung mit C++

Enthält:

- Wichtige C++-Desktopfeatures

Optionale Komponenten:

- MSVC v142 - VS 2019 C++ x64/x86-Buildtools (v14.21)
- Windows 10 SDK (10.0.17763.0)
- Just-In-Time-Debugger
- C++-Profilerstellungstools
- C++-CMake-Tools für Windows
- C++-ATL für v142-Buildtools (x86 & x64)
- Testadapter für Boost.Test
- Testadapter für Google Test
- Live Share
- IntelliCode
- IntelliTrace (nur Enterprise)
- C++ MFC für v142-Buildtools (x86 & x64)
- C++-/CLI-Unterstützung für v142-Buildtools (14.21)
- C++-Module für v142-Buildtools (x64/x86 – experimentell)
- Clang-Compiler für Windows
- IncrediBuild – Buildbeschleunigung
- Windows 10 SDK (10.0.17134.0)
- Windows 10 SDK (10.0.16299.0)
- MSVC v141 - VS 2017 C++ x64/x86-Buildtools (v14.16)
- MSVC v140 – VS 2015: C++-Buildtools (v14.00)

### <a name="linux-development-with-c"></a>Linux-Entwicklung mit C++

Enthält:

- C++-Kernfeatures
- Windows Universal C Runtime
- C++ für die Linux-Entwicklung

Optionale Komponenten:

- C++-CMake-Tools für Linux
- Embedded-Tools und Tools für die IoT-Entwicklung

### <a name="universal-windows-platform-development"></a>Entwicklung für die universelle Windows-Plattform

Enthält:

- Blend for Visual Studio
- .NET Native und .NET Standard
- NuGet-Paket-Manager
- UWP-Tools (Universelle Windows-Plattform)
- Windows 10 SDK (10.0.17763.0)

Optionale Komponenten:

- IntelliCode
- IntelliTrace (nur Enterprise)
- USB-Gerätekonnektivität
- UWP-Tools (Universelle Windows-Plattform) für C++ (v142)
- UWP-Tools (Universelle Windows-Plattform) für C++ (v141)
- Grafikdebugger und GPU-Profiler für DirectX
- Windows 10 SDK (10.0.18362.0)
- Windows 10 SDK (10.0.17134.0)
- Windows 10 SDK (10.0.16299.0)
- Architektur- und Analysetools

### <a name="c-game-development"></a>Spieleentwicklung mit C++

Enthält:

- C++-Kernfeatures
- Windows Universal C Runtime
- C++ 2019 Redistributable-Update
- MSVC v142 - VS 2019 C++ x64/x86-Buildtools (v14.21)

Optionale Komponenten:

- C++-Profilerstellungstools
- Windows 10 SDK (10.0.17763.0)
- IntelliCode
- IntelliTrace (nur Enterprise)
- Windows 10 SDK (10.0.17134.0)
- Windows 10 SDK (10.0.16299.0)
- IncrediBuild – Buildbeschleunigung
- Cocos
- Unreal Engine-Installer
- Unterstützung der Android-IDE für die Unreal-Engine

### <a name="mobile-development-with-c"></a>Mobile Entwicklung mit C++

Enthält:

- C++-Kernfeatures
- Android SDK-Setup (API-Ebene 25, lokale Installation für die Mobile-Entwicklung mit C++)

Optionale Komponenten:

- Android NDK (R16B)
- Apache Ant (1.9.3)
- C++ Android-Entwicklungstools
- IntelliCode
- Google Android-Emulator (API-Ebene 25) (lokale Installation)
- Intel Hardware Accelerated Execution Manager (HAXM), lokale Installation
- Android NDK (R16B) (32 Bit)
- C++ iOS-Entwicklungstools
- IncrediBuild – Buildbeschleunigung

## <a name="individual-components"></a>Screenshot: Einzelne Komponenten

Sie können diese Komponenten unabhängig von der Workload installieren.

- JavaScript-Diagnose
- Live Share
- C++-Runtime für die Universelle Windows-Plattform für v142-Buildtools
- ClickOnce-Veröffentlichung
- Microsoft Visual Studio Installer Projects

## <a name="libraries-and-headers"></a>Bibliotheken und Header

- Windows-Header und -Bibliotheken
- Windows Universal C-Runtime (CRT)
- C++-Standardbibliothek
- ATL
- MFC
- .NET Framework-Klassenbibliothek
- C++-Unterstützungsbibliothek für .NET
- OpenMP 2.0
- Über 900 Open-Source-Bibliotheken im vcpkg-Katalog

## <a name="build-and-project-systems"></a>Build- und Projektsysteme

- CMake
- Beliebiges Buildsystem per „Ordner öffnen“
- Befehlszeilenbuilds (msbuild.exe)
- Systemeigene Festlegung von Zielversionen
- Verwaltete Festlegung von Zielversionen
- Parallele Builds
- Buildanpassungen
- Erweiterbarkeit der Eigenschaftenseiten

## <a name="project-templates"></a>Projektvorlagen

Je nachdem, welche Workloads Sie installiert haben, sind die folgenden Projektvorlagen verfügbar.

Windows-Desktop:

- Leeres Projekt
- Konsolenanwendung
- Windows-Desktop-Assistenten
- Windows-Desktopanwendung
- Projekt mit freigegebenen Elementen
- MFC-App
- Dynamic Link Library (DLL)
- Leeres CLR-Projekt
- CLR-Konsolen-App
- Statische Bibliothek
- CMake-Projekt
- ATL-Projekt
- MFC-Dynamic Link Library (DLL)
- CLR-Klassenbibliothek
- Makefile-Projekt (Windows)
- MFC-ActiveXControl
- Testprojekt für systemeigene Komponente
- Google Test

Universelle Windows-Plattform (C++/CX):

- Leere App
- DirectX 11- und XAML-App
- DirectX 11-App
- DirectX 12-App
- Komponententest-App
- DLL
- Komponente für Windows-Runtime
- Statische Bibliothek
- Paketerstellungsprojekt für Windows-Anwendungen

Linux:

- Konsolenanwendung (Linux)
- Leeres Projekt (Linux)
- Raspberry Pi Blink
- Makefile-Projekt (Linux)

## <a name="tools"></a>Tools

- Incremental Linker (Link.exe)
- Microsoft Makefile-Hilfsprogramm (Nmake.exe)
- Lib-Generator (Lib.exe)
- Windows-Ressourcencompiler (Rc.exe)
- Windows Resource to Object Converter (CvtRes.exe)
- Browse Information Maintenance-Programm (BscMake.exe)
- C++ Name Undecorator (Undname.exe)
- COFF/PE-Dumper (Dumpbin.exe)
- COFF/PE-Editor (Editbin.exe)
- MASM (Ml.exe)
- Spy++
- ErrLook
- AtlTrace
- Rückschlussregeln
- Profilgesteuerte Optimierungen (PGO)

## <a name="debugging-features"></a>Debugfunktionen

- Systemeigenes Debuggen
- Natvis (Visualisierung des systemeigenen Typs)
- Grafikdebugging
- Verwaltetes Debuggen
- GPU-Nutzung
- Speicherauslastung
- Remote Debugging
- SQL-Debugging
- Statische Codeanalyse

## <a name="designers-and-editors"></a>Designer und Editoren

- XAML-Designer
- CSS-Format-Designer/Editor
- HTML-Designer/Editor
- XML-Editor
- Quellcode-Editor
- Features zur Steigerung der Produktivität: Refactoring, EDG-IntelliSense-Engine, C++-Codeformatierung
- Windows Forms-Designer
- Daten-Designer
- Systemeigener Ressourcen-Editor (RC-Dateien)
- Ressourcen-Editor
- Modell-Editor
- Shader-Designer
- Live-Abhängigkeitsüberprüfung (nur Enterprise)
- Architekturebenendiagramme (nur Enterprise)
- Architekturüberprüfung (nur Enterprise)
- Codeklon (nur Enterprise)

## <a name="data-features"></a>Datenfunktionen

- Daten-Designer
- Datenobjekte
- Webdienste
- Server-Explorer

## <a name="automation-and-extensibility"></a>Automatisierung und Erweiterbarkeit

- Erweiterbarkeitsobjektmodelle
- Codemodell
- Projektmodell
- Modell für den Ressourcen-Editor
- Assistentenmodell
- Debuggerobjektmodell

## <a name="application-lifecycle-management-tools"></a>Anwendungslebenszyklus-Verwaltungstools

- Unittests (Microsoft Native C++, Boost.Test, Google Test, CTest)
- Code Map und Abhängigkeitsdiagramme (Professional und Enterprise)
- Code Coverage (nur Enterprise)
- Manuelle Tests (nur Enterprise)
- Explorative Tests (nur Enterprise)
- Testfallverwaltung (nur Enterprise)
- Code Map-Debuggerintegration (nur Enterprise)
- Live Unit Testing (nur Enterprise)
- IntelliTrace (nur Enterprise)
- IntelliTest (nur Enterprise)
- Microsoft Fakes (Isolation von Komponententests) (nur Enterprise)
- Code Coverage (nur Enterprise)

## <a name="see-also"></a>Siehe auch

[Installieren von Visual Studio](/visualstudio/install/install-visual-studio)<br/>
[Neues in Visual Studio](/visualstudio/ide/whats-new-in-visual-studio)<br/>
[C++-Projektvorlagen](../build/reference/visual-cpp-project-types.md)

::: moniker-end

::: moniker range="<=vs-2017"

In den folgenden Tabellen werden Visual C++-Features aufgeführt, die in Visual Studio 2017 verfügbar sind. Ein „X“ in einer Zelle gibt an, dass die Funktion verfügbar ist. Eine leere Zelle gibt an, dass die Funktion nicht verfügbar ist. Hinweise in Klammern geben an, dass eine Funktion eingeschränkt verfügbar ist.

## <a name="platforms"></a>Plattformen

||||||
|-|-|-|-|-|
|Plattform|Visual Studio Express für Windows 10|Visual Studio Express für Windows Desktop|Visual Studio-Community/Professional|Visual Studio Enterprise|
|Windows-Desktop||X|X|X|
|Universelle Windows-Plattform ((Telefon, Tablet, PC, Xbox, IoT und HoloLens))|X||X|X|
|Linux|X|X|
|Microsoft Store 8.1|||X|X|
|Windows Phone 8.0|||X|X|
|Android|||X|X|
|iOS|||X|X|

## <a name="compilers"></a>Compiler

|Compiler|Visual Studio Express für Windows|Visual Studio Express für Windows Desktop|Visual Studio Professional / Community|Visual Studio Enterprise|
|--------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|32-Bit-MSVC-Compiler für x86|X|X|X|X|
|X86_arm-Cross-Compiler|X||X|X|
|64-Bit-MSVC-Compiler für x64|||X|X|
|x86_x64-Cross-Compiler|X|X|X|X|

## <a name="libraries-and-headers"></a>Bibliotheken und Header

|Bibliothek oder Header|Visual Studio Express für Windows|Visual Studio Express für Windows Desktop|Visual Studio Professional / Community|Visual Studio Enterprise|
|-----------------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|Windows-Header und Bibliotheken und CRT-Bibliothek|(X)|X|X|X|
|C++-Standardbibliothek|X|X|X|X|
|ATL|||X|X|
|MFC|||X|X|
|.NET Framework-Klassenbibliothek||X|X|X|
|C++-Unterstützungsbibliothek für .NET||X|X|X|
|OpenMP 2.0|X|X|X|X|

## <a name="project-templates"></a>Projektvorlagen

|Vorlage|Visual Studio Express für Windows|Visual Studio Express für Windows Desktop|Visual Studio Professional / Community|Visual Studio Enterprise|
|--------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|XAML-Vorlagen für UWP, Windows 8.1, Windows Phone 8.0|X||X|X|
|Direct3D-App|X||X|X|
|DLL (Universelles Windows)|X||X|X|
|Statische Bibliothek (Universelles Windows)|X||X|X|
|Komponente für Windows-Runtime|X||X|X|
|Komponententest-App (Universelles Windows)|X||X|X|
|ATL-Projekt|||X|X|
|Klassenbibliothek (CLR)||X|X|X|
|CLR-Konsolenanwendung||X|X|X|
|Leeres CLR-Projekt||X|X|X|
|Benutzerdefinierter Assistent|||X|X|
|Leeres Projekt||X|X|X|
|Makefile-Projekt||X|X|X|
|MFC-ActiveX-Steuerelement|||X|X|
|MFC-Anwendung|||X|X|
|MFC-DLL|||X|X|
|Testprojekt|X|X|X|X|
|Win32-Konsolenanwendung||X|X|X|
|Win32-Projekt||X|X|X|

## <a name="tools"></a>Tools

|Tool|Visual Studio Express für Windows|Visual Studio Express für Windows Desktop|Visual Studio Professional / Community|Visual Studio Enterprise|
|----------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|Incremental Linker (Link.exe)|X|X|X|X|
|Program Maintenance Utility (Nmake.exe)||X|X|X|
|Lib-Generator (Lib.exe)|X|X|X|X|
|Windows-Ressourcencompiler (Rc.exe)|X|X|X|X|
|Windows Resource to Object Converter (CvtRes.exe)||X|X|X|
|Browse Information Maintenance-Programm (BscMake.exe)|X|X|X|X|
|C++ Name Undecorator (Undname.exe)|X|X|X|X|
|COFF/PE-Dumper (Dumpbin.exe)|X|X|X|X|
|COFF/PE-Editor (Editbin.exe)|X|X|X|X|
|MASM (Ml.exe)|||X|X|
|Spy++|||X|X|
|ErrLook|||X|X|
|AtlTrace|||X|X|
|Devenv.com|||X|X|
|Rückschlussregeln|||X|X|
|Aktualisieren von VCBuild-VCPROJ-Projekten auf MSBuild (VCUpgrade.exe)|X|X|X|X|
|Profilgesteuerte Optimierungen (PGO)|||X|X|

## <a name="debugging-features"></a>Debugfunktionen

|Debugfunktion|Visual Studio Express für Windows|Visual Studio Express für Windows Desktop|Visual Studio Professional / Community|Visual Studio Enterprise|
|-----------------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|Systemeigenes Debuggen|X|X|X|X|
|Natvis (Visualisierung des systemeigenen Typs)|X|X|X|X|
|Grafikdebugging|X||X|X|
|Verwaltetes Debuggen||X|X|X|
|GPU-Nutzung|X||X|X|
|Speicherauslastung|X||X|X|
|Remote Debugging|X|X|X|X|
|SQL-Debugging|||X|X|
|Statische Codeanalyse|Eingeschränkt|Eingeschränkt|X|X|

## <a name="designers-and-editors"></a>Designer und Editoren

|Designer oder Editor|Visual Studio Express für Windows|Visual Studio Express für Windows Desktop|Visual Studio Professional / Community|Visual Studio Enterprise|
|------------------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|XAML-Designer|X||X|X|
|CSS-Format-Designer/Editor|X|X|X|X|
|HTML-Designer/Editor|X|X|X|X|
|XML-Editor|X|X|X|X|
|Quellcode-Editor|X|X|X|X|
|Features zur Steigerung der Produktivität: Refactoring, IntelliSense, C++-Codeformatierung|X|X|X|X|
|Windows Forms-Designer||X|X|X|
|Daten-Designer|||X|X|
|Systemeigener Ressourcen-Editor (RC-Dateien)|||X|X|
|Ressourcen-Editor|X|X|X|X|
|Modell-Editor|X||X|X|
|Shader-Designer|X||X|X|

## <a name="data-features"></a>Datenfunktionen

|Datenfunktion|Visual Studio Express für Windows|Visual Studio Express für Windows Desktop|Visual Studio Professional / Community|Visual Studio Enterprise|
|------------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|Daten-Designer|||X|X|
|Datenobjekte|||X|X|
|Webdienste|||X|X|
|Server-Explorer|||X|X|

## <a name="build-and-project-systems"></a>Build- und Projektsysteme

|Build- oder Projektfunktion|Visual Studio Express für Windows|Visual Studio Express für Windows Desktop|Visual Studio Professional / Community|Visual Studio Enterprise|
|------------------------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|Befehlszeilenbuilds (msbuild.exe)|X|X|X|X|
|Systemeigene Festlegung von Zielversionen||X|X|X|
|Verwaltete Festlegung von Zielversionen||X|X|X|
|Parallele Builds|X|X|X|X|
|Buildanpassungen|X|X|X|X|
|Erweiterbarkeit der Eigenschaftenseiten|X|X|X|X|

## <a name="automation-and-extensibility"></a>Automatisierung und Erweiterbarkeit

|Automatisierung und Erweiterbarkeit|Visual Studio Express für Windows|Visual Studio Express für Windows Desktop|Visual Studio Professional / Community|Visual Studio Enterprise|
|----------------------------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|Erweiterbarkeitsobjektmodelle|||X|X|
|Codemodell|||X|X|
|Projektmodell|||X|X|
|Modell für den Ressourcen-Editor|||X|X|
|Assistentenmodell|||X|X|
|Debuggerobjektmodell|||X|X|

## <a name="application-lifecycle-management-tools"></a>Anwendungslebenszyklus-Verwaltungstools

||||||
|-|-|-|-|-|
|Tool|Visual Studio Express für Windows|Visual Studio Express für Windows Desktop|Visual Studio Professional / Community|Visual Studio Enterprise|
|Unittests (natives Framework)|X|X|X|X|
|Unittests (verwaltetes Framework)||X|X|X|
|Codeabdeckung||||X|
|Manuelle Tests||||X|
|Explorative Tests||||X|
|Testfallverwaltung||||X|
|Codezuordnung und Abhängigkeitsdiagramme|||Schreibgeschützt|X|
|Code Map-Debugging||||X|

## <a name="see-also"></a>Siehe auch

[Installieren von Visual Studio](/visualstudio/install/install-visual-studio)<br/>
[Neues in Visual Studio](/visualstudio/ide/whats-new-in-visual-studio)<br/>
[C++-Projektvorlagen](../build/reference/visual-cpp-project-types.md)

::: moniker-end
