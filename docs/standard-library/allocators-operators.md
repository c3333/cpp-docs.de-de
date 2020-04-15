---
title: '&lt;Allocators&gt;-Operatoren'
ms.date: 11/04/2016
f1_keywords:
- allocators/std::operator!=
- allocators/std::operator==
ms.assetid: b55d67cb-3c69-46bf-ad40-e845fb096c4e
ms.openlocfilehash: 7bc37e98ed85582cac8fc7ae21e54a6d5da9e06f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364964"
---
# <a name="ltallocatorsgt-operators"></a>&lt;Allocators&gt;-Operatoren

Dies sind die globalen &lt;Vorlagenoperatorfunktionen, die in Zuallokatoren&gt;definiert sind. Informationen zu Klassenmemberoperatorfunktionen finden Sie in der Klassendokumentation.

|||
|-|-|
|[Operator!=](#op_neq)|[Betreiber== Einzelnachweise ==](#op_eq_eq)|

## <a name="operator"></a><a name="op_neq"></a>Operator!=

Es wird auf Ungleichheit zwischen Zuweisungsobjekten einer bestimmten Klasse getestet.

```cpp
template <class Type, class Sync>
bool operator!=(
    const allocator_base<Type, Sync>& left,
    const allocator_base<Type, Sync>& right);
```

### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|*Links*|Eines der Zuweisungsobjekte, die auf Ungleichheit geprüft werden sollen.|
|*Richting*|Eines der Zuweisungsobjekte, die auf Ungleichheit geprüft werden sollen.|

### <a name="return-value"></a>Rückgabewert

**TRUE**, wenn die Zuweisungsobjekte nicht gleich sind; **FALSE**, wenn die Zuweisungsobjekte gleich sind.

### <a name="remarks"></a>Bemerkungen

Der Vorlagenoperator gibt `!(left == right)` zurück.

## <a name="operator"></a><a name="op_eq_eq"></a>Betreiber== Einzelnachweise ==

Es wird auf Gleichheit zwischen Zuweisungsobjekten einer bestimmten Klasse getestet.

```cpp
template <class Type, class Sync>
bool operator==(
    const allocator_base<Type, Sync>& left,
    const allocator_base<Type, Sync>& right);
```

### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|*Links*|Eines der Zuweisungsobjekte, die auf Gleichheit geprüft werden sollen.|
|*Richting*|Eines der Zuweisungsobjekte, die auf Gleichheit geprüft werden sollen.|

### <a name="return-value"></a>Rückgabewert

**TRUE**, wenn die Zuweisungsobjekte gleich sind; **FALSE**, wenn die Zuweisungsobjekte nicht gleich sind.

### <a name="remarks"></a>Bemerkungen

Dieser Vorlagenoperator gibt `left.equals(right)` zurück.

## <a name="see-also"></a>Siehe auch

[\<Zuallokatoren>](../standard-library/allocators-header.md)
