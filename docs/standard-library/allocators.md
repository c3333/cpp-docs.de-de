---
title: Allocators
ms.date: 11/04/2016
helpviewer_keywords:
- allocators
- C++ Standard Library, allocators
ms.assetid: ac95023b-9e7d-49f5-861a-bf7a9a340746
ms.openlocfilehash: 5aee23f72c5b0fb955b4dcc76a3f8c51eca7be70
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87204234"
---
# <a name="allocators"></a>Allocators

Allocators werden von der C++-Standardbibliothek zum Verarbeiten der Zuordnung und der Aufhebung der Zuordnung von Elementen verwendet, die in Containern gespeichert sind. Alle C++-Standardbibliothekcontainer außer „std::array“ verfügen über einen Vorlagenparameter des Typs `allocator<Type>`, wobei `Type` den Typ des Containerelements darstellt. Die Vektorklasse wird zum Beispiel wie folgt deklariert:

```cpp
template <
    class Type,
    class Allocator = allocator<Type>
>
class vector
```

Die C++-Standardbibliothek stellt eine Standardimplementierung für einen Allocator bereit. In C ++ Version 11 und höher wurde der Standardallocator aktualisiert, um eine kleinere Schnittstelle verfügbar zu machen. Die neue Zuweisung wird als *minimaler Allocator* bezeichnet. Insbesondere unterstützt das `construct()`-Member des minimalen Allocators die Move-Semantik, wodurch die Leistung erheblich verbessert werden kann. In den meisten Fällen ist dieser Standardallocator ausreichend. In C ++ 11 unterstützen alle Standardbibliothekstypen und Funktionen, die einen Allocatortypparameter verwenden können, die Schnittstelle des minimalen Allocators, einschließlich `std::function`, `shared_ptr, allocate_shared()` und `basic_string`.  Weitere Informationen über den Standardallocator finden Sie unter [allocator-Klasse](allocator-class.md).

## <a name="writing-your-own-allocator-c11"></a>Schreiben von eigenen Allocators (C ++ 11)

Der standardallocator verwendet **`new`** und **`delete`** , um Speicher zuzuweisen und dessen Zuordnung zu verringern. Wenn Sie eine andere Methode für die Speicherzuordnung verwenden möchten, z. B. die Verwendung von gemeinsam genutztem Speicher, müssen Sie einen eigenen Allocator erstellen. Wenn Sie C ++ 11 als Ziel verwenden und Sie einen neuen benutzerdefinierten Allocator schreiben müssen, erstellen Sie möglichst einen minimalen Allocator. Auch wenn Sie bereits einen herkömmlichen Allocator implementiert haben, ziehen Sie in Betracht, ihn in einen *minimalen Allocator* zu ändern, um die effizientere Methode `construct()` nutzen zu können, die Ihnen automatisch bereitgestellt wird.

Ein minimaler Allocator benötigt viel weniger Textbausteine und ermöglicht Ihnen, sich auf die `allocate`- und `deallocate`-Memberfunktionen zu konzentrieren, die die gesamte Arbeit erledigen. Implementieren Sie beim Erstellen eines minimalen Allocators keine Member außer den im folgenden Beispiel dargestellten:

1. ein konvertierender Kopierkonstruktor (siehe Beispiel)

1. Operator ==

1. Operator!=

1. allocate

1. deallocate

Der C ++ 11-Standardmember `construct()`, der Ihnen bereitgestellt wird, optimiert die Weiterleitung und aktiviert die move-Semantik. Diese Version ist in den meisten Fällen wesentlich effizienter als die ältere Version.

> [!WARNING]
> Zum Zeitpunkt der Kompilierung verwendet die C++-Standardbibliothek die allocator_traits-Klasse, um zu ermitteln, welche Member Sie explizit angegeben haben. Sie stellt dann eine Standardimplementierung für alle Member bereit, die nicht vorhanden sind. Greifen Sie nicht in diesen Mechanismus ein, indem Sie eine Spezialisierung ovn „allocator_traits“ für Ihren Allocator angeben!

Das folgende Beispiel zeigt eine minimale Implementierung eines Allocators, der `malloc` und `free` verwendet. Beachten Sie die Verwendung des neuen Ausnahmetyps `std::bad_array_new_length`. Diese Ausnahme wird ausgelöst, wenn die Arraygröße kleiner als 0 (null) oder größer als die maximal zulässige Größe ist.

```cpp
#pragma once
#include <stdlib.h> //size_t, malloc, free
#include <new> // bad_alloc, bad_array_new_length
#include <memory>
template <class T>
struct Mallocator
{
    typedef T value_type;
    Mallocator() noexcept {} //default ctor not required by C++ Standard Library

    // A converting copy constructor:
    template<class U> Mallocator(const Mallocator<U>&) noexcept {}
    template<class U> bool operator==(const Mallocator<U>&) const noexcept
    {
        return true;
    }
    template<class U> bool operator!=(const Mallocator<U>&) const noexcept
    {
        return false;
    }
    T* allocate(const size_t n) const;
    void deallocate(T* const p, size_t) const noexcept;
};

template <class T>
T* Mallocator<T>::allocate(const size_t n) const
{
    if (n == 0)
    {
        return nullptr;
    }
    if (n > static_cast<size_t>(-1) / sizeof(T))
    {
        throw std::bad_array_new_length();
    }
    void* const pv = malloc(n * sizeof(T));
    if (!pv) { throw std::bad_alloc(); }
    return static_cast<T*>(pv);
}

template<class T>
void Mallocator<T>::deallocate(T * const p, size_t) const noexcept
{
    free(p);
}
```

## <a name="writing-your-own-allocator-c03"></a>Schreiben von eigenen Allocators (C ++ 03)

In C ++03 muss jeder Allocator, der mit C++-Standardbibliohekcontainern verwendet wird, die folgenden Typdefinitionen implementieren:

|||
|-|-|
|`const_pointer`|`rebind`|
|`const_reference`|`reference`|
|`difference_type`|`size_type`|
|`pointer`|`value_type`|

Außerdem muss jeder Allocator, der mit C++-Standardbibliohekcontainern verwendet wird, die folgenden Methoden implementieren:

|||
|-|-|
|Konstruktor|`deallocate`|
|Kopierkonstruktor|`destroy`|
|Destruktor|`max_size`|
|`address`|`operator==`|
|`allocate`|`operator!=`|
|`construct`||

Weitere Informationen zu diesen Typdefinitionen und Methoden finden Sie unter [allocator-Klasse](allocator-class.md).

## <a name="see-also"></a>Weitere Informationen

[C++-Standard Bibliotheks Referenz](cpp-standard-library-reference.md)
