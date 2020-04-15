---
title: CWorkerThread-Klasse
ms.date: 11/04/2016
f1_keywords:
- CWorkerThread
- ATLUTIL/ATL::CWorkerThread
- ATLUTIL/ATL::CWorkerThread::CWorkerThread
- ATLUTIL/ATL::CWorkerThread::AddHandle
- ATLUTIL/ATL::CWorkerThread::AddTimer
- ATLUTIL/ATL::CWorkerThread::GetThreadHandle
- ATLUTIL/ATL::CWorkerThread::GetThreadId
- ATLUTIL/ATL::CWorkerThread::Initialize
- ATLUTIL/ATL::CWorkerThread::RemoveHandle
- ATLUTIL/ATL::CWorkerThread::Shutdown
helpviewer_keywords:
- CWorkerThread class
ms.assetid: be79a832-1345-4a36-a13e-a406cc65286f
ms.openlocfilehash: 05e6b432d44927fa7e276792643e29c80c42d822
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330210"
---
# <a name="cworkerthread-class"></a>CWorkerThread-Klasse

Diese Klasse erstellt einen Arbeitsthread oder verwendet einen vorhandenen, wartet auf ein oder mehrere Kernelobjekthandles und führt eine angegebene Clientfunktion aus, wenn eines der Handles signalisiert wird.

> [!IMPORTANT]
> Diese Klasse und ihre Member können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

## <a name="syntax"></a>Syntax

```
template <class ThreadTraits = DefaultThreadTraits>
class CWorkerThread
```

### <a name="parameters"></a>Parameter

*ThreadTraits*<br/>
Die Klasse, die die Threaderstellungsfunktion bereitstellt, z. B. [CRTThreadTraits](../../atl/reference/crtthreadtraits-class.md) oder [Win32ThreadTraits](../../atl/reference/win32threadtraits-class.md).

## <a name="members"></a>Member

### <a name="protected-structures"></a>Geschützte Strukturen

|Name|BESCHREIBUNG|
|----------|-----------------|
|`WorkerClientEntry`||

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CWorkerThread::CWorkerThread](#cworkerthread)|Der Konstruktor für den Arbeitsthread.|
|[CWorkerThread::'CWorkerThread](#dtor)|Der Destruktor für den Arbeitsthread.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CWorkerThread::AddHandle](#addhandle)|Rufen Sie diese Methode auf, um der Liste, die vom Arbeitsthread verwaltet wird, das Handle eines abwartenden Objekts hinzuzufügen.|
|[CWorkerThread::AddTimer](#addtimer)|Rufen Sie diese Methode auf, um der Liste, die vom Arbeitsthread verwaltet wird, einen periodischen, abprüfbaren Timer hinzuzufügen.|
|[CWorkerThread::GetThreadHandle](#getthreadhandle)|Rufen Sie diese Methode auf, um das Threadhandle des Arbeitsthreads abzurufen.|
|[CWorkerThread::GetThreadId](#getthreadid)|Rufen Sie diese Methode auf, um die Thread-ID des Arbeitsthreads abzurufen.|
|[CWorkerThread::Initialisieren](#initialize)|Rufen Sie diese Methode auf, um den Arbeitsthread zu initialisieren.|
|[CWorkerThread::RemoveHandle](#removehandle)|Rufen Sie diese Methode auf, um ein Handle aus der Liste der abwätbaren Objekte zu entfernen.|
|[CWorkerThread::Shutdown](#shutdown)|Rufen Sie diese Methode auf, um den Arbeitsthread herunterzufahren.|

## <a name="remarks"></a>Bemerkungen

### <a name="to-use-cworkerthread"></a>So verwenden Sie CWorkerThread

1. Erstellen Sie eine Instanz dieser Klasse.

1. Aufrufen von [CWorkerThread::Initialize](#initialize).

1. Rufen Sie [CWorkerThread::AddHandle](#addhandle) mit dem Handle eines Kernelobjekts und einem Zeiger auf eine Implementierung von [IWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md)auf.

   \- oder -

   Rufen Sie [CWorkerThread::AddTimer](#addtimer) mit einem Zeiger auf eine Implementierung von [IWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md)auf.

1. Implementieren Sie [IWorkerThreadClient::Ausführen,](../../atl/reference/iworkerthreadclient-interface.md#execute) um Aktionen auszuführen, wenn das Handle oder der Timer signalisiert wird.

1. Um ein Objekt aus der Liste der abwätbaren Objekte zu entfernen, rufen Sie [CWorkerThread::RemoveHandle](#removehandle)auf.

1. Um den Thread zu beenden, rufen Sie [CWorkerThread::Shutdown](#shutdown)auf.

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlutil.h

## <a name="cworkerthreadaddhandle"></a><a name="addhandle"></a>CWorkerThread::AddHandle

Rufen Sie diese Methode auf, um der Liste, die vom Arbeitsthread verwaltet wird, das Handle eines abwartenden Objekts hinzuzufügen.

```
HRESULT AddHandle(
    HANDLE hObject,
    IWorkerThreadClient* pClient,
    DWORD_PTR dwParam) throw();
```

### <a name="parameters"></a>Parameter

*hObject*<br/>
Das Handle für ein abwartendes Objekt.

*pClient*<br/>
Der Zeiger auf die [IWorkerThreadClient-Schnittstelle](../../atl/reference/iworkerthreadclient-interface.md) für das Objekt, das aufgerufen werden soll, wenn der Handle signalisiert wird.

*dwParam*<br/>
Der Parameter, der an [IWorkerThreadClient::Execute](../../atl/reference/iworkerthreadclient-interface.md#execute) übergeben werden soll, wenn das Handle signalisiert wird.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

### <a name="remarks"></a>Bemerkungen

[IWorkerThreadClient::Execute](../../atl/reference/iworkerthreadclient-interface.md#execute) wird über *pClient* aufgerufen, wenn das Handle *hObject*signalisiert wird.

## <a name="cworkerthreadaddtimer"></a><a name="addtimer"></a>CWorkerThread::AddTimer

Rufen Sie diese Methode auf, um der Liste, die vom Arbeitsthread verwaltet wird, einen periodischen, abprüfbaren Timer hinzuzufügen.

```
HRESULT AddTimer(
    DWORD dwInterval,
    IWorkerThreadClient* pClient,
    DWORD_PTR dwParam,
    HANDLE* phTimer) throw();
```

### <a name="parameters"></a>Parameter

*dwInterval*<br/>
Gibt den Zeitraum des Timers in Millisekunden an.

*pClient*<br/>
Der Zeiger auf die [IWorkerThreadClient-Schnittstelle](../../atl/reference/iworkerthreadclient-interface.md) für das Objekt, das aufgerufen werden soll, wenn der Handle signalisiert wird.

*dwParam*<br/>
Der Parameter, der an [IWorkerThreadClient::Execute](../../atl/reference/iworkerthreadclient-interface.md#execute) übergeben werden soll, wenn das Handle signalisiert wird.

*phTimer*<br/>
[out] Adresse der HANDLE-Variablen, die bei Erfolg das Handle an den neu erstellten Timer empfängt.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

### <a name="remarks"></a>Bemerkungen

[IWorkerThreadClient::Execute](../../atl/reference/iworkerthreadclient-interface.md#execute) wird über *pClient* aufgerufen, wenn der Timer signalisiert wird.

Übergeben Sie das Timerhandle von *phTimer* an [CWorkerThread::RemoveHandle,](#removehandle) um den Timer zu schließen.

## <a name="cworkerthreadcworkerthread"></a><a name="cworkerthread"></a>CWorkerThread::CWorkerThread

Der Konstruktor.

```
CWorkerThread() throw();
```

## <a name="cworkerthreadcworkerthread"></a><a name="dtor"></a>CWorkerThread::'CWorkerThread

Der Destruktor.

```
~CWorkerThread() throw();
```

### <a name="remarks"></a>Bemerkungen

Ruft [CWorkerThread::Shutdown](#shutdown)auf.

## <a name="cworkerthreadgetthreadhandle"></a><a name="getthreadhandle"></a>CWorkerThread::GetThreadHandle

Rufen Sie diese Methode auf, um das Threadhandle des Arbeitsthreads abzurufen.

```
HANDLE GetThreadHandle() throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt das Threadhandle oder NULL zurück, wenn der Arbeitsthread nicht initialisiert wurde.

## <a name="cworkerthreadgetthreadid"></a><a name="getthreadid"></a>CWorkerThread::GetThreadId

Rufen Sie diese Methode auf, um die Thread-ID des Arbeitsthreads abzurufen.

```
DWORD GetThreadId() throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt die Thread-ID oder NULL zurück, wenn der Arbeitsthread nicht initialisiert wurde.

## <a name="cworkerthreadinitialize"></a><a name="initialize"></a>CWorkerThread::Initialisieren

Rufen Sie diese Methode auf, um den Arbeitsthread zu initialisieren.

```
HRESULT Initialize() throw();

HRESULT Initialize(CWorkerThread<ThreadTraits>* pThread) throw();
```

### <a name="parameters"></a>Parameter

*Pthread*<br/>
Ein vorhandener Arbeitsthread.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

### <a name="remarks"></a>Bemerkungen

Diese Methode sollte aufgerufen werden, um das Objekt nach der Erstellung oder nach einem Aufruf von [CWorkerThread::Shutdown](#shutdown)zu initialisieren.

Wenn zwei oder `CWorkerThread` mehr Objekte denselben Arbeitsthread verwenden, initialisieren Sie eines von ihnen, ohne `Initialize` Argumente zu übergeben, und übergeben Sie dann einen Zeiger an dieses Objekt an die Methoden der anderen. Die mit dem Zeiger initialisierten Objekte sollten vor dem Objekt, das zum Initialisieren verwendet wird, heruntergefahren werden.

Unter [CWorkerThread::Shutdown](#shutdown) finden Sie Informationen darüber, wie sich das Verhalten dieser Methode ändert, wenn sie mithilfe eines Zeigers auf ein vorhandenes Objekt initialisiert wird.

## <a name="cworkerthreadremovehandle"></a><a name="removehandle"></a>CWorkerThread::RemoveHandle

Rufen Sie diese Methode auf, um ein Handle aus der Liste der abwätbaren Objekte zu entfernen.

```
HRESULT RemoveHandle(HANDLE hObject) throw();
```

### <a name="parameters"></a>Parameter

*hObject*<br/>
Das zu entfernende Handle.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

### <a name="remarks"></a>Bemerkungen

Wenn das Handle entfernt wird, wird [IWorkerThreadClient::CloseHandle](../../atl/reference/iworkerthreadclient-interface.md#closehandle) für das zugeordnete Objekt aufgerufen, das an [AddHandle](#addhandle)übergeben wurde. Wenn dieser Aufruf `CWorkerThread` fehlschlägt, wird die Windows [CloseHandle-Funktion](/windows/win32/api/handleapi/nf-handleapi-closehandle) für das Handle aufrufen.

## <a name="cworkerthreadshutdown"></a><a name="shutdown"></a>CWorkerThread::Shutdown

Rufen Sie diese Methode auf, um den Arbeitsthread herunterzufahren.

```
HRESULT Shutdown(DWORD dwWait = ATL_WORKER_THREAD_WAIT) throw();
```

### <a name="parameters"></a>Parameter

*dwWait*<br/>
Die Zeit in Millisekunden, die auf das Herunterfahren des Arbeitsthreads gewartet werden soll. ATL_WORKER_THREAD_WAIT beträgt standardmäßig 10 Sekunden. Bei Bedarf können Sie einen eigenen Wert für dieses Symbol definieren, bevor Sie atlutil.h einschließen.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück, z. B. wenn der Timeoutwert *dwWait*überschritten wird.

### <a name="remarks"></a>Bemerkungen

Um das Objekt wiederzuverwenden, rufen Sie [CWorkerThread::Initialize](#initialize) auf, nachdem Sie diese Methode aufgerufen haben.

Beachten Sie, dass das Aufrufen `Shutdown` eines Objekts, das mit einem Zeiger auf ein anderes `CWorkerThread` Objekt initialisiert wurde, keine Auswirkungen hat und immer S_OK zurückgibt.

## <a name="see-also"></a>Siehe auch

[DefaultThreadTraits](atl-typedefs.md#defaultthreadtraits)<br/>
[Klassen](../../atl/reference/atl-classes.md)<br/>
[Multithreading: Erstellen von Arbeitsthreads](../../parallel/multithreading-creating-worker-threads.md)<br/>
[IWorkerThreadClient-Schnittstelle](../../atl/reference/iworkerthreadclient-interface.md)
