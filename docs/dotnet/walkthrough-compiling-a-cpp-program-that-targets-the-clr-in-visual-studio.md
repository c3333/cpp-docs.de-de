---
title: Kompilieren eines C++/CLI-Programms, das die CLR als Ziel hat
description: Verwenden Sie C++ Microsoft zum Erstellen von Programmen und Bibliotheken, die C++ systemeigenen Code und .net-Programme verbinden können.
ms.date: 04/23/2019
helpviewer_keywords:
- command-line applications [C++], managed code
- compiling programs [C++]
- Visual C++, managed code
- managed code [C++]
ms.assetid: 339f89df-a5d2-4040-831a-ddbe25b5dce4
ms.openlocfilehash: 36c41856dfcdb5c5f50ba59205b4c73c5fde5963
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "80080020"
---
# <a name="walkthrough-compile-a-ccli-program-that-targets-the-clr-in-visual-studio"></a>Exemplarische Vorgehensweise: C++Kompilieren eines/CLI-Programms für die CLR in Visual Studio

Mithilfe C++von/CLI können Sie Programme C++ erstellen, die .NET-Klassen und systemeigene C++ Typen verwenden. C++/CLI ist für die Verwendung in Konsolen Anwendungen und DLLs vorgesehen, die System C++ eigenen Code einbinden und über .net-Programme zugänglich machen. Verwenden C# Sie zum Erstellen einer Windows-Benutzeroberfläche, die auf .NET basiert, oder Visual Basic.

Für dieses Verfahren können Sie ein eigenes C++ Programm eingeben oder eines der Beispiel Programme verwenden. Das Beispielprogramm, das für diese Vorgehensweise verwendet wird, erstellt eine Textdatei namens „textfile.txt“, die im Projektverzeichnis gespeichert wird.

## <a name="prerequisites"></a>Voraussetzungen

- Grundlegende Kenntnisse der Programmiersprache C++.
- In Visual Studio 2017 und höher ist C++die/CLI-Unterstützung eine optionale Komponente. Öffnen Sie die **Visual Studio-Installer** über das Windows-Startmenü, um Sie zu installieren. Stellen Sie sicher, dass die **Desktop C++ Entwicklung mit** der Kachel aktiviert ist, und aktivieren Sie **Optional**  **C++** im Abschnitt optionale Komponenten auch/CLI-Unterstützung.

## <a name="create-a-new-project"></a>Erstellen eines neuen Projekts

Die folgenden Schritte variieren leicht, je nachdem, welche Version von Visual Studio Sie verwenden. Stellen Sie sicher, dass Sie in der Versionsauswahl links oben auf dieser Seite die richtige Version ausgewählt haben.

::: moniker range="vs-2019"

### <a name="to-create-a-ccli-project-in-visual-studio-2019"></a>So erstellen Sie C++ein/CLI-Projekt in Visual Studio 2019

1. Klicken Sie in **Projektmappen-Explorer**mit der rechten Maustaste auf den oberen Rand, um das Dialogfeld **Neues Projekt erstellen** zu öffnen.

1. Geben Sie im oberen Bereich des Dialog Felds **CLR** in das Suchfeld ein, und wählen Sie dann **leeres CLR-Projekt** aus der Ergebnisliste aus.

1. Klicken Sie auf die Schaltfläche **Erstellen**, um das Projekt zu erstellen.

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-ccli-project-in-visual-studio-2017"></a>So erstellen Sie C++ein/CLI-Projekt in Visual Studio 2017

1. Erstellen Sie ein neues Projekt. Zeigen Sie im Menü **Datei** auf **Neu**, und klicken Sie dann auf **Projekt**.

1. Klicken Sie in den Visual C++-Projekttypen auf **CLR**, und klicken Sie dann auf **leeres CLR-Projekt**.

1. Geben Sie einen Projektnamen ein. Standardmäßig erhält die Projektmappe, in der das Projekt enthalten ist, den gleichen Namen wie das neue Projekt. Sie können jedoch auch einen anderen Namen eingeben. Wenn Sie möchten, können Sie auch einen anderen Speicherort für das Projekt angeben.

1. Klicken Sie auf **OK**, um das neue Projekt zu erstellen.

::: moniker-end

::: moniker range="vs-2015"

### <a name="to-create-a-ccli-project-in-visual-studio-2015"></a>So erstellen Sie C++ein/CLI-Projekt in Visual Studio 2015

1. Erstellen Sie ein neues Projekt. Zeigen Sie im Menü **Datei** auf **Neu**, und klicken Sie dann auf **Projekt**.

1. Klicken Sie in den Visual C++-Projekttypen auf **CLR**, und klicken Sie dann auf **leeres CLR-Projekt**.

1. Geben Sie einen Projektnamen ein. Standardmäßig erhält die Projektmappe, in der das Projekt enthalten ist, den gleichen Namen wie das neue Projekt. Sie können jedoch auch einen anderen Namen eingeben. Wenn Sie möchten, können Sie auch einen anderen Speicherort für das Projekt angeben.

1. Klicken Sie auf **OK**, um das neue Projekt zu erstellen.

::: moniker-end

## <a name="add-a-source-file"></a>Hinzufügen einer Quelldatei

1. Wenn der **Projektmappen-Explorer** nicht angezeigt wird, klicken Sie im Menü **Ansicht** auf **Projektmappen-Explorer**.

1. Fügen Sie dem Projekt eine neue Quelldatei hinzu:

   - Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf den Ordner **Quelldateien**, zeigen Sie auf **Hinzufügen**, und klicken Sie dann auf **Neues Element**.

   - Klicken Sie auf **C++-Datei (.cpp)** , geben Sie einen Dateinamen ein, und klicken Sie dann auf **Hinzufügen**.

   Die **CPP**-Datei wird im Ordner **Quelldateien** im **Projektmappen-Explorer** angezeigt. Au0erdem wird ein Fenster im Registerkartenformat angezeigt, in dem Sie den Code eingeben können, den Sie in diese Datei einfügen möchten.

1. Klicken Sie in Visual Studio in die neu erstellte Registerkarte, und geben Sie ein gültiges Visual C++-Programm ein, oder kopieren Sie eines der Beispielprogramme und fügen es ein.

   Sie können beispielsweise das Beispielprogramm [How to: Write a Text File (C++/CLI) (Vorgehensweise: Schreiben einer Textdatei (C++/CLI))](how-to-write-a-text-file-cpp-cli.md) verwenden (im Knoten **Dateibehandlung und E/A** des Programmierhandbuchs).

   Beachten Sie, wenn Sie das Beispielprogramm verwenden, dass Sie das Schlüsselwort `gcnew` anstelle von `new` beim Erstellen eines .NET-Objekts verwenden, und dass `gcnew` ein Handle (`^`) anstelle eines Pointers (`*`) zurückgibt:

   `StreamWriter^ sw = gcnew StreamWriter(fileName);`

   Weitere Informationen zur C++/CLI-Syntax finden Sie unter [Komponenten Erweiterungen für laufzeitplattformen](../extensions/component-extensions-for-runtime-platforms.md).

1. Klicken Sie im Menü **Build** auf **Projektmappe erstellen**.

   Im **Ausgabefenster** werden Informationen zum Kompilierungsprozess angezeigt, z.B. der Speicherort des Buildprotokolls und eine Meldung über den Buildstatus.

   Wenn Sie Änderungen vornehmen und das Programm ausführen, ohne einen Buildvorgang auszuführen, gibt ein Dialogfeld möglicherweise an, dass das Projekt nicht mehr aktuell ist. Aktivieren Sie in diesem Dialogfeld das Kontrollkästchen, bevor Sie auf **OK** klicken, wenn Sie möchten, dass Visual Studio immer die aktuellen Versionen von Dateien verwendet, anstatt Sie jedes zur Eingabe aufzufordern, wenn die Anwendung erstellt wird.

1. Klicken Sie im Menü **Debuggen** auf **Starten ohne Debuggen**.

1. Wenn Sie das Beispielprogramm verwendet haben und das Programm ausführen, wird ein Befehlsfenster angezeigt, das angibt, dass die Textdatei erstellt wurde.

   Die Textdatei **textfile.txt** befindet sich nun in Ihrem Projektverzeichnis. Sie können diese Datei mit dem Editor öffnen.

   > [!NOTE]
   > Durch Auswählen der leeren CLR-Projektvorlage wird automatisch die Compileroption `/clr` festgelegt. Klicken Sie zum Überprüfen mit der rechten Maustaste auf das Projekt im **Projektmappen-Explorer**, klicken Sie auf **Eigenschaften**, und überprüfen Sie dann die Option **Common Language Runtime-Unterstützung** im Knoten **Allgemein** der **Konfigurationseigenschaften**.

## <a name="see-also"></a>Weitere Informationen

[C++-Programmiersprachenreferenz](../cpp/cpp-language-reference.md)<br/>
[Projekte und Buildsysteme](../build/projects-and-build-systems-cpp.md)<br/>
