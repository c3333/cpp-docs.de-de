---
title: Eigenschaftenseite "Allgemein" (Projekt)
ms.date: 07/17/2019
f1_keywords:
- VC.Project.VCConfiguration.IntermediateDirectory
- VC.Project.VCConfiguration.ConfigurationType
- VC.Project.VCConfiguration.ManagedExtensions
- VC.Project.VCConfiguration.BuildBrowserInformation
- VC.Project.VCConfiguration.BuildLogFile
- VC.Project.VCConfiguration.PlatformToolset
- VC.Project.VCConfiguration.TargetName
- VC.Project.VCConfiguration.
- VC.Project.VCConfiguration.TargetExt
- VC.Project.VCConfiguration.ATLMinimizesCRunTimeLibraryUsage
- VC.Project.VCConfiguration.ReferencesPath
- VC.Project.VCConfiguration.DeleteExtensionsOnClean
- VC.Project.VCConfiguration.useOfMfc
- VC.Project.VCConfiguration.CharacterSet
- VC.Project.VCGeneralMakefileSettings.ConfigurationType
- VC.Project.VCConfiguration.OutputDirectory
- VC.Project.VCConfiguration.AppSupport
- VC.Project.VCConfiguration.ToolFiles
- VC.Project.VCConfiguration.useOfATL
helpviewer_keywords:
- Clean Build option
- output files, setting directory
- Unicode, creating C++ build configuration
ms.openlocfilehash: bb301f63bfd1e6839d7893cdc03d61e021409666
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91500066"
---
# <a name="general-property-page-project"></a>Eigenschaftenseite "Allgemein" (Projekt)

::: moniker range=">=vs-2019"

Dieses Thema bezieht sich auf Visual Studio-Projekte für Windows. Informationen zu Linux-Projekten finden Sie unter [Linux C++ Eigenschaften Seiten Referenz](../../linux/prop-pages-linux.md). Informationen zu cmake-Projekten finden Sie unter [cmake-Projekte in Visual Studio](../cmake-projects-in-visual-studio.md). Informationen zu Android-Projekten finden Sie unter [allgemeine Projekteigenschaften (Android C++)](../../cross-platform/general-android-prop-page.md). Informationen zu Android Makefile-Projekten finden Sie unter [allgemeine Projekteigenschaften (Android C++ Makefile)](../../cross-platform/general-makefile-android-prop-page.md) .

Wenn Sie in Projektmappen-Explorer mit der rechten Maustaste auf einen Projekt Knoten klicken und **Eigenschaften**auswählen, werden auf der Eigenschaften Seite **Allgemein** unter dem Knoten **Konfigurations Eigenschaften** im linken Bereich folgende Eigenschaften angezeigt:

- **Ausgabeverzeichnis**

   Legt das Verzeichnis fest, in dem Tools wie Linker alle endgültigen Ausgabedateien ablegen, die während des Buildprozesses erstellt werden. In der Regel handelt es sich um Ausgabedateien von Tools wie Linker, Bibliothekar oder BSCMake. Diese Eigenschaft ist standardmäßig das Verzeichnis, das durch die Makros $(SolutionDir)$(Configuration)\ angegeben wird.

   Informationen zum programmgesteuerten Zugriff auf diese Eigenschaft finden Sie unter <xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.OutputDirectory%2A>.

- **Zwischenverzeichnis**

   Legt das Verzeichnis fest, in dem Tools wie der Compiler alle Zwischendateien ablegt, die während des Buildprozesses erstellt werden. In der Regel handelt es sich um Ausgabedateien von Tools wie C/C++-Compiler, MIDL und Ressourcencompiler. Diese Eigenschaft ist standardmäßig das Verzeichnis, das durch das Makro $(Configuration)\ angegeben wird.

   Informationen zum programmgesteuerten Zugriff auf diese Eigenschaft finden Sie unter <xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.IntermediateDirectory%2A>.

- **Zielname**

   Gibt den von diesem Projekt generierten Dateinamen an. Diese Eigenschaft ist standardmäßig der Dateiname, der durch das Makro $(ProjectName) angegeben wird.

- **Konfigurationstyp**

  Sie können aus einer Reihe unterschiedlicher Konfigurationstypen auswählen:

  - **Anwendung (EXE-Datei)**

     Zeigt das Linkertoolset (C/C++-Compiler, MIDL, Ressourcencompiler, Linker, BSCMake, XML-Webdienst-Proxy-Generator, benutzerdefinierte Build-, Präbuild-, Prälink- und Postbuildereignisse) an.

  - **Dynamische Bibliothek (.dll)**

     Zeigt das Linkertoolset an, legt die /DLL-Linkeroption fest und fügt CL die _WINDLL-Definition hinzu.

  - **Makefile**

     Zeigt das Makefile-Toolset (NMake) an.

  - **Statische Bibliothek (LIB-Datei)**

     Zeigt das Bibliothekstoolset an (von zwei Ausnahmen abgesehen ist dieses Toolset mit dem Linkertoolset identisch: Der Linker wird durch den Bibliothekar ersetzt, und der XML-Webdienst-Proxy-Generator fällt weg).

  - **Hilfsprogramm**

     Zeigt das Hilfsprogramm-Toolset (MIDL, benutzerdefinierte Build-, Präbuild-, Postbuildereignisse) an.

  Informationen zum programmgesteuerten Zugriff auf diese Eigenschaft finden Sie unter <xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.ConfigurationType%2A>.

- **Windows SDK Version**

   Gibt für die Windows-Zielplattform die Version des Windows SDK an, mit dem Ihr Projekt erstellt wird. Wenn Sie eine C++-Workload mit dem Visual Studio-Installer installieren, werden auch die erforderlichen Teile des Windows SDK installiert. Wenn Sie auf Ihrem Computer über andere Versionen des Windows SDK verfügen, wird jede installierte Version der SDK Tools in der Dropdownliste angezeigt.

   Verwenden Sie den Wert **8.1**, um Windows 7 oder Windows Vista als Zielplattform anzugeben, da Windows SDK 8.1 für diese Plattformen abwärtskompatibel ist. Darüber hinaus müssen Sie den entsprechenden Wert für **_WIN32_WINNT** in „argetver.h“ definieren. Für Windows 7 ist dies "0x0601". Siehe [Ändern von WINVER und _WIN32_WINNT](../../porting/modifying-winver-and-win32-winnt.md)

   Sie können das in Visual Studio enthaltene Windows XP-Plattformtoolset installieren, um die aktuellen Versionen der Bibliotheken zum Erstellen von Windows XP- und Windows 2003-Serverprojekten zu verwenden. Informationen zum Herunterladen und Verwenden dieses Plattformtoolsets finden Sie unter [Konfigurieren von Programmen für Windows XP](../configuring-programs-for-windows-xp.md). Weitere Informationen zum Ändern des Plattformtoolsets finden Sie unter [Vorgehensweise: Ändern des Zielframeworks und des Plattformtoolsets](../how-to-modify-the-target-framework-and-platform-toolset.md).

- **Platt Form Toolset**

   Ermöglicht eine Ausrichtung des Projekts auf andere Versionen der Visual C++-Bibliotheken und des Compilers. Visual Studio C++ Projekte können entweder auf das von Visual Studio installierte Standard Toolset oder auf eines der Toolsets abzielen, die von mehreren früheren Versionen von Visual Studio installiert wurden. Hierzu zählen auch Toolsets, mit denen ausführbare Dateien erstellt werden können, die unter Windows XP ausgeführt werden können. Informationen zum Ändern des Plattformtoolsets finden Sie unter [How to: Modify the Target Framework and Platform Toolset (Vorgehensweise: Ändern des Zielframeworks und des Plattformtoolsets)](../how-to-modify-the-target-framework-and-platform-toolset.md).

- **C++-sprach Standard**

   Gibt an, welcher Sprachstandard verwendet werden soll. Der Standardwert ist/Std: c++ 14. Geben Sie/Std: c++ 17 an, um c++ 17-Features zu verwenden, oder/Std: c++ + latest, um c++ 20 oder andere experimentelle Features zu verwenden. Weitere Informationen finden Sie unter [/Std (angeben der Standard Version für die Sprache)](std-specify-language-standard-version.md) .

::: moniker-end

::: moniker range="<=vs-2017"

Wenn Sie in Visual Studio 2015 und Visual Studio 2017 in **Projektmappen-Explorer**mit der rechten Maustaste auf einen Projekt Knoten klicken und **Eigenschaften**auswählen, werden auf der Eigenschaften Seite **Allgemein** unter dem Knoten **Konfigurations Eigenschaften** im linken Bereich zwei Eigenschaften Abschnitte angezeigt:

- Allgemein

- Projektstandards

## <a name="general"></a>Allgemein

- **Zielplattform**

   Gibt die Plattform an, auf der das Projekt ausgeführt wird. Beispielsweise Windows, Android oder iOS. Der Wert **Windows 10** bedeutet, dass das Projekt für die Universelle Windows-Plattform vorgesehen ist. Wenn Sie auf frühere Versionen von Windows abzielen, wird die Version nicht aufgeführt, und der Wert in diesem Feld wird einfach als **Windows** angezeigt. Dies ist ein schreibgeschütztes Feld, das festgelegt wird, wenn Sie ein Projekt erstellen.

- **Ziel Platt Form Version (Visual Studio 2015)**

   Gibt die niedrigste Version der Plattform an, auf der das Projekt ausgeführt werden kann. Diese Eigenschaft wird nur angezeigt, wenn der Projekttyp Sie unterstützt. Wenn Ihre App Features in einer neueren Version des Windows SDK nutzen, unter früheren Versionen aber weiterhin ohne diese Features ausgeführt werden kann (möglicherweise mit verringerter Funktionalität), kann der Wert dieser beiden Eigenschaften unterschiedlich sein. Ist dies der Fall, sollte in Ihrem Code zur Laufzeit die Version der Plattform geprüft werden, auf der er ausgeführt wird. Es sollte nicht versucht werden, Features zu verwenden, die in älteren Plattformversionen nicht verfügbar sind.

   Das C++-Projekt System erzwingt diese Option nicht. Sie ist aus Gründen der Konsistenz mit anderen Sprachen wie C# und JavaScript sowie als Leitfaden für jede Person eingefügt, die Ihr Projekt verwendet. Visual C++ generiert keinen Fehler, wenn Sie ein Feature verwenden, das in der Mindestversion nicht verfügbar ist.

- **Windows SDK Version (Visual Studio 2017)**

   Gibt für die Windows-Zielplattform die Version des Windows SDK an, mit dem Ihr Projekt erstellt wird. Wenn Sie eine C++-Workload mit dem Visual Studio-Installer installieren, werden auch die erforderlichen Teile des Windows SDK installiert. Wenn Sie auf Ihrem Computer über andere Versionen des Windows SDK verfügen, wird jede installierte Version der SDK Tools in der Dropdownliste angezeigt.

   Verwenden Sie den Wert **8.1**, um Windows 7 oder Windows Vista als Zielplattform anzugeben, da Windows SDK 8.1 für diese Plattformen abwärtskompatibel ist. Darüber hinaus müssen Sie den entsprechenden Wert für **_WIN32_WINNT** in „argetver.h“ definieren. Für Windows 7 ist dies "0x0601". Siehe [Ändern von WINVER und _WIN32_WINNT](../../porting/modifying-winver-and-win32-winnt.md)

   Sie können das in Visual Studio enthaltene Windows XP-Plattformtoolset installieren, um die aktuellen Versionen der Bibliotheken zum Erstellen von Windows XP- und Windows 2003-Serverprojekten zu verwenden. Informationen zum Herunterladen und Verwenden dieses Plattformtoolsets finden Sie unter [Konfigurieren von Programmen für Windows XP](../configuring-programs-for-windows-xp.md). Weitere Informationen zum Ändern des Plattformtoolsets finden Sie unter [Vorgehensweise: Ändern des Zielframeworks und des Plattformtoolsets](../how-to-modify-the-target-framework-and-platform-toolset.md).

- **Ausgabeverzeichnis**

   Legt das Verzeichnis fest, in dem Tools wie Linker alle endgültigen Ausgabedateien ablegen, die während des Buildprozesses erstellt werden. In der Regel handelt es sich um Ausgabedateien von Tools wie Linker, Bibliothekar oder BSCMake. Diese Eigenschaft ist standardmäßig das Verzeichnis, das durch die Makros $(SolutionDir)$(Configuration)\ angegeben wird.

   Informationen zum programmgesteuerten Zugriff auf diese Eigenschaft finden Sie unter <xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.OutputDirectory%2A>.

- **Zwischenverzeichnis**

   Legt das Verzeichnis fest, in dem Tools wie der Compiler alle Zwischendateien ablegt, die während des Buildprozesses erstellt werden. In der Regel handelt es sich um Ausgabedateien von Tools wie C/C++-Compiler, MIDL und Ressourcencompiler. Diese Eigenschaft ist standardmäßig das Verzeichnis, das durch das Makro $(Configuration)\ angegeben wird.

   Informationen zum programmgesteuerten Zugriff auf diese Eigenschaft finden Sie unter <xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.IntermediateDirectory%2A>.

- **Zielname**

   Gibt den von diesem Projekt generierten Dateinamen an. Diese Eigenschaft ist standardmäßig der Dateiname, der durch das Makro $(ProjectName) angegeben wird.

- **Zielerweiterung**

   Gibt die vom Projekt generierte Dateinamenerweiterung an, z. B. .exe oder .dll.

- **Bei der Bereinigung zu löschende Erweiterungen**

   Durch die Option **Bereinigen** (Menü **Build**) werden Dateien aus dem Zwischenverzeichnis gelöscht, in dem die Projektkonfiguration erstellt wurde. Dateien mit Erweiterungen, die durch diese Eigenschaft festgelegt werden, werden gelöscht, sobald **Bereinigen** ausgeführt bzw. eine Neuerstellung gestartet wurde. Zusätzlich zu Dateien, die über diese Erweiterungen verfügen und sich im Zwischenverzeichnis befinden, werden vom Buildsystem alle bekannten Ausgaben (einschließlich Zwischenausgaben wie OBJ-Dateien) des Builds unabhängig von ihrem Speicherort gelöscht. Sie können auch Platzhalterzeichen angeben.

   Informationen zum programmgesteuerten Zugriff auf diese Eigenschaft finden Sie unter <xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.DeleteExtensionsOnClean%2A>.

- **Buildprotokolldatei**

   Ermöglicht es Ihnen, ein vom Standardspeicherort abweichendes Verzeichnis für die Protokolldatei anzugeben, die bei jedem Erstellen eines Projekts generiert wird. Der Standardspeicherort wird durch die Makros $(IntDir)$(MSBuildProjectName).log angegeben.

   Sie können Projektmakros verwenden, um den Verzeichnispfad zu ändern. Siehe [Allgemeine Makros für Buildbefehle und-Eigenschaften](common-macros-for-build-commands-and-properties.md).

- **Platt Form Toolset**

   Ermöglicht eine Ausrichtung des Projekts auf andere Versionen der Visual C++-Bibliotheken und des Compilers. Visual Studio C++ Projekte können entweder auf das von Visual Studio installierte Standard Toolset oder auf eines der Toolsets abzielen, die von mehreren früheren Versionen von Visual Studio installiert wurden. Hierzu zählen auch Toolsets, mit denen ausführbare Dateien erstellt werden können, die unter Windows XP ausgeführt werden können. Informationen zum Ändern des Plattformtoolsets finden Sie unter [How to: Modify the Target Framework and Platform Toolset (Vorgehensweise: Ändern des Zielframeworks und des Plattformtoolsets)](../how-to-modify-the-target-framework-and-platform-toolset.md).

- **Verwalteten inkrementellen Build aktivieren**

   Für verwaltete Projekte aktiviert diese Option die Erkennung von externer Sichtbarkeit, wenn Sie Assemblys generieren. Wenn eine Änderung an einem verwalteten Projekt nicht für andere Projekte sichtbar ist, werden abhängige Projekte nicht neu erstellt. Dies kann Buildzeiten in Projektmappen mit verwalteten Projekten deutlich verbessern.

## <a name="project-defaults"></a>Projektstandards

Die Eigenschaften im Abschnitt “Projektstandards“ stellen änderbare Standardeigenschaften dar. Die Definition für diese Eigenschaften befindet sich in den PROPS-Dateien unter *Installationsverzeichnis*\VC\VCProjectDefaults.

- **Konfigurationstyp**

  Sie können aus einer Reihe unterschiedlicher Konfigurationstypen auswählen:

  - **Anwendung (EXE-Datei)**

     Zeigt das Linkertoolset (C/C++-Compiler, MIDL, Ressourcencompiler, Linker, BSCMake, XML-Webdienst-Proxy-Generator, benutzerdefinierte Build-, Präbuild-, Prälink- und Postbuildereignisse) an.

  - **Dynamische Bibliothek (.dll)**

     Zeigt das Linkertoolset an, legt die /DLL-Linkeroption fest und fügt CL die _WINDLL-Definition hinzu.

  - **Makefile**

     Zeigt das Makefile-Toolset (NMake) an.

  - **Statische Bibliothek (LIB-Datei)**

     Zeigt das Bibliothekstoolset an (von zwei Ausnahmen abgesehen ist dieses Toolset mit dem Linkertoolset identisch: Der Linker wird durch den Bibliothekar ersetzt, und der XML-Webdienst-Proxy-Generator fällt weg).

  - **Hilfsprogramm**

     Zeigt das Hilfsprogramm-Toolset (MIDL, benutzerdefinierte Build-, Präbuild-, Postbuildereignisse) an.

  Informationen zum programmgesteuerten Zugriff auf diese Eigenschaft finden Sie unter <xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.ConfigurationType%2A>.

- **Verwendung von MFC**

   Legt fest, ob das MFC-Projekt statisch oder dynamisch mit der MFC-DLL verknüpft wird. Für MFC-fremde Projekte kann **Windows-Standardbibliotheken verwenden** ausgewählt werden, um eine Verknüpfung mit verschiedenen Win32-Bibliotheken herzustellen, die bei Verwendung von MFC einbezogen werden.

   Informationen zum programmgesteuerten Zugriff auf diese Eigenschaft finden Sie unter <xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.useOfMfc%2A>.

- **Zeichensatz**

   Legt fest, ob _UNICODE oder _MBCS verwendet werden soll. Außerdem kann sich diese Option ggf. auf den Linkereinstiegspunkt auswirken.

   Informationen zum programmgesteuerten Zugriff auf diese Eigenschaft finden Sie unter <xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.CharacterSet%2A>.

- **Common Language Runtime-Unterstützung**

   Bewirkt, dass die [/clr](clr-common-language-runtime-compilation.md)-Compileroption verwendet wird.

   Informationen zum programmgesteuerten Zugriff auf diese Eigenschaft finden Sie unter <xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.ManagedExtensions%2A>.

- **.NET Framework-Zielversion**

   Gibt in verwalteten Projekten die Zielversion von .NET-Framework an.

- **Optimierung des gesamten Programms**

   Legt die Verwendung der [/GL](gl-whole-program-optimization.md)-Compileroption und der [/LTCG](ltcg-link-time-code-generation.md)-Linkeroption fest. Dies ist standardmäßig für die Debugkonfiguration deaktiviert und für die Verkaufskonfiguration aktiviert.

- **Unterstützung für Windows Store-Apps**

   Gibt an, ob dieses Projekt Windows-Runtime-Apps (Universelle Windows-Plattform) unterstützt. Weitere Informationen finden Sie unter [/ZW (Windows Runtime Compilation) (/ZW (Windows-Runtime-Kompilierung))](zw-windows-runtime-compilation.md) und im Windows Developer Center.

::: moniker-end

## <a name="see-also"></a>Siehe auch

[Windows C++-Projekteigenschaftenseitenverweis](property-pages-visual-cpp.md)
