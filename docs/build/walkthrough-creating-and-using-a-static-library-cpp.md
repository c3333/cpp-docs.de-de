---
title: 'Exemplarische Vorgehensweise: Erstellen einer statischen Bibliothek (C++)'
description: Verwenden Sie C++, um eine statische Bibliothek (.lib) in Visual Studio zu erstellen.
ms.custom: get-started-article
ms.date: 04/13/2020
helpviewer_keywords:
- libraries [C++], static
- static libraries [C++]
ms.assetid: 3cc36411-7d66-4240-851e-dacb9a8fd6ac
ms.openlocfilehash: 6cb379baafc506570b1bdc1b286b35c40f8cd0d8
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "92924372"
---
# <a name="walkthrough-create-and-use-a-static-library"></a>Exemplarische Vorgehensweise: Erstellen und Verwenden einer statischen Bibliothek

In dieser schrittweise erläuterten exemplarischen Vorgehensweise wird die Erstellung einer statischen Bibliothek (LIB-Datei) für die Verwendung mit C++-Apps erläutert. Die Verwendung einer statischen Bibliothek stellt eine gute Möglichkeit zur Wiederverwendung von Code dar. Anstatt in jeder App, für die eine bestimmte Funktion erforderlich ist, die gleichen Routinen immer wieder zu implementieren, schreiben Sie sie einmal in eine statische Bibliothek und verweisen dann in den Apps darauf. Code in einer statischen Bibliothek, auf den verwiesen wird, wird Teil der App. Sie müssen keine andere Datei installieren, um den Code zu verwenden.

In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben behandelt:

- [Erstellen eines statischen Bibliotheksprojekts](#CreateLibProject)

- [Hinzufügen einer Klasse zur statischen Bibliothek](#AddClassToLib)

- [Erstellen einer Konsolen-App in C++, die auf die statische Bibliothek verweist](#CreateAppToRefTheLib)

- [Verwenden der Funktionalität der statischen Bibliothek in der App](#UseLibInApp)

- [Ausführen der App](#RunApp)

## <a name="prerequisites"></a>Voraussetzungen

Grundlegende Kenntnisse der Programmiersprache C++.

## <a name="create-a-static-library-project"></a><a name="CreateLibProject"></a> Erstellen eines statischen Bibliotheksprojekts

Die Anweisungen für das Erstellen des Projekts variieren abhängig von Ihrer Version von Visual Studio. Um die Dokumentation für Ihre bevorzugte Version von Visual Studio anzuzeigen, verwenden Sie das Auswahlsteuerelement **Version**. Es befindet sich am Anfang des Inhaltsverzeichnisses auf dieser Seite.

::: moniker range="msvc-160"

### <a name="to-create-a-static-library-project-in-visual-studio-2019"></a>Erstellen eines statischen Bibliotheksprojekts in Visual Studio 2019

1. Klicken Sie in der Menüleiste auf **Datei**  > **Neu**  > **Projekt** , um das Dialogfeld **Neues Projekt erstellen** zu öffnen.

1. Legen Sie oben im Dialogfeld die **Sprache** auf **C++** , die **Plattform** auf **Windows** und den **Projekttyp** auf **Bibliothek** fest.

1. Wählen Sie aus der gefilterten Projekttypliste **Windows-Desktopassistent** aus, und klicken Sie auf **Weiter**.

1. Geben Sie auf der Seite **Neues Projekt konfigurieren** in das Feld **Projektname** den Namen *MathLibrary* ein, um einen Namen für das Projekt festzulegen. Geben Sie in das Feld **Projektmappenname** den Namen *StaticMath* ein. Klicken Sie auf die Schaltfläche **Erstellen** , um das Dialogfeld **Windows-Desktopprojekt** zu öffnen.

1. Wählen Sie im Dialogfeld **Windows-Desktopprojekt** unter **Anwendungstyp** den Eintrag **Statische Bibliothek (.lib)** aus.

1. Deaktivieren Sie unter **Zusätzliche Optionen** das Kontrollkästchen bei **Vorkompilierter Header** , wenn es aktiviert ist. Aktivieren Sie das Feld bei **Leeres Projekt**.

1. Klicken Sie auf **OK** , um das Projekt zu erstellen.

::: moniker-end

::: moniker range="msvc-150"

### <a name="to-create-a-static-library-project-in-visual-studio-2017"></a>Erstellen eines statischen Bibliotheksprojekts in Visual Studio 2017

1. Wählen Sie in der Menüleiste **Datei** > **Neu** > **Projekt** aus.

1. Klicken Sie im Dialogfeld **Neues Projekt** auf **Installiert** > **Visual C++**  > **Windows Desktop**. Wählen Sie im mittleren Bereich **Windows-Desktop-Assistent** aus.

1. Geben Sie im Feld **Name** einen Namen für das Projekt an, z. B. *MathLibrary*. Geben Sie im Feld **Projektmappenname** einen Namen für die Projektmappe an, z. B. *StaticMath*. Klicken Sie auf die Schaltfläche **OK** .

1. Wählen Sie im Dialogfeld **Windows-Desktopprojekt** unter **Anwendungstyp** den Eintrag **Statische Bibliothek (.lib)** aus.

1. Deaktivieren Sie unter **Zusätzliche Optionen** das Kontrollkästchen bei **Vorkompilierter Header** , wenn es aktiviert ist. Aktivieren Sie das Feld bei **Leeres Projekt**.

1. Klicken Sie auf **OK** , um das Projekt zu erstellen.

::: moniker-end

::: moniker range="msvc-140"

### <a name="to-create-a-static-library-project-in-visual-studio-2015"></a>Erstellen eines statischen Bibliotheksprojekts in Visual Studio 2015

1. Wählen Sie in der Menüleiste **Datei** > **Neu** > **Projekt** aus.

1. Klicken Sie im Dialogfeld **Neues Projekt** auf **Installiert** > **Vorlagen** > **Visual C++**  > **Win32**. Wählen Sie im mittleren Bereich **Win32-Konsolenanwendung** aus.

1. Geben Sie im Feld **Name** einen Namen für das Projekt an, z. B. *MathLibrary*. Geben Sie im Feld **Projektmappenname** einen Namen für die Projektmappe an, z. B. *StaticMath*. Klicken Sie auf die Schaltfläche **OK** .

1. Klicken Sie im **Win32-Anwendungs-Assistenten** auf **Weiter**.

1. Wählen Sie auf der Seite **Anwendungseinstellungen** unter **Anwendungstyp** **Statische Bibliothek** aus. Deaktivieren Sie unter **Zusätzliche Optionen** das Kontrollkästchen bei **Vorkompilierter Header**. Klicken Sie auf **Fertig stellen** , um das Projekt zu erstellen.

::: moniker-end

## <a name="add-a-class-to-the-static-library"></a><a name="AddClassToLib"></a> Hinzufügen einer Klasse zur statischen Bibliothek

### <a name="to-add-a-class-to-the-static-library"></a>So fügen Sie der statischen Bibliothek eine Klasse hinzu

1. Öffnen Sie per Rechtsklick das Kontextmenü für das Projekt **MathLibrary** im **Projektmappen-Explorer** , und klicken Sie dann auf **Hinzufügen** > **Neues Element** , um eine Headerdatei für eine neue Klasse zu erstellen.

1. Klicken Sie im Dialogfeld **Neues Element hinzufügen** auf **Visual C++**  > **Code**. Wählen Sie im mittleren Bereich die Option **Headerdatei (.h)** . Geben Sie einen Namen für die Headerdatei an, z. B. *MathLibrary.h* , und klicken Sie auf die Schaltfläche **Hinzufügen**. Eine nahezu leere Headerdatei wird angezeigt.

1. Fügen Sie eine Deklaration für eine Klasse mit dem Namen `Arithmetic` hinzu, die zur Ausführung geläufiger mathematischer Operationen wie Addition, Subtraktion, Multiplikation und Division dient. Der Code sollte diesem ähneln:

    ```cpp
    // MathLibrary.h
    #pragma once

    namespace MathLibrary
    {
        class Arithmetic
        {
        public:
            // Returns a + b
            static double Add(double a, double b);

            // Returns a - b
            static double Subtract(double a, double b);

            // Returns a * b
            static double Multiply(double a, double b);

            // Returns a / b
            static double Divide(double a, double b);
        };
    }
    ```

1. Öffnen Sie das Kontextmenü für das Projekt **MathLibrary** im **Projektmappen-Explorer** , und klicken Sie dann auf **Hinzufügen** > **Neues Element** , um eine Quelldatei für die neue Klasse zu erstellen.

1. Klicken Sie im mittleren Bereich des Dialogfelds **Neues Element hinzufügen** auf **C++-Datei (.cpp)** . Geben Sie einen Namen für die Quelldatei an, z. B. *MathLibrary.cpp* , und klicken Sie auf die Schaltfläche **Hinzufügen**. Eine leere Quelldatei wird angezeigt.

1. Verwenden Sie diese Quelldatei zum Implementieren der Funktionalität für die Klasse `Arithmetic`. Der Code sollte diesem ähneln:

    ```cpp
    // MathLibrary.cpp
    // compile with: cl /c /EHsc MathLibrary.cpp
    // post-build command: lib MathLibrary.obj

    #include "MathLibrary.h"

    namespace MathLibrary
    {
        double Arithmetic::Add(double a, double b)
        {
            return a + b;
        }

        double Arithmetic::Subtract(double a, double b)
        {
            return a - b;
        }

        double Arithmetic::Multiply(double a, double b)
        {
            return a * b;
        }

        double Arithmetic::Divide(double a, double b)
        {
            return a / b;
        }
    }
    ```

1. Erstellen Sie die statische Bibliothek, indem Sie in der Menüleiste auf **Erstellen** > **Projektmappe erstellen** klicken. Dadurch wird eine statische Bibliothek erstellt, *MathLibrary.lib* , die in anderen Programmen verwendet werden kann.

   > [!NOTE]
   > Beim Erstellen über die Befehlszeile von Visual Studio müssen Sie das Programm in zwei Schritten erstellen. Führen Sie zunächst `cl /c /EHsc MathLibrary.cpp` aus, um den Code zu kompilieren und eine Objektdatei namens *MathLibrary.obj* zu erstellen. (Mit dem `cl`-Befehl wird der Compiler, "Cl.exe", aufgerufen, und mit der `/c`-Option wird Kompilieren ohne zu verknüpfen angegeben. Weitere Informationen finden Sie unter [/c (Kompilieren ohne Verknüpfen)](../build/reference/c-compile-without-linking.md).) Führen Sie anschließend `lib MathLibrary.obj` aus, um den Code zu verknüpfen und die statische Bibliothek *MathLibrary.lib* zu erstellen. (Mit dem `lib` Befehl wird der Bibliotheks-Manager, "Lib.exe", aufgerufen. Weitere Informationen finden Sie unter [LIB Reference](../build/reference/lib-reference.md).)

## <a name="create-a-c-console-app-that-references-the-static-library"></a><a name="CreateAppToRefTheLib"></a> Erstellen einer Konsolen-App in C++, die auf die statische Bibliothek verweist

::: moniker range="msvc-160"

### <a name="to-create-a-c-console-app-that-references-the-static-library-in-visual-studio-2019"></a>Erstellen einer Konsolen-App in C++, die auf die statische Bibliothek verweist, in Visual Studio 2019

1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf den obersten Knoten, die **Projektmappe „StaticMath“** , um das Kontextmenü zu öffnen. Klicken Sie auf **Hinzufügen** > **Neues Projekt** , um das Dialogfeld **Neues Projekt hinzufügen** zu öffnen.

1. Legen Sie oben im Dialogfeld für den Filter **Projekttyp** **Konsole** fest.

1. Wählen Sie aus der gefilterten Projekttypliste **Konsolen-App** aus, und klicken Sie auf **Weiter**. Geben Sie auf der nächsten Seite im Feld **Name** *MathClient* als Projektnamen an.

1. Klicken Sie auf die Schaltfläche **Erstellen** , um das Clientprojekt zu erstellen.

1. Nach dem Erstellen einer Konsolenanwendung wird ein leeres Programm für Sie erstellt. Die Quelldatei erhält denselben Namen, den Sie zuvor ausgewählt haben. In diesem Beispiel heißt sie `MathClient.cpp`.

::: moniker-end

::: moniker range="msvc-150"

### <a name="to-create-a-c-console-app-that-references-the-static-library-in-visual-studio-2017"></a>Erstellen einer Konsolen-App in C++, die auf die statische Bibliothek verweist, in Visual Studio 2017

1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf den obersten Knoten, die **Projektmappe „StaticMath“** , um das Kontextmenü zu öffnen. Klicken Sie auf **Hinzufügen** > **Neues Projekt** , um das Dialogfeld **Neues Projekt hinzufügen** zu öffnen.

1. Klicken Sie im Dialogfeld **Neues Projekt hinzufügen** auf **Installiert** > **Visual C++**  > **Windows Desktop**. Wählen Sie im mittleren Bereich **Windows-Desktop-Assistent** aus.

1. Geben Sie im Feld **Name** einen Namen für das Projekt an, z. B. *MathClient*. Klicken Sie auf die Schaltfläche **OK** .

1. Wählen Sie im Dialogfeld **Windows-Desktopprojekt** unter **Anwendungstyp** den Eintrag **Konsolenanwendung (.exe)** aus.

1. Deaktivieren Sie unter **Zusätzliche Optionen** das Kontrollkästchen bei **Vorkompilierter Header** , wenn es aktiviert ist.

1. Klicken Sie auf **OK** , um das Projekt zu erstellen.

1. Nach dem Erstellen einer Konsolenanwendung wird ein leeres Programm für Sie erstellt. Die Quelldatei erhält denselben Namen, den Sie zuvor ausgewählt haben. In diesem Beispiel heißt sie `MathClient.cpp`.

::: moniker-end

::: moniker range="msvc-140"

### <a name="to-create-a-c-console-app-that-references-the-static-library-in-visual-studio-2015"></a>Erstellen einer Konsolen-App in C++, die auf die statische Bibliothek verweist, in Visual Studio 2015

1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf den obersten Knoten, die **Projektmappe „StaticMath“** , um das Kontextmenü zu öffnen. Klicken Sie auf **Hinzufügen** > **Neues Projekt** , um das Dialogfeld **Neues Projekt hinzufügen** zu öffnen.

1. Klicken Sie im Dialogfeld **Neues Projekt hinzufügen** auf **Installiert** > **Visual C++**  > **Win32**. Wählen Sie im mittleren Bereich **Win32-Konsolenanwendung** aus.

1. Geben Sie im Feld **Name** einen Namen für das Projekt an, z. B. *MathClient*. Klicken Sie auf die Schaltfläche **OK** .

1. Klicken Sie im Dialogfeld **Win32-Anwendungs-Assistent** auf **Weiter**.

1. Stellen Sie sicher, dass auf der Seite **Anwendungseinstellungen** unter **Anwendungstyp** **Konsolenanwendung** ausgewählt ist. Deaktivieren Sie unter **Zusätzliche Optionen** das Kontrollkästchen bei **Vorkompilierter Header** , und aktivieren Sie dann das Kontrollkästchen bei **Leeres Projekt**. Klicken Sie auf **Fertig stellen** , um das Projekt zu erstellen.

1. Öffnen Sie per Rechtsklick das Kontextmenü für das Projekt **MathClient** im **Projektmappen-Explorer** , und klicken Sie dann auf **Hinzufügen**  > **Neues Element** , um eine Quelldatei zum leeren Projekt hinzuzufügen.

1. Klicken Sie im Dialogfeld **Neues Element hinzufügen** auf **Visual C++**  > **Code**. Wählen Sie im mittleren Bereich die Option **C++-Datei (.cpp)** . Geben Sie einen Namen für die Quelldatei an, z. B. *MathClient.cpp* , und klicken Sie auf die Schaltfläche **Hinzufügen**. Eine leere Quelldatei wird angezeigt.

::: moniker-end

## <a name="use-the-functionality-from-the-static-library-in-the-app"></a><a name="UseLibInApp"></a> Verwenden der Funktionalität der statischen Bibliothek in der App

### <a name="to-use-the-functionality-from-the-static-library-in-the-app"></a>So verwenden Sie die Funktionalität der statischen Bibliothek in der App

1. Bevor Sie die mathematischen Routinen verwenden können, müssen Sie auf die erstellte statische Bibliothek verweisen. Öffnen Sie das Kontextmenü für das Projekt **MathClient** im **Projektmappen-Explorer** , und klicken Sie dann auf **Hinzufügen** > **Verweis**.

1. Im Dialogfeld **Verweis hinzufügen** werden Bibliotheken aufgeführt, auf die Sie verweisen können. Auf der Registerkarte **Projekte** sind die Projekte in der aktuellen Projektmappe aufgeführt sowie die Bibliotheken, auf die in ihnen verwiesen wird. Öffnen Sie die Registerkarte **Projekte** , aktivieren Sie das Kontrollkästchen bei **MathLibrary** , und klicken Sie dann auf die Schaltfläche **OK**.

1. Wenn Sie auf die Headerdatei `MathLibrary.h` verweisen möchten, müssen Sie den enthaltenen Verzeichnispfad ändern. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf **MathClient** , um das Kontextmenü zu öffnen. Klicken Sie auf **Eigenschaften** , um das Dialogfeld **MathClient Eigenschaftenseiten** zu öffnen.

1. Wählen Sie im Dialogfeld **MathClient Eigenschaftenseiten** in der Dropdownliste **Konfiguration** die Option **Alle Konfigurationen** aus. Wählen Sie in der Dropdownliste **Plattform** die Option **Alle Plattformen** aus.

1. Navigieren Sie zur Eigenschaftenseite **Konfigurationseigenschaften** > **C/C++**  > **Allgemein**. Geben Sie bei der Eigenschaft **Zusätzliche Includeverzeichnisse** den Pfad des **MathLibrary** -Verzeichnisses an, oder suchen Sie danach.

   So suchen Sie nach dem Verzeichnispfad:

   1. Öffnen Sie die Dropdownliste für Eigenschaftswerte **Zusätzliche Includeverzeichnisse** , und klicken Sie dann auf **Bearbeiten**.

   1. Doppelklicken Sie im Dialogfeld **Zusätzliche Includeverzeichnisse** in den oberen Bereich des Textfelds. Klicken Sie dann am Ende der Zeile auf die Schaltfläche mit den drei Punkten ( **...** ).

   1. Navigieren Sie im Dialogfeld **Verzeichnis auswählen** eine Ebene weiter nach oben, und klicken Sie dann auf das **MathLibrary** -Verzeichnis. Klicken Sie anschließend auf die Schaltfläche **Ordner auswählen** , um Ihre Auswahl zu speichern.

   1. Klicken Sie im Dialogfeld **Zusätzliche Includeverzeichnisse** auf die Schaltfläche **OK**.

   1. Klicken Sie im Dialogfeld **Eigenschaftenseiten** auf die Schaltfläche **OK** , um Ihre Änderungen am Projekt zu speichern.

1. Sie können nun die Klasse `Arithmetic` in dieser App verwenden, indem Sie den Header `#include "MathLibrary.h"` in Ihrem Code verwenden. Ersetzen Sie den Inhalt von `MathClient.cpp` durch den folgenden Code:

    ```cpp
    // MathClient.cpp
    // compile with: cl /EHsc MathClient.cpp /link MathLibrary.lib

    #include <iostream>
    #include "MathLibrary.h"

    int main()
    {
        double a = 7.4;
        int b = 99;

        std::cout << "a + b = " <<
            MathLibrary::Arithmetic::Add(a, b) << std::endl;
        std::cout << "a - b = " <<
            MathLibrary::Arithmetic::Subtract(a, b) << std::endl;
        std::cout << "a * b = " <<
            MathLibrary::Arithmetic::Multiply(a, b) << std::endl;
        std::cout << "a / b = " <<
            MathLibrary::Arithmetic::Divide(a, b) << std::endl;

        return 0;
    }
    ```

1. Erstellen Sie die ausführbare Datei, indem Sie in der Menüleiste auf **Erstellen** > **Projektmappe erstellen** klicken.

## <a name="run-the-app"></a><a name="RunApp"></a> Ausführen der App

### <a name="to-run-the-app"></a>So führen Sie die App aus

1. Stellen Sie sicher, dass **MathClient** als Standardprojekt ausgewählt ist. Öffnen Sie per Rechtsklick das Kontextmenü für das Projekt **MathClient** im **Projektmappen-Explorer** , und klicken Sie dann auf **Als Startprojekt festlegen** , um es als Standardprojekt auszuwählen.

1. Klicken Sie zum Ausführen des Projekts auf der Menüleiste auf **Debuggen** > **Starten ohne Debuggen**. Die Ausgabe sollte in etwa wie folgt aussehen:

    ```Output
    a + b = 106.4
    a - b = -91.6
    a * b = 732.6
    a / b = 0.0747475
    ```

## <a name="see-also"></a>Siehe auch

[Exemplarische Vorgehensweise: Erstellen und Verwenden einer Dynamic Link Library (C++)](../build/walkthrough-creating-and-using-a-dynamic-link-library-cpp.md)<br/>
[Desktopanwendungen (Visual C++)](../windows/desktop-applications-visual-cpp.md)<br/>
