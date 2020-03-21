---
title: 'Exemplarische Vorgehensweise: Erstellen C++ eines StandardC++Programms ()'
ms.custom: get-started-article
ms.date: 04/25/2019
helpviewer_keywords:
- command-line applications [C++], standard
- standard applications [C++]
ms.assetid: 48217e35-d892-46b7-93e3-f6f0b7e2da35
ms.openlocfilehash: 381fa347a4ca2872ef0697d76a1e788c97e8a014
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "80075441"
---
# <a name="walkthrough-creating-a-standard-c-program-c"></a>Exemplarische Vorgehensweise: Erstellen C++ eines StandardC++Programms ()

Sie können Visual Studio verwenden, um Standard C++ Programme zu erstellen. Indem Sie die Schritte in dieser exemplarischen Vorgehensweise ausführen, können Sie ein Projekt erstellen, dem Projekt eine neue Datei hinzufügen, die Datei C++ ändern, um Code hinzuzufügen, und das Programm dann mithilfe von Visual Studio kompilieren und ausführen.

Sie können ein eigenes C++-Programm eingeben oder eines der Beispielprogramme verwenden. Das Beispielprogramm in dieser exemplarischen Vorgehensweise ist eine Konsolenanwendung. Diese Anwendung verwendet den `set`-Container in C++ der Standard Bibliothek.

> [!NOTE]
> Wenn die Kompatibilität mit einer bestimmten Version des C++ Sprachstandards (d. h. c++ 14 oder c++ 17) erforderlich ist, verwenden Sie die Compileroption `/std:c++14` oder `/std:c++17`. (Visual Studio 2017 und höher.)

## <a name="prerequisites"></a>Voraussetzungen

Zur Durchführung dieser exemplarischen Vorgehensweise benötigen Sie Grundkenntnisse in C++.

### <a name="to-create-a-project-and-add-a-source-file"></a>So erstellen Sie ein neues Projekt und fügen eine Quelldatei hinzu

Die folgenden Schritte variieren leicht, je nachdem, welche Version von Visual Studio Sie verwenden. Stellen Sie sicher, dass Sie in der Versionsauswahl links oben auf dieser Seite die richtige Version ausgewählt haben.

::: moniker range="vs-2019"

### <a name="to-create-a-c-project-in-visual-studio-2019"></a>So erstellen Sie C++ ein Projekt in Visual Studio 2019

1. Wählen Sie im Hauptmenü **Datei** > **neue** > **Projekt** aus, um das Dialogfeld **Neues Projekt erstellen** zu öffnen.

1. Legen Sie oben im Dialogfeld die **Sprache** auf **C++** , die **Plattform** auf **Windows** und den **Projekttyp** auf **Konsole** fest.

1. Wählen Sie aus der gefilterten Projekttypliste **Konsolen-App** aus, und klicken Sie auf **Weiter**. Geben Sie auf der nächsten Seite einen Namen für das Projekt ein, und geben Sie den Speicherort des Projekts an, wenn dies gewünscht ist.

1. Klicken Sie auf die Schaltfläche **Erstellen**, um das Projekt zu erstellen.

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-c-project-in-visual-studio-2017"></a>So erstellen Sie C++ ein Projekt in Visual Studio 2017

1. Erstellen Sie ein Projekt, indem Sie im Menü **Datei** auf **neu** zeigen und dann auf **Projekt**klicken.

1. Klicken Sie im Bereich **visuelle C++**  Projekttypen auf **Windows-Desktop**, und klicken Sie dann auf **Windows-Konsolenanwendung**.

1. Geben Sie einen Namen für das Projekt ein. Standardmäßig erhält die Lösung, in der das Projekt enthalten ist, den gleichen Namen wie das Projekt. Sie können jedoch auch einen anderen Namen eingeben. Sie können auch einen anderen Speicherort für das Projekt eingeben.

1. Klicken Sie auf **OK**, um das Projekt zu erstellen.

::: moniker-end

::: moniker range="vs-2015"

### <a name="to-create-a-c-project-in-visual-studio-2015"></a>So erstellen Sie C++ ein Projekt in Visual Studio 2015

1. Erstellen Sie ein Projekt, indem Sie im Menü **Datei** auf **neu** zeigen und dann auf **Projekt**klicken.

1. Klicken Sie im Bereich **visuelle C++**  Projekttypen auf **Windows-Desktop**, und klicken Sie dann auf **Windows-Konsolenanwendung**.

1. Erweitern Sie im Dialogfeld **Neues Projekt** den Eintrag **installierte** > **Vorlagen** > **Visualisierung C++** , und wählen Sie dann **Win32**aus. Wählen Sie im mittleren Bereich **Win32-Konsolenanwendung**aus.

1. Geben Sie einen Namen für das Projekt ein. Standardmäßig erhält die Lösung, in der das Projekt enthalten ist, den gleichen Namen wie das Projekt. Sie können jedoch auch einen anderen Namen eingeben. Sie können auch einen anderen Speicherort für das Projekt eingeben.

1. Klicken Sie auf **OK**, um das Projekt zu erstellen.

1. Schließen Sie den **Win32-Anwendungs-Assistenten**ab.

1. Klicken Sie auf **weiter**, und stellen Sie sicher, dass **Konsolenanwendung** ausgewählt ist, und deaktivieren Sie das Kontrollkästchen **Vorkompilierte Header** .

1. Klicken Sie auf **Fertig stellen**.

::: moniker-end

## <a name="add-a-new-source-file"></a>Neue Quelldatei hinzufügen

1. Wenn **Projektmappen-Explorer** nicht angezeigt wird, klicken Sie im Menü **Ansicht** auf **Projektmappen-Explorer**.

1. Fügen Sie dem Projekt folgendermaßen eine neue Quelldatei hinzu:

   1. Klicken Sie in **Projektmappen-Explorer**mit der rechten Maustaste auf den Ordner **Quelldateien** , zeigen Sie auf **Hinzufügen**, und klicken Sie dann auf **Neues Element**.

   1. Klicken Sie im **Code** Knoten auf  **C++ Datei (. cpp)** , geben Sie einen Namen für die Datei ein, und klicken Sie dann auf **Hinzufügen**.

   Die CPP-Datei wird im Ordner **Quelldateien** in **Projektmappen-Explorer**angezeigt, und die Datei wird im Visual Studio-Editor geöffnet.

1. Geben Sie in der-Datei im Editor ein gültiges C++ Programm ein, das C++ die Standard Bibliothek verwendet, oder kopieren Sie eines der Beispiel Programme, und fügen Sie es in die Datei ein.

1. Speichern Sie die Datei .

1. Klicken Sie im Menü **Build** auf **Projektmappe erstellen**.

   Im Fenster **Ausgabe** werden Informationen zum Kompilierungs Fortschritt angezeigt, z. b. der Speicherort des Buildprotokolls und eine Meldung, die den Buildstatus angibt.

1. Klicken Sie im Menü **Debuggen** auf **Starten ohne Debuggen**.

   Wenn Sie das Beispielprogramm verwendet haben, wird ein Befehlsfenster angezeigt. Dieses gibt an, ob bestimmte ganze Zahlen im Set enthalten sind.

## <a name="next-steps"></a>Nächste Schritte

**Vorheriges:** [Konsolen Anwendungen in C++ Visual](../windows/console-applications-in-visual-cpp.md)<br/>
**Weiter:** Exemplarische [Vorgehensweise: Kompilieren C++ eines nativen Programms in der Befehlszeile](../build/walkthrough-compiling-a-native-cpp-program-on-the-command-line.md)

## <a name="see-also"></a>Weitere Informationen

[C++-Programmiersprachenreferenz](../cpp/cpp-language-reference.md)<br/>
[C++-Standardbibliothek](../standard-library/cpp-standard-library-reference.md)
