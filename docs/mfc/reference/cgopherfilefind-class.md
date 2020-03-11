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
ms.openlocfilehash: 55c40fc04934f00ccb541a01cce611d9532bee1a
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78875785"
---
# <a name="cgopherfilefind-class"></a>CGopherFileFind-Klasse

Unterstützt die Internetsuche nach Dateien auf Gopherservern.

> [!NOTE]
>  Die Klassen `CGopherConnection`, `CGopherFile`, `CGopherFileFind`, `CGopherLocator` und deren Member sind veraltet, da Sie nicht auf der Windows XP-Plattform funktionieren, aber Sie funktionieren weiterhin auf früheren Plattformen.

## <a name="syntax"></a>Syntax

```
class CGopherFileFind : public CFileFind
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CGopherFileFind:: CGopherFileFind](#cgopherfilefind)|Erstellt ein `CGopherFileFind`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CGopherFileFind:: FindFile](#findfile)|Sucht eine Datei auf einem Gopher-Server.|
|[CGopherFileFind:: FindNextFile](#findnextfile)|Setzt eine Dateisuche von einem vorherigen Befehl von " [FindFile](#findfile)" fort.|
|[CGopherFileFind:: getkreationtime](#getcreationtime)|Ruft den Zeitpunkt ab, zu dem die angegebene Datei erstellt wurde.|
|[CGopherFileFind:: GetLastAccessTime](#getlastaccesstime)|Ruft den Zeitpunkt des letzten Zugriffs auf die angegebene Datei ab.|
|[CGopherFileFind:: getlastschreitetime](#getlastwritetime)|Ruft den Zeitpunkt ab, zu dem zuletzt in die angegebene Datei geschrieben wurde.|
|[CGopherFileFind:: GetLength](#getlength)|Ruft die Länge der gefundenen Datei in Bytes ab.|
|[CGopherFileFind:: GetLocator](#getlocator)|`CGopherLocator`-Objekt erhalten.|
|[CGopherFileFind:: getscreenname](#getscreenname)|Ruft den Namen eines Gopher-Bildschirms ab.|
|[CGopherFileFind:: isdots](#isdots)|Testet beim Durchlaufen von Dateien auf die aktuellen Verzeichnis-und übergeordneten Verzeichnis Marker.|

## <a name="remarks"></a>Bemerkungen

`CGopherFileFind` enthält Member-Funktionen, die eine Suche starten, eine Datei suchen und die URL einer Datei zurückgeben.

Andere MFC-Klassen, die für das Internet und die lokale Datei durchsucht wurden, umfassen [CFtpFileFind](../../mfc/reference/cftpfilefind-class.md) und [CFileFind](../../mfc/reference/cfilefind-class.md). Diese Klassen bieten eine nahtlose Methode, `CGopherFileFind`mit der der Benutzer nach bestimmten Dateien suchen kann, unabhängig vom Server Protokoll, Dateityp oder Speicherort (entweder auf einem lokalen Computer oder auf einem Remote Server). Beachten Sie, dass es keine MFC-Klasse für die Suche von HTTP-Servern gibt, da HTTP die von Such Vorgängen benötigte direkte Dateibearbeitung nicht unterstützt.

> [!NOTE]
> die folgenden Element Funktionen der Basisklasse [CFileFind](../../mfc/reference/cfilefind-class.md)werden von `CGopherFileFind` nicht unterstützt:

- [GetRoot](../../mfc/reference/cfilefind-class.md#getroot)

- [GetFileName](../../mfc/reference/cfilefind-class.md#getfilename)

- [GetFilePath](../../mfc/reference/cfilefind-class.md#getfilepath)

- [GetFileTitle](../../mfc/reference/cfilefind-class.md#getfiletitle)

- [Getfileurl](../../mfc/reference/cfilefind-class.md#getfileurl)

Außerdem ist bei Verwendung mit `CGopherFileFind`die `CFileFind` Member-Funktion [isdots](../../mfc/reference/cfilefind-class.md#isdots) immer false.

Weitere Informationen zur Verwendung `CGopherFileFind` und der anderen WinInet-Klassen finden Sie im Artikel [Internet Programmierung mit WinInet](../../mfc/win32-internet-extensions-wininet.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)

[CFileFind](../../mfc/reference/cfilefind-class.md)

`CGopherFileFind`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** AFXINET. h

##  <a name="cgopherfilefind"></a>CGopherFileFind:: CGopherFileFind

Diese Member-Funktion wird aufgerufen, um ein `CGopherFileFind` Objekt zu erstellen.

```
explicit CGopherFileFind(
    CGopherConnection* pConnection,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>Parameter

*pConnection*<br/>
Ein Zeiger auf ein [CGopherConnection](../../mfc/reference/cgopherconnection-class.md) -Objekt.

*dwcontext*<br/>
Der Kontext Bezeichner für den Vorgang. Weitere Informationen zu *dwcontext*finden Sie unter " **Hinweise** ".

### <a name="remarks"></a>Bemerkungen

Der Standardwert für *dwcontext* wird vom MFC an das `CGopherFileFind` Objekt aus dem [cinternettession](../../mfc/reference/cinternetsession-class.md) -Objekt gesendet, das das `CGopherFileFind`-Objekt erstellt hat. Wenn Sie ein `CGopherFileFind` Objekt erstellen, können Sie die Standardeinstellung überschreiben, um den Kontext Bezeichner auf einen Wert Ihrer Wahl festzulegen. Der Kontext Bezeichner wird an [cinternetzession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) zurückgegeben, um den Status für das Objekt bereitzustellen, mit dem es identifiziert wird. Weitere Informationen zum Kontext Bezeichner finden Sie im Artikel [Internet First Steps: WinInet](../../mfc/wininet-basics.md) .

##  <a name="findfile"></a>CGopherFileFind:: FindFile

Diese Member-Funktion wird aufgerufen, um eine Gopher-Datei zu suchen.

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

*reflocator*<br/>
Ein Verweis auf ein [CGopherLocator](../../mfc/reference/cgopherlocator-class.md) -Objekt.

*pstrinstring*<br/>
Ein Zeiger auf eine Zeichenfolge, die den Dateinamen enthält.

*dwFlags*<br/>
Die Flags, die beschreiben, wie diese Sitzung behandelt werden soll. Gültige Flags:

- INTERNET_FLAG_RELOAD die Daten vom Remote Server zu erhalten, auch wenn Sie lokal zwischengespeichert werden.

- In INTERNET_FLAG_DONT_CACHE werden die Daten weder lokal noch in Gateways zwischengespeichert.

- INTERNET_FLAG_SECURE eine sichere Transaktion bei der Übertragung mit Secure Sockets Layer oder PCT anfordern. Dieses Flag gilt nur für HTTP-Anforderungen.

- Verwenden Sie nach Möglichkeit INTERNET_FLAG_USE_EXISTING die vorhandenen Verbindungen mit dem Server für neue `FindFile` Anforderungen, anstatt eine neue Sitzung für jede Anforderung zu erstellen.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null). Um erweiterte Fehlerinformationen abzurufen, nennen Sie die Win32-Funktion [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

### <a name="remarks"></a>Bemerkungen

Nachdem Sie `FindFile` aufgerufen haben, um das erste Gopher-Objekt abzurufen, können Sie [FindNextFile](#findnextfile) aufrufen, um nachfolgende Gopher-Dateien abzurufen.

##  <a name="findnextfile"></a>CGopherFileFind:: FindNextFile

Diese Member-Funktion wird aufgerufen, um eine Dateisuche fortzusetzen, die mit einem [CGopherFileFind:: FindFile](#findfile)-Befehl begonnen wurde.

```
virtual BOOL FindNextFile();
```

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn weitere Dateien vorhanden sind. 0 (null), wenn die gefundene Datei das letzte im Verzeichnis ist, oder, wenn ein Fehler aufgetreten ist. Um erweiterte Fehlerinformationen abzurufen, nennen Sie die Win32-Funktion [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror). Wenn es sich bei der gefundenen Datei um die letzte Datei im Verzeichnis handelt oder wenn keine übereinstimmenden Dateien gefunden werden können, gibt die `GetLastError` Funktion ERROR_NO_MORE_FILES zurück.

##  <a name="getcreationtime"></a>CGopherFileFind:: getkreationtime

Ruft den Erstellungs Zeitpunkt für die aktuelle Datei ab.

```
virtual BOOL GetCreationTime(FILETIME* pTimeStamp) const;
virtual BOOL GetCreationTime(CTime& refTime) const;
```

### <a name="parameters"></a>Parameter

*ptimestamp*<br/>
Ein Zeiger auf eine [FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime) -Struktur, die die Uhrzeit enthält, zu der die Datei erstellt wurde.

*Ref-Zeit*<br/>
Ein Verweis auf ein [ctime](../../atl-mfc-shared/reference/ctime-class.md) -Objekt.

### <a name="return-value"></a>Rückgabewert

Ungleich NULL, wenn erfolgreich; 0, wenn nicht erfolgreich. `GetCreationTime` gibt 0 nur zurück, wenn [FindNextFile](#findnextfile) für dieses `CGopherFileFind` Objekt noch nie aufgerufen wurde.

### <a name="remarks"></a>Bemerkungen

[FindNextFile](#findnextfile) muss mindestens einmal aufgerufen werden, bevor `GetCreationTime`aufgerufen wird.

> [!NOTE]
>  Nicht alle Dateisysteme verwenden die gleiche Semantik, um den von dieser Funktion zurückgegebenen Zeitstempel zu implementieren. Diese Funktion gibt möglicherweise denselben Wert zurück, der von anderen Zeitstempel Funktionen zurückgegeben wird, wenn das zugrunde liegende Dateisystem oder der Server das Beibehalten des Zeit Attributs nicht unterstützt. Informationen zu Zeitformaten finden Sie in der [WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) -Struktur. Bei einigen Betriebssystemen befindet sich die zurückgegebene Zeit in der lokalen Zeitzone des Computers, in dem sich die Datei befindet. Weitere Informationen finden Sie in der Win32 [filetimetolocalfiletime](/windows/win32/api/fileapi/nf-fileapi-filetimetolocalfiletime) -API.

##  <a name="getlastaccesstime"></a>CGopherFileFind:: GetLastAccessTime

Ruft den Zeitpunkt des letzten Zugriffs auf die angegebene Datei ab.

```
virtual BOOL GetLastAccessTime(CTime& refTime) const;
virtual BOOL GetLastAccessTime(FILETIME* pTimeStamp) const;
```

### <a name="parameters"></a>Parameter

*Ref-Zeit*<br/>
Ein Verweis auf ein [ctime](../../atl-mfc-shared/reference/ctime-class.md) -Objekt.

*ptimestamp*<br/>
Ein Zeiger auf eine [FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime) -Struktur, die die Uhrzeit des letzten Zugriffs auf die Datei enthält.

### <a name="return-value"></a>Rückgabewert

Ungleich NULL, wenn erfolgreich; 0, wenn nicht erfolgreich. `GetLastAccessTime` gibt 0 nur zurück, wenn [FindNextFile](#findnextfile) für dieses `CGopherFileFind` Objekt noch nie aufgerufen wurde.

### <a name="remarks"></a>Bemerkungen

[FindNextFile](#findnextfile) muss mindestens einmal aufgerufen werden, bevor `GetLastAccessTime`aufgerufen wird.

> [!NOTE]
>  Nicht alle Dateisysteme verwenden die gleiche Semantik, um den von dieser Funktion zurückgegebenen Zeitstempel zu implementieren. Diese Funktion gibt möglicherweise denselben Wert zurück, der von anderen Zeitstempel Funktionen zurückgegeben wird, wenn das zugrunde liegende Dateisystem oder der Server das Beibehalten des Zeit Attributs nicht unterstützt. Informationen zu Zeitformaten finden Sie in der [WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) -Struktur. Bei einigen Betriebssystemen befindet sich die zurückgegebene Zeit in der lokalen Zeitzone des Computers, in dem sich die Datei befindet. Weitere Informationen finden Sie in der Win32 [filetimetolocalfiletime](/windows/win32/api/fileapi/nf-fileapi-filetimetolocalfiletime) -API.

##  <a name="getlastwritetime"></a>CGopherFileFind:: getlastschreitetime

Ruft den Zeitpunkt ab, zu dem die Datei zuletzt geändert wurde.

```
virtual BOOL GetLastWriteTime(FILETIME* pTimeStamp) const;
virtual BOOL GetLastWriteTime(CTime& refTime) const;
```

### <a name="parameters"></a>Parameter

*ptimestamp*<br/>
Ein Zeiger auf eine [FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime) -Struktur, die den Zeitpunkt enthält, zu dem zuletzt in die Datei geschrieben wurde.

*Ref-Zeit*<br/>
Ein Verweis auf ein [ctime](../../atl-mfc-shared/reference/ctime-class.md) -Objekt.

### <a name="return-value"></a>Rückgabewert

Ungleich NULL, wenn erfolgreich; 0, wenn nicht erfolgreich. `GetLastWriteTime` gibt 0 nur zurück, wenn [FindNextFile](#findnextfile) für dieses `CGopherFileFind` Objekt noch nie aufgerufen wurde.

### <a name="remarks"></a>Bemerkungen

[FindNextFile](#findnextfile) muss mindestens einmal aufgerufen werden, bevor `GetLastWriteTime`aufgerufen wird.

> [!NOTE]
>  Nicht alle Dateisysteme verwenden die gleiche Semantik, um den von dieser Funktion zurückgegebenen Zeitstempel zu implementieren. Diese Funktion gibt möglicherweise denselben Wert zurück, der von anderen Zeitstempel Funktionen zurückgegeben wird, wenn das zugrunde liegende Dateisystem oder der Server das Beibehalten des Zeit Attributs nicht unterstützt. Informationen zu Zeitformaten finden Sie in der [WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) -Struktur. Bei einigen Betriebssystemen befindet sich die zurückgegebene Zeit in der lokalen Zeitzone des Computers, in dem sich die Datei befindet. Weitere Informationen finden Sie in der Win32 [filetimetolocalfiletime](/windows/win32/api/fileapi/nf-fileapi-filetimetolocalfiletime) -API.

##  <a name="getlength"></a>CGopherFileFind:: GetLength

Mit dieser Member-Funktion können Sie die Länge der gefundenen Datei in Byte abrufen.

```
virtual ULONGLONG GetLength() const;
```

### <a name="return-value"></a>Rückgabewert

Die Länge (in Byte) der gefundenen Datei.

### <a name="remarks"></a>Bemerkungen

`GetLength` verwendet die Win32-Struktur [WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) , um den Wert der Dateigröße in Bytes zu erhalten.

> [!NOTE]
>  Ab MFC 7,0 unterstützt `GetLength` ganzzahlige Typen mit 64 Bit. Zuvor vorhandener Code, der mit dieser neueren Version der Bibliothek erstellt wurde, führt möglicherweise zu abkürzen von Warnungen.

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [CFile:: GetLength](../../mfc/reference/cfile-class.md#getlength) (die Basisklassen Implementierung).

##  <a name="getlocator"></a>CGopherFileFind:: GetLocator

Mit dieser Member-Funktion können Sie das [CGopherLocator](../../mfc/reference/cgopherlocator-class.md) -Objekt abrufen, das von [FindFile](#findfile) zum Suchen der Gopher-Datei verwendet wird.

```
CGopherLocator GetLocator() const;
```

### <a name="return-value"></a>Rückgabewert

Ein `CGopherLocator` -Objekt.

##  <a name="getscreenname"></a>CGopherFileFind:: getscreenname

Mit dieser Member-Funktion können Sie den Namen des Gopher-Bildschirms abrufen.

```
CString GetScreenName() const;
```

### <a name="return-value"></a>Rückgabewert

Der Name des Gopher-Bildschirms.

##  <a name="isdots"></a>CGopherFileFind:: isdots

Testet beim Durchlaufen von Dateien auf die aktuellen Verzeichnis-und übergeordneten Verzeichnis Marker.

```
virtual BOOL IsDots() const;
```

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn die gefundene Datei den Namen "." oder ".." hat, was darauf hinweist, dass es sich bei der gefundenen Datei tatsächlich um ein Verzeichnis handelt. andernfalls 0.

### <a name="remarks"></a>Bemerkungen

[FindNextFile](#findnextfile) muss mindestens einmal aufgerufen werden, bevor `IsDots`aufgerufen wird.

## <a name="see-also"></a>Weitere Informationen

[CFileFind-Klasse](../../mfc/reference/cfilefind-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CFtpFileFind-Klasse](../../mfc/reference/cftpfilefind-class.md)<br/>
[CFileFind-Klasse](../../mfc/reference/cfilefind-class.md)<br/>
[CInternetFile-Klasse](../../mfc/reference/cinternetfile-class.md)<br/>
[CGopherFile-Klasse](../../mfc/reference/cgopherfile-class.md)<br/>
[CHttpFile-Klasse](../../mfc/reference/chttpfile-class.md)
