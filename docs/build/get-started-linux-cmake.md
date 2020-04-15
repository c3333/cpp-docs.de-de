---
title: Erstellen plattformübergreifender C++-Projekte in Visual Studio
description: Einrichten, Kompilieren und Debuggen eines C++-Open-Source-CMake-Projekts in Visual Studio, das sowohl auf Linux als auch auf Windows abzielt.
ms.topic: tutorial
ms.date: 01/08/2020
ms.openlocfilehash: aac536f488cf22adf5aa835c9fe5b884fc5d7298
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328746"
---
# <a name="tutorial-create-c-cross-platform-projects-in-visual-studio"></a>Tutorial: Erstellen von c++-plattformübergreifenden Projekten in Visual Studio

Die Entwicklung mit C und C++ in Visual Studio eignet sich nicht nur für Windows-Anwendungen. In diesem Tutorial wird gezeigt, wie Visual Studio für C++-Plattformübergreifende Entwicklung unter Windows und Linux verwendet wird. Es basiert auf CMake, sodass Sie keine Visual Studio-Projekte erstellen oder generieren müssen. Wenn Sie einen Ordner öffnen, der eine CMakeLists.txt-Datei enthält, konfiguriert Visual Studio die IntelliSense- und Buildeinstellungen automatisch. Sie können schnell mit dem Bearbeiten, Erstellen und Debuggen des Codes lokal unter Windows beginnen. Wechseln Sie dann Ihre Konfiguration, um dasselbe unter Linux zu tun, und zwar alle in Visual Studio.

In diesem Tutorial lernen Sie Folgendes:

> [!div class="checklist"]
>
> * Klonen eines Open Source-CMake-Projekts über GitHub
> * Öffnen des Projekts in Visual Studio
> * Erstellen und Debuggen eines ausführbaren Ziels unter Windows
> * Hinzufügen einer Verbindung zu einem Linux-Computer
> * Erstellen und Debuggen des gleichen Ziels unter Linux

## <a name="prerequisites"></a>Voraussetzungen

* Einrichten von Visual Studio für die plattformübergreifende C++-Entwicklung
  * Installieren Sie zunächst [Visual Studio,](https://visualstudio.microsoft.com/vs/) und wählen Sie die **Desktopentwicklung mit C++-** und **Linux-Entwicklung mit C++-Workloads**aus. Diese minimale Installation beträgt nur 3 GB. Je nach Download-Geschwindigkeit sollte die Installation nicht mehr als 10 Minuten dauern.

* Einrichten eines Linux-Computers für die plattformübergreifende C++-Entwicklung
  * Visual Studio erfordert keine bestimmte Linux-Distribution. Das Betriebssystem kann auf einem physischen Computer, auf einer VM oder in der Cloud ausgeführt werden. Sie können auch das Windows Subsystem für Linux (WSL) verwenden. Für dieses Tutorial ist jedoch eine grafische Umgebung erforderlich. WSL wird hier nicht empfohlen, da es in erster Linie für Befehlszeilenoperationen gedacht ist.
  * Visual Studio benötigt diese Tools auf dem Linux-Computer: C++-Compiler, gdb, ssh, rsync, ninja und zip. Auf Debian-basierten Systemen können Sie diesen Befehl verwenden, um diese Abhängigkeiten zu installieren:

    ```cmd
    sudo apt install -y openssh-server build-essential gdb rsync ninja-build zip
    ```

  * Visual Studio erfordert eine aktuelle Version von CMake auf dem Linux-Computer, auf dem der Servermodus aktiviert ist (mindestens 3.8). Microsoft gibt einen universellen CMake-Build heraus, den Sie auf allen Linux-Distributionen veröffentlichen können. Es wird empfohlen, diesen Build zu verwenden, um sicherzustellen, dass Sie über die neuesten Funktionen verfügen. Sie können die CMake-Binärdateien aus dem [Microsoft-Fork des CMake-Repositorys](https://github.com/Microsoft/CMake/releases) auf GitHub herunterladen. Gehen Sie zu dieser Seite, und laden Sie die Version herunter, die der Systemarchitektur auf Ihrem Linux-Computer entspricht, und markieren Sie sie dann als ausführbare Datei:

    ```cmd
    wget <path to binary>
    chmod +x cmake-3.11.18033000-MSVC_2-Linux-x86_64.sh
    ```

  * Sie sehen die Optionen zum Ausführen des Skripts mit `-–help`. Es wird empfohlen, `–prefix` die Option zum Angeben der Installation im **/usr-Pfad** zu verwenden, da **/usr/bin** der Standardspeicherort ist, an dem Visual Studio nach CMake sucht. Im folgenden Beispiel sehen Sie das Linux-x86_64-Skript. Ändern Sie es nach Bedarf, wenn Sie eine andere Zielplattform verwenden.

    ```cmd
    sudo ./cmake-3.11.18033000-MSVC_2-Linux-x86_64.sh --skip-license --prefix=/usr
    ```

* Auf Ihrem Windows-Computer muss Git für Windows installiert sein.
* Ein GitHub-Konto.

## <a name="clone-an-open-source-cmake-project-from-github"></a>Klonen eines Open Source-CMake-Projekts über GitHub

In diesem Tutorial wird das Bullet Physics SDK auf GitHub verwendet. Es bietet Kollisionserkennung und Physiksimulationen für viele Anwendungen. Das SDK enthält ausführbare Beispielprogramme, die kompiliert und ausgeführt werden, ohne zusätzlichen Code schreiben zu müssen. In diesem Tutorial werden weder Quellcode noch Buildskripts geändert. Klonen Sie zunächst das *bullet3-Repository* von GitHub auf dem Computer, auf dem Visual Studio installiert ist.

```cmd
git clone https://github.com/bulletphysics/bullet3.git
```

1. Wählen Sie im Visual Studio-Hauptmenü **Datei > Öffnen > CMake**aus. Navigieren Sie zur Datei CMakeLists.txt im Stammverzeichnis des bullet3-Repositorys, das Sie gerade heruntergeladen haben.

    ![Visual Studio-Menü „Datei > Öffnen > CMake“](media/cmake-open-cmake.png)

    Sobald Sie den Ordner öffnen, wird Ihre Ordnerstruktur im **Projektmappen-Explorer**sichtbar.

    ![Ordneransicht im Projektmappen-Explorer von Visual Studio](media/cmake-bullet3-solution-explorer.png)

    In dieser Ansicht sehen Sie genau, was sich auf dem Datenträger befindet. Die Ansicht ist nicht logisch oder gefiltert. Standardmäßig werden keine ausgeblendeten Dateien angezeigt.

1. Wählen Sie die Schaltfläche **Alle Dateien anzeigen** aus, um alle Dateien im Ordner anzuzeigen.

    ![Schaltfläche zum Anzeigen aller Dateien im Projektmappen-Explorer von Visual Studio](media/cmake-bullet3-show-all-files.png)

## <a name="switch-to-targets-view"></a>Wechseln zur Zielansicht

Wenn Sie einen Ordner öffnen, der CMake verwendet, generiert Visual Studio automatisch einen CMake-Cache. Je nach Größe des Projekts kann dieser Vorgang etwas Zeit in Anspruch nehmen.

1. Wählen Sie im **Ausgabefenster****Ausgabe anzeigen von:** aus, und wählen Sie dann **CMake**, um den Status der Cacheerstellung zu überwachen. Sobald der Vorgang abgeschlossen ist, wird „Extrahieren von Zielinformationen abgeschlossen.“ angezeigt.

   ![Visual Studio-Ausgabefenster mit Ausgabe aus CMake](media/cmake-bullet3-output-window.png)

   Nach Abschluss dieses Vorgangs wird IntelliSense konfiguriert. Sie können das Projekt erstellen und die Anwendung debuggen. Visual Studio zeigt nun eine logische Ansicht der Projektmappe basierend auf den in den CMakeLists-Dateien angegebenen Zielen an.

1. Über die Schaltfläche für **Projektmappen und Ordner** im **Projektmappen-Explorer** können Sie zur CMake-Zielansicht wechseln.

   ![Schaltfläche für Projektmappen und Ordner im Projektmappen-Explorer zum Wechseln zur CMake-Zielansicht](media/cmake-bullet3-show-targets.png)

   Die Ansicht für das Bullet Physics SDK sieht wie folgt aus:

   ![CMake-Zielansicht im Projektmappen-Explorer](media/cmake-bullet3-targets-view.png)

   Mit der Zielansicht erhalten Sie eine intuitivere Ansicht der Inhalte einer Quellbasis. Sie erkennen, dass einige Ziele Bibliotheken und andere ausführbare Dateien sind.

1. Erweitern Sie einen Knoten in der CMake-Zielansicht, um die Quellcodedateien anzuzeigen, egal wo sich diese auf dem Datenträger befinden.

## <a name="add-an-explicit-windows-x64-debug-configuration"></a>Hinzufügen einer expliziten Windows x64-Debug-Konfiguration

Visual Studio erstellt eine **standardmäßige x64-Debug-Konfiguration** für Windows. Durch Konfigurationen wird festgelegt, welche Plattformziele von Visual Studio für CMake verwendet werden sollen. Die Standardkonfiguration ist standardmäßig nicht auf dem Datenträger vorhanden. Wenn Sie explizit eine Konfiguration hinzufügen, erstellt Visual Studio eine Datei mit dem Namen *CMakeSettings.json*. Es wird mit Einstellungen für alle von Ihnen angegebenen Konfigurationen aufgefüllt.

1. Fügen Sie eine neue Konfiguration hinzu. Öffnen Sie die Dropdown-Liste **Konfiguration** in der Symbolleiste, und wählen Sie **Konfigurationen verwalten**aus.

   ![Dropdownmenü „Konfigurationen verwalten“](media/cmake-bullet3-manage-configurations.png)

   Der [CMake-Einstellungs-Editor](customize-cmake-settings.md) wird geöffnet. Wählen Sie das grüne Pluszeichen auf der linken Seite des Editors aus, um eine neue Konfiguration hinzuzufügen. Das Dialogfeld **Konfiguration zu CMakeSettings** hinzufügen wird angezeigt.

   ![Dialogfeld „Konfiguration zu CMakeSettings hinzufügen“](media/cmake-bullet3-add-configuration-x64-debug.png)

   In diesem Dialogfeld werden alle in Visual Studio enthaltenen Konfigurationen sowie alle von Ihnen erstellten benutzerdefinierten Konfigurationen angezeigt. Wenn Sie weiterhin eine **x64-Debug-Konfiguration** verwenden möchten, sollte dies die erste sein, die Sie hinzufügen. Wählen Sie **x64-Debug**aus, und wählen Sie dann die Schaltfläche **Auswählen** aus. Visual Studio erstellt die Datei CMakeSettings.json mit einer Konfiguration für **x64-Debug**und speichert sie auf dem Datenträger. Sie können Ihre Konfigurationen beliebig benennen, indem Sie den Namensparameter direkt in „CMakeSettings.json“ ändern.

## <a name="set-a-breakpoint-build-and-run-on-windows"></a>Festlegen eines Haltepunkts, Erstellen und Ausführen unter Windows

In diesem Schritt debuggen wir ein Beispielprogramm, das die Bullet Physics-Bibliothek veranschaulicht.
  
1. Wählen Sie „AppBasicExampleGui“ im **Projektmappen-Explorer**, und erweitern Sie es.

1. Öffnen Sie die Datei `BasicExample.cpp`.

1. Legen Sie einen Haltepunkt fest, der beim Klicken in der ausgeführten Anwendung erreicht wird. Das Klickereignis wird in einer Methode in einer Hilfsklasse behandelt. Führen Sie folgende Schritte aus, um schnell dorthin zu gelangen:

   1. Wählen `CommonRigidBodyBase` Sie `BasicExample` aus, von dem die Struktur abgeleitet ist. Es ist um Linie 30.

   1. Klicken Sie mit der rechten Maustaste, und wählen Sie **Gehe zu Definition**. Jetzt sind Sie in der Kopfzeile CommonRigidBodyBase.h.

   1. In der Browseransicht über der Quelle sollten Sie `CommonRigidBodyBase`sehen, dass Sie sich in der sind. Rechts können Sie Member auswählen, die Sie sich genauer ansehen möchten. Öffnen Sie die Dropdown-Liste, und wählen Sie aus, ob Sie `mouseButtonCallback` zur Definition dieser Funktion im Header wechseln möchten.

      ![Symbolleiste der Memberliste in Visual Studio](media/cmake-bullet3-member-list-toolbar.png)

1. Setzen Sie in der ersten Zeile dieser Funktion einen Breakpoint. Es wird getroffen, wenn Sie eine Maustaste im Fenster der Anwendung klicken, wenn Sie unter dem Visual Studio-Debugger ausgeführt werden.

1. Um die Anwendung zu starten, wählen Sie die Start-Dropdown-Liste in der Symbolleiste aus. Es ist diejenige mit dem grünen Wiedergabesymbol, das "Startelement auswählen" sagt. Wählen Sie in der Dropdownliste AppBasicExampleGui.exe aus. Der Name der ausführbaren Datei wird jetzt auf der Startschaltfläche angezeigt:

   ![Startdropdownmenü auf der Symbolleiste von Visual Studio für „Startelement auswählen“](media/cmake-bullet3-launch-button.png)

1. Wählen Sie die Startschaltfläche aus, um die Anwendung und die erforderlichen Abhängigkeiten zu erstellen, und starten Sie sie dann mit dem angefügten Visual Studio-Debugger. Nach kurzer Zeit wird die ausgeführte Anwendung angezeigt:

   ![Debugging einer Windows-Anwendung in Visual Studio](media/cmake-bullet3-launched.png)

1. Bewegen Sie den Mauszeiger in das Anwendungsfenster, und drücken Sie anschließend eine Taste, um den Breakpoint auszulösen. Der Haltepunkt bringt Visual Studio wieder in den Vordergrund, und der Editor zeigt die Zeile an, in der die Ausführung angehalten wird. Sie können die Anwendungsvariablen, Objekte, Threads und Arbeitsspeicher überprüfen oder den Code interaktiv durchlaufen. Wählen Sie **Weiter,** um die Anwendung fortsetzen zu lassen, und beenden Sie sie dann normal. Oder halten Sie die Ausführung in Visual Studio mithilfe der Stopp-Schaltfläche an.

## <a name="add-a-linux-configuration-and-connect-to-the-remote-machine"></a>Hinzufügen einer Linux-Konfiguration und Verbinden mit dem Remotecomputer

1. Fügen Sie eine Linux-Konfiguration hinzu. Klicken Sie mit der rechten Maustaste im **Projektmappen-Explorer** auf die Datei „CMakeSettings.json“, und wählen Sie **Konfiguration hinzufügen** aus. Das Dialogfeld „Konfiguration zu CMakeSettings hinzufügen“ wird geöffnet, das Sie schon aus dem vorherigen Schritt kennen. Wählen Sie diesmal **Linux-Debug** und speichern Sie dann die Datei CMakeSettings.json (strg + s).

1. Wählen Sie **Linux-Debug** in der Konfigurations-Dropdown-Liste.

   ![Konfigurationsdropdownmenü mit den Optionen x64-Debug und Linux-Debug](media/cmake-bullet3-linux-configuration-item.png)

   Wenn Sie zum ersten Mal eine Verbindung zu einem Linux-System herstellen, wird das Dialogfeld **"Mit Remotesystem verbinden"** angezeigt.

   ![Dialogfeld „Mit Remotesystem verbinden“ in Visual Studio](media/cmake-bullet3-connection-manager.png)

   Wenn Sie bereits eine Remoteverbindung hinzugefügt haben, können Sie dieses Fenster öffnen, indem Sie zu **Tools > Optionen > Plattformübergreifende>-Verbindungs-Manager**navigieren.

1. Geben Sie die [Verbindungsinformationen für Ihren Linux-Computer](/cpp/linux/connect-to-your-remote-linux-computer) an, und wählen Sie **Verbinden**aus. Visual Studio fügt diesen Computer als Standardverbindung für **Linux-Debug**zu CMakeSettings.json hinzu. Es zieht auch die Header von Ihrem Remote-Computer nach unten, so dass Sie [IntelliSense spezifisch für diese Remote-Verbindung](/cpp/linux/configure-a-linux-project?view=vs-2019#remote_intellisense)erhalten. Als Nächstes sendet Visual Studio Ihre Dateien an den Remotecomputer und generiert den CMake-Cache auf dem Remotesystem. Diese Schritte können einige Zeit in Anspruch nehmen, abhängig von der Geschwindigkeit Ihres Netzwerks und der Leistung Ihres Remotecomputers. Sie werden wissen, dass es abgeschlossen ist, wenn die Meldung "Zielinformationen-Extraktion durchgeführt" im CMake-Ausgabefenster angezeigt wird.

## <a name="set-a-breakpoint-build-and-run-on-linux"></a>Festlegen eines Haltepunkts, Erstellen und Ausführen unter Linux

Da es sich um eine Desktopanwendung handelt, müssen Sie der Debugkonfiguration einige zusätzliche Konfigurationsinformationen bereitstellen.

1. Klicken Sie in der Ansicht "CMake-Ziele" mit der rechten Maustaste auf AppBasicExampleGui, und wählen Sie **Debug- und Starteinstellungen** aus, um die Datei launch.vs.json zu öffnen, die sich im ausgeblendeten **Unterordner .vs** befindet. Diese Datei befindet sich lokal in Ihrer Entwicklungsumgebung. Sie können sie zum Stamm Ihres Projekts verschieben, wenn Sie sie bei Ihrem Team einchecken und speichern möchten. In dieser Datei wurde eine Konfiguration für AppBasicExampleGui hinzugefügt. Diese Standardeinstellungen funktionieren in den meisten Fällen, aber nicht hier. Da es sich um eine Desktopanwendung handelt, müssen Sie einige zusätzliche Informationen bereitstellen, um das Programm zu starten, damit Sie es auf Ihrem Linux-Computer sehen können.

1. Um den Wert der `DISPLAY` Umgebungsvariablen auf Ihrem Linux-Computer zu finden, führen Sie diesen Befehl aus:

   ```cmd
   echo $DISPLAY
   ```

   In der Konfiguration für AppBasicExampleGui gibt es ein Parameterarray, "pipeArgs". Sie enthält eine Zeile: "-debuggerCommand". Es ist der Befehl, der gdb auf dem Remote-Computer startet. Visual Studio muss die Anzeige in diesen Kontext exportieren, bevor dieser Befehl ausgeführt wird. Wenn der Wert der Anzeige `:1`z. B. lautet, ändern Sie diese Zeile wie folgt:

   ```cmd
   "export DISPLAY=:1;${debuggerCommand}",
   ```

1. Starten und debuggen Sie Ihre Anwendung. Öffnen Sie die Dropdown-Dropdown-Liste **Startelement auswählen** in der Symbolleiste, und wählen Sie **AppBasicExampleGui**. Wählen Sie als Nächstes entweder das grüne Wiedergabesymbol in der Symbolleiste aus, oder drücken Sie **F5**. Die Anwendung und ihre Abhängigkeiten werden auf dem Remote-Linux-Computer erstellt und dann mit dem angefügten Visual Studio-Debugger gestartet. Auf Ihrem Linux-Remotecomputer sollte ein Anwendungsfenster geöffnet werden.

1. Bewegen Sie die Maus in das Anwendungsfenster, und klicken Sie auf eine Schaltfläche. Der Haltepunkt wird getroffen. Programmausführung sausiert, Visual Studio kehrt in den Vordergrund zurück, und Sie sehen Ihren Haltepunkt. Außerdem sollte ein Linux-Konsolenfenster in Visual Studio angezeigt werden. Das Fenster bietet die Ausgabe von der Remote-Linux-Maschine, und es kann auch Eingaben für `stdin`akzeptieren. Wie jedes Visual Studio-Fenster können Sie es an die Stelle andocken, an der Sie es sehen möchten. Seine Position wird in zukünftigen Sitzungen beibehalten.

   ![Linux-Konsolenfenster in Visual Studio](media/cmake-bullet3-linux-console.png)

1. Sie können sich die Variablen, Objekte, Threads und den Arbeitsspeicher der Anwendung ansehen und Ihren Code in Visual Studio schrittweise und interaktiv ausführen. Aber dieses Mal tun Sie alles auf einem Remote-Linux-Computer anstelle Ihrer lokalen Windows-Umgebung. Sie können **Fortfahren** auswählen, um die Anwendung normal fortsetzen und beenden zu lassen, oder Sie können die Stopp-Schaltfläche wählen, genau wie bei der lokalen Ausführung.

1. Sehen Sie sich das Aufruflistenfenster an, und zeigen Sie die Aufrufe von `x11OpenGLWindow` seit dem Start der Anwendung durch Visual Studio auf dem Linux-Computer an.

   ![Fenster „Aufrufliste“ mit der Linux-Aufrufliste](media/cmake-bullet3-linux-callstack.png)

## <a name="what-you-learned"></a>Zusammenfassung

In diesem Tutorial haben Sie eine Codebasis direkt von GitHub geklont. Sie haben es ohne Änderungen unter Windows erstellt, ausgeführt und gedebugwart. Anschließend haben Sie dieselbe Codebasis mit geringfügigen Konfigurationsänderungen zum Erstellen, Ausführen und Debuggen auf einem Remote-Linux-Computer verwendet.

## <a name="next-steps"></a>Nächste Schritte

In den folgenden Artikeln erhalten Sie weitere Informationen zum Konfigurieren und Debuggen von CMake-Projekten in Visual Studio:

> [!div class="nextstepaction"]
> [CMake-Projekte in Visual Studio](cmake-projects-in-visual-studio.md)<br/><br/>
> [Konfigurieren eines Linux CMake-Projekts](../linux/cmake-linux-project.md)<br/><br/>
> [Herstellen einer Verbindung mit Ihrem Linux-Remotecomputer](../linux/connect-to-your-remote-linux-computer.md)<br/><br/>
> [Anpassen von CMake-Buildeinstellungen](customize-cmake-settings.md)<br/><br/>
> [Konfigurieren von CMake-Debugsitzungen](configure-cmake-debugging-sessions.md)<br/><br/>
> [Bereitstellen, Ausführen und Debuggen Ihres Linux-Projekts](../linux/deploy-run-and-debug-your-linux-project.md)<br/><br/>
> [CMake predefined configuration reference (Referenz für vordefinierte CMake-Konfigurationen)](cmake-predefined-configuration-reference.md)
>
