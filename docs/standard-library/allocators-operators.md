---
title: '&lt;Allocators&gt;-Operatoren'
ms.date: 11/04/2016
f1_keywords:
- allocators/std::operator!=
- allocators/std::operator==
ms.assetid: b55d67cb-3c69-46bf-ad40-e845fb096c4e
ms.openlocfilehash: 969c9f8e05a9fafad4d3a1102060e2b3d4d0eb2e
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88844781"
---
# <a name="ltallocatorsgt-operators"></a>&lt;Allocators&gt;-Operatoren

Dabei handelt es sich um die Funktionen des globalen Vorlagen Operators, die in Zuweisungen definiert sind &lt; &gt; . Informationen zu Klassenmember-Operator Funktionen finden Sie in der-Klassen Dokumentation.

[Operator! =](#op_neq)\
[Operator = =](#op_eq_eq)

## <a name="operator"></a><a name="op_neq"></a> Operator! =

Es wird auf Ungleichheit zwischen Zuweisungsobjekten einer bestimmten Klasse getestet.

```cpp
template <class Type, class Sync>
bool operator!=(
    const allocator_base<Type, Sync>& left,
    const allocator_base<Type, Sync>& right);
```

### <a name="parameters"></a>Parameter

*linken*\
Eines der Zuweisungsobjekte, die auf Ungleichheit geprüft werden sollen.

*Richting*\
Eines der Zuweisungsobjekte, die auf Ungleichheit geprüft werden sollen.

### <a name="return-value"></a>Rückgabewert

**`true`** , wenn die zuordnerobjekte nicht gleich sind. , **`false`** Wenn zuordnerobjekte gleich sind.

### <a name="remarks"></a>Bemerkungen

Der Vorlagenoperator gibt `!(left == right)` zurück.

## <a name="operator"></a><a name="op_eq_eq"></a> Operator = =

Es wird auf Gleichheit zwischen Zuweisungsobjekten einer bestimmten Klasse getestet.

```cpp
template <class Type, class Sync>
bool operator==(
    const allocator_base<Type, Sync>& left,
    const allocator_base<Type, Sync>& right);
```

### <a name="parameters"></a>Parameter

*linken*\
Eines der Zuweisungsobjekte, die auf Gleichheit geprüft werden sollen.

*Richting*\
Eines der Zuweisungsobjekte, die auf Gleichheit geprüft werden sollen.

### <a name="return-value"></a>Rückgabewert

**`true`** , wenn die zuordnerobjekte gleich sind. , **`false`** Wenn zuordnerobjekte nicht gleich sind.

### <a name="remarks"></a>Bemerkungen

Dieser Vorlagenoperator gibt `left.equals(right)` zurück.

## <a name="see-also"></a>Weitere Informationen

[\<allocators>](allocators-header.md)
