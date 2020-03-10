---
title: CSocket-Klasse
ms.date: 11/04/2016
f1_keywords:
- CSocket
- AFXSOCK/CSocket
- AFXSOCK/CSocket::CSocket
- AFXSOCK/CSocket::Attach
- AFXSOCK/CSocket::CancelBlockingCall
- AFXSOCK/CSocket::Create
- AFXSOCK/CSocket::FromHandle
- AFXSOCK/CSocket::IsBlocking
- AFXSOCK/CSocket::OnMessagePending
helpviewer_keywords:
- CSocket [MFC], CSocket
- CSocket [MFC], Attach
- CSocket [MFC], CancelBlockingCall
- CSocket [MFC], Create
- CSocket [MFC], FromHandle
- CSocket [MFC], IsBlocking
- CSocket [MFC], OnMessagePending
ms.assetid: 7f23c081-d24d-42e3-b511-8053ca53d729
ms.openlocfilehash: a861e557b7368d13d615aaf796faded93c72b040
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78854548"
---
# <a name="csocket-class"></a>CSocket-Klasse

Wird von `CAsyncSocket`abgeleitet, erbt seine Kapselung der Windows Sockets-API und stellt eine höhere Abstraktions Ebene dar als die eines `CAsyncSocket` Objekts.

## <a name="syntax"></a>Syntax

```
class CSocket : public CAsyncSocket
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CSocket:: CSocket](#csocket)|Erstellt ein `CSocket`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CSocket:: Attach](#attach)|Fügt ein Sockethandle an ein `CSocket` Objekt an.|
|[CSocket:: cancelblockingstatement](#cancelblockingcall)|Bricht einen blockierenden-Befehl ab, der gerade ausgeführt wird.|
|[CSocket:: Create](#create)|Erstellt einen Socket.|
|[CSocket:: FromHandle](#fromhandle)|Gibt einen Zeiger auf ein `CSocket` Objekt zurück, wenn ein Sockethandle angegeben ist.|
|[CSocket:: isblocking](#isblocking)|Bestimmt, ob ein blockierender-Vorgang ausgeführt wird.|

### <a name="protected-methods"></a>Geschützte Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CSocket:: OnMessagePending](#onmessagepending)|Wird aufgerufen, um ausstehende Meldungen beim Warten auf den Abschluss eines blockierenden Aufrufs zu verarbeiten.|

## <a name="remarks"></a>Bemerkungen

`CSocket` funktioniert mit Klassen `CSocketFile` und `CArchive`, um das Senden und empfangen von Daten zu verwalten.

Ein `CSocket`-Objekt stellt auch Blockierungen bereit, die für den synchronen Betrieb von `CArchive`unverzichtbar sind. Blockierende Funktionen, wie z. b. `Receive`, `Send`, `ReceiveFrom`, `SendTo`und `Accept` (alle von `CAsyncSocket`geerbt), geben keinen `WSAEWOULDBLOCK` Fehler in `CSocket`zurück. Stattdessen warten diese Funktionen, bis der Vorgang abgeschlossen ist. Außerdem wird der ursprüngliche Aufruf mit dem Fehler "WSAEINTR" beendet, wenn `CancelBlockingCall` aufgerufen wird, während eine dieser Funktionen blockiert wird.

Um ein `CSocket` Objekt zu verwenden, rufen Sie den-Konstruktor auf, und rufen Sie dann `Create` auf, um das zugrunde liegende Sockethandle (Type Socket) Die Standardparameter `Create` erstellen einen Streamsocket, aber wenn Sie den Socket nicht mit einem `CArchive`-Objekt verwenden, können Sie einen Parameter angeben, um stattdessen einen Datagramm-Socket zu erstellen, oder eine Bindung an einen bestimmten Port erstellen, um einen Serversocket zu erstellen. Stellen Sie eine Verbindung mit einem Clientsocket her, indem Sie `Connect` auf der Clientseite verwenden und auf der Serverseite `Accept`. Erstellen Sie dann ein `CSocketFile` Objekt, und ordnen Sie es dem `CSocket`-Objekt im `CSocketFile`-Konstruktor zu. Erstellen Sie als nächstes ein `CArchive` Objekt zum Senden und eines zum Empfangen von Daten (bei Bedarf), und ordnen Sie diese dann dem `CSocketFile`-Objekt im `CArchive`-Konstruktor zu. Wenn die Kommunikation beendet ist, zerstören Sie die Objekte `CArchive`, `CSocketFile`und `CSocket`. Der Socket-Datentyp wird im Artikel [Windows Sockets: Hintergrund](../../mfc/windows-sockets-background.md)beschrieben.

Wenn Sie `CArchive` mit `CSocketFile` und `CSocket`verwenden, tritt möglicherweise eine Situation auf, in der `CSocket::Receive` in eine Schleife wechselt (`PumpMessages(FD_READ)`), die auf die angeforderte Byte Menge wartet. Dies liegt daran, dass Windows Sockets pro FD_READ Benachrichtigung nur einen empfangener-Aufruf zulässt, `CSocketFile` und `CSocket` mehrere empfangener-Aufrufe pro FD_READ zulassen. Wenn Sie eine FD_READ erhalten, wenn keine zu lesenden Daten vorhanden sind, ist die Anwendung nicht mehr vorhanden. Wenn Sie nie eine andere FD_READ erhalten, hält die Anwendung keine Verbindung mehr über den Socket.

Sie können dieses Problem wie folgt beheben. Geben Sie in der `OnReceive`-Methode der Socket-Klasse `CAsyncSocket::IOCtl(FIONREAD, ...)` ein, bevor Sie die `Serialize`-Methode der Message-Klasse aufzurufen, wenn die erwarteten Daten, die vom Socket gelesen werden sollen, die Größe eines TCP-Pakets überschreiten (maximale Übertragungseinheit des Netzwerk Mediums, normalerweise mindestens 1096 Bytes). Wenn die Größe der verfügbaren Daten geringer als benötigt ist, warten Sie, bis alle Daten empfangen wurden, und starten Sie dann den Lesevorgang.

Im folgenden Beispiel ist `m_dwExpected` die ungefähre Anzahl von Bytes, die der Benutzer erwartet. Es wird davon ausgegangen, dass Sie es an anderer Stelle im Code deklarieren.

[!code-cpp[NVC_MFCSocketThread#4](../../mfc/reference/codesnippet/cpp/csocket-class_1.cpp)]

> [!NOTE]
>  Wenn Sie MFC-Sockets in sekundären Threads in einer statisch verknüpften MFC-Anwendung verwenden, müssen Sie `AfxSocketInit` in jedem Thread, der Sockets verwendet, zum Initialisieren der Socket-Bibliotheken verwenden. Standardmäßig wird `AfxSocketInit` nur im primären Thread aufgerufen.

Weitere Informationen finden Sie unter [Windows Sockets in MFC](../../mfc/windows-sockets-in-mfc.md), [Windows Sockets: Verwenden von Sockets mit Archiven](../../mfc/windows-sockets-using-sockets-with-archives.md), [Windows Sockets: wie Sockets mit Archiven funktionieren](../../mfc/windows-sockets-how-sockets-with-archives-work.md), [Windows Sockets: Sequenz von Vorgängen](../../mfc/windows-sockets-sequence-of-operations.md), [Windows Sockets: Beispiel für Sockets mithilfe von Archiven](../../mfc/windows-sockets-example-of-sockets-using-archives.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)

[CAsyncSocket](../../mfc/reference/casyncsocket-class.md)

`CSocket`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** AfxSock. h

##  <a name="attach"></a>CSocket:: Attach

Mit dieser Member-Funktion können Sie das `hSocket` Handle an ein `CSocket` Objekt anfügen.

```
BOOL Attach(SOCKET hSocket);
```

### <a name="parameters"></a>Parameter

*hsocket*<br/>
Enthält ein Handle für einen Socket.

### <a name="return-value"></a>Rückgabewert

Ungleich null, wenn die Funktion erfolgreich ist.

### <a name="remarks"></a>Bemerkungen

Das Sockethandle wird im [m_hSocket](../../mfc/reference/casyncsocket-class.md#m_hsocket) Datenmember des Objekts gespeichert.

Weitere Informationen finden Sie unter [Windows Sockets: Verwenden von Sockets mit Archiven](../../mfc/windows-sockets-using-sockets-with-archives.md).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCSocketThread#1](../../mfc/reference/codesnippet/cpp/csocket-class_2.h)]

[!code-cpp[NVC_MFCSocketThread#2](../../mfc/reference/codesnippet/cpp/csocket-class_3.cpp)]

[!code-cpp[NVC_MFCSocketThread#3](../../mfc/reference/codesnippet/cpp/csocket-class_4.cpp)]

##  <a name="cancelblockingcall"></a>CSocket:: cancelblockingstatement

Rufen Sie diese Member-Funktion auf, um einen derzeit ausgeführten blockierenden aufzurufen.

```
void CancelBlockingCall();
```

### <a name="remarks"></a>Bemerkungen

Diese Funktion bricht alle ausstehenden Blockierungs Vorgänge für diesen Socket ab. Der ursprüngliche blockierende-Aufrufvorgang wird so bald wie möglich mit dem Fehler "WSAEINTR" beendet.

Bei einem blockierenden `Connect` Vorgang wird der blockierende Befehl von der Windows Sockets-Implementierung so bald wie möglich beendet, aber möglicherweise ist es nicht möglich, dass die socketressourcen freigegeben werden, bis die Verbindung abgeschlossen (und dann zurückgesetzt) oder ein Timeout aufgetreten ist. Dies ist wahrscheinlich nur dann spürbar, wenn die Anwendung sofort versucht, einen neuen Socket zu öffnen (wenn keine Sockets verfügbar sind) oder eine Verbindung mit dem gleichen Peer herzustellen.

Wenn Sie einen anderen Vorgang als `Accept` abbrechen, kann der Socket in einem unbestimmten Zustand belassen werden. Wenn eine Anwendung einen blockierenden Vorgang für einen Socket abbricht, ist der einzige Vorgang, von dem die Anwendung abhängig sein kann, von der Möglichkeit, auf dem Socket auszuführen, ein Aufruf von `Close`, obwohl andere Vorgänge möglicherweise für einige Windows Sockets-Implementierungen funktionieren. Wenn Sie für Ihre Anwendung eine maximale Portabilität wünschen, müssen Sie darauf achten, dass Sie nach einem Abbruch nicht auf die Ausführung von Vorgängen angewiesen sind.

Weitere Informationen finden Sie unter [Windows Sockets: Verwenden von Sockets mit Archiven](../../mfc/windows-sockets-using-sockets-with-archives.md).

##  <a name="create"></a>CSocket:: Create

Rufen Sie die **Create** Member-Funktion nach dem Erstellen eines Socket-Objekts auf, um den Windows-Socket zu erstellen und anzufügen.

```
BOOL Create(
    UINT nSocketPort = 0,
    int nSocketType = SOCK_STREAM,
    LPCTSTR lpszSocketAddress = NULL);
```

### <a name="parameters"></a>Parameter

*nsocketport*<br/>
Ein bestimmter Port, der mit dem Socket verwendet werden soll, oder 0, wenn MFC einen Port auswählen soll.

*nsockettype*<br/>
SOCK_STREAM oder SOCK_DGRAM.

*lpszsocketaddress*<br/>
Ein Zeiger auf eine Zeichenfolge, die die Netzwerkadresse des verbundenen Sockets enthält, eine gepunktete Zahl wie z. b. "128.56.22.8". Durch das übergeben der NULL-Zeichenfolge für diesen Parameter wird angegeben, dass die `CSocket` Instanz auf allen Netzwerkschnittstellen auf Client Aktivitäten lauschen soll.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn die Funktion erfolgreich ist. Andernfalls kann der Wert 0 und ein bestimmter Fehlercode durch Aufrufen von `GetLastError`abgerufen werden.

### <a name="remarks"></a>Bemerkungen

`Create` dann `Bind` aufrufen, um den Socket an die angegebene Adresse zu binden. Die folgenden sockettypen werden unterstützt:

- SOCK_STREAM stellt sequenzierte, zuverlässige, bidirektionale, Verbindungs basierte Bytestreams bereit. Verwendet das Transmission Control Protocol (TCP) für die Internet Adressfamilie.

- SOCK_DGRAM unterstützt Datagramme, bei denen es sich um verbindungslose, unzuverlässige Puffer mit einer festgelegten (normalerweise kleinen) maximalen Länge handelt. Verwendet UDP (User Datagram Protocol) für die Internet Adressfamilie. Wenn Sie diese Option verwenden möchten, dürfen Sie den Socket nicht mit einem `CArchive`-Objekt verwenden.

    > [!NOTE]
    >  Die `Accept` Member-Funktion nimmt einen Verweis auf ein neues, leeres `CSocket`-Objekt als Parameter auf. Sie müssen dieses Objekt erstellen, bevor Sie `Accept`abrufen. Beachten Sie, dass die Verbindung geschlossen wird, wenn dieses Socketobjekt den Gültigkeitsbereich verlässt. `Create` für dieses neue Socketobjekt nicht aufzurufen.

Weitere Informationen zu Stream-und Datagramm-Sockets finden Sie in den Artikeln [Windows Sockets: Hintergrund](../../mfc/windows-sockets-background.md), [Windows Sockets: Ports und Socketadressen](../../mfc/windows-sockets-ports-and-socket-addresses.md)und [Windows Sockets: Verwenden von Sockets mit Archiven](../../mfc/windows-sockets-using-sockets-with-archives.md).

##  <a name="csocket"></a>CSocket:: CSocket

Erstellt ein `CSocket`-Objekt.

```
CSocket();
```

### <a name="remarks"></a>Bemerkungen

Nach der Erstellung müssen Sie die `Create` Member-Funktion aufzurufen.

Weitere Informationen finden Sie unter [Windows Sockets: Verwenden von Sockets mit Archiven](../../mfc/windows-sockets-using-sockets-with-archives.md).

##  <a name="fromhandle"></a>CSocket:: FromHandle

Gibt einen Zeiger auf ein `CSocket`-Objekt zurück.

```
static CSocket* PASCAL FromHandle(SOCKET hSocket);
```

### <a name="parameters"></a>Parameter

*hsocket*<br/>
Enthält ein Handle für einen Socket.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf ein `CSocket` Objekt oder NULL, wenn kein `CSocket` Objekt an *hsocket*angeschlossen ist.

### <a name="remarks"></a>Bemerkungen

Wenn ein Sockethandle einem `CSocket` Objekt nicht an das Handle angefügt ist, gibt die Member-Funktion NULL zurück und erstellt kein temporäres Objekt.

Weitere Informationen finden Sie unter [Windows Sockets: Verwenden von Sockets mit Archiven](../../mfc/windows-sockets-using-sockets-with-archives.md).

##  <a name="isblocking"></a>CSocket:: isblocking

Mit dieser Member-Funktion können Sie ermitteln, ob ein blockierender-Vorgang ausgeführt wird.

```
BOOL IsBlocking();
```

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn der Socket blockiert wird. andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [Windows Sockets: Verwenden von Sockets mit Archiven](../../mfc/windows-sockets-using-sockets-with-archives.md).

##  <a name="onmessagepending"></a>CSocket:: OnMessagePending

Überschreiben Sie diese Member-Funktion, um nach bestimmten Nachrichten von Windows zu suchen und in Ihrem Socket darauf zu reagieren.

```
virtual BOOL OnMessagePending();
```

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn die Meldung behandelt wurde. andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Hierbei handelt es sich um eine erweiterte über schreibbare.

Das Framework ruft `OnMessagePending` auf, während der Socket Windows-Nachrichten pumpt, um Ihnen die Möglichkeit zu geben, relevante Nachrichten für Ihre Anwendung zu behandeln. Beispiele für die Verwendung von `OnMessagePending`finden Sie im Artikel [Windows Sockets: Ableiten von Socketklassen](../../mfc/windows-sockets-deriving-from-socket-classes.md).

Weitere Informationen finden Sie unter [Windows Sockets: Verwenden von Sockets mit Archiven](../../mfc/windows-sockets-using-sockets-with-archives.md).

## <a name="see-also"></a>Weitere Informationen

[CAsyncSocket-Klasse](../../mfc/reference/casyncsocket-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CAsyncSocket-Klasse](../../mfc/reference/casyncsocket-class.md)<br/>
[CSocketFile-Klasse](../../mfc/reference/csocketfile-class.md)
