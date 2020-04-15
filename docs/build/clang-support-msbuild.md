---
title: Clang/LLVM-Unterstützung in Visual Studio Visual Studio-Projekten
ms.date: 08/30/2019
ms.description: Configure a Visual Studio MSBuild project to use the Clang/LLVM toolchain.
helpviewer_keywords:
- Clang support for C++ MSBuild projects
ms.openlocfilehash: 8d7d7fec979d3e7b8f665e56094ee1c309e3b686
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323123"
---
# <a name="clangllvm-support-in-visual-studio-projects"></a>Clang/LLVM-Unterstützung in Visual Studio-Projekten

::: moniker range="<=vs-2017"

Clang-Unterstützung für CMake- und MSBuild-Projekte ist in Visual Studio 2019 verfügbar.

::: moniker-end

::: moniker range="vs-2019"

Sie können Visual Studio 2019 Version 16.2 mit Clang verwenden, um C++ Visual Studio-Projekte (MSBuild) zu bearbeiten, zu erstellen und zu debuggen, die auf Windows oder Linux abzielen.

## <a name="install"></a>Installieren

Für die beste IDE-Unterstützung in Visual Studio wird die Verwendung der neuesten Clang-Compilertools für Windows empfohlen. Wenn Sie diese noch nicht haben, können Sie sie installieren, indem Sie Visual Studio Installer öffnen und **C++-Clang-Tools für Windows** unter Desktopentwicklung mit optionalen **C++-Komponenten** auswählen. Wenn Sie eine vorhandene Clang-Installation auf Ihrem Computer verwenden möchten, wählen Sie **c++ Clang-cl für v142-Buildtools aus.** optionale Komponente. Die Microsoft C++-Standardbibliothek benötigt derzeit mindestens Clang 8.0.0; Die gebündelte Version von Clang wird automatisch aktualisiert, um mit Updates in der Microsoft-Implementierung der Standardbibliothek auf dem neuesten Stand zu bleiben.

![Clang-Komponenteninstallation](media/clang-install-vs2019.png)

## <a name="configure-a-windows-project-to-use-clang-tools"></a>Konfigurieren eines Windows-Projekts für die Verwendung von Clang-Tools

Um ein Visual Studio-Projekt für die Verwendung von Clang zu konfigurieren, klicken Sie mit der rechten Maustaste auf den Projektknoten im **Projektmappen-Explorer,** und wählen Sie **Eigenschaften**aus. In der Regel sollten Sie zuerst **Alle Konfigurationen** oben im Dialogfeld auswählen. Wählen Sie dann unter **General** > **Platform Toolset** **LLVM (clang-cl)** und dann **OK**aus.

![Clang-Komponenteninstallation](media/clang-msbuild-prop-page.png)

Wenn Sie die Clang-Tools verwenden, die mit Visual Studio gebündelt sind, sind keine zusätzlichen Schritte erforderlich. Bei Windows-Projekten ruft Visual Studio standardmäßig Clang im [clang-cl-Modus](https://llvm.org/devmtg/2014-04/PDFs/Talks/clang-cl.pdf) auf und verknüpft mit der Microsoft-Implementierung der Standardbibliothek. Standardmäßig befindet sich **clang-cl.exe** in `C:\Program Files (x86)\Microsoft Visual Studio\2019\Common7\IDE\CommonExtensions\Microsoft\Llvm\bin`.

Wenn Sie eine benutzerdefinierte Clang-Installation verwenden, können Sie entweder die**ausführbaren** Verzeichnisse der `LLVMInstallDir` **Projekteigenschaften** > **Properties** > **VC++ DIrectories** > Configuration**Properties** > ändern, indem Sie den benutzerdefinierten Clang-Installationsstamm als erstes Verzeichnis dort hinzufügen oder den Wert der Eigenschaft ändern. Weitere Informationen finden Sie unter [Festlegen eines benutzerdefinierten LLVM-Speicherorts.](#custom_llvm_location)

## <a name="configure-a-linux-project-to-use-clang-tools"></a>Konfigurieren eines Linux-Projekts für die Verwendung von Clang-Tools

Für Linux-Projekte verwendet Visual Studio das Clang GCC-kompatible Frontend. Die Projekteigenschaften und fast alle Compilerflags sind identisch

So konfigurieren Sie ein Visual Studio Linux-Projekt für die Verwendung von Clang:

1. Klicken Sie mit der rechten Maustaste auf den Projektknoten im **Projektmappen-Explorer,** und wählen Sie **Eigenschaften**aus.
1. In der Regel sollten Sie zuerst **Alle Konfigurationen** oben im Dialogfeld auswählen.
1. Wählen Sie unter **General** > **Platform Toolset** **WSL_Clang_1_0** aus, ob Sie Windows Subsystem für Linux verwenden, oder **Remote_Clang_1_0,** wenn Sie einen Remotecomputer oder eine VM verwenden.
1. Klicken Sie auf **OK**.

![Clang-Komponenteninstallation](media/clang-msbuild-prop-page.png)

Unter Linux verwendet Visual Studio standardmäßig den ersten Clang-Speicherort, auf den es in der PATH-Umgebungseigenschaft trifft. Wenn Sie eine benutzerdefinierte Clang-Installation verwenden, müssen `LLVMInstallDir` Sie den Wert der Eigenschaft ändern oder einen Pfad unter > **Projekteigenschaften** > **VC++ DIrectories** > **Configuration Properties** > **Executable Directories**ersetzen. **Project** Weitere Informationen finden Sie unter [Festlegen eines benutzerdefinierten LLVM-Speicherorts.](#custom_llvm_location)

## <a name="set-a-custom-llvm-location"></a><a name="custom_llvm_location"></a>Festlegen eines benutzerdefinierten LLVM-Speicherorts

Sie können einen benutzerdefinierten Pfad für LLVM für ein oder mehrere Projekte festlegen, indem Sie eine *Datei Directory.build.props* erstellen und diese Datei dem Stammordner eines beliebigen Projekts hinzufügen. Sie können es dem Stammprojektmappenordner hinzufügen, um ihn auf alle Projekte in der Projektmappe anzuwenden. Die Datei sollte wie folgt aussehen (aber ersetzen Sie Ihren tatsächlichen Pfad):

```xml
<Project>
  <PropertyGroup>
    <LLVMInstallDir>c:\MyLLVMRootDir</LLVMInstallDir>
  </PropertyGroup>
</Project>
```

## <a name="set-additional-properties-edit-build-and-debug"></a>Festlegen zusätzlicher Eigenschaften, Bearbeiten, Erstellen und Debuggen

Nachdem Sie eine Clang-Konfiguration eingerichtet haben, klicken Sie erneut mit der rechten Maustaste auf den Projektknoten, und wählen Sie **Projekt neu laden**aus. Sie können das Projekt jetzt mit den Clang-Tools erstellen und debuggen. Visual Studio erkennt, dass Sie den Clang-Compiler verwenden, und stellt IntelliSense, Hervorhebung, Navigation und andere Bearbeitungsfeatures bereit. Fehler und Warnungen werden im **Ausgabefenster**angezeigt. Die Projekteigenschaftenseiten für eine Clang-Konfiguration ähneln denen für MSVC, obwohl einige compilerabhängige Features wie Bearbeiten und Fortsetzen für Clang-Konfigurationen nicht verfügbar sind. Um eine Clang-Compiler- oder Linkeroption festzulegen, die auf den Eigenschaftenseiten nicht verfügbar ist, können Sie sie manuell in den Eigenschaftenseiten unter **Konfigurationseigenschaften** > **C/C++ (oder Linker)** > **Befehlszeilen-Zusatzoptionen****Command Line** > hinzufügen.

Beim Debuggen können Sie Haltepunkte, Speicher- und Datenvisualisierung und die meisten anderen Debugfunktionen verwenden.  

![Clang-Debugging](media/clang-debug-msbuild.png)

::: moniker-end
