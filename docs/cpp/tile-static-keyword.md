---
title: tile_static-Schlüsselwort
ms.date: 11/04/2016
f1_keywords:
- tile_static_CPP
helpviewer_keywords:
- tile_static keyword
ms.assetid: d78384d4-65d9-45cf-b3df-7e904f489d06
ms.openlocfilehash: 9476c0c446463c04084f46ed17a8ada7fb01fd7e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80188128"
---
# <a name="tile_static-keyword"></a>tile_static-Schlüsselwort

Das **tile_static** -Schlüsselwort wird verwendet, um eine Variable zu deklarieren, auf die von allen Threads in einer Kachel von Threads zugegriffen werden kann. Die Lebensdauer der Variable beginnt, wenn die Ausführung den Punkt der Deklaration erreicht, und sie endet dann, wenn die Kernelfunktion zurückgegeben wird. Weitere Informationen zur Verwendung von Kacheln finden Sie unter [Verwenden von Kacheln](../parallel/amp/using-tiles.md).

Das **tile_static** -Schlüsselwort weist die folgenden Einschränkungen auf:

- Es kann nur für Variablen verwendet werden, die sich in einer Funktion befinden, die den Modifizierer `restrict(amp)` aufweist.

- Es kann nicht für Variablen verwendet werden, die Zeiger- oder Verweistypen sind.

- Eine **tile_static** Variable darf keinen Initialisierer aufweisen. Standardkonstruktoren und -destruktoren werden nicht automatisch aufgerufen.

- Der Wert einer nicht initialisierten **tile_static** Variablen ist nicht definiert.

- Wenn eine **tile_static** Variable in einem Aufruf Diagramm deklariert ist, das durch einen nicht gekachelten Aufruf von `parallel_for_each`verankert ist, wird eine Warnung generiert, und das Verhalten der Variablen ist nicht definiert.

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt, wie eine **tile_static** Variable verwendet werden kann, um Daten über mehrere Threads in einer Kachel hinweg zu sammeln.

```cpp
// Sample data:
int sampledata[] = {
    2, 2, 9, 7, 1, 4,
    4, 4, 8, 8, 3, 4,
    1, 5, 1, 2, 5, 2,
    6, 8, 3, 2, 7, 2};

// The tiles:
// 2 2    9 7    1 4
// 4 4    8 8    3 4
//
// 1 5    1 2    5 2
// 6 8    3 2    7 2

// Averages:
int averagedata[] = {
    0, 0, 0, 0, 0, 0,
    0, 0, 0, 0, 0, 0,
    0, 0, 0, 0, 0, 0,
    0, 0, 0, 0, 0, 0,
};

array_view<int, 2> sample(4, 6, sampledata);
array_view<int, 2> average(4, 6, averagedata);

parallel_for_each(
    // Create threads for sample.extent and divide the extent into 2 x 2 tiles.
    sample.extent.tile<2,2>(),
    [=](tiled_index<2,2> idx) restrict(amp)
    {
        // Create a 2 x 2 array to hold the values in this tile.
        tile_static int nums[2][2];
        // Copy the values for the tile into the 2 x 2 array.
        nums[idx.local[1]][idx.local[0]] = sample[idx.global];
        // When all the threads have executed and the 2 x 2 array is complete, find the average.
        idx.barrier.wait();
        int sum = nums[0][0] + nums[0][1] + nums[1][0] + nums[1][1];
        // Copy the average into the array_view.
        average[idx.global] = sum / 4;
      }
);

for (int i = 0; i < 4; i++) {
    for (int j = 0; j < 6; j++) {
        std::cout << average(i,j) << " ";
    }
    std::cout << "\n";
}

// Output:
// 3 3 8 8 3 3
// 3 3 8 8 3 3
// 5 5 2 2 4 4
// 5 5 2 2 4 4
// Sample data.
int sampledata[] = {
    2, 2, 9, 7, 1, 4,
    4, 4, 8, 8, 3, 4,
    1, 5, 1, 2, 5, 2,
    6, 8, 3, 2, 7, 2};

// The tiles are:
// 2 2    9 7    1 4
// 4 4    8 8    3 4
//
// 1 5    1 2    5 2
// 6 8    3 2    7 2

// Averages.
int averagedata[] = {
    0, 0, 0, 0, 0, 0,
    0, 0, 0, 0, 0, 0,
    0, 0, 0, 0, 0, 0,
    0, 0, 0, 0, 0, 0,
};

array_view<int, 2> sample(4, 6, sampledata);
array_view<int, 2> average(4, 6, averagedata);

parallel_for_each(
    // Create threads for sample.grid and divide the grid into 2 x 2 tiles.
    sample.extent.tile<2,2>(),
    [=](tiled_index<2,2> idx) restrict(amp)
    {
        // Create a 2 x 2 array to hold the values in this tile.
        tile_static int nums[2][2];
        // Copy the values for the tile into the 2 x 2 array.
        nums[idx.local[1]][idx.local[0]] = sample[idx.global];
        // When all the threads have executed and the 2 x 2 array is complete, find the average.
        idx.barrier.wait();
        int sum = nums[0][0] + nums[0][1] + nums[1][0] + nums[1][1];
        // Copy the average into the array_view.
        average[idx.global] = sum / 4;
      }
);

for (int i = 0; i < 4; i++) {
    for (int j = 0; j < 6; j++) {
        std::cout << average(i,j) << " ";
    }
    std::cout << "\n";
}

// Output.
// 3 3 8 8 3 3
// 3 3 8 8 3 3
// 5 5 2 2 4 4
// 5 5 2 2 4 4
```

## <a name="see-also"></a>Weitere Informationen

[Microsoft-spezifische Modifizierer](../cpp/microsoft-specific-modifiers.md)<br/>
[Übersicht über C++ AMP](../parallel/amp/cpp-amp-overview.md)<br/>
[Parallel_for_each-FunktionC++ (amp)](../parallel/amp/reference/concurrency-namespace-functions-amp.md#parallel_for_each)<br/>
[Exemplarische Vorgehensweise: Matrixmultiplikation](../parallel/amp/walkthrough-matrix-multiplication.md)
