---
title: is_pod-Klasse
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_pod
helpviewer_keywords:
- is_pod class
- is_pod
ms.assetid: d73ebdee-746b-4082-9fa4-2db71432eb0e
ms.openlocfilehash: 1398da92890072d8aa8a6f07c61920fe3bee1776
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212240"
---
# <a name="is_pod-class"></a>is_pod-Klasse

Testet, ob der Typ POD ist.

## <a name="syntax"></a>Syntax

```cpp
template <class T>
struct is_pod;
```

### <a name="parameters"></a>Parameter

*Bund*\
Der abzufragende Typ.

## <a name="remarks"></a>Bemerkungen

`is_pod<T>::value`Gibt an, **`true`** ob der Typ *T* Plain Old Data (Pod) ist. Andernfalls ist der Wert **`false`** .

Arithmetische Typen, Enumerationstypen, Zeigertypen und Zeiger auf Membertypen sind POD.

Eine cv-qualifizierte Version eines POD-Typs ist selbst ein POD-Typ.

Ein Array von POD ist selbst POD.

Eine Struktur oder Union, all deren nicht statische Datenmember POD sind, ist selbst POD, wenn sie Folgendes aufweist:

- Keine benutzerdeklarierten Konstruktoren

- Keine privaten oder geschützten nicht statischen Datenmember

- Keine Basisklassen

- Keine virtuellen Funktionen

- Keine nicht statischen Datenmember des Verweistyps

- Keinen benutzerdefinierten Kopierzuweisungsoperator

- Keinen benutzerdefinierten Destruktor

Aus diesem Grund können Sie rekursiv POD-Strukturen und -Arrays erstellen, die POD-Strukturen und -Arrays enthalten.

## <a name="example"></a>Beispiel

```cpp
// std__type_traits__is_pod.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

struct trivial {
    int val;
};

struct throws {
    throws() {}  // User-declared ctor, so not POD

    int val;
};

int main() {
    std::cout << "is_pod<trivial> == " << std::boolalpha
        << std::is_pod<trivial>::value << std::endl;
    std::cout << "is_pod<int> == " << std::boolalpha
        << std::is_pod<int>::value << std::endl;
    std::cout << "is_pod<throws> == " << std::boolalpha
        << std::is_pod<throws>::value << std::endl;

    return (0);
}
```

```Output
is_pod<trivial> == true
is_pod<int> == true
is_pod<throws> == false
```

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<type_traits>

**Namespace:** std

## <a name="see-also"></a>Weitere Informationen

[<type_traits>](../standard-library/type-traits.md)
