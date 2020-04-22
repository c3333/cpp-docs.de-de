---
title: Erstellen und Ausführen eines C++-Konsolen-App-Projekts
description: Erstellen und Ausführen einer Hello World-Konsolen-App in Visual C++
ms.custom: mvc
ms.date: 04/20/2020
ms.topic: tutorial
ms.devlang: cpp
ms.assetid: 45138d71-719d-42dc-90d7-1d0ca31a2f55
ms.openlocfilehash: d1e92e598b370312730a7c4e208b935a264010bf
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81749245"
---
# <a name="build-and-run-a-c-console-app-project"></a>Erstellen und Ausführen eines C++-Konsolen-App-Projekts

Sie haben ein C++-Konsolen-App-Projekt erstellt und Ihren Code eingegeben. Jetzt können Sie es in Visual Studio erstellen und ausführen. Führen Sie sie dann als eigenständige App über die Befehlszeile aus.

## <a name="prerequisites"></a>Voraussetzungen

- Visual Studio mit der Workload „Desktopentwicklung mit C++“ muss auf Ihrem Computer installiert sein und ausgeführt werden. Wenn es noch nicht installiert ist, führen Sie die Schritte unter [C++-Unterstützung installieren in Visual Studio](vscpp-step-0-installation.md)aus.

- Erstellen Sie ein "Hallo, Welt!" und geben Sie den Quellcode ein. Wenn Sie diesen Schritt noch nicht ausgeführt haben, führen Sie die Schritte unter [Erstellen eines C++-Konsolen-App-Projekts](vscpp-step-1-create.md)aus.

Wenn Visual Studio wie folgt aussieht, können Sie Ihre App erstellen und ausführen:

   ![Bereit zum Bau des neuen Projekts](media/vscpp-ready-to-build.png "Bereit zum Bau des neuen Projekts")

## <a name="build-and-run-your-code-in-visual-studio"></a>Erstellen und Ausführen des Codes in Visual Studio

1. Wählen Sie zum Erstellen Ihres Projekts aus dem Menü **Erstellen** die Option **Projektmappe erstellen** aus. Im Fenster **Ausgabe** wird das Ergebnis des Erstellungsprozess angezeigt.

   ![Erstellen des Projekts](media/vscpp-build-solution.gif "Erstellen des Projekts")

1. Klicken Sie zum Ausführen des Codes auf der Menüleiste auf **Debuggen** > **Ohne Debuggen starten**.

   ![Starten des Projekts](media/vscpp-start-without-debugging.gif "Starten des Projekts")

   Ein Konsolenfenster wird geöffnet, und Ihre App daraufhin ausgeführt. Wenn Sie eine Konsolen-App in Visual Studio starten, führt diese Ihren Code aus und gibt dann „Press any key to continue . ." (Beliebige Taste zum Fortfahren drücken) zurück, damit Sie sich die Ausgabe ansehen können.

Glückwunsch! Sie haben Ihre erste „Hallo, Welt!“- Konsolen-App in Visual Studio erstellt! Drücken Sie eine Taste, um das Konsolenfenster zu schließen, und kehren Sie zu Visual Studio zurück.

[Ein Problem ist aufgetreten.](#build-and-run-your-code-in-visual-studio-issues)

## <a name="run-your-code-in-a-command-window"></a>Ausführen des Codes in einem Befehlsfenster

Normalerweise führen Sie Konsolen-Apps an der Eingabeaufforderung aus, nicht in Visual Studio. Sobald Ihre App von Visual Studio erstellt wurde, können Sie sie über jedes Befehlsfenster ausführen. Hier erfahren Sie, wie Sie Ihre neue App in einem Eingabeaufforderungsfenster suchen und ausführen.

1. Wählen Sie im **Projektmappen-Explorer**die HelloWorld-Lösung (nicht das HelloWorld-Projekt) aus, und klicken Sie mit der rechten Maustaste, um das Kontextmenü zu öffnen. Wählen Sie **Ordner öffnen im Datei-Explorer** aus, um ein **Datei-Explorer-Fenster** im HelloWorld-Lösungsordner zu öffnen.

1. Öffnen Sie im Fenster **Datei-Explorer** den Debug-Ordner. Dieser Ordner enthält Ihre App, *HelloWorld.exe*, und ein paar andere Debugdateien. Halten Sie die **Umschalttaste** gedrückt und klicken Sie mit der rechten Maustaste auf *HelloWorld.exe,* um das Kontextmenü zu öffnen. Wählen Sie **Kopieren als Pfad,** um den Pfad zu Ihrer App in die Zwischenablage zu kopieren.

1. Um ein Eingabeaufforderungsfenster zu öffnen, drücken Sie **Windows+R,** um das Dialogfeld **Ausführen** zu öffnen. Geben Sie *cmd.exe* in das Textfeld **Öffnen** ein, und wählen Sie dann **OK** aus, um ein Eingabeaufforderungsfenster auszuführen.

1. Klicken Sie im Eingabeaufforderungsfenster mit der rechten Maustaste, um den Pfad zu Ihrer App in die Eingabeaufforderung einzufügen. Drücken Sie die Eingabetaste, um Ihre App auszuführen.

   ![Ausführen der App an der Eingabeaufforderung](media/vscpp-run-in-cmd.gif "Ausführen der App an der Eingabeaufforderung")

Herzlichen Glückwunsch, Sie haben eine Konsolen-App in Visual Studio erstellt und ausgeführt!

[Ein Problem ist aufgetreten.](#run-your-code-in-a-command-window-issues)

## <a name="next-steps"></a>Nächste Schritte

Sobald Sie diese einfache App erstellt und ausgeführt haben, sind Sie bereit für komplexere Projekte. Weitere Informationen finden Sie unter [Verwenden der Visual Studio-IDE für C++ Desktop Development](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md). Es enthält ausführlichere exemplarische Vorgehensweisen, die die Funktionen von Microsoft C++ in Visual Studio untersuchen.

## <a name="troubleshooting-guide"></a>Handbuch zur Problembehandlung

Kommen Sie hier her, um Lösungen für häufig auftretende Probleme zu finden, wenn Sie Ihr erstes C++-Projekt erstellen.

### <a name="build-and-run-your-code-in-visual-studio-issues"></a>Erstellen und Ausführen des Codes in Visual Studio: Probleme

Wenn rote Wellenschalter unter einem Anderen im Quellcode-Editor angezeigt werden, kann der Build Fehler oder Warnungen aufweisen. Überprüfen Sie, ob der Code in Rechtschreibung, Satzzeichen und Fall mit dem Beispiel übereinstimmt.

[Zurück.](#build-and-run-your-code-in-visual-studio)

### <a name="run-your-code-in-a-command-window-issues"></a>Ausführen des Codes in einem Befehlsfenster: Probleme

Wenn der im Datei-Explorer angezeigte Pfad in * \\HelloWorld\\HelloWorld*endet, haben Sie das HelloWorld-Projekt anstelle der HelloWorld-Lösung geöffnet. *project* *solution* Sie werden durch einen Debugordner verwirrt, der Ihre App nicht enthält. Navigieren Sie auf einer Ebene im Datei-Explorer nach oben, um zum Projektmappenordner, dem ersten *HelloWorld* im Pfad, zu gelangen. Dieser Ordner enthält auch einen Debugordner, und Sie finden Ihre App dort.

Sie können auch zum Lösungsdebugordner in der Befehlszeile navigieren, um Ihre App auszuführen. Ihre App wird nicht von anderen Verzeichnissen ausgeführt, ohne den Pfad zur App anzugeben. Sie können Ihre App jedoch in ein anderes Verzeichnis kopieren und von dort aus ausführen. Es ist auch möglich, es in ein Verzeichnis zu kopieren, das von Ihrer PATH-Umgebungsvariablen angegeben wird, und es dann von überall aus auszuführen.

Wenn Sie Copy **nicht als Pfad** im Kontextmenü sehen, schließen Sie das Menü, und halten Sie dann die **Umschalttaste** gedrückt, während Sie es erneut öffnen. Dieser Befehl dient nur der Bequemlichkeit. Sie können den Pfad auch aus der Suchleiste des Datei-Explorers in den Ordner kopieren und in das Dialogfeld **Ausführen** einfügen und dann am Ende den Namen der ausführbaren Datei eingeben. Es ist nur ein wenig mehr Tippen, aber es hat das gleiche Ergebnis.

[Zurück.](#run-your-code-in-a-command-window)

<iframe src="" height="0" width="0" frameborder="0" name="frameTarget" />
