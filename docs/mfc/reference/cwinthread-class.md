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
ms.openlocfilehash: f2e95dd3ba8be31633590e37d95dedc8749ebdd8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367419"
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
|[CWinThread::CWinThread](#cwinthread)|Erstellt ein `CWinThread`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CWinThread::CreateThread](#createthread)|Startet die `CWinThread` Ausführung eines Objekts.|
|[CWinThread::ExitInstance](#exitinstance)|Überschreiben, um zu bereinigen, wenn der Thread beendet wird.|
|[CWinThread::GetMainWnd](#getmainwnd)|Ruft einen Zeiger auf das Hauptfenster für den Thread ab.|
|[CWinThread::GetThreadPriority](#getthreadpriority)|Ruft die Priorität des aktuellen Threads ab.|
|[CWinThread::InitInstance](#initinstance)|Überschreiben, um die Threadinstanzinitialisierung durchzuführen.|
|[CWinThread::IsIdleMessage](#isidlemessage)|Überprüft, ob spezielle Nachrichten angezeigt werden.|
|[CwinThread::OnIdle](#onidle)|Überschreiben, um threadspezifische Leerlaufverarbeitung durchzuführen.|
|[CWinThread::PostThreadMessage](#postthreadmessage)|Sendet eine Nachricht `CWinThread` an ein anderes Objekt.|
|[CWinThread::PreTranslateMessage](#pretranslatemessage)|Filtert Nachrichten, bevor sie an die Windows-Funktionen [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) und [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage)gesendet werden.|
|[CWinThread::ProcessMessageFilter](#processmessagefilter)|Fängt bestimmte Nachrichten ab, bevor sie die Anwendung erreichen.|
|[CWinThread::ProcessWndProcException](#processwndprocexception)|Fängt alle nicht behandelten Ausnahmen ab, die von den Nachrichten- und Befehlshandlern des Threads ausgelöst werden.|
|[CWinThread::PumpMessage](#pumpmessage)|Enthält die Nachrichtenschleife des Threads.|
|[CWinThread::ResumeThread](#resumethread)|Dekrementiert die Suspendanzahl eines Threads.|
|[CWinThread::Ausführen](#run)|Steuerungsfunktion für Gewinde mit Einer Nachrichtenpumpe. Überschreiben, um die Standardnachrichtenschleife anzupassen.|
|[CWinThread::SetThreadPriority](#setthreadpriority)|Legt die Priorität des aktuellen Threads fest.|
|[CWinThread::SuspendThread](#suspendthread)|Inkrementiert die Suspend-Anzahl eines Threads.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CWinThread::operator HANDLE](#operator_handle)|Ruft das Handle `CWinThread` des Objekts ab.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CWinThread::m_bAutoDelete](#m_bautodelete)|Gibt an, ob das Objekt bei Threadbeendigung zerstört werden soll.|
|[CWinThread::m_hThread](#m_hthread)|Handle für den aktuellen Thread.|
|[CWinThread::m_nThreadID](#m_nthreadid)|ID des aktuellen Threads.|
|[CWinThread::m_pActiveWnd](#m_pactivewnd)|Zeigen Sie mit dem Zeiger auf das Hauptfenster der Containeranwendung, wenn ein OLE-Server aktiv ist.|
|[CWinThread::m_pMainWnd](#m_pmainwnd)|Hält einen Zeiger auf das Hauptfenster der Anwendung.|

## <a name="remarks"></a>Bemerkungen

Der Hauptthread der Ausführung wird in `CWinApp`der Regel von einem Objekt bereitgestellt, das von abgeleitet ist; `CWinApp` wird von `CWinThread`abgeleitet. Zusätzliche `CWinThread` Objekte ermöglichen mehrere Threads innerhalb einer bestimmten Anwendung.

Es gibt zwei allgemeine `CWinThread` Threadtypen, die unterstützt werden: Arbeitsthreads und Benutzeroberflächenthreads. Arbeitsthreads haben keine Nachrichtenpumpe: z. B. einen Thread, der Hintergrundberechnungen in einer Tabellenkalkulationsanwendung durchführt. Benutzeroberflächenthreads verfügen über eine Nachrichtenpumpe und verarbeiten vom System empfangene Nachrichten. [CWinApp](../../mfc/reference/cwinapp-class.md) und daraus abgeleitete Klassen sind Beispiele für Benutzeroberflächenthreads. Andere Benutzeroberflächenthreads können auch direkt `CWinThread`von abgeleitet werden.

Klassenobjekte `CWinThread` sind in der Regel für die Dauer des Threads vorhanden. Wenn Sie dieses Verhalten ändern möchten, legen Sie [m_bAutoDelete](#m_bautodelete) auf FALSE fest.

Die `CWinThread` Klasse ist erforderlich, um Ihren Code und MFC vollständig threadsicher zu machen. Threadlokale Daten, die vom Framework zum Verwalten threadspezifischer Informationen verwendet werden, werden von `CWinThread` Objekten verwaltet. Aufgrund dieser Abhängigkeit `CWinThread` von der Verarbeitung von threadlokalen Daten muss jeder Thread, der MFC verwendet, von MFC erstellt werden. Beispielsweise kann ein Thread, der von der Laufzeitfunktion [erstellt wurde, _beginthread, _beginthreadex](../../c-runtime-library/reference/beginthread-beginthreadex.md) keine MFC-APIs verwenden.

Um einen Thread zu erstellen, rufen Sie [AfxBeginThread](application-information-and-management.md#afxbeginthread)auf. Es gibt zwei Formulare, je nachdem, ob Sie eine Arbeitskraft oder einen Benutzeroberflächenthread wünschen. Wenn Sie einen Benutzeroberflächenthread wünschen, übergeben Sie ihn an `AfxBeginThread` einen Zeiger an die `CRuntimeClass` der `CWinThread`-abgeleiteten Klasse. Wenn Sie einen Arbeitsthread erstellen `AfxBeginThread` möchten, übergeben Sie an einen Zeiger an die steuernde Funktion und den Parameter an die steuernde Funktion. Sowohl für Arbeitsthreads als auch für Benutzeroberflächenthreads können Sie optionale Parameter angeben, die Priorität, Stapelgröße, Erstellungsflags und Sicherheitsattribute ändern. `AfxBeginThread`gibt einen Zeiger auf `CWinThread` das neue Objekt zurück.

Anstatt aufzurufen, `AfxBeginThread`können `CWinThread`Sie ein -derived-Objekt erstellen und dann aufrufen. `CreateThread` Diese zweistufige Konstruktionsmethode ist nützlich, wenn `CWinThread` Sie das Objekt zwischen aufeinander folgender Erstellung und Beendigungen von Threadausführungen wiederverwenden möchten.

Weitere `CWinThread`Informationen zu finden Sie in den Artikeln [Multithreading mit C++ und MFC](../../parallel/multithreading-with-cpp-and-mfc.md), [Multithreading: Erstellen von Benutzeroberflächenthreads](../../parallel/multithreading-creating-user-interface-threads.md), [Multithreading: Erstellen von Arbeitsthreads](../../parallel/multithreading-creating-worker-threads.md)und [Multithreading: Verwenden der Synchronisierungsklassen](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`CWinThread`

## <a name="requirements"></a>Anforderungen

**Header:** afxwin.h

## <a name="cwinthreadcreatethread"></a><a name="createthread"></a>CWinThread::CreateThread

Erstellt einen Thread, der innerhalb des Adressraums des aufrufenden Prozesses ausgeführt werden soll.

```
BOOL CreateThread(
    DWORD dwCreateFlags = 0,
    UINT nStackSize = 0,
    LPSECURITY_ATTRIBUTES lpSecurityAttrs = NULL);
```

### <a name="parameters"></a>Parameter

*dwCreateFlags*<br/>
Gibt ein zusätzliches Flag an, das die Erstellung des Threads steuert. Dieses Flag kann einen von zwei Werten enthalten:

- CREATE_SUSPENDED Starten Sie den Thread mit einer Suspend-Anzahl von 1. Verwenden Sie CREATE_SUSPENDED, wenn Sie Memberdaten `CWinThread` des Objekts initialisieren möchten, z. B. [m_bAutoDelete](#m_bautodelete) oder Member der abgeleiteten Klasse, bevor der Thread ausgeführt wird. Nachdem die Initialisierung abgeschlossen ist, verwenden Sie den [CWinThread::ResumeThread,](#resumethread) um die Threadausführung zu starten. Der Thread wird erst ausgeführt, wenn `CWinThread::ResumeThread` aufgerufen wurde.

- **0** Starten Sie den Thread unmittelbar nach der Erstellung.

*nStackSize*<br/>
Gibt die Stapelgröße für den neuen Thread in Bytes an. Wenn **0**, hat die Stapelgröße standardmäßig die gleiche Größe wie die des primären Threads des Prozesses.

*lpSecurityAttrs*<br/>
Verweist auf eine [SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) Struktur, die die Sicherheitsattribute für den Thread angibt.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn der Thread erfolgreich erstellt wurde; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Verwenden `AfxBeginThread` Sie diese Datei, um ein Threadobjekt zu erstellen und in einem Schritt auszuführen. Verwenden `CreateThread` Sie diese Verwendung, wenn Sie das Threadobjekt zwischen aufeinander folgender Erstellung und Beendigung von Threadausführungen wiederverwenden möchten.

## <a name="cwinthreadcwinthread"></a><a name="cwinthread"></a>CWinThread::CWinThread

Erstellt ein `CWinThread`-Objekt.

```
CWinThread();
```

### <a name="remarks"></a>Bemerkungen

Um mit der Ausführung des Threads zu beginnen, rufen Sie die [CreateThread-Memberfunktion](#createthread) auf. Normalerweise erstellen Sie Threads, indem Sie [AfxBeginThread](application-information-and-management.md#afxbeginthread)aufrufen, das diesen Konstruktor und `CreateThread`.

## <a name="cwinthreadexitinstance"></a><a name="exitinstance"></a>CWinThread::ExitInstance

Wird vom Framework aus einer [Run](#run) selten überschriebenen Run-Memberfunktion aufgerufen, um diese Instanz des Threads zu beenden, oder wenn ein Aufruf von [InitInstance](#initinstance) fehlschlägt.

```
virtual int ExitInstance();
```

### <a name="return-value"></a>Rückgabewert

Der Exitcode des Threads; 0 gibt keine Fehler an, und Werte größer als 0 weisen auf einen Fehler hin. Dieser Wert kann abgerufen werden, indem [GetExitCodeThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getexitcodethread)aufgerufen wird.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Memberfunktion nicht `Run` von überall als innerhalb der Memberfunktion auf. Diese Memberfunktion wird nur in Benutzeroberflächenthreads verwendet.

Die Standardimplementierung dieser Funktion `CWinThread` löscht das Objekt, wenn [m_bAutoDelete](#m_bautodelete) TRUE ist. Überschreiben Sie diese Funktion, wenn Sie eine zusätzliche Bereinigung durchführen möchten, wenn der Thread beendet wird. Ihre Implementierung `ExitInstance` von sollte die Basisklasseversion aufrufen, nachdem ihr Code ausgeführt wurde.

## <a name="cwinthreadgetmainwnd"></a><a name="getmainwnd"></a>CWinThread::GetMainWnd

Wenn es sich bei Ihrer Anwendung um einen OLE-Server handelt, rufen Sie diese Funktion `m_pMainWnd` auf, um einen Zeiger auf das aktive Hauptfenster der Anwendung abzurufen, anstatt direkt auf das Element des Anwendungsobjekts zu verweisen.

```
virtual CWnd* GetMainWnd();
```

### <a name="return-value"></a>Rückgabewert

Diese Funktion gibt einen Zeiger auf einen von zwei Fenstertypen zurück. Wenn Ihr Thread Teil eines OLE-Servers ist und ein Objekt enthält, das in einem aktiven Container aktiv ist, gibt diese Funktion das [CWinApp:m_pActiveWnd](../../mfc/reference/cwinapp-class.md#m_pactivewnd) Datenmember des `CWinThread` Objekts zurück.

Wenn in einem Container kein Objekt vorhanden ist, das in einem Container aktiv ist, oder ihre Anwendung kein OLE-Server ist, gibt diese Funktion den [m_pMainWnd](#m_pmainwnd) Datenmember des Threadobjekts zurück.

### <a name="remarks"></a>Bemerkungen

Bei Benutzeroberflächenthreads entspricht dies dem direkten `m_pActiveWnd` Verweis auf das Element des Anwendungsobjekts.

Wenn es sich bei der Anwendung nicht um einen OLE-Server handelt, entspricht das Aufrufen dieser Funktion dem direkten Verweisen auf den `m_pMainWnd`-Member des Anwendungsobjekts.

Überschreiben Sie diese Funktion, um das Standardverhalten zu ändern.

## <a name="cwinthreadgetthreadpriority"></a><a name="getthreadpriority"></a>CWinThread::GetThreadPriority

Ruft die aktuelle Threadprioritätsebene dieses Threads ab.

```
int GetThreadPriority();
```

### <a name="return-value"></a>Rückgabewert

Die aktuelle Threadprioritätsebene innerhalb der Prioritätsklasse. Der zurückgegebene Wert ist einer der folgenden, von der höchsten Priorität bis zum niedrigsten Wert aufgeführt:

- THREAD_PRIORITY_TIME_CRITICAL

- THREAD_PRIORITY_HIGHEST

- THREAD_PRIORITY_ABOVE_NORMAL

- THREAD_PRIORITY_NORMAL

- THREAD_PRIORITY_BELOW_NORMAL

- THREAD_PRIORITY_LOWEST

- THREAD_PRIORITY_IDLE

Weitere Informationen zu diesen Prioritäten finden Sie unter [SetThreadPriority](/windows/win32/api/processthreadsapi/nf-processthreadsapi-setthreadpriority) im Windows SDK.

## <a name="cwinthreadinitinstance"></a><a name="initinstance"></a>CWinThread::InitInstance

`InitInstance`muss überschrieben werden, um jede neue Instanz eines Benutzeroberflächenthreads zu initialisieren.

```
virtual BOOL InitInstance();
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Initialisierung erfolgreich ist; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

In der Regel `InitInstance` überschreiben Sie, um Aufgaben auszuführen, die abgeschlossen werden müssen, wenn ein Thread zum ersten Mal erstellt wird.

Diese Memberfunktion wird nur in Benutzeroberflächenthreads verwendet. Initialisierung von Arbeitsthreads in der steuernden Funktion, die an [AfxBeginThread](application-information-and-management.md#afxbeginthread)übergeben wird.

## <a name="cwinthreadisidlemessage"></a><a name="isidlemessage"></a>CWinThread::IsIdleMessage

Überschreiben Sie diese `OnIdle` Funktion, um zu verhindern, dass bestimmte Nachrichten aufgerufen werden, nachdem bestimmte Nachrichten generiert wurden.

```
virtual BOOL IsIdleMessage(MSG* pMsg);
```

### <a name="parameters"></a>Parameter

*pMsg*<br/>
Zeigt auf die aktuelle Nachricht, die verarbeitet wird.

### <a name="return-value"></a>Rückgabewert

Ein Wert `OnIdle` ungleich Null, wenn nach der Verarbeitung der Nachricht aufgerufen werden soll; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Die Standardimplementierung ruft `OnIdle` nach redundanten Mausnachrichten und Nachrichten, die von blinkenden Einsern generiert werden, nicht auf.

Wenn eine Anwendung einen kurzen `OnIdle` Timer erstellt hat, wird häufig aufgerufen, was zu Leistungsproblemen führt. Um die Leistung einer solchen Anwendung `IsIdleMessage` zu verbessern, `CWinApp`überschreiben Sie in der -abgeleiteten Klasse der Anwendung, um WM_TIMER Meldungen wie folgt zu überprüfen:

[!code-cpp[NVC_MFCDocView#189](../../mfc/codesnippet/cpp/cwinthread-class_1.cpp)]

Die Handhabung WM_TIMER auf diese Weise die Leistung von Anwendungen verbessern, die kurze Timer verwenden.

## <a name="cwinthreadm_bautodelete"></a><a name="m_bautodelete"></a>CWinThread::m_bAutoDelete

Gibt an, ob das `CWinThread`-Objekt der Threadbeendigung automatisch gelöscht werden soll.

```
BOOL m_bAutoDelete;
```

### <a name="remarks"></a>Bemerkungen

Der `m_bAutoDelete` Datenmember ist eine öffentliche Variable vom Typ BOOL.

Der Wert `m_bAutoDelete` von hat keinen Einfluss darauf, wie das zugrunde liegende Threadhandle geschlossen wird, aber er wirkt sich auf das Timing des Schließens des Handles aus. Das Threadhandle wird immer geschlossen, wenn das `CWinThread`-Objekt zerstört wird.

## <a name="cwinthreadm_hthread"></a><a name="m_hthread"></a>CWinThread::m_hThread

Handle an den Thread, der an diese `CWinThread`angefügt ist.

```
HANDLE m_hThread;
```

### <a name="remarks"></a>Bemerkungen

Der `m_hThread` Datenmember ist eine öffentliche Variable vom Typ HANDLE. Sie ist nur gültig, wenn das zugrunde liegende Kernelthreadobjekt derzeit vorhanden ist und das Handle noch nicht geschlossen wurde.

Der CWinThread-Destruktor `m_hThread`ruft CloseHandle auf . Wenn [m_bAutoDelete](#m_bautodelete) TRUE ist, wenn der Thread beendet wird, wird das CWinThread-Objekt zerstört, wodurch alle Zeiger auf das CWinThread-Objekt und seine Membervariablen ungültig werden. Möglicherweise benötigen `m_hThread` Sie das Element, um den Thread-Ausgangswert zu überprüfen oder auf ein Signal zu warten. Um das CWinThread-Objekt `m_hThread` und sein Member während der `m_bAutoDelete` Threadausführung und nach dem Beenden beizubehalten, legen Sie false fest, bevor Sie die Threadausführung fortsetzen. Andernfalls kann der Thread beendet werden, das CWinThread-Objekt zerstören und das Handle schließen, bevor Sie versuchen, es zu verwenden. Wenn Sie diese Technik verwenden, sind Sie für das Löschen des CWinThread-Objekts verantwortlich.

## <a name="cwinthreadm_nthreadid"></a><a name="m_nthreadid"></a>CWinThread::m_nThreadID

ID des Threads, `CWinThread`der an diese angefügt ist.

```
DWORD m_nThreadID;
```

### <a name="remarks"></a>Bemerkungen

Der `m_nThreadID` Datenmember ist eine öffentliche Variable vom Typ DWORD. Sie ist nur gültig, wenn das zugrunde liegende Kernelthreadobjekt derzeit vorhanden ist.
Siehe auch Bemerkungen [über m_hThread](#m_hthread) Lebenszeit.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [AfxGetThread](application-information-and-management.md#afxgetthread).

## <a name="cwinthreadm_pactivewnd"></a><a name="m_pactivewnd"></a>CWinThread::m_pActiveWnd

Verwenden Sie dieses Datenelement, um einen Zeiger auf das aktive Fensterobjekt des Threads zu speichern.

```
CWnd* m_pActiveWnd;
```

### <a name="remarks"></a>Bemerkungen

Die Microsoft Foundation-Klassenbibliothek beendet den Thread automatisch, wenn das Fenster, auf das von `m_pActiveWnd` verwiesen wird, geschlossen wird. Wenn dieser Thread der primäre Thread für eine Anwendung ist, wird auch die Anwendung beendet. Wenn dieser Datenmember NULL ist, wird das `CWinApp` aktive Fenster für das Objekt der Anwendung vererbt. `m_pActiveWnd`ist eine öffentliche `CWnd*`Variable vom Typ .

In der Regel legen Sie diese `InitInstance`Membervariable fest, wenn Sie überschreiben. In einem Arbeitsthread wird der Wert dieses Datenmembers vom übergeordneten Thread geerbt.

## <a name="cwinthreadm_pmainwnd"></a><a name="m_pmainwnd"></a>CWinThread::m_pMainWnd

Verwenden Sie dieses Datenelement, um einen Zeiger auf das Hauptfensterobjekt des Threads zu speichern.

```
CWnd* m_pMainWnd;
```

### <a name="remarks"></a>Bemerkungen

Die Microsoft Foundation-Klassenbibliothek beendet den Thread automatisch, wenn das Fenster, auf das von `m_pMainWnd` verwiesen wird, geschlossen wird. Wenn dieser Thread der primäre Thread für eine Anwendung ist, wird auch die Anwendung beendet. Wenn dieser Datenmember NULL ist, wird das `CWinApp` Hauptfenster für das Objekt der Anwendung verwendet, um zu bestimmen, wann der Thread beendet werden soll. `m_pMainWnd`ist eine öffentliche `CWnd*`Variable vom Typ .

In der Regel legen Sie diese `InitInstance`Membervariable fest, wenn Sie überschreiben. In einem Arbeitsthread wird der Wert dieses Datenmembers vom übergeordneten Thread geerbt.

## <a name="cwinthreadonidle"></a><a name="onidle"></a>CwinThread::OnIdle

Überschreiben Sie diese Memberfunktion, um die Verarbeitung im Leerlauf durchzuführen.

```
virtual BOOL OnIdle(LONG lCount);
```

### <a name="parameters"></a>Parameter

*lCount*<br/>
Ein Zähler, der `OnIdle` jedes Mal erhöht wird, wenn die Nachrichtenwarteschlange des Threads leer ist. Diese Anzahl wird jedes Mal auf 0 zurückgesetzt, wenn eine neue Nachricht verarbeitet wird. Sie können den *Parameter lCount* verwenden, um die relative Dauer des Threads im Leerlauf zu bestimmen, ohne eine Nachricht zu verarbeiten.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, um mehr Verarbeitungszeit im Leerlauf zu erhalten; 0, wenn keine weitere Verarbeitungszeit im Leerlauf benötigt wird.

### <a name="remarks"></a>Bemerkungen

`OnIdle`wird in der Standardnachrichtenschleife aufgerufen, wenn die Nachrichtenwarteschlange des Threads leer ist. Verwenden Sie Ihre Außerkraftsetzung, um Ihre eigenen Aufgaben im Leerlauf im Leerlauf aufzurufen.

`OnIdle`0 zurückgeben, um anzugeben, dass keine zusätzliche Verarbeitungszeit im Leerlauf erforderlich ist. Der *lCount-Parameter* wird `OnIdle` jedes Mal erhöht, wenn die Nachrichtenwarteschlange leer ist, und wird jedes Mal auf 0 zurückgesetzt, wenn eine neue Nachricht verarbeitet wird. Basierend auf dieser Anzahl können Sie Ihre verschiedenen Leerlaufroutinen aufrufen.

Die Standardimplementierung dieser Memberfunktion gibt temporäre Objekte und nicht verwendete dynamische Verknüpfungsbibliotheken aus dem Arbeitsspeicher frei.

Diese Memberfunktion wird nur in Benutzeroberflächenthreads verwendet.

Da die Anwendung Nachrichten `OnIdle` erst verarbeiten kann, wenn sie zurückgegeben wird, führen Sie in dieser Funktion keine langwierigen Aufgaben aus.

## <a name="cwinthreadoperator-handle"></a><a name="operator_handle"></a>CWinThread::operator HANDLE

Ruft das Handle `CWinThread` des Objekts ab.

```
operator HANDLE() const;
```

### <a name="return-value"></a>Rückgabewert

Wenn erfolgreich, das Handle des Threadobjekts; andernfalls NULL.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie das Handle, um Windows-APIs direkt aufzurufen.

## <a name="cwinthreadpostthreadmessage"></a><a name="postthreadmessage"></a>CWinThread::PostThreadMessage

Wird aufgerufen, um eine benutzerdefinierte Nachricht an ein anderes `CWinThread` Objekt zu senden.

```
BOOL PostThreadMessage(
    UINT message,
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>Parameter

*Nachricht*<br/>
ID der benutzerdefinierten Nachricht.

*wParam*<br/>
Erster Nachrichtenparameter.

*lParam*<br/>
Zweiter Nachrichtenparameter.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Die gesendete Nachricht wird dem richtigen Nachrichtenhandler vom Message Map-Makro ON_THREAD_MESSAGE zugeordnet.

> [!NOTE]
> Wenn Sie [PostThreadMessage](/windows/win32/api/winuser/nf-winuser-postthreadmessagew)aufrufen, wird die Nachricht in der Nachrichtenwarteschlange des Threads platziert. Da auf diese Weise gesendete Nachrichten jedoch keinem Fenster zugeordnet sind, werden sie von MFC nicht an Nachrichten- oder Befehlshandler gesendet. Um diese Nachrichten zu verarbeiten, `PreTranslateMessage()` überschreiben Sie die Funktion Ihrer von CWinApp abgeleiteten Klasse, und behandeln Sie die Nachrichten manuell.

## <a name="cwinthreadpretranslatemessage"></a><a name="pretranslatemessage"></a>CWinThread::PreTranslateMessage

Überschreiben Sie diese Funktion, um Fenstermeldungen zu filtern, bevor sie an die Windows-Funktionen [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) und [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage)gesendet werden.

```
virtual BOOL PreTranslateMessage(MSG* pMsg);
```

### <a name="parameters"></a>Parameter

*pMsg*<br/>
Verweist auf eine [MSG-Struktur,](/windows/win32/api/winuser/ns-winuser-msg) die die zu verarbeitende Nachricht enthält.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, `PreTranslateMessage` wenn die Nachricht vollständig verarbeitet wurde und nicht weiter verarbeitet werden sollte. Null, wenn die Nachricht auf die normale Weise verarbeitet werden soll.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion wird nur in Benutzeroberflächenthreads verwendet.

## <a name="cwinthreadprocessmessagefilter"></a><a name="processmessagefilter"></a>CWinThread::ProcessMessageFilter

Die Hook-Funktion des Frameworks ruft diese Memberfunktion auf, um bestimmte Windows-Nachrichten zu filtern und darauf zu reagieren.

```
virtual BOOL ProcessMessageFilter(
    int code,
    LPMSG lpMsg);
```

### <a name="parameters"></a>Parameter

*Code*<br/>
Gibt einen Hookcode an. Diese Memberfunktion verwendet den Code, um zu bestimmen, wie *lpMsg* verarbeitet wird.

*lpMsg*<br/>
Ein Zeiger auf eine Windows [MSG-Struktur](/windows/win32/api/winuser/ns-winuser-msg).

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Nachricht verarbeitet wird; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Eine Hook-Funktion verarbeitet Ereignisse, bevor sie an die normale Nachrichtenverarbeitung der Anwendung gesendet werden.

Wenn Sie diese erweiterte Funktion überschreiben, rufen Sie die Basisklasseversion auf, um die Hook-Verarbeitung des Frameworks beizubehalten.

## <a name="cwinthreadprocesswndprocexception"></a><a name="processwndprocexception"></a>CWinThread::ProcessWndProcException

Das Framework ruft diese Memberfunktion auf, wenn der Handler keine Ausnahme abfängt, die in einem der Nachrichten- oder Befehlshandler des Threads ausgelöst wird.

```
virtual LRESULT ProcessWndProcException(
    CException* e,
    const MSG* pMsg);
```

### <a name="parameters"></a>Parameter

*E*<br/>
Verweist auf eine nicht behandelte Ausnahme.

*pMsg*<br/>
Verweist auf eine [MSG-Struktur,](/windows/win32/api/winuser/ns-winuser-msg) die Informationen über die Windows-Meldung enthält, die dazu geführt hat, dass das Framework eine Ausnahme auslöst.

### <a name="return-value"></a>Rückgabewert

-1, wenn eine WM_CREATE Ausnahme generiert wird; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Memberfunktion nicht direkt auf.

Die Standardimplementierung dieser Memberfunktion behandelt nur Ausnahmen, die aus den folgenden Meldungen generiert wurden:

|Get-Help|Aktion|
|-------------|------------|
|Wm_create|Fehler.|
|Wm_paint|Überprüfen Sie das betroffene Fenster, um zu verhindern, dass eine weitere WM_PAINT Nachricht generiert wird.|

Überschreiben Sie diese Memberfunktion, um eine globale Behandlung Ihrer Ausnahmen bereitzustellen. Rufen Sie die Basisfunktionalität nur auf, wenn Sie das Standardverhalten anzeigen möchten.

Diese Memberfunktion wird nur in Threads mit einer Nachrichtenpumpe verwendet.

## <a name="cwinthreadpumpmessage"></a><a name="pumpmessage"></a>CWinThread::PumpMessage

Enthält die Nachrichtenschleife des Threads.

```
virtual BOOL PumpMessage();
```

### <a name="remarks"></a>Bemerkungen

`PumpMessage`enthält die Nachrichtenschleife des Threads. `PumpMessage`wird aufgerufen, `CWinThread` um die Nachrichten des Threads zu pumpen. Sie können `PumpMessage` direkt aufrufen, um die Verarbeitung von `PumpMessage` Nachrichten zu erzwingen, oder Sie können überschreiben, um das Standardverhalten zu ändern.

Das `PumpMessage` direkte Aufrufen und Überschreiben des Standardverhaltens wird nur für fortgeschrittene Benutzer empfohlen.

## <a name="cwinthreadresumethread"></a><a name="resumethread"></a>CWinThread::ResumeThread

Wird aufgerufen, um die Ausführung eines Threads fortzusetzen, der von der [SuspendThread-Memberfunktion](#suspendthread) angehalten wurde, oder eines Threads, der mit dem CREATE_SUSPENDED-Flag erstellt wurde.

```
DWORD ResumeThread();
```

### <a name="return-value"></a>Rückgabewert

Die vorherige Suspend-Anzahl des Threads, wenn sie erfolgreich ist. `0xFFFFFFFF` andernfalls. Wenn der Rückgabewert Null ist, wurde der aktuelle Thread nicht angehalten. Wenn der Rückgabewert eins ist, wurde der Thread angehalten, wird nun aber neu gestartet. Jeder Rückgabewert größer als eins bedeutet, dass der Thread angehalten bleibt.

### <a name="remarks"></a>Bemerkungen

Die Suspend-Anzahl des aktuellen Threads wird um eins reduziert. Wenn die Suspend-Anzahl auf Null reduziert wird, nimmt der Thread die Ausführung wieder auf. Andernfalls bleibt der Thread hängen.

## <a name="cwinthreadrun"></a><a name="run"></a>CWinThread::Ausführen

Stellt eine Standardnachrichtenschleife für Benutzeroberflächenthreads bereit.

```
virtual int Run();
```

### <a name="return-value"></a>Rückgabewert

Ein **int-Wert,** der vom Thread zurückgegeben wird. Dieser Wert kann abgerufen werden, indem [GetExitCodeThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getexitcodethread)aufgerufen wird.

### <a name="remarks"></a>Bemerkungen

`Run`erfasst und sendet Windows-Nachrichten, bis die Anwendung eine [WM_QUIT](/windows/win32/winmsg/wm-quit) Nachricht empfängt. Wenn die Nachrichtenwarteschlange des Threads derzeit `Run` `OnIdle` keine Nachrichten enthält, werden Aufrufe zur Verarbeitung im Leerlauf ausgeführt. Eingehende Nachrichten gehen zur speziellen Verarbeitung an die [PreTranslateMessage-Memberfunktion](#pretranslatemessage) und dann an die Windows-Funktion [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) für die Standardtastaturübersetzung. Schließlich wird die [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage) Windows-Funktion aufgerufen.

`Run`wird selten überschrieben, aber Sie können es überschreiben, um spezielles Verhalten zu implementieren.

Diese Memberfunktion wird nur in Benutzeroberflächenthreads verwendet.

## <a name="cwinthreadsetthreadpriority"></a><a name="setthreadpriority"></a>CWinThread::SetThreadPriority

Diese Funktion legt die Prioritätsebene des aktuellen Threads innerhalb seiner Prioritätsklasse fest.

```
BOOL SetThreadPriority(int nPriority);
```

### <a name="parameters"></a>Parameter

*nPriorität*<br/>
Gibt die neue Threadprioritätsebene innerhalb der Prioritätsklasse an. Dieser Parameter muss einer der folgenden Werte sein, die von der höchsten Priorität bis zum niedrigsten Wert aufgeführt sind:

- THREAD_PRIORITY_TIME_CRITICAL

- THREAD_PRIORITY_HIGHEST

- THREAD_PRIORITY_ABOVE_NORMAL

- THREAD_PRIORITY_NORMAL

- THREAD_PRIORITY_BELOW_NORMAL

- THREAD_PRIORITY_LOWEST

- THREAD_PRIORITY_IDLE

Weitere Informationen zu diesen Prioritäten finden Sie unter [SetThreadPriority](/windows/win32/api/processthreadsapi/nf-processthreadsapi-setthreadpriority) im Windows SDK.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Funktion erfolgreich war; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Sie kann erst aufgerufen werden, nachdem [CreateThread](#createthread) erfolgreich zurückgegeben wurde.

## <a name="cwinthreadsuspendthread"></a><a name="suspendthread"></a>CWinThread::SuspendThread

Inkrementiert die Suspend-Anzahl des aktuellen Threads.

```
DWORD SuspendThread();
```

### <a name="return-value"></a>Rückgabewert

Die vorherige Suspend-Anzahl des Threads, wenn sie erfolgreich ist. `0xFFFFFFFF` andernfalls.

### <a name="remarks"></a>Bemerkungen

Wenn ein Thread eine Suspend-Anzahl über Null hat, wird dieser Thread nicht ausgeführt. Der Thread kann fortgesetzt werden, indem die [ResumeThread-Memberfunktion](#resumethread) aufgerufen wird.

## <a name="see-also"></a>Siehe auch

[CCmdTarget-Klasse](../../mfc/reference/ccmdtarget-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CWinApp-Klasse](../../mfc/reference/cwinapp-class.md)<br/>
[CCmdTarget-Klasse](../../mfc/reference/ccmdtarget-class.md)
