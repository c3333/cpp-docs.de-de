---
title: 'Exemplarische Vorgehensweise: Implementieren von Futures'
ms.date: 04/25/2019
helpviewer_keywords:
- implementing futures [Concurrency Runtime]
- futures, implementing [Concurrency Runtime]
ms.assetid: 82ea75cc-aaec-4452-b10d-8abce0a87e5b
ms.openlocfilehash: 9bf46b7f2a761aaf0c07e1017524c8ddf533aca6
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230297"
---
# <a name="walkthrough-implementing-futures"></a>Exemplarische Vorgehensweise: Implementieren von Futures

In diesem Thema erfahren Sie, wie Sie Futures in Ihre Anwendung implementieren. Es wird veranschaulicht, wie Sie die vorhandenen Funktionen in der Concurrency Runtime kombinieren können, um mehr Funktionalität zu erzielen.

> [!IMPORTANT]
> In diesem Thema wird das Konzept von Futures zu Demonstrationszwecken veranschaulicht. Es wird empfohlen, [Std:: Future](../../standard-library/future-class.md) oder [parallelcurrency:: Task](../../parallel/concrt/reference/task-class.md) zu verwenden, wenn Sie eine asynchrone Aufgabe benötigen, mit der ein Wert für die spätere Verwendung berechnet wird.

Bei einem *Task* handelt es sich um eine Berechnung, die in zusätzliche, differenziertere Berechnungen zerlegt werden kann. Eine *Zukunft* ist eine asynchrone Aufgabe, die einen Wert für die spätere Verwendung berechnet.

Zur Implementierung von Futures wird in diesem Thema die `async_future`-Klasse definiert. Die `async_future` -Klasse verwendet diese Komponenten der Concurrency Runtime: die Klasse " [parallelcurrency:: task_group](reference/task-group-class.md) " und die Klasse " [parallelcurrency:: Single_assignment](../../parallel/concrt/reference/single-assignment-class.md) ". Die `async_future`-Klasse verwendet die `task_group`-Klasse zur asynchronen Berechnung eines Werts und die `single_assignment`-Klasse zum Speichern des Ergebnisses. Der Konstruktor der `async_future`-Klasse akzeptiert eine Arbeitsfunktion, die das Ergebnis berechnet, das mit der `get`-Methode abgerufen wird.

### <a name="to-implement-the-async_future-class"></a>So implementieren Sie die async_future-Klasse

1. Deklarieren Sie eine Vorlagenklasse mit dem Namen `async_future`, die auf der Grundlage des Typs der resultierenden Berechnung parametrisiert wird. Fügen **`public`** Sie **`private`** dieser Klasse die Abschnitte und hinzu.

[!code-cpp[concrt-futures#2](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_1.cpp)]

1. **`private`** Deklarieren Sie im-Abschnitt der `async_future` -Klasse einen `task_group` und einen `single_assignment` Datenmember.

[!code-cpp[concrt-futures#3](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_2.cpp)]

1. Implementieren Sie im- **`public`** Abschnitt der- `async_future` Klasse den-Konstruktor. Der Konstruktor ist eine Vorlage, die auf Grundlage der Arbeitsfunktion, die zur Berechnung des Ergebnisses dient, parametrisiert wird. Der Konstruktor führt die Arbeitsfunktion im Datenmember asynchron aus `task_group` und verwendet die Funktion " [parallelcurrency:: Send](reference/concurrency-namespace-functions.md#send) ", um das Ergebnis in das `single_assignment` Datenmember zu schreiben.

[!code-cpp[concrt-futures#4](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_3.cpp)]

1. Implementieren Sie im- **`public`** Abschnitt der- `async_future` Klasse den-Dekonstruktor. Der Destruktor wartet auf das Beenden der Aufgabe.

[!code-cpp[concrt-futures#5](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_4.cpp)]

1. Implementieren Sie im- **`public`** Abschnitt der- `async_future` Klasse die- `get` Methode. Diese Methode verwendet die Funktion " [parallelcurrency:: Receive](reference/concurrency-namespace-functions.md#receive) ", um das Ergebnis der Arbeitsfunktion abzurufen.

[!code-cpp[concrt-futures#6](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_5.cpp)]

## <a name="example"></a>Beispiel

### <a name="description"></a>BESCHREIBUNG

Das folgende Beispiel zeigt die vollständige `async_future`-Klasse mit einer Verwendungsmöglichkeit. Die- `wmain` Funktion erstellt ein Std::[Vector](../../standard-library/vector-class.md) -Objekt, das 10.000 zufällige ganzzahlige Werte enthält. Anschließend werden mithilfe von `async_future`-Objekten der kleinste und der größte Wert im `vector`-Objekt gesucht.

### <a name="code"></a>Code

[!code-cpp[concrt-futures#1](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_6.cpp)]

### <a name="comments"></a>Kommentare

Dieses Beispiel erzeugt die folgende Ausgabe:

```Output
smallest: 0
largest:  9999
average:  4981
```

Im Beispiel werden die Ergebnisse der Berechnung mit der `async_future::get`-Methode abgerufen. Die `async_future::get`-Methode wartet, bis die Berechnung beendet ist.

## <a name="robust-programming"></a>Stabile Programmierung

Um die- `async_future` Klasse zu erweitern, um Ausnahmen zu behandeln, die von der Arbeitsfunktion ausgelöst werden, ändern Sie die- `async_future::get` Methode, um die Methode " [parallelcurrency:: task_group:: Wait](reference/task-group-class.md#wait) " aufzurufen Die `task_group::wait`-Methode löst alle von der Arbeitsfunktion generierten Ausnahmen aus.

Das folgende Beispiel zeigt die geänderte Version der `async_future`-Klasse. Die- `wmain` Funktion verwendet einen- **`try`** - **`catch`** Block, um das Ergebnis des- `async_future` Objekts auszugeben oder den Wert der Ausnahme auszugeben, die von der Arbeitsfunktion generiert wird.

[!code-cpp[concrt-futures-with-eh#1](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_7.cpp)]

Dieses Beispiel erzeugt die folgende Ausgabe:

```Output
caught exception: error
```

Weitere Informationen über das Ausnahme Behandlungsmodell im Concurrency Runtime finden Sie unter [Ausnahmebehandlung](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).

## <a name="compiling-the-code"></a>Kompilieren des Codes

Kopieren Sie den Beispielcode, und fügen Sie ihn in ein Visual Studio-Projekt ein. Alternativ dazu können Sie ihn auch in eine Datei mit dem Namen einfügen `futures.cpp` und dann den folgenden Befehl in einem Visual Studio-Eingabe Aufforderungs Fenster ausführen.

**cl.exe/EHsc Futures. cpp**

## <a name="see-also"></a>Weitere Informationen

[Exemplarische Vorgehensweisen Concurrency Runtime](../../parallel/concrt/concurrency-runtime-walkthroughs.md)<br/>
[Behandlung von Ausnahmen](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)<br/>
[Task_group-Klasse](reference/task-group-class.md)<br/>
[Single_assignment-Klasse](../../parallel/concrt/reference/single-assignment-class.md)
