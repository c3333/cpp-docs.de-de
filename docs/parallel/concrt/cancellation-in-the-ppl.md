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
ms.openlocfilehash: e85de9a07b625030976e6f03c9e965d34c3134d4
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220976"
---
# <a name="cancellation-in-the-ppl"></a>Abbruch in der PPL

In diesem Dokument wird die Rolle des Abbruchs in der Parallel Patterns Library (PPL) erläutert und beschrieben, wie Sie die parallele Arbeitsvorgänge abbrechen, und wie Sie erkennen können, ob parallele Arbeitsvorgänge abgebrochen wurden.

> [!NOTE]
> Die Laufzeit implementiert Abbrüche mithilfe der Ausnahmebehandlung. Diese Ausnahmen dürfen im eigenen Code nicht abgefangen oder behandelt werden. Außerdem empfiehlt es sich, ausnahmesicheren Code in den Funktionsrümpfen der Aufgaben zu schreiben. Beispielsweise können Sie das Muster *Resource Acquisition Is Initialization* (RAII) verwenden, um sicherzustellen, dass Ressourcen ordnungsgemäß verarbeitet werden, wenn eine Ausnahme im Text einer Aufgabe ausgelöst wird. Ein umfassendes Beispiel, in dem das RAII-Muster verwendet wird, um eine Ressource in einer abbrechbaren Aufgabe zu bereinigen, finden Sie unter Exemplarische Vorgehensweise [: Entfernen von Arbeit aus einem Benutzeroberflächen Thread](../../parallel/concrt/walkthrough-removing-work-from-a-user-interface-thread.md).

## <a name="key-points"></a>Die wichtigsten Punkte

- Das Abbrechen ist ein kooperativer Vorgang und beinhaltet die Koordination zwischen dem Code, der den Abbruch verlangt, und der Aufgabe, die auf den Abbruch reagieren muss.

- Verwenden Sie wenn möglich Abbruchtoken, um Arbeitsvorgänge abzubrechen. Die Klasse " [parallelcurrency:: cancellation_token](../../parallel/concrt/reference/cancellation-token-class.md) " definiert ein Abbruch Token.

- Wenn Sie Abbruch Token verwenden, verwenden Sie die [parallelcurrency:: cancellation_token_source:: Cancel](reference/cancellation-token-source-class.md#cancel) -Methode, um den Abbruch zu initiieren, und die Funktion " [parallelcurrency:: cancel_current_task](reference/concurrency-namespace-functions.md#cancel_current_task) ", um auf den Abbruch zu reagieren. Verwenden Sie die Methode " [parallelcurrency:: cancellation_token:: is_canceled](reference/cancellation-token-class.md#is_canceled) ", um zu überprüfen, ob ein anderer Task einen Abbruch angefordert hat.

- Der Abbruch erfolgt nicht unmittelbar. Obwohl neue Arbeit nicht gestartet wird, wenn eine Aufgabe oder eine Aufgaben Gruppe abgebrochen wird, muss die aktive Arbeit nach einem Abbruch suchen und darauf reagieren.

- Eine wertbasierte Fortsetzung erbt das Abbruchtoken ihrer Vorgängeraufgabe. Eine aufgabenbasierte Fortsetzung erbt das Token der Vorgängeraufgabe dagegen nicht.

- Verwenden Sie die Methode " [parallelcurrency:: cancellation_token:: None](reference/cancellation-token-class.md#none) ", wenn Sie einen Konstruktor oder eine Funktion mit einem-Objekt aufzurufen, `cancellation_token` der Vorgang jedoch nicht abgebrochen werden soll. Wenn Sie kein Abbruch Token an den [parallelcurrency:: Task](../../parallel/concrt/reference/task-class.md) -Konstruktor oder an die Funktion " [parallelcurrency:: create_task](reference/concurrency-namespace-functions.md#create_task) " übergeben, kann diese Aufgabe nicht abgebrochen werden.

## <a name="in-this-document"></a><a name="top"></a>In diesem Dokument

- [Parallele Arbeitsstrukturen](#trees)

- [Abbrechen von parallelen Aufgaben](#tasks)

  - [Verwenden eines Abbruchtokens zum Abbrechen paralleler Aufgaben](#tokens)

  - [Abbrechen paralleler Aufgaben mit der cancel-Methode](#cancel)

  - [Abbrechen paralleler Aufgaben mit Ausnahmen](#exceptions)

- [Abbrechen von parallelen Algorithmen](#algorithms)

- [Wann ein Abbruch nicht verwendet werden sollte](#when)

## <a name="parallel-work-trees"></a><a name="trees"></a>Parallele Arbeitsstrukturen

Differenzierte Aufgaben und Berechnungen werden in der PPL mithilfe von Aufgaben und Aufgabengruppen verwaltet. Sie können Aufgaben Gruppen schachteln, um Strukturen paralleler Arbeitsvorgänge *zu bilden.* Die folgende Abbildung zeigt eine parallele Arbeitsstruktur. In dieser Abbildung stellen `tg1` und `tg2` Aufgabengruppen dar; `t1`, `t2`, `t3`, `t4` und `t5` stellen die Arbeitsvorgänge dar, die von den Aufgabengruppen durchgeführt wird.

![Parallele Arbeitsstruktur](../../parallel/concrt/media/parallelwork_trees.png "Parallele Arbeitsstruktur")

Das folgende Beispiel zeigt den Code, der zum Erstellen der Struktur in der Abbildung erforderlich ist. In diesem Beispiel `tg1` sind und `tg2` [parallelcurrency:: structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) -Objekte,,, `t1` `t2` `t3` , `t4` und `t5` sind [parallelcurrency:: task_handle](../../parallel/concrt/reference/task-handle-class.md) -Objekte.

[!code-cpp[concrt-task-tree#1](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_1.cpp)]

Sie können auch die Klasse " [parallelcurrency:: task_group](reference/task-group-class.md) " verwenden, um eine ähnliche Arbeitsstruktur zu erstellen. Die " [parallelcurrency:: Task](../../parallel/concrt/reference/task-class.md) "-Klasse unterstützt auch das Konzept der Arbeit. Eine `task`-Struktur ist jedoch eine Abhängigkeitsstruktur. In einer `task`-Struktur werden zukünftige Arbeitsvorgänge nach aktuellen Arbeitsvorgängen abgeschlossen. In einer Aufgabengruppenstruktur werden interne Arbeitsvorgänge vor externen Arbeitsvorgängen abgeschlossen. Weitere Informationen zu den Unterschieden zwischen Aufgaben und Aufgaben Gruppen finden Sie Unteraufgaben [Parallelität](../../parallel/concrt/task-parallelism-concurrency-runtime.md).

[Nach[oben](#top)]

## <a name="canceling-parallel-tasks"></a><a name="tasks"></a>Abbrechen paralleler Aufgaben

Es gibt verschiedene Möglichkeiten, parallele Arbeitsvorgänge abzubrechen. Die bevorzugte Methode ist, ein Abbruchtoken zu verwenden. Aufgaben Gruppen unterstützen auch die Methode " [parallelcurrency:: task_group:: Cancel](reference/task-group-class.md#cancel) " und die Methode " [parallelcurrency:: structured_task_group:: Cancel](reference/structured-task-group-class.md#cancel) ". Eine letzte Möglichkeit ist, im Text einer Arbeitsfunktion einer Aufgabe eine Ausnahme auszulösen. Unabhängig von der gewählten Methode sollten Sie bedenken, dass der Abbruch nicht sofort auftritt. Obwohl neue Arbeit nicht gestartet wird, wenn eine Aufgabe oder eine Aufgaben Gruppe abgebrochen wird, muss die aktive Arbeit nach einem Abbruch suchen und darauf reagieren.

Weitere Beispiele für das Abbrechen paralleler Aufgaben finden Sie unter Exemplarische Vorgehensweise [: Herstellen einer Verbindung mithilfe von Aufgaben und XML-HTTP-Anforderungen](../../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md), Gewusst [wie: Verwenden von Abbruch zum Unterbrechen einer parallelen Schleife](../../parallel/concrt/how-to-use-cancellation-to-break-from-a-parallel-loop.md)und Gewusst [wie: Verwenden der Ausnahmebehandlung zum Unterbrechen einer parallelen Schleife](../../parallel/concrt/how-to-use-exception-handling-to-break-from-a-parallel-loop.md).

### <a name="using-a-cancellation-token-to-cancel-parallel-work"></a><a name="tokens"></a>Verwenden eines Abbruch Tokens zum Abbrechen paralleler Aufgaben

Die Klassen `task`, `task_group` und `structured_task_group` unterstützen Abbruchvorgänge durch die Verwendung von Abbruchtoken. Die ppl definiert zu diesem Zweck die Klassen " [parallelcurrency:: cancellation_token_source](../../parallel/concrt/reference/cancellation-token-source-class.md) " und " [parallelcurrency:: cancellation_token](../../parallel/concrt/reference/cancellation-token-class.md) ". Wenn Sie Arbeit mithilfe eines Abbruchtokens abbrechen, wird von der Runtime keine neue Verarbeitung gestartet, die dieses Token abonniert. Bereits aktive arbeiten können die [is_canceled](../../parallel/concrt/reference/cancellation-token-class.md#is_canceled) Member-Funktion verwenden, um das Abbruch Token zu überwachen und zu beenden, wenn dies möglich ist.

Um den Abbruch zu initiieren, rufen Sie die Methode " [parallelcurrency:: cancellation_token_source:: Cancel](reference/cancellation-token-source-class.md#cancel) " auf. Auf Abbrüche reagieren Sie folgendermaßen:

- Verwenden Sie für- `task` Objekte die Funktion " [parallelcurrency:: cancel_current_task](reference/concurrency-namespace-functions.md#cancel_current_task) ". `cancel_current_task` bricht die aktuelle Aufgabe und alle wertbasierten Fortsetzungen ab. (Das Abbruch *Token* , das der Aufgabe oder den Fortsetzungen zugeordnet ist, wird nicht abgebrochen.)

- Verwenden Sie für Aufgaben Gruppen und parallele Algorithmen die Funktion " [parallelcurrency:: Is_current_task_group_canceling](reference/concurrency-namespace-functions.md#is_current_task_group_canceling) ", um den Abbruch zu erkennen und so bald wie möglich aus dem Aufgaben Text zurückzugeben, wenn diese Funktion zurückgibt **`true`** . (Verwenden Sie bei Aufgabengruppen nicht `cancel_current_task`.)

Das folgende Beispiel zeigt das erste grundlegende Muster für den Aufgabenabbruch. Der Aufgabentext überprüft die Schleife von Zeit zu Zeit auf Abbrüche.

[!code-cpp[concrt-task-basic-cancellation#1](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_2.cpp)]

Die `cancel_current_task`-Funktion löst eine Ausnahme aus; daher müssen Sie nicht explizit von der aktuellen Schleife oder Funktion zurückkehren.

> [!TIP]
> Alternativ können Sie die Funktion " [parallelcurrency:: interruption_point](reference/concurrency-namespace-functions.md#interruption_point) " anstelle von "" aufzurufen `cancel_current_task` .

Es ist wichtig, `cancel_current_task` als Reaktion auf einen Abbruch aufzurufen, da die Aufgabe dadurch in den abgebrochenen Zustand übergeht. Wenn Sie zu früh zurückkehren, anstatt `cancel_current_task` aufzurufen, geht der Vorgang in den abgeschlossenen Zustand über, und alle wertbasierten Fortsetzungen werden ausgeführt.

> [!CAUTION]
> Lösen Sie nie `task_canceled` in Ihrem Code aus. Rufen Sie stattdessen `cancel_current_task` auf.

Wenn eine Aufgabe im Zustand "abgebrochen" beendet wird, löst die parallelcurrency [:: Task:: Get](reference/task-class.md#get) -Methode " [parallelcurrency:: task_canceled](../../parallel/concrt/reference/task-canceled-class.md)" aus. (Umgekehrt gibt " [parallelcurrency:: Task:: Wait](reference/task-class.md#wait) " [task_status:: abgebrochen](reference/concurrency-namespace-enums.md#task_group_status) zurück und löst nicht aus.) Im folgenden Beispiel wird dieses Verhalten für eine aufgabenbasierte Fortsetzung veranschaulicht. Eine aufgabenbasierte Fortsetzung wird immer aufgerufen, auch wenn die Vorgängeraufgabe abgebrochen wurde.

[!code-cpp[concrt-task-canceled#1](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_3.cpp)]

Da wertbasierte Fortsetzungen das Token der Vorgängeraufgabe erben, wenn sie nicht mit einem expliziten Token erstellt wurden, gehen die Fortsetzungen sofort in den abgebrochenen Zustand über, auch wenn die Vorgängeraufgabe noch ausgeführt wird. Daher wird jede Ausnahme, die von der Vorgängeraufgabe nach dem Abbruch ausgelöst wird, nicht an die Fortsetzungsaufgaben weitergegeben. Der Abbruch überschreibt immer den Status der Vorgängeraufgabe. Das folgende Beispiel ähnelt dem vorhergehenden, veranschaulicht jedoch das Verhalten einer wertbasierten Fortsetzung.

[!code-cpp[concrt-task-canceled#2](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_4.cpp)]

> [!CAUTION]
> Wenn Sie kein Abbruch Token an den `task` Konstruktor oder an die Funktion " [parallelcurrency:: create_task](reference/concurrency-namespace-functions.md#create_task) " übergeben, kann diese Aufgabe nicht abgebrochen werden. Außerdem müssen Sie an den Konstruktor geschachtelter Aufgaben – Aufgaben, die im Text einer anderen Aufgabe erstellt werden – das Abbruchtoken dieser Aufgabe übergeben, um alle Aufgaben gleichzeitig abzubrechen.

Sie haben die Möglichkeit, beliebigen Code auszuführen, wenn ein Abbruchtoken abgebrochen wird. Wenn der Benutzer z. b. auf der Benutzeroberfläche eine Schaltfläche **Abbrechen** auswählt, um den Vorgang abzubrechen, können Sie diese Schaltfläche deaktivieren, bis der Benutzer einen anderen Vorgang startet. Das folgende Beispiel zeigt, wie Sie die Methode " [parallelcurrency:: cancellation_token:: Register_callback](reference/cancellation-token-class.md#register_callback) " verwenden, um eine Rückruffunktion zu registrieren, die ausgeführt wird, wenn ein Abbruch Token abgebrochen wird.

[!code-cpp[concrt-task-cancellation-callback#1](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_5.cpp)]

In der Dokument [Aufgaben Parallelität](../../parallel/concrt/task-parallelism-concurrency-runtime.md) wird der Unterschied zwischen Wert basierten und aufgabenbasierten Fortsetzungen erläutert. Wenn Sie kein `cancellation_token`-Objekt für eine Fortsetzungsaufgabe angeben, erbt die Fortsetzung das Abbruchtoken der Vorgängeraufgabe wie folgt:

- Eine wertbasierte Fortsetzung erbt immer das Abbruchtoken der Vorgängeraufgabe.

- Eine aufgabenbasierte Fortsetzung erbt dagegen das Abbruchtoken der Vorgängeraufgabe nicht. Die einzige Möglichkeit, eine aufgabenbasierte Fortsetzung abbrechbar zu machen, ist die explizite Übergabe eines Abbruchtokens.

Diese Verhalten werden nicht durch eine fehlerhafte Aufgabe beeinträchtigt (das heißt, eine Aufgabe, die eine Ausnahme auslöst). In diesem Fall wird eine Wert basierte Fortsetzung abgebrochen. eine aufgabenbasierte Fortsetzung wird nicht abgebrochen.

> [!CAUTION]
> Eine Aufgabe, die in einer anderen Aufgabe erstellt wird (das heißt, eine geschachtelte Aufgabe) erbt nicht das Abbruchtoken der übergeordneten Aufgabe. Nur wertbasierte Fortsetzungen erben das Abbruchtoken ihrer Vorgängeraufgabe.

> [!TIP]
> Verwenden Sie die Methode " [parallelcurrency:: cancellation_token:: None](reference/cancellation-token-class.md#none) ", wenn Sie einen Konstruktor oder eine Funktion aufzurufen, die ein `cancellation_token` -Objekt annimmt und Sie nicht möchten, dass der Vorgang abgebrochen werden kann.

Sie können auch ein Abbruchtoken für den Konstruktor eines `task_group`- oder `structured_task_group`-Objekts angeben. Ein wichtiger Aspekt hierfür ist, dass die untergeordneten Aufgabengruppen dieses Abbruchtoken erben. Ein Beispiel zur Veranschaulichung dieses Konzepts mithilfe der " [parallelcurrency:: run_with_cancellation_token](reference/concurrency-namespace-functions.md#run_with_cancellation_token) "-Funktion, um aufzurufen `parallel_for` , finden Sie unter [Abbrechen paralleler Algorithmen](#algorithms) weiter unten in diesem Dokument.

[Nach[oben](#top)]

#### <a name="cancellation-tokens-and-task-composition"></a>Abbruchtoken und Aufgabenkomposition

Die Funktionen " [parallelcurrency:: when_all](reference/concurrency-namespace-functions.md#when_all) " und " [parallelcurrency:: when_any](reference/concurrency-namespace-functions.md#when_all) " können Ihnen helfen, mehrere Aufgaben zu verfassen, um allgemeine Muster zu implementieren. In diesem Abschnitt wird beschrieben, wie diese Funktionen mit Abbruchtoken verwendet werden können.

Wenn Sie ein Abbruch Token für die `when_all` -Funktion und die- `when_any` Funktion angeben, wird diese Funktion nur abgebrochen, wenn das Abbruch Token abgebrochen wird, oder wenn eine der Teilnehmer Aufgaben in einem abgebrochenen Zustand endet oder eine Ausnahme auslöst.

Die Funktion `when_all` erbt das Abbruchtoken von jeder Aufgabe, die zum Gesamtvorgang gehört, sofern Sie ihr kein Abbruchtoken übergeben. Die Aufgabe, die von zurückgegeben wird, `when_all` wird abgebrochen, wenn eines dieser Token abgebrochen wird und mindestens eine der Teilnehmer Aufgaben noch nicht gestartet wurde oder ausgeführt wird. Ein ähnliches Verhalten tritt auf, wenn eine der Aufgaben eine Ausnahme auslöst: die Aufgabe, die von zurückgegeben wird, `when_all` wird mit dieser Ausnahme sofort abgebrochen.

Die Runtime wählt das Abbruchtoken für die Aufgabe aus, das von der Funktion `when_any` zurückgegeben wird, wenn diese Aufgabe abgeschlossen ist. Wenn keine der beteiligten Aufgaben mit einem abgeschlossenen Zustand beendet wird und mindestens eine der Aufgaben eine Ausnahme auslöst, wird eine der auslösenden Aufgaben ausgewählt, um `when_any` zu beenden, und dessen Token wird als Token für die letzte Aufgabe ausgewählt. Wenn mehr als eine Aufgabe mit einem abgeschlossenen Zustand beendet wird, endet die Aufgabe, die von der Aufgabe `when_any` zurückgegeben wird, mit einem abgeschlossenen Zustand. Die Runtime versucht, eine abgeschlossene Aufgabe auszuwählen, deren Token zum Zeitpunkt des Abschlusses nicht abgebrochen ist, sodass die Aufgabe, die von `when_any` zurückgegeben wird, nicht sofort abgebrochen wird, auch wenn wenn andere ausgeführte Aufgaben möglicherweise zu einem späteren Zeitpunkt abgeschlossen werden.

[Nach[oben](#top)]

### <a name="using-the-cancel-method-to-cancel-parallel-work"></a><a name="cancel"></a>Abbrechen paralleler Aufgaben mithilfe der Cancel-Methode

Mit den Methoden " [parallelcurrency:: task_group:: Cancel](reference/task-group-class.md#cancel) " und " [parallelcurrency:: structured_task_group:: Cancel](reference/structured-task-group-class.md#cancel) " wird eine Aufgaben Gruppe auf den Zustand "abgebrochen" festgelegt. Nach dem Aufruf der `cancel`-Methode startet die Aufgabengruppe keine neuen Aufgaben mehr. Die `cancel`-Methoden können von mehreren untergeordneten Aufgaben aufgerufen werden. Eine abgebrochene Aufgabe bewirkt, dass die Methoden "parallelcurrency:: [task_group:: Wait](reference/task-group-class.md#wait) " und " [parallelcurrency:: structured_task_group:: Wait](reference/structured-task-group-class.md#wait) " " [parallelcurrency:: abgebrochen](reference/concurrency-namespace-enums.md#task_group_status)" zurückgeben.

Wenn eine Aufgaben Gruppe abgebrochen wird, können Aufrufe von den einzelnen untergeordneten Aufgaben in der Laufzeit einen *Unterbrechungs Punkt*auslösen, der bewirkt, dass die Laufzeit einen internen Ausnahmetyp auslöst und abfängt, um aktive Aufgaben abzubrechen. Die Concurrency Runtime definiert keine bestimmten Unterbrechungspunkte. Diese können in jedem Aufruf der Runtime auftreten. Die Runtime muss die ausgelösten Ausnahmen behandeln, um den Abbruch durchzuführen. Behandeln Sie daher keine unbekannten Ausnahmen im Text einer Aufgabe.

Wenn eine untergeordnete Aufgabe einen zeitaufwändigen Vorgang ausführt und die Runtime nicht aufruft, muss sie regelmäßig nach einem Abbruch suchen und rechtzeitig beendet werden können. Das folgende Beispiel zeigt eine Möglichkeit zur Bestimmung des Abbruchzeitpunkts. Die Aufgabe `t4` bricht die übergeordnete Aufgabengruppe ab, wenn sie auf einen Fehler stößt. Die Aufgabe `t5` ruft regelmäßig die `structured_task_group::is_canceling`-Methode auf, um nach einem Abbruch zu suchen. Wenn die übergeordnete Aufgabengruppe abgebrochen wird, druckt die Aufgabe `t5` eine Meldung und wird beendet.

[!code-cpp[concrt-task-tree#6](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_6.cpp)]

In diesem Beispiel wird bei jeder 100<sup>.</sup> Iterationen der Task Schleife auf einen Abbruch überprüft. Die Häufigkeit, mit der nach einem Abbruch gesucht wird, hängt vom Arbeitsaufwand der Aufgabe ab und davon, wie schnell die Reaktion der Aufgaben auf den Abbruch sein soll.

Wenn Sie keinen Zugriff auf das übergeordnete Aufgaben Gruppen Objekt haben, können Sie die Funktion " [parallelcurrency:: Is_current_task_group_canceling](reference/concurrency-namespace-functions.md#is_current_task_group_canceling) " aufrufen, um zu bestimmen, ob die übergeordnete Aufgaben Gruppe abgebrochen wird.

Die `cancel`-Methode wird nur auf die jeweils untergeordneten Aufgaben angewendet. Wenn Sie z. B. die Aufgabengruppe `tg1` in der Abbildung der parallelen Arbeitsstruktur abbrechen, sind alle Aufgaben in der Struktur (`t1`, `t2`, `t3`, `t4` und `t5`) betroffen. Wenn Sie die geschachtelte Aufgabengruppe `tg2` abbrechen, sind dagegen nur die Aufgaben `t4` und `t5` betroffen.

Wenn Sie die `cancel`-Methode aufrufen, werden auch alle untergeordneten Aufgabengruppen abgebrochen. Dies gilt jedoch nicht für die übergeordneten Elemente der Aufgabengruppe in der parallelen Arbeitsstruktur. In den folgenden Beispielen wird dies auf Grundlage der Abbildung der parallelen Arbeitsstruktur veranschaulicht.

Im ersten Beispiel wird eine Arbeitsfunktion für die Aufgabe `t4` erstellt, die der Arbeitsgruppe `tg2` untergeordnet ist. Die Arbeitsfunktion ruft die Funktion `work` in einer Schleife auf. Wenn ein Aufruf von `work` fehlschlägt, wird die übergeordnete Aufgabengruppe der Aufgabe abgebrochen. Hierdurch geht die Aufgabengruppe `tg2` in den Zustand "abgebrochen" über, die Aufgabengruppe `tg1` wird jedoch nicht abgebrochen.

[!code-cpp[concrt-task-tree#2](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_7.cpp)]

Dieses zweite Beispiel ähnelt dem ersten, mit dem Unterschied, dass die Aufgabe hier die Aufgabengruppe `tg1` abbricht. Dadurch sind alle Aufgaben in der Struktur betroffen (`t1`, `t2`, `t3`, `t4` und `t5`).

[!code-cpp[concrt-task-tree#3](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_8.cpp)]

Die `structured_task_group`-Klasse ist nicht threadsicher. Daher erzeugt eine untergeordnete Aufgabe, die eine Methode des übergeordneten `structured_task_group`-Objekts aufruft, ein nicht spezifiziertes Verhalten. Die Ausnahmen für diese Regel sind die `structured_task_group::cancel` -Methode und die [parallelcurrency:: structured_task_group:: is_canceling](reference/structured-task-group-class.md#is_canceling) -Methode. Eine untergeordnete Aufgabe kann diese Methoden aufrufen, um die übergeordnete Aufgabengruppe abzubrechen und auf einen Abbruch zu prüfen.

> [!CAUTION]
> Sie können zwar ein Abbruchtoken verwenden, um Arbeitsvorgänge einer Aufgabengruppe abzubrechen, die als untergeordnetes Objekt eines `task`-Objekts ausgeführt werden, Sie können jedoch nicht die Methoden `task_group::cancel` oder `structured_task_group::cancel` verwenden, um `task`-Objekte abzubrechen, die in einer Aufgabengruppe ausgeführt werden.

[Nach[oben](#top)]

### <a name="using-exceptions-to-cancel-parallel-work"></a><a name="exceptions"></a>Verwenden von Ausnahmen zum Abbrechen paralleler Aufgaben

Die Verwendung von Abbruchtoken und `cancel`-Methode ist effizienter als die Ausnahmebehandlung beim Abbrechen einer parallelen Arbeitsstruktur. Abbruchtoken und die `cancel`-Methode brechen eine Aufgabe und alle untergeordneten Aufgaben von oben nach unten ab (Top-Down-Ansatz). Bei der Ausnahmebehandlung wird dagegen die umgekehrte Reihenfolge verwendet (Bottom-Up-Ansatz), sodass jede untergeordnete Aufgabengruppe einzeln abgebrochen werden muss. Im Thema [Ausnahmebehandlung](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md) wird erläutert, wie die Concurrency Runtime Ausnahmen zum Übermitteln von Fehlern verwendet. Nicht alle Ausnahmen geben jedoch einen Fehler an. Ein Suchalgorithmus kann z. B. die zugeordnete Aufgabe abbrechen, wenn das Ergebnis gefunden wurde. Wie jedoch bereits erwähnt ist die Ausnahmebehandlung im Vergleich zur `cancel`-Methode die weniger effiziente Möglichkeit zum Abbrechen paralleler Aufgaben.

> [!CAUTION]
> Es wird empfohlen, dass Sie nur dann Ausnahmen verwenden, um parallele Arbeit abzubrechen, wenn dies notwendig ist. Abbruchtoken und die `cancel`-Methoden der Aufgabengruppen sind effizienter und weniger fehleranfällig.

Wenn Sie im Text einer Arbeitsfunktion, die Sie an eine Aufgabengruppe übergeben, eine Ausnahme auslösen, speichert die Runtime diese Ausnahme und marshallt sie an den Kontext, der auf das Beenden der Aufgabengruppe wartet. Wie auch bei der `cancel`-Methode verwirft die Runtime alle Aufgaben, die noch nicht gestartet wurden, und akzeptiert keine neuen Aufgaben.

Dieses dritte Beispiel ähnelt dem zweiten, mit dem Unterschied, dass die Aufgabe `t4` eine Ausnahme auslöst, um die Aufgabengruppe `tg2` abzubrechen. In diesem Beispiel wird ein- **`try`** - **`catch`** Block verwendet, um auf einen Abbruch zu prüfen, wenn die Aufgaben Gruppe auf das `tg2` Beenden der untergeordneten Aufgaben wartet. Wie im ersten Beispiel geht die Aufgabengruppe `tg2` in den Zustand „abgebrochen“ über, die Aufgabengruppe `tg1` ist jedoch nicht betroffen.

[!code-cpp[concrt-task-tree#4](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_9.cpp)]

In diesem vierten Beispiel wird mithilfe der Ausnahmebehandlung die gesamte Arbeitsstruktur abgebrochen. Im Beispiel wird die Ausnahme abgefangen, wenn Aufgabengruppe `tg1` auf das Beenden der untergeordneten Aufgaben wartet, nicht `tg2`. Wie im zweiten Beispiel gehen so beide Aufgabengruppen in der Struktur (`tg1` und `tg2`) in den Zustand "abgebrochenen" über.

[!code-cpp[concrt-task-tree#5](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_10.cpp)]

Da die `task_group::wait`-Methode und die `structured_task_group::wait`-Methode ausgelöst werden, wenn eine untergeordnete Aufgabe eine Ausnahme auslöst, geben diese keinen Rückgabewert aus.

[Nach[oben](#top)]

## <a name="canceling-parallel-algorithms"></a><a name="algorithms"></a>Abbrechen paralleler Algorithmen

Parallele Algorithmen in der PPL, z. B. `parallel_for`, basieren auf Aufgabengruppen. Daher können Sie die meisten Techniken für Aufgabengruppen auch zum Abbrechen paralleler Algorithmen verwenden.

In den folgenden Beispielen werden mehrere Möglichkeiten zum Abbrechen eines parallelen Algorithmus gezeigt.

Im folgenden Beispiel wird die `run_with_cancellation_token`-Funktion verwendet, um den `parallel_for`-Algorithmus aufzurufen. Die `run_with_cancellation_token`-Funktion nimmt ein Abbruchtoken als Argument und ruft die bereitgestellte Arbeitsfunktion synchron auf. Da parallele Algorithmen auf Aufgaben basieren, erben sie das Abbruchtoken der übergeordneten Aufgabe. Daher kann `parallel_for` auf den Abbruch reagieren.

[!code-cpp[concrt-cancel-parallel-for#1](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_11.cpp)]

Im folgenden Beispiel wird die [parallelcurrency:: structured_task_group:: run_and_wait](reference/structured-task-group-class.md#run_and_wait) -Methode verwendet, um den-Algorithmus aufzurufen `parallel_for` . Die `structured_task_group::run_and_wait`-Methode wartet auf das Beenden der angegebenen Aufgabe. Das `structured_task_group`-Objekt aktiviert die Arbeitsfunktion zum Abbrechen der Aufgabe.

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

[Nach[oben](#top)]

## <a name="when-not-to-use-cancellation"></a><a name="when"></a>Wann sollte kein Abbruch verwendet werden?

Die Verwendung eines Abbruchs ist sinnvoll, wenn jeder Member einer Gruppe zusammenhängender Aufgaben rechtzeitig beendet werden kann. In einigen Fällen ist ein Abbruch jedoch für die Anwendung nicht sinnvoll. Da der Aufgabenabbruch kooperativ ist, wird die übergeordnete Aufgabengruppe beispielsweise nicht abgebrochen, wenn eine einzelne Aufgabe blockiert wird. Wenn z. B. eine Aufgabe, mit der die Blockierung einer anderen aktiven Aufgabe aufgehoben wird, noch nicht gestartet wurde, wird diese bei Abbruch der Aufgabengruppe nicht gestartet. Dies kann zu einem Deadlock-Fehler in der Anwendung führen. Ein Abbruch ist ebenfalls nicht sinnvoll, wenn eine Aufgabe abgebrochen wird, die untergeordnete Aufgabe jedoch einen wichtigen Vorgang, z. B. das Freigeben einer Ressource, ausführt. Da mit dem Abbruch der übergeordneten Aufgabe der gesamte Satz von Aufgaben abgebrochen wird, wird der Vorgang nicht ausgeführt. Ein Beispiel zur Veranschaulichung dieses Punkts finden Sie im Abschnitt Grundlegendes zur [Auswirkung der Abbruch-und Ausnahmebehandlung auf die Objekt Zerstörung](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md#object-destruction) in den bewährten Methoden im Thema Parallel Patterns Library.

[Nach[oben](#top)]

## <a name="related-topics"></a>Verwandte Themen

|Titel|BESCHREIBUNG|
|-----------|-----------------|
|[Gewusst wie: Verwenden von Abbruch zum Abbrechen einer parallelen Schleife](../../parallel/concrt/how-to-use-cancellation-to-break-from-a-parallel-loop.md)|Zeigt, wie mit dem Abbrechen ein paralleler Suchalgorithmus implementiert wird.|
|[Gewusst wie: Verwenden der Ausnahmebehandlung zum Unterbrechen einer parallelen Schleife](../../parallel/concrt/how-to-use-exception-handling-to-break-from-a-parallel-loop.md)|Zeigt, wie mit der `task_group`-Klasse ein Suchalgorithmus für eine einfache Struktur geschrieben wird.|
|[Behandlung von Ausnahmen](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)|Beschreibt, wie die Runtime Ausnahmen behandelt, die von Aufgabengruppen, einfachen Aufgaben und asynchronen Agents ausgelöst werden, und wie in Anwendungen auf Ausnahmen reagiert wird.|
|[Aufgaben Parallelität](../../parallel/concrt/task-parallelism-concurrency-runtime.md)|Beschreibt, wie sich Aufgaben und Aufgabengruppen zueinander verhalten und wie Sie unstrukturierte und strukturierte Parallelität in Ihren Anwendungen verwenden können.|
|[Parallele Algorithmen](../../parallel/concrt/parallel-algorithms.md)|Beschreibt die parallelen Algorithmen, die Auflistungen von Daten gleichzeitig verarbeiten.|
|[Parallel Patterns Library (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)|Eine Übersicht über die Parallel Patterns Library.|

## <a name="reference"></a>Verweis

[Task-Klasse (Concurrency Runtime)](../../parallel/concrt/reference/task-class.md)

[cancellation_token_source-Klasse](../../parallel/concrt/reference/cancellation-token-source-class.md)

[cancellation_token-Klasse](../../parallel/concrt/reference/cancellation-token-class.md)

[Task_group-Klasse](reference/task-group-class.md)

[structured_task_group-Klasse](../../parallel/concrt/reference/structured-task-group-class.md)

[parallel_for-Funktion](reference/concurrency-namespace-functions.md#parallel_for)
