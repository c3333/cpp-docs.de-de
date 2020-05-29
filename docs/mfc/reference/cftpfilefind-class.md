---
title: CFtpFileFind-Klasse
ms.date: 05/28/2020
f1_keywords:
- CFtpFileFind
- AFXINET/CFtpFileFind
- AFXINET/CFtpFileFind::CFtpFileFind
- AFXINET/CFtpFileFind::FindFile
- AFXINET/CFtpFileFind::FindNextFile
- AFXINET/CFtpFileFind::GetFileURL
helpviewer_keywords:
- CFtpFileFind [MFC], CFtpFileFind
- CFtpFileFind [MFC], FindFile
- CFtpFileFind [MFC], FindNextFile
- CFtpFileFind [MFC], GetFileURL
ms.assetid: 9667cf01-657f-4b11-b9db-f11e5a7b4e4c
ms.openlocfilehash: e53e16f738f0436cbd02074c10ca24dbcc9d0fd8
ms.sourcegitcommit: 426e327c9f7c3a3b02300e3f924f9786d62958e9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2020
ms.locfileid: "84206231"
---
# <a name="cftpfilefind-class"></a>CFtpFileFind-Klasse

Unterstützt die Internetsuche nach Dateien auf FTP-Servern.

## <a name="syntax"></a>Syntax

```
class CFtpFileFind : public CFileFind
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|Beschreibung|
|----------|-----------------|
|[CFtpFileFind:: CFtpFileFind](#cftpfilefind)|Erstellt ein `CFtpFileFind`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|name|Beschreibung|
|----------|-----------------|
|[CFtpFileFind:: FindFile](#findfile)|Sucht eine Datei auf einem FTP-Server.|
|[CFtpFileFind:: FindNextFile](#findnextfile)|Setzt eine Dateisuche von einem vorherigen Befehl von " [FindFile](#findfile)" fort.|
|[CFtpFileFind:: getfileurl](#getfileurl)|Ruft die URL (einschließlich Pfad) der gefundenen Datei ab.|

## <a name="remarks"></a>Hinweise

`CFtpFileFind`umfasst Member-Funktionen, die eine Suche starten, eine Datei suchen und die URL oder andere beschreibende Informationen über die Datei zurückgeben.

Andere MFC-Klassen, die für das Internet und die lokale Datei durchsucht wurden, umfassen [CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md) und [CFileFind](../../mfc/reference/cfilefind-class.md). In kombinieren `CFtpFileFind` Diese Klassen eine nahtlose Methode, mit der der Client bestimmte Dateien suchen kann, unabhängig vom Server Protokoll oder Dateityp (entweder ein lokaler Computer oder ein Remote Server). Es gibt keine MFC-Klasse für die Suche nach HTTP-Servern, da HTTP die direkte Dateibearbeitung nicht unterstützt, die für Suchvorgänge erforderlich ist.

Weitere Informationen zur Verwendung von `CFtpFileFind` und der anderen WinInet-Klassen finden Sie im Artikel [Internet Programmierung mit WinInet](../../mfc/win32-internet-extensions-wininet.md).

## <a name="example"></a>Beispiel

Der folgende Code veranschaulicht, wie alle Dateien im aktuellen Verzeichnis des FTP-Servers aufgelistet werden.

[!code-cpp[NVC_MFCWinInet#8](../../mfc/codesnippet/cpp/cftpfilefind-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)

[CFileFind](../../mfc/reference/cfilefind-class.md)

`CFtpFileFind`

## <a name="requirements"></a>Anforderungen

**Header:** AFXINET. h

## <a name="cftpfilefindcftpfilefind"></a><a name="cftpfilefind"></a>CFtpFileFind:: CFtpFileFind

Diese Member-Funktion wird aufgerufen, um ein-Objekt zu erstellen `CFtpFileFind` .

```
explicit CFtpFileFind(
    CFtpConnection* pConnection,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>Parameter

*pConnection*<br/>
Ein Zeiger auf ein `CFtpConnection`-Objekt. Sie können eine FTP-Verbindung abrufen, indem Sie [cinternetzession:: GetFtpConnection](../../mfc/reference/cinternetsession-class.md#getftpconnection)aufrufen.

*dwcontext*<br/>
Der Kontext Bezeichner für das- `CFtpFileFind` Objekt. Weitere Informationen finden Sie in **den folgenden Hinweisen**.

### <a name="remarks"></a>Hinweise

Der Standardwert für *dwcontext* wird von MFC an das- `CFtpFileFind` Objekt aus dem [cinternetzession](../../mfc/reference/cinternetsession-class.md) -Objekt gesendet, das das Objekt erstellt hat `CFtpFileFind` . Sie können die Standardeinstellung überschreiben, um den Kontext Bezeichner auf einen Wert Ihrer Wahl festzulegen. Der Kontext Bezeichner wird an [cinternetzession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) zurückgegeben, um den Status für das Objekt bereitzustellen, mit dem es identifiziert wird. Weitere Informationen zum Kontext Bezeichner finden Sie im Artikel [Internet First Steps: WinInet](../../mfc/wininet-basics.md) .

### <a name="example"></a>Beispiel

  Siehe das Beispiel in der Übersicht über die-Klasse weiter oben in diesem Thema.

## <a name="cftpfilefindfindfile"></a><a name="findfile"></a>CFtpFileFind:: FindFile

Diese Member-Funktion wird aufgerufen, um eine FTP-Datei zu suchen.

```
virtual BOOL FindFile(
    LPCTSTR pstrName = NULL,
    DWORD dwFlags = INTERNET_FLAG_RELOAD);
```

### <a name="parameters"></a>Parameter

*pstrinname*<br/>
Ein Zeiger auf eine Zeichenfolge, die den Namen der zu suchenden Datei enthält. Wenn der Wert NULL ist, führt der-Befehl eine Platzhalter Suche durch (*).

*dwFlags*<br/>
Die Flags, die beschreiben, wie diese Sitzung behandelt werden soll. Diese Flags können mit dem bitweisen OR-Operator (&#124;) kombiniert werden und lauten wie folgt:

- `INTERNET_FLAG_RELOAD`Sie erhalten die Daten aus dem Netzwerk, auch wenn Sie lokal zwischengespeichert werden. Dies ist das Standardflag.

- `INTERNET_FLAG_DONT_CACHE`Zwischenspeichern Sie die Daten weder lokal noch in Gateways.

- `INTERNET_FLAG_RAW_DATA`Überschreiben Sie die Standardeinstellung, um die Rohdaten ( [WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) -Strukturen für FTP) zurückzugeben.

- `INTERNET_FLAG_SECURE`Sichert Transaktionen mit Secure Sockets Layer oder PCT. Dieses Flag gilt nur für HTTP-Anforderungen.

- `INTERNET_FLAG_EXISTING_CONNECT`Verwenden Sie nach Möglichkeit die vorhandenen Verbindungen mit dem Server für neue `FindFile` Anforderungen, anstatt eine neue Sitzung für jede Anforderung zu erstellen.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null). Um erweiterte Fehlerinformationen abzurufen, nennen Sie die Win32-Funktion [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

### <a name="remarks"></a>Hinweise

Nachdem `FindFile` Sie aufgerufen haben, um die erste FTP-Datei abzurufen, können Sie [FindNextFile](#findnextfile) aufrufen, um nachfolgende FTP-Dateien abzurufen.

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im vorherigen Beispiel in diesem Thema.

## <a name="cftpfilefindfindnextfile"></a><a name="findnextfile"></a>CFtpFileFind:: FindNextFile

Diese Member-Funktion wird aufgerufen, um eine Dateisuche fortzusetzen, die mit einem Aufrufder [FindFile](#findfile) -Element Funktion begonnen wurde.

```
virtual BOOL FindNextFile();
```

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn weitere Dateien vorhanden sind. 0 (null), wenn die gefundene Datei das letzte im Verzeichnis ist, oder, wenn ein Fehler aufgetreten ist. Um erweiterte Fehlerinformationen abzurufen, nennen Sie die Win32-Funktion [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror). Wenn es sich bei der gefundenen Datei um die letzte Datei im Verzeichnis handelt oder wenn keine übereinstimmenden Dateien gefunden werden können, `GetLastError` gibt die Funktion ERROR_NO_MORE_FILES zurück.

### <a name="remarks"></a>Hinweise

Sie müssen diese Funktion mindestens einmal aufrufen, bevor Sie eine beliebige Attribut Funktion aufrufen (siehe [CFileFind:: FindNextFile](../../mfc/reference/cfilefind-class.md#findnextfile)).

`FindNextFile`umschließt die Win32-Funktion " [FindNextFile](/windows/win32/api/fileapi/nf-fileapi-findnextfilew)".

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel weiter oben in diesem Thema.

## <a name="cftpfilefindgetfileurl"></a><a name="getfileurl"></a>CFtpFileFind:: getfileurl

Mit dieser Member-Funktion können Sie die URL der angegebenen Datei abrufen.

```
CString GetFileURL() const;
```

### <a name="return-value"></a>Rückgabewert

Die Datei und der Pfad der URL (Universal Resource Locator).

### <a name="remarks"></a>Hinweise

`GetFileURL`ähnelt der Member-Funktion [CFileFind:: GetFilePath](../../mfc/reference/cfilefind-class.md#getfilepath) , mit der Ausnahme, dass Sie das Ergebnis im URL-Format bereitstellt. Wie bei `CFileFind::GetFilePath` enthält das Ergebnis nicht den Dateinamen. Beispielsweise wird `file1.txt` in der-Wert `//moose/dir/file1.txt:` zurückgegeben `ftp://moose/dir/` .

## <a name="see-also"></a>Weitere Informationen:

[CFileFind-Klasse](../../mfc/reference/cfilefind-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CGopherFileFind-Klasse](../../mfc/reference/cgopherfilefind-class.md)<br/>
[CInternetFile-Klasse](../../mfc/reference/cinternetfile-class.md)<br/>
[CGopherFile-Klasse](../../mfc/reference/cgopherfile-class.md)<br/>
[CHttpFile-Klasse](../../mfc/reference/chttpfile-class.md)
