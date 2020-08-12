---
title: Erweiterte Eigenschaften Seite (Projekt)
ms.date: 08/10/2020
f1_keywords:
- VC.Project.VCConfiguration.VCToolsVersion
ms.description: Use the Advanced property page in Visual Studio 2019 to set various properties for C++ projects.
ms.openlocfilehash: 3d6694e44d3da4023998a0335cd06c85b353b2b1
ms.sourcegitcommit: 8140647370017b885432349ce89f187c3068b46a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/12/2020
ms.locfileid: "88144164"
---
# <a name="advanced-property-page"></a>Erweiterte Eigenschaften Seite

::: moniker range="<=vs-2017"

Die Eigenschaften Seite erweitert ist in Visual Studio 2019 und höher verfügbar. Wenn die Dokumentation für diese Version angezeigt werden soll, legen Sie das Steuerelement zur Auswahl der **Version** für diesen Artikel auf Visual Studio 2019 fest. Es befindet sich am Anfang des Inhaltsverzeichnisses auf dieser Seite.

::: moniker-end

::: moniker range="vs-2019"

Die Eigenschaften Seite erweitert ist in Visual Studio 2019 und höher verfügbar.

## <a name="advanced-properties"></a>Erweiterte Eigenschaften

- **Ziel Dateierweiterung**

   Gibt die Dateierweiterung an, die für die Buildausgabe verwendet werden soll. Wird standardmäßig *`.exe`* für-Anwendungen, *`.lib`* für statische Bibliotheken und *`.dll`* für DLLs verwendet.

- **Bei der Bereinigung zu löschende Erweiterungen**

   Durch die Option **Bereinigen** (Menü **Build**) werden Dateien aus dem Zwischenverzeichnis gelöscht, in dem die Projektkonfiguration erstellt wurde. Dateien mit Erweiterungen, die in dieser Eigenschaft angegeben sind, werden gelöscht, wenn **Clean** ausgeführt wird oder wenn Sie neu erstellen. Das Buildsystem löscht alle Dateien, die über diese Erweiterungen im zwischen Verzeichnis verfügen. Außerdem werden alle bekannten Ausgaben des Builds gelöscht, unabhängig davon, wo Sie sich befinden. (Einschließlich der zwischen Ausgaben wie z *`.obj`* . b. Dateien). In dieser Eigenschaft können Sie Platzhalter Zeichen angeben.

   Informationen zum programmgesteuerten Zugriff auf diese Eigenschaft finden Sie unter <xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.DeleteExtensionsOnClean%2A>.

- **Buildprotokolldatei**

   Ermöglicht es Ihnen, einen nicht standardmäßigen Speicherort für die Protokolldatei anzugeben, die erstellt wird, wenn Sie ein Projekt erstellen. Der Standard Speicherort wird durch die Makros angegeben `$(IntDir)$(MSBuildProjectName).log` .

   Sie können Projektmakros verwenden, um den Verzeichnispfad zu ändern. Siehe [Allgemeine Makros für Buildbefehle und-Eigenschaften](common-macros-for-build-commands-and-properties.md).

- **Bevorzugte buildtoolarchitektur**

   Gibt an, ob die x86-oder x64-Buildtools verwendet werden.

- **Debugbibliotheken verwenden**

   Gibt an, ob ein Debug-oder Releasebuild erstellt werden soll.

- **Unity-Build (groß) aktivieren**

   Ermöglicht einen schnelleren Buildprozess, der viele C++-Quelldateien vor der Kompilierung in einer oder mehreren Dateien kombiniert. Diese kombinierten Dateien werden als *Unity* -Dateien bezeichnet. Sie sind nicht mit der Unity-Spiel-Engine verknüpft.

- **Inhalt in OutDir kopieren**

   Kopieren Sie die im Projekt als *Inhalt* markierten Elemente in das Ausgabeverzeichnis des Projekts ( `$(OutDir)` ). Diese Einstellung kann die Bereitstellung vereinfachen. Diese Eigenschaft ist ab Visual Studio 2019 Version 16,7 verfügbar.

- **Projekt Verweise in OutDir kopieren**

   Kopieren Sie die ausführbaren Projekt Verweis Elemente (dll-und exe-Datei) in das Ausgabeverzeichnis des Projekts ( `$(OutDir)` ). In C++/CLI ( [`/clr`](clr-common-language-runtime-compilation.md) )-Projekten wird diese Eigenschaft ignoriert. Stattdessen steuert die Eigenschaft **lokale Kopie** jedes Projekt Verweises, ob Sie in das Ausgabeverzeichnis kopiert wird. Diese Einstellung kann die lokale Bereitstellung vereinfachen. Sie steht ab Visual Studio 2019, Version 16,7, zur Verfügung.

- **Symbole für Projekt Verweise in Ausgabe kopieren**

   Kopieren Sie die PDB-Dateien für Projekt Verweis Elemente zusammen mit den ausführbaren Projekt Verweis Elementen in das Ausgabeverzeichnis des Projekts ( `$(OutDir)` ). Diese Eigenschaft ist für C++/CLI-Projekte immer aktiviert. Diese Einstellung kann die debugbereitstellung vereinfachen. Sie steht ab Visual Studio 2019, Version 16,7, zur Verfügung.

- **C++ Runtime in OutDir kopieren**

   Kopieren Sie die Lauf Zeit-DLLs in das Ausgabeverzeichnis des Projekts ( `$(OutDir)` ). Diese Einstellung kann die lokale Bereitstellung vereinfachen. Sie steht ab Visual Studio 2019, Version 16,7, zur Verfügung.

- **Verwendung von MFC**

   Gibt an, ob das MFC-Projekt statisch oder dynamisch mit der MFC-DLL verknüpft ist. Wählen Sie in nicht-MFC-Projekten die Option **Windows-Standard Bibliotheken verwenden** aus, um die von MFC enthaltenen Win32-Bibliotheken zu verknüpfen.

   Informationen zum programmgesteuerten Zugriff auf diese Eigenschaft finden Sie unter <xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.useOfMfc%2A>.

- **Zeichensatz**

   Definiert, ob `_UNICODE` oder `_MBCS` festgelegt werden soll. Außerdem kann sich diese Option ggf. auf den Linkereinstiegspunkt auswirken.

   Informationen zum programmgesteuerten Zugriff auf diese Eigenschaft finden Sie unter <xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.CharacterSet%2A>.

- **Optimierung des gesamten Programms**

   Gibt die [`/GL`](gl-whole-program-optimization.md) Compileroption und die [`/LTCG`](ltcg-link-time-code-generation.md) Linkeroption an. Standardmäßig ist die Optimierung des gesamten Programms für Debugkonfigurationen deaktiviert und für Releasekonfigurationen aktiviert.

- **MSVC-Toolsetversion**

   Gibt die Vollversion des MSVC-Toolsets an, das zum Erstellen des Projekts verwendet wird. Möglicherweise verfügen Sie über verschiedene Update-und Vorschau Versionen eines Toolsets. Hier können Sie angeben, welcher Wert verwendet werden soll.

## <a name="ccli-properties"></a>C++/CLI-Eigenschaften

- **Common Language Runtime-Unterstützung**

   Bewirkt [`/clr`](clr-common-language-runtime-compilation.md) , dass die-Compileroption verwendet wird.

   Informationen zum programmgesteuerten Zugriff auf diese Eigenschaft finden Sie unter <xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.ManagedExtensions%2A>.

- **.NET Framework-Zielversion**

   Gibt in verwalteten Projekten die Zielversion von .NET-Framework an.

- **Verwalteten inkrementellen Build aktivieren**

   Bei verwalteten Projekten ermöglicht diese Option die Erkennung externer Sichtbarkeit beim Generieren von Assemblys. Wenn eine Änderung an einem verwalteten Projekt für andere Projekte nicht sichtbar ist, werden abhängige Projekte nicht neu erstellt. Verwaltete inkrementelle Builds können Buildzeiten in Lösungen mit verwalteten Projekten erheblich verbessern.

::: moniker-end
