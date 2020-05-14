---
title: Erstellen eines C++-Konsolen-App-Projekts
description: Erstellen Sie eine „Hallo Welt“-Konsolen-App mit Microsoft C++ in Visual Studio.
ms.custom: mvc
ms.date: 04/20/2020
ms.topic: tutorial
ms.assetid: 45138d70-719d-42dc-90d7-1d0ca31a2f54
ms.openlocfilehash: 07e88da9a8a3712e1d37e319c29fd25aebce8ea7
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81749307"
---
# <a name="create-a-c-console-app-project"></a>Erstellen eines C++-Konsolen-App-Projekts

C++-Programmierer beginnen häufig mit einer „Hallo, Welt!“- Anwendung, die über die Befehlszeile ausgeführt wird. Eine solche Anwendung werden Sie in diesem Schritt ebenfalls in Visual Studio erstellen.

## <a name="prerequisites"></a>Voraussetzungen

- Visual Studio mit der Workload „Desktopentwicklung mit C++“ muss auf Ihrem Computer installiert sein und ausgeführt werden. Ist dies noch nicht der Fall, finden Sie unter [Install C++ support in Visual Studio (Installieren von C++-Komponenten in Visual Studio)](vscpp-step-0-installation.md) weitere Informationen.

## <a name="create-your-app-project"></a>Erstellen Ihres App-Projekts

Visual Studio verwendet *Projekte*, um Code für eine App zu ordnen, und *Projektmappen*, um Ihre Projekte zu ordnen. Ein Projekt beinhaltet alle Optionen, Einstellungen und Regeln, die Sie zum Erstellen Ihrer Anwendung verwendet haben. Es verwaltet die Beziehungen zwischen allen Projektdateien und externen Dateien. Wenn Sie Ihre App erstellen möchten, müssen Sie zuerst ein neues Projekt und eine Projektmappe erstellen.

::: moniker range=">=vs-2019"

1. Öffnen Sie in Visual Studio das Menü **Datei**, und klicken Sie auf **Neu > Projekt**, um das Dialogfeld **Neues Projekt erstellen** zu öffnen. Wählen Sie die Vorlage **Konsolen-App** aus, die über die Tags **C++** , **Windows** und **Konsole** verfügt, und klicken Sie dann auf **Weiter**.

   ![Neues Projekt erstellen](media/vs2019-choose-console-app.png "Öffnen des Dialogfelds „Neues Projekt erstellen“")

1. Geben Sie im Dialogfeld **Neues Projekt konfigurieren** in das Bearbeitungsfeld **Projektname** *HelloWorld* ein. Klicken Sie auf **Erstellen**, um das Projekt zu erstellen.

   ![Benennen und Erstellen des neuen Projekts](media/vs2019-configure-new-project-hello-world.png "Benennen und Erstellen des neuen Projekts")

   Visual Studio erstellt daraufhin ein neues Projekt. Nun können Sie Ihren Quellcode dort hinzufügen und bearbeiten. Standardmäßig fügt die Konsolen-App-Vorlage als Quellcode eine „Hallo Welt“-App ein:

   ![„Hallo Welt“-Projekt in der IDE](media/vs2019-hello-world-code.png "„Hallo Welt“-Projekt in der IDE")

   Wenn der Code im Editor wie hier aussieht, können Sie mit dem nächsten Schritt fortfahren und Ihre App erstellen.

[Ein Problem ist aufgetreten.](#create-your-app-project-issues)

::: moniker-end

::: moniker range="<=vs-2017"

1. Öffnen Sie in Visual Studio das Menü **Datei**, und klicken Sie auf **Neu > Projekt**, um das Dialogfeld **Neues Projekt** zu öffnen.

   ![Öffnen des Dialogfelds „Neues Projekt“](media/vscpp-file-new-project.gif "Öffnen des Dialogfelds „Neues Projekt“")

1. Wählen Sie im Dialogfeld **Neues Projekt** **Installiert > Visual C++** aus, sofern dies nicht bereits ausgewählt ist, und dann die Vorlage **Leeres Projekt**. Geben Sie in das Feld **Name** *HelloWorld* ein. Klicken Sie auf **OK**, um das Projekt zu erstellen.

   ![Benennen und Erstellen des neuen Projekts](media/vscpp-concierge-project-name-callouts.png "Benennen und Erstellen des neuen Projekts")

Visual Studio erstellt daraufhin ein neues leeres Projekt. Sie können das Projekt nun für die Art von App anpassen, die Sie erstellen möchten, und Ihre Quellcodedateien hinzufügen. Diesen Schritt führen Sie als Nächstes durch.

[Ein Problem ist aufgetreten.](#create-your-app-project-issues)

## <a name="make-your-project-a-console-app"></a>So machen Sie aus Ihrem Projekt eine Konsolen-App

Visual Studio kann viele verschiedene Arten von Apps und Komponenten für Windows und andere Plattformen erstellen. Mit der Vorlage **Leeres Projekt** wird keine bestimmte Art von App erstellt. Eine *Konsolen-App* ist eine App, die in einem Konsolen- oder Eingabeaufforderungsfenster ausgeführt wird. Wenn Sie eine solche App erstellen möchten, müssen Sie Visual Studio anweisen, Ihre App so zu erstellen, dass diese das Konsolensubsystem verwendet.

1. Öffnen Sie in Visual Studio das Menü **Projekt**, und klicken Sie auf **Eigenschaften**, um das Dialogfeld **HelloWorld Eigenschaftenseiten** zu öffnen.

1. Klicken Sie im Dialogfeld **Eigenschaftenseiten** auf **Konfigurationseigenschaften > Linker > System** und dann auf das Bearbeitungsfeld neben der Eigenschaft **SubSystem**. Wählen Sie im angezeigten Dropdownmenü **Konsole (/SUBSYSTEM:CONSOLE)** aus. Klicken Sie auf **OK**, um die Änderungen zu speichern.

   ![Öffnen des Dialogfelds „Eigenschaftenseiten“](media/vscpp-properties-linker-subsystem.gif "Öffnen des Dialogfelds „Eigenschaftenseiten“")

Visual Studio weiß nun, dass Ihr Projekt so erstellt werden soll, dass es in einem Konsolenfenster ausgeführt wird. Fügen Sie als Nächstes eine Quellcodedatei hinzu, und geben Sie den Code für Ihre App ein.

[Ein Problem ist aufgetreten.](#make-your-project-a-console-app-issues)

## <a name="add-a-source-code-file"></a>Hinzufügen einer Quellcodedatei

1. Wählen Sie im **Projektmappen-Explorer** das Projekt „HelloWorld“ aus. Klicken Sie in der Menüleiste auf **Projekt** und dann auf **Neues Element hinzufügen**, um das Dialogfeld **Neues Element hinzufügen** zu öffnen.

1. Wählen Sie im Dialogfeld **Neues Element hinzufügen** unter **Installiert** **Visual C++** aus, sofern dies nicht bereits ausgewählt ist. Klicken Sie im mittleren Bereich auf **C++-Datei (.cpp)** . Ändern Sie den **Namen** in *HelloWorld.cpp*. Klicken Sie auf **Hinzufügen**, um das Dialogfeld zu schließen und die Datei zu erstellen.

   ![Hinzufügen einer Quelldatei für HelloWorld.cpp](media/vscpp-add-new-item.gif "Hinzufügen einer Quelldatei für HelloWorld.cpp")

Visual Studio erstellt eine neue leere Quellcodedatei und öffnet diese in einem Editorfenster, in dem Sie Ihren Quellcode eingeben können.

[Ein Problem ist aufgetreten.](#add-a-source-code-file-issues)

## <a name="add-code-to-the-source-file"></a>Hinzufügen von Code zur Quelldatei

1. Kopieren Sie den folgenden Code in das Editorfenster für HelloWorld.cpp.

   ```cpp
   #include <iostream>

   int main()
   {
       std::cout << "Hello, world!" << std::endl;
       return 0;
   }
   ```

   Im Editorfenster sollte der Code wie folgt aussehen:

   ![„Hallo Welt“-Code im Editor](media/vscpp-hello-world-editor.png "„Hallo Welt“-Code im Editor")

Wenn der Code im Editor wie hier aussieht, können Sie mit dem nächsten Schritt fortfahren und Ihre App erstellen.

[Ein Problem ist aufgetreten.](#add-a-source-code-file-issues)

::: moniker-end

## <a name="next-steps"></a>Nächste Schritte

> [!div class="nextstepaction"]
> [Erstellen und Ausführen eines C++-Projekts](vscpp-step-2-build.md)

## <a name="troubleshooting-guide"></a>Handbuch zur Problembehandlung

Hier finden Sie Lösungen für häufig auftretende Probleme beim Erstellen Ihres ersten C++-Projekts.

### <a name="create-your-app-project-issues"></a>Erstellen Ihres App-Projekts: Probleme

::: moniker range="vs-2019"

Im Dialogfeld **Neues Projekt** sollte eine Vorlage namens **Konsolen-App** angezeigt werden, die über die Tags **C++** , **Windows** und **Konsole** verfügt. Wenn sie nicht angezeigt wird, gibt es hierfür zwei mögliche Ursachen. Sie wurde möglicherweise aus der Liste herausgefiltert, oder sie ist möglicherweise nicht installiert. Überprüfen Sie zunächst die Filterdropdownlisten über der Liste der Vorlagen. Legen Sie dort **C++** , **Windows** und **Konsole** fest. Die C++-Vorlage **Konsolen-App** sollte nun angezeigt werden. Andernfalls ist die Workload **Desktopentwicklung mit C++** nicht installiert.

Wenn Sie **Desktopentwicklung mit C++** installieren möchten, können Sie das Installationsprogramm direkt über das Dialogfeld **Neues Projekt** ausführen. Klicken Sie auf den Link **Weitere Tools und Features installieren** am Ende der Vorlagenliste, um das Installationsprogramm zu starten. Wenn im Dialogfeld **User Account Control** (Benutzerkontensteuerung) Berechtigungen angefordert werden, klicken Sie auf **Ja**. Stellen Sie sicher, dass im Installationsprogramm die Workload **Desktopentwicklung mit C++** aktiviert ist. Klicken Sie dann auf **Ändern**, um Ihre Visual Studio-Installation zu aktualisieren.

Wenn bereits ein anderes Projekt mit dem gleichen Namen vorhanden ist, verwenden Sie einen anderen Namen für das Projekt. Alternativ können Sie das vorhandene Projekt löschen und den Vorgang wiederholen. Wenn Sie ein vorhandenes Projekt löschen möchten, müssen Sie den Projektmappenordner (den Ordner, der die Datei *helloworld.sln* enthält) im Datei-Explorer löschen.

[Zurück](#create-your-app-project)

::: moniker-end

::: moniker range="vs-2017"

Wenn im Dialogfeld **Neues Projekt** unter **Installiert** kein Eintrag **Visual C++** angezeigt wird, ist bei Ihrer Kopie von Visual Studio wahrscheinlich die Workload **Desktopentwicklung mit C++** nicht installiert. Sie können das Installationsprogramm direkt über das Dialogfeld **Neues Projekt** ausführen. Klicken Sie auf den Link **Visual Studio-Installer öffnen**, um das Installationsprogramm noch mal zu starten. Wenn im Dialogfeld **User Account Control** (Benutzerkontensteuerung) Berechtigungen angefordert werden, klicken Sie auf **Ja**. Aktualisieren Sie ggf. das Installationsprogramm. Stellen Sie sicher, dass im Installationsprogramm die Workload **Desktopentwicklung mit C++** aktiviert ist, und klicken Sie auf **OK**, um Ihre Visual Studio-Installation zu aktualisieren.

::: moniker-end

::: moniker range="<=vs-2017"

Wenn bereits ein anderes Projekt mit dem gleichen Namen vorhanden ist, verwenden Sie einen anderen Namen für das Projekt. Alternativ können Sie das vorhandene Projekt löschen und den Vorgang wiederholen. Wenn Sie ein vorhandenes Projekt löschen möchten, müssen Sie den Projektmappenordner (den Ordner, der die Datei *helloworld.sln* enthält) im Datei-Explorer löschen.

[Zurück](#create-your-app-project)

### <a name="make-your-project-a-console-app-issues"></a>So machen Sie aus Ihrem Projekt eine Konsolen-App: Probleme

Wenn **Linker** unter **Konfigurationseigenschaften** nicht aufgeführt ist, klicken Sie auf **Abbrechen**, um das Dialogfeld **Eigenschaftenseiten** zu schließen. Stellen Sie sicher, dass im **Projektmappen-Explorer** das Projekt **HelloWorld** ausgewählt ist, bevor Sie es noch mal versuchen. Wählen Sie nicht im **Projektmappen-Explorer** die Projektmappe **HelloWorld** oder ein anderes Element aus.

Das Dropdown-Steuerelement im Bearbeitungsfeld für die Eigenschaft **SubSystem** wird erst angezeigt, wenn Sie die Eigenschaft auswählen. Klicken Sie in das Bearbeitungsfeld, um sie auszuwählen. Alternativ können Sie die **TAB-TASTE** drücken, um die Dialogfeld-Steuerelemente zu durchlaufen, bis **SubSystem** hervorgehoben ist. Klicken Sie auf das Dropdown-Steuerelement, oder drücken Sie **ALT+NACH-UNTEN-TASTE**, um es zu öffnen.

[Zurück](#make-your-project-a-console-app)

### <a name="add-a-source-code-file-issues"></a>Hinzufügen einer Quellcodedatei: Probleme

Sie können der Quellcodedatei einen anderen Namen geben. Fügen Sie jedoch nicht mehr als eine Datei mit dem gleichen Code zu Ihrem Projekt hinzu.

Wenn Sie den falschen Dateityp zu Ihrem Projekt hinzugefügt haben, z. B. eine Headerdatei, löschen Sie die entsprechende Datei, und wiederholen Sie den Vorgang. Klicken Sie im **Projektmappen-Explorer** auf die Datei, um sie zu löschen. Drücken Sie dann die **ENTF-TASTE**.

[Zurück](#add-a-source-code-file)

### <a name="add-code-to-the-source-file-issues"></a>Hinzufügen von Code zur Quelldatei: Probleme

Wenn Sie das Editorfenster für die Quellcodedatei versehentlich geschlossen haben, können Sie es einfach wieder öffnen. Doppelklicken Sie hierzu im Fenster **Projektmappen-Explorer** auf HelloWorld.cpp.

Wenn im Quellcode-Editor irgendetwas mit einer roten Wellenlinie unterstrichen ist, überprüfen Sie, ob Ihr Code in Bezug auf Rechtschreibung, Interpunktion und Groß-/Kleinschreibung mit dem Beispiel übereinstimmt. In C++-Code ist die Groß-/Kleinschreibung von Bedeutung.

[Zurück](#add-code-to-the-source-file)

::: moniker-end

<iframe src="" height="0" width="0" frameborder="0" name="frameTarget" />
