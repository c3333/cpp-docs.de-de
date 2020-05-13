---
title: COleDateTime-Klasse
ms.date: 03/27/2019
f1_keywords:
- COleDateTime
- ATLCOMTIME/ATL::COleDateTime
- ATLCOMTIME/ATL::COleDateTime::COleDateTime
- ATLCOMTIME/ATL::COleDateTime::Format
- ATLCOMTIME/ATL::COleDateTime::GetAsDBTIMESTAMP
- ATLCOMTIME/ATL::COleDateTime::GetAsSystemTime
- ATLCOMTIME/ATL::COleDateTime::GetAsUDATE
- ATLCOMTIME/ATL::COleDateTime::GetCurrentTime
- ATLCOMTIME/ATL::COleDateTime::GetDay
- ATLCOMTIME/ATL::COleDateTime::GetDayOfWeek
- ATLCOMTIME/ATL::COleDateTime::GetDayOfYear
- ATLCOMTIME/ATL::COleDateTime::GetHour
- ATLCOMTIME/ATL::COleDateTime::GetMinute
- ATLCOMTIME/ATL::COleDateTime::GetMonth
- ATLCOMTIME/ATL::COleDateTime::GetSecond
- ATLCOMTIME/ATL::COleDateTime::GetStatus
- ATLCOMTIME/ATL::COleDateTime::GetYear
- ATLCOMTIME/ATL::COleDateTime::ParseDateTime
- ATLCOMTIME/ATL::COleDateTime::SetDate
- ATLCOMTIME/ATL::COleDateTime::SetDateTime
- ATLCOMTIME/ATL::COleDateTime::SetStatus
- ATLCOMTIME/ATL::COleDateTime::SetTime
- ATLCOMTIME/ATL::COleDateTime::m_dt
- ATLCOMTIME/ATL::COleDateTime::m_status
helpviewer_keywords:
- shared classes, COleDateTime
- time-only values
- Date data type, MFC encapsulation of
- COleDateTime class
- dates, handling in MFC
- time, handling in MFC
ms.assetid: e718f294-16ec-4649-88b6-a4dbae5178fb
ms.openlocfilehash: 8ba09430427b6ece8ae5956912cbcc40fb33fcf2
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81747162"
---
# <a name="coledatetime-class"></a>COleDateTime-Klasse

Kapselt den Datentyp, der in der `DATE` OLE-Automatisierung verwendet wird.

## <a name="syntax"></a>Syntax

```
class COleDateTime
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[COleDateTime::COleDateTime](#coledatetime)|Erstellt ein `COleDateTime`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[COleDateTime::Format](#format)|Generiert eine formatierte Zeichenfolgendarstellung eines `COleDateTime` Objekts.|
|[COleDateTime::GetAsDBTIMESTAMP](#getasdbtimestamp)|Rufen Sie diese Methode auf, um die Zeit im `COleDateTime` Objekt als `DBTIMESTAMP` Datenstruktur abzurufen.|
|[COleDateTime::GetasSystemTime](#getassystemtime)|Rufen Sie diese Methode auf, um die Zeit im `COleDateTime` Objekt als [SYSTEMTIME-Datenstruktur](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) abzurufen.|
|[ColeDateTime::GetAsUDATE](#getasudate)|Rufen Sie diese Methode auf, um die Zeit im `COleDateTime` als `UDATE` Datenstruktur abzurufen.|
|[COleDateTime::GetCurrentTime](#getcurrenttime)|Erstellt `COleDateTime` ein Objekt, das die aktuelle Uhrzeit darstellt (statische Memberfunktion).|
|[COleDateTime::GetDay](#getday)|Gibt den `COleDateTime` Tag zurück, den dieses Objekt darstellt (1 - 31).|
|[COleDateTime::GetDayOfWeek](#getdayofweek)|Gibt den Wochentag `COleDateTime` zurück, den dieses Objekt darstellt (Sonntag = 1).|
|[COleDateTime::GetDayOfYear](#getdayofyear)|Gibt den Tag des `COleDateTime` Jahres zurück, den dieses Objekt darstellt (Jan 1 = 1).|
|[COleDateTime::GetHour](#gethour)|Gibt die `COleDateTime` Stunde zurück, die dieses Objekt darstellt (0 - 23).|
|[COleDateTime::GetMinute](#getminute)|Gibt die `COleDateTime` Minute zurück, die dieses Objekt darstellt (0 - 59).|
|[COleDateTime::GetMonth](#getmonth)|Gibt den `COleDateTime` Monat zurück, den dieses Objekt darstellt (1 - 12).|
|[COleDateTime::GetSecond](#getsecond)|Gibt die `COleDateTime` Sekunde zurück, die dieses Objekt darstellt (0 - 59).|
|[COleDateTime::GetStatus](#getstatus)|Ruft den Status (Gültigkeit) dieses Objekts `COleDateTime` ab.|
|[COleDateTime::Jahr](#getyear)|Gibt das `COleDateTime` Jahr zurück, das dieses Objekt darstellt.|
|[COleDateTime::ParseDateTime](#parsedatetime)|Liest einen Datums-/Uhrzeitwert aus `COleDateTime`einer Zeichenfolge und legt den Wert von fest.|
|[COleDateTime::SetDate](#setdate)|Legt den Wert `COleDateTime` dieses Objekts auf den angegebenen Datumswert fest.|
|[COleDateTime::SetDateTime](#setdatetime)|Legt den Wert `COleDateTime` dieses Objekts auf den angegebenen Datums-/Uhrzeitwert fest.|
|[COleDateTime::SetStatus](#setstatus)|Legt den Status (Gültigkeit) dieses `COleDateTime` Objekts fest.|
|[COleDateTime::SetTime](#settime)|Legt den Wert `COleDateTime` dieses Objekts auf den angegebenen Nur-Zeit-Wert fest.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[COleDateTime::operator ==, COleDateTime::operator < usw.](#coledatetime_relational_operators)|Vergleichen `COleDateTime` Sie zwei Werte.|
|[COleDateTime::operator +, COleDateTime::operator -](#operator_add_-)|Hinzufügen und `COleDateTime` Subtrahieren von Werten.|
|[COleDateTime::operator +=, COleDateTime::operator -=](#operator_add_eq_-_eq)|Fügen Sie einen `COleDateTime` Wert `COleDateTime` von diesem Objekt hinzu und subtrahieren Sie ihn.|
|[COleDateTime::Operator =](#operator_eq)|Kopiert `COleDateTime` einen Wert.|
|[COleDateTime::operator DATE, COleDateTime::operator Datum*](#operator_date)|Konvertiert einen `COleDateTime` Wert `DATE` in `DATE*`eine oder eine .|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[COleDateTime::m_dt](#m_dt)|Enthält den `DATE` Basiswert für dieses `COleDateTime` Objekt.|
|[COleDateTime::m_status](#m_status)|Enthält den Status `COleDateTime` dieses Objekts.|

## <a name="remarks"></a>Bemerkungen

`COleDateTime`hat keine Basisklasse.

Es ist einer der möglichen [VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant) Typen für den VARIANT-Datentyp der OLE-Automatisierung. Ein `COleDateTime` Wert stellt einen absoluten Datums- und Uhrzeitwert dar.

Der `DATE` Typ wird als Gleitkommawert implementiert. Die Tage werden ab dem 30. Dezember 1899 um Mitternacht gemessen. Die folgende Tabelle zeigt einige Datumsangaben und die zugehörigen Werte:

|Date|Wert|
|----------|-----------|
|29. Dezember 1899, Mitternacht|-1.0|
|29. Dezember 1899, 6 Uhr|-1.25|
|30. Dezember 1899, Mitternacht|0,0|
|31. Dezember 1899, Mitternacht|1.0|
|1. Januar 1900, 6 Uhr|2,25|

> [!CAUTION]
> In der obigen Tabelle werden die Tageswerte zwar vor Mitternacht am 30. Dezember 1899 negativ, die Tageszeitwerte jedoch nicht. Beispielsweise wird 6:00 Uhr immer durch einen Bruchwert 0,25 dargestellt, unabhängig davon, ob die ganze Zahl, die den Tag darstellt, positiv (nach dem 30. Dezember 1899) oder negativ (vor dem 30. Dezember 1899) ist. Dies bedeutet, dass ein einfacher Gleitkommavergleich fälschlicherweise eine Darstellung von `COleDateTime` 6:00 Uhr am 29.12.1899 als **später** als eine, die 7:00 Uhr am selben Tag darstellt.

Die `COleDateTime` Unterrichtspunkte stammen vom 1. Januar 100 bis zum 31. Dezember 9999. Die `COleDateTime` Klasse verwendet den Gregorianischen Kalender. Julian-Termine werden nicht unterstützt. `COleDateTime`ignoriert die Sommerzeit. (Siehe [Datum und Uhrzeit: Automatisierungsunterstützung](../../atl-mfc-shared/date-and-time-automation-support.md).)

> [!NOTE]
> Sie können `%y` das Format verwenden, um ein zweistelliges Jahr nur für Datumsangaben ab 1900 abzurufen. Wenn Sie `%y` das Format an einem Datum vor 1900 verwenden, generiert der Code einen ASSERT-Fehler.

Dieser Typ wird auch verwendet, um Nur-Datums- oder Zeitwerte darzustellen. Konventionell wird das Datum 0 (30. Dezember 1899) für nur Zeitwerte und die Uhrzeit 00:00 (Mitternacht) für nur Datumswerte verwendet.

Wenn Sie `COleDateTime` ein Objekt mit einem Datum kleiner als 100 erstellen, `GetYear` `GetMonth`wird `GetDay` `GetHour`das `GetMinute`Datum `GetSecond` akzeptiert, aber nachfolgende Aufrufe von , , , , und fail und return -1. Früher konnten Sie zweistellige Datumsangaben verwenden, Datumsangaben müssen jedoch in MFC 4.2 und höher 100 oder größer sein.

Um Probleme zu vermeiden, geben Sie ein vierstelliges Datum an. Beispiel:

[!code-cpp[NVC_ATLMFC_Utilities#1](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_1.cpp)]

Grundlegende arithmetische Operationen `COleDateTime` für die Werte verwenden die Begleitklasse [COleDateTimeSpan](../../atl-mfc-shared/reference/coledatetimespan-class.md). `COleDateTimeSpan`Werte definieren ein Zeitintervall. Die Beziehung zwischen diesen Klassen ähnelt der zwischen [CTime](../../atl-mfc-shared/reference/ctime-class.md) und [CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md).

Weitere Informationen zu `COleDateTime` `COleDateTimeSpan` den und Klassen finden Sie im Artikel [Datum und Uhrzeit: Automatisierungssupport](../../atl-mfc-shared/date-and-time-automation-support.md).

## <a name="requirements"></a>Requirements (Anforderungen)

**Kopfzeile:** ATLComTime.h

## <a name="coledatetime-relational-operators"></a><a name="coledatetime_relational_operators"></a>COleDateTime Relationale Operatoren

Vergleichsoperatoren.

```
bool operator==(const COleDateTime& date) const throw();
bool operator!=(const COleDateTime& date) const throw();
bool operator<(const COleDateTime& date) const throw();
bool operator>(const COleDateTime& date) const throw();
bool operator<=(const COleDateTime& date) const throw();
bool operator>=(const COleDateTime& date) const throw();
```

### <a name="parameters"></a>Parameter

*date*<br/>
Das zu vergleichende `COleDateTime`-Objekt.

### <a name="remarks"></a>Bemerkungen

> [!NOTE]
> Ein ATLASSERT tritt auf, wenn einer der beiden Operanden ungültig ist.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#13](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_2.cpp)]

### <a name="example"></a>Beispiel

Die **>=** Operatoren **>**, **<** ** \< **, und `COleDateTime` bestätigen, wenn das Objekt auf null gesetzt ist.

[!code-cpp[NVC_ATLMFC_Utilities#170](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_3.cpp)]

## <a name="coledatetimecoledatetime"></a><a name="coledatetime"></a>COleDateTime::COleDateTime

Erstellt ein `COleDateTime`-Objekt.

```
COleDateTime() throw();
COleDateTime(const VARIANT& varSrc) throw();
COleDateTime(DATE dtSrc) throw();
COleDateTime(time_t timeSrc) throw();
COleDateTime(__time64_t timeSrc) throw();
COleDateTime(const SYSTEMTIME& systimeSrc) throw();
COleDateTime(const FILETIME& filetimeSrc) throw();

COleDateTime(int nYear,
    int nMonth,
    int nDay,
    int nHour,
    int nMin,
    int nSec) throw();

COleDateTime(WORD wDosDate,
    WORD wDosTime) throw();
COleDateTime(const DBTIMESTAMP& timeStamp) throw();
```

### <a name="parameters"></a>Parameter

*dateSrc*<br/>
Ein `COleDateTime` vorhandenes Objekt, das `COleDateTime` in das neue Objekt kopiert werden soll.

*varSrc*<br/>
Eine `VARIANT` vorhandene Datenstruktur `COleVariant` (möglicherweise ein Objekt), die in einen Datums-/Uhrzeitwert (VT_DATE) konvertiert und in das neue `COleDateTime` Objekt kopiert werden soll.

*dtSrc*<br/>
Ein Datums-/Uhrzeitwert (`DATE`), `COleDateTime` der in das neue Objekt kopiert werden soll.

*timeSrc*<br/>
Ein `time_t` `__time64_t` oder ein Wert, der in einen Datums-/Uhrzeitwert konvertiert und in das neue `COleDateTime` Objekt kopiert werden soll.

*systimeSrc*<br/>
Eine `SYSTEMTIME` Struktur, die in einen Datums-/Uhrzeitwert konvertiert und in das neue `COleDateTime` Objekt kopiert werden soll.

*filetimeSrc*<br/>
Eine `FILETIME` Struktur, die in einen Datums-/Uhrzeitwert konvertiert und in das neue `COleDateTime` Objekt kopiert werden soll. A `FILETIME` verwendet UTC (Universal Coordinated Time), wenn Sie also eine ortszeite Zeit in der Struktur übergeben, sind Ihre Ergebnisse falsch. Weitere Informationen finden Sie unter [Dateizeiten](/windows/win32/SysInfo/file-times) im Windows SDK.

*nJahr*, *nMonat*, *nDay*, *nHour*, *nMin*, *nSec*<br/>
Geben Sie die Datums- und `COleDateTime` Uhrzeitwerte an, die in das neue Objekt kopiert werden sollen.

*wDosDate*, *wDosTime*<br/>
MS-DOS-Datums- und -Uhrzeitwerte, die in einen `COleDateTime` Datums-/Uhrzeitwert konvertiert und in das neue Objekt kopiert werden sollen.

*Timestamp*<br/>
Ein Verweis auf eine [DBTimeStamp-Struktur,](/dotnet/api/system.data.oledb.oledbtype) die die aktuelle Ortszeit enthält.

### <a name="remarks"></a>Bemerkungen

Alle diese Konstruktoren `COleDateTime` erstellen neue Objekte, die auf den angegebenen Wert initialisiert wurden. Die folgende Tabelle zeigt gültige Bereiche für jede Datums- und Uhrzeitkomponente:

|Datum/Uhrzeit-Komponente|Gültiger Bereich|
|--------------------------|-----------------|
|year|100 - 9999|
|month|0 - 12|
|day|0 - 31|
|hour|0 - 23|
|minute|0 - 59|
|second|0 - 59|

Beachten Sie, dass die tatsächliche Obergrenze für die Tageskomponente je nach Denmonats- und Jahreskomponenten variiert. Weitere Informationen finden `SetDate` `SetDateTime` Sie unter den Or-Member-Funktionen.

Im Folgenden finden Sie eine kurze Beschreibung der einzelnen Konstruktore:

- `COleDateTime(`**)** Erstellt `COleDateTime` ein Objekt, das auf 0 (Mitternacht, 30. Dezember 1899) initialisiert wurde.

- `COleDateTime(``dateSrc` **)** Erstellt `COleDateTime` ein Objekt `COleDateTime` aus einem vorhandenen Objekt.

- `COleDateTime(`*varSrc* **)** Erstellt `COleDateTime` ein Objekt. Versucht, eine `VARIANT` Struktur oder ein [COleVariant-Objekt](../../mfc/reference/colevariant-class.md) in einen Datums-/Uhrzeitwert ( `VT_DATE`) zu konvertieren. Wenn diese Konvertierung erfolgreich ist, wird der `COleDateTime` konvertierte Wert in das neue Objekt kopiert. Ist dies nicht der `COleDateTime` Fall, wird der Wert des Objekts auf 0 (Mitternacht, 30. Dezember 1899) und sein Status auf ungültig gesetzt.

- `COleDateTime(``dtSrc` **)** Erstellt `COleDateTime` ein Objekt `DATE` aus einem Wert.

- `COleDateTime(``timeSrc` **)** Erstellt `COleDateTime` ein Objekt `time_t` aus einem Wert.

- `COleDateTime(`*systimeSrc* **)** Erstellt `COleDateTime` ein `SYSTEMTIME` Objekt aus einem Wert.

- `COleDateTime(``filetimeSrc` **)** Erstellt `COleDateTime` ein Objekt `FILETIME` aus einem Wert. . A `FILETIME` verwendet UTC (Universal Coordinated Time), wenn Sie also eine ortszeite Zeit in der Struktur übergeben, sind Ihre Ergebnisse falsch. Weitere Informationen finden Sie unter [Dateizeiten](/windows/win32/SysInfo/file-times) im Windows SDK.

- `COleDateTime(``nYear`, `nMonth` `nDay`, `nHour` `nMin`, `nSec` , **)** Erstellt ein `COleDateTime` Objekt aus den angegebenen numerischen Werten.

- `COleDateTime(``wDosDate`, `wDosTime` **)** Erstellt `COleDateTime` ein Objekt aus den angegebenen MS-DOS-Datums- und -Uhrzeitwerten.

Weitere Informationen zum `time_t` Datentyp finden Sie in der [Zeitfunktion](../../c-runtime-library/reference/time-time32-time64.md) in der *Laufzeitbibliotheksreferenz*.

Weitere Informationen finden Sie in den Strukturen [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) und [FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime) im Windows SDK.

Weitere Informationen zu den `COleDateTime` Grenzwerten für Werte finden Sie im Artikel [Datum und Uhrzeit: Automatisierungssupport](../../atl-mfc-shared/date-and-time-automation-support.md).

> [!NOTE]
> Der Konstruktor, `DBTIMESTAMP` der Parameter verwendet, ist nur verfügbar, wenn OLEDB.h enthalten ist.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#2](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_4.cpp)]

## <a name="coledatetimeformat"></a><a name="format"></a>COleDateTime::Format

Erstellt eine formatierte Darstellung des Datums-/Uhrzeitwerts.

```
CString Format(DWORD dwFlags = 0,  LCID lcid = LANG_USER_DEFAULT) const;
CString Format(LPCTSTR lpszFormat) const;
CString Format(UINT nFormatID) const;
```

### <a name="parameters"></a>Parameter

*dwFlags*<br/>
Gibt eines der folgenden Gebietsschemaflags an:

- LOCALE_NOUSEROVERRIDE Verwenden Sie die Standardgebietsschemaeinstellungen des Systems anstelle von benutzerdefinierten Benutzereinstellungen.

- VAR_TIMEVALUEONLY Ignorieren Sie den Datumsteil während der Analyse.

- VAR_DATEVALUEONLY Ignorieren Sie den Zeitabschnitt während der Analyse.

*Lcid*<br/>
Gibt die Gebietsschema-ID an, die für die Konvertierung verwendet werden soll. Weitere Informationen zu Sprachbezeichnern finden Sie unter [Sprachbezeichner](/windows/win32/Intl/language-identifiers).

*lpszFormat*<br/>
Eine Formatierungszeichenfolge, die der `printf` Formatierungszeichenfolge ähnelt. Jeder Formatierungscode, dem `%`ein Prozentzeichen ( `COleDateTime` ) vorangestellt ist, wird durch die entsprechende Komponente ersetzt. Andere Zeichen in der Formatierungszeichenfolge werden unverändert in die zurückgegebene Zeichenfolge kopiert. Weitere Informationen finden Sie in der Laufzeitfunktion [strftime](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md). Der Wert und die Bedeutung `Format` der Formatierungscodes für sind:

- `%H`Stunden am aktuellen Tag

- `%M`Minuten in der aktuellen Stunde

- `%S`Sekunden in der aktuellen Minute

- `%%`Prozentzeichen

*nFormatID*<br/>
Die Ressourcen-ID für die Formatsteuerungszeichenfolge.

### <a name="return-value"></a>Rückgabewert

A, `CString` das den formatierten Datums-/Uhrzeitwert enthält.

### <a name="remarks"></a>Bemerkungen

Wenn der Status `COleDateTime` dieses Objekts null ist, ist der Rückgabewert eine leere Zeichenfolge. Wenn der Status ungültig ist, wird die Rückgabezeichenfolge durch die Zeichenfolgenressource ATL_IDS_DATETIME_INVALID angegeben.

Eine kurze Beschreibung der drei Formulare für diese Funktion folgt:

`Format`( *dwFlags*, *lcid*)<br/>
Dieses Formular formatiert den Wert mithilfe der Sprachspezifikationen (Gebietsschema-IDs) für Datum und Uhrzeit. Mit den Standardparametern wird dieses Formular das Datum und die Uhrzeit drucken, es sei denn, der Zeitabschnitt ist 0 (Mitternacht), in diesem Fall wird nur das Datum gedruckt, oder der Datumsabschnitt ist 0 (30. Dezember 1899), in diesem Fall wird es nur die Uhrzeit drucken. Wenn der Datums-/Uhrzeitwert 0 (30. Dezember 1899, Mitternacht) ist, wird dieses Formular mit den Standardparametern Mitternacht gedruckt.

`Format`( *lpszFormat*)<br/>
Dieses Formular formatiert den Wert mithilfe der Formatzeichenfolge, die spezielle Formatierungscodes enthält, denen ein Prozentzeichen (%) vorangestellt ist, wie in `printf`. Die Formatierungszeichenfolge wird als Parameter an die Funktion übergeben. Weitere Informationen zu den Formatierungscodes finden Sie unter [strftime, wcsftime](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) in der Laufzeitbibliotheksreferenz.

`Format`( *nFormatID*)<br/>
Dieses Formular formatiert den Wert mithilfe der Formatzeichenfolge, die spezielle Formatierungscodes enthält, denen ein Prozentzeichen (%) vorangestellt ist, wie in `printf`. Die Formatierungszeichenfolge ist eine Ressource. Die ID dieser Zeichenfolgenressource wird als Parameter übergeben. Weitere Informationen zu den Formatierungscodes finden Sie unter [strftime, wcsftime](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) in der *Laufzeitbibliotheksreferenz*.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#3](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_5.cpp)]

## <a name="coledatetimegetasdbtimestamp"></a><a name="getasdbtimestamp"></a>COleDateTime::GetAsDBTIMESTAMP

Rufen Sie diese Methode auf, um die Zeit im `COleDateTime` Objekt als `DBTIMESTAMP` Datenstruktur abzurufen.

```
bool GetAsDBTIMESTAMP(DBTIMESTAMP& timeStamp) const throw();
```

### <a name="parameters"></a>Parameter

*Timestamp*<br/>
Ein Verweis auf eine [DBTimeStamp-Struktur.](/dotnet/api/system.data.oledb.oledbtype)

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Speichert die resultierende Zeit in der referenzierten *timeStamp-Struktur.* Für `DBTIMESTAMP` die von dieser Funktion initialisierte Datenstruktur wird der `fraction` Member auf Null gesetzt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#4](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_6.cpp)]

## <a name="coledatetimegetassystemtime"></a><a name="getassystemtime"></a>COleDateTime::GetasSystemTime

Rufen Sie diese Methode auf, um die Zeit im `COleDateTime` Objekt als `SYSTEMTIME` Datenstruktur abzurufen.

```
bool GetAsSystemTime(SYSTEMTIME& sysTime) const throw();
```

### <a name="parameters"></a>Parameter

*Systime*<br/>
Ein Verweis auf eine [SYSTEMTIME-Struktur,](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) um den `COleDateTime` konvertierten Datums-/Uhrzeitwert vom Objekt zu erhalten.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE zurück, wenn erfolgreich; FALSE, wenn die Konvertierung `COleDateTime` fehlschlägt oder wenn das Objekt NULL oder ungültig ist.

### <a name="remarks"></a>Bemerkungen

`GetAsSystemTime`speichert die resultierende Zeit im referenzierten *sysTime-Objekt.* Für `SYSTEMTIME` die von dieser Funktion initialisierte Datenstruktur wird der `wMilliseconds` Member auf Null gesetzt.

Weitere Informationen zu den Statusinformationen, die in einem `COleDateTime` Objekt enthalten sind, finden Sie unter [GetStatus](#getstatus).

## <a name="coledatetimegetasudate"></a><a name="getasudate"></a>ColeDateTime::GetAsUDATE

Rufen Sie diese Methode auf, um die Zeit im `COleDateTime` Objekt als `UDATE` Datenstruktur abzurufen.

```
bool GetAsUDATE(UDATE& uDate) const throw();
```

### <a name="parameters"></a>Parameter

*Udate*<br/>
Ein Verweis `UDATE` auf eine Struktur, um den `COleDateTime` konvertierten Datums-/Uhrzeitwert vom Objekt zu erhalten.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE zurück, wenn erfolgreich; FALSE, wenn die Konvertierung `COleDateTime` fehlschlägt oder wenn das Objekt NULL oder ungültig ist.

### <a name="remarks"></a>Bemerkungen

Eine `UDATE` Struktur stellt ein "entpacktes" Datum dar.

## <a name="coledatetimegetcurrenttime"></a><a name="getcurrenttime"></a>COleDateTime::GetCurrentTime

Rufen Sie diese statische Memberfunktion auf, um den aktuellen Datums-/Uhrzeitwert zurückzugeben.

```
static COleDateTime WINAPI GetCurrentTime() throw();
```

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#5](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_7.cpp)]

## <a name="coledatetimegetday"></a><a name="getday"></a>COleDateTime::GetDay

Ruft den Tag des Monats ab, der durch diesen Datums-/Uhrzeitwert dargestellt wird.

```
int GetDay() const throw();
```

### <a name="return-value"></a>Rückgabewert

Der Tag des Monats, der `COleDateTime` durch `COleDateTime::error` den Wert dieses Objekts dargestellt wird oder wenn der Tag nicht abgerufen werden konnte.

### <a name="remarks"></a>Bemerkungen

Gültige Rückgabewerte liegen zwischen 1 und 31.

Informationen zu anderen Memberfunktionen, die `COleDateTime` den Wert dieses Objekts abfragen, finden Sie in den folgenden Memberfunktionen:

- [Getmonth](#getmonth)

- [Getyear](#getyear)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#6](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_8.cpp)]

## <a name="coledatetimegetdayofweek"></a><a name="getdayofweek"></a>COleDateTime::GetDayOfWeek

Ruft den Tag des Monats ab, der durch diesen Datums-/Uhrzeitwert dargestellt wird.

```
int GetDayOfWeek() const throw();
```

### <a name="return-value"></a>Rückgabewert

Der Wochentag, der durch den `COleDateTime` Wert `COleDateTime::error` dieses Objekts dargestellt wird oder wenn der Wochentag nicht abgerufen werden konnte.

### <a name="remarks"></a>Bemerkungen

Gültige Rückgabewerte liegen zwischen 1 und 7, wobei 1=Sonntag, 2=Montag usw.

Informationen zu anderen Memberfunktionen, die `COleDateTime` den Wert dieses Objekts abfragen, finden Sie in den folgenden Memberfunktionen:

- [GetDay](#getday)

- [Getmonth](#getmonth)

- [Getyear](#getyear)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfYear](#getdayofyear)

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#7](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_9.cpp)]

## <a name="coledatetimegetdayofyear"></a><a name="getdayofyear"></a>COleDateTime::GetDayOfYear

Ruft den Tag des Jahres ab, der durch diesen Datums-/Uhrzeitwert dargestellt wird.

```
int GetDayOfYear() const throw();
```

### <a name="return-value"></a>Rückgabewert

Der Tag des Jahres, der `COleDateTime` durch `COleDateTime::error` den Wert dieses Objekts dargestellt wird oder wenn der Tag des Jahres nicht ermittelt werden konnte.

### <a name="remarks"></a>Bemerkungen

Gültige Rückgabewerte liegen zwischen 1 und 366, wobei der 1. Januar = 1. Januar 1.

Informationen zu anderen Memberfunktionen, die `COleDateTime` den Wert dieses Objekts abfragen, finden Sie in den folgenden Memberfunktionen:

- [GetDay](#getday)

- [Getmonth](#getmonth)

- [Getyear](#getyear)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#8](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_10.cpp)]

## <a name="coledatetimegethour"></a><a name="gethour"></a>COleDateTime::GetHour

Ruft die Stunde ab, die durch diesen Datums-/Uhrzeitwert dargestellt wird.

```
int GetHour() const throw();
```

### <a name="return-value"></a>Rückgabewert

Die Stunde, die durch `COleDateTime` den `COleDateTime::error` Wert dieses Objekts dargestellt wird oder wenn die Stunde nicht abgerufen werden konnte.

### <a name="remarks"></a>Bemerkungen

Gültige Rückgabewerte liegen zwischen 0 und 23.

Informationen zu anderen Memberfunktionen, die `COleDateTime` den Wert dieses Objekts abfragen, finden Sie in den folgenden Memberfunktionen:

- [GetDay](#getday)

- [Getmonth](#getmonth)

- [Getyear](#getyear)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#9](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_11.cpp)]

## <a name="coledatetimegetminute"></a><a name="getminute"></a>COleDateTime::GetMinute

Ruft die Minute ab, die durch diesen Datums-/Uhrzeitwert dargestellt wird.

```
int GetMinute() const throw();
```

### <a name="return-value"></a>Rückgabewert

Die Minute, die durch `COleDateTime` den `COleDateTime::error` Wert dieses Objekts dargestellt wird oder wenn die Minute nicht abgerufen werden konnte.

### <a name="remarks"></a>Bemerkungen

Gültige Rückgabewerte liegen zwischen 0 und 59.

Informationen zu anderen Memberfunktionen, die `COleDateTime` den Wert dieses Objekts abfragen, finden Sie in den folgenden Memberfunktionen:

- [GetDay](#getday)

- [Getmonth](#getmonth)

- [Getyear](#getyear)

- [GetHour](#gethour)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

### <a name="example"></a>Beispiel

Siehe Beispiel für [GetHour](#gethour).

## <a name="coledatetimegetmonth"></a><a name="getmonth"></a>COleDateTime::GetMonth

Ruft den Monat ab, der durch diesen Datums-/Uhrzeitwert dargestellt wird.

```
int GetMonth() const throw();
```

### <a name="return-value"></a>Rückgabewert

Der Monat, der durch `COleDateTime` den `COleDateTime::error` Wert dieses Objekts dargestellt wird oder wenn der Monat nicht abgerufen werden konnte.

### <a name="remarks"></a>Bemerkungen

Gültige Rückgabewerte liegen zwischen 1 und 12.

Informationen zu anderen Memberfunktionen, die `COleDateTime` den Wert dieses Objekts abfragen, finden Sie in den folgenden Memberfunktionen:

- [GetDay](#getday)

- [Getyear](#getyear)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

### <a name="example"></a>Beispiel

Siehe Beispiel für [GetDay](#getday).

## <a name="coledatetimegetsecond"></a><a name="getsecond"></a>COleDateTime::GetSecond

Ruft die Sekunde ab, die durch diesen Datums-/Uhrzeitwert dargestellt wird.

```
int GetSecond() const throw();
```

### <a name="return-value"></a>Rückgabewert

Die zweite, die durch `COleDateTime` den `COleDateTime::error` Wert dieses Objekts dargestellt wird, oder wenn das zweite Objekt nicht erhalten werden konnte.

### <a name="remarks"></a>Bemerkungen

Gültige Rückgabewerte liegen zwischen 0 und 59.

> [!NOTE]
> Die `COleDateTime` Klasse unterstützt keine Schaltsekunden.

Weitere Informationen zur Implementierung `COleDateTime`für finden Sie im Artikel [Datum und Uhrzeit: Automatisierungssupport](../../atl-mfc-shared/date-and-time-automation-support.md).

Informationen zu anderen Memberfunktionen, die `COleDateTime` den Wert dieses Objekts abfragen, finden Sie in den folgenden Memberfunktionen:

- [GetDay](#getday)

- [Getmonth](#getmonth)

- [Getyear](#getyear)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

### <a name="example"></a>Beispiel

Siehe Beispiel für [GetHour](#gethour).

## <a name="coledatetimegetstatus"></a><a name="getstatus"></a>COleDateTime::GetStatus

Ruft den Status (Gültigkeit) `COleDateTime` eines bestimmten Objekts ab.

```
DateTimeStatus GetStatus() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt den Status `COleDateTime` dieses Werts zurück. Wenn Sie `GetStatus` ein `COleDateTime` Objekt aufrufen, das mit dem Standarderstellt erstellt wurde, wird es gültig zurückgegeben. Wenn Sie `GetStatus` ein `COleDateTime` Objekt aufrufen, das mit dem `GetStatus` Konstruktor auf null initialisiert wurde, gibt null zurück.

### <a name="remarks"></a>Bemerkungen

Der Rückgabewert wird `DateTimeStatus` durch den aufgezählten Typ definiert, der innerhalb der `COleDateTime` Klasse definiert ist.

```
enum DateTimeStatus
{
   error = -1,
   valid = 0,
   invalid = 1,    // Invalid date (out of range, etc.)
   null = 2,       // Literally has no value
};
```

Eine kurze Beschreibung dieser Statuswerte finden Sie in der folgenden Liste:

- `COleDateTime::error`Gibt an, dass beim Versuch, einen Teil des Datums-/Uhrzeitwerts abzuholen, ein Fehler aufgetreten ist.

- `COleDateTime::valid`Gibt an, dass dieses `COleDateTime` Objekt gültig ist.

- `COleDateTime::invalid`Gibt an, dass dieses `COleDateTime` Objekt ungültig ist. das heißt, sein Wert kann falsch sein.

- `COleDateTime::null`Gibt an, dass dieses `COleDateTime` Objekt null ist, d. h., dass kein Wert für dieses Objekt angegeben wurde. (Dies ist "null" im Datenbanksinn "keinen Wert haben" im Gegensatz zum C++ NULL.)

Der Status `COleDateTime` eines Objekts ist in den folgenden Fällen ungültig:

- Wenn sein Wert von `VARIANT` `COleVariant` einem oder einem Wert festgelegt wird, der nicht in einen Datums-/Uhrzeitwert konvertiert werden konnte.

- Wenn der Wert von `time_t` `SYSTEMTIME`einem `FILETIME` , oder wert festgelegt wird, der nicht in einen gültigen Datums-/Uhrzeitwert konvertiert werden konnte.

- Wenn sein Wert `SetDateTime` mit ungültigen Parameterwerten festgelegt wird.

- Wenn dieses Objekt während eines arithmetischen Zuweisungsvorgangs einen `+=` Über- oder Unterlauf erlebt hat, nämlich, oder `-=`.

- Wenn diesem Objekt ein ungültiger Wert zugewiesen wurde.

- Wenn der Status dieses Objekts explizit `SetStatus`auf ungültig mit festgelegt wurde.

Weitere Informationen zu den Vorgängen, die den Status auf ungültig festlegen können, finden Sie in den folgenden Memberfunktionen:

- [Coledatetime](#coledatetime)

- [SetDateTime](#setdatetime)

- [Betreiber +, -](#operator_add_-)

- [Operator +=, -=](#operator_add_eq_-_eq)

Weitere Informationen zu den `COleDateTime` Grenzwerten für Werte finden Sie im Artikel [Datum und Uhrzeit: Automatisierungssupport](../../atl-mfc-shared/date-and-time-automation-support.md).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#10](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_12.cpp)]

## <a name="coledatetimegetyear"></a><a name="getyear"></a>COleDateTime::Jahr

Ruft das Jahr ab, das durch diesen Datums-/Uhrzeitwert dargestellt wird.

```
int GetYear() const throw();
```

### <a name="return-value"></a>Rückgabewert

Das Jahr, das durch `COleDateTime` den `COleDateTime::error` Wert dieses Objekts dargestellt wird oder wenn das Jahr nicht ermittelt werden konnte.

### <a name="remarks"></a>Bemerkungen

Gültige Rückgabewerte liegen zwischen 100 und 9999, einschließlich des Jahrhunderts.

Informationen zu anderen Memberfunktionen, die `COleDateTime` den Wert dieses Objekts abfragen, finden Sie in den folgenden Memberfunktionen:

- [GetDay](#getday)

- [Getmonth](#getmonth)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

Weitere Informationen zu den `COleDateTime` Grenzwerten für Werte finden Sie im Artikel [Datum und Uhrzeit: Automatisierungssupport](../../atl-mfc-shared/date-and-time-automation-support.md).

### <a name="example"></a>Beispiel

Siehe Beispiel für [GetDay](#getday).

## <a name="coledatetimem_dt"></a><a name="m_dt"></a>COleDateTime::m_dt

Die `DATE` zugrunde liegende `COleDateTime` Struktur für dieses Objekt.

```
DATE m_dt;
```

### <a name="remarks"></a>Bemerkungen

> [!CAUTION]
> Wenn Sie den `DATE` Wert in dem Objekt ändern, auf das `COleDateTime` der Zeiger von dieser Funktion zurückgreift, wird der Wert dieses Objekts geändert. Der Status dieses `COleDateTime` Objekts wird nicht geändert.

Weitere Informationen zur Implementierung `DATE` des Objekts finden Sie im Artikel [Datum und Uhrzeit: Automatisierungssupport](../../atl-mfc-shared/date-and-time-automation-support.md).

## <a name="coledatetimem_status"></a><a name="m_status"></a>COleDateTime::m_status

Enthält den Status `COleDateTime` dieses Objekts.

```
DateTimeStatus m_status;
```

### <a name="remarks"></a>Bemerkungen

Der Typ dieses Datenmembers ist der `DateTimeStatus`aufgezählte Typ `COleDateTime` , der innerhalb der Klasse definiert ist. Weitere Informationen finden Sie unter [COleDateTime::GetStatus](#getstatus).

> [!CAUTION]
> Dieser Datenmember ist für fortgeschrittene Programmiersituationen. Sie sollten die Inline-Memberfunktionen [GetStatus](#getstatus) und [SetStatus](#setstatus)verwenden. Weitere `SetStatus` Hinweise zur expliziten Einstellung dieses Datenmembers finden Sie unter .

## <a name="coledatetimeoperator-"></a><a name="operator_eq"></a>COleDateTime::Operator =

Kopiert `COleDateTime` einen Wert.

```
COleDateTime& operator=(const VARIANT& varSrc) throw();
COleDateTime& operator=(DATE dtSrc) throw();
COleDateTime& operator=(const time_t& timeSrc) throw();
COleDateTime& operator=(const __time64_t& timeSrc) throw();
COleDateTime& operator=(const SYSTEMTIME& systimeSrc) throw();
COleDateTime& operator=(const FILETIME& filetimeSrc) throw();
COleDateTime& operator=(const UDATE& uDate) throw();
```

### <a name="remarks"></a>Bemerkungen

Diese überladenen Zuweisungsoperatoren kopieren den `COleDateTime` Quelldatums-/Uhrzeitwert in dieses Objekt. Eine kurze Beschreibung der einzelnen überlasteten Zuweisungsoperatoren folgt:

- **Operator =(** `dateSrc` **)** Der Wert und der Status des `COleDateTime` Operanden werden in dieses Objekt kopiert.

- **Operator =(** *varSrc* **)** Wenn die Konvertierung des [VARIANT-Werts](/windows/win32/api/oaidl/ns-oaidl-variant) (oder [COleVariant-Objekts)](../../mfc/reference/colevariant-class.md) in ein Datum/Uhrzeit `COleDateTime` (VT_DATE) erfolgreich ist, wird der konvertierte Wert in dieses Objekt kopiert und sein Status auf gültig festgelegt. Wenn die Konvertierung nicht erfolgreich ist, wird der Wert dieses Objekts auf Null (30. Dezember 1899, Mitternacht) und sein Status auf ungültig gesetzt.

- **Operator =(** `dtSrc` **)** Der `DATE` Wert wird `COleDateTime` in dieses Objekt kopiert, und sein Status ist auf gültig festgelegt.

- **Operator =(** `timeSrc` **)** Der `time_t` `__time64_t` oder-Wert wird konvertiert `COleDateTime` und in dieses Objekt kopiert. Wenn die Konvertierung erfolgreich ist, wird der Status dieses Objekts auf gültig festgelegt. Wenn sie nicht erfolgreich ist, wird sie auf ungültig gesetzt.

- **Operator =(** *systimeSrc* **)** Der [SYSTEMTIME-Wert](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) wird konvertiert `COleDateTime` und in dieses Objekt kopiert. Wenn die Konvertierung erfolgreich ist, wird der Status dieses Objekts auf gültig festgelegt. Wenn sie nicht erfolgreich ist, wird sie auf ungültig gesetzt.

- **Operator =(** `uDate` **)** Der `UDATE` Wert wird konvertiert `COleDateTime` und in dieses Objekt kopiert. Wenn die Konvertierung erfolgreich ist, wird der Status dieses Objekts auf gültig festgelegt. Wenn sie nicht erfolgreich ist, wird sie auf ungültig gesetzt. Eine `UDATE` Struktur stellt ein "entpacktes" Datum dar. Weitere Informationen finden Sie in der Funktion [VarDateFromUdate](/windows/win32/api/oleauto/nf-oleauto-vardatefromudate).

- **Operator =(** `filetimeSrc` **)** Der [FILETIME-Wert](/windows/win32/api/minwinbase/ns-minwinbase-filetime) wird konvertiert `COleDateTime` und in dieses Objekt kopiert. Wenn die Konvertierung erfolgreich ist, wird der Status dieses Objekts auf gültig festgelegt. andernfalls wird sie auf ungültig gesetzt. `FILETIME`verwendet Universal Coordinated Time (UTC), also wenn Sie eine UTC-Zeit in der Struktur passieren, werden Ihre Ergebnisse von UTC-Zeit in lokale Zeit konvertiert und als Variantenzeit gespeichert. Dieses Verhalten ist das gleiche wie in Visual C++ 6.0 und Visual C++.NET 2003 SP2. Weitere Informationen finden Sie unter [Dateizeiten](/windows/win32/SysInfo/file-times) im Windows SDK.

Weitere Informationen finden Sie im [VARIANT-Eintrag](/windows/win32/api/oaidl/ns-oaidl-variant) im Windows SDK.

Weitere Informationen zum `time_t` Datentyp finden Sie in der [Zeitfunktion](../../c-runtime-library/reference/time-time32-time64.md) in der *Laufzeitbibliotheksreferenz*.

Weitere Informationen finden Sie in den Strukturen [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) und [FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime) im Windows SDK.

Weitere Informationen zu den `COleDateTime` Grenzwerten für Werte finden Sie im Artikel [Datum und Uhrzeit: Automatisierungssupport](../../atl-mfc-shared/date-and-time-automation-support.md).

## <a name="coledatetimeoperator---"></a><a name="operator_add_-"></a>COleDateTime::operator +, -

Hinzufügen und `ColeDateTime` Subtrahieren von Werten.

```
COleDateTime operator+(COleDateTimeSpan dateSpan) const throw();
COleDateTime operator-(COleDateTimeSpan dateSpan) const throw();
COleDateTimeSpan operator-(const COleDateTime& date) const throw();
```

### <a name="remarks"></a>Bemerkungen

`COleDateTime`Objekte stellen absolute Zeiten dar. [COleDateTimeSpan-Objekte](../../atl-mfc-shared/reference/coledatetimespan-class.md) stellen relative Zeiten dar. Mit den ersten beiden Operatoren können `COleDateTimeSpan` Sie `COleDateTime` einen Wert hinzufügen und von einem Wert subtrahieren. Mit dem dritten Operator können `COleDateTime` Sie einen Wert `COleDateTimeSpan` von einem anderen subtrahieren, um einen Wert zu erhalten.

Wenn einer der Operanden null ist, `COleDateTime` ist der Status des resultierenden Werts null.

Wenn der `COleDateTime` resultierende Wert außerhalb der Grenzen akzeptabler `COleDateTime` Werte liegt, ist der Status dieses Werts ungültig.

Wenn einer der Operanden ungültig und der andere nicht null `COleDateTime` ist, ist der Status des resultierenden Werts ungültig.

Die **+** **-** und-Operatoren `COleDateTime` bestätigen, wenn das Objekt auf null gesetzt ist. Ein Beispiel finden Sie unter [COleDateTime Relational Operators.](#coledatetime_relational_operators)

Weitere Informationen zu den gültigen, ungültigen und NULL-Statuswerten finden Sie in der m_status-Membervariablen. [m_status](#m_status)

Weitere Informationen zu den `COleDateTime` Grenzwerten für Werte finden Sie im Artikel [Datum und Uhrzeit: Automatisierungssupport](../../atl-mfc-shared/date-and-time-automation-support.md).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#12](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_13.cpp)]

## <a name="coledatetimeoperator---"></a><a name="operator_add_eq_-_eq"></a>COleDateTime::operator +=, -=

Fügen Sie einen `ColeDateTime` Wert `COleDateTime` von diesem Objekt hinzu und subtrahieren Sie ihn.

```
COleDateTime& operator+=(COleDateTimeSpan dateSpan) throw();
COleDateTime& operator-=(COleDateTimeSpan dateSpan) throw();
```

### <a name="remarks"></a>Bemerkungen

Mit diesen Operatoren können Sie `COleDateTimeSpan` einen Wert `COleDateTime`zu und von diesem hinzufügen und subtrahieren. Wenn einer der Operanden null ist, `COleDateTime` ist der Status des resultierenden Werts null.

Wenn der `COleDateTime` resultierende Wert außerhalb der Grenzen akzeptabler `COleDateTime` Werte liegt, wird der Status dieses Werts auf ungültig festgelegt.

Wenn einer der Operanden ungültig und ein anderer nicht null `COleDateTime` ist, ist der Status des resultierenden Werts ungültig.

Weitere Informationen zu den gültigen, ungültigen und NULL-Statuswerten finden Sie in der m_status-Membervariablen. [m_status](#m_status)

Die **+=** **-=** und-Operatoren `COleDateTime` bestätigen, wenn das Objekt auf null gesetzt ist. Ein Beispiel finden Sie unter [COleDateTime Relational Operators.](#coledatetime_relational_operators)

Weitere Informationen zu den `COleDateTime` Grenzwerten für Werte finden Sie im Artikel [Datum und Uhrzeit: Automatisierungssupport](../../atl-mfc-shared/date-and-time-automation-support.md).

## <a name="coledatetimeoperator-date"></a><a name="operator_date"></a>COleDateTime::operator DATE

Konvertiert einen `ColeDateTime` Wert `DATE`in eine .

```
operator DATE() const throw();
```

### <a name="remarks"></a>Bemerkungen

Dieser Operator `DATE` gibt ein Objekt zurück, dessen Wert aus diesem `COleDateTime` Objekt kopiert wird. Weitere Informationen zur Implementierung `DATE` des Objekts finden Sie im Artikel [Datum und Uhrzeit: Automatisierungssupport](../../atl-mfc-shared/date-and-time-automation-support.md).

Der `DATE` Operator bestätigt, `COleDateTime` ob das Objekt auf null gesetzt ist. Ein Beispiel finden Sie unter [COleDateTime Relational Operators.](#coledatetime_relational_operators)

## <a name="coledatetimeparsedatetime"></a><a name="parsedatetime"></a>COleDateTime::ParseDateTime

Analysiert eine Zeichenfolge, um einen Datums-/Uhrzeitwert zu lesen.

```
bool ParseDateTime(
    LPCTSTR lpszDate,
    DWORD dwFlags = 0,
    LCID lcid = LANG_USER_DEFAULT) throw();
```

### <a name="parameters"></a>Parameter

*lpszDate*<br/>
Ein Zeiger auf die null-terminierte Zeichenfolge, die analysiert werden soll. Einzelheiten finden Sie unter "Hinweise".

*dwFlags*<br/>
Gibt Flags für Gebietsschemaeinstellungen und Analyse an. Mindestens eine der folgenden Flags:

- LOCALE_NOUSEROVERRIDE Verwenden Sie die Standardgebietsschemaeinstellungen des Systems anstelle von benutzerdefinierten Benutzereinstellungen.

- VAR_TIMEVALUEONLY Ignorieren Sie den Datumsteil während der Analyse.

- VAR_DATEVALUEONLY Ignorieren Sie den Zeitabschnitt während der Analyse.

*Lcid*<br/>
Gibt die Gebietsschema-ID an, die für die Konvertierung verwendet werden soll.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE zurück, wenn die Zeichenfolge erfolgreich in einen Datums-/Uhrzeitwert konvertiert wurde, andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Wenn die Zeichenfolge erfolgreich in einen Datums-/Uhrzeitwert konvertiert wurde, wird der Wert dieses `COleDateTime` Objekts auf diesen Wert und dessen Status auf gültig festgelegt.

> [!NOTE]
> Die Jahreswerte müssen zwischen 100 und 9999 liegen, einschließlich.

Der Parameter *lpszDate* kann eine Vielzahl von Formaten annehmen. Die folgenden Zeichenfolgen enthalten beispielsweise akzeptable Datums-/Uhrzeitformate:

`"25 January 1996"`

`"8:30:00"`

`"20:30:00"`

`"January 25, 1996 8:30:00"`

`"8:30:00 Jan. 25, 1996"`

`"1/25/1996 8:30:00"  // always specify the full year, even in a 'short date' format`

Die Gebietsschema-ID wirkt sich auch darauf aus, ob das Zeichenfolgenformat für die Konvertierung in einen Datums-/Uhrzeitwert akzeptabel ist.

Bei VAR_DATEVALUEONLY wird der Zeitwert auf Zeit 0 oder Mitternacht festgelegt. Bei VAR_TIMEVALUEONLY wird der Datumswert auf das Datum 0, d. h. den 30. Dezember 1899, festgelegt.

Wenn die Zeichenfolge nicht in einen Datums-/Uhrzeitwert konvertiert werden konnte `COleDateTime` oder ein numerischer Überlauf vorlag, ist der Status dieses Objekts ungültig.

Weitere Informationen zu den Grenzwerten `COleDateTime` und der Implementierung für Werte finden Sie im Artikel [Datum und Uhrzeit: Automatisierungssupport](../../atl-mfc-shared/date-and-time-automation-support.md).

## <a name="coledatetimesetdate"></a><a name="setdate"></a>COleDateTime::SetDate

Legt das Datum `COleDateTime` dieses Objekts fest.

```
int SetDate(
    int nYear,
    int nMonth,
    int nDay) throw();
```

### <a name="parameters"></a>Parameter

*nJahr*, *nMonat*, *nDay*<br/>
Geben Sie die Datumskomponenten `COleDateTime` an, die in dieses Objekt kopiert werden sollen.

### <a name="return-value"></a>Rückgabewert

Null, wenn der `COleDateTime` Wert dieses Objekts erfolgreich festgelegt wurde; andernfalls 1. Dieser Rückgabewert basiert `DateTimeStatus` auf dem aufgezählten Typ. Weitere Informationen finden [SetStatus](#setstatus) Sie unter SetStatus-Memberfunktion.

### <a name="remarks"></a>Bemerkungen

Das Datum wird auf die angegebenen Werte festgelegt. Die Uhrzeit ist auf Zeit 0, Mitternacht eingestellt.

Siehe die folgende Tabelle für Grenzen für die Parameterwerte:

|Parameter|Begrenzungen|
|---------------|------------|
|*nJahr*|100 - 9999|
|*nMonat*|1 - 12|
|*nDay*|0 - 31|

Wenn der Tag des Monats überläuft, wird er in den richtigen Tag des nächsten Monats umgerechnet, und der Monat und/oder das Jahr wird entsprechend erhöht. Ein Tageswert von Null gibt den letzten Tag des Vormonats an. Das Verhalten ist `SystemTimeToVariantTime`das gleiche wie .

Wenn der von den Parametern angegebene Datumswert ungültig ist, wird der Status dieses Objekts auf `COleDateTime::invalid`festgelegt. Sie sollten [GetStatus](#getstatus) verwenden, um `DATE` die Gültigkeit des Werts zu überprüfen, und sie sollten nicht davon ausgehen, dass der Wert von [m_dt](#m_dt) unverändert bleibt.

Hier sind einige Beispiele für Datumswerte:

|*nJahr*|*nMonat*|*nDay*|Wert|
|-------------|--------------|------------|-----------|
|2000|2|29|29. Februar 2000|
|1776|7|4|4. Juli 1776|
|1925|4|35|35. April 1925 (ungültiges Datum)|
|10000|1|1|1. Januar 10000 (ungültiges Datum)|

Informationen zum Festlegen von Datum und Uhrzeit finden Sie unter [COleDateTime::SetDateTime](#setdatetime).

Informationen zu Memberfunktionen, die den `COleDateTime` Wert dieses Objekts abfragen, finden Sie in den folgenden Memberfunktionen:

- [GetDay](#getday)

- [Getmonth](#getmonth)

- [Getyear](#getyear)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

Weitere Informationen zu den `COleDateTime` Grenzwerten für Werte finden Sie im Artikel [Datum und Uhrzeit: Automatisierungssupport](../../atl-mfc-shared/date-and-time-automation-support.md).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#11](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_14.cpp)]

## <a name="coledatetimesetdatetime"></a><a name="setdatetime"></a>COleDateTime::SetDateTime

Legt das Datum und `COleDateTime` die Uhrzeit dieses Objekts fest.

```
int SetDateTime(
    int nYear,
    int nMonth,
    int nDay,
    int nHour,
    int nMin,
    int nSec) throw();
```

### <a name="parameters"></a>Parameter

*nJahr*, *nMonat*, *nDay*, *nHour*, *nMin*, *nSec*<br/>
Geben Sie die Datums- und `COleDateTime` Uhrzeitkomponenten an, die in dieses Objekt kopiert werden sollen.

### <a name="return-value"></a>Rückgabewert

Null, wenn der `COleDateTime` Wert dieses Objekts erfolgreich festgelegt wurde; andernfalls 1. Dieser Rückgabewert basiert `DateTimeStatus` auf dem aufgezählten Typ. Weitere Informationen finden [SetStatus](#setstatus) Sie unter SetStatus-Memberfunktion.

### <a name="remarks"></a>Bemerkungen

Siehe die folgende Tabelle für Grenzen für die Parameterwerte:

|Parameter|Begrenzungen|
|---------------|------------|
|*nJahr*|100 - 9999|
|*nMonat*|1 - 12|
|*nDay*|0 - 31|
|*nStunde*|0 - 23|
|*Nmin*|0 - 59|
|*Nsec*|0 - 59|

Wenn der Tag des Monats überläuft, wird er in den richtigen Tag des nächsten Monats umgerechnet, und der Monat und/oder das Jahr wird entsprechend erhöht. Ein Tageswert von Null gibt den letzten Tag des Vormonats an. Das Verhalten ist das gleiche wie [bei SystemTimeToVariantTime](/windows/win32/api/oleauto/nf-oleauto-systemtimetovarianttime).

Wenn der von den Parametern angegebene Datums- oder Uhrzeitwert ungültig ist, wird der Status dieses Objekts auf ungültig gesetzt, und der Wert dieses Objekts wird nicht geändert.

Hier sind einige Beispiele für Zeitwerte:

|*nStunde*|*Nmin*|*Nsec*|Wert|
|-------------|------------|------------|-----------|
|1|3|3|01:03:03|
|23|45|0|23:45:00|
|25|30|0|Ungültig|
|9|60|0|Ungültig|

Hier sind einige Beispiele für Datumswerte:

|*nJahr*|*nMonat*|*nDay*|Wert|
|-------------|--------------|------------|-----------|
|1995|4|15|15. April 1995|
|1789|7|14|17. Juli 1789|
|1925|2|30|Ungültig|
|10000|1|1|Ungültig|

Informationen zum Festlegen nur des Datums finden Sie unter [COleDateTime::SetDate](#setdate). Informationen zum Festlegen nur der Uhrzeit finden Sie unter [COleDateTime::SetTime](#settime).

Informationen zu Memberfunktionen, die den `COleDateTime` Wert dieses Objekts abfragen, finden Sie in den folgenden Memberfunktionen:

- [GetDay](#getday)

- [Getmonth](#getmonth)

- [Getyear](#getyear)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

Weitere Informationen zu den `COleDateTime` Grenzwerten für Werte finden Sie im Artikel [Datum und Uhrzeit: Automatisierungssupport](../../atl-mfc-shared/date-and-time-automation-support.md).

### <a name="example"></a>Beispiel

Siehe Beispiel für [GetStatus](#getstatus).

## <a name="coledatetimesetstatus"></a><a name="setstatus"></a>COleDateTime::SetStatus

Legt den Status `COleDateTime` dieses Objekts fest.

```cpp
void SetStatus(DateTimeStatus status) throw();
```

### <a name="parameters"></a>Parameter

*status*<br/>
Der neue Statuswert `COleDateTime` für dieses Objekt.

### <a name="remarks"></a>Bemerkungen

Der *Statusparameterwert* wird `DateTimeStatus` durch den aufgezählten Typ definiert, der innerhalb der `COleDateTime` Klasse definiert ist. Weitere Informationen finden Sie unter [COleDateTime::GetStatus.](#getstatus)

> [!CAUTION]
> Diese Funktion ist für fortgeschrittene Programmiersituationen. Diese Funktion ändert die Daten in diesem Objekt nicht. Es wird am häufigsten verwendet, um den Status auf **null** oder **ungültig**festzulegen. Der Zuweisungsoperator ([operator =](#operator_eq)) und [SetDateTime](#setdatetime) legen den Status des Objekts basierend auf dem Quellwert(n) fest.

### <a name="example"></a>Beispiel

Siehe Beispiel für [GetStatus](#getstatus).

## <a name="coledatetimesettime"></a><a name="settime"></a>COleDateTime::SetTime

Legt die Zeit `COleDateTime` dieses Objekts fest.

```
int SetTime(
    int nHour,
    int nMin,
    int nSec) throw();
```

### <a name="parameters"></a>Parameter

*nHour*, *nMin*, *nSec*<br/>
Geben Sie die Zeitkomponenten `COleDateTime` an, die in dieses Objekt kopiert werden sollen.

### <a name="return-value"></a>Rückgabewert

Null, wenn der `COleDateTime` Wert dieses Objekts erfolgreich festgelegt wurde; andernfalls 1. Dieser Rückgabewert basiert `DateTimeStatus` auf dem aufgezählten Typ. Weitere Informationen finden [SetStatus](#setstatus) Sie unter SetStatus-Memberfunktion.

### <a name="remarks"></a>Bemerkungen

Die Zeit wird auf die angegebenen Werte festgelegt. Das Datum wird auf das Datum 0 festgelegt, was den 30. Dezember 1899 bedeutet.

Siehe die folgende Tabelle für Grenzen für die Parameterwerte:

|Parameter|Begrenzungen|
|---------------|------------|
|*nStunde*|0 - 23|
|*Nmin*|0 - 59|
|*Nsec*|0 - 59|

Wenn der von den Parametern angegebene Zeitwert ungültig ist, wird der Status dieses Objekts auf ungültig gesetzt, und der Wert dieses Objekts wird nicht geändert.

Hier sind einige Beispiele für Zeitwerte:

|*nStunde*|*Nmin*|*Nsec*|Wert|
|-------------|------------|------------|-----------|
|1|3|3|01:03:03|
|23|45|0|23:45:00|
|25|30|0|Ungültig|
|9|60|0|Ungültig|

Informationen zum Festlegen von Datum und Uhrzeit finden Sie unter [COleDateTime::SetDateTime](#setdatetime).

Informationen zu Memberfunktionen, die den `COleDateTime` Wert dieses Objekts abfragen, finden Sie in den folgenden Memberfunktionen:

- [GetDay](#getday)

- [Getmonth](#getmonth)

- [Getyear](#getyear)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

Weitere Informationen zu den `COleDateTime` Grenzwerten für Werte finden Sie im Artikel [Datum und Uhrzeit: Automatisierungssupport](../../atl-mfc-shared/date-and-time-automation-support.md).

### <a name="example"></a>Beispiel

Siehe Beispiel für [SetDate](#setdate).

## <a name="see-also"></a>Weitere Informationen

[COleVariant-Klasse](../../mfc/reference/colevariant-class.md)<br/>
[CTime-Klasse](../../atl-mfc-shared/reference/ctime-class.md)<br/>
[CTimeSpan-Klasse](../../atl-mfc-shared/reference/ctimespan-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[FREIGEGEBENe ATL/MFC-Klassen](../../atl-mfc-shared/atl-mfc-shared-classes.md)
