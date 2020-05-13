---
title: CFileFind-Klasse
ms.date: 11/04/2016
f1_keywords:
- CFileFind
- AFX/CFileFind
- AFX/CFileFind::CFileFind
- AFX/CFileFind::Close
- AFX/CFileFind::FindFile
- AFX/CFileFind::FindNextFile
- AFX/CFileFind::GetCreationTime
- AFX/CFileFind::GetFileName
- AFX/CFileFind::GetFilePath
- AFX/CFileFind::GetFileTitle
- AFX/CFileFind::GetFileURL
- AFX/CFileFind::GetLastAccessTime
- AFX/CFileFind::GetLastWriteTime
- AFX/CFileFind::GetLength
- AFX/CFileFind::GetRoot
- AFX/CFileFind::IsArchived
- AFX/CFileFind::IsCompressed
- AFX/CFileFind::IsDirectory
- AFX/CFileFind::IsDots
- AFX/CFileFind::IsHidden
- AFX/CFileFind::IsNormal
- AFX/CFileFind::IsReadOnly
- AFX/CFileFind::IsSystem
- AFX/CFileFind::IsTemporary
- AFX/CFileFind::MatchesMask
- AFX/CFileFind::CloseContext
- AFX/CFileFind::m_pTM
helpviewer_keywords:
- CFileFind [MFC], CFileFind
- CFileFind [MFC], Close
- CFileFind [MFC], FindFile
- CFileFind [MFC], FindNextFile
- CFileFind [MFC], GetCreationTime
- CFileFind [MFC], GetFileName
- CFileFind [MFC], GetFilePath
- CFileFind [MFC], GetFileTitle
- CFileFind [MFC], GetFileURL
- CFileFind [MFC], GetLastAccessTime
- CFileFind [MFC], GetLastWriteTime
- CFileFind [MFC], GetLength
- CFileFind [MFC], GetRoot
- CFileFind [MFC], IsArchived
- CFileFind [MFC], IsCompressed
- CFileFind [MFC], IsDirectory
- CFileFind [MFC], IsDots
- CFileFind [MFC], IsHidden
- CFileFind [MFC], IsNormal
- CFileFind [MFC], IsReadOnly
- CFileFind [MFC], IsSystem
- CFileFind [MFC], IsTemporary
- CFileFind [MFC], MatchesMask
- CFileFind [MFC], CloseContext
- CFileFind [MFC], m_pTM
ms.assetid: 9990068c-b023-4114-9580-a50182d15240
ms.openlocfilehash: 5bb53a6abf7040bd6ee9f5f2cf56b0feb4d62e66
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81755034"
---
# <a name="cfilefind-class"></a>CFileFind-Klasse

Führt lokale Dateisuchen durch und ist die Basisklasse für [CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md) und [CFtpFileFind](../../mfc/reference/cftpfilefind-class.md), die Internetdateisuchen durchführen.

## <a name="syntax"></a>Syntax

```
class CFileFind : public CObject
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CFileFind::CFileFind](#cfilefind)|Erstellt ein `CFileFind`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CFileFind::Schließen](#close)|Schließt die Suchanforderung.|
|[CFileFind::FindFile](#findfile)|Durchsucht ein Verzeichnis nach einem angegebenen Dateinamen.|
|[CFileFind::FindNextFile](#findnextfile)|Setzt die Dateisuche nach einem vorherigen Aufruf von [FindFile](#findfile)fort.|
|[CFileFind::GetCreationTime](#getcreationtime)|Ruft den Zeitpunkt ab, zu dem die Datei erstellt wurde.|
|[CFileFind::GetFileName](#getfilename)|Ruft den Namen der gefundenen Datei ab, einschließlich der Erweiterung.|
|[CFileFind::GetFilePath](#getfilepath)|Ruft den gesamten Pfad der gefundenen Datei ab.|
|[CFileFind::GetFileTitle](#getfiletitle)|Ruft den Titel der gefundenen Datei ab. Der Titel enthält nicht die Erweiterung.|
|[CFileFind::GetFileURL](#getfileurl)|Ruft die URL der gefundenen Datei ab, einschließlich des Dateipfads.|
|[CFileFind::GetLastAccessTime](#getlastaccesstime)|Ruft die Zeit ab, zu der zuletzt auf die Datei zugegriffen wurde.|
|[CFileFind::GetLastWriteTime](#getlastwritetime)|Ruft den Zeitpunkt ab, zu dem die Datei zuletzt geändert und gespeichert wurde.|
|[CFileFind::GetLength](#getlength)|Ruft die Länge der gefundenen Datei in Bytes ab.|
|[CFileFind::GetRoot](#getroot)|Ruft das Stammverzeichnis der gefundenen Datei ab.|
|[CFileFind::IsArchived](#isarchived)|Bestimmt, ob die gefundene Datei archiviert ist.|
|[CFileFind::IsCompressed](#iscompressed)|Bestimmt, ob die gefundene Datei komprimiert ist.|
|[CFileFind::IsDirectory](#isdirectory)|Bestimmt, ob es sich bei der gefundenen Datei um ein Verzeichnis handelt.|
|[CFileFind::IsDots](#isdots)|Bestimmt, ob der Name der gefundenen Datei den Namen "." oder ".." hat, was darauf hinweist, dass es sich tatsächlich um ein Verzeichnis handelt.|
|[CFileFind::IsHidden](#ishidden)|Bestimmt, ob die gefundene Datei ausgeblendet ist.|
|[CFileFind::IsNormal](#isnormal)|Bestimmt, ob die gefundene Datei normal ist (d. h. keine anderen Attribute hat).|
|[CFileFind::IsReadOnly](#isreadonly)|Bestimmt, ob die gefundene Datei schreibgeschützt ist.|
|[CFileFind::IsSystem](#issystem)|Bestimmt, ob es sich bei der gefundenen Datei um eine Systemdatei handelt.|
|[CFileFind::IsTemporary](#istemporary)|Bestimmt, ob die gefundene Datei temporär ist.|
|[CFileFind::MatchesMask](#matchesmask)|Gibt die gewünschten Dateiattribute der zu findenden Datei an.|

### <a name="protected-methods"></a>Geschützte Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CFileFind::CloseContext](#closecontext)|Schließt die vom aktuellen Suchhandle angegebene Datei.|

### <a name="protected-data-members"></a>Geschützte Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CFileFind::m_pTM](#m_ptm)|Zeiger auf `CAtlTransactionManager` ein Objekt.|

## <a name="remarks"></a>Bemerkungen

`CFileFind`enthält Memberfunktionen, die eine Suche starten, eine Datei suchen und den Titel, den Namen oder den Pfad der Datei zurückgeben. Bei Internetsuchen gibt die Memberfunktion [GetFileURL](#getfileurl) die URL der Datei zurück.

`CFileFind`ist die Basisklasse für zwei weitere MFC-Klassen, die für die Suche nach bestimmten Servertypen entwickelt wurden: `CGopherFileFind` arbeitet speziell mit Gopher-Servern und `CFtpFileFind` arbeitet speziell mit FTP-Servern. Zusammen bieten diese drei Klassen einen nahtlosen Mechanismus für den Client, um Dateien unabhängig vom Serverprotokoll, dem Dateityp oder Speicherort auf einem lokalen Computer oder einem Remoteserver zu finden.

Der folgende Code führt alle Dateien im aktuellen Verzeichnis auf und druckt den Namen jeder Datei:

[!code-cpp[NVC_MFCFiles#31](../../atl-mfc-shared/reference/codesnippet/cpp/cfilefind-class_1.cpp)]

Um das Beispiel einfach zu halten, verwendet `cout` dieser Code die C++-Standardbibliotheksklasse. Die `cout` Leitung kann durch einen `CListBox::AddString`Aufruf von ersetzt werden, z. B. in einem Programm mit einer grafischen Benutzeroberfläche.

Weitere Informationen zur Verwendung `CFileFind` und zu den anderen WinInet-Klassen finden Sie im Artikel [Internetprogrammierung mit WinInet](../../mfc/win32-internet-extensions-wininet.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

`CFileFind`

## <a name="requirements"></a>Requirements (Anforderungen)

**Kopf:** afx.h

## <a name="cfilefindcfilefind"></a><a name="cfilefind"></a>CFileFind::CFileFind

Diese Memberfunktion wird `CFileFind` aufgerufen, wenn ein Objekt erstellt wird.

```
CFileFind();
CFileFind(CAtlTransactionManager* pTM);
```

### <a name="parameters"></a>Parameter

*Ptm*<br/>
Zeiger auf CAtlTransactionManager-Objekt

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CFileFind::GetFileName](#getfilename).

## <a name="cfilefindclose"></a><a name="close"></a>CFileFind::Schließen

Rufen Sie diese Memberfunktion auf, um die Suche zu beenden, den Kontext zurückzusetzen und alle Ressourcen freizugeben.

```cpp
void Close();
```

### <a name="remarks"></a>Bemerkungen

Nach `Close`dem Aufruf müssen Sie keine `CFileFind` neue Instanz erstellen, bevor Sie [FindFile](#findfile) aufrufen, um eine neue Suche zu starten.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CFileFind::GetFileName](#getfilename).

## <a name="cfilefindclosecontext"></a><a name="closecontext"></a>CFileFind::CloseContext

Schließt die vom aktuellen Suchhandle angegebene Datei.

```
virtual void CloseContext();
```

### <a name="remarks"></a>Bemerkungen

Schließt die Datei, die durch den aktuellen Wert des Suchhandles angegeben wird. Überschreiben Sie diese Funktion, um das Standardverhalten zu ändern.

Sie müssen die [Funktionen FindFile](#findfile) oder [FindNextFile](#findnextfile) mindestens einmal aufrufen, um ein gültiges Suchhandle abzurufen. Die `FindFile` `FindNextFile` und-Funktionen verwenden das Suchhandle, um Dateien mit Namen zu suchen, die einem bestimmten Namen entsprechen.

## <a name="cfilefindfindfile"></a><a name="findfile"></a>CFileFind::FindFile

Rufen Sie diese Memberfunktion auf, um eine Dateisuche zu öffnen.

```
virtual BOOL FindFile(
    LPCTSTR pstrName = NULL,
    DWORD dwUnused = 0);
```

### <a name="parameters"></a>Parameter

*pstrName*<br/>
Ein Zeiger auf eine Zeichenfolge, die den Namen der zu suchenden Datei enthält. Wenn Sie NULL für *pstrName übergeben,* `FindFile` \*wird ein Platzhalter (*. ) gesucht.

*dwUnused*<br/>
Reserviert, `FindFile` um polymorph mit abgeleiteten Klassen zu machen. Muss den Wert 0 (null) haben.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null). Um erweiterte Fehlerinformationen zu erhalten, rufen Sie die Win32-Funktion [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)auf.

### <a name="remarks"></a>Bemerkungen

Rufen `FindFile` Sie nach dem Aufruf auf, um die Dateisuche zu starten, rufen Sie [FindNextFile](#findnextfile) auf, um nachfolgende Dateien abzurufen. Sie müssen `FindNextFile` mindestens einmal aufrufen, bevor Sie eine der folgenden Attributmemberfunktionen aufrufen:

- [GetCreationTime](#getcreationtime)

- [GetFileName](#getfilename)

- [GetFileTitle](#getfiletitle)

- [GetFilePath](#getfilepath)

- [GetFileURL](#getfileurl)

- [GetLastAccessTime](#getlastaccesstime)

- [GetLastWriteTime](#getlastwritetime)

- [Getlength](#getlength)

- [GetRoot](#getroot)

- [IsArchived](#isarchived)

- [IsCompressed](#iscompressed)

- [Isdirectory](#isdirectory)

- [IsDots](#isdots)

- [IsHidden](#ishidden)

- [IsNormal](#isnormal)

- [IsReadOnly](#isreadonly)

- [IsSystem](#issystem)

- [IsTemporary](#istemporary)

- [MatchesMask](#matchesmask)

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CFileFind::IsDirectory](#isdirectory).

## <a name="cfilefindfindnextfile"></a><a name="findnextfile"></a>CFileFind::FindNextFile

Rufen Sie diese Memberfunktion auf, um die Dateisuche von einem vorherigen Aufruf von [FindFile](#findfile)fortzusetzen.

```
virtual BOOL FindNextFile();
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn mehr Dateien vorhanden sind; Null, wenn die gefundene Datei die letzte im Verzeichnis ist oder wenn ein Fehler aufgetreten ist. Um erweiterte Fehlerinformationen zu erhalten, rufen Sie die Win32-Funktion [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)auf. Wenn die gefundene Datei die letzte Datei im Verzeichnis ist oder `GetLastError` keine übereinstimmenden Dateien gefunden werden können, gibt die Funktion ERROR_NO_MORE_FILES zurück.

### <a name="remarks"></a>Bemerkungen

Sie müssen `FindNextFile` mindestens einmal aufrufen, bevor Sie eine der folgenden Attributmemberfunktionen aufrufen:

- [GetCreationTime](#getcreationtime)

- [GetFileName](#getfilename)

- [GetFileTitle](#getfiletitle)

- [GetFilePath](#getfilepath)

- [GetFileURL](#getfileurl)

- [GetLastAccessTime](#getlastaccesstime)

- [GetLastWriteTime](#getlastwritetime)

- [Getlength](#getlength)

- [GetRoot](#getroot)

- [IsArchived](#isarchived)

- [IsCompressed](#iscompressed)

- [Isdirectory](#isdirectory)

- [IsDots](#isdots)

- [IsHidden](#ishidden)

- [IsNormal](#isnormal)

- [IsReadOnly](#isreadonly)

- [IsSystem](#issystem)

- [IsTemporary](#istemporary)

- [MatchesMask](#matchesmask)

`FindNextFile`umschließt die Win32-Funktion [FindNextFile](/windows/win32/api/fileapi/nf-fileapi-findnextfilew).

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CFileFind::IsDirectory](#isdirectory).

## <a name="cfilefindgetcreationtime"></a><a name="getcreationtime"></a>CFileFind::GetCreationTime

Rufen Sie diese Memberfunktion auf, um die Zeit abzurufen, zu der die angegebene Datei erstellt wurde.

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

Ungleich Null, wenn erfolgreich; 0, wenn nicht erfolgreich. `GetCreationTime`gibt 0 nur zurück, wenn [FindNextFile](#findnextfile) noch nie für dieses `CFileFind` Objekt aufgerufen wurde.

### <a name="remarks"></a>Bemerkungen

Sie müssen [FindNextFile](#findnextfile) mindestens einmal `GetCreationTime`aufrufen, bevor Sie anrufen.

> [!NOTE]
> Nicht alle Dateisysteme verwenden dieselbe Semantik, um den von dieser Funktion zurückgegebenen Zeitstempel zu implementieren. Diese Funktion gibt möglicherweise denselben Wert zurück, der von anderen Zeitstempelfunktionen zurückgegeben wird, wenn das zugrunde liegende Dateisystem oder der zugrunde liegende Server das Beibehalten des Zeitattributs nicht unterstützt. Informationen zu Zeitformaten finden Sie in der [WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) Struktur. Auf einigen Betriebssystemen befindet sich die zurückgegebene Zeit in der Zeitzone, die auf dem Computer lokal ist, wenn sich die Datei befindet. Weitere Informationen finden Sie in der Win32 [FileTimeToLocalFileTime-API.](/windows/win32/api/fileapi/nf-fileapi-filetimetolocalfiletime)

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CFileFind::GetLength](#getlength).

## <a name="cfilefindgetfilename"></a><a name="getfilename"></a>CFileFind::GetFileName

Rufen Sie diese Memberfunktion auf, um den Namen der gefundenen Datei abzurufen.

```
virtual CString GetFileName() const;
```

### <a name="return-value"></a>Rückgabewert

Der Name der zuletzt gefundenen Datei.

### <a name="remarks"></a>Bemerkungen

Sie müssen [FindNextFile](#findnextfile) mindestens einmal aufrufen, bevor Sie GetFileName aufrufen.

`GetFileName`ist eine `CFileFind` von drei Memberfunktionen, die eine Form des Dateinamens zurückgeben. Die folgende Liste beschreibt die drei und wie sie variieren:

- `GetFileName`gibt den Dateinamen zurück, einschließlich der Erweiterung. Wenn Sie `GetFileName` z. B. eine Benutzernachricht über die Datei *c:'myhtml'myfile.txt'* aufrufen, wird der Dateiname *myfile.txt*zurückgegeben.

- [GetFilePath](#getfilepath) gibt den gesamten Pfad für die Datei zurück. Wenn Sie `GetFilePath` z. B. eine Benutzernachricht über die Datei *c:'myhtml'myfile.txt'* aufrufen, wird der Dateipfad *c:'myhtml'myfile.txt'* zurückgegeben.

- [GetFileTitle](#getfiletitle) gibt den Dateinamen mit Ausnahme der Dateierweiterung zurück. Wenn Sie `GetFileTitle` z. B. eine Benutzernachricht über die Datei *c:'myhtml'myfile.txt'* aufrufen, wird der Dateititel *myfile*zurückgegeben.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCFiles#32](../../atl-mfc-shared/reference/codesnippet/cpp/cfilefind-class_2.cpp)]

## <a name="cfilefindgetfilepath"></a><a name="getfilepath"></a>CFileFind::GetFilePath

Rufen Sie diese Memberfunktion auf, um den vollständigen Pfad der angegebenen Datei abzurufen.

```
virtual CString GetFilePath() const;
```

### <a name="return-value"></a>Rückgabewert

Der Pfad der angegebenen Datei.

### <a name="remarks"></a>Bemerkungen

Sie müssen [FindNextFile](#findnextfile) mindestens einmal `GetFilePath`aufrufen, bevor Sie anrufen.

`GetFilePath`ist eine `CFileFind` von drei Memberfunktionen, die eine Form des Dateinamens zurückgeben. Die folgende Liste beschreibt die drei und wie sie variieren:

- [GetFileName](#getfilename) gibt den Dateinamen zurück, einschließlich der Erweiterung. Wenn Sie `GetFileName` z. B. eine Benutzernachricht über die Datei *c:'myhtml'myfile.txt'* aufrufen, wird der Dateiname *myfile.txt*zurückgegeben.

- `GetFilePath`gibt den gesamten Pfad für die Datei zurück. Wenn Sie `GetFilePath` z. B. eine `c:\myhtml\myfile.txt` Benutzernachricht über `c:\myhtml\myfile.txt`die Datei generieren, wird der Dateipfad zurückgegeben.

- [GetFileTitle](#getfiletitle) gibt den Dateinamen mit Ausnahme der Dateierweiterung zurück. Wenn Sie `GetFileTitle` z. B. eine Benutzernachricht über die Datei *c:'myhtml'myfile.txt'* aufrufen, wird der Dateititel *myfile*zurückgegeben.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CFileFind::GetFileName](#getfilename).

## <a name="cfilefindgetfiletitle"></a><a name="getfiletitle"></a>CFileFind::GetFileTitle

Rufen Sie diese Memberfunktion auf, um den Titel der gefundenen Datei abzurufen.

```
virtual CString GetFileTitle() const;
```

### <a name="return-value"></a>Rückgabewert

Der Titel der Datei.

### <a name="remarks"></a>Bemerkungen

Sie müssen [FindNextFile](#findnextfile) mindestens einmal `GetFileTitle`aufrufen, bevor Sie anrufen.

`GetFileTitle`ist eine `CFileFind` von drei Memberfunktionen, die eine Form des Dateinamens zurückgeben. Die folgende Liste beschreibt die drei und wie sie variieren:

- [GetFileName](#getfilename) gibt den Dateinamen zurück, einschließlich der Erweiterung. Wenn Sie `GetFileName` z. B. eine Benutzernachricht über die Datei *c:'myhtml'myfile.txt'* aufrufen, wird der Dateiname *myfile.txt*zurückgegeben.

- [GetFilePath](#getfilepath) gibt den gesamten Pfad für die Datei zurück. Wenn Sie `GetFilePath` z. B. eine Benutzernachricht über die Datei *c:'myhtml'myfile.txt'* aufrufen, wird der Dateipfad *c:'myhtml'myfile.txt'* zurückgegeben.

- `GetFileTitle`gibt den Dateinamen zurück, mit Ausnahme der Dateierweiterung. Wenn Sie `GetFileTitle` z. B. eine Benutzernachricht über die Datei *c:'myhtml'myfile.txt'* aufrufen, wird der Dateititel *myfile*zurückgegeben.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CFileFind::GetFileName](#getfilename).

## <a name="cfilefindgetfileurl"></a><a name="getfileurl"></a>CFileFind::GetFileURL

Rufen Sie diese Memberfunktion auf, um die angegebene URL abzurufen.

```
virtual CString GetFileURL() const;
```

### <a name="return-value"></a>Rückgabewert

Die vollständige URL.

### <a name="remarks"></a>Bemerkungen

Sie müssen [FindNextFile](#findnextfile) mindestens einmal `GetFileURL`aufrufen, bevor Sie anrufen.

`GetFileURL`ähnelt der Memberfunktion [GetFilePath](#getfilepath), mit der Ausnahme, `file://path`dass die URL im Formular zurückgegeben wird. Wenn Sie `GetFileURL` beispielsweise aufrufen, um die vollständige URL für `file://c:\myhtml\myfile.txt` *myfile.txt* abzurufen, wird die URL zurückgegeben.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CFileFind::GetFileName](#getfilename).

## <a name="cfilefindgetlastaccesstime"></a><a name="getlastaccesstime"></a>CFileFind::GetLastAccessTime

Rufen Sie diese Memberfunktion auf, um die Zeit abzurufen, zu der zuletzt auf die angegebene Datei zugegriffen wurde.

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

Ungleich Null, wenn erfolgreich; 0, wenn nicht erfolgreich. `GetLastAccessTime`gibt 0 nur zurück, wenn [FindNextFile](#findnextfile) noch nie für dieses `CFileFind` Objekt aufgerufen wurde.

### <a name="remarks"></a>Bemerkungen

Sie müssen [FindNextFile](#findnextfile) mindestens einmal `GetLastAccessTime`aufrufen, bevor Sie anrufen.

> [!NOTE]
> Nicht alle Dateisysteme verwenden dieselbe Semantik, um den von dieser Funktion zurückgegebenen Zeitstempel zu implementieren. Diese Funktion gibt möglicherweise denselben Wert zurück, der von anderen Zeitstempelfunktionen zurückgegeben wird, wenn das zugrunde liegende Dateisystem oder der zugrunde liegende Server das Beibehalten des Zeitattributs nicht unterstützt. Informationen zu Zeitformaten finden Sie in der [WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) Struktur. Auf einigen Betriebssystemen befindet sich die zurückgegebene Zeit in der Zeitzone, die auf dem Computer lokal ist, wenn sich die Datei befindet. Weitere Informationen finden Sie in der Win32 [FileTimeToLocalFileTime-API.](/windows/win32/api/fileapi/nf-fileapi-filetimetolocalfiletime)

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CFileFind::GetLength](#getlength).

## <a name="cfilefindgetlastwritetime"></a><a name="getlastwritetime"></a>CFileFind::GetLastWriteTime

Rufen Sie diese Memberfunktion auf, um die letzte Änderung der Datei abzurufen.

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

Ungleich Null, wenn erfolgreich; 0, wenn nicht erfolgreich. `GetLastWriteTime`gibt 0 nur zurück, wenn [FindNextFile](#findnextfile) noch nie für dieses `CFileFind` Objekt aufgerufen wurde.

### <a name="remarks"></a>Bemerkungen

Sie müssen [FindNextFile](#findnextfile) mindestens einmal `GetLastWriteTime`aufrufen, bevor Sie anrufen.

> [!NOTE]
> Nicht alle Dateisysteme verwenden dieselbe Semantik, um den von dieser Funktion zurückgegebenen Zeitstempel zu implementieren. Diese Funktion gibt möglicherweise denselben Wert zurück, der von anderen Zeitstempelfunktionen zurückgegeben wird, wenn das zugrunde liegende Dateisystem oder der zugrunde liegende Server das Beibehalten des Zeitattributs nicht unterstützt. Informationen zu Zeitformaten finden Sie in der [WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) Struktur. Auf einigen Betriebssystemen befindet sich die zurückgegebene Zeit in der Zeitzone, die auf dem Computer lokal ist, wenn sich die Datei befindet. Weitere Informationen finden Sie in der Win32 [FileTimeToLocalFileTime-API.](/windows/win32/api/fileapi/nf-fileapi-filetimetolocalfiletime)

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CFileFind::GetLength](#getlength).

## <a name="cfilefindgetlength"></a><a name="getlength"></a>CFileFind::GetLength

Rufen Sie diese Memberfunktion auf, um die Länge der gefundenen Datei in Bytes abzurufen.

```
ULONGLONG GetLength() const;
```

### <a name="return-value"></a>Rückgabewert

Die Länge der gefundenen Datei in Bytes.

### <a name="remarks"></a>Bemerkungen

Sie müssen [FindNextFile](#findnextfile) mindestens einmal `GetLength`aufrufen, bevor Sie anrufen.

`GetLength`verwendet die Win32-Struktur [WIN32_FIND_DATA,](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) um den Wert der Dateigröße in Bytes abzuspeichern und zurückzugeben.

> [!NOTE]
> `GetLength` Unterstützt ab MFC 7.0 Ganzzahltypen mit 64 Bit. Zuvor vorhandener Code, der mit dieser neueren Version der Bibliothek erstellt wurde, kann zu Abschneidewarnungen führen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCFiles#33](../../atl-mfc-shared/reference/codesnippet/cpp/cfilefind-class_3.cpp)]

## <a name="cfilefindgetroot"></a><a name="getroot"></a>CFileFind::GetRoot

Rufen Sie diese Memberfunktion auf, um den Stamm der gefundenen Datei abzurufen.

```
virtual CString GetRoot() const;
```

### <a name="return-value"></a>Rückgabewert

Der Stamm der aktiven Suche.

### <a name="remarks"></a>Bemerkungen

Sie müssen [FindNextFile](#findnextfile) mindestens einmal `GetRoot`aufrufen, bevor Sie anrufen.

Diese Memberfunktion gibt den Laufwerkbezeichner und den Pfadnamen zurück, der zum Starten einer Suche verwendet wird. Wenn Sie beispielsweise [FindFile](#findfile) aufrufen, mit `*.dat` dem Ergebnis, dass eine leere Zeichenfolge `GetRoot` zurückgegeben wird. Übergeben eines `c:\windows\system\*.dll`Pfads, `FindFile` z. B. , an Ergebnisse, `GetRoot` die zurückgegeben werden. `c:\windows\system\`

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CFileFind::GetFileName](#getfilename).

## <a name="cfilefindisarchived"></a><a name="isarchived"></a>CFileFind::IsArchived

Rufen Sie diese Memberfunktion auf, um zu ermitteln, ob die gefundene Datei archiviert ist.

```
BOOL IsArchived() const;
```

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Anwendungen markieren eine Archivdatei, die gesichert oder entfernt werden soll, mit FILE_ATTRIBUTE_ARCHIVE, einem Dateiattribut, das in der [WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) Struktur identifiziert ist.

Sie müssen [FindNextFile](#findnextfile) mindestens einmal `IsArchived`aufrufen, bevor Sie anrufen.

Eine vollständige Liste der Dateiattribute finden Sie in der Memberfunktion [MatchesMask.](#matchesmask)

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CFileFind::GetLength](#getlength).

## <a name="cfilefindiscompressed"></a><a name="iscompressed"></a>CFileFind::IsCompressed

Rufen Sie diese Memberfunktion auf, um zu ermitteln, ob die gefundene Datei komprimiert ist.

```
BOOL IsCompressed() const;
```

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Eine komprimierte Datei ist mit FILE_ATTRIBUTE_COMPRESSED gekennzeichnet, einem Dateiattribut, das in der [WIN32_FIND_DATA-Struktur](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) identifiziert wird. Für eine Datei gibt dieses Attribut an, dass alle Daten in der Datei komprimiert sind. Für ein Verzeichnis gibt dieses Attribut an, dass die Komprimierung die Standardeinstellung für neu erstellte Dateien und Unterverzeichnisse ist.

Sie müssen [FindNextFile](#findnextfile) mindestens einmal `IsCompressed`aufrufen, bevor Sie anrufen.

Eine vollständige Liste der Dateiattribute finden Sie in der Memberfunktion [MatchesMask.](#matchesmask)

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CFileFind::GetLength](#getlength).

## <a name="cfilefindisdirectory"></a><a name="isdirectory"></a>CFileFind::IsDirectory

Rufen Sie diese Memberfunktion auf, um zu ermitteln, ob es sich bei der gefundenen Datei um ein Verzeichnis handelt.

```
BOOL IsDirectory() const;
```

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Eine Datei, die ein Verzeichnis ist, wird mit FILE_ATTRIBUTE_DIRECTORY einem Dateiattribut gekennzeichnet, das in der [WIN32_FIND_DATA-Struktur](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) identifiziert wurde.

Sie müssen [FindNextFile](#findnextfile) mindestens einmal `IsDirectory`aufrufen, bevor Sie anrufen.

Eine vollständige Liste der Dateiattribute finden Sie in der Memberfunktion [MatchesMask.](#matchesmask)

### <a name="example"></a>Beispiel

Dieses kleine Programm reverflucht jedes Verzeichnis auf der C:" und druckt den Namen des Verzeichnisses.

[!code-cpp[NVC_MFCFiles#34](../../atl-mfc-shared/reference/codesnippet/cpp/cfilefind-class_4.cpp)]

## <a name="cfilefindisdots"></a><a name="isdots"></a>CFileFind::IsDots

Rufen Sie diese Memberfunktion auf, um beim Durchlaufen von Dateien auf das aktuelle Verzeichnis und die übergeordneten Verzeichnismarkierungen zu testen.

```
virtual BOOL IsDots() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die gefundene Datei den Namen "." oder ".." hat, was darauf hinweist, dass es sich bei der gefundenen Datei tatsächlich um ein Verzeichnis handelt. andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Sie müssen [FindNextFile](#findnextfile) mindestens einmal `IsDots`aufrufen, bevor Sie anrufen.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CFileFind::IsDirectory](#isdirectory).

## <a name="cfilefindishidden"></a><a name="ishidden"></a>CFileFind::IsHidden

Rufen Sie diese Memberfunktion auf, um festzustellen, ob die gefundene Datei ausgeblendet ist.

```
BOOL IsHidden() const;
```

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Ausgeblendete Dateien, die mit FILE_ATTRIBUTE_HIDDEN markiert sind, ein Dateiattribut, das in der [WIN32_FIND_DATA-Struktur](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) identifiziert wird. Eine ausgeblendete Datei ist nicht in einer normalen Verzeichnisliste enthalten.

Sie müssen [FindNextFile](#findnextfile) mindestens einmal `IsHidden`aufrufen, bevor Sie anrufen.

Eine vollständige Liste der Dateiattribute finden Sie in der Memberfunktion [MatchesMask.](#matchesmask)

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CFileFind::GetLength](#getlength).

## <a name="cfilefindisnormal"></a><a name="isnormal"></a>CFileFind::IsNormal

Rufen Sie diese Memberfunktion auf, um festzustellen, ob es sich bei der gefundenen Datei um eine normale Datei handelt.

```
BOOL IsNormal() const;
```

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Dateien, die mit FILE_ATTRIBUTE_NORMAL markiert sind, ein Dateiattribut, das in der [WIN32_FIND_DATA-Struktur](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) identifiziert wird. Für eine normale Datei sind keine anderen Attribute festgelegt. Alle anderen Dateiattribute überschreiben dieses Attribut.

Sie müssen [FindNextFile](#findnextfile) mindestens einmal `IsNormal`aufrufen, bevor Sie anrufen.

Eine vollständige Liste der Dateiattribute finden Sie in der Memberfunktion [MatchesMask.](#matchesmask)

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CFileFind::GetLength](#getlength).

## <a name="cfilefindisreadonly"></a><a name="isreadonly"></a>CFileFind::IsReadOnly

Rufen Sie diese Memberfunktion auf, um festzustellen, ob die gefundene Datei schreibgeschützt ist.

```
BOOL IsReadOnly() const;
```

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Eine schreibgeschützte Datei ist mit FILE_ATTRIBUTE_READONLY gekennzeichnet, einem Dateiattribut, das in der [WIN32_FIND_DATA-Struktur](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) identifiziert wird. Anwendungen können eine solche Datei lesen, aber sie können nicht darauf schreiben oder sie löschen.

Sie müssen [FindNextFile](#findnextfile) mindestens einmal `IsReadOnly`aufrufen, bevor Sie anrufen.

Eine vollständige Liste der Dateiattribute finden Sie in der Memberfunktion [MatchesMask.](#matchesmask)

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CFileFind::GetLength](#getlength).

## <a name="cfilefindissystem"></a><a name="issystem"></a>CFileFind::IsSystem

Rufen Sie diese Memberfunktion auf, um festzustellen, ob es sich bei der gefundenen Datei um eine Systemdatei handelt.

```
BOOL IsSystem() const;
```

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Eine Systemdatei ist mit FILE_ATTRIBUTE_SYSTEM, gekennzeichnet, einem Dateiattribut, das in der [WIN32_FIND_DATA-Struktur](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) identifiziert wurde. Eine Systemdatei ist Teil des Betriebssystems oder wird ausschließlich vom Betriebssystem verwendet.

Sie müssen [FindNextFile](#findnextfile) mindestens einmal `IsSystem`aufrufen, bevor Sie anrufen.

Eine vollständige Liste der Dateiattribute finden Sie in der Memberfunktion [MatchesMask.](#matchesmask)

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CFileFind::GetLength](#getlength).

## <a name="cfilefindistemporary"></a><a name="istemporary"></a>CFileFind::IsTemporary

Rufen Sie diese Memberfunktion auf, um festzustellen, ob es sich bei der gefundenen Datei um eine temporäre Datei handelt.

```
BOOL IsTemporary() const;
```

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Eine temporäre Datei ist mit FILE_ATTRIBUTE_TEMPORARY markiert, einem Dateiattribut, das in der [WIN32_FIND_DATA-Struktur](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) identifiziert wird. Eine temporäre Datei wird für den temporären Speicher verwendet. Anwendungen sollten nur dann in die Datei schreiben, wenn dies unbedingt erforderlich ist. Die meisten Daten der Datei verbleiben im Speicher, ohne auf das Medium geleert zu werden, da die Datei bald gelöscht wird.

Sie müssen [FindNextFile](#findnextfile) mindestens einmal `IsTemporary`aufrufen, bevor Sie anrufen.

Eine vollständige Liste der Dateiattribute finden Sie in der Memberfunktion [MatchesMask.](#matchesmask)

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CFileFind::GetLength](#getlength).

## <a name="cfilefindm_ptm"></a><a name="m_ptm"></a>CFileFind::m_pTM

Zeiger auf `CAtlTransactionManager` ein Objekt.

```
CAtlTransactionManager* m_pTM;
```

### <a name="remarks"></a>Bemerkungen

## <a name="cfilefindmatchesmask"></a><a name="matchesmask"></a>CFileFind::MatchesMask

Rufen Sie diese Memberfunktion auf, um die Dateiattribute in der gefundenen Datei zu testen.

```
virtual BOOL MatchesMask(DWORD dwMask) const;
```

### <a name="parameters"></a>Parameter

*dwMask*<br/>
Gibt ein oder mehrere Dateiattribute an, die in der [WIN32_FIND_DATA-Struktur](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) für die gefundene Datei identifiziert wurden. Um nach mehreren Attributen zu suchen, verwenden Sie den operator bitweise s/ ODER (&#124;). Jede Kombination der folgenden Attribute ist akzeptabel:

- FILE_ATTRIBUTE_ARCHIVE Die Datei ist eine Archivdatei. Anwendungen verwenden dieses Attribut, um Dateien für die Sicherung oder Entfernung zu markieren.

- FILE_ATTRIBUTE_COMPRESSED Die Datei oder das Verzeichnis wird komprimiert. Für eine Datei bedeutet dies, dass alle Daten in der Datei komprimiert werden. Für ein Verzeichnis bedeutet dies, dass die Komprimierung die Standardeinstellung für neu erstellte Dateien und Unterverzeichnisse ist.

- FILE_ATTRIBUTE_DIRECTORY Die Datei ist ein Verzeichnis.

- FILE_ATTRIBUTE_NORMAL Für die Datei sind keine anderen Attribute festgelegt. Dieses Attribut ist nur gültig, wenn es allein verwendet wird. Alle anderen Dateiattribute überschreiben dieses Attribut.

- FILE_ATTRIBUTE_HIDDEN Die Datei ist ausgeblendet. Es ist nicht in einer gewöhnlichen Verzeichnisliste enthalten.

- FILE_ATTRIBUTE_READONLY Die Datei ist schreibgeschützt. Anwendungen können die Datei lesen, aber nicht darauf schreiben oder löschen.

- FILE_ATTRIBUTE_SYSTEM Die Datei ist Teil des Betriebssystems oder wird ausschließlich vom Betriebssystem verwendet.

- FILE_ATTRIBUTE_TEMPORARY Die Datei wird für den temporären Speicher verwendet. Anwendungen sollten nur dann in die Datei schreiben, wenn dies unbedingt erforderlich ist. Die meisten Daten der Datei verbleiben im Speicher, ohne auf das Medium geleert zu werden, da die Datei bald gelöscht wird.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null). Um erweiterte Fehlerinformationen zu erhalten, rufen Sie die Win32-Funktion [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)auf.

### <a name="remarks"></a>Bemerkungen

Sie müssen [FindNextFile](#findnextfile) mindestens einmal `MatchesMask`aufrufen, bevor Sie anrufen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCFiles#35](../../atl-mfc-shared/reference/codesnippet/cpp/cfilefind-class_5.cpp)]

## <a name="see-also"></a>Weitere Informationen

[CObject-Klasse](../../mfc/reference/cobject-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CFtpFileFind-Klasse](../../mfc/reference/cftpfilefind-class.md)<br/>
[CGopherFileFind-Klasse](../../mfc/reference/cgopherfilefind-class.md)<br/>
[CInternetFile-Klasse](../../mfc/reference/cinternetfile-class.md)<br/>
[CGopherFile-Klasse](../../mfc/reference/cgopherfile-class.md)<br/>
[CHttpFile-Klasse](../../mfc/reference/chttpfile-class.md)
