---
title: C/C++-Projekte und -Buildsysteme in Visual Studio
ms.description: Use Visual Studio to compile and build C++ projects for Windows, ARM or Linux based on any project system.
ms.date: 07/17/2019
helpviewer_keywords:
- builds [C++]
- C++ projects, building
- projects [C++], building
- builds [C++], options
- C++, build options
ms.assetid: fa6ed4ff-334a-4d99-b5e2-a1f83d2b3008
ms.topic: overview
ms.openlocfilehash: 3d82ac4569e06a4472047a79da60032ad2db43ca
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "80078476"
---
# <a name="cc-projects-and-build-systems-in-visual-studio"></a>C/C++-Projekte und -Buildsysteme in Visual Studio

Mithilfe von Visual Studio können Sie jede C++-Codebasis mit vollständiger IntelliSense-Unterstützung bearbeiten, kompilieren und erstellen, ohne den Code in ein Visual Studio-Projekt konvertieren oder mit dem MSVC-Toolset kompilieren zu müssen. Sie können beispielsweise ein plattformübergreifendes CMake-Projekt in Visual Studio auf einem Windows-Computer bearbeiten und dann für Linux mit g++ auf einem Linux-Remotecomputer kompilieren.

## <a name="c-compilation"></a>C++-Kompilierung

Ein C++-Programm zu *erstellen* (englisch: „build“), bedeutet, Quellcode aus einer oder mehreren Dateien zu kompilieren und diese Dateien dann in eine ausführbare Datei (.exe), eine Dynamic Load Library (.dll) oder eine statische Bibliothek (.lib) zu verknüpfen.

Die grundlegende C++-Kompilierung umfasst drei Hauptschritte:

- Der C++-Präprozessor transformiert alle #Anweisungen und Makrodefinitionen in jeder Quelldatei. Dadurch wird eine *Übersetzungseinheit* erstellt.
- Der C++-Compiler kompiliert jede Übersetzungseinheit in Objektdateien (.obj) und wendet dabei alle festgelegten Compileroptionen an.
- Der *Linker* führt die Objektdateien in einer einzelnen ausführbaren Datei zusammen und wendet dabei die festgelegten Linkeroptionen an.

## <a name="the-msvc-toolset"></a>Das MSVC-Toolset

Der Microsoft C++-Compiler, der Linker, die Standardbibliotheken und zugehörige Hilfsprogramme bilden das MSVC-Compilertoolset (auch als Toolkette oder "Buildtools" bezeichnet). Diese sind in Visual Studio enthalten. Sie können das Toolset auch auf der [Download-Seite für Buildtools zu Visual Studio 2019](https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2019) kostenlos als eigenständiges Paket herunterladen und verwenden.

Sie können einfache Programme erstellen, indem Sie den MSVC-Compiler (cl.exe) direkt über die Befehlszeile aufrufen. Der folgende Befehl akzeptiert eine einzelne Quellcodedatei und ruft cl.exe auf, um eine ausführbare Datei mit dem Namen *hello.exe* zu erstellen:

```cmd
cl /EHsc hello.cpp
```

Beachten Sie, dass der Compiler (cl.exe) hier den C++-Präprozessor und den Linker automatisch aufruft, um die endgültige Ausgabedatei zu generieren.  Weitere Informationen finden Sie unter [Erstellen über die Befehlszeile](building-on-the-command-line.md).

## <a name="build-systems-and-projects"></a>Buildsysteme und Projekte

In den meisten realen Programmen wird ein *Buildsystem* verwendet, um die Komplexität der Kompilierung mehrerer Quelldateien für mehrere Konfigurationen (d. h. Debuggen vs. Release), mehrere Plattformen (x86, x64, ARM usw.), benutzerdefinierte Buildschritte und sogar mehrere ausführbare und in einer bestimmten Reihenfolge zu kompilierende Dateien zu verwalten. Sie nehmen Einstellungen in einer Buildkonfigurationsdatei vor, und das Buildsystem akzeptiert diese Datei als Eingabe, bevor es den Compiler aufruft. Die Quellcodedateien und Buildkonfigurationsdateien, die zum Erstellen einer ausführbaren Datei erforderlich sind, werden als *Projekt* bezeichnet.

In der folgenden Liste werden verschiedene Optionen für Visual Studio-Projekte (C++) angezeigt:

- Erstellen Sie ein Visual Studio-Projekt mithilfe der Visual Studio-IDE, und konfigurieren Sie es mithilfe von Eigenschaftenseiten. Visual Studio-Projekte erzeugen Programme, die unter Windows ausgeführt werden. Eine Übersicht finden Sie unter [Kompilieren und Erstellen](/visualstudio/ide/compiling-and-building-in-visual-studio) in der Visual Studio-Dokumentation.

- Öffnen Sie einen Ordner, der eine Datei „CMakeLists.txt“ enthält. CMake-Unterstützung ist in Visual Studio integriert. Sie können die IDE zum Bearbeiten, Testen und Debuggen verwenden, ohne die CMake-Dateien in irgendeiner Weise zu ändern. So können Sie im selben CMake-Projekt arbeiten wie andere Benutzer, die möglicherweise andere Editoren verwenden. CMake ist der empfohlene Ansatz für die plattformübergreifende Entwicklung. Weitere Informationen finden Sie unter [CMake-Projekte](cmake-projects-in-visual-studio.md).

- Öffnen Sie einen losen Ordner von Quelldateien ohne Projektdatei. Visual Studio bedient sich der Heuristik, um die Dateien zu erstellen. Dies ist eine einfache Methode, um kleine Konsolenanwendungen zu kompilieren und auszuführen. Weitere Informationen finden Sie unter [„Ordner öffnen“-Projekte](open-folder-projects-cpp.md).

- Öffnen Sie einen Ordner, der ein Makefile oder eine beliebige andere Buildsystemkonfigurationsdatei enthält. Sie können Visual Studio so konfigurieren, dass beliebige Buildbefehle aufgerufen werden, indem Sie dem Ordner JSON-Dateien hinzufügen. Weitere Informationen finden Sie unter [„Ordner öffnen“-Projekte](open-folder-projects-cpp.md).

- Öffnen Sie in Visual Studio ein Windows-Makefile. Weitere Informationen finden Sie unter [NMAKE-Referenz](reference/nmake-reference.md).

## <a name="msbuild-from-the-command-line"></a>MSBuild über die Befehlszeile

Sie können MSBuild von der Befehlszeile aus aufrufen, indem Sie eine VCXPROJ-Datei zusammen mit Befehlszeilenoptionen übergeben. Diese Vorgehensweise erfordert gute Kenntnisse von MSBuild und wird nur empfohlen, wenn dies unbedingt erforderlich ist. Weitere Informationen finden Sie unter [MSBuild](msbuild-visual-cpp.md).

## <a name="in-this-section"></a>In diesem Abschnitt

[Visual Studio-Projekte](creating-and-managing-visual-cpp-projects.md) Erstellen und Konfigurieren von C++-Projekten in Visual Studio mithilfe seines nativen Buildsystems (MSBuild)

[CMake-Projekte](cmake-projects-in-visual-studio.md) Programmieren, Erstellen und Bereitstellen von CMake-Projekten in Visual Studio

[„Ordner öffnen“-Projekte](open-folder-projects-cpp.md) Verwenden von Visual Studio, um C++-Projekte auf der Grundlage beliebiger Buildsysteme oder ohne ein Buildsystem zu programmieren, zu erstellen und bereitzustellen

[Releasebuilds](release-builds.md) Erstellen und Troubleshooting optimierter Releasebuilds für die Bereitstellung an Endbenutzer

[Verwenden des MSVC-Toolsets über die Befehlszeile](building-on-the-command-line.md)<br/>
Erläutert, wie der C/C++-Compiler und die Buildtools direkt über die Befehlszeile anstatt mithilfe der Visual Studio-IDE verwendet werden.

[Erstellen von DLLs in Visual Studio](dlls-in-visual-cpp.md) Erstellen, Debuggen und Bereitstellen von C/C++-DLLs (freigegebene Bibliotheken) in Visual Studio

[Exemplarische Vorgehensweise: Erstellen und Verwenden einer statischen Bibliothek](walkthrough-creating-and-using-a-static-library-cpp.md) Erstellen einer LIB-Binärdatei

[Erstellen isolierter C/C++-Anwendungen und paralleler Assemblys](building-c-cpp-isolated-applications-and-side-by-side-assemblies.md) Beschreibt das Bereitstellungsmodell für Windows-Desktopanwendungen basierend auf dem Konzept isolierter Anwendungen und paralleler Assemblys.

[Konfigurieren von C++-Projekten für 64-Bit-x64-Ziele](configuring-programs-for-64-bit-visual-cpp.md) Verwenden der MSVC-Buildtools für 64-Bit-x64-Hardware

[Konfigurieren von C++-Projekten für ARM-Prozessoren](configuring-programs-for-arm-processors-visual-cpp.md) Verwenden der MSVC-Buildtools für ARM-Hardware

[Optimieren Ihres Codes](optimizing-your-code.md) Optimieren Ihres Codes auf unterschiedliche Weise, einschließlich programmgeführter Optimierungen

[Konfigurieren von Programmen für Windows XP](configuring-programs-for-windows-xp.md) Verwenden der MSVC-Buildtools für Windows XP

[Referenz zur C/C++-Erstellung](reference/c-cpp-building-reference.md)<br/>
Bietet Links zu Referenzartikeln für das Erstellen von Programmen in C++, zu Compiler- und Linkeroptionen und verschiedenen Buildtools.
