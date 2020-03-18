---
title: Internet-URL-paramenungen und Hilfsprogramme
ms.date: 04/03/2017
helpviewer_keywords:
- parsing, URLs
- URLs, parsing
ms.assetid: 46c6384f-e4a6-4dbd-9196-219c19040ec5
ms.openlocfilehash: 310e4ffb3fc207d874e97ba1fac65f6f8cb41a31
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2020
ms.locfileid: "79426666"
---
# <a name="internet-url-parsing-globals-and-helpers"></a>Internet-URL-paramenungen und Hilfsprogramme

Wenn ein Client eine Abfrage an den Internet Server sendet, können Sie eine der Variablen für die URL-Verarbeitung verwenden, um Informationen über den Client zu extrahieren. Die Hilfsfunktionen bieten weitere Internet Funktionen.

## <a name="internet-url-parsing-globals"></a>Globale Variablen zur Analyse von Internet-URLs

|||
|-|-|
|[Afxparser-URL](#afxparseurl)|Analysiert eine URL-Zeichenfolge und gibt den Diensttyp und dessen Komponenten zurück.|
|[Afxparser](#afxparseurlex)|Analysiert eine URL-Zeichenfolge und gibt den Diensttyp und die zugehörigen Komponenten sowie den Benutzernamen und das Kennwort zurück.|

## <a name="other-internet-helpers"></a>Weitere Internet Hilfsprogramme

|||
|-|-|
|[Afxthrowinterntexception](#afxthrowinternetexception)|Löst eine Ausnahme aus, die sich auf die Internetverbindung bezieht.|
|[Afxgetinternetthandletype](#afxgetinternethandletype)|Bestimmt den Typ eines Internet Handles.|

##  <a name="afxparseurl"></a>Afxparser-URL

Diese globale wird in [cinternetzession:: OpenURL](../../mfc/reference/cinternetsession-class.md#openurl)verwendet.

```
BOOL AFXAPI AfxParseURL(
    LPCTSTR pstrURL,
    DWORD& dwServiceType,
    CString& strServer,
    CString& strObject,
    INTERNET_PORT& nPort);
```

### <a name="parameters"></a>Parameter

*pstrinurl*<br/>
Ein Zeiger auf eine Zeichenfolge, die die URL enthält, die analysiert werden soll.

*dwservicetype*<br/>
Gibt den Typ des Internet Dienes an. Folgende Werte sind möglich:

- AFX_INET_SERVICE_FTP

- AFX_INET_SERVICE_HTTP

- AFX_INET_SERVICE_HTTPS

- AFX_INET_SERVICE_GOPHER

- AFX_INET_SERVICE_FILE

- AFX_INET_SERVICE_MAILTO

- AFX_INET_SERVICE_NEWS

- AFX_INET_SERVICE_NNTP

- AFX_INET_SERVICE_TELNET

- AFX_INET_SERVICE_WAIS

- AFX_INET_SERVICE_MID

- AFX_INET_SERVICE_CID

- AFX_INET_SERVICE_PROSPERO

- AFX_INET_SERVICE_AFS

- AFX_INET_SERVICE_UNK

*-Server*<br/>
Das erste Segment der URL, das auf den Diensttyp folgt.

*strObject*<br/>
Ein Objekt, auf das sich die URL bezieht (kann leer sein).

*Nport*<br/>
Wird entweder durch den Server oder die Objektteile der URL bestimmt, sofern vorhanden.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn die URL erfolgreich analysiert wurde. Andernfalls ist der Wert 0, wenn er leer ist oder keinen bekannten Internet Diensttyp enthält.

### <a name="remarks"></a>Hinweise

Es analysiert eine URL-Zeichenfolge und gibt den Diensttyp und seine Komponenten zurück.

`AfxParseURL` analysiert beispielsweise URLs des Formulars *Service://Server/dir/dir/Object.ext:Port* und gibt die zugehörigen Komponenten wie folgt zurück:

" *strindserver* = =" Server "

*strObject* = = "/dir/dir/Object/Object.ext"

*Nport* = = #Port

*dwservicetype* = = #Service

> [!NOTE]
>  Um diese Funktion aufzurufen, muss das Projekt AFXINET enthalten. Micha.

### <a name="requirements"></a>Voraussetzungen

  **Header** AFXINET. h

##  <a name="afxparseurlex"></a>Afxparser

Diese globale Funktion ist die erweiterte Version von [afxparser URL](#afxparseurl) und wird in [cinternetzession:: OpenURL](../../mfc/reference/cinternetsession-class.md#openurl)verwendet.

```
BOOL AFXAPI AfxParseURLEx(
    LPCTSTR pstrURL,
    DWORD& dwServiceType,
    CString& strServer,
    CString& strObject,
    INTERNET_PORT& nPort,
    CString& strUsername,
    CString& strPassword,
    DWORD dwFlags = 0);
```

### <a name="parameters"></a>Parameter

*pstrinurl*<br/>
Ein Zeiger auf eine Zeichenfolge, die die URL enthält, die analysiert werden soll.

*dwservicetype*<br/>
Gibt den Typ des Internet Dienes an. Folgende Werte sind möglich:

- AFX_INET_SERVICE_FTP

- AFX_INET_SERVICE_HTTP

- AFX_INET_SERVICE_HTTPS

- AFX_INET_SERVICE_GOPHER

- AFX_INET_SERVICE_FILE

- AFX_INET_SERVICE_MAILTO

- AFX_INET_SERVICE_NEWS

- AFX_INET_SERVICE_NNTP

- AFX_INET_SERVICE_TELNET

- AFX_INET_SERVICE_WAIS

- AFX_INET_SERVICE_MID

- AFX_INET_SERVICE_CID

- AFX_INET_SERVICE_PROSPERO

- AFX_INET_SERVICE_AFS

- AFX_INET_SERVICE_UNK

*-Server*<br/>
Das erste Segment der URL, das auf den Diensttyp folgt.

*strObject*<br/>
Ein Objekt, auf das sich die URL bezieht (kann leer sein).

*Nport*<br/>
Wird entweder durch den Server oder die Objektteile der URL bestimmt, sofern vorhanden.

*strUserName*<br/>
Ein Verweis auf ein `CString` Objekt, das den Namen des Benutzers enthält.

*"Straume"*<br/>
Ein Verweis auf ein `CString` Objekt, das das Kennwort des Benutzers enthält.

*dwFlags*<br/>
Die Flags, die Steuern, wie die URL analysiert werden soll. Kann eine Kombination der folgenden Werte sein:

|Wert|Bedeutung|
|-----------|-------------|
|ICU_DECODE|Konvertieren von% XX-Escapesequenzen in Zeichen.|
|ICU_NO_ENCODE|Nicht unsichere Zeichen in Escapesequenz konvertieren.|
|ICU_NO_META|Entfernen Sie keine Metasequenzen (z. b. "\"). und "\..") aus der URL.|
|ICU_ENCODE_SPACES_ONLY|Nur Leerzeichen codieren.|
|ICU_BROWSER_MODE|Codieren oder Decodieren Sie Zeichen nach ' # ' oder ' ' nicht, und entfernen Sie keine nachfolgenden Leerzeichen nach ' '. Wenn dieser Wert nicht angegeben wird, wird die gesamte URL codiert, und nachfolgende Leerzeichen werden entfernt.|

Wenn Sie die MFC-Standardeinstellung verwenden, bei der es sich nicht um Flags handelt, konvertiert die-Funktion alle unsicheren Zeichen und Metasequenzen (z. b. \\., \.. und \\...) in Escapesequenzen.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn die URL erfolgreich analysiert wurde. Andernfalls ist der Wert 0, wenn er leer ist oder keinen bekannten Internet Diensttyp enthält.

### <a name="remarks"></a>Hinweise

Es analysiert eine URL-Zeichenfolge und gibt den Diensttyp und seine Komponenten sowie den Namen und das Kennwort des Benutzers zurück. Die Flags geben an, wie unsichere Zeichen behandelt werden.

> [!NOTE]
>  Um diese Funktion aufzurufen, muss das Projekt AFXINET enthalten. Micha.

### <a name="requirements"></a>Voraussetzungen

  **Header** AFXINET. h

## <a name="afxgetinternethandletype"></a>Afxgetinternetthandletype

Verwenden Sie diese globale Funktion, um den Typ eines Internet Handles zu bestimmen.

### <a name="syntax"></a>Syntax

  ```
DWORD AFXAPI AfxGetInternetHandleType(  HINTERNET hQuery );
```

### <a name="parameters"></a>Parameter

*hquery*<br/>
Ein Handle für eine Internet Abfrage.

### <a name="return-value"></a>Rückgabewert

Alle durch Wininet definierten Internet Dienst Typen. Micha. Eine Liste dieser Internet Dienste finden Sie im Abschnitt "Hinweise". Wenn das Handle NULL ist oder nicht erkannt wird, gibt die Funktion AFX_INET_SERVICE_UNK zurück.

### <a name="remarks"></a>Hinweise

Die folgende Liste enthält mögliche Internet Typen, die von `AfxGetInternetHandleType`zurückgegeben werden.

- INTERNET_HANDLE_TYPE_INTERNET

- INTERNET_HANDLE_TYPE_CONNECT_FTP

- INTERNET_HANDLE_TYPE_CONNECT_GOPHER

- INTERNET_HANDLE_TYPE_CONNECT_HTTP

- INTERNET_HANDLE_TYPE_FTP_FIND

- INTERNET_HANDLE_TYPE_FTP_FIND_HTML

- INTERNET_HANDLE_TYPE_FTP_FILE

- INTERNET_HANDLE_TYPE_FTP_FILE_HTML

- INTERNET_HANDLE_TYPE_GOPHER_FIND

- INTERNET_HANDLE_TYPE_GOPHER_FIND_HTML

- INTERNET_HANDLE_TYPE_GOPHER_FILE

- INTERNET_HANDLE_TYPE_GOPHER_FILE_HTML

- INTERNET_HANDLE_TYPE_HTTP_REQUEST

> [!NOTE]
>  Um diese Funktion aufzurufen, muss das Projekt AFXINET enthalten. Micha.

### <a name="requirements"></a>Voraussetzungen

**Header:** AFXINET. h

## <a name="afxthrowinternetexception"></a>Afxthrowinterntexception

Löst eine Internet Ausnahme aus.

### <a name="syntax"></a>Syntax

```
   void AFXAPI AfxThrowInternetException(  DWORD dwContext,  DWORD dwError = 0 );
```

### <a name="parameters"></a>Parameter

*dwcontext*<br/>
Der Kontext Bezeichner für den Vorgang, der den Fehler verursacht hat. Der Standardwert von *dwcontext* wird ursprünglich in [cinternetzession](cinternetsession-class.md) angegeben und an [CInternetConnection](cinternetconnection-class.md)-und [CInternetFile](cinternetfile-class.md)-abgeleitete Klassen übergeben. Für bestimmte Vorgänge, die für eine Verbindung oder eine Datei ausgeführt werden, überschreiben Sie in der Regel die Standardeinstellung mit einem eigenen *dwcontext* . Dieser Wert wird dann an [cinternetzession:: OnStatusCallback](cinternetsession-class.md#onstatuscallback) zurückgegeben, um den Status des jeweiligen Vorgangs zu identifizieren.

*dwError*<br/>
Der Fehler, der die Ausnahme verursacht hat.

### <a name="remarks"></a>Hinweise

Sie sind dafür verantwortlich, die Ursache basierend auf dem Fehlercode des Betriebssystems zu ermitteln.

> [!NOTE]
>  Um diese Funktion aufzurufen, muss das Projekt AFXINET enthalten. Micha.

### <a name="requirements"></a>Voraussetzungen

**Header:** AFXINET. h

## <a name="see-also"></a>Siehe auch

[Makros und Globals](mfc-macros-and-globals.md)<br/>
[CInternetException-Klasse](cinternetexception-class.md)<br/>
[Afxparser-URL](internet-url-parsing-globals.md#afxparseurl)
