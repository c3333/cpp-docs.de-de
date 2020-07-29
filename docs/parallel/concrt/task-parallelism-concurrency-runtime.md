---
title: Aufgabenparallelität (Concurrency Runtime)
ms.date: 11/04/2016
helpviewer_keywords:
- structured task groups [Concurrency Runtime]
- structured tasks [Concurrency Runtime]
- task groups [Concurrency Runtime]
- task parallelism
- tasks [Concurrency Runtime]
ms.assetid: 42f05ac3-2098-494a-ba84-737fcdcad077
ms.openlocfilehash: 09c6153a1440684156226acbda909ca8b0398989
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224928"
---
# <a name="task-parallelism-concurrency-runtime"></a>Aufgabenparallelität (Concurrency Runtime)

Im Concurrency Runtime handelt es sich bei einer *Aufgabe* um eine Arbeitseinheit, die einen bestimmten Auftrag ausführt und in der Regel parallel mit anderen Aufgaben ausgeführt wird. Eine Aufgabe kann in zusätzliche, differenziertere Aufgaben zerlegt werden, die in einer *Aufgaben Gruppe*organisiert sind.

Sie verwenden Aufgaben, wenn Sie asynchronen Code schreiben und ein Vorgang erst ausgeführt werden soll, nachdem der asynchrone Vorgang abgeschlossen ist. Beispielsweise können Sie eine Aufgabe verwenden, um asynchron aus einer Datei zu lesen und dann eine andere Aufgabe zu verwenden – eine *Fortsetzungs Aufgabe*, die weiter unten in diesem Dokument erläutert wird –, um die Daten zu verarbeiten, nachdem Sie verfügbar ist. Umgekehrt können Sie Aufgabengruppen verwenden, um parallele Arbeitsvorgänge in kleinere Teile zu zerlegen. Nehmen Sie zum Beispiel einmal an, dass Sie über einen rekursiven Algorithmus verfügen, der die verbleibende Arbeit in zwei Partitionen unterteilt. Sie können Aufgabengruppen verwenden, um diese Partitionen gleichzeitig auszuführen, und dann warten, bis die aufgeteilte Arbeit abgeschlossen ist.

> [!TIP]
> Wenn Sie dieselbe Routine parallel auf jedes Element einer Auflistung anwenden möchten, verwenden Sie einen parallelen Algorithmus, z. b. Parallelität [::p arallel_for](reference/concurrency-namespace-functions.md#parallel_for), anstelle einer Aufgabe oder Aufgaben Gruppe. Weitere Informationen zu parallelen Algorithmen finden Sie unter [parallele Algorithmen](../../parallel/concrt/parallel-algorithms.md).

## <a name="key-points"></a>Die wichtigsten Punkte

- Wenn Sie Variablen als Verweis an einen Lambdaausdruck übergeben, müssen Sie sicherstellen, dass die Lebensdauer dieser Variablen bis zum Beenden der Aufgabe erhalten bleibt.

- Verwenden Sie zum Schreiben von asynchronem Code Tasks (die Klasse "Parallelität [:: Task](../../parallel/concrt/reference/task-class.md) "). Die Aufgabenklasse verwendet den Windows-ThreadPool als zugehörigen Planer und nicht die Concurrency Runtime.

- Verwenden Sie Aufgaben Gruppen (die [parallelcurrency:: task_group](reference/task-group-class.md) -Klasse oder den Algorithmus "Parallelität [::p arallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) "), wenn Sie parallele Arbeit in kleinere Teile zerlegen möchten, und warten Sie, bis die kleineren Teile fertig sind.

- Verwenden Sie die " [parallelcurrency:: Task:: Then](reference/task-class.md#then) "-Methode, um Fortsetzungen zu erstellen. Eine *Fortsetzung* ist eine Aufgabe, die asynchron ausgeführt wird, nachdem eine andere Aufgabe abgeschlossen wurde. Sie können eine beliebige Anzahl an Fortsetzungen verbinden, um eine Kette asynchroner Arbeitsvorgänge zu bilden.

- Die Ausführung einer aufgabenbasierten Fortsetzung wird immer für den Zeitpunkt geplant, zu dem die Vorgängeraufgabe abgeschlossen ist, auch wenn die Vorgängeraufgabe abgebrochen wird oder wenn diese eine Ausnahme auslöst.

- Verwenden Sie "Parallelität [:: when_all](reference/concurrency-namespace-functions.md#when_all) ", um eine Aufgabe zu erstellen, die abgeschlossen wird, nachdem alle Mitglieder eines Satzes von Aufgaben abgeschlossen wurden. Verwenden Sie "Parallelität [:: when_any](reference/concurrency-namespace-functions.md#when_any) ", um eine Aufgabe zu erstellen, die abgeschlossen wird, nachdem ein Mitglied eines Satzes von Aufgaben abgeschlossen wurde.

- Für Aufgaben und Aufgabengruppen kann der Abbruchmechanismus der Parallel Patterns Library (PPL) verwendet werden. Weitere Informationen finden Sie unter [Abbruch in der ppl](cancellation-in-the-ppl.md).

- Informationen dazu, wie die Runtime Ausnahmen behandelt, die von Aufgaben und Aufgaben Gruppen ausgelöst werden, finden Sie unter [Ausnahmebehandlung](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).

## <a name="in-this-document"></a>In diesem Dokument

- [Verwenden von Lambdaausdrücken](#lambdas)

- [Die Aufgabenklasse](#task-class)

- [Fortsetzungsaufgaben](#continuations)

- [Wertbasierte und aufgabenbasierte Fortsetzungen](#value-versus-task)

- [Verfassen von Aufgaben](#composing-tasks)

  - [Die Funktion "when_all"](#when-all)

  - [Die Funktion "when_any"](#when-any)

- [Verzögerte Aufgabenausführung](#delayed-tasks)

- [Aufgaben Gruppen](#task-groups)

- [task_group und structured_task_group im Vergleich](#comparing-groups)

- [Beispiel](#example)

- [Robuste Programmierung](#robust)

## <a name="using-lambda-expressions"></a><a name="lambdas"></a>Verwenden von Lambda-Ausdrücken

Aufgrund ihrer kompakten Syntax werden Lambda-Ausdrücke häufig zur Definition der Arbeit verwendet, die von Aufgaben und Aufgabengruppen ausgeführt wird. Im Folgenden finden Sie einige Verwendungstipps:

- Da Aufgaben in der Regel in Hintergrundthreads ausgeführt werden, beachten Sie die Objektlebensdauer, wenn Sie Variablen in Lambdaausdrücken erfassen. Wenn Sie eine Variable als Wert erfassen, wird eine Kopie dieser Variablen im Lambda-Text erstellt. Wenn Sie sie als Verweis erfassen, wird keine Kopie erstellt. Daher müssen Sie sicherstellen, dass die Lebensdauer jeder Variablen, die Sie als Verweis erfassen, länger ist als die Lebensdauer der Aufgabe, die diese verwendet.

- Wenn Sie einen Lambda-Ausdruck an eine Aufgabe übergeben, erfassen Sie keine Variablen, die auf dem Stapel als Verweis zugeordnet sind.

- Legen Sie die Variablen, die Sie in Lambda Ausdrücken erfassen, explizit fest, damit Sie identifizieren können, was Sie als Wert und als Verweis erfassen. Aus diesem Grund wird empfohlen, die Option `[=]` oder `[&]` für Lambda-Ausdrücke nicht zu verwenden.

Häufig wird in einer Aufgabe in einer Fortsetzungskette eine Zuweisung zu einer Variablen vorgenommen und in einer anderen Aufgabe diese Variable gelesen. Sie können nicht nach Wert erfassen, da jede Fortsetzungs Aufgabe eine andere Kopie der Variablen enthalten würde. Bei Stapel zugeordneten Variablen können Sie auch nicht als Verweis erfassen, da die Variable möglicherweise nicht mehr gültig ist.

Um dieses Problem zu beheben, verwenden Sie einen intelligenten Zeiger, wie z. b. " [Std:: shared_ptr](../../standard-library/shared-ptr-class.md)", um die Variable zu umschließen und den intelligenten Zeiger als Wert zu übergeben. Auf diese Weise kann eine Zuweisung zum zugrunde liegenden Objekt erfolgen, und es kann aus diesem Objekt gelesen werden. Außerdem ist seine Lebensdauer länger als die der Aufgaben, die es verwenden. Verwenden Sie diese Methode auch, wenn die Variable ein Zeiger oder ein Handle mit Verweiszählung (`^`) für ein Windows-Runtime-Objekt ist. Im Folgenden finden Sie ein einfaches Beispiel:

[!code-cpp[concrt-lambda-task-lifetime#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_1.cpp)]

Weitere Informationen zu Lambda-Ausdrücken finden Sie unter [Lambda-Ausdrücke](../../cpp/lambda-expressions-in-cpp.md).

## <a name="the-task-class"></a><a name="task-class"></a>Die Task-Klasse

Sie können die Klasse " [parallelcurrency:: Task](../../parallel/concrt/reference/task-class.md) " verwenden, um Aufgaben in einen Satz abhängiger Vorgänge zu verfassen. Dieses Kompositions Modell wird durch das Konzept von *Fortsetzungen*unterstützt. Eine Fortsetzung ermöglicht das Ausführen von Code, wenn die vorherige (oder *vorangehende*) Aufgabe abgeschlossen ist. Das Ergebnis der Vorgängeraufgabe wird als Eingabe an eine oder mehrere Fortsetzungsaufgaben übergeben. Wenn eine Vorgängeraufgabe abgeschlossen wird, werden alle Fortsetzungsaufgaben, die darauf warten, für die Ausführung geplant. Jede Fortsetzungsaufgabe erhält eine Kopie des Ergebnisses der Vorgängeraufgabe. Diese Fortsetzungsaufgaben wiederum können auch Vorgängeraufgaben für andere Fortsetzungen sein, sodass sie eine Kette von Aufgaben bilden. Mit Fortsetzungen können Sie Ketten von Aufgaben beliebiger Länge erstellen, die bestimmte Abhängigkeiten untereinander aufweisen. Außerdem kann für eine Aufgabe der Abbruchmechanismus verwendet werden – entweder vor dem Start einer Aufgabe oder in kooperativer Weise, während die Aufgabe ausgeführt wird. Weitere Informationen zu diesem Abbruch Modell finden Sie unter [Abbruch in der ppl](cancellation-in-the-ppl.md).

Bei `task` handelt es sich um eine Vorlagenklasse. Der Typparameter `T` gibt den Typ des Ergebnisses an, das von der Aufgabe erzeugt wird. Dieser Typ kann sein, **`void`** Wenn der Task keinen Wert zurückgibt. `T`der-Modifizierer kann nicht verwendet werden **`const`** .

Wenn Sie eine Aufgabe erstellen, geben Sie eine *Arbeitsfunktion* an, die den Aufgaben Text ausführt. Bei dieser Arbeitsfunktion kann es sich um eine Lambda-Funktion, einen Funktionszeiger oder ein Funktionsobjekt handeln. Um auf den Abschluss einer Aufgabe zu warten, ohne das Ergebnis zu erhalten, müssen Sie die Methode " [parallelcurrency:: Task:: Wait](reference/task-class.md#wait) " aufrufen. Die- `task::wait` Methode gibt einen " [parallelcurrency:: task_status](reference/concurrency-namespace-enums.md#task_group_status) "-Wert zurück, der beschreibt, ob die Aufgabe abgeschlossen oder abgebrochen wurde. Um das Ergebnis der Aufgabe abzurufen, wenden Sie die Methode " [parallelcurrency:: Task:: Get](reference/task-class.md#get) " an. Von dieser Methode wird `task::wait` aufgerufen, um darauf zu warten, dass die Aufgabe beendet wird. Daher wird die Ausführung des aktuellen Threads blockiert, bis das Ergebnis zur Verfügung steht.

Im folgenden Beispiel wird gezeigt, wie eine Aufgabe erstellt, auf das Ergebnis gewartet und dessen Wert angezeigt wird. In den Beispielen in dieser Dokumentation werden Lambda-Funktionen verwendet, da sie eine kompaktere Syntax aufweisen. Sie können bei der Verwendung von Aufgaben jedoch auch Funktionszeiger und Funktionsobjekte verwenden.

[!code-cpp[concrt-basic-task#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_2.cpp)]

Wenn Sie die Funktion " [parallelcurrency:: create_task](reference/concurrency-namespace-functions.md#create_task) " verwenden, können Sie das **`auto`** Schlüsselwort verwenden, anstatt den Typ zu deklarieren. Betrachten Sie beispielsweise diesen Code, mit dem die Identitätsmatrix erstellt und ausgegeben wird:

[!code-cpp[concrt-create-task#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_3.cpp)]

Sie können die `create_task`-Funktion verwenden, um den entsprechenden Vorgang zu erstellen.

[!code-cpp[concrt-create-task#2](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_4.cpp)]

Wenn während der Ausführung einer Aufgabe eine Ausnahme ausgelöst wird, wird die Ausnahme von der Laufzeit im nachfolgenden Aufruf an `task::get`, `task::wait` oder eine aufgabenbasierte Fortsetzung gemarshallt. Weitere Informationen zum Task Ausnahme Behandlungs Mechanismus finden Sie unter [Ausnahmebehandlung](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).

Ein Beispiel für die Verwendung von, Parallelität `task` [:: task_completion_event](../../parallel/concrt/reference/task-completion-event-class.md), Abbruch finden Sie unter Exemplarische Vorgehensweise [: Herstellen einer Verbindung mithilfe von Aufgaben und XML-HTTP-Anforderungen](../../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md). (Die `task_completion_event`-Klasse wird weiter unten in diesem Dokument beschrieben.)

> [!TIP]
> Ausführliche Informationen zu Aufgaben in UWP-apps finden Sie unter [asynchrone Programmierung in C++](/windows/uwp/threading-async/asynchronous-programming-in-cpp-universal-windows-platform-apps) und [Erstellen von asynchronen Vorgängen in C++ für UWP-apps](../../parallel/concrt/creating-asynchronous-operations-in-cpp-for-windows-store-apps.md).

## <a name="continuation-tasks"></a><a name="continuations"></a>Fortsetzungs Aufgaben

Bei der asynchronen Programmierung werden nach Abschluss eines asynchronen Vorgangs häufig ein zweiter Vorgang aufgerufen und Daten an diesen weitergegeben. Herkömmlicherweise werden hierfür Rückrufmethoden verwendet. Im Concurrency Runtime wird die gleiche Funktionalität durch *Fortsetzungs Aufgaben*bereitgestellt. Eine Fortsetzungs Aufgabe (auch als Fortsetzung bezeichnet) ist eine asynchrone Aufgabe, die von einer anderen Aufgabe aufgerufen wird, die als *Vorgänger*bezeichnet wird, wenn der Vorgänger abgeschlossen ist. Mithilfe von Fortsetzungen können Sie folgende Aufgaben ausführen:

- Übergeben von Daten vom Vorgänger an die Fortsetzung

- Angeben der präzisen Bedingungen, unter denen die Fortsetzung aufgerufen bzw. nicht aufgerufen wird

- Abbrechen einer Fortsetzung, bevor diese gestartet wird oder kooperativ während sie ausgeführt wird

- Bereitstellen von Hinweisen zur Planung der Fortsetzung (Dies gilt nur für universelle Windows-Plattform-Apps (UWP). Weitere Informationen finden Sie unter [Erstellen von asynchronen Vorgängen in C++ für UWP-apps](../../parallel/concrt/creating-asynchronous-operations-in-cpp-for-windows-store-apps.md).)

- Aufrufen mehrerer Fortsetzungen durch den gleichen Vorgänger

- Aufrufen einer Fortsetzung, wenn alle Vorgänger oder einer der Vorgänger abgeschlossen wird

- Verketten von Fortsetzungen auf eine beliebige Länge

- Behandeln von durch den Vorgänger ausgelöste Ausnahmen mithilfe einer Fortsetzung

Mithilfe dieser Funktionen können Sie eine oder mehrere Aufgaben ausführen, wenn die erste Aufgabe abgeschlossen wird. Sie können beispielsweise eine Fortsetzung erstellen, in der eine Datei komprimiert wird, nachdem sie von der ersten Aufgabe vom Datenträger gelesen wurde.

Im folgenden Beispiel wird das vorherige so geändert, dass die " [parallelcurrency:: Task:: Then](reference/task-class.md#then) "-Methode verwendet wird, um eine Fortsetzung zu planen, die den Wert der Vorgänger Aufgabe ausgibt, wenn Sie verfügbar ist.

[!code-cpp[concrt-basic-continuation#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_5.cpp)]

Sie können Aufgaben auf eine beliebige Länge verketten und schachteln. Eine Aufgabe kann auch über mehrere Fortsetzungen verfügen. Im folgenden Beispiel wird eine einfache Fortsetzungskette dargestellt, in der der Wert der vorherigen Aufgabe dreimal erhöht wird.

[!code-cpp[concrt-continuation-chain#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_6.cpp)]

Eine Fortsetzung kann auch eine andere Aufgabe zurückgeben. Wenn kein Abbruch erfolgt, wird diese Aufgabe vor der nachfolgenden Fortsetzung ausgeführt. Diese Technik wird als *asynchrone entpacken*bezeichnet. Das asynchrone Entpacken ist nützlich, wenn Sie zusätzliche Arbeitsvorgänge im Hintergrund ausführen möchten, jedoch nicht möchten, dass der aktuelle Thread durch die aktuelle Aufgabe blockiert wird. (Dies ist bei UWP-apps üblich, bei denen Fortsetzungen im UI-Thread ausgeführt werden können.) Im folgenden Beispiel werden drei Aufgaben gezeigt. Die erste Aufgabe gibt eine andere Aufgabe zurück, die vor einer Fortsetzungsaufgabe ausgeführt wird.

[!code-cpp[concrt-async-unwrapping#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_7.cpp)]

> [!IMPORTANT]
> Wenn eine Fortsetzung einer Aufgabe eine geschachtelte Aufgabe vom Typ `N` zurückgibt, ist die resultierende Aufgabe vom Typ `N`, nicht vom Typ `task<N>`, und wird abgeschlossen, wenn die geschachtelte Aufgabe abgeschlossen wird. Das heißt, die Fortsetzung entpackt die geschachtelte Aufgabe.

## <a name="value-based-versus-task-based-continuations"></a><a name="value-versus-task"></a>Wert basierte und aufgabenbasierte Fortsetzungen

Bei einem `task`-Objekt, dessen Rückgabetyp `T` ist, können Sie einen Wert des Typs `T` oder `task<T>` für die zugehörigen Fortsetzungsaufgaben bereitstellen. Eine Fortsetzung, die Type annimmt, `T` wird als *Wert basierte Fortsetzung*bezeichnet. Eine wertbasierte Fortsetzung wird für die Ausführung geplant, wenn die Vorgängeraufgabe ohne Fehler abgeschlossen und nicht abgebrochen wird. Eine Fortsetzung, die `task<T>` den Typ als Parameter annimmt, wird als *aufgabenbasierte Fortsetzung*bezeichnet. Die Ausführung einer aufgabenbasierten Fortsetzung wird immer für den Zeitpunkt geplant, zu dem die Vorgängeraufgabe abgeschlossen ist, auch wenn die Vorgängeraufgabe abgebrochen wird oder wenn diese eine Ausnahme auslöst. Sie können dann `task::get` aufrufen, um das Ergebnis der Vorgängeraufgabe abzurufen. Wenn die Vorgänger Aufgabe abgebrochen wurde, löst `task::get` " [parallelcurrency:: task_canceled](../../parallel/concrt/reference/task-canceled-class.md)" aus. Wenn von der Vorgängeraufgabe eine Ausnahme ausgelöst wurde, wird von `task::get` diese Ausnahme erneut ausgelöst. Eine aufgabenbasierte Fortsetzung wird nicht als abgebrochen markiert, wenn die zugehörige Vorgängeraufgabe abgebrochen wird.

## <a name="composing-tasks"></a><a name="composing-tasks"></a>Verfassen von Aufgaben

In diesem Abschnitt werden die Funktionen " [parallelcurrency:: when_all](reference/concurrency-namespace-functions.md#when_all) " und " [parallelcurrency:: when_any](reference/concurrency-namespace-functions.md#when_all) " beschrieben, die Ihnen helfen können, mehrere Aufgaben zum Implementieren allgemeiner Muster zu verfassen.

### <a name="the-when_all-function"></a><a name="when-all"></a>Die when_all-Funktion

Von der `when_all`-Funktion wird eine Aufgabe erstellt, die abgeschlossen wird, nachdem ein Satz von Aufgaben abgeschlossen wurde. Diese Funktion gibt ein Std::[Vector](../../standard-library/vector-class.md) -Objekt zurück, das das Ergebnis jeder Aufgabe im Satz enthält. Im folgenden einfachen Beispiel wird mithilfe von `when_all` eine Aufgabe erstellt, die den Abschluss von drei anderen Aufgaben darstellt.

[!code-cpp[concrt-join-tasks#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_8.cpp)]

> [!NOTE]
> Die Aufgaben, die Sie an `when_all` übergeben, müssen einheitlich sein. Das heißt, sie müssen alle den gleichen Typ zurückgeben.

Sie können auch die Syntax `&&` verwenden, um eine Aufgabe zu erstellen, die nach Abschluss eines Satzes von Aufgaben abgeschlossen wird, wie im folgenden Beispiel gezeigt.

`auto t = t1 && t2; // same as when_all`

Es ist üblich, eine Fortsetzung zusammen mit `when_all` zu verwenden, um eine Aktion auszuführen, nachdem ein Satz von Aufgaben abgeschlossen wurde. Im folgenden Beispiel wird die vorherige geändert, um die Summe von drei Aufgaben auszugeben, die jeweils ein **`int`** Ergebnis liefern.

[!code-cpp[concrt-join-tasks#2](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_9.cpp)]

In diesem Beispiel können Sie auch `task<vector<int>>` angeben, um eine aufgabenbasierte Fortsetzung zu erstellen.

Wenn eine Aufgabe in einem Satz von Aufgaben abgebrochen wird oder eine Ausnahme auslöst, wird `when_all` sofort abgeschlossen und wartet nicht, bis die übrigen Aufgaben beendet sind. Wenn eine Ausnahme ausgelöst wird, löst die Laufzeit die Ausnahme erneut aus, wenn Sie `task::get` oder `task::wait` für das Task-Objekt aufrufen, das von `when_all` zurückgegeben wird. Wenn von mehr als einer Aufgabe eine Ausnahme ausgelöst wird, wird von der Laufzeit eine ausgewählt. Daher müssen Sie sicherstellen, dass Sie alle Ausnahmen nach Abschluss aller Aufgaben berücksichtigen. Eine nicht behandelte Ausnahme einer Aufgabe führt dazu, dass die App beendet wird.

Hier ist eine Utility-Funktion, mit der Sie sicherstellen können, dass Ihr Programm alle Ausnahmen beachtet. Die Funktion `observe_all_exceptions` löst für jede Aufgabe im bereitgestellten Bereich jede aufgetretene Ausnahme aus, damit diese erneut ausgelöst wird, und "schluckt" diese anschließend.

[!code-cpp[concrt-eh-when_all#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_10.cpp)]

Angenommen, Sie verwenden eine UWP-APP, die C++ und XAML verwendet und einen Satz von Dateien auf den Datenträger schreibt. Im folgenden Beispiel wird gezeigt, wie `when_all` und `observe_all_exceptions` verwendet werden, um sicherzustellen, dass das Programm alle Ausnahmen berücksichtigt.

[!code-cpp[concrt-eh-when_all#2](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_11.cpp)]

##### <a name="to-run-this-example"></a>So führen Sie dieses Beispiel aus

1. Fügen Sie in "MainPage.xaml" ein `Button`-Steuerelement hinzu.

[!code-xml[concrt-eh-when_all#3](../../parallel/concrt/codesnippet/xaml/task-parallelism-concurrency-runtime_12.xaml)]

1. Fügen Sie in "MainPage. XAML. h" Diese vorwärts Deklarationen zum- **`private`** Abschnitt der `MainPage` Klassen Deklaration hinzu.

[!code-cpp[concrt-eh-when_all#4](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_13.h)]

1. Implementieren Sie in "MainPage.xaml.cpp" den `Button_Click`-Ereignishandler.

[!code-cpp[concrt-eh-when_all#5](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_14.cpp)]

1. Implementieren Sie in "MainPage.xaml.cpp" `WriteFilesAsync` wie im Beispiel dargestellt.

> [!TIP]
> `when_all` ist eine nicht blockierende Funktion, die `task` als Ergebnis erzeugt. Anders als bei [Task:: Wait](reference/task-class.md#wait)ist es sicher, diese Funktion in einer UWP-App auf dem AStA-Thread (Application STA) aufzurufen.

### <a name="the-when_any-function"></a><a name="when-any"></a>Die when_any-Funktion

Die `when_any`-Funktion erstellt eine Aufgabe, die abgeschlossen wird, wenn die erste Aufgabe in einem Satz von Aufgaben abgeschlossen wird. Diese Funktion gibt ein [Std::p Air](../../standard-library/pair-structure.md) -Objekt zurück, das das Ergebnis der abgeschlossenen Aufgabe und den Index der Aufgabe in der Menge enthält.

Die `when_any`-Funktion ist insbesondere in folgenden Szenarien nützlich:

- Redundante Vorgänge. Betrachten Sie einen Algorithmus oder einen Vorgang, der auf verschiedene Weise ausgeführt werden kann. Sie können die `when_any`-Funktion verwenden, um den Vorgang auszuwählen, der zuerst beendet wird, und dann die verbleibenden Vorgänge abzubrechen.

- Überlappende Vorgänge. Sie können mehrere Vorgänge starten, die alle beendet werden müssen, und die `when_any`-Funktion verwenden, um Ergebnisse zu verarbeiten, wenn jeder Vorgang beendet wird. Nachdem ein Vorgang beendet wurde, können Sie eine oder mehrere weitere Aufgaben starten.

- Eingeschränkte Vorgänge. Sie können die `when_any`-Funktion verwenden, um das vorherige Szenario zu erweitern, indem Sie die Anzahl der gleichzeitigen Vorgänge einschränken.

- Abgelaufene Vorgänge. Sie können die `when_any`-Funktion verwenden, um zwischen einer oder mehreren Aufgaben und einer Aufgabe auszuwählen, die nach einer bestimmten Zeit beendet wird.

Wie bei `when_all` wird häufig eine Fortsetzung verwendet, in der mithilfe von `when_any` eine Aktion ausgeführt wird, wenn die erste Aufgabe in einem Satz von Aufgaben beendet wird. Im folgenden einfachen Beispiel wird mithilfe von `when_any` eine Aufgabe erstellt, die abgeschlossen wird, wenn die erste von drei anderen Aufgaben abgeschlossen wird.

[!code-cpp[concrt-select-task#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_15.cpp)]

In diesem Beispiel können Sie auch `task<pair<int, size_t>>` angeben, um eine aufgabenbasierte Fortsetzung zu erstellen.

> [!NOTE]
> Wie bei `when_all` müssen alle an `when_any` übergebenen Aufgaben denselben Typ zurückgeben.

Sie können auch die Syntax `||` verwenden, um eine Aufgabe zu erstellen, die nach der ersten Aufgabe in einem Satz von Aufgaben abgeschlossen wird, wie im folgenden Beispiel gezeigt.

`auto t = t1 || t2; // same as when_any`

> [!TIP]
> Wie bei `when_all` `when_any` ist auch nicht blockierend und kann sicher in einer UWP-App auf dem AStA-Thread aufgerufen werden.

## <a name="delayed-task-execution"></a><a name="delayed-tasks"></a>Verzögerte Task Ausführung

In einigen Fällen ist es notwendig, die Ausführung einer Aufgabe zu verzögern, bis eine Bedingung erfüllt ist, oder eine Aufgabe als Reaktion auf ein externes Ereignis zu starten. Bei der asynchronen Programmierung müssen Sie zum Beispiel möglicherweise eine Aufgabe als Reaktion auf ein E/A-Abschlussereignis starten.

Hierfür gibt es zwei Möglichkeiten, eine Fortsetzung zu verwenden oder eine Aufgabe zu starten und auf ein Ereignis innerhalb der Arbeitsfunktion der Aufgabe zu warten. Allerdings gibt es Fälle, in denen es nicht möglich, eine dieser Techniken zu verwenden. Sie müssen beispielsweise über die Vorgängeraufgabe verfügen, um eine Fortsetzung zu erstellen. Wenn Sie jedoch nicht über die Vorgänger Aufgabe verfügen, können Sie ein *Aufgaben Abschluss Ereignis* erstellen und das Abschluss Ereignis später an die vorangehende Aufgabe verketten, wenn Sie verfügbar wird. Da eine wartende Aufgabe auch einen Thread blockiert, können Sie Aufgabenabschlussereignisse außerdem dazu verwenden, Arbeitsvorgänge auszuführen, wenn ein asynchroner Vorgang abgeschlossen wird, und dadurch einen Thread freigeben.

Die Klasse " [parallelcurrency:: task_completion_event](../../parallel/concrt/reference/task-completion-event-class.md) " hilft, eine solche Komposition von Aufgaben zu vereinfachen. Wie die `task`-Klasse ist der Typparameter `T` der Typ des Ergebnisses, das von der Aufgabe erzeugt wird. Dieser Typ kann sein, **`void`** Wenn der Task keinen Wert zurückgibt. `T`der-Modifizierer kann nicht verwendet werden **`const`** . In der Regel wird ein `task_completion_event`-Objekt für einen Thread oder eine Aufgabe bereitgestellt, der bzw. die signalisieren, wenn der Wert für das Objekt zur Verfügung steht. Gleichzeitig wird mindestens eine Aufgabe als Listener dieses Ereignisses festgelegt. Wenn das Ereignis festgelegt wird, werden die Listeneraufgaben abgeschlossen und ihre Fortsetzungen für die Ausführung geplant.

Ein Beispiel, in dem verwendet `task_completion_event` wird, um eine Aufgabe zu implementieren, die nach einer Verzögerung abgeschlossen wird, finden Sie unter Gewusst [wie: Erstellen einer Aufgabe, die nach einer Verzögerung abgeschlossen](../../parallel/concrt/how-to-create-a-task-that-completes-after-a-delay.md)wird.

## <a name="task-groups"></a><a name="task-groups"></a>Aufgaben Gruppen

Eine Aufgaben *Gruppe* organisiert eine Auflistung von Aufgaben. Aufgabengruppen verschieben Aufgaben in eine Arbeitsübernahme-Warteschlange. Der Planer entfernt Aufgaben aus dieser Warteschlange und führt sie auf verfügbaren Computerressourcen aus. Nachdem Sie einer Aufgabengruppe Aufgaben hinzugefügt haben, können Sie warten, bis alle Aufgaben aufgeführt wurden, oder Sie können Aufgaben abbrechen, die noch nicht gestartet wurden.

Die ppl verwendet die Klassen " [parallelcurrency:: task_group](reference/task-group-class.md) " und " [parallelcurrency:: structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) " zur Darstellung von Aufgaben Gruppen, und die Klasse " [parallelcurrency:: task_handle](../../parallel/concrt/reference/task-handle-class.md) " stellt die Aufgaben dar, die in diesen Gruppen ausgeführt werden. In der `task_handle`-Klasse wird der Code gekapselt, der die Arbeit ausführt. Wie die `task`-Klasse steht die Arbeitsfunktion in Form einer Lambda-Funktion, eines Funktionszeigers oder eines Funktionsobjekts zur Verfügung. In der Regel ist es nicht erforderlich, direkt mit `task_handle`-Objekten zu arbeiten. Stattdessen übergeben Sie Arbeitsfunktionen an eine Aufgabengruppe, die die `task_handle`-Objekte erstellt und verwaltet.

Die ppl dividiert Aufgaben Gruppen in diese zwei Kategorien: *unstrukturierte Aufgaben Gruppen* und *strukturierte Aufgaben Gruppen*. In der PPL werden unstrukturierte Aufgabengruppen mithilfe der `task_group`-Klasse und strukturierte Aufgabengruppen mithilfe der `structured_task_group`-Klasse dargestellt.

> [!IMPORTANT]
> Die ppl definiert auch den " [parallelcurrency::p arallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) -Algorithmus, der die-Klasse verwendet, `structured_task_group` um eine Reihe von Aufgaben parallel auszuführen. Da der `parallel_invoke`-Algorithmus eine kompaktere Syntax aufweist, wird empfohlen, diesen, sofern möglich, anstelle der `structured_task_group`-Klasse zu verwenden. Das Thema [parallele Algorithmen](../../parallel/concrt/parallel-algorithms.md) beschreibt ausführlicher `parallel_invoke` .

Verwenden Sie `parallel_invoke`, um mehrere unabhängige Aufgaben gleichzeitig auszuführen und sofort darauf zu warten, dass alle Aufgaben abgeschlossen sind. Diese Technik wird häufig als *Verzweigung und* joinparallelität bezeichnet. Verwenden Sie `task_group`, um mehrere unabhängige Aufgaben gleichzeitig auszuführen und später darauf zu warten, dass allle Aufgaben abgeschlossen sind. Beispielsweise können Sie einem `task_group`-Objekt Aufgaben hinzufügen und in einer anderen Funktion oder einem anderen Thread darauf warten, dass die Aufgaben beendet werden.

Aufgabengruppen unterstützen das Konzept eines Abbruchs. Mit einem Abbruch können Sie für alle aktiven Aufgaben angeben, dass der gesamte Vorgang abgebrochen werden soll. Durch den Abbruch wird außerdem verhindert, dass Aufgaben gestartet werden, die noch nicht gestartet wurden. Weitere Informationen zu Abbruch finden Sie unter [Abbruch in der ppl](cancellation-in-the-ppl.md).

Die Laufzeit stellt außerdem ein Modell für die Ausnahmebehandlung bereit, mit dem Sie eine Ausnahme für eine Aufgabe auslösen und behandeln können, während Sie darauf warten, das die zugeordnete Aufgabengruppe fertig gestellt wird. Weitere Informationen zu diesem Modell zur Ausnahmebehandlung finden Sie unter [Ausnahmebehandlung](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).

## <a name="comparing-task_group-to-structured_task_group"></a><a name="comparing-groups"></a>Vergleichen von task_group mit structured_task_group

Grundsätzlich wird die Verwendung von `task_group` oder `parallel_invoke` anstelle der `structured_task_group`-Klasse empfohlen. In Einzelfällen, beispielsweise beim Schreiben eines parallelen Algorithmus für eine variable Anzahl von Aufgaben oder mit der Möglichkeit eines Abbruchs, können Sie jedoch `structured_task_group` verwenden. In diesem Abschnitt werden die Unterschiede zwischen der `task_group`-Klasse und der `structured_task_group`-Klasse erläutert.

Die `task_group`-Klasse ist threadsicher. Sie können einem `task_group`-Objekt daher Aufgaben von mehreren Threads hinzufügen und in mehreren Threads auf ein `task_group`-Objekt warten oder dieses abbrechen. Das Erstellen und Zerstören eines `structured_task_group`-Objekts muss im gleichen lexikalischen Gültigkeitsbereich erfolgen. Darüber hinaus müssen alle Vorgänge für ein `structured_task_group`-Objekt im gleichen Thread ausgeführt werden. Eine Ausnahme von dieser Regel sind die Methoden " [parallelcurrency:: structured_task_group:: Cancel](reference/structured-task-group-class.md#cancel) " und " [parallelcurrency:: structured_task_group:: is_canceling](reference/structured-task-group-class.md#is_canceling) ". Eine untergeordnete Aufgabe kann diese Methoden aufrufen, um die übergeordnete Aufgabengruppe abzubrechen oder das Abbrechen jederzeit zu überprüfen.

Sie können zusätzliche Aufgaben für ein- `task_group` Objekt ausführen, nachdem Sie die Methode ' [parallelcurrency:: task_group:: Wait](reference/task-group-class.md#wait) ' oder ' [parallelcurrency:: task_group:: run_and_wait](reference/task-group-class.md#run_and_wait) ' aufgerufen haben. Wenn Sie im Gegensatz dazu zusätzliche Aufgaben für ein-Objekt ausführen, `structured_task_group` nachdem Sie die Methoden " [parallelcurrency:: structured_task_group:: Wait](reference/structured-task-group-class.md#wait) " oder " [parallelcurrency:: structured_task_group:: run_and_wait](reference/structured-task-group-class.md#run_and_wait) " aufgerufen haben, ist das Verhalten nicht definiert.

Da die `structured_task_group`-Klasse nicht threadübergreifend synchronisiert, ist ihr Ausführungsaufwand im Vergleich zur `task_group`-Klasse geringer. Wenn die Planung von Arbeit für mehrere Threads nicht Teil eines Problems ist und der `parallel_invoke`-Algorithmus nicht verwendet werden kann, können Sie mit der `structured_task_group`-Klasse leistungsfähigeren Code schreiben.

Wenn Sie ein `structured_task_group`-Objekt in einem anderen `structured_task_group`-Objekt verwenden, muss das innere Objekt abgeschlossen und zerstört sein, bevor das äußere Objekt beendet wird. Bei der `task_group`-Klasse ist die Fertigstellung geschachtelter Aufgabengruppen vor der äußeren Gruppe nicht erforderlich.

Unstrukturierte Aufgabengruppen und strukturierte Aufgabengruppen verwenden Aufgabenhandles auf unterschiedliche Weise. Sie können Arbeitsfunktionen direkt an ein `task_group`-Objekt übergeben; das Aufgabenhandle wird unmittelbar vom `task_group`-Objekt für Sie erstellt und verwaltet. Die `structured_task_group`-Klasse erfordert die Verwaltung eines `task_handle`-Objekts für jede Aufgabe. Jedes `task_handle`-Objekt muss über die gesamte Lebensdauer des zugeordneten `structured_task_group`-Objekts hinweg gültig sein. Verwenden Sie die Funktion " [parallelcurrency:: Make_task](reference/concurrency-namespace-functions.md#make_task) ", um ein-Objekt zu erstellen `task_handle` , wie im folgenden grundlegenden Beispiel gezeigt:

[!code-cpp[concrt-make-task-structure#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_16.cpp)]

Verwenden Sie zum Verwalten von Task Handles in Fällen mit einer Variablen Anzahl von Tasks eine Stapel Zuordnungs Routine, wie z. b. [_malloca](../../c-runtime-library/reference/malloca.md) oder eine Container Klasse wie Std::[Vector](../../standard-library/vector-class.md).

`task_group` und `structured_task_group` unterstützen die Möglichkeit eines Abbruchs. Weitere Informationen zu Abbruch finden Sie unter [Abbruch in der ppl](cancellation-in-the-ppl.md).

## <a name="example"></a><a name="example"></a> Beispiel

Im folgenden grundlegenden Beispiel wird die Verwendung von Aufgabengruppen veranschaulicht. In diesem Beispiel werden vom `parallel_invoke`-Algorithmus zwei Aufgaben gleichzeitig ausgeführt. In jeder Aufgabe werden einem `task_group`-Objekt untergeordnete Aufgaben hinzugefügt. Die `task_group`-Klasse ermöglicht das zeitgleiche Hinzufügen für mehrere Aufgaben.

[!code-cpp[concrt-using-task-groups#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_17.cpp)]

Nachfolgend wird eine Beispielausgabe für dieses Beispiel angezeigt:

```Output
Message from task: Hello
Message from task: 3.14
Message from task: 42
```

Da die Aufgaben vom `parallel_invoke`-Algorithmus gleichzeitig ausgeführt werden, kann sich die Reihenfolge der Ausgabemeldungen unterscheiden.

Vollständige Beispiele, die zeigen, wie der- `parallel_invoke` Algorithmus verwendet wird, finden Sie unter Gewusst [wie: Verwenden von parallel_invoke zum Schreiben einer parallelen Sortier Routine](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md) und Gewusst [wie: Verwenden von parallel_invoke zum Ausführen paralleler Vorgänge](../../parallel/concrt/how-to-use-parallel-invoke-to-execute-parallel-operations.md). Ein umfassendes Beispiel, in dem die- `task_group` Klasse zum Implementieren asynchroner Futures verwendet wird, finden Sie unter Exemplarische Vorgehensweise [: Implementieren von Futures](../../parallel/concrt/walkthrough-implementing-futures.md).

## <a name="robust-programming"></a><a name="robust"></a>Robuste Programmierung

Es ist wichtig, dass Sie die Rolle des Abbruchs und der Ausnahmebehandlung verstehen, wenn Sie Aufgaben, Aufgabengruppen und parallele Algorithmen verwenden. Beispielweise kann eine abgebrochene Aufgabe in einer Struktur paralleler Arbeitsaufgaben dazu führen, dass untergeordnete Aufgaben nicht ausgeführt werden. Dies kann Probleme verursachen, wenn eine der untergeordneten Aufgaben einen Vorgang ausführen soll, der für die Anwendung von Bedeutung ist, beispielsweise das Freigeben einer Ressource. Wenn eine untergeordnete Aufgabe eine Ausnahme auslöst, kann diese Ausnahme außerdem über einen Objektdestruktor weitergeben werden und nicht definiertes Verhalten in der Anwendung auslösen. Ein Beispiel, das diese Punkte veranschaulicht, finden Sie im Abschnitt Grundlegendes zur [Auswirkung von Abbruch und Ausnahmebehandlung auf die Objekt Zerstörung](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md#object-destruction) in den bewährten Methoden im Dokument zur Parallel Patterns Library. Weitere Informationen zu Abbruch-und Ausnahme Behandlungs Modellen in der ppl finden Sie unter [Abbruch](../../parallel/concrt/cancellation-in-the-ppl.md) und [Ausnahmebehandlung](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).

## <a name="related-topics"></a>Verwandte Themen

|Titel|Beschreibung|
|-----------|-----------------|
|[Gewusst wie: Verwenden von parallel_invoke zum Schreiben einer parallelen Sortier Routine](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md)|Erläutert, wie die Leistung des bitonischen Sortieralgorithmus mit dem `parallel_invoke`-Algorithmus verbessert werden.|
|[Vorgehensweise: Verwenden von parallel_invoke zum Ausführen paralleler Vorgänge](../../parallel/concrt/how-to-use-parallel-invoke-to-execute-parallel-operations.md)|Erläutert, wie die Leistung eines Programms mit dem `parallel_invoke`-Algorithmus verbessert werden kann, das mehrere Vorgänge in einer freigegebenen Datenquelle ausführt.|
|[Vorgehensweise: Erstellen einer Aufgabe, die nach einer Verzögerung abgeschlossen wird](../../parallel/concrt/how-to-create-a-task-that-completes-after-a-delay.md)|Zeigt, wie die `task` Klassen, `cancellation_token_source` , und verwendet werden, `cancellation_token` `task_completion_event` um eine Aufgabe zu erstellen, die nach einer Verzögerung abgeschlossen wird.|
|[Exemplarische Vorgehensweise: Implementieren von Futures](../../parallel/concrt/walkthrough-implementing-futures.md)|Zeigt, wie die vorhandene Funktionalität in der Concurrency Runtime kombiniert werden kann, um mehr Funktionalität zu erreichen.|
|[Parallel Patterns Library (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)|Beschreibt die PPL, die ein obligatorisches Programmiermodell zum Entwickeln gleichzeitiger Anwendungen bereitstellt.|

## <a name="reference"></a>Verweis

[Task-Klasse (Concurrency Runtime)](../../parallel/concrt/reference/task-class.md)

[task_completion_event-Klasse](../../parallel/concrt/reference/task-completion-event-class.md)

[when_all-Funktion](reference/concurrency-namespace-functions.md#when_all)

[when_any-Funktion](reference/concurrency-namespace-functions.md#when_any)

[Task_group-Klasse](reference/task-group-class.md)

[Parallel_invoke-Funktion](reference/concurrency-namespace-functions.md#parallel_invoke)

[structured_task_group-Klasse](../../parallel/concrt/reference/structured-task-group-class.md)
