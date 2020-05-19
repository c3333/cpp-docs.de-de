---
title: CMake-Projekte in Visual Studio
description: Hier wird das Erstellen von C++-Projekten mithilfe von CMake in Visual Studio erläutert.
ms.date: 01/08/2020
helpviewer_keywords:
- CMake in Visual C++
ms.assetid: 444d50df-215e-4d31-933a-b41841f186f8
ms.openlocfilehash: 49ba53eaa8ac075ab6d3b2a66f33160c5c3ec410
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329163"
---
# <a name="cmake-projects-in-visual-studio"></a>CMake-Projekte in Visual Studio

CMake ist ein plattformübergreifendes Open Source-Tool, das zum Definieren von Buildprozessen verwendet wird, die auf mehreren Plattformen ausgeführt werden. In diesem Artikel wird davon ausgegangen, dass Sie mit CMake vertraut sind. Weitere Informationen finden Sie unter [Build, Test and Package Your Software With CMake (Erstellen, Testen und Packen Ihrer Software mit CMake)](https://cmake.org/).

> [!NOTE]
> CMake wurde in den letzten Releases immer mehr in Visual Studio integriert. Um die Dokumentation für Ihre bevorzugte Version von Visual Studio anzuzeigen, verwenden Sie das Auswahlsteuerelement **Version**. Es befindet sich am Anfang des Inhaltsverzeichnisses auf dieser Seite.

::: moniker range="vs-2019"

Die Komponente **C++-CMake-Tools für Windows** verwendet die Funktion [Ordner öffnen](open-folder-projects-cpp.md), um CMake-Projektdateien (z. B. *CMakeLists.txt*) direkt für IntelliSense und das Durchsuchen nutzen zu können. Es werden sowohl Ninja- als auch Visual Studio-Generatoren unterstützt. Wenn Sie einen Visual Studio-Generator verwenden, generiert dieser eine temporäre Projektdatei und übergibt sie an „msbuild.exe“. Das Projekt wird jedoch nie für IntelliSense oder zum Durchsuchen geladen. Sie können auch einen vorhandenen CMake-Cache importieren.

## <a name="installation"></a>Installation

Die Komponente **C++-CMake-Tools für Windows** wird als Teil der Workloads **Desktopentwicklung mit C++** und **Linux Entwicklung mit C++** installiert. Weitere Informationen finden Sie unter [Erstellen und Konfigurieren eines Linux-CMake-Projekts](../linux/cmake-linux-project.md).

![CMake-Komponente in der Workload „Desktopentwicklung mit C++“](media/cmake-install-2019.png)

Weitere Informationen finden Sie unter [Install the C++ Linux workload in Visual Studio (Installieren der C++-Workload unter Linux in Visual Studio)](../linux/download-install-and-setup-the-linux-development-workload.md).

## <a name="ide-integration"></a>IDE-Integration

Wenn Sie auf **Datei > Öffnen > Ordner** klicken, um einen Ordner zu öffnen, der eine *CMakeLists.txt*-Datei enthält, geschieht Folgendes:

- Visual Studio fügt ein **CMake**-Element zum Menü **Projekt** mit Befehlen zum Anzeigen und Bearbeiten von CMake-Skripts hinzu.

- Der **Projektmappen-Explorer** zeigt die Ordnerstruktur und die Dateien an.

- Visual Studio führt „cmake.exe“ aus und generiert die CMake-Cachedatei (*CMakeCache.txt*) für die Standardkonfiguration (x64 Debug). Die CMake-Befehlszeile wird im **Ausgabefenster** zusammen mit zusätzlichen Ausgaben von CMake angezeigt.

- Im Hintergrund beginnt Visual Studio damit, die Quelldateien zu indizieren, um IntelliSense, das Durchsuchen von Informationen, das Refactoring und vieles mehr zu ermöglichen. Während Sie arbeiten, überwacht Visual Studio die Änderungen im Editor und auf dem Datenträger, damit der Index mit den Quellen synchron ist.

Sie können Ordner öffnen, die eine beliebige Anzahl von CMake-Projekten enthalten. Visual Studio erkennt und konfiguriert alle *CMakeLists.txt*-Stammdateien in Ihrem Arbeitsbereich. CMake-Vorgänge (Konfigurieren, Erstellen, Debuggen), IntelliSense für C++ und das Durchsuchen sind für alle CMake-Projekte in Ihrem Arbeitsbereich verfügbar.

![CMake-Projekte mit mehreren Stammdateien](media/cmake-multiple-roots.png)

Sie können die Projekte auch logisch strukturiert nach Zielen anzeigen. Wählen Sie in der Dropdownliste der Symbolleiste des **Projektmappen-Explorers** die Option **Zielansicht** aus:

![Schaltfläche für CMake-Zielansicht](media/cmake-targets-view.png)

Klicken Sie oben im **Projektmappen-Explorer** auf **Alle Dateien anzeigen**, um die von CMake generierten Ausgaben in den Ordnern *out/build\<config>* anzuzeigen.

Visual Studio verwendet eine Konfigurationsdatei namens **CMakeSettings.json**. Mit dieser Datei können Sie mehrere Buildkonfigurationen definieren und speichern und in der IDE zwischen ihnen wechseln. Eine *Konfiguration* ist ein Visual Studio-Konstrukt, das Einstellungen kapselt, die für einen bestimmten Buildtyp spezifisch sind. Die Einstellungen werden verwendet, um die Standardbefehlszeilenoptionen zu konfigurieren, die Visual Studio an cmake.exe übergibt. Sie können hier auch weitere CMake-Optionen angeben und alle weiteren gewünschten Variablen definieren. Alle Optionen werden entweder als interne oder externe Variablen in den CMake-Cache geschrieben. In Visual Studio 2019 bietet der **Editor für CMake-Einstellungen** eine bequeme Möglichkeit zum Bearbeiten der Einstellungen. Weitere Informationen finden Sie unter [Customize CMake settings (Anpassen von CMake-Einstellungen)](customize-cmake-settings.md).

Die Einstellung `intelliSenseMode` wird nicht an CMake übergeben, sondern wird nur von Visual Studio verwendet.

Verwenden Sie die Datei **CMakeLists.txt** in jedem Projektordner genau so wie in jedem anderen CMake-Projekt. Sie können Quelldateien angeben, Bibliotheken suchen, Compiler- und Linkeroptionen festlegen und weitere Informationen im Zusammenhang mit dem Buildsystem angeben.

Sie können eine andere Datei namens **launch.vs.json** verwenden, um zur Debugzeit Argumente an eine ausführbare Datei zu übergeben. In einigen Szenarios werden diese Dateien von Visual Studio automatisch generiert. Sie können sie manuell bearbeiten oder sogar die Datei selbst erstellen.

> [!NOTE]
> Für andere Arten von „Ordner öffnen“-Projekten werden zwei zusätzliche JSON-Dateien verwendet: **CppProperties.json** und **tasks.vs.json**. Diese sind für CMake-Projekte jedoch nicht relevant.

## <a name="open-an-existing-cache"></a>Öffnen eines vorhandenen Caches

Wenn Sie eine vorhandene CMake-Cachedatei (*CMakeCache.txt*) öffnen, versucht Visual Studio nicht, Ihren Cache und die Buildstruktur für Sie zu verwalten. Ihre benutzerdefinierten oder bevorzugten Tools haben die umfassende Kontrolle darüber, wie CMake das Projekt konfiguriert. Klicken Sie auf **Datei > Öffnen > CMake**, um einen vorhandenen Cache in Visual Studio zu öffnen. Navigieren Sie dann zu einer vorhandenen *CMakeCache.txt*-Datei.

Sie können einem geöffneten Projekt einen vorhandenen CMake-Cache hinzufügen. Dies erfolgt auf die gleiche Weise wie das Hinzufügen einer neuen Konfiguration. Weitere Informationen finden Sie in unserem Blogbeitrag zum [Öffnen eines vorhandenen Caches in Visual Studio](https://devblogs.microsoft.com/cppblog/open-existing-cmake-caches-in-visual-studio/).

## <a name="building-cmake-projects"></a>Erstellen von CMake-Projekten

Folgende Optionen stehen Ihnen zum Erstellen eines CMake-Projekts zur Verfügung:

1. Suchen Sie auf der Symbolleiste „Allgemein“ nach dem Dropdownmenü **Konfigurationen**. Es wird wahrscheinlich standardmäßig „x64-Debug“ angezeigt. Klicken Sie auf die bevorzugte Konfiguration, und drücken Sie **F5** oder auf der Symbolleiste auf die Schaltfläche **Ausführen** (grünes Dreieck). Das Projekt wird genau wie eine Visual Studio-Projektmappe zunächst erstellt.

1. Klicken Sie mit der rechten Maustaste auf *CMakeLists.txt* und anschließend im Kontextmenü auf **Erstellen**. Wenn mehrere Ziele in Ihrer Ordnerstruktur vorhanden sind, können Sie auswählen, den Build für alle oder nur für ein bestimmtes Ziel durchzuführen.

1. Klicken Sie im Hauptmenü auf **Erstellen > Alle erstellen** (**F7** oder **STRG+UMSCHALT+B**). Stellen Sie sicher, dass ein CMake-Ziel bereits in der Dropdownliste **Startelement** auf der Symbolleiste **Allgemein** ausgewählt ist.

![CMake-Menübefehl „Erstellen“](media/cmake-build-menu.png "CMake-Menübefehl „Erstellen“")

Erwartungsgemäß werden die Buildergebnisse im **Ausgabefenster** und in der **Fehlerliste** angezeigt.

![CMake-Buildfehler](media/cmake-build-errors.png "CMake-Buildfehler")

In einem Ordner mit mehreren Buildzielen können Sie angeben, welches CMake-Ziel erstellt werden soll: Klicken Sie im **CMake**-Menü auf das Element **Erstellen** oder das Kontextmenü *CMakeLists.txt*, um das Ziel anzugeben. Wenn Sie in einem CMake-Projekt **STRG+UMSCHALT+B** drücken, wird das derzeit aktive Dokument erstellt.

## <a name="debugging-cmake-projects"></a>Debuggen von CMake-Projekten

Wenn Sie ein CMake-Projekt debuggen möchten, wählen Sie die gewünschte Konfiguration aus, und drücken Sie **F5**. Klicken Sie alternativ auf die Schaltfläche **Ausführen** auf der Symbolleiste. Wenn die Schaltfläche **Ausführen** die Option „Startelement auswählen“ anzeigt, klicken Sie auf den Dropdownpfeil. Wählen Sie das Ziel aus, das Sie ausführen möchten. (In einem CMake-Projekt ist die Option „Aktuelles Dokument“ nur für CPP-Dateien gültig.)

![CMake-Schaltfläche „Ausführen“](media/cmake-run-button.png "CMake-Schaltfläche „Ausführen“")

Durch **Ausführen** oder **F5** wird das Projekt zunächst erstellt, wenn seit dem vorherigen Build Änderungen vorgenommen wurden. Änderungen an *CMakeSettings.json* bewirken, dass der CMake-Cache erneut generiert wird.

Sie können eine CMake-Debugsitzung durch das Festlegen von Eigenschaften in der Datei **launch.vs.json** anpassen. Weitere Informationen finden Sie unter [Configure CMake debugging sessions (Konfigurieren von CMake-Debugsitzungen)](configure-cmake-debugging-sessions.md).

## <a name="just-my-code-for-cmake-projects"></a>„Nur eigenen Code“ für CMake-Projekte

Wenn Sie für Windows mit dem MSVC-Compiler erstellen, unterstützen CMake-Projekte das „Nur eigenen Code“-Debuggen. Navigieren Sie zu **Extras** > **Optionen** > **Debuggen** > **Allgemein**, um die „Nur eigenen Code“-Einstellung zu ändern.

## <a name="vcpkg-integration"></a>Vcpkg-Integration

Wenn Sie [vcpkg](vcpkg.md) installiert haben, integrieren in Visual Studio geöffnete CMake-Projekte automatisch die vcpkg-Toolkettendatei. Dies bedeutet, dass für die Verwendung von vcpkg mit Ihren CMake-Projekten keine zusätzliche Konfiguration erforderlich ist. Diese Unterstützung kann sowohl für lokale vcpkg-Installationen als auch für vcpkg-Installationen auf Remotesystemen verwendet werden, die Sie als Ziel verwenden. Dieses Verhalten wird automatisch deaktiviert, wenn Sie eine andere Toolkette in der Konfiguration der CMake-Einstellungen angeben.

## <a name="customize-configuration-feedback"></a>Anpassen von Konfigurationsmeldungen

Die meisten Konfigurationsmeldungen werden standardmäßig unterdrückt, es sei denn, es ist ein Fehler aufgetreten. Sie können alle Nachrichten anzeigen, indem Sie dieses Feature über **Extras** > **Optionen** > **CMake** aktivieren.

   ![Konfigurieren von CMake-Diagnoseoptionen](media/vs2019-cmake-configure-options.png "CMake-Diagnoseoptionen")

## <a name="editing-cmakeliststxt-files"></a>Bearbeiten von CMakeLists.txt-Dateien

Wenn Sie eine *CMakeLists.txt*-Datei bearbeiten möchten, klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf die Datei und danach auf **Öffnen**. Wenn Sie Änderungen an der Datei vornehmen, wird eine gelbe Statusleiste angezeigt, die Sie darüber informiert, dass IntelliSense ein Update durchführen möchte. Sie haben die Möglichkeit, den Updatevorgang abzubrechen. Weitere Informationen zu *CMakeLists.txt* finden Sie in der [CMake-Dokumentation](https://cmake.org/documentation/).

   ![Bearbeiten von CMakeLists.txt-Dateien](media/cmake-cmakelists.png "Bearbeiten von CMakeLists.txt-Dateien")

Sobald Sie die Datei speichern, wird der Konfigurationsschritt automatisch erneut ausgeführt. Dieser zeigt Informationen im **Ausgabefenster** an. Fehler und Warnungen werden in der **Fehlerliste** oder im **Ausgabefenster** angezeigt. Doppelklicken Sie auf einen Fehler in der **Fehlerliste**, um zur problematischen Zeile in *CMakeLists.txt* zu navigieren.

   ![CMakeLists.txt-Dateifehler](media/cmake-cmakelists-error.png "CMakeLists.txt-Dateifehler")

## <a name="cmake-configure-step"></a>CMake-Konfigurationsschritt

Wenn Sie wichtige Änderungen an den Dateien *CMakeSettings.json* oder *CMakeLists.txt* vornehmen, führt Visual Studio den CMake-Konfigurationsschritt automatisch erneut aus. Wenn der Konfigurationsschritt ohne Fehler abgeschlossen wird, sind die gesammelten Informationen in IntelliSense für C++ und den Sprachdiensten verfügbar. Er wird auch in Erstellungs- und Debugvorgängen verwendet.

## <a name="troubleshooting-cmake-cache-errors"></a>Behandlung von CMake-Cachefehlern

Wenn Sie weitere Informationen zum Status des CMake-Caches benötigen, um ein Problem zu diagnostizieren, öffnen Sie das Hauptmenü **Projekt** oder das Kontextmenü *CMakeLists.txt* im **Projektmappen-Explorer**, um einen der folgenden Befehle auszuführen:

- **Cache anzeigen** öffnet die Datei *CMakeCache.txt* aus dem Stammordner des Builds im Editor. (Alle Änderungen, die Sie hier an *CMakeCache.txt* vornehmen, werden verworfen, wenn Sie den Cache bereinigen. Informationen zum Vornehmen von Änderungen, die nach dem Bereinigen des Caches beibehalten werden, finden Sie unter [Anpassen von CMake-Einstellungen](customize-cmake-settings.md).)

- **Cacheordner öffnen** öffnet ein Explorer-Fenster zum Stammordner des Builds.

- **Cache bereinigen** löscht den Stammordner des Builds, sodass der nächste CMake-Konfigurationsschritt mit einem leeren Cache beginnt.

- **Cache generieren** erzwingt die Ausführung des Schritts „Generieren“, auch wenn Visual Studio die Umgebung für aktuell hält.

Die automatische Cachegenerierung kann im Dialogfeld **Extras > Optionen > CMake > Allgemein** deaktiviert werden.

## <a name="run-cmake-from-the-command-line"></a>Ausführen von CMake über die Befehlszeile

Wenn Sie CMake über den Visual Studio-Installer installiert haben, können Sie CMake über die Befehlszeile ausführen, indem Sie die folgenden Schritte ausführen:

1. Führen Sie die entsprechende Datei „vsdevcmd.bat“ (x86/x64) aus. Weitere Informationen finden Sie unter [Erstellen über die Befehlszeile](building-on-the-command-line.md).

1. Wechseln Sie zu Ihrem Ausgabeordner.

1. Führen Sie CMake zum Erstellen/Konfigurieren Ihrer App aus.

::: moniker-end

::: moniker range="vs-2017"

Visual Studio 2017 bietet umfangreiche Unterstützung für CMake einschließlich [plattformübergreifender CMake-Projekte](../linux/cmake-linux-project.md). Die Komponente **Visual C++-Tools für CMake** verwendet die Funktion **Ordner öffnen**, um der IDE die Verwendung von CMake-Projektdateien (z. B. *CMakeLists.txt*) direkt für IntelliSense und das Durchsuchen zu ermöglichen. Es werden sowohl Ninja- als auch Visual Studio-Generatoren unterstützt. Wenn Sie einen Visual Studio-Generator verwenden, generiert dieser eine temporäre Projektdatei und übergibt sie an „msbuild.exe“. Das Projekt wird jedoch nie für IntelliSense oder zum Durchsuchen geladen. Sie können auch einen vorhandenen CMake-Cache verwenden.

## <a name="installation"></a>Installation

Die Komponente **Visual C++-Tools für CMake** wird standardmäßig als Teil der Workloads **Desktopentwicklung mit C++** und **Linux Entwicklung mit C++** installiert.

![CMake-Komponente in der Workload „Desktopentwicklung mit C++“](media/cmake-install.png)

Weitere Informationen finden Sie unter [Install the C++ Linux workload in Visual Studio (Installieren der C++-Workload unter Linux in Visual Studio)](../linux/download-install-and-setup-the-linux-development-workload.md).

## <a name="ide-integration"></a>IDE-Integration

Wenn Sie auf **Datei > Öffnen > Ordner** klicken, um einen Ordner zu öffnen, der eine *CMakeLists.txt*-Datei enthält, geschieht Folgendes:

- Visual Studio fügt ein **CMake**-Menüelement zum Hauptmenü hinzu, das Befehle für das Anzeigen und Bearbeiten von CMake-Skripts enthält.

- Der **Projektmappen-Explorer** zeigt die Ordnerstruktur und die Dateien an.

- Visual Studio führt „CMake.exe“ aus und generiert optional den CMake-Cache für die *Standardkonfiguration* (x86 Debug). Die CMake-Befehlszeile wird im **Ausgabefenster** zusammen mit zusätzlichen Ausgaben von CMake angezeigt.

- Im Hintergrund beginnt Visual Studio damit, die Quelldateien zu indizieren, um IntelliSense, das Durchsuchen von Informationen, das Refactoring und vieles mehr zu ermöglichen. Während Sie arbeiten, überwacht Visual Studio die Änderungen im Editor und auf dem Datenträger, damit der Index mit den Quellen synchron ist.

Sie können Ordner öffnen, die eine beliebige Anzahl von CMake-Projekten enthalten. Visual Studio erkennt und konfiguriert alle *CMakeLists.txt*-Stammdateien in Ihrem Arbeitsbereich. CMake-Vorgänge (Konfigurieren, Erstellen, Debuggen), IntelliSense für C++ und das Durchsuchen sind für alle CMake-Projekte in Ihrem Arbeitsbereich verfügbar.

![CMake-Projekte mit mehreren Stammdateien](media/cmake-multiple-roots.png)

Sie können die Projekte auch logisch strukturiert nach Zielen anzeigen. Wählen Sie in der Dropdownliste der Symbolleiste des **Projektmappen-Explorers** die Option **Zielansicht** aus:

![Schaltfläche für CMake-Zielansicht](media/cmake-targets-view.png)

Visual Studio verwendet die Datei *CMakeSettings.json* zum Speichern von Umgebungsvariablen oder Befehlszeilenoptionen für „CMake.exe“. *CMakeSettings.json* ermöglicht außerdem das Definieren und Speichern mehrerer CMake-Buildkonfigurationen. Sie können in der IDE bequem zwischen ihnen wechseln.

Verwenden Sie *CMakeLists.txt* andernfalls einfach wie in jedem anderen CMake-Projekt zum Angeben von Quelldateien, Suchen von Bibliotheken, Festlegen von Compiler- und Linkeroptionen sowie zum Angeben anderer Informationen zum Buildsystem.

Wenn Sie beim Debuggen Argumente an eine ausführbare Datei übergeben müssen, können Sie eine andere Datei namens **launch.vs.json** verwenden. In einigen Szenarios werden diese Dateien von Visual Studio automatisch generiert. Sie können sie manuell bearbeiten oder sogar die Datei selbst erstellen.

> [!NOTE]
> Für andere Arten von „Ordner öffnen“-Projekten werden zwei zusätzliche JSON-Dateien verwendet: **CppProperties.json** und **tasks.vs.json**. Diese sind für CMake-Projekte jedoch nicht relevant.

## <a name="import-an-existing-cache"></a>Importieren eines vorhandenen Caches

Wenn Sie eine vorhandene *CMakeLists.txt*-Datei importieren, extrahiert Visual Studio benutzerdefinierte Variablen automatisch und erstellt eine vorab mit Daten aufgefüllte *CMakeSettings.json*-Datei, die auf diesen basiert. Der ursprüngliche Cache wird in keiner Weise geändert. Er kann weiterhin über die Befehlszeile oder mit einem beliebigen Tool oder der IDE verwendet werden, die zum Generieren verwendet werden. Die neue *CMakeSettings.json*-Datei wird zusammen mit der *CMakeLists.txt*-Stammdatei des Projekts abgelegt. Visual Studio generiert einen neuen Cache, der auf der Einstellungsdatei basiert. Sie können die automatische Cachegenerierung im Dialogfeld **Extras > Optionen > CMake > Allgemein** außer Kraft setzen.

Nicht der gesamte Inhalt des Caches wird importiert.  Eigenschaften wie der Generator und der Speicherort des Compilers werden durch die Standardwerte ersetzt, die in der IDE bekanntermaßen funktionieren.

### <a name="to-import-an-existing-cache"></a>Importieren eines vorhandenen Caches

1. Klicken Sie im Hauptmenü auf **Datei > Öffnen > CMake**:

   ![CMake öffnen](media/cmake-file-open.png "Datei, Öffnen, CMake")

   Mit diesem Befehl wird der Assistent **CMake-Projekt aus Cache importieren** gestartet.

2. Navigieren Sie zur *CMakeCache.txt*-Datei, die Sie importieren möchten, und klicken Sie dann auf **OK**. Der Assistent **CMake-Projekt aus Cache importieren** wird angezeigt:

   ![Importieren eines CMake-Caches](media/cmake-import-wizard.png "Öffnen des Assistenten zum Importieren von CMake-Caches")

   Wenn der Assistent abgeschlossen ist, wird die neue Datei *CMakeCache.txt* im **Projektmappen-Explorer** neben der Stammdatei *CMakeLists.txt* in Ihrem Projekt geöffnet.

## <a name="building-cmake-projects"></a>Erstellen von CMake-Projekten

Folgende Optionen stehen Ihnen zum Erstellen eines CMake-Projekts zur Verfügung:

1. Suchen Sie auf der Symbolleiste „Allgemein“ nach dem Dropdownmenü **Konfigurationen**. Es wird wahrscheinlich standardmäßig „Linux-Debug“ oder „x64-Debug“ angezeigt. Klicken Sie auf die bevorzugte Konfiguration, und drücken Sie **F5** oder auf der Symbolleiste auf die Schaltfläche **Ausführen** (grünes Dreieck). Das Projekt wird genau wie eine Visual Studio-Projektmappe zunächst erstellt.

1. Klicken Sie mit der rechten Maustaste auf *CMakeLists.txt* und dann im Kontextmenü auf **Erstellen**. Wenn mehrere Ziele in Ihrer Ordnerstruktur vorhanden sind, können Sie auswählen, den Build für alle oder nur für ein bestimmtes Ziel durchzuführen.

1. Alternativ können Sie im Hauptmenü auf **Erstellen > Projektmappe erstellen** klicken (**F7** oder **STRG+UMSCHALT+B**). Stellen Sie sicher, dass ein CMake-Ziel bereits in der Dropdownliste **Startelement** auf der Symbolleiste **Allgemein** ausgewählt ist.

![CMake-Menübefehl „Erstellen“](media/cmake-build-menu.png "CMake-Menübefehl „Erstellen“")

Sie können Buildkonfigurationen, Umgebungsvariablen, Befehlszeilenargumente und andere Einstellungen in der *CMakeSettings.json*-Datei anpassen. Sie können Änderungen vornehmen, ohne die Datei *CMakeLists.txt* zu ändern. Weitere Informationen finden Sie unter [Customize CMake settings (Anpassen von CMake-Einstellungen)](customize-cmake-settings.md).

Erwartungsgemäß werden die Buildergebnisse im **Ausgabefenster** und in der **Fehlerliste** angezeigt.

![CMake-Buildfehler](media/cmake-build-errors.png "CMake-Buildfehler")

In einem Ordner mit mehreren Buildzielen können Sie angeben, welches CMake-Ziel erstellt werden soll: Klicken Sie im **CMake**-Menü auf das Element **Erstellen** oder das Kontextmenü *CMakeLists.txt*, um das Ziel anzugeben. Wenn Sie in einem CMake-Projekt **STRG+UMSCHALT+B** drücken, wird das derzeit aktive Dokument erstellt.

## <a name="debugging-cmake-projects"></a>Debuggen von CMake-Projekten

Wenn Sie ein CMake-Projekt debuggen möchten, wählen Sie die gewünschte Konfiguration aus, und drücken Sie **F5**. Alternativ können Sie auf die Schaltfläche **Ausführen** auf der Symbolleiste klicken. Wenn die Schaltfläche **Ausführen** „Startelement auswählen“ anzeigt, klicken Sie auf den Dropdownpfeil, und wählen Sie das Ziel aus, das ausgeführt werden soll. (In einem CMake-Projekt ist die Option „Aktuelles Dokument“ nur für CPP-Dateien gültig.)

![CMake-Schaltfläche „Ausführen“](media/cmake-run-button.png "CMake-Schaltfläche „Ausführen“")

Durch **Ausführen** oder **F5** wird das Projekt zunächst erstellt, wenn seit dem vorherigen Build Änderungen vorgenommen wurden.

Sie können eine CMake-Debugsitzung durch das Festlegen von Eigenschaften in der Datei **launch.vs.json** anpassen. Weitere Informationen finden Sie unter [Configure CMake debugging sessions (Konfigurieren von CMake-Debugsitzungen)](configure-cmake-debugging-sessions.md).

## <a name="editing-cmakeliststxt-files"></a>Bearbeiten von CMakeLists.txt-Dateien

Wenn Sie eine *CMakeLists.txt*-Datei bearbeiten möchten, klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf die Datei und danach auf **Öffnen**. Wenn Sie Änderungen an der Datei vornehmen, wird eine gelbe Statusleiste angezeigt, die Sie darüber informiert, dass IntelliSense ein Update durchführen möchte. Sie haben die Möglichkeit, den Updatevorgang abzubrechen. Weitere Informationen zu *CMakeLists.txt* finden Sie in der [CMake-Dokumentation](https://cmake.org/documentation/).

   ![Bearbeiten von CMakeLists.txt-Dateien](media/cmake-cmakelists.png "Bearbeiten von CMakeLists.txt-Dateien")

Sobald Sie die Datei speichern, wird der Konfigurationsschritt automatisch erneut ausgeführt. Dieser zeigt Informationen im **Ausgabefenster** an. Fehler und Warnungen werden in der **Fehlerliste** oder im **Ausgabefenster** angezeigt. Doppelklicken Sie auf einen Fehler in der **Fehlerliste**, um zur problematischen Zeile in *CMakeLists.txt* zu navigieren.

   ![CMakeLists.txt-Dateifehler](media/cmake-cmakelists-error.png "CMakeLists.txt-Dateifehler")

## <a name="cmake-configure-step"></a>CMake-Konfigurationsschritt

Wenn wichtige Änderungen an den Dateien *CMakeSettings.json* oder *CMakeLists.txt* vorgenommen werden, führt Visual Studio den CMake-Konfigurationsschritt automatisch erneut aus. Wenn der Konfigurationsschritt ohne Fehler abgeschlossen wird, sind die gesammelten Informationen in IntelliSense für C++ und den Sprachdiensten verfügbar. Er wird auch in Erstellungs- und Debugvorgängen verwendet.

Mehrere CMake-Projekte verwenden möglicherweise denselben CMake-Konfigurationsnamen (z. B. „x86-Debug“). Wenn diese Konfiguration ausgewählt ist, werden diese (in ihrem eigenen Buildstammordner) konfiguriert und erstellt. Sie können die Ziele aller CMake-Projekte debuggen, die in dieser CMake-Konfiguration enthalten sind.

   ![CMake-Menüelement „Nur erstellen“](media/cmake-build-only.png "CMake-Menüelement „Nur erstellen“")

Sie können Build- und Debugsitzungen auf eine Teilmenge der Projekte im Arbeitsbereich beschränken. Erstellen Sie eine neue Konfiguration mit einem eindeutigen Namen in der Datei *CMakeSettings.json*. Wenden Sie die Konfiguration dann nur auf diese Projekte an. Wenn diese Konfiguration ausgewählt ist, werden IntelliSense und die Build- und Debugbefehle nur für die angegebenen Projekte angewendet.

## <a name="troubleshooting-cmake-cache-errors"></a>Behandlung von CMake-Cachefehlern

Wenn Sie weitere Informationen zum Status des CMake-Caches benötigen, um ein Problem zu diagnostizieren, öffnen Sie das Hauptmenü **CMake** oder das Kontextmenü *CMakeLists.txt* im **Projektmappen-Explorer**, um einen der folgenden Befehle auszuführen:

- **Cache anzeigen** öffnet die Datei *CMakeCache.txt* aus dem Stammordner des Builds im Editor. (Alle Änderungen, die Sie hier an *CMakeCache.txt* vornehmen, werden verworfen, wenn Sie den Cache bereinigen. Informationen zum Vornehmen von Änderungen, die nach dem Bereinigen des Caches beibehalten werden, finden Sie unter [Anpassen von CMake-Einstellungen](customize-cmake-settings.md).)

- **Cacheordner öffnen** öffnet ein Explorer-Fenster zum Stammordner des Builds.

- **Cache bereinigen** löscht den Stammordner des Builds, sodass der nächste CMake-Konfigurationsschritt mit einem leeren Cache beginnt.

- **Cache generieren** erzwingt die Ausführung des Schritts „Generieren“, auch wenn Visual Studio die Umgebung für aktuell hält.

Die automatische Cachegenerierung kann im Dialogfeld **Extras > Optionen > CMake > Allgemein** deaktiviert werden.

## <a name="single-file-compilation"></a>Kompilierung einzelner Dateien

Klicken Sie zum Erstellen einer einzelnen Datei in einem CMake-Projekt im **Projektmappen-Explorer** mit der rechten Maustaste auf die Datei. Klicken Sie im Popupmenü auf **Kompilieren**. Sie können die derzeit im Editor geöffnete Datei auch über das **CMake**-Hauptmenü erstellen:

![Kompilierung einzelner Dateien in CMake](media/cmake-single-file-compile.png)

## <a name="run-cmake-from-the-command-line"></a>Ausführen von CMake über die Befehlszeile

Wenn Sie CMake über den Visual Studio-Installer installiert haben, können Sie CMake über die Befehlszeile ausführen, indem Sie die folgenden Schritte ausführen:

1. Führen Sie die entsprechende Datei „vsdevcmd.bat“ (x86/x64) aus. Weitere Informationen finden Sie unter [Erstellen über die Befehlszeile](building-on-the-command-line.md).

1. Wechseln Sie zu Ihrem Ausgabeordner.

1. Führen Sie CMake zum Erstellen/Konfigurieren Ihrer App aus.

::: moniker-end

::: moniker range="vs-2015"

In Visual Studio 2015 können Visual Studio-Benutzer einen [CMake-Generator](https://cmake.org/cmake/help/latest/manual/cmake-generators.7.html) verwenden, um MSBuild-Projektdateien zu generieren, die anschließend von der IDE für IntelliSense sowie für das Durchsuchen und die Kompilierung verwendet werden.

::: moniker-end

## <a name="see-also"></a>Siehe auch

[Tutorial: Erstellen plattformübergreifender C++-Projekte in Visual Studio](get-started-linux-cmake.md)\
[Konfigurieren eines Linux CMake-Projekts](../linux/cmake-linux-project.md)\
[Herstellen einer Verbindung mit Ihrem Linux-Remotecomputer](../linux/connect-to-your-remote-linux-computer.md)\
[Anpassen von CMake-Buildeinstellungen](customize-cmake-settings.md)\
[CMakeSettings.json-Schemareferenz](cmakesettings-reference.md)\
[Konfigurieren von CMake-Debugsitzungen](configure-cmake-debugging-sessions.md)\
[Bereitstellen, Ausführen und Debuggen Ihres Linux-Projekts](../linux/deploy-run-and-debug-your-linux-project.md)\
[CMake predefined configuration reference (Referenz für vordefinierte CMake-Konfigurationen)](cmake-predefined-configuration-reference.md)
