---
title: Referenz zur STL/CLR-Bibliothek
ms.date: 09/18/2018
ms.topic: reference
helpviewer_keywords:
- STL/CLR Library
- STL/CLR, redistribution
- cliext directory
ms.assetid: a9d9ca00-7bf2-48c1-b205-3ae6f8c25f82
ms.openlocfilehash: e6804dab814eca4ecc5fd23c74cbbb21eac3be77
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88839698"
---
# <a name="stlclr-library-reference"></a>Referenz zur STL/CLR-Bibliothek

Die STL/CLR-Bibliothek bietet eine Schnittstelle, die den C++-Standard Bibliotheks Containern für die Verwendung mit C++ und der .NET Framework Common Language Runtime (CLR) ähnelt. STL/CLR ist vollständig getrennt von der Microsoft-Implementierung der C++-Standard Bibliothek. STL/CLR wird für Legacy Unterstützung verwaltet, aber nicht mit dem C++-Standard auf dem neuesten Stand gehalten. Wir empfehlen dringend die Verwendung der nativen [C++-Standard Bibliotheks](../standard-library/cpp-standard-library-reference.md) Container anstelle von STL/CLR, wann immer dies möglich ist.

Verwendung von STL/CLR:

- Einschließen von Headern aus dem **cliext** include-Unterverzeichnis anstelle der üblichen Entsprechungen der C++-Standard Bibliothek.

- Qualifizieren Sie Bibliotheksnamen mit `cliext::` statt mit `std::`.

Die STL/CLR-Bibliothek stellt eine STL-ähnliche Oberfläche für die Verwendung mit C++ und der .NET Framework Common Language Runtime (CLR) bereit. Diese Bibliothek wird für Legacy Unterstützung verwaltet, aber nicht mit dem C++-Standard auf dem neuesten Stand gehalten. Es wird dringend empfohlen, die nativen [C++-Standard Bibliotheks](../standard-library/cpp-standard-library-reference.md) Container anstelle von STL/CLR zu verwenden.

## <a name="in-this-section"></a>In diesem Abschnitt

[cliext-Namespace](../dotnet/cliext-namespace.md)<br/>
Erläutert den Namespace, der alle Typen der STL/CLR-Bibliothek enthält.

[STL/CLR-Container](../dotnet/stl-clr-containers.md)<br/>
Bietet eine Übersicht über die Container, die in der C++-Standard Bibliothek enthalten sind, einschließlich der Anforderungen für Container Elemente, der Typen von Elementen, die eingefügt werden können, und der Besitz Probleme.

[Anforderungen für STL/CLR-Container Elemente](../dotnet/requirements-for-stl-clr-container-elements.md)<br/>
Beschreibt die Mindestanforderungen für alle Verweis Typen, die in C++-Standard Bibliotheks Container eingefügt werden.

[Gewusst wie: Konvertieren einer .net-Auflistung in einen STL/CLR-Container](../dotnet/how-to-convert-from-a-dotnet-collection-to-a-stl-clr-container.md)<br/>
Beschreibt, wie eine .NET-Auflistung in einen STL/CLR-Container konvertiert wird.

[Gewusst wie: Konvertieren eines STL/CLR-Containers in eine .net-Auflistung](../dotnet/how-to-convert-from-a-stl-clr-container-to-a-dotnet-collection.md)<br/>
Beschreibt, wie ein STL/CLR-Container in eine .NET-Auflistung konvertiert wird.

[Gewusst wie: verfügbar machen eines STL/CLR-Containers aus einer Assembly](../dotnet/how-to-expose-an-stl-clr-container-from-an-assembly.md)<br/>
Erläutert, wie die Elemente einiger STL/CLR-Container aus einer C++-Assembly anzeigt werden.

Außerdem beschreibt dieser Abschnitt die folgenden STL/CLR-Komponenten:

:::row:::
   :::column span="":::
      [`adapter` (STL/CLR)](../dotnet/adapter-stl-clr.md)\
      [`algorithm` (STL/CLR)](../dotnet/algorithm-stl-clr.md)\
      [`deque` (STL/CLR)](../dotnet/deque-stl-clr.md)\
      [`for each`, `in`](../dotnet/for-each-in.md)\
      [`functional` (STL/CLR)](../dotnet/functional-stl-clr.md)\
      [`hash_map` (STL/CLR)](../dotnet/hash-map-stl-clr.md)\
      [`hash_multimap` (STL/CLR)](../dotnet/hash-multimap-stl-clr.md)\
      [`hash_multiset` (STL/CLR)](../dotnet/hash-multiset-stl-clr.md)\
      [`hash_set` (STL/CLR)](../dotnet/hash-set-stl-clr.md)\
      [`list` (STL/CLR)](../dotnet/list-stl-clr.md)\
   :::column-end:::
   :::column span="":::
      [`map` (STL/CLR)](../dotnet/map-stl-clr.md)\
      [`multimap` (STL/CLR)](../dotnet/multimap-stl-clr.md)\
      [`multiset` (STL/CLR)](../dotnet/multiset-stl-clr.md)\
      [`numeric` (STL/CLR)](../dotnet/numeric-stl-clr.md)\
      [`priority_queue` (STL/CLR)](../dotnet/priority-queue-stl-clr.md)\
      [`queue` (STL/CLR)](../dotnet/queue-stl-clr.md)\
      [`set` (STL/CLR)](../dotnet/set-stl-clr.md)\
      [`stack` (STL/CLR)](../dotnet/stack-stl-clr.md)\
      [`utility` (STL/CLR)](../dotnet/utility-stl-clr.md)\
      [`vector` (STL/CLR)](../dotnet/vector-stl-clr.md)\
   :::column-end:::
:::row-end:::

## <a name="see-also"></a>Weitere Informationen

[C++-Standard Bibliothek](../standard-library/cpp-standard-library-reference.md)
