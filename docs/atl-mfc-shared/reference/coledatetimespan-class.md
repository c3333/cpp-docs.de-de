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
ms.openlocfilehash: 7173fa0b6261ea718a02d399d944a1b5bb98b9f6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317742"
---
# <a name="coledatetimespan-class"></a>COleDateTimeSpan-Klasse

Stellt eine relative Zeit, eine Zeitspanne dar.

## <a name="syntax"></a>Syntax

```
class COleDateTimeSpan
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[ColedateTimeSpan::ColeDateTimeSpan](#coledatetimespan)|Erstellt ein `COleDateTimeSpan`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[COleDateTimeSpan::Format](#format)|Generiert eine formatierte Zeichenfolgendarstellung eines `COleDateTimeSpan` Objekts.|
|[COleDateTimeSpan::GetDays](#getdays)|Gibt den Tagesteil der `COleDateTimeSpan` Spanne zurück, die dieses Objekt darstellt.|
|[COledateTimeSpan::GetHours](#gethours)|Gibt den Stundenteil der `COleDateTimeSpan` Spanne zurück, die dieses Objekt darstellt.|
|[COleDateTimeSpan::GetMinutes](#getminutes)|Gibt den Minutenteil der `COleDateTimeSpan` Spanne zurück, die dieses Objekt darstellt.|
|[COleDateTimeSpan::GetSeconds](#getseconds)|Gibt den zweiten Teil `COleDateTimeSpan` der Spanne zurück, die dieses Objekt darstellt.|
|[COleDateTimeSpan::GetStatus](#getstatus)|Ruft den Status (Gültigkeit) dieses Objekts `COleDateTimeSpan` ab.|
|[COleDateTimeSpan::GetTotalDays](#gettotaldays)|Gibt die Anzahl `COleDateTimeSpan` der Tage zurück, die dieses Objekt darstellt.|
|[COledateTimeSpan::GetTotalHours](#gettotalhours)|Gibt die Anzahl `COleDateTimeSpan` der Stunden zurück, die dieses Objekt darstellt.|
|[COledateTimeSpan::GetTotalMinuten](#gettotalminutes)|Gibt die Anzahl `COleDateTimeSpan` der Minuten zurück, die dieses Objekt darstellt.|
|[COleDateTimeSpan::GetTotalSekunden](#gettotalseconds)|Gibt die Anzahl `COleDateTimeSpan` der Sekunden zurück, die dieses Objekt darstellt.|
|[COledateTimeSpan::SetDateTimeSpan](#setdatetimespan)|Legt den Wert `COleDateTimeSpan` dieses Objekts fest.|
|[COleDateTimeSpan::SetStatus](#setstatus)|Legt den Status (Gültigkeit) dieses `COleDateTimeSpan` Objekts fest.|

### <a name="public-operators"></a>Öffentliche Operatoren

|||
|-|-|
|[Betreiber +, -](#operator_add_-)|Hinzufügen, Subtrahieren und `COleDateTimeSpan` Ändern von Zeichen für Werte.|
|[Operator +=, -=](#operator_add_eq_-_eq)|Fügen Sie einen `COleDateTimeSpan` Wert `COleDateTimeSpan` hinzu, und subtrahieren Sie ihn von diesem Wert.|
|[Operator =](#operator_eq)|Kopiert `COleDateTimeSpan` einen Wert.|
|[Operator ==, <, <=](#coledatetimespan_relational_operators)|Vergleichen `COleDateTimeSpan` Sie zwei Werte.|
|[Operator double](#operator_double)|Konvertiert diesen `COleDateTimeSpan` Wert in eine **doppelte**.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[COleDateTimeSpan::m_span](#m_span)|Enthält das **double** zugrunde `COleDateTimeSpan` liegende Double für dieses Objekt.|
|[COleDateTimeSpan::m_status](#m_status)|Enthält den Status `COleDateTimeSpan` dieses Objekts.|

## <a name="remarks"></a>Bemerkungen

`COleDateTimeSpan`hat keine Basisklasse.

A `COleDateTimeSpan` hält Zeit in Tagen.

`COleDateTimeSpan`wird mit der Begleitklasse [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)verwendet. `COleDateTime`kapselt den `DATE` Datentyp der OLE-Automatisierung. `COleDateTime`stellt absolute Zeitwerte dar. Alle `COleDateTime` Berechnungen `COleDateTimeSpan` beinhalten Werte. Die Beziehung zwischen diesen Klassen ist analog zu der zwischen [CTime](../../atl-mfc-shared/reference/ctime-class.md) und [CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md).

Weitere Informationen zu `COleDateTime` `COleDateTimeSpan` den und Klassen finden Sie im Artikel [Datum und Uhrzeit: Automatisierungssupport](../../atl-mfc-shared/date-and-time-automation-support.md).

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** ATLComTime.h

## <a name="coledatetimespan-relational-operators"></a><a name="coledatetimespan_relational_operators"></a>COleDateTimeSpan Relationale Operatoren

Vergleichsoperatoren.

```
bool operator==(const COleDateTimeSpan& dateSpan) const throw();
bool operator!=(const COleDateTimeSpan& dateSpan) const throw();
bool operator<(const COleDateTimeSpan& dateSpan) const throw();
bool operator>(const COleDateTimeSpan& dateSpan) const throw();
bool operator<=(const COleDateTimeSpan& dateSpan) const throw();
bool operator>=(const COleDateTimeSpan& dateSpan) const throw();
```

### <a name="parameters"></a>Parameter

*dateSpan*<br/>
Das zu vergleichende `COleDateTimeSpan`-Element.

### <a name="return-value"></a>Rückgabewert

Diese Operatoren vergleichen zwei Datums-/Zeitzeitwerte und geben TRUE zurück, wenn die Bedingung wahr ist. andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

> [!NOTE]
> Ein ATLASSERT tritt auf, wenn einer der beiden Operanden ungültig ist.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#25](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_1.cpp)]

[!code-cpp[NVC_ATLMFC_Utilities#26](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_2.cpp)]

## <a name="coledatetimespancoledatetimespan"></a><a name="coledatetimespan"></a>ColedateTimeSpan::ColeDateTimeSpan

Erstellt ein `COleDateTimeSpan`-Objekt.

```
COleDateTimeSpan() throw();
COleDateTimeSpan(double dblSpanSrc) throw();
COleDateTimeSpan(LONG lDays, int nHours, int nMins, int nSecs) throw();
```

### <a name="parameters"></a>Parameter

*dblSpanSrc*<br/>
Die Anzahl der Tage, die `COleDateTimeSpan` in das neue Objekt kopiert werden sollen.

*lDays*, *nHours*, *nMins*, *nSecs*<br/>
Geben Sie die Tages- und Zeitwerte an, die in das neue `COleDateTimeSpan` Objekt kopiert werden sollen.

### <a name="remarks"></a>Bemerkungen

Alle diese Konstruktoren `COleDateTimeSpan` erstellen neue Objekte, die auf den angegebenen Wert initialisiert wurden. Eine kurze Beschreibung der einzelnen Konstruktoren folgt:

- **COleDateTimeSpan( )** Erstellt ein `COleDateTimeSpan` Objekt, das auf 0 initialisiert wurde.

- **COleDateTimeSpan(** `dblSpanSrc` **)** Erstellt ein `COleDateTimeSpan` Objekt aus einem Gleitkommawert.

- **COleDateTimeSpan(** `lDays` **,** `nHours` **,** `nMins` **)** `nSecs` **)** Erstellt ein `COleDateTimeSpan` Objekt, das auf die angegebenen numerischen Werte initialisiert wurde.

Der Status des `COleDateTimeSpan` neuen Objekts ist auf gültig festgelegt.

Weitere Informationen zu den `COleDateTimeSpan` Grenzwerten für Werte finden Sie im Artikel [Datum und Uhrzeit: Automatisierungssupport](../../atl-mfc-shared/date-and-time-automation-support.md).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#14](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_3.cpp)]

## <a name="coledatetimespanformat"></a><a name="format"></a>COleDateTimeSpan::Format

Generiert eine formatierte Zeichenfolgendarstellung eines `COleDateTimeSpan` Objekts.

```
CString Format(LPCTSTR pFormat) const;
CString Format(UINT nID) const;
```

### <a name="parameters"></a>Parameter

*pFormat*<br/>
Eine Formatierungszeichenfolge, die der `printf` Formatierungszeichenfolge ähnelt. Formatierungscodes, denen`%`ein Prozentzeichen ( ) `COleDateTimeSpan` vorangestellt ist, werden durch die entsprechende Komponente ersetzt. Andere Zeichen in der Formatierungszeichenfolge werden unverändert in die zurückgegebene Zeichenfolge kopiert. Der Wert und die Bedeutung `Format` der Formatierungscodes für sind unten aufgeführt:

- **%H** Stunden am aktuellen Tag

- **%M** Minuten in der aktuellen Stunde

- **%S** Sekunden in der aktuellen Minute

- **%%** Prozentzeichen

Die vier oben aufgeführten Formatcodes sind die einzigen Codes, die Format akzeptiert.

-

*nID*<br/>
Die Ressourcen-ID für die Formatsteuerungszeichenfolge.

### <a name="return-value"></a>Rückgabewert

A, `CString` das den formatierten Datums-/Zeitzeitwert enthält.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Funktionen auf, um eine formatierte Darstellung des Zeitzeitwerts zu erstellen. Wenn der Status `COleDateTimeSpan` dieses Objekts null ist, ist der Rückgabewert eine leere Zeichenfolge. Wenn der Status ungültig ist, wird die Rückgabezeichenfolge durch die Zeichenfolgenressource IDS_INVALID_DATETIMESPAN angegeben.

Eine kurze Beschreibung der Formulare für diese Funktion folgt:

**Format(** *pFormat* **)**<br/>
Dieses Formular formatiert den Wert mithilfe der Formatzeichenfolge, die spezielle Formatierungscodes enthält, denen ein Prozentzeichen (%) vorangestellt ist, wie in `printf`. Die Formatierungszeichenfolge wird als Parameter an die Funktion übergeben.

**Format(** *nID* **)**<br/>
Dieses Formular formatiert den Wert mithilfe der Formatzeichenfolge, die spezielle Formatierungscodes enthält, denen ein Prozentzeichen (%) vorangestellt ist, wie in `printf`. Die Formatierungszeichenfolge ist eine Ressource. Die ID dieser Zeichenfolgenressource wird als Parameter übergeben.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#15](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_4.cpp)]

## <a name="coledatetimespangetdays"></a><a name="getdays"></a>COleDateTimeSpan::GetDays

Ruft den Tagesteil dieses Datums-/Zeitspannenwerts ab.

```
LONG GetDays() const throw();
```

### <a name="return-value"></a>Rückgabewert

Der Tagesteil dieses Datums-/Zeitspannenwerts.

### <a name="remarks"></a>Bemerkungen

Die Rückgabewerte dieser Funktion liegen zwischen ca. - 3.615.000 und 3.615.000.

Weitere Funktionen, die den `COleDateTimeSpan` Wert eines Objekts abfragen, finden Sie in den folgenden Memberfunktionen:

- [GetHours](#gethours)

- [Getminutes](#getminutes)

- [Getseconds](#getseconds)

- [GetTotalDays](#gettotaldays)

- [GetTotalHours](#gettotalhours)

- [GetTotalMinutes](#gettotalminutes)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#16](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_5.cpp)]

## <a name="coledatetimespangethours"></a><a name="gethours"></a>COledateTimeSpan::GetHours

Ruft den Stundenteil dieses Datums-/Zeitspannenwerts ab.

```
LONG GetHours() const throw();
```

### <a name="return-value"></a>Rückgabewert

Der Stundenteil dieses Datums-/Zeitspannenwerts.

### <a name="remarks"></a>Bemerkungen

Die Rückgabewerte dieser Funktion reichen zwischen - 23 und 23.

Weitere Funktionen, die den `COleDateTimeSpan` Wert eines Objekts abfragen, finden Sie in den folgenden Memberfunktionen:

- [GetDays](#getdays)

- [Getminutes](#getminutes)

- [Getseconds](#getseconds)

- [GetTotalDays](#gettotaldays)

- [GetTotalHours](#gettotalhours)

- [GetTotalMinutes](#gettotalminutes)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#17](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_6.cpp)]

## <a name="coledatetimespangetminutes"></a><a name="getminutes"></a>COleDateTimeSpan::GetMinutes

Ruft den Minutenteil dieses Datums-/Zeitspannenwerts ab.

```
LONG GetMinutes() const throw();
```

### <a name="return-value"></a>Rückgabewert

Der Minutenteil dieses Datums-/Zeitspannenwerts.

### <a name="remarks"></a>Bemerkungen

Die Rückgabewerte dieser Funktion liegen zwischen - 59 und 59.

Weitere Funktionen, die den `COleDateTimeSpan` Wert eines Objekts abfragen, finden Sie in den folgenden Memberfunktionen:

- [GetDays](#getdays)

- [GetHours](#gethours)

- [Getseconds](#getseconds)

- [GetTotalDays](#gettotaldays)

- [GetTotalHours](#gettotalhours)

- [GetTotalMinutes](#gettotalminutes)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#18](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_7.cpp)]

## <a name="coledatetimespangetseconds"></a><a name="getseconds"></a>COleDateTimeSpan::GetSeconds

Ruft den zweiten Teil dieses Datums-/Zeitzeitwerts ab.

```
LONG GetSeconds() const throw();
```

### <a name="return-value"></a>Rückgabewert

Der Sekundenteil dieses Datums/Zeitspannenwerts.

### <a name="remarks"></a>Bemerkungen

Die Rückgabewerte dieser Funktion liegen zwischen - 59 und 59.

Weitere Funktionen, die den `COleDateTimeSpan` Wert eines Objekts abfragen, finden Sie in den folgenden Memberfunktionen:

- [GetDays](#getdays)

- [GetHours](#gethours)

- [Getminutes](#getminutes)

- [GetTotalDays](#gettotaldays)

- [GetTotalHours](#gettotalhours)

- [GetTotalMinutes](#gettotalminutes)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#19](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_8.cpp)]

## <a name="coledatetimespangetstatus"></a><a name="getstatus"></a>COleDateTimeSpan::GetStatus

Ruft den Status (Gültigkeit) dieses Objekts `COleDateTimeSpan` ab.

```
DateTimeSpanStatus GetStatus() const throw();
```

### <a name="return-value"></a>Rückgabewert

Der Status `COleDateTimeSpan` dieses Werts.

### <a name="remarks"></a>Bemerkungen

Der Rückgabewert wird `DateTimeSpanStatus` durch den aufgezählten Typ definiert, der innerhalb der `COleDateTimeSpan` Klasse definiert ist.

```
enum DateTimeSpanStatus{
   valid = 0,
   invalid = 1,
   null = 2,
};
```

Eine kurze Beschreibung dieser Statuswerte finden Sie in der folgenden Liste:

- `COleDateTimeSpan::valid`Gibt an, dass dieses `COleDateTimeSpan` Objekt gültig ist.

- `COleDateTimeSpan::invalid`Gibt an, dass dieses `COleDateTimeSpan` Objekt ungültig ist. das heißt, sein Wert kann falsch sein.

- `COleDateTimeSpan::null`Gibt an, dass dieses `COleDateTimeSpan` Objekt null ist, d. h., dass kein Wert für dieses Objekt angegeben wurde. (Dies ist "null" im Datenbanksinn "keinen Wert haben" im Gegensatz zum C++ NULL.)

Der Status `COleDateTimeSpan` eines Objekts ist in den folgenden Fällen ungültig:

- Wenn dieses Objekt während eines arithmetischen Zuweisungsvorgangs einen `+=` Über- oder Unterlauf erlebt hat, nämlich, oder `-=`.

- Wenn diesem Objekt ein ungültiger Wert zugewiesen wurde.

- Wenn der Status dieses Objekts explizit `SetStatus`auf ungültig mit festgelegt wurde.

Weitere Informationen zu den Vorgängen, die den Status auf ungültig festlegen können, finden Sie unter [COleDateTimeSpan::operator +, -](../../atl-mfc-shared/reference/coledatetime-class.md#operator_add_-) und [COleDateTimeSpan::operator +=, -=](../../atl-mfc-shared/reference/coledatetime-class.md#operator_add_eq_-_eq).

Weitere Informationen zu den `COleDateTimeSpan` Grenzwerten für Werte finden Sie im Artikel [Datum und Uhrzeit: Automatisierungssupport](../../atl-mfc-shared/date-and-time-automation-support.md).

## <a name="coledatetimespangettotaldays"></a><a name="gettotaldays"></a>COleDateTimeSpan::GetTotalDays

Ruft diesen Datums-/Zeitzeitwert ab, ausgedrückt in Tagen.

```
double GetTotalDays() const throw();
```

### <a name="return-value"></a>Rückgabewert

Dieser Datums-/Zeitzeitwert wird in Tagen ausgedrückt. Obwohl diese Funktion prototypiert ist, um ein Double zurückzugeben, wird immer ein Ganzzahlwert zurückgegeben.

### <a name="remarks"></a>Bemerkungen

Die Rückgabewerte dieser Funktion liegen zwischen etwa - 3,65e6 und 3,65e6.

Weitere Funktionen, die den `COleDateTimeSpan` Wert eines Objekts abfragen, finden Sie in den folgenden Memberfunktionen:

- [GetDays](#getdays)

- [GetHours](#gethours)

- [Getminutes](#getminutes)

- [Getseconds](#getseconds)

- [GetTotalHours](#gettotalhours)

- [GetTotalMinutes](#gettotalminutes)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#20](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_9.cpp)]

## <a name="coledatetimespangettotalhours"></a><a name="gettotalhours"></a>COledateTimeSpan::GetTotalHours

Ruft diesen Datums-/Zeitspannenwert ab, ausgedrückt in Stunden.

```
double GetTotalHours() const throw();
```

### <a name="return-value"></a>Rückgabewert

Dieser Datums-/Zeitzeitwert wird in Stunden ausgedrückt. Obwohl diese Funktion prototypiert ist, um ein Double zurückzugeben, wird immer ein Ganzzahlwert zurückgegeben.

### <a name="remarks"></a>Bemerkungen

Die Rückgabewerte dieser Funktion liegen zwischen etwa - 8,77e7 und 8,77e7.

Weitere Funktionen, die den `COleDateTimeSpan` Wert eines Objekts abfragen, finden Sie in den folgenden Memberfunktionen:

- [GetDays](#getdays)

- [GetHours](#gethours)

- [Getminutes](#getminutes)

- [Getseconds](#getseconds)

- [GetTotalDays](#gettotaldays)

- [GetTotalMinutes](#gettotalminutes)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>Beispiel

Siehe Beispiel für [GetTotalDays](#gettotaldays).

## <a name="coledatetimespangettotalminutes"></a><a name="gettotalminutes"></a>COledateTimeSpan::GetTotalMinuten

Ruft diesen Datums-/Zeitzeitwert in Minuten ab.

```
double GetTotalMinutes() const throw();
```

### <a name="return-value"></a>Rückgabewert

Dieser Datums-/Zeitstichwert wird in Minuten ausgedrückt. Obwohl diese Funktion prototypiert ist, um ein Double zurückzugeben, wird immer ein Ganzzahlwert zurückgegeben.

### <a name="remarks"></a>Bemerkungen

Die Rückgabewerte dieser Funktion liegen zwischen etwa - 5.26e9 und 5.26e9.

Weitere Funktionen, die den `COleDateTimeSpan` Wert eines Objekts abfragen, finden Sie in den folgenden Memberfunktionen:

- [GetDays](#getdays)

- [GetHours](#gethours)

- [Getminutes](#getminutes)

- [Getseconds](#getseconds)

- [GetTotalDays](#gettotaldays)

- [GetTotalHours](#gettotalhours)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>Beispiel

Siehe Beispiel für [GetTotalDays](#gettotaldays).

## <a name="coledatetimespangettotalseconds"></a><a name="gettotalseconds"></a>COleDateTimeSpan::GetTotalSekunden

Ruft diesen Datums-/Zeitspannenwert in Sekunden um.

```
double GetTotalSeconds() const throw();
```

### <a name="return-value"></a>Rückgabewert

Dieser Datums-/Zeitzeitwert wird in Sekunden ausgedrückt. Obwohl diese Funktion prototypiert ist, um ein Double zurückzugeben, wird immer ein Ganzzahlwert zurückgegeben.

### <a name="remarks"></a>Bemerkungen

Die Rückgabewerte dieser Funktion reichen zwischen etwa - 3.16e11 und 3.16e11.

Weitere Funktionen, die den `COleDateTimeSpan` Wert eines Objekts abfragen, finden Sie in den folgenden Memberfunktionen:

- [GetDays](#getdays)

- [GetHours](#gethours)

- [Getminutes](#getminutes)

- [Getseconds](#getseconds)

- [GetTotalDays](#gettotaldays)

- [GetTotalHours](#gettotalhours)

- [GetTotalMinutes](#gettotalminutes)

### <a name="example"></a>Beispiel

Siehe Beispiel für [GetTotalDays](#gettotaldays).

## <a name="coledatetimespanm_span"></a><a name="m_span"></a>COleDateTimeSpan::m_span

Der **double** zugrunde liegende `COleDateTime` doppelte Wert für dieses Objekt.

```
double m_span;
```

### <a name="remarks"></a>Bemerkungen

Dieser Wert gibt die Datums-/Zeitspanne in Tagen an.

> [!CAUTION]
> Wenn Sie den Wert im **Doppeldatenelement** `COleDateTimeSpan` ändern, wird der Wert dieses Objekts geändert. Der Status dieses `COleDateTimeSpan` Objekts wird nicht geändert.

## <a name="coledatetimespanm_status"></a><a name="m_status"></a>COleDateTimeSpan::m_status

Der Typ für diesen Datenmember ist `DateTimeSpanStatus`der aufgezählte `COleDateTimeSpan` Typ , der innerhalb der Klasse definiert ist.

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

- `COleDateTimeSpan::valid`Gibt an, dass dieses `COleDateTimeSpan` Objekt gültig ist.

- `COleDateTimeSpan::invalid`Gibt an, dass dieses `COleDateTimeSpan` Objekt ungültig ist. das heißt, sein Wert kann falsch sein.

- `COleDateTimeSpan::null`Gibt an, dass dieses `COleDateTimeSpan` Objekt null ist, d. h., dass kein Wert für dieses Objekt angegeben wurde. (Dies ist "null" im Datenbanksinn "keinen Wert haben" im Gegensatz zum C++ NULL.)

Der Status `COleDateTimeSpan` eines Objekts ist in den folgenden Fällen ungültig:

- Wenn dieses Objekt während eines arithmetischen Zuweisungsvorgangs einen `+=` Über- oder Unterlauf erlebt hat, nämlich, oder `-=`.

- Wenn diesem Objekt ein ungültiger Wert zugewiesen wurde.

- Wenn der Status dieses Objekts mit [SetStatus](#setstatus)explizit auf ungültig festgelegt wurde.

Weitere Informationen zu den Vorgängen, die den Status auf ungültig festlegen können, finden Sie unter [COleDateTimeSpan::operator +, -](../../atl-mfc-shared/reference/coledatetime-class.md#operator_add_-) und [COleDateTimeSpan::operator +=, -=](../../atl-mfc-shared/reference/coledatetime-class.md#operator_add_eq_-_eq).

> [!CAUTION]
> Dieser Datenmember ist für fortgeschrittene Programmiersituationen. Sie sollten die Inline-Memberfunktionen [GetStatus](#getstatus) und [SetStatus](#setstatus)verwenden. Weitere `SetStatus` Hinweise zur expliziten Einstellung dieses Datenmembers finden Sie unter .

Weitere Informationen zu den `COleDateTimeSpan` Grenzwerten für Werte finden Sie im Artikel [Datum und Uhrzeit: Automatisierungssupport](../../atl-mfc-shared/date-and-time-automation-support.md).

## <a name="coledatetimespanoperator-"></a><a name="operator_eq"></a>COleDateTimeSpan::Operator =

Kopiert `COleDateTimeSpan` einen Wert.

```
COleDateTimeSpan& operator=(double dblSpanSrc) throw();
```

### <a name="remarks"></a>Bemerkungen

Dieser überladene Zuweisungsoperator kopiert den Quelldatums-/Zeitzeitwert in dieses `COleDateTimeSpan` Objekt.

## <a name="coledatetimespanoperator---"></a><a name="operator_add_-"></a>COleDateTimeSpan::operator +, -

Hinzufügen, Subtrahieren und `COleDateTimeSpan` Ändern von Zeichen für Werte.

```
COleDateTimeSpan operator+(const COleDateTimeSpan& dateSpan) const throw();
COleDateTimeSpan operator-(const COleDateTimeSpan& dateSpan) const throw();
COleDateTimeSpan operator-() const throw();
```

### <a name="remarks"></a>Bemerkungen

Mit den ersten beiden Operatoren können Sie Datums-/Zeitzeitwerte hinzufügen und subtrahieren. Mit der dritten Seite können Sie das Vorzeichen eines Datums-/Zeitzeitwerts ändern.

Wenn einer der Operanden null ist, `COleDateTimeSpan` ist der Status des resultierenden Werts null.

Wenn einer der Operanden ungültig und der andere nicht null `COleDateTimeSpan` ist, ist der Status des resultierenden Werts ungültig.

Weitere Informationen zu den gültigen, ungültigen und NULL-Statuswerten finden Sie in der m_status-Membervariablen. [m_status](#m_status)

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#23](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_10.cpp)]

## <a name="coledatetimespanoperator---"></a><a name="operator_add_eq_-_eq"></a>COleDateTimeSpan::operator +=, -=

Fügen Sie einen `COleDateTimeSpan` Wert `COleDateTimeSpan` hinzu, und subtrahieren Sie ihn von diesem Wert.

```
COleDateTimeSpan& operator+=(const COleDateTimeSpan dateSpan) throw();
COleDateTimeSpan& operator-=(const COleDateTimeSpan dateSpan) throw();
```

### <a name="remarks"></a>Bemerkungen

Mit diesen Operatoren können Sie Datums-/Zeitzeitwerte von diesem `COleDateTimeSpan` Objekt hinzufügen und subtrahieren. Wenn einer der Operanden null ist, `COleDateTimeSpan` ist der Status des resultierenden Werts null.

Wenn einer der Operanden ungültig und der andere nicht null `COleDateTimeSpan` ist, ist der Status des resultierenden Werts ungültig.

Weitere Informationen zu den gültigen, ungültigen und NULL-Statuswerten finden Sie in der m_status-Membervariablen. [m_status](#m_status)

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#24](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_11.cpp)]

## <a name="coledatetimespanoperator-double"></a><a name="operator_double"></a>COleDateTimeSpan::Operator-Doppel

Konvertiert diesen `COleDateTimeSpan` Wert in eine **doppelte**.

```
operator double() const throw();
```

### <a name="remarks"></a>Bemerkungen

Dieser Operator gibt den `COleDateTimeSpan` Wert dieses Werts als Gleitkommazahlvon Tagen zurück.

## <a name="coledatetimespansetdatetimespan"></a><a name="setdatetimespan"></a>COledateTimeSpan::SetDateTimeSpan

Legt den Wert dieses Datums-/Zeitzeitwerts fest.

```
void SetDateTimeSpan(LONG lDays, int nHours, int nMins, int nSecs) throw();
```

### <a name="parameters"></a>Parameter

*lDays*, *nHours*, *nMins*, *nSecs*<br/>
Geben Sie die Datums- und Zeitzeitwerte `COleDateTimeSpan` an, die in dieses Objekt kopiert werden sollen.

### <a name="remarks"></a>Bemerkungen

Funktionen, die den Wert `COleDateTimeSpan` eines Objekts abfragen, finden Sie in den folgenden Memberfunktionen:

- [GetDays](#getdays)

- [GetHours](#gethours)

- [Getminutes](#getminutes)

- [Getseconds](#getseconds)

- [GetTotalDays](#gettotaldays)

- [GetTotalHours](#gettotalhours)

- [GetTotalMinutes](#gettotalminutes)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#21](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_12.cpp)]

## <a name="coledatetimespansetstatus"></a><a name="setstatus"></a>COleDateTimeSpan::SetStatus

Legt den Status (Gültigkeit) dieses `COleDateTimeSpan` Objekts fest.

```
void SetStatus(DateTimeSpanStatus status) throw();
```

### <a name="parameters"></a>Parameter

*Status*<br/>
Der neue Statuswert `COleDateTimeSpan` für dieses Objekt.

### <a name="remarks"></a>Bemerkungen

Der *Statusparameterwert* wird `DateTimeSpanStatus` durch den aufgezählten Typ definiert, der innerhalb der `COleDateTimeSpan` Klasse definiert ist.

```
enum DateTimeSpanStatus{
   valid = 0,
   invalid = 1,
   null = 2,
   };
```

Eine kurze Beschreibung dieser Statuswerte finden Sie in der folgenden Liste:

- `COleDateTimeSpan::valid`Gibt an, dass dieses `COleDateTimeSpan` Objekt gültig ist.

- `COleDateTimeSpan::invalid`Gibt an, dass dieses `COleDateTimeSpan` Objekt ungültig ist. das heißt, sein Wert kann falsch sein.

- `COleDateTimeSpan::null`Gibt an, dass dieses `COleDateTimeSpan` Objekt null ist, d. h., dass kein Wert für dieses Objekt angegeben wurde. (Dies ist "null" im Datenbanksinn "keinen Wert haben" im Gegensatz zum C++ NULL.)

   > [!CAUTION]
   > Diese Funktion ist für fortgeschrittene Programmiersituationen. Diese Funktion ändert die Daten in diesem Objekt nicht. Es wird am häufigsten verwendet, um den Status auf **null** oder **ungültig**festzulegen. Beachten Sie, dass der Zuweisungsoperator ([operator =](#operator_eq)) und [SetDateTimeSpan](#setdatetimespan) den Status des Objekts basierend auf dem Quellwert(n) festlegen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#22](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_13.cpp)]

## <a name="see-also"></a>Siehe auch

[COleDateTime-Klasse](../../atl-mfc-shared/reference/coledatetime-class.md)<br/>
[CTime-Klasse](../../atl-mfc-shared/reference/ctime-class.md)<br/>
[CTimeSpan-Klasse](../../atl-mfc-shared/reference/ctimespan-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[FREIGEGEBENe ATL/MFC-Klassen](../../atl-mfc-shared/atl-mfc-shared-classes.md)
