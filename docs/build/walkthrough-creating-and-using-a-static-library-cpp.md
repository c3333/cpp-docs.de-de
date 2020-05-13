---
title: 'Exemplarische Vorgehensweise: Erstellen und Verwenden einer statischen Bibliothek (C++)'
description: Verwenden Sie C++, um eine statische Bibliothek (.lib) in Visual Studio zu erstellen.
ms.custom: get-started-article
ms.date: 04/13/2020
helpviewer_keywords:
- libraries [C++], static
- static libraries [C++]
ms.assetid: 3cc36411-7d66-4240-851e-dacb9a8fd6ac
ms.openlocfilehash: 7148cc1de7c06ae57d61560311b342a1fc9dda1f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81335140"
---
# <a name="walkthrough-create-and-use-a-static-library"></a>Exemplarische Vorgehensweise: Erstellen und Verwenden einer statischen Bibliothek

In dieser schrittweise erläuterten exemplarischen Vorgehensweise wird die Erstellung einer statischen Bibliothek (LIB-Datei) für die Verwendung mit C++-Apps erläutert. Die Verwendung einer statischen Bibliothek stellt eine gute Möglichkeit zur Wiederverwendung von Code dar. Anstatt die gleichen Routinen in jeder App, die die Funktionalität erfordert, neu zu implementieren, schreiben Sie sie einmal in eine statische Bibliothek und verweisen dann auf sie aus den Apps. Code, der von einer statischen Bibliothek verknüpft ist, wird Teil Ihrer App – Sie müssen keine andere Datei installieren, um den Code zu verwenden.

In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben behandelt:

- [Erstellen eines statischen Bibliotheksprojekts](#CreateLibProject)

- [Hinzufügen einer Klasse zur statischen Bibliothek](#AddClassToLib)

- [Erstellen einer C++-Konsolen-App, die auf die statische Bibliothek verweist](#CreateAppToRefTheLib)

- [Verwenden der Funktionalität aus der statischen Bibliothek in der App](#UseLibInApp)

- [Ausführen der App](#RunApp)

## <a name="prerequisites"></a>Voraussetzungen

Grundlegende Kenntnisse der Programmiersprache C++.

## <a name="create-a-static-library-project"></a><a name="CreateLibProject"></a>Erstellen eines statischen Bibliotheksprojekts

Die Anweisungen zum Erstellen des Projekts hängen von Ihrer Version von Visual Studio ab. Verwenden Sie das Versionsauswahlsteuerelement, um die **Version** Dokumentation für Ihre bevorzugte Version von Visual Studio anzuzeigen. Es befindet sich oben im Inhaltsverzeichnis auf dieser Seite.

::: moniker range="vs-2019"

### <a name="to-create-a-static-library-project-in-visual-studio-2019"></a>So erstellen Sie ein statisches Bibliotheksprojekt in Visual Studio 2019

1. Klicken Sie in der Menüleiste auf **Datei** > **Neu** > **Projekt**, um das Dialogfeld **Neues Projekt erstellen** zu öffnen.

1. Legen Sie oben im Dialogfeld die **Sprache** auf **C++**, die **Plattform** auf **Windows** und den **Projekttyp** auf **Bibliothek** fest.

1. Wählen Sie in der gefilterten Liste der Projekttypen **den Windows-Desktop-Assistenten**aus , und wählen Sie dann **Weiter**aus.

1. Geben Sie im **Feld Konfigurieren der neuen Projektseite** *MathLibrary* in das Feld **Projektname** ein, um einen Namen für das Projekt anzugeben. Geben Sie *StaticMath* in das Feld **Projektmappenname ein.** Wählen Sie die Schaltfläche **Erstellen** aus, um das **Dialogfeld Windows Desktop Project** zu öffnen.

1. Wählen Sie im Dialogfeld **Windows Desktop Project** unter **Anwendungstyp** **die Option Statische Bibliothek (.lib)** aus.

1. Deaktivieren Sie unter **Zusätzliche Optionen**das Kontrollkästchen **Vorkompilierte Kopfzeile,** wenn diese option. Aktivieren Sie das Kontrollkästchen **Leeres Projekt.**

1. Wählen Sie **OK,** um das Projekt zu erstellen.

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-static-library-project-in-visual-studio-2017"></a>So erstellen Sie ein statisches Bibliotheksprojekt in Visual Studio 2017

1. Wählen Sie in der Menüleiste **Datei** > **Neu** > **Projekt** aus.

1. Wählen Sie im Dialogfeld **Neues Projekt** die Option **Installiertes** > **Visual C++** > **Windows Desktop**aus. Wählen Sie im mittleren Bereich **Windows-Desktop-Assistent** aus.

1. Geben Sie im Feld **Name** einen Namen für das Projekt an, z. B. *MathLibrary.* Geben Sie im Feld **Lösungsname** einen Namen für die Projektmappe an, z. B. *StaticMath.* Klicken Sie auf die Schaltfläche **OK** .

1. Wählen Sie im Dialogfeld **Windows Desktop Project** unter **Anwendungstyp** **die Option Statische Bibliothek (.lib)** aus.

1. Deaktivieren Sie unter **Zusätzliche Optionen**das Kontrollkästchen **Vorkompilierte Kopfzeile,** wenn diese option. Aktivieren Sie das Kontrollkästchen **Leeres Projekt.**

1. Wählen Sie **OK,** um das Projekt zu erstellen.

::: moniker-end

::: moniker range="vs-2015"

### <a name="to-create-a-static-library-project-in-visual-studio-2015"></a>So erstellen Sie ein statisches Bibliotheksprojekt in Visual Studio 2015

1. Wählen Sie in der Menüleiste **Datei** > **Neu** > **Projekt** aus.

1. Wählen Sie im Dialogfeld **Neues Projekt** die Option **Installierte** > **Vorlagen** > **Visual C++** > **Win32**aus. Wählen Sie im mittleren Bereich **Win32-Konsolenanwendung**aus.

1. Geben Sie im Feld **Name** einen Namen für das Projekt an, z. B. *MathLibrary.* Geben Sie im Feld **Lösungsname** einen Namen für die Projektmappe an, z. B. *StaticMath.* Klicken Sie auf die Schaltfläche **OK** .

1. Wählen Sie im **Win32-Anwendungs-Assistenten** **Weiter**aus.

1. Wählen Sie auf der Seite **Anwendungseinstellungen** unter **Anwendungstyp**die Option **Statische Bibliothek**aus. Deaktivieren Sie unter **Zusätzliche Optionen**das Kontrollkästchen **Vorkompilierte Kopfzeile.** Wählen Sie **Fertig stellen** aus, um das Projekt zu erstellen.

::: moniker-end

## <a name="add-a-class-to-the-static-library"></a><a name="AddClassToLib"></a>Hinzufügen einer Klasse zur statischen Bibliothek

### <a name="to-add-a-class-to-the-static-library"></a>So fügen Sie der statischen Bibliothek eine Klasse hinzu

1. Um eine Headerdatei für eine neue Klasse zu erstellen, klicken Sie mit der rechten Maustaste, um das Kontextmenü für das **MathLibrary-Projekt** im **Projektmappen-Explorer**zu öffnen, und wählen Sie dann**Neues Element** **hinzufügen** > aus.

1. Wählen Sie im Dialogfeld **Neues Element hinzufügen** die Option Visual **C++** > **Code**aus. Wählen Sie im mittleren Bereich die Option **Headerdatei (.h)**. Geben Sie einen Namen für die Headerdatei an, z. *B. MathLibrary.h,* und wählen Sie dann die Schaltfläche **Hinzufügen** aus. Eine nahezu leere Headerdatei wird angezeigt.

1. Fügen Sie eine Deklaration für eine Klasse hinzu, die für allgemeine mathematische Operationen wie Addition, Subtraktion, Multiplikation und Division benannt `Arithmetic` ist. Der Code sollte wie folgt aussehen:

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

1. Um eine Quelldatei für die neue Klasse zu erstellen, öffnen Sie das Kontextmenü für das **MathLibrary-Projekt** im **Projektmappen-Explorer**, und wählen Sie dann**Neues Element** **hinzufügen** > aus.

1. Wählen Sie im Dialogfeld **Neues Element hinzufügen** im mittleren Bereich **C++-Datei (.cpp)** aus. Geben Sie einen Namen für die Quelldatei an, z. *B. MathLibrary.cpp,* und wählen Sie dann die Schaltfläche **Hinzufügen** aus. Eine leere Quelldatei wird angezeigt.

1. Verwenden Sie diese Quelldatei, `Arithmetic`um die Funktionalität für die Klasse zu implementieren. Der Code sollte wie folgt aussehen:

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

1. Um die statische Bibliothek zu erstellen, **wählen** > Sie**Build-Lösung** in der Menüleiste erstellen aus. Der Build erstellt eine statische Bibliothek, *MathLibrary.lib*, die von anderen Programmen verwendet werden kann.

   > [!NOTE]
   > Beim Erstellen über die Befehlszeile von Visual Studio müssen Sie das Programm in zwei Schritten erstellen. Führen Sie `cl /c /EHsc MathLibrary.cpp` zunächst aus, um den Code zu kompilieren und eine Objektdatei mit dem Namen *MathLibrary.obj*zu erstellen. (Der `cl` Befehl ruft den Compiler Cl.exe `/c` auf, und die Option gibt Kompilierung ohne Verknüpfung an. Weitere Informationen finden Sie unter [/c (Kompilieren ohne Verknüpfung)](../build/reference/c-compile-without-linking.md).) Führen Sie `lib MathLibrary.obj` zweitens aus, um den Code zu verknüpfen und die statische Bibliothek *MathLibrary.lib*zu erstellen. (Mit dem `lib` Befehl wird der Bibliotheks-Manager, "Lib.exe", aufgerufen. Weitere Informationen finden Sie unter [LIB Reference](../build/reference/lib-reference.md).)

## <a name="create-a-c-console-app-that-references-the-static-library"></a><a name="CreateAppToRefTheLib"></a>Erstellen einer C++-Konsolen-App, die auf die statische Bibliothek verweist

::: moniker range="vs-2019"

### <a name="to-create-a-c-console-app-that-references-the-static-library-in-visual-studio-2019"></a>So erstellen Sie eine C++-Konsolen-App, die auf die statische Bibliothek in Visual Studio 2019 verweist

1. Klicken Sie im **Projektmappen-Explorer**mit der rechten Maustaste auf den obersten **Knoten, Solution 'StaticMath',** um das Kontextmenü zu öffnen. Wählen Sie**Neues Projekt** **hinzufügen** > aus, um das Dialogfeld **Neues Projekt hinzufügen** zu öffnen.

1. Legen Sie oben im Dialogfeld den **Projekttypfilter** auf **Konsole**fest.

1. Wählen Sie aus der gefilterten Projekttypliste **Konsolen-App** aus, und klicken Sie auf **Weiter**. Geben Sie auf der nächsten Seite *MathClient* in das Feld **Name** ein, um einen Namen für das Projekt anzugeben.

1. Klicken Sie auf die Schaltfläche **Erstellen**, um das Clientprojekt zu erstellen.

1. Nach dem Erstellen einer Konsolenanwendung wird ein leeres Programm für Sie erstellt. Die Quelldatei erhält denselben Namen, den Sie zuvor ausgewählt haben. Im Beispiel heißt es `MathClient.cpp`.

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-c-console-app-that-references-the-static-library-in-visual-studio-2017"></a>So erstellen Sie eine C++-Konsolen-App, die auf die statische Bibliothek in Visual Studio 2017 verweist

1. Klicken Sie im **Projektmappen-Explorer**mit der rechten Maustaste auf den obersten **Knoten, Solution 'StaticMath',** um das Kontextmenü zu öffnen. Wählen Sie**Neues Projekt** **hinzufügen** > aus, um das Dialogfeld **Neues Projekt hinzufügen** zu öffnen.

1. Wählen Sie im Dialogfeld **Neues Projekt hinzufügen** die Option **Installiertes** > **Visual C++** > **Windows Desktop**aus. Wählen Sie im mittleren Bereich **Windows-Desktop-Assistent** aus.

1. Geben Sie im Feld **Name** einen Namen für das Projekt an, z. B. *MathClient.* Klicken Sie auf die Schaltfläche **OK** .

1. Wählen Sie im Dialogfeld **Windows Desktop Project** unter **Anwendungstyp**die Option **Konsolenanwendung (.exe)** aus.

1. Deaktivieren Sie unter **Zusätzliche Optionen**das Kontrollkästchen **Vorkompilierte Kopfzeile,** wenn diese option.

1. Wählen Sie **OK,** um das Projekt zu erstellen.

1. Nach dem Erstellen einer Konsolenanwendung wird ein leeres Programm für Sie erstellt. Die Quelldatei erhält denselben Namen, den Sie zuvor ausgewählt haben. Im Beispiel heißt es `MathClient.cpp`.

::: moniker-end

::: moniker range="vs-2015"

### <a name="to-create-a-c-console-app-that-references-the-static-library-in-visual-studio-2015"></a>So erstellen Sie eine C++-Konsolen-App, die auf die statische Bibliothek in Visual Studio 2015 verweist

1. Klicken Sie im **Projektmappen-Explorer**mit der rechten Maustaste auf den obersten **Knoten, Solution 'StaticMath',** um das Kontextmenü zu öffnen. Wählen Sie**Neues Projekt** **hinzufügen** > aus, um das Dialogfeld **Neues Projekt hinzufügen** zu öffnen.

1. Wählen Sie im Dialogfeld **Neues Projekt hinzufügen** die Option **Installiertes** > **visuelles C++** > **Win32**aus. Wählen Sie im mittleren Bereich **Win32-Konsolenanwendung**aus.

1. Geben Sie im Feld **Name** einen Namen für das Projekt an, z. B. *MathClient.* Klicken Sie auf die Schaltfläche **OK** .

1. Wählen Sie im Dialogfeld **Win32 Application Wizard** die Option **Weiter**aus.

1. Stellen Sie auf der Seite **Anwendungseinstellungen** unter **Anwendungstyp**sicher, dass die **Konsolenanwendung** ausgewählt ist. Unter **Zusätzliche Optionen**deaktivieren Sie die Option **Vorkompilierte Kopfzeile**, und aktivieren Sie dann das Kontrollkästchen **Leeres Projekt.** Wählen Sie **Fertig stellen** aus, um das Projekt zu erstellen.

1. Um dem leeren Projekt eine Quelldatei hinzuzufügen, klicken Sie mit der rechten Maustaste, um das Kontextmenü für das **MathClient-Projekt** im **Projektmappen-Explorer**zu öffnen, und wählen Sie dann **Neues Element** **hinzufügen** > aus.

1. Wählen Sie im Dialogfeld **Neues Element hinzufügen** die Option Visual **C++** > **Code**aus. Wählen Sie im mittleren Bereich die Option **C++-Datei (.cpp)**. Geben Sie einen Namen für die Quelldatei an, z. *B. MathClient.cpp,* und wählen Sie dann die Schaltfläche **Hinzufügen** aus. Eine leere Quelldatei wird angezeigt.

::: moniker-end

## <a name="use-the-functionality-from-the-static-library-in-the-app"></a><a name="UseLibInApp"></a>Verwenden der Funktionalität aus der statischen Bibliothek in der App

### <a name="to-use-the-functionality-from-the-static-library-in-the-app"></a>So verwenden Sie die Funktionalität der statischen Bibliothek in der App

1. Bevor Sie die mathematischen Routinen verwenden können, müssen Sie auf die erstellte statische Bibliothek verweisen. Öffnen Sie das Kontextmenü für das **MathClient-Projekt** im **Projektmappen-Explorer**, und wählen Sie dann**Referenz** **hinzufügen** > aus.

1. Im Dialogfeld **Verweis hinzufügen** werden Bibliotheken aufgeführt, auf die Sie verweisen können. Auf der Registerkarte **Projekte** werden die Projekte in der aktuellen Projektmappe und alle Bibliotheken, auf die sie verweisen, aufgelistet. Öffnen Sie die Registerkarte **Projekte,** aktivieren Sie das Kontrollkästchen **MathLibrary,** und wählen Sie dann die Schaltfläche **OK** aus.

1. Um auf `MathLibrary.h` die Headerdatei zu verweisen, müssen Sie den Pfad der eingeschlossenen Verzeichnisse ändern. Klicken Sie im **Projektmappen-Explorer**mit der rechten Maustaste auf **MathClient,** um das Kontextmenü zu öffnen. Wählen Sie **Eigenschaften** aus, um das Dialogfeld **MathClient-Eigenschaftenseiten** zu öffnen.

1. Legen Sie im Dialogfeld **MathClient-Eigenschaftenseiten** die Dropdown-Liste **Konfiguration** auf **Alle Konfigurationen**fest. Legendenstellen **der Plattform** auf **Alle Plattformen**.

1. Wählen Sie die **Eigenschaftenseite "Konfigurationseigenschaften** > **C/C++** > **Allgemeine"** aus. Geben Sie in der Eigenschaft **Zusätzliche Include-Verzeichnisse** den Pfad des **MathLibrary-Verzeichnisses** an, oder suchen Sie danach.

   So suchen Sie nach dem Verzeichnispfad:

   1. Öffnen Sie die Dropdownliste der **Eigenschaftswert für zusätzliche Include-Verzeichnisse,** und wählen Sie dann **Bearbeiten**aus.

   1. Doppelklicken Sie im Dialogfeld **Zusätzliche Stellverzeichnisse** oben im Textfeld. Wählen Sie dann die Auslassungstaste (**...**) am Ende der Zeile aus.

   1. Navigieren Sie im Dialogfeld **Verzeichnis auswählen** auf einer Ebene nach oben, und wählen Sie dann das **Verzeichnis MathLibrary** aus. Wählen Sie dann die Schaltfläche **Ordner auswählen** aus, um Ihre Auswahl zu speichern.

   1. Wählen Sie im Dialogfeld **Zusätzliche Stellverzeichnisse** die Schaltfläche **OK** aus.

   1. Wählen Sie im Dialogfeld **Eigenschaftenseiten** die Schaltfläche **OK** aus, um Ihre Änderungen am Projekt zu speichern.

1. Sie können nun `Arithmetic` die Klasse in `#include "MathLibrary.h"` dieser App verwenden, indem Sie den Header in Ihren Code einbeziehen. Ersetzen Sie `MathClient.cpp` den Inhalt von durch diesen Code:

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

1. Um die ausführbare Datei zu erstellen, **wählen** > Sie**Build-Lösung** in der Menüleiste erstellen aus.

## <a name="run-the-app"></a><a name="RunApp"></a>Ausführen der App

### <a name="to-run-the-app"></a>So führen Sie die App aus

1. Stellen Sie sicher, dass **MathClient** als Standardprojekt ausgewählt ist. Um es auszuwählen, klicken Sie mit der rechten Maustaste, um das Kontextmenü für **MathClient** im **Projektmappen-Explorer**zu öffnen, und wählen Sie dann **Als Startup-Projekt festlegen**aus.

1. Um das Projekt auszuführen, wählen Sie in der Menüleiste **Debugstart** > **ohne Debuggen**aus. Die Ausgabe sollte wie folgt aussehen:

    ```Output
    a + b = 106.4
    a - b = -91.6
    a * b = 732.6
    a / b = 0.0747475
    ```

## <a name="see-also"></a>Siehe auch

[Exemplarische Vorgehensweise: Erstellen und Verwenden einer dynamischen Verknüpfungsbibliothek (C++)](../build/walkthrough-creating-and-using-a-dynamic-link-library-cpp.md)<br/>
[Desktopanwendungen (Visual C++)](../windows/desktop-applications-visual-cpp.md)<br/>
