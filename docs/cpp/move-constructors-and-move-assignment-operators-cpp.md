---
title: 'Gewusst wie: Definieren von bewegungskonstruktoren und Bewegungs Zuweisungs Operatoren (C++)'
ms.date: 03/05/2018
helpviewer_keywords:
- move constructor [C++]
ms.assetid: e75efe0e-4b74-47a9-96ed-4e83cfc4378d
ms.openlocfilehash: 81f717162e2c7bebc62a9deeb208700380f62cb8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179366"
---
# <a name="move-constructors-and-move-assignment-operators-c"></a>Bewegungskonstruktoren und Bewegungszuweisungsoperatoren (C++)

In diesem Thema wird beschrieben, wie ein *bewegungskonstruktor* und ein Bewegungs Zuweisungs C++ Operator für eine Klasse geschrieben werden. Ein bewegungskonstruktor ermöglicht, dass die Ressourcen, die im Besitz eines Rvalue-Objekts sind, ohne Kopieren in einen lvalue verschoben werden. Weitere Informationen zur Verschiebungs Semantik finden Sie unter [rvalue reference declarator: & &](../cpp/rvalue-reference-declarator-amp-amp.md).

Dieses Thema baut auf der C++-Klasse `MemoryBlock` auf, mit der ein Arbeitsspeicherpuffer verwaltet wird.

```cpp
// MemoryBlock.h
#pragma once
#include <iostream>
#include <algorithm>

class MemoryBlock
{
public:

   // Simple constructor that initializes the resource.
   explicit MemoryBlock(size_t length)
      : _length(length)
      , _data(new int[length])
   {
      std::cout << "In MemoryBlock(size_t). length = "
                << _length << "." << std::endl;
   }

   // Destructor.
   ~MemoryBlock()
   {
      std::cout << "In ~MemoryBlock(). length = "
                << _length << ".";

      if (_data != nullptr)
      {
         std::cout << " Deleting resource.";
         // Delete the resource.
         delete[] _data;
      }

      std::cout << std::endl;
   }

   // Copy constructor.
   MemoryBlock(const MemoryBlock& other)
      : _length(other._length)
      , _data(new int[other._length])
   {
      std::cout << "In MemoryBlock(const MemoryBlock&). length = "
                << other._length << ". Copying resource." << std::endl;

      std::copy(other._data, other._data + _length, _data);
   }

   // Copy assignment operator.
   MemoryBlock& operator=(const MemoryBlock& other)
   {
      std::cout << "In operator=(const MemoryBlock&). length = "
                << other._length << ". Copying resource." << std::endl;

      if (this != &other)
      {
         // Free the existing resource.
         delete[] _data;

         _length = other._length;
         _data = new int[_length];
         std::copy(other._data, other._data + _length, _data);
      }
      return *this;
   }

   // Retrieves the length of the data resource.
   size_t Length() const
   {
      return _length;
   }

private:
   size_t _length; // The length of the resource.
   int* _data; // The resource.
};
```

Die folgenden Prozeduren beschreiben, wie ein Bewegungskonstruktor und ein Bewegungszuweisungsoperator für die C++-Beispielklasse geschrieben werden.

### <a name="to-create-a-move-constructor-for-a-c-class"></a>So erstellen Sie einen Bewegungskonstruktor für eine C++-Klasse

1. Definieren Sie, wie im folgenden Beispiel veranschaulicht, eine leere Konstruktormethode, die einen rvalu-Verweis auf den Klassentyp als Parameter akzeptiert:

    ```cpp
    MemoryBlock(MemoryBlock&& other)
       : _data(nullptr)
       , _length(0)
    {
    }
    ```

1. Weisen Sie dem Objekt, das erstellt wird, im Bewegungskonstruktor die Klassendatenmember aus dem Quellobjekt zu:

    ```cpp
    _data = other._data;
    _length = other._length;
    ```

1. Weisen Sie den Standardwerten die Datenmember des Quellobjekts zu. Das hindert den Destruktor an der mehrfachen Freigabe von Ressourcen (z. B. Arbeitsspeicher):

    ```cpp
    other._data = nullptr;
    other._length = 0;
    ```

### <a name="to-create-a-move-assignment-operator-for-a-c-class"></a>So erstellen Sie einen Bewegungszuweisungsoperator für eine C++-Klasse

1. Definieren Sie, wie im folgenden Beispiel veranschaulicht, einen leeren Zuweisungsoperator, der einen rvalu-Verweis auf den Klassentyp als dessen Parameter akzeptiert und einen Verweis auf den Klassentyp zurückgibt:

    ```cpp
    MemoryBlock& operator=(MemoryBlock&& other)
    {
    }
    ```

1. Fügen Sie dem Bewegungszuweisungsoperator eine bedingte Anweisung hinzu, die bei dem Versuch, das Objekt sich selbst zuzuweisen, keinen Vorgang ausführt.

    ```cpp
    if (this != &other)
    {
    }
    ```

1. Geben Sie in der Bedingungsanweisung alle Ressourcen (z. B. Arbeitsspeicher) aus dem Objekt, dem sie zugewiesen sind, frei.

   Im folgenden Beispiel wird der `_data`-Member vom zugewiesenen Objekt freigegeben.

    ```cpp
    // Free the existing resource.
    delete[] _data;
    ```

   Führen Sie die Schritte 2 und 3 der ersten Prozedur aus, um die Datenmember aus dem Quellobjekt auf das zu erstellende Objekt zu übergeben:

    ```cpp
    // Copy the data pointer and its length from the
    // source object.
    _data = other._data;
    _length = other._length;

    // Release the data pointer from the source object so that
    // the destructor does not free the memory multiple times.
    other._data = nullptr;
    other._length = 0;
    ```

1. Geben Sie, wie im folgenden Beispiel veranschaulicht, einen Verweis auf das aktuelle Objekt zurück:

    ```cpp
    return *this;
    ```

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird der vollständige Bewegungskonstruktor und der Bewegungszuweisungsoperator für die `MemoryBlock`-Klasse veranschaulicht:

```cpp
// Move constructor.
MemoryBlock(MemoryBlock&& other)
   : _data(nullptr)
   , _length(0)
{
   std::cout << "In MemoryBlock(MemoryBlock&&). length = "
             << other._length << ". Moving resource." << std::endl;

   // Copy the data pointer and its length from the
   // source object.
   _data = other._data;
   _length = other._length;

   // Release the data pointer from the source object so that
   // the destructor does not free the memory multiple times.
   other._data = nullptr;
   other._length = 0;
}

// Move assignment operator.
MemoryBlock& operator=(MemoryBlock&& other)
{
   std::cout << "In operator=(MemoryBlock&&). length = "
             << other._length << "." << std::endl;

   if (this != &other)
   {
      // Free the existing resource.
      delete[] _data;

      // Copy the data pointer and its length from the
      // source object.
      _data = other._data;
      _length = other._length;

      // Release the data pointer from the source object so that
      // the destructor does not free the memory multiple times.
      other._data = nullptr;
      other._length = 0;
   }
   return *this;
}
```

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird eine Verbesserung der Leistung Ihrer Anwendungen mithilfe von Bewegungssemantik veranschaulicht. Im Beispiel werden einem Vektorobjekt zwei Elemente hinzugefügt, daraufhin wird ein neues Element zwischen den beiden bestehenden Elementen eingefügt. Die `vector`-Klasse verwendet Verschiebungs Semantik, um den Einfügevorgang effizient auszuführen, indem die Elemente des Vektors verschoben werden, anstatt Sie zu kopieren.

```cpp
// rvalue-references-move-semantics.cpp
// compile with: /EHsc
#include "MemoryBlock.h"
#include <vector>

using namespace std;

int main()
{
   // Create a vector object and add a few elements to it.
   vector<MemoryBlock> v;
   v.push_back(MemoryBlock(25));
   v.push_back(MemoryBlock(75));

   // Insert a new element into the second position of the vector.
   v.insert(v.begin() + 1, MemoryBlock(50));
}
```

Hierdurch wird folgende Ausgabe generiert:

```Output
In MemoryBlock(size_t). length = 25.
In MemoryBlock(MemoryBlock&&). length = 25. Moving resource.
In ~MemoryBlock(). length = 0.
In MemoryBlock(size_t). length = 75.
In MemoryBlock(MemoryBlock&&). length = 25. Moving resource.
In ~MemoryBlock(). length = 0.
In MemoryBlock(MemoryBlock&&). length = 75. Moving resource.
In ~MemoryBlock(). length = 0.
In MemoryBlock(size_t). length = 50.
In MemoryBlock(MemoryBlock&&). length = 50. Moving resource.
In MemoryBlock(MemoryBlock&&). length = 50. Moving resource.
In operator=(MemoryBlock&&). length = 75.
In operator=(MemoryBlock&&). length = 50.
In ~MemoryBlock(). length = 0.
In ~MemoryBlock(). length = 0.
In ~MemoryBlock(). length = 25. Deleting resource.
In ~MemoryBlock(). length = 50. Deleting resource.
In ~MemoryBlock(). length = 75. Deleting resource.
```

Vor Visual Studio 2010 wurde in diesem Beispiel die folgende Ausgabe erzeugt:

```Output
In MemoryBlock(size_t). length = 25.
In MemoryBlock(const MemoryBlock&). length = 25. Copying resource.
In ~MemoryBlock(). length = 25. Deleting resource.
In MemoryBlock(size_t). length = 75.
In MemoryBlock(const MemoryBlock&). length = 25. Copying resource.
In ~MemoryBlock(). length = 25. Deleting resource.
In MemoryBlock(const MemoryBlock&). length = 75. Copying resource.
In ~MemoryBlock(). length = 75. Deleting resource.
In MemoryBlock(size_t). length = 50.
In MemoryBlock(const MemoryBlock&). length = 50. Copying resource.
In MemoryBlock(const MemoryBlock&). length = 50. Copying resource.
In operator=(const MemoryBlock&). length = 75. Copying resource.
In operator=(const MemoryBlock&). length = 50. Copying resource.
In ~MemoryBlock(). length = 50. Deleting resource.
In ~MemoryBlock(). length = 50. Deleting resource.
In ~MemoryBlock(). length = 25. Deleting resource.
In ~MemoryBlock(). length = 50. Deleting resource.
In ~MemoryBlock(). length = 75. Deleting resource.
```

Die Version dieses Beispiels mit Bewegungssemantik ist effizienter als die Version ohne Bewegungssemantik, da weniger Vorgänge zum Kopieren, zur Speicherbelegung und zur Freigabe der Speicherbelegung ausgeführt werden.

## <a name="robust-programming"></a>Robuste Programmierung

Zur Vermeidung von Ressourcenverlusten geben Sie Ressourcen (z. B. Arbeitsspeicher, Dateihandles und Sockets) im Bewegungszuweisungsoperator immer frei.

Um eine nicht behebbare Zerstörung von Ressourcen zu verhindern, müssen Sie die Selbstzuweisung im Bewegungszuweisungsoperator ordnungsgemäß behandeln.

Werden sowohl ein Bewegungskonstruktor als auch ein Bewegungszuweisungsoperator für die Klasse bereitgestellt, kann redundanter Code vermeiden werden, indem der Bewegungskonstruktor für den Aufruf des Bewegungszuweisungsoperators geschrieben wird. Im folgenden Beispiel wird eine überarbeitete Version des Bewegungskonstruktors, der den Bewegungszuweisungsoperator aufruft, veranschaulicht:

```cpp
// Move constructor.
MemoryBlock(MemoryBlock&& other)
   : _data(nullptr)
   , _length(0)
{
   *this = std::move(other);
}
```

Die [Std:: Move](../standard-library/utility-functions.md#move) -Funktion behält die Rvalue-Eigenschaft des *anderen* Parameters bei.

## <a name="see-also"></a>Siehe auch

[Rvalue-Verweisdeklarator: &&](../cpp/rvalue-reference-declarator-amp-amp.md)<br/>
[Std:: Move](../standard-library/utility-functions.md#move)
