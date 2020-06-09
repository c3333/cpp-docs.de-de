---
title: aligned_storage-Klasse
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::aligned_storage
helpviewer_keywords:
- aligned_storage class
- aligned_storage
ms.assetid: f255e345-1f05-4d07-81e4-017f420839fb
ms.openlocfilehash: 741106888cdab63a75e090e860269f125c35efa6
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84623829"
---
# <a name="aligned_storage-class"></a>aligned_storage-Klasse

Erstellt einen entsprechend ausgerichteten Typ.

## <a name="syntax"></a>Syntax

```cpp
template <std::size_t Len, std::size_t Align>
struct aligned_storage;

template <std::size_t Len, std::size_t Align = alignment_of<max_align_t>::value>
using aligned_storage_t = typename aligned_storage<Len, Align>::type;
```

### <a name="parameters"></a>Parameter

*Nest*\
Die Objektgröße.

*Abzustimmen*\
Die Objektausrichtung.

## <a name="remarks"></a>Hinweise

Das Vorlagenmember-Typdefinition `type` ist ein Synonym für einen POD-Typ *Align* mit Ausrichtungs Ausrichtung und Größen- *len*. *Align* muss `alignment_of<T>::value` bei einem Typ `T` oder der Standardausrichtung gleich sein.

## <a name="example"></a>Beispiel

```cpp
#include <type_traits>
#include <iostream>

typedef std::aligned_storage<sizeof (int),
    std::alignment_of<double>::value>::type New_type;
int main()
    {
    std::cout << "alignment_of<int> == "
        << std::alignment_of<int>::value << std::endl;
    std::cout << "aligned to double == "
        << std::alignment_of<New_type>::value << std::endl;

    return (0);
    }
```

```Output
alignment_of<int> == 4
aligned to double == 8
```

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<type_traits>

**Namespace:** std

## <a name="see-also"></a>Siehe auch

[<type_traits>](type-traits.md)\
[alignment_of-Klasse](alignment-of-class.md)
