---
title: Erstellen und Ausführen eines C++-Konsolen-App-Projekts
description: Erstellen einer Hallo-Welt-Konsolen-App in Visual C++
ms.custom: mvc
ms.date: 04/20/2020
ms.topic: tutorial
ms.devlang: cpp
ms.assetid: 45138d71-719d-42dc-90d7-1d0ca31a2f55
ms.openlocfilehash: d1e92e598b370312730a7c4e208b935a264010bf
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81749245"
---
# <a name="build-and-run-a-c-console-app-project"></a>Erstellen und Ausführen eines C++-Konsolen-App-Projekts

Sie haben ein Projekt für eine C++-Konsolen-App erstellt und Ihren Code eingegeben. Nun können Sie es erstellen und in Visual Studio ausführen. Anschließend führen Sie es als eigenständige App über die Befehlszeile aus.

## <a name="prerequisites"></a>Voraussetzungen

- Visual Studio mit der Workload „Desktopentwicklung mit C++“ muss auf Ihrem Computer installiert sein und ausgeführt werden. Ist dies noch nicht der Fall, finden Sie unter [Installieren von C++-Unterstützung in Visual Studio](vscpp-step-0-installation.md) eine Anleitung.

- Darüber hinaus müssen Sie ein Hallo-Welt-Projekt erstellen und den entsprechenden Quellcode eingeben. Wenn Sie diesen Schritt noch nicht ausgeführt haben, befolgen Sie die Anleitung unter [Erstellen eines C++-Konsolen-App-Projekts](vscpp-step-1-create.md).

Wenn Ihre Visual Studio-Benutzeroberfläche wie folgt aussieht, können Sie Ihre App erstellen und ausführen:

   ![Bereit für die Erstellung des neuen Projekts](media/vscpp-ready-to-build.png "Bereit für die Erstellung des neuen Projekts")

## <a name="build-and-run-your-code-in-visual-studio"></a>Erstellen und Ausführen Ihres Codes in Visual Studio

1. Wählen Sie zum Erstellen Ihres Projekts aus dem Menü **Erstellen** die Option **Projektmappe erstellen** aus. Im Fenster **Ausgabe** wird das Ergebnis des Erstellungsprozess angezeigt.

   ![Erstellen des Projekts](media/vscpp-build-solution.gif "Erstellen des Projekts")

1. Klicken Sie zum Ausführen des Codes auf der Menüleiste auf **Debuggen** > **Ohne Debuggen starten**.

   ![Starten des Projekts](media/vscpp-start-without-debugging.gif "Starten des Projekts")

   Ein Konsolenfenster wird geöffnet, und Ihre App daraufhin ausgeführt. Wenn Sie eine Konsolen-App in Visual Studio starten, führt diese Ihren Code aus und gibt dann „Press any key to continue . .“ (Beliebige Taste zum Fortfahren drücken) zurück, damit Sie sich die Ausgabe ansehen können.

Herzlichen Glückwunsch! Sie haben Ihre erste „Hallo, Welt!“- Konsolen-App in Visual Studio erstellt! Drücken Sie eine Taste, um das Konsolenfenster zu schließen, und kehren Sie zu Visual Studio zurück.

[Ein Problem ist aufgetreten.](#build-and-run-your-code-in-visual-studio-issues)

## <a name="run-your-code-in-a-command-window"></a>Ausführen Ihres Codes in einem Befehlsfenster

Normalerweise werden Konsolen-Apps in der Eingabeaufforderung, nicht in Visual Studio ausgeführt. Nachdem Ihre App in Visual Studio erstellt wurde, können Sie sie über jedes beliebige Befehlsfenster ausführen. Nachstehend wird erläutert, wie Sie Ihre neue App in einem Eingabeaufforderungsfenster finden und ausführen.

1. Wählen Sie im **Projektmappen-Explorer** die Lösung „HelloWorld“ aus (nicht das Projekt „HelloWorld“), und klicken Sie mit der rechten Maustaste drauf, um das Kontextmenü zu öffnen. Klicken Sie auf **Ordner im Datei-Explorer öffnen**, um den **Datei-Explorer** im Ordner der Lösung „HelloWorld“ zu öffnen.

1. Öffnen Sie im **Datei-Explorer** den Ordner „Debug“. Dieser Ordner enthält Ihre App, *HelloWorld.exe* und einige andere Debuggingdateien. Halten Sie die **UMSCHALTTASTE** gedrückt, und klicken Sie mit der rechten Maustaste auf *HelloWorld.exe*, um das Kontextmenü zu öffnen. Klicken Sie auf **Copy as path** (Als Pfad kopieren), um den Pfad zu Ihrer Anwendung in die Zwischenablage zu kopieren.

1. Zum Öffnen eines Eingabeaufforderungsfensters, drücken Sie **WINDOWS-TASTE+R**, um das Dialogfeld **Ausführen** zu öffnen. Geben Sie *cmd.exe* in das Textfeld **Öffnen** ein, und klicken Sie dann auf **OK**, um ein Eingabeaufforderungsfenster auszuführen.

1. Klicken Sie mit der rechten Maustaste in das Eingabeaufforderungsfenster, um den Pfad zu Ihrer App in die Eingabeaufforderung einzufügen. Drücken Sie die EINGABETASTE, um Ihre App auszuführen.

   ![Ausführen der App in der Eingabeaufforderung](media/vscpp-run-in-cmd.gif "Ausführen der App in der Eingabeaufforderung")

Herzlichen Glückwunsch! Sie haben eine Konsolen-App in Visual Studio erstellt und ausgeführt.

[Ein Problem ist aufgetreten.](#run-your-code-in-a-command-window-issues)

## <a name="next-steps"></a>Nächste Schritte

Nachdem Sie die einfache App erstellt und ausgeführt haben, sind Sie bereit, komplexere Projekte in Angriff zu nehmen. Weitere Informationen finden Sie unter [Verwenden der Visual Studio-IDE für die C++-Desktopentwicklung](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md). Der Artikel enthält detailliertere exemplarische Vorgehensweisen, in denen die Funktionen von Microsoft C++ in Visual Studio erläutert werden.

## <a name="troubleshooting-guide"></a>Handbuch zur Problembehandlung

Hier finden Sie Lösungen für häufig auftretende Probleme beim Erstellen Ihres ersten C++-Projekts.

### <a name="build-and-run-your-code-in-visual-studio-issues"></a>Erstellen und Ausführen Ihres Codes in Visual Studio: Probleme

Wenn im Quellcode-Editor unter Codeelementen rote Wellenlinien angezeigt werden, enthält der Build möglicherweise Fehler oder Warnungen. Überprüfen Sie, ob Ihr Code hinsichtlich der Rechtschreibung, der Interpunktion und der Groß- und Kleinschreibung mit dem Beispiel übereinstimmt.

[Zurück](#build-and-run-your-code-in-visual-studio)

### <a name="run-your-code-in-a-command-window-issues"></a>Ausführen Ihres Codes in einem Befehlsfenster: Probleme

Wenn der im Datei-Explorer angezeigte Pfad auf *\\HelloWorld\\HelloWorld* endet, haben Sie das *Projekt* „HelloWorld“ anstatt der *Lösung* geöffnet. Vermutlich werden Sie sich über den Debugordner wundern, der nicht Ihre App enthält. Navigieren Sie im Datei-Explorer eine Ebene höher, um in den Lösungsordner zu gelangen (das erste *HelloWorld* im Pfad). Dieser Ordner enthält ebenfalls einen Debugordner, der jedoch Ihre App enthält.

Sie können auch in der Befehlszeile zum Debugordner der Lösung navigieren, um Ihre App auszuführen. Ihre App ist aus anderen Verzeichnissen nicht ausführbar, ohne dass der Pfad zur App angegeben wird. Sie können Ihre App jedoch in ein anderes Verzeichnis kopieren und von dort ausführen. Es ist außerdem möglich, die App in ein Verzeichnis zu kopieren, das von Ihrer PATH-Umgebungsvariablen angegeben wird, und sie dann von einem beliebigen Ort aus auszuführen.

Wenn die Option **Copy as path** (Als Pfad kopieren) nicht im Kontextmenü angezeigt wird, schließen Sie das Menü, und halten Sie die **UMSCHALTTASTE** gedrückt, während Sie es noch einmal öffnen. Dieser Befehl ist der einfachere Weg. Sie können den Pfad jedoch auch aus der Suchleiste des Datei-Explorers in den Ordner kopieren, ihn in das Dialogfeld **Ausführen** kopieren, und dann den Namen Ihrer ausführbaren Datei am Ende eingeben. Bei diesem Schritt müssen Sie etwas mehr tippen, das Ergebnis ist jedoch dasselbe.

[Zurück](#run-your-code-in-a-command-window)

<iframe src="" height="0" width="0" frameborder="0" name="frameTarget" />
