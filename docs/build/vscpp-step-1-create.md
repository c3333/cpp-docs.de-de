---
title: Erstellen eines C++-Konsolen-App-Projekts
description: Erstellen Sie eine Hello World-Konsolen-App mit Microsoft C++ in Visual Studio.
ms.custom: mvc
ms.date: 04/20/2020
ms.topic: tutorial
ms.assetid: 45138d70-719d-42dc-90d7-1d0ca31a2f54
ms.openlocfilehash: 07e88da9a8a3712e1d37e319c29fd25aebce8ea7
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81749307"
---
# <a name="create-a-c-console-app-project"></a>Erstellen eines C++-Konsolen-App-Projekts

C++-Programmierer beginnen häufig mit einer „Hallo, Welt!“- Anwendung, die über die Befehlszeile ausgeführt wird. Das erstellen Sie in Visual Studio in diesem Schritt.

## <a name="prerequisites"></a>Voraussetzungen

- Visual Studio mit der Workload „Desktopentwicklung mit C++“ muss auf Ihrem Computer installiert sein und ausgeführt werden. Ist dies noch nicht der Fall, finden Sie unter [Install C++ support in Visual Studio (Installieren von C++-Komponenten in Visual Studio)](vscpp-step-0-installation.md) weitere Informationen.

## <a name="create-your-app-project"></a>Erstellen Ihres App-Projekts

Visual Studio verwendet *Projekte*, um Code für eine App zu ordnen, und *Projektmappen*, um Ihre Projekte zu ordnen. Ein Projekt beinhaltet alle Optionen, Einstellungen und Regeln, die Sie zum Erstellen Ihrer Anwendung verwendet haben. Es verwaltet die Beziehung zwischen allen Projektdateien und allen externen Dateien. Wenn Sie Ihre App erstellen möchten, müssen Sie zuerst ein neues Projekt und eine Projektmappe erstellen.

::: moniker range=">=vs-2019"

1. Öffnen Sie in Visual Studio das Menü **Datei,** und wählen Sie **Neues > Projekt** aus, um das Dialogfeld Neues **Projekt** erstellen zu öffnen. Wählen Sie die **Konsolen-App-Vorlage** mit **C++-,** **Windows-** und **Konsolentags** aus, und wählen Sie dann **Weiter**aus.

   ![Erstellen eines neuen Projekts](media/vs2019-choose-console-app.png "Öffnen des Dialogfelds Erstellen eines neuen Projekts")

1. Geben Sie im **Dialogfeld Konfigurieren des neuen Projekts** *HelloWorld* in das Bearbeitungsfeld **Projektnamen** ein. Wählen Sie **Erstellen** aus, um das Projekt zu erstellen.

   ![Benennen und Erstellen des neuen Projekts](media/vs2019-configure-new-project-hello-world.png "Benennen und Erstellen des neuen Projekts")

   Visual Studio erstellt ein neues Projekt. Es ist bereit für Sie, Ihren Quellcode hinzuzufügen und zu bearbeiten. Standardmäßig füllt die Konsolen-App-Vorlage Ihren Quellcode mit einer "Hello World"-App aus:

   ![Hello World Projekt in der IDE](media/vs2019-hello-world-code.png "Hello World Projekt in der IDE")

   Wenn der Code im Editor so aussieht, können Sie mit dem nächsten Schritt fortfahren und Ihre App erstellen.

[Ein Problem ist aufgetreten.](#create-your-app-project-issues)

::: moniker-end

::: moniker range="<=vs-2017"

1. Öffnen Sie in Visual Studio das Menü **Datei,** und wählen Sie **Neues > Projekt** aus, um das Dialogfeld Neues **Projekt** zu öffnen.

   ![Öffnen des Dialogfelds „Neues Projekt“](media/vscpp-file-new-project.gif "Öffnen des Dialogfelds „Neues Projekt“")

1. Wählen Sie im Dialogfeld **Neues Projekt** die Option **Installiertes > Visual C++aus,** wenn es noch nicht ausgewählt ist, und wählen Sie dann die Vorlage **Leeres Projekt** aus. Geben Sie im Feld **Name** *HelloWorld*ein. Wählen Sie **OK,** um das Projekt zu erstellen.

   ![Benennen und Erstellen des neuen Projekts](media/vscpp-concierge-project-name-callouts.png "Benennen und Erstellen des neuen Projekts")

Visual Studio erstellt ein neues, leeres Projekt. Es ist bereit für Sie, sich auf die Art der App zu spezialisieren, die Sie erstellen möchten, und Ihre Quellcodedateien hinzuzufügen. Diesen Schritt führen Sie als Nächstes durch.

[Ein Problem ist aufgetreten.](#create-your-app-project-issues)

## <a name="make-your-project-a-console-app"></a>Machen Sie Ihr Projekt zu einer Konsolen-App

Visual Studio kann alle Arten von Apps und Komponenten für Windows und andere Plattformen erstellen. Die Vorlage **"Leeres Projekt"** ist nicht spezifisch für die Art der App, die sie erstellt. Eine *Konsolen-App* ist eine, die in einer Konsole oder einem Eingabeaufforderungsfenster ausgeführt wird. Um eine zu erstellen, müssen Sie Visual Studio anweisen, Ihre App für die Verwendung des Konsolensubsystems zu erstellen.

1. Öffnen Sie in Visual Studio das **Menü Projekt,** und wählen Sie **Eigenschaften** aus, um das Dialogfeld **HelloWorld-Eigenschaftenseiten** zu öffnen.

1. Wählen Sie im Dialogfeld **Eigenschaftenseiten** die Option **Konfigurationseigenschaften > Linker > System**aus , und wählen Sie dann das Bearbeitungsfeld neben der **Subsystem-Eigenschaft** aus. Wählen Sie im angezeigten Dropdown-Menü **Konsole (/SUBSYSTEM:CONSOLE)** aus. Klicken Sie auf **OK**, um die Änderungen zu speichern.

   ![Öffnen des Dialogfelds Eigenschaftenseiten](media/vscpp-properties-linker-subsystem.gif "Öffnen des Dialogfelds Eigenschaftenseiten")

Visual Studio weiß jetzt, dass Ihr Projekt für die Ausführung in einem Konsolenfenster erstellt wird. Als Nächstes fügen Sie eine Quellcodedatei hinzu und geben den Code für Ihre App ein.

[Ein Problem ist aufgetreten.](#make-your-project-a-console-app-issues)

## <a name="add-a-source-code-file"></a>Hinzufügen einer Quellcodedatei

1. Wählen Sie im **Projektmappen-Explorer**das HelloWorld-Projekt aus. Wählen Sie in der Menüleiste **Projekt**, **Neues Element hinzufügen** aus, um das Dialogfeld Neues Element **hinzufügen** zu öffnen.

1. Wählen Sie im Dialogfeld **Neues Element hinzufügen** die Option Visual **C++** unter **Installiert** aus, wenn es noch nicht ausgewählt ist. Wählen Sie im mittleren Bereich die **C++-Datei (.cpp)** aus. Ändern Sie den **Namen** in *HelloWorld.cpp*. Wählen Sie **Hinzufügen** aus, um das Dialogfeld zu schließen und die Datei zu erstellen.

   ![Hinzufügen einer Quelldatei für HelloWorld.cpp](media/vscpp-add-new-item.gif "Hinzufügen einer Quelldatei für HelloWorld.cpp")

Visual Studio erstellt eine neue, leere Quellcodedatei und öffnet sie in einem Editorfenster, das bereit ist, den Quellcode einzugeben.

[Ein Problem ist aufgetreten.](#add-a-source-code-file-issues)

## <a name="add-code-to-the-source-file"></a>Hinzufügen von Code zur Quelldatei

1. Kopieren Sie diesen Code in das Editorfenster HelloWorld.cpp.

   ```cpp
   #include <iostream>

   int main()
   {
       std::cout << "Hello, world!" << std::endl;
       return 0;
   }
   ```

   Der Code sollte im Editorfenster wie folgt aussehen:

   ![Hello World-Code im Editor](media/vscpp-hello-world-editor.png "Hello World-Code im Editor")

Wenn der Code im Editor so aussieht, können Sie mit dem nächsten Schritt fortfahren und Ihre App erstellen.

[Ein Problem ist aufgetreten.](#add-a-source-code-file-issues)

::: moniker-end

## <a name="next-steps"></a>Nächste Schritte

> [!div class="nextstepaction"]
> [Erstellen und Ausführen eines C++-Projekts](vscpp-step-2-build.md)

## <a name="troubleshooting-guide"></a>Handbuch zur Problembehandlung

Kommen Sie hier her, um Lösungen für häufig auftretende Probleme zu finden, wenn Sie Ihr erstes C++-Projekt erstellen.

### <a name="create-your-app-project-issues"></a>Erstellen Sie Ihr App-Projekt: Probleme

::: moniker range="vs-2019"

Das Dialogfeld **Neues Projekt** sollte eine **Konsolen-App-Vorlage** mit **C++-,** **Windows-** und **Konsolentags** anzeigen. Wenn Sie es nicht sehen, gibt es zwei mögliche Ursachen. Möglicherweise wird sie aus der Liste herausgefiltert oder nicht installiert. Überprüfen Sie zunächst die Filter-Dropdowns oben in der Liste der Vorlagen. Legen Sie sie auf **C++**, **Windows**und **Konsole**fest. Die **C++-Konsolen-App-Vorlage** sollte angezeigt werden. Andernfalls ist die **Desktopentwicklung mit C++-Workload** nicht installiert.

Um die **Desktopentwicklung mit C++** zu installieren, können Sie das Installationsprogramm direkt im Dialogfeld **Neues Projekt** ausführen. Wählen Sie den Link **Weitere Tools und Funktionen** installieren am unteren Rand der Vorlagenliste aus, um das Installationsprogramm zu starten. Wenn das Dialogfeld **Benutzerkontensteuerung** Berechtigungen anfordert, wählen Sie **Ja**aus. Stellen Sie im Installationsprogramm sicher, dass die **Desktopentwicklung mit C++-Workload** überprüft ist. Wählen Sie dann **Ändern** aus, um ihre Visual Studio-Installation zu aktualisieren.

Wenn bereits ein anderes Projekt mit demselben Namen vorhanden ist, wählen Sie einen anderen Namen für das Projekt aus. Oder löschen Sie das vorhandene Projekt, und versuchen Sie es erneut. Um ein vorhandenes Projekt zu löschen, löschen Sie den Projektmappenordner (den Ordner, der die Datei *helloworld.sln* enthält) im Datei-Explorer.

[Gehen Sie zurück](#create-your-app-project).

::: moniker-end

::: moniker range="vs-2017"

Wenn im Dialogfeld **Neues Projekt** kein **Visual C++-Eintrag** unter **Installiert**angezeigt wird, ist für Ihre Kopie von Visual Studio die **Desktopentwicklung mit C++-Workload** wahrscheinlich nicht installiert. Sie können das Installationsprogramm direkt im Dialogfeld **Neues Projekt** ausführen. Wählen Sie den Link **Visual Studio Installer öffnen** aus, um das Installationsprogramm erneut zu starten. Wenn das Dialogfeld **Benutzerkontensteuerung** Berechtigungen anfordert, wählen Sie **Ja**aus. Aktualisieren Sie ggf. das Installationsprogramm. Stellen Sie im Installationsprogramm sicher, dass die **Desktopentwicklung mit C++-Workload** aktiviert ist, und wählen Sie **OK** aus, um die Visual Studio-Installation zu aktualisieren.

::: moniker-end

::: moniker range="<=vs-2017"

Wenn bereits ein anderes Projekt mit demselben Namen vorhanden ist, wählen Sie einen anderen Namen für das Projekt aus. Oder löschen Sie das vorhandene Projekt, und versuchen Sie es erneut. Um ein vorhandenes Projekt zu löschen, löschen Sie den Projektmappenordner (den Ordner, der die Datei *helloworld.sln* enthält) im Datei-Explorer.

[Gehen Sie zurück](#create-your-app-project).

### <a name="make-your-project-a-console-app-issues"></a>Machen Sie Ihr Projekt zu einer Konsolen-App: Probleme

Wenn **Linker** unter **Konfigurationseigenschaften**nicht aufgeführt ist, wählen Sie **Abbrechen** aus, um das Dialogfeld **Eigenschaftenseiten** zu schließen. Stellen Sie sicher, dass das **HelloWorld-Projekt** im **Projektmappen-Explorer** ausgewählt ist, bevor Sie es erneut versuchen. Wählen Sie im **Projektmappen-Explorer**nicht die **HelloWorld-Lösung** oder ein anderes Element aus.

Das Dropdown-Steuerelement wird erst im Bearbeitungsfeld der **SubSystem-Eigenschaft** angezeigt, wenn Sie die Eigenschaft auswählen. Klicken Sie in das Bearbeitungsfeld, um es auszuwählen. Sie können auch die **Tabulatortaste** drücken, um die Dialogsteuerelemente zu durchlaufen, bis **SubSystem** hervorgehoben ist. Wählen Sie das Dropdown-Steuerelement aus, oder drücken Sie **Alt+Down,** um es zu öffnen.

[Zurück](#make-your-project-a-console-app)

### <a name="add-a-source-code-file-issues"></a>Hinzufügen einer Quellcodedatei: Probleme

Es ist in Ordnung, wenn Sie der Quellcodedatei einen anderen Namen geben. Fügen Sie dem Projekt jedoch nicht mehr als eine Datei hinzu, die denselben Code enthält.

Wenn Sie dem Projekt den falschen Dateityp hinzugefügt haben, z. B. eine Headerdatei, löschen Sie ihn, und versuchen Sie es erneut. Um die Datei zu löschen, wählen Sie sie im **Projektmappen-Explorer**aus. Drücken Sie dann die **Taste Löschen.**

[Gehen Sie zurück](#add-a-source-code-file).

### <a name="add-code-to-the-source-file-issues"></a>Hinzufügen von Code zur Quelldatei: Probleme

Wenn Sie das Quellcodedatei-Editorfenster versehentlich geschlossen haben, können Sie es einfach wieder öffnen. Um es zu öffnen, doppelklicken Sie im **Projektmappen-Explorer** auf HelloWorld.cpp.

Wenn rote Wellenzeichen unter einem Anderen im Quellcode-Editor angezeigt werden, überprüfen Sie, ob der Code in Rechtschreibung, Satzzeichen und Groß-/Kleinschreibung mit dem Beispiel übereinstimmt. Der Fall ist im C++-Code von Bedeutung.

[Gehen Sie zurück](#add-code-to-the-source-file).

::: moniker-end

<iframe src="" height="0" width="0" frameborder="0" name="frameTarget" />
