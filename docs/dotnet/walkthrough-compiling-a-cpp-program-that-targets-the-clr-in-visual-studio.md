---
title: Kompilieren eines C++/CLI-Programms, das auf die CLR abzielt
description: Verwenden Sie Microsoft C++, um Programme und Bibliotheken zu erstellen, die systemeigenen C++-Code und .NET-Programme verbinden können.
ms.date: 04/23/2019
helpviewer_keywords:
- command-line applications [C++], managed code
- compiling programs [C++]
- Visual C++, managed code
- managed code [C++]
ms.assetid: 339f89df-a5d2-4040-831a-ddbe25b5dce4
ms.openlocfilehash: 0d661d9e77211a0e49f8695ad713b607377a236a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371808"
---
# <a name="walkthrough-compile-a-ccli-program-that-targets-the-clr-in-visual-studio"></a>Exemplarische Vorgehensweise: Kompilieren eines C++/CLI-Programms, das auf die CLR in Visual Studio abzielt

Mithilfe von C++/CLI können Sie C++-Programme erstellen, die auch .NET-Klassen sowie systemeigene C++-Typen verwenden. C++/CLI ist für die Verwendung in Konsolenanwendungen und in DLLs vorgesehen, die systemeigenen C++-Code umschließen und über .NET-Programme zugänglich machen. Um eine Windows-Benutzeroberfläche basierend auf .NET zu erstellen, verwenden Sie C- oder Visual Basic.

Für dieses Verfahren können Sie Ein eigenes C++-Programm eingeben oder eines der Beispielprogramme verwenden. Das Beispielprogramm, das für diese Vorgehensweise verwendet wird, erstellt eine Textdatei namens „textfile.txt“, die im Projektverzeichnis gespeichert wird.

## <a name="prerequisites"></a>Voraussetzungen

- Grundlegende Kenntnisse der Programmiersprache C++.
- In Visual Studio 2017 und höher ist die C++/CLI-Unterstützung eine optionale Komponente. Um es zu installieren, öffnen Sie Visual **Studio Installer** im Windows-Startmenü. Stellen Sie sicher, dass die **Desktopentwicklung mit C++-Kachel** aktiviert ist, und überprüfen Sie im Abschnitt **Optionale** Komponenten auch **C++/CLI-Unterstützung**.

## <a name="create-a-new-project"></a>Erstellen eines neuen Projekts

Die folgenden Schritte variieren leicht, je nachdem, welche Version von Visual Studio Sie verwenden. Verwenden Sie das Versionsauswahlsteuerelement, um die **Version** Dokumentation für Ihre bevorzugte Version von Visual Studio anzuzeigen. Es befindet sich oben im Inhaltsverzeichnis auf dieser Seite.

::: moniker range="vs-2019"

### <a name="to-create-a-ccli-project-in-visual-studio-2019"></a>So erstellen Sie ein C++/CLI-Projekt in Visual Studio 2019

1. Klicken Sie im **Projektmappen-Explorer**mit der rechten Maustaste nach oben, um das Dialogfeld **Neues Projekt erstellen** zu öffnen.

1. Geben Sie oben im Dialogfeld **CLR** in das Suchfeld ein, und wählen Sie dann **CLR Empty Project** aus der Ergebnisliste aus.

1. Klicken Sie auf die Schaltfläche **Erstellen**, um das Projekt zu erstellen.

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-ccli-project-in-visual-studio-2017"></a>So erstellen Sie ein C++/CLI-Projekt in Visual Studio 2017

1. Erstellen Sie ein neues Projekt. Zeigen Sie im Menü **Datei** auf **Neu**, und klicken Sie dann auf **Projekt**.

1. Klicken Sie in den Visual C++-Projekttypen auf **CLR**, und klicken Sie dann auf **leeres CLR-Projekt**.

1. Geben Sie einen Projektnamen ein. Standardmäßig erhält die Projektmappe, in der das Projekt enthalten ist, den gleichen Namen wie das neue Projekt. Sie können jedoch auch einen anderen Namen eingeben. Wenn Sie möchten, können Sie auch einen anderen Speicherort für das Projekt angeben.

1. Klicken Sie auf **OK**, um das neue Projekt zu erstellen.

::: moniker-end

::: moniker range="vs-2015"

### <a name="to-create-a-ccli-project-in-visual-studio-2015"></a>So erstellen Sie ein C++/CLI-Projekt in Visual Studio 2015

1. Erstellen Sie ein neues Projekt. Zeigen Sie im Menü **Datei** auf **Neu**, und klicken Sie dann auf **Projekt**.

1. Klicken Sie in den Visual C++-Projekttypen auf **CLR**, und klicken Sie dann auf **leeres CLR-Projekt**.

1. Geben Sie einen Projektnamen ein. Standardmäßig erhält die Projektmappe, in der das Projekt enthalten ist, den gleichen Namen wie das neue Projekt. Sie können jedoch auch einen anderen Namen eingeben. Wenn Sie möchten, können Sie auch einen anderen Speicherort für das Projekt angeben.

1. Klicken Sie auf **OK**, um das neue Projekt zu erstellen.

::: moniker-end

## <a name="add-a-source-file"></a>Hinzufügen einer Quelldatei

1. Wenn der **Projektmappen-Explorer** nicht angezeigt wird, klicken Sie im Menü **Ansicht** auf **Projektmappen-Explorer**.

1. Fügen Sie dem Projekt eine neue Quelldatei hinzu:

   - Klicken Sie mit der rechten Maustaste auf den Ordner **Quelldateien** im **Projektmappen-Explorer**, zeigen Sie auf **Hinzufügen**, und klicken Sie auf **Neues Element**.

   - Klicken Sie auf **C++-Datei (.cpp)**, geben Sie einen Dateinamen ein, und klicken Sie dann auf **Hinzufügen**.

   Die **CPP-Datei** wird im Ordner **"Quelldateien"** im **Projektmappen-Explorer** angezeigt, und ein Registerkartenfenster wird angezeigt, in dem Sie den gewünschten Code in diese Datei eingeben.

1. Klicken Sie in Visual Studio in die neu erstellte Registerkarte, und geben Sie ein gültiges Visual C++-Programm ein, oder kopieren Sie eines der Beispielprogramme und fügen es ein.

   Sie können beispielsweise das Beispielprogramm [How to: Write a Text File (C++/CLI) (Vorgehensweise: Schreiben einer Textdatei (C++/CLI))](how-to-write-a-text-file-cpp-cli.md) verwenden (im Knoten **Dateibehandlung und E/A** des Programmierhandbuchs).

   Beachten Sie, wenn Sie das Beispielprogramm verwenden, dass Sie das Schlüsselwort `gcnew` anstelle von `new` beim Erstellen eines .NET-Objekts verwenden, und dass `gcnew` ein Handle (`^`) anstelle eines Pointers (`*`) zurückgibt:

   `StreamWriter^ sw = gcnew StreamWriter(fileName);`

   Weitere Informationen zur C++/CLI-Syntax finden Sie unter [Komponentenerweiterungen für Laufzeitplattformen](../extensions/component-extensions-for-runtime-platforms.md).

1. Klicken Sie im Menü **Build** auf **Projektmappe erstellen**.

   Im **Ausgabefenster** werden Informationen zum Kompilierungsprozess angezeigt, z.B. der Speicherort des Buildprotokolls und eine Meldung über den Buildstatus.

   Wenn Sie Änderungen vornehmen und das Programm ausführen, ohne einen Buildvorgang auszuführen, gibt ein Dialogfeld möglicherweise an, dass das Projekt nicht mehr aktuell ist. Aktivieren Sie in diesem Dialogfeld das Kontrollkästchen, bevor Sie auf **OK** klicken, wenn Sie möchten, dass Visual Studio immer die aktuellen Versionen von Dateien verwendet, anstatt Sie jedes zur Eingabe aufzufordern, wenn die Anwendung erstellt wird.

1. Klicken Sie im Menü **Debuggen** auf **Starten ohne Debuggen**.

1. Wenn Sie das Beispielprogramm verwendet haben und das Programm ausführen, wird ein Befehlsfenster angezeigt, das angibt, dass die Textdatei erstellt wurde.

   Die Textdatei **textfile.txt** befindet sich nun in Ihrem Projektverzeichnis. Sie können diese Datei mit dem Editor öffnen.

   > [!NOTE]
   > Durch Auswählen der leeren CLR-Projektvorlage wird automatisch die Compileroption `/clr` festgelegt. Klicken Sie zum Überprüfen mit der rechten Maustaste auf das Projekt im **Projektmappen-Explorer**, klicken Sie auf **Eigenschaften**, und überprüfen Sie dann die Option **Common Language Runtime-Unterstützung** im Knoten **Allgemein** der **Konfigurationseigenschaften**.

## <a name="see-also"></a>Siehe auch

[C++-Sprachreferenz](../cpp/cpp-language-reference.md)<br/>
[Projekte und Buildsysteme](../build/projects-and-build-systems-cpp.md)<br/>
