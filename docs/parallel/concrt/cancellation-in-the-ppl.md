---
title: Abbruch in der PPL
ms.date: 11/19/2018
helpviewer_keywords:
- parallel algorithms, canceling [Concurrency Runtime]
- canceling parallel algorithms [Concurrency Runtime]
- parallel tasks, canceling [Concurrency Runtime]
- cancellation in the PPL
- parallel work trees [Concurrency Runtime]
- canceling parallel tasks [Concurrency Runtime]
ms.assetid: baaef417-b2f9-470e-b8bd-9ed890725b35
ms.openlocfilehash: 27c0ea3cfcf62060800c1c0b034dde7de6357250
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368493"
---
# <a name="cancellation-in-the-ppl"></a>Abbruch in der PPL

In diesem Dokument wird die Rolle des Abbruchs in der Parallel Patterns Library (PPL) erläutert und beschrieben, wie Sie die parallele Arbeitsvorgänge abbrechen, und wie Sie erkennen können, ob parallele Arbeitsvorgänge abgebrochen wurden.

> [!NOTE]
> Die Laufzeit implementiert Abbrüche mithilfe der Ausnahmebehandlung. Diese Ausnahmen dürfen im eigenen Code nicht abgefangen oder behandelt werden. Außerdem empfiehlt es sich, ausnahmesicheren Code in den Funktionsrümpfen der Aufgaben zu schreiben. Sie können z. B. das *RAII-Muster (Resource Acquisition Is Initialization)* verwenden, um sicherzustellen, dass Ressourcen ordnungsgemäß behandelt werden, wenn eine Ausnahme im Hauptteil eines Vorgangs ausgelöst wird. Ein vollständiges Beispiel, das das RAII-Muster zum Bereinigen einer Ressource in einem abbruchfähigen Vorgang verwendet, finden Sie unter [Exemplarische Vorgehensweise: Entfernen von Arbeit aus einem Benutzeroberflächenthread](../../parallel/concrt/walkthrough-removing-work-from-a-user-interface-thread.md).

## <a name="key-points"></a>Die wichtigsten Punkte

- Das Abbrechen ist ein kooperativer Vorgang und beinhaltet die Koordination zwischen dem Code, der den Abbruch verlangt, und der Aufgabe, die auf den Abbruch reagieren muss.

- Verwenden Sie wenn möglich Abbruchtoken, um Arbeitsvorgänge abzubrechen. Die [concurrency::cancellation_token-Klasse](../../parallel/concrt/reference/cancellation-token-class.md) definiert ein Abbruchtoken.

- Wenn Sie Abbruchtoken verwenden, verwenden Sie die [parallelcurrency::cancellation_token_source::cancel-Methode,](reference/cancellation-token-source-class.md#cancel) um den Abbruch zu initiieren, und die [Concurrency::cancel_current_task-Funktion,](reference/concurrency-namespace-functions.md#cancel_current_task) um auf Denerzugung zu reagieren. Verwenden Sie die [parallelcurrency::cancellation_token:is_canceled-Methode,](reference/cancellation-token-class.md#is_canceled) um zu überprüfen, ob eine andere Aufgabe einen Abbruch angefordert hat.

- Der Abbruch erfolgt nicht unmittelbar. Obwohl neue Arbeit nicht gestartet wird, wenn eine Aufgabe oder Aufgabengruppe abgebrochen wird, muss die aktive Arbeit nach einem Abbruch suchen und darauf reagieren.

- Eine wertbasierte Fortsetzung erbt das Abbruchtoken ihrer Vorgängeraufgabe. Eine aufgabenbasierte Fortsetzung erbt das Token der Vorgängeraufgabe dagegen nicht.

- Verwenden Sie die [parallel::cancellation_token::none-Methode,](reference/cancellation-token-class.md#none) wenn Sie einen `cancellation_token` Konstruktor oder eine Funktion aufrufen, die ein Objekt verwendet, aber Sie möchten nicht, dass der Vorgang kannbar sein. Wenn Sie kein Abbruchtoken an den [Concurrency::task-Konstruktor](../../parallel/concrt/reference/task-class.md) oder die [Concurrency::create_task-Funktion](reference/concurrency-namespace-functions.md#create_task) übergeben, kann diese Aufgabe nicht mehr ausgeführt werden.

## <a name="in-this-document"></a><a name="top"></a>In diesem Dokument

- [Parallele Arbeitsstrukturen](#trees)

- [Abbrechen von parallelen Aufgaben](#tasks)

  - [Verwenden eines Abbruchtokens zum Abbrechen paralleler Aufgaben](#tokens)

  - [Abbrechen paralleler Aufgaben mit der cancel-Methode](#cancel)

  - [Abbrechen paralleler Aufgaben mit Ausnahmen](#exceptions)

- [Abbrechen von parallelen Algorithmen](#algorithms)

- [Wann ein Abbruch nicht verwendet werden sollte](#when)

## <a name="parallel-work-trees"></a><a name="trees"></a>Parallele Arbeitsbäume

Differenzierte Aufgaben und Berechnungen werden in der PPL mithilfe von Aufgaben und Aufgabengruppen verwaltet. Sie können Aufgabengruppen verschachteln, um *Strukturen* mit paralleler Arbeit zu bilden. Die folgende Abbildung zeigt eine parallele Arbeitsstruktur. In dieser Abbildung stellen `tg1` und `tg2` Aufgabengruppen dar; `t1`, `t2`, `t3`, `t4` und `t5` stellen die Arbeitsvorgänge dar, die von den Aufgabengruppen durchgeführt wird.

![Parallele Arbeitsstruktur](../../parallel/concrt/media/parallelwork_trees.png "Parallele Arbeitsstruktur")

Das folgende Beispiel zeigt den Code, der zum Erstellen der Struktur in der Abbildung erforderlich ist. In diesem `tg1` Beispiel `tg2` und sind [parallel::structured_task_group-Objekte;](../../parallel/concrt/reference/structured-task-group-class.md) `t1`, `t2` `t3`, `t4`, `t5` und sind [concurrency::task_handle-Objekte.](../../parallel/concrt/reference/task-handle-class.md)

[!code-cpp[concrt-task-tree#1](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_1.cpp)]

Sie können auch die [Concurrency::task_group-Klasse](reference/task-group-class.md) verwenden, um eine ähnliche Arbeitsstruktur zu erstellen. Die [Concurrency::task-Klasse](../../parallel/concrt/reference/task-class.md) unterstützt auch den Begriff eines Arbeitsbaums. Eine `task`-Struktur ist jedoch eine Abhängigkeitsstruktur. In einer `task`-Struktur werden zukünftige Arbeitsvorgänge nach aktuellen Arbeitsvorgängen abgeschlossen. In einer Aufgabengruppenstruktur werden interne Arbeitsvorgänge vor externen Arbeitsvorgängen abgeschlossen. Weitere Informationen zu den Unterschieden zwischen Vorgängen und Aufgabengruppen finden Sie unter [Vorgangsparallelität](../../parallel/concrt/task-parallelism-concurrency-runtime.md).

[[Oben](#top)]

## <a name="canceling-parallel-tasks"></a><a name="tasks"></a>Abbrechen paralleler Aufgaben

Es gibt verschiedene Möglichkeiten, parallele Arbeitsvorgänge abzubrechen. Die bevorzugte Methode ist, ein Abbruchtoken zu verwenden. Aufgabengruppen unterstützen auch die [parallel::task_group::cancel-Methode](reference/task-group-class.md#cancel) und die [parallelcurrency::structured_task_group::cancel-Methode.](reference/structured-task-group-class.md#cancel) Eine letzte Möglichkeit ist, im Text einer Arbeitsfunktion einer Aufgabe eine Ausnahme auszulösen. Unabhängig von der gewählten Methode sollten Sie bedenken, dass der Abbruch nicht sofort auftritt. Obwohl neue Arbeit nicht gestartet wird, wenn eine Aufgabe oder Aufgabengruppe abgebrochen wird, muss die aktive Arbeit nach einem Abbruch suchen und darauf reagieren.

Weitere Beispiele, die parallele Aufgaben abbrechen, finden Sie unter [Exemplarische Vorgehensweise: Verbinden mit Aufgaben und XML-HTTP-Anforderungen](../../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md), [Gewusst wie: Verwenden](../../parallel/concrt/how-to-use-cancellation-to-break-from-a-parallel-loop.md)von Abbruch aus einer parallelen Schleife und [Gewusst wie: Verwenden](../../parallel/concrt/how-to-use-exception-handling-to-break-from-a-parallel-loop.md)der Ausnahmebehandlung zum Unterbrechen von einer parallelen Schleife .

### <a name="using-a-cancellation-token-to-cancel-parallel-work"></a><a name="tokens"></a>Verwenden eines Abbruchtokens zum Abbrechen paralleler Arbeit

Die Klassen `task`, `task_group` und `structured_task_group` unterstützen Abbruchvorgänge durch die Verwendung von Abbruchtoken. Die PPL definiert die [Klassen concurrency::cancellation_token_source](../../parallel/concrt/reference/cancellation-token-source-class.md) und [concurrency::cancellation_token](../../parallel/concrt/reference/cancellation-token-class.md) für diesen Zweck. Wenn Sie Arbeit mithilfe eines Abbruchtokens abbrechen, wird von der Runtime keine neue Verarbeitung gestartet, die dieses Token abonniert. Bereits aktive Arbeit kann [is_canceled](../../parallel/concrt/reference/cancellation-token-class.md#is_canceled) die is_canceled-Memberfunktion verwenden, um das Abbruchtoken zu überwachen und zu beenden, wenn dies möglich ist.

Um den Abbruch zu initiieren, rufen Sie die [parallel::cancellation_token_source::cancel-Methode](reference/cancellation-token-source-class.md#cancel) auf. Auf Abbrüche reagieren Sie folgendermaßen:

- Verwenden `task` Sie für Objekte die [Funktion concurrency::cancel_current_task.](reference/concurrency-namespace-functions.md#cancel_current_task) `cancel_current_task` bricht die aktuelle Aufgabe und alle wertbasierten Fortsetzungen ab. (Das *Abbruchtoken,* das der Aufgabe oder ihren Fortsetzungen zugeordnet ist, wird nicht abgebrochen.)

- Verwenden Sie für Aufgabengruppen und parallele Algorithmen die [Funktion concurrency::is_current_task_group_canceling,](reference/concurrency-namespace-functions.md#is_current_task_group_canceling) um Abbruch und Rückgabe so schnell wie möglich aus dem Aufgabentext zu erkennen, wenn diese Funktion **true**zurückgibt. (Verwenden Sie bei Aufgabengruppen nicht `cancel_current_task`.)

Das folgende Beispiel zeigt das erste grundlegende Muster für den Aufgabenabbruch. Der Aufgabentext überprüft die Schleife von Zeit zu Zeit auf Abbrüche.

[!code-cpp[concrt-task-basic-cancellation#1](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_2.cpp)]

Die `cancel_current_task`-Funktion löst eine Ausnahme aus; daher müssen Sie nicht explizit von der aktuellen Schleife oder Funktion zurückkehren.

> [!TIP]
> Alternativ können Sie die [Funktion concurrency::interruption_point](reference/concurrency-namespace-functions.md#interruption_point) anstelle aufrufen. `cancel_current_task`

Es ist wichtig, `cancel_current_task` als Reaktion auf einen Abbruch aufzurufen, da die Aufgabe dadurch in den abgebrochenen Zustand übergeht. Wenn Sie zu früh zurückkehren, anstatt `cancel_current_task` aufzurufen, geht der Vorgang in den abgeschlossenen Zustand über, und alle wertbasierten Fortsetzungen werden ausgeführt.

> [!CAUTION]
> Lösen Sie nie `task_canceled` in Ihrem Code aus. Rufen Sie stattdessen `cancel_current_task` auf.

Wenn eine Aufgabe im abgebrochenen Zustand endet, löst die [parallelcurrency::task::get-Methode](reference/task-class.md#get) [parallel::task_canceled](../../parallel/concrt/reference/task-canceled-class.md)aus. (Umgekehrt kehrt [concurrency::task::wait](reference/task-class.md#wait) [task_status::abgebrochen](reference/concurrency-namespace-enums.md#task_group_status) und wird nicht geworfen.) Das folgende Beispiel veranschaulicht dieses Verhalten für eine aufgabenbasierte Fortsetzung. Eine aufgabenbasierte Fortsetzung wird immer aufgerufen, auch wenn die Vorgängeraufgabe abgebrochen wurde.

[!code-cpp[concrt-task-canceled#1](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_3.cpp)]

Da wertbasierte Fortsetzungen das Token der Vorgängeraufgabe erben, wenn sie nicht mit einem expliziten Token erstellt wurden, gehen die Fortsetzungen sofort in den abgebrochenen Zustand über, auch wenn die Vorgängeraufgabe noch ausgeführt wird. Daher wird jede Ausnahme, die von der Vorgängeraufgabe nach dem Abbruch ausgelöst wird, nicht an die Fortsetzungsaufgaben weitergegeben. Der Abbruch überschreibt immer den Status der Vorgängeraufgabe. Das folgende Beispiel ähnelt dem vorhergehenden, veranschaulicht jedoch das Verhalten einer wertbasierten Fortsetzung.

[!code-cpp[concrt-task-canceled#2](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_4.cpp)]

> [!CAUTION]
> Wenn Sie kein Abbruchtoken an `task` den Konstruktor oder die [Concurrency::create_task-Funktion](reference/concurrency-namespace-functions.md#create_task) übergeben, kann diese Aufgabe nicht mehr ausgeführt werden. Außerdem müssen Sie an den Konstruktor geschachtelter Aufgaben – Aufgaben, die im Text einer anderen Aufgabe erstellt werden – das Abbruchtoken dieser Aufgabe übergeben, um alle Aufgaben gleichzeitig abzubrechen.

Sie haben die Möglichkeit, beliebigen Code auszuführen, wenn ein Abbruchtoken abgebrochen wird. Wenn Ihr Benutzer beispielsweise auf der Benutzeroberfläche eine Schaltfläche **Abbrechen** auswählt, um den Vorgang abzubrechen, können Sie diese Schaltfläche deaktivieren, bis der Benutzer einen anderen Vorgang startet. Das folgende Beispiel zeigt, wie Sie die [parallel::cancellation_token:register_callback-Methode](reference/cancellation-token-class.md#register_callback) verwenden, um eine Rückruffunktion zu registrieren, die ausgeführt wird, wenn ein Abbruchtoken abgebrochen wird.

[!code-cpp[concrt-task-cancellation-callback#1](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_5.cpp)]

Das Dokument [Task Parallelism](../../parallel/concrt/task-parallelism-concurrency-runtime.md) erläutert den Unterschied zwischen wertbasierten und aufgabenbasierten Fortsetzungen. Wenn Sie kein `cancellation_token`-Objekt für eine Fortsetzungsaufgabe angeben, erbt die Fortsetzung das Abbruchtoken der Vorgängeraufgabe wie folgt:

- Eine wertbasierte Fortsetzung erbt immer das Abbruchtoken der Vorgängeraufgabe.

- Eine aufgabenbasierte Fortsetzung erbt dagegen das Abbruchtoken der Vorgängeraufgabe nicht. Die einzige Möglichkeit, eine aufgabenbasierte Fortsetzung abbrechbar zu machen, ist die explizite Übergabe eines Abbruchtokens.

Diese Verhalten werden nicht durch eine fehlerhafte Aufgabe beeinträchtigt (das heißt, eine Aufgabe, die eine Ausnahme auslöst). In diesem Fall wird eine wertbasierte Fortsetzung abgebrochen. Eine aufgabenbasierte Fortsetzung wird nicht abgebrochen.

> [!CAUTION]
> Eine Aufgabe, die in einer anderen Aufgabe erstellt wird (das heißt, eine geschachtelte Aufgabe) erbt nicht das Abbruchtoken der übergeordneten Aufgabe. Nur wertbasierte Fortsetzungen erben das Abbruchtoken ihrer Vorgängeraufgabe.

> [!TIP]
> Verwenden Sie die [parallel::cancellation_token::none-Methode,](reference/cancellation-token-class.md#none) wenn Sie einen `cancellation_token` Konstruktor oder eine Funktion aufrufen, die ein Objekt verwendet, und Sie möchten nicht, dass der Vorgang kannbar sein.

Sie können auch ein Abbruchtoken für den Konstruktor eines `task_group`- oder `structured_task_group`-Objekts angeben. Ein wichtiger Aspekt hierfür ist, dass die untergeordneten Aufgabengruppen dieses Abbruchtoken erben. Ein Beispiel, das dieses Konzept mithilfe der [Funktion concurrency::run_with_cancellation_token](reference/concurrency-namespace-functions.md#run_with_cancellation_token) zum Ausführen von Aufrufen `parallel_for`veranschaulicht, finden Sie weiter unten in diesem Dokument unter Abbrechen [paralleler Algorithmen.](#algorithms)

[[Oben](#top)]

#### <a name="cancellation-tokens-and-task-composition"></a>Abbruchtoken und Aufgabenkomposition

Die Funktionen [concurrency::when_all](reference/concurrency-namespace-functions.md#when_all) und [concurrency::when_any](reference/concurrency-namespace-functions.md#when_all) können Ihnen beim Komponieren mehrerer Aufgaben helfen, um allgemeine Muster zu implementieren. In diesem Abschnitt wird beschrieben, wie diese Funktionen mit Abbruchtoken verwendet werden können.

Wenn Sie ein Abbruchtoken `when_all` für `when_any` die und die Funktion bereitstellen, wird diese Funktion nur abgebrochen, wenn dieses Abbruchtoken abgebrochen wird oder wenn eine der Teilnehmeraufgaben in einem abgebrochenen Zustand endet oder eine Ausnahme auslöst.

Die Funktion `when_all` erbt das Abbruchtoken von jeder Aufgabe, die zum Gesamtvorgang gehört, sofern Sie ihr kein Abbruchtoken übergeben. Die Aufgabe, von `when_all` der zurückgegeben wird, wird abgebrochen, wenn eines dieser Token abgebrochen wird und mindestens eine der Teilnehmeraufgaben noch nicht gestartet wurde oder ausgeführt wird. Ein ähnliches Verhalten tritt auf, wenn eine der Aufgaben `when_all` eine Ausnahme auslöst – die Aufgabe, von der zurückgegeben wird, wird mit dieser Ausnahme sofort abgebrochen.

Die Runtime wählt das Abbruchtoken für die Aufgabe aus, das von der Funktion `when_any` zurückgegeben wird, wenn diese Aufgabe abgeschlossen ist. Wenn keine der beteiligten Aufgaben mit einem abgeschlossenen Zustand beendet wird und mindestens eine der Aufgaben eine Ausnahme auslöst, wird eine der auslösenden Aufgaben ausgewählt, um `when_any` zu beenden, und dessen Token wird als Token für die letzte Aufgabe ausgewählt. Wenn mehr als eine Aufgabe mit einem abgeschlossenen Zustand beendet wird, endet die Aufgabe, die von der Aufgabe `when_any` zurückgegeben wird, mit einem abgeschlossenen Zustand. Die Runtime versucht, eine abgeschlossene Aufgabe auszuwählen, deren Token zum Zeitpunkt des Abschlusses nicht abgebrochen ist, sodass die Aufgabe, die von `when_any` zurückgegeben wird, nicht sofort abgebrochen wird, auch wenn wenn andere ausgeführte Aufgaben möglicherweise zu einem späteren Zeitpunkt abgeschlossen werden.

[[Oben](#top)]

### <a name="using-the-cancel-method-to-cancel-parallel-work"></a><a name="cancel"></a>Verwenden der Abbruchmethode zum Abbrechen paralleler Arbeit

Die [Methoden concurrency::task_group::cancel](reference/task-group-class.md#cancel) und [concurrency::structured_task_group::cancel](reference/structured-task-group-class.md#cancel) legen eine Taskgruppe auf den abgebrochenen Zustand fest. Nach dem Aufruf der `cancel`-Methode startet die Aufgabengruppe keine neuen Aufgaben mehr. Die `cancel`-Methoden können von mehreren untergeordneten Aufgaben aufgerufen werden. Ein abgebrochener Task verursacht die [parallelität::task_group::wait](reference/task-group-class.md#wait) and [concurrency::structured_task_group::wait-Methoden,](reference/structured-task-group-class.md#wait) um [concurrency::canceled](reference/concurrency-namespace-enums.md#task_group_status)zurückzugeben.

Wenn eine Taskgruppe abgebrochen wird, können Aufrufe von jedem untergeordneten Task in die Laufzeit einen *Unterbrechungspunkt*auslösen, wodurch die Laufzeit ausgelöst wird und ein interner Ausnahmetyp abgefangen wird, um aktive Aufgaben abzubrechen. Die Concurrency Runtime definiert keine bestimmten Unterbrechungspunkte. Diese können in jedem Aufruf der Runtime auftreten. Die Runtime muss die ausgelösten Ausnahmen behandeln, um den Abbruch durchzuführen. Behandeln Sie daher keine unbekannten Ausnahmen im Text einer Aufgabe.

Wenn eine untergeordnete Aufgabe einen zeitaufwändigen Vorgang ausführt und die Runtime nicht aufruft, muss sie regelmäßig nach einem Abbruch suchen und rechtzeitig beendet werden können. Das folgende Beispiel zeigt eine Möglichkeit zur Bestimmung des Abbruchzeitpunkts. Die Aufgabe `t4` bricht die übergeordnete Aufgabengruppe ab, wenn sie auf einen Fehler stößt. Die Aufgabe `t5` ruft regelmäßig die `structured_task_group::is_canceling`-Methode auf, um nach einem Abbruch zu suchen. Wenn die übergeordnete Aufgabengruppe abgebrochen wird, druckt die Aufgabe `t5` eine Meldung und wird beendet.

[!code-cpp[concrt-task-tree#6](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_6.cpp)]

In diesem Beispiel wird bei<sup>th</sup> jeder 100. Iteration der Taskschleife auf Abbruch überprüft. Die Häufigkeit, mit der nach einem Abbruch gesucht wird, hängt vom Arbeitsaufwand der Aufgabe ab und davon, wie schnell die Reaktion der Aufgaben auf den Abbruch sein soll.

Wenn Sie keinen Zugriff auf das übergeordnete Aufgabengruppenobjekt haben, rufen Sie die [Funktion concurrency::is_current_task_group_canceling](reference/concurrency-namespace-functions.md#is_current_task_group_canceling) auf, um zu bestimmen, ob die übergeordnete Aufgabengruppe abgebrochen wird.

Die `cancel`-Methode wird nur auf die jeweils untergeordneten Aufgaben angewendet. Wenn Sie z. B. die Aufgabengruppe `tg1` in der Abbildung der parallelen Arbeitsstruktur abbrechen, sind alle Aufgaben in der Struktur (`t1`, `t2`, `t3`, `t4` und `t5`) betroffen. Wenn Sie die geschachtelte Aufgabengruppe `tg2` abbrechen, sind dagegen nur die Aufgaben `t4` und `t5` betroffen.

Wenn Sie die `cancel`-Methode aufrufen, werden auch alle untergeordneten Aufgabengruppen abgebrochen. Dies gilt jedoch nicht für die übergeordneten Elemente der Aufgabengruppe in der parallelen Arbeitsstruktur. In den folgenden Beispielen wird dies auf Grundlage der Abbildung der parallelen Arbeitsstruktur veranschaulicht.

Im ersten Beispiel wird eine Arbeitsfunktion für die Aufgabe `t4` erstellt, die der Arbeitsgruppe `tg2` untergeordnet ist. Die Arbeitsfunktion ruft die Funktion `work` in einer Schleife auf. Wenn ein Aufruf von `work` fehlschlägt, wird die übergeordnete Aufgabengruppe der Aufgabe abgebrochen. Hierdurch geht die Aufgabengruppe `tg2` in den Zustand "abgebrochen" über, die Aufgabengruppe `tg1` wird jedoch nicht abgebrochen.

[!code-cpp[concrt-task-tree#2](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_7.cpp)]

Dieses zweite Beispiel ähnelt dem ersten, mit dem Unterschied, dass die Aufgabe hier die Aufgabengruppe `tg1` abbricht. Dadurch sind alle Aufgaben in der Struktur betroffen (`t1`, `t2`, `t3`, `t4` und `t5`).

[!code-cpp[concrt-task-tree#3](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_8.cpp)]

Die `structured_task_group`-Klasse ist nicht threadsicher. Daher erzeugt eine untergeordnete Aufgabe, die eine Methode des übergeordneten `structured_task_group`-Objekts aufruft, ein nicht spezifiziertes Verhalten. Die Ausnahmen von dieser `structured_task_group::cancel` Regel sind die und [concurrency::structured_task_group::is_canceling-Methoden.](reference/structured-task-group-class.md#is_canceling) Eine untergeordnete Aufgabe kann diese Methoden aufrufen, um die übergeordnete Aufgabengruppe abzubrechen und auf einen Abbruch zu prüfen.

> [!CAUTION]
> Sie können zwar ein Abbruchtoken verwenden, um Arbeitsvorgänge einer Aufgabengruppe abzubrechen, die als untergeordnetes Objekt eines `task`-Objekts ausgeführt werden, Sie können jedoch nicht die Methoden `task_group::cancel` oder `structured_task_group::cancel` verwenden, um `task`-Objekte abzubrechen, die in einer Aufgabengruppe ausgeführt werden.

[[Oben](#top)]

### <a name="using-exceptions-to-cancel-parallel-work"></a><a name="exceptions"></a>Verwenden von Ausnahmen zum Abbrechen paralleler Arbeit

Die Verwendung von Abbruchtoken und `cancel`-Methode ist effizienter als die Ausnahmebehandlung beim Abbrechen einer parallelen Arbeitsstruktur. Abbruchtoken und die `cancel`-Methode brechen eine Aufgabe und alle untergeordneten Aufgaben von oben nach unten ab (Top-Down-Ansatz). Bei der Ausnahmebehandlung wird dagegen die umgekehrte Reihenfolge verwendet (Bottom-Up-Ansatz), sodass jede untergeordnete Aufgabengruppe einzeln abgebrochen werden muss. Im Thema [Ausnahmebehandlung](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md) wird erläutert, wie die Concurrency Runtime Ausnahmen verwendet, um Fehler zu kommunizieren. Nicht alle Ausnahmen geben jedoch einen Fehler an. Ein Suchalgorithmus kann z. B. die zugeordnete Aufgabe abbrechen, wenn das Ergebnis gefunden wurde. Wie jedoch bereits erwähnt ist die Ausnahmebehandlung im Vergleich zur `cancel`-Methode die weniger effiziente Möglichkeit zum Abbrechen paralleler Aufgaben.

> [!CAUTION]
> Es wird empfohlen, dass Sie nur dann Ausnahmen verwenden, um parallele Arbeit abzubrechen, wenn dies notwendig ist. Abbruchtoken und die `cancel`-Methoden der Aufgabengruppen sind effizienter und weniger fehleranfällig.

Wenn Sie im Text einer Arbeitsfunktion, die Sie an eine Aufgabengruppe übergeben, eine Ausnahme auslösen, speichert die Runtime diese Ausnahme und marshallt sie an den Kontext, der auf das Beenden der Aufgabengruppe wartet. Wie auch bei der `cancel`-Methode verwirft die Runtime alle Aufgaben, die noch nicht gestartet wurden, und akzeptiert keine neuen Aufgaben.

Dieses dritte Beispiel ähnelt dem zweiten, mit dem Unterschied, dass die Aufgabe `t4` eine Ausnahme auslöst, um die Aufgabengruppe `tg2` abzubrechen. In diesem `try` - `catch` Beispiel wird ein Block verwendet, um nach einem Abbruch zu suchen, wenn die Aufgabengruppe `tg2` darauf wartet, dass ihre untergeordneten Aufgaben abgeschlossen sind. Wie im ersten Beispiel geht die Aufgabengruppe `tg2` in den Zustand „abgebrochen“ über, die Aufgabengruppe `tg1` ist jedoch nicht betroffen.

[!code-cpp[concrt-task-tree#4](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_9.cpp)]

In diesem vierten Beispiel wird mithilfe der Ausnahmebehandlung die gesamte Arbeitsstruktur abgebrochen. Im Beispiel wird die Ausnahme abgefangen, wenn Aufgabengruppe `tg1` auf das Beenden der untergeordneten Aufgaben wartet, nicht `tg2`. Wie im zweiten Beispiel gehen so beide Aufgabengruppen in der Struktur (`tg1` und `tg2`) in den Zustand "abgebrochenen" über.

[!code-cpp[concrt-task-tree#5](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_10.cpp)]

Da die `task_group::wait`-Methode und die `structured_task_group::wait`-Methode ausgelöst werden, wenn eine untergeordnete Aufgabe eine Ausnahme auslöst, geben diese keinen Rückgabewert aus.

[[Oben](#top)]

## <a name="canceling-parallel-algorithms"></a><a name="algorithms"></a>Abbrechen paralleler Algorithmen

Parallele Algorithmen in der PPL, z. B. `parallel_for`, basieren auf Aufgabengruppen. Daher können Sie die meisten Techniken für Aufgabengruppen auch zum Abbrechen paralleler Algorithmen verwenden.

In den folgenden Beispielen werden mehrere Möglichkeiten zum Abbrechen eines parallelen Algorithmus gezeigt.

Im folgenden Beispiel wird die `run_with_cancellation_token`-Funktion verwendet, um den `parallel_for`-Algorithmus aufzurufen. Die `run_with_cancellation_token`-Funktion nimmt ein Abbruchtoken als Argument und ruft die bereitgestellte Arbeitsfunktion synchron auf. Da parallele Algorithmen auf Aufgaben basieren, erben sie das Abbruchtoken der übergeordneten Aufgabe. Daher kann `parallel_for` auf den Abbruch reagieren.

[!code-cpp[concrt-cancel-parallel-for#1](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_11.cpp)]

Im folgenden Beispiel wird die [parallel::structured_task_group::run_and_wait](reference/structured-task-group-class.md#run_and_wait) Methode zum Aufrufen des `parallel_for` Algorithmus verwendet. Die `structured_task_group::run_and_wait`-Methode wartet auf das Beenden der angegebenen Aufgabe. Das `structured_task_group`-Objekt aktiviert die Arbeitsfunktion zum Abbrechen der Aufgabe.

[!code-cpp[concrt-task-tree#7](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_12.cpp)]

Folgende Ergebnisse werden zurückgegeben:

```Output
The task group status is: canceled.
```

Im folgenden Beispiel wird eine `parallel_for`-Schleife mithilfe der Ausnahmebehandlung abgebrochen. Die Runtime marshallt die Ausnahme an den aufrufenden Kontext.

[!code-cpp[concrt-task-tree#9](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_13.cpp)]

Folgende Ergebnisse werden zurückgegeben:

```Output
Caught 50
```

Im folgenden Beispiel wird der Abbruch in einer `parallel_for`-Schleife mit einem booleschen Flag koordiniert. Jede Aufgabe wird ausgeführt, da in diesem Beispiel nicht die übergeordnete Aufgabengruppe mit der `cancel`-Methode oder mit Ausnahmebehandlung abgebrochen wird. Diese Methode kann daher mehr Rechenleistung erfordern als die anderen Methoden.

[!code-cpp[concrt-task-tree#8](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_14.cpp)]

Jede Abbruchmethode hat andere Vorteile. Wählen Sie die Methode, die Ihren Anforderungen am besten entspricht.

[[Oben](#top)]

## <a name="when-not-to-use-cancellation"></a><a name="when"></a>Wann nicht zu verwenden Stornierung

Die Verwendung eines Abbruchs ist sinnvoll, wenn jeder Member einer Gruppe zusammenhängender Aufgaben rechtzeitig beendet werden kann. In einigen Fällen ist ein Abbruch jedoch für die Anwendung nicht sinnvoll. Da der Aufgabenabbruch kooperativ ist, wird die übergeordnete Aufgabengruppe beispielsweise nicht abgebrochen, wenn eine einzelne Aufgabe blockiert wird. Wenn z. B. eine Aufgabe, mit der die Blockierung einer anderen aktiven Aufgabe aufgehoben wird, noch nicht gestartet wurde, wird diese bei Abbruch der Aufgabengruppe nicht gestartet. Dies kann zu einem Deadlock-Fehler in der Anwendung führen. Ein Abbruch ist ebenfalls nicht sinnvoll, wenn eine Aufgabe abgebrochen wird, die untergeordnete Aufgabe jedoch einen wichtigen Vorgang, z. B. das Freigeben einer Ressource, ausführt. Da mit dem Abbruch der übergeordneten Aufgabe der gesamte Satz von Aufgaben abgebrochen wird, wird der Vorgang nicht ausgeführt. Ein Beispiel, das diesen Punkt veranschaulicht, finden Sie im Abschnitt [Verstehen, wie Abbruch und Ausnahmebehandlung die Objektzerstörung beeinflussen,](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md#object-destruction) im Thema "Bewährte Methoden im Thema Parallel patterns Library".

[[Oben](#top)]

## <a name="related-topics"></a>Verwandte Themen

|Titel|BESCHREIBUNG|
|-----------|-----------------|
|[Gewusst wie: Verwenden eines Abbruchs zum Verlassen einer Parallel-Schleife](../../parallel/concrt/how-to-use-cancellation-to-break-from-a-parallel-loop.md)|Zeigt, wie mit dem Abbrechen ein paralleler Suchalgorithmus implementiert wird.|
|[Gewusst wie: Verwenden der Ausnahmebehandlung zum Verlassen einer Parallel-Schleife](../../parallel/concrt/how-to-use-exception-handling-to-break-from-a-parallel-loop.md)|Zeigt, wie mit der `task_group`-Klasse ein Suchalgorithmus für eine einfache Struktur geschrieben wird.|
|[Ausnahmebehandlung](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)|Beschreibt, wie die Runtime Ausnahmen behandelt, die von Aufgabengruppen, einfachen Aufgaben und asynchronen Agents ausgelöst werden, und wie in Anwendungen auf Ausnahmen reagiert wird.|
|[Aufgabe Parallelität](../../parallel/concrt/task-parallelism-concurrency-runtime.md)|Beschreibt, wie sich Aufgaben und Aufgabengruppen zueinander verhalten und wie Sie unstrukturierte und strukturierte Parallelität in Ihren Anwendungen verwenden können.|
|[Parallele Algorithmen](../../parallel/concrt/parallel-algorithms.md)|Beschreibt die parallelen Algorithmen, die Auflistungen von Daten gleichzeitig verarbeiten.|
|[Parallel Patterns Library (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)|Eine Übersicht über die Parallel Patterns Library.|

## <a name="reference"></a>Verweis

[task-Klasse (Concurrency Runtime)](../../parallel/concrt/reference/task-class.md)

[cancellation_token_source-Klasse](../../parallel/concrt/reference/cancellation-token-source-class.md)

[cancellation_token-Klasse](../../parallel/concrt/reference/cancellation-token-class.md)

[task_group-Klasse](reference/task-group-class.md)

[structured_task_group-Klasse](../../parallel/concrt/reference/structured-task-group-class.md)

[parallel_for-Funktion](reference/concurrency-namespace-functions.md#parallel_for)
