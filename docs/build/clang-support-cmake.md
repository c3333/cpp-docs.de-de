---
title: Clang/LLVM-Unterstützung in Visual Studio CMake-Projekten
ms.date: 07/01/2019
ms.description: Configure a CMake project in Visual Studio to use the Clang/LLVM toolchain.
helpviewer_keywords:
- Clang support for C++ CMake projects
ms.openlocfilehash: 46bfe788c13df3a37dd9cba654d16cfe4c3fe177
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323180"
---
# <a name="clangllvm-support-in-visual-studio-cmake-projects"></a>Clang/LLVM-Unterstützung in Visual Studio CMake-Projekten

::: moniker range="<=vs-2017"

Die Clang-Unterstützung ist in Visual Studio 2019 verfügbar.

::: moniker-end

::: moniker range="vs-2019"

Sie können Visual Studio mit Clang verwenden, um C++ CMake-Projekte zu bearbeiten und zu debuggen, die auf Windows oder Linux abzielen.

**Windows**: Visual Studio 2019 Version 16.1 unterstützt das Bearbeiten, Erstellen und Debuggen mit Clang/LLVM in CMake-Projekten, die auf Windows abzielen.

**Linux**: Für Linux CMake-Projekte ist keine spezielle Visual Studio-Unterstützung erforderlich. Sie können Clang mit dem Paket-Manager Ihres Distroinstallierens installieren und die entsprechenden Befehle in der Datei CMakeLists.txt hinzufügen.

## <a name="install"></a>Installieren

Für die beste IDE-Unterstützung in Visual Studio wird die Verwendung der neuesten Clang-Compilertools für Windows empfohlen. Wenn Sie diese noch nicht haben, können Sie sie installieren, indem Sie Visual Studio Installer öffnen und den **C++-Clang-Compiler für Windows** unter Desktopentwicklung mit optionalen **C++-Komponenten** auswählen. Wenn Sie eine benutzerdefinierte Clang-Installation verwenden, überprüfen Sie die **C++ Clang-cl für v142 Buildtools.**

![Clang-Komponenteninstallation](media/clang-install-vs2019.png)

## <a name="create-a-new-configuration"></a>Erstellen einer neuen Konfiguration

So fügen Sie einem CMake-Projekt eine neue Clang-Konfiguration hinzu:

1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf CMakeLists.txt und wählen Sie **CMake-Einstellungen für Project**.

1. Drücken Sie unter **Konfigurationen**die Schaltfläche **Konfiguration hinzufügen:**

   ![Hinzufügen einer Konfiguration](media/cmake-add-config-icon.png)

1. Wählen Sie die gewünschte Clang-Konfiguration (beachten Sie, dass separate Clang-Konfigurationen für Windows und Linux bereitgestellt werden), und drücken Sie dann **Auswählen:**

   ![CMake Clang-Konfiguration](media/cmake-clang-configuration.png)

1. Um Änderungen an dieser Konfiguration vorzunehmen, verwenden Sie den **CMake-Einstellungs-Editor**. Weitere Informationen finden Sie unter [Anpassen von CMake-Buildeinstellungen in Visual Studio](customize-cmake-settings.md).

## <a name="modify-an-existing-configuration-to-use-clang"></a>Ändern einer vorhandenen Konfiguration zur Verwendung von Clang

Gehen Sie folgendzulande vor, um eine vorhandene Konfiguration für die Verwendung von Clang zu ändern:

1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf CMakeLists.txt und wählen Sie **CMake-Einstellungen für Project**.

1. Wählen Sie unter **Allgemein** die Dropdown-Liste **Toolset** aus und wählen Sie das gewünschte Clang-Toolset aus:

   ![CMake Clang Toolset](media/cmake-clang-toolset.png)

## <a name="custom-clang-locations"></a>Benutzerdefinierte Clang-Standorte

Standardmäßig sucht Visual Studio an zwei Stellen nach Clang:

- (Windows) Die intern installierte Kopie von Clang/LLVM, die im Mitprogramm des Visual Studio-Installationsprogramms ist.
- (Windows und Linux) Die PATH-Umgebungsvariable.

Sie können eine andere Position angeben, indem Sie die **CMAKE_C_COMPILER** und **CMAKE_CXX_COMPILER** CMake-Variablen in **cMake-Einstellungen**festlegen:

![CMake Clang Toolset](media/clang-location-cmake.png)

## <a name="clang-compatibility-modes"></a>Clang-Kompatibilitätsmodi

Bei Windows-Konfigurationen ruft CMake standardmäßig Clang im [clang-cl-Modus](https://llvm.org/devmtg/2014-04/PDFs/Talks/clang-cl.pdf) auf und verknüpft mit der Microsoft-Implementierung der Standardbibliothek. Standardmäßig befindet sich **clang-cl.exe** in `C:\Program Files (x86)\Microsoft Visual Studio\2019\Common7\IDE\CommonExtensions\Microsoft\Llvm\bin`.

Sie können diese Werte in **den CMake-Einstellungen** unter **CMake-Variablen und Cache**ändern. Klicken Sie auf **Erweiterte Variablen anzeigen**. Scrollen Sie nach unten, um **CMAKE_CXX_COMPILER**zu finden, und klicken Sie dann auf die Schaltfläche **Durchsuchen,** um einen anderen Compilerpfad anzugeben.

## <a name="edit-build-and-debug"></a>Bearbeiten, Erstellen und Debuggen

Nachdem Sie eine Clang-Konfiguration eingerichtet haben, können Sie das Projekt erstellen und debuggen. Visual Studio erkennt, dass Sie den Clang-Compiler verwenden, und stellt IntelliSense, Hervorhebung, Navigation und andere Bearbeitungsfeatures bereit. Fehler und Warnungen werden im **Ausgabefenster**angezeigt.

Beim Debuggen können Sie Haltepunkte, Speicher- und Datenvisualisierung und die meisten anderen Debugfunktionen verwenden. Einige Compiler-abhängige Features wie Bearbeiten und Fortfahren sind für Clang-Konfigurationen nicht verfügbar.

![CMake Clang-Debugging](media/clang-debug-visualize.png)

::: moniker-end
