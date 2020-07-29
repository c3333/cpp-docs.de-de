---
title: CThreadPool-Klasse
ms.date: 11/04/2016
f1_keywords:
- CThreadPool
- ATLUTIL/ATL::CThreadPool
- ATLUTIL/ATL::CThreadPool::CThreadPool
- ATLUTIL/ATL::CThreadPool::AddRef
- ATLUTIL/ATL::CThreadPool::GetNumThreads
- ATLUTIL/ATL::CThreadPool::GetQueueHandle
- ATLUTIL/ATL::CThreadPool::GetSize
- ATLUTIL/ATL::CThreadPool::GetTimeout
- ATLUTIL/ATL::CThreadPool::Initialize
- ATLUTIL/ATL::CThreadPool::QueryInterface
- ATLUTIL/ATL::CThreadPool::QueueRequest
- ATLUTIL/ATL::CThreadPool::Release
- ATLUTIL/ATL::CThreadPool::SetSize
- ATLUTIL/ATL::CThreadPool::SetTimeout
- ATLUTIL/ATL::CThreadPool::Shutdown
helpviewer_keywords:
- CThreadPool class
ms.assetid: 06683718-01b9-413c-9481-2dc1734ec70f
ms.openlocfilehash: 12b28cd4f54fa426bb6ad2b2710d62b426ada2b6
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226541"
---
# <a name="cthreadpool-class"></a>CThreadPool-Klasse

Diese Klasse stellt einen Pool von Arbeitsthreads bereit, die eine Warteschlange von Arbeits Elementen verarbeiten.

## <a name="syntax"></a>Syntax

```
template <class Worker, class ThreadTraits = DefaultThreadTraits>
class CThreadPool : public IThreadPoolConfig
```

#### <a name="parameters"></a>Parameter

*Arbeiter*<br/>
Die Klasse, die dem [workerarchetype](../../atl/reference/worker-archetype.md) entspricht, der den Code bereitstellt, der zum Verarbeiten von Arbeitsaufgaben im Thread Pool verwendet wird.

*Thread Merkmale*<br/>
Die Klasse, die die Funktion bereitstellt, die zum Erstellen der Threads im Pool verwendet wird.

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|Beschreibung|
|----------|-----------------|
|[CThreadPool:: CThreadPool](#cthreadpool)|Der Konstruktor für den Thread Pool.|
|[CThreadPool:: ~ CThreadPool](#dtor)|Der Dekonstruktor für den Thread Pool.|

### <a name="public-methods"></a>Öffentliche Methoden

|name|Beschreibung|
|----------|-----------------|
|[CThreadPool:: adressf](#addref)|Implementierung von `IUnknown::AddRef`.|
|[CThreadPool:: getnumthreads](#getnumthreads)|Mit dieser Methode können Sie die Anzahl der Threads im Pool abrufen.|
|[CThreadPool:: getqueuehandle](#getqueuehandle)|Mit dieser Methode wird das Handle des e/a-Abschlussports aufgerufen, der für die Warteschlange von Arbeits Elementen|
|[CThreadPool:: GetSize](#getsize)|Mit dieser Methode können Sie die Anzahl der Threads im Pool abrufen.|
|[CThreadPool:: getTimeout](#gettimeout)|Mit dieser Methode können Sie die maximale Zeit in Millisekunden abrufen, die der Thread Pool darauf wartet, dass ein Thread heruntergefahren wird.|
|[CThreadPool:: Initialize](#initialize)|Ruft diese Methode auf, um den Thread Pool zu initialisieren.|
|[CThreadPool:: QueryInterface](#queryinterface)|Implementierung von `IUnknown::QueryInterface`.|
|[CThreadPool:: queuerequest](#queuerequest)|Mit dieser Methode können Sie eine Arbeitsaufgabe in die Warteschlange stellen, die von einem Thread im Pool behandelt werden soll.|
|[CThreadPool:: Release](#release)|Implementierung von `IUnknown::Release`.|
|[CThreadPool:: SetSize](#setsize)|Mit dieser Methode können Sie die Anzahl der Threads im Pool festlegen.|
|[CThreadPool:: setTimeout](#settimeout)|Mit dieser Methode können Sie die maximale Zeit in Millisekunden festlegen, die der Thread Pool darauf wartet, dass ein Thread heruntergefahren wird.|
|[CThreadPool:: Shutdown](#shutdown)|Mit dieser Methode wird der Thread Pool heruntergefahren.|

## <a name="remarks"></a>Bemerkungen

Threads im Pool werden erstellt und zerstört, wenn der Pool initialisiert, verkleinert oder heruntergefahren wird. Eine Instanz der Klasse *Worker* wird auf dem Stapel jedes Arbeitsthreads im Pool erstellt. Jede Instanz wird für die Lebensdauer des Threads verwendet.

Nach der Erstellung eines Threads wird *Worker*:: `Initialize` für das diesem Thread zugeordnete Objekt aufgerufen. Vor der Zerstörung eines Threads wird " *Worker*::" `Terminate` aufgerufen. Beide Methoden müssen ein- **`void`** <strong>\*</strong> Argument akzeptieren. Der Wert dieses Arguments wird über den *pvworkerparam* -Parameter von [CThreadPool:: Initialize](#initialize)an den Thread Pool übergeben.

Wenn Arbeitselemente in der Warteschlange vorhanden sind und Arbeitsthreads für die Arbeit verfügbar sind, Ruft ein Arbeits Thread ein Element aus der Warteschlange ab und ruft die- `Execute` Methode des workerobjekts für diesen Thread auf. *Worker* Anschließend werden drei Elemente an die-Methode weitergegeben: das Element aus der Warteschlange, das `pvWorkerParam` an *Worker*:: `Initialize` und *Worker*:: weitergegeben wurde, `Terminate` und ein Zeiger auf die [über](/windows/win32/api/minwinbase/ns-minwinbase-overlapped) Lapp Ende Struktur, die für die e/a-Abschlussport-Warteschlange verwendet wird

Die *Worker* -Klasse deklariert den Typ der Elemente, die in die Warteschlange für den Thread Pool eingereiht werden, indem Sie eine typedef, *Worker*::, bereitstellt `RequestType` . Dieser Typ muss in einen und aus einem ULONG_PTR umgewandelt werden können.

Ein Beispiel für eine *Worker* -Klasse ist die [cnonstatus-Worker-Klasse](../../atl/reference/cnonstatelessworker-class.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`IUnknown`

[IThreadPoolConfig](../../atl/reference/ithreadpoolconfig-interface.md)

`CThreadPool`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atlutil. h

## <a name="cthreadpooladdref"></a><a name="addref"></a>CThreadPool:: adressf

Implementierung von `IUnknown::AddRef`.

```
ULONG STDMETHODCALLTYPE AddRef() throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt immer 1 zurück.

### <a name="remarks"></a>Bemerkungen

Diese Klasse implementiert die Lebensdauer Steuerung nicht mithilfe der Verweis Zählung.

## <a name="cthreadpoolcthreadpool"></a><a name="cthreadpool"></a>CThreadPool:: CThreadPool

Der Konstruktor für den Thread Pool.

```
CThreadPool() throw();
```

### <a name="remarks"></a>Bemerkungen

Initialisiert den Timeout Wert, der ATLS_DEFAULT_THREADPOOLSHUTDOWNTIMEOUT werden soll. Die Standardzeit beträgt 36 Sekunden. Bei Bedarf können Sie einen eigenen positiven ganzzahligen Wert für dieses Symbol definieren, bevor Sie "atlutil. h" einschließen.

## <a name="cthreadpoolcthreadpool"></a><a name="dtor"></a>CThreadPool:: ~ CThreadPool

Der Dekonstruktor für den Thread Pool.

```
~CThreadPool() throw();
```

### <a name="remarks"></a>Bemerkungen

Ruft [CThreadPool:: Shutdown](#shutdown)auf.

## <a name="cthreadpoolgetnumthreads"></a><a name="getnumthreads"></a>CThreadPool:: getnumthreads

Mit dieser Methode können Sie die Anzahl der Threads im Pool abrufen.

```
int GetNumThreads() throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt die Anzahl der Threads im Pool zurück.

## <a name="cthreadpoolgetqueuehandle"></a><a name="getqueuehandle"></a>CThreadPool:: getqueuehandle

Mit dieser Methode wird das Handle des e/a-Abschlussports aufgerufen, der für die Warteschlange von Arbeits Elementen

```
HANDLE GetQueueHandle() throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt das Warteschlangen handle oder NULL zurück, wenn der Thread Pool nicht initialisiert wurde.

## <a name="cthreadpoolgetsize"></a><a name="getsize"></a>CThreadPool:: GetSize

Mit dieser Methode können Sie die Anzahl der Threads im Pool abrufen.

```
HRESULT STDMETHODCALLTYPE GetSize(int* pnNumThreads) throw();
```

### <a name="parameters"></a>Parameter

*pnnumthreads*<br/>
vorgenommen Adresse der Variablen, die bei Erfolg die Anzahl der Threads im Pool empfängt.

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg S_OK oder bei einem Fehler HRESULT zurück.

## <a name="cthreadpoolgettimeout"></a><a name="gettimeout"></a>CThreadPool:: getTimeout

Mit dieser Methode können Sie die maximale Zeit in Millisekunden abrufen, die der Thread Pool darauf wartet, dass ein Thread heruntergefahren wird.

```
HRESULT STDMETHODCALLTYPE GetTimeout(DWORD* pdwMaxWait) throw();
```

### <a name="parameters"></a>Parameter

*pdwmaxwait*<br/>
vorgenommen Die Adresse der Variablen, die bei Erfolg die maximale Zeit in Millisekunden empfängt, die der Thread Pool auf das Herunterfahren eines Threads wartet.

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg S_OK oder bei einem Fehler HRESULT zurück.

### <a name="remarks"></a>Bemerkungen

Dieser Timeout Wert wird von [CThreadPool:: Shutdown](#shutdown) verwendet, wenn kein anderer Wert für diese Methode angegeben wird.

## <a name="cthreadpoolinitialize"></a><a name="initialize"></a>CThreadPool:: Initialize

Ruft diese Methode auf, um den Thread Pool zu initialisieren.

```
HRESULT Initialize(
    void* pvWorkerParam = NULL,
    int nNumThreads = 0,
    DWORD dwStackSize = 0,
    HANDLE hCompletion = INVALID_HANDLE_VALUE) throw();
```

### <a name="parameters"></a>Parameter

*pvworkerparam*<br/>
Der Worker-Parameter, der an die-,-und-Methoden des Arbeits Thread Objekts übergeben werden soll `Initialize` `Execute` `Terminate` .

*nnumthreads*<br/>
Die angeforderte Anzahl von Threads im Pool.

Wenn *nnumthreads* negativ ist, wird der absolute Wert mit der Anzahl der Prozessoren auf dem Computer multipliziert, um die Gesamtzahl der Threads zu erhalten.

Wenn *nnumthreads* gleich 0 (null) ist, werden ATLS_DEFAULT_THREADSPERPROC mit der Anzahl der Prozessoren auf dem Computer multipliziert, um die Gesamtzahl der Threads zu erhalten.  Der Standardwert ist 2 Threads pro Prozessor. Bei Bedarf können Sie einen eigenen positiven ganzzahligen Wert für dieses Symbol definieren, bevor Sie "atlutil. h" einschließen.

*dwstacksize*<br/>
Die Stapelgröße für jeden Thread im Pool.

*hcompletion*<br/>
Das Handle eines Objekts, das dem Abschlussport zugeordnet werden soll.

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg S_OK oder bei einem Fehler HRESULT zurück.

## <a name="cthreadpoolqueryinterface"></a><a name="queryinterface"></a>CThreadPool:: QueryInterface

Implementierung von `IUnknown::QueryInterface`.

```
HRESULT STDMETHODCALLTYPE QueryInterface(REFIID riid, void** ppv) throw();
```

### <a name="remarks"></a>Bemerkungen

Objekte dieser Klasse können für die `IUnknown` Schnittstellen und [IThreadPoolConfig](../../atl/reference/ithreadpoolconfig-interface.md) erfolgreich abgefragt werden.

## <a name="cthreadpoolqueuerequest"></a><a name="queuerequest"></a>CThreadPool:: queuerequest

Mit dieser Methode können Sie eine Arbeitsaufgabe in die Warteschlange stellen, die von einem Thread im Pool behandelt werden soll.

```
BOOL QueueRequest(Worker::RequestType request) throw();
```

### <a name="parameters"></a>Parameter

*Anforderung*<br/>
Die Anforderung, die in die Warteschlange gestellt werden soll.

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg TRUE zurück, false bei einem Fehler.

### <a name="remarks"></a>Bemerkungen

Mit dieser Methode wird der Warteschlange ein Arbeits Element hinzugefügt. Die Threads im Pool wählen Elemente aus der Warteschlange in der Reihenfolge aus, in der Sie empfangen werden.

## <a name="cthreadpoolrelease"></a><a name="release"></a>CThreadPool:: Release

Implementierung von `IUnknown::Release`.

```
ULONG STDMETHODCALLTYPE Release() throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt immer 1 zurück.

### <a name="remarks"></a>Bemerkungen

Diese Klasse implementiert die Lebensdauer Steuerung nicht mithilfe der Verweis Zählung.

## <a name="cthreadpoolsetsize"></a><a name="setsize"></a>CThreadPool:: SetSize

Mit dieser Methode können Sie die Anzahl der Threads im Pool festlegen.

```
HRESULT STDMETHODCALLTYPE SetSizeint nNumThreads) throw();
```

### <a name="parameters"></a>Parameter

*nnumthreads*<br/>
Die angeforderte Anzahl von Threads im Pool.

Wenn *nnumthreads* negativ ist, wird der absolute Wert mit der Anzahl der Prozessoren auf dem Computer multipliziert, um die Gesamtzahl der Threads zu erhalten.

Wenn *nnumthreads* gleich 0 (null) ist, werden ATLS_DEFAULT_THREADSPERPROC mit der Anzahl der Prozessoren auf dem Computer multipliziert, um die Gesamtzahl der Threads zu erhalten. Der Standardwert ist 2 Threads pro Prozessor. Bei Bedarf können Sie einen eigenen positiven ganzzahligen Wert für dieses Symbol definieren, bevor Sie "atlutil. h" einschließen.

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg S_OK oder bei einem Fehler HRESULT zurück.

### <a name="remarks"></a>Bemerkungen

Wenn die Anzahl der angegebenen Threads kleiner ist als die Anzahl der Threads, die sich derzeit im Pool befinden, fügt das Objekt eine Nachricht zum Herunterfahren in die Warteschlange ein, die von einem wartenden Thread übernommen werden soll. Wenn ein wartender Thread die Nachricht aus der Warteschlange abruft, wird der Thread Pool benachrichtigt, und die Thread Prozedur wird beendet. Dieser Prozess wird wiederholt, bis die Anzahl der Threads im Pool die angegebene Anzahl erreicht oder der Thread nicht innerhalb des durch [getTimeout](#gettimeout) /  [setTimeout](#settimeout)angegebenen Zeitraums beendet wurde. In dieser Situation gibt die Methode ein HRESULT zurück, das wait_timeout entspricht, und die Meldung zum Herunterfahren des ausstehenden wird abgebrochen.

## <a name="cthreadpoolsettimeout"></a><a name="settimeout"></a>CThreadPool:: setTimeout

Mit dieser Methode können Sie die maximale Zeit in Millisekunden festlegen, die der Thread Pool darauf wartet, dass ein Thread heruntergefahren wird.

```
HRESULT STDMETHODCALLTYPE SetTimeout(DWORD dwMaxWait) throw();
```

### <a name="parameters"></a>Parameter

*dwmaxwait*<br/>
Die angeforderte maximale Zeit in Millisekunden, die der Thread Pool darauf wartet, dass ein Thread heruntergefahren wird.

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg S_OK oder bei einem Fehler HRESULT zurück.

### <a name="remarks"></a>Bemerkungen

Das Timeout wird mit ATLS_DEFAULT_THREADPOOLSHUTDOWNTIMEOUT initialisiert. Die Standardzeit beträgt 36 Sekunden. Bei Bedarf können Sie einen eigenen positiven ganzzahligen Wert für dieses Symbol definieren, bevor Sie "atlutil. h" einschließen.

Beachten Sie, dass *dwmaxwait* die Zeit ist, die der Pool darauf wartet, dass ein einzelner Thread heruntergefahren wird. Die maximale Zeit, die zum Entfernen mehrerer Threads aus dem Pool verwendet werden kann, ist möglicherweise etwas kleiner als *dwmaxwait* , multipliziert mit der Anzahl der Threads.

## <a name="cthreadpoolshutdown"></a><a name="shutdown"></a>CThreadPool:: Shutdown

Mit dieser Methode wird der Thread Pool heruntergefahren.

```cpp
void Shutdown(DWORD dwMaxWait = 0) throw();
```

### <a name="parameters"></a>Parameter

*dwmaxwait*<br/>
Die angeforderte maximale Zeit in Millisekunden, die der Thread Pool darauf wartet, dass ein Thread heruntergefahren wird. Wenn 0 oder kein Wert angegeben wird, verwendet diese Methode das von [CThreadPool:: setTimeout](#settimeout)festgelegte Timeout.

### <a name="remarks"></a>Bemerkungen

Diese Methode sendet eine Anforderung zum Herunterfahren an alle Threads im Pool. Wenn das Timeout abläuft, ruft diese Methode [TerminateThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-terminatethread) für jeden Thread auf, der nicht beendet wurde. Diese Methode wird automatisch vom Dekonstruktor der-Klasse aufgerufen.

## <a name="see-also"></a>Siehe auch

[IThreadPoolConfig-Schnittstelle](../../atl/reference/ithreadpoolconfig-interface.md)<br/>
[Defaultthreadmerkmalen](atl-typedefs.md#defaultthreadtraits)<br/>
[Klassen](../../atl/reference/atl-classes.md)
