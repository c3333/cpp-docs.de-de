---
title: 'Exemplarische Vorgehensweise: Erstellen einer agentbasierten Anwendung'
ms.date: 04/25/2019
helpviewer_keywords:
- asynchronous agents, creating
- agent class, example
ms.assetid: 730f42ce-6d58-4753-b948-fd9c9ef2ce6c
ms.openlocfilehash: 20197786e3d3c2d34d29af748c1cc073902cf70d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377459"
---
# <a name="walkthrough-creating-an-agent-based-application"></a>Exemplarische Vorgehensweise: Erstellen einer agentbasierten Anwendung

In diesem Thema wird die Erstellung einer einfachen agentbasierten Anwendung beschrieben. In dieser exemplarischen Vorgehensweise können Sie einen Agent erstellen, der Daten asynchron aus einer Textdatei ausliest. Die Anwendung berechnet die Prüfsumme des Inhalts dieser Datei mithilfe des Adler-32-Prüfsummenalgorithmus.

## <a name="prerequisites"></a>Voraussetzungen

Zum Durchführen dieser exemplarischen Vorgehensweise sollten Sie die folgenden Themen lesen:

- [Asynchrone Agenten](../../parallel/concrt/asynchronous-agents.md)

- [Asynchrone Nachrichtenblöcke](../../parallel/concrt/asynchronous-message-blocks.md)

- [Message Passing-Funktionen](../../parallel/concrt/message-passing-functions.md)

- [Synchronisierungsdatenstrukturen](../../parallel/concrt/synchronization-data-structures.md)

## <a name="sections"></a><a name="top"></a>Bereichen

Mit dieser exemplarischen Vorgehensweise wird die Durchführung der folgenden Aufgaben beschrieben:

- [Erstellen der Konsolenanwendung](#createapplication)

- [Erstellen der file_reader-Klasse](#createagentclass)

- [Verwenden der file_reader-Klasse in der Anwendung](#useagentclass)

## <a name="creating-the-console-application"></a><a name="createapplication"></a>Erstellen der Konsolenanwendung

In diesem Abschnitt wird gezeigt, wie Sie eine C++-Konsolenanwendung erstellen, die auf die Headerdateien verweist, die das Programm verwenden wird. Die ersten Schritte variieren je nachdem, welche Version von Visual Studio Sie verwenden. Verwenden Sie das Versionsauswahlsteuerelement, um die **Version** Dokumentation für Ihre bevorzugte Version von Visual Studio anzuzeigen. Es befindet sich oben im Inhaltsverzeichnis auf dieser Seite.

::: moniker range="vs-2019"

### <a name="to-create-a-c-console-application-in-visual-studio-2019"></a>So erstellen Sie eine C++-Konsolenanwendung in Visual Studio 2019

1. Klicken Sie im Hauptmenü auf **Datei** > **Neu** > **Projekt**, um das Dialogfeld **Neues Projekt erstellen** zu öffnen.

1. Legen Sie oben im Dialogfeld die **Sprache** auf **C++**, die **Plattform** auf **Windows** und den **Projekttyp** auf **Konsole** fest.

1. Wählen Sie aus der gefilterten Projekttypliste **Konsolen-App** aus, und klicken Sie auf **Weiter**. Geben Sie auf `BasicAgent` der nächsten Seite den Namen für das Projekt ein, und geben Sie ggf. den Projektspeicherort an.

1. Klicken Sie auf die Schaltfläche **Erstellen**, um das Projekt zu erstellen.

1. Klicken Sie im **Projektmappen-Explorer**mit der rechten Maustaste auf den Projektknoten , und wählen Sie **Eigenschaften**aus. Wählen Sie unter **Konfigurationseigenschaften** > **C/C++** > **Vorkompilierte Header** > **vorkompilierte Header** die Option **Erstellen**aus.

::: moniker-end

::: moniker range="<=vs-2017"

### <a name="to-create-a-c-console-application-in-visual-studio-2017-and-earlier"></a>So erstellen Sie eine C++-Konsolenanwendung in Visual Studio 2017 und früher

1. Klicken Sie im Menü **Datei** auf **Neu**, und klicken Sie dann auf **Projekt,** um das Dialogfeld **Neues Projekt** anzuzeigen.

1. Wählen Sie im Dialogfeld **Neues Projekt** den **Visual C++-Knoten** im Bereich **Projekttypen** aus, und wählen Sie dann **Win32-Konsolenanwendung** im Bereich **Vorlagen** aus. Geben Sie einen Namen für `BasicAgent`das Projekt ein, z. B. , und klicken Sie dann auf **OK,** um den **Win32 Console Application Wizard**anzuzeigen.

1. Klicken Sie im Dialogfeld **Win32 Console Application Wizard** auf **Fertig stellen**.

::: moniker-end

1. Fügen Sie in *pch.h* (*stdafx.h* in Visual Studio 2017 und früher) den folgenden Code hinzu:

[!code-cpp[concrt-basic-agent#1](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_1.h)]

   Die Headerdatei agents.h enthält die Funktionalität der [concurrency::agent-Klasse.](../../parallel/concrt/reference/agent-class.md)

1. Überprüfen Sie, ob die Anwendung erfolgreich erstellt wurde, indem Sie sie erstellen und ausführen. Um die Anwendung zu erstellen, klicken Sie im Menü **Build** auf **Lösung erstellen**. Wenn die Anwendung erfolgreich erstellt wird, führen Sie die Anwendung aus, indem Sie **im** Menü Debuggen starten im **Menü Debuggen** klicken.

[[Oben](#top)]

## <a name="creating-the-file_reader-class"></a><a name="createagentclass"></a>Erstellen der file_reader-Klasse

In diesem Abschnitt wird die Erstellung der `file_reader`-Klasse beschrieben. Die Runtime plant jeden Agent so, dass er Arbeiten im eigenen Kontext ausführt. Daher können Sie einen Agent erstellen, der Arbeiten synchron ausführt, aber asynchron mit anderen Komponenten interagiert. Die `file_reader`-Klasse liest Daten aus einer angegebenen Eingabedatei aus und sendet Daten aus dieser Datei an eine angegebene Zielkomponente.

#### <a name="to-create-the-file_reader-class"></a>So erstellen Sie die file_reader-Klasse

1. Fügen Sie dem Projekt eine neue C++-Headerdatei hinzu. Klicken Sie dazu mit der rechten Maustaste auf den Knoten **Headerdateien** im **Projektmappen-Explorer**, klicken Sie auf **Hinzufügen**, und klicken Sie dann auf **Neues Element**. Wählen Sie im Bereich **Vorlagen** die Option **HeaderDatei (.h)** aus. Geben **Add New Item** Sie `file_reader.h` im Dialogfeld Neues Element hinzufügen in das Feld **Name** ein, und klicken Sie dann auf **Hinzufügen**.

1. Fügen Sie in der Datei file_reader.h den folgenden Code hinzu.

[!code-cpp[concrt-basic-agent#17](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_2.h)]

1. Erstellen Sie in der Datei file_reader.h eine Klasse mit dem Namen `file_reader`, die von `agent` abgeleitet wird.

[!code-cpp[concrt-basic-agent#2](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_3.h)]

1. Fügen Sie dem `private`-Abschnitt der Klasse die folgenden Datenmember hinzu.

[!code-cpp[concrt-basic-agent#3](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_4.h)]

   Der `_file_name`-Member ist der Name der Datei, die vom Agent ausgelesen wird. Das `_target` Member ist ein [concurrency::ITarget-Objekt,](../../parallel/concrt/reference/itarget-class.md) in das der Agent den Inhalt der Datei schreibt. Der `_error`-Member speichert alle Fehler, die während der Lebensdauer des Agents auftreten.

1. Fügen Sie dem `file_reader`-Abschnitt der  `public`-Klasse den folgenden Code für die `file_reader`-Konstruktoren hinzu.

[!code-cpp[concrt-basic-agent#4](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_5.h)]

   Mit jeder Konstruktorüberladung werden die `file_reader`-Datenmember festgelegt. Mit der zweiten und dritten Konstruktorüberladung wird es der Anwendung ermöglicht, mit dem Agent einen bestimmten Planer zu verwenden. Bei der ersten Überladung wird der Standardplaner mit dem Agent verwendet.

1. Fügen Sie dem public-Abschnitt der `get_error`-Klasse die `file_reader`-Methode hinzu.

[!code-cpp[concrt-basic-agent#5](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_6.h)]

   Die `get_error`-Methode ruft alle Fehler ab, die während der Lebensdauer des Agents auftreten.

1. Implementieren Sie die [parallelität::agent::run-Methode](reference/agent-class.md#run) im `protected` Abschnitt Ihrer Klasse.

[!code-cpp[concrt-basic-agent#6](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_7.h)]

Die `run`-Methode öffnet die Datei und liest Daten aus. Die `run`-Methode erfasst mithilfe der Ausnahmebehandlung alle Fehler, die während der Dateiverarbeitung auftreten.

   Jedes Mal, wenn diese Methode Daten aus der Datei liest, ruft sie die [concurrency::asend-Funktion](reference/concurrency-namespace-functions.md#asend) auf, um diese Daten an den Zielpuffer zu senden. Sie sendet die leere Zeichenfolge an den Zielpuffer, um so das Ende der Verarbeitung anzugeben.

Im folgenden Beispiel wird der vollständige Inhalt der Datei file_reader.h dargestellt.

[!code-cpp[concrt-basic-agent#7](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_8.h)]

[[Oben](#top)]

## <a name="using-the-file_reader-class-in-the-application"></a><a name="useagentclass"></a>Verwenden der file_reader-Klasse in der Anwendung

In diesem Abschnitt wird beschrieben, wie mithilfe der `file_reader`-Klasse der Inhalt einer Textdatei gelesen wird. Außerdem wird gezeigt, wie ein [concurrency::call-Objekt](../../parallel/concrt/reference/call-class.md) erstellt wird, das diese Dateidaten empfängt und die Adler-32-Prüfsumme berechnet.

#### <a name="to-use-the-file_reader-class-in-your-application"></a>So verwenden Sie die file_reader-Klasse in der Anwendung

1. Fügen Sie in der Datei BasicAgent.cpp die folgende `#include`-Anweisung hinzu.

[!code-cpp[concrt-basic-agent#8](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_9.cpp)]

1. Fügen Sie in der Datei BasicAgent.cpp die folgenden `using`-Anweisungen hinzu.

[!code-cpp[concrt-basic-agent#9](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_10.cpp)]

1. Erstellen `_tmain` Sie in der Funktion ein [concurrency::event-Objekt,](../../parallel/concrt/reference/event-class.md) das das Ende der Verarbeitung signalisiert.

[!code-cpp[concrt-basic-agent#10](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_11.cpp)]

1. Erstellen Sie ein `call`-Objekt, das beim Empfang von Daten die Prüfsumme aktualisiert.

[!code-cpp[concrt-basic-agent#11](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_12.cpp)]

   Dieses `call`-Objekt legt darüber hinaus auch das `event`-Objekt fest, wenn es die leere Zeichenfolge empfängt, um das Ende der Verarbeitung zu signalisieren.

1. Erstellen Sie ein `file_reader`-Objekt, das aus der Datei test.txt ausliest und den Inhalt dieser Datei in das `call`-Objekt schreibt.

[!code-cpp[concrt-basic-agent#12](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_13.cpp)]

1. Starten Sie den Agent, und warten Sie, bis er beendet wird.

[!code-cpp[concrt-basic-agent#13](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_14.cpp)]

1. Warten Sie, bis das `call`-Objekt alle Daten empfangen hat, beenden Sie den Agent.

[!code-cpp[concrt-basic-agent#14](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_15.cpp)]

1. Überprüfen Sie die file_reader-Klasse auf Fehler. Wenn kein Fehler aufgetreten ist, berechnen Sie die abschließende Adler-32-Prüfsumme, und geben Sie die Summe an der Konsole aus.

[!code-cpp[concrt-basic-agent#15](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_16.cpp)]

Das folgende Beispiel zeigt die vollständige BasicAgent.cpp-Datei.

[!code-cpp[concrt-basic-agent#16](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_17.cpp)]

[[Oben](#top)]

## <a name="sample-input"></a>Beispieleingabe

Dies ist der Beispielinhalt der Eingabedatei text.txt:

```Output
The quick brown fox
jumps
over the lazy dog
```

## <a name="sample-output"></a>Beispielausgabe

Wenn dieses Programm mit der Beispieleingabe verwendet wird, generiert es die folgende Ausgabe:

```Output
Adler-32 sum is fefb0d75
```

## <a name="robust-programming"></a>Stabile Programmierung

Um gleichzeitigen Zugriff auf Datenmember zu verhindern, wird empfohlen, Methoden hinzufügen, die Arbeiten am `protected`-Abschnitt oder am `private`-Abschnitt der Klasse durchführen. Fügen Sie dem `public`-Abschnitt der Klasse nur Methoden hinzu, die Nachrichten an den Agent senden oder vom Agent empfangen.

Rufen Sie immer die [parallel::agent::done-Methode](reference/agent-class.md#done) auf, um den Agenten in den abgeschlossenen Zustand zu verschieben. Diese Methode wird in der Regel vor der Rückkehr von der `run`-Methode aufgerufen.

## <a name="next-steps"></a>Nächste Schritte

Ein weiteres Beispiel für eine Agenten-basierte Anwendung finden Sie unter [Exemplarische Vorgehensweise: Verwenden von Join to Prevent Deadlock](../../parallel/concrt/walkthrough-using-join-to-prevent-deadlock.md).

## <a name="see-also"></a>Siehe auch

[Asynchronous Agents Library](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[Asynchrone Nachrichtenblöcke](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Message Passing-Funktionen](../../parallel/concrt/message-passing-functions.md)<br/>
[Synchronisierungsdatenstrukturen](../../parallel/concrt/synchronization-data-structures.md)<br/>
[Exemplarische Vorgehensweise: Verhindern von Deadlocks mit join](../../parallel/concrt/walkthrough-using-join-to-prevent-deadlock.md)
