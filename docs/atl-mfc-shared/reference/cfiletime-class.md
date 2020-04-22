---
title: CFileTime-Klasse
ms.date: 10/18/2018
f1_keywords:
- CFileTime
- ATLTIME/ATL::CFileTime
- ATLTIME/ATL::CFileTime::CFileTime
- ATLTIME/ATL::CFileTime::GetCurrentTime
- ATLTIME/ATL::CFileTime::GetTime
- ATLTIME/ATL::CFileTime::LocalToUTC
- ATLTIME/ATL::CFileTime::SetTime
- ATLTIME/ATL::CFileTime::UTCToLocal
- ATLTIME/ATL::CFileTime::Day
- ATLTIME/ATL::CFileTime::Hour
- ATLTIME/ATL::CFileTime::Millisecond
- ATLTIME/ATL::CFileTime::Minute
- ATLTIME/ATL::CFileTime::Second
- ATLTIME/ATL::CFileTime::Week
helpviewer_keywords:
- CFileTime class
- shared classes, CFileTime
ms.assetid: 1a358a65-1383-4124-b0d4-59b026e6860f
ms.openlocfilehash: fd19d941365c7772363417ce3e9225bd9b0300b2
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81748840"
---
# <a name="cfiletime-class"></a>CFileTime-Klasse

Diese Klasse stellt Methoden zum Verwalten der Datums- und Uhrzeitwerte bereit, die einer Datei zugeordnet sind.

## <a name="syntax"></a>Syntax

```
class CFileTime :  public FILETIME
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CFileTime::CFileTime](#cfiletime)|Der Konstruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CFileTime::GetCurrentTime](#getcurrenttime)|Rufen Sie diese statische `CFileTime` Funktion auf, um ein Objekt abzurufen, das das aktuelle Systemdatum und die aktuelle Systemzeit darstellt.|
|[CFileTime::GetTime](#gettime)|Rufen Sie diese Methode auf, um die Uhrzeit aus dem `CFileTime` Objekt abzurufen.|
|[CFileTime::LocalToUTC](#localtoutc)|Rufen Sie diese Methode auf, um eine lokale Dateizeit in eine Dateizeit basierend auf der koordinierten Weltzeit (UTC) zu konvertieren.|
|[CFileTime::SetTime](#settime)|Rufen Sie diese Methode auf, um `CFileTime` das vom Objekt gespeicherte Datum und die Uhrzeit festzulegen.|
|[CFileTime::UTCToLocal](#utctolocal)|Rufen Sie diese Methode auf, um die Zeit basierend auf der koordinierten Weltzeit (UTC) in die lokale Dateizeit zu konvertieren.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CFileTime::Operator -](#operator_-)|Dieser Operator wird verwendet, um `CFileTime` `CFileTimeSpan` Subtraktion für ein oder ein Objekt durchzuführen.|
|[CFileTime::operator !=](#operator_neq)|Dieser Operator vergleicht zwei `CFileTime` Objekte auf Ungleichheit.|
|[CFileTime::Operator +](#operator_add)|Dieser Operator wird verwendet, um Addition für ein `CFileTimeSpan`-Objekt auszuführen.|
|[CFileTime::Operator +=](#operator_add_eq)|Dieser Operator wird verwendet, um Addition für ein `CFileTimeSpan`-Objekt auszuführen und das Ergebnis dem aktuellen Objekt zuzuweisen.|
|[CFileTime::Operator&lt;](#operator_lt)|Dieser Operator vergleicht zwei `CFileTime`-Objekte, um das kleinere zu bestimmen.|
|[CFileTime::Operator&lt;=](#operator_lt_eq)|Dieser Operator vergleicht zwei `CFileTime`-Objekte, um zu bestimmen, ob sie gleich sind oder welches kleiner ist.|
|[CFileTime::Operator =](#operator_eq)|Der Zuweisungsoperator.|
|[CFileTime::operator -=](#operator_-_eq)|Dieser Operator wird verwendet, um `CFileTimeSpan` subtraktion für ein Objekt durchzuführen und das Ergebnis dem aktuellen Objekt zuzuweisen.|
|[CFileTime::operator ==](#operator_eq_eq)|Dieser Operator überprüft zwei `CFileTime`-Objekte auf Gleichheit.|
|[CFileTime::Operator&gt;](#operator_gt)|Dieser Operator vergleicht zwei `CFileTime`-Objekte, um das größere zu bestimmen.|
|[CFileTime::Operator&gt;=](#operator_gt_eq)|Dieser Operator vergleicht zwei `CFileTime`-Objekte, um zu bestimmen, ob sie gleich sind oder welches größer ist.|

### <a name="public-constants"></a>Öffentliche Konstanten

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CFileTime::Day](#day)|Ein statisches Datenelement, das die Anzahl der 100-Nanosekunden-Intervalle speichert, aus denen sich ein Tag zusammensetzen.|
|[CFileTime::Stunde](#hour)|Ein statisches Datenelement, das die Anzahl von 100-Nanosekunden-Intervallen speichert, die eine Stunde ausmachen.|
|[CFileTime::Millisekunde](#millisecond)|Ein statisches Datenelement, das die Anzahl von 100-Nanosekunden-Intervallen speichert, die eine Millisekunde ausmachen.|
|[CFileTime::Minute](#minute)|Ein statisches Datenelement, das die Anzahl von 100-Nanosekunden-Intervallen speichert, die eine Minute ausmachen.|
|[CFileTime::Sekunde](#second)|Ein statisches Datenelement, das die Anzahl der 100-Nanosekunden-Intervalle speichert, die eine Sekunde ausmachen.|
|[CFileTime::Woche](#week)|Ein statisches Datenelement, das die Anzahl der 100-Nanosekunden-Intervalle speichert, aus denen eine Woche besteht.|

## <a name="remarks"></a>Bemerkungen

Diese Klasse stellt Methoden zum Verwalten der Datums- und Uhrzeitwerte bereit, die mit dem Erstellen, Demontieren und Ändern von Dateien verknüpft sind. Die Methoden und Daten dieser Klasse werden `CFileTimeSpan` häufig in Verbindung mit Objekten verwendet, die sich mit relativen Zeitwerten befassen.

Der Datums- und Uhrzeitwert wird als 64-Bit-Wert gespeichert, der die Anzahl der 100-Nanosekunden-Intervalle seit dem 1. Januar 1601 darstellt. Dies ist das UTC-Format (Coordinated Universal Time).

Die folgenden statischen const-Membervariablen werden bereitgestellt, um Berechnungen zu vereinfachen:

|Membervariable|Anzahl der 100-Nanosekunden-Intervalle|
|---------------------|-----------------------------------------|
|Millisekunde|10.000|
|Sekunde|Millisekunde \* 1.000|
|Minute|Zweite \* 60|
|Hour|Minute \* 60|
|Day (Tag)|Stunde \* 24|
|Week|Tag \* 7|

**Hinweis** Nicht alle Dateisysteme können die Erstellung und die letzte Zugriffszeit aufzeichnen, und nicht alle Dateisysteme zeichnen sie auf die gleiche Weise auf. Beispielsweise hat die Erstellungszeit auf dem Windows NT FAT-Dateisystem eine Auflösung von 10 Millisekunden, die Schreibzeit eine Auflösung von 2 Sekunden und die Zugriffszeit eine Auflösung von 1 Tag (das Zugriffsdatum). Auf NTFS hat die Zugriffszeit eine Auflösung von 1 Stunde. Darüber hinaus zeichnet FAT Zeiten auf dem Datenträger in ortszeit auf, aber NTFS zeichnet Zeiten auf dem Datenträger in UTC auf. Weitere Informationen finden Sie unter [Dateizeiten](/windows/win32/SysInfo/file-times).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`FILETIME`

`CFileTime`

## <a name="requirements"></a>Requirements (Anforderungen)

**Kopfzeile:** atltime.h

## <a name="cfiletimecfiletime"></a><a name="cfiletime"></a>CFileTime::CFileTime

Der Konstruktor.

```
CFileTime() throw();
CFileTime(const FILETIME& ft) throw();
CFileTime(ULONGLONG nTime) throw();
```

### <a name="parameters"></a>Parameter

*Ft*<br/>
Eine [FILETIME-Struktur.](/windows/win32/api/minwinbase/ns-minwinbase-filetime)

*nZeit*<br/>
Das Datum und die Uhrzeit, die als 64-Bit-Wert ausgedrückt werden.

### <a name="remarks"></a>Bemerkungen

Das `CFileTime` Objekt kann mit einem vorhandenen Datum `FILETIME` und einer vorhandenen Uhrzeit aus einer Struktur erstellt oder als 64-Bit-Wert ausgedrückt werden (in lokalen oder koordinierten UTC-Zeitformaten). Der Standardkonstruktor legt die Zeit auf 0 fest.

## <a name="cfiletimeday"></a><a name="day"></a>CFileTime::Day

Ein statisches Datenelement, das die Anzahl der 100-Nanosekunden-Intervalle speichert, aus denen sich ein Tag zusammensetzen.

```
static const ULONGLONG Day = Hour* 24;
```

### <a name="example"></a>Beispiel

Siehe Beispiel für [CFileTime::Millisecond](#millisecond).

## <a name="cfiletimegetcurrenttime"></a><a name="getcurrenttime"></a>CFileTime::GetCurrentTime

Rufen Sie diese statische `CFileTime` Funktion auf, um ein Objekt abzurufen, das das aktuelle Systemdatum und die aktuelle Systemzeit darstellt.

```
static CFileTime GetCurrentTime() throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt das aktuelle Systemdatum und die aktuelle Systemzeit im UTC-Format (Coordinated Universal Time) zurück.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCFiles#41](../../atl-mfc-shared/reference/codesnippet/cpp/cfiletime-class_1.cpp)]

## <a name="cfiletimegettime"></a><a name="gettime"></a>CFileTime::GetTime

Rufen Sie diese Methode auf, um die Uhrzeit aus dem `CFileTime` Objekt abzurufen.

```
ULONGLONG GetTime() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt das Datum und die Uhrzeit als 64-Bit-Zahl zurück, die entweder im lokalen oder im UTC-Format (Coordinated Universal Time) vorliegen kann.

## <a name="cfiletimehour"></a><a name="hour"></a>CFileTime::Stunde

Ein statisches Datenelement, das die Anzahl von 100-Nanosekunden-Intervallen speichert, die eine Stunde ausmachen.

```
static const ULONGLONG Hour = Minute* 60;
```

### <a name="example"></a>Beispiel

Siehe Beispiel für [CFileTime::Millisecond](#millisecond).

## <a name="cfiletimelocaltoutc"></a><a name="localtoutc"></a>CFileTime::LocalToUTC

Rufen Sie diese Methode auf, um eine lokale Dateizeit in eine Dateizeit basierend auf der koordinierten Weltzeit (UTC) zu konvertieren.

```
CFileTime LocalToUTC() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt `CFileTime` ein Objekt zurück, das die Uhrzeit im UTC-Format enthält.

### <a name="example"></a>Beispiel

Siehe Beispiel für [CFileTime::UTCToLocal](#utctolocal).

## <a name="cfiletimemillisecond"></a><a name="millisecond"></a>CFileTime::Millisekunde

Ein statisches Datenelement, das die Anzahl von 100-Nanosekunden-Intervallen speichert, die eine Millisekunde ausmachen.

```
static const ULONGLONG Millisecond = 10000;
```

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCFiles#44](../../atl-mfc-shared/reference/codesnippet/cpp/cfiletime-class_2.cpp)]

## <a name="cfiletimeminute"></a><a name="minute"></a>CFileTime::Minute

Ein statisches Datenelement, das die Anzahl von 100-Nanosekunden-Intervallen speichert, die eine Minute ausmachen.

```
static const ULONGLONG Minute = Second* 60;
```

### <a name="example"></a>Beispiel

Siehe Beispiel für [CFileTime::Millisecond](#millisecond).

## <a name="cfiletimeoperator--"></a><a name="operator_-"></a>CFileTime::Operator -

Dieser Operator wird verwendet, um `CFileTime` `CFileTimeSpan` Subtraktion für ein oder ein Objekt durchzuführen.

```
CFileTime operator-(CFileTimeSpan span) const throw();
CFileTimeSpan operator-(CFileTime ft) const throw();
```

### <a name="parameters"></a>Parameter

*Span*<br/>
Ein `CFileTimeSpan` -Objekt.

*Ft*<br/>
Ein `CFileTime` -Objekt.

### <a name="return-value"></a>Rückgabewert

Gibt `CFileTime` ein Objekt `CFileTimeSpan` oder ein Objekt zurück, das das Ergebnis der Zeitdifferenz zwischen den beiden Objekten darstellt.

## <a name="cfiletimeoperator-"></a><a name="operator_neq"></a>CFileTime::operator !=

Dieser Operator vergleicht zwei `CFileTime` Objekte auf Ungleichheit.

```
bool operator!=(CFileTime ft) const throw();
```

### <a name="parameters"></a>Parameter

*Ft*<br/>
Das zu vergleichende `CFileTime`-Objekt.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE zurück, wenn das verglichene Element nicht gleich dem `CFileTime` Objekt ist, andernfalls FALSE.

## <a name="cfiletimeoperator-"></a><a name="operator_add"></a>CFileTime::Operator +

Dieser Operator wird verwendet, um Addition für ein `CFileTimeSpan`-Objekt auszuführen.

```
CFileTime operator+(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parameter

*Span*<br/>
Ein `CFileTimeSpan` -Objekt.

### <a name="return-value"></a>Rückgabewert

Gibt `CFileTime` ein Objekt zurück, das das Ergebnis der ursprünglichen Zeit plus eine relative Zeit darstellt.

## <a name="cfiletimeoperator-"></a><a name="operator_add_eq"></a>CFileTime::Operator +=

Dieser Operator wird verwendet, um Addition für ein `CFileTimeSpan`-Objekt auszuführen und das Ergebnis dem aktuellen Objekt zuzuweisen.

```
CFileTime& operator+=(CFileTimeSpan span) throw();
```

### <a name="parameters"></a>Parameter

*Span*<br/>
Ein `CFileTimeSpan` -Objekt.

### <a name="return-value"></a>Rückgabewert

Gibt das `CFileTime` aktualisierte Objekt zurück, das das Ergebnis der ursprünglichen Zeit plus eine relative Zeit darstellt.

## <a name="cfiletimeoperator-lt"></a><a name="operator_lt"></a>CFileTime::Operator&lt;

Dieser Operator vergleicht zwei `CFileTime`-Objekte, um das kleinere zu bestimmen.

```
bool operator<(CFileTime ft) const throw();
```

### <a name="parameters"></a>Parameter

*Ft*<br/>
Das zu vergleichende `CFileTime`-Objekt.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE zurück, wenn das erste Objekt kleiner (früher) als das zweite ist, ANDERNFALLS FALSE.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCFiles#43](../../atl-mfc-shared/reference/codesnippet/cpp/cfiletime-class_3.cpp)]

## <a name="cfiletimeoperator-lt"></a><a name="operator_lt_eq"></a>CFileTime::Operator&lt;=

Dieser Operator vergleicht zwei `CFileTime`-Objekte, um zu bestimmen, ob sie gleich sind oder welches kleiner ist.

```
bool operator<=(CFileTime ft) const throw();
```

### <a name="parameters"></a>Parameter

*Ft*<br/>
Das zu vergleichende `CFileTime`-Objekt.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE zurück, wenn das erste Objekt kleiner als (früher in der Zeit) oder gleich dem zweiten ist, andernfalls FALSE.

## <a name="cfiletimeoperator-"></a><a name="operator_eq"></a>CFileTime::Operator =

Der Zuweisungsoperator.

```
CFileTime& operator=(const FILETIME& ft) throw();
```

### <a name="parameters"></a>Parameter

*Ft*<br/>
Ein `CFileTime` Objekt, das die neue Uhrzeit und das neue Datum enthält.

### <a name="return-value"></a>Rückgabewert

Gibt das `CFileTime` aktualisierte Objekt zurück.

## <a name="cfiletimeoperator--"></a><a name="operator_-_eq"></a>CFileTime::operator -=

Dieser Operator wird verwendet, um `CFileTimeSpan` subtraktion für ein Objekt durchzuführen und das Ergebnis dem aktuellen Objekt zuzuweisen.

```
CFileTime& operator-=(CFileTimeSpan span) throw();
```

### <a name="parameters"></a>Parameter

*Span*<br/>
Ein `CFileTimeSpan` Objekt, das die relative Zeit zum Subtrahieren enthält.

### <a name="return-value"></a>Rückgabewert

Gibt das `CFileTime` aktualisierte Objekt zurück.

## <a name="cfiletimeoperator-"></a><a name="operator_eq_eq"></a>CFileTime::operator ==

Dieser Operator überprüft zwei `CFileTime`-Objekte auf Gleichheit.

```
bool operator==(CFileTime ft) const throw();
```

### <a name="parameters"></a>Parameter

*Ft*<br/>
Das zu vergleichende `CFileTime`-Objekt.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE zurück, wenn die Objekte gleich sind, andernfalls FALSE.

## <a name="cfiletimeoperator-gt"></a><a name="operator_gt"></a>CFileTime::Operator&gt;

Dieser Operator vergleicht zwei `CFileTime`-Objekte, um das größere zu bestimmen.

```
bool operator>(CFileTime ft) const throw();
```

### <a name="parameters"></a>Parameter

*Ft*<br/>
Das zu vergleichende `CFileTime`-Objekt.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE zurück, wenn das erste Objekt größer als (später) als das zweite ist, andernfalls FALSE.

## <a name="cfiletimeoperator-gt"></a><a name="operator_gt_eq"></a>CFileTime::Operator&gt;=

Dieser Operator vergleicht zwei `CFileTime`-Objekte, um zu bestimmen, ob sie gleich sind oder welches größer ist.

```
bool operator>=(CFileTime ft) const throw();
```

### <a name="parameters"></a>Parameter

*Ft*<br/>
Das zu vergleichende `CFileTime`-Objekt.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE zurück, wenn das erste Objekt größer als (später in der Zeit) oder gleich dem zweiten ist, andernfalls FALSE.

## <a name="cfiletimesecond"></a><a name="second"></a>CFileTime::Sekunde

Ein statisches Datenelement, das die Anzahl der 100-Nanosekunden-Intervalle speichert, aus denen sich ein Tag zusammensetzen.

```
static const ULONGLONG Second = Millisecond* 1000;
```

### <a name="example"></a>Beispiel

Siehe Beispiel für [CFileTime::Millisecond](#millisecond).

## <a name="cfiletimesettime"></a><a name="settime"></a>CFileTime::SetTime

Rufen Sie diese Methode auf, um `CFileTime` das vom Objekt gespeicherte Datum und die Uhrzeit festzulegen.

```cpp
void SetTime(ULONGLONG nTime) throw();
```

### <a name="parameters"></a>Parameter

*nZeit*<br/>
Der 64-Bit-Wert, der das Datum und die Uhrzeit im lokalen oder im UTC-Format (Coordinated Universal Time) darstellt.

## <a name="cfiletimeutctolocal"></a><a name="utctolocal"></a>CFileTime::UTCToLocal

Rufen Sie diese Methode auf, um die Zeit basierend auf der koordinierten Weltzeit (UTC) in die lokale Dateizeit zu konvertieren.

```
CFileTime UTCToLocal() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt `CFileTime` ein Objekt zurück, das die Uhrzeit im lokalen Dateizeitformat enthält.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCFiles#42](../../atl-mfc-shared/reference/codesnippet/cpp/cfiletime-class_4.cpp)]

## <a name="cfiletimeweek"></a><a name="week"></a>CFileTime::Woche

Ein statisches Datenelement, das die Anzahl der 100-Nanosekunden-Intervalle speichert, aus denen eine Woche besteht.

```
static const ULONGLONG Week = Day* 7;
```

### <a name="example"></a>Beispiel

Siehe Beispiel für [CFileTime::Millisecond](#millisecond).

## <a name="see-also"></a>Weitere Informationen

[FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime)<br/>
[CFileTimeSpan-Klasse](../../atl-mfc-shared/reference/cfiletimespan-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[FREIGEGEBENe ATL/MFC-Klassen](../../atl-mfc-shared/atl-mfc-shared-classes.md)
