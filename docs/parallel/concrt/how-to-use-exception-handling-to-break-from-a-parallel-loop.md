---
title: 'Gewusst wie: Verwenden der Ausnahmebehandlung zum Verlassen einer Parallel-Schleife'
ms.date: 11/04/2016
helpviewer_keywords:
- search algorithm, writing [Concurrency Runtime]
- writing a search algorithm [Concurrency Runtime]
ms.assetid: 16d7278c-2d10-4014-9f58-f1899e719ff9
ms.openlocfilehash: f6842e3093a577289c0c4432d96298e3c7b2bb92
ms.sourcegitcommit: 43cee7a0d41a062661229043c2f7cbc6ace17fa3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/13/2020
ms.locfileid: "92008497"
---
# <a name="how-to-use-exception-handling-to-break-from-a-parallel-loop"></a>Gewusst wie: Verwenden der Ausnahmebehandlung zum Verlassen einer Parallel-Schleife

In diesem Thema wird gezeigt, wie ein Suchalgorithmus für eine einfache Baumstruktur geschrieben wird.

Der Thema [Abbruch](cancellation-in-the-ppl.md) erläutert die Rolle des Abbruchs in der Parallel Patterns Library. Die Verwendung der Ausnahmebehandlung ist eine weniger effiziente Möglichkeit zum Abbrechen paralleler Aufgaben als die Verwendung der Methoden " [parallelcurrency:: task_group:: Cancel](reference/task-group-class.md#cancel) " und " [parallelcurrency:: structured_task_group:: Cancel](reference/structured-task-group-class.md#cancel) ". Ein Szenario, in dem die Verwendung der Ausnahmebehandlung zum Abbrechen von Arbeit angebracht ist, ist jedoch, wenn Sie eine Bibliothek eines Drittanbieters aufruft, die Tasks oder parallele Algorithmen verwendet, aber kein- `task_group` oder- `structured_task_group` Objekt zum Abbrechen bereitstellt.

## <a name="example-basic-tree-type"></a>Beispiel: grundlegender bauentyp

Das folgende Beispiel zeigt einen `tree` Basistyp, der ein Datenelement und eine Liste mit untergeordneten Knoten enthält. Der folgende Abschnitt zeigt den Text der- `for_all` Methode, die rekursiv eine Arbeitsfunktion auf jedem untergeordneten Knoten ausführt.

[!code-cpp[concrt-task-tree-search#2](../../parallel/concrt/codesnippet/cpp/how-to-use-exception-handling-to-break-from-a-parallel-loop_1.cpp)]

## <a name="example-perform-work-in-parallel"></a>Beispiel: parallele Ausführung von Aufgaben

Im folgenden Beispiel wird die- `for_all` Methode veranschaulicht. Dabei wird der Parallelitäts [::p arallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) -Algorithmus verwendet, um eine Arbeitsfunktion auf jedem Knoten der Struktur parallel auszuführen.

[!code-cpp[concrt-task-tree-search#1](../../parallel/concrt/codesnippet/cpp/how-to-use-exception-handling-to-break-from-a-parallel-loop_2.cpp)]

## <a name="example--search-the-tree-for-a-value"></a>Beispiel: Durchsuchen der Struktur nach einem Wert

Das folgende Beispiel zeigt die `search_for_value`-Funktion, die nach einem Wert im bereitgestellten `tree`-Objekt sucht. Diese Funktion übergibt an die- `for_all` Methode eine Arbeitsfunktion, die auslöst, wenn ein Struktur Knoten gefunden wird, der den bereitgestellten Wert enthält.

Angenommen, die `tree` -Klasse wird von einer Drittanbieter Bibliothek bereitgestellt und kann nicht geändert werden. In diesem Fall ist die Verwendung der Ausnahmebehandlung sinnvoll, da die `for_all` Methode dem Aufrufer kein- `task_group` Objekt oder-Objekt bereitstellt `structured_task_group` . Daher kann die Arbeitsfunktion die übergeordnete Aufgaben Gruppe nicht direkt abbrechen.

Wenn die Arbeitsfunktion, die Sie einer Aufgaben Gruppe bereitstellen, eine Ausnahme auslöst, beendet die Common Language Runtime alle Aufgaben in der Aufgaben Gruppe (einschließlich aller untergeordneten Aufgaben Gruppen) und verwirft alle Aufgaben, die noch nicht gestartet wurden. Die `search_for_value` -Funktion verwendet einen **`try`** - **`catch`** -Block, um die Ausnahme zu erfassen und das Ergebnis in der Konsole auszugeben.

[!code-cpp[concrt-task-tree-search#3](../../parallel/concrt/codesnippet/cpp/how-to-use-exception-handling-to-break-from-a-parallel-loop_3.cpp)]

## <a name="example-create-and-search-a-tree-in-parallel"></a>Beispiel: parallele Erstellung und Durchsuchen einer Struktur

Im folgenden Beispiel wird ein `tree` -Objekt erstellt und nach mehreren Werten parallel durchsucht. Die- `build_tree` Funktion wird weiter unten in diesem Thema gezeigt.

[!code-cpp[concrt-task-tree-search#4](../../parallel/concrt/codesnippet/cpp/how-to-use-exception-handling-to-break-from-a-parallel-loop_4.cpp)]

In diesem Beispiel wird der " [parallelcurrency::p arallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) -Algorithmus verwendet, um parallele Werte zu suchen. Weitere Informationen zu diesem Algorithmus finden Sie unter [parallele Algorithmen](../../parallel/concrt/parallel-algorithms.md).

## <a name="example-finished-exception-handling-code-sample"></a>Beispiel: Fertigstellung des Code Beispiels für die Ausnahmebehandlung

Im folgenden Beispiel wird die Ausnahmebehandlung verwendet, um nach Werten in einer grundlegenden Baumstruktur zu suchen.

[!code-cpp[concrt-task-tree-search#5](../../parallel/concrt/codesnippet/cpp/how-to-use-exception-handling-to-break-from-a-parallel-loop_5.cpp)]

Dieses Beispiel erzeugt die folgende Beispielausgabe.

```Output
Found a node with value 32614.
Found a node with value 86131.
Did not find node with value 17522.
```

## <a name="compiling-the-code"></a>Kompilieren des Codes

Kopieren Sie den Beispielcode, und fügen Sie ihn in ein Visual Studio-Projekt ein. Alternativ dazu können Sie ihn auch in eine Datei mit dem Namen einfügen `task-tree-search.cpp` und dann den folgenden Befehl in einem Visual Studio-Eingabe Aufforderungs Fenster ausführen.

> **cl.exe/EHsc Task-Tree-Search. cpp**

## <a name="see-also"></a>Siehe auch

[Abbruch in der PPL](cancellation-in-the-ppl.md)<br/>
[Ausnahmebehandlung](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)<br/>
[Aufgaben Parallelität](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br/>
[Parallele Algorithmen](../../parallel/concrt/parallel-algorithms.md)<br/>
[Task_group-Klasse](reference/task-group-class.md)<br/>
[structured_task_group-Klasse](../../parallel/concrt/reference/structured-task-group-class.md)<br/>
[parallel_for_each-Funktion](reference/concurrency-namespace-functions.md#parallel_for_each)
