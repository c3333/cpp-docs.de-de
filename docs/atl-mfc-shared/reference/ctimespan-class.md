---
title: CTimeSpan-Klasse
ms.date: 10/18/2018
f1_keywords:
- CTimeSpan
- ATLTIME/ATL::CTimeSpan
- ATLTIME/ATL::CTimeSpan::CTimeSpan
- ATLTIME/ATL::CTimeSpan::Format
- ATLTIME/ATL::CTimeSpan::GetDays
- ATLTIME/ATL::CTimeSpan::GetHours
- ATLTIME/ATL::CTimeSpan::GetMinutes
- ATLTIME/ATL::CTimeSpan::GetSeconds
- ATLTIME/ATL::CTimeSpan::GetTimeSpan
- ATLTIME/ATL::CTimeSpan::GetTotalHours
- ATLTIME/ATL::CTimeSpan::GetTotalMinutes
- ATLTIME/ATL::CTimeSpan::GetTotalSeconds
- ATLTIME/ATL::CTimeSpan::Serialize64
helpviewer_keywords:
- elapsed time, CTimeSpan object
- timespan
- time span
- CTimeSpan class
- shared classes, CTimeSpan
- time, elapsed
ms.assetid: ee1e42f6-1839-477a-8435-fb26ad475140
ms.openlocfilehash: 14aa5eb52e2c631a92e40ae7053c566284e00e57
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317503"
---
# <a name="ctimespan-class"></a>CTimeSpan-Klasse

Eine Zeit, die intern als Anzahl von Sekunden im Zeitraum gespeichert wird.

## <a name="syntax"></a>Syntax

```
class CTimeSpan
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CTimeSpan::CTimeSpan](#ctimespan)|Erstellt `CTimeSpan` Objekte auf verschiedene Weise.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CTimeSpan::Format](#format)|Konvertiert eine `CTimeSpan` in eine formatierte Zeichenfolge.|
|[CTimeSpan::GetDays](#getdays)|Gibt einen Wert zurück, der die `CTimeSpan`Anzahl der vollständigen Tage in dieser darstellt.|
|[CTimeSpan::GetHours](#gethours)|Gibt einen Wert zurück, der die Anzahl der Stunden am aktuellen Tag darstellt (-23 bis 23).|
|[CTimeSpan::GetMinutes](#getminutes)|Gibt einen Wert zurück, der die Anzahl der Minuten in der aktuellen Stunde (-59 bis 59) darstellt.|
|[CTimeSpan::Sekunden abrufen](#getseconds)|Gibt einen Wert zurück, der die Anzahl der Sekunden in der aktuellen Minute (-59 bis 59) darstellt.|
|[CTimeSpan::GetTimeSpan](#gettimespan)|Gibt den Wert `CTimeSpan` des Objekts zurück.|
|[CTimeSpan::GetTotalHours](#gettotalhours)|Gibt einen Wert zurück, der die `CTimeSpan`Gesamtzahl der vollständigen Stunden in dieser darstellt.|
|[CTimeSpan::GetTotalMinuten](#gettotalminutes)|Gibt einen Wert zurück, der die `CTimeSpan`Gesamtzahl der vollständigen Minuten in dieser darstellt.|
|[CTimeSpan::GetTotalSekunden](#gettotalseconds)|Gibt einen Wert zurück, der die `CTimeSpan`Gesamtzahl der vollständigen Sekunden in dieser darstellt.|
|[CTimeSpan::Serialize64](#serialize64)|Serialisiert Daten in oder aus einem Archiv.|

### <a name="operators"></a>Operatoren

|||
|-|-|
|[Betreiber + -](#operator_add_-)|Fügt Objekte hinzu `CTimeSpan` und subtrahiert sie.|
|[Operator += -=](#operator_add_eq_-_eq)|Fügt ein `CTimeSpan` Objekt zu und von `CTimeSpan`diesem hinzu und subtrahiert es.|
|[Operator == < usw.](#ctimespan_comparison_operators)|Vergleicht zwei relative Zeitwerte.|

## <a name="remarks"></a>Bemerkungen

`CTimeSpan`hat keine Basisklasse.

`CTimeSpan`Funktionen konvertieren Sekunden in verschiedene Kombinationen von Tagen, Stunden, Minuten und Sekunden.

Das `CTimeSpan` Objekt wird in einer **__time64_t** Struktur gespeichert, die 8 Bytes beträgt.

Eine Begleitklasse, [CTime](../../atl-mfc-shared/reference/ctime-class.md), stellt eine absolute Zeit dar.

Die `CTime` `CTimeSpan` und-Klassen sind nicht für die Ableitung ausgelegt. Da es keine virtuellen Funktionen gibt, beträgt die Größe von beiden `CTime` und `CTimeSpan` Objekten genau 8 Bytes. Die meisten Memberfunktionen sind inline.

Weitere Informationen zur `CTimeSpan`Verwendung finden Sie in den Artikeln [Datum und Uhrzeit](../../atl-mfc-shared/date-and-time.md)und [Zeitverwaltung](../../c-runtime-library/time-management.md) in der *Laufzeitbibliotheksreferenz*.

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atltime.h

## <a name="ctimespan-comparison-operators"></a><a name="ctimespan_comparison_operators"></a>CTimeSpan-Vergleichsoperatoren

Vergleichsoperatoren.

```
bool operator==(CTimeSpan span) const throw();
bool operator!=(CTimeSpan span) const throw();
bool operator<(CTimeSpan span) const throw();
bool operator>(CTimeSpan span) const throw();
bool operator<=(CTimeSpan span) const throw();
bool operator>=(CTimeSpan span) const throw();
```

### <a name="parameters"></a>Parameter

*Span*<br/>
Das zu vergleichende Objekt.

### <a name="return-value"></a>Rückgabewert

Diese Operatoren vergleichen zwei relative Zeitwerte. Sie geben TRUE zurück, wenn die Bedingung wahr ist; andernfalls FALSE.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#169](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_1.cpp)]

## <a name="ctimespanctimespan"></a><a name="ctimespan"></a>CTimeSpan::CTimeSpan

Erstellt `CTimeSpan` Objekte auf verschiedene Weise.

```
CTimeSpan() throw();
CTimeSpan(__time64_t time) throw();

CTimeSpan(
    LONG lDays,
    int nHours,
    int nMins,
    int nSecs) throw();
```

### <a name="parameters"></a>Parameter

*timeSpanSrc*<br/>
Ein `CTimeSpan` Objekt, das bereits vorhanden ist.

*time*<br/>
Ein **__time64_t** Zeitwert, d. h. die Anzahl der Sekunden im Zeitraum.

*lDays*, *nHours*, *nMins*, *nSecs*<br/>
Tage, Stunden, Minuten und Sekunden.

### <a name="remarks"></a>Bemerkungen

Alle diese Konstruktoren `CTimeSpan` erstellen ein neues Objekt, das mit der angegebenen relativen Zeit initialisiert wurde. Jeder Konstruktor wird unten beschrieben:

- `CTimeSpan( );`Erstellt ein nicht `CTimeSpan` initialisiertes Objekt.

- `CTimeSpan( const CTimeSpan& );`Erstellt ein `CTimeSpan` Objekt `CTimeSpan` aus einem anderen Wert.

- `CTimeSpan( __time64_t );`Erstellt ein `CTimeSpan` Objekt aus einem **__time64_t** Typ.

- `CTimeSpan( LONG, int, int, int );`Erstellt ein `CTimeSpan` Objekt aus Komponenten, wobei jede Komponente auf die folgenden Bereiche beschränkt ist:

   |Komponente|Bereich|
   |---------------|-----------|
   |*lTage*|0-25.000 (ungefähr)|
   |*nStunden*|0-23|
   |*nMins*|0-59|
   |*nSecs*|0-59|

Beachten Sie, dass die Debugversion der Microsoft Foundation-Klassenbibliothek bestätigt, ob eine oder mehrere der Tageskomponenten anicht in Reichweite sind. Es liegt in Ihrer Verantwortung, die Argumente vor dem Aufruf zu validieren.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#162](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_2.cpp)]

## <a name="ctimespanformat"></a><a name="format"></a>CTimeSpan::Format

Generiert eine formatierte Zeichenfolge, `CTimeSpan`die dieser entspricht.

```
CString Format(LPCSTR pFormat) const;
CString Format(LPCTSTR pszFormat) const;
CString Format(UINT nID) const;
```

### <a name="parameters"></a>Parameter

*pFormat*, *pszFormat*<br/>
Eine Formatierungszeichenfolge, die der `printf` Formatierungszeichenfolge ähnelt. Formatierungscodes, denen`%`ein Prozentzeichen ( ) `CTimeSpan` vorangestellt ist, werden durch die entsprechende Komponente ersetzt. Andere Zeichen in der Formatierungszeichenfolge werden unverändert in die zurückgegebene Zeichenfolge kopiert. Der Wert und die Bedeutung `Format` der Formatierungscodes für sind unten aufgeführt:

- **%D** Gesamttage in diesem`CTimeSpan`

- **%H** Stunden am aktuellen Tag

- **%M** Minuten in der aktuellen Stunde

- **%S** Sekunden in der aktuellen Minute

- **%%** Prozentzeichen

*nID*<br/>
Die ID der Zeichenfolge, die dieses Format identifiziert.

### <a name="return-value"></a>Rückgabewert

Ein `CString` Objekt, das die formatierte Zeit enthält.

### <a name="remarks"></a>Bemerkungen

Die Debugversion der Bibliothek überprüft die Formatierungscodes und bestätigt, ob der Code nicht in der obigen Liste enthalten ist.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#163](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_3.cpp)]

## <a name="ctimespangetdays"></a><a name="getdays"></a>CTimeSpan::GetDays

Gibt einen Wert zurück, der die `CTimeSpan`Anzahl der vollständigen Tage in dieser darstellt.

```
LONGLONG GetDays() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt die Anzahl der vollständigen 24-Stunden-Tage im Zeitraum zurück. Dieser Wert kann negativ sein, wenn die Zeitspanne negativ ist.

### <a name="remarks"></a>Bemerkungen

Beachten Sie, dass `GetDays` Sommerzeit ein potenziell überraschendes Ergebnis zurückgeben kann. Wenn z. B. die `GetDays` Zeitanzeige in Kraft ist, wird die Anzahl der Tage zwischen dem 1. April und dem 1. Mai als 29 und nicht als 30 bezeichnet, da ein Tag im April um eine Stunde verkürzt wird und daher nicht als vollständiger Tag gilt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#164](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_4.cpp)]

## <a name="ctimespangethours"></a><a name="gethours"></a>CTimeSpan::GetHours

Gibt einen Wert zurück, der die Anzahl der Stunden am aktuellen Tag darstellt (-23 bis 23).

```
LONG GetHours() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt die Anzahl der Stunden im aktuellen Tag zurück. Der Bereich ist -23 bis 23.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#165](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_5.cpp)]

## <a name="ctimespangetminutes"></a><a name="getminutes"></a>CTimeSpan::GetMinutes

Gibt einen Wert zurück, der die Anzahl der Minuten in der aktuellen Stunde (-59 bis 59) darstellt.

```
LONG GetMinutes() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt die Anzahl der Minuten in der aktuellen Stunde zurück. Der Bereich ist -59 bis 59.

### <a name="example"></a>Beispiel

Siehe Beispiel für [GetHours](#gethours).

## <a name="ctimespangetseconds"></a><a name="getseconds"></a>CTimeSpan::Sekunden abrufen

Gibt einen Wert zurück, der die Anzahl der Sekunden in der aktuellen Minute (-59 bis 59) darstellt.

```
LONG GetSeconds() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt die Anzahl der Sekunden in der aktuellen Minute zurück. Der Bereich ist -59 bis 59.

### <a name="example"></a>Beispiel

Siehe Beispiel für [GetHours](#gethours).

## <a name="ctimespangettimespan"></a><a name="gettimespan"></a>CTimeSpan::GetTimeSpan

Gibt den Wert `CTimeSpan` des Objekts zurück.

```
__ time64_t GetTimeSpan() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt den aktuellen `CTimeSpan` Wert des Objekts zurück.

## <a name="ctimespangettotalhours"></a><a name="gettotalhours"></a>CTimeSpan::GetTotalHours

Gibt einen Wert zurück, der die `CTimeSpan`Gesamtzahl der vollständigen Stunden in dieser darstellt.

```
LONGLONG GetTotalHours() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt die Gesamtzahl der vollständigen `CTimeSpan`Stunden in dieser zurück.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#166](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_6.cpp)]

## <a name="ctimespangettotalminutes"></a><a name="gettotalminutes"></a>CTimeSpan::GetTotalMinuten

Gibt einen Wert zurück, der die `CTimeSpan`Gesamtzahl der vollständigen Minuten in dieser darstellt.

```
LONGLONG GetTotalMinutes() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt die Gesamtzahl der vollständigen `CTimeSpan`Minuten in dieser zurück.

### <a name="example"></a>Beispiel

Siehe Beispiel für [GetTotalHours](#gettotalhours).

## <a name="ctimespangettotalseconds"></a><a name="gettotalseconds"></a>CTimeSpan::GetTotalSekunden

Gibt einen Wert zurück, der die `CTimeSpan`Gesamtzahl der vollständigen Sekunden in dieser darstellt.

```
LONGLONG GetTotalSeconds() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt die Gesamtzahl der vollständigen `CTimeSpan`Sekunden in dieser zurück.

### <a name="example"></a>Beispiel

Siehe Beispiel für [GetTotalHours](#gettotalhours).

## <a name="ctimespanoperator---"></a><a name="operator_add_-"></a>CTimeSpan::Operator +, -

Fügt Objekte hinzu `CTimeSpan` und subtrahiert sie.

```
CTimeSpan operator+(CTimeSpan span) const throw();
CTimeSpan operator-(CTimeSpan span) const throw();
```

### <a name="parameters"></a>Parameter

*Span*<br/>
Der Wert, der `CTimeSpan` dem Objekt hinzugefügt werden soll.

### <a name="return-value"></a>Rückgabewert

Ein `CTimeSpan` Objekt, das das Ergebnis des Vorgangs darstellt.

### <a name="remarks"></a>Bemerkungen

Mit diesen beiden Operatoren können `CTimeSpan` Sie Objekte zu und von einander hinzufügen und subtrahieren.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#167](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_7.cpp)]

## <a name="ctimespanoperator---"></a><a name="operator_add_eq_-_eq"></a>CTimeSpan::operator +=, -=

Fügt ein `CTimeSpan` Objekt zu und von `CTimeSpan`diesem hinzu und subtrahiert es.

```
CTimeSpan& operator+=(CTimeSpan span) throw();
CTimeSpan& operator-=(CTimeSpan span) throw();
```

### <a name="parameters"></a>Parameter

*Span*<br/>
Der Wert, der `CTimeSpan` dem Objekt hinzugefügt werden soll.

### <a name="return-value"></a>Rückgabewert

Das `CTimeSpan` aktualisierte Objekt.

### <a name="remarks"></a>Bemerkungen

Mit diesen Operatoren können Sie `CTimeSpan` ein Objekt `CTimeSpan`zu und von diesem hinzufügen und subtrahieren.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#168](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_8.cpp)]

## <a name="ctimespanserialize64"></a><a name="serialize64"></a>CTimeSpan::Serialize64

> [!NOTE]
> Diese Methode ist nur in MFC-Projekten verfügbar.

Serialisiert die Daten, die der Membervariablen zugeordnet sind, zu oder aus einem Archiv.

```
CArchive& Serialize64(CArchive& ar);
```

### <a name="parameters"></a>Parameter

*ar*<br/>
Das `CArchive` Objekt, das Sie aktualisieren möchten.

### <a name="return-value"></a>Rückgabewert

Das `CArchive` aktualisierte Objekt.

## <a name="see-also"></a>Siehe auch

[asctime, _wasctime](../../c-runtime-library/reference/asctime-wasctime.md)<br/>
[_ftime, _ftime32, _ftime64](../../c-runtime-library/reference/ftime-ftime32-ftime64.md)<br/>
[gmtime, _gmtime32, _gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)<br/>
[localtime, _localtime32, _localtime64](../../c-runtime-library/reference/localtime-localtime32-localtime64.md)<br/>
[strftime, wcsftime, _strftime_l, _wcsftime_l](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)<br/>
[time, _time32, _time64](../../c-runtime-library/reference/time-time32-time64.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[FREIGEGEBENe ATL/MFC-Klassen](../../atl-mfc-shared/atl-mfc-shared-classes.md)
