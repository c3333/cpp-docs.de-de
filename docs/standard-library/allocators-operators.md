---
title: '&lt;Allocators&gt;-Operatoren'
ms.date: 11/04/2016
f1_keywords:
- allocators/std::operator!=
- allocators/std::operator==
ms.assetid: b55d67cb-3c69-46bf-ad40-e845fb096c4e
ms.openlocfilehash: a21708ca090b0db561391308f347d90b77c62645
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84623571"
---
# <a name="ltallocatorsgt-operators"></a>&lt;Allocators&gt;-Operatoren

Dabei handelt es sich um die Funktionen des globalen Vorlagen Operators, die in Zuweisungen definiert sind &lt; &gt; . Informationen zu Klassenmember-Operator Funktionen finden Sie in der-Klassen Dokumentation.

|||
|-|-|
|[Operator! =](#op_neq)|[Operator = =](#op_eq_eq)|

## <a name="operator"></a><a name="op_neq"></a>Operator! =

Es wird auf Ungleichheit zwischen Zuweisungsobjekten einer bestimmten Klasse getestet.

```cpp
template <class Type, class Sync>
bool operator!=(
    const allocator_base<Type, Sync>& left,
    const allocator_base<Type, Sync>& right);
```

### <a name="parameters"></a>Parameter

|Parameter|Beschreibung|
|---------------|-----------------|
|*linken*|Eines der Zuweisungsobjekte, die auf Ungleichheit geprüft werden sollen.|
|*Richting*|Eines der Zuweisungsobjekte, die auf Ungleichheit geprüft werden sollen.|

### <a name="return-value"></a>Rückgabewert

**TRUE**, wenn die Zuweisungsobjekte nicht gleich sind; **FALSE**, wenn die Zuweisungsobjekte gleich sind.

### <a name="remarks"></a>Hinweise

Der Vorlagenoperator gibt `!(left == right)` zurück.

## <a name="operator"></a><a name="op_eq_eq"></a>Operator = =

Es wird auf Gleichheit zwischen Zuweisungsobjekten einer bestimmten Klasse getestet.

```cpp
template <class Type, class Sync>
bool operator==(
    const allocator_base<Type, Sync>& left,
    const allocator_base<Type, Sync>& right);
```

### <a name="parameters"></a>Parameter

|Parameter|Beschreibung|
|---------------|-----------------|
|*linken*|Eines der Zuweisungsobjekte, die auf Gleichheit geprüft werden sollen.|
|*Richting*|Eines der Zuweisungsobjekte, die auf Gleichheit geprüft werden sollen.|

### <a name="return-value"></a>Rückgabewert

**TRUE**, wenn die Zuweisungsobjekte gleich sind; **FALSE**, wenn die Zuweisungsobjekte nicht gleich sind.

### <a name="remarks"></a>Hinweise

Dieser Vorlagenoperator gibt `left.equals(right)` zurück.

## <a name="see-also"></a>Siehe auch

[\<allocators>](allocators-header.md)
