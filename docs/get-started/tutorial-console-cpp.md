---
title: Erstellen eines Konsolenrechners in C++
description: Erstellen einer „Hallo Welt“-Konsolen-App und einer Taschenrechner-App in Visual C++
ms.custom: mvc
ms.date: 08/19/2019
ms.topic: tutorial
ms.devlang: cpp
ms.assetid: 45138d70-719d-42dc-90d7-1d0ca31a2f54
ms.openlocfilehash: b292d5b8e1db7415aed6427f2327788e08a28a20
ms.sourcegitcommit: 6b3d793f0ef3bbb7eefaf9f372ba570fdfe61199
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2020
ms.locfileid: "86404449"
---
# <a name="create-a-console-calculator-in-c"></a>Erstellen eines Konsolenrechners in C++

::: moniker range=">=vs-2019"

C++-Programmierer beginnen häufig mit einer „Hallo, Welt!“- Anwendung, die über die Befehlszeile ausgeführt wird. Eine solche Anwendung erstellen Sie mithilfe dieses Artikels in Visual Studio. Anschließend beschäftigen Sie sich mit einer etwas schwierigeren Aufgabe: der Erstellung einer Taschenrechner-App.

## <a name="prerequisites"></a>Voraussetzungen

- Visual Studio mit der Workload **Desktopentwicklung mit C++** muss auf Ihrem Computer installiert sein und ausgeführt werden. Ist dies noch nicht der Fall, finden Sie unter [Install C++ support in Visual Studio (Installieren von C++-Komponenten in Visual Studio)](../build/vscpp-step-0-installation.md) weitere Informationen.

## <a name="create-your-app-project"></a>Erstellen Ihres App-Projekts

Visual Studio verwendet *Projekte*, um Code für eine App zu ordnen, und *Projektmappen*, um Ihre Projekte zu ordnen. Ein Projekt beinhaltet alle Optionen, Einstellungen und Regeln, die Sie zum Erstellen Ihrer Anwendung verwendet haben. Es verwaltet auch die Beziehungen zwischen allen Projektdateien und externen Dateien. Wenn Sie Ihre App erstellen möchten, müssen Sie zuerst ein neues Projekt und eine Projektmappe erstellen.

1. Wenn Sie Visual Studio starten, wird das Dialogfeld für Visual Studio 2019 angezeigt. Klicken Sie auf **Neues Projekt erstellen**, um zu beginnen.

   ![Startdialogfeld von Visual Studio 2019](./media/calc-vs2019-initial-dialog.png "Startdialogfeld von Visual Studio 2019")

   Alternativ können Sie auch in der Menüleiste in Visual Studio **Datei** > **Neu** > **Projekt** aufrufen. Dadurch wird das Fenster **Neues Projekt erstellen** geöffnet.

1. Wählen Sie in der Liste der Projektvorlagen **Konsolen-App** aus, und klicken Sie anschließend auf **Weiter**.

   ![Auswählen der Vorlage für die Konsolen-App](./media/calc-vs2019-choose-console-app.png "Auswählen der Vorlage für die Konsolen-App")

   > [!Important]
   > Wählen Sie die C++-Version der Vorlage **Konsolen-App** aus. Diese erkennen Sie an den Tags **C++** , **Windows** und **Konsole**, und das Symbol enthält „++“ in der Ecke.

1. Klicken Sie im Dialogfeld **Neues Projekt konfigurieren** in das Feld **Projektname**, und geben Sie dort den Namen *CalculatorTutorial* für das neue Projekt ein. Klicken Sie anschließend auf **Erstellen**.

   ![Benennen Ihres Projekts im Dialogfeld „Neues Projekt konfigurieren“](./media/calc-vs2019-name-your-project.png "Benennen Ihres Projekts im Dialogfeld „Neues Projekt konfigurieren“")

   Eine leere C++-Windows-Konsolenanwendung wird erstellt. Konsolenanwendungen verwenden ein Windows-Konsolenfenster, um Ausgabe anzuzeigen und Benutzereingaben entgegenzunehmen. In Visual Studio wird ein Editorfenster geöffnet und der generierte Code angezeigt:

    ```cpp
    // CalculatorTutorial.cpp : This file contains the 'main' function. Program execution begins and ends there.
    //

    #include <iostream>

    int main()
    {
        std::cout << "Hello World!\n";
    }

    // Run program: Ctrl + F5 or Debug > Start Without Debugging menu
    // Debug program: F5 or Debug > Start Debugging menu

    // Tips for Getting Started:
    //   1. Use the Solution Explorer window to add/manage files
    //   2. Use the Team Explorer window to connect to source control
    //   3. Use the Output window to see build output and other messages
    //   4. Use the Error List window to view errors
    //   5. Go to Project > Add New Item to create new code files, or Project > Add Existing Item to add existing code files to the project
    //   6. In the future, to open this project again, go to File > Open > Project and select the .sln file
    ```

## <a name="verify-that-your-new-app-builds-and-runs"></a>Überprüfen, dass Ihre neue App erstellt und ausgeführt wird

Die Vorlage für eine neue Windows-Konsolenanwendung erstellt eine einfache „Hallo Welt“-App in C++. An diesem Punkt können Sie sehen, wie die Apps, die Sie direkt in der IDE erstellen, in Visual Studio erstellt und ausgeführt werden.

1. Wählen Sie zum Erstellen Ihres Projekts aus dem Menü **Erstellen** die Option **Projektmappe erstellen** aus. Im Fenster **Ausgabe** wird das Ergebnis des Erstellungsprozess angezeigt.

   ![Erstellen des Projekts](./media/calc-vs2019-build-your-project.png "Erstellen des Projekts")

1. Klicken Sie zum Ausführen des Codes auf der Menüleiste auf **Debuggen** > **Ohne Debuggen starten**.

   ![Starten des Projekts](./media/calc-vs2019-hello-world-console.png "Starten des Projekts")

   Ein Konsolenfenster wird geöffnet, und Ihre App daraufhin ausgeführt. Wenn Sie eine Konsolen-App in Visual Studio starten, führt diese Ihren Code aus und gibt dann „Press any key to close this window.“ (Drücken Sie eine beliebige Taste, um dieses Fenster zu schließen.) aus. . .“ (Beliebige Taste zum Fortfahren drücken) zurück, damit Sie sich die Ausgabe ansehen können. Herzlichen Glückwunsch! Sie haben Ihre erste „Hallo, Welt!“- Konsolen-App in Visual Studio erstellt!

1. Drücken Sie eine Taste, um das Konsolenfenster zu schließen, und kehren Sie zu Visual Studio zurück.

Sie haben nun die Tools, um Ihre App nach jeder Änderung zu erstellen und auszuführen, um zu überprüfen, ob der Code noch so funktioniert, wie Sie es erwarten. Später erhalten Sie Informationen zum Debuggen, wenn Ihr Code nicht funktioniert.

## <a name="edit-the-code"></a>Bearbeiten des Codes

Wandeln Sie den Code in dieser Vorlage nun in eine Rechner-App um.

1. Bearbeiten Sie in der Datei *CalculatorTutorial.cpp* den Code, sodass dieser dem folgenden Beispiel entspricht:

    ```cpp
    // CalculatorTutorial.cpp : This file contains the 'main' function. Program execution begins and ends there.
    //

    #include <iostream>

    using namespace std;

    int main()
    {
        cout << "Calculator Console Application" << endl << endl;
        cout << "Please enter the operation to perform. Format: a+b | a-b | a*b | a/b"
            << endl;
        return 0;
    }

    // Run program: Ctrl + F5 or Debug > Start Without Debugging menu
    // Debug program: F5 or Debug > Start Debugging menu
    // Tips for Getting Started:
    //   1. Use the Solution Explorer window to add/manage files
    //   2. Use the Team Explorer window to connect to source control
    //   3. Use the Output window to see build output and other messages
    //   4. Use the Error List window to view errors
    //   5. Go to Project > Add New Item to create new code files, or Project > Add Existing Item to add existing code files to the project
    //   6. In the future, to open this project again, go to File > Open > Project and select the .sln file
    ```

   > Grundlegendes zum Code:
   >
   > - Die `#include`-Anweisungen ermöglichen es Ihnen, auf Code zu verweisen, der sich in anderen Dateien befindet. Manchmal kommt es vor, dass Sie einen Dateinamen sehen, der von spitzen Klammern ( **\<\>** ) eingeschlossen wird, manchmal wird er von Anführungszeichen ( **" "** ) eingeschlossen. Generell werden spitze Klammern verwendet, wenn auf die C++-Standardbibliothek verwiesen wird, während Anführungszeichen für andere Dateien verwendet werden.
   > - Die `using namespace std;`-Zeile sagt dem Compiler, dass dieser Inhalt aus der C++-Standardbibliothek zu erwarten hat, der in dieser Datei verwendet werden soll. Ohne diese Zeile müsste vor jedem Stichwort aus der Bibliothek `std::` stehen, um dessen Bereich anzuzeigen. Ohne diese Zeile müsste beispielsweise jeder Verweis auf `cout` als `std::cout` geschrieben werden. Die `using`-Anweisung wird hinzugefügt, um den Code übersichtlicher zu gestalten.
   > - Das Schlüsselwort `cout` wird verwendet, damit die Standardausgabe in C++ erfolgt. Der Operator **\<\<** sagt dem Compiler, dass dieser alles, was rechts von ihm steht, an die Standardausgabe senden soll.
   > - Das Schlüsselwort **endl** ist ähnlich wie die Eingabetaste. Es beendet die Zeile und lässt den Cursor in die nächste Zeile springen. Es hat sich aber noch mehr bewährt, innerhalb der Zeichenfolge mit demselben Effekt ein `\n`-Zeichen zu setzen (eingeschlossen von ""), da `endl` den Puffer immer leert und der Leistung des Programms schaden kann. Da es sich hier aber um eine kleine App handelt, wird stattdessen aus Gründen der besseren Lesbarkeit `endl` verwendet.
   > - Alle C++-Anweisungen müssen mit einem Semikolon enden, und alle C++-Anwendungen müssen eine `main()`-Funktion enthalten. Diese Funktion wird vom Programm zuerst ausgeführt. Die Funktion `main()` muss auf den ganzen Code zugreifen können, damit dieser verwendet werden kann.

1. Wenn Sie die Datei speichern möchten, drücken Sie **STRG+S**, oder klicken Sie im oberen Bereich der IDE auf das **Speichern**-Symbol: das Diskettensymbol in der Symbolleiste unterhalb der Menüleiste.

1. Drücken Sie **STRG+F5**, um die Anwendung auszuführen, oder wechseln Sie zum **Debuggen**-Menü, und wählen Sie dort **Ohne Debuggen starten** aus. Es sollte nun ein Konsolenfenster mit dem im Code angegebenen Text angezeigt werden.

1. Schließen Sie das Konsolenfenster, sobald Sie fertig sind.

## <a name="add-code-to-do-some-math"></a>Hinzufügen von Code für Berechnungen

Jetzt können Sie mathematische Logik hinzufügen.

### <a name="to-add-a-calculator-class"></a>Hinzufügen einer Rechnerklasse

1. Wechseln Sie zum Menü **Projekt**, und wählen Sie **Klasse hinzufügen** aus. Geben Sie im Eingabefeld für **Klassenname** den Namen *Calculator* (Taschenrechner) ein. Klicken Sie auf **OK**. Zwei neue Dateien werden Ihrem Projekt hinzugefügt. Um alle geänderten Dateien auf einmal zu speichern, drücken Sie **STRG+UMSCHALT+S**. Dies ist die Tastenkombination für **Datei** > **Alle speichern**. Es gibt auch eine Symbolleistenschaltfläche für **Alle speichern**: ein Symbol mit zwei Disketten. Diese Schaltfläche befindet sich neben der Schaltfläche **Speichern**. Generell hat es sich bewährt, **Alle speichern** häufig auszuführen, damit auch wirklich alle Dateien gespeichert werden.

   ![Erstellen der Calculator-Klasse](./media/calc-vs2019-create-calculator-class.png "Erstellen der Calculator-Klasse")

   Eine Klasse ist wie ein Entwurf für ein Objekt, das etwas tut. In diesem Fall soll ein Rechner und dessen Funktionsweise definiert werden. Der Assistent **Klasse hinzufügen**, den Sie oben verwendet haben, hat .h- und .cpp-Dateien erstellt, die denselben Namen wie die Klasse haben. Im am Rand der IDE angezeigten Fenster **Projektmappen-Explorer** können Sie sich eine vollständige Liste Ihrer Projektdateien ansehen. Wenn das Fenster nicht angezeigt wird, können Sie es über die Menüleiste öffnen: Klicken Sie auf **Ansicht** > **Projektmappen-Explorer**.

   ![Projektmappen-Explorer](./media/calc-vs2019-solution-explorer.png "Projektmappen-Explorer")

   Sie sollten in Editor nun drei Registerkarten geöffnet haben: *CalculatorTutorial.cpp*, *Calculator.h* und *Calculator.cpp*. Wenn Sie eine davon versehentlich schließen, können Sie sie im **Projektmappen-Explorer**-Fenster jeweils mit einem Doppelklick auf die Datei wieder öffnen.

1. Entfernen Sie in **Calculator.h** die Zeilen `Calculator();` und `~Calculator();`, die erstellt wurden, jedoch nicht benötigt werden. Fügen Sie dann die folgende Codezeile hinzu, sodass die Datei nun folgendermaßen aussieht:

    ```cpp
    #pragma once
    class Calculator
    {
    public:
        double Calculate(double x, char oper, double y);
    };
    ```

   > Grundlegendes zum Code
   >
   > - Die Zeile, die Sie hinzugefügt haben, deklariert eine neue Funktion namens `Calculate`, die Sie verwenden, um mathematische Operationen für Addition, Subtraktion, Multiplikation und Division auszuführen.
   > - C++-Code ist unterteilt in *Headerdateien* (.h) und *Quelldateien* (.cpp). Von verschiedenen Compilern werden auch noch andere Dateierweiterungen unterstützt; die eben vorgestellten sind aber die wichtigsten, die Sie kennen sollten. Funktionen und Variablen werden normalerweise *deklariert*, d. h. ihnen wird in den Headerdateien ein Name und ein Typ zugeordnet, und *implementiert*, d. h. ihnen wird in den Quelldateien eine Definition zugeordnet. Um auf in einer anderen Datei definierten Code zuzugreifen, können Sie `#include "filename.h"` verwenden. Dabei ist „filename.h“ der Name der Datei, die die Variablen und Funktionen deklariert, die Sie verwenden möchten.
   > - Die zwei Zeilen, die Sie gelöscht haben, haben einen *Konstruktor* und einen *Destruktor* für die Klasse deklariert. Für eine einfache Klasse wie die vorliegende werden diese vom Compiler für Sie erstellt. Deren Verwendung liegt aber außerhalb des in diesem Tutorial abgedeckten Bereichs.
   > - Es hat sich bewährt, Ihren Code auf Grundlage der jeweiligen Funktion in verschiedenen Dateien zu organisieren. Dies erleichtert das spätere Auffinden des benötigen Codes. Hier definieren Sie die `Calculator`-Klasse und die Datei, die die `main()`-Funktion enthält, einzeln. Es soll aber dennoch in `main()` auf die `Calculator`-Klasse verwiesen werden.

1. Unter `Calculate` wird eine grüne Wellenlinie angezeigt. Dies liegt daran, dass die `Calculate`-Funktion in der CPP-Datei nicht definiert wurde. Zeigen Sie mit dem Mauszeiger auf das Wort, und klicken Sie auf den angezeigten Schraubendreher und anschließend auf **Create definition of 'Calculate' in Calculator.cpp** (Definition von „Calculate“ in Calculator.cpp erstellen).

   ![Erstellen der Definition von Calculate](./media/calc-vs2019-create-definition.png "Erstellen der Definition von Calculate")

   Ein Popupelement wird angezeigt, das Ihnen eine Vorschau der Codeänderung anzeigt, die in der anderen Datei vorgenommen wurde. Der Code wurde *Calculator.cpp* hinzugefügt.

   ![Popupelement mit Definition von Calculate](./media/calc-vs2019-pop-up-definition.png "Popupelement mit Definition von Calculate")

   Momentan wird nur 0.0 zurückgegeben. Ändern Sie das nun. Drücken Sie **ESC**, um das Popupelement zu schließen.

1. Wechseln Sie zur *Calculator.cpp*-Datei im Editorfenster. Entfernen Sie die Bereiche `Calculator()` und `~Calculator()` (wie in der .h-Datei bereits geschehen), und fügen Sie `Calculate()` den folgenden Code hinzu:

    ```cpp
    #include "Calculator.h"

    double Calculator::Calculate(double x, char oper, double y)
    {
        switch(oper)
        {
            case '+':
                return x + y;
            case '-':
                return x - y;
            case '*':
                return x * y;
            case '/':
                return x / y;
            default:
                return 0.0;
        }
    }
    ```

   > Grundlegendes zum Code
   >
   > - Die Funktion `Calculate` nimmt eine Zahl, einen Operator und eine zweite Zahl, und führt dann die angeforderte Operation mit den angegebenen Zahlen durch.
   > - Die Switch-Anweisung überprüft, welcher Operator bereitgestellt wurde, und führt nur den für diese Operation entsprechenden Fall aus. Der „default:“-Fall ist ein Fallback, falls der Benutzer einen Operator eingibt, der nicht akzeptiert wird, damit das Programm nicht unterbrochen wird. Allgemein wird mit ungültiger Benutzereingabe am besten auf elegantere Weise umgegangen. Dies würde für dieses Tutorial aber zu weit führen.
   > - Das `double`-Schlüsselwort denotiert eine Zahlenart, die Dezimalzahlen unterstützt. Auf diese Weise kann der Rechner sowohl Berechnungen mit Dezimalzahlen als auch mit ganzen Zahlen verarbeiten. Die `Calculate`-Funktion muss aufgrund von `double` ganz am Anfang des Codes (dadurch wird der Rückgabetyp der Funktion angegeben) immer eine solche Zahl zurückgeben. Deshalb wird auch im „default:“-Fall 0.0 zurückgegeben.
   > - Die .h-Datei deklariert die Funktion *prototype*, die dem Compiler bereits vorab sagt, welcher Parameter benötigt wird, und welcher Rückgabetyp zu erwarten ist. In der .cpp-Datei sind alle Implementierungsdetails der Funktion enthalten.

Wenn Sie nun den Code noch einmal erstellen und ausführen, wird er nach der Aufforderung, den gewünschten Vorgang anzugeben, erneut beendet. Bearbeiten Sie als nächsten Schritt die `main`-Funktion, um einige Berechnungen durchzuführen.

### <a name="to-call-the-calculator-class-member-functions"></a>Aufrufen der Memberfunktionen der Rechnerklasse

1. Aktualisieren Sie nun die `main`-Funktion in *CalculatorTutorial.cpp*:

    ```cpp
    // CalculatorTutorial.cpp : This file contains the 'main' function. Program execution begins and ends there.
    //

    #include <iostream>
    #include "Calculator.h"

    using namespace std;

    int main()
    {
        double x = 0.0;
        double y = 0.0;
        double result = 0.0;
        char oper = '+';

        cout << "Calculator Console Application" << endl << endl;
        cout << "Please enter the operation to perform. Format: a+b | a-b | a*b | a/b"
             << endl;

        Calculator c;
        while (true)
        {
            cin >> x >> oper >> y;
            result = c.Calculate(x, oper, y);
            cout << "Result is: " << result << endl;
        }

        return 0;
    }
    ```

   > Grundlegendes zum Code
   >
   > - Da C++-Programme immer bei der `main()`-Funktion starten, müssen Sie den weiteren Code von dort aus aufrufen. Es wird also eine `#include`-Anweisung benötigt.
   > - Einige anfängliche Variablen (`x`, `y`, `oper` und `result`) werden deklariert, um jeweils die erste Zahl, die zweite Zahl, den Operator und das Endergebnis zu speichern. Es empfiehlt sich immer, einige anfängliche Variablen anzugeben, um nicht definiertes Verhalten zu vermeiden. Genau dies ist hier geschehen.
   > - Die `Calculator c;`-Zeile deklariert ein Objekt namens „c“ als Instanz der `Calculator`-Klasse. Die Klasse selbst ist lediglich ein Entwurf dafür, wie der Rechner funktioniert. Das Objekt ist der spezifische Rechner, der die Berechnungen ausführt.
   > - Die `while (true)`-Anweisung ist eine Schleife. Der Code innerhalb der Schleife wird wieder und wieder ausgeführt, so lange, bis die Bedingung innerhalb der `()` erfüllt ist. Da die Bedingung nur als `true` aufgeführt ist, ist sie immer wahr, die Schleife wird also ununterbrochen ausgeführt. Um das Programm zu schließen, muss der Benutzer das Konsolenfenster manuell schließen. Andernfalls wartet das Programm ständig auf eine neue Eingabe.
   > - Das `cin`-Schlüsselwort wird verwendet, um Benutzereingaben anzunehmen. Dieser Eingabestream ist intelligent genug, um eine Textzeile zu verarbeiten, die im Konsolenfenster eingegeben wird, und diese in der richtigen Reihenfolge innerhalb aller aufgeführten Variablen zu platzieren, vorausgesetzt, die Benutzereingabe entspricht den benötigten Spezifikationen. Sie können diese Zeile bearbeiten, sodass verschiedene Eingabearten akzeptiert werden, z. B. mehr als zwei Zahlen. Dafür müsste aber auch die `Calculate()`-Funktion aktualisiert werden.
   > - Der `c.Calculate(x, oper, y);`-Ausdruck ruft die zuvor definierte `Calculate`-Funktion auf und stellt die eingegebenen Eingabewerte zur Verfügung. Die Funktion gibt dann eine Zahl zurück, die in `result` gespeichert wird.
   > - Abschließend wird `result` in der Konsole ausgegeben, sodass der Benutzer das Ergebnis der Berechnung ansehen kann.

### <a name="build-and-test-the-code-again"></a>Erneutes Erstellen und Testen des Codes

Testen Sie das Programm nun erneut, ob auch alles wie vorgesehen funktioniert.

1. Drücken Sie **STRG+F5**, um die App neu zu erstellen und zu starten.

1. Geben Sie `5 + 5` ein, und drücken Sie die **EINGABETASTE**. Überprüfen Sie, ob das Ergebnis 10 ist.

   ![Das Ergebnis von 5 + 5](./media/calc-vs2019-five-plus-five.png "Das Ergebnis von 5 + 5")

## <a name="debug-the-app"></a>Debuggen der App

Da es keine Beschränkungen gibt, was der Benutzer im Konsolenfenster eingeben kann, sorgen Sie nun dafür, dass der Rechner Eingaben wie erwartet verarbeitet. Anstatt das Programm auszuführen, debuggen Sie es, damit Sie sich ansehen können, wie genau das Programm Schritt für Schritt abläuft.

### <a name="to-run-the-app-in-the-debugger"></a>Ausführen der App im Debugger

1. Setzen Sie auf der `result = c.Calculate(x, oper, y);`-Zeile einen Breakpoint, exakt nach dem Punkt, an dem der Benutzer zur Eingabe aufgefordert wurde. Um den Breakpoint festzulegen, klicken Sie auf der linken Seite des Editorfensters neben der Zeile auf den grauen, vertikalen Rand. Ein roter Punkt wird angezeigt.

   ![Festlegen eines Breakpoints](./media/calc-vs2019-set-breakpoint.png "Haltepunkt festlegen")

   Ab sofort wird die Ausführung dann immer bei dieser Zeile angehalten, wenn Sie das Programm debuggen. Wir haben bereits eine grobe Vorstellung, dass das Programm in einfachen Fällen funktioniert. Da wir die Ausführung nicht jedes Mal anhalten möchten, legen wir den Breakpoint als bedingt fest.

1. Klicken Sie mit der rechten Maustaste auf den roten Punkt, der den Breakpoint darstellt, und wählen Sie dann **Bedingungen** aus. Geben Sie im Eingabefeld für die Bedingung `(y == 0) && (oper == '/')` ein. Wenn Sie fertig sind, wählen Sie die Schaltfläche **OK** aus. Die Bedingung wird automatisch gespeichert.

   ![Festlegen eines bedingten Breakpoints](./media/calc-vs2019-conditional-breakpoint.png "Festlegen eines bedingten Breakpoints")

   Die Ausführung wird nun also genau dann am Breakpoint angehalten, wenn versucht wird, durch 0 zu teilen.

1. Drücken Sie **F5**, um das Programm zu debuggen, oder wählen Sie die Schaltfläche **Lokaler Windows-Debugger** mit dem grünen Pfeilsymbol auf der Symbolleiste aus. Wenn Sie in Ihrer Konsolen-App z. B. „5 - 0“ eingeben, verhält sich das Programm normal und wird weiter ausgeführt. Wenn Sie nun jedoch „10 / 0“ eingeben, hält das Programm am Breakpoint an. Auch wenn Sie eine beliebige Anzahl von Leerzeichen zwischen dem Operator und den Zahlen einfügen, ist `cin` intelligent genug, die Eingabe korrekt zu analysieren.

   ![Anhalten am bedingten Breakpoint](./media/calc-vs2019-debug-breakpoint.png "Anhalten am bedingten Breakpoint")

### <a name="useful-windows-in-the-debugger"></a>Nützliche Fenster im Debugger

Sobald Sie Ihren Code debuggen, können Sie feststellen, dass ein paar neue Fenster angezeigt werden. Diese Fenster unterstützen Sie beim Debuggen. Sehen Sie sich das Fenster **Auto** an. Im Fenster **Auto** sehen Sie die aktuellen Werte der Variablen, die mindestens in den letzten drei Zeilen und bis zur aktuellen Zeile verwendet wurden. Wenn Sie alle Variablen dieser Funktion ansehen möchten, wechseln Sie zum Fenster **Lokale**. Tatsächlich können Sie die Werte dieser Variablen während des Debuggens bearbeiten, um zu erfahren, welche Auswirkung sie auf das Programm haben würden. Hier bearbeiten Sie die Variablen jedoch nicht.

   ![Fenster „Lokale Variablen“](./media/calc-vs2019-debug-locals.png "Fenster „Lokale Variablen“")

Sie können auch einfach direkt im Code den Mauszeiger auf Variablen bewegen, um deren aktuelle Werte an den Stellen anzeigen zu lassen, an denen die Ausführung jeweils pausiert wurde. Sorgen Sie dafür, dass sich das Editorfenster im Vordergrund befindet, indem Sie darauf klicken, bevor Sie diesen Vorgang testen.

   ![Daraufzeigen zur Anzeige der aktuellen Variablenwerte](./media/calc-vs2019-hover-tooltip.png "Daraufzeigen zur Anzeige der aktuellen Variablenwerte")

### <a name="to-continue-debugging"></a>Fortsetzen mit dem Debuggen

1. In der gelben Zeile auf der linken Seite wird der aktuelle Stand der Ausführung angezeigt. Die aktuelle Zeile ruft `Calculate` auf. Drücken Sie also **F11**, um einen **Einzelschritt** in der Funktion auszuführen. Dadurch wechseln Sie zum Text der `Calculate`-Funktion. Wenden Sie den **Einzelschritt** mit Bedacht an; wenn Sie dies zu oft tun, verschwenden Sie unter Umständen viel Zeit. Sie gehen damit in jeden Code, den Sie in der Zeile verwenden, einschließlich der standardmäßigen Bibliotheksfunktionen.

1. Der Ausführungsstand befindet sich nun gerade auf dem Beginn der `Calculate`-Funktion. Drücken Sie **F10**, um zur nächsten Zeile in der Programmausführung zu wechseln. **F10** wird auch als **Prozedurschritt** bezeichnet. Sie können die Option **Überspringen** verwenden, um von Zeile zu Zeile zu springen, ohne dabei genau die Details jedes Teils der Zeile anzusehen. Prinzipiell sollten Sie **Überspringen** gegenüber **Hineinspringen** bevorzugen, es sei denn, Sie möchten sich wirklich den Code genauer ansehen, der von einem anderen Punkt abgerufen wird, so wie Sie dies getan haben, um sich den Textkörper von `Calculate` anzusehen.

1. Verwenden Sie **F10**, um solange Zeilen zu **überspringen**, bis Sie sich wieder in der `main()`-Funktion in der anderen Datei befinden, und halten Sie dort in der Zeile `cout` an.

   Es scheint, das Programm funktioniert wie erwartet: Es nimmt die erste Zahl und dividiert sie durch die zweite. Bewegen Sie in der `cout`-Zeile den Mauszeiger über die Variable `result`, oder sehen Sie sich `result` im Fenster **Auto** an. Sie sehen, dass der Wert als „inf“ aufgelistet ist, was offenbar falsch ist, also korrigieren wir dies. Die `cout`-Zeile gibt nur aus, welcher Wert auch immer in `result` gespeichert ist. Wenn Sie also mithilfe von **F10** eine Zeile weiter springen, wird im Konsolenfenster Folgendes angezeigt:

   ![Das Ergebnis der Division durch 0](./media/calc-vs2019-divide-by-zero-fail.png "Das Ergebnis der Division durch 0")

   Dieses Ergebnis resultiert daraus, dass die Division durch Null (0) nicht definiert ist. Das Programm hat also keine numerische Antwort für die angeforderte Operation.

### <a name="to-fix-the-divide-by-zero-error"></a>Beheben des Fehlers „Division durch Null“

Entwickeln Sie eine elegantere Lösung für die Division durch Null, damit der Benutzer das Problem auch versteht.

1. Nehmen Sie in *CalculatorTutorial.cpp* die folgenden Änderungen vor. Dank eines Debuggerfeatures namens **Bearbeiten und Fortfahren** kann das Programm weiter ausgeführt werden, während Sie Änderungen vornehmen:

    ```cpp
    // CalculatorTutorial.cpp : This file contains the 'main' function. Program execution begins and ends there.
    //

    #include <iostream>
    #include "Calculator.h"

    using namespace std;

    int main()
    {
        double x = 0.0;
        double y = 0.0;
        double result = 0.0;
        char oper = '+';

        cout << "Calculator Console Application" << endl << endl;
        cout << "Please enter the operation to perform. Format: a+b | a-b | a*b | a/b" << endl;

        Calculator c;
        while (true)
        {
            cin  >> x  >> oper  >> y;
            if (oper == '/' && y == 0)
            {
                cout << "Division by 0 exception" << endl;
                continue;
            }
            else
            {
                result = c.Calculate(x, oper, y);
            }
            cout << "Result is: " << result << endl;
        }

        return 0;
    }
    ```

1. Drücken Sie nun einmal **F5**. Die Programmausführung wird ordnungsgemäß fortgeführt, bis das Programm pausiert, um eine Benutzereingabe anzufordern. Geben Sie noch einmal `10 / 0` ein. Nun wird eine hilfreichere Antwort ausgegeben. Der Benutzer wird zu weiterer Eingabe aufgefordert, und das Programm wird weiter normal ausgeführt.

   ![Das Endergebnis nach den Änderungen](./media/calc-vs2019-final-verification.png "Das Endergebnis nach den Änderungen")

   > [!Note]
   > Wenn Sie Code bearbeiten, während sich das Programm im Debugmodus befindet, besteht die Gefahr, dass der Code veraltet. Dies geschieht, wenn der Debugger noch Ihren alten Code ausführt, und Ihre Änderungen noch nicht übernommen wurden. In so einem Fall werden Sie durch eine Popupmeldung vom Debugger informiert. Gelegentlich sollten Sie **F5** drücken, um den gerade ausgeführten Code zu aktualisieren. Insbesondere wenn Sie eine Änderung in einer Funktion vornehmen, während sich der Ausführungspunkt innerhalb genau dieser Funktion befindet, müssen Sie einen Prozedurschritt aus dieser Funktion vornehmen, und danach wieder in die Funktion hineinspringen, um den aktualisierten Code zu erhalten. Wenn dies aus welchen Gründen auch immer nicht funktioniert, und eine Fehlermeldung zurückgegeben wird, können Sie das Debuggen anhalten, indem Sie oben in der IDE in der Symbolleiste unter den Menüs auf das rote Quadrat klicken, dann das Debugging mithilfe von **F5** erneut starten, oder in der Symbolleiste neben der Stoppschaltfläche auf den grünen Wiedergabepfeil klicken.

   > Grundlegendes zu den Tastenkombinationen zum Ausführen und Debuggen
   >
   > - **F5** bzw. **Debuggen** > **Debuggen starten** startet eine Debugsitzung, wenn noch keine aktiv ist, und führt das Programm so lange aus, bis ein Breakpoint erreicht wird, oder das Programm Benutzereingabe erfordert. Wenn keine Benutzereingabe benötigt wird, und es keinen Breakpoint gibt, der erreicht werden könnte, wird das Programm beendet, und das Konsolenfenster schließt sich automatisch, sobald das Programm die Ausführung beendet hat. Wenn ein „Hallo Welt“- oder ein ähnliches Programm ausgeführt werden soll, verwenden Sie **STRG+F5** oder legen einen Breakpoint fest, bevor Sie **F5** drücken, damit das Fenster nicht geschlossen wird.
   > - Mit **STRG+F5** bzw. **Debuggen** > **Ohne Debuggen starten** wird die Anwendung ausgeführt, ohne dass der Debugmodus gestartet wird. Dies benötigt etwas weniger Zeit als das Debuggen, und das Konsolenfenster bleibt geöffnet, nachdem das Programm die Ausführung beendet hat.
   > - **F10** bzw. **Überspringen** ermöglicht es Ihnen, Zeile für Zeile den Code zu durchlaufen, wodurch Sie eine Vorstellung davon erhalten, wie der Code ausgeführt wird, und welche Variablenwerte es an jedem Ausführungsschritt gibt.
   > - **F11** bzw. **Hineinspringen** funktioniert ähnlich wie **Überspringen**. Allerdings wird hierbei in jede Funktion hineingesprungen, die auf der jeweiligen Ausführungszeile aufgerufen wird. Wenn die Zeile, die ausgeführt wird, z. B. eine Funktion aufruft, lässt **F11** den Zeiger in den Textkörper dieser Funktion springen, damit Sie dem ausgeführten Funktionscode folgen können, bevor Sie zur Zeile zurückkehren, in der Sie F11 gedrückt haben. Wenn Sie **F10** drücken, werden Funktionsaufrufe einfach übersprungen, und der Zeiger geht einfach zur nächsten Zeile. Der Funktionsaufruf findet dennoch statt, das Programm pausiert jedoch nicht, damit Sie sich ansehen können, was es gerade tut.

### <a name="close-the-app"></a>Schließen der App

- Wenn die Ausführung noch nicht beendet ist, schließen Sie das Konsolenfenster für die Rechner-App.

## <a name="the-finished-app"></a>Die fertige App

Herzlichen Glückwunsch! Sie haben den Code für die Rechner-App fertiggestellt, und diese in Visual Studio erstellt und debuggt.

## <a name="next-steps"></a>Nächste Schritte

[Weitere Informationen zu Visual Studio für C++](https://devblogs.microsoft.com/cppblog/getting-started-with-visual-studio-for-c-and-cpp-development/)

::: moniker-end

::: moniker range="<vs-2019"

C++-Programmierer beginnen häufig mit einer „Hallo, Welt!“- Anwendung, die über die Befehlszeile ausgeführt wird. Eine solche Anwendung erstellen Sie mithilfe dieses Artikels in Visual Studio. Anschließend beschäftigen Sie sich mit einer etwas schwierigeren Aufgabe: der Erstellung einer Taschenrechner-App.

## <a name="prerequisites"></a>Voraussetzungen

- Visual Studio mit der Workload **Desktopentwicklung mit C++** muss auf Ihrem Computer installiert sein und ausgeführt werden. Ist dies noch nicht der Fall, finden Sie unter [Install C++ support in Visual Studio (Installieren von C++-Komponenten in Visual Studio)](../build/vscpp-step-0-installation.md) weitere Informationen.

## <a name="create-your-app-project"></a>Erstellen Ihres App-Projekts

Visual Studio verwendet *Projekte*, um Code für eine App zu ordnen, und *Projektmappen*, um Ihre Projekte zu ordnen. Ein Projekt beinhaltet alle Optionen, Einstellungen und Regeln, die Sie zum Erstellen Ihrer Anwendung verwendet haben. Es verwaltet auch die Beziehungen zwischen allen Projektdateien und externen Dateien. Wenn Sie Ihre App erstellen möchten, müssen Sie zuerst ein neues Projekt und eine Projektmappe erstellen.

1. Klicken Sie in der Menüleiste in Visual Studio auf **Datei** > **Neu** > **Projekt**. Das Fenster **Neues Projekt** wird angezeigt.

2. Prüfen Sie auf der linken Randleiste, ob **Visual C++** ausgewählt ist. Wählen Sie im mittleren Bereich **Windows-Konsolenanwendung** aus.

3. Geben Sie unten im Eingabefeld **Name** den Begriff *CalculatorTutorial* als Name für das neue Projekt ein, und klicken Sie dann auf **OK**.

   ![Das Dialogfeld „Neues Projekt“](./media/calculator-new-project-dialog.png "Das Dialogfeld „Neues Projekt“")

   Eine leere C++-Windows-Konsolenanwendung wird erstellt. Konsolenanwendungen verwenden ein Windows-Konsolenfenster, um Ausgabe anzuzeigen und Benutzereingaben entgegenzunehmen. In Visual Studio wird ein Editorfenster geöffnet und der generierte Code angezeigt:

    ```cpp
    // CalculatorTutorial.cpp : This file contains the 'main' function. Program execution begins and ends there.
    //

    #include "pch.h"
    #include <iostream>

    int main()
    {
        std::cout << "Hello World!\n";
    }

    // Run program: Ctrl + F5 or Debug > Start Without Debugging menu
    // Debug program: F5 or Debug > Start Debugging menu

    // Tips for Getting Started:
    //   1. Use the Solution Explorer window to add/manage files
    //   2. Use the Team Explorer window to connect to source control
    //   3. Use the Output window to see build output and other messages
    //   4. Use the Error List window to view errors
    //   5. Go to Project > Add New Item to create new code files, or Project > Add Existing Item to add existing code files to the project
    //   6. In the future, to open this project again, go to File > Open > Project and select the .sln file
    ```

## <a name="verify-that-your-new-app-builds-and-runs"></a>Überprüfen, dass Ihre neue App erstellt und ausgeführt wird

Die Vorlage für eine neue Windows-Konsolenanwendung erstellt eine einfache C++-„Hallo Welt“-App. An diesem Punkt können Sie sehen, wie die Apps, die Sie direkt in der IDE erstellen, in Visual Studio erstellt und ausgeführt werden.

1. Wählen Sie zum Erstellen Ihres Projekts aus dem Menü **Erstellen** die Option **Projektmappe erstellen** aus. Im Fenster **Ausgabe** wird das Ergebnis des Erstellungsprozess angezeigt.

   ![Erstellen des Projekts](./media/calculator-initial-build-output.png "Erstellen des Projekts")

1. Klicken Sie zum Ausführen des Codes auf der Menüleiste auf **Debuggen** > **Ohne Debuggen starten**.

   ![Starten des Projekts](./media/calculator-hello-world-console.png "Starten des Projekts")

   Ein Konsolenfenster wird geöffnet, und Ihre App daraufhin ausgeführt. Wenn Sie eine Konsolen-App in Visual Studio starten, führt diese Ihren Code aus und gibt dann „Press any key to continue . .“ (Beliebige Taste zum Fortfahren drücken) zurück, damit Sie sich die Ausgabe ansehen können. Herzlichen Glückwunsch! Sie haben Ihre erste „Hallo, Welt!“- Konsolen-App in Visual Studio erstellt!

1. Drücken Sie eine Taste, um das Konsolenfenster zu schließen, und kehren Sie zu Visual Studio zurück.

Sie haben nun die Tools, um Ihre App nach jeder Änderung zu erstellen und auszuführen, um zu überprüfen, ob der Code noch so funktioniert, wie Sie es erwarten. Später erhalten Sie Informationen zum Debuggen, wenn Ihr Code nicht funktioniert.

## <a name="edit-the-code"></a>Bearbeiten des Codes

Wandeln Sie den Code in dieser Vorlage nun in eine Rechner-App um.

1. Bearbeiten Sie in der Datei *CalculatorTutorial.cpp* den Code, sodass dieser dem folgenden Beispiel entspricht:

    ```cpp
    // CalculatorTutorial.cpp : This file contains the 'main' function. Program execution begins and ends there.
    //

    #include "pch.h"
    #include <iostream>

    using namespace std;

    int main()
    {
        cout << "Calculator Console Application" << endl << endl;
        cout << "Please enter the operation to perform. Format: a+b | a-b | a*b | a/b"
            << endl;
        return 0;
    }

    // Run program: Ctrl + F5 or Debug > Start Without Debugging menu
    // Debug program: F5 or Debug > Start Debugging menu
    // Tips for Getting Started:
    //   1. Use the Solution Explorer window to add/manage files
    //   2. Use the Team Explorer window to connect to source control
    //   3. Use the Output window to see build output and other messages
    //   4. Use the Error List window to view errors
    //   5. Go to Project > Add New Item to create new code files, or Project > Add Existing Item to add existing code files to the project
    //   6. In the future, to open this project again, go to File > Open > Project and select the .sln file
    ```

   > Grundlegendes zum Code:
   >
   > - Die `#include`-Anweisungen ermöglichen es Ihnen, auf Code zu verweisen, der sich in anderen Dateien befindet. Manchmal kommt es vor, dass Sie einen Dateinamen sehen, der von spitzen Klammern ( **\<\>** ) eingeschlossen wird, manchmal wird er von Anführungszeichen ( **" "** ) eingeschlossen. Generell werden spitze Klammern verwendet, wenn auf die C++-Standardbibliothek verwiesen wird, während Anführungszeichen für andere Dateien verwendet werden.
   > - Die `#include "pch.h"`-Zeile (bzw. die `#include "stdafx.h"`-Zeile in Visual Studio 2017 und früher) verweist auf etwas, das als vorkompilierter Header bezeichnet wird. Diese werden oft von professionellen Programmierern verwendet, um Kompilierungszeiten zu verbessern. Für dieses Tutorial wären das aber schon zu weit gegriffen.
   > - Die `using namespace std;`-Zeile sagt dem Compiler, dass dieser Inhalt aus der C++-Standardbibliothek zu erwarten hat, der in dieser Datei verwendet werden soll. Ohne diese Zeile müsste vor jedem Stichwort aus der Bibliothek `std::` stehen, um dessen Bereich anzuzeigen. Ohne diese Zeile müsste beispielsweise jeder Verweis auf `cout` als `std::cout` geschrieben werden. Die `using`-Anweisung wird hinzugefügt, um den Code übersichtlicher zu gestalten.
   > - Das Schlüsselwort `cout` wird verwendet, damit die Standardausgabe in C++ erfolgt. Der Operator **\<\<** sagt dem Compiler, dass dieser alles, was rechts von ihm steht, an die Standardausgabe senden soll.
   > - Das Schlüsselwort **endl** ist ähnlich wie die Eingabetaste. Es beendet die Zeile und lässt den Cursor in die nächste Zeile springen. Es hat sich aber noch mehr bewährt, innerhalb der Zeichenfolge mit demselben Effekt ein `\n`-Zeichen zu setzen (eingeschlossen von ""), da `endl` den Puffer immer leert und der Leistung des Programms schaden kann. Da es sich hier aber um eine kleine App handelt, wird stattdessen aus Gründen der besseren Lesbarkeit `endl` verwendet.
   > - Alle C++-Anweisungen müssen mit einem Semikolon enden, und alle C++-Anwendungen müssen eine `main()`-Funktion enthalten. Diese Funktion wird vom Programm zuerst ausgeführt. Die Funktion `main()` muss auf den ganzen Code zugreifen können, damit dieser verwendet werden kann.

1. Wenn Sie die Datei speichern möchten, drücken Sie **STRG+S**, oder klicken Sie im oberen Bereich der IDE auf das **Speichern**-Symbol: das Diskettensymbol in der Symbolleiste unterhalb der Menüleiste.

1. Drücken Sie **STRG+F5**, um die Anwendung auszuführen, oder wechseln Sie zum **Debuggen**-Menü, und wählen Sie dort **Ohne Debuggen starten** aus. Wenn ein Popupelement mit der Meldung **Dieses Projekt ist nicht mehr aktuell** angezeigt wird, können Sie **Dieses Dialogfeld nicht mehr anzeigen** auswählen, und dann **Ja**, um Ihre Anwendung zu erstellen. Es sollte nun ein Konsolenfenster mit dem im Code angegebenen Text angezeigt werden.

   ![Erstellen und Starten der Anwendung](./media/calculator-first-launch.gif "Erstellen und Starten der Anwendung")

1. Schließen Sie das Konsolenfenster, sobald Sie fertig sind.

## <a name="add-code-to-do-some-math"></a>Hinzufügen von Code für Berechnungen

Jetzt können Sie mathematische Logik hinzufügen.

### <a name="to-add-a-calculator-class"></a>Hinzufügen einer Rechnerklasse

1. Wechseln Sie zum Menü **Projekt**, und wählen Sie **Klasse hinzufügen** aus. Geben Sie im Eingabefeld für **Klassenname** den Namen *Calculator* (Taschenrechner) ein. Klicken Sie auf **OK**. Zwei neue Dateien werden Ihrem Projekt hinzugefügt. Um alle geänderten Dateien auf einmal zu speichern, drücken Sie **STRG+UMSCHALT+S**. Dies ist die Tastenkombination für **Datei** > **Alle speichern**. Es gibt auch eine Symbolleistenschaltfläche für **Alle speichern**: ein Symbol mit zwei Disketten. Diese Schaltfläche befindet sich neben der Schaltfläche **Speichern**. Generell hat es sich bewährt, **Alle speichern** häufig auszuführen, damit auch wirklich alle Dateien gespeichert werden.

   ![Erstellen der Calculator-Klasse](./media/calculator-create-class.gif "Erstellen der Calculator-Klasse")

   Eine Klasse ist wie ein Entwurf für ein Objekt, das etwas tut. In diesem Fall soll ein Rechner und dessen Funktionsweise definiert werden. Der Assistent **Klasse hinzufügen**, den Sie oben verwendet haben, hat .h- und .cpp-Dateien erstellt, die denselben Namen wie die Klasse haben. Im am Rand der IDE angezeigten Fenster **Projektmappen-Explorer** können Sie sich eine vollständige Liste Ihrer Projektdateien ansehen. Wenn das Fenster nicht angezeigt wird, können Sie es über die Menüleiste öffnen: Klicken Sie auf **Ansicht** > **Projektmappen-Explorer**.

   ![Projektmappen-Explorer](./media/calculator-solution-explorer.png "Projektmappen-Explorer")

   Sie sollten in Editor nun drei Registerkarten geöffnet haben: *CalculatorTutorial.cpp*, *Calculator.h* und *Calculator.cpp*. Wenn Sie eine davon versehentlich schließen, können Sie sie im **Projektmappen-Explorer**-Fenster jeweils mit einem Doppelklick auf die Datei wieder öffnen.

1. Entfernen Sie in **Calculator.h** die Zeilen `Calculator();` und `~Calculator();`, die erstellt wurden, jedoch nicht benötigt werden. Fügen Sie dann die folgende Codezeile hinzu, sodass die Datei nun folgendermaßen aussieht:

    ```cpp
    #pragma once
    class Calculator
    {
    public:
        double Calculate(double x, char oper, double y);
    };
    ```

   > Grundlegendes zum Code
   >
   > - Die Zeile, die Sie hinzugefügt haben, deklariert eine neue Funktion namens `Calculate`, die Sie verwenden, um mathematische Operationen für Addition, Subtraktion, Multiplikation und Division auszuführen.
   > - C++-Code ist unterteilt in *Headerdateien* (.h) und *Quelldateien* (.cpp). Von verschiedenen Compilern werden auch noch andere Dateierweiterungen unterstützt; die eben vorgestellten sind aber die wichtigsten, die Sie kennen sollten. Funktionen und Variablen werden normalerweise *deklariert*, d. h. ihnen wird in den Headerdateien ein Name und ein Typ zugeordnet, und *implementiert*, d. h. ihnen wird in den Quelldateien eine Definition zugeordnet. Um auf in einer anderen Datei definierten Code zuzugreifen, können Sie `#include "filename.h"` verwenden. Dabei ist „filename.h“ der Name der Datei, die die Variablen und Funktionen deklariert, die Sie verwenden möchten.
   > - Die zwei Zeilen, die Sie gelöscht haben, haben einen *Konstruktor* und einen *Destruktor* für die Klasse deklariert. Für eine einfache Klasse wie die vorliegende werden diese vom Compiler für Sie erstellt. Deren Verwendung liegt aber außerhalb des in diesem Tutorial abgedeckten Bereichs.
   > - Es hat sich bewährt, Ihren Code auf Grundlage der jeweiligen Funktion in verschiedenen Dateien zu organisieren. Dies erleichtert das spätere Auffinden des benötigen Codes. Hier definieren Sie die `Calculator`-Klasse und die Datei, die die `main()`-Funktion enthält, einzeln. Es soll aber dennoch in `main()` auf die `Calculator`-Klasse verwiesen werden.

1. Unter `Calculate` wird eine grüne Wellenlinie angezeigt. Dies liegt daran, dass die `Calculate`-Funktion in der CPP-Datei nicht definiert wurde. Bewegen Sie den Mauszeiger über das Wort, klicken Sie dann auf die Glühbirne, die angezeigt wird, und wählen Sie dann **Create definition of „Calculate“ in Calculator.cpp** (Definition von „Calculate“ in Calculator.cpp erstellen). Ein Popupelement wird angezeigt, das Ihnen eine Vorschau der Codeänderung anzeigt, die in der anderen Datei vorgenommen wurde. Der Code wurde *Calculator.cpp* hinzugefügt.

   ![Erstellen der Definition von Calculate](./media/calculator-create-definition.gif "Erstellen der Definition von Calculate")

   Momentan wird nur 0.0 zurückgegeben. Ändern Sie das nun. Drücken Sie **ESC**, um das Popupelement zu schließen.

1. Wechseln Sie zur *Calculator.cpp*-Datei im Editorfenster. Entfernen Sie die Bereiche `Calculator()` und `~Calculator()` (wie in der .h-Datei bereits geschehen), und fügen Sie `Calculate()` den folgenden Code hinzu:

    ```cpp
    #include "pch.h"
    #include "Calculator.h"

    double Calculator::Calculate(double x, char oper, double y)
    {
        switch(oper)
        {
            case '+':
                return x + y;
            case '-':
                return x - y;
            case '*':
                return x * y;
            case '/':
                return x / y;
            default:
                return 0.0;
        }
    }
    ```

   > Grundlegendes zum Code
   >
   > - Die Funktion `Calculate` nimmt eine Zahl, einen Operator und eine zweite Zahl, und führt dann die angeforderte Operation mit den angegebenen Zahlen durch.
   > - Die Switch-Anweisung überprüft, welcher Operator bereitgestellt wurde, und führt nur den für diese Operation entsprechenden Fall aus. Der „default:“-Fall ist ein Fallback, falls der Benutzer einen Operator eingibt, der nicht akzeptiert wird, damit das Programm nicht unterbrochen wird. Allgemein wird mit ungültiger Benutzereingabe am besten auf elegantere Weise umgegangen. Dies würde für dieses Tutorial aber zu weit führen.
   > - Das `double`-Schlüsselwort denotiert eine Zahlenart, die Dezimalzahlen unterstützt. Auf diese Weise kann der Rechner sowohl Berechnungen mit Dezimalzahlen als auch mit ganzen Zahlen verarbeiten. Die `Calculate`-Funktion muss aufgrund von `double` ganz am Anfang des Codes (dadurch wird der Rückgabetyp der Funktion angegeben) immer eine solche Zahl zurückgeben. Deshalb wird auch im „default:“-Fall 0.0 zurückgegeben.
   > - Die .h-Datei deklariert die Funktion *prototype*, die dem Compiler bereits vorab sagt, welcher Parameter benötigt wird, und welcher Rückgabetyp zu erwarten ist. In der .cpp-Datei sind alle Implementierungsdetails der Funktion enthalten.

Wenn Sie nun den Code noch einmal erstellen und ausführen, wird er nach der Aufforderung, den gewünschten Vorgang anzugeben, erneut beendet. Bearbeiten Sie als nächsten Schritt die `main`-Funktion, um einige Berechnungen durchzuführen.

### <a name="to-call-the-calculator-class-member-functions"></a>Aufrufen der Memberfunktionen der Rechnerklasse

1. Aktualisieren Sie nun die `main`-Funktion in *CalculatorTutorial.cpp*:

    ```cpp
    // CalculatorTutorial.cpp : This file contains the 'main' function. Program execution begins and ends there.
    //

    #include "pch.h"
    #include <iostream>
    #include "Calculator.h"

    using namespace std;

    int main()
    {
        double x = 0.0;
        double y = 0.0;
        double result = 0.0;
        char oper = '+';

        cout << "Calculator Console Application" << endl << endl;
        cout << "Please enter the operation to perform. Format: a+b | a-b | a*b | a/b"
             << endl;

        Calculator c;
        while (true)
        {
            cin >> x >> oper >> y;
            result = c.Calculate(x, oper, y);
            cout << "Result is: " << result << endl;
        }

        return 0;
    }
    ```

   > Grundlegendes zum Code
   >
   > - Da C++-Programme immer bei der `main()`-Funktion starten, müssen Sie den weiteren Code von dort aus aufrufen. Es wird also eine `#include`-Anweisung benötigt.
   > - Einige anfängliche Variablen (`x`, `y`, `oper` und `result`) werden deklariert, um jeweils die erste Zahl, die zweite Zahl, den Operator und das Endergebnis zu speichern. Es empfiehlt sich immer, einige anfängliche Variablen anzugeben, um nicht definiertes Verhalten zu vermeiden. Genau dies ist hier geschehen.
   > - Die `Calculator c;`-Zeile deklariert ein Objekt namens „c“ als Instanz der `Calculator`-Klasse. Die Klasse selbst ist lediglich ein Entwurf dafür, wie der Rechner funktioniert. Das Objekt ist der spezifische Rechner, der die Berechnungen ausführt.
   > - Die `while (true)`-Anweisung ist eine Schleife. Der Code innerhalb der Schleife wird wieder und wieder ausgeführt, so lange, bis die Bedingung innerhalb der `()` erfüllt ist. Da die Bedingung nur als `true` aufgeführt ist, ist sie immer wahr, die Schleife wird also ununterbrochen ausgeführt. Um das Programm zu schließen, muss der Benutzer das Konsolenfenster manuell schließen. Andernfalls wartet das Programm ständig auf eine neue Eingabe.
   > - Das `cin`-Schlüsselwort wird verwendet, um Benutzereingaben anzunehmen. Dieser Eingabestream ist intelligent genug, um eine Textzeile zu verarbeiten, die im Konsolenfenster eingegeben wird, und diese in der richtigen Reihenfolge innerhalb aller aufgeführten Variablen zu platzieren, vorausgesetzt, die Benutzereingabe entspricht den benötigten Spezifikationen. Sie können diese Zeile bearbeiten, sodass verschiedene Eingabearten akzeptiert werden, z. B. mehr als zwei Zahlen. Dafür müsste aber auch die `Calculate()`-Funktion aktualisiert werden.
   > - Der `c.Calculate(x, oper, y);`-Ausdruck ruft die zuvor definierte `Calculate`-Funktion auf und stellt die eingegebenen Eingabewerte zur Verfügung. Die Funktion gibt dann eine Zahl zurück, die in `result` gespeichert wird.
   > - Abschließend wird `result` in der Konsole ausgegeben, sodass der Benutzer das Ergebnis der Berechnung ansehen kann.

### <a name="build-and-test-the-code-again"></a>Erneutes Erstellen und Testen des Codes

Testen Sie das Programm nun erneut, ob auch alles wie vorgesehen funktioniert.

1. Drücken Sie **STRG+F5**, um die App neu zu erstellen und zu starten.

1. Geben Sie `5 + 5` ein, und drücken Sie die **EINGABETASTE**. Überprüfen Sie, ob das Ergebnis 10 ist.

   ![Das Ergebnis von 5 + 5](./media/calculator-five-plus-five.png "Das Ergebnis von 5 + 5")

## <a name="debug-the-app"></a>Debuggen der App

Da es keine Beschränkungen gibt, was der Benutzer im Konsolenfenster eingeben kann, sorgen Sie nun dafür, dass der Rechner Eingaben wie erwartet verarbeitet. Anstatt das Programm auszuführen, debuggen Sie es, damit Sie sich ansehen können, wie genau das Programm Schritt für Schritt abläuft.

### <a name="to-run-the-app-in-the-debugger"></a>Ausführen der App im Debugger

1. Setzen Sie auf der `result = c.Calculate(x, oper, y);`-Zeile einen Breakpoint, exakt nach dem Punkt, an dem der Benutzer zur Eingabe aufgefordert wurde. Um den Breakpoint festzulegen, klicken Sie auf der linken Seite des Editorfensters neben der Zeile auf den grauen, vertikalen Rand. Ein roter Punkt wird angezeigt.

   ![Festlegen eines Breakpoints](./media/calculator-set-breakpoint.gif "Haltepunkt festlegen")

   Ab sofort wird die Ausführung dann immer bei dieser Zeile angehalten, wenn Sie das Programm debuggen. Wir haben bereits eine grobe Vorstellung, dass das Programm in einfachen Fällen funktioniert. Da wir die Ausführung nicht jedes Mal anhalten möchten, legen wir den Breakpoint als bedingt fest.

1. Klicken Sie mit der rechten Maustaste auf den roten Punkt, der den Breakpoint darstellt, und wählen Sie dann **Bedingungen** aus. Geben Sie im Eingabefeld für die Bedingung `(y == 0) && (oper == '/')` ein. Wenn Sie fertig sind, wählen Sie die Schaltfläche **OK** aus. Die Bedingung wird automatisch gespeichert.

   ![Festlegen eines bedingten Breakpoints](./media/calculator-conditional-breakpoint.gif "Festlegen eines bedingten Breakpoints")

   Die Ausführung wird nun also genau dann am Breakpoint angehalten, wenn versucht wird, durch 0 zu teilen.

1. Drücken Sie **F5**, um das Programm zu debuggen, oder wählen Sie die Schaltfläche **Lokaler Windows-Debugger** mit dem grünen Pfeilsymbol auf der Symbolleiste aus. Wenn Sie in Ihrer Konsolen-App z. B. „5 - 0“ eingeben, verhält sich das Programm normal und wird weiter ausgeführt. Wenn Sie nun jedoch „10 / 0“ eingeben, hält das Programm am Breakpoint an. Auch wenn Sie eine beliebige Anzahl von Leerzeichen zwischen den Operator und die Zahlen setzen, ist `cin` intelligent genug, um die Eingabe dennoch korrekt zu analysieren.

   ![Anhalten am bedingten Breakpoint](./media/calculator-debug-conditional.gif "Anhalten am bedingten Breakpoint")

### <a name="useful-windows-in-the-debugger"></a>Nützliche Fenster im Debugger

Sobald Sie Ihren Code debuggen, können Sie feststellen, dass ein paar neue Fenster angezeigt werden. Diese Fenster unterstützen Sie beim Debuggen. Sehen Sie sich das Fenster **Auto** an. Im Fenster **Auto** sehen Sie die aktuellen Werte der Variablen, die mindestens in den letzten drei Zeilen und bis zur aktuellen Zeile verwendet wurden.

   ![Fenster „Auto“](./media/calculator-autos.png "Fenster „Auto“")

Wenn Sie alle Variablen dieser Funktion ansehen möchten, wechseln Sie zum Fenster **Lokale**. Tatsächlich können Sie die Werte dieser Variablen während des Debuggens bearbeiten, um zu erfahren, welche Auswirkung sie auf das Programm haben würden. Hier bearbeiten Sie die Variablen jedoch nicht.

   ![Fenster „Lokale Variablen“](./media/calculator-locals.png "Fenster „Lokale Variablen“")

Sie können auch einfach direkt im Code den Mauszeiger auf Variablen bewegen, um deren aktuelle Werte an den Stellen anzeigen zu lassen, an denen die Ausführung jeweils pausiert wurde. Sorgen Sie dafür, dass sich das Editorfenster im Vordergrund befindet, indem Sie darauf klicken, bevor Sie diesen Vorgang testen.

   ![Daraufzeigen zur Anzeige der aktuellen Variablenwerte](./media/calculator-hover-tooltip.gif "Daraufzeigen zur Anzeige der aktuellen Variablenwerte")

### <a name="to-continue-debugging"></a>Fortsetzen mit dem Debuggen

1. In der gelben Zeile auf der linken Seite wird der aktuelle Stand der Ausführung angezeigt. Die aktuelle Zeile ruft `Calculate` auf. Drücken Sie also **F11**, um einen **Einzelschritt** in der Funktion auszuführen. Dadurch wechseln Sie zum Text der `Calculate`-Funktion. Wenden Sie den **Einzelschritt** mit Bedacht an; wenn Sie dies zu oft tun, verschwenden Sie unter Umständen viel Zeit. Sie gehen damit in jeden Code, den Sie in der Zeile verwenden, einschließlich der standardmäßigen Bibliotheksfunktionen.

1. Der Ausführungsstand befindet sich nun gerade auf dem Beginn der `Calculate`-Funktion. Drücken Sie **F10**, um zur nächsten Zeile in der Programmausführung zu wechseln. **F10** wird auch als **Prozedurschritt** bezeichnet. Sie können die Option **Überspringen** verwenden, um von Zeile zu Zeile zu springen, ohne dabei genau die Details jedes Teils der Zeile anzusehen. Prinzipiell sollten Sie **Überspringen** gegenüber **Hineinspringen** bevorzugen, es sei denn, Sie möchten sich wirklich den Code genauer ansehen, der von einem anderen Punkt abgerufen wird, so wie Sie dies getan haben, um sich den Textkörper von `Calculate` anzusehen.

1. Verwenden Sie **F10**, um solange Zeilen zu **überspringen**, bis Sie sich wieder in der `main()`-Funktion in der anderen Datei befinden, und halten Sie dort in der Zeile `cout` an.

   ![Ausführen von Calculate bis Rücksprung und Überprüfen des Ergebnisses](./media/calculator-undefined-zero.gif "Ausführen von Calculate bis Rücksprung und Überprüfen des Ergebnisses")

   Es scheint, das Programm funktioniert wie erwartet: Es nimmt die erste Zahl und dividiert sie durch die zweite. Bewegen Sie in der `cout`-Zeile den Mauszeiger über die Variable `result`, oder sehen Sie sich `result` im Fenster **Auto** an. Sie sehen, dass der Wert als „inf“ aufgelistet ist, was offenbar falsch ist, also korrigieren wir dies. Die `cout`-Zeile gibt nur aus, welcher Wert auch immer in `result` gespeichert ist. Wenn Sie also mithilfe von **F10** eine Zeile weiter springen, wird im Konsolenfenster Folgendes angezeigt:

   ![Das Ergebnis der Division durch 0](./media/calculator-divide-by-zero-fail.png "Das Ergebnis der Division durch 0")

   Dieses Ergebnis resultiert daraus, dass die Division durch Null (0) nicht definiert ist. Das Programm hat also keine numerische Antwort für die angeforderte Operation.

### <a name="to-fix-the-divide-by-zero-error"></a>Beheben des Fehlers „Division durch Null“

Entwickeln Sie eine elegantere Lösung für die Division durch Null, damit der Benutzer das Problem auch versteht.

1. Nehmen Sie in *CalculatorTutorial.cpp* die folgenden Änderungen vor. Dank eines Debuggerfeatures namens **Bearbeiten und Fortfahren** kann das Programm weiter ausgeführt werden, während Sie Änderungen vornehmen:

    ```cpp
    // CalculatorTutorial.cpp : This file contains the 'main' function. Program execution begins and ends there.
    //

    #include "pch.h"
    #include <iostream>
    #include "Calculator.h"

    using namespace std;

    int main()
    {
        double x = 0.0;
        double y = 0.0;
        double result = 0.0;
        char oper = '+';

        cout << "Calculator Console Application" << endl << endl;
        cout << "Please enter the operation to perform. Format: a+b | a-b | a*b | a/b" << endl;

        Calculator c;
        while (true)
        {
            cin  >> x  >> oper  >> y;
            if (oper == '/' && y == 0)
            {
                cout << "Division by 0 exception" << endl;
                continue;
            }
            else
            {
                result = c.Calculate(x, oper, y);
            }
            cout << "Result is: " << result << endl;
        }

        return 0;
    }
    ```

1. Drücken Sie nun einmal **F5**. Die Programmausführung wird ordnungsgemäß fortgeführt, bis das Programm pausiert, um eine Benutzereingabe anzufordern. Geben Sie noch einmal `10 / 0` ein. Nun wird eine hilfreichere Antwort ausgegeben. Der Benutzer wird zu weiterer Eingabe aufgefordert, und das Programm wird weiter normal ausgeführt.

   ![Das Endergebnis nach den Änderungen](./media/calculator-final-verification.gif "Das Endergebnis nach den Änderungen")

   > [!Note]
   > Wenn Sie Code bearbeiten, während sich das Programm im Debugmodus befindet, besteht die Gefahr, dass der Code veraltet. Dies geschieht, wenn der Debugger noch Ihren alten Code ausführt, und Ihre Änderungen noch nicht übernommen wurden. In so einem Fall werden Sie durch eine Popupmeldung vom Debugger informiert. Gelegentlich sollten Sie **F5** drücken, um den gerade ausgeführten Code zu aktualisieren. Insbesondere wenn Sie eine Änderung in einer Funktion vornehmen, während sich der Ausführungspunkt innerhalb genau dieser Funktion befindet, müssen Sie einen Prozedurschritt aus dieser Funktion vornehmen, und danach wieder in die Funktion hineinspringen, um den aktualisierten Code zu erhalten. Wenn dies aus welchen Gründen auch immer nicht funktioniert, und eine Fehlermeldung zurückgegeben wird, können Sie das Debuggen anhalten, indem Sie oben in der IDE in der Symbolleiste unter den Menüs auf das rote Quadrat klicken, dann das Debugging mithilfe von **F5** erneut starten, oder in der Symbolleiste neben der Stoppschaltfläche auf den grünen Wiedergabepfeil klicken.

   > Grundlegendes zu den Tastenkombinationen zum Ausführen und Debuggen
   >
   > - **F5** bzw. **Debuggen** > **Debuggen starten** startet eine Debugsitzung, wenn noch keine aktiv ist, und führt das Programm so lange aus, bis ein Breakpoint erreicht wird, oder das Programm Benutzereingabe erfordert. Wenn keine Benutzereingabe benötigt wird, und es keinen Breakpoint gibt, der erreicht werden könnte, wird das Programm beendet, und das Konsolenfenster schließt sich automatisch, sobald das Programm die Ausführung beendet hat. Wenn ein „Hallo Welt“- oder ein ähnliches Programm ausgeführt werden soll, verwenden Sie **STRG+F5** oder legen einen Breakpoint fest, bevor Sie **F5** drücken, damit das Fenster nicht geschlossen wird.
   > - Mit **STRG+F5** bzw. **Debuggen** > **Ohne Debuggen starten** wird die Anwendung ausgeführt, ohne dass der Debugmodus gestartet wird. Dies benötigt etwas weniger Zeit als das Debuggen, und das Konsolenfenster bleibt geöffnet, nachdem das Programm die Ausführung beendet hat.
   > - **F10** bzw. **Überspringen** ermöglicht es Ihnen, Zeile für Zeile den Code zu durchlaufen, wodurch Sie eine Vorstellung davon erhalten, wie der Code ausgeführt wird, und welche Variablenwerte es an jedem Ausführungsschritt gibt.
   > - **F11** bzw. **Hineinspringen** funktioniert ähnlich wie **Überspringen**. Allerdings wird hierbei in jede Funktion hineingesprungen, die auf der jeweiligen Ausführungszeile aufgerufen wird. Wenn die Zeile, die ausgeführt wird, z. B. eine Funktion aufruft, lässt **F11** den Zeiger in den Textkörper dieser Funktion springen, damit Sie dem ausgeführten Funktionscode folgen können, bevor Sie zur Zeile zurückkehren, in der Sie F11 gedrückt haben. Wenn Sie **F10** drücken, werden Funktionsaufrufe einfach übersprungen, und der Zeiger geht einfach zur nächsten Zeile. Der Funktionsaufruf findet dennoch statt, das Programm pausiert jedoch nicht, damit Sie sich ansehen können, was es gerade tut.

### <a name="close-the-app"></a>Schließen der App

- Wenn die Ausführung noch nicht beendet ist, schließen Sie das Konsolenfenster für die Rechner-App.

## <a name="the-finished-app"></a>Die fertige App

Herzlichen Glückwunsch! Sie haben den Code für die Rechner-App fertiggestellt, und diese in Visual Studio erstellt und debuggt.

## <a name="next-steps"></a>Nächste Schritte

[Weitere Informationen zu Visual Studio für C++](https://devblogs.microsoft.com/cppblog/getting-started-with-visual-studio-for-c-and-cpp-development/)

::: moniker-end
