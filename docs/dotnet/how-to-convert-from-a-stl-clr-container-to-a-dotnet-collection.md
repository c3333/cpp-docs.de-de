---
title: 'Gewusst wie: Umwandeln eines STL/CLR-Containers in eine .NET-Auflistung'
ms.date: 11/04/2016
helpviewer_keywords:
- STL/CLR Containers [STL/CLR]
- STL/CLR, converting to .NET collections
ms.assetid: 70b2dfd9-869c-4e0f-9a29-b1ee0cb0d107
ms.openlocfilehash: f5e289c330c83ac0c630a5b1f8f97b8c65fc7efb
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/16/2020
ms.locfileid: "90686443"
---
# <a name="how-to-convert-from-a-stlclr-container-to-a-net-collection"></a>Gewusst wie: Umwandeln eines STL/CLR-Containers in eine .NET-Auflistung

In diesem Thema wird gezeigt, wie Sie STL/CLR-Container in ihre entsprechenden .NET-Auflistungen konvertieren. Als Beispiel wird veranschaulicht, wie Sie einen STL/CLR- [Vektor](../dotnet/vector-stl-clr.md) in einen .NET-Code konvertieren <xref:System.Collections.Generic.ICollection%601> und eine STL/CLR- [map](../dotnet/map-stl-clr.md) Zuordnung in eine .NET-Struktur konvertieren <xref:System.Collections.Generic.IDictionary%602> , aber die Prozedur ist für alle Sammlungen und Container ähnlich.

### <a name="to-create-a-collection-from-a-container"></a>So erstellen Sie eine Sammlung aus einem Container

1. Verwenden Sie eine der folgenden Methoden:

   - Um einen Teil eines Containers zu konvertieren, nennen Sie die [make_collection](../dotnet/make-collection-stl-clr.md) -Funktion, und übergeben Sie den BEGIN-Iterator und den End-Iterator des STL/CLR-Containers, der in die .net-Auflistung kopiert werden soll. Diese Vorlagen Funktion nimmt einen STL/CLR-Iterator als Vorlagen Argument an. Das erste Beispiel veranschaulicht diese Methode.

   - Um einen gesamten Container zu konvertieren, wandeln Sie den Container in eine entsprechende .net-Auflistungs Schnittstelle oder Schnittstellen Auflistung um. Das zweite Beispiel veranschaulicht diese Methode.

## <a name="examples"></a>Beispiele

In diesem Beispiel erstellen wir eine STL/CLR `vector` und fügen ihr 5 Elemente hinzu. Anschließend erstellen Sie eine .net-Auflistung, indem Sie die- `make_collection` Funktion aufrufen. Schließlich wird der Inhalt der neu erstellten Auflistung angezeigt.

```cpp
// cliext_convert_vector_to_icollection.cpp
// compile with: /clr

#include <cliext/adapter>
#include <cliext/vector>

using namespace cliext;
using namespace System;
using namespace System::Collections::Generic;

int main(array<System::String ^> ^args)
{
    cliext::vector<int> primeNumbersCont;
    primeNumbersCont.push_back(2);
    primeNumbersCont.push_back(3);
    primeNumbersCont.push_back(5);
    primeNumbersCont.push_back(7);
    primeNumbersCont.push_back(11);

    System::Collections::Generic::ICollection<int> ^iColl =
        make_collection<cliext::vector<int>::iterator>(
            primeNumbersCont.begin() + 1,
            primeNumbersCont.end() - 1);

    Console::WriteLine("The contents of the System::Collections::Generic::ICollection are:");
    for each (int i in iColl)
    {
        Console::WriteLine(i);
    }
}
```

```Output
The contents of the System::Collections::Generic::ICollection are:
3
5
7
```

In diesem Beispiel erstellen wir eine STL/CLR `map` und fügen ihr 5 Elemente hinzu. Anschließend erstellen wir eine .net <xref:System.Collections.Generic.IDictionary%602> -Datei und weisen `map` Ihr direkt zu. Schließlich wird der Inhalt der neu erstellten Auflistung angezeigt.

```cpp
// cliext_convert_map_to_idictionary.cpp
// compile with: /clr

#include <cliext/adapter>
#include <cliext/map>

using namespace cliext;
using namespace System;
using namespace System::Collections::Generic;

int main(array<System::String ^> ^args)
{
    cliext::map<float, int> ^aMap = gcnew cliext::map<float, int>;
    aMap->insert(cliext::make_pair<float, int>(42.0, 42));
    aMap->insert(cliext::make_pair<float, int>(13.0, 13));
    aMap->insert(cliext::make_pair<float, int>(74.0, 74));
    aMap->insert(cliext::make_pair<float, int>(22.0, 22));
    aMap->insert(cliext::make_pair<float, int>(0.0, 0));

    System::Collections::Generic::IDictionary<float, int> ^iDict = aMap;

    Console::WriteLine("The contents of the IDictionary are:");
    for each (KeyValuePair<float, int> ^kvp in iDict)
    {
        Console::WriteLine("Key: {0:F} Value: {1}", kvp->Key, kvp->Value);
    }
}
```

```Output
The contents of the IDictionary are:
Key: 0.00 Value: 0
Key: 13.00 Value: 13
Key: 22.00 Value: 22
Key: 42.00 Value: 42
Key: 74.00 Value: 74
```

## <a name="see-also"></a>Weitere Informationen

[STL/CLR-Bibliotheks Referenz](../dotnet/stl-clr-library-reference.md)<br/>
[Gewusst wie: Konvertieren einer .net-Auflistung in einen STL/CLR-Container](../dotnet/how-to-convert-from-a-dotnet-collection-to-a-stl-clr-container.md)<br/>
[range_adapter (STL/CLR)](../dotnet/range-adapter-stl-clr.md)
