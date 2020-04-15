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
ms.openlocfilehash: 3f0a7a9a90250ede7b112cfbd9bc1ca14d583356
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318193"
---
# <a name="csocket-class"></a>CSocket-Klasse

Leitet von `CAsyncSocket`ab , erbt seine Kapselung der Windows Sockets-API und stellt eine höhere `CAsyncSocket` Abstraktionsebene als die eines Objekts dar.

## <a name="syntax"></a>Syntax

```
class CSocket : public CAsyncSocket
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CSocket::CSocket](#csocket)|Erstellt ein `CSocket`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CSocket::Attach](#attach)|Fügt ein SOCKET-Handle `CSocket` an ein Objekt an.|
|[CSocket::CancelBlockingCall](#cancelblockingcall)|Bricht einen blockierenden Anruf ab, der gerade ausgeführt wird.|
|[CSocket::Erstellen](#create)|Erstellt einen Socket.|
|[CSocket::FromHandle](#fromhandle)|Gibt einen Zeiger `CSocket` auf ein Objekt mit einem SOCKET-Handle zurück.|
|[CSocket::IsBlocking](#isblocking)|Bestimmt, ob ein blockierender Aufruf ausgeführt wird.|

### <a name="protected-methods"></a>Geschützte Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CSocket::OnMessagePending](#onmessagepending)|Aufgerufen, um ausstehende Nachrichten zu verarbeiten, während auf den Abschluss eines blockierenden Aufrufs gewartet wird.|

## <a name="remarks"></a>Bemerkungen

`CSocket`arbeitet mit `CSocketFile` `CArchive` Klassen und verwaltet das Senden und Empfangen von Daten.

Ein `CSocket` Objekt bietet auch eine Blockierung, die `CArchive`für den synchronen Betrieb von von unerlässlich ist. Blockierende Funktionen, `Receive` `Send`z. `SendTo`B. , , `CAsyncSocket` `ReceiveFrom`, und `Accept` `WSAEWOULDBLOCK` (alle von geerbt), geben keinen Fehler in `CSocket`zurück. Stattdessen warten diese Funktionen, bis der Vorgang abgeschlossen ist. Darüber hinaus wird der ursprüngliche Aufruf mit dem `CancelBlockingCall` Fehler WSAEINTR beendet, wenn er aufgerufen wird, während eine dieser Funktionen blockiert wird.

Um ein `CSocket` Objekt zu verwenden, rufen `Create` Sie den Konstruktor auf und rufen Sie dann auf, um das zugrunde liegende SOCKET-Handle zu erstellen (Geben Sie SOCKET ein). Die Standardparameter `Create` zum Erstellen eines Streamsockets, aber wenn `CArchive` Sie den Socket nicht mit einem Objekt verwenden, können Sie einen Parameter angeben, um stattdessen einen Datagrammsocket zu erstellen, oder an einen bestimmten Port binden, um einen Serversocket zu erstellen. Stellen Sie eine `Connect` Verbindung mit einem `Accept` Clientsocket her, der auf der Clientseite und auf der Serverseite verwendet wird. Erstellen Sie `CSocketFile` dann ein Objekt, und ordnen Sie es dem `CSocket` Objekt im `CSocketFile` Konstruktor zu. Erstellen Sie `CArchive` als Nächstes ein Objekt zum Senden und eines zum `CSocketFile` Empfangen `CArchive` von Daten (bei Bedarf), und ordnen Sie sie dann dem Objekt im Konstruktor zu. Wenn die Kommunikation abgeschlossen `CArchive` `CSocketFile`ist, `CSocket` zerstören Sie die , und die Objekte. Der SOCKET-Datentyp wird im Artikel [Windows Sockets: Background](../../mfc/windows-sockets-background.md)beschrieben.

Wenn Sie `CArchive` `CSocketFile` mit `CSocket`und verwenden, kann `CSocket::Receive` es vorkommen, `PumpMessages(FD_READ)`dass eine Schleife (durch ) eintritt, die auf die angeforderte Menge an Bytes wartet. Dies liegt daran, dass Windows-Sockets nur `CSocketFile` einen `CSocket` recv-Aufruf pro FD_READ Benachrichtigung zulassen, aber mehrere recv-Aufrufe pro FD_READ. Wenn Sie eine FD_READ erhalten, wenn keine Daten zum Lesen vorhanden sind, hängt die Anwendung. Wenn Sie nie eine weitere FD_READ erhalten, beendet die Anwendung die Kommunikation über den Socket.

Sie können dieses Problem wie folgt beheben. Rufen `OnReceive` Sie in der Methode `CAsyncSocket::IOCtl(FIONREAD, ...)` ihrer Socketklasse auf, bevor Sie die `Serialize` Methode Ihrer Nachrichtenklasse aufrufen, wenn die erwarteten Daten, die vom Socket gelesen werden sollen, die Größe eines TCP-Pakets überschreiten (maximale Übertragungseinheit des Netzwerkmediums, in der Regel mindestens 1096 Bytes). Wenn die Größe der verfügbaren Daten geringer ist als erforderlich, warten Sie, bis alle Daten empfangen wurden, und starten Sie dann den Lesevorgang.

Im folgenden Beispiel `m_dwExpected` ist die ungefähre Anzahl von Bytes, die der Benutzer erwartet. Es wird davon ausgegangen, dass Sie es an anderer Stelle im Code deklarieren.

[!code-cpp[NVC_MFCSocketThread#4](../../mfc/reference/codesnippet/cpp/csocket-class_1.cpp)]

> [!NOTE]
> Wenn Sie MFC-Sockets in sekundären Threads in einer `AfxSocketInit` statisch verknüpften MFC-Anwendung verwenden, müssen Sie in jedem Thread aufrufen, der Sockets verwendet, um die Socketbibliotheken zu initialisieren. Standardmäßig `AfxSocketInit` wird nur im primären Thread aufgerufen.

Weitere Informationen finden Sie unter [Windows Sockets in MFC](../../mfc/windows-sockets-in-mfc.md), [Windows Sockets: Using Sockets with Archives](../../mfc/windows-sockets-using-sockets-with-archives.md), Windows [Sockets: How Sockets with Archives Work](../../mfc/windows-sockets-how-sockets-with-archives-work.md), Windows [Sockets: Sequence of Operations](../../mfc/windows-sockets-sequence-of-operations.md), Windows [Sockets: Example of Sockets Using Archives](../../mfc/windows-sockets-example-of-sockets-using-archives.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CAsyncSocket](../../mfc/reference/casyncsocket-class.md)

`CSocket`

## <a name="requirements"></a>Anforderungen

**Kopf:** afxsock.h

## <a name="csocketattach"></a><a name="attach"></a>CSocket::Attach

Rufen Sie diese Memberfunktion auf, um das `hSocket` Handle an ein `CSocket` Objekt anzufügen.

```
BOOL Attach(SOCKET hSocket);
```

### <a name="parameters"></a>Parameter

*hSocket*<br/>
Enthält ein Handle für einen Socket.

### <a name="return-value"></a>Rückgabewert

Ungleich null, wenn die Funktion erfolgreich ist.

### <a name="remarks"></a>Bemerkungen

Das SOCKET-Handle wird im [m_hSocket-Datenmember](../../mfc/reference/casyncsocket-class.md#m_hsocket) des Objekts gespeichert.

Weitere Informationen finden Sie unter [Windows Sockets: Verwenden von Sockets mit Archiven](../../mfc/windows-sockets-using-sockets-with-archives.md).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCSocketThread#1](../../mfc/reference/codesnippet/cpp/csocket-class_2.h)]

[!code-cpp[NVC_MFCSocketThread#2](../../mfc/reference/codesnippet/cpp/csocket-class_3.cpp)]

[!code-cpp[NVC_MFCSocketThread#3](../../mfc/reference/codesnippet/cpp/csocket-class_4.cpp)]

## <a name="csocketcancelblockingcall"></a><a name="cancelblockingcall"></a>CSocket::CancelBlockingCall

Rufen Sie diese Memberfunktion auf, um einen blockierenden Anruf abzubrechen, der derzeit ausgeführt wird.

```
void CancelBlockingCall();
```

### <a name="remarks"></a>Bemerkungen

Diese Funktion bricht alle ausstehenden Blockierungsoperationen für diesen Socket ab. Der ursprüngliche Blockierende Aufruf wird so schnell wie möglich mit dem Fehler WSAEINTR beendet.

Im Falle eines `Connect` Blockierungsvorgangs beendet die Windows Sockets-Implementierung den blockierenden Aufruf so schnell wie möglich, aber es ist möglicherweise nicht möglich, dass die Socketressourcen freigegeben werden, bis die Verbindung abgeschlossen (und dann zurückgesetzt wurde) oder ein Timeout aufgetreten ist. Dies ist wahrscheinlich nur dann spürbar, wenn die Anwendung sofort versucht, einen neuen Socket zu öffnen (wenn keine Sockets verfügbar sind) oder eine Verbindung mit demselben Peer herzustellen.

Das Abbrechen eines `Accept` anderen Vorgangs als kann den Socket in einem unbestimmten Zustand belassen. Wenn eine Anwendung einen Blockierungsvorgang für einen Socket abbricht, kann die Anwendung nur davon `Close`abhängen, ob sie für den Socket ausführen kann, ein Aufruf von , obwohl andere Vorgänge bei einigen Windows Sockets-Implementierungen funktionieren können. Wenn Sie maximale Portabilität für Ihre Anwendung wünschen, müssen Sie darauf achten, dass Sie sich nicht auf die Ausführung von Vorgängen nach einem Abbruch verlassen.

Weitere Informationen finden Sie unter [Windows Sockets: Verwenden von Sockets mit Archiven](../../mfc/windows-sockets-using-sockets-with-archives.md).

## <a name="csocketcreate"></a><a name="create"></a>CSocket::Erstellen

Rufen Sie die **Memberfunktion Erstellen** auf, nachdem Sie ein Socketobjekt erstellt haben, um den Windows-Socket zu erstellen und anzuhängen.

```
BOOL Create(
    UINT nSocketPort = 0,
    int nSocketType = SOCK_STREAM,
    LPCTSTR lpszSocketAddress = NULL);
```

### <a name="parameters"></a>Parameter

*nSocketPort*<br/>
Ein bestimmter Port, der mit dem Socket verwendet werden soll, oder 0, wenn MFC einen Port auswählen soll.

*nSocketType*<br/>
SOCK_STREAM oder SOCK_DGRAM.

*lpszSocketAddress*<br/>
Ein Zeiger auf eine Zeichenfolge, die die Netzwerkadresse des verbundenen Sockets enthält, eine gepunktete Zahl wie "128.56.22.8". Das Übergeben der NULL-Zeichenfolge `CSocket` für diesen Parameter gibt an, dass die Instanz auf Clientaktivitäten auf allen Netzwerkschnittstellen lauschen soll.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Funktion erfolgreich ist; Andernfalls 0, und ein bestimmter Fehlercode `GetLastError`kann abgerufen werden, indem Sie aufrufen.

### <a name="remarks"></a>Bemerkungen

`Create`ruft `Bind` dann auf, um den Socket an die angegebene Adresse zu binden. Die folgenden Sockettypen werden unterstützt:

- SOCK_STREAM Bietet sequenzierte, zuverlässige, zweiseitige, verbindungsbasierte Byte-Streams. Verwendet Tcp (Transmission Control Protocol) für die Internetadressfamilie.

- SOCK_DGRAM Unterstützt Datagramme, bei denen es sich um verbindungslose, unzuverlässige Puffer mit einer festen (in der Regel kleinen) maximalen Länge handelt. Verwendet User Datagram Protocol (UDP) für die Internetadressfamilie. Um diese Option zu verwenden, dürfen `CArchive` Sie den Socket mit einem Objekt nicht verwenden.

    > [!NOTE]
    >  Die `Accept` Memberfunktion nimmt einen Verweis `CSocket` auf ein neues, leeres Objekt als Parameter. Sie müssen dieses Objekt `Accept`erstellen, bevor Sie aufrufen. Beachten Sie, dass die Verbindung geschlossen wird, wenn dieses Socketobjekt den Gültigkeitsbereich verlässt. Rufen `Create` Sie dieses neue Socketobjekt nicht auf.

Weitere Informationen zu Stream- und Datagrammsockets finden Sie in den Artikeln [Windows Sockets: Background](../../mfc/windows-sockets-background.md), [Windows Sockets: Ports and Socket Addresses](../../mfc/windows-sockets-ports-and-socket-addresses.md)und Windows [Sockets: Using Sockets with Archives](../../mfc/windows-sockets-using-sockets-with-archives.md).

## <a name="csocketcsocket"></a><a name="csocket"></a>CSocket::CSocket

Erstellt ein `CSocket`-Objekt.

```
CSocket();
```

### <a name="remarks"></a>Bemerkungen

Nach dem Bau müssen `Create` Sie die Memberfunktion aufrufen.

Weitere Informationen finden Sie unter [Windows Sockets: Verwenden von Sockets mit Archiven](../../mfc/windows-sockets-using-sockets-with-archives.md).

## <a name="csocketfromhandle"></a><a name="fromhandle"></a>CSocket::FromHandle

Gibt einen Zeiger `CSocket` auf ein Objekt zurück.

```
static CSocket* PASCAL FromHandle(SOCKET hSocket);
```

### <a name="parameters"></a>Parameter

*hSocket*<br/>
Enthält ein Handle für einen Socket.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf `CSocket` ein Objekt oder NULL, wenn kein `CSocket` Objekt an *hSocket*angefügt ist.

### <a name="remarks"></a>Bemerkungen

Wenn ein SOCKET-Handle `CSocket` angegeben wird, gibt die Memberfunktion NULL zurück, wenn ein Objekt nicht an das Handle angefügt ist, und erstellt kein temporäres Objekt.

Weitere Informationen finden Sie unter [Windows Sockets: Verwenden von Sockets mit Archiven](../../mfc/windows-sockets-using-sockets-with-archives.md).

## <a name="csocketisblocking"></a><a name="isblocking"></a>CSocket::IsBlocking

Rufen Sie diese Memberfunktion auf, um zu ermitteln, ob ein blockierender Aufruf ausgeführt wird.

```
BOOL IsBlocking();
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn der Socket blockiert wird; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [Windows Sockets: Verwenden von Sockets mit Archiven](../../mfc/windows-sockets-using-sockets-with-archives.md).

## <a name="csocketonmessagepending"></a><a name="onmessagepending"></a>CSocket::OnMessagePending

Überschreiben Sie diese Memberfunktion, um nach bestimmten Nachrichten von Windows zu suchen und auf diese in Ihrem Socket zu reagieren.

```
virtual BOOL OnMessagePending();
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Nachricht verarbeitet wurde; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Dies ist ein fortgeschrittenes Überridable.

Das Framework `OnMessagePending` ruft auf, während der Socket Windows-Nachrichten pumpt, um Ihnen die Möglichkeit zu geben, mit Nachrichten von Interesse für Ihre Anwendung umzugehen. Beispiele für die Verwendung `OnMessagePending`finden Sie im Artikel [Windows Sockets: Von Socketklassen ableiten](../../mfc/windows-sockets-deriving-from-socket-classes.md).

Weitere Informationen finden Sie unter [Windows Sockets: Verwenden von Sockets mit Archiven](../../mfc/windows-sockets-using-sockets-with-archives.md).

## <a name="see-also"></a>Siehe auch

[CAsyncSocket-Klasse](../../mfc/reference/casyncsocket-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CAsyncSocket-Klasse](../../mfc/reference/casyncsocket-class.md)<br/>
[CSocketFile-Klasse](../../mfc/reference/csocketfile-class.md)
