---
title: CGopherConnection-Klasse
ms.date: 11/04/2016
f1_keywords:
- CGopherConnection
- AFXINET/CGopherConnection
- AFXINET/CGopherConnection::CGopherConnection
- AFXINET/CGopherConnection::CreateLocator
- AFXINET/CGopherConnection::GetAttribute
- AFXINET/CGopherConnection::OpenFile
helpviewer_keywords:
- CGopherConnection [MFC], CGopherConnection
- CGopherConnection [MFC], CreateLocator
- CGopherConnection [MFC], GetAttribute
- CGopherConnection [MFC], OpenFile
ms.assetid: b5b96aea-ac99-430e-bd84-d1372b43f78f
ms.openlocfilehash: eade1a82b674d5ad2e91146559139445ef017180
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373710"
---
# <a name="cgopherconnection-class"></a>CGopherConnection-Klasse

Verwaltet die Verbindung mit einem Gopherinternetserver.

> [!NOTE]
> Die `CGopherConnection`Klassen `CGopherFile` `CGopherFileFind`, `CGopherLocator` , und ihre Mitglieder wurden veraltet, weil sie nicht auf der Windows XP-Plattform funktionieren, aber sie werden weiterhin auf früheren Plattformen arbeiten.

## <a name="syntax"></a>Syntax

```
class CGopherConnection : public CInternetConnection
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CGopherConnection::CGopherConnection](#cgopherconnection)|Erstellt ein `CGopherConnection`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CGopherConnection::CreateLocator](#createlocator)|Erstellt ein [CGopherLocator-Objekt,](../../mfc/reference/cgopherlocator-class.md) um Dateien auf einem Gopher-Server zu suchen.|
|[CGopherConnection::GetAttribute](#getattribute)|Ruft Attributinformationen zum gopher-Objekt ab.|
|[CGopherConnection::OpenFile](#openfile)|Öffnet eine Gopher-Datei.|

## <a name="remarks"></a>Bemerkungen

Der gopher-Dienst ist einer von drei Internetdiensten, die von den MFC WinInet-Klassen erkannt werden.

Die `CGopherConnection` Klasse enthält einen Konstruktor und drei zusätzliche Memberfunktionen, die den gopher-Dienst verwalten: [OpenFile](#openfile), [CreateLocator](#createlocator)und [GetAttribute](#getattribute).

Um mit einem gopher-Internetserver zu kommunizieren, müssen Sie zunächst eine Instanz von [CInternetSession](../../mfc/reference/cinternetsession-class.md)erstellen und `CGopherConnection` dann [CInternetSession::GetGopherConnection](../../mfc/reference/cinternetsession-class.md#getgopherconnection)aufrufen, die das Objekt erstellt und einen Zeiger darauf zurückgibt. Sie erstellen `CGopherConnection` nie direkt ein Objekt.

Weitere Informationen zur `CGopherConnection` Funktionsweise mit den anderen MFC-Internetklassen finden Sie im Artikel [Internetprogrammierung mit WinInet](../../mfc/win32-internet-extensions-wininet.md). Weitere Informationen zur Verwendung der beiden anderen unterstützten Internetdienste, FTP und HTTP, finden Sie in den Klassen [CHttpConnection](../../mfc/reference/chttpconnection-class.md) und [CFtpConnection](../../mfc/reference/cftpconnection-class.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CInternetConnection](../../mfc/reference/cinternetconnection-class.md)

`CGopherConnection`

## <a name="requirements"></a>Anforderungen

**Kopf:** afxinet.h

## <a name="cgopherconnectioncgopherconnection"></a><a name="cgopherconnection"></a>CGopherConnection::CGopherConnection

Diese Memberfunktion wird aufgerufen, um ein `CGopherConnection` Objekt zu erstellen.

```
CGopherConnection(
    CInternetSession* pSession,
    HINTERNET hConnected,
    LPCTSTR pstrServer,
    DWORD_PTR dwContext);

CGopherConnection(
    CInternetSession* pSession,
    LPCTSTR pstrServer,
    LPCTSTR pstrUserName = NULL,
    LPCTSTR pstrPassword = NULL,
    DWORD_PTR dwContext = 0,
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER);
```

### <a name="parameters"></a>Parameter

*pSession*<br/>
Ein Zeiger auf das zugehörige [CInternetSession-Objekt.](../../mfc/reference/cinternetsession-class.md)

*hConnected*<br/>
Das Windows-Handle der aktuellen Internetsitzung.

*pstrServer*<br/>
Ein Zeiger auf eine Zeichenfolge, die den FTP-Servernamen enthält.

*dwContext*<br/>
Der Kontextbezeichner für den Vorgang. *dwContext* identifiziert die Statusinformationen des Vorgangs, die von [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback)zurückgegeben werden. Der Standardwert ist auf 1 festgelegt. Sie können dem Vorgang jedoch explizit eine bestimmte Kontext-ID zuweisen. Das Objekt und alle Arbeiten, die es ausführt, werden dieser Kontext-ID zugeordnet.

*pstrUserName*<br/>
Zeiger auf eine null-terminierte Zeichenfolge, die den Namen des Benutzers angibt, der sich anmelden soll. Wenn NULL, ist der Standardwert anonym.

*pstrPassword*<br/>
Ein Zeiger auf eine null-terminierte Zeichenfolge, die das Kennwort angibt, das zum Anmelden verwendet werden soll. Wenn sowohl *pstrPassword* als auch *pstrUserName* NULL sind, ist das anonyme Standardkennwort der E-Mail-Name des Benutzers. Wenn *pstrPassword* NULL (oder eine leere Zeichenfolge) ist, *pstrUserName* jedoch nicht NULL ist, wird ein leeres Kennwort verwendet. In der folgenden Tabelle wird das Verhalten für die vier möglichen Einstellungen von *pstrUserName* und *pstrPassword*beschrieben:

|*pstrUserName*|*pstrPassword*|Benutzername, der an FTP-Server gesendet wird|An FTP-Server gesendetes Kennwort|
|--------------------|--------------------|---------------------------------|---------------------------------|
|NULL oder " "|NULL oder " "|"anonym"|E-Mail-Name des Benutzers|
|Nicht-NULL-Zeichenfolge|NULL oder " "|*pstrUserName*|" "|
|NULL Non- NULL String|ERROR|ERROR||
|Nicht-NULL-Zeichenfolge|Nicht-NULL-Zeichenfolge|*pstrUserName*|*pstrPassword*|

*nPort*<br/>
Eine Zahl, die den TCP/IP-Port identifiziert, der auf dem Server verwendet werden soll.

### <a name="remarks"></a>Bemerkungen

Sie erstellen `CGopherConnection` nie direkt. Rufen Sie stattdessen [CInternetSession::GetGopherConnection](../../mfc/reference/cinternetsession-class.md#getgopherconnection) `CGopherConnection` auf, das ein Objekt erstellt und einen Zeiger darauf zurückgibt.

## <a name="cgopherconnectioncreatelocator"></a><a name="createlocator"></a>CGopherConnection::CreateLocator

Rufen Sie diese Memberfunktion auf, um einen Gopher-Locator zu erstellen, um eine Datei auf einem Gopher-Server zu suchen oder zu identifizieren.

```
CGopherLocator CreateLocator(
    LPCTSTR pstrDisplayString,
    LPCTSTR pstrSelectorString,
    DWORD dwGopherType);

static CGopherLocator CreateLocator(LPCTSTR pstrLocator);

static CGopherLocator CreateLocator(
    LPCTSTR pstrServerName,
    LPCTSTR pstrDisplayString,
    LPCTSTR pstrSelectorString,
    DWORD dwGopherType,
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER);
```

### <a name="parameters"></a>Parameter

*pstrDisplayString*<br/>
Ein Zeiger auf eine Zeichenfolge, die den Namen des zu holenden Gopher-Dokuments oder Verzeichnisses enthält. Wenn der Parameter *pstrDisplayString* NULL ist, wird das Standardverzeichnis für den gopher-Server zurückgegeben.

*pstrSelectorString*<br/>
Ein Zeiger auf die Selektorzeichenfolge, die an den Gopher-Server gesendet werden soll, um ein Element abzurufen. *pstrSelectorString* kann NULL sein.

*dwGopherType*<br/>
Dies gibt an, ob *pstrSelectorString* auf ein Verzeichnis oder Dokument verweist und ob die Anforderung gopher oder gopher+ ist. Siehe die Attribute für die Struktur [GOPHER_FIND_DATA](/windows/win32/api/wininet/ns-wininet-gopher_find_dataw) im Windows SDK.

*pstrLocator*<br/>
Ein Zeiger auf eine Zeichenfolge, die die zu öffnende Datei identifiziert. Im Allgemeinen wird diese Zeichenfolge von einem Aufruf von [CGopherFileFind::GetLocator](../../mfc/reference/cgopherfilefind-class.md#getlocator)zurückgegeben.

*pstrServerName*<br/>
Ein Zeiger auf eine Zeichenfolge, die den Gopher-Servernamen enthält.

*nPort*<br/>
Die Nummer, die den Internetport für diese Verbindung identifiziert.

### <a name="return-value"></a>Rückgabewert

Ein [CGopherLocator-Objekt.](../../mfc/reference/cgopherlocator-class.md)

### <a name="remarks"></a>Bemerkungen

Die statische Version der Memberfunktion erfordert, dass Sie einen Server angeben, während die nicht statische Version den Servernamen aus dem Verbindungsobjekt verwendet.

Um Informationen von einem Gopher-Server abzurufen, muss eine Anwendung zuerst einen Gopher-Locator erhalten. Die Anwendung muss den Locator dann als undurchsichtiges Token behandeln (d. h., die Anwendung kann den Locator verwenden, aber nicht direkt manipulieren oder vergleichen). Normalerweise verwendet die Anwendung den Locator für Aufrufe der [CGopherFileFind::FindFile-Memberfunktion,](../../mfc/reference/cgopherfilefind-class.md#findfile) um eine bestimmte Information abzurufen.

## <a name="cgopherconnectiongetattribute"></a><a name="getattribute"></a>CGopherConnection::GetAttribute

Rufen Sie diese Memberfunktion auf, um bestimmte Attributinformationen zu einem Element vom Gopher-Server abzurufen.

```
BOOL GetAttribute(
    CGopherLocator& refLocator    CString strRequestedAttributes,
    CString& strResult,);
```

### <a name="parameters"></a>Parameter

*refLocator*<br/>
Ein Verweis auf ein [CGopherLocator-Objekt.](../../mfc/reference/cgopherlocator-class.md)

*strRequestedAttributes*<br/>
Eine durch Leerzeichen getrennte Zeichenfolge, die die Namen der angeforderten Attribute angibt.

*strResult*<br/>
Ein Verweis auf einen [CString,](../../atl-mfc-shared/reference/cstringt-class.md) der den Locator-Typ empfängt.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null). Wenn der Aufruf fehlschlägt, kann die Win32-Funktion [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) aufgerufen werden, um die Ursache des Fehlers zu ermitteln.

## <a name="cgopherconnectionopenfile"></a><a name="openfile"></a>CGopherConnection::OpenFile

Rufen Sie diese Memberfunktion auf, um eine Datei auf einem Gopher-Server zu öffnen.

```
CGopherFile* OpenFile(
    CGopherLocator& refLocator,
    DWORD dwFlags = 0,
    LPCTSTR pstrView = NULL,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>Parameter

*refLocator*<br/>
Ein Verweis auf ein [CGopherLocator-Objekt.](../../mfc/reference/cgopherlocator-class.md)

*dwFlags*<br/>
Jede Kombination von INTERNET_FLAG_*-Flags. Weitere Informationen zu INTERNET_FLAG_-Flags\* finden Sie unter [CInternetSession::OpenUrl.](../../mfc/reference/cinternetsession-class.md#openurl)

*pstrView*<br/>
Ein Zeiger auf eine Dateiansichtszeichenfolge. Wenn mehrere Ansichten der Datei auf dem Server vorhanden sind, gibt dieser Parameter an, welche Dateiansicht geöffnet werden soll. Wenn *pstrView* NULL ist, wird die Standarddateiansicht verwendet.

*dwContext*<br/>
Die Kontext-ID für die zu öffnende Datei. Weitere Informationen zu *dwContext*finden Sie unter **Hinweise** .

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das zu öffnende [CGopherFile-Objekt.](../../mfc/reference/cgopherfile-class.md)

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie die *standardeinstellung dwContext,* um den Kontextbezeichner auf einen Wert Ihrer Wahl festzulegen. Der Kontextbezeichner ist diesem `CGopherConnection` spezifischen Vorgang des Objekts zugeordnet, das von seinem [CInternetSession-Objekt](../../mfc/reference/cinternetsession-class.md) erstellt wurde. Der Wert wird an [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) zurückgegeben, um den Status für den Vorgang bereitzustellen, mit dem er identifiziert wird. Weitere Informationen zum Kontextbezeichner finden Sie im Artikel [Internet First Steps: WinInet.](../../mfc/wininet-basics.md)

## <a name="see-also"></a>Siehe auch

[CInternetConnection-Klasse](../../mfc/reference/cinternetconnection-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CFtpConnection-Klasse](../../mfc/reference/cftpconnection-class.md)<br/>
[CHttpConnection-Klasse](../../mfc/reference/chttpconnection-class.md)<br/>
[CInternetConnection-Klasse](../../mfc/reference/cinternetconnection-class.md)<br/>
[CGopherLocator-Klasse](../../mfc/reference/cgopherlocator-class.md)<br/>
[CGopherFile-Klasse](../../mfc/reference/cgopherfile-class.md)<br/>
[CInternetSession-Klasse](../../mfc/reference/cinternetsession-class.md)
