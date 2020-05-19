---
title: Clang-/LLVM-Unterstützung in CMake-Projekten in Visual Studio
ms.date: 07/01/2019
ms.description: Configure a CMake project in Visual Studio to use the Clang/LLVM toolchain.
helpviewer_keywords:
- Clang support for C++ CMake projects
ms.openlocfilehash: 46bfe788c13df3a37dd9cba654d16cfe4c3fe177
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323180"
---
# <a name="clangllvm-support-in-visual-studio-cmake-projects"></a>Clang-/LLVM-Unterstützung in CMake-Projekten in Visual Studio

::: moniker range="<=vs-2017"

Die Unterstützung für Clang ist in Visual Studio 2019 verfügbar.

::: moniker-end

::: moniker range="vs-2019"

Sie können Visual Studio mit Clang zum Bearbeiten und Debuggen von C++-CMake-Projekten verwenden, die Windows oder Linux als Ziel verwenden.

**Windows:** Visual Studio 2019 Version 16.1 bietet Unterstützung für das Bearbeiten, Erstellen und Debuggen mit Clang/LLVM in CMake-Projekten, die Windows als Ziel verwenden.

**Linux**: Für Linux-CMake-Projekte ist keine besondere Visual Studio-Unterstützung erforderlich. Sie können Clang mit dem Paket-Manager Ihrer Distribution installieren und die entsprechenden Befehle in der Datei „CMakeLists.txt“ hinzufügen.

## <a name="install"></a>Installieren

Für die beste IDE-Unterstützung in Visual Studio wird die Verwendung der aktuellen Clang-Compilertools für Windows empfohlen. Wenn Sie diese noch nicht installiert haben, können Sie dies nachholen, indem Sie den Visual Studio-Installer öffnen und **C++-Clang-Compiler für Windows** unter den optionalen Komponenten für die **Desktopentwicklung mit C++** auswählen. Wenn Sie eine benutzerdefinierte Clang-Installation verwenden, überprüfen Sie die Komponente **C++-Clang-cl für v142-Buildtools**.

![Clang-Komponenteninstallation](media/clang-install-vs2019.png)

## <a name="create-a-new-configuration"></a>Erstellen einer neuen Konfiguration

So fügen Sie einem CMake-Projekt eine neue Clang-Konfiguration hinzu:

1. Klicken Sie mit der rechten Maustaste auf „CMakeLists.txt“ im **Projektmappen-Explorer**, und wählen Sie **CMake Settings for Project** (Einstellungen für CMake-Projekt) aus.

1. Klicken Sie unter **Konfigurationen** auf **Konfiguration hinzufügen**:

   ![Hinzufügen einer Konfiguration](media/cmake-add-config-icon.png)

1. Wählen Sie die gewünschte Clang-Konfiguration aus (beachten Sie, dass separate Clang-Konfigurationen für Windows und Linux bereitgestellt werden), und klicken Sie dann auf **Auswählen**:

   ![CMake-Clang-Konfiguration](media/cmake-clang-configuration.png)

1. Wenn Sie Änderungen an dieser Konfiguration vornehmen möchten, verwenden Sie den **Editor für CMake-Einstellungen**. Weitere Informationen finden Sie unter [Anpassen von CMake-Buildeinstellungen](customize-cmake-settings.md).

## <a name="modify-an-existing-configuration-to-use-clang"></a>Ändern einer bestehenden Konfiguration zur Verwendung von Clang

Führen Sie die folgenden Schritte durch, um eine bestehende Konfiguration für die Verwendung von Clang zu ändern:

1. Klicken Sie mit der rechten Maustaste auf „CMakeLists.txt“ im **Projektmappen-Explorer**, und wählen Sie **CMake Settings for Project** (Einstellungen für CMake-Projekt) aus.

1. Wählen Sie unter **Allgemein** aus dem Dropdownmenü **Toolset** das gewünschte Clang-Toolset aus:

   ![CMake-Clang-Toolset](media/cmake-clang-toolset.png)

## <a name="custom-clang-locations"></a>Benutzerdefinierte Clang-Speicherorte

Standardmäßig sucht Visual Studio an zwei Stellen nach Clang:

- Unter Windows: bei der intern installierten Kopie von Clang/LLVM, die im Visual Studio-Installer enthalten ist
- Unter Windows und Linux: bei der PATH-Umgebungsvariable

Sie können einen anderen Speicherort angeben, indem Sie die CMake-Variablen **CMAKE_C_COMPILER** und **CMAKE_CXX_COMPILER** in den **CMake-Einstellungen** festlegen:

![CMake-Clang-Toolset](media/clang-location-cmake.png)

## <a name="clang-compatibility-modes"></a>Clang-Kompatibilitätsmodi

Bei Windows-Konfigurationen ruft CMake Clang standardmäßig im Modus [clang-cl](https://llvm.org/devmtg/2014-04/PDFs/Talks/clang-cl.pdf) auf und erstellt eine Verknüpfung mit der Microsoft-Implementierung der Standardbibliothek. Standardmäßig befindet sich **clang-cl.exe** unter `C:\Program Files (x86)\Microsoft Visual Studio\2019\Common7\IDE\CommonExtensions\Microsoft\Llvm\bin`.

Sie können diese Werte in den **CMake-Einstellungen** unter **CMake-Variablen und -Cache** ändern. Klicken Sie auf **Erweiterte Variablen anzeigen**. Scrollen Sie nach unten zu **CMAKE_CXX_COMPILER**, und klicken Sie auf die Schaltfläche **Durchsuchen**, um einen anderen Compilerpfad anzugeben.

## <a name="edit-build-and-debug"></a>Bearbeiten, Erstellen und Debuggen

Nachdem Sie eine Clang-Konfiguration eingerichtet haben, können Sie das Projekt erstellen und debuggen. Visual Studio erkennt, dass Sie den Clang-Compiler verwenden, und stellt IntelliSense, die Hervorhebung, die Navigation und andere Bearbeitungsfunktionen bereit. Fehler und Warnungen werden im **Ausgabefenster** angezeigt.

Beim Debuggen können Sie Haltepunkte, die Speicher- und Datenvisualisierung sowie die meisten anderen Debugfunktionen verwenden. Einige compilerabhängige Funktionen wie das Bearbeiten und Fortfahren sind für Clang-Konfigurationen nicht verfügbar.

![CMake-Clang-Debuggen](media/clang-debug-visualize.png)

::: moniker-end
