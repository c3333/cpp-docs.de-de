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
ms.openlocfilehash: f1aa76514b98bbf12f8e516d3d54f68e8ef4dd7d
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2020
ms.locfileid: "79423141"
---
# <a name="cworkerthread-class"></a>CWorkerThread-Klasse

Diese Klasse erstellt einen Arbeits Thread oder verwendet einen vorhandenen Thread, wartet auf ein oder mehrere Kernel Objekt Handles und führt eine angegebene Client Funktion aus, wenn eines der Handles signalisiert wird.

> [!IMPORTANT]
> Diese Klasse und ihre Member können in Anwendungen, die im Windows-Runtime ausgeführt werden, nicht verwendet werden.

## <a name="syntax"></a>Syntax

```
template <class ThreadTraits = DefaultThreadTraits>
class CWorkerThread
```

### <a name="parameters"></a>Parameter

*Thread Merkmale*<br/>
Die Klasse, die die Thread Erstellungs Funktion bereitstellt, z. [b. crtthreadmerkmalen](../../atl/reference/crtthreadtraits-class.md) oder [Win32ThreadTraits](../../atl/reference/win32threadtraits-class.md).

## <a name="members"></a>Member

### <a name="protected-structures"></a>Geschützte Strukturen

|Name|Beschreibung|
|----------|-----------------|
|`WorkerClientEntry`||

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|Beschreibung|
|----------|-----------------|
|[CWorkerThread:: CWorkerThread](#cworkerthread)|Der Konstruktor für den Arbeits Thread.|
|[CWorkerThread:: ~ CWorkerThread](#dtor)|Der Dekonstruktor für den Arbeits Thread.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|Beschreibung|
|----------|-----------------|
|[CWorkerThread:: addhandle](#addhandle)|Mit dieser Methode können Sie der Liste, die vom Arbeits Thread verwaltet wird, das Handle eines wabbaren Objekts hinzufügen.|
|[CWorkerThread:: addTIMER](#addtimer)|Mit dieser Methode können Sie der Liste, die vom Arbeits Thread verwaltet wird, einen periodischen, aufnutzbaren Timer hinzufügen.|
|[CWorkerThread:: getthreadhandle](#getthreadhandle)|Mit dieser Methode können Sie das Thread Handle des Arbeitsthreads abrufen.|
|[CWorkerThread:: getthreadid](#getthreadid)|Mit dieser Methode können Sie die Thread-ID des Arbeitsthreads abrufen.|
|[CWorkerThread:: Initialize](#initialize)|Ruft diese Methode auf, um den Arbeits Thread zu initialisieren.|
|[CWorkerThread:: removehandle](#removehandle)|Mit dieser Methode können Sie ein Handle aus der Liste der aufnutzbaren Objekte entfernen.|
|[CWorkerThread:: Shutdown](#shutdown)|Mit dieser Methode können Sie den Arbeits Thread beenden.|

## <a name="remarks"></a>Hinweise

### <a name="to-use-cworkerthread"></a>So verwenden Sie CWorkerThread

1. Erstellen Sie eine Instanz dieser Klasse.

1. [CWorkerThread:: Initialize](#initialize)aufruft.

1. Ruft [CWorkerThread:: addhandle](#addhandle) mit dem Handle eines Kernel Objekts und einem Zeiger auf eine Implementierung von [iworkerthreadclient](../../atl/reference/iworkerthreadclient-interface.md)auf.

   \- oder -

   Ruft [CWorkerThread:: addTIMER](#addtimer) mit einem Zeiger auf eine Implementierung von [iworkerthreadclient](../../atl/reference/iworkerthreadclient-interface.md)auf.

1. Implementieren Sie [iworkerthreadclient:: Execute](../../atl/reference/iworkerthreadclient-interface.md#execute) , um eine Aktion auszuführen, wenn das Handle oder der Timer signalisiert wird.

1. Um ein Objekt aus der Liste der aufnutzbaren Objekte zu entfernen, nennen Sie [CWorkerThread:: removehandle](#removehandle).

1. Um den Thread zu beenden, nennen Sie [CWorkerThread:: Shutdown](#shutdown).

## <a name="requirements"></a>Voraussetzungen

**Header:** atlutil. h

##  <a name="addhandle"></a>CWorkerThread:: addhandle

Mit dieser Methode können Sie der Liste, die vom Arbeits Thread verwaltet wird, das Handle eines wabbaren Objekts hinzufügen.

```
HRESULT AddHandle(
    HANDLE hObject,
    IWorkerThreadClient* pClient,
    DWORD_PTR dwParam) throw();
```

### <a name="parameters"></a>Parameter

*hobject*<br/>
Das Handle für ein Objekt, das nicht mehr nutzbar ist.

*pclient*<br/>
Der Zeiger auf die [iworkerthreadclient](../../atl/reference/iworkerthreadclient-interface.md) -Schnittstelle auf dem Objekt, das aufgerufen werden soll, wenn das Handle signalisiert wird.

*dwparam*<br/>
Der Parameter, der an [iworkerthreadclient:: Execute](../../atl/reference/iworkerthreadclient-interface.md#execute) übergeben werden soll, wenn das Handle signalisiert wird.

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg S_OK oder bei einem Fehler HRESULT zurück.

### <a name="remarks"></a>Hinweise

[Iworkerthreadclient:: Execute](../../atl/reference/iworkerthreadclient-interface.md#execute) wird über *pclient* aufgerufen, wenn das Handle, *hobject*, signalisiert wird.

##  <a name="addtimer"></a>CWorkerThread:: addTIMER

Mit dieser Methode können Sie der Liste, die vom Arbeits Thread verwaltet wird, einen periodischen, aufnutzbaren Timer hinzufügen.

```
HRESULT AddTimer(
    DWORD dwInterval,
    IWorkerThreadClient* pClient,
    DWORD_PTR dwParam,
    HANDLE* phTimer) throw();
```

### <a name="parameters"></a>Parameter

*dwinterval*<br/>
Gibt den Zeitraum des Timers in Millisekunden an.

*pclient*<br/>
Der Zeiger auf die [iworkerthreadclient](../../atl/reference/iworkerthreadclient-interface.md) -Schnittstelle auf dem Objekt, das aufgerufen werden soll, wenn das Handle signalisiert wird.

*dwparam*<br/>
Der Parameter, der an [iworkerthreadclient:: Execute](../../atl/reference/iworkerthreadclient-interface.md#execute) übergeben werden soll, wenn das Handle signalisiert wird.

*phtimer*<br/>
vorgenommen Adresse der Handle-Variablen, die bei Erfolg das Handle für den neu erstellten Timer empfängt.

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg S_OK oder bei einem Fehler HRESULT zurück.

### <a name="remarks"></a>Hinweise

[Iworkerthreadclient:: Execute](../../atl/reference/iworkerthreadclient-interface.md#execute) wird über *pclient* aufgerufen, wenn der Timer signalisiert wird.

Übergeben Sie das Timer-Handle von *phtimer* an [CWorkerThread:: removehandle](#removehandle) , um den Timer zu schließen.

##  <a name="cworkerthread"></a>CWorkerThread:: CWorkerThread

Der Konstruktor.

```
CWorkerThread() throw();
```

##  <a name="dtor"></a>CWorkerThread:: ~ CWorkerThread

Der Destruktor.

```
~CWorkerThread() throw();
```

### <a name="remarks"></a>Hinweise

Ruft [CWorkerThread:: Shutdown](#shutdown)auf.

##  <a name="getthreadhandle"></a>CWorkerThread:: getthreadhandle

Mit dieser Methode können Sie das Thread Handle des Arbeitsthreads abrufen.

```
HANDLE GetThreadHandle() throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt das Thread handle oder NULL zurück, wenn der Arbeits Thread nicht initialisiert wurde.

##  <a name="getthreadid"></a>CWorkerThread:: getthreadid

Mit dieser Methode können Sie die Thread-ID des Arbeitsthreads abrufen.

```
DWORD GetThreadId() throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt die Thread-ID oder NULL zurück, wenn der Arbeits Thread nicht initialisiert wurde.

##  <a name="initialize"></a>CWorkerThread:: Initialize

Ruft diese Methode auf, um den Arbeits Thread zu initialisieren.

```
HRESULT Initialize() throw();

HRESULT Initialize(CWorkerThread<ThreadTraits>* pThread) throw();
```

### <a name="parameters"></a>Parameter

*pThread*<br/>
Ein vorhandener Arbeits Thread.

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg S_OK oder bei einem Fehler HRESULT zurück.

### <a name="remarks"></a>Hinweise

Diese Methode sollte aufgerufen werden, um das Objekt nach der Erstellung oder nach einem Aufruf von [CWorkerThread:: Shutdown](#shutdown)zu initialisieren.

Wenn zwei oder mehr `CWorkerThread` Objekten denselben Arbeits Thread verwenden, initialisieren Sie einen von Ihnen, ohne Argumente zu übergeben, und übergeben Sie dann einen Zeiger auf das Objekt an die `Initialize` Methoden der anderen. Die-Objekte, die mit dem-Zeiger initialisiert werden, sollten vor dem-Objekt heruntergefahren werden, um Sie zu initialisieren.

Informationen dazu, wie sich das Verhalten dieser Methode ändert, wenn Sie mithilfe eines Zeigers auf ein vorhandenes Objekt initialisiert wird, finden Sie unter [CWorkerThread:: Shutdown](#shutdown) .

##  <a name="removehandle"></a>CWorkerThread:: removehandle

Mit dieser Methode können Sie ein Handle aus der Liste der aufnutzbaren Objekte entfernen.

```
HRESULT RemoveHandle(HANDLE hObject) throw();
```

### <a name="parameters"></a>Parameter

*hobject*<br/>
Das Handle, das entfernt werden soll.

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg S_OK oder bei einem Fehler HRESULT zurück.

### <a name="remarks"></a>Hinweise

Wenn das Handle entfernt wird, wird [iworkerthreadclient:: CloseHandle](../../atl/reference/iworkerthreadclient-interface.md#closehandle) für das zugeordnete Objekt aufgerufen, das an [addhandle](#addhandle)weitergeleitet wurde. Wenn dieser Rückruf fehlschlägt, ruft `CWorkerThread` die Windows [CloseHandle](/windows/win32/api/handleapi/nf-handleapi-closehandle) -Funktion für das Handle auf.

##  <a name="shutdown"></a>CWorkerThread:: Shutdown

Mit dieser Methode können Sie den Arbeits Thread beenden.

```
HRESULT Shutdown(DWORD dwWait = ATL_WORKER_THREAD_WAIT) throw();
```

### <a name="parameters"></a>Parameter

*dwwait*<br/>
Die Zeit in Millisekunden, die auf das Herunterfahren des Arbeitsthreads gewartet werden soll. ATL_WORKER_THREAD_WAIT standardmäßig 10 Sekunden. Falls erforderlich, können Sie einen eigenen Wert für dieses Symbol definieren, bevor Sie "atlutil. h" einschließen.

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg S_OK oder einen Fehler HRESULT bei einem Fehler zurück, z. b. wenn der Timeout Wert, *dwwait*, überschritten wird.

### <a name="remarks"></a>Hinweise

Um das-Objekt wiederzuverwenden, rufen Sie [CWorkerThread:: Initialize](#initialize) nach dem Aufruf dieser Methode auf.

Beachten Sie, dass das Aufrufen von `Shutdown` für ein Objekt, das mit einem Zeiger auf ein anderes `CWorkerThread` Objekt initialisiert wird, keine Auswirkung hat und immer S_OK zurückgibt

## <a name="see-also"></a>Siehe auch

[Defaultthreadmerkmalen](atl-typedefs.md#defaultthreadtraits)<br/>
[Klassen](../../atl/reference/atl-classes.md)<br/>
[Multithreading: Erstellen von Arbeitsthreads](../../parallel/multithreading-creating-worker-threads.md)<br/>
[IWorkerThreadClient-Schnittstelle](../../atl/reference/iworkerthreadclient-interface.md)
