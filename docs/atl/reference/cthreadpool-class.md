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
ms.openlocfilehash: 5e52868f23883836919b96be9aec1815bc1c17b3
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81747446"
---
# <a name="cthreadpool-class"></a>CThreadPool-Klasse

Diese Klasse stellt einen Pool von Arbeitsthreads bereit, die eine Warteschlange von Arbeitsaufgaben verarbeiten.

## <a name="syntax"></a>Syntax

```
template <class Worker, class ThreadTraits = DefaultThreadTraits>
class CThreadPool : public IThreadPoolConfig
```

#### <a name="parameters"></a>Parameter

*Worker*<br/>
Die Klasse, die dem [Workerarchetyp](../../atl/reference/worker-archetype.md) entspricht und den Code bereitstellt, der zum Verarbeiten von Arbeitsaufgaben verwendet wird, die in der Warteschlange des Threadpools stehen.

*ThreadTraits*<br/>
Die Klasse, die die Funktion bereitstellt, die zum Erstellen der Threads im Pool verwendet wird.

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CThreadPool::CThreadPool](#cthreadpool)|Der Konstruktor für den Threadpool.|
|[CThreadPool::'CThreadPool](#dtor)|Der Destruktor für den Threadpool.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CThreadPool::AddRef](#addref)|Implementierung von `IUnknown::AddRef`.|
|[CThreadPool::GetNumThreads](#getnumthreads)|Rufen Sie diese Methode auf, um die Anzahl der Threads im Pool abzurufen.|
|[CthreadPool::GetQueueHandle](#getqueuehandle)|Rufen Sie diese Methode auf, um das Handle des E/A-Abschlussports abzurufen, der zum Warteschlangen von Arbeitsaufgaben verwendet wird.|
|[CThreadPool::GetSize](#getsize)|Rufen Sie diese Methode auf, um die Anzahl der Threads im Pool abzurufen.|
|[CThreadPool::GetTimeout](#gettimeout)|Rufen Sie diese Methode auf, um die maximale Zeit in Millisekunden abzurufen, die der Threadpool auf das Herunterfahren eines Threads wartet.|
|[CThreadPool::Initialisieren](#initialize)|Rufen Sie diese Methode auf, um den Threadpool zu initialisieren.|
|[CThreadPool::QueryInterface](#queryinterface)|Implementierung von `IUnknown::QueryInterface`.|
|[CThreadPool::QueueRequest](#queuerequest)|Rufen Sie diese Methode auf, um eine Arbeitsaufgabe in die Warteschlange zu stellen, die von einem Thread im Pool verarbeitet werden soll.|
|[CThreadPool::Release](#release)|Implementierung von `IUnknown::Release`.|
|[CThreadPool::SetSize](#setsize)|Rufen Sie diese Methode auf, um die Anzahl der Threads im Pool festzulegen.|
|[CThreadPool::SetTimeout](#settimeout)|Rufen Sie diese Methode auf, um die maximale Zeit in Millisekunden festzulegen, die der Threadpool auf das Herunterfahren eines Threads wartet.|
|[CThreadPool::Shutdown](#shutdown)|Rufen Sie diese Methode auf, um den Threadpool herunterzufahren.|

## <a name="remarks"></a>Bemerkungen

Threads im Pool werden erstellt und zerstört, wenn der Pool initialisiert, in der Größe geändert oder heruntergefahren wird. Eine Instanz von Class *Worker* wird auf dem Stapel jedes Arbeitsthreads im Pool erstellt. Jede Instanz wird während der Lebensdauer des Threads leben.

Unmittelbar nach der Erstellung *Worker*eines`Initialize` Threads wird Worker :: für das Objekt aufgerufen, das diesem Thread zugeordnet ist. Unmittelbar vor der Zerstörung *Worker*eines`Terminate` Threads wird Worker :: aufgerufen. Beide Methoden müssen ein **void-Argument** <strong>\*</strong> akzeptieren. Der Wert dieses Arguments wird über den *parameter pvWorkerParam* von [CThreadPool::Initialize](#initialize)an den Threadpool übergeben.

Wenn Arbeitsaufgaben in der Warteschlange vorhanden sind und Arbeitsthreads für die Arbeit verfügbar `Execute` sind, zieht ein Arbeitsthread ein Element aus der Warteschlange und ruft die Methode des *Worker-Objekts* für diesen Thread auf. Drei Elemente werden dann an die Methode übergeben: `pvWorkerParam` das Element aus `Initialize` der Warteschlange, das gleiche an *Worker*übergeben :: und *Worker*:: `Terminate`, und ein Zeiger auf die [OVERLAPPED-Struktur,](/windows/win32/api/minwinbase/ns-minwinbase-overlapped) die für die IO-Abschlussportwarteschlange verwendet wird.

Die *Worker-Klasse* deklariert den Typ der Elemente, die im Threadpool in die `RequestType`Warteschlange eingereiht werden, indem sie einen typedef, *Worker*:: bereitstellt. Dieser Typ muss in der Lage sein, von und zu einem ULONG_PTR.

Ein Beispiel für eine *Worker-Klasse* ist die [CNonStatelessWorker-Klasse](../../atl/reference/cnonstatelessworker-class.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`IUnknown`

[IThreadPoolConfig](../../atl/reference/ithreadpoolconfig-interface.md)

`CThreadPool`

## <a name="requirements"></a>Requirements (Anforderungen)

**Kopfzeile:** atlutil.h

## <a name="cthreadpooladdref"></a><a name="addref"></a>CThreadPool::AddRef

Implementierung von `IUnknown::AddRef`.

```
ULONG STDMETHODCALLTYPE AddRef() throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt immer 1 zurück.

### <a name="remarks"></a>Bemerkungen

Diese Klasse implementiert keine Lebensdauersteuerung mithilfe der Referenzzählung.

## <a name="cthreadpoolcthreadpool"></a><a name="cthreadpool"></a>CThreadPool::CThreadPool

Der Konstruktor für den Threadpool.

```
CThreadPool() throw();
```

### <a name="remarks"></a>Bemerkungen

Initialisiert den Timeoutwert auf ATLS_DEFAULT_THREADPOOLSHUTDOWNTIMEOUT. Die Standardzeit beträgt 36 Sekunden. Bei Bedarf können Sie Ihren eigenen positiven Ganzzahlwert für dieses Symbol definieren, bevor Sie atlutil.h einschließen.

## <a name="cthreadpoolcthreadpool"></a><a name="dtor"></a>CThreadPool::'CThreadPool

Der Destruktor für den Threadpool.

```
~CThreadPool() throw();
```

### <a name="remarks"></a>Bemerkungen

Ruft [cthreadPool::Shutdown](#shutdown)auf.

## <a name="cthreadpoolgetnumthreads"></a><a name="getnumthreads"></a>CThreadPool::GetNumThreads

Rufen Sie diese Methode auf, um die Anzahl der Threads im Pool abzurufen.

```
int GetNumThreads() throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt die Anzahl der Threads im Pool zurück.

## <a name="cthreadpoolgetqueuehandle"></a><a name="getqueuehandle"></a>CthreadPool::GetQueueHandle

Rufen Sie diese Methode auf, um das Handle des E/A-Abschlussports abzurufen, der zum Warteschlangen von Arbeitsaufgaben verwendet wird.

```
HANDLE GetQueueHandle() throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt das Warteschlangenhandle oder NULL zurück, wenn der Threadpool nicht initialisiert wurde.

## <a name="cthreadpoolgetsize"></a><a name="getsize"></a>CThreadPool::GetSize

Rufen Sie diese Methode auf, um die Anzahl der Threads im Pool abzurufen.

```
HRESULT STDMETHODCALLTYPE GetSize(int* pnNumThreads) throw();
```

### <a name="parameters"></a>Parameter

*pnNumThreads*<br/>
[out] Adresse der Variablen, die bei Erfolg die Anzahl der Threads im Pool empfängt.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

## <a name="cthreadpoolgettimeout"></a><a name="gettimeout"></a>CThreadPool::GetTimeout

Rufen Sie diese Methode auf, um die maximale Zeit in Millisekunden abzurufen, die der Threadpool auf das Herunterfahren eines Threads wartet.

```
HRESULT STDMETHODCALLTYPE GetTimeout(DWORD* pdwMaxWait) throw();
```

### <a name="parameters"></a>Parameter

*pdwMaxWait*<br/>
[out] Adresse der Variablen, die bei Erfolg die maximale Zeit in Millisekunden erhält, die der Threadpool auf das Herunterfahren eines Threads wartet.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

### <a name="remarks"></a>Bemerkungen

Dieser Timeoutwert wird von [CThreadPool::Shutdown](#shutdown) verwendet, wenn für diese Methode kein anderer Wert angegeben wird.

## <a name="cthreadpoolinitialize"></a><a name="initialize"></a>CThreadPool::Initialisieren

Rufen Sie diese Methode auf, um den Threadpool zu initialisieren.

```
HRESULT Initialize(
    void* pvWorkerParam = NULL,
    int nNumThreads = 0,
    DWORD dwStackSize = 0,
    HANDLE hCompletion = INVALID_HANDLE_VALUE) throw();
```

### <a name="parameters"></a>Parameter

*pvWorkerParam*<br/>
Der Workerparameter, der an die , `Initialize` `Execute`und `Terminate` Methoden des Arbeitsthreadobjekts übergeben werden soll.

*nNumThreads*<br/>
Die angeforderte Anzahl von Threads im Pool.

Wenn *nNumThreads* negativ ist, wird der absolute Wert mit der Anzahl der Prozessoren auf dem Computer multipliziert, um die Gesamtzahl der Threads abzubekommen.

Wenn *nNumThreads* Null ist, werden ATLS_DEFAULT_THREADSPERPROC mit der Anzahl der Prozessoren auf dem Computer multipliziert, um die Gesamtzahl der Threads abzubekommen.  Der Standardwert ist 2 Threads pro Prozessor. Bei Bedarf können Sie Ihren eigenen positiven Ganzzahlwert für dieses Symbol definieren, bevor Sie atlutil.h einschließen.

*dwStackSize*<br/>
Die Stapelgröße für jeden Thread im Pool.

*hVervollständigen*<br/>
Das Handle eines Objekts, das dem Abschlussport zugeordnet werden soll.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

## <a name="cthreadpoolqueryinterface"></a><a name="queryinterface"></a>CThreadPool::QueryInterface

Implementierung von `IUnknown::QueryInterface`.

```
HRESULT STDMETHODCALLTYPE QueryInterface(REFIID riid, void** ppv) throw();
```

### <a name="remarks"></a>Bemerkungen

Objekte dieser Klasse können erfolgreich für `IUnknown` die und [IThreadPoolConfig-Schnittstellen](../../atl/reference/ithreadpoolconfig-interface.md) abgefragt werden.

## <a name="cthreadpoolqueuerequest"></a><a name="queuerequest"></a>CThreadPool::QueueRequest

Rufen Sie diese Methode auf, um eine Arbeitsaufgabe in die Warteschlange zu stellen, die von einem Thread im Pool verarbeitet werden soll.

```
BOOL QueueRequest(Worker::RequestType request) throw();
```

### <a name="parameters"></a>Parameter

*Anforderung*<br/>
Die Anforderung, die in die Warteschlange eingereiht werden soll.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE bei Erfolg zurück, FALSE bei Fehler.

### <a name="remarks"></a>Bemerkungen

Diese Methode fügt der Warteschlange eine Arbeitsaufgabe hinzu. Die Threads im Pool nehmen Artikel in der Reihenfolge, in der sie empfangen werden, aus der Warteschlange heraus.

## <a name="cthreadpoolrelease"></a><a name="release"></a>CThreadPool::Release

Implementierung von `IUnknown::Release`.

```
ULONG STDMETHODCALLTYPE Release() throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt immer 1 zurück.

### <a name="remarks"></a>Bemerkungen

Diese Klasse implementiert keine Lebensdauersteuerung mithilfe der Referenzzählung.

## <a name="cthreadpoolsetsize"></a><a name="setsize"></a>CThreadPool::SetSize

Rufen Sie diese Methode auf, um die Anzahl der Threads im Pool festzulegen.

```
HRESULT STDMETHODCALLTYPE SetSizeint nNumThreads) throw();
```

### <a name="parameters"></a>Parameter

*nNumThreads*<br/>
Die angeforderte Anzahl von Threads im Pool.

Wenn *nNumThreads* negativ ist, wird der absolute Wert mit der Anzahl der Prozessoren auf dem Computer multipliziert, um die Gesamtzahl der Threads abzubekommen.

Wenn *nNumThreads* Null ist, werden ATLS_DEFAULT_THREADSPERPROC mit der Anzahl der Prozessoren auf dem Computer multipliziert, um die Gesamtzahl der Threads abzubekommen. Der Standardwert ist 2 Threads pro Prozessor. Bei Bedarf können Sie Ihren eigenen positiven Ganzzahlwert für dieses Symbol definieren, bevor Sie atlutil.h einschließen.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

### <a name="remarks"></a>Bemerkungen

Wenn die Anzahl der angegebenen Threads kleiner ist als die Anzahl der Threads, die sich derzeit im Pool befinden, sendet das Objekt eine Abschaltmeldung in die Warteschlange, die von einem wartenden Thread aufgenommen werden soll. Wenn ein wartender Thread die Nachricht aus der Warteschlange zieht, benachrichtigt er den Threadpool und beendet die Threadprozedur. Dieser Vorgang wird wiederholt, bis die Anzahl der Threads im Pool die angegebene Anzahl erreicht oder bis kein Thread innerhalb des von [GetTimeout](#gettimeout)/ [SetTimeout](#settimeout)angegebenen Zeitraums beendet wurde. In diesem Fall gibt die Methode ein HRESULT zurück, das WAIT_TIMEOUT entspricht, und die ausstehende Shutdown-Meldung wird abgebrochen.

## <a name="cthreadpoolsettimeout"></a><a name="settimeout"></a>CThreadPool::SetTimeout

Rufen Sie diese Methode auf, um die maximale Zeit in Millisekunden festzulegen, die der Threadpool auf das Herunterfahren eines Threads wartet.

```
HRESULT STDMETHODCALLTYPE SetTimeout(DWORD dwMaxWait) throw();
```

### <a name="parameters"></a>Parameter

*dwMaxWait*<br/>
Die angeforderte maximale Zeit in Millisekunden, die der Threadpool wartet, bis ein Thread heruntergefahren wird.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

### <a name="remarks"></a>Bemerkungen

Das Timeout wird initialisiert, um ATLS_DEFAULT_THREADPOOLSHUTDOWNTIMEOUT. Die Standardzeit beträgt 36 Sekunden. Bei Bedarf können Sie Ihren eigenen positiven Ganzzahlwert für dieses Symbol definieren, bevor Sie atlutil.h einschließen.

Beachten Sie, dass *dwMaxWait* die Zeit ist, zu der der Pool auf das Herunterfahren eines einzelnen Threads wartet. Die maximale Zeit, die zum Entfernen mehrerer Threads aus dem Pool verwendet werden kann, kann etwas kleiner als *dwMaxWait* multipliziert mit der Anzahl der Threads sein.

## <a name="cthreadpoolshutdown"></a><a name="shutdown"></a>CThreadPool::Shutdown

Rufen Sie diese Methode auf, um den Threadpool herunterzufahren.

```cpp
void Shutdown(DWORD dwMaxWait = 0) throw();
```

### <a name="parameters"></a>Parameter

*dwMaxWait*<br/>
Die angeforderte maximale Zeit in Millisekunden, die der Threadpool wartet, bis ein Thread heruntergefahren wird. Wenn 0 oder kein Wert angegeben wird, verwendet diese Methode das von [CThreadPool::SetTimeout](#settimeout)festgelegte Timeout.

### <a name="remarks"></a>Bemerkungen

Diese Methode sendet eine Herunterfahranforderung an alle Threads im Pool. Wenn das Timeout abläuft, ruft diese Methode [TerminateThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-terminatethread) für jeden Thread auf, der nicht beendet wurde. Diese Methode wird automatisch vom Destruktor der Klasse aufgerufen.

## <a name="see-also"></a>Weitere Informationen

[IThreadPoolConfig-Schnittstelle](../../atl/reference/ithreadpoolconfig-interface.md)<br/>
[DefaultThreadTraits](atl-typedefs.md#defaultthreadtraits)<br/>
[Klassen](../../atl/reference/atl-classes.md)
