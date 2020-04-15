---
title: ATL-Operatoren
ms.date: 11/04/2016
helpviewer_keywords:
- operators [ATL]
ms.assetid: 58ccd252-2869-45ee-8a5c-3ca40ee7f8a2
ms.openlocfilehash: 8c15daa1d2b12c58323ef5ef75559a2ab911ad93
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319236"
---
# <a name="atl-operators"></a>ATL-Operatoren

Dieser Abschnitt enthält die Referenzthemen für die globalen ATL-Operatoren.

|Operator|BESCHREIBUNG|
|--------------|-----------------|
|[Operator ==](#operator_eq_eq)|Vergleicht `CSid` zwei `SID` Objekte oder Strukturen für die Gleichheit.|
|[Operator !=](#operator_neq)|Vergleicht `CSid` zwei `SID` Objekte oder Strukturen für Ungleichheit.|
|[Betreiber <](#operator_lt)|Testet, `CSid` ob `SID` das Objekt oder die Struktur auf `CSid` der `SID` linken Seite des Operators kleiner als das Objekt oder die Struktur auf der rechten Seite ist (für C++-Standardbibliothekskompatibilität).|
|[Betreiber >](#operator_gt)|Testet, `CSid` ob `SID` das Objekt oder die Struktur auf `CSid` der `SID` linken Seite des Operators größer ist als das Objekt oder die Struktur auf der rechten Seite (für C++-Standardbibliothekskompatibilität).|
|[Operator <=](#operator_lt__eq)|Testet, `CSid` ob `SID` das Objekt oder die Struktur auf der linken `CSid` Seite `SID` des Operators kleiner oder gleich dem Objekt oder der Struktur auf der rechten Seite ist (für C++-Standardbibliothekskompatibilität).|
|[Operator >=](#operator_gt__eq)|Testet, `CSid` ob `SID` das Objekt oder die Struktur auf der linken `CSid` Seite `SID` des Operators größer oder gleich dem Objekt oder der Struktur auf der rechten Seite ist (für C++-Standardbibliothekskompatibilität).|

## <a name="requirements"></a>Anforderungen

**Header:** atlsecurity.h.

## <a name="operator-"></a><a name="operator_eq_eq"></a>Operator ==

Vergleicht `CSid` Objekte `SID` oder (Sicherheitskennungs-)Strukturen auf Gleichheit.

```
bool operator==(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>Parameter

*Lhs*<br/>
Das `CSid` erste `SID` zu vergleichende Objekt oder die erste Struktur.

*rhs*<br/>
Das `CSid` zweite `SID` zu vergleichende Objekt oder die zweite Struktur.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE zurück, wenn die Objekte gleich sind, FALSE, wenn sie nicht gleich sind.

## <a name="operator-"></a><a name="operator_neq"></a>Operator !=

Vergleicht `CSid` Objekte `SID` oder (Sicherheitskennungs-)Strukturen mit Ungleichheit.

```
bool operator==(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>Parameter

*Lhs*<br/>
Das `CSid` erste `SID` zu vergleichende Objekt oder die erste Struktur.

*rhs*<br/>
Das `CSid` zweite `SID` zu vergleichende Objekt oder die zweite Struktur.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE zurück, wenn die Objekte nicht gleich sind, FALSE, wenn sie gleich sind.

## <a name="operator-"></a><a name="operator_lt"></a>Betreiber <

Testet, `CSid` ob `SID` das Objekt oder die Struktur auf `CSid` der `SID` linken Seite des Operators kleiner als das Objekt oder die Struktur auf der rechten Seite ist (für C++-Standardbibliothekskompatibilität).

```
bool operator<(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>Parameter

*Lhs*<br/>
Das `CSid` erste `SID` zu vergleichende Objekt oder die erste Struktur.

*rhs*<br/>
Das `CSid` zweite `SID` zu vergleichende Objekt oder die zweite Struktur.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE zurück, wenn die Adresse des *lhs-Objekts* kleiner als die Adresse des *rhs-Objekts* ist, andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Dieser Operator wirkt auf `CSid` die `SID` Adresse des Objekts oder der Struktur und wird implementiert, um die Kompatibilität mit C++ Standardlibrary-Auflistungsklassen bereitzustellen.

## <a name="operator-"></a><a name="operator_gt"></a>Betreiber >

Testet, `CSid` ob `SID` das Objekt oder die Struktur auf `CSid` der `SID` linken Seite des Operators größer ist als das Objekt oder die Struktur auf der rechten Seite (für C++-Standardbibliothekskompatibilität).

```
bool operator<(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>Parameter

*Lhs*<br/>
Das `CSid` erste `SID` zu vergleichende Objekt oder die erste Struktur.

*rhs*<br/>
Das `CSid` zweite `SID` zu vergleichende Objekt oder die zweite Struktur.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE zurück, wenn die Adresse des *lhs* größer als die Adresse des *rhs*ist, ANDERNFALLS FALSE.

### <a name="remarks"></a>Bemerkungen

Dieser Operator wirkt auf `CSid` die `SID` Adresse des Objekts oder der Struktur und wird implementiert, um die Kompatibilität mit C++ Standardlibrary-Auflistungsklassen bereitzustellen.

## <a name="operator-"></a><a name="operator_lt__eq"></a>Operator <=

Testet, `CSid` ob `SID` das Objekt oder die Struktur auf der linken `CSid` Seite `SID` des Operators kleiner oder gleich dem Objekt oder der Struktur auf der rechten Seite ist (für C++-Standardbibliothekskompatibilität).

```
bool operator<(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>Parameter

*Lhs*<br/>
Das `CSid` erste `SID` zu vergleichende Objekt oder die erste Struktur.

*rhs*<br/>
Das `CSid` zweite `SID` zu vergleichende Objekt oder die zweite Struktur.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE zurück, wenn die Adresse des *lhs* kleiner oder gleich der Adresse des *rhs*ist, andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Dieser Operator wirkt auf `CSid` die `SID` Adresse des Objekts oder der Struktur und wird implementiert, um die Kompatibilität mit C++ Standardlibrary-Auflistungsklassen bereitzustellen.

## <a name="operator-"></a><a name="operator_gt__eq"></a>Operator >=

Testet, `CSid` ob `SID` das Objekt oder die Struktur auf der linken `CSid` Seite `SID` des Operators größer oder gleich dem Objekt oder der Struktur auf der rechten Seite ist (für C++-Standardbibliothekskompatibilität).

```
bool operator<(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>Parameter

*Lhs*<br/>
Das `CSid` erste `SID` zu vergleichende Objekt oder die erste Struktur.

*rhs*<br/>
Das `CSid` zweite `SID` zu vergleichende Objekt oder die zweite Struktur.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE zurück, wenn die Adresse der *lhs* größer oder gleich der Adresse des *rhs*ist, andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Dieser Operator wirkt auf `CSid` die `SID` Adresse des Objekts oder der Struktur und wird implementiert, um die Kompatibilität mit C++ Standardlibrary-Auflistungsklassen bereitzustellen.
