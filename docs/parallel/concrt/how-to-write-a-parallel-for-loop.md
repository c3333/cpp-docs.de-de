---
title: 'Gewusst wie: Schreiben einer parallel_for-Schleife'
ms.date: 11/04/2016
helpviewer_keywords:
- writing a parallel_for loop [Concurrency Runtime]
- parallel_for function, example
ms.assetid: adb4d64e-5514-4b70-8dcb-b9210e6b5a1c
ms.openlocfilehash: 8d2d54e084652a8f34b125b96c3f502dd9cdb1fa
ms.sourcegitcommit: 43cee7a0d41a062661229043c2f7cbc6ace17fa3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/13/2020
ms.locfileid: "92008967"
---
# <a name="how-to-write-a-parallel_for-loop"></a>Gewusst wie: Schreiben einer parallel_for-Schleife

Dieses Beispiel veranschaulicht die Verwendung von Parallelität [::p arallel_for](reference/concurrency-namespace-functions.md#parallel_for) , um das Produkt von zwei Matrizen zu berechnen.

## <a name="example-compute-the-product-of-two-matrices"></a>Beispiel: Berechnen des Produkts von zwei Matrizen

Das folgende Beispiel zeigt die `matrix_multiply`-Funktion, die das Produkt von zwei quadratischen Matrizen berechnet.

[!code-cpp[concrt-parallel-matrix-multiply#1](../../parallel/concrt/codesnippet/cpp/how-to-write-a-parallel-for-loop_1.cpp)]

## <a name="example-compute-a-matrix-multiply-in-parallel"></a>Beispiel: Berechnen einer parallelen multiplizieren einer Matrix

Das folgende Beispiel zeigt die `parallel_matrix_multiply`-Funktion, die den `parallel_for`-Algorithmus zur parallelen Ausführung der äußeren Schleife verwendet.

[!code-cpp[concrt-parallel-matrix-multiply#2](../../parallel/concrt/codesnippet/cpp/how-to-write-a-parallel-for-loop_2.cpp)]

In diesem Beispiel wird nur die äußere Schleife parallelisiert, da diese genügend Arbeitsvorgänge ausführt, um von dem zusätzlichen Aufwand für die parallele Verarbeitung zu profitieren. Durch die Parallelisierung der inneren Schleife erzielen Sie keine Leistungssteigerung, da die innere Schleife nicht genügend Arbeitsvorgänge ausführt, um den zusätzlichen Aufwand für die parallele Verarbeitung zu kompensieren. Daher ist eine Parallelisierung der äußeren Schleife die beste Möglichkeit, die Vorteile der Parallelität in den meisten Systemen zu maximieren.

## <a name="example-finished-parallel_for-loop-code-sample"></a>Beispiel: Fertigstellung von parallel_for Schleifen Codebeispiel

Im folgenden ausführlicheren Beispiel wird die Leistung der `matrix_multiply`-Funktion mit der Leistung der `parallel_matrix_multiply`-Funktion verglichen.

[!code-cpp[concrt-parallel-matrix-multiply#3](../../parallel/concrt/codesnippet/cpp/how-to-write-a-parallel-for-loop_3.cpp)]

Die folgende Beispielausgabe entspricht einem Ergebnis auf einem Computer mit vier Prozessoren.

```Output
serial: 3853
parallel: 1311
```

## <a name="compiling-the-code"></a>Kompilieren des Codes

Um den Code zu kompilieren, kopieren Sie ihn, und fügen Sie ihn in ein Visual Studio-Projekt ein, oder fügen Sie ihn in eine Datei mit dem Namen ein, `parallel-matrix-multiply.cpp` und führen Sie dann den folgenden Befehl in einem Visual Studio-Eingabe Aufforderungs Fenster aus.

> **cl.exe/EHsc parallel-Matrix-Multiply. cpp**

## <a name="see-also"></a>Siehe auch

[Parallele Algorithmen](../../parallel/concrt/parallel-algorithms.md)<br/>
[parallel_for-Funktion](reference/concurrency-namespace-functions.md#parallel_for)
