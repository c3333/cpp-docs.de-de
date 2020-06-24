---
title: Konfigurieren eines C++ Projekts unter Linux in Visual Studio
ms.date: 06/22/2020
ms.assetid: 4d7c6adf-54b9-4b23-bd23-5de0c825b768
ms.openlocfilehash: 6bc38e925e366804c8fe37604066b7cc20e04f15
ms.sourcegitcommit: f9344b09a734e8b05a7494415991a22b7aec5ae8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/23/2020
ms.locfileid: "85269740"
---
# <a name="configure-a-linux-project"></a>Konfigurieren eines Linux-Projekts

::: moniker range="vs-2015"

Die Unterstützung für Linux ist in Visual Studio 2017 und höher verfügbar.

::: moniker-end

In diesem Thema wird das Konfigurieren eines C++-Linux-Projekts beschrieben. Den entsprechenden Artikel finden Sie unter [Create a new C++ Linux project in Visual Studio (Erstellen eines neuen C++-Linux-Projekts in Visual Studio)](create-a-new-linux-project.md). Informationen zu CMake-Linux-Projekten finden Sie unter [Konfigurieren eines Linux-CMake-Projekts](cmake-linux-project.md).

Sie können ein Linux-Projekt so konfigurieren, dass dieses auf einen physischen Linux-Computer, einen virtuellen Computer oder das [Windows-Subsystem für Linux](/windows/wsl/about) (WSL) abzielt.

::: moniker range="vs-2019"

**Visual Studio 2019 Version 16.1:**

- Für das Windows-Subsystem für Linux können Sie die Kopiervorgänge vermeiden, die für die Erstellung und IntelliSense erforderlich sind, wenn auf Linux-Remotesysteme abgezielt wird.

- Sie können separate Linux-Ziele zum Erstellen und Debuggen angeben.

::: moniker-end

## <a name="general-settings"></a>Allgemeine Einstellungen

Wählen Sie zum Anzeigen von Konfigurationsoptionen das Menü **Projekt > Eigenschaften** aus, oder klicken Sie mit der rechten Maustaste auf das Projekt im **Projektmappen-Explorer**, und wählen Sie dann **Eigenschaften** aus dem Kontextmenü aus: Die **allgemeinen** Einstellungen werden angezeigt.

![Allgemeine Konfiguration](media/settings_general.png)

Standardmäßig wird eine ausführbare Datei (.out) erstellt. Verwenden Sie zum Erstellen einer statischen oder dynamischen Bibliothek entweder die Einstellung **Konfigurationstyp** oder eine vorhandene Makefile-Datei.

Weitere Informationen zu den Einstellungen auf den Eigenschaftenseiten finden Sie unter [Linux Project Property Page Reference (Referenz zur Linux-Projekteigenschaftenseite)](prop-pages-linux.md).

## <a name="remote-settings"></a>Remoteeinstellungen

Konfigurieren Sie die Remoteeinstellungen, die unter [Allgemein](prop-pages/general-linux.md) angezeigt werden, um die Einstellungen für den Linux-Remotecomputer zu ändern.

- Verwenden Sie den **Remotebuildcomputer**, um einen Linux-Remotezielcomputer anzugeben. Dadurch können Sie eine der zuvor erstellten Verbindungen auswählen. Weitere Informationen zum Erstellen eines neuen Eintrags finden Sie im Abschnitt [Connecting to Your Remote Linux Computer (Herstellen einer Verbindung mit Ihrem Linux-Remotecomputer)](connect-to-your-remote-linux-computer.md).

   ![Buildcomputer](media/remote-build-machine-vs2019.png)

   ::: moniker range="vs-2019"

   **Visual Studio 2019 Version 16.1:** Klicken Sie für das **Plattformtoolset** auf die NACH-UNTEN-TASTE, und wählen Sie **WSL_1_0** aus, um auf das Windows-Subsystem für Linux abzuzielen. Die anderen Remoteoptionen werden ausgeblendet, und der Pfad zur standardmäßigen WSL-Shell wird stattdessen angezeigt:

   ![WSL-Buildcomputer](media/wsl-remote-vs2019.png)

   Wenn Sie über parallele WSL-Installationen verfügen, können Sie hier einen anderen Pfad angeben. Weitere Informationen zum Verwalten von mehreren Distributionen finden Sie unter [Manage and configure Windows Subsystem for Linux (Verwalten und Konfigurieren von Windows-Subsystem für Linux)](/windows/wsl/wsl-config#set-a-default-distribution).

   Auf der Seite **Konfigurationseigenschaften** > **Debuggen** können Sie ein anderes Ziel für das Debuggen angeben.

   ::: moniker-end

- Das **Remotebuild-Stammverzeichnis** bestimmt das Stammverzeichnis, in dem das Projekt auf dem Linux-Remotecomputer erstellt wird. Standardmäßig handelt es sich dabei um **~/projects**, sofern nicht anders angegeben.

- Das **Remotebuild-Projektverzeichnis** ist das Verzeichnis, in dem dieses spezifische Projekt auf dem Linux-Remotecomputer erstellt wird. Standardmäßig handelt es sich dabei um das Verzeichnis **$(RemoteRootDir)/$(ProjektName)** . Es wird zu einem Verzeichnis erweitert, das den Namen des aktuellen Projekts unter dem oben angegebenen Stammverzeichnis trägt.

> [!NOTE]
> Verwenden Sie zum Ändern der C- und C++-Standardcompiler bzw. der Linker und Archivierungsprogramme, die zur Erstellung des Projekts verwendet werden, die entsprechenden Einträge im Abschnitt **C/C++ > Allgemein** sowie im Abschnitt **Linker > Allgemein**. Sie können beispielsweise eine bestimmte Version von GCC (GNU Compiler Collection) oder Clang angeben. Weitere Informationen finden Sie unter [C/C++-Eigenschaften (Linux C++)](prop-pages/c-cpp-linux.md) und [Linkereigenschaften (Linux C++)](prop-pages/linker-linux.md).

## <a name="copy-sources-remote-systems-only"></a>Kopieren von Quellen (nur Remotesysteme)

::: moniker range="vs-2019"

Dieser Abschnitt gilt nicht, wenn auf WSL abgezielt wird.

::: moniker-end

Beim Erstellen auf Remotesystemen werden die Quelldateien auf Ihrem Entwicklungs-PC auf den Linux-Computer kopiert und dort kompiliert. Standardmäßig werden alle Datenquellen im Visual Studio-Projekt an die Speicherorte kopiert, die in den oben genannten Einstellungen festgelegt wurden. Zusätzliche Quellen können ebenfalls zur Liste hinzugefügt werden und das Kopieren von Datenquellen kann vollständig deaktiviert werden, was der Standardeinstellung für Makefile-Projekt entspricht.

- **Zu kopierende Quellen** legt fest, welche Quellen auf den Remotecomputer kopiert werden. Standardmäßig bezieht **\@(RemoteZuKopierendeQuellen)** alle Quellcodedateien im Projekt, jedoch keine Asset-/Ressourcendateien wie beispielsweise Bilder ein.

- **Quellen kopieren** kann aktiviert und deaktiviert werden und kann damit das Kopieren von Quelldateien auf den Remotecomputer aktivieren bzw. deaktivieren.

- Mit **Weitere zu kopierende Quellen** können Sie zusätzliche Quelldateien hinzufügen, die anschließend auf das Remotesystem kopiert werden. Sie können eine durch Semikolons getrennte Liste angeben, oder Sie können die Syntax **: =** verwenden, um einen lokalen und einen Remote-Namen anzugeben:

`C:\Projects\ConsoleApplication1\MyFile.cpp:=~/projects/ConsoleApplication1/ADifferentName.cpp;C:\Projects\ConsoleApplication1\MyFile2.cpp:=~/projects/ConsoleApplication1/ADifferentName2.cpp;`

## <a name="build-events"></a>Buildereignisse

Da die gesamte Kompilierung auf einem Remotecomputer (oder WSL) erfolgt, wurden dem Abschnitt „Buildereignisse“ in den Projekteigenschaften mehrere zusätzliche Buildereignisse hinzugefügt. Dazu gehören das **Remote-Präbuildereignis**, das **Remote-Prälinkereignis** und das **Remote-Postbuildereignis**. Diese Ereignisse finden auf dem Remotecomputer vor oder nach den einzelnen Schritten im Prozess statt.

![Buildereignisse](media/settings_buildevents.png)

## <a name="intellisense-for-headers-on-remote-systems"></a><a name="remote_intellisense"></a> IntelliSense für Header auf Remotesystemen

Beim Hinzufügen einer neuen Verbindung im **Verbindungs-Manager** erkennt Visual Studio automatisch die Includeverzeichnisse für den Compiler auf dem Remotesystem. Visual Studio komprimiert diese Dateien dann und kopiert sie in ein Verzeichnis auf dem lokalen Windows-Computer. Wenn Sie anschließend diese Verbindung in Visual Studio oder CMake nutzen, wird mithilfe der Header in diesen Verzeichnissen IntelliSense bereitgestellt.

> [!NOTE]
> In Visual Studio 2019, Version 16.5 und höher, wurde die Remoteheaderkopie optimiert. Header werden nun bedarfsgesteuert kopiert, wenn ein Linux-Projekt geöffnet oder CMake für ein Linux-Ziel konfiguriert wird. Der Kopiervorgang erfolgt pro Projekt und im Hintergrund, basierend auf den angegebenen Compilern des Projekts. Weitere Informationen finden Sie unter [Improvements to Accuracy and Performance of Linux IntelliSense](https://devblogs.microsoft.com/cppblog/improvements-to-accuracy-and-performance-of-linux-intellisense/) (Verbesserung der Genauigkeit und Leistung von Linux IntelliSense).

Diese Funktion hängt davon ab, ob auf dem Linux-Computer Zip installiert ist. Sie können Zip mit diesem apt-get-Befehl installieren:

```cmd
sudo apt install zip
```

Navigieren Sie zum Verwalten Ihres Header-Caches zu **Extras > Optionen > Plattformübergreifend > Verbindungs-Manager > IntelliSense-Manager für Remoteheader**. Wählen Sie zum Aktualisieren des Header-Caches nach Änderungen auf dem Linux-Computer die Remoteverbindung aus, und klicken Sie dann auf **Aktualisieren**. Klicken Sie auf **Löschen**, um die Header zu entfernen, ohne die Verbindung selbst zu löschen. Klicken Sie auf **Erkunden**, um das lokale Verzeichnis im **Datei-Explorer** zu öffnen. Behandeln Sie diesen Ordner, als sei er schreibgeschützt. Wählen Sie zum Herunterladen von Headern für eine vorhandene Verbindung, die vor Version 15.3 von Visual Studio 2017 erstellt wurde, die Verbindung aus, und klicken Sie dann auf **Herunterladen**.

::: moniker range="vs-2017"

![IntelliSense-Remoteheader](media/remote-header-intellisense.png)

::: moniker-end

::: moniker range="vs-2019"

![IntelliSense-Remoteheader](media/connection-manager-vs2019.png)

Sie können die Protokollierung aktivieren, um Probleme zu beheben:

![Remoteprotokollierung](media/remote-logging-vs2019.png)

::: moniker-end

## <a name="linux-target-locale"></a><a name="locale"></a> Linux-Zielgebietsschema

Visual Studio-Spracheinstellungen werden nicht an Linux-Ziele weitergegeben, da Visual Studio installierte Pakete nicht verwaltet oder konfiguriert. Nachrichten, die im **Ausgabefenster** angezeigt werden (z. B. Buildfehler), werden mit der Sprache und dem Gebietsschema des Linux-Ziels angezeigt. Sie müssen Ihre Linux-Ziele für das gewünschte Gebietsschema konfigurieren.

## <a name="see-also"></a>Siehe auch

[Festlegen der Compiler- und Buildeigenschaften](../build/working-with-project-properties.md)<br/>
[Allgemeine C++-Eigenschaften (Linux C++)](prop-pages/general-linux.md)<br/>
[VC++-Verzeichnisse (Linux C++)](prop-pages/directories-linux.md)<br/>
[Kopieren von Quellprojekteigenschaften (Linux C++)](prop-pages/copy-sources-project.md)<br/>
[Buildereigniseigenschaften (Linux C++)](prop-pages/build-events-linux.md)
