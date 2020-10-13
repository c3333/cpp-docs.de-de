---
title: 'Gewusst wie: Ausführen von parallelen Vorgängen mithilfe von parallel_invoke'
ms.date: 11/04/2016
helpviewer_keywords:
- parallel_invoke function, example
- calling multiple functions in parallel [Concurrency Runtime]
ms.assetid: a6aea69b-d647-4b7e-bf3b-e6a6a9880072
ms.openlocfilehash: 62781b2915704c4104bd7e8a13e48e43d81955c6
ms.sourcegitcommit: 43cee7a0d41a062661229043c2f7cbc6ace17fa3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/13/2020
ms.locfileid: "92008339"
---
# <a name="how-to-use-parallel_invoke-to-execute-parallel-operations"></a>Gewusst wie: Ausführen von parallelen Vorgängen mithilfe von parallel_invoke

In diesem Beispiel wird gezeigt, wie der Algorithmus "Parallelität [::p arallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) verwendet wird, um die Leistung eines Programms zu verbessern, das mehrere Vorgänge für eine freigegebene Datenquelle ausführt. Da die Quelle durch keinen der Vorgänge geändert wird, können diese auf einfache Weise parallel ausgeführt werden.

## <a name="example-create-initialize-and-perform-operations-on-a-variable"></a>Beispiel: erstellen, initialisieren und Ausführen von Vorgängen für eine Variable

Betrachten Sie das folgende Codebeispiel, in dem eine Variable vom Typ `MyDataType` erstellt wird, eine Funktion zum Initialisieren dieser Variablen aufgerufen wird und dann mehrere langwierige Operationen mit diesen Daten ausgeführt werden.

[!code-cpp[concrt-parallel-word-mining#1](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-execute-parallel-operations_1.cpp)]

Wenn die Funktionen `lengthy_operation1`, `lengthy_operation2` und `lengthy_operation3` die `MyDataType`-Variable nicht ändern, können sie ohne weitere Änderungen parallel ausgeführt werden.

## <a name="example-run-previous-example-in-parallel"></a>Beispiel: Paralleles Ausführen eines vorherigen Beispiels

Im folgenden Beispiel wird das vorhergehende Beispiel geändert, um es parallel auszuführen. Der `parallel_invoke`-Algorithmus führt jede Aufgabe parallel aus und wird zurückgegeben, nachdem alle Aufgaben beendet wurden.

[!code-cpp[concrt-parallel-word-mining#2](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-execute-parallel-operations_2.cpp)]

## <a name="example-perform-multiple-operations-on-a-downloaded-file"></a>Beispiel: Ausführen mehrerer Vorgänge für eine heruntergeladene Datei

Im folgenden Beispiel wird *Iliad* von Homer von Gutenberg.org heruntergeladen, und es werden mehrere Vorgänge für diese Datei durchführt. Im Beispiel werden diese Vorgänge zunächst seriell und dann parallel ausgeführt.

[!code-cpp[concrt-parallel-word-mining#3](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-execute-parallel-operations_3.cpp)]

Dieses Beispiel erzeugt die folgende Beispielausgabe.

```Output
Downloading 'The Iliad'...

Running serial version... took 953 ms.
Running parallel version... took 656 ms.

The most common words that have five or more letters are:
    their (953)
    shall (444)
    which (431)
    great (398)
    Hector (349)
    Achilles (309)
    through (301)
    these (268)
    chief (259)
The longest sequence of words that have the same first letter is:
    through the tempest to the tented
The following palindromes appear in the text:
    spots stops
    speed deeps
    keels sleek
```

In diesem Beispiel werden mit dem `parallel_invoke`-Algorithmus mehrere Funktionen aufgerufen, die auf dieselbe Datenquelle angewendet werden. Sie können mit dem `parallel_invoke`-Algorithmus jeden Satz von Funktionen parallel aufrufen, nicht nur Funktionen, die auf dieselben Daten angewendet werden.

Da der `parallel_invoke`-Algorithmus die Arbeitsfunktionen parallel aufruft, liegt die Leistungsgrenze bei der Funktion, die am längsten braucht (wenn die Runtime jede Funktion auf einem separaten Prozessor ausführt). Wenn mehr Aufgaben parallel ausgeführt werden, als Prozessoren verfügbar sind, können auf jedem Prozessor mehrere Aufgaben ausgeführt werden. In diesem Fall liegt die Leistungsgrenze bei der Aufgabengruppe, die am längsten braucht.

Da in diesem Beispiel drei Aufgaben parallel ausgeführt werden, sollten Sie keine Leistungsskalierung auf Computern mit mehr als drei Prozessoren erwarten. Um die Leistung zusätzlich zu steigern, können Sie die Aufgaben mit der längsten Ausführungsdauer in kleinere Aufgaben aufteilen und diese Aufgaben parallel ausführen.

Sie können den `parallel_invoke` Algorithmus anstelle der Klassen " [parallelcurrency:: task_group](reference/task-group-class.md) " und " [parallelcurrency:: structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) " verwenden, wenn Sie keine Unterstützung für den Abbruch benötigen. Ein Beispiel für die Verwendung des-Algorithmus im `parallel_invoke` Vergleich zu Aufgaben Gruppen finden Sie unter Gewusst [wie: Verwenden von parallel_invoke zum Schreiben einer parallelen Sortier Routine](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md).

## <a name="compiling-the-code"></a>Kompilieren des Codes

Um den Code zu kompilieren, kopieren Sie ihn, und fügen Sie ihn in ein Visual Studio-Projekt ein, oder fügen Sie ihn in eine Datei mit dem Namen ein, `parallel-word-mining.cpp` und führen Sie dann den folgenden Befehl in einem Visual Studio-Eingabe Aufforderungs Fenster aus.

> **cl.exe/EHsc/MD/DUNICODE/D_AFXDLL parallel-Word-Mining. cpp**

## <a name="see-also"></a>Siehe auch

[Parallele Algorithmen](../../parallel/concrt/parallel-algorithms.md)<br/>
[Parallel_invoke-Funktion](reference/concurrency-namespace-functions.md#parallel_invoke)
