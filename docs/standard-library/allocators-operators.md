---
title: '&lt;Allocators&gt;-Operatoren'
ms.date: 11/04/2016
f1_keywords:
- allocators/std::operator!=
- allocators/std::operator==
ms.assetid: b55d67cb-3c69-46bf-ad40-e845fb096c4e
ms.openlocfilehash: b7429e298cdf14d727fc481db6c4a3bf8574b5e7
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78875957"
---
# <a name="ltallocatorsgt-operators"></a>&lt;Allocators&gt;-Operatoren

Dies sind die Funktionen des globalen Vorlagen Operators, die in &lt;Zuweisungs&gt;definiert sind. Informationen zu Klassenmember-Operator Funktionen finden Sie in der-Klassen Dokumentation.

|||
|-|-|
|[operator!=](#op_neq)|[operator==](#op_eq_eq)|

## <a name="op_neq"></a> operator!=

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
|*left*|Eines der Zuweisungsobjekte, die auf Ungleichheit geprüft werden sollen.|
|*right*|Eines der Zuweisungsobjekte, die auf Ungleichheit geprüft werden sollen.|

### <a name="return-value"></a>Rückgabewert

**TRUE**, wenn die Zuweisungsobjekte nicht gleich sind; **FALSE**, wenn die Zuweisungsobjekte gleich sind.

### <a name="remarks"></a>Bemerkungen

Der Vorlagenoperator gibt `!(left == right)` zurück.

## <a name="op_eq_eq"></a> operator==

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
|*left*|Eines der Zuweisungsobjekte, die auf Gleichheit geprüft werden sollen.|
|*right*|Eines der Zuweisungsobjekte, die auf Gleichheit geprüft werden sollen.|

### <a name="return-value"></a>Rückgabewert

**TRUE**, wenn die Zuweisungsobjekte gleich sind; **FALSE**, wenn die Zuweisungsobjekte nicht gleich sind.

### <a name="remarks"></a>Bemerkungen

Dieser Vorlagenoperator gibt `left.equals(right)` zurück.

## <a name="see-also"></a>Weitere Informationen

[\<allocators>](../standard-library/allocators-header.md)
