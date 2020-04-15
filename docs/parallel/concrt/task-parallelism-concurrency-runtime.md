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
ms.openlocfilehash: f65521771db3eb0fe19dc863b1b49e9627fc60e6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368588"
---
# <a name="task-parallelism-concurrency-runtime"></a>Aufgabenparallelität (Concurrency Runtime)

In der Parallelitätslaufzeit ist eine *Aufgabe* eine Arbeitseinheit, die einen bestimmten Auftrag ausführt und in der Regel parallel zu anderen Aufgaben ausgeführt wird. Eine Aufgabe kann in zusätzliche, detailliertere Aufgaben zerlegt werden, die in einer *Aufgabengruppe*organisiert sind.

Sie verwenden Aufgaben, wenn Sie asynchronen Code schreiben und ein Vorgang erst ausgeführt werden soll, nachdem der asynchrone Vorgang abgeschlossen ist. Sie können z. B. eine Aufgabe verwenden, um asynchron aus einer Datei zu lesen, und dann eine andere Aufgabe verwenden – eine *Fortsetzungsaufgabe*, die weiter unten in diesem Dokument erläutert wird –, um die Daten zu verarbeiten, nachdem sie verfügbar sind. Umgekehrt können Sie Aufgabengruppen verwenden, um parallele Arbeitsvorgänge in kleinere Teile zu zerlegen. Nehmen Sie zum Beispiel einmal an, dass Sie über einen rekursiven Algorithmus verfügen, der die verbleibende Arbeit in zwei Partitionen unterteilt. Sie können Aufgabengruppen verwenden, um diese Partitionen gleichzeitig auszuführen, und dann warten, bis die aufgeteilte Arbeit abgeschlossen ist.

> [!TIP]
> Wenn Sie dieselbe Routine auf jedes Element einer Auflistung parallel anwenden möchten, verwenden Sie einen parallelen Algorithmus, z. [B. concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for), anstelle einer Aufgabe oder Aufgabengruppe. Weitere Informationen zu parallelen Algorithmen finden Sie unter [Parallelalgorithmen](../../parallel/concrt/parallel-algorithms.md).

## <a name="key-points"></a>Die wichtigsten Punkte

- Wenn Sie Variablen als Verweis an einen Lambdaausdruck übergeben, müssen Sie sicherstellen, dass die Lebensdauer dieser Variablen bis zum Beenden der Aufgabe erhalten bleibt.

- Verwenden Sie Aufgaben (die [parallelität::task-Klasse),](../../parallel/concrt/reference/task-class.md) wenn Sie asynchronen Code schreiben. Die Aufgabenklasse verwendet den Windows-ThreadPool als zugehörigen Planer und nicht die Concurrency Runtime.

- Verwenden Sie Aufgabengruppen (die [concurrency::task_group-Klasse](reference/task-group-class.md) oder den [Concurrency::parallel_invoke-Algorithmus),](reference/concurrency-namespace-functions.md#parallel_invoke) wenn Sie parallele Arbeiten in kleinere Teile zerlegen und dann warten möchten, bis diese kleineren Teile abgeschlossen sind.

- Verwenden Sie die [parallelcurrency::task::then-Methode,](reference/task-class.md#then) um Fortsetzungen zu erstellen. Eine *Fortsetzung* ist eine Aufgabe, die asynchron ausgeführt wird, nachdem eine andere Aufgabe abgeschlossen wurde. Sie können eine beliebige Anzahl an Fortsetzungen verbinden, um eine Kette asynchroner Arbeitsvorgänge zu bilden.

- Die Ausführung einer aufgabenbasierten Fortsetzung wird immer für den Zeitpunkt geplant, zu dem die Vorgängeraufgabe abgeschlossen ist, auch wenn die Vorgängeraufgabe abgebrochen wird oder wenn diese eine Ausnahme auslöst.

- Verwenden Sie [concurrency::when_all,](reference/concurrency-namespace-functions.md#when_all) um eine Aufgabe zu erstellen, die abgeschlossen wird, nachdem jedes Mitglied einer Gruppe von Aufgaben abgeschlossen wurde. Verwenden Sie [concurrency::when_any,](reference/concurrency-namespace-functions.md#when_any) um eine Aufgabe zu erstellen, die abgeschlossen wird, nachdem ein Mitglied einer Gruppe von Aufgaben abgeschlossen wurde.

- Für Aufgaben und Aufgabengruppen kann der Abbruchmechanismus der Parallel Patterns Library (PPL) verwendet werden. Weitere Informationen finden Sie [unter Stornierung in der PPL](cancellation-in-the-ppl.md).

- Informationen dazu, wie die Laufzeit Ausnahmen behandelt, die von Aufgaben und Aufgabengruppen ausgelöst werden, finden Sie unter [Ausnahmebehandlung](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).

## <a name="in-this-document"></a>In diesem Dokument

- [Verwenden von Lambdaausdrücken](#lambdas)

- [Die Aufgabenklasse](#task-class)

- [Fortsetzungsaufgaben](#continuations)

- [Wertbasierte und aufgabenbasierte Fortsetzungen](#value-versus-task)

- [Komponieren von Aufgaben](#composing-tasks)

  - [Die Funktion "when_all"](#when-all)

  - [Die Funktion "when_any"](#when-any)

- [Verzögerte Aufgabenausführung](#delayed-tasks)

- [Aufgabengruppen](#task-groups)

- [task_group und structured_task_group im Vergleich](#comparing-groups)

- [Beispiel](#example)

- [Stabile Programmierung](#robust)

## <a name="using-lambda-expressions"></a><a name="lambdas"></a>Verwenden von Lambda-Ausdrücken

Aufgrund ihrer kompakten Syntax werden Lambda-Ausdrücke häufig zur Definition der Arbeit verwendet, die von Aufgaben und Aufgabengruppen ausgeführt wird. Im Folgenden finden Sie einige Verwendungstipps:

- Da Aufgaben in der Regel in Hintergrundthreads ausgeführt werden, beachten Sie die Objektlebensdauer, wenn Sie Variablen in Lambdaausdrücken erfassen. Wenn Sie eine Variable als Wert erfassen, wird eine Kopie dieser Variablen im Lambda-Text erstellt. Wenn Sie sie als Verweis erfassen, wird keine Kopie erstellt. Daher müssen Sie sicherstellen, dass die Lebensdauer jeder Variablen, die Sie als Verweis erfassen, länger ist als die Lebensdauer der Aufgabe, die diese verwendet.

- Wenn Sie einen Lambda-Ausdruck an eine Aufgabe übergeben, erfassen Sie keine Variablen, die dem Stapel als Verweis zugewiesen sind.

- Seien Sie explizit über die Variablen, die Sie in Lambda-Ausdrücken erfassen, damit Sie identifizieren können, was Sie nach Wert im Vergleich zu Verweis erfassen. Aus diesem Grund wird empfohlen, die Option `[=]` oder `[&]` für Lambda-Ausdrücke nicht zu verwenden.

Häufig wird in einer Aufgabe in einer Fortsetzungskette eine Zuweisung zu einer Variablen vorgenommen und in einer anderen Aufgabe diese Variable gelesen. Sie können nicht nach Wert erfassen, da jede Fortsetzungsaufgabe eine andere Kopie der Variablen enthalten würde. Bei stapelgebundenen Variablen können Sie auch nicht als Verweis erfassen, da die Variable möglicherweise nicht mehr gültig ist.

Um dieses Problem zu lösen, verwenden Sie einen intelligenten Zeiger, z. B. [std::shared_ptr](../../standard-library/shared-ptr-class.md), um die Variable umzuschließen und den intelligenten Zeiger nach Wert zu übergeben. Auf diese Weise kann eine Zuweisung zum zugrunde liegenden Objekt erfolgen, und es kann aus diesem Objekt gelesen werden. Außerdem ist seine Lebensdauer länger als die der Aufgaben, die es verwenden. Verwenden Sie diese Methode auch, wenn die Variable ein Zeiger oder ein Handle mit Verweiszählung (`^`) für ein Windows-Runtime-Objekt ist. Hier ist ein grundlegendes Beispiel:

[!code-cpp[concrt-lambda-task-lifetime#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_1.cpp)]

Weitere Informationen zu Lambda-Ausdrücken finden Sie unter [Lambda-Ausdrücke](../../cpp/lambda-expressions-in-cpp.md).

## <a name="the-task-class"></a><a name="task-class"></a>Die Aufgabenklasse

Sie können die [Concurrency::task-Klasse](../../parallel/concrt/reference/task-class.md) verwenden, um Vorgänge in eine Reihe abhängiger Vorgänge zu verfassen. Dieses Kompositionsmodell wird durch den Begriff der *Fortsetzungen*unterstützt. Eine Fortsetzung ermöglicht die Ausführung von Code, wenn die vorherige oder *Vorgängeraufgabe*abgeschlossen ist. Das Ergebnis der Vorgängeraufgabe wird als Eingabe an eine oder mehrere Fortsetzungsaufgaben übergeben. Wenn eine Vorgängeraufgabe abgeschlossen wird, werden alle Fortsetzungsaufgaben, die darauf warten, für die Ausführung geplant. Jede Fortsetzungsaufgabe erhält eine Kopie des Ergebnisses der Vorgängeraufgabe. Diese Fortsetzungsaufgaben wiederum können auch Vorgängeraufgaben für andere Fortsetzungen sein, sodass sie eine Kette von Aufgaben bilden. Mit Fortsetzungen können Sie Ketten von Aufgaben beliebiger Länge erstellen, die bestimmte Abhängigkeiten untereinander aufweisen. Außerdem kann für eine Aufgabe der Abbruchmechanismus verwendet werden – entweder vor dem Start einer Aufgabe oder in kooperativer Weise, während die Aufgabe ausgeführt wird. Weitere Informationen zu diesem Stornierungsmodell finden Sie [unter Stornierung in der PPL](cancellation-in-the-ppl.md).

Bei `task` handelt es sich um eine Vorlagenklasse. Der Typparameter `T` gibt den Typ des Ergebnisses an, das von der Aufgabe erzeugt wird. Dieser Typ kann `void` sein, wenn die Aufgabe keinen Wert zurückgibt. Für `T` kann der `const`-Modifizierer nicht verwendet werden.

Wenn Sie eine Aufgabe erstellen, stellen Sie eine *Arbeitsfunktion* bereit, die den Aufgabentext ausführt. Bei dieser Arbeitsfunktion kann es sich um eine Lambda-Funktion, einen Funktionszeiger oder ein Funktionsobjekt handeln. Um zu warten, bis ein Vorgang abgeschlossen ist, ohne das Ergebnis zu erhalten, rufen Sie die [parallel::task::wait-Methode auf.](reference/task-class.md#wait) Die `task::wait` Methode gibt einen [parallel::task_status-Wert](reference/concurrency-namespace-enums.md#task_group_status) zurück, der beschreibt, ob die Aufgabe abgeschlossen oder abgebrochen wurde. Um das Ergebnis der Aufgabe zu erhalten, rufen Sie die [parallel::task::get-Methode auf.](reference/task-class.md#get) Von dieser Methode wird `task::wait` aufgerufen, um darauf zu warten, dass die Aufgabe beendet wird. Daher wird die Ausführung des aktuellen Threads blockiert, bis das Ergebnis zur Verfügung steht.

Im folgenden Beispiel wird gezeigt, wie eine Aufgabe erstellt, auf das Ergebnis gewartet und dessen Wert angezeigt wird. In den Beispielen in dieser Dokumentation werden Lambda-Funktionen verwendet, da sie eine kompaktere Syntax aufweisen. Sie können bei der Verwendung von Aufgaben jedoch auch Funktionszeiger und Funktionsobjekte verwenden.

[!code-cpp[concrt-basic-task#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_2.cpp)]

Wenn Sie die Funktion [concurrency::create_task](reference/concurrency-namespace-functions.md#create_task) verwenden, können Sie das `auto` Schlüsselwort verwenden, anstatt den Typ zu deklarieren. Betrachten Sie beispielsweise diesen Code, mit dem die Identitätsmatrix erstellt und ausgegeben wird:

[!code-cpp[concrt-create-task#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_3.cpp)]

Sie können die `create_task`-Funktion verwenden, um den entsprechenden Vorgang zu erstellen.

[!code-cpp[concrt-create-task#2](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_4.cpp)]

Wenn während der Ausführung einer Aufgabe eine Ausnahme ausgelöst wird, wird die Ausnahme von der Laufzeit im nachfolgenden Aufruf an `task::get`, `task::wait` oder eine aufgabenbasierte Fortsetzung gemarshallt. Weitere Informationen zum Mechanismus zur Behandlung von Aufgabenausnahmen finden Sie unter [Ausnahmebehandlung](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).

Ein Beispiel, `task`das [, concurrency::task_completion_event](../../parallel/concrt/reference/task-completion-event-class.md), Abbruch verwendet, finden Sie unter [Exemplarisierung: Verbinden mit Aufgaben und XML-HTTP-Anforderungen](../../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md). (Die `task_completion_event`-Klasse wird weiter unten in diesem Dokument beschrieben.)

> [!TIP]
> Weitere Informationen zu Aufgaben in UWP-Apps finden Sie unter [Asynchrone Programmierung in C++](/windows/uwp/threading-async/asynchronous-programming-in-cpp-universal-windows-platform-apps) und [Erstellen asynchroner Vorgänge in C++ für UWP-Apps](../../parallel/concrt/creating-asynchronous-operations-in-cpp-for-windows-store-apps.md).

## <a name="continuation-tasks"></a><a name="continuations"></a>Fortsetzungsaufgaben

Bei der asynchronen Programmierung werden nach Abschluss eines asynchronen Vorgangs häufig ein zweiter Vorgang aufgerufen und Daten an diesen weitergegeben. Herkömmlicherweise werden hierfür Rückrufmethoden verwendet. In der Concurrency Runtime wird die gleiche Funktionalität durch *Fortsetzungsaufgaben*bereitgestellt. Eine Fortsetzungsaufgabe (auch als Fortsetzung bezeichnet) ist eine asynchrone Aufgabe, die von einer anderen Aufgabe aufgerufen wird, die als *Vorgänger*bezeichnet wird, wenn der Vorgänger abgeschlossen wird. Mithilfe von Fortsetzungen können Sie folgende Aufgaben ausführen:

- Übergeben von Daten vom Vorgänger an die Fortsetzung

- Angeben der präzisen Bedingungen, unter denen die Fortsetzung aufgerufen bzw. nicht aufgerufen wird

- Abbrechen einer Fortsetzung, bevor diese gestartet wird oder kooperativ während sie ausgeführt wird

- Bereitstellen von Hinweisen zur Planung der Fortsetzung (Dies gilt nur für UWP-Apps (Universelle Windows-Plattform). Weitere Informationen finden Sie unter [Erstellen von asynchronen Vorgängen in C++ für UWP-Apps](../../parallel/concrt/creating-asynchronous-operations-in-cpp-for-windows-store-apps.md).)

- Aufrufen mehrerer Fortsetzungen durch den gleichen Vorgänger

- Aufrufen einer Fortsetzung, wenn alle Vorgänger oder einer der Vorgänger abgeschlossen wird

- Verketten von Fortsetzungen auf eine beliebige Länge

- Behandeln von durch den Vorgänger ausgelöste Ausnahmen mithilfe einer Fortsetzung

Mithilfe dieser Funktionen können Sie eine oder mehrere Aufgaben ausführen, wenn die erste Aufgabe abgeschlossen wird. Sie können beispielsweise eine Fortsetzung erstellen, in der eine Datei komprimiert wird, nachdem sie von der ersten Aufgabe vom Datenträger gelesen wurde.

Im folgenden Beispiel wird das vorherige geändert, um die [parallel::task::then-Methode](reference/task-class.md#then) zum Planen einer Fortsetzung zu verwenden, die den Wert der Vorgängeraufgabe druckt, wenn sie verfügbar ist.

[!code-cpp[concrt-basic-continuation#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_5.cpp)]

Sie können Aufgaben auf eine beliebige Länge verketten und schachteln. Eine Aufgabe kann auch über mehrere Fortsetzungen verfügen. Im folgenden Beispiel wird eine einfache Fortsetzungskette dargestellt, in der der Wert der vorherigen Aufgabe dreimal erhöht wird.

[!code-cpp[concrt-continuation-chain#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_6.cpp)]

Eine Fortsetzung kann auch eine andere Aufgabe zurückgeben. Wenn kein Abbruch erfolgt, wird diese Aufgabe vor der nachfolgenden Fortsetzung ausgeführt. Diese Technik wird als *asynchrones Entpacken*bezeichnet. Das asynchrone Entpacken ist nützlich, wenn Sie zusätzliche Arbeitsvorgänge im Hintergrund ausführen möchten, jedoch nicht möchten, dass der aktuelle Thread durch die aktuelle Aufgabe blockiert wird. (Dies ist in UWP-Apps üblich, in denen Fortsetzungen im UI-Thread ausgeführt werden können). Im folgenden Beispiel werden drei Aufgaben gezeigt. Die erste Aufgabe gibt eine andere Aufgabe zurück, die vor einer Fortsetzungsaufgabe ausgeführt wird.

[!code-cpp[concrt-async-unwrapping#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_7.cpp)]

> [!IMPORTANT]
> Wenn eine Fortsetzung einer Aufgabe eine geschachtelte Aufgabe vom Typ `N` zurückgibt, ist die resultierende Aufgabe vom Typ `N`, nicht vom Typ `task<N>`, und wird abgeschlossen, wenn die geschachtelte Aufgabe abgeschlossen wird. Das heißt, die Fortsetzung entpackt die geschachtelte Aufgabe.

## <a name="value-based-versus-task-based-continuations"></a><a name="value-versus-task"></a>Wertbasierte versus aufgabenbasierte Fortsetzungen

Bei einem `task`-Objekt, dessen Rückgabetyp `T` ist, können Sie einen Wert des Typs `T` oder `task<T>` für die zugehörigen Fortsetzungsaufgaben bereitstellen. Eine Fortsetzung, `T` die den Typ annimmt, wird als *wertbasierte Fortsetzung*bezeichnet. Eine wertbasierte Fortsetzung wird für die Ausführung geplant, wenn die Vorgängeraufgabe ohne Fehler abgeschlossen und nicht abgebrochen wird. Eine Fortsetzung, `task<T>` die den Typ als Parameter annimmt, wird als *aufgabenbasierte Fortsetzung*bezeichnet. Die Ausführung einer aufgabenbasierten Fortsetzung wird immer für den Zeitpunkt geplant, zu dem die Vorgängeraufgabe abgeschlossen ist, auch wenn die Vorgängeraufgabe abgebrochen wird oder wenn diese eine Ausnahme auslöst. Sie können dann `task::get` aufrufen, um das Ergebnis der Vorgängeraufgabe abzurufen. Wenn die Vorgängeraufgabe abgebrochen wurde, `task::get` wird [parallel::task_canceled](../../parallel/concrt/reference/task-canceled-class.md). Wenn von der Vorgängeraufgabe eine Ausnahme ausgelöst wurde, wird von `task::get` diese Ausnahme erneut ausgelöst. Eine aufgabenbasierte Fortsetzung wird nicht als abgebrochen markiert, wenn die zugehörige Vorgängeraufgabe abgebrochen wird.

## <a name="composing-tasks"></a><a name="composing-tasks"></a>Komponieren von Aufgaben

In diesem Abschnitt werden die Funktionen [concurrency::when_all](reference/concurrency-namespace-functions.md#when_all) und [concurrency::when_any](reference/concurrency-namespace-functions.md#when_all) beschrieben, mit denen Sie mehrere Aufgaben zum Implementieren allgemeiner Muster erstellen können.

### <a name="the-when_all-function"></a><a name="when-all"></a>Die when_all-Funktion

Von der `when_all`-Funktion wird eine Aufgabe erstellt, die abgeschlossen wird, nachdem ein Satz von Aufgaben abgeschlossen wurde. Diese Funktion gibt ein std::[Vektorobjekt](../../standard-library/vector-class.md) zurück, das das Ergebnis jeder Aufgabe in der Gruppe enthält. Im folgenden einfachen Beispiel wird mithilfe von `when_all` eine Aufgabe erstellt, die den Abschluss von drei anderen Aufgaben darstellt.

[!code-cpp[concrt-join-tasks#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_8.cpp)]

> [!NOTE]
> Die Aufgaben, die Sie an `when_all` übergeben, müssen einheitlich sein. Das heißt, sie müssen alle den gleichen Typ zurückgeben.

Sie können auch die Syntax `&&` verwenden, um eine Aufgabe zu erstellen, die nach Abschluss eines Satzes von Aufgaben abgeschlossen wird, wie im folgenden Beispiel gezeigt.

`auto t = t1 && t2; // same as when_all`

Es ist üblich, eine Fortsetzung zusammen mit `when_all` zu verwenden, um eine Aktion auszuführen, nachdem ein Satz von Aufgaben abgeschlossen wurde. Im folgenden Beispiel wird das vorherige so geändert, dass die Summe von drei Aufgaben ausgegeben wird, die jeweils ein Ergebnis vom Typ `int` liefern.

[!code-cpp[concrt-join-tasks#2](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_9.cpp)]

In diesem Beispiel können Sie auch `task<vector<int>>` angeben, um eine aufgabenbasierte Fortsetzung zu erstellen.

Wenn eine Aufgabe in einem Satz von Aufgaben abgebrochen wird oder eine Ausnahme auslöst, wird `when_all` sofort abgeschlossen und wartet nicht, bis die übrigen Aufgaben beendet sind. Wenn eine Ausnahme ausgelöst wird, löst die Laufzeit die Ausnahme erneut aus, wenn Sie `task::get` oder `task::wait` für das Task-Objekt aufrufen, das von `when_all` zurückgegeben wird. Wenn von mehr als einer Aufgabe eine Ausnahme ausgelöst wird, wird von der Laufzeit eine ausgewählt. Daher müssen Sie sicherstellen, dass Sie alle Ausnahmen nach Abschluss aller Aufgaben berücksichtigen. Eine nicht behandelte Ausnahme einer Aufgabe führt dazu, dass die App beendet wird.

Hier ist eine Dienstprogrammfunktion, die Sie verwenden können, um sicherzustellen, dass Ihr Programm alle Ausnahmen einhält. Die Funktion `observe_all_exceptions` löst für jede Aufgabe im bereitgestellten Bereich jede aufgetretene Ausnahme aus, damit diese erneut ausgelöst wird, und "schluckt" diese anschließend.

[!code-cpp[concrt-eh-when_all#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_10.cpp)]

Betrachten Sie eine UWP-App, die C++ und XAML verwendet und eine Reihe von Dateien auf den Datenträger schreibt. Im folgenden Beispiel wird gezeigt, wie `when_all` und `observe_all_exceptions` verwendet werden, um sicherzustellen, dass das Programm alle Ausnahmen berücksichtigt.

[!code-cpp[concrt-eh-when_all#2](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_11.cpp)]

##### <a name="to-run-this-example"></a>So führen Sie dieses Beispiel aus

1. Fügen Sie in "MainPage.xaml" ein `Button`-Steuerelement hinzu.

[!code-xml[concrt-eh-when_all#3](../../parallel/concrt/codesnippet/xaml/task-parallelism-concurrency-runtime_12.xaml)]

1. Fügen Sie in "MainPage.xaml.h" diese Vorwärtsdeklarationen zum Abschnitt `private` der `MainPage`-Klassendeklaration hinzu.

[!code-cpp[concrt-eh-when_all#4](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_13.h)]

1. Implementieren Sie in "MainPage.xaml.cpp" den `Button_Click`-Ereignishandler.

[!code-cpp[concrt-eh-when_all#5](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_14.cpp)]

1. Implementieren Sie in "MainPage.xaml.cpp" `WriteFilesAsync` wie im Beispiel dargestellt.

> [!TIP]
> `when_all` ist eine nicht blockierende Funktion, die `task` als Ergebnis erzeugt. Im Gegensatz zu [task::wait](reference/task-class.md#wait)ist es sicher, diese Funktion in einer UWP-App im ASTA-Thread (Application STA) aufzurufen.

### <a name="the-when_any-function"></a><a name="when-any"></a>Die when_any Funktion

Die `when_any`-Funktion erstellt eine Aufgabe, die abgeschlossen wird, wenn die erste Aufgabe in einem Satz von Aufgaben abgeschlossen wird. Diese Funktion gibt ein [std::pair-Objekt](../../standard-library/pair-structure.md) zurück, das das Ergebnis der abgeschlossenen Aufgabe und den Index dieser Aufgabe in der Gruppe enthält.

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
> Wie `when_all`bei `when_any` ist nicht blockierend und sicher in einer UWP-App im ASTA-Thread aufzurufen.

## <a name="delayed-task-execution"></a><a name="delayed-tasks"></a>Verzögerte Aufgabenausführung

In einigen Fällen ist es notwendig, die Ausführung einer Aufgabe zu verzögern, bis eine Bedingung erfüllt ist, oder eine Aufgabe als Reaktion auf ein externes Ereignis zu starten. Bei der asynchronen Programmierung müssen Sie zum Beispiel möglicherweise eine Aufgabe als Reaktion auf ein E/A-Abschlussereignis starten.

Zwei Möglichkeiten, dies zu erreichen, sind die Verwendung einer Fortsetzung oder das Starten einer Aufgabe und das Warten auf ein Ereignis innerhalb der Arbeitsfunktion des Tasks. Allerdings gibt es Fälle, in denen es nicht möglich, eine dieser Techniken zu verwenden. Sie müssen beispielsweise über die Vorgängeraufgabe verfügen, um eine Fortsetzung zu erstellen. Wenn Sie jedoch nicht über die Vorgängeraufgabe verfügen, können Sie ein *Vorgangsabschlussereignis* erstellen und dieses Abschlussereignis später mit der Vorgängeraufgabe verketten, sobald sie verfügbar ist. Da eine wartende Aufgabe auch einen Thread blockiert, können Sie Aufgabenabschlussereignisse außerdem dazu verwenden, Arbeitsvorgänge auszuführen, wenn ein asynchroner Vorgang abgeschlossen wird, und dadurch einen Thread freigeben.

Die [parallel::task_completion_event-Klasse](../../parallel/concrt/reference/task-completion-event-class.md) vereinfacht diese Aufgabenzusammensetzung. Wie die `task`-Klasse ist der Typparameter `T` der Typ des Ergebnisses, das von der Aufgabe erzeugt wird. Dieser Typ kann `void` sein, wenn die Aufgabe keinen Wert zurückgibt. Für `T` kann der `const`-Modifizierer nicht verwendet werden. In der Regel wird ein `task_completion_event`-Objekt für einen Thread oder eine Aufgabe bereitgestellt, der bzw. die signalisieren, wenn der Wert für das Objekt zur Verfügung steht. Gleichzeitig wird mindestens eine Aufgabe als Listener dieses Ereignisses festgelegt. Wenn das Ereignis festgelegt wird, werden die Listeneraufgaben abgeschlossen und ihre Fortsetzungen für die Ausführung geplant.

Ein Beispiel, `task_completion_event` das zum Implementieren einer Aufgabe verwendet wird, die nach einer Verzögerung abgeschlossen wird, finden Sie unter [Gewusst wie: Erstellen einer Aufgabe, die nach einer Verzögerung abgeschlossen wird.](../../parallel/concrt/how-to-create-a-task-that-completes-after-a-delay.md)

## <a name="task-groups"></a><a name="task-groups"></a>Aufgabengruppen

Eine *Aufgabengruppe* organisiert eine Auflistung von Vorgängen. Aufgabengruppen verschieben Aufgaben in eine Arbeitsübernahme-Warteschlange. Der Planer entfernt Aufgaben aus dieser Warteschlange und führt sie auf verfügbaren Computerressourcen aus. Nachdem Sie einer Aufgabengruppe Aufgaben hinzugefügt haben, können Sie warten, bis alle Aufgaben aufgeführt wurden, oder Sie können Aufgaben abbrechen, die noch nicht gestartet wurden.

Die PPL verwendet die [Klassen concurrency::task_group](reference/task-group-class.md) und [concurrency::structured_task_group,](../../parallel/concrt/reference/structured-task-group-class.md) um Aufgabengruppen darzustellen, und die [Parallelität::task_handle-Klasse,](../../parallel/concrt/reference/task-handle-class.md) um die Aufgaben darzustellen, die in diesen Gruppen ausgeführt werden. In der `task_handle`-Klasse wird der Code gekapselt, der die Arbeit ausführt. Wie die `task`-Klasse steht die Arbeitsfunktion in Form einer Lambda-Funktion, eines Funktionszeigers oder eines Funktionsobjekts zur Verfügung. In der Regel ist es nicht erforderlich, direkt mit `task_handle`-Objekten zu arbeiten. Stattdessen übergeben Sie Arbeitsfunktionen an eine Aufgabengruppe, die die `task_handle`-Objekte erstellt und verwaltet.

Die PPL unterteilt Aufgabengruppen in diese beiden Kategorien: *unstrukturierte Aufgabengruppen* und *strukturierte Aufgabengruppen*. In der PPL werden unstrukturierte Aufgabengruppen mithilfe der `task_group`-Klasse und strukturierte Aufgabengruppen mithilfe der `structured_task_group`-Klasse dargestellt.

> [!IMPORTANT]
> Die PPL definiert auch den [Concurrency::parallel_invoke-Algorithmus,](reference/concurrency-namespace-functions.md#parallel_invoke) der die `structured_task_group` Klasse verwendet, um eine Reihe von Aufgaben parallel auszuführen. Da der `parallel_invoke`-Algorithmus eine kompaktere Syntax aufweist, wird empfohlen, diesen, sofern möglich, anstelle der `structured_task_group`-Klasse zu verwenden. Das Thema [Parallelalgorithmen](../../parallel/concrt/parallel-algorithms.md) wird ausführlicher beschrieben. `parallel_invoke`

Verwenden Sie `parallel_invoke`, um mehrere unabhängige Aufgaben gleichzeitig auszuführen und sofort darauf zu warten, dass alle Aufgaben abgeschlossen sind. Diese Technik wird oft als Gabel bezeichnet *und schließt sich* paralleler Art an. Verwenden Sie `task_group`, um mehrere unabhängige Aufgaben gleichzeitig auszuführen und später darauf zu warten, dass allle Aufgaben abgeschlossen sind. Beispielsweise können Sie einem `task_group`-Objekt Aufgaben hinzufügen und in einer anderen Funktion oder einem anderen Thread darauf warten, dass die Aufgaben beendet werden.

Aufgabengruppen unterstützen das Konzept eines Abbruchs. Mit einem Abbruch können Sie für alle aktiven Aufgaben angeben, dass der gesamte Vorgang abgebrochen werden soll. Durch den Abbruch wird außerdem verhindert, dass Aufgaben gestartet werden, die noch nicht gestartet wurden. Weitere Informationen zur Stornierung finden Sie [unter Stornierung in der PPL](cancellation-in-the-ppl.md).

Die Laufzeit stellt außerdem ein Modell für die Ausnahmebehandlung bereit, mit dem Sie eine Ausnahme für eine Aufgabe auslösen und behandeln können, während Sie darauf warten, das die zugeordnete Aufgabengruppe fertig gestellt wird. Weitere Informationen zu diesem Ausnahmebehandlungsmodell finden Sie unter [Ausnahmebehandlung](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).

## <a name="comparing-task_group-to-structured_task_group"></a><a name="comparing-groups"></a>Vergleich task_group mit structured_task_group

Grundsätzlich wird die Verwendung von `task_group` oder `parallel_invoke` anstelle der `structured_task_group`-Klasse empfohlen. In Einzelfällen, beispielsweise beim Schreiben eines parallelen Algorithmus für eine variable Anzahl von Aufgaben oder mit der Möglichkeit eines Abbruchs, können Sie jedoch `structured_task_group` verwenden. In diesem Abschnitt werden die Unterschiede zwischen der `task_group`-Klasse und der `structured_task_group`-Klasse erläutert.

Die `task_group`-Klasse ist threadsicher. Sie können einem `task_group`-Objekt daher Aufgaben von mehreren Threads hinzufügen und in mehreren Threads auf ein `task_group`-Objekt warten oder dieses abbrechen. Das Erstellen und Zerstören eines `structured_task_group`-Objekts muss im gleichen lexikalischen Gültigkeitsbereich erfolgen. Darüber hinaus müssen alle Vorgänge für ein `structured_task_group`-Objekt im gleichen Thread ausgeführt werden. Die Ausnahme von dieser Regel sind die [Methoden concurrency::structured_task_group::cancel](reference/structured-task-group-class.md#cancel) und [concurrency::structured_task_group::is_canceling.](reference/structured-task-group-class.md#is_canceling) Eine untergeordnete Aufgabe kann diese Methoden aufrufen, um die übergeordnete Aufgabengruppe abzubrechen oder das Abbrechen jederzeit zu überprüfen.

Sie können zusätzliche Aufgaben `task_group` für ein Objekt ausführen, nachdem Sie die [Parallelität::task_group::wait](reference/task-group-class.md#wait) oder [concurrency::task_group::run_and_wait-Methode](reference/task-group-class.md#run_and_wait) aufrufen. Umgekehrt, wenn Sie zusätzliche Aufgaben `structured_task_group` für ein Objekt ausführen, nachdem Sie die [Methoden concurrency::structured_task_group::wait](reference/structured-task-group-class.md#wait) oder [concurrency::structured_task_group::run_and_wait](reference/structured-task-group-class.md#run_and_wait) aufrufen, ist das Verhalten nicht definiert.

Da die `structured_task_group`-Klasse nicht threadübergreifend synchronisiert, ist ihr Ausführungsaufwand im Vergleich zur `task_group`-Klasse geringer. Wenn die Planung von Arbeit für mehrere Threads nicht Teil eines Problems ist und der `parallel_invoke`-Algorithmus nicht verwendet werden kann, können Sie mit der `structured_task_group`-Klasse leistungsfähigeren Code schreiben.

Wenn Sie ein `structured_task_group`-Objekt in einem anderen `structured_task_group`-Objekt verwenden, muss das innere Objekt abgeschlossen und zerstört sein, bevor das äußere Objekt beendet wird. Bei der `task_group`-Klasse ist die Fertigstellung geschachtelter Aufgabengruppen vor der äußeren Gruppe nicht erforderlich.

Unstrukturierte Aufgabengruppen und strukturierte Aufgabengruppen verwenden Aufgabenhandles auf unterschiedliche Weise. Sie können Arbeitsfunktionen direkt an ein `task_group`-Objekt übergeben; das Aufgabenhandle wird unmittelbar vom `task_group`-Objekt für Sie erstellt und verwaltet. Die `structured_task_group`-Klasse erfordert die Verwaltung eines `task_handle`-Objekts für jede Aufgabe. Jedes `task_handle`-Objekt muss über die gesamte Lebensdauer des zugeordneten `structured_task_group`-Objekts hinweg gültig sein. Verwenden Sie die [Funktion concurrency::make_task,](reference/concurrency-namespace-functions.md#make_task) um ein `task_handle` Objekt zu erstellen, wie im folgenden grundlegenden Beispiel gezeigt:

[!code-cpp[concrt-make-task-structure#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_16.cpp)]

Verwenden Sie eine Stapelzuordnungsroutine, z. B. [_malloca](../../c-runtime-library/reference/malloca.md) oder eine Containerklasse, z. B. std::[vector](../../standard-library/vector-class.md).

`task_group` und `structured_task_group` unterstützen die Möglichkeit eines Abbruchs. Weitere Informationen zur Stornierung finden Sie [unter Stornierung in der PPL](cancellation-in-the-ppl.md).

## <a name="example"></a><a name="example"></a>Beispiel

Im folgenden grundlegenden Beispiel wird die Verwendung von Aufgabengruppen veranschaulicht. In diesem Beispiel werden vom `parallel_invoke`-Algorithmus zwei Aufgaben gleichzeitig ausgeführt. In jeder Aufgabe werden einem `task_group`-Objekt untergeordnete Aufgaben hinzugefügt. Die `task_group`-Klasse ermöglicht das zeitgleiche Hinzufügen für mehrere Aufgaben.

[!code-cpp[concrt-using-task-groups#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_17.cpp)]

Nachfolgend wird eine Beispielausgabe für dieses Beispiel angezeigt:

```Output
Message from task: Hello
Message from task: 3.14
Message from task: 42
```

Da die Aufgaben vom `parallel_invoke`-Algorithmus gleichzeitig ausgeführt werden, kann sich die Reihenfolge der Ausgabemeldungen unterscheiden.

Beispiele für die Verwendung des `parallel_invoke` Algorithmus finden Sie unter [How to: Verwenden parallel_invoke zum Schreiben einer parallelen Sortierroutine](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md) und [How to: Use parallel_invoke to Execute Parallel Operations](../../parallel/concrt/how-to-use-parallel-invoke-to-execute-parallel-operations.md). Ein vollständiges Beispiel, `task_group` das die Klasse zum Implementieren asynchroner Futures verwendet, finden Sie unter [Exemplarweiter Vorgehensweise: Implementieren von Futures](../../parallel/concrt/walkthrough-implementing-futures.md).

## <a name="robust-programming"></a><a name="robust"></a>Robuste Programmierung

Es ist wichtig, dass Sie die Rolle des Abbruchs und der Ausnahmebehandlung verstehen, wenn Sie Aufgaben, Aufgabengruppen und parallele Algorithmen verwenden. Beispielweise kann eine abgebrochene Aufgabe in einer Struktur paralleler Arbeitsaufgaben dazu führen, dass untergeordnete Aufgaben nicht ausgeführt werden. Dies kann Probleme verursachen, wenn eine der untergeordneten Aufgaben einen Vorgang ausführen soll, der für die Anwendung von Bedeutung ist, beispielsweise das Freigeben einer Ressource. Wenn eine untergeordnete Aufgabe eine Ausnahme auslöst, kann diese Ausnahme außerdem über einen Objektdestruktor weitergeben werden und nicht definiertes Verhalten in der Anwendung auslösen. Ein Beispiel, das diese Punkte veranschaulicht, finden Sie im Abschnitt [Verstehen, wie Abbruch und Ausnahmebehandlung die Objektzerstörung beeinflussen,](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md#object-destruction) in den Best Practices im Dokument Parallel Patterns Library. Weitere Informationen zu den Abbruch- und Ausnahmebehandlungsmodellen in der PPL finden Sie unter [Abbruch-](../../parallel/concrt/cancellation-in-the-ppl.md) und [Ausnahmebehandlung](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).

## <a name="related-topics"></a>Verwandte Themen

|Titel|BESCHREIBUNG|
|-----------|-----------------|
|[Gewusst wie: Verwenden von parallel_invoke zum Schreiben einer Runtime für paralleles Sortieren](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md)|Erläutert, wie die Leistung des bitonischen Sortieralgorithmus mit dem `parallel_invoke`-Algorithmus verbessert werden.|
|[Gewusst wie: Verwenden parallel_invoke zum Ausführen paralleler Vorgänge](../../parallel/concrt/how-to-use-parallel-invoke-to-execute-parallel-operations.md)|Erläutert, wie die Leistung eines Programms mit dem `parallel_invoke`-Algorithmus verbessert werden kann, das mehrere Vorgänge in einer freigegebenen Datenquelle ausführt.|
|[Gewusst wie: Erstellen einer Aufgabe, die nach einer Verzögerung abgeschlossen wird](../../parallel/concrt/how-to-create-a-task-that-completes-after-a-delay.md)|Zeigt, wie `task`die `cancellation_token_source` `cancellation_token`Klassen `task_completion_event` , , und Klassen verwendet werden, um eine Aufgabe zu erstellen, die nach einer Verzögerung abgeschlossen wird.|
|[Exemplarische Vorgehensweise: Implementieren von Futures](../../parallel/concrt/walkthrough-implementing-futures.md)|Zeigt, wie die vorhandene Funktionalität in der Concurrency Runtime kombiniert werden kann, um mehr Funktionalität zu erreichen.|
|[Parallel Patterns Library (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)|Beschreibt die PPL, die ein obligatorisches Programmiermodell zum Entwickeln gleichzeitiger Anwendungen bereitstellt.|

## <a name="reference"></a>Verweis

[task-Klasse (Concurrency Runtime)](../../parallel/concrt/reference/task-class.md)

[task_completion_event-Klasse](../../parallel/concrt/reference/task-completion-event-class.md)

[when_all-Funktion](reference/concurrency-namespace-functions.md#when_all)

[when_any-Funktion](reference/concurrency-namespace-functions.md#when_any)

[task_group-Klasse](reference/task-group-class.md)

[parallel_invoke Funktion](reference/concurrency-namespace-functions.md#parallel_invoke)

[structured_task_group-Klasse](../../parallel/concrt/reference/structured-task-group-class.md)
