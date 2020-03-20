---
title: 'Gewusst wie: Umwandeln eines STL/CLR-Containers in eine .NET-Auflistung'
ms.date: 11/04/2016
helpviewer_keywords:
- STL/CLR Containers [STL/CLR]
- STL/CLR, converting to .NET collections
ms.assetid: 70b2dfd9-869c-4e0f-9a29-b1ee0cb0d107
ms.openlocfilehash: f7539b10ca6c503aede61d19de3d14fb9dcee8be
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2019
ms.locfileid: "79545306"
---
# <a name="how-to-convert-from-a-stlclr-container-to-a-net-collection"></a>Gewusst wie: Umwandeln eines STL/CLR-Containers in eine .NET-Auflistung

In diesem Thema wird gezeigt, wie Sie STL/CLR-Container in ihre entsprechenden .NET-Auflistungen konvertieren. Als Beispiel wird gezeigt, wie Sie einen STL/CLR- [Vektor](../dotnet/vector-stl-clr.md) in eine .net-<xref:System.Collections.Generic.ICollection%601> konvertieren und eine STL/CLR-Zuordnung [in eine](../dotnet/map-stl-clr.md) .net-<xref:System.Collections.Generic.IDictionary%602>konvertieren, aber die Prozedur ist für alle Sammlungen und Container ähnlich.

### <a name="to-create-a-collection-from-a-container"></a>So erstellen Sie eine Sammlung aus einem Container

1. Führen Sie einen der folgenden Schritte aus:

   - Um einen Teil eines Containers zu konvertieren, nennen Sie die [make_collection](../dotnet/make-collection-stl-clr.md) -Funktion, und übergeben Sie den BEGIN-Iterator und den End-Iterator des STL/CLR-Containers, der in die .net-Auflistung kopiert werden soll. Diese Vorlagen Funktion nimmt einen STL/CLR-Iterator als Vorlagen Argument an. Das erste Beispiel veranschaulicht diese Methode.

   - Um einen gesamten Container zu konvertieren, wandeln Sie den Container in eine entsprechende .net-Auflistungs Schnittstelle oder Schnittstellen Auflistung um. Das zweite Beispiel veranschaulicht diese Methode.

## <a name="example"></a>Beispiel

In diesem Beispiel erstellen wir eine STL/CLR-`vector` und fügen ihr 5 Elemente hinzu. Anschließend erstellen Sie eine .net-Auflistung, indem Sie die `make_collection`-Funktion aufrufen. Schließlich wird der Inhalt der neu erstellten Auflistung angezeigt.

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

## <a name="example"></a>Beispiel

In diesem Beispiel erstellen wir eine STL/CLR-`map` und fügen ihr 5 Elemente hinzu. Anschließend erstellen wir ein .net-<xref:System.Collections.Generic.IDictionary%602> und weisen ihm das `map` direkt zu. Schließlich wird der Inhalt der neu erstellten Auflistung angezeigt.

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

## <a name="see-also"></a>Siehe auch

[Referenz zur STL/CLR-Bibliothek](../dotnet/stl-clr-library-reference.md)<br/>
[Vorgehensweise: Umwandeln einer .Net-Auflistung in einen STL/CLR-Container](../dotnet/how-to-convert-from-a-dotnet-collection-to-a-stl-clr-container.md)<br/>
[range_adapter (STL/CLR)](../dotnet/range-adapter-stl-clr.md)
