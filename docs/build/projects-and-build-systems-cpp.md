---
title: C/C++ Projekte und Buildsysteme in Visual Studio
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
ms.openlocfilehash: df3b768c139bc4dc000c185d7153fd4aa38ae94a
ms.sourcegitcommit: 44eeb065c3148d0484de791080a3f963109744fc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/18/2020
ms.locfileid: "79509450"
---
# <a name="cc-projects-and-build-systems-in-visual-studio"></a>C/C++ Projekte und Buildsysteme in Visual Studio

Mithilfe von Visual Studio können Sie jede C++ Codebasis mit vollständiger IntelliSense-Unterstützung bearbeiten, kompilieren und erstellen, ohne den Code in ein Visual Studio-Projekt konvertieren oder mit dem MSVC-Toolset kompilieren zu müssen. Beispielsweise können Sie ein plattformübergreifendes cmake-Projekt in Visual Studio auf einem Windows-Computer bearbeiten und dann für Linux mit g + + auf einem Linux-Remote Computer kompilieren.

## <a name="c-compilation"></a>C++Neuauflage

C++ Um *ein Programm zu erstellen,* können Sie Quellcode aus einer oder mehreren Dateien kompilieren und diese Dateien dann in eine ausführbare Datei (exe), eine Dynamic Load Library (dll) oder eine statische Bibliothek (. lib) verknüpfen. 

Die C++ grundlegende Kompilierung umfasst drei Hauptschritte:

- Der C++ Präprozessor wandelt alle #Directives-und Makro Definitionen in jeder Quelldatei um. Dadurch wird eine *Übersetzungseinheit*erstellt.
- Der C++ Compiler kompiliert jede Übersetzungseinheit in Objektdateien (. obj) und wendet alle festgelegten Compileroptionen an.
- Der *Linker* führt die Objektdateien in einer einzelnen ausführbaren Datei zusammen und wendet dabei die Linkeroptionen an, die festgelegt wurden. 

## <a name="the-msvc-toolset"></a>Das MSVC-Toolset

Der Microsoft C++ -Compiler, Linker, Standardbibliotheken und zugehörige Hilfsprogramme bilden das MSVC-Compilertoolset (auch als Toolkette oder "Buildtools" bezeichnet). Diese sind in Visual Studio enthalten. Sie können das Toolset auch als eigenständiges Paket kostenlos über den [Download Speicherort für Buildtools für Visual Studio 2019](https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2019)herunterladen und verwenden.

Sie können einfache Programme erstellen, indem Sie den MSVC-Compiler (cl. exe) direkt über die Befehlszeile aufrufen. Der folgende Befehl akzeptiert eine einzelne Quell Code Datei und ruft cl. exe auf, um eine ausführbare Datei mit dem Namen " *Hello. exe*" zu erstellen: 

```cmd
cl /EHsc hello.cpp
```

Beachten Sie, dass der Compiler (cl. exe) den C++ Präprozessor und den Linker automatisch aufruft, um die endgültige Ausgabedatei zu entwickeln.  Weitere Informationen finden Sie unter [Building in der Befehlszeile](building-on-the-command-line.md).

## <a name="build-systems-and-projects"></a>Buildsysteme und Projekte

In den meisten realen Programmen wird ein *Buildsystem* verwendet, um die Komplexität der Kompilierung mehrerer Quelldateien für mehrere Konfigurationen (d. h. Debug oder Release), mehrere Plattformen (x86, x64, Arm usw.), benutzerdefinierte Buildschritte und sogar mehrere ausführbare Dateien zu verwalten, die in einer bestimmten Reihenfolge kompiliert werden müssen. Sie nehmen Einstellungen in einer buildkonfigurationsdatei (en) vor, und das Buildsystem akzeptiert diese Datei als Eingabe, bevor Sie den Compiler aufruft. Der Satz von Quell Code Dateien und buildkonfigurationsdateien, die zum Erstellen einer ausführbaren Datei erforderlich sind, wird als *Projekt*bezeichnet. 

In der folgenden Liste werden verschiedene Optionen für Visual Studio- C++Projekte angezeigt:

- Erstellen Sie ein Visual Studio-Projekt mithilfe der Visual Studio-IDE, und konfigurieren Sie es mithilfe von Eigenschaften Seiten. In Visual Studio-Projekten werden Programme erzeugt, die unter Windows ausgeführt werden. Eine Übersicht finden Sie unter [Kompilieren und erstellen](/visualstudio/ide/compiling-and-building-in-visual-studio) in der Visual Studio-Dokumentation.

- Öffnen Sie einen Ordner, der die Datei "CMakeLists. txt" enthält. Cmake-Unterstützung ist in Visual Studio integriert. Sie können die IDE zum Bearbeiten, testen und Debuggen verwenden, ohne die cmake-Dateien in irgendeiner Weise zu ändern. Auf diese Weise können Sie im gleichen cmake-Projekt arbeiten wie andere, die möglicherweise unterschiedliche Editoren verwenden. Cmake ist die empfohlene Vorgehensweise für die plattformübergreifende Entwicklung. Weitere Informationen finden Sie unter [cmake-Projekte](cmake-projects-in-visual-studio.md).
 
- Öffnen Sie einen losen Ordner der Quelldateien ohne Projektdatei. Visual Studio verwendet Heuristik, um die Dateien zu erstellen. Dies ist eine einfache Möglichkeit, kleine Konsolen Anwendungen zu kompilieren und auszuführen. Weitere Informationen finden Sie unter [Öffnen von Ordner Projekten](open-folder-projects-cpp.md).

- Öffnen Sie einen Ordner, der ein Makefile oder eine beliebige andere buildsystemkonfigurationsdatei enthält. Sie können Visual Studio so konfigurieren, dass beliebige Buildbefehle aufgerufen werden, indem Sie dem Ordner JSON-Dateien hinzufügen. Weitere Informationen finden Sie unter [Öffnen von Ordner Projekten](open-folder-projects-cpp.md).
 
- Öffnen Sie in Visual Studio ein Windows-Makefile. Weitere Informationen finden Sie unter [NMAKE-Referenz](reference/nmake-reference.md).

## <a name="msbuild-from-the-command-line"></a>MSBuild über die Befehlszeile 

Sie können MSBuild von der Befehlszeile aus aufrufen, indem Sie eine vcxproj-Datei zusammen mit Befehlszeilenoptionen übergeben. Diese Vorgehensweise erfordert ein gutes Verständnis von MSBuild und wird nur empfohlen, wenn dies unbedingt erforderlich ist. Weitere Informationen finden Sie unter [MSBuild](msbuild-visual-cpp.md).

## <a name="in-this-section"></a>In diesem Abschnitt

[Visual Studio-Projekte](creating-and-managing-visual-cpp-projects.md) Erstellen, konfigurieren und Erstellen von C++ Projekten in Visual Studio mithilfe des nativen Buildsystems (MSBuild).

[Cmake-Projekte](cmake-projects-in-visual-studio.md) Gewusst wie: Programmieren, erstellen und Bereitstellen von cmake-Projekten in Visual Studio

[Ordner Projekte öffnen](open-folder-projects-cpp.md) Verwenden von Visual Studio zum Programmieren, erstellen und bereit C++ stellen von Projekten auf der Grundlage beliebiger Buildsysteme oder eines Buildsystems. Überhaupt. 

[Releasebuilds](release-builds.md) Erstellen und Beheben von Problemen mit optimierten Releasebuilds für die Bereitstellung für Endbenutzer.

[Verwenden des MSVC-Toolsets über die Befehlszeile](building-on-the-command-line.md)<br/>
Erläutert, wie der C/CompilerC++ und die Buildtools direkt über die Befehlszeile anstelle der Visual Studio-IDE verwendet werden.

Entwickeln von [DLLs in Visual Studio](dlls-in-visual-cpp.md) Erstellen, Debuggen und Bereitstellen vonC++ C/DLLs (freigegebene Bibliotheken) in Visual Studio.

Exemplarische Vorgehensweise [: Erstellen und Verwenden einer statischen Bibliothek](walkthrough-creating-and-using-a-static-library-cpp.md) So erstellen Sie eine lib-Binärdatei.

[Aufbauen von CC++ /isolierten Anwendungen und](building-c-cpp-isolated-applications-and-side-by-side-assemblies.md) parallelen Assemblys Beschreibt das Bereitstellungs Modell für Windows-Desktop Anwendungen, das auf der Idee von isolierten Anwendungen und parallelen Assemblys basiert.

[Konfigurieren C++ von Projekten für 64-Bit-, x64-Ziele](configuring-programs-for-64-bit-visual-cpp.md) Gewusst wie: Erstellen von 64-Bit-x64-Hardware mit den MSVC-Buildtools

[Konfigurieren C++ von Projekten für ARM-Prozessoren](configuring-programs-for-arm-processors-visual-cpp.md) Verwenden der MSVC-Buildtools zum Ausrichten von Arm-Hardware

[Optimieren Ihres Codes](optimizing-your-code.md) Wie Sie Ihren Code auf verschiedene Weise optimieren, einschließlich Programm gesteuerter Optimierungen.

[Konfigurieren von Programmen für Windows XP](configuring-programs-for-windows-xp.md) Gewusst wie: Erstellen von Windows XP mit den MSVC-Buildtools

[Referenz zur C/C++-Erstellung](reference/c-cpp-building-reference.md)<br/>
Bietet Links zu Referenzartikeln für das Erstellen von Programmen in C++, zu Compiler- und Linkeroptionen und verschiedenen Buildtools.
