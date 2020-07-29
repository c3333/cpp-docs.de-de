---
title: 'Exemplarische Vorgehensweise: Verhindern von Deadlocks mit join'
ms.date: 04/25/2019
helpviewer_keywords:
- preventing deadlock with joins [Concurrency Runtime]
- deadlock, preventing [Concurrency Runtime]
- non-greedy joins, example
- join class, example
ms.assetid: d791f697-bb93-463e-84bd-5df1651b7446
ms.openlocfilehash: 5bdd6cd81051d224714dd66d4604cbdec4ddb552
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217882"
---
# <a name="walkthrough-using-join-to-prevent-deadlock"></a>Exemplarische Vorgehensweise: Verhindern von Deadlocks mit join

In diesem Thema wird das Problem mit dem Thema "gastronomische Philosophen" verwendet, um zu veranschaulichen, wie die Klasse " [parallelcurrency:: Join](../../parallel/concrt/reference/join-class.md) " verwendet wird, um Deadlocks In einer Softwareanwendung kommt es zu einem *Deadlock*, wenn zwei oder mehr Prozesse jeweils eine Ressource halten und gegenseitig darauf warten, dass ein anderer Prozess eine andere Ressource freigibt.

Das Philosophenproblem ist ein spezifisches Beispiel dafür, welche Probleme allgemein auftreten können, wenn ein Satz von Ressourcen von mehreren gleichzeitig ablaufenden Prozessen gemeinsam verwendet wird.

## <a name="prerequisites"></a>Voraussetzungen

Lesen Sie sich folgende Themen durch, bevor Sie mit dieser exemplarischen Vorgehensweise beginnen:

- [Asynchrone Agents](../../parallel/concrt/asynchronous-agents.md)

- [Exemplarische Vorgehensweise: Erstellen einer agentbasierten Anwendung](../../parallel/concrt/walkthrough-creating-an-agent-based-application.md)

- [Asynchrone Nachrichten Blöcke](../../parallel/concrt/asynchronous-message-blocks.md)

- [Nachrichten Übergabe Funktionen](../../parallel/concrt/message-passing-functions.md)

- [Synchronisierungs Datenstrukturen](../../parallel/concrt/synchronization-data-structures.md)

## <a name="sections"></a><a name="top"></a>Strecken

Diese exemplarische Vorgehensweise enthält folgende Abschnitte:

- [Das Philosophenproblem](#problem)

- [Eine naive Implementierung](#deadlock)

- [Verwenden von Join zum Verhindern von Deadlocks](#solution)

## <a name="the-dining-philosophers-problem"></a><a name="problem"></a>Das Problem mit den gastronomischen Philosophen

Das Philosophenproblem veranschaulicht, wie Deadlocks in einer Anwendung auftreten. Bei diesem Problem sitzen fünf Philosophen an einem runden Tisch. Die einzelnen Philosophen haben Phasen, in denen sie denken, und Phasen, in denen sie essen. Jeder Philosoph muss ein Essstäbchen mit dem Tischnachbarn zu seiner Linken und ein anderes Essstäbchen mit dem Tischnachbarn zu seiner Rechten teilen. Die folgende Abbildung veranschaulicht diese Anordnung.

![Das Philosophenproblem](../../parallel/concrt/media/dining_philosophersproblem.png "Das Philosophenproblem")

Um essen zu können, benötigt ein Philosoph zwei Essstäbchen. Wenn jeder Philosoph nur ein Essstäbchen hat und auf das zweite wartet, kann kein Philosoph essen und alle bleiben hungrig.

[Nach[oben](#top)]

## <a name="a-nave-implementation"></a><a name="deadlock"></a>Eine naive Implementierung

Im folgenden Beispiel wird eine naive Implementierung des Philosophenproblems veranschaulicht. Die- `philosopher` Klasse, die von " [parallelcurrency:: Agent](../../parallel/concrt/reference/agent-class.md)" abgeleitet wird, ermöglicht jedem Philosoph, unabhängig zu agieren. Im Beispiel wird ein frei gegebenes Array von [parallelcurrency:: CRITICAL_SECTION](../../parallel/concrt/reference/critical-section-class.md) -Objekten verwendet, um jedem `philosopher` Objekt exklusiven Zugriff auf ein paar von Essstäbchen zu geben.

Um die Implementierung mit der Abbildung in Verbindung zu bringen, stellt die `philosopher`-Klasse einen Philosophen dar. Eine **`int`** Variable stellt die einzelnen Essstäbchen dar. Die `critical_section`-Objekte dienen als Halter für die Essstäbchen. Die `run`-Methode simuliert das Leben des Philosophen. Die `think`-Methode simuliert das Denken und die `eat`-Methode das Essen.

Ein `philosopher`-Objekt sperrt beide `critical_section`-Objekte, um das Herausnehmen der Essstäbchen aus den Haltern zu simulieren, bevor die `eat`-Methode aufgerufen wird. Nach dem Aufruf von `eat` werden die Essstäbchen wieder vom `philosopher`-Objekt in die Halter zurückgelegt, und zwar durch Zurücksetzen der `critical_section`-Objekte in den entsperrten Zustand.

Die `pickup_chopsticks`-Methode veranschaulicht, wo ein Deadlock auftreten kann. Wenn jedes `philosopher`-Objekt Zugriff auf eine der Sperren erlangt, kann kein `philosopher`-Objekt fortfahren, weil die andere Sperre von einem anderen `philosopher`-Objekt gesteuert wird.

### <a name="example"></a>Beispiel

[!code-cpp[concrt-philosophers-deadlock#1](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_1.cpp)]

### <a name="compiling-the-code"></a>Kompilieren des Codes

Kopieren Sie den Beispielcode, und fügen Sie ihn in ein Visual Studio-Projekt ein. Alternativ dazu können Sie ihn auch in eine Datei mit dem Namen einfügen `philosophers-deadlock.cpp` und dann den folgenden Befehl in einem Visual Studio-Eingabe Aufforderungs Fenster ausführen.

> **cl.exe/EHsc Philosophers-Deadlock. cpp**

[Nach[oben](#top)]

## <a name="using-join-to-prevent-deadlock"></a><a name="solution"></a>Verwenden von Join zum Verhindern von Deadlocks

In diesem Abschnitt wird gezeigt, wie Meldungspuffer und Meldungsübergabefunktionen verwendet werden, um Deadlocks zu vermeiden.

Um dieses Beispiel mit dem vorherigen zu verknüpfen, ersetzt die- `philosopher` Klasse jedes `critical_section` -Objekt mithilfe eines [parallelcurrency:: Unbounded_buffer](reference/unbounded-buffer-class.md) -Objekts und eines- `join` Objekts. Das `join`-Objekt dient als Vermittler, das dem Philosophen die Essstäbchen bereitstellt.

In diesem Beispiel wird die `unbounded_buffer`-Klasse verwendet, da die Meldung aus der Meldungswarteschlange entfernt wird, wenn ein Ziel eine Meldung von einem `unbounded_buffer`-Objekt empfängt. So kann ein `unbounded_buffer`-Objekt, das eine Meldung enthält, darauf hinweisen, dass das Essstäbchen zur Verfügung steht. Ein `unbounded_buffer`-Objekt, das keine Meldung enthält, weist darauf hin, dass das Essstäbchen verwendet wird.

In diesem Beispiel wird ein nicht gieriges `join`-Objekt verwendet, da ein nicht gieriger Join nur dann jedem `philosopher`-Objekt Zugriff auf beide Essstäbchen gewährt, wenn beide `unbounded_buffer`-Objekte eine Meldung enthalten. Ein gieriger Join würde Deadlocks nicht verhindern, da Meldungen von ihm akzeptiert werden, sobald sie verfügbar sind. Deadlocks können auftreten, wenn alle gierigen `join`-Objekte eine der Meldungen empfangen, aber ewig warten, bis die andere verfügbar wird.

Weitere Informationen über gierige und nicht gierige Joins sowie die Unterschiede zwischen den verschiedenen Nachrichten Puffer Typen finden Sie unter [asynchrone Nachrichten Blöcke](../../parallel/concrt/asynchronous-message-blocks.md).

### <a name="to-prevent-deadlock-in-this-example"></a>So verhindern Sie Deadlocks in diesem Beispiel

1. Entfernen Sie folgenden Code aus dem Beispiel.

[!code-cpp[concrt-philosophers-deadlock#2](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_2.cpp)]

1. Ändern Sie den Typ der Datenmember `_left` und `_right` der `philosopher`-Klasse in `unbounded_buffer`.

[!code-cpp[concrt-philosophers-join#2](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_3.cpp)]

1. Ändern Sie den `philosopher`-Konstruktor, damit `unbounded_buffer`-Objekte als Parameter verwendet werden.

[!code-cpp[concrt-philosophers-join#3](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_4.cpp)]

1. Ändern Sie die `pickup_chopsticks`-Methode, um ein nicht gieriges `join`-Objekt zum Empfangen von Meldungen von den Meldungspuffern für beide Essstäbchen.

[!code-cpp[concrt-philosophers-join#4](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_5.cpp)]

1. Ändern Sie die `putdown_chopsticks`-Methode, um den Zugriff auf die Essstäbchen freizugeben, indem eine Meldung an die Meldungspuffer für beide Essstäbchen gesendet wird.

[!code-cpp[concrt-philosophers-join#5](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_6.cpp)]

1. Ändern Sie die `run`-Methode, um die Ergebnisse der `pickup_chopsticks`-Methode aufzunehmen und diese Ergebnisse an die `putdown_chopsticks`-Methode weiterzuleiten.

[!code-cpp[concrt-philosophers-join#6](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_7.cpp)]

1. Ändern Sie die Deklaration der `chopsticks`-Variable in der `wmain`-Funktion, damit sie ein Array von `unbounded_buffer`-Objekten ist, die jeweils über eine Meldung verfügen.

[!code-cpp[concrt-philosophers-join#7](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_8.cpp)]

### <a name="description"></a>BESCHREIBUNG

Nachfolgend sehen Sie das vollständige Beispiel, bei dem nicht gierige `join`-Objekte verwendet werden, um das Risiko von Deadlocks auszuschließen.

### <a name="example"></a>Beispiel

[!code-cpp[concrt-philosophers-join#1](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_9.cpp)]

Folgende Ergebnisse werden zurückgegeben:

```Output
aristotle ate 50 times.
descartes ate 50 times.
hobbes ate 50 times.
socrates ate 50 times.
plato ate 50 times.
```

### <a name="compiling-the-code"></a>Kompilieren des Codes

Kopieren Sie den Beispielcode, und fügen Sie ihn in ein Visual Studio-Projekt ein. Alternativ dazu können Sie ihn auch in eine Datei mit dem Namen einfügen `philosophers-join.cpp` und dann den folgenden Befehl in einem Visual Studio-Eingabe Aufforderungs Fenster ausführen.

> **cl.exe/EHsc Philosophers-Join. cpp**

[Nach[oben](#top)]

## <a name="see-also"></a>Weitere Informationen

[Exemplarische Vorgehensweisen Concurrency Runtime](../../parallel/concrt/concurrency-runtime-walkthroughs.md)<br/>
[Asynchronous Agents Library](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[Asynchrone Agents](../../parallel/concrt/asynchronous-agents.md)<br/>
[Asynchrone Nachrichten Blöcke](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Nachrichten Übergabe Funktionen](../../parallel/concrt/message-passing-functions.md)<br/>
[Synchronisierungs Datenstrukturen](../../parallel/concrt/synchronization-data-structures.md)
