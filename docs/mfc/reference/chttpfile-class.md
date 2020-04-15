---
title: CHttpFile-Klasse
ms.date: 11/04/2016
f1_keywords:
- CHttpFile
- AFXINET/CHttpFile
- AFXINET/CHttpFile::CHttpFile
- AFXINET/CHttpFile::AddRequestHeaders
- AFXINET/CHttpFile::EndRequest
- AFXINET/CHttpFile::GetFileURL
- AFXINET/CHttpFile::GetObject
- AFXINET/CHttpFile::GetVerb
- AFXINET/CHttpFile::QueryInfo
- AFXINET/CHttpFile::QueryInfoStatusCode
- AFXINET/CHttpFile::SendRequest
- AFXINET/CHttpFile::SendRequestEx
helpviewer_keywords:
- CHttpFile [MFC], CHttpFile
- CHttpFile [MFC], AddRequestHeaders
- CHttpFile [MFC], EndRequest
- CHttpFile [MFC], GetFileURL
- CHttpFile [MFC], GetObject
- CHttpFile [MFC], GetVerb
- CHttpFile [MFC], QueryInfo
- CHttpFile [MFC], QueryInfoStatusCode
- CHttpFile [MFC], SendRequest
- CHttpFile [MFC], SendRequestEx
ms.assetid: 399e7c68-bbce-4374-8c55-206e9c7baac6
ms.openlocfilehash: cba3ba7d86577703de2bf5709d66bbd5e0298863
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368395"
---
# <a name="chttpfile-class"></a>CHttpFile-Klasse

Stellt die Funktionalität bereit, um Dateien auf einem HTTP-Server anfordern und zu lesen.

## <a name="syntax"></a>Syntax

```
class CHttpFile : public CInternetFile
```

## <a name="members"></a>Member

### <a name="protected-constructors"></a>Geschützte Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CHttpFile::CHttpFile](#chttpfile)|Erstellt ein `CHttpFile` -Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CHttpFile::AddRequestHeaders](#addrequestheaders)|Fügt der Anforderung Header hinzu, die an einen HTTP-Server gesendet werden.|
|[CHttpFile::EndRequest](#endrequest)|Beendet eine Anforderung, die mit der [SendRequestEx-Memberfunktion](#sendrequestex) an einen HTTP-Server gesendet wird.|
|[CHttpFile::GetFileURL](#getfileurl)|Ruft die URL für die angegebene Datei ab.|
|[CHttpFile::GetObject](#getobject)|Ruft das Zielobjekt des Verbs in einer Anforderung an einen HTTP-Server ab.|
|[CHttpFile::GetVerb](#getverb)|Ruft das Verb ab, das in einer Anforderung an einen HTTP-Server verwendet wurde.|
|[CHttpFile::QueryInfo](#queryinfo)|Gibt die Antwort- oder Anforderungsheader vom HTTP-Server zurück.|
|[CHttpFile::QueryInfoStatusCode](#queryinfostatuscode)|Ruft den Statuscode ab, der einer HTTP-Anforderung zugeordnet ist, und platziert ihn im angegebenen `dwStatusCode` Parameter.|
|[CHttpFile::SendRequest](#sendrequest)|Sendet eine Anforderung an einen HTTP-Server.|
|[CHttpFile::SendRequestEx](#sendrequestex)|Sendet eine Anforderung mithilfe der [Write-](../../mfc/reference/cinternetfile-class.md#write) oder `CInternetFile` [WriteString-Methoden](../../mfc/reference/cinternetfile-class.md#writestring) von an einen HTTP-Server.|

## <a name="remarks"></a>Bemerkungen

Wenn Ihre Internetsitzung Daten von einem HTTP-Server `CHttpFile`liest, müssen Sie eine Instanz von erstellen.

Weitere Informationen zur `CHttpFile` Funktionsweise mit den anderen MFC-Internetklassen finden Sie im Artikel [Internetprogrammierung mit WinInet](../../mfc/win32-internet-extensions-wininet.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[CStdioFile](../../mfc/reference/cstdiofile-class.md)

[CInternetFile](../../mfc/reference/cinternetfile-class.md)

`CHttpFile`

## <a name="requirements"></a>Anforderungen

**Kopf:** afxinet.h

## <a name="chttpfileaddrequestheaders"></a><a name="addrequestheaders"></a>CHttpFile::AddRequestHeaders

Rufen Sie diese Memberfunktion auf, um dem HTTP-Anforderungshandle einen oder mehrere HTTP-Anforderungsheader hinzuzufügen.

```
BOOL AddRequestHeaders(
    LPCTSTR pstrHeaders,
    DWORD dwFlags = HTTP_ADDREQ_FLAG_ADD_IF_NEW,
    int dwHeadersLen = -1);

BOOL AddRequestHeaders(
    CString& str,
    DWORD dwFlags = HTTP_ADDREQ_FLAG_ADD_IF_NEW);
```

### <a name="parameters"></a>Parameter

*pstrHeaders*<br/>
Ein Zeiger auf eine Zeichenfolge, die den Header oder die Header enthält, die an die Anforderung angehängt werden sollen. Jeder Header muss durch ein CR/LF-Paar beendet werden.

*dwFlags*<br/>
Ändert die Semantik der neuen Header. Dabei kann es sich um eine der folgenden Methoden handeln:

- HTTP_ADDREQ_FLAG_COALESCE Merges-Header mit demselben Namen, indem das Flag verwendet wird, um den ersten Header hinzuzufügen, der dem nachfolgenden Header gefunden wurde. Beispiel:\*"Accept: text/ " gefolgt von\*"Accept: audio/ " ergibt die Bildung\*der\*einzelnen Kopfzeile "Accept: text/ , audio/ ". Es ist An der Aufforderungsanwendung, ein kohäsives Schema in Bezug auf Daten sicherzustellen, die von Anfragen empfangen werden, die mit zusammengeschlossenen oder separaten Headern gesendet werden.

- HTTP_ADDREQ_FLAG_REPLACE Führt ein Entfernen und Hinzufügen aus, um den aktuellen Header zu ersetzen. Der Headername wird verwendet, um den aktuellen Header zu entfernen, und der vollständige Wert wird verwendet, um den neuen Header hinzuzufügen. Wenn der Headerwert leer ist und der Header gefunden wird, wird er entfernt. Wenn nicht leer, wird der Header-Wert ersetzt.

- HTTP_ADDREQ_FLAG_ADD_IF_NEW fügt den Header nur hinzu, wenn er noch nicht vorhanden ist. Wenn einer vorhanden ist, wird ein Fehler zurückgegeben.

- HTTP_ADDREQ_FLAG_ADD wird mit REPLACE verwendet. Fügt den Header hinzu, wenn er nicht vorhanden ist.

*dwHeadersLen*<br/>
Die Länge von *pstrHeaders*in Zeichen . Wenn dies -1L ist, wird *von pstrHeaders* angenommen, dass sie Null-Termin sind, und die Länge wird berechnet.

*Str*<br/>
Ein Verweis auf ein [CString-Objekt,](../../atl-mfc-shared/reference/cstringt-class.md) das den hinzuzufügenden Anforderungsheader oder die hinzuzufügenden Header enthält.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null). Wenn der Aufruf fehlschlägt, kann die Win32-Funktion [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) aufgerufen werden, um die Ursache des Fehlers zu ermitteln.

### <a name="remarks"></a>Bemerkungen

`AddRequestHeaders`fügt zusätzliche Header im freien Format an das HTTP-Anforderungshandle an. Es ist für die Verwendung durch anspruchsvolle Clients vorgesehen, die eine detaillierte Kontrolle über die genaue Anforderung benötigen, die an den HTTP-Server gesendet wird.

> [!NOTE]
> Die Anwendung kann mehrere Header in *pstrHeaders* oder *str* für einen `AddRequestHeaders` Aufruf mit HTTP_ADDREQ_FLAG_ADD oder HTTP_ADDREQ_FLAG_ADD_IF_NEW übergeben. Wenn die Anwendung versucht, einen Header mithilfe von HTTP_ADDREQ_FLAG_REMOVE oder HTTP_ADDREQ_FLAG_REPLACE zu entfernen oder zu ersetzen, kann nur ein Header in *lpszHeaders*bereitgestellt werden.

## <a name="chttpfilechttpfile"></a><a name="chttpfile"></a>CHttpFile::CHttpFile

Diese Memberfunktion wird aufgerufen, um ein `CHttpFile` Objekt zu erstellen.

```
CHttpFile(
    HINTERNET hFile,
    HINTERNET hSession,
    LPCTSTR pstrObject,
    LPCTSTR pstrServer,
    LPCTSTR pstrVerb,
    DWORD_PTR dwContext);

CHttpFile(
    HINTERNET hFile,
    LPCTSTR pstrVerb,
    LPCTSTR pstrObject,
    CHttpConnection* pConnection);
```

### <a name="parameters"></a>Parameter

*hDatei*<br/>
Ein Handle für eine Internetdatei.

*hSession*<br/>
Ein Handle für eine Internetsitzung.

*pstrObject*<br/>
Ein Zeiger auf eine `CHttpFile` Zeichenfolge, die das Objekt enthält.

*pstrServer*<br/>
Ein Zeiger auf eine Zeichenfolge, die den Namen des Servers enthält.

*pstrVerb*<br/>
Ein Zeiger auf eine Zeichenfolge, die die Methode enthält, die beim Senden der Anforderung verwendet werden soll. Kann POST, HEAD oder GET sein.

*dwContext*<br/>
Der Kontextbezeichner für das `CHttpFile` Objekt. Weitere Informationen zu diesem Parameter finden Sie unter **Hinweise.**

*pConnection*<br/>
Ein Zeiger auf ein [CHttpConnection-Objekt.](../../mfc/reference/chttpconnection-class.md)

### <a name="remarks"></a>Bemerkungen

Sie erstellen `CHttpFile` niemals ein Objekt direkt. rufen Sie stattdessen [CInternetSession::OpenURL](../../mfc/reference/cinternetsession-class.md#openurl) oder [CHttpConnection::OpenRequest](../../mfc/reference/chttpconnection-class.md#openrequest) auf.

Der Standardwert `dwContext` für wird von `CHttpFile` MFC aus dem [CInternetSession-Objekt,](../../mfc/reference/cinternetsession-class.md) das das `CHttpFile` Objekt erstellt hat, an das Objekt gesendet. Wenn Sie `CInternetSession::OpenURL` `CHttpConnection` ein `CHttpFile` Objekt aufrufen oder erstellen, können Sie die Standardeinstellung überschreiben, um den Kontextbezeichner auf einen Wert Ihrer Wahl festzulegen. Der Kontextbezeichner wird an [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) zurückgegeben, um den Status für das Objekt bereitzustellen, mit dem er identifiziert wird. Weitere Informationen zum Kontextbezeichner finden Sie im Artikel [Internet First Steps: WinInet.](../../mfc/wininet-basics.md)

## <a name="chttpfileendrequest"></a><a name="endrequest"></a>CHttpFile::EndRequest

Rufen Sie diese Memberfunktion auf, um eine Anforderung zu beenden, die an einen HTTP-Server mit der [SendRequestEx-Memberfunktion](#sendrequestex) gesendet wird.

```
BOOL EndRequest(
    DWORD dwFlags = 0,
    LPINTERNET_BUFFERS lpBuffIn = NULL,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>Parameter

*dwFlags*<br/>
Flags, die den Vorgang beschreiben. Eine Liste der entsprechenden Flags finden Sie unter [HttpEndRequest](/windows/win32/api/wininet/nf-wininet-httpendrequestw) im Windows SDK.

*lpBuffIn*<br/>
Zeiger auf eine initialisierte [INTERNET_BUFFERS,](/windows/win32/api/wininet/ns-wininet-internet_buffersw) die den für den Vorgang verwendeten Eingabepuffer beschreibt.

*dwContext*<br/>
Der Kontextbezeichner für den `CHttpFile`-Vorgang. Weitere Informationen zu diesem Parameter finden Sie unter Hinweise.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null). Wenn der Aufruf fehlschlägt, ermitteln Sie die Ursache des Fehlers, indem Sie das ausgelöste [CInternetException-Objekt](../../mfc/reference/cinternetexception-class.md) untersuchen.

### <a name="remarks"></a>Bemerkungen

Der Standardwert für *dwContext* wird von `CHttpFile` MFC aus dem [CInternetSession-Objekt,](../../mfc/reference/cinternetsession-class.md) das das `CHttpFile` Objekt erstellt hat, an das Objekt gesendet. Wenn Sie [CInternetSession::OpenURL](../../mfc/reference/cinternetsession-class.md#openurl) oder [CHttpConnection](../../mfc/reference/chttpconnection-class.md) aufrufen, um ein `CHttpFile` Objekt zu erstellen, können Sie die Standardeinstellung überschreiben, um den Kontextbezeichner auf einen Wert Ihrer Wahl festzulegen. Der Kontextbezeichner wird an [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) zurückgegeben, um den Status für das Objekt bereitzustellen, mit dem er identifiziert wird. Weitere Informationen zum Kontextbezeichner finden Sie im Artikel [Internet First Steps: WinInet.](../../mfc/wininet-basics.md)

## <a name="chttpfilegetfileurl"></a><a name="getfileurl"></a>CHttpFile::GetFileURL

Rufen Sie diese Memberfunktion auf, um den Namen der HTTP-Datei als URL abzurufen.

```
virtual CString GetFileURL() const;
```

### <a name="return-value"></a>Rückgabewert

Ein [CString-Objekt,](../../atl-mfc-shared/reference/cstringt-class.md) das eine URL enthält, die auf die dieser Datei zugeordnete Ressource verweist.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Memberfunktion nur nach einem `CHttpFile` erfolgreichen Aufruf von [SendRequest](#sendrequest) oder für ein Objekt, das erfolgreich von [OpenURL](../../mfc/reference/cinternetsession-class.md#openurl)erstellt wurde.

## <a name="chttpfilegetobject"></a><a name="getobject"></a>CHttpFile::GetObject

Rufen Sie diese Memberfunktion auf, um `CHttpFile`den Namen des Objekts abzurufen, das diesem zugeordnet ist.

```
CString GetObject() const;
```

### <a name="return-value"></a>Rückgabewert

Ein [CString-Objekt,](../../atl-mfc-shared/reference/cstringt-class.md) das den Namen des Objekts enthält.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Memberfunktion nur nach einem `CHttpFile` erfolgreichen Aufruf von [SendRequest](#sendrequest) oder für ein Objekt, das erfolgreich von [OpenURL](../../mfc/reference/cinternetsession-class.md#openurl)erstellt wurde.

## <a name="chttpfilegetverb"></a><a name="getverb"></a>CHttpFile::GetVerb

Rufen Sie diese Memberfunktion auf, um das `CHttpFile`HTTP-Verb (oder die Methode) abzurufen, das dieser verknüpft ist.

```
CString GetVerb() const;
```

### <a name="return-value"></a>Rückgabewert

Ein [CString-Objekt,](../../atl-mfc-shared/reference/cstringt-class.md) das den Namen des HTTP-Verbs (oder der Methode) enthält.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Memberfunktion nur nach einem `CHttpFile` erfolgreichen Aufruf von [SendRequest](#sendrequest) oder für ein Objekt, das erfolgreich von [OpenURL](../../mfc/reference/cinternetsession-class.md#openurl)erstellt wurde.

## <a name="chttpfilequeryinfo"></a><a name="queryinfo"></a>CHttpFile::QueryInfo

Rufen Sie diese Memberfunktion auf, um Antwort- oder Anforderungsheader von einer HTTP-Anforderung zurückzugeben.

```
BOOL QueryInfo(
    DWORD dwInfoLevel,
    LPVOID lpvBuffer,
    LPDWORD lpdwBufferLength,
    LPDWORD lpdwIndex = NULL) const;

BOOL QueryInfo(
    DWORD dwInfoLevel,
    CString& str,
    LPDWORD dwIndex = NULL) const;

BOOL QueryInfo(
    DWORD dwInfoLevel,
    SYSTEMTIME* pSysTime,
    LPDWORD dwIndex = NULL) const;
```

### <a name="parameters"></a>Parameter

*dwInfoLevel*<br/>
Eine Kombination aus dem abzufragenden Attribut und den folgenden Flags, die den Typ der angeforderten Informationen angeben:

- HTTP_QUERY_CUSTOM Sucht den Headernamen und gibt diesen Wert bei der Ausgabe in *lpvBuffer* zurück. HTTP_QUERY_CUSTOM eine Assertion auslöst, wenn der Header nicht gefunden wird.

- HTTP_QUERY_FLAG_REQUEST_HEADERS In der Regel fragt die Anwendung die Antwortheader ab, aber eine Anwendung kann auch Anforderungsheader mithilfe dieses Flags abfragen.

- HTTP_QUERY_FLAG_SYSTEMTIME Für die Header, deren Wert eine Datums-/Uhrzeitzeichenfolge ist, z. B. "Last-Modified-Time", gibt dieses Flag den Headerwert als standardmäßige [Win32-SYSTEMTIME-Struktur](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) zurück, für die die Anwendung die Daten nicht analysieren muss. Wenn Sie dieses Flag verwenden, können `SYSTEMTIME` Sie die Außerkraftsetzung der Funktion verwenden.

- HTTP_QUERY_FLAG_NUMBER Für Die Header, deren Wert eine Zahl ist, z. B. der Statuscode, gibt dieses Flag die Daten als 32-Bit-Nummer zurück.

Eine Liste der möglichen Werte finden Sie im Abschnitt **"Bemerkungen".**

*lpvBuffer*<br/>
Ein Zeiger auf den Puffer, der die Informationen empfängt.

*lpdwBufferLength*<br/>
Bei der Eingabe zeigt dies auf einen Wert, der die Länge des Datenpuffers in der Anzahl der Zeichen oder Bytes enthält. Ausführlichere Informationen zu diesem Parameter finden Sie im Abschnitt **"Bemerkungen".**

*lpdwIndex*<br/>
Ein Zeiger auf einen nullbasierten Headerindex. Kann den Wert NULL haben. Verwenden Sie dieses Flag, um mehrere Header mit demselben Namen aufzuzählen. Bei der Eingabe gibt *lpdwIndex* den Index des angegebenen Headers an, der zurückgegeben werden soll. Bei der Ausgabe gibt *lpdwIndex* den Index des nächsten Headers an. Wenn der nächste Index nicht gefunden werden kann, wird ERROR_HTTP_HEADER_NOT_FOUND zurückgegeben.

*Str*<br/>
Ein Verweis auf das [CString-Objekt,](../../atl-mfc-shared/reference/cstringt-class.md) das die zurückgegebenen Informationen empfängt.

*dwIndex*<br/>
Ein Indexwert. Siehe *lpdwIndex*.

*pSysTime*<br/>
Ein Zeiger auf eine Win32 [SYSTEMTIME-Struktur.](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null). Wenn der Aufruf fehlschlägt, kann die Win32-Funktion [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) aufgerufen werden, um die Ursache des Fehlers zu ermitteln.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Memberfunktion nur nach einem `CHttpFile` erfolgreichen Aufruf von [SendRequest](#sendrequest) oder für ein Objekt, das erfolgreich von [OpenURL](../../mfc/reference/cinternetsession-class.md#openurl)erstellt wurde.

Sie können die folgenden Datentypen abrufen: `QueryInfo`

- Zeichenfolgen (Standard)

- `SYSTEMTIME`(für "Data:" "Expires:" etc, Header)

- DWORD (für STATUS_CODE, CONTENT_LENGTH usw.)

Wenn eine Zeichenfolge in den Puffer geschrieben wird `lpdwBufferLength` und die Memberfunktion erfolgreich ist, enthält die Länge der Zeichenfolge in Zeichen minus 1 für das beendende NULL-Zeichen.

Zu den möglichen *dwInfoLevel-Werten* gehören:

- HTTP_QUERY_MIME_VERSION

- HTTP_QUERY_CONTENT_TYPE

- HTTP_QUERY_CONTENT_TRANSFER_ENCODING

- HTTP_QUERY_CONTENT_ID

- HTTP_QUERY_CONTENT_DESCRIPTION

- HTTP_QUERY_CONTENT_LENGTH

- HTTP_QUERY_ALLOWED_METHODS

- HTTP_QUERY_PUBLIC_METHODS

- HTTP_QUERY_DATE

- HTTP_QUERY_EXPIRES

- HTTP_QUERY_LAST_MODIFIED

- HTTP_QUERY_MESSAGE_ID

- HTTP_QUERY_URI

- HTTP_QUERY_DERIVED_FROM

- HTTP_QUERY_LANGUAGE

- HTTP_QUERY_COST

- HTTP_QUERY_WWW_LINK

- HTTP_QUERY_PRAGMA

- HTTP_QUERY_VERSION

- HTTP_QUERY_STATUS_CODE

- HTTP_QUERY_STATUS_TEXT

- HTTP_QUERY_RAW_HEADERS

- HTTP_QUERY_RAW_HEADERS_CRLF

## <a name="chttpfilequeryinfostatuscode"></a><a name="queryinfostatuscode"></a>CHttpFile::QueryInfoStatusCode

Rufen Sie diese Memberfunktion auf, um den Statuscode abzurufen, der einer HTTP-Anforderung zugeordnet ist, und platzieren Sie ihn im angegebenen *dwStatusCode-Parameter.*

```
BOOL QueryInfoStatusCode(DWORD& dwStatusCode) const;
```

### <a name="parameters"></a>Parameter

*dwStatusCode*<br/>
Ein Verweis auf einen Statuscode. Statuscodes geben den Erfolg oder Misserfolg des angeforderten Ereignisses an. Eine Auswahl von Statuscodebeschreibungen finden Sie unter **Hinweise.**

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null). Wenn der Aufruf fehlschlägt, kann die Win32-Funktion [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) aufgerufen werden, um die Ursache des Fehlers zu ermitteln.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Memberfunktion nur nach einem `CHttpFile` erfolgreichen Aufruf von [SendRequest](#sendrequest) oder für ein Objekt, das erfolgreich von [OpenURL](../../mfc/reference/cinternetsession-class.md#openurl)erstellt wurde.

HTTP-Statuscodes fallen in Gruppen, die den Erfolg oder Misserfolg der Anforderung angeben. In den folgenden Tabellen werden die Statuscodegruppen und die gängigsten HTTP-Statuscodes beschrieben.

|Group|Bedeutung|
|-----------|-------------|
|200–299|Erfolg|
|300–399|Information|
|400-499|Anforderungsfehler|
|500-599|Serverfehler|

Allgemeine HTTP-Statuscodes:

|Statuscode|Bedeutung|
|-----------------|-------------|
|200|URL gefunden, Übertragung folgt|
|400|Unverständliche Anfrage|
|404|Angeforderte URL nicht gefunden|
|405|Server unterstützt keine angeforderte Methode|
|500|Unbekannter Serverfehler|
|503|Serverkapazität erreicht|

## <a name="chttpfilesendrequest"></a><a name="sendrequest"></a>CHttpFile::SendRequest

Rufen Sie diese Memberfunktion auf, um eine Anforderung an einen HTTP-Server zu senden.

```
BOOL SendRequest(
    LPCTSTR pstrHeaders = NULL,
    DWORD dwHeadersLen = 0,
    LPVOID lpOptional = NULL,
    DWORD dwOptionalLen = 0);

BOOL SendRequest(
    CString& strHeaders,
    LPVOID lpOptional = NULL,
    DWORD dwOptionalLen = 0);
```

### <a name="parameters"></a>Parameter

*pstrHeaders*<br/>
Ein Zeiger auf eine Zeichenfolge, die den Namen der zu sendenden Header enthält.

*dwHeadersLen*<br/>
Die Länge der von *pstrHeaders*identifizierten Header .

*lpOptional*<br/>
Alle optionalen Daten, die unmittelbar nach den Anforderungsheadern gesendet werden sollen. Dies wird in der Regel für POST- und PUT-Vorgänge verwendet. Dies kann NULL sein, wenn keine optionalen Daten gesendet werden.

*dwOptionalLen*<br/>
Die Länge von *lpOptional*.

*strHeaders*<br/>
Eine Zeichenfolge, die den Namen der Header für die gesendete Anforderung enthält.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null). Wenn der Aufruf fehlschlägt, ermitteln Sie die Ursache des Fehlers, indem Sie das ausgelöste [CInternetException-Objekt](../../mfc/reference/cinternetexception-class.md) untersuchen.

## <a name="chttpfilesendrequestex"></a><a name="sendrequestex"></a>CHttpFile::SendRequestEx

Rufen Sie diese Memberfunktion auf, um eine Anforderung an einen HTTP-Server zu senden.

```
BOOL SendRequestEx(
    DWORD dwTotalLen,
    DWORD dwFlags = HSR_INITIATE,
    DWORD_PTR dwContext = 1);

BOOL SendRequestEx(
    LPINTERNET_BUFFERS lpBuffIn,
    LPINTERNET_BUFFERS lpBuffOut,
    DWORD dwFlags = HSR_INITIATE,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>Parameter

*dwTotalLen*<br/>
Anzahl der Bytes, die in der Anforderung gesendet werden sollen.

*dwFlags*<br/>
Flags, die den Vorgang beschreiben. Eine Liste der entsprechenden Flags finden Sie unter [HttpSendRequestEx](/windows/win32/api/wininet/nf-wininet-httpsendrequestexw) im Windows SDK.

*dwContext*<br/>
Der Kontextbezeichner für den `CHttpFile`-Vorgang. Weitere Informationen zu diesem Parameter finden Sie unter Hinweise.

*lpBuffIn*<br/>
Zeiger auf eine initialisierte [INTERNET_BUFFERS,](/windows/win32/api/wininet/ns-wininet-internet_buffersw) die den für den Vorgang verwendeten Eingabepuffer beschreibt.

*lpBuffOut*<br/>
Zeiger auf eine initialisierte INTERNET_BUFFERS, die den ausgabepuffer beschreibt, der für den Vorgang verwendet wird.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich. Wenn der Aufruf fehlschlägt, ermitteln Sie die Ursache des Fehlers, indem Sie das ausgelöste [CInternetException-Objekt](../../mfc/reference/cinternetexception-class.md) untersuchen.

### <a name="remarks"></a>Bemerkungen

Mit dieser Funktion kann Ihre Anwendung Daten mit `CInternetFile`den [Write-](../../mfc/reference/cinternetfile-class.md#write) und [WriteString-Methoden](../../mfc/reference/cinternetfile-class.md#writestring) von senden. Sie müssen die Länge der zu sendenden Daten kennen, bevor Sie eine der beiden Außerkraftsetzungen dieser Funktion aufrufen. Mit der ersten Außerkraftsetzung können Sie die Länge der Daten angeben, die Sie senden möchten. Die zweite Außerkraftsetzung akzeptiert Zeiger auf INTERNET_BUFFERS Strukturen, die verwendet werden können, um den Puffer ausführlich zu beschreiben.

Nachdem Inhalt in die Datei geschrieben wurde, rufen Sie [EndRequest](#endrequest) auf, um den Vorgang zu beenden.

Der Standardwert für *dwContext* wird von `CHttpFile` MFC aus dem [CInternetSession-Objekt,](../../mfc/reference/cinternetsession-class.md) das das `CHttpFile` Objekt erstellt hat, an das Objekt gesendet. Wenn Sie [CInternetSession::OpenURL](../../mfc/reference/cinternetsession-class.md#openurl) oder [CHttpConnection](../../mfc/reference/chttpconnection-class.md) aufrufen, um ein `CHttpFile` Objekt zu erstellen, können Sie die Standardeinstellung überschreiben, um den Kontextbezeichner auf einen Wert Ihrer Wahl festzulegen. Der Kontextbezeichner wird an [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) zurückgegeben, um den Status für das Objekt bereitzustellen, mit dem er identifiziert wird. Weitere Informationen zum Kontextbezeichner finden Sie im Artikel [Internet First Steps: WinInet.](../../mfc/wininet-basics.md)

### <a name="example"></a>Beispiel

Dieses Codefragment sendet den Inhalt einer Zeichenfolge an eine DLL mit dem Namen MFCISAPI. DLL auf dem LOCALHOST-Server. Während in diesem Beispiel `WriteString`nur ein Aufruf von verwendet wird, ist die Verwendung mehrerer Aufrufe zum Senden von Daten in Blöcken akzeptabel.

[!code-cpp[NVC_MFCWinInet#9](../../mfc/codesnippet/cpp/chttpfile-class_1.cpp)]

## <a name="see-also"></a>Siehe auch

[CInternetFile-Klasse](../../mfc/reference/cinternetfile-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CInternetFile-Klasse](../../mfc/reference/cinternetfile-class.md)<br/>
[CGopherFile-Klasse](../../mfc/reference/cgopherfile-class.md)<br/>
[CHttpConnection-Klasse](../../mfc/reference/chttpconnection-class.md)
