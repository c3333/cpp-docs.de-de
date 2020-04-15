---
title: CAsyncSocket-Klasse
ms.date: 09/03/2019
f1_keywords:
- CAsyncSocket
- AFXSOCK/CAsyncSocket
- AFXSOCK/CAsyncSocket::CAsyncSocket
- AFXSOCK/CAsyncSocket::Accept
- AFXSOCK/CAsyncSocket::AsyncSelect
- AFXSOCK/CAsyncSocket::Attach
- AFXSOCK/CAsyncSocket::Bind
- AFXSOCK/CAsyncSocket::Close
- AFXSOCK/CAsyncSocket::Connect
- AFXSOCK/CAsyncSocket::Create
- AFXSOCK/CAsyncSocket::Detach
- AFXSOCK/CAsyncSocket::FromHandle
- AFXSOCK/CAsyncSocket::GetLastError
- AFXSOCK/CAsyncSocket::GetPeerName
- AFXSOCK/CAsyncSocket::GetPeerNameEx
- AFXSOCK/CAsyncSocket::GetSockName
- AFXSOCK/CAsyncSocket::GetSockNameEx
- AFXSOCK/CAsyncSocket::GetSockOpt
- AFXSOCK/CAsyncSocket::IOCtl
- AFXSOCK/CAsyncSocket::Listen
- AFXSOCK/CAsyncSocket::Receive
- AFXSOCK/CAsyncSocket::ReceiveFrom
- AFXSOCK/CAsyncSocket::ReceiveFromEx
- AFXSOCK/CAsyncSocket::Send
- AFXSOCK/CAsyncSocket::SendTo
- AFXSOCK/CAsyncSocket::SendToEx
- AFXSOCK/CAsyncSocket::SetSockOpt
- AFXSOCK/CAsyncSocket::ShutDown
- AFXSOCK/CASyncSocket::Socket
- AFXSOCK/CAsyncSocket::OnAccept
- AFXSOCK/CAsyncSocket::OnClose
- AFXSOCK/CAsyncSocket::OnConnect
- AFXSOCK/CAsyncSocket::OnOutOfBandData
- AFXSOCK/CAsyncSocket::OnReceive
- AFXSOCK/CAsyncSocket::OnSend
- AFXSOCK/CAsyncSocket::m_hSocket
helpviewer_keywords:
- CAsyncSocket [MFC], CAsyncSocket
- CAsyncSocket [MFC], Accept
- CAsyncSocket [MFC], AsyncSelect
- CAsyncSocket [MFC], Attach
- CAsyncSocket [MFC], Bind
- CAsyncSocket [MFC], Close
- CAsyncSocket [MFC], Connect
- CAsyncSocket [MFC], Create
- CAsyncSocket [MFC], Detach
- CAsyncSocket [MFC], FromHandle
- CAsyncSocket [MFC], GetLastError
- CAsyncSocket [MFC], GetPeerName
- CAsyncSocket [MFC], GetPeerNameEx
- CAsyncSocket [MFC], GetSockName
- CAsyncSocket [MFC], GetSockNameEx
- CAsyncSocket [MFC], GetSockOpt
- CAsyncSocket [MFC], IOCtl
- CAsyncSocket [MFC], Listen
- CAsyncSocket [MFC], Receive
- CAsyncSocket [MFC], ReceiveFrom
- CAsyncSocket [MFC], ReceiveFromEx
- CAsyncSocket [MFC], Send
- CAsyncSocket [MFC], SendTo
- CAsyncSocket [MFC], SendToEx
- CAsyncSocket [MFC], SetSockOpt
- CAsyncSocket [MFC], ShutDown
- CASyncSocket [MFC], Socket
- CAsyncSocket [MFC], OnAccept
- CAsyncSocket [MFC], OnClose
- CAsyncSocket [MFC], OnConnect
- CAsyncSocket [MFC], OnOutOfBandData
- CAsyncSocket [MFC], OnReceive
- CAsyncSocket [MFC], OnSend
- CAsyncSocket [MFC], m_hSocket
ms.assetid: cca4d5a1-aa0f-48bd-843e-ef0e2d7fc00b
ms.openlocfilehash: 7ab02dba4bf10b04dddac4e2e954623223af42d9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81353025"
---
# <a name="casyncsocket-class"></a>CAsyncSocket-Klasse

Stellt einen Windows Socket dar – einen Endpunkt der Netzwerkkommunikation.

## <a name="syntax"></a>Syntax

```
class CAsyncSocket : public CObject
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAsyncSocket::CAsyncSocket](#casyncsocket)|Erstellt ein `CAsyncSocket`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAsyncSocket::Akzeptieren](#accept)|Akzeptiert eine Verbindung auf dem Socket.|
|[CAsyncSocket::AsyncSelect](#asyncselect)|Fordert eine Ereignisbenachrichtigung für den Socket an.|
|[CAsyncSocket::Anfügen](#attach)|Fügt ein Sockethandle `CAsyncSocket` an ein Objekt an.|
|[CAsyncSocket::Bind](#bind)|Ordnet dem Socket eine lokale Adresse zu.|
|[CAsyncSocket::Schließen](#close)|Schließt den Socket.|
|[CAsyncSocket::Verbinden](#connect)|Stellt eine Verbindung zu einem Peersocket her.|
|[CAsyncSocket::Create](#create)|Erstellt einen Socket.|
|[CAsyncSocket::Detach](#detach)|Trennt ein Sockethandle von `CAsyncSocket` einem Objekt.|
|[CAsyncSocket::FromHandle](#fromhandle)|Gibt einen Zeiger `CAsyncSocket` auf ein Objekt mit einem Sockethandle zurück.|
|[CAsyncSocket::GetLastError](#getlasterror)|Ruft den Fehlerstatus für den letzten fehlgeschlagenen Vorgang ab.|
|[CAsyncSocket::GetPeerName](#getpeername)|Ruft die Adresse des Peersockets ab, mit dem der Socket verbunden ist.|
|[CAsyncSocket::GetPeerNameEx](#getpeernameex)|Ruft die Adresse des Peersockets ab, mit dem der Socket verbunden ist (behandelt IPv6-Adressen).|
|[CAsyncSocket::GetSockName](#getsockname)|Ruft den lokalen Namen für einen Socket ab.|
|[CAsyncSocket::GetSockNameEx](#getsocknameex)|Ruft den lokalen Namen für einen Socket ab (behandelt IPv6-Adressen).|
|[CAsyncSocket::GetSockOpt](#getsockopt)|Ruft eine Socketoption ab.|
|[CAsyncSocket::IOCtl](#ioctl)|Steuert den Modus des Sockets.|
|[CAsyncSocket::Listen](#listen)|Erstellt einen Socket, um eingehende Verbindungsanforderungen zu verarbeiten.|
|[CAsyncSocket::Empfangen](#receive)|Empfängt Daten vom Socket.|
|[CAsyncSocket::ReceiveVon](#receivefrom)|Empfängt ein Datagramm und speichert die Quelladresse.|
|[CAsyncSocket::ReceiveFromEx](#receivefromex)|Empfängt ein Datagramm und speichert die Quelladresse (behandelt IPv6-Adressen).|
|[CAsyncSocket::Senden](#send)|Sendet Daten an einen verbundenen Socket.|
|[CAsyncSocket::SendTo](#sendto)|Sendet Daten an ein bestimmtes Ziel.|
|[CAsyncSocket::SendToEx](#sendtoex)|Sendet Daten an ein bestimmtes Ziel (behandelt IPv6-Adressen).|
|[CAsyncSocket::SetSockOpt](#setsockopt)|Legt eine Socketoption fest.|
|[CAsyncSocket::ShutDown](#shutdown)|Deaktiviert `Send` und/oder `Receive` ruft den Socket auf.|
|[CASyncSocket::Socket](#socket)|Ordnet ein Sockethandle zu.|

### <a name="protected-methods"></a>Geschützte Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAsyncSocket::OnAccept](#onaccept)|Benachrichtigt einen abhörenden Socket, dass er `Accept`ausstehende Verbindungsanforderungen akzeptieren kann, indem er aufruft.|
|[CAsyncSocket::OnClose](#onclose)|Benachrichtigt einen Socket, dass der mit ihm verbundene Socket geschlossen wurde.|
|[CAsyncSocket::OnConnect](#onconnect)|Benachrichtigt einen Verbindungssocket, dass der Verbindungsversuch abgeschlossen ist, ob erfolgreich oder fehlerhaft.|
|[CAsyncSocket::OnOutOfBandData](#onoutofbanddata)|Benachrichtigt einen empfangenden Socket, dass Out-of-Band-Daten auf dem Socket gelesen werden müssen, in der Regel eine dringende Meldung.|
|[CAsyncSocket::OnReceive](#onreceive)|Benachrichtigt einen Abhörsocket, dass Daten abgerufen `Receive`werden müssen, die durch Aufrufen abgerufen werden sollen.|
|[CAsyncSocket::OnSend](#onsend)|Benachrichtigt einen Socket, dass er Daten `Send`senden kann, indem er aufruft.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAsyncSocket::operator =](#operator_eq)|Weist einem `CAsyncSocket` Objekt einen neuen Wert zu.|
|[CAsyncSocket::operator SOCKET](#operator_socket)|Verwenden Sie diesen Operator, um `CAsyncSocket` das SOCKET-Handle des Objekts abzurufen.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAsyncSocket::m_hSocket](#m_hsocket)|Gibt das SOCKET-Handle `CAsyncSocket` an, das an dieses Objekt angefügt ist.|

## <a name="remarks"></a>Bemerkungen

Die `CAsyncSocket` Klasse kapselt die Windows Socket Functions-API und stellt eine objektorientierte Abstraktion für Programmierer bereit, die Windows Sockets in Verbindung mit MFC verwenden möchten.

Diese Klasse basiert auf der Annahme, dass Sie die Netzwerkkommunikation verstehen. Sie sind für den Umgang mit Blockierungen, Bytereihenfolgeunterschieden und Konvertierungen zwischen Unicode- und MBCS-Zeichenfolgen (Multibyte Character Set) verantwortlich. Wenn Sie eine bequemere Schnittstelle benötigen, die diese Probleme für Sie verwaltet, lesen Sie klasse [CSocket](../../mfc/reference/csocket-class.md).

Um ein `CAsyncSocket` Objekt zu verwenden, rufen Sie seinen Konstruktor auf, `SOCKET`und rufen Sie dann die [Create-Funktion](#create) auf, um das zugrunde liegende Sockethandle (Typ ) mit Ausnahme der akzeptierten Sockets zu erstellen. Rufen Sie für [Listen](#listen) einen Serversocket die Listen-Memberfunktion auf, für einen Clientsocket die Connect-Memberfunktion. [Connect](#connect) Der Serversocket sollte die [Accept-Funktion](#accept) aufrufen, wenn er eine Verbindungsanforderung empfängt. Verwenden Sie `CAsyncSocket` die verbleibenden Funktionen, um die Kommunikation zwischen Sockets durchzuführen. Zerstören Sie das `CAsyncSocket` Objekt nach Abschluss, wenn es auf dem Heap erstellt wurde. der Destruktor ruft automatisch die [Close-Funktion](#close) auf. Der SOCKET-Datentyp wird im Artikel [Windows Sockets: Background](../../mfc/windows-sockets-background.md)beschrieben.

> [!NOTE]
> Wenn Sie MFC-Sockets in sekundären Threads in einer `AfxSocketInit` statisch verknüpften MFC-Anwendung verwenden, müssen Sie in jedem Thread aufrufen, der Sockets verwendet, um die Socketbibliotheken zu initialisieren. Standardmäßig `AfxSocketInit` wird nur im primären Thread aufgerufen.

Weitere Informationen finden Sie unter [Windows Sockets: Verwenden von Klasse CAsyncSocket](../../mfc/windows-sockets-using-class-casyncsocket.md) und verwandten Artikeln sowie [Windows Sockets 2 API](/windows/win32/WinSock/windows-sockets-start-page-2).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

`CAsyncSocket`

## <a name="requirements"></a>Anforderungen

**Kopf:** afxsock.h

## <a name="casyncsocketaccept"></a><a name="accept"></a>CAsyncSocket::Akzeptieren

Rufen Sie diese Memberfunktion auf, um eine Verbindung auf einem Socket zu akzeptieren.

```
virtual BOOL Accept(
    CAsyncSocket& rConnectedSocket,
    SOCKADDR* lpSockAddr = NULL,
    int* lpSockAddrLen = NULL);
```

### <a name="parameters"></a>Parameter

*rConnectedSocket*<br/>
Eine Referenz, die einen neuen Socket identifiziert, der für die Verbindung verfügbar ist.

*lpSockAddr*<br/>
Ein Zeiger auf eine [SOCKADDR-Struktur,](/windows/win32/winsock/sockaddr-2) die die Adresse des Verbindungssockets empfängt, wie im Netzwerk bekannt. Das genaue Format des *arguments lpSockAddr* wird durch die Adressfamilie bestimmt, die beim Erstellen des Sockets festgelegt wurde. Wenn *lpSockAddr* und/oder *lpSockAddrLen* gleich NULL sind, werden keine Informationen über die Remoteadresse des akzeptierten Sockets zurückgegeben.

*lpSockAddrLen*<br/>
Ein Zeiger auf die Länge der Adresse in *lpSockAddr* in Bytes. Der *lpSockAddrLen* ist ein Wert-Ergebnis-Parameter: Er sollte zunächst die Menge an Speicherplatz enthalten, auf die *lpSockAddr*zeigt; bei der Rückgabe enthält es die tatsächliche Länge (in Bytes) der zurückgegebenen Adresse.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Funktion erfolgreich ist; Andernfalls 0, und ein bestimmter Fehlercode kann abgerufen werden, indem [GetLastError](#getlasterror)aufgerufen wird. Die folgenden Fehler gelten für diese Memberfunktion:

- WSANOTINITIALISED Ein erfolgreicher [AfxSocketSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) muss auftreten, bevor diese API verwendet werden kann.

- WSAENETDOWN Die Windows Sockets-Implementierung hat festgestellt, dass das Netzwerksubsystem ausgefallen ist.

- WSAEFAULT Das Argument *lpSockAddrLen* ist zu klein (kleiner als die Größe einer [SOCKADDR-Struktur).](/windows/win32/winsock/sockaddr-2)

- WSAEINPROGRESS Ein blockierender Windows Sockets-Aufruf wird ausgeführt.

- WSAEINVAL `Listen` wurde vor der Annahme nicht aufgerufen.

- WSAEMFILE Die Warteschlange ist beim Zuspruch leer, und es sind keine Deskriptoren verfügbar.

- WSAENOBUFS Kein Pufferspeicher verfügbar.

- WSAENOTSOCK Der Deskriptor ist kein Socket.

- WSAEOPNOTSUPP Der referenzierte Socket ist kein Typ, der verbindungsorientierten Dienst unterstützt.

- WSAEWOULDBLOCK Der Socket ist als nicht blockierend markiert, und es sind keine Verbindungen vorhanden, die akzeptiert werden sollen.

### <a name="remarks"></a>Bemerkungen

Diese Routine extrahiert die erste Verbindung in der Warteschlange ausstehender Verbindungen, erstellt einen neuen Socket mit den gleichen Eigenschaften wie dieser Socket und fügt ihn an *rConnectedSocket*an. Wenn keine ausstehenden Verbindungen in `Accept` der `GetLastError` Warteschlange vorhanden sind, gibt Null zurück und gibt einen Fehler zurück. Der akzeptierte Socket ( *rConnectedSocket)* kann nicht verwendet werden, um mehr Verbindungen zu akzeptieren. Der ursprüngliche Sockel bleibt offen und hört zu.

Das Argument *lpSockAddr* ist ein Ergebnisparameter, der mit der Adresse des Verbindungssockets gefüllt wird, wie er der Kommunikationsschicht bekannt ist. `Accept`wird mit verbindungsbasierten Sockettypen wie SOCK_STREAM verwendet.

## <a name="casyncsocketasyncselect"></a><a name="asyncselect"></a>CAsyncSocket::AsyncSelect

Rufen Sie diese Memberfunktion auf, um eine Ereignisbenachrichtigung für einen Socket anzufordern.

```
BOOL AsyncSelect(long lEvent = FD_READ | FD_WRITE | FD_OOB | FD_ACCEPT | FD_CONNECT | FD_CLOSE);
```

### <a name="parameters"></a>Parameter

*lEvent*<br/>
Eine Bitmaske, die eine Kombination von Netzwerkereignissen angibt, an denen die Anwendung interessiert ist.

- FD_READ möchten eine Benachrichtigung über die Lesebereitschaft erhalten.

- FD_WRITE möchten Benachrichtigungen erhalten, wenn Daten zum Lesen verfügbar sind.

- FD_OOB möchten eine Benachrichtigung über das Eintreffen von Out-of-Band-Daten erhalten.

- FD_ACCEPT möchten Benachrichtigungen über eingehende Verbindungen erhalten.

- FD_CONNECT möchten Benachrichtigungen über Verbindungsergebnisse erhalten.

- FD_CLOSE möchten eine Benachrichtigung erhalten, wenn ein Socket von einem Peer geschlossen wurde.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Funktion erfolgreich ist; Andernfalls 0, und ein bestimmter Fehlercode kann abgerufen werden, indem [GetLastError](#getlasterror)aufgerufen wird. Die folgenden Fehler gelten für diese Memberfunktion:

- WSANOTINITIALISED Ein erfolgreicher [AfxSocketSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) muss auftreten, bevor diese API verwendet werden kann.

- WSAENETDOWN Die Windows Sockets-Implementierung hat festgestellt, dass das Netzwerksubsystem ausgefallen ist.

- WSAEINVAL Gibt an, dass einer der angegebenen Parameter ungültig war.

- WSAEINPROGRESS Ein blockierender Windows Sockets-Vorgang wird ausgeführt.

### <a name="remarks"></a>Bemerkungen

Diese Funktion wird verwendet, um anzugeben, welche MFC-Rückrufbenachrichtigungsfunktionen für den Socket aufgerufen werden. `AsyncSelect`setzt diesen Socket automatisch in den nicht blockierenden Modus. Weitere Informationen finden Sie im Artikel [Windows Sockets: Socket Notifications](../../mfc/windows-sockets-socket-notifications.md).

## <a name="casyncsocketattach"></a><a name="attach"></a>CAsyncSocket::Anfügen

Rufen Sie diese Memberfunktion auf, `CAsyncSocket` um das *hSocket-Handle* an ein Objekt anzuhängen.

```
BOOL Attach(
    SOCKET hSocket, long lEvent = FD_READ | FD_WRITE | FD_OOB | FD_ACCEPT | FD_CONNECT | FD_CLOSE);
```

### <a name="parameters"></a>Parameter

*hSocket*<br/>
Enthält ein Handle für einen Socket.

*lEvent*<br/>
Eine Bitmaske, die eine Kombination von Netzwerkereignissen angibt, an denen die Anwendung interessiert ist.

- FD_READ möchten eine Benachrichtigung über die Lesebereitschaft erhalten.

- FD_WRITE möchten Benachrichtigungen erhalten, wenn Daten zum Lesen verfügbar sind.

- FD_OOB möchten eine Benachrichtigung über das Eintreffen von Out-of-Band-Daten erhalten.

- FD_ACCEPT möchten Benachrichtigungen über eingehende Verbindungen erhalten.

- FD_CONNECT möchten Benachrichtigungen über Verbindungsergebnisse erhalten.

- FD_CLOSE möchten eine Benachrichtigung erhalten, wenn ein Socket von einem Peer geschlossen wurde.

### <a name="return-value"></a>Rückgabewert

Ungleich null, wenn die Funktion erfolgreich ist.

### <a name="remarks"></a>Bemerkungen

Das SOCKET-Handle wird im [m_hSocket-Datenmember](#m_hsocket) des Objekts gespeichert.

## <a name="casyncsocketbind"></a><a name="bind"></a>CAsyncSocket::Bind

Rufen Sie diese Memberfunktion auf, um dem Socket eine lokale Adresse zuzuordnen.

```
BOOL Bind(
    UINT nSocketPort,
    LPCTSTR lpszSocketAddress = NULL);

BOOL Bind (
    const SOCKADDR* lpSockAddr,
    int nSockAddrLen);
```

### <a name="parameters"></a>Parameter

*nSocketPort*<br/>
Der Port, der die Socketanwendung identifiziert.

*lpszSocketAddress*<br/>
Die Netzwerkadresse, eine gepunktete Zahl wie "128.56.22.8". Das Übergeben der NULL-Zeichenfolge `CAsyncSocket` für diesen Parameter gibt an, dass die Instanz auf Clientaktivitäten auf allen Netzwerkschnittstellen lauschen soll.

*lpSockAddr*<br/>
Ein Zeiger auf eine [SOCKADDR-Struktur,](/windows/win32/winsock/sockaddr-2) die die Adresse enthält, die diesem Socket zugewiesen werden soll.

*nSockAddrLen*<br/>
Die Länge der Adresse in *lpSockAddr* in Bytes.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Funktion erfolgreich ist; Andernfalls 0, und ein bestimmter Fehlercode kann abgerufen werden, indem [GetLastError](#getlasterror)aufgerufen wird. Die folgende Liste enthält einige der Fehler, die möglicherweise zurückgegeben werden. Eine vollständige Liste finden Sie unter [Windows Sockets Error Codes](/windows/win32/winsock/windows-sockets-error-codes-2).

- WSANOTINITIALISED Ein erfolgreicher [AfxSocketSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) muss auftreten, bevor diese API verwendet werden kann.

- WSAENETDOWN Die Windows Sockets-Implementierung hat festgestellt, dass das Netzwerksubsystem ausgefallen ist.

- WSAEADDRINUSE Die angegebene Adresse wird bereits verwendet. (Siehe die SO_REUSEADDR Socket-Option unter [SetSockOpt](#setsockopt).)

- WSAEFAULT Das Argument *nSockAddrLen* ist zu klein (kleiner als die Größe einer [SOCKADDR-Struktur).](/windows/win32/winsock/sockaddr-2)

- WSAEINPROGRESS Ein blockierender Windows Sockets-Aufruf wird ausgeführt.

- WSAEAFNOSUPPORT Die angegebene Adressfamilie wird von diesem Port nicht unterstützt.

- WSAEINVAL Der Socket ist bereits an eine Adresse gebunden.

- WSAENOBUFS Nicht genügend Puffer verfügbar, zu viele Verbindungen.

- WSAENOTSOCK Der Deskriptor ist kein Socket.

### <a name="remarks"></a>Bemerkungen

Diese Routine wird vor nachfolgenden `Connect` oder `Listen` Aufrufen in einem nicht verbundenen Datagramm oder Streamsocket verwendet. Bevor Verbindungsanforderungen akzeptiert werden können, muss ein Abhörenvonserversocket eine Portnummer `Bind`auswählen und Windows Sockets durch Aufrufen davon bekannt machen. `Bind`richtet die lokale Zuordnung (Hostadresse/Portnummer) des Sockets ein, indem einem unbenannten Socket ein lokaler Name zugewiesen wird.

## <a name="casyncsocketcasyncsocket"></a><a name="casyncsocket"></a>CAsyncSocket::CAsyncSocket

Erstellt ein leeres Socketobjekt.

```
CAsyncSocket();
```

### <a name="remarks"></a>Bemerkungen

Nach dem Erstellen des Objekts müssen Sie seine `Create` Memberfunktion aufrufen, um die SOCKET-Datenstruktur zu erstellen und seine Adresse zu binden. (Auf der Serverseite einer Windows Sockets-Kommunikation rufen Sie diesen `Accept` Socket nicht `Create` an, wenn der Abhörsocket einen Socket erstellt, der für den Anruf verwendet werden soll.)

## <a name="casyncsocketclose"></a><a name="close"></a>CAsyncSocket::Schließen

Schließt den Socket.

```
virtual void Close();
```

### <a name="remarks"></a>Bemerkungen

Diese Funktion gibt den Socketdeskriptor frei, sodass weitere Verweise darauf mit dem Fehler WSAENOTSOCK fehlschlagen. Wenn dies der letzte Verweis auf den zugrunde liegenden Socket ist, werden die zugehörigen Namensinformationen und Daten in der Warteschlange verworfen. Der Destruktor des `Close` Socketobjekts ruft Sie auf.

Für `CAsyncSocket`, aber `CSocket`nicht für , `Close` wird die Semantik von von den Socketoptionen SO_LINGER und SO_DONTLINGER beeinflusst. Weitere Informationen finden Sie `GetSockOpt`unter Memberfunktion .

## <a name="casyncsocketconnect"></a><a name="connect"></a>CAsyncSocket::Verbinden

Rufen Sie diese Memberfunktion auf, um eine Verbindung zu einem nicht verbundenen Stream oder Datagrammsocket herzustellen.

```
BOOL Connect(
    LPCTSTR lpszHostAddress,
    UINT nHostPort);

BOOL Connect(
    const SOCKADDR* lpSockAddr,
    int nSockAddrLen);
```

### <a name="parameters"></a>Parameter

*lpszHostAddress*<br/>
Die Netzwerkadresse des Sockets, mit dem dieses Objekt verbunden ist: ein Maschinenname wie "ftp.microsoft.com" oder eine gepunktete Zahl wie "128.56.22.8".

*nHostPort*<br/>
Der Port, der die Socketanwendung identifiziert.

*lpSockAddr*<br/>
Ein Zeiger auf eine [SOCKADDR-Struktur,](/windows/win32/winsock/sockaddr-2) die die Adresse des verbundenen Sockets enthält.

*nSockAddrLen*<br/>
Die Länge der Adresse in *lpSockAddr* in Bytes.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Funktion erfolgreich ist; Andernfalls 0, und ein bestimmter Fehlercode kann abgerufen werden, indem [GetLastError](#getlasterror)aufgerufen wird. Wenn dies auf einen Fehlercode von WSAEWOULDBLOCK hinweist und Ihre Anwendung die `OnConnect` überschreibbaren Rückrufe verwendet, erhält Ihre Anwendung eine Meldung, wenn der Verbindungsvorgang abgeschlossen ist. Die folgenden Fehler gelten für diese Memberfunktion:

- WSANOTINITIALISED Ein erfolgreicher [AfxSocketSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) muss auftreten, bevor diese API verwendet werden kann.

- WSAENETDOWN Die Windows Sockets-Implementierung hat festgestellt, dass das Netzwerksubsystem ausgefallen ist.

- WSAEADDRINUSE Die angegebene Adresse wird bereits verwendet.

- WSAEINPROGRESS Ein blockierender Windows Sockets-Aufruf wird ausgeführt.

- WSAEADDRNOTAVAIL Die angegebene Adresse ist vom lokalen Computer nicht verfügbar.

- WSAEAFNOSUPPORT-Adressen in der angegebenen Familie können nicht mit diesem Socket verwendet werden.

- WSAECONNREFUSED Der Verbindungsversuch wurde abgelehnt.

- WSAEDESTADDRREQ Eine Zieladresse ist erforderlich.

- WSAEFAULT Das Argument *nSockAddrLen* ist falsch.

- WSAEINVAL Ungültige Hostadresse.

- WSAEISCONN Der Socket ist bereits angeschlossen.

- WSAEMFILE Es sind keine weiteren Dateideskriptoren verfügbar.

- WSAENETUNREACH Das Netzwerk kann derzeit nicht von diesem Host aus erreicht werden.

- WSAENOBUFS Kein Pufferspeicher verfügbar. Der Socket kann nicht angeschlossen werden.

- WSAENOTSOCK Der Deskriptor ist kein Socket.

- WSAETIMEDOUT Versuch, eine Verbindung herzustellen, ohne eine Verbindung herzustellen.

- WSAEWOULDBLOCK Der Socket ist als nicht blockierend markiert und die Verbindung kann nicht sofort abgeschlossen werden.

### <a name="remarks"></a>Bemerkungen

Wenn der Socket ungebunden ist, werden der lokalen Zuordnung vom System eindeutige Werte zugewiesen, und der Socket wird als gebunden markiert. Beachten Sie, dass, wenn das Adressfeld `Connect` der Namensstruktur alle Nullen ist, Null zurückgegeben wird. Um erweiterte Fehlerinformationen zu `GetLastError` erhalten, rufen Sie die Memberfunktion auf.

Bei Streamsockets (Typ SOCK_STREAM) wird eine aktive Verbindung zum fremden Host initiiert. Wenn der Socketaufruf erfolgreich abgeschlossen wird, kann der Socket Daten senden/empfangen.

Für einen Datagrammsocket (Typ SOCK_DGRAM) wird ein Standardziel `Send` festgelegt, das bei nachfolgenden Aufrufen und `Receive` Aufrufen verwendet wird.

## <a name="casyncsocketcreate"></a><a name="create"></a>CAsyncSocket::Erstellen

Rufen `Create` Sie die Memberfunktion auf, nachdem Sie ein Socketobjekt erstellt haben, um den Windows-Socket zu erstellen und anzuhängen.

```
BOOL Create(
    UINT nSocketPort = 0,
    int nSocketType = SOCK_STREAM,
    long lEvent = FD_READ | FD_WRITE | FD_OOB | FD_ACCEPT | FD_CONNECT | FD_CLOSE,
    LPCTSTR lpszSocketAddress = NULL);
```

### <a name="parameters"></a>Parameter

*nSocketPort*<br/>
Ein bekannter Port, der mit dem Socket verwendet werden soll, oder 0, wenn Windows Sockets einen Port auswählen soll.

*nSocketType*<br/>
SOCK_STREAM oder SOCK_DGRAM.

*lEvent*<br/>
Eine Bitmaske, die eine Kombination von Netzwerkereignissen angibt, an denen die Anwendung interessiert ist.

- FD_READ möchten eine Benachrichtigung über die Lesebereitschaft erhalten.

- FD_WRITE möchten eine Benachrichtigung über die Schreibbereitschaft erhalten.

- FD_OOB möchten eine Benachrichtigung über das Eintreffen von Out-of-Band-Daten erhalten.

- FD_ACCEPT möchten Benachrichtigungen über eingehende Verbindungen erhalten.

- FD_CONNECT möchten eine Benachrichtigung über die abgeschlossene Verbindung erhalten.

- FD_CLOSE möchten eine Benachrichtigung über den Socket-Verschluss erhalten.

*lpszSockAddress*<br/>
Ein Zeiger auf eine Zeichenfolge, die die Netzwerkadresse des verbundenen Sockets enthält, eine gepunktete Zahl wie "128.56.22.8". Das Übergeben der NULL-Zeichenfolge `CAsyncSocket` für diesen Parameter gibt an, dass die Instanz auf Clientaktivitäten auf allen Netzwerkschnittstellen lauschen soll.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Funktion erfolgreich ist; Andernfalls 0, und ein bestimmter Fehlercode kann abgerufen werden, indem [GetLastError](#getlasterror)aufgerufen wird. Die folgenden Fehler gelten für diese Memberfunktion:

- WSANOTINITIALISED Ein erfolgreicher [AfxSocketSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) muss auftreten, bevor diese API verwendet werden kann.

- WSAENETDOWN Die Windows Sockets-Implementierung hat festgestellt, dass das Netzwerksubsystem ausgefallen ist.

- WSAEAFNOSUPPORT Die angegebene Adressfamilie wird nicht unterstützt.

- WSAEINPROGRESS Ein blockierender Windows Sockets-Vorgang wird ausgeführt.

- WSAEMFILE Es sind keine weiteren Dateideskriptoren verfügbar.

- WSAENOBUFS Kein Pufferspeicher verfügbar. Der Socket kann nicht erstellt werden.

- WSAEPROTONOSUPPORT Der angegebene Port wird nicht unterstützt.

- WSAEPROTOTYPE Der angegebene Port ist der falsche Typ für diesen Socket.

- WSAESOCKTNOSUPPORT Der angegebene Sockettyp wird in dieser Adressfamilie nicht unterstützt.

### <a name="remarks"></a>Bemerkungen

`Create`ruft [Socket](#socket) auf, und wenn erfolgreich, ruft es [Bind](#bind) auf, um den Socket an die angegebene Adresse zu binden. Die folgenden Sockettypen werden unterstützt:

- SOCK_STREAM Bietet sequenzierte, zuverlässige, vollduplex- verbindungsbasierte Byte-Streams. Verwendet das Tcp (Transmission Control Protocol) für die Internetadressfamilie.

- SOCK_DGRAM Unterstützt Datagramme, bei denen es sich um verbindungslose, unzuverlässige Pakete mit einer festen (in der Regel kleinen) maximalen Länge handelt. Verwendet das User Datagram Protocol (UDP) für die Internetadressfamilie.

    > [!NOTE]
    >  Die `Accept` Memberfunktion nimmt einen Verweis `CSocket` auf ein neues, leeres Objekt als Parameter. Sie müssen dieses Objekt `Accept`erstellen, bevor Sie aufrufen. Beachten Sie, dass die Verbindung geschlossen wird, wenn dieses Socketobjekt den Gültigkeitsbereich verlässt. Rufen `Create` Sie dieses neue Socketobjekt nicht auf.

> [!IMPORTANT]
> `Create`ist **nicht** threadsicher.  Wenn Sie es in einer Umgebung mit mehreren Threads aufrufen, in der es gleichzeitig von verschiedenen Threads aufgerufen werden kann, achten Sie darauf, jeden Aufruf mit einem Mutex oder einer anderen Synchronisierungssperre zu schützen.

Weitere Informationen zu Stream- und Datagrammsockets finden Sie in den Artikeln [Windows Sockets: Background](../../mfc/windows-sockets-background.md) and [Windows Sockets: Ports and Socket Addresses](../../mfc/windows-sockets-ports-and-socket-addresses.md) and Windows [Sockets 2 API](/windows/win32/WinSock/windows-sockets-start-page-2).

## <a name="casyncsocketdetach"></a><a name="detach"></a>CAsyncSocket::Detach

Rufen Sie diese Memberfunktion auf, um das SOCKET-Handle im *m_hSocket* Datenmember vom `CAsyncSocket` Objekt zu trennen, und legen Sie *m_hSocket* auf NULL fest.

```
SOCKET Detach();
```

## <a name="casyncsocketfromhandle"></a><a name="fromhandle"></a>CAsyncSocket::FromHandle

Gibt einen Zeiger `CAsyncSocket` auf ein Objekt zurück.

```
static CAsyncSocket* PASCAL FromHandle(SOCKET hSocket);
```

### <a name="parameters"></a>Parameter

*hSocket*<br/>
Enthält ein Handle für einen Socket.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf `CAsyncSocket` ein Objekt oder NULL, wenn kein `CAsyncSocket` Objekt an *hSocket*angefügt ist.

### <a name="remarks"></a>Bemerkungen

Wenn ein SOCKET-Handle `CAsyncSocket` angegeben wird, gibt die Memberfunktion NULL zurück, wenn ein Objekt nicht an das Handle angefügt ist.

## <a name="casyncsocketgetlasterror"></a><a name="getlasterror"></a>CAsyncSocket::GetLastError

Rufen Sie diese Memberfunktion auf, um den Fehlerstatus für den letzten fehlgeschlagenen Vorgang abzurufen.

```
static int PASCAL GetLastError();
```

### <a name="return-value"></a>Rückgabewert

Der Rückgabewert gibt den Fehlercode für die letzte Windows Sockets-API-Routine an, die von diesem Thread ausgeführt wird.

### <a name="remarks"></a>Bemerkungen

Wenn eine bestimmte Memberfunktion angibt, `GetLastError` dass ein Fehler aufgetreten ist, sollten Sie aufgerufen werden, um den entsprechenden Fehlercode abzurufen. Eine Liste der anwendbaren Fehlercodes finden Sie in den einzelnen Memberfunktionsbeschreibungen.

Weitere Informationen zu den Fehlercodes finden Sie unter [Windows Sockets 2 API](/windows/win32/WinSock/windows-sockets-start-page-2).

## <a name="casyncsocketgetpeername"></a><a name="getpeername"></a>CAsyncSocket::GetPeerName

Rufen Sie diese Memberfunktion auf, um die Adresse des Peersockets abzurufen, mit dem dieser Socket verbunden ist.

```
BOOL GetPeerName(
    CString& rPeerAddress,
    UINT& rPeerPort);

BOOL GetPeerName(
    SOCKADDR* lpSockAddr,
    int* lpSockAddrLen);
```

### <a name="parameters"></a>Parameter

*rPeerAddress*<br/>
Verweis auf `CString` ein Objekt, das eine IP-Adresse mit gepunkteter Nummer empfängt.

*rPeerPort*<br/>
Verweis auf ein UINT, das einen Port speichert.

*lpSockAddr*<br/>
Ein Zeiger auf die [SOCKADDR-Struktur,](/windows/win32/winsock/sockaddr-2) die den Namen des Peersockets empfängt.

*lpSockAddrLen*<br/>
Ein Zeiger auf die Länge der Adresse in *lpSockAddr* in Bytes. Bei der Rückgabe enthält das Argument *lpSockAddrLen* die tatsächliche Größe von *lpSockAddr,* die in Bytes zurückgegeben wird.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Funktion erfolgreich ist; Andernfalls 0, und ein bestimmter Fehlercode kann abgerufen werden, indem [GetLastError](#getlasterror)aufgerufen wird. Die folgenden Fehler gelten für diese Memberfunktion:

- WSANOTINITIALISED Ein erfolgreicher [AfxSocketSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) muss auftreten, bevor diese API verwendet werden kann.

- WSAENETDOWN Die Windows Sockets-Implementierung hat festgestellt, dass das Netzwerksubsystem ausgefallen ist.

- WSAEFAULT Das Argument *lpSockAddrLen* ist nicht groß genug.

- WSAEINPROGRESS Ein blockierender Windows Sockets-Aufruf wird ausgeführt.

- WSAENOTCONN Der Sockel ist nicht angeschlossen.

- WSAENOTSOCK Der Deskriptor ist kein Socket.

### <a name="remarks"></a>Bemerkungen

Um IPv6-Adressen zu behandeln, verwenden Sie [CAsyncSocket::GetPeerNameEx](#getpeernameex).

## <a name="casyncsocketgetpeernameex"></a><a name="getpeernameex"></a>CAsyncSocket::GetPeerNameEx

Rufen Sie diese Memberfunktion auf, um die Adresse des Peersockets abzurufen, mit dem dieser Socket verbunden ist (behandelt IPv6-Adressen).

```
BOOL GetPeerNameEx(
    CString& rPeerAddress,
    UINT& rPeerPort);
```

### <a name="parameters"></a>Parameter

*rPeerAddress*<br/>
Verweis auf `CString` ein Objekt, das eine IP-Adresse mit gepunkteter Nummer empfängt.

*rPeerPort*<br/>
Verweis auf ein UINT, das einen Port speichert.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Funktion erfolgreich ist; Andernfalls 0, und ein bestimmter Fehlercode kann abgerufen werden, indem [GetLastError](#getlasterror)aufgerufen wird. Die folgenden Fehler gelten für diese Memberfunktion:

- WSANOTINITIALISED Ein erfolgreicher [AfxSocketSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) muss auftreten, bevor diese API verwendet werden kann.

- WSAENETDOWN Die Windows Sockets-Implementierung hat festgestellt, dass das Netzwerksubsystem ausgefallen ist.

- WSAEFAULT Das Argument *lpSockAddrLen* ist nicht groß genug.

- WSAEINPROGRESS Ein blockierender Windows Sockets-Aufruf wird ausgeführt.

- WSAENOTCONN Der Sockel ist nicht angeschlossen.

- WSAENOTSOCK Der Deskriptor ist kein Socket.

### <a name="remarks"></a>Bemerkungen

Diese Funktion ist die gleiche wie [CAsyncSocket::GetPeerName,](#getpeername) außer dass sie IPv6-Adressen sowie ältere Protokolle verarbeitet.

## <a name="casyncsocketgetsockname"></a><a name="getsockname"></a>CAsyncSocket::GetSockName

Rufen Sie diese Memberfunktion auf, um den lokalen Namen für einen Socket abzurufen.

```
BOOL GetSockName(
    CString& rSocketAddress,
    UINT& rSocketPort);

BOOL GetSockName(
    SOCKADDR* lpSockAddr,
    int* lpSockAddrLen);
```

### <a name="parameters"></a>Parameter

*rSocketAddress*<br/>
Verweis auf `CString` ein Objekt, das eine IP-Adresse mit gepunkteter Nummer empfängt.

*rSocketPort*<br/>
Verweis auf ein UINT, das einen Port speichert.

*lpSockAddr*<br/>
Ein Zeiger auf eine [SOCKADDR-Struktur,](/windows/win32/winsock/sockaddr-2) die die Adresse des Sockets empfängt.

*lpSockAddrLen*<br/>
Ein Zeiger auf die Länge der Adresse in *lpSockAddr* in Bytes.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Funktion erfolgreich ist; Andernfalls 0, und ein bestimmter Fehlercode kann abgerufen werden, indem [GetLastError](#getlasterror)aufgerufen wird. Die folgenden Fehler gelten für diese Memberfunktion:

- WSANOTINITIALISED Ein erfolgreicher [AfxSocketSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) muss auftreten, bevor diese API verwendet werden kann.

- WSAENETDOWN Die Windows Sockets-Implementierung hat festgestellt, dass das Netzwerksubsystem ausgefallen ist.

- WSAEFAULT Das Argument *lpSockAddrLen* ist nicht groß genug.

- WSAEINPROGRESS Ein blockierender Windows Sockets-Vorgang wird ausgeführt.

- WSAENOTSOCK Der Deskriptor ist kein Socket.

- WSAEINVAL Der Socket wurde nicht an `Bind`eine Adresse mit gebunden.

### <a name="remarks"></a>Bemerkungen

Dieser Aufruf ist besonders `Connect` nützlich, wenn ein `Bind` Anruf ohne eine erste Aufruf erfolgt ist. Dieser Aufruf stellt die einzige Möglichkeit dar, mit der Sie die lokale Zuordnung bestimmen können, die vom System festgelegt wurde.

Um IPv6-Adressen zu behandeln, verwenden Sie [CAsyncSocket::GetSockNameEx](#getsocknameex)

## <a name="casyncsocketgetsocknameex"></a><a name="getsocknameex"></a>CAsyncSocket::GetSockNameEx

Rufen Sie diese Memberfunktion auf, um den lokalen Namen für einen Socket abzurufen (behandelt IPv6-Adressen).

```
BOOL GetSockNameEx(
    CString& rSocketAddress,
    UINT& rSocketPort);
```

### <a name="parameters"></a>Parameter

*rSocketAddress*<br/>
Verweis auf `CString` ein Objekt, das eine IP-Adresse mit gepunkteter Nummer empfängt.

*rSocketPort*<br/>
Verweis auf ein UINT, das einen Port speichert.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Funktion erfolgreich ist; Andernfalls 0, und ein bestimmter Fehlercode kann abgerufen werden, indem [GetLastError](#getlasterror)aufgerufen wird. Die folgenden Fehler gelten für diese Memberfunktion:

- WSANOTINITIALISED Ein erfolgreicher [AfxSocketSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) muss auftreten, bevor diese API verwendet werden kann.

- WSAENETDOWN Die Windows Sockets-Implementierung hat festgestellt, dass das Netzwerksubsystem ausgefallen ist.

- WSAEFAULT Das Argument *lpSockAddrLen* ist nicht groß genug.

- WSAEINPROGRESS Ein blockierender Windows Sockets-Vorgang wird ausgeführt.

- WSAENOTSOCK Der Deskriptor ist kein Socket.

- WSAEINVAL Der Socket wurde nicht an `Bind`eine Adresse mit gebunden.

### <a name="remarks"></a>Bemerkungen

Dieser Aufruf ist derselbe wie [CAsyncSocket::GetSockName,](#getsockname) außer dass er IPv6-Adressen sowie ältere Protokolle verarbeitet.

Dieser Aufruf ist besonders `Connect` nützlich, wenn ein `Bind` Anruf ohne eine erste Aufruf erfolgt ist. Dieser Aufruf stellt die einzige Möglichkeit dar, mit der Sie die lokale Zuordnung bestimmen können, die vom System festgelegt wurde.

## <a name="casyncsocketgetsockopt"></a><a name="getsockopt"></a>CAsyncSocket::GetSockOpt

Rufen Sie diese Memberfunktion auf, um eine Socketoption abzurufen.

```
BOOL GetSockOpt(
    int nOptionName,
    void* lpOptionValue,
    int* lpOptionLen,
    int nLevel = SOL_SOCKET);
```

### <a name="parameters"></a>Parameter

*nOptionName*<br/>
Die Socketoption, für die der Wert abgerufen werden soll.

*lpOptionValue*<br/>
Ein Zeiger auf den Puffer, in dem der Wert für die angeforderte Option zurückgegeben werden soll. Der der ausgewählten Option zugeordnete Wert wird im Puffer *lpOptionValue*zurückgegeben. Die ganze Zahl, auf die *lpOptionLen* zeigt, sollte ursprünglich die Größe dieses Puffers in Bytes enthalten. und bei der Rückgabe wird sie auf die Größe des zurückgegebenen Werts gesetzt. Für SO_LINGER wird dies die `LINGER` Größe einer Struktur sein; für alle anderen Optionen wird es die Größe eines BOOL oder eines **int**sein, abhängig von der Option. Die Liste der Optionen und deren Größen finden Sie im Abschnitt "Bemerkungen".

*lpOptionLen*<br/>
Ein Zeiger auf die Größe des *lpOptionValue-Puffers* in Bytes.

*nLevel*<br/>
Die Ebene, auf der die Option definiert wird; die einzigen unterstützten Ebenen sind SOL_SOCKET und IPPROTO_TCP.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Funktion erfolgreich ist; Andernfalls 0, und ein bestimmter Fehlercode kann abgerufen werden, indem [GetLastError](#getlasterror)aufgerufen wird. Wenn eine Option nie `SetSockOpt`mit `GetSockOpt` festgelegt wurde, gibt der Standardwert für die Option zurück. Die folgenden Fehler gelten für diese Memberfunktion:

- WSANOTINITIALISED Ein erfolgreicher [AfxSocketSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) muss auftreten, bevor diese API verwendet werden kann.

- WSAENETDOWN Die Windows Sockets-Implementierung hat festgestellt, dass das Netzwerksubsystem ausgefallen ist.

- WSAEFAULT Das Argument *lpOptionLen* war ungültig.

- WSAEINPROGRESS Ein blockierender Windows Sockets-Vorgang wird ausgeführt.

- WSAENOPROTOOPT Die Option ist unbekannt oder wird nicht unterstützt. Insbesondere wird SO_BROADCAST für Sockets vom Typ SOCK_STREAM nicht unterstützt, während SO_ACCEPTCONN, SO_DONTLINGER, SO_KEEPALIVE, SO_LINGER und SO_OOBINLINE für Sockets vom Typ SOCK_DGRAM nicht unterstützt werden.

- WSAENOTSOCK Der Deskriptor ist kein Socket.

### <a name="remarks"></a>Bemerkungen

`GetSockOpt`ruft den aktuellen Wert für eine Socketoption ab, die einem Socket eines beliebigen Typs in einem beliebigen Zustand zugeordnet ist, und speichert das Ergebnis in *lpOptionValue*. Optionen wirken sich auf Socketvorgänge aus, z. B. das Routing von Paketen, die Out-of-Band-Datenübertragung usw.

Die folgenden Optionen `GetSockOpt`werden für unterstützt. Der Typ identifiziert den Datentyp, der von *lpOptionValue*adressiert wird. Die Option TCP_NODELAY verwendet IPPROTO_TCP. Alle anderen Optionen verwenden Ebene SOL_SOCKET.

|Wert|type|Bedeutung|
|-----------|----------|-------------|
|SO_ACCEPTCONN|BOOL|Socket hört zu.|
|SO_BROADCAST|BOOL|Socket ist für die Übertragung von Broadcast-Nachrichten konfiguriert.|
|SO_DEBUG|BOOL|Das Debuggen ist aktiviert.|
|SO_DONTLINGER|BOOL|Wenn true, ist die Option SO_LINGER deaktiviert.|
|SO_DONTROUTE|BOOL|Routing ist deaktiviert.|
|SO_ERROR|**int**|Rufen Sie den Fehlerstatus ab, und löschen Sie.|
|SO_KEEPALIVE|BOOL|Keep-alives werden gesendet.|
|SO_LINGER|`struct LINGER`|Gibt die aktuellen Verweiloptionen zurück.|
|SO_OOBINLINE|BOOL|Out-of-Band-Daten werden im normalen Datenstrom empfangen.|
|SO_RCVBUF|INT|Puffergröße für Empfange.|
|SO_REUSEADDR|BOOL|Der Socket kann an eine Adresse gebunden werden, die bereits verwendet wird.|
|SO_SNDBUF|**int**|Puffergröße für Sendesendet.|
|SO_TYPE|**int**|Der Typ des Sockets (z. B. SOCK_STREAM).|
|TCP_NODELAY|BOOL|Deaktiviert den Nagle-Algorithmus für Sammelsendungen.|

Berkeley Software Distribution (BSD)-Optionen werden nicht unterstützt: `GetSockOpt`

|Wert|type|Bedeutung|
|-----------|----------|-------------|
|SO_RCVLOWAT|**int**|Erhalten Sie niedrige Wassermark.|
|SO_RCVTIMEO|**int**|Erhalten Sie ein Timeout.|
|SO_SNDLOWAT|**int**|Senden Sie niedrige Wassermarke.|
|SO_SNDTIMEO|**int**|Zeitout senden.|
|IP_OPTIONS||Abrufen von Optionen im IP-Header.|
|TCP_MAXSEG|**int**|Erhalten Sie die maximale TCP-Segmentgröße.|

Wenn `GetSockOpt` Sie mit einer nicht unterstützten Option aufrufen, wird ein Fehlercode von WSAENOPROTOOPT von `GetLastError`zurückgegeben.

## <a name="casyncsocketioctl"></a><a name="ioctl"></a>CAsyncSocket::IOCtl

Rufen Sie diese Memberfunktion auf, um den Modus eines Sockets zu steuern.

```
BOOL IOCtl(
    long lCommand,
    DWORD* lpArgument);
```

### <a name="parameters"></a>Parameter

*lCommand*<br/>
Der Befehl, der für den Socket ausgeführt werden soll.

*lpArgument*<br/>
Ein Zeiger auf einen Parameter für *lCommand*.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Funktion erfolgreich ist; Andernfalls 0, und ein bestimmter Fehlercode kann abgerufen werden, indem [GetLastError](#getlasterror)aufgerufen wird. Die folgenden Fehler gelten für diese Memberfunktion:

- WSANOTINITIALISED Ein erfolgreicher [AfxSocketSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) muss auftreten, bevor diese API verwendet werden kann.

- WSAENETDOWN Die Windows Sockets-Implementierung hat festgestellt, dass das Netzwerksubsystem ausgefallen ist.

- WSAEINVAL *lCommand* ist kein gültiger Befehl, oder *lpArgument* ist kein akzeptabler Parameter für *lCommand*, oder der Befehl ist nicht auf den angegebenen Sockettyp anwendbar.

- WSAEINPROGRESS Ein blockierender Windows Sockets-Vorgang wird ausgeführt.

- WSAENOTSOCK Der Deskriptor ist kein Socket.

### <a name="remarks"></a>Bemerkungen

Diese Routine kann auf jedem Socket in jedem Zustand verwendet werden. Es wird verwendet, um Betriebsparameter abzurufen oder abzurufen, die dem Socket zugeordnet sind, unabhängig vom Protokoll- und Kommunikationssubsystem. Die folgenden Befehle werden unterstützt:

- FIONBIO Aktivieren oder deaktivieren Sie den Nichtblockierungsmodus auf dem Socket. Der *lpArgument-Parameter* `DWORD`zeigt auf ein , das ungleich Null ist, wenn der nicht blockierende Modus aktiviert werden soll, und Null, wenn er deaktiviert werden soll. Wenn `AsyncSelect` für einen Socket ausgegeben wurde, `IOCtl` schlägt jeder Versuch fehl, den Socket wieder in den Blockierungsmodus zu versetzen. Um den Socket wieder in den Blockierungsmodus zu versetzen und `AsyncSelect` den `AsyncSelect` WSAEINVAL-Fehler zu verhindern, muss eine Anwendung zuerst durch Aufrufen des *parameters lEvent* gleich 0 und dann aufrufen. `IOCtl`

- FIONREAD Bestimmen Sie die maximale Anzahl von `Receive` Bytes, die mit einem Aufruf von diesem Socket gelesen werden können. Der *lpArgument-Parameter* `DWORD` zeigt `IOCtl` auf ein, in dem das Ergebnis gespeichert wird. Wenn dieser Socket vom Typ SOCK_STREAM ist, gibt FIONREAD die Gesamtmenge der Daten zurück, die in einem einzigen `Receive`gelesen werden können. Dies entspricht normalerweise der Gesamtmenge der Daten, die auf dem Socket in die Warteschlange eingereiht werden. Wenn dieser Socket vom Typ SOCK_DGRAM ist, gibt FIONREAD die Größe des ersten Datagramms zurück, das in der Warteschlange auf dem Socket steht.

- SIOCATMARK Bestimmen Sie, ob alle Out-of-Band-Daten gelesen wurden. Dies gilt nur für einen Socket vom Typ SOCK_STREAM der für den Inline-Empfang von Out-of-Band-Daten (SO_OOBINLINE) konfiguriert wurde. Wenn keine Out-of-Band-Daten auf das Lesen warten, gibt der Vorgang einen Wert ungleich Null zurück. Andernfalls gibt es 0 `Receive` zurück, und die nächste oder `ReceiveFrom` auf dem Socket ausgeführte wird einige oder alle Daten vor der "Marke" abrufen; Die Anwendung sollte den SIOCATMARK-Vorgang verwenden, um zu bestimmen, ob Daten übrig bleiben. Wenn den "dringenden" (Out-of-Band) Daten vorausgegangen sind, werden diese in der Reihenfolge empfangen. (Beachten Sie, dass ein `Receive` oder `ReceiveFrom` wird nie Out-of-Band und normale Daten in einem Anruf mischen.) Der *lpArgument-Parameter* `DWORD` zeigt `IOCtl` auf ein, in dem das Ergebnis gespeichert wird.

Diese Funktion ist eine `ioctl()` Teilmenge von wie in Berkeley-Sockets verwendet. Insbesondere gibt es keinen Befehl, der FIOASYNC entspricht, während SIOCATMARK der einzige Befehl auf Socketebene ist, der unterstützt wird.

## <a name="casyncsocketlisten"></a><a name="listen"></a>CAsyncSocket::Listen

Rufen Sie diese Memberfunktion auf, um eingehende Verbindungsanforderungen zu beantworten.

```
BOOL Listen(int nConnectionBacklog = 5);
```

### <a name="parameters"></a>Parameter

*nConnectionBacklog*<br/>
Die maximale Länge, bis zu der die Warteschlange ausstehender Verbindungen wachsen kann. Gültiger Bereich liegt zwischen 1 und 5.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Funktion erfolgreich ist; Andernfalls 0, und ein bestimmter Fehlercode kann abgerufen werden, indem [GetLastError](#getlasterror)aufgerufen wird. Die folgenden Fehler gelten für diese Memberfunktion:

- WSANOTINITIALISED Ein erfolgreicher [AfxSocketSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) muss auftreten, bevor diese API verwendet werden kann.

- WSAENETDOWN Die Windows Sockets-Implementierung hat festgestellt, dass das Netzwerksubsystem ausgefallen ist.

- WSAEADDRINUSE Es wurde versucht, eine in Der Verwendung verwendende Adresse anzuhören.

- WSAEINPROGRESS Ein blockierender Windows Sockets-Vorgang wird ausgeführt.

- WSAEINVAL Der Socket wurde `Bind` nicht gebunden oder ist bereits angeschlossen.

- WSAEISCONN Der Socket ist bereits angeschlossen.

- WSAEMFILE Es sind keine weiteren Dateideskriptoren verfügbar.

- WSAENOBUFS Kein Pufferspeicher verfügbar.

- WSAENOTSOCK Der Deskriptor ist kein Socket.

- WSAEOPNOTSUPP Der socket, auf den verwiesen `Listen` wird, ist nicht von einem Typ, der den Vorgang unterstützt.

### <a name="remarks"></a>Bemerkungen

Um Verbindungen zu akzeptieren, wird `Create`der Socket zuerst mit erstellt, `Listen`ein Backlog für `Accept`eingehende Verbindungen wird mit angegeben, und dann werden die Verbindungen mit akzeptiert. `Listen`gilt nur für Sockets, die Verbindungen unterstützen, d. h. solche vom Typ SOCK_STREAM. Dieser Socket wird in den "passiven" Modus versetzt, in dem eingehende Verbindungen bestätigt und bis zur Annahme durch den Prozess in die Warteschlange gestellt werden.

Diese Funktion wird in der Regel von Servern (oder jeder Anwendung, die Verbindungen akzeptieren möchte) verwendet, die mehr als eine Verbindungsanforderung gleichzeitig haben können: Wenn eine Verbindungsanforderung mit der Warteschlange vollständig eintrifft, erhält der Client eine Fehlermeldung mit der Angabe VON WSAECONNREFUSED.

`Listen`versucht, weiterhin rational zu funktionieren, wenn keine Ports verfügbar sind (Deskriptoren). Verbindungen werden akzeptiert, bis die Warteschlange geleert wird. Wenn Ports verfügbar werden, `Listen` wird `Accept` die Warteschlange nach Möglichkeit durch einen späteren Aufruf oder auf den aktuellen oder letzten "Backlog" aufgefüllt, und die Suche nach eingehenden Verbindungen wird fortgesetzt.

## <a name="casyncsocketm_hsocket"></a><a name="m_hsocket"></a>CAsyncSocket::m_hSocket

Enthält das SOCKET-Handle für den Socket, der von diesem `CAsyncSocket` Objekt gekapselt wird.

```
SOCKET m_hSocket;
```

## <a name="casyncsocketonaccept"></a><a name="onaccept"></a>CAsyncSocket::OnAccept

Wird vom Framework aufgerufen, um einen abhörenden Socket zu benachrichtigen, dass er ausstehende Verbindungsanforderungen akzeptieren kann, indem die [Memberfunktion Akzeptieren](#accept) aufgerufen wird.

```
virtual void OnAccept(int nErrorCode);
```

### <a name="parameters"></a>Parameter

*nErrorCode*<br/>
Der letzte Fehler in einem Socket. Die folgenden Fehlercodes `OnAccept` gelten für die Memberfunktion:

- **0** Die Funktion wurde erfolgreich ausgeführt.

- WSAENETDOWN Die Windows Sockets-Implementierung hat festgestellt, dass das Netzwerksubsystem ausgefallen ist.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [Windows Sockets: Socket Notifications](../../mfc/windows-sockets-socket-notifications.md).

## <a name="casyncsocketonclose"></a><a name="onclose"></a>CAsyncSocket::OnClose

Wird vom Framework aufgerufen, um diesen Socket zu benachrichtigen, dass der verbundene Socket durch seinen Prozess geschlossen wird.

```
virtual void OnClose(int nErrorCode);
```

### <a name="parameters"></a>Parameter

*nErrorCode*<br/>
Der letzte Fehler in einem Socket. Die folgenden Fehlercodes `OnClose` gelten für die Memberfunktion:

- **0** Die Funktion wurde erfolgreich ausgeführt.

- WSAENETDOWN Die Windows Sockets-Implementierung hat festgestellt, dass das Netzwerksubsystem ausgefallen ist.

- WSAECONNRESET Die Verbindung wurde von der Entferntenseite zurückgesetzt.

- WSAECONNABORTED Die Verbindung wurde aufgrund eines Timeouts oder eines anderen Fehlers abgebrochen.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [Windows Sockets: Socket Notifications](../../mfc/windows-sockets-socket-notifications.md).

## <a name="casyncsocketonconnect"></a><a name="onconnect"></a>CAsyncSocket::OnConnect

Wird vom Framework aufgerufen, um diesen Verbindungssocket zu benachrichtigen, dass der Verbindungsversuch erfolgreich oder fehlerhaft abgeschlossen wurde.

```
virtual void OnConnect(int nErrorCode);
```

### <a name="parameters"></a>Parameter

*nErrorCode*<br/>
Der letzte Fehler in einem Socket. Die folgenden Fehlercodes `OnConnect` gelten für die Memberfunktion:

- **0** Die Funktion wurde erfolgreich ausgeführt.

- WSAEADDRINUSE Die angegebene Adresse wird bereits verwendet.

- WSAEADDRNOTAVAIL Die angegebene Adresse ist vom lokalen Computer nicht verfügbar.

- WSAEAFNOSUPPORT-Adressen in der angegebenen Familie können nicht mit diesem Socket verwendet werden.

- WSAECONNREFUSED Der Verbindungsversuch wurde mit Nachdruck abgelehnt.

- WSAEDESTADDRREQ Eine Zieladresse ist erforderlich.

- WSAEFAULT Das Argument *lpSockAddrLen* ist falsch.

- WSAEINVAL Der Socket ist bereits an eine Adresse gebunden.

- WSAEISCONN Der Socket ist bereits angeschlossen.

- WSAEMFILE Es sind keine weiteren Dateideskriptoren verfügbar.

- WSAENETUNREACH Das Netzwerk kann derzeit nicht von diesem Host aus erreicht werden.

- WSAENOBUFS Kein Pufferspeicher verfügbar. Der Socket kann nicht angeschlossen werden.

- WSAENOTCONN Der Sockel ist nicht angeschlossen.

- WSAENOTSOCK Der Deskriptor ist eine Datei, kein Socket.

- WSAETIMEDOUT Der Versuch, eine Verbindung herzustellen, wurde ohne Herstellen einer Verbindung ausgeschlossen.

### <a name="remarks"></a>Bemerkungen

> [!NOTE]
> In [CSocket](../../mfc/reference/csocket-class.md) `OnConnect` wird die Benachrichtigungsfunktion nie aufgerufen. Bei Verbindungen rufen `Connect`Sie einfach auf, die zurückgegeben wird, wenn die Verbindung abgeschlossen ist (entweder erfolgreich oder irrtümlich). Wie Verbindungsbenachrichtigungen behandelt werden, ist ein Detail der MFC-Implementierung.

Weitere Informationen finden Sie unter [Windows Sockets: Socket Notifications](../../mfc/windows-sockets-socket-notifications.md).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCAsyncSocket#1](../../mfc/reference/codesnippet/cpp/casyncsocket-class_1.cpp)]

## <a name="casyncsocketonoutofbanddata"></a><a name="onoutofbanddata"></a>CAsyncSocket::OnOutOfBandData

Wird vom Framework aufgerufen, um den empfangenden Socket zu benachrichtigen, dass der sendende Socket Out-of-Band-Daten zum Senden hat.

```
virtual void OnOutOfBandData(int nErrorCode);
```

### <a name="parameters"></a>Parameter

*nErrorCode*<br/>
Der letzte Fehler in einem Socket. Die folgenden Fehlercodes `OnOutOfBandData` gelten für die Memberfunktion:

- **0** Die Funktion wurde erfolgreich ausgeführt.

- WSAENETDOWN Die Windows Sockets-Implementierung hat festgestellt, dass das Netzwerksubsystem ausgefallen ist.

### <a name="remarks"></a>Bemerkungen

Out-of-Band-Daten sind ein logisch unabhängiger Kanal, der jedem Paar verbundener Sockets vom Typ SOCK_STREAM zugeordnet ist. Der Kanal wird in der Regel verwendet, um dringende Daten zu senden.

MFC unterstützt Out-of-Band-Daten, `CAsyncSocket` aber Benutzer von Klassen werden davon abgeraten, sie zu verwenden. Die einfachere Möglichkeit ist, einen zweiten Socket für die Weitergabe solcher Daten zu erstellen. Weitere Informationen zu Out-of-Band-Daten finden Sie unter [Windows Sockets: Socket Notifications](../../mfc/windows-sockets-socket-notifications.md).

## <a name="casyncsocketonreceive"></a><a name="onreceive"></a>CAsyncSocket::OnReceive

Wird vom Framework aufgerufen, um diesen Socket darüber zu benachrichtigen, dass sich Daten im Puffer befinden, die durch Aufrufen der `Receive` Memberfunktion abgerufen werden können.

```
virtual void OnReceive(int nErrorCode);
```

### <a name="parameters"></a>Parameter

*nErrorCode*<br/>
Der letzte Fehler in einem Socket. Die folgenden Fehlercodes `OnReceive` gelten für die Memberfunktion:

- **0** Die Funktion wurde erfolgreich ausgeführt.

- WSAENETDOWN Die Windows Sockets-Implementierung hat festgestellt, dass das Netzwerksubsystem ausgefallen ist.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [Windows Sockets: Socket Notifications](../../mfc/windows-sockets-socket-notifications.md).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCAsyncSocket#2](../../mfc/reference/codesnippet/cpp/casyncsocket-class_2.cpp)]

## <a name="casyncsocketonsend"></a><a name="onsend"></a>CAsyncSocket::OnSend

Wird vom Framework aufgerufen, um den Socket zu `Send` benachrichtigen, dass er jetzt Daten senden kann, indem die Memberfunktion aufgerufen wird.

```
virtual void OnSend(int nErrorCode);
```

### <a name="parameters"></a>Parameter

*nErrorCode*<br/>
Der letzte Fehler in einem Socket. Die folgenden Fehlercodes `OnSend` gelten für die Memberfunktion:

- **0** Die Funktion wurde erfolgreich ausgeführt.

- WSAENETDOWN Die Windows Sockets-Implementierung hat festgestellt, dass das Netzwerksubsystem ausgefallen ist.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [Windows Sockets: Socket Notifications](../../mfc/windows-sockets-socket-notifications.md).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCAsyncSocket#3](../../mfc/reference/codesnippet/cpp/casyncsocket-class_3.cpp)]

## <a name="casyncsocketoperator-"></a><a name="operator_eq"></a>CAsyncSocket::operator =

Weist einem `CAsyncSocket` Objekt einen neuen Wert zu.

```
void operator=(const CAsyncSocket& rSrc);
```

### <a name="parameters"></a>Parameter

*rSrc*<br/>
Ein Verweis auf `CAsyncSocket` ein vorhandenes Objekt.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Funktion `CAsyncSocket` auf, `CAsyncSocket` um ein vorhandenes Objekt in ein anderes Objekt zu kopieren.

## <a name="casyncsocketoperator-socket"></a><a name="operator_socket"></a>CAsyncSocket::operator SOCKET

Verwenden Sie diesen Operator, um `CAsyncSocket` das SOCKET-Handle des Objekts abzurufen.

```
operator SOCKET() const;
```

### <a name="return-value"></a>Rückgabewert

Wenn erfolgreich, das Handle des SOCKET-Objekts; andernfalls NULL.

### <a name="remarks"></a>Bemerkungen

Sie können das Handle verwenden, um Windows-APIs direkt aufzurufen.

## <a name="casyncsocketreceive"></a><a name="receive"></a>CAsyncSocket::Empfangen

Rufen Sie diese Memberfunktion auf, um Daten von einem Socket zu empfangen.

```
virtual int Receive(
    void* lpBuf,
    int nBufLen,
    int nFlags = 0);
```

### <a name="parameters"></a>Parameter

*lpBuf*<br/>
Ein Puffer für die eingehenden Daten.

*nBufLen*<br/>
Die Länge von *lpBuf* in Bytes.

*nFlags*<br/>
Gibt die Art und Weise an, in der der Aufruf erfolgt. Die Semantik dieser Funktion wird durch die Socketoptionen und den Parameter *nFlags* bestimmt. Letzteres wird durch Kombinieren eines der folgenden Werte mit dem **C++-OR-Operator** erstellt:

- MSG_PEEK Blick auf die eingehenden Daten. Die Daten werden in den Puffer kopiert, aber nicht aus der Eingabewarteschlange entfernt.

- MSG_OOB Out-of-Band-Daten verarbeiten.

### <a name="return-value"></a>Rückgabewert

Wenn kein Fehler `Receive` auftritt, wird die Anzahl der empfangenen Bytes zurückgegeben. Wenn die Verbindung geschlossen wurde, wird 0 zurückgegeben. Andernfalls wird ein Wert von SOCKET_ERROR zurückgegeben, und ein bestimmter Fehlercode kann abgerufen werden, indem [GetLastError](#getlasterror)aufgerufen wird. Die folgenden Fehler gelten für diese Memberfunktion:

- WSANOTINITIALISED Ein erfolgreicher [AfxSocketSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) muss auftreten, bevor diese API verwendet werden kann.

- WSAENETDOWN Die Windows Sockets-Implementierung hat festgestellt, dass das Netzwerksubsystem ausgefallen ist.

- WSAENOTCONN Der Sockel ist nicht angeschlossen.

- WSAEINPROGRESS Ein blockierender Windows Sockets-Vorgang wird ausgeführt.

- WSAENOTSOCK Der Deskriptor ist kein Socket.

- WSAEOPNOTSUPP MSG_OOB angegeben wurde, aber der Socket ist nicht vom Typ SOCK_STREAM.

- WSAESHUTDOWN Der Socket wurde heruntergefahren; Es ist nicht `Receive` möglich, einen `ShutDown` Socket aufzurufen, nachdem er aufgerufen wurde, wobei *nHow* auf 0 oder 2 gesetzt ist.

- WSAEWOULDBLOCK Der Socket ist als `Receive` nicht blockierend markiert und der Vorgang würde blockieren.

- WSAEMSGSIZE Das Datagramm war zu groß, um in den angegebenen Puffer zu passen, und wurde abgeschnitten.

- WSAEINVAL Der Socket wurde `Bind`nicht an gebunden.

- WSAECONNABORTED Die virtuelle Verbindung wurde aufgrund eines Timeouts oder eines anderen Fehlers abgebrochen.

- WSAECONNRESET Die virtuelle Schaltung wurde von der entfernten Seite zurückgesetzt.

### <a name="remarks"></a>Bemerkungen

Diese Funktion wird für verbundene Stream- oder Datagrammsockets verwendet und zum Lesen eingehender Daten verwendet.

Bei Sockets vom Typ SOCK_STREAM werden so viele Informationen zurückgegeben, wie derzeit bis zur Größe des bereitgestellten Puffers verfügbar sind. Wenn der Socket für den Inline-Empfang von Out-of-Band-Daten konfiguriert wurde (Socketoption SO_OOBINLINE) und Out-of-Band-Daten ungelesen sind, werden nur Out-of-Band-Daten zurückgegeben. Die Anwendung kann `IOCtlSIOCATMARK` die Option oder [OnOutOfBandData](#onoutofbanddata) verwenden, um zu bestimmen, ob weitere Out-of-Band-Daten gelesen werden müssen.

Bei Datagrammsockets werden die Daten aus dem ersten in die Warteschlange nustonten Datagramm bis zur Größe des bereitgestellten Puffers extrahiert. Wenn das Datagramm größer als der angegebene Puffer ist, wird der Puffer mit dem ersten `Receive` Teil des Datagramms gefüllt, die überschüssigen Daten gehen verloren und geben den Wert SOCKET_ERROR zurück, wobei der Fehlercode auf WSAEMSGSIZE festgelegt ist. Wenn am Socket keine eingehenden Daten verfügbar sind, wird der Wert SOCKET_ERROR zurückgegeben, wobei der Fehlercode auf WSAEWOULDBLOCK festgelegt ist. Die [OnReceive-Rückruffunktion](#onreceive) kann verwendet werden, um zu bestimmen, wann weitere Daten eintreffen.

Wenn der Socket vom Typ SOCK_STREAM ist und die Remoteseite `Receive` die Verbindung ordnungsgemäß heruntergefahren hat, wird eine sofort mit 0 empfangenen Bytes abgeschlossen. Wenn die Verbindung zurückgesetzt `Receive` wurde, schlägt a mit dem Fehler WSAECONNRESET fehl.

`Receive`sollte nur einmal für jedes Mal aufgerufen [werden, wenn CAsyncSocket::OnReceive](#onreceive) aufgerufen wird.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CAsyncSocket::OnReceive](#onreceive).

## <a name="casyncsocketreceivefrom"></a><a name="receivefrom"></a>CAsyncSocket::ReceiveVon

Rufen Sie diese Memberfunktion auf, um ein Datagramm zu empfangen und die Quelladresse in der [SOCKADDR-Struktur](/windows/win32/winsock/sockaddr-2) oder in *rSocketAddress zu*speichern.

```
int ReceiveFrom(
    void* lpBuf,
    int nBufLen,
    CString& rSocketAddress,
    UINT& rSocketPort,
    int nFlags = 0);

int ReceiveFrom(
    void* lpBuf,
    int nBufLen,
    SOCKADDR* lpSockAddr,
    int* lpSockAddrLen,
    int nFlags = 0);
```

### <a name="parameters"></a>Parameter

*lpBuf*<br/>
Ein Puffer für die eingehenden Daten.

*nBufLen*<br/>
Die Länge von *lpBuf* in Bytes.

*rSocketAddress*<br/>
Verweis auf `CString` ein Objekt, das eine IP-Adresse mit gepunkteter Nummer empfängt.

*rSocketPort*<br/>
Verweis auf ein UINT, das einen Port speichert.

*lpSockAddr*<br/>
Ein Zeiger auf eine [SOCKADDR-Struktur,](/windows/win32/winsock/sockaddr-2) die die Quelladresse bei der Rückgabe enthält.

*lpSockAddrLen*<br/>
Ein Zeiger auf die Länge der Quelladresse in *lpSockAddr* in Bytes.

*nFlags*<br/>
Gibt die Art und Weise an, in der der Aufruf erfolgt. Die Semantik dieser Funktion wird durch die Socketoptionen und den Parameter *nFlags* bestimmt. Letzteres wird durch Kombinieren eines der folgenden Werte mit dem **C++-OR-Operator** erstellt:

- MSG_PEEK Blick auf die eingehenden Daten. Die Daten werden in den Puffer kopiert, aber nicht aus der Eingabewarteschlange entfernt.

- MSG_OOB Out-of-Band-Daten verarbeiten.

### <a name="return-value"></a>Rückgabewert

Wenn kein Fehler `ReceiveFrom` auftritt, wird die Anzahl der empfangenen Bytes zurückgegeben. Wenn die Verbindung geschlossen wurde, wird 0 zurückgegeben. Andernfalls wird ein Wert von SOCKET_ERROR zurückgegeben, und ein `GetLastError`bestimmter Fehlercode kann durch Aufrufen abgerufen werden. Die folgenden Fehler gelten für diese Memberfunktion:

- WSANOTINITIALISED Ein erfolgreicher [AfxSocketSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) muss auftreten, bevor diese API verwendet werden kann.

- WSAENETDOWN Die Windows Sockets-Implementierung hat festgestellt, dass das Netzwerksubsystem ausgefallen ist.

- WSAEFAULT Das Argument *lpSockAddrLen* war ungültig: Der *puffer lpSockAddr* war zu klein, um die Peeradresse aufzunehmen.

- WSAEINPROGRESS Ein blockierender Windows Sockets-Vorgang wird ausgeführt.

- WSAEINVAL Der Socket wurde `Bind`nicht an gebunden.

- WSAENOTCONN Der Sockel ist nicht angeschlossen (nur SOCK_STREAM).

- WSAENOTSOCK Der Deskriptor ist kein Socket.

- WSAEOPNOTSUPP MSG_OOB angegeben wurde, aber der Socket ist nicht vom Typ SOCK_STREAM.

- WSAESHUTDOWN Der Socket wurde heruntergefahren; Es ist nicht `ReceiveFrom` möglich, einen `ShutDown` Socket aufzurufen, nachdem er aufgerufen wurde, wobei *nHow* auf 0 oder 2 gesetzt ist.

- WSAEWOULDBLOCK Der Socket ist als `ReceiveFrom` nicht blockierend markiert und der Vorgang würde blockieren.

- WSAEMSGSIZE Das Datagramm war zu groß, um in den angegebenen Puffer zu passen, und wurde abgeschnitten.

- WSAECONNABORTED Die virtuelle Verbindung wurde aufgrund eines Timeouts oder eines anderen Fehlers abgebrochen.

- WSAECONNRESET Die virtuelle Schaltung wurde von der entfernten Seite zurückgesetzt.

### <a name="remarks"></a>Bemerkungen

Diese Funktion wird verwendet, um eingehende Daten auf einem (möglicherweise verbundenen) Socket zu lesen und die Adresse zu erfassen, von der aus die Daten gesendet wurden.

Um IPv6-Adressen zu verarbeiten, verwenden Sie [CAsyncSocket::ReceiveFromEx](#receivefromex).

Bei Sockets vom Typ SOCK_STREAM werden so viele Informationen zurückgegeben, wie derzeit bis zur Größe des bereitgestellten Puffers verfügbar sind. Wenn der Socket für den Inline-Empfang von Out-of-Band-Daten konfiguriert wurde (Socketoption SO_OOBINLINE) und Out-of-Band-Daten ungelesen sind, werden nur Out-of-Band-Daten zurückgegeben. Die Anwendung kann `IOCtlSIOCATMARK` die `OnOutOfBandData` Option verwenden oder bestimmen, ob weitere Out-of-Band-Daten noch gelesen werden müssen. Die Parameter *lpSockAddr* und *lpSockAddrLen* werden für SOCK_STREAM Sockets ignoriert.

Bei Datagrammsockets werden die Daten aus dem ersten in die Warteschlange nustonten Datagramm bis zur Größe des bereitgestellten Puffers extrahiert. Wenn das Datagramm größer als der bereitgestellte Puffer ist, wird der Puffer mit dem `ReceiveFrom` ersten Teil der Nachricht gefüllt, die überschüssigen Daten gehen verloren und geben den Wert SOCKET_ERROR zurück, wobei der Fehlercode auf WSAEMSGSIZE festgelegt ist.

Wenn *lpSockAddr* ungleich Null ist und der Socket vom Typ SOCK_DGRAM ist, wird die Netzwerkadresse des Sockets, der die Daten gesendet hat, in die entsprechende [SOCKADDR-Struktur](/windows/win32/winsock/sockaddr-2) kopiert. Der von *lpSockAddrLen* hervorgehobene Wert wird auf die Größe dieser Struktur initialisiert und bei der Rückgabe geändert, um die tatsächliche Größe der dort gespeicherten Adresse anzugeben. Wenn keine eingehenden Daten am Socket `ReceiveFrom` verfügbar sind, wartet der Aufruf, bis Daten eintreffen, es sei denn, der Socket blockiert nicht. In diesem Fall wird der Wert SOCKET_ERROR zurückgegeben, wobei der Fehlercode auf WSAEWOULDBLOCK festgelegt ist. Der `OnReceive` Rückruf kann verwendet werden, um zu bestimmen, wann weitere Daten eintreffen.

Wenn der Socket vom Typ SOCK_STREAM ist und die Remoteseite `ReceiveFrom` die Verbindung ordnungsgemäß heruntergefahren hat, wird eine sofort mit 0 empfangenen Bytes abgeschlossen.

## <a name="casyncsocketreceivefromex"></a><a name="receivefromex"></a>CAsyncSocket::ReceiveFromEx

Rufen Sie diese Memberfunktion auf, um ein Datagramm zu empfangen und die Quelladresse in der [SOCKADDR-Struktur](/windows/win32/winsock/sockaddr-2) oder in *rSocketAddress* (handle IPv6-Adressen) zu speichern.

```
int ReceiveFromEx(
    void* lpBuf,
    int nBufLen,
    CString& rSocketAddress,
    UINT& rSocketPort,
    int nFlags = 0);
```

### <a name="parameters"></a>Parameter

*lpBuf*<br/>
Ein Puffer für die eingehenden Daten.

*nBufLen*<br/>
Die Länge von *lpBuf* in Bytes.

*rSocketAddress*<br/>
Verweis auf `CString` ein Objekt, das eine IP-Adresse mit gepunkteter Nummer empfängt.

*rSocketPort*<br/>
Verweis auf ein UINT, das einen Port speichert.

*nFlags*<br/>
Gibt die Art und Weise an, in der der Aufruf erfolgt. Die Semantik dieser Funktion wird durch die Socketoptionen und den Parameter *nFlags* bestimmt. Letzteres wird durch Kombinieren eines der folgenden Werte mit dem **C++-OR-Operator** erstellt:

- MSG_PEEK Blick auf die eingehenden Daten. Die Daten werden in den Puffer kopiert, aber nicht aus der Eingabewarteschlange entfernt.

- MSG_OOB Out-of-Band-Daten verarbeiten.

### <a name="return-value"></a>Rückgabewert

Wenn kein Fehler `ReceiveFromEx` auftritt, wird die Anzahl der empfangenen Bytes zurückgegeben. Wenn die Verbindung geschlossen wurde, wird 0 zurückgegeben. Andernfalls wird ein Wert von SOCKET_ERROR zurückgegeben, und ein `GetLastError`bestimmter Fehlercode kann durch Aufrufen abgerufen werden. Die folgenden Fehler gelten für diese Memberfunktion:

- WSANOTINITIALISED Ein erfolgreicher [AfxSocketSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) muss auftreten, bevor diese API verwendet werden kann.

- WSAENETDOWN Die Windows Sockets-Implementierung hat festgestellt, dass das Netzwerksubsystem ausgefallen ist.

- WSAEFAULT Das Argument *lpSockAddrLen* war ungültig: Der *puffer lpSockAddr* war zu klein, um die Peeradresse aufzunehmen.

- WSAEINPROGRESS Ein blockierender Windows Sockets-Vorgang wird ausgeführt.

- WSAEINVAL Der Socket wurde `Bind`nicht an gebunden.

- WSAENOTCONN Der Sockel ist nicht angeschlossen (nur SOCK_STREAM).

- WSAENOTSOCK Der Deskriptor ist kein Socket.

- WSAEOPNOTSUPP MSG_OOB angegeben wurde, aber der Socket ist nicht vom Typ SOCK_STREAM.

- WSAESHUTDOWN Der Socket wurde heruntergefahren; Es ist nicht `ReceiveFromEx` möglich, einen `ShutDown` Socket aufzurufen, nachdem er aufgerufen wurde, wobei *nHow* auf 0 oder 2 gesetzt ist.

- WSAEWOULDBLOCK Der Socket ist als `ReceiveFromEx` nicht blockierend markiert und der Vorgang würde blockieren.

- WSAEMSGSIZE Das Datagramm war zu groß, um in den angegebenen Puffer zu passen, und wurde abgeschnitten.

- WSAECONNABORTED Die virtuelle Verbindung wurde aufgrund eines Timeouts oder eines anderen Fehlers abgebrochen.

- WSAECONNRESET Die virtuelle Schaltung wurde von der entfernten Seite zurückgesetzt.

### <a name="remarks"></a>Bemerkungen

Diese Funktion wird verwendet, um eingehende Daten auf einem (möglicherweise verbundenen) Socket zu lesen und die Adresse zu erfassen, von der aus die Daten gesendet wurden.

Diese Funktion ist die gleiche wie [CAsyncSocket::ReceiveFrom,](#receivefrom) außer dass sie IPv6-Adressen sowie ältere Protokolle verarbeitet.

Bei Sockets vom Typ SOCK_STREAM werden so viele Informationen zurückgegeben, wie derzeit bis zur Größe des bereitgestellten Puffers verfügbar sind. Wenn der Socket für den Inline-Empfang von Out-of-Band-Daten konfiguriert wurde (Socketoption SO_OOBINLINE) und Out-of-Band-Daten ungelesen sind, werden nur Out-of-Band-Daten zurückgegeben. Die Anwendung kann `IOCtlSIOCATMARK` die `OnOutOfBandData` Option verwenden oder bestimmen, ob weitere Out-of-Band-Daten noch gelesen werden müssen. Die Parameter *lpSockAddr* und *lpSockAddrLen* werden für SOCK_STREAM Sockets ignoriert.

Bei Datagrammsockets werden die Daten aus dem ersten in die Warteschlange nustonten Datagramm bis zur Größe des bereitgestellten Puffers extrahiert. Wenn das Datagramm größer als der bereitgestellte Puffer ist, wird der Puffer mit dem `ReceiveFromEx` ersten Teil der Nachricht gefüllt, die überschüssigen Daten gehen verloren und geben den Wert SOCKET_ERROR zurück, wobei der Fehlercode auf WSAEMSGSIZE festgelegt ist.

Wenn *lpSockAddr* ungleich Null ist und der Socket vom Typ SOCK_DGRAM ist, wird die Netzwerkadresse des Sockets, der die Daten gesendet hat, in die entsprechende [SOCKADDR-Struktur](/windows/win32/winsock/sockaddr-2) kopiert. Der von *lpSockAddrLen* hervorgehobene Wert wird auf die Größe dieser Struktur initialisiert und bei der Rückgabe geändert, um die tatsächliche Größe der dort gespeicherten Adresse anzugeben. Wenn keine eingehenden Daten am Socket `ReceiveFromEx` verfügbar sind, wartet der Aufruf, bis Daten eintreffen, es sei denn, der Socket blockiert nicht. In diesem Fall wird der Wert SOCKET_ERROR zurückgegeben, wobei der Fehlercode auf WSAEWOULDBLOCK festgelegt ist. Der `OnReceive` Rückruf kann verwendet werden, um zu bestimmen, wann weitere Daten eintreffen.

Wenn der Socket vom Typ SOCK_STREAM ist und die Remoteseite `ReceiveFromEx` die Verbindung ordnungsgemäß heruntergefahren hat, wird eine sofort mit 0 empfangenen Bytes abgeschlossen.

## <a name="casyncsocketsend"></a><a name="send"></a>CAsyncSocket::Senden

Rufen Sie diese Memberfunktion auf, um Daten auf einem verbundenen Socket zu senden.

```
virtual int Send(
    const void* lpBuf,
    int nBufLen,
    int nFlags = 0);
```

### <a name="parameters"></a>Parameter

*lpBuf*<br/>
Ein Puffer, der die zu übertragenden Daten enthält.

*nBufLen*<br/>
Die Länge der Daten in *lpBuf* in Bytes.

*nFlags*<br/>
Gibt die Art und Weise an, in der der Aufruf erfolgt. Die Semantik dieser Funktion wird durch die Socketoptionen und den Parameter *nFlags* bestimmt. Letzteres wird durch Kombinieren eines der folgenden Werte mit dem **C++-OR-Operator** erstellt:

- MSG_DONTROUTE Gibt an, dass die Daten nicht dem Routing unterliegen sollen. Ein Windows Sockets-Lieferant kann dieses Flag ignorieren.

- MSG_OOB Ausbanddaten senden (nur SOCK_STREAM).

### <a name="return-value"></a>Rückgabewert

Wenn kein Fehler `Send` auftritt, wird die Gesamtzahl der gesendeten Zeichen zurückgegeben. (Beachten Sie, dass dies kleiner sein kann als die von *nBufLen*angegebene Zahl .) Andernfalls wird ein Wert von SOCKET_ERROR zurückgegeben, und ein bestimmter Fehlercode kann abgerufen werden, indem [GetLastError](#getlasterror)aufgerufen wird. Die folgenden Fehler gelten für diese Memberfunktion:

- WSANOTINITIALISED Ein erfolgreicher [AfxSocketSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) muss auftreten, bevor diese API verwendet werden kann.

- WSAENETDOWN Die Windows Sockets-Implementierung hat festgestellt, dass das Netzwerksubsystem ausgefallen ist.

- WSAEACCES Die angeforderte Adresse ist eine Broadcastadresse, aber das entsprechende Flag wurde nicht festgelegt.

- WSAEINPROGRESS Ein blockierender Windows Sockets-Vorgang wird ausgeführt.

- WSAEFAULT Das *argument lpBuf* befindet sich nicht in einem gültigen Teil des Benutzeradressraums.

- WSAENETRESET Die Verbindung muss zurückgesetzt werden, da sie von der Windows Sockets-Implementierung gelöscht wurde.

- WSAENOBUFS Die Windows Sockets-Implementierung meldet einen Pufferdeadlock.

- WSAENOTCONN Der Sockel ist nicht angeschlossen.

- WSAENOTSOCK Der Deskriptor ist kein Socket.

- WSAEOPNOTSUPP MSG_OOB angegeben wurde, aber der Socket ist nicht vom Typ SOCK_STREAM.

- WSAESHUTDOWN Der Socket wurde heruntergefahren; Es ist nicht `Send` möglich, einen `ShutDown` Socket aufzurufen, nachdem er aufgerufen wurde, wobei *nHow* auf 1 oder 2 gesetzt ist.

- WSAEWOULDBLOCK Der Socket ist als nicht blockierend markiert und der angeforderte Vorgang wird blockiert.

- WSAEMSGSIZE Der Socket ist vom Typ SOCK_DGRAM, und das Datagramm ist größer als das maximum, das von der Windows Sockets-Implementierung unterstützt wird.

- WSAEINVAL Der Socket wurde `Bind`nicht an gebunden.

- WSAECONNABORTED Die virtuelle Verbindung wurde aufgrund eines Timeouts oder eines anderen Fehlers abgebrochen.

- WSAECONNRESET Die virtuelle Schaltung wurde von der entfernten Seite zurückgesetzt.

### <a name="remarks"></a>Bemerkungen

`Send`wird verwendet, um ausgehende Daten auf verbundenen Stream- oder Datagrammsockets zu schreiben. Bei Datagrammsockets ist darauf zu achten, dass die maximale IP-Paketgröße der `iMaxUdpDg` zugrunde liegenden Subnetze nicht `AfxSocketInit`überschritten wird, die durch das Element in der [WSADATA-Struktur](/windows/win32/api/winsock2/ns-winsock2-wsadata) angegeben wird, das von zurückgegeben wird. Wenn die Daten zu lang sind, um das zugrunde liegende Protokoll atomar `GetLastError`zu durchlaufen, wird der Fehler WSAEMSGSIZE über zurückgegeben, und es werden keine Daten übertragen.

Beachten Sie, dass für einen Datagrammsocket der erfolgreiche Abschluss von a `Send` nicht darauf hinweist, dass die Daten erfolgreich übermittelt wurden.

Bei `CAsyncSocket` Objekten vom Typ SOCK_STREAM kann die Anzahl der geschriebenen Bytes zwischen 1 und der angeforderten Länge liegen, abhängig von der Pufferverfügbarkeit sowohl auf den lokalen als auch auf den ausländischen Hosts.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CAsyncSocket::OnSend](#onsend).

## <a name="casyncsocketsendto"></a><a name="sendto"></a>CAsyncSocket::SendTo

Rufen Sie diese Memberfunktion auf, um Daten an ein bestimmtes Ziel zu senden.

```
int SendTo(
    const void* lpBuf,
    int nBufLen,
    UINT nHostPort,
    LPCTSTR lpszHostAddress = NULL,
    int nFlags = 0);

int SendTo(
    const void* lpBuf,
    int nBufLen,
    const SOCKADDR* lpSockAddr,
    int nSockAddrLen,
    int nFlags = 0);
```

### <a name="parameters"></a>Parameter

*lpBuf*<br/>
Ein Puffer, der die zu übertragenden Daten enthält.

*nBufLen*<br/>
Die Länge der Daten in *lpBuf* in Bytes.

*nHostPort*<br/>
Der Port, der die Socketanwendung identifiziert.

*lpszHostAddress*<br/>
Die Netzwerkadresse des Sockets, mit dem dieses Objekt verbunden ist: ein Computername wie "ftp.microsoft.com" oder eine gepunktete Zahl wie "128.56.22.8".

*nFlags*<br/>
Gibt die Art und Weise an, in der der Aufruf erfolgt. Die Semantik dieser Funktion wird durch die Socketoptionen und den Parameter *nFlags* bestimmt. Letzteres wird durch Kombinieren eines der folgenden Werte mit dem **C++-OR-Operator** erstellt:

- MSG_DONTROUTE Gibt an, dass die Daten nicht dem Routing unterliegen sollen. Ein Windows Sockets-Lieferant kann dieses Flag ignorieren.

- MSG_OOB Ausbanddaten senden (nur SOCK_STREAM).

*lpSockAddr*<br/>
Ein Zeiger auf eine [SOCKADDR-Struktur,](/windows/win32/winsock/sockaddr-2) die die Adresse des Zielsockets enthält.

*nSockAddrLen*<br/>
Die Länge der Adresse in *lpSockAddr* in Bytes.

### <a name="return-value"></a>Rückgabewert

Wenn kein Fehler `SendTo` auftritt, wird die Gesamtzahl der gesendeten Zeichen zurückgegeben. (Beachten Sie, dass dies kleiner sein kann als die von *nBufLen*angegebene Zahl .) Andernfalls wird ein Wert von SOCKET_ERROR zurückgegeben, und ein bestimmter Fehlercode kann abgerufen werden, indem [GetLastError](#getlasterror)aufgerufen wird. Die folgenden Fehler gelten für diese Memberfunktion:

- WSANOTINITIALISED Ein erfolgreicher [AfxSocketSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) muss auftreten, bevor diese API verwendet werden kann.

- WSAENETDOWN Die Windows Sockets-Implementierung hat festgestellt, dass das Netzwerksubsystem ausgefallen ist.

- WSAEACCES Die angeforderte Adresse ist eine Broadcastadresse, aber das entsprechende Flag wurde nicht festgelegt.

- WSAEINPROGRESS Ein blockierender Windows Sockets-Vorgang wird ausgeführt.

- WSAEFAULT Die Parameter *lpBuf* oder *lpSockAddr* sind nicht Teil des Benutzeradressraums, oder das Argument *lpSockAddr* ist zu klein (kleiner als die Größe einer [SOCKADDR-Struktur).](/windows/win32/winsock/sockaddr-2)

- WSAEINVAL Der Hostname ist ungültig.

- WSAENETRESET Die Verbindung muss zurückgesetzt werden, da sie von der Windows Sockets-Implementierung gelöscht wurde.

- WSAENOBUFS Die Windows Sockets-Implementierung meldet einen Pufferdeadlock.

- WSAENOTCONN Der Sockel ist nicht angeschlossen (nur SOCK_STREAM).

- WSAENOTSOCK Der Deskriptor ist kein Socket.

- WSAEOPNOTSUPP MSG_OOB angegeben wurde, aber der Socket ist nicht vom Typ SOCK_STREAM.

- WSAESHUTDOWN Der Socket wurde heruntergefahren; Es ist nicht `SendTo` möglich, einen `ShutDown` Socket aufzurufen, nachdem er aufgerufen wurde, wobei *nHow* auf 1 oder 2 gesetzt ist.

- WSAEWOULDBLOCK Der Socket ist als nicht blockierend markiert und der angeforderte Vorgang wird blockiert.

- WSAEMSGSIZE Der Socket ist vom Typ SOCK_DGRAM, und das Datagramm ist größer als das maximum, das von der Windows Sockets-Implementierung unterstützt wird.

- WSAECONNABORTED Die virtuelle Verbindung wurde aufgrund eines Timeouts oder eines anderen Fehlers abgebrochen.

- WSAECONNRESET Die virtuelle Schaltung wurde von der entfernten Seite zurückgesetzt.

- WSAEADDRNOTAVAIL Die angegebene Adresse ist vom lokalen Computer nicht verfügbar.

- WSAEAFNOSUPPORT-Adressen in der angegebenen Familie können nicht mit diesem Socket verwendet werden.

- WSAEDESTADDRREQ Eine Zieladresse ist erforderlich.

- WSAENETUNREACH Das Netzwerk kann derzeit nicht von diesem Host aus erreicht werden.

### <a name="remarks"></a>Bemerkungen

`SendTo`wird auf Datagramm- oder Streamsockets verwendet und zum Schreiben ausgehender Daten auf einen Socket verwendet. Bei Datagrammsockets ist darauf zu achten, dass die maximale IP-Paketgröße der `iMaxUdpDg` zugrunde liegenden Subnetze nicht überschritten wird, die durch das Element in der [WSADATA-Struktur](/windows/win32/api/winsock2/ns-winsock2-wsadata) angegeben wird, das von [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)ausgefüllt wird. Wenn die Daten zu lang sind, um das zugrunde liegende Protokoll atomar zu durchlaufen, wird der Fehler WSAEMSGSIZE zurückgegeben, und es werden keine Daten übertragen.

Beachten Sie, dass `SendTo` der erfolgreiche Abschluss von a nicht darauf hinweist, dass die Daten erfolgreich übermittelt wurden.

`SendTo`wird nur auf einem SOCK_DGRAM Socket verwendet, um ein Datagramm an einen bestimmten Socket zu senden, der durch den Parameter *lpSockAddr* identifiziert wird.

Um eine Übertragung zu senden (nur auf einem SOCK_DGRAM), sollte die Adresse im Parameter *lpSockAddr* mit der speziellen IP-Adresse INADDR_BROADCAST (definiert in der Windows Sockets-Headerdatei WINSOCK) erstellt werden. H) zusammen mit der vorgesehenen Portnummer. Oder wenn der Parameter *lpszHostAddress* NULL ist, wird der Socket für Broadcast konfiguriert. Es ist im Allgemeinen nicht ratsam, dass ein Broadcast-Datagramm die Größe überschreitet, bei der eine Fragmentierung auftreten kann, was bedeutet, dass der Datenteil des Datagramms (ohne Header) 512 Bytes nicht überschreiten sollte.

Um IPv6-Adressen zu behandeln, verwenden Sie [CAsyncSocket::SendToEx](#sendtoex).

## <a name="casyncsocketsendtoex"></a><a name="sendtoex"></a>CAsyncSocket::SendToEx

Rufen Sie diese Memberfunktion auf, um Daten an ein bestimmtes Ziel zu senden (behandelt IPv6-Adressen).

```
int SendToEx(
    const void* lpBuf,
    int nBufLen,
    UINT nHostPort,
    LPCTSTR lpszHostAddress = NULL,
    int nFlags = 0);
```

### <a name="parameters"></a>Parameter

*lpBuf*<br/>
Ein Puffer, der die zu übertragenden Daten enthält.

*nBufLen*<br/>
Die Länge der Daten in *lpBuf* in Bytes.

*nHostPort*<br/>
Der Port, der die Socketanwendung identifiziert.

*lpszHostAddress*<br/>
Die Netzwerkadresse des Sockets, mit dem dieses Objekt verbunden ist: ein Computername wie "ftp.microsoft.com" oder eine gepunktete Zahl wie "128.56.22.8".

*nFlags*<br/>
Gibt die Art und Weise an, in der der Aufruf erfolgt. Die Semantik dieser Funktion wird durch die Socketoptionen und den Parameter *nFlags* bestimmt. Letzteres wird durch Kombinieren eines der folgenden Werte mit dem **C++-OR-Operator** erstellt:

- MSG_DONTROUTE Gibt an, dass die Daten nicht dem Routing unterliegen sollen. Ein Windows Sockets-Lieferant kann dieses Flag ignorieren.

- MSG_OOB Ausbanddaten senden (nur SOCK_STREAM).

### <a name="return-value"></a>Rückgabewert

Wenn kein Fehler `SendToEx` auftritt, wird die Gesamtzahl der gesendeten Zeichen zurückgegeben. (Beachten Sie, dass dies kleiner sein kann als die von *nBufLen*angegebene Zahl .) Andernfalls wird ein Wert von SOCKET_ERROR zurückgegeben, und ein bestimmter Fehlercode kann abgerufen werden, indem [GetLastError](#getlasterror)aufgerufen wird. Die folgenden Fehler gelten für diese Memberfunktion:

- WSANOTINITIALISED Ein erfolgreicher [AfxSocketSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) muss auftreten, bevor diese API verwendet werden kann.

- WSAENETDOWN Die Windows Sockets-Implementierung hat festgestellt, dass das Netzwerksubsystem ausgefallen ist.

- WSAEACCES Die angeforderte Adresse ist eine Broadcastadresse, aber das entsprechende Flag wurde nicht festgelegt.

- WSAEINPROGRESS Ein blockierender Windows Sockets-Vorgang wird ausgeführt.

- WSAEFAULT Die Parameter *lpBuf* oder *lpSockAddr* sind nicht Teil des Benutzeradressraums, oder das Argument *lpSockAddr* ist zu klein (kleiner als die Größe einer [SOCKADDR-Struktur).](/windows/win32/winsock/sockaddr-2)

- WSAEINVAL Der Hostname ist ungültig.

- WSAENETRESET Die Verbindung muss zurückgesetzt werden, da sie von der Windows Sockets-Implementierung gelöscht wurde.

- WSAENOBUFS Die Windows Sockets-Implementierung meldet einen Pufferdeadlock.

- WSAENOTCONN Der Sockel ist nicht angeschlossen (nur SOCK_STREAM).

- WSAENOTSOCK Der Deskriptor ist kein Socket.

- WSAEOPNOTSUPP MSG_OOB angegeben wurde, aber der Socket ist nicht vom Typ SOCK_STREAM.

- WSAESHUTDOWN Der Socket wurde heruntergefahren; Es ist nicht `SendToEx` möglich, einen `ShutDown` Socket aufzurufen, nachdem er aufgerufen wurde, wobei *nHow* auf 1 oder 2 gesetzt ist.

- WSAEWOULDBLOCK Der Socket ist als nicht blockierend markiert und der angeforderte Vorgang wird blockiert.

- WSAEMSGSIZE Der Socket ist vom Typ SOCK_DGRAM, und das Datagramm ist größer als das maximum, das von der Windows Sockets-Implementierung unterstützt wird.

- WSAECONNABORTED Die virtuelle Verbindung wurde aufgrund eines Timeouts oder eines anderen Fehlers abgebrochen.

- WSAECONNRESET Die virtuelle Schaltung wurde von der entfernten Seite zurückgesetzt.

- WSAEADDRNOTAVAIL Die angegebene Adresse ist vom lokalen Computer nicht verfügbar.

- WSAEAFNOSUPPORT-Adressen in der angegebenen Familie können nicht mit diesem Socket verwendet werden.

- WSAEDESTADDRREQ Eine Zieladresse ist erforderlich.

- WSAENETUNREACH Das Netzwerk kann derzeit nicht von diesem Host aus erreicht werden.

### <a name="remarks"></a>Bemerkungen

Diese Methode ist die gleiche wie [CAsyncSocket::SendTo,](#sendto) außer dass sie IPv6-Adressen sowie ältere Protokolle verarbeitet.

`SendToEx`wird auf Datagramm- oder Streamsockets verwendet und zum Schreiben ausgehender Daten auf einen Socket verwendet. Bei Datagrammsockets ist darauf zu achten, dass die maximale IP-Paketgröße der `iMaxUdpDg` zugrunde liegenden Subnetze nicht überschritten wird, die durch das Element in der [WSADATA-Struktur](/windows/win32/api/winsock2/ns-winsock2-wsadata) angegeben wird, das von [AfxSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit)ausgefüllt wird. Wenn die Daten zu lang sind, um das zugrunde liegende Protokoll atomar zu durchlaufen, wird der Fehler WSAEMSGSIZE zurückgegeben, und es werden keine Daten übertragen.

Beachten Sie, dass `SendToEx` der erfolgreiche Abschluss von a nicht darauf hinweist, dass die Daten erfolgreich übermittelt wurden.

`SendToEx`wird nur auf einem SOCK_DGRAM Socket verwendet, um ein Datagramm an einen bestimmten Socket zu senden, der durch den Parameter *lpSockAddr* identifiziert wird.

Um eine Übertragung zu senden (nur auf einem SOCK_DGRAM), sollte die Adresse im Parameter *lpSockAddr* mit der speziellen IP-Adresse INADDR_BROADCAST (definiert in der Windows Sockets-Headerdatei WINSOCK) erstellt werden. H) zusammen mit der vorgesehenen Portnummer. Oder wenn der Parameter *lpszHostAddress* NULL ist, wird der Socket für Broadcast konfiguriert. Es ist im Allgemeinen nicht ratsam, dass ein Broadcast-Datagramm die Größe überschreitet, bei der eine Fragmentierung auftreten kann, was bedeutet, dass der Datenteil des Datagramms (ohne Header) 512 Bytes nicht überschreiten sollte.

## <a name="casyncsocketsetsockopt"></a><a name="setsockopt"></a>CAsyncSocket::SetSockOpt

Rufen Sie diese Memberfunktion auf, um eine Socketoption festzulegen.

```
BOOL SetSockOpt(
    int nOptionName,
    const void* lpOptionValue,
    int nOptionLen,
    int nLevel = SOL_SOCKET);
```

### <a name="parameters"></a>Parameter

*nOptionName*<br/>
Die Socketoption, für die der Wert festgelegt werden soll.

*lpOptionValue*<br/>
Ein Zeiger auf den Puffer, in dem der Wert für die angeforderte Option angegeben wird.

*nOptionLen*<br/>
Die Größe des *lpOptionValue-Puffers* in Bytes.

*nLevel*<br/>
Die Ebene, auf der die Option definiert wird; die einzigen unterstützten Ebenen sind SOL_SOCKET und IPPROTO_TCP.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Funktion erfolgreich ist; Andernfalls 0, und ein bestimmter Fehlercode kann abgerufen werden, indem [GetLastError](#getlasterror)aufgerufen wird. Die folgenden Fehler gelten für diese Memberfunktion:

- WSANOTINITIALISED Ein erfolgreicher [AfxSocketSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) muss auftreten, bevor diese API verwendet werden kann.

- WSAENETDOWN Die Windows Sockets-Implementierung hat festgestellt, dass das Netzwerksubsystem ausgefallen ist.

- WSAEFAULT *lpOptionValue* befindet sich nicht in einem gültigen Teil des Prozessadressraums.

- WSAEINPROGRESS Ein blockierender Windows Sockets-Vorgang wird ausgeführt.

- WSAEINVAL *nLevel* ist ungültig, oder die Informationen in *lpOptionValue* sind ungültig.

- Das Zeitfürst für die WSAENETRESET-Verbindung ist abgelaufen, wenn SO_KEEPALIVE festgelegt ist.

- WSAENOPROTOOPT Die Option ist unbekannt oder wird nicht unterstützt. Insbesondere wird SO_BROADCAST für Sockets vom Typ SOCK_STREAM nicht unterstützt, während SO_DONTLINGER, SO_KEEPALIVE, SO_LINGER und SO_OOBINLINE auf Sockets vom Typ SOCK_DGRAM nicht unterstützt werden.

- DIE WSAENOTCONN-Verbindung wurde zurückgesetzt, wenn SO_KEEPALIVE gesetzt ist.

- WSAENOTSOCK Der Deskriptor ist kein Socket.

### <a name="remarks"></a>Bemerkungen

`SetSockOpt`legt den aktuellen Wert für eine Socketoption fest, die einem Socket eines beliebigen Typs in einem beliebigen Zustand zugeordnet ist. Obwohl Optionen auf mehreren Protokollebenen vorhanden sein können, definiert diese Spezifikation nur Optionen, die auf der obersten "Socket"-Ebene vorhanden sind. Optionen wirken sich auf Socketvorgänge aus, z. B. ob beschleunigte Daten im normalen Datenstrom empfangen werden, ob Broadcastnachrichten auf dem Socket gesendet werden können usw.

Es gibt zwei Arten von Socketoptionen: boolesche Optionen, die ein Feature oder Verhalten aktivieren oder deaktivieren, und Optionen, die einen ganzzahligen Wert oder eine ganze Reihe erfordern. Um eine boolesche Option zu aktivieren, zeigt *lpOptionValue* auf eine ganzzahlige Zahl ungleich Null. Um die Option zu deaktivieren, zeigt *lpOptionValue* auf eine ganze Zahl gleich Null. *nOptionLen* sollte `sizeof(BOOL)` für boolesche Optionen gleich sein. Bei anderen Optionen zeigt *lpOptionValue* auf die ganze Zahl oder Struktur, die den gewünschten Wert für die Option enthält, und *nOptionLen* ist die Länge der ganzzahligen oder strukturierten Struktur.

SO_LINGER steuert die Aktion, die ausgeführt wird, wenn `Close` nicht gesendete Daten in die Warteschlange eines Sockets gestellt werden und die Funktion aufgerufen wird, um den Socket zu schließen.

Standardmäßig kann ein Socket nicht an eine lokale Adresse gebunden werden (siehe [Binden](#bind)), die bereits verwendet wird. Gelegentlich kann es jedoch wünschenswert sein, eine Adresse auf diese Weise "wiederzuverwenden". Da jede Verbindung durch die Kombination von lokalen und Remoteadressen eindeutig identifiziert wird, ist es kein Problem, dass zwei Sockets an dieselbe lokale Adresse gebunden sind, solange die Remoteadressen unterschiedlich sind.

Um die Windows Sockets-Implementierung darüber zu informieren, dass ein `Bind` Aufruf eines Sockets nicht unzulässig sein sollte, da die gewünschte `Bind` Adresse bereits von einem anderen Socket verwendet wird, sollte die Anwendung die SO_REUSEADDR Socketoption für den Socket festlegen, bevor der Aufruf ausgegeben wird. Beachten Sie, dass die Option nur `Bind` zum Zeitpunkt des Aufrufs interpretiert wird: Es ist daher unnötig (aber harmlos), die Option auf einem `Bind` Socket festzulegen, der nicht an eine vorhandene Adresse gebunden werden soll, und das Festlegen oder Zurücksetzen der Option nach dem Aufruf hat keine Auswirkungen auf diesen oder einen anderen Socket.

Eine Anwendung kann anfordern, dass die Windows Sockets-Implementierung die Verwendung von "Keep-alive"-Paketen in TCP-Verbindungen (Transmission Control Protocol) aktiviert, indem die SO_KEEPALIVE Socketoption aktiviert wird. Eine Windows Sockets-Implementierung muss die Verwendung von Keep-alives nicht unterstützen: Wenn dies der Fall ist, ist die genaue Semantik implementierungsspezifisch, sollte aber Abschnitt 4.2.3.6 von RFC 1122: "Anforderungen für Internethosts – Kommunikationsebenen" entsprechen. Wenn eine Verbindung als Ergebnis von "keep-alives" abgebrochen wird, wird der Fehlercode WSAENETRESET an alle laufenden Aufrufe auf dem Socket zurückgegeben, und alle nachfolgenden Aufrufe schlagen mit WSAENOTCONN fehl.

Die Option TCP_NODELAY deaktiviert den Nagle-Algorithmus. Der Nagle-Algorithmus wird verwendet, um die Anzahl der kleinen Pakete zu reduzieren, die von einem Host gesendet werden, indem nicht bestätigte Sendedaten gepuffert werden, bis ein Paket in voller Größe gesendet werden kann. Für einige Anwendungen kann dieser Algorithmus jedoch die Leistung beeinträchtigen, und TCP_NODELAY kann verwendet werden, um ihn auszuschalten. Anwendungsautoren sollten TCP_NODELAY nicht festlegen, es sei denn, die Auswirkungen sind gut verstanden und erwünscht, da die Einstellung TCP_NODELAY erhebliche negative Auswirkungen auf die Netzwerkleistung haben kann. TCP_NODELAY ist die einzige unterstützte Socketoption, die Level-IPPROTO_TCP verwendet. Alle anderen Optionen verwenden Ebene SOL_SOCKET.

Einige Implementierungen von Windows Sockets liefern Ausgabedebuginformationen, wenn die Option SO_DEBUG von einer Anwendung festgelegt wird.

Die folgenden Optionen `SetSockOpt`werden für unterstützt. Der Typ identifiziert den Datentyp, der von *lpOptionValue*adressiert wird.

|Wert|type|Bedeutung|
|-----------|----------|-------------|
|SO_BROADCAST|BOOL|Die Übertragung von Broadcast-Nachrichten auf dem Sockel zulassen.|
|SO_DEBUG|BOOL|Zeichnet Debuginformationen auf.|
|SO_DONTLINGER|BOOL|Blockieren `Close` Sie nicht das Warten auf das Senden nicht gesendeter Daten. Das Festlegen dieser Option entspricht `l_onoff` dem Festlegen SO_LINGER mit einem Satz auf Null.|
|SO_DONTROUTE|BOOL|Nicht weiterleiten: Direkt an schnittstelle senden.|
|SO_KEEPALIVE|BOOL|Senden Sie Keep-alives.|
|SO_LINGER|`struct LINGER`|Linger `Close` on, wenn nicht gesendete Daten vorhanden sind.|
|SO_OOBINLINE|BOOL|Empfangen von Out-of-Band-Daten im normalen Datenstrom.|
|SO_RCVBUF|**int**|Geben Sie die Puffergröße für Empfangen an.|
|SO_REUSEADDR|BOOL|Lassen Sie zu, dass der Socket an eine Adresse gebunden wird, die bereits verwendet wird. (Siehe [Bind](#bind).)|
|SO_SNDBUF|**int**|Geben Sie die Puffergröße für Sendesendet an.|
|TCP_NODELAY|BOOL|Deaktiviert den Nagle-Algorithmus für Sammelsendungen.|

Berkeley Software Distribution (BSD)-Optionen werden nicht unterstützt: `SetSockOpt`

|Wert|type|Bedeutung|
|-----------|----------|-------------|
|SO_ACCEPTCONN|BOOL|Sockel hört zu|
|SO_ERROR|**int**|Erhalten Sie den Fehlerstatus und löschen Sie.|
|SO_RCVLOWAT|**int**|Erhalten Sie niedrige Wassermark.|
|SO_RCVTIMEO|**int**|Empfangstimeout|
|SO_SNDLOWAT|**int**|Senden Sie niedrige Wassermarke.|
|SO_SNDTIMEO|**int**|Zeitout senden.|
|SO_TYPE|**int**|Typ des Sockets.|
|IP_OPTIONS||Festlegen des Optionsfelds im IP-Header.|

## <a name="casyncsocketshutdown"></a><a name="shutdown"></a>CAsyncSocket::ShutDown

Rufen Sie diese Memberfunktion auf, um Sendet, Empfängt oder beides auf dem Socket zu deaktivieren.

```
BOOL ShutDown(int nHow = sends);
```

### <a name="parameters"></a>Parameter

*Nhow*<br/>
Ein Flag, das beschreibt, welche Arten von Vorgangsvorgang nicht mehr zulässig sind, mit den folgenden aufgezählten Werten:

- **erhält = 0**

- **sendet = 1**

- **beide = 2**

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Funktion erfolgreich ist; Andernfalls 0, und ein bestimmter Fehlercode kann abgerufen werden, indem [GetLastError](#getlasterror)aufgerufen wird. Die folgenden Fehler gelten für diese Memberfunktion:

- WSANOTINITIALISED Ein erfolgreicher [AfxSocketSocketInit](../../mfc/reference/application-information-and-management.md#afxsocketinit) muss auftreten, bevor diese API verwendet werden kann.

- WSAENETDOWN Die Windows Sockets-Implementierung hat festgestellt, dass das Netzwerksubsystem ausgefallen ist.

- WSAEINVAL *nHow* ist ungültig.

- WSAEINPROGRESS Ein blockierender Windows Sockets-Vorgang wird ausgeführt.

- WSAENOTCONN Der Sockel ist nicht angeschlossen (nur SOCK_STREAM).

- WSAENOTSOCK Der Deskriptor ist kein Socket.

### <a name="remarks"></a>Bemerkungen

`ShutDown`wird auf allen Sockettypen verwendet, um Empfang, Übertragung oder beides zu deaktivieren. Wenn *nHow* 0 ist, werden nachfolgende Empfängt auf dem Socket nicht zulässig sein. Dies hat keine Auswirkungen auf die unteren Protokollebenen.

Bei Tcp (Transmission Control Protocol) wird das TCP-Fenster nicht geändert, und eingehende Daten werden akzeptiert (aber nicht bestätigt), bis das Fenster erschöpft ist. Für User Datagram Protocol (UDP) werden eingehende Datagramme akzeptiert und in die Warteschlange gestellt. In keinem Fall wird ein ICMP-Fehlerpaket generiert. Wenn *nHow* 1 ist, werden nachfolgende Sendungen nicht zulässig. Bei TCP-Sockets wird eine FIN gesendet. Das Festlegen *von nWie* auf 2 deaktiviert sowohl Sende- als auch -empfängt wie oben beschrieben.

Beachten `ShutDown` Sie, dass der Socket nicht geschlossen wird und `Close` die an den Socket angeschlossenen Ressourcen erst freigegeben werden, wenn sie aufgerufen werden. Eine Anwendung sollte sich nicht darauf verlassen, dass sie einen Socket wiederverwenden kann, nachdem er heruntergefahren wurde. Insbesondere ist eine Windows Sockets-Implementierung nicht erforderlich, um die Verwendung auf `Connect` einem solchen Socket zu unterstützen.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CAsyncSocket::OnReceive](#onreceive).

## <a name="casyncsocketsocket"></a><a name="socket"></a>CASyncSocket::Socket

Ordnet ein Sockethandle zu.

```
BOOL Socket(
    int nSocketType = SOCK_STREAM,
    long lEvent = FD_READ | FD_WRITE | FD_OOB | FD_ACCEPT | FD_CONNECT | FD_CLOSE,
    int nProtocolType = 0,
    int nAddressFormat = PF_INET);
```

### <a name="parameters"></a>Parameter

*nSocketType*<br/>
Gibt `SOCK_STREAM` an `SOCK_DGRAM`oder .

*lEvent*<br/>
Eine Bitmaske, die eine Kombination von Netzwerkereignissen angibt, an denen die Anwendung interessiert ist.

- `FD_READ`: Möchten Sie eine Benachrichtigung über die Lesebereitschaft erhalten.

- `FD_WRITE`: Möchten Sie eine Benachrichtigung über die Schreibbereitschaft erhalten.

- `FD_OOB`: Möchten Sie eine Benachrichtigung über das Eintreffen von Out-of-Band-Daten erhalten.

- `FD_ACCEPT`: Möchten Sie eine Benachrichtigung über eingehende Verbindungen erhalten.

- `FD_CONNECT`: Möchten Sie eine Benachrichtigung über die abgeschlossene Verbindung erhalten.

- `FD_CLOSE`: Möchten Sie eine Benachrichtigung über den Socket-Verschluss erhalten.

*nProtocolType*<br/>
Protokoll, das mit dem Socket verwendet werden soll, der für die angegebene Adressfamilie spezifisch ist.

*nAddressFormat*<br/>
Adressfamilienspezifikation.

### <a name="return-value"></a>Rückgabewert

Gibt `TRUE` bei Erfolg bzw. `FALSE` bei einem Fehler zurück.

### <a name="remarks"></a>Bemerkungen

Diese Methode weist ein Sockethandle zu. [CAsyncSocket::Bind](#bind) wird nicht aufrufen, um den Socket an eine `Bind` angegebene Adresse zu binden, daher müssen Sie später aufrufen, um den Socket an eine angegebene Adresse zu binden. Sie können [CAsyncSocket::SetSockOpt](#setsockopt) verwenden, um die Socketoption festzulegen, bevor sie gebunden wird.

## <a name="see-also"></a>Siehe auch

[CObject-Klasse](../../mfc/reference/cobject-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CSocket-Klasse](../../mfc/reference/csocket-class.md)<br/>
[CSocketFile-Klasse](../../mfc/reference/csocketfile-class.md)
