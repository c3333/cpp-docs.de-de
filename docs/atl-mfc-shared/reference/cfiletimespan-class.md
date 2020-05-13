---
title: CFileTimeSpan-Klasse
description: Die CFileTimeSpan-Klasse (Active Template Library, ATL) und Microsoft Foundation Classes (MFC) verwaltet Zeitintervalle in FILETIME-Einheiten.
ms.date: 01/10/2020
f1_keywords:
- CFileTimeSpan
- ATLTIME/ATL::CFileTimeSpan
- ATLTIME/ATL::CFileTimeSpan::CFileTimeSpan
- ATLTIME/ATL::CFileTimeSpan::GetTimeSpan
- ATLTIME/ATL::CFileTimeSpan::SetTimeSpan
helpviewer_keywords:
- shared classes, CFileTimeSpan
- CFileTimeSpan class
ms.assetid: 5856fb39-9c82-4027-8ccf-8760890491ec
ms.openlocfilehash: 87737ea1c778660a68510b484bcdfa3a4670e8ab
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317851"
---
# <a name="cfiletimespan-class"></a>CFileTimeSpan-Klasse

Diese Klasse stellt Methoden zum Verwalten relativer Datums- und Uhrzeitwerte bereit, die einer Datei zugeordnet sind.

## <a name="syntax"></a>Syntax

```cpp
class CFileTimeSpan
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CFileTimeSpan::CFileTimeSpan](#cfiletimespan)|Der Konstruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CFileTimeSpan::GetTimeSpan](#gettimespan)|Rufen Sie diese Methode auf, `CFileTimeSpan` um die Zeitspanne aus dem Objekt abzurufen.|
|[CFileTimeSpan::SetTimeSpan](#settimespan)|Rufen Sie diese Methode auf, `CFileTimeSpan` um die Zeitspanne des Objekts festzulegen.|

### <a name="public-operators"></a>Öffentliche Betreiber

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CFileTimeSpan::Operator -](#operator_-)|Führt die Subtraktion für ein Objekt aus. `CFileTimeSpan`|
|[CFileTimeSpan::operator !=](#operator_neq)|Überprüft zwei `CFileTimeSpan`-Objekte auf Ungleichheit.|
|[CFileTimeSpan::Operator +](#operator_add)|Führt eine `CFileTimeSpan` Addition für ein Objekt aus.|
|[CFileTimeSpan::Operator +=](#operator_add_eq)|Führt eine `CFileTimeSpan` Addition für ein Objekt aus, und weist das Ergebnis dem aktuellen Objekt zu.|
|[CFileTimeSpan::Operator&lt;](#operator_lt)|Vergleicht `CFileTimeSpan` zwei Objekte, um das kleinere zu bestimmen.|
|[CFileTimeSpan::Operator&lt;=](#operator_lt_eq)|Vergleicht `CFileTimeSpan` zwei Objekte, um die Gleichheit oder die kleinere zu bestimmen.|
|[CFileTimeSpan::Operator =](#operator_eq)|Der Zuweisungsoperator.|
|[CFileTimeSpan::operator -=](#operator_-_eq)|Führt die Subtraktion für ein `CFileTimeSpan` Objekt aus, und weist das Ergebnis dem aktuellen Objekt zu.|
|[CFileTimeSpan::operator ==](#operator_eq_eq)|Überprüft zwei `CFileTimeSpan`-Objekte auf Gleichheit.|
|[CFileTimeSpan::Operator&gt;](#operator_gt)|Vergleicht `CFileTimeSpan` zwei Objekte, um das größere zu bestimmen.|
|[CFileTimeSpan::Operator&gt;=](#operator_gt_eq)|Vergleicht `CFileTimeSpan` zwei Objekte, um die Gleichheit oder die größere zu bestimmen.|

## <a name="remarks"></a>Bemerkungen

Die `CFileTimeSpan` Klasse stellt Methoden bereit, um relative Zeiträume in den Einheiten zu verarbeiten, die das Dateisystem verwendet. Diese Einheiten werden häufig in Dateivorgängen verwendet, z. B. beim Erstellen, beim letzten Zugriff oder beim letzten Ändern. Die Methoden dieser Klasse werden häufig in Verbindung mit [CFileTime-Klassenobjekten](../../atl-mfc-shared/reference/cfiletime-class.md) verwendet.

## <a name="example"></a>Beispiel

Siehe Beispiel für [CFileTime::Millisecond](../../atl-mfc-shared/reference/cfiletime-class.md#millisecond).

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atltime.h

## <a name="cfiletimespancfiletimespan"></a><a name="cfiletimespan"></a>CFileTimeSpan::CFileTimeSpan

Der Konstruktor.

```cpp
CFileTimeSpan() throw();
CFileTimeSpan(const CFileTimeSpan& span) throw();
CFileTimeSpan(LONGLONG nSpan) throw();
```

### <a name="parameters"></a>Parameter

*Span*\
Ein vorhandenes `CFileTimeSpan`-Objekt.

*nSpan*\
Ein Zeitraum in FILETIME-Einheiten.

### <a name="remarks"></a>Bemerkungen

Das `CFileTimeSpan` Objekt kann mit `CFileTimeSpan` einem vorhandenen Objekt erstellt oder als 64-Bit-Wert in 100-Nanosekunden-FILETIME-Einheiten ausgedrückt werden. Weitere Informationen finden Sie unter [CFileTime](cfiletime-class.md). Der Standardkonstruktor legt die Zeitspanne auf 0 fest.

## <a name="cfiletimespangettimespan"></a><a name="gettimespan"></a>CFileTimeSpan::GetTimeSpan

Rufen Sie diese Methode auf, `CFileTimeSpan` um die Zeitspanne aus dem Objekt abzurufen.

```cpp
LONGLONG GetTimeSpan() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt die Zeitspanne in 100-Nanosekunden-FILETIME-Einheiten zurück. Weitere Informationen finden Sie unter [CFileTime](cfiletime-class.md).

## <a name="cfiletimespanoperator--"></a><a name="operator_-"></a>CFileTimeSpan::Operator -

Führt die Subtraktion für ein Objekt aus. `CFileTimeSpan`

```cpp
CFileTimeSpan operator-(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parameter

*Span*\
Ein `CFileTimeSpan` -Objekt.

### <a name="return-value"></a>Rückgabewert

Gibt `CFileTimeSpan` ein Objekt zurück, das das Ergebnis der Differenz zwischen zwei Zeitspannen darstellt.

## <a name="cfiletimespanoperator-"></a><a name="operator_neq"></a>CFileTimeSpan::operator !=

Überprüft zwei `CFileTimeSpan`-Objekte auf Ungleichheit.

```cpp
bool operator!=(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parameter

*Span*\
Das zu vergleichende `CFileTimeSpan`-Objekt.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE zurück, wenn das verglichene `CFileTimeSpan` Element nicht mit dem Objekt gleich ist. andernfalls FALSE.

## <a name="cfiletimespanoperator-"></a><a name="operator_add"></a>CFileTimeSpan::Operator +

Führt eine `CFileTimeSpan` Addition für ein Objekt aus.

```cpp
CFileTimeSpan operator+(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parameter

*Span*\
Ein `CFileTimeSpan` -Objekt.

### <a name="return-value"></a>Rückgabewert

Gibt `CFileTimeSpan` ein Objekt zurück, das die Summe der beiden Zeitspannen enthält.

## <a name="cfiletimespanoperator-"></a><a name="operator_add_eq"></a>CFileTimeSpan::Operator +=

Führt eine `CFileTimeSpan` Addition für ein Objekt aus und weist das Ergebnis dem aktuellen Objekt zu.

```cpp
CFileTimeSpan& operator+=(CFileTimeSpan span) throw();
```

### <a name="parameters"></a>Parameter

*Span*\
Ein `CFileTimeSpan` -Objekt.

### <a name="return-value"></a>Rückgabewert

Gibt das `CFileTimeSpan` aktualisierte Objekt zurück, das die Summe der beiden Zeitspannen enthält.

## <a name="cfiletimespanoperator-lt"></a><a name="operator_lt"></a>CFileTimeSpan::Operator&lt;

Vergleicht `CFileTimeSpan` zwei Objekte, um das kleinere zu bestimmen.

```cpp
bool operator<(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parameter

*Span*\
Das zu vergleichende `CFileTimeSpan`-Objekt.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE zurück, wenn das erste Objekt kleiner ist (d. h. einen kürzeren Zeitraum darstellt) als das zweite, andernfalls FALSE.

## <a name="cfiletimespanoperator-lt"></a><a name="operator_lt_eq"></a>CFileTimeSpan::Operator&lt;=

Vergleicht `CFileTimeSpan` zwei Objekte, um die Gleichheit oder die kleinere zu bestimmen.

```cpp
bool operator<=(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parameter

*Span*\
Das zu vergleichende `CFileTimeSpan`-Objekt.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE zurück, wenn das erste Objekt kleiner als (d. h. einen kürzeren Zeitraum darstellt) oder gleich dem zweiten, andernfalls FALSE ist.

## <a name="cfiletimespanoperator-"></a><a name="operator_eq"></a>CFileTimeSpan::Operator =

Der Zuweisungsoperator.

```cpp
CFileTimeSpan& operator=(const CFileTimeSpan& span) throw();
```

### <a name="parameters"></a>Parameter

*Span*\
Ein `CFileTimeSpan` -Objekt.

### <a name="return-value"></a>Rückgabewert

Gibt das `CFileTimeSpan` aktualisierte Objekt zurück.

## <a name="cfiletimespanoperator--"></a><a name="operator_-_eq"></a>CFileTimeSpan::operator -=

Führt die Subtraktion für ein `CFileTimeSpan` Objekt aus und weist das Ergebnis dem aktuellen Objekt zu.

```cpp
CFileTimeSpan& operator-=(CFileTimeSpan span) throw();
```

### <a name="parameters"></a>Parameter

*Span*\
Ein `CFileTimeSpan` -Objekt.

### <a name="return-value"></a>Rückgabewert

Gibt das `CFileTimeSpan` aktualisierte Objekt zurück.

## <a name="cfiletimespanoperator-"></a><a name="operator_eq_eq"></a>CFileTimeSpan::operator ==

Überprüft zwei `CFileTimeSpan`-Objekte auf Gleichheit.

```cpp
bool operator==(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parameter

*Span*\
Das zu vergleichende `CFileTimeSpan`-Objekt.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE zurück, wenn die Objekte gleich sind, andernfalls FALSE.

## <a name="cfiletimespanoperator-gt"></a><a name="operator_gt"></a>CFileTimeSpan::Operator&gt;

Vergleicht `CFileTimeSpan` zwei Objekte, um das größere zu bestimmen.

```cpp
bool operator>(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parameter

*Span*\
Das zu vergleichende `CFileTimeSpan`-Objekt.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE zurück, wenn das erste Objekt größer als (d. h. einen längeren Zeitraum darstellt) als das zweite, andernfalls FALSE ist.

## <a name="cfiletimespanoperator-gt"></a><a name="operator_gt_eq"></a>CFileTimeSpan::Operator&gt;=

Vergleicht `CFileTimeSpan` zwei Objekte, um die Gleichheit oder die größere zu bestimmen.

```cpp
bool operator>=(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parameter

*Span*\
Das zu vergleichende `CFileTimeSpan`-Objekt.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE zurück, wenn das erste Objekt größer als (d. h. einen längeren Zeitraum darstellt) oder gleich dem zweiten, andernfalls FALSE ist.

## <a name="cfiletimespansettimespan"></a><a name="settimespan"></a>CFileTimeSpan::SetTimeSpan

Rufen Sie diese Methode auf, `CFileTimeSpan` um die Zeitspanne des Objekts festzulegen.

```cpp
void SetTimeSpan(LONGLONG nSpan) throw();
```

### <a name="parameters"></a>Parameter

*nSpan*\
Der neue Wert für den Zeitraum in 100-Nanosekunden-FILETIME-Einheiten. Weitere Informationen finden Sie unter [CFileTime](cfiletime-class.md).

## <a name="see-also"></a>Siehe auch

[Filetime](/windows/win32/api/minwinbase/ns-minwinbase-filetime)\
[CFileTime-Klasse](cfiletime-class.md)\
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)\
[FREIGEGEBENe ATL/MFC-Klassen](../../atl-mfc-shared/atl-mfc-shared-classes.md)
