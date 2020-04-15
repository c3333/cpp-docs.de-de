---
title: 'Exemplarische Vorgehensweise: Erstellen eines Standard C++-Konsolenprogramms (C++)'
ms.custom: get-started-article
ms.date: 04/25/2019
helpviewer_keywords:
- command-line applications [C++], standard
- standard applications [C++]
ms.assetid: 48217e35-d892-46b7-93e3-f6f0b7e2da35
ms.openlocfilehash: 105ac62131b45afdea2a445b5888a344f1e4d46c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370229"
---
# <a name="walkthrough-creating-a-standard-c-program-c"></a>Exemplarische Vorgehensweise: Erstellen eines Standard C++-Konsolenprogramms (C++)

Sie können Visual Studio verwenden, um Standard-C++-Programme zu erstellen. Wenn Sie die Schritte in dieser exemplarischen Vorgehensweise ausführen, können Sie ein Projekt erstellen, dem Projekt eine neue Datei hinzufügen, die Datei so ändern, dass C++-Code hinzugefügt wird, und dann das Programm mithilfe von Visual Studio kompilieren und ausführen.

Sie können ein eigenes C++-Programm eingeben oder eines der Beispielprogramme verwenden. Das Beispielprogramm in dieser exemplarischen Vorgehensweise ist eine Konsolenanwendung. Diese Anwendung `set` verwendet den Container in der C++-Standardbibliothek.

> [!NOTE]
> Wenn die Einhaltung einer bestimmten Version des C++-Sprachstandards (z. B. C++14 oder `/std:c++14` `/std:c++17` C++17) erforderlich ist, verwenden Sie die oder Compileroption. (Visual Studio 2017 und höher.)

## <a name="prerequisites"></a>Voraussetzungen

Zur Durchführung dieser exemplarischen Vorgehensweise benötigen Sie Grundkenntnisse in C++.

### <a name="to-create-a-project-and-add-a-source-file"></a>So erstellen Sie ein neues Projekt und fügen eine Quelldatei hinzu

Die folgenden Schritte variieren leicht, je nachdem, welche Version von Visual Studio Sie verwenden. Verwenden Sie das Versionsauswahlsteuerelement, um die **Version** Dokumentation für Ihre bevorzugte Version von Visual Studio anzuzeigen. Es befindet sich oben im Inhaltsverzeichnis auf dieser Seite.

::: moniker range="vs-2019"

### <a name="to-create-a-c-project-in-visual-studio-2019"></a>So erstellen Sie ein C++-Projekt in Visual Studio 2019

1. Klicken Sie im Hauptmenü auf **Datei** > **Neu** > **Projekt**, um das Dialogfeld **Neues Projekt erstellen** zu öffnen.

1. Legen Sie oben im Dialogfeld die **Sprache** auf **C++**, die **Plattform** auf **Windows** und den **Projekttyp** auf **Konsole** fest.

1. Wählen Sie aus der gefilterten Projekttypliste **Konsolen-App** aus, und klicken Sie auf **Weiter**. Geben Sie auf der nächsten Seite einen Namen für das Projekt ein, und geben Sie ggf. den Projektspeicherort an.

1. Klicken Sie auf die Schaltfläche **Erstellen**, um das Projekt zu erstellen.

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-c-project-in-visual-studio-2017"></a>So erstellen Sie ein C++-Projekt in Visual Studio 2017

1. Erstellen Sie ein Projekt, indem Sie im Menü **Datei** auf **Neu** zeigen und dann auf **Projekt**klicken.

1. Klicken Sie im Bereich **Visual C++-Projekttypen** auf **Windows Desktop**, und dann auf Windows **Console Application**.

1. Geben Sie einen Namen für das Projekt ein. Standardmäßig erhält die Lösung, in der das Projekt enthalten ist, den gleichen Namen wie das Projekt. Sie können jedoch auch einen anderen Namen eingeben. Sie können auch einen anderen Speicherort für das Projekt eingeben.

1. Klicken Sie auf **OK**, um das Projekt zu erstellen.

::: moniker-end

::: moniker range="vs-2015"

### <a name="to-create-a-c-project-in-visual-studio-2015"></a>So erstellen Sie ein C++-Projekt in Visual Studio 2015

1. Erstellen Sie ein Projekt, indem Sie im Menü **Datei** auf **Neu** zeigen und dann auf **Projekt**klicken.

1. Klicken Sie im Bereich **Visual C++-Projekttypen** auf **Windows Desktop**, und dann auf Windows **Console Application**.

1. Erweitern**Templates** > Sie im Dialogfeld **Neues Projekt** **Visual** > **C++**, und wählen Sie dann **Win32**aus. Wählen Sie im mittleren Bereich **Win32-Konsolenanwendung**aus.

1. Geben Sie einen Namen für das Projekt ein. Standardmäßig erhält die Lösung, in der das Projekt enthalten ist, den gleichen Namen wie das Projekt. Sie können jedoch auch einen anderen Namen eingeben. Sie können auch einen anderen Speicherort für das Projekt eingeben.

1. Klicken Sie auf **OK**, um das Projekt zu erstellen.

1. Schließen Sie den **Win32-Anwendungsassistenten ab.**

1. Klicken Sie auf **Weiter**, und stellen Sie sicher, dass **Konsolenanwendung** ausgewählt ist, und deaktivieren Sie das Kontrollkästchen **Vorkompilierte Kopfzeilen.**

1. Klicken Sie auf **Fertig stellen**.

::: moniker-end

## <a name="add-a-new-source-file"></a>Hinzufügen einer neuen Quelldatei

1. Wenn der **Projektmappen-Explorer** nicht angezeigt wird, klicken Sie im Menü **Ansicht** auf **Projektmappen-Explorer**.

1. Fügen Sie dem Projekt folgendermaßen eine neue Quelldatei hinzu:

   1. Klicken Sie im **Projektmappen-Explorer**mit der rechten Maustaste auf den Ordner **"Quelldateien",** zeigen Sie auf **Hinzufügen**, und klicken Sie dann auf **Neues Element**.

   1. Klicken Sie im **Codeknoten** auf **C++-Datei (.cpp),** geben Sie einen Namen für die Datei ein, und klicken Sie dann auf **Hinzufügen**.

   Die CPP-Datei wird im Ordner **"Quelldateien"** im **Projektmappen-Explorer**angezeigt, und die Datei wird im Visual Studio-Editor geöffnet.

1. Geben Sie in der Datei im Editor ein gültiges C++-Programm ein, das die C++-Standardbibliothek verwendet, oder kopieren Sie eines der Beispielprogramme, und fügen Sie es in die Datei ein.

1. Speichern Sie die Datei .

1. Klicken Sie im Menü **Build** auf **Projektmappe erstellen**.

   Im **Fenster Ausgabe** werden Informationen über den Kompilierungsfortschritt angezeigt, z. B. der Speicherort des Buildprotokolls und eine Meldung, die den Buildstatus angibt.

1. Klicken Sie im Menü **Debuggen** auf **Starten ohne Debuggen**.

   Wenn Sie das Beispielprogramm verwendet haben, wird ein Befehlsfenster angezeigt. Dieses gibt an, ob bestimmte ganze Zahlen im Set enthalten sind.

## <a name="next-steps"></a>Nächste Schritte

**Vorheriger Artikel:** [Konsolenanwendungen in Visual C++](../windows/console-applications-in-visual-cpp.md)<br/>
**Nächstes Thema:** [Exemplarische Vorgehensweise: Kompilieren eines nativen C++-Programms in der Befehlszeile](../build/walkthrough-compiling-a-native-cpp-program-on-the-command-line.md)

## <a name="see-also"></a>Siehe auch

[C++-Sprachreferenz](../cpp/cpp-language-reference.md)<br/>
[C++-Standardbibliothek](../standard-library/cpp-standard-library-reference.md)
