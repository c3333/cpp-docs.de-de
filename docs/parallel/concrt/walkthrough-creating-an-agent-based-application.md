---
title: 'Exemplarische Vorgehensweise: Erstellen einer agentbasierten Anwendung'
ms.date: 04/25/2019
helpviewer_keywords:
- asynchronous agents, creating
- agent class, example
ms.assetid: 730f42ce-6d58-4753-b948-fd9c9ef2ce6c
ms.openlocfilehash: 4e67b3fc3363955ae02973847912c021eca95ded
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219481"
---
# <a name="walkthrough-creating-an-agent-based-application"></a>Exemplarische Vorgehensweise: Erstellen einer agentbasierten Anwendung

In diesem Thema wird die Erstellung einer einfachen agentbasierten Anwendung beschrieben. In dieser exemplarischen Vorgehensweise können Sie einen Agent erstellen, der Daten asynchron aus einer Textdatei ausliest. Die Anwendung berechnet die Prüfsumme des Inhalts dieser Datei mithilfe des Adler-32-Prüfsummenalgorithmus.

## <a name="prerequisites"></a>Voraussetzungen

Zum Durchführen dieser exemplarischen Vorgehensweise sollten Sie die folgenden Themen lesen:

- [Asynchrone Agents](../../parallel/concrt/asynchronous-agents.md)

- [Asynchrone Nachrichten Blöcke](../../parallel/concrt/asynchronous-message-blocks.md)

- [Nachrichten Übergabe Funktionen](../../parallel/concrt/message-passing-functions.md)

- [Synchronisierungs Datenstrukturen](../../parallel/concrt/synchronization-data-structures.md)

## <a name="sections"></a><a name="top"></a>Strecken

Mit dieser exemplarischen Vorgehensweise wird die Durchführung der folgenden Aufgaben beschrieben:

- [Erstellen der Konsolenanwendung](#createapplication)

- [Erstellen der file_reader-Klasse](#createagentclass)

- [Verwenden der file_reader-Klasse in der Anwendung](#useagentclass)

## <a name="creating-the-console-application"></a><a name="createapplication"></a>Erstellen der Konsolenanwendung

In diesem Abschnitt wird gezeigt, wie eine C++-Konsolenanwendung erstellt wird, die auf die vom Programm verwendeten Header Dateien verweist. Die ersten Schritte sind abhängig von der verwendeten Version von Visual Studio. Um die Dokumentation für Ihre bevorzugte Version von Visual Studio anzuzeigen, verwenden Sie das Auswahlsteuerelement **Version**. Es befindet sich am Anfang des Inhaltsverzeichnisses auf dieser Seite.

::: moniker range="vs-2019"

### <a name="to-create-a-c-console-application-in-visual-studio-2019"></a>So erstellen Sie eine C++-Konsolenanwendung in Visual Studio 2019

1. Klicken Sie im Hauptmenü auf **Datei** > **Neu** > **Projekt**, um das Dialogfeld **Neues Projekt erstellen** zu öffnen.

1. Legen Sie oben im Dialogfeld die **Sprache** auf **C++** , die **Plattform** auf **Windows** und den **Projekttyp** auf **Konsole** fest.

1. Wählen Sie aus der gefilterten Projekttypliste **Konsolen-App** aus, und klicken Sie auf **Weiter**. Geben Sie auf der nächsten Seite `BasicAgent` als Namen für das Projekt ein, und geben Sie den Speicherort des Projekts an, wenn gewünscht.

1. Klicken Sie auf die Schaltfläche **Erstellen**, um das Projekt zu erstellen.

1. Klicken Sie in **Projektmappen-Explorer**mit der rechten Maustaste auf den Projekt Knoten, und wählen Sie **Eigenschaften**aus. Wählen Sie unter **Konfigurations Eigenschaften**  >  **C/C++** vorkompilierte Header für  >  **vorkompilierte**  >  **Precompiled header** **Create**Header die Option erstellen aus.

::: moniker-end

::: moniker range="<=vs-2017"

### <a name="to-create-a-c-console-application-in-visual-studio-2017-and-earlier"></a>So erstellen Sie eine C++-Konsolenanwendung in Visual Studio 2017 und früher

1. Klicken Sie im Menü **Datei** auf **neu**, und klicken Sie dann auf **Projekt** , um das Dialogfeld **Neues Projekt** anzuzeigen.

1. Wählen Sie im Dialogfeld **Neues Projekt** im Bereich **Projekttypen** den Knoten **Visual C++** aus, und wählen Sie dann im Bereich **Vorlagen** die Option **Win32-Konsolenanwendung** aus. Geben Sie einen Namen für das Projekt ein, z. b `BasicAgent` ., und klicken Sie dann auf **OK** , um den Assistenten für die **Win32-Konsolenanwendung**anzuzeigen.

1. Klicken Sie im Dialogfeld **Assistent für Win32-Konsolen Anwendungen** auf **Fertig**stellen.

::: moniker-end

1. Fügen Sie in " *PCH. h* " (*stdafx. h* in Visual Studio 2017 und früher) den folgenden Code hinzu:

[!code-cpp[concrt-basic-agent#1](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_1.h)]

   Die Header Datei "Agents. h" enthält die Funktionalität der " [parallelcurrency:: Agent](../../parallel/concrt/reference/agent-class.md) "-Klasse.

1. Überprüfen Sie, ob die Anwendung erfolgreich erstellt wurde, indem Sie sie erstellen und ausführen. Klicken Sie im Menü **Erstellen** auf Projekt Mappe **Erstellen**, um die Anwendung zu erstellen. Wenn die Anwendung erfolgreich erstellt wird, führen Sie die Anwendung aus, indem Sie im Menü **Debuggen** auf **Debugging starten** klicken.

[Nach[oben](#top)]

## <a name="creating-the-file_reader-class"></a><a name="createagentclass"></a>Erstellen der file_reader-Klasse

In diesem Abschnitt wird die Erstellung der `file_reader`-Klasse beschrieben. Die Runtime plant jeden Agent so, dass er Arbeiten im eigenen Kontext ausführt. Daher können Sie einen Agent erstellen, der Arbeiten synchron ausführt, aber asynchron mit anderen Komponenten interagiert. Die `file_reader`-Klasse liest Daten aus einer angegebenen Eingabedatei aus und sendet Daten aus dieser Datei an eine angegebene Zielkomponente.

#### <a name="to-create-the-file_reader-class"></a>So erstellen Sie die file_reader-Klasse

1. Fügen Sie dem Projekt eine neue C++-Headerdatei hinzu. Klicken Sie hierzu in **Projektmappen-Explorer**mit der rechten Maustaste auf den Knoten **Header Dateien** , klicken Sie auf **Hinzufügen**, und klicken Sie dann auf **Neues Element**. Wählen Sie im Bereich **Vorlagen** die Option **Header Datei (. h)** aus. Geben Sie im Dialogfeld **Neues Element hinzufügen** `file_reader.h` im Feld **Name den Namen** ein, und klicken Sie dann auf **Hinzufügen**.

1. Fügen Sie in der Datei file_reader.h den folgenden Code hinzu.

[!code-cpp[concrt-basic-agent#17](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_2.h)]

1. Erstellen Sie in der Datei file_reader.h eine Klasse mit dem Namen `file_reader`, die von `agent` abgeleitet wird.

[!code-cpp[concrt-basic-agent#2](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_3.h)]

1. Fügen Sie dem-Abschnitt der-Klasse die folgenden Datenmember hinzu **`private`** .

[!code-cpp[concrt-basic-agent#3](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_4.h)]

   Der `_file_name`-Member ist der Name der Datei, die vom Agent ausgelesen wird. Der `_target` Member ist ein [parallelcurrency:: ITarget](../../parallel/concrt/reference/itarget-class.md) -Objekt, in das der Agent den Inhalt der Datei schreibt. Der `_error`-Member speichert alle Fehler, die während der Lebensdauer des Agents auftreten.

1. Fügen Sie dem-Abschnitt der-Klasse den folgenden Code für die- `file_reader` Konstruktoren hinzu **`public`** `file_reader` .

[!code-cpp[concrt-basic-agent#4](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_5.h)]

   Mit jeder Konstruktorüberladung werden die `file_reader`-Datenmember festgelegt. Mit der zweiten und dritten Konstruktorüberladung wird es der Anwendung ermöglicht, mit dem Agent einen bestimmten Planer zu verwenden. Bei der ersten Überladung wird der Standardplaner mit dem Agent verwendet.

1. Fügen Sie dem public-Abschnitt der `get_error`-Klasse die `file_reader`-Methode hinzu.

[!code-cpp[concrt-basic-agent#5](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_6.h)]

   Die `get_error`-Methode ruft alle Fehler ab, die während der Lebensdauer des Agents auftreten.

1. Implementieren Sie die Methode " [parallelcurrency:: Agent:: Run](reference/agent-class.md#run) " im- **`protected`** Abschnitt der-Klasse.

[!code-cpp[concrt-basic-agent#6](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_7.h)]

Die `run`-Methode öffnet die Datei und liest Daten aus. Die `run`-Methode erfasst mithilfe der Ausnahmebehandlung alle Fehler, die während der Dateiverarbeitung auftreten.

   Jedes Mal, wenn diese Methode Daten aus der Datei liest, ruft Sie die [parallelcurrency:: Asend](reference/concurrency-namespace-functions.md#asend) -Funktion auf, um diese Daten an den Ziel Puffer zu senden. Sie sendet die leere Zeichenfolge an den Zielpuffer, um so das Ende der Verarbeitung anzugeben.

Im folgenden Beispiel wird der vollständige Inhalt der Datei file_reader.h dargestellt.

[!code-cpp[concrt-basic-agent#7](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_8.h)]

[Nach[oben](#top)]

## <a name="using-the-file_reader-class-in-the-application"></a><a name="useagentclass"></a>Verwenden der file_reader-Klasse in der Anwendung

In diesem Abschnitt wird beschrieben, wie mithilfe der `file_reader`-Klasse der Inhalt einer Textdatei gelesen wird. Außerdem wird gezeigt, wie ein [parallelcurrency:: Callcenter](../../parallel/concrt/reference/call-class.md) -Objekt erstellt wird, das diese Datei Daten empfängt und seine Adler-32-Prüfsumme berechnet.

#### <a name="to-use-the-file_reader-class-in-your-application"></a>So verwenden Sie die file_reader-Klasse in der Anwendung

1. Fügen Sie in der Datei BasicAgent.cpp die folgende `#include`-Anweisung hinzu.

[!code-cpp[concrt-basic-agent#8](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_9.cpp)]

1. Fügen Sie in der Datei basicagent. cpp die folgenden **`using`** Direktiven hinzu.

[!code-cpp[concrt-basic-agent#9](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_10.cpp)]

1. Erstellen Sie in der- `_tmain` Funktion ein [parallelcurrency:: Event](../../parallel/concrt/reference/event-class.md) -Objekt, das das Ende der Verarbeitung signalisiert.

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

[Nach[oben](#top)]

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

Um gleichzeitigen Zugriff auf Datenmember zu verhindern, wird empfohlen, dass Sie Methoden hinzufügen, die Arbeit im **`protected`** **`private`** Abschnitt oder der Klasse ausführen. Fügen Sie dem-Abschnitt der Klasse nur Methoden hinzu, die Nachrichten an den Agent senden oder vom Agent empfangen **`public`** .

Die Methode " [parallelcurrency:: Agent::d One](reference/agent-class.md#done) " wird immer aufgerufen, um den Agent in den Zustand "abgeschlossen" zu verschieben. Diese Methode wird in der Regel vor der Rückkehr von der `run`-Methode aufgerufen.

## <a name="next-steps"></a>Nächste Schritte

Ein weiteres Beispiel für eine agentbasierte Anwendung finden Sie unter Exemplarische Vorgehensweise [: Verwenden von Join zum verhindern](../../parallel/concrt/walkthrough-using-join-to-prevent-deadlock.md)von Deadlocks.

## <a name="see-also"></a>Weitere Informationen

[Asynchronous Agents Library](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[Asynchrone Nachrichten Blöcke](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Nachrichten Übergabe Funktionen](../../parallel/concrt/message-passing-functions.md)<br/>
[Synchronisierungs Datenstrukturen](../../parallel/concrt/synchronization-data-structures.md)<br/>
[Exemplarische Vorgehensweise: verhindern von Deadlocks mithilfe von Join](../../parallel/concrt/walkthrough-using-join-to-prevent-deadlock.md)
