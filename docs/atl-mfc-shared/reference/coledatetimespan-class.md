---
title: COleDateTimeSpan-Klasse
ms.date: 03/27/2019
f1_keywords:
- COleDateTimeSpan
- ATLCOMTIME/ATL::COleDateTimeSpan
- ATLCOMTIME/ATL::COleDateTimeSpan::COleDateTimeSpan
- ATLCOMTIME/ATL::COleDateTimeSpan::Format
- ATLCOMTIME/ATL::COleDateTimeSpan::GetDays
- ATLCOMTIME/ATL::COleDateTimeSpan::GetHours
- ATLCOMTIME/ATL::COleDateTimeSpan::GetMinutes
- ATLCOMTIME/ATL::COleDateTimeSpan::GetSeconds
- ATLCOMTIME/ATL::COleDateTimeSpan::GetStatus
- ATLCOMTIME/ATL::COleDateTimeSpan::GetTotalDays
- ATLCOMTIME/ATL::COleDateTimeSpan::GetTotalHours
- ATLCOMTIME/ATL::COleDateTimeSpan::GetTotalMinutes
- ATLCOMTIME/ATL::COleDateTimeSpan::GetTotalSeconds
- ATLCOMTIME/ATL::COleDateTimeSpan::SetDateTimeSpan
- ATLCOMTIME/ATL::COleDateTimeSpan::SetStatus
- ATLCOMTIME/ATL::COleDateTimeSpan::m_span
- ATLCOMTIME/ATL::COleDateTimeSpan::m_status
helpviewer_keywords:
- timespan
- time span
- shared classes, COleDateTimeSpan
- Date data type, MFC encapsulation of
- COleDateTimeSpan class
ms.assetid: 7441526d-a30a-4019-8fb3-3fee6f897cbe
ms.openlocfilehash: 746cfdce3265dff7e5b20a5135aa026aca9facdf
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88832099"
---
# <a name="coledatetimespan-class"></a>COleDateTimeSpan-Klasse

Stellt eine relative Zeitspanne, eine Zeitspanne dar.

## <a name="syntax"></a>Syntax

```
class COleDateTimeSpan
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|name|Beschreibung|
|----------|-----------------|
|[COleDateTimeSpan:: COleDateTimeSpan](#coledatetimespan)|Erstellt ein `COleDateTimeSpan`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|name|Beschreibung|
|----------|-----------------|
|[COleDateTimeSpan:: Format](#format)|Generiert eine formatierte Zeichen folgen Darstellung eines- `COleDateTimeSpan` Objekts.|
|[COleDateTimeSpan:: GetDays](#getdays)|Gibt den tagteil der Spanne zurück, die dieses `COleDateTimeSpan` Objekt darstellt.|
|[COleDateTimeSpan:: getHours](#gethours)|Gibt den Stunden Teil der Spanne zurück, die dieses `COleDateTimeSpan` Objekt darstellt.|
|[COleDateTimeSpan:: getMinutes](#getminutes)|Gibt den Minuten Teil der Spanne zurück, die dieses `COleDateTimeSpan` Objekt darstellt.|
|[COleDateTimeSpan:: getSeconds](#getseconds)|Gibt den zweiten Teil der Spanne zurück, die dieses `COleDateTimeSpan` Objekt darstellt.|
|[COleDateTimeSpan:: GetStatus](#getstatus)|Ruft den Status (Gültigkeit) dieses- `COleDateTimeSpan` Objekts ab.|
|[COleDateTimeSpan:: GetTotalDays](#gettotaldays)|Gibt die Anzahl von Tagen zurück, die dieses- `COleDateTimeSpan` Objekt darstellt.|
|[COleDateTimeSpan:: GetTotalHours](#gettotalhours)|Gibt die Anzahl der Stunden zurück, die dieses `COleDateTimeSpan` Objekt darstellt.|
|[COleDateTimeSpan:: GetTotalMinutes](#gettotalminutes)|Gibt die Anzahl der Minuten zurück, die dieses- `COleDateTimeSpan` Objekt darstellt.|
|[COleDateTimeSpan:: GetTotalSeconds](#gettotalseconds)|Gibt die Anzahl der Sekunden zurück, die dieses- `COleDateTimeSpan` Objekt darstellt.|
|[COleDateTimeSpan:: setdatetimespan](#setdatetimespan)|Legt den Wert dieses- `COleDateTimeSpan` Objekts fest.|
|[COleDateTimeSpan:: SetStatus](#setstatus)|Legt den Status (Gültigkeit) dieses `COleDateTimeSpan` Objekts fest.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|Beschreibung|
|-|-|
|[Operator +,-](#operator_add_-)|Fügen Sie das Zeichen für Werte hinzu, subtrahieren und ändern `COleDateTimeSpan` .|
|[Operator + =,-=](#operator_add_eq_-_eq)|Fügen Sie einen Wert hinzu, und subtrahieren Sie `COleDateTimeSpan` diesen `COleDateTimeSpan` Wert.|
|[Operator =](#operator_eq)|Kopiert einen `COleDateTimeSpan` Wert.|
|[Operator = =, <, <=](#coledatetimespan_relational_operators)|Vergleicht zwei `COleDateTimeSpan` Werte.|
|[Operator Double](#operator_double)|Konvertiert diesen `COleDateTimeSpan` Wert in einen **`double`** .|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|Beschreibung|
|----------|-----------------|
|[COleDateTimeSpan:: m_span](#m_span)|Enthält den zugrunde liegenden **`double`** für dieses `COleDateTimeSpan` Objekt.|
|[COleDateTimeSpan:: m_status](#m_status)|Enthält den Status dieses `COleDateTimeSpan` Objekts.|

## <a name="remarks"></a>Bemerkungen

`COleDateTimeSpan` weist keine Basisklasse auf.

Ein `COleDateTimeSpan` behält die Zeit in Tagen bei.

`COleDateTimeSpan` wird mit der Begleit Klasse [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)verwendet. `COleDateTime` kapselt den `DATE` Datentyp der OLE-Automatisierung. `COleDateTime` stellt absolute Zeit Werte dar. Alle `COleDateTime` Berechnungen beinhalten `COleDateTimeSpan` Werte. Die Beziehung zwischen diesen Klassen entspricht der Beziehung zwischen [ctime](../../atl-mfc-shared/reference/ctime-class.md) und [CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md).

Weitere Informationen zu den `COleDateTime` -und- `COleDateTimeSpan` Klassen finden Sie im Artikel [Datum und Uhrzeit: Automatisierungsunterstützung](../../atl-mfc-shared/date-and-time-automation-support.md).

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** ATLComTime. h

## <a name="coledatetimespan-relational-operators"></a><a name="coledatetimespan_relational_operators"></a> Relationale COleDateTimeSpan-Operatoren

Vergleichs Operatoren.

```
bool operator==(const COleDateTimeSpan& dateSpan) const throw();
bool operator!=(const COleDateTimeSpan& dateSpan) const throw();
bool operator<(const COleDateTimeSpan& dateSpan) const throw();
bool operator>(const COleDateTimeSpan& dateSpan) const throw();
bool operator<=(const COleDateTimeSpan& dateSpan) const throw();
bool operator>=(const COleDateTimeSpan& dateSpan) const throw();
```

### <a name="parameters"></a>Parameter

*datespan*<br/>
Der zu vergleichende `COleDateTimeSpan`.

### <a name="return-value"></a>Rückgabewert

Diese Operatoren vergleichen zwei Datums-/uhrzeitspannen-Werte und geben true zurück, wenn die Bedingung erfüllt ist. andernfalls false.

### <a name="remarks"></a>Bemerkungen

> [!NOTE]
> Ein ATLASSERT-Vorgang tritt auf, wenn einer der beiden Operanden ungültig ist.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#25](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_1.cpp)]

[!code-cpp[NVC_ATLMFC_Utilities#26](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_2.cpp)]

## <a name="coledatetimespancoledatetimespan"></a><a name="coledatetimespan"></a> COleDateTimeSpan:: COleDateTimeSpan

Erstellt ein `COleDateTimeSpan`-Objekt.

```
COleDateTimeSpan() throw();
COleDateTimeSpan(double dblSpanSrc) throw();
COleDateTimeSpan(LONG lDays, int nHours, int nMins, int nSecs) throw();
```

### <a name="parameters"></a>Parameter

*dblspansrc*<br/>
Die Anzahl der Tage, die in das neue- `COleDateTimeSpan` Objekt kopiert werden.

*ldays*, *nhours*, *nmins*, *nSekunden*<br/>
Geben Sie die in das neue-Objekt zu kopierenden Tages-und Uhrzeitwerte an `COleDateTimeSpan` .

### <a name="remarks"></a>Bemerkungen

Alle diese Konstruktoren erstellen neue `COleDateTimeSpan` Objekte, die mit dem angegebenen Wert initialisiert werden. Es folgt eine kurze Beschreibung der einzelnen Konstruktoren:

- **COleDateTimeSpan ()** Erstellt ein- `COleDateTimeSpan` Objekt, das mit 0 initialisiert wird.

- **COleDateTimeSpan (** `dblSpanSrc` **)** erstellt ein- `COleDateTimeSpan` Objekt aus einem Gleit Komma Wert.

- **COleDateTimeSpan (** `lDays` **,** `nHours` **,** `nMins` **,** `nSecs` **)** erstellt ein- `COleDateTimeSpan` Objekt, das mit den angegebenen numerischen Werten initialisiert wird.

Der Status des neuen `COleDateTimeSpan` Objekts ist auf "gültig" festgelegt.

Weitere Informationen zu den Begrenzungen für `COleDateTimeSpan` Werte finden Sie im Artikel " [Datum und Uhrzeit: Automation-Support](../../atl-mfc-shared/date-and-time-automation-support.md)".

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#14](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_3.cpp)]

## <a name="coledatetimespanformat"></a><a name="format"></a> COleDateTimeSpan:: Format

Generiert eine formatierte Zeichen folgen Darstellung eines- `COleDateTimeSpan` Objekts.

```
CString Format(LPCTSTR pFormat) const;
CString Format(UINT nID) const;
```

### <a name="parameters"></a>Parameter

*pformat*<br/>
Eine Formatierungs Zeichenfolge ähnlich der `printf` Formatierungs Zeichenfolge. Formatierungscodes, denen ein Prozent `%` Zeichen () vorangestellt ist, werden durch die entsprechende `COleDateTimeSpan` Komponente ersetzt. Andere Zeichen in der Formatierungs Zeichenfolge werden unverändert in die zurückgegebene Zeichenfolge kopiert. Der Wert und die Bedeutung der Formatierungscodes für `Format` sind unten aufgeführt:

- **% H** Stunden des aktuellen Tages

- **% M** Minuten in der aktuellen Stunde

- **% S** Sekunden in der aktuellen Minute

- **%%** Prozentzeichen

Die vier oben aufgeführten Formatierungscodes sind die einzigen Codes, die das Format akzeptieren wird.

-

*nID*<br/>
Die Ressourcen-ID für die Format Steuerelement Zeichenfolge.

### <a name="return-value"></a>Rückgabewert

Ein `CString` -Wert, der den formatierten Datums-/uhrzeitspannen-Wert enthält.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Funktionen auf, um eine formatierte Darstellung des Zeitspannen Werts zu erstellen. Wenn der Status dieses `COleDateTimeSpan` Objekts NULL ist, ist der Rückgabewert eine leere Zeichenfolge. Wenn der Status ungültig ist, wird die Rückgabe Zeichenfolge durch die IDS_INVALID_DATETIMESPAN der Zeichen folgen Ressource angegeben.

Eine kurze Beschreibung der Formulare für diese Funktion folgt:

**Format (** *pformat* **)**<br/>
Dieses Formular formatiert den Wert mit der Format Zeichenfolge, die besondere Formatierungscodes enthält, denen ein Prozentzeichen (%) vorangestellt ist, wie in `printf` . Die Formatierungs Zeichenfolge wird als Parameter an die Funktion übergeben.

**Format (** *NID* **)**<br/>
Dieses Formular formatiert den Wert mit der Format Zeichenfolge, die besondere Formatierungscodes enthält, denen ein Prozentzeichen (%) vorangestellt ist, wie in `printf` . Die Formatierungs Zeichenfolge ist eine Ressource. Die ID dieser Zeichen folgen Ressource wird als-Parameter übergeben.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#15](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_4.cpp)]

## <a name="coledatetimespangetdays"></a><a name="getdays"></a> COleDateTimeSpan:: GetDays

Ruft den tagteil dieses Datums-/uhrzeitspannen-Werts ab.

```
LONG GetDays() const throw();
```

### <a name="return-value"></a>Rückgabewert

Der Tages Teil dieses Datums-/uhrzeitspannen-Werts.

### <a name="remarks"></a>Bemerkungen

Die Rückgabewerte von diesem Funktionsbereich zwischen ungefähr-3.615.000 und 3.615.000.

Informationen zu anderen Funktionen, die den Wert eines- `COleDateTimeSpan` Objekts Abfragen, finden Sie in den folgenden Member-Funktionen:

- [GetHours](#gethours)

- [GetMinutes](#getminutes)

- [GetSeconds](#getseconds)

- [GetTotalDays](#gettotaldays)

- [GetTotalHours](#gettotalhours)

- [GetTotalMinutes](#gettotalminutes)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#16](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_5.cpp)]

## <a name="coledatetimespangethours"></a><a name="gethours"></a> COleDateTimeSpan:: getHours

Ruft den Stunden Teil dieses Datums-/uhrzeitspannen-Werts ab.

```
LONG GetHours() const throw();
```

### <a name="return-value"></a>Rückgabewert

Der Stunden Teil dieses Datums-/uhrzeitspannen-Werts.

### <a name="remarks"></a>Bemerkungen

Die Rückgabewerte aus diesem Funktionsbereich zwischen-23 und 23.

Informationen zu anderen Funktionen, die den Wert eines- `COleDateTimeSpan` Objekts Abfragen, finden Sie in den folgenden Member-Funktionen:

- [GetDays](#getdays)

- [GetMinutes](#getminutes)

- [GetSeconds](#getseconds)

- [GetTotalDays](#gettotaldays)

- [GetTotalHours](#gettotalhours)

- [GetTotalMinutes](#gettotalminutes)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#17](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_6.cpp)]

## <a name="coledatetimespangetminutes"></a><a name="getminutes"></a> COleDateTimeSpan:: getMinutes

Ruft den Minuten Anteil dieses Datums-/uhrzeitspannen-Werts ab.

```
LONG GetMinutes() const throw();
```

### <a name="return-value"></a>Rückgabewert

Der Minuten Teil dieses Datums-/uhrzeitspannen-Werts.

### <a name="remarks"></a>Bemerkungen

Die Rückgabewerte aus diesem Funktionsbereich zwischen-59 und 59.

Informationen zu anderen Funktionen, die den Wert eines- `COleDateTimeSpan` Objekts Abfragen, finden Sie in den folgenden Member-Funktionen:

- [GetDays](#getdays)

- [GetHours](#gethours)

- [GetSeconds](#getseconds)

- [GetTotalDays](#gettotaldays)

- [GetTotalHours](#gettotalhours)

- [GetTotalMinutes](#gettotalminutes)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#18](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_7.cpp)]

## <a name="coledatetimespangetseconds"></a><a name="getseconds"></a> COleDateTimeSpan:: getSeconds

Ruft den zweiten Teil dieses Datums-/uhrzeitspannen Werts ab.

```
LONG GetSeconds() const throw();
```

### <a name="return-value"></a>Rückgabewert

Der Sekunden Teil dieses Datums-/uhrzeitspannen-Werts.

### <a name="remarks"></a>Bemerkungen

Die Rückgabewerte aus diesem Funktionsbereich zwischen-59 und 59.

Informationen zu anderen Funktionen, die den Wert eines- `COleDateTimeSpan` Objekts Abfragen, finden Sie in den folgenden Member-Funktionen:

- [GetDays](#getdays)

- [GetHours](#gethours)

- [GetMinutes](#getminutes)

- [GetTotalDays](#gettotaldays)

- [GetTotalHours](#gettotalhours)

- [GetTotalMinutes](#gettotalminutes)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#19](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_8.cpp)]

## <a name="coledatetimespangetstatus"></a><a name="getstatus"></a> COleDateTimeSpan:: GetStatus

Ruft den Status (Gültigkeit) dieses- `COleDateTimeSpan` Objekts ab.

```
DateTimeSpanStatus GetStatus() const throw();
```

### <a name="return-value"></a>Rückgabewert

Der Status dieses `COleDateTimeSpan` Werts.

### <a name="remarks"></a>Bemerkungen

Der Rückgabewert wird durch den `DateTimeSpanStatus` enumerierten Typ definiert, der in der- `COleDateTimeSpan` Klasse definiert ist.

```
enum DateTimeSpanStatus{
   valid = 0,
   invalid = 1,
   null = 2,
};
```

Eine kurze Beschreibung dieser Statuswerte finden Sie in der folgenden Liste:

- `COleDateTimeSpan::valid` Gibt an, dass dieses- `COleDateTimeSpan` Objekt gültig ist.

- `COleDateTimeSpan::invalid` Gibt an, dass dieses- `COleDateTimeSpan` Objekt ungültig ist, d. h., sein Wert ist möglicherweise falsch.

- `COleDateTimeSpan::null` Gibt an, dass dieses `COleDateTimeSpan` Objekt NULL ist, d. h., es wurde kein Wert für dieses Objekt angegeben. (Dies ist "Null", wenn kein Wert vorhanden ist, und nicht der C++ NULL.)

Der Status eines- `COleDateTimeSpan` Objekts ist in den folgenden Fällen ungültig:

- , Wenn bei einem arithmetischen Zuweisungs Vorgang, nämlich oder, bei diesem-Objekt ein Überlauf oder Unterlauf aufgetreten ist `+=` `-=` .

- , Wenn diesem Objekt ein ungültiger Wert zugewiesen wurde.

- , Wenn der Status dieses Objekts mithilfe von explizit auf ungültig festgelegt wurde `SetStatus` .

Weitere Informationen zu den Vorgängen, die den Status als ungültig festlegen können, finden Sie unter [COleDateTimeSpan:: Operator +,-](../../atl-mfc-shared/reference/coledatetime-class.md#operator_add_-) und [COleDateTimeSpan:: Operator + =,-=](../../atl-mfc-shared/reference/coledatetime-class.md#operator_add_eq_-_eq).

Weitere Informationen zu den Begrenzungen für `COleDateTimeSpan` Werte finden Sie im Artikel " [Datum und Uhrzeit: Automation-Support](../../atl-mfc-shared/date-and-time-automation-support.md)".

## <a name="coledatetimespangettotaldays"></a><a name="gettotaldays"></a> COleDateTimeSpan:: GetTotalDays

Ruft diesen Datums-/uhrzeitspannen-Wert in Tagen ab.

```
double GetTotalDays() const throw();
```

### <a name="return-value"></a>Rückgabewert

Dieser Datums-/uhrzeitspannen-Wert wird in Tagen angegeben. Obwohl diese Funktion für die Rückgabe eines Double-Werts verwendet wird, wird immer ein ganzzahliger Wert zurückgegeben.

### <a name="remarks"></a>Bemerkungen

Die Rückgabewerte von diesem Funktionsbereich zwischen ungefähr 3,65 E6 und 3,65 E6.

Informationen zu anderen Funktionen, die den Wert eines- `COleDateTimeSpan` Objekts Abfragen, finden Sie in den folgenden Member-Funktionen:

- [GetDays](#getdays)

- [GetHours](#gethours)

- [GetMinutes](#getminutes)

- [GetSeconds](#getseconds)

- [GetTotalHours](#gettotalhours)

- [GetTotalMinutes](#gettotalminutes)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#20](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_9.cpp)]

## <a name="coledatetimespangettotalhours"></a><a name="gettotalhours"></a> COleDateTimeSpan:: GetTotalHours

Ruft diesen Datums-/uhrzeitspannen-Wert in Stunden ab.

```
double GetTotalHours() const throw();
```

### <a name="return-value"></a>Rückgabewert

Dieser Datums-/uhrzeitspannen-Wert wird in Stunden angegeben. Obwohl diese Funktion für die Rückgabe eines Double-Werts verwendet wird, wird immer ein ganzzahliger Wert zurückgegeben.

### <a name="remarks"></a>Bemerkungen

Die Rückgabewerte aus dieser Funktion liegen zwischen ungefähr 8.77 E7 und 8.77 E7.

Informationen zu anderen Funktionen, die den Wert eines- `COleDateTimeSpan` Objekts Abfragen, finden Sie in den folgenden Member-Funktionen:

- [GetDays](#getdays)

- [GetHours](#gethours)

- [GetMinutes](#getminutes)

- [GetSeconds](#getseconds)

- [GetTotalDays](#gettotaldays)

- [GetTotalMinutes](#gettotalminutes)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie im Beispiel für [GetTotalDays](#gettotaldays).

## <a name="coledatetimespangettotalminutes"></a><a name="gettotalminutes"></a> COleDateTimeSpan:: GetTotalMinutes

Ruft diesen Datums-/uhrzeitspannen-Wert in Minuten ab.

```
double GetTotalMinutes() const throw();
```

### <a name="return-value"></a>Rückgabewert

Dieser Datums-/uhrzeitspannen-Wert wird in Minuten angegeben. Obwohl diese Funktion für die Rückgabe eines Double-Werts verwendet wird, wird immer ein ganzzahliger Wert zurückgegeben.

### <a name="remarks"></a>Bemerkungen

Die Rückgabewerte aus dieser Funktion liegen zwischen ungefähr-5,26 E9 und 5,26 E9.

Informationen zu anderen Funktionen, die den Wert eines- `COleDateTimeSpan` Objekts Abfragen, finden Sie in den folgenden Member-Funktionen:

- [GetDays](#getdays)

- [GetHours](#gethours)

- [GetMinutes](#getminutes)

- [GetSeconds](#getseconds)

- [GetTotalDays](#gettotaldays)

- [GetTotalHours](#gettotalhours)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie im Beispiel für [GetTotalDays](#gettotaldays).

## <a name="coledatetimespangettotalseconds"></a><a name="gettotalseconds"></a> COleDateTimeSpan:: GetTotalSeconds

Ruft diesen Datums-/uhrzeitspannen-Wert in Sekunden ab.

```
double GetTotalSeconds() const throw();
```

### <a name="return-value"></a>Rückgabewert

Dieser Datums-/uhrzeitspannen-Wert wird in Sekunden angegeben. Obwohl diese Funktion für die Rückgabe eines Double-Werts verwendet wird, wird immer ein ganzzahliger Wert zurückgegeben.

### <a name="remarks"></a>Bemerkungen

Die Rückgabewerte aus dieser Funktion liegen zwischen ungefähr 3,16 E11 und 3,16 e11.

Informationen zu anderen Funktionen, die den Wert eines- `COleDateTimeSpan` Objekts Abfragen, finden Sie in den folgenden Member-Funktionen:

- [GetDays](#getdays)

- [GetHours](#gethours)

- [GetMinutes](#getminutes)

- [GetSeconds](#getseconds)

- [GetTotalDays](#gettotaldays)

- [GetTotalHours](#gettotalhours)

- [GetTotalMinutes](#gettotalminutes)

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie im Beispiel für [GetTotalDays](#gettotaldays).

## <a name="coledatetimespanm_span"></a><a name="m_span"></a> COleDateTimeSpan:: m_span

Der zugrunde liegende **`double`** Wert für dieses- `COleDateTime` Objekt.

```
double m_span;
```

### <a name="remarks"></a>Bemerkungen

Dieser Wert drückt die Datums-/uhrzeitanumspanne in Tagen aus.

> [!CAUTION]
> Wenn Sie den Wert im **`double`** Datenmember ändern, ändert sich der Wert dieses `COleDateTimeSpan` Objekts. Der Status dieses Objekts wird nicht geändert `COleDateTimeSpan` .

## <a name="coledatetimespanm_status"></a><a name="m_status"></a> COleDateTimeSpan:: m_status

Der-Typ für diesen Datenmember ist der Enumerationstyp `DateTimeSpanStatus` , der in der-Klasse definiert ist `COleDateTimeSpan` .

```
DateTimeSpanStatus m_status;
```

### <a name="remarks"></a>Bemerkungen

```
enum DateTimeSpanStatus{
   valid = 0,
   invalid = 1,
   null = 2,
   };
```

Eine kurze Beschreibung dieser Statuswerte finden Sie in der folgenden Liste:

- `COleDateTimeSpan::valid` Gibt an, dass dieses- `COleDateTimeSpan` Objekt gültig ist.

- `COleDateTimeSpan::invalid` Gibt an, dass dieses- `COleDateTimeSpan` Objekt ungültig ist, d. h., sein Wert ist möglicherweise falsch.

- `COleDateTimeSpan::null` Gibt an, dass dieses `COleDateTimeSpan` Objekt NULL ist, d. h., es wurde kein Wert für dieses Objekt angegeben. (Dies ist "Null", wenn kein Wert vorhanden ist, und nicht der C++ NULL.)

Der Status eines- `COleDateTimeSpan` Objekts ist in den folgenden Fällen ungültig:

- , Wenn bei einem arithmetischen Zuweisungs Vorgang, nämlich oder, bei diesem-Objekt ein Überlauf oder Unterlauf aufgetreten ist `+=` `-=` .

- , Wenn diesem Objekt ein ungültiger Wert zugewiesen wurde.

- , Wenn der Status dieses Objekts mithilfe von [SetStatus](#setstatus)explizit auf ungültig festgelegt wurde.

Weitere Informationen zu den Vorgängen, die den Status als ungültig festlegen können, finden Sie unter [COleDateTimeSpan:: Operator +,-](../../atl-mfc-shared/reference/coledatetime-class.md#operator_add_-) und [COleDateTimeSpan:: Operator + =,-=](../../atl-mfc-shared/reference/coledatetime-class.md#operator_add_eq_-_eq).

> [!CAUTION]
> Dieser Datenmember ist für erweiterte Programmier Situationen vorgesehen. Sie sollten die Inline Member-Funktionen [GetStatus](#getstatus) und [SetStatus](#setstatus)verwenden. `SetStatus`Weitere Vorsichtsmaßnahmen bezüglich der expliziten Festlegung dieses Datenmembers finden Sie unter.

Weitere Informationen zu den Begrenzungen für `COleDateTimeSpan` Werte finden Sie im Artikel " [Datum und Uhrzeit: Automation-Support](../../atl-mfc-shared/date-and-time-automation-support.md)".

## <a name="coledatetimespanoperator-"></a><a name="operator_eq"></a> COleDateTimeSpan:: Operator =

Kopiert einen `COleDateTimeSpan` Wert.

```
COleDateTimeSpan& operator=(double dblSpanSrc) throw();
```

### <a name="remarks"></a>Bemerkungen

Dieser überladene Zuweisungs Operator kopiert den Quell Datums-/uhrzeitspannen-Wert in dieses- `COleDateTimeSpan` Objekt.

## <a name="coledatetimespanoperator---"></a><a name="operator_add_-"></a> COleDateTimeSpan:: Operator +,-

Fügen Sie das Zeichen für Werte hinzu, subtrahieren und ändern `COleDateTimeSpan` .

```
COleDateTimeSpan operator+(const COleDateTimeSpan& dateSpan) const throw();
COleDateTimeSpan operator-(const COleDateTimeSpan& dateSpan) const throw();
COleDateTimeSpan operator-() const throw();
```

### <a name="remarks"></a>Bemerkungen

Die ersten beiden Operatoren ermöglichen es Ihnen, Datums-/Zeitspannen Werte hinzuzufügen und zu subtrahieren. Mit dem dritten können Sie das Vorzeichen eines Datums-/uhrzeitspannen-Werts ändern.

Wenn einer der Operanden NULL ist, ist der Status des resultierenden `COleDateTimeSpan` Werts Null.

Wenn einer der Operanden ungültig ist und der andere nicht NULL ist, ist der Status des resultierenden `COleDateTimeSpan` Werts ungültig.

Weitere Informationen zu den gültigen, ungültigen und NULL-Status Werten finden Sie in der [m_status](#m_status) Member-Variable.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#23](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_10.cpp)]

## <a name="coledatetimespanoperator---"></a><a name="operator_add_eq_-_eq"></a> COleDateTimeSpan:: Operator + =,-=

Fügen Sie einen Wert hinzu, und subtrahieren Sie `COleDateTimeSpan` diesen `COleDateTimeSpan` Wert.

```
COleDateTimeSpan& operator+=(const COleDateTimeSpan dateSpan) throw();
COleDateTimeSpan& operator-=(const COleDateTimeSpan dateSpan) throw();
```

### <a name="remarks"></a>Bemerkungen

Mit diesen Operatoren können Sie Datums-/Zeitspannen Werte von diesem Objekt hinzufügen und subtrahieren `COleDateTimeSpan` . Wenn einer der Operanden NULL ist, ist der Status des resultierenden `COleDateTimeSpan` Werts Null.

Wenn einer der Operanden ungültig ist und der andere nicht NULL ist, ist der Status des resultierenden `COleDateTimeSpan` Werts ungültig.

Weitere Informationen zu den gültigen, ungültigen und NULL-Status Werten finden Sie in der [m_status](#m_status) Member-Variable.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#24](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_11.cpp)]

## <a name="coledatetimespanoperator-double"></a><a name="operator_double"></a> COleDateTimeSpan:: Operator Double

Konvertiert diesen `COleDateTimeSpan` Wert in einen **`double`** .

```
operator double() const throw();
```

### <a name="remarks"></a>Bemerkungen

Dieser Operator gibt den Wert dieses `COleDateTimeSpan` Werts als Gleit Komma Zahl von Tagen zurück.

## <a name="coledatetimespansetdatetimespan"></a><a name="setdatetimespan"></a> COleDateTimeSpan:: setdatetimespan

Legt den Wert dieses Datums-/uhrzeitspannen Werts fest.

```cpp
void SetDateTimeSpan(LONG lDays, int nHours, int nMins, int nSecs) throw();
```

### <a name="parameters"></a>Parameter

*ldays*, *nhours*, *nmins*, *nSekunden*<br/>
Geben Sie die Datums Spannen-und Zeitspannen Werte an, die in dieses Objekt kopiert werden sollen `COleDateTimeSpan` .

### <a name="remarks"></a>Bemerkungen

Informationen zu Funktionen, die den Wert eines- `COleDateTimeSpan` Objekts Abfragen, finden Sie in den folgenden Member-Funktionen:

- [GetDays](#getdays)

- [GetHours](#gethours)

- [GetMinutes](#getminutes)

- [GetSeconds](#getseconds)

- [GetTotalDays](#gettotaldays)

- [GetTotalHours](#gettotalhours)

- [GetTotalMinutes](#gettotalminutes)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#21](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_12.cpp)]

## <a name="coledatetimespansetstatus"></a><a name="setstatus"></a> COleDateTimeSpan:: SetStatus

Legt den Status (Gültigkeit) dieses `COleDateTimeSpan` Objekts fest.

```cpp
void SetStatus(DateTimeSpanStatus status) throw();
```

### <a name="parameters"></a>Parameter

*status*<br/>
Der neue Statuswert für dieses- `COleDateTimeSpan` Objekt.

### <a name="remarks"></a>Bemerkungen

Der *Status* Parameterwert wird durch den `DateTimeSpanStatus` enumerierten Typ definiert, der in der- `COleDateTimeSpan` Klasse definiert ist.

```
enum DateTimeSpanStatus{
   valid = 0,
   invalid = 1,
   null = 2,
   };
```

Eine kurze Beschreibung dieser Statuswerte finden Sie in der folgenden Liste:

- `COleDateTimeSpan::valid` Gibt an, dass dieses- `COleDateTimeSpan` Objekt gültig ist.

- `COleDateTimeSpan::invalid` Gibt an, dass dieses- `COleDateTimeSpan` Objekt ungültig ist, d. h., sein Wert ist möglicherweise falsch.

- `COleDateTimeSpan::null` Gibt an, dass dieses `COleDateTimeSpan` Objekt NULL ist, d. h., es wurde kein Wert für dieses Objekt angegeben. (Dies ist "Null", wenn kein Wert vorhanden ist, und nicht der C++ NULL.)

   > [!CAUTION]
   > Diese Funktion ist für erweiterte Programmier Situationen vorgesehen. Diese Funktion ändert nicht die Daten in diesem-Objekt. Es wird am häufigsten verwendet, um den Status auf **null** oder **ungültig**festzulegen. Beachten Sie, dass der Zuweisungs Operator ([Operator =](#operator_eq)) und [setdatetimespan](#setdatetimespan) den Status des Objekts basierend auf den Quell Werten festlegen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#22](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_13.cpp)]

## <a name="see-also"></a>Weitere Informationen

[COleDateTime-Klasse](../../atl-mfc-shared/reference/coledatetime-class.md)<br/>
[CTime-Klasse](../../atl-mfc-shared/reference/ctime-class.md)<br/>
[CTimeSpan-Klasse](../../atl-mfc-shared/reference/ctimespan-class.md)<br/>
[Hierarchie Diagramm](../../mfc/hierarchy-chart.md)<br/>
[Gemeinsam genutzte ATL/MFC-Klassen](../../atl-mfc-shared/atl-mfc-shared-classes.md)
