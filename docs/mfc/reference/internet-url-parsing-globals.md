---
title: Internet-URL-Analyse von Globalen und Helfern
ms.date: 04/03/2017
helpviewer_keywords:
- parsing, URLs
- URLs, parsing
ms.assetid: 46c6384f-e4a6-4dbd-9196-219c19040ec5
ms.openlocfilehash: 742b381ecb55c433d0f384174b7612fcc21e9716
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81356610"
---
# <a name="internet-url-parsing-globals-and-helpers"></a>Internet-URL-Analyse von Globalen und Helfern

Wenn ein Client eine Abfrage an den Internetserver sendet, können Sie eine der URL-Analyseglobals verwenden, um Informationen über den Client zu extrahieren. Die Hilfsfunktionen bieten weitere Internetfunktionen.

## <a name="internet-url-parsing-globals"></a>Globale Variablen zur Analyse von Internet-URLs

|||
|-|-|
|[AfxParseURL](#afxparseurl)|Analysiert eine URL-Zeichenfolge und gibt den Diensttyp und seine Komponenten zurück.|
|[AfxParseURLEx](#afxparseurlex)|Analysiert eine URL-Zeichenfolge und gibt den Diensttyp und seine Komponenten zurück sowie den Benutzernamen und das Kennwort.|

## <a name="other-internet-helpers"></a>Andere Internet-Helfer

|||
|-|-|
|[AfxThrowInternetException](#afxthrowinternetexception)|Löst eine Ausnahme aus, die sich auf die Internetverbindung bezieht.|
|[AfxGetInternetHandleType](#afxgetinternethandletype)|Bestimmt den Typ eines Internethandles.|

## <a name="afxparseurl"></a><a name="afxparseurl"></a>AfxParseURL

Diese globale Wird in [CInternetSession::OpenURL](../../mfc/reference/cinternetsession-class.md#openurl)verwendet.

```
BOOL AFXAPI AfxParseURL(
    LPCTSTR pstrURL,
    DWORD& dwServiceType,
    CString& strServer,
    CString& strObject,
    INTERNET_PORT& nPort);
```

### <a name="parameters"></a>Parameter

*pstrURL*<br/>
Ein Zeiger auf eine Zeichenfolge, die die zu analysierende URL enthält.

*dwServiceType*<br/>
Gibt den Typ des Internetdienstes an. Folgende Werte sind möglich:

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

*strServer*<br/>
Das erste Segment der URL, das dem Diensttyp folgt.

*strObject*<br/>
Ein Objekt, auf das sich die URL bezieht (kann leer sein).

*nPort*<br/>
Ermittelt entweder aus den Server- oder Objektteilen der URL, sofern vorhanden.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die URL erfolgreich analysiert wurde; Andernfalls 0, wenn es leer ist oder keinen bekannten Internetdiensttyp enthält.

### <a name="remarks"></a>Bemerkungen

Es analysiert eine URL-Zeichenfolge und gibt den Diensttyp und seine Komponenten zurück.

`AfxParseURL` Analysiert beispielsweise URLs des Formulars *service://server/dir/dir/object.ext:port* und gibt seine Komponenten wie folgt zurück:

*strServer* == "Server"

*strObject* == "/dir/dir/object/object.ext"

*nPort* == #port

*dwServiceType* == #service

> [!NOTE]
> Um diese Funktion aufzurufen, muss Ihr Projekt AFXINET enthalten. H.

### <a name="requirements"></a>Anforderungen

  **Header** afxinet.h

## <a name="afxparseurlex"></a><a name="afxparseurlex"></a>AfxParseURLEx

Diese globale Funktion ist die erweiterte Version von [AfxParseURL](#afxparseurl) und wird in [CInternetSession::OpenURL](../../mfc/reference/cinternetsession-class.md#openurl)verwendet.

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

*pstrURL*<br/>
Ein Zeiger auf eine Zeichenfolge, die die zu analysierende URL enthält.

*dwServiceType*<br/>
Gibt den Typ des Internetdienstes an. Folgende Werte sind möglich:

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

*strServer*<br/>
Das erste Segment der URL, das dem Diensttyp folgt.

*strObject*<br/>
Ein Objekt, auf das sich die URL bezieht (kann leer sein).

*nPort*<br/>
Ermittelt entweder aus den Server- oder Objektteilen der URL, sofern vorhanden.

*strUsername*<br/>
Ein Verweis `CString` auf ein Objekt, das den Namen des Benutzers enthält.

*strPassword*<br/>
Ein Verweis `CString` auf ein Objekt, das das Kennwort des Benutzers enthält.

*dwFlags*<br/>
Die Flags, die steuern, wie die URL analysiert wird. Kann eine Kombination der folgenden Werte sein:

|Wert|Bedeutung|
|-----------|-------------|
|ICU_DECODE|Konvertieren Sie %XX Escapesequenzen in Zeichen.|
|ICU_NO_ENCODE|Konvertieren Sie keine unsicheren Zeichen in escape-Sequenz.|
|ICU_NO_META|Entfernen Sie keine Metasequenzen (z. B. "A "" und "..") aus der URL.|
|ICU_ENCODE_SPACES_ONLY|Nur Leerzeichen codieren.|
|ICU_BROWSER_MODE|Codieren oder dekodieren Sie Zeichen nicht nach ''' oder '', und entfernen Sie nach '' keinen nachgestellten Leerraum. Wenn dieser Wert nicht angegeben ist, wird die gesamte URL codiert und das nachfolgende Leerzeichen entfernt.|

Wenn Sie den MFC-Standard verwenden, der keine Flags ist, konvertiert die Funktion \\alle unsicheren Zeichen \\und Metasequenzen (z. B. ., . . und ...), um Sequenzen zu entkommen.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die URL erfolgreich analysiert wurde; Andernfalls 0, wenn es leer ist oder keinen bekannten Internetdiensttyp enthält.

### <a name="remarks"></a>Bemerkungen

Es analysiert eine URL-Zeichenfolge und gibt den Diensttyp und seine Komponenten zurück sowie den Namen und das Kennwort des Benutzers. Die Flags geben an, wie unsicher e.v.a. mit Zeichen umgeschlagen wird.

> [!NOTE]
> Um diese Funktion aufzurufen, muss Ihr Projekt AFXINET enthalten. H.

### <a name="requirements"></a>Anforderungen

  **Header** afxinet.h

## <a name="afxgetinternethandletype"></a><a name="afxgetinternethandletype"></a>AfxGetInternetHandleType

Verwenden Sie diese globale Funktion, um den Typ eines Internethandles zu bestimmen.

### <a name="syntax"></a>Syntax

  ```
DWORD AFXAPI AfxGetInternetHandleType(  HINTERNET hQuery );
```

### <a name="parameters"></a>Parameter

*hQuery*<br/>
Ein Handle für eine Internetabfrage.

### <a name="return-value"></a>Rückgabewert

Alle von WININET definierten Internetdiensttypen. H. Eine Liste dieser Internetdienste finden Sie im Abschnitt "Hinweise". Wenn das Handle NULL ist oder nicht erkannt wird, gibt die Funktion AFX_INET_SERVICE_UNK zurück.

### <a name="remarks"></a>Bemerkungen

Die folgende Liste enthält mögliche `AfxGetInternetHandleType`Internettypen, die von zurückgegeben werden.

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
> Um diese Funktion aufzurufen, muss Ihr Projekt AFXINET enthalten. H.

### <a name="requirements"></a>Anforderungen

**Kopf:** afxinet.h

## <a name="afxthrowinternetexception"></a><a name="afxthrowinternetexception"></a>AfxThrowInternetException

Löst eine Internetausnahme aus.

### <a name="syntax"></a>Syntax

```
   void AFXAPI AfxThrowInternetException(  DWORD dwContext,  DWORD dwError = 0 );
```

### <a name="parameters"></a>Parameter

*dwContext*<br/>
Der Kontextbezeichner für den Vorgang, der den Fehler verursacht hat. Der Standardwert von *dwContext* wurde ursprünglich in [CInternetSession](cinternetsession-class.md) angegeben und an [CInternetConnection](cinternetconnection-class.md)- und [CInternetFile](cinternetfile-class.md)-abgeleitete Klassen übergeben. Bei bestimmten Vorgängen, die für eine Verbindung oder eine Datei ausgeführt werden, überschreiben Sie in der Regel die Standardeinstellung mit einem eigenen *dwContext.* Dieser Wert wird dann an [CInternetSession::OnStatusCallback](cinternetsession-class.md#onstatuscallback) zurückgegeben, um den Status des bestimmten Vorgangs zu identifizieren.

*dwError*<br/>
Der Fehler, der die Ausnahme verursacht hat.

### <a name="remarks"></a>Bemerkungen

Sie sind für die Ermittlung der Ursache auf der Grundlage des Betriebssystemfehlercodes verantwortlich.

> [!NOTE]
> Um diese Funktion aufzurufen, muss Ihr Projekt AFXINET enthalten. H.

### <a name="requirements"></a>Anforderungen

**Kopf:** afxinet.h

## <a name="see-also"></a>Siehe auch

[MFC-Makros, globale Funktionen und globale Variablen](mfc-macros-and-globals.md)<br/>
[CInternetException-Klasse](cinternetexception-class.md)<br/>
[AfxParseURL](internet-url-parsing-globals.md#afxparseurl)
