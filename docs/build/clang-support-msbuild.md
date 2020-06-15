---
title: Clang-/LLVM-Unterstützung in Visual Studio-Projekten
ms.date: 06/02/2020
ms.description: Configure a Visual Studio MSBuild project to use the Clang/LLVM toolchain.
helpviewer_keywords:
- Clang support for C++ MSBuild projects
ms.openlocfilehash: 1a1dfef033bffd3d7f1d24233752d7beae11af8e
ms.sourcegitcommit: d695bb727bd2b081af4d50127b0242a9a5bdce61
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/03/2020
ms.locfileid: "84332278"
---
# <a name="clangllvm-support-in-visual-studio-projects"></a>Clang-/LLVM-Unterstützung in Visual Studio-Projekten

::: moniker range="<=vs-2017"

Die Clang-Unterstützung für CMake- und MSBuild-Projekte ist in Visual Studio 2019 verfügbar.

::: moniker-end

::: moniker range="vs-2019"

Sie können Visual Studio 2019-Version 16.2 mit Clang zum Bearbeiten, Erstellen und Debuggen von C++-Projekten (MSBuild) für Windows oder Linux in Visual Studio verwenden.

## <a name="install"></a>Installieren

Für die beste IDE-Unterstützung in Visual Studio wird die Verwendung der aktuellen Clang-Compilertools für Windows empfohlen. Wenn Sie diese noch nicht installiert haben, können Sie dies nachholen, indem Sie den Visual Studio-Installer öffnen und **C++-Clang-Tools für Windows** unter den optionalen Komponenten für die **Desktopentwicklung mit C++** auswählen. Wenn Sie es bevorzugen, eine auf Ihrem Computer vorhandene Clang-Installation zu verwenden, wählen Sie die optionale Komponente **C++-Clang-cl für v142-Buildtools (x64/x86)** aus. Die Microsoft C++-Standardbibliothek erfordert derzeit mindestens Clang 8.0.0. Die gebündelte Version von Clang wird automatisch aktualisiert, damit sie mit den Updates der Microsoft-Implementierung der Standardbibliothek aktuell bleibt.

![Clang-Komponenteninstallation](media/clang-install-vs2019.png)

## <a name="configure-a-windows-project-to-use-clang-tools"></a>Konfigurieren eines Windows-Projekts zur Verwendung von Clang-Tools

Klicken Sie mit der rechten Maustaste auf den Projektknoten im **Projektmappen-Explorer**, und wählen Sie dann **Eigenschaften** aus, um ein Visual Studio-Projekt zur Verwendung von Clang zu konfigurieren. In der Regel sollten Sie zuerst oben im Dialogfeld auf **Alle Konfigurationen** klicken. Wählen Sie dann unter **Allgemein** > **Plattformtoolset** die Option **LLVM (clang-cl)** aus, und klicken Sie auf **OK**.

![Clang-Komponenteninstallation](media/clang-msbuild-prop-page.png)

Wenn Sie die Clang-Tools verwenden, die in Visual Studio enthalten sind, sind keine weiteren Schritte erforderlich. Bei Windows-Projekten ruft Visual Studio standardmäßig Clang im Modus [clang-cl](https://llvm.org/devmtg/2014-04/PDFs/Talks/clang-cl.pdf) auf und erstellt eine Verknüpfung mit der Microsoft-Implementierung der Standardbibliothek. Standardmäßig befindet sich **clang-cl.exe** unter *%VCINSTALLDIR%\\Extras\\Llvm\\bin\\* und *%VCINSTALLDIR%\\Extras\\Llvm\\x64\\bin\\* .

Wenn Sie eine benutzerdefinierte Clang-Installation verwenden, können Sie Änderungen unter **Projekt** > **Eigenschaften** > **VC++-Verzeichnisse** > **Konfigurationseigenschaften** > **Ausführbare Verzeichnisse** vornehmen, indem Sie dort das Stammverzeichnis der benutzerdefinierten Clang-Installation als erstes Verzeichnis hinzufügen. Alternativ können Sie den Wert der `LLVMInstallDir`-Eigenschaft ändern. Weitere Informationen finden Sie unter [Festlegen eines benutzerdefinierten LLVM-Speicherorts](#custom_llvm_location).

## <a name="configure-a-linux-project-to-use-clang-tools"></a>Konfigurieren eines Linux-Projekts zur Verwendung von Clang-Tools

Für Linux-Projekte verwendet Visual Studio das Front-End mit Clang GCC-Kompatibilität. Die Projekteigenschaften und nahezu alle Compilerflags sind identisch.

So konfigurieren Sie ein Linux-Projekt in Visual Studio für die Verwendung von Clang:

1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf den Projektknoten, und wählen Sie dann **Eigenschaften** aus.
1. In der Regel sollten Sie zuerst oben im Dialogfeld auf **Alle Konfigurationen** klicken.
1. Wählen Sie unter **Allgemein** > **Plattformtoolset** die Option **WSL_Clang_1_0**, wenn Sie das Windows-Subsystem für Linux verwenden, oder **Remote_Clang_1_0** aus, wenn Sie einen Remotecomputer oder eine VM verwenden.
1. Klicken Sie auf **OK**.

![Clang-Komponenteninstallation](media/clang-msbuild-prop-page.png)

Unter Linux verwendet Visual Studio standardmäßig den ersten Clang-Speicherort, der in der PATH-Umgebungseigenschaft gefunden wird. Wenn Sie eine benutzerdefinierte Clang-Installation verwenden, müssen Sie den Wert der `LLVMInstallDir`-Eigenschaft ändern oder einen Pfad unter **Projekt** > **Eigenschaften** > **VC++-Verzeichnisse** > **Konfigurationseigenschaften** > **Ausführbare Verzeichnisse** ersetzen. Weitere Informationen finden Sie unter [Festlegen eines benutzerdefinierten LLVM-Speicherorts](#custom_llvm_location).

## <a name="set-a-custom-llvm-location"></a><a name="custom_llvm_location"></a> Festlegen eines benutzerdefinierten LLVM-Speicherorts

Sie können einen benutzerdefinierten Pfad für LLVM für mehrere Projekte festlegen, indem Sie eine *Directory.build.props*-Datei erstellen und zum Stammverzeichnis der jeweiligen Projekte hinzufügen. Sie können die Datei zum Stammprojektmappen-Ordner hinzufügen, um den Pfad für alle Projekte in der Projektmappe festzulegen. Die Datei sollte wie folgt aussehen (fügen Sie jedoch Ihren tatsächlichen Pfad ein):

```xml
<Project>
  <PropertyGroup>
    <LLVMInstallDir>c:\MyLLVMRootDir</LLVMInstallDir>
  </PropertyGroup>
</Project>
```

## <a name="set-additional-properties-edit-build-and-debug"></a>Festlegen zusätzlicher Eigenschaften, Bearbeiten, Erstellen und Debuggen

Nachdem Sie eine Clang-Konfiguration eingerichtet haben, klicken Sie wieder mit der rechten Maustaste auf den Projektknoten, und wählen Sie dann **Projekt erneut laden** aus. Sie können nun damit beginnen, das Projekt mit den Clang-Tools zu erstellen und zu debuggen. Visual Studio erkennt, dass Sie den Clang-Compiler verwenden, und stellt IntelliSense, die Hervorhebung, die Navigation und andere Bearbeitungsfunktionen bereit. Fehler und Warnungen werden im **Ausgabefenster** angezeigt. Die Seite „Projekteigenschaften“ einer Clang-Konfiguration ähneln denen für MSVC, jedoch sind einige compilerabhängige Features wie „Bearbeiten und fortfahren“ nicht für Clang-Konfigurationen verfügbar. Zum Festlegen einer Clang-Compileroption oder -Linkeroption, die nicht auf den Eigenschaftenseiten verfügbar ist, können Sie sie manuell in den Eigenschaftenseiten unter **Konfigurationseigenschaften** > **C/C++ (oder Linker)**  > **Befehlszeile** > **Zusätzliche Optionen** hinzufügen.

Beim Debuggen können Sie Haltepunkte, die Speicher- und Datenvisualisierung sowie die meisten anderen Debugfunktionen verwenden.  

![Clang-Debugging](media/clang-debug-msbuild.png)

::: moniker-end
