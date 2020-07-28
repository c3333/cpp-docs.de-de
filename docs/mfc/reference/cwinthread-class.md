---
title: CWinThread-Klasse
ms.date: 11/04/2016
f1_keywords:
- CWinThread
- AFXWIN/CWinThread
- AFXWIN/CWinThread::CWinThread
- AFXWIN/CWinThread::CreateThread
- AFXWIN/CWinThread::ExitInstance
- AFXWIN/CWinThread::GetMainWnd
- AFXWIN/CWinThread::GetThreadPriority
- AFXWIN/CWinThread::InitInstance
- AFXWIN/CWinThread::IsIdleMessage
- AFXWIN/CWinThread::OnIdle
- AFXWIN/CWinThread::PostThreadMessage
- AFXWIN/CWinThread::PreTranslateMessage
- AFXWIN/CWinThread::ProcessMessageFilter
- AFXWIN/CWinThread::ProcessWndProcException
- AFXWIN/CWinThread::PumpMessage
- AFXWIN/CWinThread::ResumeThread
- AFXWIN/CWinThread::Run
- AFXWIN/CWinThread::SetThreadPriority
- AFXWIN/CWinThread::SuspendThread
- AFXWIN/CWinThread::m_bAutoDelete
- AFXWIN/CWinThread::m_hThread
- AFXWIN/CWinThread::m_nThreadID
- AFXWIN/CWinThread::m_pActiveWnd
- AFXWIN/CWinThread::m_pMainWnd
helpviewer_keywords:
- CWinThread [MFC], CWinThread
- CWinThread [MFC], CreateThread
- CWinThread [MFC], ExitInstance
- CWinThread [MFC], GetMainWnd
- CWinThread [MFC], GetThreadPriority
- CWinThread [MFC], InitInstance
- CWinThread [MFC], IsIdleMessage
- CWinThread [MFC], OnIdle
- CWinThread [MFC], PostThreadMessage
- CWinThread [MFC], PreTranslateMessage
- CWinThread [MFC], ProcessMessageFilter
- CWinThread [MFC], ProcessWndProcException
- CWinThread [MFC], PumpMessage
- CWinThread [MFC], ResumeThread
- CWinThread [MFC], Run
- CWinThread [MFC], SetThreadPriority
- CWinThread [MFC], SuspendThread
- CWinThread [MFC], m_bAutoDelete
- CWinThread [MFC], m_hThread
- CWinThread [MFC], m_nThreadID
- CWinThread [MFC], m_pActiveWnd
- CWinThread [MFC], m_pMainWnd
ms.assetid: 10cdc294-4057-4e76-ac7c-a8967a89af0b
ms.openlocfilehash: 6dbe4c4d3ed5edaf0563abf589cd844cca6803f0
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87182771"
---
# <a name="cwinthread-class"></a>CWinThread-Klasse

Stellt einen Ausführungsthread innerhalb einer Anwendung dar.

## <a name="syntax"></a>Syntax

```
class CWinThread : public CCmdTarget
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CWinThread:: CWinThread](#cwinthread)|Erstellt ein `CWinThread`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|name|BESCHREIBUNG|
|----------|-----------------|
|[CWinThread:: kreatethread](#createthread)|Startet die Ausführung eines- `CWinThread` Objekts.|
|[CWinThread:: ExitInstance](#exitinstance)|Außer Kraft Setzung zum Bereinigen, wenn der Thread beendet wird.|
|[CWinThread:: getmainwnd](#getmainwnd)|Ruft einen Zeiger auf das Hauptfenster des Threads ab.|
|[CWinThread:: getthreadpriority](#getthreadpriority)|Ruft die Priorität des aktuellen Threads ab.|
|[CWinThread:: InitInstance](#initinstance)|Überschreiben, um die Thread Instanzen Initialisierung auszuführen.|
|[CWinThread:: isidlemessage](#isidlemessage)|Prüft, ob spezielle Meldungen angezeigt werden.|
|[CWinThread:: OnIdle](#onidle)|Überschreiben, um Thread spezifische Leerlaufzeit Verarbeitung auszuführen.|
|[CWinThread::P ostthreadmessage](#postthreadmessage)|Sendet eine Nachricht an ein anderes `CWinThread` Objekt.|
|[CWinThread::P retranslatemess Age](#pretranslatemessage)|Filtert Nachrichten, bevor diese an die Windows-Funktionen [translatemess](/windows/win32/api/winuser/nf-winuser-translatemessage) und [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage)gesendet werden.|
|[CWinThread::P rocess MessageFilter](#processmessagefilter)|Fängt bestimmte Nachrichten ab, bevor Sie die Anwendung erreichen.|
|[CWinThread::P rocess wndprocexception](#processwndprocexception)|Fängt alle nicht behandelten Ausnahmen ab, die von den Meldungs-und Befehls Handlern des Threads ausgelöst werden.|
|[CWinThread::P umpmessage](#pumpmessage)|Enthält die Nachrichten Schleife des Threads.|
|[CWinThread:: ResumeThread](#resumethread)|Dekrementierungen den anhaltezähler eines Threads.|
|[CWinThread:: Run](#run)|Steuern der Funktion für Threads mit einem nachrichtenpump. Überschreiben, um die Standard Nachrichten Schleife anzupassen.|
|[CWinThread:: SetThreadPriority](#setthreadpriority)|Legt die Priorität des aktuellen Threads fest.|
|[CWinThread:: SuspendThread](#suspendthread)|Erhöht die Unterbrechungs Anzahl eines Threads.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CWinThread:: Operator handle](#operator_handle)|Ruft das Handle des- `CWinThread` Objekts ab.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CWinThread:: m_bAutoDelete](#m_bautodelete)|Gibt an, ob das Objekt bei der Thread Beendigung zerstört werden soll.|
|[CWinThread:: m_hThread](#m_hthread)|Handle für den aktuellen Thread.|
|[CWinThread:: m_nThreadID](#m_nthreadid)|ID des aktuellen Threads.|
|[CWinThread:: m_pActiveWnd](#m_pactivewnd)|Zeiger auf das Hauptfenster der Containeranwendung, wenn ein OLE-Server direkt aktiv ist.|
|[CWinThread:: m_pMainWnd](#m_pmainwnd)|Enthält einen Zeiger auf das Hauptfenster der Anwendung.|

## <a name="remarks"></a>Bemerkungen

Der hauptausführungs Thread wird normalerweise von einem von abgeleiteten Objekt bereitgestellt `CWinApp` ; `CWinApp` wird von abgeleitet `CWinThread` . Zusätzliche `CWinThread` Objekte lassen mehrere Threads innerhalb einer bestimmten Anwendung zu.

Es gibt zwei allgemeine Arten von Threads, die von `CWinThread` unterstützt werden: Arbeitsthreads und Benutzeroberflächenthreads. Arbeitsthreads verfügen über keine nachrichtenpump (z. b. einen Thread, der Hintergrund Berechnungen in einer Tabellenkalkulationsanwendung ausführt). Benutzeroberflächenthreads verfügen über eine nachrichtenpump und verarbeiten Nachrichten, die vom System empfangen wurden. [CWinApp](../../mfc/reference/cwinapp-class.md) und Klassen, die von diesem abgeleitet werden, sind Beispiele für Benutzeroberflächenthreads. Andere Benutzeroberflächenthreads können auch direkt von abgeleitet werden `CWinThread` .

Objekte der Klasse sind `CWinThread` in der Regel für die Dauer des Threads vorhanden. Wenn Sie dieses Verhalten ändern möchten, legen Sie [m_bAutoDelete](#m_bautodelete) auf false fest.

Die `CWinThread` -Klasse ist erforderlich, um Ihren Code und MFC vollständig Thread sicher zu machen. Thread lokale Daten, die vom Framework verwendet werden, um Thread spezifische Informationen beizubehalten, werden von- `CWinThread` Objekten verwaltet. Aufgrund dieser Abhängigkeit von, `CWinThread` um Thread lokale Daten zu verarbeiten, muss jeder Thread, der MFC verwendet, von MFC erstellt werden. Beispielsweise kann ein Thread, der von der Lauf Zeitfunktion [_beginthread erstellt wurde, _beginthreadex](../../c-runtime-library/reference/beginthread-beginthreadex.md) keine MFC-APIs verwenden.

Um einen Thread zu erstellen, rufen Sie [AfxBeginThread](application-information-and-management.md#afxbeginthread)auf. Je nachdem, ob Sie einen Worker-oder Benutzeroberflächen Thread benötigen, gibt es zwei Formen. Wenn Sie einen Benutzeroberflächen Thread benötigen, übergeben Sie an `AfxBeginThread` einen Zeiger auf den `CRuntimeClass` der von `CWinThread` abgeleiteten Klasse. Wenn Sie einen Arbeits Thread erstellen möchten, übergeben Sie an `AfxBeginThread` einen Zeiger zur Steuerungsfunktion und den-Parameter an die Steuerungsfunktion. Sowohl für Arbeitsthreads als auch für Benutzeroberflächenthreads können Sie optionale Parameter angeben, mit denen Priorität, Stapelgröße, erstellungsflags und Sicherheits Attribute geändert werden. `AfxBeginThread`Gibt einen Zeiger auf das neue `CWinThread` Objekt zurück.

Statt aufzurufen `AfxBeginThread` , können Sie ein von `CWinThread` abgeleitetes Objekt erstellen und dann aufrufen `CreateThread` . Diese zweistufige Konstruktionsmethode ist nützlich, wenn Sie das `CWinThread` Objekt zwischen aufeinander folgender Erstellung und Beendigung von Thread Ausführungen wieder verwenden möchten.

Weitere Informationen zu finden Sie in `CWinThread` den Artikeln [Multithreading mit C++ und MFC](../../parallel/multithreading-with-cpp-and-mfc.md), [Multithreading: Erstellen](../../parallel/multithreading-creating-user-interface-threads.md)von Benutzeroberflächenthreads, [Multithreading: Erstellen von Arbeitsthreads](../../parallel/multithreading-creating-worker-threads.md)und [Multithreading: Verwenden der Synchronisierungs Klassen](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`CWinThread`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxwin.h

## <a name="cwinthreadcreatethread"></a><a name="createthread"></a>CWinThread:: kreatethread

Erstellt einen Thread, der innerhalb des Adressraums des aufrufenden Prozesses ausgeführt werden soll.

```
BOOL CreateThread(
    DWORD dwCreateFlags = 0,
    UINT nStackSize = 0,
    LPSECURITY_ATTRIBUTES lpSecurityAttrs = NULL);
```

### <a name="parameters"></a>Parameter

*dwkreateflags*<br/>
Gibt ein zusätzliches Flag an, das die Erstellung des Threads steuert. Dieses Flag kann einen von zwei Werten enthalten:

- CREATE_SUSPENDED den Thread mit einer Unterbrechungs Anzahl von einem Thread starten. Verwenden Sie CREATE_SUSPENDED, wenn Sie alle Elementdaten des Objekts initialisieren möchten `CWinThread` , z. b. [m_bAutoDelete](#m_bautodelete) oder Member der abgeleiteten Klasse, bevor der Thread gestartet wird. Verwenden Sie nach Abschluss der Initialisierung den [CWinThread:: ResumeThread](#resumethread) , um den Thread zu starten, der ausgeführt wird. Der Thread wird erst ausgeführt, wenn `CWinThread::ResumeThread` aufgerufen wurde.

- **0** starten Sie den Thread sofort nach der Erstellung.

*nstacksize*<br/>
Gibt die Stapelgröße für den neuen Thread in Bytes an. Wenn der Wert **0**ist, entspricht die Stapelgröße standardmäßig der Größe des primären Threads des Prozesses.

*lpsecurityattrs*<br/>
Verweist auf eine [SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) -Struktur, die die Sicherheits Attribute für den Thread angibt.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn der Thread erfolgreich erstellt wurde. andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Verwenden `AfxBeginThread` Sie, um ein Thread Objekt zu erstellen und in einem Schritt auszuführen. Verwenden `CreateThread` Sie, wenn Sie das Thread Objekt zwischen aufeinander folgender Erstellung und Beendigung von Thread Ausführungen wieder verwenden möchten.

## <a name="cwinthreadcwinthread"></a><a name="cwinthread"></a>CWinThread:: CWinThread

Erstellt ein `CWinThread`-Objekt.

```
CWinThread();
```

### <a name="remarks"></a>Bemerkungen

Um die Ausführung des Threads zu starten, müssen Sie die Member-Funktion von " [foratethread](#createthread) " aufrufen. Sie erstellen Threads in der Regel durch Aufrufen von [AfxBeginThread](application-information-and-management.md#afxbeginthread), der diesen Konstruktor und aufruft `CreateThread` .

## <a name="cwinthreadexitinstance"></a><a name="exitinstance"></a>CWinThread:: ExitInstance

Wird von Framework in einer selten überschriebenen Funktion zum [Ausführen](#run) von Membern aufgerufen, um diese Instanz des Threads zu beenden, oder, wenn ein Aufruf von [InitInstance](#initinstance) fehlschlägt.

```
virtual int ExitInstance();
```

### <a name="return-value"></a>Rückgabewert

Der Exitcode des Threads. der Wert 0 gibt keine Fehler an, und Werte größer als 0 deuten auf einen Fehler hin. Dieser Wert kann durch Aufrufen von [GetExitCodeThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getexitcodethread)abgerufen werden.

### <a name="remarks"></a>Bemerkungen

Diese Member-Funktion nicht von einem beliebigen Ort aus aufrufen, sondern innerhalb der `Run` Member-Funktion. Diese Member-Funktion wird nur in Benutzeroberflächenthreads verwendet.

Die Standard Implementierung dieser Funktion löscht das- `CWinThread` Objekt, wenn [m_bAutoDelete](#m_bautodelete) true ist. Überschreiben Sie diese Funktion, wenn Sie zusätzliche Bereinigungs Vorgänge durchführen möchten, wenn der Thread beendet wird. Ihre Implementierung von `ExitInstance` sollte die Version der Basisklasse nach der Ausführung des Codes abrufen.

## <a name="cwinthreadgetmainwnd"></a><a name="getmainwnd"></a>CWinThread:: getmainwnd

Wenn es sich bei der Anwendung um einen OLE-Server handelt, rufen Sie diese Funktion auf, um einen Zeiger auf das aktive Hauptfenster der Anwendung abzurufen, statt direkt auf den `m_pMainWnd` Member des Anwendungs Objekts zu verweisen.

```
virtual CWnd* GetMainWnd();
```

### <a name="return-value"></a>Rückgabewert

Diese Funktion gibt einen Zeiger auf einen von zwei Windows-Typen zurück. Wenn Ihr Thread Teil eines OLE-Servers ist und ein-Objekt aufweist, das innerhalb eines aktiven Containers direkt aktiv ist, gibt diese Funktion das [CWinApp:: m_pActiveWnd](../../mfc/reference/cwinapp-class.md#m_pactivewnd) -Datenmember des- `CWinThread` Objekts zurück.

Wenn in einem Container kein Objekt vorhanden ist, das direkt aktiv ist, oder wenn es sich bei der Anwendung nicht um einen OLE-Server handelt, gibt diese Funktion den [m_pMainWnd](#m_pmainwnd) Datenmember des Thread Objekts zurück.

### <a name="remarks"></a>Bemerkungen

Bei Benutzeroberflächenthreads entspricht dies dem direkten Verweis auf den `m_pActiveWnd` Member des Anwendungs Objekts.

Wenn es sich bei der Anwendung nicht um einen OLE-Server handelt, entspricht das Aufrufen dieser Funktion dem direkten Verweisen auf den `m_pMainWnd`-Member des Anwendungsobjekts.

Überschreiben Sie diese Funktion, um das Standardverhalten zu ändern.

## <a name="cwinthreadgetthreadpriority"></a><a name="getthreadpriority"></a>CWinThread:: getthreadpriority

Ruft die aktuelle Thread Prioritätsstufe dieses Threads ab.

```
int GetThreadPriority();
```

### <a name="return-value"></a>Rückgabewert

Die aktuelle Thread Prioritätsstufe innerhalb der Prioritäts Klasse. Der zurückgegebene Wert ist einer der folgenden Werte, der von der höchsten Priorität bis zum niedrigsten aufgelistet wird:

- THREAD_PRIORITY_TIME_CRITICAL

- THREAD_PRIORITY_HIGHEST

- THREAD_PRIORITY_ABOVE_NORMAL

- THREAD_PRIORITY_NORMAL

- THREAD_PRIORITY_BELOW_NORMAL

- THREAD_PRIORITY_LOWEST

- THREAD_PRIORITY_IDLE

Weitere Informationen zu diesen Prioritäten finden Sie unter [SetThreadPriority](/windows/win32/api/processthreadsapi/nf-processthreadsapi-setthreadpriority) in der Windows SDK.

## <a name="cwinthreadinitinstance"></a><a name="initinstance"></a>CWinThread:: InitInstance

`InitInstance`muss überschrieben werden, um jede neue Instanz eines Benutzeroberflächen Threads zu initialisieren.

```
virtual BOOL InitInstance();
```

### <a name="return-value"></a>Rückgabewert

Ungleich NULL, wenn die Initialisierung erfolgreich ist. andernfalls 0.

### <a name="remarks"></a>Bemerkungen

In der Regel überschreiben Sie `InitInstance` , um Aufgaben auszuführen, die bei der ersten Erstellung eines Threads abgeschlossen werden müssen.

Diese Member-Funktion wird nur in Benutzeroberflächenthreads verwendet. Führt die Initialisierung von Arbeitsthreads in der Steuerungsfunktion aus, die an [AfxBeginThread](application-information-and-management.md#afxbeginthread)übermittelt wird.

## <a name="cwinthreadisidlemessage"></a><a name="isidlemessage"></a>CWinThread:: isidlemessage

Überschreiben Sie diese Funktion, damit `OnIdle` Sie nicht mehr aufgerufen wird, nachdem bestimmte Meldungen generiert wurden.

```
virtual BOOL IsIdleMessage(MSG* pMsg);
```

### <a name="parameters"></a>Parameter

*pmsg*<br/>
Verweist auf die aktuelle Meldung, die verarbeitet wird.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich NULL `OnIdle` , wenn nach dem Verarbeiten der Nachricht aufgerufen werden soll, andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Die Standard Implementierung ruft `OnIdle` nach redundanten Maus Nachrichten und Nachrichten, die durch blinkende Einfügezeichen generiert werden, nicht auf

Wenn eine Anwendung einen kurzen Timer erstellt hat, `OnIdle` wird häufig aufgerufen, was zu Leistungsproblemen führt. Um die Leistung einer solchen Anwendung zu verbessern, `IsIdleMessage` Überschreiben Sie in der von `CWinApp` abgeleiteten Klasse der Anwendung, um nach WM_TIMER-Nachrichten wie folgt zu suchen:

[!code-cpp[NVC_MFCDocView#189](../../mfc/codesnippet/cpp/cwinthread-class_1.cpp)]

Wenn Sie WM_TIMER auf diese Weise behandeln, wird die Leistung von Anwendungen verbessert, die kurze Timer verwenden.

## <a name="cwinthreadm_bautodelete"></a><a name="m_bautodelete"></a>CWinThread:: m_bAutoDelete

Gibt an, ob das `CWinThread`-Objekt der Threadbeendigung automatisch gelöscht werden soll.

```
BOOL m_bAutoDelete;
```

### <a name="remarks"></a>Bemerkungen

Der `m_bAutoDelete` Datenmember ist eine öffentliche Variable des Typs bool.

Der Wert von `m_bAutoDelete` wirkt sich nicht darauf aus, wie das zugrunde liegende Thread Handle geschlossen wird, sondern wirkt sich auf die zeitliche Schließung des Handles aus. Das Threadhandle wird immer geschlossen, wenn das `CWinThread`-Objekt zerstört wird.

## <a name="cwinthreadm_hthread"></a><a name="m_hthread"></a>CWinThread:: m_hThread

Handle für den Thread, der diesem zugeordnet ist `CWinThread` .

```
HANDLE m_hThread;
```

### <a name="remarks"></a>Bemerkungen

Der `m_hThread` Datenmember ist eine öffentliche Variable des Typs handle. Sie ist nur gültig, wenn das zugrunde liegende Kernel Thread Objekt derzeit vorhanden ist und das Handle noch nicht geschlossen wurde.

Der CWinThread-Dekonstruktor ruft CloseHandle für auf `m_hThread` . Wenn [m_bAutoDelete](#m_bautodelete) true ist, wenn der Thread beendet wird, wird das CWinThread-Objekt zerstört, das alle Zeiger auf das CWinThread-Objekt und seine Member-Variablen ungültig macht. Möglicherweise muss der `m_hThread` Member den Thread Beendigungs Wert überprüfen oder auf ein Signal warten. Wenn das CWinThread-Objekt und dessen `m_hThread` Member während der Thread Ausführung beibehalten werden sollen, und nachdem es beendet wurde, legen `m_bAutoDelete` Sie auf false fest, bevor Sie die Ausführung der Thread Ausführung zulassen. Andernfalls kann der Thread beendet werden, das CWinThread-Objekt zerstören und das Handle schließen, bevor Sie versuchen, es zu verwenden. Wenn Sie dieses Verfahren verwenden, sind Sie dafür verantwortlich, das CWinThread-Objekt zu löschen.

## <a name="cwinthreadm_nthreadid"></a><a name="m_nthreadid"></a>CWinThread:: m_nThreadID

ID des Threads, der diesem zugeordnet ist `CWinThread` .

```
DWORD m_nThreadID;
```

### <a name="remarks"></a>Bemerkungen

Der `m_nThreadID` Datenmember ist eine öffentliche Variable des Typs DWORD. Sie ist nur gültig, wenn das zugrunde liegende Kernel Thread Objekt derzeit vorhanden ist.
Siehe auch Hinweise zur [m_hThread](#m_hthread) Lebensdauer.

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [afxgetthread](application-information-and-management.md#afxgetthread).

## <a name="cwinthreadm_pactivewnd"></a><a name="m_pactivewnd"></a>CWinThread:: m_pActiveWnd

Verwenden Sie diesen Datenmember zum Speichern eines Zeigers auf das aktive Fenster Objekt Ihres Threads.

```
CWnd* m_pActiveWnd;
```

### <a name="remarks"></a>Bemerkungen

Der-Microsoft Foundation Class-Bibliothek beendet Ihren Thread automatisch, wenn das Fenster, auf das von verwiesen `m_pActiveWnd` wird, geschlossen ist. Wenn dieser Thread der primäre Thread für eine Anwendung ist, wird die Anwendung auch beendet. Wenn dieser Datenmember NULL ist, wird das aktive Fenster für das- `CWinApp` Objekt der Anwendung geerbt. `m_pActiveWnd`ist eine öffentliche Variable vom Typ `CWnd*` .

In der Regel legen Sie diese Element Variable fest, wenn Sie überschreiben `InitInstance` . In einem Arbeits Thread wird der Wert dieses Datenmembers von seinem übergeordneten Thread geerbt.

## <a name="cwinthreadm_pmainwnd"></a><a name="m_pmainwnd"></a>CWinThread:: m_pMainWnd

Verwenden Sie diesen Datenmember zum Speichern eines Zeigers auf das Hauptfenster Objekt Ihres Threads.

```
CWnd* m_pMainWnd;
```

### <a name="remarks"></a>Bemerkungen

Der-Microsoft Foundation Class-Bibliothek beendet Ihren Thread automatisch, wenn das Fenster, auf das von verwiesen `m_pMainWnd` wird, geschlossen ist. Wenn dieser Thread der primäre Thread für eine Anwendung ist, wird die Anwendung auch beendet. Wenn dieser Datenmember NULL ist, wird das Hauptfenster für das- `CWinApp` Objekt der Anwendung verwendet, um zu bestimmen, wann der Thread beendet werden soll. `m_pMainWnd`ist eine öffentliche Variable vom Typ `CWnd*` .

In der Regel legen Sie diese Element Variable fest, wenn Sie überschreiben `InitInstance` . In einem Arbeits Thread wird der Wert dieses Datenmembers von seinem übergeordneten Thread geerbt.

## <a name="cwinthreadonidle"></a><a name="onidle"></a>CWinThread:: OnIdle

Überschreiben Sie diese Member-Funktion, um die Leerlaufzeit Verarbeitung auszuführen.

```
virtual BOOL OnIdle(LONG lCount);
```

### <a name="parameters"></a>Parameter

*lCount*<br/>
Ein gegen Mal inkrementierter Wert `OnIdle` wird aufgerufen, wenn die Meldungs Warteschlange des Threads leer ist. Diese Anzahl wird jedes Mal auf 0 zurückgesetzt, wenn eine neue Nachricht verarbeitet wird. Sie können den *lCount* -Parameter verwenden, um die relative Zeitspanne zu bestimmen, in der sich der Thread im Leerlauf befunden hat, ohne eine Nachricht zu verarbeiten.

### <a name="return-value"></a>Rückgabewert

Nicht NULL, um mehr Leerlauf Verarbeitungszeit zu erhalten. 0, wenn keine weitere Leerlauf Verarbeitungszeit benötigt wird.

### <a name="remarks"></a>Bemerkungen

`OnIdle`wird in der Standard Nachrichten Schleife aufgerufen, wenn die Meldungs Warteschlange des Threads leer ist. Verwenden Sie Ihre außer Kraft setzung, um eigene hintergrundhandleraufgaben im Hintergrund aufzurufen.

`OnIdle`gibt 0 zurück, um anzugeben, dass keine zusätzliche Leerlauf Verarbeitungszeit erforderlich ist. Der *lCount* -Parameter wird jedes Mal inkrementiert `OnIdle` , wenn aufgerufen wird, wenn die Nachrichten Warteschlange leer ist, und wird bei jeder Verarbeitung einer neuen Nachricht auf 0 zurückgesetzt. Basierend auf dieser Anzahl können Sie Ihre verschiedenen Leerlauf Routinen aufzurufen.

Die Standard Implementierung dieser Member-Funktion gibt temporäre Objekte und nicht verwendete Dynamic Link Libraries aus dem Arbeitsspeicher frei.

Diese Member-Funktion wird nur in Benutzeroberflächenthreads verwendet.

Da die Anwendung Nachrichten erst dann verarbeiten kann `OnIdle` , wenn Sie zurückgibt, führen Sie in dieser Funktion keine langen Aufgaben aus.

## <a name="cwinthreadoperator-handle"></a><a name="operator_handle"></a>CWinThread:: Operator handle

Ruft das Handle des- `CWinThread` Objekts ab.

```
operator HANDLE() const;
```

### <a name="return-value"></a>Rückgabewert

Wenn erfolgreich, das Handle des Thread Objekts. andernfalls NULL.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie das Handle, um Windows-APIs direkt aufzurufen.

## <a name="cwinthreadpostthreadmessage"></a><a name="postthreadmessage"></a>CWinThread::P ostthreadmessage

Wird aufgerufen, um eine benutzerdefinierte Meldung an ein anderes Objekt zu senden `CWinThread` .

```
BOOL PostThreadMessage(
    UINT message,
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>Parameter

*Nachricht*<br/>
ID der benutzerdefinierten Meldung.

*wParam*<br/>
Der erste Message-Parameter.

*lParam*<br/>
Der zweite Meldungs Parameter.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Die gepostete Nachricht wird durch das Message Map-Makro ON_THREAD_MESSAGE dem richtigen Nachrichten Handler zugeordnet.

> [!NOTE]
> Wenn Sie [PostThreadMessage](/windows/win32/api/winuser/nf-winuser-postthreadmessagew)aufzurufen, wird die Nachricht in der Nachrichten Warteschlange des Threads abgelegt. Da Nachrichten, die auf diese Weise gepostet werden, jedoch keinem Fenster zugeordnet sind, werden Sie von MFC nicht an Nachrichten-oder Befehls Handler weitergeleitet. Um diese Nachrichten zu verarbeiten, überschreiben `PreTranslateMessage()` Sie die-Funktion der von CWinApp abgeleiteten Klasse, und behandeln Sie die Nachrichten manuell.

## <a name="cwinthreadpretranslatemessage"></a><a name="pretranslatemessage"></a>CWinThread::P retranslatemess Age

Überschreiben Sie diese Funktion, um Fenster Meldungen zu filtern, bevor diese an die Windows-Funktionen [translatemess](/windows/win32/api/winuser/nf-winuser-translatemessage) und [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage)gesendet werden.

```
virtual BOOL PreTranslateMessage(MSG* pMsg);
```

### <a name="parameters"></a>Parameter

*pmsg*<br/>
Verweist auf eine [MSG-Struktur](/windows/win32/api/winuser/ns-winuser-msg) , die die zu verarbeitende Meldung enthält.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich 0 (null), wenn die Nachricht in vollständig verarbeitet wurde `PreTranslateMessage` und nicht weiterverarbeitet werden sollte. 0 (null), wenn die Meldung auf normale Weise verarbeitet werden soll.

### <a name="remarks"></a>Bemerkungen

Diese Member-Funktion wird nur in Benutzeroberflächenthreads verwendet.

## <a name="cwinthreadprocessmessagefilter"></a><a name="processmessagefilter"></a>CWinThread::P rocess MessageFilter

Die Hook-Funktion des Frameworks ruft diese Element Funktion auf, um bestimmte Windows-Meldungen zu filtern und darauf zu reagieren.

```
virtual BOOL ProcessMessageFilter(
    int code,
    LPMSG lpMsg);
```

### <a name="parameters"></a>Parameter

*code*<br/>
Gibt einen Hook-Code an. Diese Member-Funktion verwendet den Code, um zu bestimmen, wie *lpmsg* verarbeitet wird.

*lpmsg*<br/>
Ein Zeiger auf eine Windows [MSG-Struktur](/windows/win32/api/winuser/ns-winuser-msg).

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn die Nachricht verarbeitet wird. andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Eine Hook-Funktion verarbeitet Ereignisse, bevor Sie an die normale Nachrichtenverarbeitung der Anwendung gesendet werden.

Wenn Sie diese erweiterte Funktion überschreiben, müssen Sie die Basisklassen Version zum Verwalten der Hook-Verarbeitung des Frameworks aufzurufen.

## <a name="cwinthreadprocesswndprocexception"></a><a name="processwndprocexception"></a>CWinThread::P rocess wndprocexception

Das Framework ruft diese Member-Funktion immer dann auf, wenn der Handler eine Ausnahme abfängt, die in einem der Meldungs-oder Befehls Handler Ihres Threads ausgelöst wird.

```
virtual LRESULT ProcessWndProcException(
    CException* e,
    const MSG* pMsg);
```

### <a name="parameters"></a>Parameter

*e*<br/>
Zeigt auf eine nicht behandelte Ausnahme.

*pmsg*<br/>
Verweist auf eine [MSG-Struktur](/windows/win32/api/winuser/ns-winuser-msg) , die Informationen über die Windows-Meldung enthält, die bewirkt hat, dass das Framework eine Ausnahme ausgelöst hat.

### <a name="return-value"></a>Rückgabewert

-1, wenn eine WM_CREATE Ausnahme generiert wird. andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Nennen Sie diese Member-Funktion nicht direkt.

Die Standard Implementierung dieser Member-Funktion verarbeitet nur Ausnahmen, die aus den folgenden Meldungen generiert werden:

|Get-Help|Aktion|
|-------------|------------|
|WM_CREATE|UN.|
|WM_PAINT|Überprüfen Sie das betroffene Fenster, wodurch verhindert wird, dass eine andere WM_PAINT Nachricht generiert wird.|

Überschreiben Sie diese Member-Funktion, um eine globale Behandlung der Ausnahmen bereitzustellen. Die Basisfunktionalität wird nur aufgerufen, wenn Sie das Standardverhalten anzeigen möchten.

Diese Member-Funktion wird nur in Threads mit einem nachrichtenpump verwendet.

## <a name="cwinthreadpumpmessage"></a><a name="pumpmessage"></a>CWinThread::P umpmessage

Enthält die Nachrichten Schleife des Threads.

```
virtual BOOL PumpMessage();
```

### <a name="remarks"></a>Bemerkungen

`PumpMessage`enthält die Nachrichten Schleife des Threads. `PumpMessage`wird von aufgerufen `CWinThread` , um die Nachrichten des Threads zu verschieben. Sie können direkt aufzurufen `PumpMessage` , um zu erzwingen, dass Nachrichten verarbeitet werden, oder Sie können überschreiben, `PumpMessage` um das Standardverhalten zu ändern.

`PumpMessage`Das direkte Aufrufen und Überschreiben des Standard Verhaltens wird nur für fortgeschrittene Benutzer empfohlen.

## <a name="cwinthreadresumethread"></a><a name="resumethread"></a>CWinThread:: ResumeThread

Wird aufgerufen, um die Ausführung eines von der [SuspendThread](#suspendthread) -Element Funktion angehaltenen Threads fortzusetzen, oder ein Thread, der mit dem CREATE_SUSPENDED-Flag erstellt wurde.

```
DWORD ResumeThread();
```

### <a name="return-value"></a>Rückgabewert

Die vorherige anhalteanzahl des Threads, wenn erfolgreich. `0xFFFFFFFF`andernfalls. Wenn der Rückgabewert 0 (null) ist, wurde der aktuelle Thread nicht angehalten. Wenn der Rückgabewert 1 ist, wurde der Thread angehalten, aber jetzt neu gestartet. Jeder Rückgabewert größer als 1 bedeutet, dass der Thread angehalten wird.

### <a name="remarks"></a>Bemerkungen

Der Unterbrechungs Zähler des aktuellen Threads wird um 1 reduziert. Wenn die Anzahl der Sperren auf 0 (null) reduziert wird, wird die Ausführung des Threads fortgesetzt. Andernfalls bleibt der Thread angehalten.

## <a name="cwinthreadrun"></a><a name="run"></a>CWinThread:: Run

Stellt eine Standard Nachrichten Schleife für Benutzeroberflächenthreads bereit.

```
virtual int Run();
```

### <a name="return-value"></a>Rückgabewert

Ein- **`int`** Wert, der vom Thread zurückgegeben wird. Dieser Wert kann durch Aufrufen von [GetExitCodeThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getexitcodethread)abgerufen werden.

### <a name="remarks"></a>Bemerkungen

`Run`Ruft Windows-Meldungen ab und sendet Sie, bis die Anwendung eine [WM_QUIT](/windows/win32/winmsg/wm-quit) Nachricht empfängt. Wenn die Meldungs Warteschlange des Threads zurzeit keine Nachrichten enthält, wird `Run` aufgerufen, `OnIdle` um die Leerlaufzeit Verarbeitung auszuführen. Eingehende Nachrichten werden an die [pretranslatemess Age](#pretranslatemessage) -Member-Funktion für die spezielle Verarbeitung und dann an die Windows-Funktion [translatemess](/windows/win32/api/winuser/nf-winuser-translatemessage) für die Standardtastatur Übersetzung geleitet. Zum Schluss wird die Windows-Funktion [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage) aufgerufen.

`Run`wird nur selten überschrieben, Sie können es jedoch außer Kraft setzen, um spezielles Verhalten zu implementieren.

Diese Member-Funktion wird nur in Benutzeroberflächenthreads verwendet.

## <a name="cwinthreadsetthreadpriority"></a><a name="setthreadpriority"></a>CWinThread:: SetThreadPriority

Diese Funktion legt die Prioritäts Ebene des aktuellen Threads innerhalb der Prioritäts Klasse fest.

```
BOOL SetThreadPriority(int nPriority);
```

### <a name="parameters"></a>Parameter

*npriorität*<br/>
Gibt die neue Thread Prioritätsstufe innerhalb der Prioritäts Klasse an. Dieser Parameter muss einer der folgenden Werte sein, der von der höchsten Priorität bis zum niedrigsten aufgelistet ist:

- THREAD_PRIORITY_TIME_CRITICAL

- THREAD_PRIORITY_HIGHEST

- THREAD_PRIORITY_ABOVE_NORMAL

- THREAD_PRIORITY_NORMAL

- THREAD_PRIORITY_BELOW_NORMAL

- THREAD_PRIORITY_LOWEST

- THREAD_PRIORITY_IDLE

Weitere Informationen zu diesen Prioritäten finden Sie unter [SetThreadPriority](/windows/win32/api/processthreadsapi/nf-processthreadsapi-setthreadpriority) in der Windows SDK.

### <a name="return-value"></a>Rückgabewert

Nicht-NULL, wenn die Funktion erfolgreich war. andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Sie kann nur aufgerufen werden, nachdem " [kreatethread](#createthread) " erfolgreich zurückgegeben wurde.

## <a name="cwinthreadsuspendthread"></a><a name="suspendthread"></a>CWinThread:: SuspendThread

Erhöht den anhaltezähler des aktuellen Threads.

```
DWORD SuspendThread();
```

### <a name="return-value"></a>Rückgabewert

Die vorherige anhalteanzahl des Threads, wenn erfolgreich. `0xFFFFFFFF`andernfalls.

### <a name="remarks"></a>Bemerkungen

Wenn ein Thread eine Suspend-Anzahl über 0 (null) aufweist, wird dieser Thread nicht ausgeführt. Der Thread kann fortgesetzt werden, indem die [ResumeThread](#resumethread) -Member-Funktion aufgerufen wird.

## <a name="see-also"></a>Weitere Informationen

[CCmdTarget-Klasse](../../mfc/reference/ccmdtarget-class.md)<br/>
[Hierarchie Diagramm](../../mfc/hierarchy-chart.md)<br/>
[CWinApp-Klasse](../../mfc/reference/cwinapp-class.md)<br/>
[CCmdTarget-Klasse](../../mfc/reference/ccmdtarget-class.md)
