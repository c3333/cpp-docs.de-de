---
title: Erweiterte Eigenschaftenseite (Projekt)
ms.date: 07/19/2019
f1_keywords:
- VC.Project.VCConfiguration.VCToolsVersion
ms.description: Use the Advanced property page in Visual Studio 2019 to set various properties for C++ projects.
ms.openlocfilehash: 8ce62b768f5cda30501e791bcd040a40b18bfb23
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328425"
---
# <a name="advanced-property-page"></a>Erweiterte Eigenschaftenseite

Die Erweiterte Eigenschaftenseite ist in Visual Studio 2019 und höher verfügbar.

::: moniker range="vs-2019"

## <a name="advanced-properties"></a>Erweiterte Eigenschaften

- **Zieldateierweiterung**

   Gibt die Dateierweiterung an, die für die Buildausgabe verwendet werden soll. Standardwerte auf **.exe** für Anwendungen, **.lib** für statische Bibliotheken und **.dll** für DLLs.

- **Bei der Bereinigung zu löschende Erweiterungen**

   Durch die Option **Bereinigen** (Menü **Build**) werden Dateien aus dem Zwischenverzeichnis gelöscht, in dem die Projektkonfiguration erstellt wurde. Dateien mit Erweiterungen, die durch diese Eigenschaft festgelegt werden, werden gelöscht, sobald **Bereinigen** ausgeführt bzw. eine Neuerstellung gestartet wurde. Zusätzlich zu Dateien, die über diese Erweiterungen verfügen und sich im Zwischenverzeichnis befinden, werden vom Buildsystem alle bekannten Ausgaben (einschließlich Zwischenausgaben wie OBJ-Dateien) des Builds unabhängig von ihrem Speicherort gelöscht. Sie können auch Platzhalterzeichen angeben.

   Informationen zum programmgesteuerten Zugriff auf diese Eigenschaft finden Sie unter <xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.DeleteExtensionsOnClean%2A>.

- **Buildprotokolldatei**

   Ermöglicht es Ihnen, ein vom Standardspeicherort abweichendes Verzeichnis für die Protokolldatei anzugeben, die bei jedem Erstellen eines Projekts generiert wird. Der Standardspeicherort wird durch die Makros $(IntDir)$(MSBuildProjectName).log angegeben.

   Sie können Projektmakros verwenden, um den Verzeichnispfad zu ändern. Siehe [Allgemeine Makros für Buildbefehle und -eigenschaften](common-macros-for-build-commands-and-properties.md).

- **Bevorzugte Build-Tool-Architektur**

   Gibt an, ob die x86- oder x64-Buildtools verwendet werden sollen.

- **Debugbibliotheken verwenden**

   Gibt an, ob ein DEBUG- oder RELEASE-Build erstellt werden soll.

- **Unity (JUMBO)-Build aktivieren**

   Ermöglicht einen Buildprozess, bei dem viele C++-Quelldateien vor der Kompilierung zu einer oder mehreren "Einheitsdateien" zusammengefasst werden, um die Buildleistung zu verbessern. In nichts mit der Unity-Spiel-Engine zu tun.

- **Verwendung von MFC**

   Legt fest, ob das MFC-Projekt statisch oder dynamisch mit der MFC-DLL verknüpft wird. Für MFC-fremde Projekte kann **Windows-Standardbibliotheken verwenden** ausgewählt werden, um eine Verknüpfung mit verschiedenen Win32-Bibliotheken herzustellen, die bei Verwendung von MFC einbezogen werden.

   Informationen zum programmgesteuerten Zugriff auf diese Eigenschaft finden Sie unter <xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.useOfMfc%2A>.

- **Zeichensatz**

   Legt fest, ob _UNICODE oder _MBCS verwendet werden soll. Außerdem kann sich diese Option ggf. auf den Linkereinstiegspunkt auswirken.

   Informationen zum programmgesteuerten Zugriff auf diese Eigenschaft finden Sie unter <xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.CharacterSet%2A>.

- **Optimierung des gesamten Programms**

   Legt die Verwendung der [/GL](gl-whole-program-optimization.md)-Compileroption und der [/LTCG](ltcg-link-time-code-generation.md)-Linkeroption fest. Dies ist standardmäßig für die Debugkonfiguration deaktiviert und für die Verkaufskonfiguration aktiviert.

- **MSVC Toolset-Version**

   Gibt die Vollversion des MSVC-Toolsets an, das zum Erstellen des Projekts verwendet wird. Wenn Sie verschiedene Update- und Vorschauversionen eines Toolsets installiert haben, können Sie hier angeben, welches Toolset hier verwendet werden soll.

## <a name="ccli-properties"></a>C++/CLI-Eigenschaften

- **Common Language Runtime-Unterstützung**

   Bewirkt, dass die [/clr](clr-common-language-runtime-compilation.md)-Compileroption verwendet wird.

   Informationen zum programmgesteuerten Zugriff auf diese Eigenschaft finden Sie unter <xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.ManagedExtensions%2A>.

- **.NET Framework-Zielversion**

   Gibt in verwalteten Projekten die Zielversion von .NET-Framework an.

- **Verwalteten inkrementellen Build aktivieren**

   Für verwaltete Projekte aktiviert diese Option die Erkennung von externer Sichtbarkeit, wenn Sie Assemblys generieren. Wenn eine Änderung an einem verwalteten Projekt nicht für andere Projekte sichtbar ist, werden abhängige Projekte nicht neu erstellt. Dies kann Buildzeiten in Projektmappen mit verwalteten Projekten deutlich verbessern.

::: moniker-end
