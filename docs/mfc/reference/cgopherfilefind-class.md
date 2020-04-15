---
title: CGopherFileFind-Klasse
ms.date: 11/04/2016
f1_keywords:
- CGopherFileFind
- AFXINET/CGopherFileFind
- AFXINET/CGopherFileFind::CGopherFileFind
- AFXINET/CGopherFileFind::FindFile
- AFXINET/CGopherFileFind::FindNextFile
- AFXINET/CGopherFileFind::GetCreationTime
- AFXINET/CGopherFileFind::GetLastAccessTime
- AFXINET/CGopherFileFind::GetLastWriteTime
- AFXINET/CGopherFileFind::GetLength
- AFXINET/CGopherFileFind::GetLocator
- AFXINET/CGopherFileFind::GetScreenName
- AFXINET/CGopherFileFind::IsDots
helpviewer_keywords:
- CGopherFileFind [MFC], CGopherFileFind
- CGopherFileFind [MFC], FindFile
- CGopherFileFind [MFC], FindNextFile
- CGopherFileFind [MFC], GetCreationTime
- CGopherFileFind [MFC], GetLastAccessTime
- CGopherFileFind [MFC], GetLastWriteTime
- CGopherFileFind [MFC], GetLength
- CGopherFileFind [MFC], GetLocator
- CGopherFileFind [MFC], GetScreenName
- CGopherFileFind [MFC], IsDots
ms.assetid: 8465a979-6323-496d-ab4b-e81383fb999d
ms.openlocfilehash: 7a42b99c919abd9098bff1897c4c5febf443314d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373681"
---
# <a name="cgopherfilefind-class"></a>CGopherFileFind-Klasse

Unterstützt die Internetsuche nach Dateien auf Gopherservern.

> [!NOTE]
> Die `CGopherConnection`Klassen `CGopherFile` `CGopherFileFind`, `CGopherLocator` , und ihre Mitglieder wurden veraltet, weil sie nicht auf der Windows XP-Plattform funktionieren, aber sie werden weiterhin auf früheren Plattformen arbeiten.

## <a name="syntax"></a>Syntax

```
class CGopherFileFind : public CFileFind
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CGopherFileFind::CGopherFileFind](#cgopherfilefind)|Erstellt ein `CGopherFileFind`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CGopherFileFind::FindFile](#findfile)|Sucht eine Datei auf einem Gopher-Server.|
|[CGopherFileFind::FindNextFile](#findnextfile)|Setzt die Dateisuche nach einem vorherigen Aufruf von [FindFile](#findfile)fort.|
|[CGopherFileFind::GetCreationTime](#getcreationtime)|Ruft die Zeit ab, zu der die angegebene Datei erstellt wurde.|
|[CGopherFileFind::GetLastAccessTime](#getlastaccesstime)|Ruft den Zeitpunkt ab, zu dem die angegebene Datei zuletzt aufgerufen wurde.|
|[CGopherFileFind::GetLastWriteTime](#getlastwritetime)|Ruft die Zeit ab, in die die angegebene Datei zuletzt geschrieben wurde.|
|[CGopherFileFind::GetLength](#getlength)|Ruft die Länge der gefundenen Datei in Bytes ab.|
|[CGopherFileFind::GetLocator](#getlocator)|Abrufen `CGopherLocator` eines Objekts.|
|[CGopherFileFind::GetScreenName](#getscreenname)|Ruft den Namen eines Gopher-Bildschirms ab.|
|[CGopherFileFind::IsDots](#isdots)|Testet das aktuelle Verzeichnis und die übergeordneten Verzeichnismarkierungen beim Durchlaufen von Dateien.|

## <a name="remarks"></a>Bemerkungen

`CGopherFileFind`enthält Memberfunktionen, die eine Suche starten, eine Datei suchen und die URL einer Datei zurückgeben.

Andere MFC-Klassen, die für die Suche im Internet und in lokalen Dateien entwickelt wurden, sind [CFtpFileFind](../../mfc/reference/cftpfilefind-class.md) und [CFileFind](../../mfc/reference/cfilefind-class.md). Zusammen `CGopherFileFind`mit bieten diese Klassen einen nahtlosen Mechanismus für den Benutzer, um bestimmte Dateien zu finden, unabhängig vom Serverprotokoll, Dateityp oder Speicherort (entweder ein lokaler Computer oder ein Remoteserver). Beachten Sie, dass es keine MFC-Klasse für die Suche auf HTTP-Servern gibt, da HTTP die direkte Dateimanipulation, die für Suchvorgänge erforderlich ist, nicht unterstützt.

> [!NOTE]
> `CGopherFileFind`unterstützt nicht die folgenden Memberfunktionen der Basisklasse [CFileFind:](../../mfc/reference/cfilefind-class.md)

- [GetRoot](../../mfc/reference/cfilefind-class.md#getroot)

- [GetFileName](../../mfc/reference/cfilefind-class.md#getfilename)

- [GetFilePath](../../mfc/reference/cfilefind-class.md#getfilepath)

- [GetFileTitle](../../mfc/reference/cfilefind-class.md#getfiletitle)

- [GetFileURL](../../mfc/reference/cfilefind-class.md#getfileurl)

Darüber hinaus ist `CGopherFileFind`bei `CFileFind` Verwendung mit die Memberfunktion [IsDots](../../mfc/reference/cfilefind-class.md#isdots) immer FALSE.

Weitere Informationen zur Verwendung `CGopherFileFind` und zu den anderen WinInet-Klassen finden Sie im Artikel [Internetprogrammierung mit WinInet](../../mfc/win32-internet-extensions-wininet.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CFileFind](../../mfc/reference/cfilefind-class.md)

`CGopherFileFind`

## <a name="requirements"></a>Anforderungen

**Kopf:** afxinet.h

## <a name="cgopherfilefindcgopherfilefind"></a><a name="cgopherfilefind"></a>CGopherFileFind::CGopherFileFind

Diese Memberfunktion wird aufgerufen, um ein `CGopherFileFind` Objekt zu erstellen.

```
explicit CGopherFileFind(
    CGopherConnection* pConnection,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>Parameter

*pConnection*<br/>
Ein Zeiger auf ein [CGopherConnection-Objekt.](../../mfc/reference/cgopherconnection-class.md)

*dwContext*<br/>
Der Kontextbezeichner für den Vorgang. Weitere Informationen zu *dwContext*finden Sie unter **Hinweise** .

### <a name="remarks"></a>Bemerkungen

Der Standardwert für *dwContext* wird von `CGopherFileFind` MFC aus dem [CInternetSession-Objekt,](../../mfc/reference/cinternetsession-class.md) das das `CGopherFileFind` Objekt erstellt hat, an das Objekt gesendet. Wenn Sie `CGopherFileFind` ein Objekt erstellen, können Sie die Standardeinstellung überschreiben, um den Kontextbezeichner auf einen Wert Ihrer Wahl festzulegen. Der Kontextbezeichner wird an [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) zurückgegeben, um den Status für das Objekt bereitzustellen, mit dem er identifiziert wird. Weitere Informationen zum Kontextbezeichner finden Sie im Artikel [Internet First Steps: WinInet.](../../mfc/wininet-basics.md)

## <a name="cgopherfilefindfindfile"></a><a name="findfile"></a>CGopherFileFind::FindFile

Rufen Sie diese Memberfunktion auf, um eine Gopher-Datei zu finden.

```
virtual BOOL FindFile(
    CGopherLocator& refLocator,
    LPCTSTR pstrString,
    DWORD dwFlags = INTERNET_FLAG_RELOAD);

virtual BOOL FindFile(
    LPCTSTR pstrString,
    DWORD dwFlags = INTERNET_FLAG_RELOAD);
```

### <a name="parameters"></a>Parameter

*refLocator*<br/>
Ein Verweis auf ein [CGopherLocator-Objekt.](../../mfc/reference/cgopherlocator-class.md)

*pstrString*<br/>
Ein Zeiger auf eine Zeichenfolge, die den Dateinamen enthält.

*dwFlags*<br/>
Die Flags, die beschreiben, wie diese Sitzung behandelt wird. Die gültigen Flags sind:

- INTERNET_FLAG_RELOAD Abrufen der Daten vom Remoteserver, auch wenn sie lokal zwischengespeichert sind.

- INTERNET_FLAG_DONT_CACHE Die Daten nicht lokal oder in Gateways zwischenspeichern.

- INTERNET_FLAG_SECURE sichere Transaktionen auf dem Draht mit Secure Sockets Layer oder PCT anfordern. Dieses Flag gilt nur für HTTP-Anforderungen.

- INTERNET_FLAG_USE_EXISTING Wenn möglich, verwenden Sie die vorhandenen `FindFile` Verbindungen zum Server für neue Anforderungen, anstatt für jede Anforderung eine neue Sitzung zu erstellen.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null). Um erweiterte Fehlerinformationen zu erhalten, rufen Sie die Win32-Funktion [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)auf.

### <a name="remarks"></a>Bemerkungen

Nach `FindFile` dem Aufruf zum Abrufen des ersten gopher-Objekts können Sie [FindNextFile](#findnextfile) aufrufen, um nachfolgende Gopher-Dateien abzurufen.

## <a name="cgopherfilefindfindnextfile"></a><a name="findnextfile"></a>CGopherFileFind::FindNextFile

Rufen Sie diese Memberfunktion auf, um eine Dateisuche fortzusetzen, die mit einem Aufruf von [CGopherFileFind::FindFile](#findfile)begonnen wurde.

```
virtual BOOL FindNextFile();
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn mehr Dateien vorhanden sind; Null, wenn die gefundene Datei die letzte im Verzeichnis ist oder wenn ein Fehler aufgetreten ist. Um erweiterte Fehlerinformationen zu erhalten, rufen Sie die Win32-Funktion [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)auf. Wenn die gefundene Datei die letzte Datei im Verzeichnis ist oder `GetLastError` keine übereinstimmenden Dateien gefunden werden können, gibt die Funktion ERROR_NO_MORE_FILES zurück.

## <a name="cgopherfilefindgetcreationtime"></a><a name="getcreationtime"></a>CGopherFileFind::GetCreationTime

Ruft die Erstellungszeit für die aktuelle Datei ab.

```
virtual BOOL GetCreationTime(FILETIME* pTimeStamp) const;
virtual BOOL GetCreationTime(CTime& refTime) const;
```

### <a name="parameters"></a>Parameter

*pTimeStamp*<br/>
Ein Zeiger auf eine [FILETIME-Struktur,](/windows/win32/api/minwinbase/ns-minwinbase-filetime) die die Zeit enthält, zu der die Datei erstellt wurde.

*refTime*<br/>
Ein Verweis auf ein [CTime-Objekt.](../../atl-mfc-shared/reference/ctime-class.md)

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich; 0, wenn nicht erfolgreich. `GetCreationTime`gibt 0 nur zurück, wenn [FindNextFile](#findnextfile) noch nie für dieses `CGopherFileFind` Objekt aufgerufen wurde.

### <a name="remarks"></a>Bemerkungen

Sie müssen [FindNextFile](#findnextfile) mindestens einmal `GetCreationTime`aufrufen, bevor Sie anrufen.

> [!NOTE]
> Nicht alle Dateisysteme verwenden dieselbe Semantik, um den von dieser Funktion zurückgegebenen Zeitstempel zu implementieren. Diese Funktion gibt möglicherweise denselben Wert zurück, der von anderen Zeitstempelfunktionen zurückgegeben wird, wenn das zugrunde liegende Dateisystem oder der zugrunde liegende Server das Beibehalten des Zeitattributs nicht unterstützt. Informationen zu Zeitformaten finden Sie in der [WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) Struktur. Auf einigen Betriebssystemen befindet sich die zurückgegebene Zeit in der Zeitzone, die auf dem Computer lokal ist, wenn sich die Datei befindet. Weitere Informationen finden Sie in der Win32 [FileTimeToLocalFileTime-API.](/windows/win32/api/fileapi/nf-fileapi-filetimetolocalfiletime)

## <a name="cgopherfilefindgetlastaccesstime"></a><a name="getlastaccesstime"></a>CGopherFileFind::GetLastAccessTime

Ruft den Zeitpunkt ab, zu dem die angegebene Datei zuletzt aufgerufen wurde.

```
virtual BOOL GetLastAccessTime(CTime& refTime) const;
virtual BOOL GetLastAccessTime(FILETIME* pTimeStamp) const;
```

### <a name="parameters"></a>Parameter

*refTime*<br/>
Ein Verweis auf ein [CTime-Objekt.](../../atl-mfc-shared/reference/ctime-class.md)

*pTimeStamp*<br/>
Ein Zeiger auf eine [FILETIME-Struktur,](/windows/win32/api/minwinbase/ns-minwinbase-filetime) die den Zeitpunkt enthält, zu dem die Datei zuletzt aufgerufen wurde.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich; 0, wenn nicht erfolgreich. `GetLastAccessTime`gibt 0 nur zurück, wenn [FindNextFile](#findnextfile) noch nie für dieses `CGopherFileFind` Objekt aufgerufen wurde.

### <a name="remarks"></a>Bemerkungen

Sie müssen [FindNextFile](#findnextfile) mindestens einmal `GetLastAccessTime`aufrufen, bevor Sie anrufen.

> [!NOTE]
> Nicht alle Dateisysteme verwenden dieselbe Semantik, um den von dieser Funktion zurückgegebenen Zeitstempel zu implementieren. Diese Funktion gibt möglicherweise denselben Wert zurück, der von anderen Zeitstempelfunktionen zurückgegeben wird, wenn das zugrunde liegende Dateisystem oder der zugrunde liegende Server das Beibehalten des Zeitattributs nicht unterstützt. Informationen zu Zeitformaten finden Sie in der [WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) Struktur. Auf einigen Betriebssystemen befindet sich die zurückgegebene Zeit in der Zeitzone, die auf dem Computer lokal ist, wenn sich die Datei befindet. Weitere Informationen finden Sie in der Win32 [FileTimeToLocalFileTime-API.](/windows/win32/api/fileapi/nf-fileapi-filetimetolocalfiletime)

## <a name="cgopherfilefindgetlastwritetime"></a><a name="getlastwritetime"></a>CGopherFileFind::GetLastWriteTime

Ruft ab, wenn die Datei das letzte Mal geändert wurde.

```
virtual BOOL GetLastWriteTime(FILETIME* pTimeStamp) const;
virtual BOOL GetLastWriteTime(CTime& refTime) const;
```

### <a name="parameters"></a>Parameter

*pTimeStamp*<br/>
Ein Zeiger auf eine [FILETIME-Struktur,](/windows/win32/api/minwinbase/ns-minwinbase-filetime) die die Zeit enthält, in die die Datei zuletzt geschrieben wurde.

*refTime*<br/>
Ein Verweis auf ein [CTime-Objekt.](../../atl-mfc-shared/reference/ctime-class.md)

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich; 0, wenn nicht erfolgreich. `GetLastWriteTime`gibt 0 nur zurück, wenn [FindNextFile](#findnextfile) noch nie für dieses `CGopherFileFind` Objekt aufgerufen wurde.

### <a name="remarks"></a>Bemerkungen

Sie müssen [FindNextFile](#findnextfile) mindestens einmal `GetLastWriteTime`aufrufen, bevor Sie anrufen.

> [!NOTE]
> Nicht alle Dateisysteme verwenden dieselbe Semantik, um den von dieser Funktion zurückgegebenen Zeitstempel zu implementieren. Diese Funktion gibt möglicherweise denselben Wert zurück, der von anderen Zeitstempelfunktionen zurückgegeben wird, wenn das zugrunde liegende Dateisystem oder der zugrunde liegende Server das Beibehalten des Zeitattributs nicht unterstützt. Informationen zu Zeitformaten finden Sie in der [WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) Struktur. Auf einigen Betriebssystemen befindet sich die zurückgegebene Zeit in der Zeitzone, die auf dem Computer lokal ist, wenn sich die Datei befindet. Weitere Informationen finden Sie in der Win32 [FileTimeToLocalFileTime-API.](/windows/win32/api/fileapi/nf-fileapi-filetimetolocalfiletime)

## <a name="cgopherfilefindgetlength"></a><a name="getlength"></a>CGopherFileFind::GetLength

Rufen Sie diese Memberfunktion auf, um die Länge der gefundenen Datei in Bytes abzurufen.

```
virtual ULONGLONG GetLength() const;
```

### <a name="return-value"></a>Rückgabewert

Die Länge der gefundenen Datei in Bytes.

### <a name="remarks"></a>Bemerkungen

`GetLength`verwendet die Win32-Struktur [WIN32_FIND_DATA,](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) um den Wert der Dateigröße in Bytes abzubekommen.

> [!NOTE]
> `GetLength` Unterstützt ab MFC 7.0 Ganzzahltypen mit 64 Bit. Zuvor vorhandener Code, der mit dieser neueren Version der Bibliothek erstellt wurde, kann zu Abschneidewarnungen führen.

### <a name="example"></a>Beispiel

  Siehe das Beispiel für [CFile::GetLength](../../mfc/reference/cfile-class.md#getlength) (die Basisklassenimplementierung).

## <a name="cgopherfilefindgetlocator"></a><a name="getlocator"></a>CGopherFileFind::GetLocator

Rufen Sie diese Memberfunktion auf, um das [CGopherLocator-Objekt](../../mfc/reference/cgopherlocator-class.md) abzurufen, das [FindFile](#findfile) zum Suchen der Gopher-Datei verwendet.

```
CGopherLocator GetLocator() const;
```

### <a name="return-value"></a>Rückgabewert

Ein `CGopherLocator` -Objekt.

## <a name="cgopherfilefindgetscreenname"></a><a name="getscreenname"></a>CGopherFileFind::GetScreenName

Rufen Sie diese Memberfunktion auf, um den Namen des Gopher-Bildschirms abzurufen.

```
CString GetScreenName() const;
```

### <a name="return-value"></a>Rückgabewert

Der Name des Gopher-Bildschirms.

## <a name="cgopherfilefindisdots"></a><a name="isdots"></a>CGopherFileFind::IsDots

Testet das aktuelle Verzeichnis und die übergeordneten Verzeichnismarkierungen beim Durchlaufen von Dateien.

```
virtual BOOL IsDots() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die gefundene Datei den Namen "." oder ".." hat, was darauf hinweist, dass es sich bei der gefundenen Datei tatsächlich um ein Verzeichnis handelt. andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Sie müssen [FindNextFile](#findnextfile) mindestens einmal `IsDots`aufrufen, bevor Sie anrufen.

## <a name="see-also"></a>Siehe auch

[CFileFind-Klasse](../../mfc/reference/cfilefind-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CFtpFileFind-Klasse](../../mfc/reference/cftpfilefind-class.md)<br/>
[CFileFind-Klasse](../../mfc/reference/cfilefind-class.md)<br/>
[CInternetFile-Klasse](../../mfc/reference/cinternetfile-class.md)<br/>
[CGopherFile-Klasse](../../mfc/reference/cgopherfile-class.md)<br/>
[CHttpFile-Klasse](../../mfc/reference/chttpfile-class.md)
