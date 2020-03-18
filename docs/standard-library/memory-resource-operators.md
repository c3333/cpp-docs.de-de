---
title: '&lt;memory_resource&gt;-Operatoren'
ms.date: 11/04/2016
f1_keywords:
- memory_resource/std::operator!=
- memory_resource/std::operator==
helpviewer_keywords:
- std::operator!= (memory_resource)
- std::operator== (memory_resource)
ms.openlocfilehash: dd7dc3e65fe58663285433f9cbc9b64cf2b81cda
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2020
ms.locfileid: "79425472"
---
# <a name="ltmemory_resourcegt-operators"></a>&lt;memory_resource&gt;-Operatoren

## <a name="op_neq"></a>Operator! =

Testet, ob das memory_resource Objekt links vom Operator ungleich dem memory_resource Objekt rechts vom Operator ist.

```cpp
template <class T1, class T2>
    bool operator!=(const polymorphic_allocator<T1>& a, const polymorphic_allocator<T2>& b) noexcept;
```

## <a name="op_eq_eq"></a>Operator = =

Testet, ob das memory_resource Objekt links vom Operator gleich dem memory_resource Objekt rechts vom Operator ist.

```cpp
template <class T1, class T2>
    bool operator==(const polymorphic_allocator<T1>& a, const polymorphic_allocator<T2>& b) noexcept;
```
