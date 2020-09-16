---
title: Erstellen plattformübergreifender C++-Projekte in Visual Studio
description: Hier erfahren Sie, wie Sie ein Open Source-CMake-Projekt in C++ in Visual Studio für Linux und Windows erstellen, kompilieren und debuggen können.
ms.topic: tutorial
ms.date: 01/08/2020
ms.openlocfilehash: 3fdd9b1dfb5075f3a71f62bc4f1e2f3c646f9e6b
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/12/2020
ms.locfileid: "90040482"
---
# <a name="tutorial-create-c-cross-platform-projects-in-visual-studio"></a>Tutorial: Erstellen plattformübergreifender C++-Projekte in Visual Studio

Die Entwicklung mit C und C++ in Visual Studio eignet sich nicht nur für Windows-Anwendungen. In diesem Tutorial erfahren Sie, wie Sie Visual Studio für plattformübergreifende C++-Entwicklung für Windows und Linux verwenden. Da CMake die Grundlage dieses Tutorials darstellt, müssen Sie keine Visual Studio-Projekte erstellen oder generieren. Wenn Sie einen Ordner öffnen, der die Datei „CMakeLists.txt“ enthält, konfiguriert Visual Studio automatisch die IntelliSense- und Buildeinstellungen. Sie können umgehend damit beginnen, Ihren Code lokal unter Windows zu bearbeiten, zu erstellen und zu debuggen. Anschließend ändern Sie Ihre Konfiguration, um dasselbe für Linux ausschließlich über Visual Studio durchzuführen.

In diesem Tutorial lernen Sie, wie die folgenden Aufgaben ausgeführt werden:

> [!div class="checklist"]
>
> * Klonen eines Open Source-CMake-Projekts über GitHub
> * Öffnen des Projekts in Visual Studio
> * Erstellen und Debuggen eines ausführbaren Ziels unter Windows
> * Hinzufügen einer Verbindung zu einem Linux-Computer
> * Erstellen und Debuggen des gleichen Ziels unter Linux

## <a name="prerequisites"></a>Voraussetzungen

* Einrichten von Visual Studio für die plattformübergreifende C++-Entwicklung
  * Zunächst [installieren Sie Visual Studio](https://visualstudio.microsoft.com/vs/) und wählen dabei die Workloads **Desktopentwicklung mit C++** und **Linux-Entwicklung mit C++** aus. Diese Installation mit den mindestens erforderlichen Komponenten ist nur 3 GB groß. Je nach Downloadgeschwindigkeit sollte die Installation also nicht länger als 10 Minuten dauern.

* Einrichten eines Linux-Computers für die plattformübergreifende C++-Entwicklung
  * Visual Studio erfordert keine bestimmte Linux-Distribution. Das Betriebssystem kann auf einem physischen Computer, einer VM (virtueller Computer) oder in der Cloud ausgeführt werden. Sie können auch das Windows-Subsystem für Linux verwenden. Für dieses Tutorial ist jedoch eine grafische Umgebung erforderlich. Das Windows-Subsystem für Linux wird hier nicht empfohlen, weil es hauptsächlich für Befehlszeilenvorgänge vorgesehen ist.
  * Visual Studio erfordert die folgenden Tools auf dem Linux-Computer: C++-Compiler, gdb, ssh, rsync, ninja und zip. Aus Systemen, die auf Debian basieren, können Sie den folgenden Befehl verwenden, um diese Abhängigkeiten zu installieren:

    ```cmd
    sudo apt install -y openssh-server build-essential gdb rsync ninja-build zip
    ```

  * Visual Studio erfordert eine aktuelle Version von CMake auf dem Linux-Computer, in der der Servermodus aktiviert ist (mindestens 3.8). Microsoft gibt einen universellen CMake-Build heraus, den Sie auf allen Linux-Distributionen veröffentlichen können. Es wird empfohlen, dass Sie diesen Build verwenden, damit Sie über die neuesten Features verfügen. Sie können die CMake-Binärdateien aus dem [Microsoft-Fork des CMake-Repositorys](https://github.com/Microsoft/CMake/releases) auf GitHub herunterladen. Rufen Sie diese Seite auf, laden Sie die Version herunter, die mit der Systemarchitektur auf Ihrem Linux-Computer übereinstimmt, und markieren Sie diese als ausführbare Datei:

    ```cmd
    wget <path to binary>
    chmod +x cmake-3.11.18033000-MSVC_2-Linux-x86_64.sh
    ```

  * Sie sehen die Optionen zum Ausführen des Skripts mit `-–help`. Es wird empfohlen, dass Sie die Option `–prefix` verwenden, um die Installation im Pfad **/usr** durchzuführen, da **/usr/bin** der Standardspeicherort ist, an dem Visual Studio nach CMake sucht. Im folgenden Beispiel sehen Sie das Linux-x86_64-Skript. Passen Sie dieses nach Bedarf an, wenn Sie eine andere Zielplattform verwenden.

    ```cmd
    sudo ./cmake-3.11.18033000-MSVC_2-Linux-x86_64.sh --skip-license --prefix=/usr
    ```

* Auf Ihrem Windows-Computer muss Git für Windows installiert sein.
* Ein GitHub-Konto.

## <a name="clone-an-open-source-cmake-project-from-github"></a>Klonen eines Open Source-CMake-Projekts über GitHub

In diesem Tutorial wird das Bullet Physics SDK auf GitHub verwendet. Dieses bietet Kollisionserkennung und Physiksimulationen für viele Anwendungszwecke. Das SDK enthält ausführbare Beispielprogramme, die kompiliert und ausgeführt werden können, ohne zusätzlichen Code schreiben zu müssen. In diesem Tutorial wird der Quellcode nicht angepasst und es werden keine Skripts erstellt. Klonen Sie zunächst das Repository *bullet3* von GitHub auf den Computer, auf dem Visual Studio installiert ist.

```cmd
git clone https://github.com/bulletphysics/bullet3.git
```

1. Klicken Sie im Hauptmenü von Visual Studio auf **Datei > Öffnen > CMake**. Navigieren Sie im Stammverzeichnis des eben heruntergeladenen Bullet3-Repositorys zur Datei „CMakeLists.txt“.

    ![Visual Studio-Menü „Datei > Öffnen > CMake“](media/cmake-open-cmake.png)

    Wenn Sie den Ordner öffnen, wird Ihre Ordnerstruktur im **Projektmappen-Explorer** angezeigt.

    ![Ordneransicht im Projektmappen-Explorer von Visual Studio](media/cmake-bullet3-solution-explorer.png)

    In dieser Ansicht sehen Sie genau, was sich auf dem Datenträger befindet. Die Ansicht ist nicht logisch oder gefiltert. Standardmäßig werden keine ausgeblendeten Dateien angezeigt.

1. Klicken Sie auf **Alle Dateien anzeigen**, um alle Dateien im Ordner anzuzeigen.

    ![Schaltfläche zum Anzeigen aller Dateien im Projektmappen-Explorer von Visual Studio](media/cmake-bullet3-show-all-files.png)

## <a name="switch-to-targets-view"></a>Wechseln zur Zielansicht

Wenn Sie einen Ordner öffnen, der CMake verwendet, generiert Visual Studio automatisch einen CMake-Cache. Je nach Größe des Projekts kann dieser Vorgang etwas Zeit in Anspruch nehmen.

1. Wählen Sie im **Ausgabefenster** **Ausgabe anzeigen von:** aus, und wählen Sie dann **CMake**, um den Status der Cacheerstellung zu überwachen. Sobald der Vorgang abgeschlossen ist, wird „Extrahieren von Zielinformationen abgeschlossen.“ angezeigt.

   ![Visual Studio-Ausgabefenster mit Ausgabe aus CMake](media/cmake-bullet3-output-window.png)

   Nach Abschluss dieses Vorgangs ist IntelliSense konfiguriert. Sie können das Projekt erstellen und die Anwendung debuggen. Visual Studio zeigt jetzt eine logische Ansicht der Projektmappe basierend auf den Zielen an, die in den CMakeLists-Dateien angegeben werden.

1. Über die Schaltfläche für **Projektmappen und Ordner** im **Projektmappen-Explorer** können Sie zur CMake-Zielansicht wechseln.

   ![Schaltfläche für Projektmappen und Ordner im Projektmappen-Explorer zum Wechseln zur CMake-Zielansicht](media/cmake-bullet3-show-targets.png)

   Die Ansicht für das Bullet Physics SDK sieht wie folgt aus:

   ![CMake-Zielansicht im Projektmappen-Explorer](media/cmake-bullet3-targets-view.png)

   Mit der Zielansicht erhalten Sie eine intuitivere Ansicht der Inhalte einer Quellbasis. Sie erkennen, dass einige Ziele Bibliotheken und andere ausführbare Dateien sind.

1. Erweitern Sie einen Knoten in der CMake-Zielansicht, um die Quellcodedateien anzuzeigen, egal wo sich diese auf dem Datenträger befinden.

## <a name="add-an-explicit-windows-x64-debug-configuration"></a>Hinzufügen einer expliziten Windows x64-Debug-Konfiguration

Visual Studio erstellt eine **x64-Debug**-Standardkonfiguration für Windows. Durch Konfigurationen wird festgelegt, welche Plattformziele von Visual Studio für CMake verwendet werden sollen. Die Standardkonfiguration ist standardmäßig nicht auf dem Datenträger vorhanden. Wenn Sie eine Konfiguration explizit hinzufügen, erstellt Visual Studio eine Datei namens *CMakeSettings.json*. Diese wird mit den Einstellungen für alle Konfigurationen aufgefüllt, die Sie festlegen.

1. Fügen Sie eine neue Konfiguration hinzu. Öffnen Sie das Dropdownmenü **Konfiguration** in der Symbolleiste, und wählen Sie dann **Konfigurationen verwalten** aus.

   ![Dropdownmenü „Konfigurationen verwalten“](media/cmake-bullet3-manage-configurations.png)

   Daraufhin wird der [Editor für CMake-Einstellungen](customize-cmake-settings.md) geöffnet. Klicken Sie auf das grüne Pluszeichen links neben dem Editor, um eine neue Konfiguration hinzuzufügen. Das Dialogfeld **Konfiguration zu CMakeSettings hinzufügen** wird angezeigt.

   ![Dialogfeld „Konfiguration zu CMakeSettings hinzufügen“](media/cmake-bullet3-add-configuration-x64-debug.png)

   In diesem Dialogfeld werden alle Konfigurationen angezeigt, die in Visual Studio enthalten sind, sowie alle benutzerdefinierten Konfigurationen, die Sie erstellt haben. Wenn Sie weiterhin die eine **x64-Debug**-Konfiguration verwenden möchten, sollten Sie diese zuerst hinzufügen. Wählen Sie **x64-Debug** aus, und klicken Sie dann auf **Auswählen**. Visual Studio erstellt die Datei „CMakeSettings.json“ mit einer Konfiguration für **x64-Debug** und speichert sie auf dem Datenträger. Sie können Ihre Konfigurationen beliebig benennen, indem Sie den Namensparameter direkt in „CMakeSettings.json“ ändern.

## <a name="set-a-breakpoint-build-and-run-on-windows"></a>Festlegen eines Breakpoints, Erstellen und Ausführen unter Windows

In diesem Schritt debuggen wir ein Beispielprogramm, das die Bullet Physics-Bibliothek veranschaulicht.
  
1. Wählen Sie „AppBasicExampleGui“ im **Projektmappen-Explorer**, und erweitern Sie es.

1. Öffnen Sie die Datei `BasicExample.cpp`.

1. Legen Sie einen Breakpoint fest, der erreicht werden soll, wenn Sie in der ausgeführten Anwendung klicken. Das Klickereignis wird in einer Methode in einer Hilfsklasse behandelt. Führen Sie folgende Schritte aus, um schnell dorthin zu gelangen:

   1. Wählen Sie das `CommonRigidBodyBase`-Objekt, von dem die Struktur `BasicExample` abgeleitet wird. Dieses befindet sich etwa in Zeile 30.

   1. Klicken Sie mit der rechten Maustaste, und wählen Sie **Gehe zu Definition**. Sie befinden sich nun im Header „CommonRigidBodyBase.h“.

   1. In der Browseransicht über Ihrer Quelle sollten Sie sehen, dass Sie sich in `CommonRigidBodyBase` befinden. Rechts können Sie Member auswählen, die Sie sich genauer ansehen möchten. Öffnen Sie das Dropdownmenü, und wählen Sie `mouseButtonCallback` aus, um zur Definition dieser Funktion im Header zu wechseln.

      ![Symbolleiste der Memberliste in Visual Studio](media/cmake-bullet3-member-list-toolbar.png)

1. Setzen Sie in der ersten Zeile dieser Funktion einen Breakpoint. Dieser wird erreicht, wenn Sie im Fenster der Anwendung einen Mausklick ausführen, wenn die Anwendung im Visual Studio-Debugger ausgeführt wird.

1. Klicken Sie auf das Startdropdownmenü in der Symbolleiste, um die Anwendung zu starten. Dieses enthält ein grünes Wiedergabesymbol und die Beschriftung „Startelement auswählen“. Wählen im Dropdownmenü „AppBasicExampleGui.exe“ aus. Der Name der ausführbaren Datei wird jetzt auf der Startschaltfläche angezeigt:

   ![Startdropdownmenü auf der Symbolleiste von Visual Studio für „Startelement auswählen“](media/cmake-bullet3-launch-button.png)

1. Klicken Sie auf „Starten“, um die Anwendung und die erforderlichen Abhängigkeiten zu erstellen, und starten Sie sie dann mit angefügtem Visual Studio-Debugger. Nach kurzer Zeit wird die ausgeführte Anwendung angezeigt:

   ![Debugging einer Windows-Anwendung in Visual Studio](media/cmake-bullet3-launched.png)

1. Bewegen Sie den Mauszeiger in das Anwendungsfenster, und drücken Sie anschließend eine Taste, um den Breakpoint auszulösen. Durch den Breakpoint wird Visual Studio wieder im Vordergrund angezeigt, und der Editor zeigt die Zeile an, in der die Ausführung pausiert wurde. Sie können die Variablen, Objekte, Threads und den Speicher der Anwendung untersuchen oder Ihren Code interaktiv in Einzelschritten durchlaufen. Klicken Sie auf **Fortfahren**, damit die Anwendung fortgesetzt wird, und beenden Sie sie dann auf herkömmliche Weise. Alternativ können Sie die Ausführung in Visual Studio mithilfe der Stoppschaltfläche anhalten.

## <a name="add-a-linux-configuration-and-connect-to-the-remote-machine"></a>Hinzufügen einer Linux-Konfiguration und Verbinden mit dem Remotecomputer

1. Fügen Sie eine Linux-Konfiguration hinzu. Klicken Sie mit der rechten Maustaste im **Projektmappen-Explorer** auf die Datei „CMakeSettings.json“, und wählen Sie **Konfiguration hinzufügen** aus. Das Dialogfeld „Konfiguration zu CMakeSettings hinzufügen“ wird geöffnet, das Sie schon aus dem vorherigen Schritt kennen. Wählen Sie dieses Mal **Linux-Debug** aus, und speichern (STRG + S) Sie die Datei „CMakeSettings.json“.

1. Wählen Sie **Linux-Debug** aus dem Dropdownmenü aus.

   ![Konfigurationsdropdownmenü mit den Optionen x64-Debug und Linux-Debug](media/cmake-bullet3-linux-configuration-item.png)

   Wenn Sie zum ersten Mal eine Verbindung mit einem Linux-System herstellen, wird das Dialogfeld **Mit Remotesystem verbinden** angezeigt.

   ![Dialogfeld „Mit Remotesystem verbinden“ in Visual Studio](media/cmake-bullet3-connection-manager.png)

   Wenn Sie bereits eine Remoteverbindung hinzugefügt haben, können Sie das Fenster über **Extras > Optionen > Plattformübergreifend > Verbindungs-Manager > Hinzufügen** öffnen.

1. Geben Sie die [Verbindungsinformationen Ihres Linux-Computers](../linux/connect-to-your-remote-linux-computer.md) ein, und klicken Sie anschließend auf **Verbinden**. Visual Studio fügt diesen Computer in „CMakeSettings.json“ als Standardverbindung für **Linux-Debug** hinzu. Außerdem werden die Header von Ihrem Remotecomputer abgerufen, damit Sie [spezifische IntelliSense-Funktionen für diese Remoteverbindung](../linux/configure-a-linux-project.md#remote_intellisense) verwenden können. Anschließend sendet Visual Studio Ihre Dateien an den Remotecomputer und generiert den CMake-Cache auf dem Remotesystem. Diese Schritte können abhängig von der Netzwerkgeschwindigkeit und der Leistung Ihres Remotecomputers einige Zeit in Anspruch nehmen. Der Vorgang ist abgeschlossen, wenn im CMake-Ausgabefenster „Extrahieren von Zielinformationen abgeschlossen“ angezeigt wird.

## <a name="set-a-breakpoint-build-and-run-on-linux"></a>Festlegen eines Breakpoints, Erstellen und Ausführen unter Linux

Da es sich um eine Desktopanwendung handelt, müssen Sie weitere Konfigurationsinformationen für die Debugkonfiguration angeben.

1. Klicken Sie in der CMake-Zielansicht mit der rechten Maustaste auf „AppBasicExampleGui“, und wählen Sie **Einstellungen für Debuggen und Starten** aus, um die Datei „launch.vs.json“ zu öffnen, die sich im versteckten **.vs**-Unterordner befindet. Diese Datei befindet sich lokal in Ihrer Entwicklungsumgebung. Sie können sie zum Stamm Ihres Projekts verschieben, wenn Sie sie bei Ihrem Team einchecken und speichern möchten. In dieser Datei wurde eine Konfiguration für „AppBasicExampleGui“ hinzugefügt. Diese Standardeinstellungen funktionieren in den meisten Fällen, jedoch nicht in diesem Fall. Da es sich hier um eine Desktopanwendung handelt, müssen Sie zusätzliche Informationen zum Starten des Programms angeben, damit es auf Ihrem Linux-Computer angezeigt wird.

1. Führen Sie den folgenden Befehl aus, um den Wert für die Umgebungsvariable `DISPLAY` auf Ihrem Linux-Computer zu finden:

   ```cmd
   echo $DISPLAY
   ```

   In der Konfiguration für „AppBasicExampleGui“ gibt es das Parameterarray „pipeArgs“. Dieses enthält die Zeile: „${debuggerCommand}“. Mit diesem Befehl wird gdb auf dem Remotecomputer gestartet. Visual Studio muss die Anzeige in diesen Kontext exportieren, bevor dieser Befehl ausgeführt wird. Wenn der Wert Ihrer Anzeige beispielsweise `:1` ist, passen Sie die Zeile wie folgt an:

   ```cmd
   "export DISPLAY=:1;${debuggerCommand}",
   ```

1. Starten und debuggen Sie Ihre Anwendung. Öffnen Sie das Dropdownmenü **Startelement auswählen** in der Symbolleiste, und wählen Sie dann **AppBasicExampleGui** aus. Klicken Sie dann auf das grüne Wiedergabesymbol in der Symbolleiste, oder drücken Sie **F5**. Die Anwendung und ihre Abhängigkeiten werden auf dem Linux-Remotecomputer erstellt und dann mit angefügtem Visual Studio-Debugger gestartet. Auf Ihrem Linux-Remotecomputer sollte ein Anwendungsfenster geöffnet werden.

1. Bewegen Sie Ihren Mauszeiger in das Anwendungsfenster, und drücken Sie eine Taste. Daraufhin wird der Breakpoint erreicht. Die Ausführung des Programms wird am Breakpoint angehalten, und Visual Studio wird wieder im Vordergrund angezeigt. Außerdem sollte ein Linux-Konsolenfenster in Visual Studio angezeigt werden. In diesem Fenster wird die Ausgabe des Linux-Computers angezeigt, und es kann auch Eingaben für `stdin` akzeptieren. Dieses Fenster können Sie wie jedes andere Visual Studio-Fenster wie gewünscht andocken. Die Position des Fensters wird in zukünftigen Sitzungen beibehalten.

   ![Linux-Konsolenfenster in Visual Studio](media/cmake-bullet3-linux-console.png)

1. Sie können sich die Variablen, Objekte, Threads und den Arbeitsspeicher der Anwendung ansehen und Ihren Code in Visual Studio schrittweise und interaktiv ausführen. Dieses Mal führen Sie diese Schritt jedoch auf einem Linux-Remotecomputer statt in einer lokalen Windows-Umgebung aus. Sie können auf **Weiter** klicken, um die Ausführung der Anwendung normal fortzusetzen und zu beenden, oder Sie können die Ausführung mit der Stoppschaltfläche abbrechen, wie Sie es auch bei der lokalen Ausführung tun würden.

1. Sehen Sie sich das Aufruflistenfenster an, und zeigen Sie die Aufrufe von `x11OpenGLWindow` seit dem Start der Anwendung durch Visual Studio auf dem Linux-Computer an.

   ![Fenster „Aufrufliste“ mit der Linux-Aufrufliste](media/cmake-bullet3-linux-callstack.png)

## <a name="what-you-learned"></a>Zusammenfassung

In diesem Tutorial haben Sie eine Codebasis direkt von GitHub geklont. Diese haben Sie ohne Änderungen unter Windows erstellt, ausgeführt und gedebuggt. Dieselbe Codebasis haben Sie dann mit geringfügigen Änderungen an der Konfiguration auf einem Linux-Remotecomputer erstellt, ausgeführt und gedebuggt.

## <a name="next-steps"></a>Nächste Schritte

In den folgenden Artikeln erhalten Sie weitere Informationen zum Konfigurieren und Debuggen von CMake-Projekten in Visual Studio:

> [!div class="nextstepaction"]
> [CMake Projects in Visual Studio (CMake-Projekte in Visual Studio)](cmake-projects-in-visual-studio.md)<br/><br/>
> [Konfigurieren eines Linux CMake-Projekts](../linux/cmake-linux-project.md)<br/><br/>
> [Herstellen einer Verbindung mit Ihrem Linux-Remotecomputer](../linux/connect-to-your-remote-linux-computer.md)<br/><br/>
> [Anpassen von CMake-Buildeinstellungen](customize-cmake-settings.md)<br/><br/>
> [Konfigurieren von CMake-Debugsitzungen](configure-cmake-debugging-sessions.md)<br/><br/>
> [Bereitstellen, Ausführen und Debuggen Ihres Linux-Projekts](../linux/deploy-run-and-debug-your-linux-project.md)<br/><br/>
> [CMake predefined configuration reference (Referenz für vordefinierte CMake-Konfigurationen)](cmake-predefined-configuration-reference.md)
>
