---
title: 'Exemplarische Vorgehensweise: Arbeiten mit Projekten und Lösungen (C++)'
ms.date: 05/14/2019
helpviewer_keywords:
- solutions [C++]
- projects [C++], about projects
- projects [C++]
- solutions [C++], about solutions
ms.assetid: 93a3f290-e294-46e3-876e-e3084d9ae833
ms.openlocfilehash: 36c64a74310c72df38021aebd8abb3ee430da3f0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375899"
---
# <a name="walkthrough-working-with-projects-and-solutions-c"></a>Exemplarische Vorgehensweise: Arbeiten mit Projekten und Lösungen (C++)

In diesem Abschnitt lesen Sie, wie Sie ein C++-Projekt in Visual Studio erstellen, Code hinzufügen und dann das Projekt erstellen und ausführen. Bei dem Projekt in dieser exemplarischen Vorgehensweise handelt es sich um ein Programm, das nachverfolgt, wie viele Spieler verschiedene Kartenspiele spielen.

In Visual Studio wird die Arbeit in Projekten und Projektmappen organisiert. Eine Projektmappe kann mehrere Projekte aufweisen, z.B. eine DLL und eine ausführbare Datei, die auf diese DLL verweist. Weitere Informationen finden Sie unter [Projektmappen und Projekte](/visualstudio/ide/solutions-and-projects-in-visual-studio).

## <a name="before-you-start"></a>Vorbereitung

Sie benötigen mindestens Visual Studio 2017, um diese exemplarische Vorgehensweise abschließen zu können. Wenn Sie eine Kopie benötigen, finden Sie eine kurze Anleitung unter [Installieren der C++-Unterstützung in Visual Studio](../build/vscpp-step-0-installation.md). Wenn Sie dies noch nicht durchgeführt haben, befolgen Sie nach der Installation die nächsten Schritte im Tutorial „Hallo Welt“, um sicherzustellen, dass die C++-Komponenten ordnungsgemäß installiert wurden und alles funktioniert.

Es ist hilfreich, die Grundlagen von C++ zu verstehen und zu wissen, wofür der Compiler, der Linker und der Debugger verwendet werden. Im Tutorial wird ebenfalls davon ausgegangen, dass Sie mit Windows vertraut sind und wissen, wie Sie z.B. Menüs und Dialogfelder verwenden.

## <a name="create-a-project"></a>Erstellen eines Projekts

Um ein Projekt zu erstellen, wählen Sie zunächst eine Projekttypvorlage. Für jeden Projekttyp legt Visual Studio Compilereinstellungen fest und generiert abhängig vom Typ Startcode, den Sie später ändern können. Die folgenden Schritte variieren leicht, je nachdem, welche Version von Visual Studio Sie verwenden. Verwenden Sie das Versionsauswahlsteuerelement, um die **Version** Dokumentation für Ihre bevorzugte Version von Visual Studio anzuzeigen. Es befindet sich oben im Inhaltsverzeichnis auf dieser Seite.

::: moniker range="vs-2019"

### <a name="to-create-a-project-in-visual-studio-2019"></a>Erstellen eines Projekts in Visual Studio 2019

1. Klicken Sie im Hauptmenü auf **Datei** > **Neu** > **Projekt**, um das Dialogfeld **Neues Projekt erstellen** zu öffnen.

1. Legen Sie oben im Dialogfeld die **Sprache** auf **C++**, die **Plattform** auf **Windows** und den **Projekttyp** auf **Konsole** fest.

1. Wählen Sie aus der gefilterten Projekttypliste **Konsolen-App** aus, und klicken Sie auf **Weiter**. Geben Sie auf der nächsten Seite *Game* als Name für das Projekt ein.

   Sie können den Standardspeicherort in der Dropdownliste **Speicherort** akzeptieren, einen anderen Speicherort eingeben oder über die Schaltfläche **Durchsuchen** das Verzeichnis auswählen, in dem Sie das Projekt speichern möchten.

   Beim Erstellen eines Projekts wird das Projekt von Visual Studio in eine Projektmappe eingefügt. Standardmäßig weist die Lösung den gleichen Namen wie das Projekt auf. Sie können den Namen im Feld **Projektmappenname** ändern. Behalten Sie für dieses Beispiel jedoch den Standardnamen bei.

1. Klicken Sie auf die Schaltfläche **Erstellen**, um das Projekt zu erstellen.

   Visual Studio erstellt Ihre neue Projektmappe und die Projektdateien und öffnet den Editor für die Quellcodedatei „Game.cpp“, die generiert wurde.

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-project-in-visual-studio-2017"></a>Erstellen eines Projekts in Visual Studio 2017

1. Wählen Sie in der Menüleiste **Datei** > **Neu** > **Projekt** aus.

1. Erweitern Sie **Installiert** im linken Bereich des Dialogfeld **Neues Projekt**, und wählen Sie **Visual C++** aus, wenn dies nicht bereits geöffnet ist.

1. Wählen Sie aus der Liste der installierten Vorlagen im mittleren Bereich **Windows-Konsolenanwendung** aus.

1. Geben Sie im Feld **Name** einen Namen für das Projekt ein. Geben Sie für dieses Beispiel *Game* ein.

   Sie können den Standardspeicherort in der Dropdownliste **Speicherort** akzeptieren, einen anderen Speicherort eingeben oder über die Schaltfläche **Durchsuchen** das Verzeichnis auswählen, in dem Sie das Projekt speichern möchten.

   Beim Erstellen eines Projekts wird das Projekt von Visual Studio in eine Projektmappe eingefügt. Standardmäßig weist die Lösung den gleichen Namen wie das Projekt auf. Sie können den Namen im Feld **Projektmappenname** ändern. Behalten Sie für dieses Beispiel jedoch den Standardnamen bei.

1. Wählen Sie die Schaltfläche **OK** aus, um das Projekt zu erstellen.

   Visual Studio erstellt Ihre neue Projektmappe und die Projektdateien und öffnet den Editor für die Quellcodedatei „Game.cpp“, die generiert wurde.

::: moniker-end

::: moniker range="vs-2015"

### <a name="to-create-a-project-in-visual-studio-2015"></a>Erstellen eines Projekts in Visual Studio 2015

1. Wählen Sie in der Menüleiste **Datei** > **Neu** > **Projekt** aus.

1. Erweitern Sie **Installiert** im linken Bereich des Dialogfeld **Neues Projekt**, und wählen Sie **Visual C++** aus, wenn dies nicht bereits geöffnet ist.

1. Wählen Sie aus der Liste der installierten Vorlagen im mittleren Bereich **Win32-Konsolenanwendung** aus.

1. Geben Sie im Feld **Name** einen Namen für das Projekt ein. Geben Sie für dieses Beispiel *Game* ein.

   Sie können den Standardspeicherort in der Dropdownliste **Speicherort** akzeptieren, einen anderen Speicherort eingeben oder über die Schaltfläche **Durchsuchen** das Verzeichnis auswählen, in dem Sie das Projekt speichern möchten.

   Beim Erstellen eines Projekts wird das Projekt von Visual Studio in eine Projektmappe eingefügt. Standardmäßig weist die Lösung den gleichen Namen wie das Projekt auf. Sie können den Namen im Feld **Projektmappenname** ändern. Behalten Sie für dieses Beispiel jedoch den Standardnamen bei.

1. Wählen Sie die Schaltfläche **OK** aus, um das Projekt zu erstellen.

   Visual Studio erstellt Ihre neue Projektmappe und die Projektdateien und öffnet den Editor für die Quellcodedatei „Game.cpp“, die generiert wurde.

::: moniker-end

## <a name="organize-projects-and-files"></a>Organisieren von Projekten und Dateien

Sie können den **Projektmappen-Explorer** verwenden, um Projekte, Dateien und andere Ressourcen in der Projektmappe zu organisieren und zu verwalten.

In diesem Teil der exemplarischen Vorgehensweise wird gezeigt, wie dem Projekt eine Klasse hinzugefügt wird. Wenn Sie die Klasse hinzufügen, fügt Visual Studio die entsprechenden H- und CPP-Dateien hinzu. Die Ergebnisse werden im **Projektmappen-Explorer** angezeigt.

### <a name="to-add-a-class-to-a-project"></a>So fügen Sie einem Projekt eine Klasse hinzu

1. Wenn das Fenster **Projektmappen-Explorer** nicht in Visual Studio angezeigt wird, klicken Sie in der Menüleiste auf **Ansicht** > **Projektmappen-Explorer**.

1. Wählen Sie im **Projektmappen-Explorer** das Projekt **Game** aus. Wählen Sie in der Menüleiste > **Projekt-Klasse hinzufügen**aus. **Project**

1. Geben Sie im Dialogfeld **Klasse hinzufügen***Cardgame* in das Feld **Klassenname** ein. Ändern Sie die Standarddateinamen und - einstellungen nicht. Klicken Sie auf die Schaltfläche **OK** .

   Visual Studio erstellt neue Dateien und fügt diese zum Projekt hinzu. Diese werden im Fenster **Projektmappen-Explorer** angezeigt. Die Dateien „Cardgame.h“ und „Cardgame.cpp“ werden im Editor geöffnet.

1. Bearbeiten Sie die Datei „Cardgame.h“, und nehmen Sie folgende Änderungen vor:

   - Fügen Sie hinter der öffnenden geschweiften Klammer der Klassendefinition zwei private Datenmember hinzu.
     <!--      [!code-cpp[NVC_Walkthrough_Working_With_Projects#100](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_1.h)] -->

      ```cpp
      int players;
      static int totalParticipants;
      ```

   - Ändern Sie den Standardkonstruktor, der von Visual Studio generiert wurde. Suchen Sie nach dem `public:`-Zugriffsspezifizierer nach der Zeile, die folgendermaßen aussieht:

      `Cardgame();`

      Ändern Sie den Konstruktor so, dass er einen Parameter des Typs `int` namens *players* annimmt.

      <!--[!code-cpp[NVC_Walkthrough_Working_With_Projects#101](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_2.h)]-->
      `Cardgame(int players);`

   - Fügen Sie nach dem Standarddestruktor eine Inline-Deklaration für eine `static int`-Memberfunktion namens *GetParticipants* hinzu, die keine Parameter übernimmt und den Wert `totalParticipants` zurückgibt.

      <!--[!code-cpp[NVC_Walkthrough_Working_With_Projects#102](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_3.h)]-->
      `static int GetParticipants() { return totalParticipants; }`

   Die Datei „Cardgame.h“ sieht nach der Änderung ungefähr wie der folgende Code aus:

   <!--[!code-cpp[NVC_Walkthrough_Working_With_Projects#103](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_4.h)]-->

    ```cpp
    #pragma once
    class Cardgame
    {
        int players;
        static int totalParticipants;
    public:
        Cardgame(int players);
        ~Cardgame();
        static int GetParticipants() { return totalParticipants; }
    };
    ```

   Die Zeile `#pragma once` teilt dem Compiler mit, die Headerdatei nur einmal aufzunehmen. Weitere Informationen finden Sie unter [once](../preprocessor/once.md). Informationen zu weiteren C++-Schlüsselwörtern in der oben gezeigten Headerdatei finden Sie unter [class](../cpp/class-cpp.md), [int](../cpp/fundamental-types-cpp.md), [static](../cpp/storage-classes-cpp.md) und [public](../cpp/public-cpp.md).

1. Klicken Sie oben im Bearbeitungsbereich auf die Registerkarte **Cardgame.cpp**, um die Datei zum Bearbeiten zu öffnen.

1. Löschen Sie den gesamten Inhalt der Datei, und ersetzen Sie ihn durch den folgenden Code:

   <!--[!code-cpp[NVC_Walkthrough_Working_With_Projects#111](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_5.cpp)]-->

    ```cpp
    #include "pch.h" // remove this line in Visual Studio 2019
    #include "Cardgame.h"
    #include <iostream>

    using namespace std;

    int Cardgame::totalParticipants = 0;

    Cardgame::Cardgame(int players)
        : players(players)
    {
        totalParticipants += players;
        cout << players << " players have started a new game.  There are now "
             << totalParticipants << " players in total." << endl;
    }

    Cardgame::~Cardgame()
    {
    }
    ```

   > [!NOTE]
   > Sie können bei der Codeeingabe die automatische Vervollständigung verwenden. Wenn Sie diesen Code beispielsweise über die Tastatur eingeben, können Sie *pl* oder *tot* eingeben und **STRG**+**LEERTASTE** drücken. Die automatische Vervollständigung gibt `players` oder `totalParticipants` für Sie ein.

## <a name="add-test-code-to-your-main-function"></a>Hinzufügen von Testcode zur main-Funktion

Fügen Sie Code zu Ihrer App hinzu, der die neuen Funktionen testet.

### <a name="to-add-test-code-to-the-project"></a>Hinzufügen von Testcode zum Projekt

1. Ersetzen Sie im Editor-Fenster **Game.cpp** den vorhandenen Code durch Folgendes:

   <!--[!code-cpp[NVC_Walkthrough_Working_With_Projects#120](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_6.cpp)]-->

    ```cpp
    // Game.cpp : Defines the entry point for the console application.
    //

    #include "pch.h" // remove this line in Visual Studio 2019
    #include "Cardgame.h"
    #include <iostream>

    using namespace std;

    void PlayGames()
    {
        Cardgame bridge(4);
        Cardgame blackjack(8);
        Cardgame solitaire(1);
        Cardgame poker(5);
    }

    int main()
    {
        PlayGames();
        return 0;
    }
    ```

   Der Code fügt eine Testfunktion (`PlayGames`) zum Quellcode hinzu und ruft diese in `main` auf.

## <a name="build-and-run-your-app-project"></a>Erstellen und Ausführen Ihres App-Projekts

Erstellen Sie nun das Projekt, und führen Sie die App aus.

### <a name="to-build-and-run-the-project"></a>So erstellen Sie das Projekt und führen es aus

1. Wählen Sie auf der Menüleiste **Erstellen** > **Projektmappe erstellen** aus.

   Die Ausgabe eines Builds wird im **Ausgabefenster** angezeigt. Wenn der Build erfolgreich erstellt wurde, sollte die Ausgabe in etwa wie folgt aussehen:

    ```Output
    1>------ Build started: Project: Game, Configuration: Debug Win32 ------
    1>pch.cpp
    1>Cardgame.cpp
    1>Game.cpp
    1>Generating Code...
    1>Game.vcxproj -> C:\Users\<username>\source\repos\Game\Debug\Game.exe
    ========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
    ```

   Abhängig von der Buildkonfiguration können im **Ausgabefenster** verschiedene Schritte angezeigt werden. Wenn das Projekt jedoch erfolgreich erstellt wird, sollte die letzte Zeile der angezeigten Ausgabe ähneln.

   Wenn die Erstellung nicht erfolgreich war, vergleichen Sie Ihren Code mit dem Code, der in den Schritten weiter oben gezeigt wurde.

1. Um das Projekt auszuführen, wählen Sie in der Menüleiste **Debugstart** > **ohne Debuggen**aus. Es sollte ein Konsolenfenster angezeigt werden, und die Ausgabe sollte dem folgenden Beispiel ähneln:

    ```Output
    4 players have started a new game.  There are now 4 players in total.
    8 players have started a new game.  There are now 12 players in total.
    1 players have started a new game.  There are now 13 players in total.
    5 players have started a new game.  There are now 18 players in total.
    ```

   Drücken Sie eine Taste, um das Konsolenfenster zu schließen.

Glückwunsch, Sie haben erfolgreich ein App-Projekt und eine Projektmappe erstellt. Fahren Sie mit der exemplarischen Vorgehensweise fort, um mehr über das Erstellen von C++-Codeprojekten in Visual Studio zu erfahren.

## <a name="next-steps"></a>Nächste Schritte

**Zurück:** [Verwenden der Visual Studio-IDE für C++-Desktopentwicklung](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md)<br/>
**Weiter:** [Exemplarische Vorgehensweise: Erstellen eines Projekts (C++)](../ide/walkthrough-building-a-project-cpp.md)

## <a name="see-also"></a>Siehe auch

[C++-Sprachreferenz](../cpp/cpp-language-reference.md)<br/>
[Projekte und Buildsysteme](../build/projects-and-build-systems-cpp.md)<br/>
