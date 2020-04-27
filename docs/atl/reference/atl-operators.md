---
title: ATL-Operatoren
ms.date: 11/04/2016
helpviewer_keywords:
- operators [ATL]
ms.assetid: 58ccd252-2869-45ee-8a5c-3ca40ee7f8a2
ms.openlocfilehash: fe5363d3d05123c17e45254898e2210797400022
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168851"
---
# <a name="atl-operators"></a>ATL-Operatoren

Dieser Abschnitt enthält die Referenz Themen für die globalen ATL-Operatoren.

|Operator|BESCHREIBUNG|
|--------------|-----------------|
|[Operator = =](#operator_eq_eq)|Vergleicht zwei `CSid` -Objekte `SID` oder-Strukturen auf Gleichheit.|
|[Operator! =](#operator_neq)|Vergleicht zwei `CSid` -Objekte `SID` oder-Strukturen auf Ungleichheit.|
|[Operator <](#operator_lt)|Testet, ob `CSid` das Objekt `SID` oder die Struktur auf der linken Seite des Operators kleiner ist als `CSid` das Objekt `SID` oder die Struktur auf der rechten Seite (für die Kompatibilität der C++-Standard Bibliothek).|
|[Operator >](#operator_gt)|Testet, ob `CSid` das Objekt `SID` oder die Struktur auf der linken Seite des Operators größer als das `CSid` Objekt oder `SID` die Struktur auf der rechten Seite ist (für die Kompatibilität der C++-Standard Bibliothek).|
|[Operator <=](#operator_lt__eq)|Testet, ob `CSid` das Objekt `SID` oder die Struktur auf der linken Seite des Operators kleiner als oder gleich dem Objekt `CSid` oder `SID` der Struktur auf der rechten Seite ist (für die Kompatibilität der C++-Standard Bibliothek).|
|[Operator >=](#operator_gt__eq)|Testet, ob `CSid` das Objekt `SID` oder die Struktur Links vom Operator größer als oder gleich dem Objekt oder `CSid` `SID` der Struktur auf der rechten Seite ist (für die Kompatibilität der C++-Standard Bibliothek).|

## <a name="requirements"></a>Anforderungen

**Header:** ATLSecurity. h.

## <a name="operator-"></a><a name="operator_eq_eq"></a>Operator = =

Vergleicht `CSid` Objekte oder `SID` (sicherheitsbezeichnerstrukturen) auf Gleichheit.

```cpp
bool operator==(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>Parameter

*LHS*<br/>
Das erste `CSid` zu vergleichende `SID` Objekt oder die erste zu vergleichende Struktur.

*rhs*<br/>
Das zweite `CSid` zu vergleichende `SID` Objekt oder die zweite zu vergleichende Struktur.

### <a name="return-value"></a>Rückgabewert

Gibt true zurück, wenn die Objekte gleich sind, false, wenn Sie nicht gleich sind.

## <a name="operator-"></a><a name="operator_neq"></a>Operator! =

Vergleicht `CSid` Objekte oder `SID` (Sicherheits-ID)-Strukturen auf Ungleichheit.

```cpp
bool operator==(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>Parameter

*LHS*<br/>
Das erste `CSid` zu vergleichende `SID` Objekt oder die erste zu vergleichende Struktur.

*rhs*<br/>
Das zweite `CSid` zu vergleichende `SID` Objekt oder die zweite zu vergleichende Struktur.

### <a name="return-value"></a>Rückgabewert

Gibt true zurück, wenn die Objekte nicht gleich sind, false, wenn Sie gleich sind.

## <a name="operator-"></a><a name="operator_lt"></a>Operator <

Testet, ob `CSid` das Objekt `SID` oder die Struktur auf der linken Seite des Operators kleiner ist als `CSid` das Objekt `SID` oder die Struktur auf der rechten Seite (für die Kompatibilität der C++-Standard Bibliothek).

```cpp
bool operator<(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>Parameter

*LHS*<br/>
Das erste `CSid` zu vergleichende `SID` Objekt oder die erste zu vergleichende Struktur.

*rhs*<br/>
Das zweite `CSid` zu vergleichende `SID` Objekt oder die zweite zu vergleichende Struktur.

### <a name="return-value"></a>Rückgabewert

Gibt true zurück, wenn die Adresse des *LHS* -Objekts kleiner als die Adresse des *RHS* -Objekts ist, andernfalls false.

### <a name="remarks"></a>Bemerkungen

Dieser Operator verhält sich mit der Adresse des `CSid` Objekts oder `SID` der Struktur und wird implementiert, um die Kompatibilität mit C++-Standard Bibliotheks Auflistungs Klassen zu gewährleisten.

## <a name="operator-"></a><a name="operator_gt"></a>Operator >

Testet, ob `CSid` das Objekt `SID` oder die Struktur auf der linken Seite des Operators größer als das `CSid` Objekt oder `SID` die Struktur auf der rechten Seite ist (für die Kompatibilität der C++-Standard Bibliothek).

```cpp
bool operator<(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>Parameter

*LHS*<br/>
Das erste `CSid` zu vergleichende `SID` Objekt oder die erste zu vergleichende Struktur.

*rhs*<br/>
Das zweite `CSid` zu vergleichende `SID` Objekt oder die zweite zu vergleichende Struktur.

### <a name="return-value"></a>Rückgabewert

Gibt "true" zurück, wenn die Adresse des *LHS* größer als die Adresse des *RHS*ist, andernfalls "false".

### <a name="remarks"></a>Bemerkungen

Dieser Operator verhält sich mit der Adresse des `CSid` Objekts oder `SID` der Struktur und wird implementiert, um die Kompatibilität mit C++-Standard Bibliotheks Auflistungs Klassen zu gewährleisten.

## <a name="operator-"></a><a name="operator_lt__eq"></a>Operator <=

Testet, ob `CSid` das Objekt `SID` oder die Struktur auf der linken Seite des Operators kleiner als oder gleich dem Objekt `CSid` oder `SID` der Struktur auf der rechten Seite ist (für die Kompatibilität der C++-Standard Bibliothek).

```cpp
bool operator<(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>Parameter

*LHS*<br/>
Das erste `CSid` zu vergleichende `SID` Objekt oder die erste zu vergleichende Struktur.

*rhs*<br/>
Das zweite `CSid` zu vergleichende `SID` Objekt oder die zweite zu vergleichende Struktur.

### <a name="return-value"></a>Rückgabewert

Gibt "true" zurück, wenn die Adresse der *LHS* kleiner oder gleich der Adresse des *RHS*ist, andernfalls "false".

### <a name="remarks"></a>Bemerkungen

Dieser Operator verhält sich mit der Adresse des `CSid` Objekts oder `SID` der Struktur und wird implementiert, um die Kompatibilität mit C++-Standard Bibliotheks Auflistungs Klassen zu gewährleisten.

## <a name="operator-"></a><a name="operator_gt__eq"></a>Operator >=

Testet, ob `CSid` das Objekt `SID` oder die Struktur Links vom Operator größer als oder gleich dem Objekt oder `CSid` `SID` der Struktur auf der rechten Seite ist (für die Kompatibilität der C++-Standard Bibliothek).

```cpp
bool operator<(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>Parameter

*LHS*<br/>
Das erste `CSid` zu vergleichende `SID` Objekt oder die erste zu vergleichende Struktur.

*rhs*<br/>
Das zweite `CSid` zu vergleichende `SID` Objekt oder die zweite zu vergleichende Struktur.

### <a name="return-value"></a>Rückgabewert

Gibt "true" zurück, wenn die Adresse der *LHS* größer oder gleich der Adresse des *RHS*ist, andernfalls "false".

### <a name="remarks"></a>Bemerkungen

Dieser Operator verhält sich mit der Adresse des `CSid` Objekts oder `SID` der Struktur und wird implementiert, um die Kompatibilität mit C++-Standard Bibliotheks Auflistungs Klassen zu gewährleisten.
