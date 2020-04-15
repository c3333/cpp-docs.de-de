---
title: CMake-Projekte in Visual Studio
description: Erstellen und Erstellen von C++-Projekten mit CMake in Visual Studio.
ms.date: 01/08/2020
helpviewer_keywords:
- CMake in Visual C++
ms.assetid: 444d50df-215e-4d31-933a-b41841f186f8
ms.openlocfilehash: 49ba53eaa8ac075ab6d3b2a66f33160c5c3ec410
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329163"
---
# <a name="cmake-projects-in-visual-studio"></a>CMake-Projekte in Visual Studio

CMake ist ein plattformübergreifendes Open Source-Tool, das zum Definieren von Buildprozessen verwendet wird, die auf mehreren Plattformen ausgeführt werden. In diesem Artikel wird davon ausgegangen, dass Sie mit CMake vertraut sind. Weitere Informationen finden Sie unter [Build, Test and Package Your Software With CMake (Erstellen, Testen und Packen Ihrer Software mit CMake)](https://cmake.org/).

> [!NOTE]
> CMake hat sich in den letzten Versionen mehr und mehr in Visual Studio integriert. Verwenden Sie das Versionsauswahlsteuerelement, um die **Version** Dokumentation für Ihre bevorzugte Version von Visual Studio anzuzeigen. Es befindet sich oben im Inhaltsverzeichnis auf dieser Seite.

::: moniker range="vs-2019"

Die **C++-CMake-Tools für die Windows-Komponente** verwenden die Funktion Ordner [öffnen,](open-folder-projects-cpp.md) um CMake-Projektdateien (z. B. *CMakeLists.txt*) direkt für die Zwecke von IntelliSense und Beim Browsen zu verwenden. Es werden sowohl Ninja- als auch Visual Studio-Generatoren unterstützt. Wenn Sie einen Visual Studio-Generator verwenden, generiert er eine temporäre Projektdatei und übergibt sie an msbuild.exe. Das Projekt wird jedoch nie für IntelliSense- oder Browserzwecke geladen. Sie können auch einen vorhandenen CMake-Cache importieren.

## <a name="installation"></a>Installation

**C++ CMake-Tools für Windows** werden als Teil der **Desktopentwicklung mit C++** und **Linux-Entwicklung mit C++-Workloads** installiert. Weitere Informationen finden Sie unter [Plattformübergreifende CMake-Projekte](../linux/cmake-linux-project.md).

![CMake-Komponente in der Workload „Desktopentwicklung mit C++“](media/cmake-install-2019.png)

Weitere Informationen finden Sie unter [Install the C++ Linux workload in Visual Studio (Installieren der C++-Workload unter Linux in Visual Studio)](../linux/download-install-and-setup-the-linux-development-workload.md).

## <a name="ide-integration"></a>IDE-Integration

Wenn Sie **Datei > Öffnen > Ordner** auswählen, um einen Ordner zu öffnen, der eine *CMakeLists.txt-Datei* enthält, geschieht Folgendes:

- Visual Studio fügt dem **Projektmenü** **CMake-Elemente** mit Befehlen zum Anzeigen und Bearbeiten von CMake-Skripten hinzu.

- Der **Projektmappen-Explorer** zeigt die Ordnerstruktur und die Dateien an.

- Visual Studio führt cmake.exe aus und generiert die CMake-Cachedatei (*CMakeCache.txt*) für die Standardkonfiguration (x64 Debug). Die CMake-Befehlszeile wird im **Ausgabefenster** zusammen mit zusätzlichen Ausgaben von CMake angezeigt.

- Im Hintergrund beginnt Visual Studio damit, die Quelldateien zu indizieren, um IntelliSense, das Durchsuchen von Informationen, das Refactoring und vieles mehr zu ermöglichen. Während Sie arbeiten, überwacht Visual Studio die Änderungen im Editor und auf dem Datenträger, damit der Index mit den Quellen synchron ist.

Sie können Ordner öffnen, die eine beliebige Anzahl von CMake-Projekten enthalten. Visual Studio erkennt und konfiguriert alle *"root"-Dateien von CMakeLists.txt* in Ihrem Arbeitsbereich. CMake-Vorgänge (Konfigurieren, Erstellen, Debuggen), C++ IntelliSense und Browsen sind für alle CMake-Projekte in Ihrem Arbeitsbereich verfügbar.

![CMake-Projekte mit mehreren Stammdateien](media/cmake-multiple-roots.png)

Sie können die Projekte auch logisch strukturiert nach Zielen anzeigen. Wählen Sie in der Dropdownliste der Symbolleiste des **Projektmappen-Explorers** die Option **Zielansicht** aus:

![Schaltfläche für CMake-Zielansicht](media/cmake-targets-view.png)

Klicken Sie oben im **Projektmappen-Explorer** auf die Schaltfläche **Alle Dateien anzeigen,** um die gesamte von CMake generierte Ausgabe in den *Ordnern out/build/config\<>* anzuzeigen.

Visual Studio verwendet eine Konfigurationsdatei namens **CMakeSettings.json**. Mit dieser Datei können Sie mehrere Buildkonfigurationen definieren und speichern und bequem zwischen ihnen in der IDE wechseln. Eine *Konfiguration* ist ein Visual Studio-Konstrukt, das Einstellungen kapselt, die für einen bestimmten Buildtyp spezifisch sind. Die Einstellungen werden verwendet, um die Standardbefehlszeilenoptionen zu konfigurieren, die Visual Studio an cmake.exe übergibt. Sie können hier auch zusätzliche CMake-Optionen angeben und alle zusätzlichen Variablen definieren, die Ihnen gefallen. Alle Optionen werden als interne oder externe Variablen in den CMake-Cache geschrieben. In Visual Studio 2019 bietet der **CMake-Einstellungs-Editor** eine bequeme Möglichkeit, Ihre Einstellungen zu bearbeiten. Weitere Informationen finden Sie unter [Customize CMake settings (Anpassen von CMake-Einstellungen)](customize-cmake-settings.md).

Eine Einstellung `intelliSenseMode` wird nicht an CMake übergeben, sondern nur von Visual Studio verwendet.

Verwenden Sie die Datei **CMakeLists.txt** in jedem Projektordner wie in jedem CMake-Projekt. Sie können Quelldateien angeben, Bibliotheken suchen, Compiler- und Linkeroptionen festlegen und andere systembezogene Buildinformationen angeben.

Um Argumente zum Zeitpunkt des Debuggens an eine ausführbare Datei zu übergeben, können Sie eine andere Datei namens **launch.vs.json**verwenden. In einigen Szenarien generiert Visual Studio diese Dateien automatisch. Sie können sie manuell bearbeiten oder sogar selbst erstellen.

> [!NOTE]
> Für andere Arten von Open Folder-Projekten werden zwei zusätzliche JSON-Dateien verwendet: **CppProperties.json** und **tasks.vs.json**. Diese sind für CMake-Projekte jedoch nicht relevant.

## <a name="open-an-existing-cache"></a>Öffnen eines vorhandenen Caches

Wenn Sie eine vorhandene CMake-Cachedatei öffnen (*CMakeCache.txt*), versucht Visual Studio nicht, den Cache zu verwalten und die Struktur für Sie zu erstellen. Ihre benutzerdefinierten oder bevorzugten Tools haben die vollständige Kontrolle darüber, wie CMake Ihr Projekt konfiguriert. Um einen vorhandenen Cache in Visual Studio zu öffnen, wählen Sie **Datei > Öffnen > CMake**aus. Navigieren Sie dann zu einer vorhandenen *Datei CMakeCache.txt.*

Sie können einem geöffneten Projekt einen vorhandenen CMake-Cache hinzufügen. Es ist auf die gleiche Weise getan, wie Sie eine neue Konfiguration hinzufügen würden. Weitere Informationen finden Sie in unserem Blogbeitrag zum [Öffnen eines vorhandenen Caches in Visual Studio](https://devblogs.microsoft.com/cppblog/open-existing-cmake-caches-in-visual-studio/).

## <a name="building-cmake-projects"></a>Erstellen von CMake-Projekten

Folgende Optionen stehen Ihnen zum Erstellen eines CMake-Projekts zur Verfügung:

1. Suchen Sie in der Symbolleiste Allgemein das Dropdownmenü **Konfiguration**. Es zeigt wahrscheinlich "x64-Debug" standardmäßig. Wählen Sie die bevorzugte Konfiguration aus, und drücken Sie **F5**, oder klicken Sie auf der Symbolleiste auf die Schaltfläche **Ausführen** (grünes Dreieck). Das Projekt wird genau wie eine Visual Studio-Projektmappe zunächst erstellt.

1. Klicken Sie mit der rechten Maustaste auf *CMakeLists.txt* und wählen Sie **Build** aus dem Kontextmenü aus. Wenn mehrere Ziele in Ihrer Ordnerstruktur vorhanden sind, können Sie auswählen, den Build für alle oder nur für ein bestimmtes Ziel durchzuführen.

1. Wählen Sie im Hauptmenü **> Build All** (**F7** oder **Strg+Umschalt+B**) aus. Stellen Sie sicher, dass ein CMake-Ziel bereits in der Dropdownliste **Startelement** auf der Symbolleiste **Allgemein** ausgewählt ist.

![CMake Build-Menü-Befehl](media/cmake-build-menu.png "CMake Build-Befehlsmenü")

Erwartungsgemäß werden die Buildergebnisse im **Ausgabefenster** und in der **Fehlerliste** angezeigt.

![CMake-Buildfehler](media/cmake-build-errors.png "CMake-Buildfehler")

In einem Ordner mit mehreren Buildzielen können Sie angeben, welches CMake-Ziel erstellt werden soll: Wählen Sie das **Buildelement** im **CMake-Menü** oder das Kontextmenü *CMakeLists.txt* aus, um das Ziel anzugeben. Wenn Sie **Strg+Umschalt+B** in ein CMake-Projekt eingeben, wird das aktuelle aktive Dokument erstellt.

## <a name="debugging-cmake-projects"></a>Debuggen von CMake-Projekten

Um ein CMake-Projekt zu debuggen, wählen Sie die bevorzugte Konfiguration aus, und drücken **Sie F5**, oder drücken Sie die Schaltfläche **Ausführen** in der Symbolleiste. Wenn die Schaltfläche **Ausführen** "Startelement auswählen" angibt, wählen Sie den Dropdown-Pfeil aus. Wählen Sie das Ziel aus, das Sie ausführen möchten. (In einem CMake-Projekt ist die Option „Aktuelles Dokument“ nur für CPP-Dateien gültig.)

![CMake Run-Taste](media/cmake-run-button.png "CMake Run-Taste")

Durch **Ausführen** oder **F5** wird das Projekt zunächst erstellt, wenn seit dem vorherigen Build Änderungen vorgenommen wurden. Änderungen an *CMakeSettings.json* führen dazu, dass der CMake-Cache neu generiert wird.

Sie können eine CMake-Debugsitzung anpassen, indem Sie Eigenschaften in der **Datei launch.vs.json** festlegen. Weitere Informationen finden Sie unter [Configure CMake debugging sessions (Konfigurieren von CMake-Debugsitzungen)](configure-cmake-debugging-sessions.md).

## <a name="just-my-code-for-cmake-projects"></a>Just My Code für CMake-Projekte

Wenn Sie mit dem MSVC-Compiler für Windows erstellen, unterstützen CMake-Projekte das Debuggen von Just My Code. Um die Einstellung Nur mein Code zu ändern, gehen Sie zu **Tools** > **Options** > **Debugging** > **General**.

## <a name="vcpkg-integration"></a>Vcpkg-Integration

Wenn Sie [vcpkg](vcpkg.md)installiert haben, integrieren in Visual Studio geöffnete CMake-Projekte automatisch die vcpkg-Toolchain-Datei. Das bedeutet, dass keine zusätzliche Konfiguration erforderlich ist, um vcpkg mit Ihren CMake-Projekten zu verwenden. Diese Unterstützung funktioniert sowohl für lokale vcpkg-Installationen als auch für vcpkg-Installationen auf Remote-Systemen, auf die Sie abzielen. Dieses Verhalten wird automatisch deaktiviert, wenn Sie eine andere Toolchain in Ihrer CMake-Einstellungen-Konfiguration angeben.

## <a name="customize-configuration-feedback"></a>Anpassen des Konfigurationsfeedbacks

Standardmäßig werden die meisten Konfigurationsmeldungen unterdrückt, es sei denn, es liegt ein Fehler vor. Sie können alle Meldungen anzeigen, indem Sie diese Funktion in **Tools** > **Options** > **CMake**aktivieren.

   ![Konfigurieren von CMake-Diagnoseoptionen](media/vs2019-cmake-configure-options.png "CMake-Diagnoseoptionen")

## <a name="editing-cmakeliststxt-files"></a>Bearbeiten von CMakeLists.txt-Dateien

Um eine *CMakeLists.txt-Datei zu* bearbeiten, klicken Sie mit der rechten Maustaste auf die Datei im **Projektmappen-Explorer** und wählen **Sie Öffnen**. Wenn Sie Änderungen an der Datei vornehmen, wird eine gelbe Statusleiste angezeigt, die Sie darüber informiert, dass IntelliSense aktualisiert wird. Es gibt Ihnen die Möglichkeit, den Aktualisierungsvorgang abzubrechen. Informationen zu *CMakeLists.txt*finden Sie in der [CMake-Dokumentation](https://cmake.org/documentation/).

   ![CMakeLists.txt Dateibearbeitung](media/cmake-cmakelists.png "CMakeLists.txt Dateibearbeitung")

Sobald Sie die Datei speichern, wird der Konfigurationsschritt automatisch erneut ausgeführt. Dieser zeigt Informationen im **Ausgabefenster** an. Fehler und Warnungen werden in der **Fehlerliste** oder im **Ausgabefenster** angezeigt. Doppelklicken Sie auf einen Fehler in der **Fehlerliste,** um zur beleidigenden Zeile in *CMakeLists.txt*zu navigieren.

   ![CMakeLists.txt-Dateifehler](media/cmake-cmakelists-error.png "CMakeLists.txt-Dateifehler")

## <a name="cmake-configure-step"></a>CMake-Konfigurationsschritt

Wenn Sie wesentliche Änderungen an den Dateien *CMakeSettings.json* oder *CMakeLists.txt* vornehmen, führt Visual Studio den CMake-Konfigurationsschritt automatisch erneut aus. Wenn der Konfigurationsschritt fehlerfrei abgeschlossen wird, sind die gesammelten Informationen in C++ IntelliSense und Sprachdiensten verfügbar. Es wird auch in Build- und Debugvorgängen verwendet.

## <a name="troubleshooting-cmake-cache-errors"></a>Behandlung von CMake-Cachefehlern

Wenn Sie weitere Informationen über den Status des CMake-Cache benötigen, um ein Problem zu diagnostizieren, öffnen Sie das **Hauptmenü von Project** oder das Kontextmenü *CMakeLists.txt* im **Projektmappen-Explorer,** um einen der folgenden Befehle auszuführen:

- **View Cache** öffnet die Datei *CMakeCache.txt* aus dem Buildstammordner im Editor. (Alle Bearbeitungen, die Sie hier an *CMakeCache.txt* vornehmen, werden gelöscht, wenn Sie den Cache säubern. Informationen zum Beibehalten von Änderungen nach dem Säubern des Caches finden Sie unter Anpassen von [CMake-Einstellungen](customize-cmake-settings.md).)

- **Cacheordner öffnen** öffnet ein Explorer-Fenster zum Stammordner des Builds.

- **Cache bereinigen** löscht den Stammordner des Builds, sodass der nächste CMake-Konfigurationsschritt mit einem leeren Cache beginnt.

- **Cache generieren** erzwingt die Ausführung des Generierungsschritts, auch wenn Visual Studio die Umgebung für aktuell hält.

Die automatische Cachegenerierung kann im **Dialogfeld Tools > Optionen > CMake > Allgemeine** deaktiviert werden.

## <a name="run-cmake-from-the-command-line"></a>Ausführen von CMake über die Befehlszeile

Wenn Sie CMake über den Visual Studio-Installer installiert haben, können Sie CMake über die Befehlszeile ausführen, indem Sie die folgenden Schritte ausführen:

1. Führen Sie die entsprechende Datei „vsdevcmd.bat“ (x86/x64) aus. Weitere Informationen finden Sie unter [Erstellen in der Befehlszeile](building-on-the-command-line.md).

1. Wechseln Sie zu Ihrem Ausgabeordner.

1. Führen Sie CMake zum Erstellen/Konfigurieren Ihrer App aus.

::: moniker-end

::: moniker range="vs-2017"

Visual Studio 2017 bietet umfassende Unterstützung für CMake, einschließlich [plattformübergreifender CMake-Projekte](../linux/cmake-linux-project.md). Die **Visual C++-Komponente "Tools for CMake"** verwendet die Funktion **Ordner öffnen,** um der IDE die Verwendung von CMake-Projektdateien (z. B. *CMakeLists.txt*) direkt für die Zwecke von IntelliSense und Das Browsen zu ermöglichen. Es werden sowohl Ninja- als auch Visual Studio-Generatoren unterstützt. Wenn Sie einen Visual Studio-Generator verwenden, generiert er eine temporäre Projektdatei und übergibt sie an msbuild.exe. Das Projekt wird jedoch nie für IntelliSense- oder Browserzwecke geladen. Sie können auch einen vorhandenen CMake-Cache importieren.

## <a name="installation"></a>Installation

**Visual C++ Tools für CMake** wird als Teil der **Desktopentwicklung mit C++** und **Linux-Entwicklung mit C++-Workloads** installiert.

![CMake-Komponente in der Workload „Desktopentwicklung mit C++“](media/cmake-install.png)

Weitere Informationen finden Sie unter [Install the C++ Linux workload in Visual Studio (Installieren der C++-Workload unter Linux in Visual Studio)](../linux/download-install-and-setup-the-linux-development-workload.md).

## <a name="ide-integration"></a>IDE-Integration

Wenn Sie **Datei > Öffnen > Ordner** auswählen, um einen Ordner zu öffnen, der eine *CMakeLists.txt-Datei* enthält, geschieht Folgendes:

- Visual Studio fügt ein **CMake**-Menüelement zum Hauptmenü hinzu, das Befehle für das Anzeigen und Bearbeiten von CMake-Skripts enthält.

- Der **Projektmappen-Explorer** zeigt die Ordnerstruktur und die Dateien an.

- Visual Studio führt „CMake.exe“ aus und generiert optional den CMake-Cache für die *Standardkonfiguration* (x86 Debug). Die CMake-Befehlszeile wird im **Ausgabefenster** zusammen mit zusätzlichen Ausgaben von CMake angezeigt.

- Im Hintergrund beginnt Visual Studio damit, die Quelldateien zu indizieren, um IntelliSense, das Durchsuchen von Informationen, das Refactoring und vieles mehr zu ermöglichen. Während Sie arbeiten, überwacht Visual Studio die Änderungen im Editor und auf dem Datenträger, damit der Index mit den Quellen synchron ist.

Sie können Ordner öffnen, die eine beliebige Anzahl von CMake-Projekten enthalten. Visual Studio erkennt und konfiguriert alle *"root"-Dateien von CMakeLists.txt* in Ihrem Arbeitsbereich. CMake-Vorgänge (Konfigurieren, Erstellen, Debuggen), C++ IntelliSense und Browsen sind für alle CMake-Projekte in Ihrem Arbeitsbereich verfügbar.

![CMake-Projekte mit mehreren Stammdateien](media/cmake-multiple-roots.png)

Sie können die Projekte auch logisch strukturiert nach Zielen anzeigen. Wählen Sie in der Dropdownliste der Symbolleiste des **Projektmappen-Explorers** die Option **Zielansicht** aus:

![Schaltfläche für CMake-Zielansicht](media/cmake-targets-view.png)

Visual Studio verwendet eine Datei mit dem Namen *CMakeSettings.json,* um Umgebungsvariablen oder Befehlszeilenoptionen für Cmake.exe zu speichern. *Mit CMakeSettings.json* können Sie auch mehrere CMake-Buildkonfigurationen definieren und speichern. Sie können bequem zwischen ihnen in der IDE wechseln.

Andernfalls verwenden Sie *cMakeLists.txt* wie in jedem CMake-Projekt, um Quelldateien anzugeben, Bibliotheken zu suchen, Compiler- und Linkeroptionen festzulegen und andere dokumentatrbezogene Buildinformationen anzugeben.

Wenn Sie Argumente zum Zeitpunkt des Debuggens an eine ausführbare Datei übergeben müssen, können Sie eine andere Datei namens **launch.vs.json**verwenden. In einigen Szenarien generiert Visual Studio diese Dateien automatisch. Sie können sie manuell bearbeiten oder sogar selbst erstellen.

> [!NOTE]
> Für andere Arten von Open Folder-Projekten werden zwei zusätzliche JSON-Dateien verwendet: **CppProperties.json** und **tasks.vs.json**. Diese sind für CMake-Projekte jedoch nicht relevant.

## <a name="import-an-existing-cache"></a>Importieren eines vorhandenen Caches

Wenn Sie eine vorhandene *CMakeCache.txt-Datei* importieren, extrahiert Visual Studio automatisch benutzerdefinierte Variablen und erstellt basierend darauf eine vorab ausgefüllte *CMakeSettings.json-Datei.* Der ursprüngliche Cache wird in keiner Weise geändert. Es kann immer noch über die Befehlszeile verwendet werden, oder mit welchem Werkzeug oder IDE verwendet, um es zu generieren. Die neue Datei *CMakeSettings.json* wird neben dem Stammverzeichnis *CMakeLists.txt*des Projekts platziert. Visual Studio generiert einen neuen Cache, der auf der Einstellungsdatei basiert. Sie können die automatische Cachegenerierung im **Dialogfeld Tools > Options > CMake > Allgemein** überschreiben.

Nicht der gesamte Inhalt des Caches wird importiert.  Eigenschaften wie der Generator und der Speicherort des Compilers werden durch die Standardwerte ersetzt, die in der IDE bekanntermaßen funktionieren.

### <a name="to-import-an-existing-cache"></a>Importieren eines vorhandenen Caches

1. Wählen Sie im Hauptmenü **Datei > öffnen > CMake**:

   ![Öffnen Sie CMake](media/cmake-file-open.png "Datei, Öffnen, CMake")

   Dieser Befehl ruft den Assistenten **zum Importieren von CMake aus Cache** auf.

2. Navigieren Sie zur Datei *CMakeCache.txt,* die Sie importieren möchten, und klicken Sie dann auf **OK**. Der Assistent **CMake-Projekt aus Cache importieren** wird angezeigt:

   ![Importieren eines CMake-Caches](media/cmake-import-wizard.png "Öffnen des CMake-Importcache-Assistenten")

   Wenn der Assistent abgeschlossen ist, können Sie die neue Datei *CMakeCache.txt* im **Projektmappen-Explorer** neben der Stammdatei *CMakeLists.txt* in Ihrem Projekt sehen.

## <a name="building-cmake-projects"></a>Erstellen von CMake-Projekten

Folgende Optionen stehen Ihnen zum Erstellen eines CMake-Projekts zur Verfügung:

1. Suchen Sie in der Symbolleiste Allgemein das Dropdownmenü **Konfiguration**. Es wird wahrscheinlich standardmäßig "Linux-Debug" oder "x64-Debug" angezeigt. Wählen Sie die bevorzugte Konfiguration aus, und drücken Sie **F5**, oder klicken Sie auf der Symbolleiste auf die Schaltfläche **Ausführen** (grünes Dreieck). Das Projekt wird genau wie eine Visual Studio-Projektmappe zunächst erstellt.

1. Klicken Sie mit der rechten Maustaste auf *CMakeLists.txt* und wählen Sie **Build** aus dem Kontextmenü aus. Wenn mehrere Ziele in Ihrer Ordnerstruktur vorhanden sind, können Sie auswählen, den Build für alle oder nur für ein bestimmtes Ziel durchzuführen.

1. Wählen Sie im Hauptmenü **> Build-Lösung** erstellen (**F7** oder **Strg+Umschalt+B**). Stellen Sie sicher, dass ein CMake-Ziel bereits in der Dropdownliste **Startelement** auf der Symbolleiste **Allgemein** ausgewählt ist.

![CMake Build-Menü-Befehl](media/cmake-build-menu.png "CMake Build-Befehlsmenü")

Sie können Buildkonfigurationen, Umgebungsvariablen, Befehlszeilenargumente und andere Einstellungen in der Datei *CMakeSettings.json* anpassen. Sie können Änderungen vornehmen, ohne die Datei *CMakeLists.txt* zu ändern. Weitere Informationen finden Sie unter [Customize CMake settings (Anpassen von CMake-Einstellungen)](customize-cmake-settings.md).

Erwartungsgemäß werden die Buildergebnisse im **Ausgabefenster** und in der **Fehlerliste** angezeigt.

![CMake-Buildfehler](media/cmake-build-errors.png "CMake-Buildfehler")

In einem Ordner mit mehreren Buildzielen können Sie angeben, welches CMake-Ziel erstellt werden soll: Wählen Sie das **Buildelement** im **CMake-Menü** oder das Kontextmenü *CMakeLists.txt* aus, um das Ziel anzugeben. Wenn Sie **Strg+Umschalt+B** in ein CMake-Projekt eingeben, wird das aktuelle aktive Dokument erstellt.

## <a name="debugging-cmake-projects"></a>Debuggen von CMake-Projekten

Um ein CMake-Projekt zu debuggen, wählen Sie die bevorzugte Konfiguration aus und drücken **Sie F5**. Oder drücken Sie die **Run-Taste** in der Symbolleiste. Wenn die Schaltfläche **Ausführen** „Startelement auswählen“ anzeigt, klicken Sie auf den Dropdownpfeil, und wählen Sie das Ziel aus, das ausgeführt werden soll. (In einem CMake-Projekt ist die Option „Aktuelles Dokument“ nur für CPP-Dateien gültig.)

![CMake Run-Taste](media/cmake-run-button.png "CMake Run-Taste")

Durch **Ausführen** oder **F5** wird das Projekt zunächst erstellt, wenn seit dem vorherigen Build Änderungen vorgenommen wurden.

Sie können eine CMake-Debugsitzung anpassen, indem Sie Eigenschaften in der **Datei launch.vs.json** festlegen. Weitere Informationen finden Sie unter [Configure CMake debugging sessions (Konfigurieren von CMake-Debugsitzungen)](configure-cmake-debugging-sessions.md).

## <a name="editing-cmakeliststxt-files"></a>Bearbeiten von CMakeLists.txt-Dateien

Um eine *CMakeLists.txt-Datei zu* bearbeiten, klicken Sie mit der rechten Maustaste auf die Datei im **Projektmappen-Explorer** und wählen **Sie Öffnen**. Wenn Sie Änderungen an der Datei vornehmen, wird eine gelbe Statusleiste angezeigt, die Sie darüber informiert, dass IntelliSense aktualisiert wird. Es gibt Ihnen die Möglichkeit, den Aktualisierungsvorgang abzubrechen. Informationen zu *CMakeLists.txt*finden Sie in der [CMake-Dokumentation](https://cmake.org/documentation/).

   ![CMakeLists.txt Dateibearbeitung](media/cmake-cmakelists.png "CMakeLists.txt Dateibearbeitung")

Sobald Sie die Datei speichern, wird der Konfigurationsschritt automatisch erneut ausgeführt. Dieser zeigt Informationen im **Ausgabefenster** an. Fehler und Warnungen werden in der **Fehlerliste** oder im **Ausgabefenster** angezeigt. Doppelklicken Sie auf einen Fehler in der **Fehlerliste,** um zur beleidigenden Zeile in *CMakeLists.txt*zu navigieren.

   ![CMakeLists.txt-Dateifehler](media/cmake-cmakelists-error.png "CMakeLists.txt-Dateifehler")

## <a name="cmake-configure-step"></a>CMake-Konfigurationsschritt

Wenn wesentliche Änderungen an den Dateien *CMakeSettings.json* oder *CMakeLists.txt* vorgenommen werden, führt Visual Studio den CMake-Konfigurationsschritt automatisch erneut aus. Wenn der Konfigurationsschritt fehlerfrei abgeschlossen wird, sind die gesammelten Informationen in C++ IntelliSense und Sprachdiensten verfügbar. Es wird auch in Build- und Debugvorgängen verwendet.

Mehrere CMake-Projekte können denselben CMake-Konfigurationsnamen verwenden (z. B. x86-Debug). Alle von ihnen werden konfiguriert und erstellt (in ihrem eigenen Build-Stammordner), wenn diese Konfiguration ausgewählt ist. Sie können die Ziele aller CMake-Projekte debuggen, die in dieser CMake-Konfiguration enthalten sind.

   ![CMake Build Only-Menüelement](media/cmake-build-only.png "CMake Build Only-Menüelement")

Sie können Builds und Debugsitzungen auf eine Teilmenge der Projekte im Arbeitsbereich beschränken. Erstellen Sie eine neue Konfiguration mit einem eindeutigen Namen in der Datei *CMakeSettings.json.* Wenden Sie dann die Konfiguration nur auf diese Projekte an. Wenn diese Konfiguration ausgewählt ist, gelten IntelliSense und die Build- und Debugbefehle nur für die angegebenen Projekte.

## <a name="troubleshooting-cmake-cache-errors"></a>Behandlung von CMake-Cachefehlern

Wenn Sie weitere Informationen zum Status des CMake-Caches benötigen, um ein Problem zu diagnostizieren, öffnen Sie das Hauptmenü **CMake** oder das Kontextmenü *CMakeLists.txt* im **Projektmappen-Explorer**, um einen der folgenden Befehle auszuführen:

- **View Cache** öffnet die Datei *CMakeCache.txt* aus dem Buildstammordner im Editor. (Alle Bearbeitungen, die Sie hier an *CMakeCache.txt* vornehmen, werden gelöscht, wenn Sie den Cache säubern. Informationen zum Beibehalten von Änderungen nach dem Säubern des Caches finden Sie unter Anpassen von [CMake-Einstellungen](customize-cmake-settings.md).)

- **Cacheordner öffnen** öffnet ein Explorer-Fenster zum Stammordner des Builds.

- **Cache bereinigen** löscht den Stammordner des Builds, sodass der nächste CMake-Konfigurationsschritt mit einem leeren Cache beginnt.

- **Cache generieren** erzwingt die Ausführung des Generierungsschritts, auch wenn Visual Studio die Umgebung für aktuell hält.

Die automatische Cachegenerierung kann im **Dialogfeld Tools > Optionen > CMake > Allgemeine** deaktiviert werden.

## <a name="single-file-compilation"></a>Zusammenstellung einzelner Dateien

Um eine einzelne Datei in einem CMake-Projekt zu erstellen, klicken Sie mit der rechten Maustaste auf die Datei im **Projektmappen-Explorer**. Wählen Sie Aus dem Popup-Menü **Kompilieren** aus. Sie können die aktuell geöffnete Datei auch im Editor erstellen, indem Sie das Hauptmenü **CMake** verwenden:

![Kompilierung einzelner Dateien in CMake](media/cmake-single-file-compile.png)

## <a name="run-cmake-from-the-command-line"></a>Ausführen von CMake über die Befehlszeile

Wenn Sie CMake über den Visual Studio-Installer installiert haben, können Sie CMake über die Befehlszeile ausführen, indem Sie die folgenden Schritte ausführen:

1. Führen Sie die entsprechende Datei „vsdevcmd.bat“ (x86/x64) aus. Weitere Informationen finden Sie unter [Erstellen in der Befehlszeile](building-on-the-command-line.md) .

1. Wechseln Sie zu Ihrem Ausgabeordner.

1. Führen Sie CMake zum Erstellen/Konfigurieren Ihrer App aus.

::: moniker-end

::: moniker range="vs-2015"

In Visual Studio 2015 können Visual Studio-Benutzer einen [CMake-Generator](https://cmake.org/cmake/help/latest/manual/cmake-generators.7.html) verwenden, um MSBuild-Projektdateien zu generieren, die anschließend von der IDE für IntelliSense sowie für das Durchsuchen und die Kompilierung verwendet werden.

::: moniker-end

## <a name="see-also"></a>Siehe auch

[Tutorial: Erstellen von c++-plattformübergreifenden Projekten in Visual Studio](get-started-linux-cmake.md)\
[Konfigurieren eines Linux CMake-Projekts](../linux/cmake-linux-project.md)\
[Verbinden Sie sich mit Ihrem Remote-Linux-Computer](../linux/connect-to-your-remote-linux-computer.md)\
[Anpassen der CMake-Buildeinstellungen](customize-cmake-settings.md)\
[CMakeSettings.json-Schemaverweis](cmakesettings-reference.md)\
[Konfigurieren von CMake-Debuggingsitzungen](configure-cmake-debugging-sessions.md)\
[Bereitstellen, Ausführen und Debuggen Ihres Linux-Projekts](../linux/deploy-run-and-debug-your-linux-project.md)\
[CMake predefined configuration reference (Referenz für vordefinierte CMake-Konfigurationen)](cmake-predefined-configuration-reference.md)
