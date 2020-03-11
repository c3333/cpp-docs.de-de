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
ms.openlocfilehash: f5d655aa7fd2eb9e41c15c60a71492c24ba43c43
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78883901"
---
# <a name="cgopherconnection-class"></a>CGopherConnection-Klasse

Verwaltet die Verbindung mit einem Gopherinternetserver.

> [!NOTE]
>  Die Klassen `CGopherConnection`, `CGopherFile`, `CGopherFileFind`, `CGopherLocator` und deren Member sind veraltet, da Sie nicht auf der Windows XP-Plattform funktionieren, aber Sie funktionieren weiterhin auf früheren Plattformen.

## <a name="syntax"></a>Syntax

```
class CGopherConnection : public CInternetConnection
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CGopherConnection:: CGopherConnection](#cgopherconnection)|Erstellt ein `CGopherConnection`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CGopherConnection:: anatelocator](#createlocator)|Erstellt ein [CGopherLocator](../../mfc/reference/cgopherlocator-class.md) -Objekt, um Dateien auf einem Gopher-Server zu suchen.|
|[CGopherConnection:: GetAttribute](#getattribute)|Ruft Attributinformationen über das Gopher-Objekt ab.|
|[CGopherConnection:: OpenFile](#openfile)|Öffnet eine Gopher-Datei.|

## <a name="remarks"></a>Bemerkungen

Der Gopher-Dienst ist einer von drei Internet Diensten, die von den MFC-WinInet-Klassen erkannt werden.

Die-Klasse `CGopherConnection` enthält einen Konstruktor und drei zusätzliche Member-Funktionen, die den Gopher-Dienst verwalten: [OpenFile](#openfile), [foatelocator](#createlocator)und [GetAttribute](#getattribute).

Um mit einem Gopher-Internet Server zu kommunizieren, müssen Sie zuerst eine Instanz von [cinternetzession](../../mfc/reference/cinternetsession-class.md)erstellen und dann [cinternetzession:: GetGopherConnection](../../mfc/reference/cinternetsession-class.md#getgopherconnection)aufrufen, wodurch das `CGopherConnection` Objekt erstellt und ein Zeiger darauf zurückgegeben wird. Sie erstellen niemals direkt ein `CGopherConnection` Objekt.

Weitere Informationen zur Funktionsweise von `CGopherConnection` mit den anderen MFC-Internet Klassen finden Sie im Artikel [Internet Programmierung mit WinInet](../../mfc/win32-internet-extensions-wininet.md). Weitere Informationen zur Verwendung der anderen beiden unterstützten Internet Dienste finden Sie unter den Klassen " [CHttpConnection](../../mfc/reference/chttpconnection-class.md) " und " [CFtpConnection](../../mfc/reference/cftpconnection-class.md)".

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)

[CInternetConnection](../../mfc/reference/cinternetconnection-class.md)

`CGopherConnection`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** AFXINET. h

##  <a name="cgopherconnection"></a>CGopherConnection:: CGopherConnection

Diese Member-Funktion wird aufgerufen, um ein `CGopherConnection` Objekt zu erstellen.

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

*psession*<br/>
Ein Zeiger auf das zugehörige [cinternetzession](../../mfc/reference/cinternetsession-class.md) -Objekt.

*hconnected*<br/>
Das Windows-Handle der aktuellen Internet Sitzung.

*pstrinserver*<br/>
Ein Zeiger auf eine Zeichenfolge, die den FTP-Servernamen enthält.

*dwcontext*<br/>
Der Kontext Bezeichner für den Vorgang. *dwcontext* identifiziert die von [cinternetzession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback)zurückgegebenen Statusinformationen des Vorgangs. Der Standardwert wird auf 1 festgelegt. Sie können jedoch explizit eine bestimmte Kontext-ID für den Vorgang zuweisen. Das-Objekt und alle Aufgaben, die es durchführt, werden mit dieser Kontext-ID verknüpft.

*pstrusername*<br/>
Zeiger auf eine mit NULL endenden Zeichenfolge, die den Namen des Benutzers angibt, der angemeldet werden soll. Wenn der Wert NULL ist, ist der Standardwert Anonymous.

*pstraupassword*<br/>
Ein Zeiger auf eine mit NULL endende Zeichenfolge, die das Kennwort für die Anmeldung angibt. Wenn sowohl *pstraupassword* als auch *pstrusername* NULL sind, ist das anonyme Standard Kennwort der e-Mail-Name des Benutzers. Wenn *pstraupassword* NULL (oder eine leere Zeichenfolge) ist, aber *pstrusername* nicht NULL ist, wird ein leeres Kennwort verwendet. In der folgenden Tabelle wird das Verhalten der vier möglichen Einstellungen von *pstrusername* und *pstrinpassword*beschrieben:

|*pstrusername*|*pstraupassword*|An FTP-Server gesendeter Benutzername|Kennwort an FTP-Server gesendet|
|--------------------|--------------------|---------------------------------|---------------------------------|
|NULL oder ""|NULL oder ""|Anonymous|E-Mail-Name des Benutzers|
|Zeichenfolge ungleich NULL|NULL oder ""|*pstrusername*|„ “|
|NULL-Zeichenfolge ungleich NULL|ERROR|ERROR||
|Zeichenfolge ungleich NULL|Zeichenfolge ungleich NULL|*pstrusername*|*pstraupassword*|

*Nport*<br/>
Eine Zahl, die den auf dem Server zu verwendenden TCP/IP-Port identifiziert.

### <a name="remarks"></a>Bemerkungen

Sie erstellen niemals direkt einen `CGopherConnection`. Stattdessen wird [cinternetzession:: GetGopherConnection](../../mfc/reference/cinternetsession-class.md#getgopherconnection)aufgerufen, das ein `CGopherConnection` Objekt erstellt und einen Zeiger darauf zurückgibt.

##  <a name="createlocator"></a>CGopherConnection:: anatelocator

Rufen Sie diese Member-Funktion auf, um einen Gopher-Serverlocatorpunkt zum Suchen oder identifizieren einer Datei auf einem Gopher-Server zu erstellen.

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

*pstrindisplaystring*<br/>
Ein Zeiger auf eine Zeichenfolge, die den Namen des zu abzurufenden gopyour-Dokuments oder-Verzeichnisses enthält. Wenn der *pstrindisplaystring* -Parameter NULL ist, wird das Standardverzeichnis für den Gopher-Server zurückgegeben.

*pstrinselector String*<br/>
Ein Zeiger auf die Auswahl Zeichenfolge, die an den Gopher-Server gesendet werden soll, um ein Element abzurufen. *pstrinselector String* kann NULL sein.

*dwgophertype*<br/>
Hiermit wird angegeben, ob *pstrinselector String* auf ein Verzeichnis oder Dokument verweist und ob die Anforderung Gopher oder Gopher + ist. Weitere Informationen finden Sie in den Attributen für die Struktur [GOPHER_FIND_DATA](/windows/win32/api/wininet/ns-wininet-gopher_find_dataw) in der Windows SDK.

*pstranlocator*<br/>
Ein Zeiger auf eine Zeichenfolge, die die zu öffnende Datei identifiziert. Im Allgemeinen wird diese Zeichenfolge von einem [CGopherFileFind:: GetLocator](../../mfc/reference/cgopherfilefind-class.md#getlocator)-Befehl zurückgegeben.

*pstrauservername*<br/>
Ein Zeiger auf eine Zeichenfolge, die den Gopher-Servernamen enthält.

*Nport*<br/>
Die Nummer, die den Internetport für diese Verbindung identifiziert.

### <a name="return-value"></a>Rückgabewert

Ein [CGopherLocator](../../mfc/reference/cgopherlocator-class.md) -Objekt.

### <a name="remarks"></a>Bemerkungen

Die statische Version der Member-Funktion erfordert, dass Sie einen Server angeben, während die nicht statische Version den Servernamen aus dem Verbindungs Objekt verwendet.

Um Informationen von einem Gopher-Server abrufen zu können, muss eine Anwendung zuerst einen Gopher-Locator erhalten. Die Anwendung muss dann den Serverlocatorpunkt als ein undurchsichtiges Token behandeln (d. h., die Anwendung kann den Serverlocatorpunkt verwenden, aber nicht direkt bearbeiten oder vergleichen). Normalerweise verwendet die Anwendung den Serverlocatorpunkt für Aufrufe der [CGopherFileFind:: FindFile](../../mfc/reference/cgopherfilefind-class.md#findfile) -Member-Funktion, um ein bestimmtes Informationselement abzurufen.

##  <a name="getattribute"></a>CGopherConnection:: GetAttribute

Rufen Sie diese Member-Funktion auf, um bestimmte Attributinformationen zu einem Element vom Gopher-Server abzurufen.

```
BOOL GetAttribute(
    CGopherLocator& refLocator    CString strRequestedAttributes,
    CString& strResult,);
```

### <a name="parameters"></a>Parameter

*reflocator*<br/>
Ein Verweis auf ein [CGopherLocator](../../mfc/reference/cgopherlocator-class.md) -Objekt.

*"Strauch Daten"*<br/>
Eine durch Leerzeichen getrennte Zeichenfolge, die die Namen der angeforderten Attribute angibt.

*Strauch Ergebnis*<br/>
Ein Verweis auf eine [CString](../../atl-mfc-shared/reference/cstringt-class.md) , die den Locatortyp empfängt.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null). Wenn der Aufruf fehlschlägt, kann die Win32-Funktion [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) aufgerufen werden, um die Ursache des Fehlers zu ermitteln.

##  <a name="openfile"></a>CGopherConnection:: OpenFile

Mit dieser Member-Funktion können Sie eine Datei auf einem Gopher-Server öffnen.

```
CGopherFile* OpenFile(
    CGopherLocator& refLocator,
    DWORD dwFlags = 0,
    LPCTSTR pstrView = NULL,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>Parameter

*reflocator*<br/>
Ein Verweis auf ein [CGopherLocator](../../mfc/reference/cgopherlocator-class.md) -Objekt.

*dwFlags*<br/>
Eine beliebige Kombination von INTERNET_FLAG_ *-Flags. Weitere Informationen zu INTERNET_FLAG_\* Flags finden Sie unter [cinternetzession:: OpenURL](../../mfc/reference/cinternetsession-class.md#openurl) .

*pstrauview*<br/>
Ein Zeiger auf eine Datei Ansichts Zeichenfolge. Wenn mehrere Ansichten der Datei auf dem Server vorhanden sind, gibt dieser Parameter an, welche Dateiansicht geöffnet werden soll. Wenn *pstrauview* NULL ist, wird die standardmäßige Dateiansicht verwendet.

*dwcontext*<br/>
Die Kontext-ID für die Datei, die geöffnet wird. Weitere Informationen zu *dwcontext*finden Sie unter " **Hinweise** ".

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das zu öffnende [CGopherFile](../../mfc/reference/cgopherfile-class.md) -Objekt.

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie den *dwcontext* -Standard, um den Kontext Bezeichner auf einen Wert Ihrer Wahl festzulegen. Der Kontext Bezeichner ist diesem speziellen Vorgang des `CGopherConnection` Objekts zugeordnet, das vom [cinternetzession](../../mfc/reference/cinternetsession-class.md) -Objekt erstellt wurde. Der Wert wird an [cinternetzession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) zurückgegeben, um den Status für den Vorgang bereitzustellen, mit dem er identifiziert wird. Weitere Informationen zum Kontext Bezeichner finden Sie im Artikel [Internet First Steps: WinInet](../../mfc/wininet-basics.md) .

## <a name="see-also"></a>Weitere Informationen

[CInternetConnection-Klasse](../../mfc/reference/cinternetconnection-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CFtpConnection-Klasse](../../mfc/reference/cftpconnection-class.md)<br/>
[CHttpConnection-Klasse](../../mfc/reference/chttpconnection-class.md)<br/>
[CInternetConnection-Klasse](../../mfc/reference/cinternetconnection-class.md)<br/>
[CGopherLocator-Klasse](../../mfc/reference/cgopherlocator-class.md)<br/>
[CGopherFile-Klasse](../../mfc/reference/cgopherfile-class.md)<br/>
[CInternetSession-Klasse](../../mfc/reference/cinternetsession-class.md)
