---
title: '&lt;forward_list&gt;-Operatoren'
ms.date: 11/04/2016
f1_keywords:
- forward_list/std::operator!=
- forward_list/std::operator==
- forward_list/std::operatoroperator&gt;
- forward_list/std::operatoroperator&gt=;
- forward_list/std::operatoroperator&lt;
- forward_list/std::operatoroperator&lt;=
ms.assetid: 57492e09-3836-4dbc-9ae5-78ecf506c190
helpviewer_keywords:
- std::operator!= (forward_list)
- std::operator== (forward_list)
- std::operatoroperator&gt; (forward_list)
- std::operatoroperator&gt=; (forward_list)
- std::operatoroperator&lt; (forward_list)
- std::operatoroperator&lt;= (forward_list)
ms.openlocfilehash: beb02a8353c6c5187dd0fa0171518c753eee7868
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87193340"
---
# <a name="ltforward_listgt-operators"></a>&lt;forward_list&gt;-Operatoren

## <a name="operator"></a><a name="op_eq_eq"></a>Operator = =

Testet, ob das Listenobjekt links vom Operator gleich dem Listenobjekt rechts vom Operator ist

```cpp
bool operator==(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>Parameter

*linken*\
Ein Objekt des Typs `forward_list`.

*Richting*\
Ein Objekt des Typs `forward_list`.

### <a name="remarks"></a>Bemerkungen

Diese Vorlagen Funktion überlädt `operator==` , um zwei Objekte der Klassen Vorlage zu vergleichen `forward_list` . Die Funktion gibt `distance(left.begin(), end()) == distance(right.begin(),right.end()) && equal(left. begin(),left. end(),right.begin())` zurück.

## <a name="operator"></a><a name="op_neq"></a>Operator! =

Testet, ob das Weiterleitungslistenobjekt links vom Operator ungleich dem Listenobjekt rechts vom Operator ist.

```cpp
bool operator!=(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>Parameter

*linken*\
Ein Objekt des Typs `forward_list`.

*Richting*\
Ein Objekt des Typs `forward_list`.

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn die Listen nicht gleich sind. , **`false`** Wenn die Listen gleich sind.

### <a name="remarks"></a>Bemerkungen

Diese Vorlagenfunktion gibt `!(left == right)` zurück.

## <a name="operatorlt"></a><a name="op_lt"></a>KOM&lt;

Testet, ob das Listenobjekt links vom Operator kleiner als das Listenobjekt auf der rechten Seite ist

```cpp
bool operator<(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>Parameter

*linken*\
Ein Objekt des Typs `forward_list`.

*Richting*\
Ein Objekt des Typs `forward_list`.

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn die Liste links vom Operator kleiner als, aber nicht gleich der Liste rechts vom Operator ist. andernfalls **`false`** .

### <a name="remarks"></a>Bemerkungen

Diese Vorlagen Funktion überlädt `operator<` , um zwei Objekte der Klassen Vorlage zu vergleichen `forward_list` . Die Funktion gibt `lexicographical_compare(lhs. begin(), lhs. end(), rhs.begin(), rhs.end())` zurück.

## <a name="operatorlt"></a><a name="op_lt_eq"></a>KOM&lt;=

Testet, ob das Listenobjekt links vom Operator kleiner als oder gleich dem Listenobjekt rechts vom Operator ist

```cpp
bool operator<=(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>Parameter

*linken*\
Ein Objekt des Typs `forward_list`.

*Richting*\
Ein Objekt des Typs `forward_list`.

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn die Liste links vom Operator kleiner als oder gleich der Liste rechts vom Operator ist. andernfalls **`false`** .

### <a name="remarks"></a>Bemerkungen

Diese Vorlagenfunktion gibt `!(right < left)` zurück.

## <a name="operatorgt"></a><a name="op_gt"></a>KOM&gt;

Testet, ob das Listenobjekt links vom Operator größer als das Listenobjekt auf der rechten Seite ist

```cpp
bool operator>(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>Parameter

*linken*\
Ein Objekt des Typs `forward_list`.

*Richting*\
Ein Objekt des Typs `forward_list`.

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn die Liste links vom Operator größer als die Liste rechts vom Operator ist. andernfalls **`false`** .

### <a name="remarks"></a>Bemerkungen

Diese Vorlagenfunktion gibt `right < left` zurück.

## <a name="operatorgt"></a><a name="op_gt_eq"></a>KOM&gt;=

Testet, ob das Listenobjekt links vom Operator größer als oder gleich dem Listenobjekt rechts vom Operator ist.

```cpp
bool operator>=(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>Parameter

*linken*\
Ein Objekt des Typs `forward_list`.

*Richting*\
Ein Objekt des Typs `forward_list`.

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn die vorwärts Liste links vom Operator größer als oder gleich der vorwärts Liste auf der rechten Seite des Operators ist. andernfalls **`false`** .

### <a name="remarks"></a>Bemerkungen

Diese Vorlagenfunktion gibt `!(left < right)` zurück.
