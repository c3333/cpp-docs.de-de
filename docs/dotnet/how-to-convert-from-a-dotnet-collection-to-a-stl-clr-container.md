---
title: 'Gewusst wie: Umwandeln einer .Net-Auflistung in einen STL/CLR-Container'
ms.date: 11/04/2016
helpviewer_keywords:
- STL/CLR, converting from .NET collections
- STL/CLR Containers [STL/CLR]
ms.assetid: bb927c48-78e8-4150-bd0b-787c651f4a87
ms.openlocfilehash: 156b4162f742915939ebdfaec6a84d77afaad8cd
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2019
ms.locfileid: "79545048"
---
# <a name="how-to-convert-from-a-net-collection-to-a-stlclr-container"></a>Gewusst wie: Umwandeln einer .Net-Auflistung in einen STL/CLR-Container

In diesem Thema wird gezeigt, wie Sie .NET-Auflistungen in ihre entsprechenden STL/CLR-Container konvertieren. Als Beispiel wird veranschaulicht, wie Sie eine .net-<xref:System.Collections.Generic.List%601> in einen STL/CLR- [Vektor](../dotnet/vector-stl-clr.md) konvertieren und eine .net-<xref:System.Collections.Generic.Dictionary%602> in eine STL/CLR-Zuordnung [konvertieren, aber](../dotnet/map-stl-clr.md)die Prozedur ist für alle Sammlungen und Container ähnlich.

### <a name="to-create-a-container-from-a-collection"></a>So erstellen Sie einen Container aus einer Sammlung

1. Erstellen Sie zum Konvertieren einer gesamten Auflistung einen STL/CLR-Container, und übergeben Sie die Auflistung an den Konstruktor.

   Im ersten Beispiel wird dieses Verfahren veranschaulicht.

ODER

1. Erstellen Sie einen generischen STL/CLR-Container, indem Sie ein [Collection_adapter](../dotnet/collection-adapter-stl-clr.md) Objekt erstellen. Diese Vorlagen Klasse nimmt eine .net-Auflistungs Schnittstelle als Argument an. Informationen dazu, welche Schnittstellen unterstützt werden, finden Sie unter [Collection_adapter (STL/CLR)](../dotnet/collection-adapter-stl-clr.md).

1. Kopieren Sie den Inhalt der .net-Auflistung in den Container. Hierzu können Sie einen STL/CLR- [Algorithmus](../dotnet/algorithm-stl-clr.md)verwenden oder die .net-Auflistung durchlaufen und eine Kopie der einzelnen Elemente in den STL/CLR-Container einfügen.

   Im zweiten Beispiel wird dieses Verfahren veranschaulicht.

## <a name="example"></a>Beispiel

In diesem Beispiel erstellen wir einen generischen <xref:System.Collections.Generic.List%601> und fügen diesem fünf Elemente hinzu. Anschließend erstellen wir eine `vector` mithilfe des Konstruktors, der einen <xref:System.Collections.Generic.IEnumerable%601> als Argument annimmt.

```cpp
// cliext_convert_list_to_vector.cpp
// compile with: /clr

#include <cliext/adapter>
#include <cliext/algorithm>
#include <cliext/vector>

using namespace System;
using namespace System::Collections;
using namespace System::Collections::Generic;

int main(array<System::String ^> ^args)
{
    List<int> ^primeNumbersColl = gcnew List<int>();
    primeNumbersColl->Add(2);
    primeNumbersColl->Add(3);
    primeNumbersColl->Add(5);
    primeNumbersColl->Add(7);
    primeNumbersColl->Add(11);

    cliext::vector<int> ^primeNumbersCont =
        gcnew cliext::vector<int>(primeNumbersColl);

    Console::WriteLine("The contents of the cliext::vector are:");
    cliext::vector<int>::const_iterator it;
    for (it = primeNumbersCont->begin(); it != primeNumbersCont->end(); it++)
    {
        Console::WriteLine(*it);
    }
}
```

```Output
The contents of the cliext::vector are:
2
3
5
7
11
```

## <a name="example"></a>Beispiel

In diesem Beispiel erstellen wir einen generischen <xref:System.Collections.Generic.Dictionary%602> und fügen diesem fünf Elemente hinzu. Anschließend erstellen wir eine `collection_adapter`, um die <xref:System.Collections.Generic.Dictionary%602> als einfachen STL/CLR-Container zu umschließen. Zum Schluss erstellen wir eine `map` und kopieren den Inhalt des <xref:System.Collections.Generic.Dictionary%602> in die `map`, indem wir die `collection_adapter`durchlaufen. Während dieses Vorgangs wird ein neues Paar mit der `make_pair`-Funktion erstellt, und das neue Paar wird direkt in die `map`eingefügt.

```cpp
// cliext_convert_dictionary_to_map.cpp
// compile with: /clr

#include <cliext/adapter>
#include <cliext/algorithm>
#include <cliext/map>

using namespace System;
using namespace System::Collections;
using namespace System::Collections::Generic;

int main(array<System::String ^> ^args)
{
    System::Collections::Generic::Dictionary<float, int> ^dict =
        gcnew System::Collections::Generic::Dictionary<float, int>();
    dict->Add(42.0, 42);
    dict->Add(13.0, 13);
    dict->Add(74.0, 74);
    dict->Add(22.0, 22);
    dict->Add(0.0, 0);

    cliext::collection_adapter<System::Collections::Generic::IDictionary<float, int>> dictAdapter(dict);
    cliext::map<float, int> aMap;
    for each (KeyValuePair<float, int> ^kvp in dictAdapter)
    {
        cliext::pair<float, int> aPair = cliext::make_pair(kvp->Key, kvp->Value);
        aMap.insert(aPair);
    }

    Console::WriteLine("The contents of the cliext::map are:");
    cliext::map<float, int>::const_iterator it;
    for (it = aMap.begin(); it != aMap.end(); it++)
    {
        Console::WriteLine("Key: {0:F} Value: {1}", it->first, it->second);
    }
}
```

```Output
The contents of the cliext::map are:
Key: 0.00 Value: 0
Key: 13.00 Value: 13
Key: 22.00 Value: 22
Key: 42.00 Value: 42
Key: 74.00 Value: 74
```

## <a name="see-also"></a>Siehe auch

[Referenz zur STL/CLR-Bibliothek](../dotnet/stl-clr-library-reference.md)<br/>
[adapter (STL/CLR)](../dotnet/adapter-stl-clr.md)<br/>
[Vorgehensweise: Umwandeln eines STL/CLR-Containers in eine .NET-Auflistung](../dotnet/how-to-convert-from-a-stl-clr-container-to-a-dotnet-collection.md)
