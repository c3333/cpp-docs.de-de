---
title: COleMessageFilter-Klasse
ms.date: 11/04/2016
f1_keywords:
- COleMessageFilter
- AFXOLE/COleMessageFilter
- AFXOLE/COleMessageFilter::COleMessageFilter
- AFXOLE/COleMessageFilter::BeginBusyState
- AFXOLE/COleMessageFilter::EnableBusyDialog
- AFXOLE/COleMessageFilter::EnableNotRespondingDialog
- AFXOLE/COleMessageFilter::EndBusyState
- AFXOLE/COleMessageFilter::OnMessagePending
- AFXOLE/COleMessageFilter::Register
- AFXOLE/COleMessageFilter::Revoke
- AFXOLE/COleMessageFilter::SetBusyReply
- AFXOLE/COleMessageFilter::SetMessagePendingDelay
- AFXOLE/COleMessageFilter::SetRetryReply
helpviewer_keywords:
- COleMessageFilter [MFC], COleMessageFilter
- COleMessageFilter [MFC], BeginBusyState
- COleMessageFilter [MFC], EnableBusyDialog
- COleMessageFilter [MFC], EnableNotRespondingDialog
- COleMessageFilter [MFC], EndBusyState
- COleMessageFilter [MFC], OnMessagePending
- COleMessageFilter [MFC], Register
- COleMessageFilter [MFC], Revoke
- COleMessageFilter [MFC], SetBusyReply
- COleMessageFilter [MFC], SetMessagePendingDelay
- COleMessageFilter [MFC], SetRetryReply
ms.assetid: b1fd1639-fac4-4fd0-bf17-15172deba13c
ms.openlocfilehash: 8a6c160a76ae27059238c3e8e26b5bea87a87f7f
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753835"
---
# <a name="colemessagefilter-class"></a>COleMessageFilter-Klasse

Verwaltet die Parallelität, die für die Interaktion von OLE-Anwendungen benötigt wird.

## <a name="syntax"></a>Syntax

```
class COleMessageFilter : public CCmdTarget
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[COleMessageFilter::COleMessageFilter](#colemessagefilter)|Erstellt ein `COleMessageFilter`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[COleMessageFilter::BeginBusyState](#beginbusystate)|Versetzt die Anwendung in den ausgelasteten Zustand.|
|[COleMessageFilter::EnableBusyDialog](#enablebusydialog)|Aktiviert und deaktiviert das Dialogfeld, das angezeigt wird, wenn eine aufgerufene Anwendung ausgelastet ist.|
|[COleMessageFilter::EnableNotRespondingDialog](#enablenotrespondingdialog)|Aktiviert und deaktiviert das Dialogfeld, das angezeigt wird, wenn eine aufgerufene Anwendung nicht reagiert.|
|[COleMessageFilter::EndbusyState](#endbusystate)|Beendet den ausgelasteten Status der Anwendung.|
|[COleMessageFilter::OnMessagePending](#onmessagepending)|Wird vom Framework aufgerufen, um Nachrichten zu verarbeiten, während ein OLE-Aufruf ausgeführt wird.|
|[COleMessageFilter::Registrieren](#register)|Registriert den Nachrichtenfilter bei den OLE-System-DLLs.|
|[COleMessageFilter::Revoke](#revoke)|Widerruft die Registrierung des Nachrichtenfilters bei den OLE-System-DLLs.|
|[COleMessageFilter::SetBusyReply](#setbusyreply)|Bestimmt die Antwort der ausgelasteten Anwendung auf einen OLE-Aufruf.|
|[COleMessageFilter::SetMessagePendingDelay](#setmessagependingdelay)|Bestimmt, wie lange die Anwendung auf eine Antwort auf einen OLE-Aufruf wartet.|
|[COleMessageFilter::SetRetryReply](#setretryreply)|Bestimmt die Antwort der aufrufenden Anwendung auf eine ausgelastete Anwendung.|

## <a name="remarks"></a>Bemerkungen

Die `COleMessageFilter` Klasse ist nützlich bei der visuellen Bearbeitung von Server- und Containeranwendungen sowie bei OLE-Automatisierungsanwendungen. Für Serveranwendungen, die aufgerufen werden, kann diese Klasse verwendet werden, um die Anwendung "beschäftigt" zu machen, sodass eingehende Aufrufe von anderen Containeranwendungen entweder abgebrochen oder später wiederholt werden. Diese Klasse kann auch verwendet werden, um die Aktion zu bestimmen, die von einer aufrufenden Anwendung ausgeführt werden soll, wenn die aufgerufene Anwendung ausgelastet ist.

Häufige Verwendung ist, dass eine Serveranwendung [BeginBusyState](#beginbusystate) und [EndBusyState](#endbusystate) aufruft, wenn es gefährlich wäre, wenn ein Dokument oder ein anderes OLE-Objekt zerstört wird. Diese Anrufe werden in [CWinApp::OnIdle](../../mfc/reference/cwinapp-class.md#onidle) während benutzeroberflächenaktualisierungen getätigt.

Standardmäßig wird `COleMessageFilter` ein Objekt zugewiesen, wenn die Anwendung initialisiert wird. Sie kann mit [AfxOleGetMessageFilter](application-control.md#afxolegetmessagefilter)abgerufen werden.

Dies ist eine fortgeschrittene Klasse; Sie müssen selten direkt damit arbeiten.

Weitere Informationen finden Sie im Artikel [Server: Implementieren eines Servers](../../mfc/servers-implementing-a-server.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`COleMessageFilter`

## <a name="requirements"></a>Requirements (Anforderungen)

**Kopfzeile:** afxole.h

## <a name="colemessagefilterbeginbusystate"></a><a name="beginbusystate"></a>COleMessageFilter::BeginBusyState

Rufen Sie diese Funktion auf, um einen ausgelasteten Zustand zu beginnen.

```
virtual void BeginBusyState();
```

### <a name="remarks"></a>Bemerkungen

Es funktioniert in Verbindung mit [EndBusyState,](#endbusystate) um den ausgelasteten Zustand der Anwendung zu steuern. Die Funktion [SetBusyReply](#setbusyreply) bestimmt die Antwort der Anwendung auf aufrufende Anwendungen, wenn sie ausgelastet ist.

Das `BeginBusyState` `EndBusyState` inkrementieren und dekrementieren bzw. dekrementieren, ein Zähler, der bestimmt, ob die Anwendung ausgelastet ist. Beispielsweise führen zwei `BeginBusyState` Aufrufe und `EndBusyState` ein Aufruf, um immer noch zu einem ausgelasteten Zustand zu führen. Um einen ausgelasteten `EndBusyState` Zustand abzubrechen, `BeginBusyState` ist es notwendig, die gleiche Anzahl von Anrufen anzurufen, die aufgerufen wurden.

Standardmäßig wechselt das Framework während der Leerlaufverarbeitung in den Ruhezustand, der von [CWinApp::OnIdle](../../mfc/reference/cwinapp-class.md#onidle)ausgeführt wird. Während die Anwendung ON_COMMANDUPDATEUI Benachrichtigungen verarbeitet, werden eingehende Anrufe später behandelt, nachdem die Verarbeitung im Leerlauf abgeschlossen ist.

## <a name="colemessagefiltercolemessagefilter"></a><a name="colemessagefilter"></a>COleMessageFilter::COleMessageFilter

Erstellt ein `COleMessageFilter` -Objekt.

```
COleMessageFilter();
```

## <a name="colemessagefilterenablebusydialog"></a><a name="enablebusydialog"></a>COleMessageFilter::EnableBusyDialog

Aktiviert und deaktiviert das dialogische Dialogfeld "Beschäftigt", das angezeigt wird, wenn die Benachrichtigungsausstehende Verzögerung abläuft (siehe [SetRetryReply](#setretryreply)) während eines OLE-Aufrufs.

```cpp
void EnableBusyDialog(BOOL bEnableBusy = TRUE);
```

### <a name="parameters"></a>Parameter

*bEnableBusy*<br/>
Gibt an, ob das Dialogfeld "beschäftigt" aktiviert oder deaktiviert ist.

## <a name="colemessagefilterenablenotrespondingdialog"></a><a name="enablenotrespondingdialog"></a>COleMessageFilter::EnableNotRespondingDialog

Aktiviert und deaktiviert das Dialogfeld "Nicht reagiert", das angezeigt wird, wenn während eines OLE-Aufrufs eine Tastatur- oder Mausnachricht aussteht und der Anruf ein Timeout aufgetreten ist.

```cpp
void EnableNotRespondingDialog(BOOL bEnableNotResponding = TRUE);
```

### <a name="parameters"></a>Parameter

*bEnableNotResponding*<br/>
Gibt an, ob das Dialogfeld "nicht reagiert" aktiviert oder deaktiviert ist.

## <a name="colemessagefilterendbusystate"></a><a name="endbusystate"></a>COleMessageFilter::EndbusyState

Rufen Sie diese Funktion auf, um einen ausgelasteten Zustand zu beenden.

```
virtual void EndBusyState();
```

### <a name="remarks"></a>Bemerkungen

Es funktioniert in Verbindung mit [BeginBusyState,](#beginbusystate) um den ausgelasteten Zustand der Anwendung zu steuern. Die Funktion [SetBusyReply](#setbusyreply) bestimmt die Antwort der Anwendung auf aufrufende Anwendungen, wenn sie ausgelastet ist.

Das `BeginBusyState` `EndBusyState` inkrementieren und dekrementieren bzw. dekrementieren, ein Zähler, der bestimmt, ob die Anwendung ausgelastet ist. Beispielsweise führen zwei `BeginBusyState` Aufrufe und `EndBusyState` ein Aufruf, um immer noch zu einem ausgelasteten Zustand zu führen. Um einen ausgelasteten `EndBusyState` Zustand abzubrechen, `BeginBusyState` ist es notwendig, die gleiche Anzahl von Anrufen anzurufen, die aufgerufen wurden.

Standardmäßig wechselt das Framework während der Leerlaufverarbeitung in den Ruhezustand, der von [CWinApp::OnIdle](../../mfc/reference/cwinapp-class.md#onidle)ausgeführt wird. Während die Anwendung ON_UPDATE_COMMAND_UI Benachrichtigungen verarbeitet, werden eingehende Anrufe nach Abschluss der Verarbeitung im Leerlauf verarbeitet.

## <a name="colemessagefilteronmessagepending"></a><a name="onmessagepending"></a>COleMessageFilter::OnMessagePending

Wird vom Framework aufgerufen, um Nachrichten zu verarbeiten, während ein OLE-Aufruf ausgeführt wird.

```
virtual BOOL OnMessagePending(const MSG* pMsg);
```

### <a name="parameters"></a>Parameter

*pMsg*<br/>
Zeiger auf die ausstehende Nachricht.

### <a name="return-value"></a>Rückgabewert

Bei Erfolg ein Wert ungleich 0 (null), andernfalls 0 (null).

### <a name="remarks"></a>Bemerkungen

Wenn eine aufrufende Anwendung auf den Abschluss eines `OnMessagePending` Aufrufs wartet, ruft das Framework mit einem Zeiger auf die ausstehende Nachricht auf. Standardmäßig löst das Framework WM_PAINT Nachrichten aus, sodass Fensteraktualisierungen während eines Anrufs auftreten können, der lange dauert.

Sie müssen Ihren Nachrichtenfilter über einen Aufruf zu [Registrieren](#register) registrieren, bevor er aktiv werden kann.

## <a name="colemessagefilterregister"></a><a name="register"></a>COleMessageFilter::Registrieren

Registriert den Nachrichtenfilter bei den OLE-System-DLLs.

```
BOOL Register();
```

### <a name="return-value"></a>Rückgabewert

Bei Erfolg ein Wert ungleich 0 (null), andernfalls 0 (null).

### <a name="remarks"></a>Bemerkungen

Ein Nachrichtenfilter hat keine Auswirkungen, es sei denn, er ist bei den System-DLLs registriert. Normalerweise registriert der Initialisierungscode Ihrer Anwendung den Nachrichtenfilter der Anwendung. Jeder andere von Ihrer Anwendung registrierte Nachrichtenfilter sollte widerrufen werden, bevor das Programm durch einen Aufruf von [Revoke](#revoke)beendet wird.

Der Standardnachrichtenfilter des Frameworks wird während der Initialisierung automatisch registriert und bei Beendigung widerrufen.

## <a name="colemessagefilterrevoke"></a><a name="revoke"></a>COleMessageFilter::Revoke

Widerruft eine vorherige Registrierung, die durch einen Aufruf von [Register](#register)durchgeführt wurde.

```cpp
void Revoke();
```

### <a name="remarks"></a>Bemerkungen

Ein Nachrichtenfilter sollte vor dem Beenden des Programms widerrufen werden.

Der Standardnachrichtenfilter, der automatisch vom Framework erstellt und registriert wird, wird ebenfalls automatisch widerrufen.

## <a name="colemessagefiltersetbusyreply"></a><a name="setbusyreply"></a>COleMessageFilter::SetBusyReply

Diese Funktion legt die "beschäftigte Antwort" der Anwendung fest.

```cpp
void SetBusyReply(SERVERCALL nBusyReply);
```

### <a name="parameters"></a>Parameter

*nBusyReply*<br/>
Ein Wert `SERVERCALL` aus der Enumeration, der in COMPOBJ definiert ist. H. Es kann einen der folgenden Werte haben:

- SERVERCALL_ISHANDLED Die Anwendung kann Aufrufe annehmen, kann jedoch bei der Verarbeitung eines bestimmten Aufrufs fehlschlagen.

- SERVERCALL_REJECTED Die Anwendung wird wahrscheinlich nie in der Lage sein, einen Aufruf zu verarbeiten.

- SERVERCALL_RETRYLATER Die Anwendung befindet sich vorübergehend in einem Zustand, in dem sie keinen Aufruf verarbeiten kann.

### <a name="remarks"></a>Bemerkungen

Die Funktionen [BeginBusyState](#beginbusystate) und [EndBusyState](#endbusystate) steuern den ausgelasteten Status der Anwendung.

Wenn eine Anwendung mit einem Aufruf `BeginBusyState`von beschäftigt wurde, reagiert sie auf Aufrufe von OLE-System-DLLs mit einem Wert, der durch die letzte Einstellung von `SetBusyReply`bestimmt wird. Die aufrufende Anwendung verwendet diese ausgelastete Antwort, um zu bestimmen, welche Aktion zu ergreifen ist.

Standardmäßig ist die ausgelastete Antwort SERVERCALL_RETRYLATER. Diese Antwort bewirkt, dass die aufrufende Anwendung den Aufruf so schnell wie möglich erneut versucht.

## <a name="colemessagefiltersetmessagependingdelay"></a><a name="setmessagependingdelay"></a>COleMessageFilter::SetMessagePendingDelay

Bestimmt, wie lange die aufrufende Anwendung auf eine Antwort von der aufgerufenen Anwendung wartet, bevor weitere Aktionen ergriffen werden.

```cpp
void SetMessagePendingDelay(DWORD nTimeout = 5000);
```

### <a name="parameters"></a>Parameter

*nTimeout*<br/>
Anzahl der Millisekunden für die Verzögerung beim Ausstehen der Nachricht.

### <a name="remarks"></a>Bemerkungen

Diese Funktion funktioniert in Verbindung mit [SetRetryReply](#setretryreply).

## <a name="colemessagefiltersetretryreply"></a><a name="setretryreply"></a>COleMessageFilter::SetRetryReply

Bestimmt die Aktion der aufrufenden Anwendung, wenn sie eine ausgelastete Antwort von einer aufgerufenen Anwendung empfängt.

```cpp
void SetRetryReply(DWORD nRetryReply = 0);
```

### <a name="parameters"></a>Parameter

*nRetryReply*<br/>
Anzahl der Millisekunden zwischen Wiederholungen.

### <a name="remarks"></a>Bemerkungen

Wenn eine aufgerufene Anwendung angibt, dass sie ausgelastet ist, kann die aufrufende Anwendung warten, bis der Server nicht mehr ausgelastet ist, den Vorgang sofort wiederholen oder nach einem angegebenen Intervall wiederholen. Es kann auch beschließen, den Anruf ganz abzubrechen.

Die Antwort des Aufrufers wird `SetRetryReply` von den Funktionen und [SetMessagePendingDelay](#setmessagependingdelay)gesteuert. `SetRetryReply`bestimmt, wie lange die aufrufende Anwendung zwischen Wiederholungen für einen bestimmten Aufruf warten soll. `SetMessagePendingDelay`bestimmt, wie lange die aufrufende Anwendung auf eine Antwort vom Server wartet, bevor weitere Aktionen ausgeführt werden.

Normalerweise sind die Standardeinstellungen akzeptabel und müssen nicht geändert werden. Das Framework versucht den Aufruf alle *nRetryReply* Millisekunden, bis der Aufruf durchgeht oder die Verzögerung beim Ausstehen der Nachricht abgelaufen ist. Der Wert 0 für *nRetryReply* gibt einen sofortigen Wiederholungsversuch an und - 1 gibt den Abbruch des Anrufs an.

Wenn die Verzögerung beim Ausstehen der Nachricht abgelaufen ist, wird das OLE-Dialogfeld "beschäftigt" (siehe [COleBusyDialog](../../mfc/reference/colebusydialog-class.md)) angezeigt, damit der Benutzer den Anruf abbrechen oder wiederholen kann. Rufen Sie [EnableBusyDialog](#enablebusydialog) auf, um dieses Dialogfeld zu aktivieren oder zu deaktivieren.

Wenn während eines Anrufs eine Tastatur- oder Mausnachricht aussteht und das Zeitlimit für den Anruf überschritten wurde (die Verzögerung beim Ausstehen der Nachricht überschritten), wird das Dialogfeld "Nicht reagieren" angezeigt. Rufen Sie [EnableNotRespondingDialog](#enablenotrespondingdialog) auf, um dieses Dialogfeld zu aktivieren oder zu deaktivieren. Normalerweise deutet dieser Zustand darauf hin, dass etwas schief gelaufen ist und der Benutzer ungeduldig wird.

Wenn die Dialogfelder deaktiviert sind, wird die aktuelle "Wiederholungsantwort" immer für Aufrufe an ausgelastete Anwendungen verwendet.

## <a name="see-also"></a>Weitere Informationen

[CCmdTarget-Klasse](../../mfc/reference/ccmdtarget-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CCmdTarget-Klasse](../../mfc/reference/ccmdtarget-class.md)
