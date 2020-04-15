---
title: CInternetSession-Klasse
ms.date: 06/20/2018
f1_keywords:
- CInternetSession
- AFXINET/CInternetSession
- AFXINET/CInternetSession::CInternetSession
- AFXINET/CInternetSession::Close
- AFXINET/CInternetSession::EnableStatusCallback
- AFXINET/CInternetSession::GetContext
- AFXINET/CInternetSession::GetCookie
- AFXINET/CInternetSession::GetCookieLength
- AFXINET/CInternetSession::GetFtpConnection
- AFXINET/CInternetSession::GetGopherConnection
- AFXINET/CInternetSession::GetHttpConnection
- AFXINET/CInternetSession::OnStatusCallback
- AFXINET/CInternetSession::OpenURL
- AFXINET/CInternetSession::SetCookie
- AFXINET/CInternetSession::SetOption
helpviewer_keywords:
- CInternetSession [MFC], CInternetSession
- CInternetSession [MFC], Close
- CInternetSession [MFC], EnableStatusCallback
- CInternetSession [MFC], GetContext
- CInternetSession [MFC], GetCookie
- CInternetSession [MFC], GetCookieLength
- CInternetSession [MFC], GetFtpConnection
- CInternetSession [MFC], GetGopherConnection
- CInternetSession [MFC], GetHttpConnection
- CInternetSession [MFC], OnStatusCallback
- CInternetSession [MFC], OpenURL
- CInternetSession [MFC], SetCookie
- CInternetSession [MFC], SetOption
ms.assetid: ef54feb4-9d0f-4e65-a45d-7a4cf6c40e51
ms.openlocfilehash: ddd7ca6676805e6de1b7afb5ebc77733701dfef9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372382"
---
# <a name="cinternetsession-class"></a>CInternetSession-Klasse

Erstellt und initialisiert einzelne oder mehrere gleichzeitige Internetsitzungen und beschreibt ggf. die Verbindung mit einem Proxyserver.

## <a name="syntax"></a>Syntax

```cpp
class CInternetSession : public CObject
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CInternetSession::CInternetSession](#cinternetsession)|Erstellt ein `CInternetSession`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CInternetSession::Schließen](#close)|Schließt die Internetverbindung, wenn die Internetsitzung beendet wird.|
|[CInternetSession::EnableStatusCallback](#enablestatuscallback)|Richtet eine Statusrückrufroutine ein.|
|[CInternetSession::GetContext](#getcontext)|Schließt die Internetverbindung, wenn die Internetsitzung beendet wird.|
|[CInternetSession::GetCookie](#getcookie)|Gibt Cookies für die angegebene URL und alle übergeordneten URLs zurück.|
|[CInternetSession::GetCookieLength](#getcookielength)|Ruft die Variable ab, die die Länge des im Puffer gespeicherten Cookies angibt.|
|[CInternetSession::GetFtpConnection](#getftpconnection)|Öffnet eine FTP-Sitzung mit einem Server. Meldet sich beim Benutzer an.|
|[CInternetSession::GetGopherConnection](#getgopherconnection)|Öffnet einen Gopherserver für eine Anwendung, die versucht, eine Verbindung zu öffnen.|
|[CInternetSession::GetHttpConnection](#gethttpconnection)|Öffnet einen HTTP-Server für eine Anwendung, die versucht, eine Verbindung zu öffnen.|
|[CInternetSession::OnStatusCallback](#onstatuscallback)|Aktualisiert den Status eines Vorgangs, wenn der Statusrückruf aktiviert ist.|
|[CInternetSession::OpenURL](#openurl)|Analysiert und öffnet eine URL.|
|[CInternetSession::SetCookie](#setcookie)|Legt ein Cookie für die angegebene URL fest.|
|[CInternetSession::SetOption](#setoption)|Legt Optionen für die Internetsitzung fest.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CInternetSession::operator HINTERNET](#operator_hinternet)|Ein Handle für die aktuelle Internetsitzung.|

## <a name="remarks"></a>Bemerkungen

Wenn Ihre Internetverbindung für die Dauer einer Anwendung aufrechterhalten `CInternetSession` werden muss, können Sie ein Mitglied der Klasse [CWinApp](../../mfc/reference/cwinapp-class.md)erstellen.

Nachdem Sie eine Internetsitzung eingerichtet haben, können Sie [OpenURL](#openurl)aufrufen. `CInternetSession`analysiert dann die URL für Sie, indem die globale Funktion [AfxParseURL](internet-url-parsing-globals.md#afxparseurl)aufgerufen wird. Unabhängig vom Protokolltyp `CInternetSession` interpretiert die URL und verwaltet sie für Sie. Es kann Anforderungen für lokale Dateien verarbeiten, die mit der URL-Ressource "file://" identifiziert wurden. `OpenURL`gibt einen Zeiger auf ein [CStdioFile-Objekt](../../mfc/reference/cstdiofile-class.md) zurück, wenn es sich bei dem übergebenen Namen um eine lokale Datei handelt.

Wenn Sie eine URL auf `OpenURL`einem Internetserver mit öffnen, können Sie Informationen von der Website lesen. Wenn Sie dienstspezifische Aktionen (z. B. HTTP, FTP oder Gopher) für Dateien auf einem Server ausführen möchten, müssen Sie die entsprechende Verbindung mit diesem Server herstellen. Um eine bestimmte Art von Verbindung direkt zu einem bestimmten Dienst zu öffnen, verwenden Sie eine der folgenden Memberfunktionen:

- [GetGopherConnection,](#getgopherconnection) um eine Verbindung zu einem Gopher-Dienst zu öffnen.

- [GetHttpConnection,](#gethttpconnection) um eine Verbindung zu einem HTTP-Dienst zu öffnen.

- [GetFtpConnection,](#getftpconnection) um eine Verbindung zu einem FTP-Dienst zu öffnen.

[Mit SetOption](#setoption) können Sie die Abfrageoptionen Ihrer Sitzung festlegen, z. B. Timeoutwerte, Anzahl der Wiederholungen usw.

`CInternetSession`Die Mitgliedsfunktionen [SetCookie](#setcookie), [GetCookie](#getcookie)und [GetCookieLength](#getcookielength) bieten die Möglichkeit, eine Win32-Cookiedatenbank zu verwalten, über die Server und Skripts Statusinformationen über die Client-Workstation verwalten.

Weitere Informationen zu grundlegenden Internetprogrammierungsaufgaben finden Sie im Artikel [Internet First Steps: WinInet](../../mfc/wininet-basics.md). Allgemeine Informationen zur Verwendung der MFC WinInet-Klassen finden Sie im Artikel [Internetprogrammierung mit WinInet](../../mfc/win32-internet-extensions-wininet.md).

> [!NOTE]
> `CInternetSession`löst eine [AfxThrowNotSupportedException](exception-processing.md#afxthrownotsupportedexception) für nicht unterstützte Diensttypen aus. Derzeit werden nur die folgenden Diensttypen unterstützt: FTP, HTTP, gopher und Datei.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)<br/>
&nbsp;&nbsp;&nbsp;&nbsp;`CInternetSession`

## <a name="requirements"></a>Anforderungen

**Kopf:** afxinet.h

## <a name="cinternetsessioncinternetsession"></a><a name="cinternetsession"></a>CInternetSession::CInternetSession

Diese Memberfunktion wird `CInternetSession` aufgerufen, wenn ein Objekt erstellt wird.

```cpp
CInternetSession(
    LPCTSTR pstrAgent = NULL,
    DWORD_PTR dwContext = 1,
    DWORD dwAccessType = PRE_CONFIG_INTERNET_ACCESS,
    LPCTSTR pstrProxyName = NULL,
    LPCTSTR pstrProxyBypass = NULL,
    DWORD dwFlags = 0);
```

### <a name="parameters"></a>Parameter

*pstrAgent*<br/>
Ein Zeiger auf eine Zeichenfolge, die den Namen der Anwendung oder Entität identifiziert, die die Internetfunktionen aufruft (z. B. "Microsoft Internet Browser"). Wenn *pstrAgent* NULL (Standard) ist, ruft das Framework die globale Funktion [AfxGetAppName](application-information-and-management.md#afxgetappname)auf, die eine null-terminierte Zeichenfolge zurückgibt, die den Namen einer Anwendung enthält. Einige Protokolle verwenden diese Zeichenfolge, um Ihre Anwendung auf dem Server zu identifizieren.

*dwContext*<br/>
Der Kontextbezeichner für den Vorgang. *dwContext* identifiziert die Statusinformationen des Vorgangs, die von [CInternetSession::OnStatusCallback](#onstatuscallback)zurückgegeben werden. Der Standardwert ist auf 1 festgelegt. Sie können dem Vorgang jedoch explizit eine bestimmte Kontext-ID zuweisen. Das Objekt und alle Arbeiten, die es ausführt, werden dieser Kontext-ID zugeordnet.

*dwAccessType*<br/>
Der erforderliche Zugriffstyp. Die folgenden Werte sind gültig, von denen genau einer angegeben werden kann:

- INTERNET_OPEN_TYPE_PRECONFIG Verbinden Sie sich mit vorkonfigurierten Einstellungen in der Registrierung. Dieser Zugriffstyp wird als Standard festgelegt. Um eine Verbindung über einen TIS-Proxy herzustellen, legen Sie *dwAccessType* auf diesen Wert fest. Legen Sie dann die Registrierung entsprechend fest.

- INTERNET_OPEN_TYPE_DIRECT Stellen Sie sich direkt mit dem Internet in Verbindung.

- INTERNET_OPEN_TYPE_PROXY verbinden Sie sich über einen CERN-Proxy.

Informationen zum Herstellen einer Verbindung mit verschiedenen Proxytypen finden Sie unter [Schritte in einer typischen FTP-Clientanwendung](../../mfc/steps-in-a-typical-ftp-client-application.md).

*pstrProxyName*<br/>
Der Name des bevorzugten CERN-Proxys, wenn *dwAccessType* als INTERNET_OPEN_TYPE_PROXY festgelegt ist. Die Standardeinstellung ist NULL.

*pstrProxyBypass*<br/>
Ein Zeiger auf eine Zeichenfolge, die eine optionale Liste von Serveradressen enthält. Diese Adressen können umgangen werden, wenn Der Proxyzugriff verwendet wird. Wenn ein NULL-Wert angegeben wird, wird die Umgehungsliste aus der Registrierung gelesen. Dieser Parameter ist nur dann aussagekräftig, wenn *dwAccessType* auf INTERNET_OPEN_TYPE_PROXY festgelegt ist.

*dwFlags*<br/>
Gibt verschiedene Caching-Optionen an. Der Standardwert ist auf 0 festgelegt. Folgende Werte sind zulässig:

- INTERNET_FLAG_DONT_CACHE Die Daten nicht lokal oder auf Gatewayservern zwischenspeichern.

- INTERNET_FLAG_OFFLINE Downloadvorgänge werden nur über den persistenten Cache erfüllt. Wenn das Element nicht im Cache vorhanden ist, wird ein entsprechender Fehlercode zurückgegeben. Dieses Flag kann mit dem bitweisen **Operator ODER** ( **&#124;**) kombiniert werden.

### <a name="remarks"></a>Bemerkungen

`CInternetSession`ist die erste Internetfunktion, die von einer Anwendung aufgerufen wird. Es initialisiert interne Datenstrukturen und bereitet sich auf zukünftige Aufrufe aus der Anwendung vor.

Wenn keine Internetverbindung geöffnet `CInternetSession` werden kann, wird eine [AfxThrowInternetException](internet-url-parsing-globals.md#afxthrowinternetexception)ausgelöst.

### <a name="example"></a>Beispiel

Siehe Beispiel für [CFtpFileFind](../../mfc/reference/cftpfilefind-class.md).

## <a name="cinternetsessionclose"></a><a name="close"></a>CInternetSession::Schließen

Rufen Sie diese Memberfunktion auf, `CInternetSession` wenn die Anwendung das Objekt verwendet hat.

```cpp
virtual void Close();
```

### <a name="example"></a>Beispiel

Siehe Beispiel für [CFtpFileFind](../../mfc/reference/cftpfilefind-class.md).

## <a name="cinternetsessionenablestatuscallback"></a><a name="enablestatuscallback"></a>CInternetSession::EnableStatusCallback

Rufen Sie diese Memberfunktion auf, um den Statusrückruf zu aktivieren.

```cpp
BOOL EnableStatusCallback(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parameter

*bEnable*<br/>
Gibt an, ob der Rückruf aktiviert oder deaktiviert ist. Der Standardwert ist TRUE.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null). Wenn der Aufruf fehlschlägt, ermitteln Sie die Ursache des Fehlers, indem Sie das ausgelöste [CInternetException-Objekt](../../mfc/reference/cinternetexception-class.md) untersuchen.

### <a name="remarks"></a>Bemerkungen

Bei der Behandlung des Statusrückrufs können Sie in der Statusleiste der Anwendung den Status über den Fortschritt des Vorgangs angeben (z. B. Das Auflösen des Namens, herstellen mit dem Server usw.). Die Anzeige des Betriebsstatus ist besonders bei einem Langzeitbetrieb wünschenswert.

Da während der Verarbeitung der Anforderung Rückrufe auftreten, sollte die Anwendung so wenig Zeit wie möglich mit dem Rückruf verbringen, um eine Verschlechterung des Datendurchsatzes im Netzwerk zu verhindern. Beispielsweise kann das Einrichten eines Dialogfelds in einem Rückruf ein so langer Vorgang sein, dass der Server die Anforderung beendet.

Der Statusrückruf kann nicht entfernt werden, solange Rückrufe ausstehen.

Um Vorgänge asynchron zu behandeln, müssen Sie entweder einen eigenen Thread erstellen oder die WinInet-Funktionen ohne MFC verwenden.

## <a name="cinternetsessiongetcontext"></a><a name="getcontext"></a>CInternetSession::GetContext

Rufen Sie diese Memberfunktion auf, um den Kontextwert für eine bestimmte Anwendungssitzung abzurufen.

```cpp
DWORD_PTR GetContext() const;
```

### <a name="return-value"></a>Rückgabewert

Der anwendungsdefinierte Kontextbezeichner.

### <a name="remarks"></a>Bemerkungen

[OnStatusCallback](#onstatuscallback) verwendet die Kontext-ID, die von `GetContext` zurückgegeben wird, um den Status einer bestimmten Anwendung zu melden. Wenn ein Benutzer beispielsweise eine Internetanforderung aktiviert, die die Rückgabe von Statusinformationen umfasst, verwendet der Statusrückruf die Kontext-ID, um den Status für diese bestimmte Anforderung zu melden. Wenn der Benutzer zwei separate Internetanforderungen aktiviert, `OnStatusCallback` bei denen beide Statusinformationen zurückgeben, verwendet er die Kontextbezeichner, um den Status für die entsprechenden Anforderungen zurückzugeben. Folglich wird der Kontextbezeichner für alle Statusrückrufvorgänge verwendet und der Sitzung zugeordnet, bis die Sitzung beendet ist.

Weitere Informationen zu asynchronen Vorgängen finden Sie im Artikel [Internet First Steps: WinInet](../../mfc/wininet-basics.md).

## <a name="cinternetsessiongetcookie"></a><a name="getcookie"></a>CInternetSession::GetCookie

Diese Memberfunktion implementiert das Verhalten der Win32-Funktion [InternetGetCookie](/windows/win32/api/wininet/nf-wininet-internetgetcookiew), wie im Windows SDK beschrieben.

```cpp
static BOOL GetCookie(
    LPCTSTR pstrUrl,
    LPCTSTR pstrCookieName,
    LPTSTR pstrCookieData,
    DWORD dwBufLen);

static BOOL GetCookie(
    LPCTSTR pstrUrl,
    LPCTSTR pstrCookieName,
    CString& strCookieData);
```

### <a name="parameters"></a>Parameter

*pstrUrl*<br/>
Ein Zeiger auf eine Zeichenfolge, die die URL enthält.

*pstrCookieName*<br/>
Ein Zeiger auf eine Zeichenfolge, die den Namen des Cookies enthält, das für die angegebene URL abzurufen ist.

*pstrCookieData*<br/>
In der ersten Überladung ein Zeiger auf eine Zeichenfolge, die die Adresse des Puffers enthält, der die Cookie-Daten empfängt. Dieser Wert kann NULL sein. In der zweiten Überladung ein Verweis auf ein [CString-Objekt,](../../atl-mfc-shared/reference/cstringt-class.md) um die Cookie-Daten zu empfangen.

*dwBufLen*<br/>
Die Variable, die die Größe des *pstrCookieData-Puffers* angibt. Wenn die Funktion erfolgreich ist, empfängt der Puffer die Menge der in den *pstrCookieData-Puffer* kopierten Daten. Wenn *pstrCookieData* NULL ist, erhält dieser Parameter einen Wert, der die Größe des Puffers angibt, der zum Kopieren aller Cookie-Daten erforderlich ist.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE zurück, wenn erfolgreich, oder FALSE andernfalls. Wenn der Aufruf fehlschlägt, rufen Sie die Win32-Funktion [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) auf, um die Ursache des Fehlers zu ermitteln. Es gelten die folgenden Fehlerwerte:

- ERROR_NO_MORE_ITEMS Es gibt kein Cookie für die angegebene URL und alle übergeordneten Dateien.

- ERROR_INSUFFICIENT_BUFFER Der in *dwBufLen* übergebene Wert reicht nicht aus, um alle Cookie-Daten zu kopieren. Der in *dwBufLen* zurückgegebene Wert ist die Größe des Puffers, der zum Abrufen aller Daten erforderlich ist.

### <a name="remarks"></a>Bemerkungen

Bei der zweiten Überladung ruft MFC die `CString` Cookie-Daten in das angegebene Objekt ab.

## <a name="cinternetsessiongetcookielength"></a><a name="getcookielength"></a>CInternetSession::GetCookieLength

Rufen Sie diese Memberfunktion auf, um die Länge des Cookies abzurufen, das im Puffer gespeichert wird.

```cpp
static DWORD GetCookieLength(
    LPCTSTR pstrUrl,
    LPCTSTR pstrCookieName);
```

### <a name="parameters"></a>Parameter

*pstrUrl*<br/>
Ein Zeiger auf eine Zeichenfolge, die die URL enthält

*pstrCookieName*<br/>
Ein Zeiger auf eine Zeichenfolge, die den Namen des Cookies enthält.

### <a name="return-value"></a>Rückgabewert

Ein DWORD-Wert, der die Länge des Cookies angibt, der im Puffer gespeichert ist. Null, wenn kein Cookie mit dem von *pstrCookieName* angegebenen Namen vorhanden ist.

### <a name="remarks"></a>Bemerkungen

Dieser Wert wird von [GetCookie](#getcookie)verwendet.

## <a name="cinternetsessiongetftpconnection"></a><a name="getftpconnection"></a>CInternetSession::GetFtpConnection

Rufen Sie diese Memberfunktion auf, um eine `CFtpConnection` FTP-Verbindung herzustellen und einen Zeiger auf ein Objekt abzurufen.

```cpp
CFtpConnection* GetFtpConnection(
    LPCTSTR pstrServer,
    LPCTSTR pstrUserName = NULL,
    LPCTSTR pstrPassword = NULL,
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER,
    BOOL bPassive = FALSE);
```

### <a name="parameters"></a>Parameter

*pstrServer*<br/>
Ein Zeiger auf eine Zeichenfolge, die den FTP-Servernamen enthält.

*pstrUserName*<br/>
Zeiger auf eine null-terminierte Zeichenfolge, die den Namen des Benutzers angibt, der sich anmelden soll. Wenn NULL, ist der Standardwert anonym.

*pstrPassword*<br/>
Ein Zeiger auf eine null-terminierte Zeichenfolge, die das Kennwort angibt, das zum Anmelden verwendet werden soll. Wenn sowohl *pstrPassword* als auch *pstrUserName* NULL sind, ist das anonyme Standardkennwort der E-Mail-Name des Benutzers. Wenn *pstrPassword* NULL (oder eine leere Zeichenfolge) ist, *pstrUserName* jedoch nicht NULL ist, wird ein leeres Kennwort verwendet. In der folgenden Tabelle wird das Verhalten für die vier möglichen Einstellungen von *pstrUserName* und *pstrPassword*beschrieben:

| *pstrUserName*  | *pstrPassword*  | Benutzername, der an FTP-Server gesendet wird | An FTP-Server gesendetes Kennwort |
|-----------------|-----------------|-----------------------------|-----------------------------|
|   NULL oder " "   |   NULL oder " "   |         "anonym"         |      E-Mail-Name des Benutzers      |
| Nicht-NULL-Zeichenfolge |   NULL oder " "   |       *pstrUserName*        |             " "             |
|      NULL       | Nicht-NULL-Zeichenfolge |            ERROR            |            ERROR            |
| Nicht-NULL-Zeichenfolge | Nicht-NULL-Zeichenfolge |       *pstrUserName*        |       *pstrPassword*        |

*nPort*<br/>
Eine Zahl, die den TCP/IP-Port identifiziert, der auf dem Server verwendet werden soll.

*bPassiv*<br/>
Gibt den passiven oder aktiven Modus für diese FTP-Sitzung an. Wenn auf TRUE festgelegt, wird die `dwFlag` Win32-API auf INTERNET_FLAG_PASSIVE festgelegt.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf ein [CFtpConnection-Objekt.](../../mfc/reference/cftpconnection-class.md) Wenn der Aufruf fehlschlägt, ermitteln Sie die Ursache des Fehlers, indem Sie das ausgelöste [CInternetException-Objekt](../../mfc/reference/cinternetexception-class.md) untersuchen.

### <a name="remarks"></a>Bemerkungen

`GetFtpConnection`stellt eine Verbindung zu einem FTP-Server her `CFTPConnection` und erstellt und gibt einen Zeiger auf ein Objekt zurück. Es führt keinen bestimmten Vorgang auf dem Server aus. Wenn Sie z. B. Dateien lesen oder in Dateien schreiben möchten, müssen Sie diese Vorgänge in separaten Schritten ausführen. Informationen zum Suchen nach Dateien, Öffnen von Dateien und Lesen oder Schreiben in Dateien finden Sie in den Klassen [CFtpConnection](../../mfc/reference/cftpconnection-class.md) und [CFtpFileFind.](../../mfc/reference/cftpfilefind-class.md) Im Artikel [Internetprogrammierung mit WinInet](../../mfc/win32-internet-extensions-wininet.md) finden Sie Schritte zum Ausführen allgemeiner FTP-Verbindungsaufgaben.

### <a name="example"></a>Beispiel

Siehe Beispiel für [CFtpFileFind](../../mfc/reference/cftpfilefind-class.md).

## <a name="cinternetsessiongetgopherconnection"></a><a name="getgopherconnection"></a>CInternetSession::GetGopherConnection

Rufen Sie diese Memberfunktion auf, um eine neue `CGopherConnection` Gopher-Verbindung herzustellen und einen Zeiger auf ein Objekt zu erhalten.

```cpp
CGopherConnection* GetGopherConnection(
    LPCTSTR pstrServer,
    LPCTSTR pstrUserName = NULL,
    LPCTSTR pstrPassword = NULL,
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER);
```

### <a name="parameters"></a>Parameter

*pstrServer*<br/>
Ein Zeiger auf eine Zeichenfolge, die den Gopher-Servernamen enthält.

*pstrUserName*<br/>
Ein Zeiger auf eine Zeichenfolge, die den Benutzernamen enthält.

*pstrPassword*<br/>
Ein Zeiger auf eine Zeichenfolge, die das Zugriffskennwort enthält.

*nPort*<br/>
Eine Zahl, die den TCP/IP-Port identifiziert, der auf dem Server verwendet werden soll.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf ein [CGopherConnection-Objekt.](../../mfc/reference/cgopherconnection-class.md) Wenn der Aufruf fehlschlägt, ermitteln Sie die Ursache des Fehlers, indem Sie das ausgelöste [CInternetException-Objekt](../../mfc/reference/cinternetexception-class.md) untersuchen.

### <a name="remarks"></a>Bemerkungen

`GetGopherConnection`stellt eine Verbindung zu einem Gopher-Server her `CGopherConnection` und erstellt und gibt einen Zeiger auf ein Objekt zurück. Es führt keinen bestimmten Vorgang auf dem Server aus. Wenn Sie z. B. Daten lesen oder schreiben möchten, müssen Sie diese Vorgänge in separaten Schritten ausführen. Informationen zum Suchen nach Dateien, Öffnen von Dateien und Lesen oder Schreiben in Dateien finden Sie in den Klassen [CGopherConnection](../../mfc/reference/cgopherconnection-class.md), [CGopherFile](../../mfc/reference/cgopherfile-class.md)und [CGopherFileFind.](../../mfc/reference/cgopherfilefind-class.md) Informationen zum Durchsuchen einer FTP-Site finden Sie in der Memberfunktion [OpenURL](#openurl). Im Artikel [Internetprogrammierung mit WinInet](../../mfc/win32-internet-extensions-wininet.md) finden Sie Schritte zum Ausführen allgemeiner Gopher-Verbindungsaufgaben.

## <a name="cinternetsessiongethttpconnection"></a><a name="gethttpconnection"></a>CInternetSession::GetHttpConnection

Rufen Sie diese Memberfunktion auf, um eine `CHttpConnection` HTTP-Verbindung herzustellen und einen Zeiger auf ein Objekt abzurufen.

```cpp
CHttpConnection* GetHttpConnection(
    LPCTSTR pstrServer,
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER,
    LPCTSTR pstrUserName = NULL,
    LPCTSTR pstrPassword = NULL);

CHttpConnection* GetHttpConnection(
    LPCTSTR pstrServer,
    DWORD dwFlags,
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER,
    LPCTSTR pstrUserName = NULL,
    LPCTSTR pstrPassword = NULL);
```

### <a name="parameters"></a>Parameter

*pstrServer*<br/>
Ein Zeiger auf eine Zeichenfolge, die den HTTP-Servernamen enthält.

*nPort*<br/>
Eine Zahl, die den TCP/IP-Port identifiziert, der auf dem Server verwendet werden soll.

*pstrUserName*<br/>
Ein Zeiger auf eine Zeichenfolge, die den Benutzernamen enthält.

*pstrPassword*<br/>
Ein Zeiger auf eine Zeichenfolge, die das Zugriffskennwort enthält.

*Dwflags*<br/>
Jede Kombination `INTERNET_FLAG_*` der Flags. Eine Beschreibung der *dwFlags-Werte* finden Sie in der Tabelle im Abschnitt **"Hinweise"** von [CHttpConnection::OpenRequest.](../../mfc/reference/chttpconnection-class.md#openrequest)

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf ein [CHttpConnection-Objekt.](../../mfc/reference/chttpconnection-class.md) Wenn der Aufruf fehlschlägt, ermitteln Sie die Ursache des Fehlers, indem Sie das ausgelöste [CInternetException-Objekt](../../mfc/reference/cinternetexception-class.md) untersuchen.

### <a name="remarks"></a>Bemerkungen

`GetHttpConnection`stellt eine Verbindung zu einem HTTP-Server her `CHttpConnection` und erstellt und gibt einen Zeiger auf ein Objekt zurück. Es führt keinen bestimmten Vorgang auf dem Server aus. Wenn Sie z. B. einen HTTP-Header abfragen möchten, müssen Sie diesen Vorgang als separaten Schritt ausführen. Informationen zu Vorgängen, die Sie mithilfe einer Verbindung zu einem HTTP-Server ausführen können, finden Sie in den Klassen [CHttpConnection](../../mfc/reference/chttpconnection-class.md) und [CHttpFile.](../../mfc/reference/chttpfile-class.md) Informationen zum Durchsuchen einer HTTP-Website finden Sie in der Memberfunktion [OpenURL](#openurl). Im Artikel [Internetprogrammierung mit WinInet](../../mfc/win32-internet-extensions-wininet.md) finden Sie Schritte zum Ausführen allgemeiner HTTP-Verbindungsaufgaben.

## <a name="cinternetsessiononstatuscallback"></a><a name="onstatuscallback"></a>CInternetSession::OnStatusCallback

Diese Memberfunktion wird vom Framework aufgerufen, um den Status zu aktualisieren, wenn der Statusrückruf aktiviert ist und ein Vorgang aussteht.

```cpp
virtual void OnStatusCallback(
    DWORD_PTR dwContext,
    DWORD dwInternetStatus,
    LPVOID lpvStatusInformation,
    DWORD dwStatusInformationLength);
```

### <a name="parameters"></a>Parameter

*dwContext*<br/>
Der von der Anwendung bereitgestellte Kontextwert.

*dwInternetStatus*<br/>
Ein Statuscode, der angibt, warum der Rückruf erfolgt. Siehe **Hinweise** für eine Tabelle mit möglichen Werten.

*lpvStatusInformationen*<br/>
Ein Zeiger auf einen Puffer, der Informationen enthält, die für diesen Rückruf relevant sind.

*dwStatusInformationLength*<br/>
Die Größe von *lpvStatusInformation*.

### <a name="remarks"></a>Bemerkungen

Sie müssen [enableStatusCallback](#enablestatuscallback) zuerst aufrufen, um den Statusrückruf nutzen zu können.

Der Parameter *dwInternetStatus* gibt den ausgeführten Vorgang an und bestimmt den Inhalt von *lpvStatusInformation.* *dwStatusInformationLength* gibt die Länge der in *lpvStatusInformation*enthaltenen Daten an. Die folgenden Statuswerte für *dwInternetStatus* sind wie folgt definiert:

|Wert|Bedeutung|
|-----------|-------------|
|INTERNET_STATUS_RESOLVING_NAME|Nachsehen der IP-Adresse des in *lpvStatusInformation*enthaltenen Namens .|
|INTERNET_STATUS_NAME_RESOLVED|Die IP-Adresse des in *lpvStatusInformation*enthaltenen Namens wurde erfolgreich gefunden.|
|INTERNET_STATUS_CONNECTING_TO_SERVER|Herstellen einer Verbindung mit der Socketadresse ([SOCKADDR](/windows/win32/winsock/sockaddr-2)), auf die von *lpvStatusInformation*verwiesen wird.|
|INTERNET_STATUS_CONNECTED_TO_SERVER|Erfolgreich mit der Socketadresse (SOCKADDR) verbunden, auf die von *lpvStatusInformation*verwiesen wird.|
|INTERNET_STATUS_SENDING_REQUEST|Senden der Informationsanforderung an den Server. Der Parameter *lpvStatusInformation* ist NULL.|
|INTERNET_STATUS_ REQUEST_SENT|Die Informationsanforderung wurde erfolgreich an den Server gesendet. Der Parameter *lpvStatusInformation* ist NULL.|
|INTERNET_STATUS_RECEIVING_RESPONSE|Warten, bis der Server auf eine Anforderung reagiert. Der Parameter *lpvStatusInformation* ist NULL.|
|INTERNET_STATUS_RESPONSE_RECEIVED|Erfolgreich eine Antwort vom Server erhalten. Der Parameter *lpvStatusInformation* ist NULL.|
|INTERNET_STATUS_CLOSING_CONNECTION|Schließen der Verbindung zum Server. Der Parameter *lpvStatusInformation* ist NULL.|
|INTERNET_STATUS_CONNECTION_CLOSED|Die Verbindung zum Server wurde erfolgreich geschlossen. Der Parameter *lpvStatusInformation* ist NULL.|
|INTERNET_STATUS_HANDLE_CREATED|Wird von der Win32-API-Funktion [InternetConnect](/windows/win32/api/wininet/nf-wininet-internetconnectw) verwendet, um anzugeben, dass das neue Handle erstellt wurde. Dadurch kann die Anwendung die Win32-Funktion [InternetCloseHandle](/windows/win32/api/wininet/nf-wininet-internetclosehandle) von einem anderen Thread aufrufen, wenn die Verbindung zu lange dauert. Weitere Informationen zu diesen Funktionen finden Sie unter Windows SDK.|
|INTERNET_STATUS_HANDLE_CLOSING|Dieser Handlewert wurde erfolgreich beendet.|

Überschreiben Sie diese Memberfunktion, um eine Aktion zu erfordern, bevor eine Statusrückrufroutine ausgeführt wird.

> [!NOTE]
> Statusrückrufe benötigen Threadstatusschutz. Wenn Sie MFC in einer freigegebenen Bibliothek verwenden, fügen Sie die folgende Zeile am Anfang der Außerkraftsetzung hinzu:

[!code-cpp[NVC_MFCHtmlHttp#8](../../mfc/reference/codesnippet/cpp/cinternetsession-class_1.cpp)]

Weitere Informationen zu asynchronen Vorgängen finden Sie im Artikel [Internet First Steps: WinInet](../../mfc/wininet-basics.md).

## <a name="cinternetsessionopenurl"></a><a name="openurl"></a>CInternetSession::OpenURL

Rufen Sie diese Memberfunktion auf, um die angegebene Anforderung an den HTTP-Server zu senden und dem Client zu ermöglichen, zusätzliche RFC822-, MIME- oder HTTP-Header anzugeben, die zusammen mit der Anforderung gesendet werden sollen.

```cpp
CStdioFile* OpenURL(
    LPCTSTR pstrURL,
    DWORD_PTR dwContext = 1,
    DWORD dwFlags = INTERNET_FLAG_TRANSFER_ASCII,
    LPCTSTR pstrHeaders = NULL,
    DWORD dwHeadersLength = 0);
```

### <a name="parameters"></a>Parameter

*pstrURL*<br/>
Ein Zeiger auf den Namen der URL, die mit dem Lesen beginnen soll. Es werden nur URLs unterstützt, die mit file:, ftp:, gopher:oder http: beginnen. Bestätigt, ob *pstrURL* NULL ist.

*dwContext*<br/>
Ein anwendungsdefinierter Wert, der mit dem zurückgegebenen Handle im Rückruf übergeben wird.

*dwFlags*<br/>
Die Flags, die beschreiben, wie diese Verbindung behandelt wird. Weitere Informationen zu den gültigen Flags finden Sie unter **Hinweise.** Die gültigen Flags sind:

- INTERNET_FLAG_TRANSFER_ASCII Der Standardwert. Übertragen Sie die Datei als ASCII-Text.

- INTERNET_FLAG_TRANSFER_BINARY Übertragen Sie die Datei als Binärdatei.

- INTERNET_FLAG_RELOAD Abrufen der Daten aus dem Draht, auch wenn sie lokal zwischengespeichert sind.

- INTERNET_FLAG_DONT_CACHE Die Daten nicht lokal oder in Gateways zwischenspeichern.

- INTERNET_FLAG_SECURE Dieses Flag gilt nur für HTTP-Anforderungen. Es fordert sichere Transaktionen auf dem Draht mit Secure Sockets Layer oder PCT.

- INTERNET_OPEN_FLAG_USE_EXISTING_CONNECT Wenn möglich, verwenden Sie die vorhandenen Verbindungen `OpenUrl` zum Server für neue Anforderungen, die von generiert werden, anstatt eine neue Sitzung für jede Verbindungsanforderung zu erstellen.

- INTERNET_FLAG_PASSIVE Wird für eine FTP-Site verwendet. Verwendet passive FTP-Semantik. Wird mit [CInternetConnection](../../mfc/reference/cinternetconnection-class.md) von `OpenURL`verwendet.

*pstrHeaders*<br/>
Ein Zeiger auf eine Zeichenfolge, die die Header enthält, die an den HTTP-Server gesendet werden sollen.

*dwHeadersLength*<br/>
Die Länge der zusätzlichen Header in Zeichen. Wenn dies -1L ist und *pstrHeaders* nicht NULL ist, wird angenommen, dass *pstrHeaders* Null beendet ist und die Länge berechnet wird.

### <a name="return-value"></a>Rückgabewert

Gibt ein Dateihandle nur für FTP-, GOPHER-, HTTP- und FILE-Typ-Internetdienste zurück. Gibt NULL zurück, wenn die Analyse fehlgeschlagen ist.

Der zurückgegebene `OpenURL` Zeiger hängt vom Diensttyp von *pstrURL*ab. Die folgende Tabelle zeigt, wie `OpenURL` die möglichen Zeiger zurückgegeben werden können.

|URL-Typ|Rückgabe|
|--------------|-------------|
|`file://`|`CStdioFile*`|
|`http://`|`CHttpFile*`|
|`gopher://`|`CGopherFile*`|
|`ftp://`|`CInternetFile*`|

### <a name="remarks"></a>Bemerkungen

Der Parameter *dwFlags* muss entweder INTERNET_FLAG_TRANSFER_ASCII oder INTERNET_FLAG_TRANSFER_BINARY enthalten, jedoch nicht beides. Die verbleibenden Flags können mit dem bitweisen **ODER-Operator** ( **&#124;) **kombiniert werden.

`OpenURL`, das die Win32-Funktion `InternetOpenURL`umschließt, erlaubt nur das Herunterladen, Abrufen und Lesen der Daten von einem Internetserver. `OpenURL`ermöglicht keine Dateimanipulation an einem Remotespeicherort, daher ist kein [CInternetConnection-Objekt](../../mfc/reference/cinternetconnection-class.md) erforderlich.

Um verbindungsspezifische (d. h. protokollspezifische) Funktionen wie das Schreiben in eine Datei zu verwenden, müssen Sie eine Sitzung öffnen und dann eine bestimmte Art von Verbindung öffnen und dann diese Verbindung verwenden, um eine Datei im gewünschten Modus zu öffnen. Weitere `CInternetConnection` Informationen zu verbindungsspezifischen Funktionen finden Sie unter .

## <a name="cinternetsessionoperator-hinternet"></a><a name="operator_hinternet"></a>CInternetSession::operator HINTERNET

Verwenden Sie diesen Operator, um das Windows-Handle für die aktuelle Internetsitzung abzubekommen.

```cpp
operator HINTERNET() const;
```

## <a name="cinternetsessionsetcookie"></a><a name="setcookie"></a>CInternetSession::SetCookie

Legt ein Cookie für die angegebene URL fest.

```cpp
static BOOL SetCookie(
    LPCTSTR pstrUrl,
    LPCTSTR pstrCookieName,
    LPCTSTR pstrCookieData);
```

### <a name="parameters"></a>Parameter

*pstrUrl*<br/>
Ein Zeiger auf eine null-terminierte Zeichenfolge, die die URL angibt, für die das Cookie festgelegt werden soll.

*pstrCookieName*<br/>
Ein Zeiger auf eine Zeichenfolge, die den Namen des Cookies enthält.

*pstrCookieData*<br/>
Ein Zeiger auf eine Zeichenfolge, die die tatsächlichen Zeichenfolgendaten enthält, die der URL zugeordnet werden sollen.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE zurück, wenn erfolgreich, oder FALSE andernfalls. Um den spezifischen Fehlercode zu erhalten, rufen Sie`GetLastError.`

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion implementiert das Verhalten der Win32-Nachricht [InternetSetCookie](/windows/win32/api/wininet/nf-wininet-internetsetcookiew), wie im Windows SDK beschrieben.

## <a name="cinternetsessionsetoption"></a><a name="setoption"></a>CInternetSession::SetOption

Rufen Sie diese Memberfunktion auf, um Optionen für die Internetsitzung festzulegen.

```cpp
BOOL SetOption(
    DWORD dwOption,
    LPVOID lpBuffer,
    DWORD dwBufferLength,
    DWORD dwFlags = 0);

BOOL SetOption(
    DWORD dwOption,
    DWORD dwValue,
    DWORD dwFlags = 0);
```

### <a name="parameters"></a>Parameter

*dwOption*<br/>
Die festzulegende Internetoption. Eine Liste der möglichen Optionen finden Sie unter [Optionsflags](/windows/win32/WinInet/option-flags) im Windows SDK.

*lpBuffer*<br/>
Ein Puffer, der die Optionseinstellung enthält.

*dwBufferLength*<br/>
Die Länge von *lpBuffer* oder die Größe von *dwValue*.

*dwValue*<br/>
Ein DWORD, das die Optionseinstellung enthält.

*dwFlags*<br/>
Gibt verschiedene Caching-Optionen an. Der Standardwert ist auf 0 festgelegt. Folgende Werte sind zulässig:

- INTERNET_FLAG_DONT_CACHE Die Daten nicht lokal oder auf Gatewayservern zwischenspeichern.

- INTERNET_FLAG_OFFLINE Downloadvorgänge werden nur über den persistenten Cache erfüllt. Wenn das Element nicht im Cache vorhanden ist, wird ein entsprechender Fehlercode zurückgegeben. Dieses Flag kann mit dem bitweisen **Operator ODER** ( **&#124;**) kombiniert werden.

### <a name="return-value"></a>Rückgabewert

Wenn der Vorgang erfolgreich war, wird der Wert TRUE zurückgegeben. Wenn ein Fehler aufgetreten ist, wird der Wert FALSE zurückgegeben. Wenn der Aufruf fehlschlägt, kann die Win32-Funktion [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) aufgerufen werden, um die Ursache des Fehlers zu ermitteln.

## <a name="see-also"></a>Siehe auch

[CObject-Klasse](../../mfc/reference/cobject-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CInternetConnection-Klasse](../../mfc/reference/cinternetconnection-class.md)<br/>
[CHttpConnection-Klasse](../../mfc/reference/chttpconnection-class.md)<br/>
[CFtpConnection-Klasse](../../mfc/reference/cftpconnection-class.md)<br/>
[CGopherConnection-Klasse](../../mfc/reference/cgopherconnection-class.md)
