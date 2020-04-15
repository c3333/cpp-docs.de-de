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
ms.openlocfilehash: af402b532b3aba28bdfefea5afa67331765db4c5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81351813"
---
# <a name="chttpconnection-class"></a>CHttpConnection-Klasse

Verwaltet die Verbindung mit einem HTTP-Server.

## <a name="syntax"></a>Syntax

```
class CHttpConnection : public CInternetConnection
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CHttpConnection::CHttpConnection](#chttpconnection)|Erstellt ein `CHttpConnection` -Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CHttpConnection::OpenRequest](#openrequest)|Öffnet eine HTTP-Anforderung.|

## <a name="remarks"></a>Bemerkungen

HTTP ist eines von drei Internetserverprotokollen, die von den MFC WinInet-Klassen implementiert werden.

Die `CHttpConnection` Klasse enthält einen Konstruktor und eine Memberfunktion, [OpenRequest](#openrequest), die Verbindungen zu einem Server mit einem HTTP-Protokoll verwaltet.

Um mit einem HTTP-Server zu kommunizieren, müssen Sie zunächst eine Instanz von [CInternetSession](../../mfc/reference/cinternetsession-class.md)erstellen und dann ein [CHttpConnection-Objekt](#chttpconnection) erstellen. Sie erstellen `CHttpConnection` niemals ein Objekt direkt; Rufen Sie stattdessen [CInternetSession::GetHttpConnection](../../mfc/reference/cinternetsession-class.md#gethttpconnection) `CHttpConnection` auf, das das Objekt erstellt und einen Zeiger darauf zurückgibt.

Weitere Informationen zur `CHttpConnection` Funktionsweise mit den anderen MFC-Internetklassen finden Sie im Artikel [Internetprogrammierung mit WinInet](../../mfc/win32-internet-extensions-wininet.md). Weitere Informationen zum Herstellen einer Verbindung mit Servern mit den beiden anderen unterstützten Internetprotokollen gopher und FTP finden Sie in den Klassen [CGopherConnection](../../mfc/reference/cgopherconnection-class.md) und [CFtpConnection](../../mfc/reference/cftpconnection-class.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CInternetConnection](../../mfc/reference/cinternetconnection-class.md)

`CHttpConnection`

## <a name="requirements"></a>Anforderungen

**Kopf:** afxinet.h

## <a name="chttpconnectionchttpconnection"></a><a name="chttpconnection"></a>CHttpConnection::CHttpConnection

Diese Memberfunktion wird aufgerufen, um ein `CHttpConnection` Objekt zu erstellen.

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

*pSession*<br/>
Ein Zeiger auf ein [CInternetSession-Objekt.](../../mfc/reference/cinternetsession-class.md)

*hConnected*<br/>
Ein Handle für eine Internetverbindung.

*pstrServer*<br/>
Ein Zeiger auf eine Zeichenfolge, die den Servernamen enthält.

*dwContext*<br/>
Der Kontextbezeichner für das `CInternetConnection` Objekt. Weitere Informationen *zu dwContext*finden Sie im Abschnitt **"Bemerkungen".**

*nPort*<br/>
Die Nummer, die den Internetport für diese Verbindung identifiziert.

*pstrUserName*<br/>
Zeiger auf eine null-terminierte Zeichenfolge, die den Namen des Benutzers angibt, der sich anmelden soll. Wenn NULL, ist der Standardwert anonym.

*pstrPassword*<br/>
Ein Zeiger auf eine null-terminierte Zeichenfolge, die das Kennwort angibt, das zum Anmelden verwendet werden soll. Wenn sowohl *pstrPassword* als auch *pstrUserName* NULL sind, ist das anonyme Standardkennwort der E-Mail-Name des Benutzers. Wenn *pstrPassword* NULL oder eine leere Zeichenfolge ist, *pstrUserName* jedoch nicht NULL ist, wird ein leeres Kennwort verwendet. In der folgenden Tabelle wird das Verhalten für die vier möglichen Einstellungen von *pstrUserName* und *pstrPassword*beschrieben:

|*pstrUserName*|*pstrPassword*|Benutzername, der an FTP-Server gesendet wird|An FTP-Server gesendetes Kennwort|
|--------------------|--------------------|---------------------------------|---------------------------------|
|NULL oder " "|NULL oder " "|"anonym"|E-Mail-Name des Benutzers|
|Nicht-NULL-Zeichenfolge|NULL oder " "|*pstrUserName*|" "|
|NULL |Nicht-NULL-Zeichenfolge|ERROR|ERROR|
|Nicht-NULL-Zeichenfolge|Nicht-NULL-Zeichenfolge|*pstrUserName*|*pstrPassword*|

*dwFlags*<br/>
Jede Kombination `INTERNET_FLAG_*` der Flags. Eine Beschreibung der *dwFlags-Werte* finden Sie in der Tabelle im Abschnitt **"Hinweise"** von [CHttpConnection::OpenRequest.](#openrequest)

### <a name="remarks"></a>Bemerkungen

Sie erstellen `CHttpConnection` nie direkt. Stattdessen erstellen Sie ein Objekt, indem Sie [CInternetSession::GetHttpConnection](../../mfc/reference/cinternetsession-class.md#gethttpconnection)aufrufen.

## <a name="chttpconnectionopenrequest"></a><a name="openrequest"></a>CHttpConnection::OpenRequest

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

*pstrVerb*<br/>
Ein Zeiger auf eine Zeichenfolge, die das Verb enthält, das in der Anforderung verwendet werden soll. Wenn NULL, wird "GET" verwendet.

*pstrObjectName*<br/>
Ein Zeiger auf eine Zeichenfolge, die das Zielobjekt des angegebenen Verbs enthält. Diese Zeichenfolge ist im Allgemeinen ein Dateiname, ein ausführbares Modul oder ein Suchbezeichner.

*pstrReferer*<br/>
Ein Zeiger auf eine Zeichenfolge, die die Adresse (URL) des Dokuments angibt, von dem die URL in der Anforderung (*pstrObjectName*) abgerufen wurde. Wenn NULL, wird kein HTTP-Header angegeben.

*dwContext*<br/>
Der Kontextbezeichner für den `OpenRequest`-Vorgang. Weitere Informationen *zu dwContext*finden Sie im Abschnitt "Bemerkungen".

*ppstrAcceptTypes*<br/>
Ein Zeiger auf ein null-terminiertes Array von LPCTSTR-Zeigern auf Zeichenfolgen, die Inhaltstypen angeben, die vom Client akzeptiert werden. Wenn *ppstrAcceptTypes* NULL ist, interpretieren die Server, dass der Client nur Dokumente vom Typ "text/*" akzeptiert (d. h. nur Textdokumente und nicht Bilder oder andere Binärdateien). Der Inhaltstyp entspricht der CGI-Variable CONTENT_TYPE, die den Typ der Daten für Abfragen kennzeichnet, denen Informationen wie HTTP POST und PUT angefügt sind.

*pstrVersion*<br/>
Ein Zeiger auf eine Zeichenfolge, mit der die HTTP-Version definiert wird. Wenn NULL, wird "HTTP/1.0" verwendet.

*dwFlags*<br/>
Beliebige Kombinationen der Flags INTERNET_ FLAG_*. Eine Beschreibung möglicher *dwFlags-Werte* finden Sie im Abschnitt Hinweise.

*nVerb*<br/>
Eine mit dem HTTP-Anforderungstyp verknüpfte Zahl. Dabei kann es sich um eine der folgenden Methoden handeln:

|HTTP-Anforderungstyp|*nVerb-Wert*|
|-----------------------|-------------------|
|HTTP_VERB_POST|0|
|HTTP_VERB_GET|1|
|HTTP_VERB_HEAD|2|
|HTTP_VERB_PUT|3|
|HTTP_VERB_LINK|4|
|HTTP_VERB_DELETE|5|
|HTTP_VERB_UNLINK|6|

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das [angeforderte CHttpFile-Objekt.](../../mfc/reference/chttpfile-class.md)

### <a name="remarks"></a>Bemerkungen

*dwFlags* kann einer der folgenden sein:

|Internet-Flag|BESCHREIBUNG|
|-------------------|-----------------|
|INTERNET_FLAG_RELOAD|Erzwingt einen Download der angeforderten Datei, des angeforderten Objekts oder der angeforderten Verzeichnisliste vom ursprünglichen Server, nicht aus dem Cache.|
|INTERNET_FLAG_DONT_CACHE|Fügt die zurückgegebene Entität nicht zum Cache hinzu.|
|INTERNET_FLAG_MAKE_PERSISTENT|Fügt die zurückgegebene Entität dem Cache als permanente Entität hinzu. Dies bedeutet, dass Standard-Cachebereinigung, Konsistenzprüfung oder Garbage Collection dieses Element nicht aus dem Cache entfernen kann.|
|INTERNET_FLAG_SECURE|Verwendung eine sichere Transaktionssemantik. Es übersetzt in die Verwendung von SSL/PCT und ist nur in HTTP-Anforderungen sinnvoll|
|INTERNET_FLAG_NO_AUTO_REDIRECT|Wird nur mit HTTP verwendet, gibt an, dass Umleitungen nicht automatisch in [CHttpFile::SendRequest](../../mfc/reference/chttpfile-class.md#sendrequest)behandelt werden sollen.|

Überschreiben Sie den `dwContext`-Standard, um den Kontextbezeichner auf einen ausgewählten Wert festzulegen. Der Kontextbezeichner ist diesem `CHttpConnection` spezifischen Vorgang des Objekts zugeordnet, das von seinem [CInternetSession-Objekt](../../mfc/reference/cinternetsession-class.md) erstellt wurde. Der Wert wird an [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) zurückgegeben, um den Status für den Vorgang bereitzustellen, mit dem er identifiziert wurde. Weitere Informationen zum Kontextbezeichner finden Sie im Artikel [Internet First Steps: WinInet.](../../mfc/wininet-basics.md)

Mit dieser Funktion können Ausnahmen ausgelöst werden.

## <a name="see-also"></a>Siehe auch

[CInternetConnection-Klasse](../../mfc/reference/cinternetconnection-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CInternetConnection-Klasse](../../mfc/reference/cinternetconnection-class.md)<br/>
[CHttpFile-Klasse](../../mfc/reference/chttpfile-class.md)
