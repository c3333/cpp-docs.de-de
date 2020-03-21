---
title: 'Exemplarische Vorgehensweise: Erstellen und Verwenden einer statischen Bibliothek (C++)'
description: Verwenden C++ Sie, um eine statische Bibliothek (. lib) in Visual Studio zu erstellen.
ms.custom: get-started-article
ms.date: 04/25/2019
helpviewer_keywords:
- libraries [C++], static
- static libraries [C++]
ms.assetid: 3cc36411-7d66-4240-851e-dacb9a8fd6ac
ms.author: corob
ms.openlocfilehash: c81ccd970383c8571a7d0d1e77d4b8fe44900bcf
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "80078179"
---
# <a name="walkthrough-creating-and-using-a-static-library-c"></a>Exemplarische Vorgehensweise: Erstellen und Verwenden einer statischen Bibliothek (C++)

In dieser schrittweise erläuterten exemplarischen Vorgehensweise wird die Erstellung einer statischen Bibliothek (LIB-Datei) für die Verwendung mit C++-Apps erläutert. Die Verwendung einer statischen Bibliothek stellt eine gute Möglichkeit zur Wiederverwendung von Code dar. Anstatt die gleichen Routinen in jeder APP, für die die Funktionalität erforderlich ist, erneut zu implementieren, schreiben Sie Sie einmal in eine statische Bibliothek und verweisen dann von den apps darauf. Der Code, der von einer statischen Bibliothek verknüpft ist, wird Teil der App. Sie müssen keine andere Datei installieren, um den Code zu verwenden.

In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben behandelt:

- [Erstellen eines statischen Bibliotheksprojekts](#CreateLibProject)

- [Hinzufügen einer Klasse zur statischen Bibliothek](#AddClassToLib)

- [Erstellen einer Konsolenanwendung in C++, die auf die statische Bibliothek verweist](#CreateAppToRefTheLib)

- [Verwenden der Funktionalität der statischen Bibliothek in der App](#UseLibInApp)

- [Ausführen der App](#RunApp)

## <a name="prerequisites"></a>Voraussetzungen

Grundlegende Kenntnisse der Programmiersprache C++.

##  <a name="creating-a-static-library-project"></a><a name="CreateLibProject"></a> Erstellen eines statischen Bibliotheksprojekts

Die Anweisungen zum Erstellen des Projekts variieren in Abhängigkeit davon, ob Sie Visual Studio 2019 oder eine frühere Version verwenden. Stellen Sie sicher, dass die richtige Version in der oberen linken Ecke dieser Seite festgelegt ist.

::: moniker range="vs-2019"

### <a name="to-create-a-static-library-project-in-visual-studio-2019"></a>So erstellen Sie ein statisches Bibliotheksprojekt in Visual Studio 2019

1. Wählen Sie in der Menüleiste **Datei** > **neue** > **Projekt** aus, um das Dialogfeld **Neues Projekt erstellen** zu öffnen.

1. Legen Sie oben im Dialogfeld die **Sprache** auf **C++** , die **Plattform** auf **Windows** und den **Projekttyp** auf **Bibliothek** fest.

1. Wählen Sie in der gefilterten Liste der Projekttypen **statische Bibliothek** aus, und klicken Sie dann auf **weiter**. Geben Sie auf der nächsten Seite *MathFuncsLib* in das Feld **Name** ein, um einen Namen für das Projekt anzugeben, und geben Sie ggf. den Speicherort des Projekts an.

1. Klicken Sie auf die Schaltfläche **Erstellen**, um das Clientprojekt zu erstellen.

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-static-library-project-in-visual-studio-2017"></a>So erstellen Sie ein statisches Bibliotheksprojekt in Visual Studio 2017

1. Wählen Sie in der Menüleiste **Datei** > **Neu** > **Projekt** aus.

1. Erweitern Sie im linken Bereich des Dialog Felds **Neues Projekt** die Option **installiert** > **Visual C++** , und wählen Sie dann **Windows-Desktop**aus. Wählen Sie im mittleren Bereich **Windows-Desktop-Assistent** aus.

1. Geben Sie im Feld *Name*einen Namen für das Projekt ein, z. B. **MathFuncsLib** . Geben Sie im Feld *Projektmappenname*einen Namen für die Projektmappe ein, z. B. **StaticLibrary** . Klicken Sie auf die Schaltfläche **OK** .

1. Wählen Sie unter **Anwendungstyp**die Option **statische Bibliothek (. lib)** aus.

1. Deaktivieren Sie unter **zusätzliche Optionen**das Kontrollkästchen **vorkompilierter Header** .

1. Wählen Sie **OK** aus, um das Projekt zu erstellen.

::: moniker-end

::: moniker range="vs-2015"

### <a name="to-create-a-static-library-project-in-visual-studio-2015"></a>So erstellen Sie ein statisches Bibliotheksprojekt in Visual Studio 2015

1. Wählen Sie in der Menüleiste **Datei** > **Neu** > **Projekt** aus.

1. Erweitern Sie im Dialogfeld **Neues Projekt** den Eintrag **installierte** > **Vorlagen** > **Visualisierung C++** , und wählen Sie dann **Win32**aus. Wählen Sie im mittleren Bereich **Win32-Konsolenanwendung**aus.

1. Geben Sie im Feld *Name*einen Namen für das Projekt ein, z. B. **MathFuncsLib** . Geben Sie im Feld *Projektmappenname*einen Namen für die Projektmappe ein, z. B. **StaticLibrary** . Klicken Sie auf die Schaltfläche **OK** .

1. Klicken Sie auf **Weiter**.

1. Wählen Sie unter **Anwendungstyp**die Option **statische Bibliothek**aus. Deaktivieren Sie dann das Kontrollkästchen **vorkompilierter Header** , und wählen Sie **Fertig**stellen aus.

::: moniker-end

##  <a name="adding-a-class-to-the-static-library"></a><a name="AddClassToLib"></a> Hinzufügen einer Klasse zur statischen Bibliothek

### <a name="to-add-a-class-to-the-static-library"></a>So fügen Sie der statischen Bibliothek eine Klasse hinzu

1. Zum Erstellen einer Header Datei für eine neue Klasse öffnen Sie das Kontextmenü für das **MathFuncsLib** -Projekt in **Projektmappen-Explorer**, und wählen Sie dann > **Neues Element** **Hinzufügen** aus. Wählen Sie im linken Bereich des Dialogfelds **Neues Element hinzufügen** unter **Visual C++** die Option **Code**aus. Wählen Sie im mittleren Bereich die Option **Headerdatei (.h)** . Geben Sie einen Namen für die Headerdatei an, z. B. *MathFuncsLib.h*, und wählen Sie die Schaltfläche **Hinzufügen** aus. Eine leere Headerdatei wird angezeigt.

1. Fügen Sie eine Klasse mit dem Namen `MyMathFuncs` hinzu, um gängige mathematische Operationen wie Addition, Subtraktion, Multiplikation und Division durchzuführen. Der Code sollte wie folgt aussehen:

   [!code-cpp[NVC_Walkthrough_Create_Static_Lib#100](../windows/codesnippet/CPP/walkthrough-creating-and-using-a-static-library-cpp_1.h)]

1. Zum Erstellen einer Quelldatei für die neue Klasse öffnen Sie das Kontextmenü für das **MathFuncsLib** -Projekt in **Projektmappen-Explorer**, und wählen Sie dann > **Neues Element** **Hinzufügen** aus. Wählen Sie im linken Bereich des Dialogfelds **Neues Element hinzufügen** unter **Visual C++** die Option **Code**aus. Wählen Sie im mittleren Bereich die Option **C++-Datei (.cpp)** . Geben Sie einen Namen für die Quelldatei an, z. B. *MathFuncsLib.cpp*, und wählen Sie die Schaltfläche **Hinzufügen** aus. Eine leere Quelldatei wird angezeigt.

1. Verwenden Sie diese Quelldatei zum Implementieren der Funktionalität von **MyMathFuncs**. Der Code sollte wie folgt aussehen:

   [!code-cpp[NVC_Walkthrough_Create_Static_Lib#110](../windows/codesnippet/CPP/walkthrough-creating-and-using-a-static-library-cpp_2.cpp)]

1. Kompilieren Sie die statische Bibliothek, indem Sie **auf der** Menüleiste die Option **Build** > Projekt Mappe erstellen auswählen. Beim Kompilieren wird eine statische Bibliothek erstellt, die von anderen Programmen verwendet werden kann.

   > [!NOTE]
   > Beim Erstellen über die Befehlszeile von Visual Studio müssen Sie das Programm in zwei Schritten erstellen. Führen Sie zuerst `cl /c /EHsc MathFuncsLib.cpp` aus, um den Code zu kompilieren, und erstellen Sie eine Objektdatei mit dem Namen `MathFuncsLib.obj`. (Mit dem `cl`-Befehl wird der Compiler, "Cl.exe", aufgerufen, und mit der `/c`-Option wird Kompilieren ohne zu verknüpfen angegeben. Weitere Informationen finden Sie unter [/c (Kompilieren ohne Verknüpfen)](../build/reference/c-compile-without-linking.md).) Führen Sie als nächstes `lib MathFuncsLib.obj` aus, um den Code zu verknüpfen und die statische Bibliotheks `MathFuncsLib.lib`zu erstellen. (Mit dem `lib` Befehl wird der Bibliotheks-Manager, "Lib.exe", aufgerufen. Weitere Informationen finden Sie unter [LIB Reference](../build/reference/lib-reference.md).)

##  <a name="creating-a-c-console-app-that-references-the-static-library"></a><a name="CreateAppToRefTheLib"></a> Erstellen einer Konsolenanwendung in C++, die auf die statische Bibliothek verweist

::: moniker range="vs-2019"

### <a name="to-create-a-c-console-app-that-references-the-static-library-in-visual-studio-2019"></a>So erstellen Sie C++ eine Konsolen-APP, die in Visual Studio 2019 auf die statische Bibliothek verweist

1. Klicken Sie in **Projektmappen-Explorer**mit der rechten Maustaste auf den obersten Knoten der Projekt Mappe, und wählen Sie > **Neues Projekt** **Hinzufügen** aus, um das Dialogfeld **Neues Projekt hinzufügen** zu öffnen.

1. Legen Sie oben im Dialogfeld die **Sprache** auf **C++** , die **Plattform** auf **Windows** und den **Projekttyp** auf **Konsole** fest.

1. Wählen Sie aus der gefilterten Projekttypliste **Konsolen-App** aus, und klicken Sie auf **Weiter**. Geben Sie auf der nächsten Seite im Feld **Name** den Namen *MyExecRefsLib* ein, um einen Namen für das Projekt anzugeben, und geben Sie ggf. den Speicherort des Projekts an.

1. Klicken Sie auf die Schaltfläche **Erstellen**, um das Clientprojekt zu erstellen.

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-c-console-app-that-references-the-static-library-in-visual-studio-2017"></a>So erstellen Sie C++ eine Konsolen-APP, die in Visual Studio 2017 auf die statische Bibliothek verweist

1. Wählen Sie in der Menüleiste **Datei** > **Neu** > **Projekt** aus.

1. Erweitern Sie im linken Bereich des Dialog Felds **Neues Projekt** die Option **installiert** > **Visual C++** , und wählen Sie dann **Windows-Desktop**aus. Wählen Sie im mittleren Bereich **Windows-Desktop-Assistent** aus.

1. Geben Sie im Feld *Name*einen Namen für das Projekt ein, z. B. **MyExecRefsLib** . Wählen Sie in der Dropdownliste neben **Projektmappe**die Option **Hinzufügen**aus. Mit dem Befehl wird das neue Projekt der Projekt Mappe hinzugefügt, die die statische Bibliothek enthält. Klicken Sie auf die Schaltfläche **OK** .

1. Wählen Sie unter **Anwendungstyp**die Option **Konsolenanwendung (. exe)** aus.

1. Deaktivieren Sie unter **zusätzliche Optionen**das Kontrollkästchen **vorkompilierter Header** .

1. Wählen Sie **OK** aus, um das Projekt zu erstellen.

::: moniker-end

::: moniker range="vs-2015"

### <a name="to-create-a-c-console-app-that-references-the-static-library-in-visual-studio-2015"></a>So erstellen Sie C++ eine Konsolen-APP, die in Visual Studio 2015 auf die statische Bibliothek verweist

1. Wählen Sie in der Menüleiste **Datei** > **Neu** > **Projekt** aus.

1. Erweitern Sie im Dialogfeld **Neues Projekt** den Eintrag **installierte** > **Vorlagen** > **Visualisierung C++** , und wählen Sie dann **Win32**aus. Wählen Sie im mittleren Bereich **Win32-Konsolenanwendung**aus.

1. Geben Sie im Feld *Name*einen Namen für das Projekt ein, z. B. **MyExecRefsLib** . Wählen Sie in der Dropdownliste neben **Projektmappe**die Option **Hinzufügen**aus. Mit dem Befehl wird das neue Projekt der Projekt Mappe hinzugefügt, die die statische Bibliothek enthält. Klicken Sie auf die Schaltfläche **OK** .

1. Klicken Sie auf **Weiter**.

1. Stellen Sie sicher, dass **Konsolenanwendung** ausgewählt ist. Aktivieren Sie dann das Feld **leeres Projekt** , und wählen Sie **Fertig**stellen aus.

::: moniker-end

##  <a name="using-the-functionality-from-the-static-library-in-the-app"></a><a name="UseLibInApp"></a> Verwenden der Funktionalität der statischen Bibliothek in der App

### <a name="to-use-the-functionality-from-the-static-library-in-the-app"></a>So verwenden Sie die Funktionalität der statischen Bibliothek in der App

1. Nach dem Erstellen einer Konsolenanwendung wird ein leeres Programm für Sie erstellt. Die Quelldatei erhält denselben Namen, den Sie zuvor ausgewählt haben. Im Beispiel wird `MyExecRefsLib.cpp`benannt.

1. Bevor Sie die mathematischen Routinen verwenden können, müssen Sie auf die erstellte statische Bibliothek verweisen. Öffnen Sie das Kontextmenü für das Projekt **myexecref slib** in **Projektmappen-Explorer**, und wählen Sie dann > **Verweis** **Hinzufügen** aus.

1. Im Dialogfeld **Verweis hinzufügen** werden Bibliotheken aufgeführt, auf die Sie verweisen können. Auf der Registerkarte **Projekte** werden die Projekte in der aktuellen Projekt Mappe und alle Bibliotheken aufgelistet, auf die Sie verweisen. Aktivieren Sie auf der Registerkarte **Projekte** das Kontrollkästchen **MathFuncsLib** aus, und wählen Sie dann die Schaltfläche **OK** aus.

1. Um auf die `MathFuncsLib.h` Header Datei zu verweisen, müssen Sie den eingeschlossenen Verzeichnispfad ändern. Erweitern Sie im Dialogfeld **Eigenschaftenseiten** von **MyExecRefsLib**den Knoten **Konfigurationseigenschaften** , erweitern Sie den Knoten **C/C++** , und wählen Sie dann **Allgemein**aus. Geben Sie neben **Zusätzliche Includeverzeichnisse**den Pfad des **MathFuncsLib** -Verzeichnisses ein, oder suchen Sie nach dem Verzeichnis.

   Um nach dem Verzeichnispfad zu suchen, öffnen Sie die Dropdownliste für Eigenschaftswerte, und wählen Sie dann **Bearbeiten**aus. Wählen Sie im Dialogfeld **Zusätzliche Includeverzeichnisse** im Textfeld eine Leerzeile aus, und klicken Sie dann auf die Schaltfläche mit den Auslassungs Punkten ( **...** ) am Ende der Zeile. Wählen Sie im Dialogfeld **Verzeichnis auswählen** das **MathFuncsLib** -Verzeichnis aus, und wählen Sie dann die **Ordner auswählen** -Schaltfläche aus, um die Auswahl zu speichern und das Dialogfeld zu schließen. Wählen Sie im Dialogfeld **Zusätzliche Includeverzeichnisse** die Schaltfläche **OK** aus, und wählen Sie dann im Dialogfeld **Eigenschaftenseiten** die Schaltfläche **OK** aus, um die Änderungen am Projekt zu speichern.

1. Sie können jetzt die `MyMathFuncs`-Klasse in dieser APP verwenden, indem Sie den `#include "MathFuncsLib.h"`-Header in Ihren Code einschließen. Ersetzen Sie den Inhalt `MyExecRefsLib.cpp` durch den folgenden Code:

   [!code-cpp[NVC_Walkthrough_Create_Static_Lib#120](../windows/codesnippet/CPP/walkthrough-creating-and-using-a-static-library-cpp_3.cpp)]

1. Erstellen Sie die ausführbare Datei, indem Sie auf der Menüleiste auf **Erstellen** > Projekt **Mappe erstellen klicken**

##  <a name="running-the-app"></a><a name="RunApp"></a> Ausführen der App

### <a name="to-run-the-app"></a>So führen Sie die App aus

1. Stellen Sie sicher, dass **MyExecRefsLib** als Standardprojekt ausgewählt wurde. Öffnen Sie dazu das Kontextmenü von **MyExecRefsLib** im **Projektmappen-Explorer**, und wählen Sie anschließend **Als Startprojekt festlegen**aus.

1. Klicken Sie zum Ausführen des Projekts auf der Menüleiste auf **Debuggen** > **Starten ohne Debuggen**. Die Ausgabe sollte wie folgt aussehen:

    ```Output
    a + b = 106.4
    a - b = -91.6
    a * b = 732.6
    a / b = 0.0747475
    ```

## <a name="see-also"></a>Weitere Informationen

[Exemplarische Vorgehensweise: Erstellen und Verwenden einer Dynamic Link Library (C++)](../build/walkthrough-creating-and-using-a-dynamic-link-library-cpp.md)<br/>
[Desktopanwendungen (Visual C++)](../windows/desktop-applications-visual-cpp.md)<br/>
