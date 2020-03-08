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
ms.openlocfilehash: 1ddfb56c7ff68ec10c7bb56af3495e4042acb83c
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78874755"
---
# <a name="ltforward_listgt-operators"></a>&lt;forward_list&gt;-Operatoren

## <a name="op_eq_eq"></a>Operator = =

Testet, ob das Weiterleitungslistenobjekt links vom Operator gleich dem Weiterleitungslistenobjekt rechts vom Operator ist.

```cpp
bool operator==(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>Parameter

*Linker*\
Ein Objekt des Typs `forward_list`.

*Rechte*\
Ein Objekt des Typs `forward_list`.

### <a name="remarks"></a>Bemerkungen

Diese Vorlagen Funktion überlädt `operator==`, um zwei Objekte der Klassen Vorlagen `forward_list`zu vergleichen. Die Funktion gibt `distance(left.begin(), end()) == distance(right.begin(),right.end()) && equal(left. begin(),left. end(),right.begin())`zurück.

## <a name="op_neq"></a>Operator! =

Testet, ob das Listenobjekt links vom Operator ungleich dem Listenobjekt rechts vom Operator ist

```cpp
bool operator!=(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>Parameter

*Linker*\
Ein Objekt des Typs `forward_list`.

*Rechte*\
Ein Objekt des Typs `forward_list`.

### <a name="return-value"></a>Rückgabewert

**TRUE**, wenn die Listen ungleich sind; **FALSE**, wenn die Listen gleich sind.

### <a name="remarks"></a>Bemerkungen

Die dritte Vorlagenfunktion gibt `!(left == right)` zurück.

## <a name="op_lt"></a>-Operator&lt;

Testet, ob das Listenobjekt links vom Operator kleiner als das Listenobjekt auf der rechten Seite ist.

```cpp
bool operator<(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>Parameter

*Linker*\
Ein Objekt des Typs `forward_list`.

*Rechte*\
Ein Objekt des Typs `forward_list`.

### <a name="return-value"></a>Rückgabewert

**TRUE**, wenn die Liste links vom Operator kleiner als, aber ungleich der Liste rechts vom Operator ist; andernfalls **FALSE**.

### <a name="remarks"></a>Bemerkungen

Diese Vorlagen Funktion überlädt `operator<`, um zwei Objekte der Klassen Vorlagen `forward_list`zu vergleichen. Die Funktion gibt `lexicographical_compare(lhs. begin(), lhs. end(), rhs.begin(), rhs.end())`zurück.

## <a name="op_lt_eq"></a>Operator&lt;=

Testet, ob das Listenobjekt links vom Operator kleiner als oder gleich dem Listenobjekt rechts vom Operator ist.

```cpp
bool operator<=(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>Parameter

*Linker*\
Ein Objekt des Typs `forward_list`.

*Rechte*\
Ein Objekt des Typs `forward_list`.

### <a name="return-value"></a>Rückgabewert

**TRUE**, wenn die Liste links vom Operator kleiner als oder gleich der Liste rechts vom Operator ist; andernfalls **FALSE**.

### <a name="remarks"></a>Bemerkungen

Die dritte Vorlagenfunktion gibt `!(right < left)` zurück.

## <a name="op_gt"></a>-Operator&gt;

Testet, ob das Listenobjekt links vom Operator größer als das Listenobjekt auf der rechten Seite ist.

```cpp
bool operator>(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>Parameter

*Linker*\
Ein Objekt des Typs `forward_list`.

*Rechte*\
Ein Objekt des Typs `forward_list`.

### <a name="return-value"></a>Rückgabewert

**TRUE**, wenn die Liste links vom Operator größer als die Liste rechts vom Operator ist; andernfalls **FALSE**.

### <a name="remarks"></a>Bemerkungen

Die dritte Vorlagenfunktion gibt `right < left` zurück.

## <a name="op_gt_eq"></a>Operator&gt;=

Testet, ob das Listenobjekt links vom Operator größer als oder gleich dem Listenobjekt rechts vom Operator ist

```cpp
bool operator>=(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>Parameter

*Linker*\
Ein Objekt des Typs `forward_list`.

*Rechte*\
Ein Objekt des Typs `forward_list`.

### <a name="return-value"></a>Rückgabewert

**true** , wenn die vorwärts Liste links vom Operator größer als oder gleich der vorwärts Liste auf der rechten Seite des Operators ist. andernfalls **false**.

### <a name="remarks"></a>Bemerkungen

Die Vorlagenfunktion gibt `!(left < right)` zurück.
