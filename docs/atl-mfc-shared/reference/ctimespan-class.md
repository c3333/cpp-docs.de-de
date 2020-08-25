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
ms.openlocfilehash: 0c13aa0d8f6c46db3b018283ab2a408a3f9531e1
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88832021"
---
# <a name="ctimespan-class"></a>CTimeSpan-Klasse

Ein Zeitraum, der intern als die Anzahl der Sekunden in der Zeitspanne gespeichert wird.

## <a name="syntax"></a>Syntax

```
class CTimeSpan
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|name|Beschreibung|
|----------|-----------------|
|[CTimeSpan:: CTimeSpan](#ctimespan)|Erstellt- `CTimeSpan` Objekte auf verschiedene Weise.|

### <a name="public-methods"></a>Öffentliche Methoden

|name|Beschreibung|
|----------|-----------------|
|[CTimeSpan:: Format](#format)|Konvertiert einen `CTimeSpan` in eine formatierte Zeichenfolge.|
|[CTimeSpan:: GetDays](#getdays)|Gibt einen-Wert zurück, der die Anzahl der kompletten Tage in diesem darstellt `CTimeSpan` .|
|[CTimeSpan:: getHours](#gethours)|Gibt einen Wert zurück, der die Anzahl der Stunden im aktuellen Tag (-23 bis 23) darstellt.|
|[CTimeSpan:: getMinutes](#getminutes)|Gibt einen Wert zurück, der die Anzahl der Minuten in der aktuellen Stunde (-59 bis 59) darstellt.|
|[CTimeSpan:: getSeconds](#getseconds)|Gibt einen Wert zurück, der die Anzahl der Sekunden in der aktuellen Minute (-59 bis 59) darstellt.|
|[CTimeSpan:: GetTimeSpan](#gettimespan)|Gibt den Wert des- `CTimeSpan` Objekts zurück.|
|[CTimeSpan:: GetTotalHours](#gettotalhours)|Gibt einen-Wert zurück, der die Gesamtzahl der vollständigen Stunden in diesem darstellt `CTimeSpan` .|
|[CTimeSpan:: GetTotalMinutes](#gettotalminutes)|Gibt einen-Wert zurück, der die Gesamtzahl der vollständigen Minuten in diesem darstellt `CTimeSpan` .|
|[CTimeSpan:: GetTotalSeconds](#gettotalseconds)|Gibt einen-Wert zurück, der die Gesamtzahl der vollständigen Sekunden in diesem darstellt `CTimeSpan` .|
|[CTimeSpan:: Serialize64](#serialize64)|Serialisiert Daten in ein oder aus einem Archiv.|

### <a name="operators"></a>Operatoren

|Name|Beschreibung|
|-|-|
|[Operator +-](#operator_add_-)|Fügt Objekte hinzu und subtrahiert `CTimeSpan` .|
|[Operator + =-=](#operator_add_eq_-_eq)|Fügt ein- `CTimeSpan` Objekt zu und von diesem hinzu und subtrahiert dieses `CTimeSpan` .|
|[Operator = = < usw.](#ctimespan_comparison_operators)|Vergleicht zwei relative Zeitwerte.|

## <a name="remarks"></a>Bemerkungen

`CTimeSpan` weist keine Basisklasse auf.

`CTimeSpan` Funktionen konvertieren Sekunden in verschiedene Kombinationen von Tagen, Stunden, Minuten und Sekunden.

Das- `CTimeSpan` Objekt wird in einer **__time64_t** -Struktur mit 8 Bytes gespeichert.

Eine Begleit Klasse, [ctime](../../atl-mfc-shared/reference/ctime-class.md), stellt eine absolute Zeit dar.

Die `CTime` -Klasse und die- `CTimeSpan` Klasse sind nicht für die Ableitung konzipiert. Da keine virtuellen Funktionen vorhanden sind, beträgt die Größe der beiden `CTime` -und- `CTimeSpan` Objekte genau 8 Bytes. Die meisten Element Funktionen sind Inline.

Weitere Informationen zur Verwendung von `CTimeSpan` finden Sie in den Artikeln " [Datum und Uhrzeit](../../atl-mfc-shared/date-and-time.md)" und " [Zeitverwaltung](../../c-runtime-library/time-management.md) " in der *Lauf Zeit Bibliotheks Referenz*.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atltime. h

## <a name="ctimespan-comparison-operators"></a><a name="ctimespan_comparison_operators"></a> CTimeSpan-Vergleichs Operatoren

Vergleichs Operatoren.

```
bool operator==(CTimeSpan span) const throw();
bool operator!=(CTimeSpan span) const throw();
bool operator<(CTimeSpan span) const throw();
bool operator>(CTimeSpan span) const throw();
bool operator<=(CTimeSpan span) const throw();
bool operator>=(CTimeSpan span) const throw();
```

### <a name="parameters"></a>Parameter

*Spanne*<br/>
Das zu vergleichende Objekt.

### <a name="return-value"></a>Rückgabewert

Diese Operatoren vergleichen zwei relative Zeitwerte. Sie geben true zurück, wenn die Bedingung true ist. andernfalls false.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#169](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_1.cpp)]

## <a name="ctimespanctimespan"></a><a name="ctimespan"></a> CTimeSpan:: CTimeSpan

Erstellt- `CTimeSpan` Objekte auf verschiedene Weise.

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

*timespansrc*<br/>
Ein- `CTimeSpan` Objekt, das bereits vorhanden ist.

*time*<br/>
Ein **__time64_t** Uhrzeitwert, der die Anzahl der Sekunden in der Zeitspanne ist.

*ldays*, *nhours*, *nmins*, *nSekunden*<br/>
Tage, Stunden, Minuten und Sekunden.

### <a name="remarks"></a>Bemerkungen

Alle diese Konstruktoren erstellen ein neues- `CTimeSpan` Objekt, das mit der angegebenen relativen Zeit initialisiert wird. Jeder Konstruktor wird im folgenden beschrieben:

- `CTimeSpan( );` Erstellt ein nicht initialisiertes `CTimeSpan` Objekt.

- `CTimeSpan( const CTimeSpan& );` Erstellt ein- `CTimeSpan` Objekt aus einem anderen- `CTimeSpan` Wert.

- `CTimeSpan( __time64_t );` Erstellt ein- `CTimeSpan` Objekt aus einem **__time64_t** -Typ.

- `CTimeSpan( LONG, int, int, int );` Erstellt ein- `CTimeSpan` Objekt aus Komponenten, wobei jede Komponente auf die folgenden Bereiche beschränkt ist:

   |Komponente|Range|
   |---------------|-----------|
   |*ldays*|0-25000 (ungefähr)|
   |*nstunden*|0-23|
   |*nmins*|0-59|
   |*nSekunden*|0-59|

Beachten Sie, dass die Debugversion des Microsoft Foundation Class-Bibliothek bestätigt, wenn eine oder mehrere der Zeit Tages Komponenten außerhalb des gültigen Bereichs liegen. Es liegt in ihrer Verantwortung, die Argumente vor dem Aufrufen von zu validieren.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#162](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_2.cpp)]

## <a name="ctimespanformat"></a><a name="format"></a> CTimeSpan:: Format

Generiert eine formatierte Zeichenfolge, die diesem entspricht `CTimeSpan` .

```
CString Format(LPCSTR pFormat) const;
CString Format(LPCTSTR pszFormat) const;
CString Format(UINT nID) const;
```

### <a name="parameters"></a>Parameter

*pformat*, *pszformat*<br/>
Eine Formatierungs Zeichenfolge ähnlich der `printf` Formatierungs Zeichenfolge. Formatierungscodes, denen ein Prozent `%` Zeichen () vorangestellt ist, werden durch die entsprechende `CTimeSpan` Komponente ersetzt. Andere Zeichen in der Formatierungs Zeichenfolge werden unverändert in die zurückgegebene Zeichenfolge kopiert. Der Wert und die Bedeutung der Formatierungscodes für `Format` sind unten aufgeführt:

- **% D** Gesamtanzahl der Tage in diesem `CTimeSpan`

- **% H** Stunden des aktuellen Tages

- **% M** Minuten in der aktuellen Stunde

- **% S** Sekunden in der aktuellen Minute

- **%%** Prozentzeichen

*nID*<br/>
Die ID der Zeichenfolge, die dieses Format identifiziert.

### <a name="return-value"></a>Rückgabewert

Ein- `CString` Objekt, das die formatierte Zeit enthält.

### <a name="remarks"></a>Bemerkungen

Die Debugversion der Bibliothek überprüft die Formatierungscodes und bestätigt, ob der Code nicht in der obigen Liste enthalten ist.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#163](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_3.cpp)]

## <a name="ctimespangetdays"></a><a name="getdays"></a> CTimeSpan:: GetDays

Gibt einen-Wert zurück, der die Anzahl der kompletten Tage in diesem darstellt `CTimeSpan` .

```
LONGLONG GetDays() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt die Anzahl der kompletten 24-Stunden-Tage in der Zeitspanne zurück. Dieser Wert kann negativ sein, wenn die Zeitspanne negativ ist.

### <a name="remarks"></a>Bemerkungen

Beachten Sie, dass die Sommerzeit `GetDays` zum Zurückgeben eines potenziell überraschenden Ergebnisses führen kann. Wenn z. b. DST gültig ist, `GetDays` meldet die Anzahl der Tage zwischen dem 1. April und dem 1. Mai als 29, nicht 30, da ein Tag im April um eine Stunde verkürzt wird und daher nicht als kompletter Tag gezählt wird.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#164](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_4.cpp)]

## <a name="ctimespangethours"></a><a name="gethours"></a> CTimeSpan:: getHours

Gibt einen Wert zurück, der die Anzahl der Stunden im aktuellen Tag (-23 bis 23) darstellt.

```
LONG GetHours() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt die Anzahl der Stunden des aktuellen Tages zurück. Der Bereich ist-23 bis 23.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#165](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_5.cpp)]

## <a name="ctimespangetminutes"></a><a name="getminutes"></a> CTimeSpan:: getMinutes

Gibt einen Wert zurück, der die Anzahl der Minuten in der aktuellen Stunde (-59 bis 59) darstellt.

```
LONG GetMinutes() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt die Anzahl der Minuten in der aktuellen Stunde zurück. Der Bereich liegt zwischen-59 und 59.

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie im Beispiel für [getHours](#gethours).

## <a name="ctimespangetseconds"></a><a name="getseconds"></a> CTimeSpan:: getSeconds

Gibt einen Wert zurück, der die Anzahl der Sekunden in der aktuellen Minute (-59 bis 59) darstellt.

```
LONG GetSeconds() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt die Anzahl der Sekunden in der aktuellen Minute zurück. Der Bereich liegt zwischen-59 und 59.

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie im Beispiel für [getHours](#gethours).

## <a name="ctimespangettimespan"></a><a name="gettimespan"></a> CTimeSpan:: GetTimeSpan

Gibt den Wert des- `CTimeSpan` Objekts zurück.

```
__ time64_t GetTimeSpan() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt den aktuellen Wert des- `CTimeSpan` Objekts zurück.

## <a name="ctimespangettotalhours"></a><a name="gettotalhours"></a> CTimeSpan:: GetTotalHours

Gibt einen-Wert zurück, der die Gesamtzahl der vollständigen Stunden in diesem darstellt `CTimeSpan` .

```
LONGLONG GetTotalHours() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt die Gesamtzahl der vollständigen Stunden in diesem zurück `CTimeSpan` .

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#166](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_6.cpp)]

## <a name="ctimespangettotalminutes"></a><a name="gettotalminutes"></a> CTimeSpan:: GetTotalMinutes

Gibt einen-Wert zurück, der die Gesamtzahl der vollständigen Minuten in diesem darstellt `CTimeSpan` .

```
LONGLONG GetTotalMinutes() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt die Gesamtzahl der vollständigen Minuten in diesem zurück `CTimeSpan` .

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie im Beispiel für [GetTotalHours](#gettotalhours).

## <a name="ctimespangettotalseconds"></a><a name="gettotalseconds"></a> CTimeSpan:: GetTotalSeconds

Gibt einen-Wert zurück, der die Gesamtzahl der vollständigen Sekunden in diesem darstellt `CTimeSpan` .

```
LONGLONG GetTotalSeconds() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt die Gesamtzahl der vollständigen Sekunden in diesem zurück `CTimeSpan` .

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie im Beispiel für [GetTotalHours](#gettotalhours).

## <a name="ctimespanoperator---"></a><a name="operator_add_-"></a> CTimeSpan:: Operator +,-

Fügt Objekte hinzu und subtrahiert `CTimeSpan` .

```
CTimeSpan operator+(CTimeSpan span) const throw();
CTimeSpan operator-(CTimeSpan span) const throw();
```

### <a name="parameters"></a>Parameter

*Spanne*<br/>
Der Wert, der dem-Objekt hinzugefügt werden soll `CTimeSpan` .

### <a name="return-value"></a>Rückgabewert

Ein- `CTimeSpan` Objekt, das das Ergebnis des Vorgangs darstellt.

### <a name="remarks"></a>Bemerkungen

Diese beiden Operatoren ermöglichen es Ihnen, Objekte zu und voneinander zu subtrahieren `CTimeSpan` .

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#167](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_7.cpp)]

## <a name="ctimespanoperator---"></a><a name="operator_add_eq_-_eq"></a> CTimeSpan:: Operator + =,-=

Fügt ein- `CTimeSpan` Objekt zu und von diesem hinzu und subtrahiert dieses `CTimeSpan` .

```
CTimeSpan& operator+=(CTimeSpan span) throw();
CTimeSpan& operator-=(CTimeSpan span) throw();
```

### <a name="parameters"></a>Parameter

*Spanne*<br/>
Der Wert, der dem-Objekt hinzugefügt werden soll `CTimeSpan` .

### <a name="return-value"></a>Rückgabewert

Das aktualisierte- `CTimeSpan` Objekt.

### <a name="remarks"></a>Bemerkungen

Diese Operatoren ermöglichen es Ihnen, ein-Objekt hinzuzufügen und `CTimeSpan` daraus zu entfernen `CTimeSpan` .

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#168](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_8.cpp)]

## <a name="ctimespanserialize64"></a><a name="serialize64"></a> CTimeSpan:: Serialize64

> [!NOTE]
> Diese Methode ist nur in MFC-Projekten verfügbar.

Serialisiert die Daten, die der Element Variablen zugeordnet sind, in ein oder aus einem Archiv.

```
CArchive& Serialize64(CArchive& ar);
```

### <a name="parameters"></a>Parameter

*Tempel*<br/>
Das `CArchive` Objekt, das Sie aktualisieren möchten.

### <a name="return-value"></a>Rückgabewert

Das aktualisierte- `CArchive` Objekt.

## <a name="see-also"></a>Weitere Informationen

[asctime, _wasctime](../../c-runtime-library/reference/asctime-wasctime.md)<br/>
[_ftime, _ftime32, _ftime64](../../c-runtime-library/reference/ftime-ftime32-ftime64.md)<br/>
[gmtime, _gmtime32, _gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)<br/>
[localtime, _localtime32, _localtime64](../../c-runtime-library/reference/localtime-localtime32-localtime64.md)<br/>
[strftime, wcsftime, _strftime_l, _wcsftime_l](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)<br/>
[time, _time32, _time64](../../c-runtime-library/reference/time-time32-time64.md)<br/>
[Hierarchie Diagramm](../../mfc/hierarchy-chart.md)<br/>
[Gemeinsam genutzte ATL/MFC-Klassen](../../atl-mfc-shared/atl-mfc-shared-classes.md)
