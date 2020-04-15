---
title: CFtpFileFind-Klasse
ms.date: 11/04/2016
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
ms.openlocfilehash: cf4afb4a683c2d0cf5f2977107d02ee300a53cb0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373745"
---
# <a name="cftpfilefind-class"></a>CFtpFileFind-Klasse

Unterstützt die Internetsuche nach Dateien auf FTP-Servern.

## <a name="syntax"></a>Syntax

```
class CFtpFileFind : public CFileFind
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CFtpFileFind::CFtpFileFind](#cftpfilefind)|Erstellt ein `CFtpFileFind`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CFtpFileFind::FindFile](#findfile)|Sucht eine Datei auf einem FTP-Server.|
|[CFtpFileFind::FindNextFile](#findnextfile)|Setzt die Dateisuche nach einem vorherigen Aufruf von [FindFile](#findfile)fort.|
|[CFtpFileFind::GetFileURL](#getfileurl)|Ruft die URL der gefundenen Datei ab, einschließlich des Pfads.|

## <a name="remarks"></a>Bemerkungen

`CFtpFileFind`enthält Memberfunktionen, die eine Suche starten, eine Datei suchen und die URL oder andere beschreibende Informationen über die Datei zurückgeben.

Andere MFC-Klassen, die für die Suche im Internet und in lokalen Dateien entwickelt wurden, sind [CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md) und [CFileFind](../../mfc/reference/cfilefind-class.md). Zusammen `CFtpFileFind`mit bieten diese Klassen einen nahtlosen Mechanismus für den Client, um bestimmte Dateien zu finden, unabhängig vom Serverprotokoll oder Dateityp (entweder ein lokaler Computer oder ein Remoteserver). Beachten Sie, dass es keine MFC-Klasse für die Suche auf HTTP-Servern gibt, da HTTP die direkte Dateimanipulation nicht unterstützt, die für die Suche erforderlich ist.

Weitere Informationen zur Verwendung `CFtpFileFind` und zu den anderen WinInet-Klassen finden Sie im Artikel [Internetprogrammierung mit WinInet](../../mfc/win32-internet-extensions-wininet.md).

## <a name="example"></a>Beispiel

Der folgende Code veranschaulicht, wie alle Dateien im aktuellen Verzeichnis des FTP-Servers aufgezählt werden.

[!code-cpp[NVC_MFCWinInet#8](../../mfc/codesnippet/cpp/cftpfilefind-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CFileFind](../../mfc/reference/cfilefind-class.md)

`CFtpFileFind`

## <a name="requirements"></a>Anforderungen

**Kopf:** afxinet.h

## <a name="cftpfilefindcftpfilefind"></a><a name="cftpfilefind"></a>CFtpFileFind::CFtpFileFind

Diese Memberfunktion wird aufgerufen, um ein `CFtpFileFind` Objekt zu erstellen.

```
explicit CFtpFileFind(
    CFtpConnection* pConnection,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>Parameter

*pConnection*<br/>
Ein Zeiger auf ein `CFtpConnection`-Objekt. Sie können eine FTP-Verbindung erhalten, indem Sie [CInternetSession::GetFtpConnection](../../mfc/reference/cinternetsession-class.md#getftpconnection)aufrufen.

*dwContext*<br/>
Der Kontextbezeichner für das `CFtpFileFind` Objekt. Weitere Informationen zu diesem Parameter finden Sie unter **Hinweise.**

### <a name="remarks"></a>Bemerkungen

Der Standardwert für *dwContext* wird von `CFtpFileFind` MFC aus dem [CInternetSession-Objekt,](../../mfc/reference/cinternetsession-class.md) das das `CFtpFileFind` Objekt erstellt hat, an das Objekt gesendet. Sie können die Standardeinstellung überschreiben, um den Kontextbezeichner auf einen Wert Ihrer Wahl festzulegen. Der Kontextbezeichner wird an [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) zurückgegeben, um den Status für das Objekt bereitzustellen, mit dem er identifiziert wird. Weitere Informationen zum Kontextbezeichner finden Sie im Artikel [Internet First Steps: WinInet.](../../mfc/wininet-basics.md)

### <a name="example"></a>Beispiel

  Siehe das Beispiel in der Klassenübersicht weiter oben in diesem Thema.

## <a name="cftpfilefindfindfile"></a><a name="findfile"></a>CFtpFileFind::FindFile

Rufen Sie diese Memberfunktion auf, um eine FTP-Datei zu finden.

```
virtual BOOL FindFile(
    LPCTSTR pstrName = NULL,
    DWORD dwFlags = INTERNET_FLAG_RELOAD);
```

### <a name="parameters"></a>Parameter

*pstrName*<br/>
Ein Zeiger auf eine Zeichenfolge, die den Namen der zu suchenden Datei enthält. Wenn NULL, führt der Aufruf eine Platzhaltersuche (*) durch.

*dwFlags*<br/>
Die Flags, die beschreiben, wie diese Sitzung behandelt wird. Diese Flags können mit dem bitweisen OR-Operator (&#124;) kombiniert werden und lauten wie folgt:

- INTERNET_FLAG_RELOAD Abrufen der Daten aus dem Draht, auch wenn sie lokal zwischengespeichert sind. Dies ist das Standardflag.

- INTERNET_FLAG_DONT_CACHE Die Daten nicht lokal oder in Gateways zwischenspeichern.

- INTERNET_FLAG_RAW_DATA überschreiben sie die Standardeinstellung, um die Rohdaten zurückzugeben [(WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) Strukturen für FTP).

- INTERNET_FLAG_SECURE Sichert Transaktionen auf dem Draht mit Secure Sockets Layer oder PCT. Dieses Flag gilt nur für HTTP-Anforderungen.

- INTERNET_FLAG_EXISTING_CONNECT Wenn möglich, verwenden Sie die vorhandenen `FindFile` Verbindungen zum Server für neue Anforderungen, anstatt für jede Anforderung eine neue Sitzung zu erstellen.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null). Um erweiterte Fehlerinformationen zu erhalten, rufen Sie die Win32-Funktion [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)auf.

### <a name="remarks"></a>Bemerkungen

Nach `FindFile` dem Aufruf zum Abrufen der ersten FTP-Datei können Sie [FindNextFile](#findnextfile) aufrufen, um nachfolgende FTP-Dateien abzurufen.

### <a name="example"></a>Beispiel

  Siehe das frühere Beispiel in diesem Thema.

## <a name="cftpfilefindfindnextfile"></a><a name="findnextfile"></a>CFtpFileFind::FindNextFile

Rufen Sie diese Memberfunktion auf, um eine Dateisuche fortzusetzen, die mit einem Aufruf der [FindFile-Memberfunktion](#findfile) begonnen wurde.

```
virtual BOOL FindNextFile();
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn mehr Dateien vorhanden sind; Null, wenn die gefundene Datei die letzte im Verzeichnis ist oder wenn ein Fehler aufgetreten ist. Um erweiterte Fehlerinformationen zu erhalten, rufen Sie die Win32-Funktion [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)auf. Wenn die gefundene Datei die letzte Datei im Verzeichnis ist oder `GetLastError` keine übereinstimmenden Dateien gefunden werden können, gibt die Funktion ERROR_NO_MORE_FILES zurück.

### <a name="remarks"></a>Bemerkungen

Sie müssen diese Funktion mindestens einmal aufrufen, bevor Sie eine Attributfunktion aufrufen (siehe [CFileFind::FindNextFile](../../mfc/reference/cfilefind-class.md#findnextfile)).

`FindNextFile`umschließt die Win32-Funktion [FindNextFile](/windows/win32/api/fileapi/nf-fileapi-findnextfilew).

### <a name="example"></a>Beispiel

  Siehe das Beispiel weiter oben in diesem Thema.

## <a name="cftpfilefindgetfileurl"></a><a name="getfileurl"></a>CFtpFileFind::GetFileURL

Rufen Sie diese Memberfunktion auf, um die URL der angegebenen Datei abzurufen.

```
CString GetFileURL() const;
```

### <a name="return-value"></a>Rückgabewert

Die Datei und der Pfad des URL (Universal Resource Locator).

### <a name="remarks"></a>Bemerkungen

`GetFileURL`ist der Memberfunktion [CFileFind::GetFilePath](../../mfc/reference/cfilefind-class.md#getfilepath)ähnlich, mit der Ausnahme, dass die URL im Formular `ftp://moose/dir/file.txt`zurückgegeben wird.

## <a name="see-also"></a>Siehe auch

[CFileFind-Klasse](../../mfc/reference/cfilefind-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CGopherFileFind-Klasse](../../mfc/reference/cgopherfilefind-class.md)<br/>
[CInternetFile-Klasse](../../mfc/reference/cinternetfile-class.md)<br/>
[CGopherFile-Klasse](../../mfc/reference/cgopherfile-class.md)<br/>
[CHttpFile-Klasse](../../mfc/reference/chttpfile-class.md)
