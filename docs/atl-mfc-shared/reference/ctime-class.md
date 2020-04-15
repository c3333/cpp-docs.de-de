---
title: CTime-Klasse
ms.date: 10/18/2018
f1_keywords:
- ATLTIME/ATL::CTime
- ATLTIME/ATL::CTime::CTime
- ATLTIME/ATL::CTime::Format
- ATLTIME/ATL::CTime::FormatGmt
- ATLTIME/ATL::CTime::GetAsDBTIMESTAMP
- ATLTIME/ATL::CTime::GetAsSystemTime
- ATLTIME/ATL::CTime::GetCurrentTime
- ATLTIME/ATL::CTime::GetDay
- ATLTIME/ATL::CTime::GetDayOfWeek
- ATLTIME/ATL::CTime::GetGmtTm
- ATLTIME/ATL::CTime::GetHour
- ATLTIME/ATL::CTime::GetLocalTm
- ATLTIME/ATL::CTime::GetMinute
- ATLTIME/ATL::CTime::GetMonth
- ATLTIME/ATL::CTime::GetSecond
- ATLTIME/ATL::CTime::GetTime
- ATLTIME/ATL::CTime::GetYear
- ATLTIME/ATL::CTime::Serialize64
helpviewer_keywords:
- CTime class
- shared classes, CTime
ms.assetid: 0a299544-485b-48dc-9d3c-fdc30f57d612
ms.openlocfilehash: e6e471fe648c5fa370cce750e8569e158eb1ffe4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317571"
---
# <a name="ctime-class"></a>CTime-Klasse

Stellt eine absolute Uhrzeit und ein absolutes Datum dar.

## <a name="syntax"></a>Syntax

```
class CTime
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CTime::CTime](#ctime)|Erstellt `CTime` Objekte auf verschiedene Weise.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CTime::Format](#format)|Konvertiert ein `CTime` Objekt in eine formatierte Zeichenfolge – basierend auf der lokalen Zeitzone.|
|[CTime::FormatGmt](#formatgmt)|Konvertiert ein `CTime` Objekt in eine formatierte Zeichenfolge – basierend auf UTC.|
|[CTime::GetAsDBTIMESTAMP](#getasdbtimestamp)|Konvertiert die im `CTime` Objekt gespeicherten Zeitinformationen in eine Win32-kompatible DBTIMESTAMP-Struktur.|
|[CTime::GetAsSystemTime](#getassystemtime)|Konvertiert die im `CTime` Objekt gespeicherten Zeitinformationen in eine Win32-kompatible [SYSTEMTIME-Struktur.](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)|
|[CTime::GetCurrentTime](#getcurrenttime)|Erstellt `CTime` ein Objekt, das die aktuelle Uhrzeit darstellt (statische Memberfunktion).|
|[CTime::GetDay](#getday)|Gibt die Tagesdarstellung `CTime` durch das Objekt zurück.|
|[CTime::GetDayOfWeek](#getdayofweek)|Gibt den Wochentag zurück, `CTime` der durch das Objekt dargestellt wird.|
|[CTime::GetGmtTm](#getgmttm)|Unterteilt ein `CTime` Objekt in Komponenten – basierend auf UTC.|
|[CTime::GetHour](#gethour)|Gibt die vom `CTime` Objekt dargestellte Stunde zurück.|
|[CTime::GetLocalTm](#getlocaltm)|Unterteilt ein `CTime` Objekt in Komponenten – basierend auf der lokalen Zeitzone.|
|[CTime::GetMinute](#getminute)|Gibt die minute `CTime` zurück, die durch das Objekt dargestellt wird.|
|[CTime::GetMonth](#getmonth)|Gibt den durch `CTime` das Objekt dargestellten Monat zurück.|
|[CTime::GetSecond](#getsecond)|Gibt die zweite, `CTime` die durch das Objekt dargestellt wird.|
|[CTime::GetTime](#gettime)|Gibt einen **__time64_t** Wert `CTime` für das angegebene Objekt zurück.|
|[CTime::GetYear](#getyear)|Gibt das durch `CTime` das Objekt dargestellte Jahr zurück.|
|[CTime::Serialize64](#serialize64)|Serialisiert Daten in oder aus einem Archiv.|

### <a name="operators"></a>Operatoren

|||
|-|-|
|[Betreiber + -](#operator_add_-)|Diese Operatoren fügen `CTimeSpan` `CTime` und subtrahieren und Objekte.|
|[Operator +=, -=](#operator_add_eq_-_eq)|Diese Operatoren fügen `CTimeSpan` ein Objekt zu `CTime` und von diesem Objekt hinzu und subtrahieren es.|
|[Operator =](#operator_eq)|Der Zuweisungsoperator.|
|[Operator ==, < usw.](#ctime_comparison_operators)|Vergleichsoperatoren.|

## <a name="remarks"></a>Bemerkungen

`CTime`hat keine Basisklasse.

`CTime`Die Werte basieren auf der koordinierten Universalzeit (UTC), die der koordinierten Weltzeit entspricht (Greenwich Mean Time, GMT). Weitere Informationen zur Bestimmten Zeitzone finden Sie unter [Zeitverwaltung.](../../c-runtime-library/time-management.md)

Wenn Sie `CTime` ein Objekt `nDST` erstellen, legen Sie den Parameter auf 0 fest, um anzugeben, dass die Standardzeit wirksam ist, oder auf einen Wert größer als 0, um anzugeben, dass die Sommerzeit in Kraft ist, oder auf einen Wert kleiner als Null, damit der C-Laufzeitbibliothekscode berechnet, ob standardzeit- oder Sommerzeitzeit ist. `tm_isdst` ist ein Pflichtfeld. Wenn nicht festgelegt, ist sein Wert nicht definiert, und der Rückgabewert von [mktime](../../c-runtime-library/reference/mktime-mktime32-mktime64.md) ist unvorhersehbar. Wenn `timeptr` auf eine tm-Struktur verweist, die von einem vorherigen `tm_isdst` Aufruf von [asctime_s](../../c-runtime-library/reference/asctime-s-wasctime-s.md), [_gmtime_s](../../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)oder [localtime_s](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md)zurückgegeben wird, enthält das Feld den richtigen Wert.

Eine Begleitklasse, [CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md), stellt ein Zeitintervall dar.

Die `CTime` `CTimeSpan` und-Klassen sind nicht für die Ableitung ausgelegt. Da es keine virtuellen Funktionen `CTime` gibt, beträgt die Größe und `CTimeSpan` der Objekte genau 8 Byte. Die meisten Memberfunktionen sind inline.

> [!NOTE]
> Die obere Datumsgrenze ist der 31.12.3000. Die untere Grenze ist 1/1/1970 12:00:00 UHR GMT.

Weitere Informationen zur `CTime`Verwendung finden Sie in den Artikeln [Datum und Uhrzeit](../../atl-mfc-shared/date-and-time.md)und [Zeitverwaltung](../../c-runtime-library/time-management.md) in der Laufzeitbibliotheksreferenz.

> [!NOTE]
> Die `CTime` Struktur wurde von MFC 7.1 auf MFC 8.0 geändert. Wenn Sie eine `CTime` Struktur mit dem **Operator <<** unter MFC 8.0 oder einer späteren Version serialisieren, kann die resultierende Datei auf älteren MFC-Versionen nicht lesbar sein.

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atltime.h

## <a name="ctime-comparison-operators"></a><a name="ctime_comparison_operators"></a>CTime-Vergleichsoperatoren

Vergleichsoperatoren.

```
bool operator==(CTime time) const throw();
bool operator!=(CTime time) const throw();
bool operator<(CTime time) const throw();
bool operator>(CTime time) const throw();
bool operator<=(CTime time) const throw();
bool operator>=(CTime time) const throw();
```

### <a name="parameters"></a>Parameter

*time*<br/>
Das zu vergleichende `CTime`-Objekt.

### <a name="return-value"></a>Rückgabewert

Diese Operatoren vergleichen zwei absolute Zeiten und geben TRUE zurück, wenn die Bedingung wahr ist. andernfalls FALSE.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#161](../../atl-mfc-shared/codesnippet/cpp/ctime-class_1.cpp)]

## <a name="ctimectime"></a><a name="ctime"></a>CTime::CTime

Erstellt ein `CTime` neues Objekt, das mit der angegebenen Zeit initialisiert wurde.

```
CTime() throw();
CTime(__time64_t time) throw();
CTime(int nYear, int nMonth, int nDay,
      int nHour, int nMin, int nSec, int nDST = -1);
CTime(WORD wDosDate, WORD wDosTime, int nDST = -1);
CTime(const SYSTEMTIME& st, int nDST = - 1) throw();
CTime(const FILETIME& ft, int nDST = - 1);
CTime(const DBTIMESTAMP& dbts, int nDST = -1) throw();
```

### <a name="parameters"></a>Parameter

*timeSrc*<br/>
Gibt `CTime` ein Objekt an, das bereits vorhanden ist.

*time*<br/>
Ein `__time64_t` Zeitwert, der die Anzahl der Sekunden nach dem 1. Januar 1970 UTC ist. Beachten Sie, dass dies an Ihre Ortszeit angepasst wird. Wenn Sie sich beispielsweise in New `CTime` York befinden und ein Objekt erstellen, indem Sie den Parameter 0 übergeben, gibt [CTime::GetMonth](#getmonth) 12 zurück.

*nJahr*, *nMonat*, *nDay*, *nHour*, *nMin*, *nSec*<br/>
Gibt die Datums- und Uhrzeitwerte an, die in das neue `CTime` Objekt kopiert werden sollen.

*nDST*<br/>
Gibt an, ob Sommerzeit in Kraft ist. Kann einen von drei Werten haben:

- *nDST* auf 0Standardzeit eingestellt ist.

- *nDST* auf einen Wert größer als 0Sommerzeit eingestellt ist.

- *nDST* auf einen Wert kleiner als 0Der Standardwert festgelegt. Berechnet automatisch, ob Standardzeit oder Sommerzeit in Kraft ist.

*wDosDate*, *wDosTime*<br/>
MS-DOS-Datums- und -Uhrzeitwerte, die in einen `CTime` Datums-/Uhrzeitwert konvertiert und in das neue Objekt kopiert werden sollen.

*St*<br/>
Eine [SYSTEMTIME-Struktur,](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) die in einen Datums-/Uhrzeitwert konvertiert und in das neue `CTime` Objekt kopiert werden soll.

*Ft*<br/>
Eine [FILETIME-Struktur,](/windows/win32/api/minwinbase/ns-minwinbase-filetime) die in einen Datums-/Uhrzeitwert konvertiert und in das neue `CTime` Objekt kopiert werden soll.

*Dbts*<br/>
Ein Verweis auf eine DBTIMESTAMP-Struktur, die die aktuelle Ortszeit enthält.

### <a name="remarks"></a>Bemerkungen

Jeder Konstruktor wird unten beschrieben:

- `CTime();`Erstellt ein nicht `CTime` initialisiertes Objekt. Mit diesem Konstruktor `CTime` können Sie Objektarrays definieren. Sie sollten solche Arrays vor der Verwendung mit gültigen Zeiten initialisieren.

- `CTime( const CTime& );`Erstellt ein `CTime` Objekt `CTime` aus einem anderen Wert.

- `CTime( __time64_t );`Erstellt ein `CTime` Objekt aus einem **__time64_t** Typ. Dieser Konstruktor erwartet eine UTC-Zeit und konvertiert das Ergebnis in eine lokale Zeit, bevor das Ergebnis gespeichert wird.

- `CTime( int, int, ...);`Erstellt ein `CTime` Objekt aus lokalen Zeitkomponenten, wobei jede Komponente auf die folgenden Bereiche beschränkt ist:

   |Komponente|Bereich|
   |---------------|-----------|
   |*nJahr*|1970-3000|
   |*nMonat*|1-12|
   |*nDay*|1-31|
   |*nStunde*|0-23|
   |*Nmin*|0-59|
   |*Nsec*|0-59|

   Dieser Konstruktor führt die entsprechende Konvertierung in UTC durch. Die Debugversion der Microsoft Foundation-Klassenbibliothek bestätigt, ob eine oder mehrere Zeitkomponenten anicht in Reichweite liegen. Sie müssen die Argumente vor dem Aufruf überprüfen. Dieser Konstruktor erwartet eine lokale Zeit.

- `CTime( WORD, WORD );`Erstellt ein `CTime` Objekt aus den angegebenen MS-DOS-Datums- und -Uhrzeitwerten. Dieser Konstruktor erwartet eine lokale Zeit.

- `CTime( const SYSTEMTIME& );`Erstellt ein `CTime` Objekt `SYSTEMTIME` aus einer Struktur. Dieser Konstruktor erwartet eine lokale Zeit.

- `CTime( const FILETIME& );`Erstellt ein `CTime` Objekt `FILETIME` aus einer Struktur. Sie werden die `CTime FILETIME` Initialisierung höchstwahrscheinlich nicht direkt verwenden. Wenn Sie `CFile` ein Objekt zum `CFile::GetStatus` Bearbeiten einer Datei verwenden, ruft `CTime` der Zeitstempel `FILETIME` der Datei für Sie über ein Objekt ab, das mit einer Struktur initialisiert wurde. Dieser Konstruktor geht von einer auf UTC basierenden Zeit aus und konvertiert den Wert automatisch in lokale Zeit, bevor das Ergebnis gespeichert wird.

   > [!NOTE]
   > Der Konstruktor, `DBTIMESTAMP` der Parameter verwendet, ist nur verfügbar, wenn OLEDB.h enthalten ist.

Weitere Informationen finden Sie in der [Struktur SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) und [FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime) im Windows SDK. Siehe auch den [MS-DOS-Datums- und -Uhrzeiteintrag](/windows/win32/SysInfo/ms-dos-date-and-time) im Windows SDK.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#148](../../atl-mfc-shared/codesnippet/cpp/ctime-class_2.cpp)]

## <a name="ctimeformat"></a><a name="format"></a>CTime::Format

Rufen Sie diese Memberfunktion auf, um eine formatierte Darstellung des Datums-/Uhrzeitwerts zu erstellen.

```
CString Format(LPCTSTR pszFormat) const;
CString Format(UINT nFormatID) const;
```

### <a name="parameters"></a>Parameter

*pszFormat*<br/>
Eine Formatierungszeichenfolge, die der `printf` Formatierungszeichenfolge ähnelt. Formatierungscodes, denen`%`ein Prozentzeichen ( ) `CTime` vorangestellt ist, werden durch die entsprechende Komponente ersetzt. Andere Zeichen in der Formatierungszeichenfolge werden unverändert in die zurückgegebene Zeichenfolge kopiert. Eine Liste der Formatierungscodes finden Sie in der Laufzeitfunktion [strftime.](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)

*nFormatID*<br/>
Die ID der Zeichenfolge, die dieses Format identifiziert.

### <a name="return-value"></a>Rückgabewert

Ein [CString,](../../atl-mfc-shared/reference/cstringt-class.md) der die formatierte Zeit enthält.

### <a name="remarks"></a>Bemerkungen

Wenn der Status `CTime` dieses Objekts null ist, ist der Rückgabewert eine leere Zeichenfolge.

Diese Methode löst eine Ausnahme aus, wenn der Datums-/Uhrzeitwert für das Format nicht zwischen Mitternacht, 1. Januar 1970 und 31. Dezember 3000 Universal Coordinated Time (UTC) reicht.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#149](../../atl-mfc-shared/codesnippet/cpp/ctime-class_3.cpp)]

## <a name="ctimeformatgmt"></a><a name="formatgmt"></a>CTime::FormatGmt

Generiert eine formatierte Zeichenfolge, `CTime` die diesem Objekt entspricht.

```
CString FormatGmt(LPCTSTR pszFormat) const;
CString FormatGmt(UINT nFormatID) const;
```

### <a name="parameters"></a>Parameter

*pszFormat*<br/>
Gibt eine Formatierungszeichenfolge `printf` an, die der Formatierungszeichenfolge ähnelt. Weitere Informationen finden Sie in der Laufzeitfunktion [strftime.](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)

*nFormatID*<br/>
Die ID der Zeichenfolge, die dieses Format identifiziert.

### <a name="return-value"></a>Rückgabewert

Ein [CString,](../../atl-mfc-shared/reference/cstringt-class.md) der die formatierte Zeit enthält.

### <a name="remarks"></a>Bemerkungen

Der Zeitwert wird nicht konvertiert und spiegelt somit UTC wider.

Diese Methode löst eine Ausnahme aus, wenn der Datums-/Uhrzeitwert für das Format nicht zwischen Mitternacht, 1. Januar 1970 und 31. Dezember 3000 Universal Coordinated Time (UTC) reicht.

### <a name="example"></a>Beispiel

Siehe Beispiel für [CTime::Format](#format).

## <a name="ctimegetasdbtimestamp"></a><a name="getasdbtimestamp"></a>CTime::GetAsDBTIMESTAMP

Rufen Sie diese Memberfunktion auf, `CTime` um die im Objekt gespeicherten Zeitinformationen in eine Win32-kompatible DBTIMESTAMP-Struktur zu konvertieren.

```
bool GetAsDBTIMESTAMP(DBTIMESTAMP& dbts) const throw();
```

### <a name="parameters"></a>Parameter

*Dbts*<br/>
Ein Verweis auf eine DBTIMESTAMP-Struktur, die die aktuelle Ortszeit enthält.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Speichert die resultierende Zeit in der referenzierten *dbts-Struktur.* Für `DBTIMESTAMP` die von dieser Funktion initialisierte Datenstruktur wird der `fraction` Member auf Null gesetzt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#150](../../atl-mfc-shared/codesnippet/cpp/ctime-class_4.cpp)]

## <a name="ctimegetassystemtime"></a><a name="getassystemtime"></a>CTime::GetAsSystemTime

Rufen Sie diese Memberfunktion auf, `CTime` um die im Objekt gespeicherten Zeitinformationen in eine Win32-kompatible [SYSTEMTIME-Struktur](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) zu konvertieren.

```
bool GetAsSystemTime(SYSTEMTIME& st) const throw();
```

### <a name="parameters"></a>Parameter

*timeDest*<br/>
Ein Verweis auf eine [SYSTEMTIME-Struktur,](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) die den `CTime` konvertierten Datums-/Uhrzeitwert des Objekts enthält.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn erfolgreich, andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

`GetAsSystemTime`speichert die resultierende Zeit in der referenzierten *timeDest-Struktur.* Für `SYSTEMTIME` die von dieser Funktion initialisierte Datenstruktur wird der `wMilliseconds` Member auf Null gesetzt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#151](../../atl-mfc-shared/codesnippet/cpp/ctime-class_5.cpp)]

## <a name="ctimegetcurrenttime"></a><a name="getcurrenttime"></a>CTime::GetCurrentTime

Gibt `CTime` ein Objekt zurück, das die aktuelle Uhrzeit darstellt.

```
static CTime WINAPI GetCurrentTime() throw();
```

### <a name="remarks"></a>Bemerkungen

Gibt das aktuelle Systemdatum und die aktuelle Systemzeit in Koordinierte Weltzeit (UTC) zurück.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#152](../../atl-mfc-shared/codesnippet/cpp/ctime-class_6.cpp)]

## <a name="ctimegetday"></a><a name="getday"></a>CTime::GetDay

Gibt die Tagesdarstellung `CTime` durch das Objekt zurück.

```
int GetDay() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt den Tag des Monats basierend auf der Ortszeit im Bereich 1 bis 31 zurück.

### <a name="remarks"></a>Bemerkungen

Diese Funktion `GetLocalTm`ruft auf, die einen internen, statisch zugewiesenen Puffer verwendet. Die Daten in diesem Puffer werden aufgrund `CTime` von Aufrufen anderer Memberfunktionen überschrieben.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#153](../../atl-mfc-shared/codesnippet/cpp/ctime-class_7.cpp)]

## <a name="ctimegetdayofweek"></a><a name="getdayofweek"></a>CTime::GetDayOfWeek

Gibt den Wochentag zurück, `CTime` der durch das Objekt dargestellt wird.

```
int GetDayOfWeek() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt den Wochentag basierend auf ortszeit zurück; 1 = Sonntag, 2 = Montag, bis 7 = Samstag.

### <a name="remarks"></a>Bemerkungen

Diese Funktion `GetLocalTm`ruft auf, die einen internen statisch zugewiesenen Puffer verwendet. Die Daten in diesem Puffer werden aufgrund `CTime` von Aufrufen anderer Memberfunktionen überschrieben.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#154](../../atl-mfc-shared/codesnippet/cpp/ctime-class_8.cpp)]

## <a name="ctimegetgmttm"></a><a name="getgmttm"></a>CTime::GetGmtTm

Ruft eine **struktur tm ab,** die eine `CTime` Zerlegung der in diesem Objekt enthaltenen Zeit enthält.

```
struct tm* GetGmtTm(struct tm* ptm) const;
```

### <a name="parameters"></a>Parameter

*Ptm*<br/>
Verweist auf einen Puffer, der die Zeitdaten empfängt. Wenn dieser Zeiger NULL ist, wird eine Ausnahme ausgelöst.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf eine ausgefüllte **Struktur tm,** wie in der Includedatei TIME definiert. H. Siehe [gmtime, _gmtime32, _gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md) für das Strukturlayout.

### <a name="remarks"></a>Bemerkungen

`GetGmtTm`gibt UTC zurück.

*ptm* kann nicht NULL sein. Wenn Sie zum alten Verhalten zurückkehren möchten, bei dem *ptm* NULL sein könnte, um anzugeben, dass ein interner, statisch zugewiesener Puffer verwendet werden soll, wird _SECURE_ATL.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#155](../../atl-mfc-shared/codesnippet/cpp/ctime-class_9.cpp)]

## <a name="ctimegethour"></a><a name="gethour"></a>CTime::GetHour

Gibt die vom `CTime` Objekt dargestellte Stunde zurück.

```
int GetHour() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt die Stunde basierend auf der Ortszeit im Bereich 0 bis 23 zurück.

### <a name="remarks"></a>Bemerkungen

Diese Funktion `GetLocalTm`ruft auf, die einen internen statisch zugewiesenen Puffer verwendet. Die Daten in diesem Puffer werden aufgrund `CTime` von Aufrufen anderer Memberfunktionen überschrieben.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#156](../../atl-mfc-shared/codesnippet/cpp/ctime-class_10.cpp)]

## <a name="ctimegetlocaltm"></a><a name="getlocaltm"></a>CTime::GetLocalTm

Ruft eine **Struktur tm ab,** die eine `CTime` Zerlegung der in diesem Objekt enthaltenen Zeit enthält.

```
struct tm* GetLocalTm(struct tm* ptm) const;
```

### <a name="parameters"></a>Parameter

*Ptm*<br/>
Verweist auf einen Puffer, der die Zeitdaten empfängt. Wenn dieser Zeiger NULL ist, wird eine Ausnahme ausgelöst.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf eine ausgefüllte **Struktur tm,** wie in der Includedatei TIME definiert. H. Siehe [gmtime, _gmtime32, _gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md) für das Strukturlayout.

### <a name="remarks"></a>Bemerkungen

`GetLocalTm`gibt Ortszeit zurück.

*ptm* kann nicht NULL sein. Wenn Sie zum alten Verhalten zurückkehren möchten, bei dem *ptm* NULL sein könnte, um anzugeben, dass ein interner, statisch zugewiesener Puffer verwendet werden soll, wird _SECURE_ATL.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#157](../../atl-mfc-shared/codesnippet/cpp/ctime-class_11.cpp)]

## <a name="ctimegetminute"></a><a name="getminute"></a>CTime::GetMinute

Gibt die minute `CTime` zurück, die durch das Objekt dargestellt wird.

```
int GetMinute() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt die Minute basierend auf der Ortszeit im Bereich 0 bis 59 zurück.

### <a name="remarks"></a>Bemerkungen

Diese Funktion `GetLocalTm`ruft auf, die einen internen statisch zugewiesenen Puffer verwendet. Die Daten in diesem Puffer werden aufgrund `CTime` von Aufrufen anderer Memberfunktionen überschrieben.

### <a name="example"></a>Beispiel

Siehe Beispiel für [GetHour](#gethour).

## <a name="ctimegetmonth"></a><a name="getmonth"></a>CTime::GetMonth

Gibt den durch `CTime` das Objekt dargestellten Monat zurück.

```
int GetMonth() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt den Monat basierend auf der Ortszeit im Bereich 1 bis 12 (1 = Januar) zurück.

### <a name="remarks"></a>Bemerkungen

Diese Funktion `GetLocalTm`ruft auf, die einen internen statisch zugewiesenen Puffer verwendet. Die Daten in diesem Puffer werden aufgrund `CTime` von Aufrufen anderer Memberfunktionen überschrieben.

### <a name="example"></a>Beispiel

Siehe Beispiel für [GetDay](#getday).

## <a name="ctimegetsecond"></a><a name="getsecond"></a>CTime::GetSecond

Gibt die zweite, `CTime` die durch das Objekt dargestellt wird.

```
int GetSecond() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt die zweite, basierend auf der Ortszeit, im Bereich 0 bis 59 zurück.

### <a name="remarks"></a>Bemerkungen

Diese Funktion `GetLocalTm`ruft auf, die einen internen statisch zugewiesenen Puffer verwendet. Die Daten in diesem Puffer werden aufgrund `CTime` von Aufrufen anderer Memberfunktionen überschrieben.

### <a name="example"></a>Beispiel

Siehe Beispiel für [GetHour](#gethour).

## <a name="ctimegettime"></a><a name="gettime"></a>CTime::GetTime

Gibt einen **__time64_t** Wert `CTime` für das angegebene Objekt zurück.

```
__time64_t GetTime() const throw();
```

### <a name="return-value"></a>Rückgabewert

`GetTime`gibt die Anzahl der Sekunden `CTime` zwischen dem aktuellen Objekt und dem 1. Januar 1970 zurück.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#158](../../atl-mfc-shared/codesnippet/cpp/ctime-class_12.cpp)]

## <a name="ctimegetyear"></a><a name="getyear"></a>CTime::GetYear

Gibt das durch `CTime` das Objekt dargestellte Jahr zurück.

```
int GetYear();
```

### <a name="return-value"></a>Rückgabewert

Gibt das Jahr basierend auf der Ortszeit im Bereich vom 1. Januar 1970 bis zum 18. Januar 2038 (inklusive) zurück.

### <a name="remarks"></a>Bemerkungen

Diese Funktion `GetLocalTm`ruft auf, die einen internen statisch zugewiesenen Puffer verwendet. Die Daten in diesem Puffer werden aufgrund `CTime` von Aufrufen anderer Memberfunktionen überschrieben.

### <a name="example"></a>Beispiel

Siehe Beispiel für [GetDay](#getday).

## <a name="ctimeoperator-"></a><a name="operator_eq"></a>CTime::Operator =

Der Zuweisungsoperator.

```
CTime& operator=(__time64_t time) throw();
```

### <a name="parameters"></a>Parameter

*time*<br/>
Der neue Datums-/Uhrzeitwert.

### <a name="return-value"></a>Rückgabewert

Das `CTime` aktualisierte Objekt.

### <a name="remarks"></a>Bemerkungen

Dieser überladene Zuweisungsoperator kopiert `CTime` die Quellzeit in dieses Objekt. Der interne Zeitspeicher `CTime` in einem Objekt ist unabhängig von der Zeitzone. Eine Zeitzonenkonvertierung ist während der Zuweisung nicht erforderlich.

## <a name="ctimeoperator---"></a><a name="operator_add_-"></a>CTime::Operator +, -

Diese Operatoren fügen `CTimeSpan` `CTime` und subtrahieren und Objekte.

```
CTime operator+(CTimeSpan timeSpan) const throw();
CTime operator-(CTimeSpan timeSpan) const throw();
CTimeSpan operator-(CTime time) const throw();
```

### <a name="parameters"></a>Parameter

*Timespan*<br/>
Das `CTimeSpan` zu addierende oder subtrahierende Objekt.

*time*<br/>
Das `CTime` zu subtrahierende Objekt.

### <a name="return-value"></a>Rückgabewert

Ein `CTime` `CTimeSpan` oder Objekt, das das Ergebnis des Vorgangs darstellt.

### <a name="remarks"></a>Bemerkungen

`CTime`Objekte stellen die `CTimeSpan` absolute Zeit dar, Objekte die relative Zeit. Mit den ersten beiden Operatoren `CTimeSpan` können Sie `CTime` Objekte zu und von Objekten hinzufügen und subtrahieren. Mit dem dritten Operator können `CTime` Sie ein Objekt `CTimeSpan` von einem anderen subtrahieren, um ein Objekt zu erhalten.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#159](../../atl-mfc-shared/codesnippet/cpp/ctime-class_13.cpp)]

## <a name="ctimeoperator---"></a><a name="operator_add_eq_-_eq"></a>CTime::operator +=, -=

Diese Operatoren fügen `CTimeSpan` ein Objekt zu `CTime` und von diesem Objekt hinzu und subtrahieren es.

```
CTime& operator+=(CTimeSpan span) throw();
CTime& operator-=(CTimeSpan span) throw();
```

### <a name="parameters"></a>Parameter

*Span*<br/>
Das `CTimeSpan` zu addierende oder subtrahierende Objekt.

### <a name="return-value"></a>Rückgabewert

Das `CTime` aktualisierte Objekt.

### <a name="remarks"></a>Bemerkungen

Mit diesen Operatoren können Sie `CTimeSpan` ein Objekt `CTime` zu und von diesem Objekt hinzufügen und subtrahieren.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#160](../../atl-mfc-shared/codesnippet/cpp/ctime-class_14.cpp)]

## <a name="ctimeserialize64"></a><a name="serialize64"></a>CTime::Serialize64

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

[asctime_s, _wasctime_s](../../c-runtime-library/reference/asctime-s-wasctime-s.md)<br/>
[_ftime_s, _ftime32_s, _ftime64_s](../../c-runtime-library/reference/ftime-s-ftime32-s-ftime64-s.md)<br/>
[gmtime_s, _gmtime32_s, _gmtime64_s](../../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)<br/>
[localtime_s, _localtime32_s, _localtime64_s](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md)<br/>
[strftime, wcsftime, _strftime_l, _wcsftime_l](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)<br/>
[time, _time32, _time64](../../c-runtime-library/reference/time-time32-time64.md)<br/>
[CTimeSpan-Klasse](../../atl-mfc-shared/reference/ctimespan-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[FREIGEGEBENe ATL/MFC-Klassen](../../atl-mfc-shared/atl-mfc-shared-classes.md)
