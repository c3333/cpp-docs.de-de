---
title: CHttpConnection-Klasse
ms.date: 03/27/2019
f1_keywords:
- CHttpConnection
- AFXINET/CHttpConnection
- AFXINET/CHttpConnection::CHttpConnection
- AFXINET/CHttpConnection::OpenRequest
helpviewer_keywords:
- CHttpConnection [MFC], CHttpConnection
- CHttpConnection [MFC], OpenRequest
ms.assetid: a402b662-c445-4988-800d-c8278551babe
ms.openlocfilehash: 1941af1e16a897235dd90db509d6ed29c2d9a875
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78890781"
---
# <a name="chttpconnection-class"></a>CHttpConnection-Klasse

Verwaltet die Verbindung mit einem HTTP-Server.

## <a name="syntax"></a>Syntax

```
class CHttpConnection : public CInternetConnection
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CHttpConnection:: CHttpConnection](#chttpconnection)|Erstellt ein `CHttpConnection`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CHttpConnection:: openrequest](#openrequest)|Öffnet eine HTTP-Anforderung.|

## <a name="remarks"></a>Bemerkungen

HTTP ist eines von drei Internet Server-Protokollen, die von den MFC-WinInet-Klassen implementiert werden.

Die-Klasse `CHttpConnection` enthält einen Konstruktor und eine Member-Funktion, [openrequest](#openrequest), die Verbindungen mit einem Server mit einem HTTP-Protokoll verwaltet.

Um mit einem HTTP-Server zu kommunizieren, müssen Sie zuerst eine Instanz von [cinternetzession](../../mfc/reference/cinternetsession-class.md)erstellen und dann ein [CHttpConnection](#chttpconnection) -Objekt erstellen. Sie erstellen niemals direkt ein `CHttpConnection` Objekt. Stattdessen wird [cinternettession:: GetHttpConnection](../../mfc/reference/cinternetsession-class.md#gethttpconnection)aufgerufen, das das `CHttpConnection` Objekt erstellt und einen Zeiger darauf zurückgibt.

Weitere Informationen zur Funktionsweise von `CHttpConnection` mit den anderen MFC-Internet Klassen finden Sie im Artikel [Internet Programmierung mit WinInet](../../mfc/win32-internet-extensions-wininet.md). Weitere Informationen zum Herstellen einer Verbindung mit Servern mithilfe der anderen beiden unterstützten Internet Protokolle (Gopher und FTP) finden Sie in den Klassen [CGopherConnection](../../mfc/reference/cgopherconnection-class.md) und [CFtpConnection](../../mfc/reference/cftpconnection-class.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)

[CInternetConnection](../../mfc/reference/cinternetconnection-class.md)

`CHttpConnection`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** AFXINET. h

##  <a name="chttpconnection"></a>CHttpConnection:: CHttpConnection

Diese Member-Funktion wird aufgerufen, um ein `CHttpConnection` Objekt zu erstellen.

```
CHttpConnection(
    CInternetSession* pSession,
    HINTERNET hConnected,
    LPCTSTR pstrServer,
    DWORD_PTR dwContext);

CHttpConnection(
    CInternetSession* pSession,
    LPCTSTR pstrServer,
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER,
    LPCTSTR pstrUserName = NULL,
    LPCTSTR pstrPassword = NULL,
    DWORD_PTR dwContext = 1);

CHttpConnection(
    CInternetSession* pSession,
    LPCTSTR pstrServer,
    DWORD dwFlags,
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER,
    LPCTSTR pstrUserName = NULL,
    LPCTSTR pstrPassword = NULL,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>Parameter

*psession*<br/>
Ein Zeiger auf ein [cinternetzession](../../mfc/reference/cinternetsession-class.md) -Objekt.

*hconnected*<br/>
Ein Handle für eine Internet Verbindung.

*pstrinserver*<br/>
Ein Zeiger auf eine Zeichenfolge, die den Servernamen enthält.

*dwcontext*<br/>
Der Kontext Bezeichner für das `CInternetConnection` Objekt. Weitere Informationen zu *dwcontext*finden Sie im Abschnitt " **Hinweise** ".

*Nport*<br/>
Die Nummer, die den Internetport für diese Verbindung identifiziert.

*pstrusername*<br/>
Zeiger auf eine mit NULL endenden Zeichenfolge, die den Namen des Benutzers angibt, der angemeldet werden soll. Wenn der Wert NULL ist, ist der Standardwert Anonymous.

*pstraupassword*<br/>
Ein Zeiger auf eine auf NULL endende Zeichenfolge, die das Kennwort für die Anmeldung angibt. Wenn sowohl *pstraupassword* als auch *pstrusername* NULL sind, ist das anonyme Standard Kennwort der e-Mail-Name des Benutzers. Wenn *pstraupassword* NULL oder eine leere Zeichenfolge ist, aber *pstrusername* nicht NULL ist, wird ein leeres Kennwort verwendet. In der folgenden Tabelle wird das Verhalten der vier möglichen Einstellungen von *pstrusername* und *pstrinpassword*beschrieben:

|*pstrusername*|*pstraupassword*|An FTP-Server gesendeter Benutzername|Kennwort an FTP-Server gesendet|
|--------------------|--------------------|---------------------------------|---------------------------------|
|NULL oder ""|NULL oder ""|Anonymous|E-Mail-Name des Benutzers|
|Zeichenfolge ungleich NULL|NULL oder ""|*pstrusername*|„ “|
|NULL |Zeichenfolge ungleich NULL|ERROR|ERROR|
|Zeichenfolge ungleich NULL|Zeichenfolge ungleich NULL|*pstrusername*|*pstraupassword*|

*dwFlags*<br/>
Eine beliebige Kombination der `INTERNET_FLAG_*`-Flags. Eine Beschreibung von *dwFlags* -Werten finden Sie in der Tabelle im Abschnitt " **Hinweise** " unter [CHttpConnection:: openrequest](#openrequest) .

### <a name="remarks"></a>Bemerkungen

Sie erstellen niemals direkt einen `CHttpConnection`. Stattdessen erstellen Sie ein-Objekt, indem Sie [cinternettession:: GetHttpConnection](../../mfc/reference/cinternetsession-class.md#gethttpconnection)aufrufen.

##  <a name="openrequest"></a>CHttpConnection:: openrequest

Rufen Sie diese Memberfunktion auf, um eine HTTP-Verbindung zu öffnen.

```
CHttpFile* OpenRequest(
    LPCTSTR pstrVerb,
    LPCTSTR pstrObjectName,
    LPCTSTR pstrReferer = NULL,
    DWORD_PTR dwContext = 1,
    LPCTSTR* ppstrAcceptTypes = NULL,
    LPCTSTR pstrVersion = NULL,
    DWORD dwFlags = INTERNET_FLAG_EXISTING_CONNECT);

CHttpFile* OpenRequest(
    int nVerb,
    LPCTSTR pstrObjectName,
    LPCTSTR pstrReferer = NULL,
    DWORD_PTR dwContext = 1,
    LPCTSTR* ppstrAcceptTypes = NULL,
    LPCTSTR pstrVersion = NULL,
    DWORD dwFlags = INTERNET_FLAG_EXISTING_CONNECT);
```

### <a name="parameters"></a>Parameter

*pstrauverb*<br/>
Ein Zeiger auf eine Zeichenfolge, die das Verb enthält, das in der Anforderung verwendet werden soll. Wenn der Wert NULL ist, wird "Get" verwendet.

*pstrobjectname*<br/>
Ein Zeiger auf eine Zeichenfolge, die das Zielobjekt des angegebenen Verbs enthält. Diese Zeichenfolge ist im Allgemeinen ein Dateiname, ein ausführbares Modul oder ein suchspezifizierer.

*pstraureferer*<br/>
Ein Zeiger auf eine Zeichenfolge, die die Adresse (URL) des Dokuments angibt, aus dem die URL in der Anforderung (*pstrobjectname*) abgerufen wurde. Wenn der Wert NULL ist, wird kein HTTP-Header angegeben.

*dwcontext*<br/>
Der Kontextbezeichner für den `OpenRequest`-Vorgang. Weitere Informationen zu *dwcontext*finden Sie im Abschnitt "Hinweise".

*ppstraccepttypes*<br/>
Ein Zeiger auf ein mit Null endendes Array von LPCTSTR-Zeigern auf Zeichen folgen, die vom Client akzeptierte Inhaltstypen angeben. Wenn *ppstraccepttypes* NULL ist, interpretieren die Server, dass der Client nur Dokumente vom Typ "Text/*" annimmt (d. h. nur Textdokumente und keine Bilder oder andere Binärdateien). Der Inhaltstyp entspricht der CGI-Variable CONTENT_TYPE, die den Typ der Daten für Abfragen kennzeichnet, denen Informationen wie HTTP POST und PUT angefügt sind.

*pstrauversion*<br/>
Ein Zeiger auf eine Zeichenfolge, mit der die HTTP-Version definiert wird. Wenn der Wert NULL ist, wird "http/1.0" verwendet.

*dwFlags*<br/>
Beliebige Kombinationen der Flags INTERNET_ FLAG_*. Eine Beschreibung möglicher *dwFlags* -Werte finden Sie im Abschnitt "Hinweise".

*nverb*<br/>
Eine mit dem HTTP-Anforderungstyp verknüpfte Zahl. Dabei kann es sich um eine der folgenden Methoden handeln:

|HTTP-Anforderungstyp|*nverb* -Wert|
|-----------------------|-------------------|
|HTTP_VERB_POST|0|
|HTTP_VERB_GET|1|
|HTTP_VERB_HEAD|2|
|HTTP_VERB_PUT|3|
|HTTP_VERB_LINK|4|
|HTTP_VERB_DELETE|5|
|HTTP_VERB_UNLINK|6|

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das angeforderte [CHttpFile](../../mfc/reference/chttpfile-class.md) -Objekt.

### <a name="remarks"></a>Bemerkungen

*dwFlags* können eine der folgenden sein:

|Internet-Flag|BESCHREIBUNG|
|-------------------|-----------------|
|INTERNET_FLAG_RELOAD|Erzwingt einen Download der angeforderten Datei, des angeforderten Objekts oder der angeforderten Verzeichnisliste vom ursprünglichen Server, nicht aus dem Cache.|
|INTERNET_FLAG_DONT_CACHE|Fügt die zurückgegebene Entität nicht zum Cache hinzu.|
|INTERNET_FLAG_MAKE_PERSISTENT|Fügt die zurückgegebene Entität dem Cache als permanente Entität hinzu. Dies bedeutet, dass die Standard Cache Bereinigung, Konsistenzüberprüfung oder Garbage Collection dieses Element nicht aus dem Cache entfernen kann.|
|INTERNET_FLAG_SECURE|Verwendung eine sichere Transaktionssemantik. Er wird in die Verwendung von SSL/PCT übersetzt und ist nur in HTTP-Anforderungen sinnvoll.|
|INTERNET_FLAG_NO_AUTO_REDIRECT|Wird nur mit HTTP verwendet und gibt an, dass Umleitungen nicht automatisch in [CHttpFile:: SendRequest](../../mfc/reference/chttpfile-class.md#sendrequest)behandelt werden sollen.|

Überschreiben Sie den `dwContext`-Standard, um den Kontextbezeichner auf einen ausgewählten Wert festzulegen. Der Kontext Bezeichner ist diesem speziellen Vorgang des `CHttpConnection` Objekts zugeordnet, das vom [cinternetzession](../../mfc/reference/cinternetsession-class.md) -Objekt erstellt wurde. Der Wert wird an [cinternetzession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) zurückgegeben, um den Status für den Vorgang bereitzustellen, mit dem er identifiziert wird. Weitere Informationen zum Kontext Bezeichner finden Sie im Artikel [Internet First Steps: WinInet](../../mfc/wininet-basics.md) .

Mit dieser Funktion können Ausnahmen ausgelöst werden.

## <a name="see-also"></a>Weitere Informationen

[CInternetConnection-Klasse](../../mfc/reference/cinternetconnection-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CInternetConnection-Klasse](../../mfc/reference/cinternetconnection-class.md)<br/>
[CHttpFile-Klasse](../../mfc/reference/chttpfile-class.md)
