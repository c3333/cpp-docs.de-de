---
title: CNonStatelessWorker-Klasse
ms.date: 11/04/2016
f1_keywords:
- CNonStatelessWorker
- ATLUTIL/ATL::CNonStatelessWorker
- ATLUTIL/ATL::CNonStatelessWorker::RequestType
- ATLUTIL/ATL::CNonStatelessWorker::Execute
- ATLUTIL/ATL::CNonStatelessWorker::Initialize
- ATLUTIL/ATL::CNonStatelessWorker::Terminate
helpviewer_keywords:
- CNonStatelessWorker class
ms.assetid: d00936c6-9e7d-49fb-b87d-417b963367d1
ms.openlocfilehash: 6264bb6bc9070b5ce170b294f9db0d371e7b6b71
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81747672"
---
# <a name="cnonstatelessworker-class"></a>CNonStatelessWorker-Klasse

Empfängt Anforderungen von einem Threadpool und gibt sie an ein Workerobjekt weiter, das bei jeder Anforderung erstellt und zerstört wird.

> [!IMPORTANT]
> Diese Klasse und ihre Member können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

## <a name="syntax"></a>Syntax

```
template <class Worker>
class CNonStatelessWorker
```

#### <a name="parameters"></a>Parameter

*Worker*<br/>
Eine Arbeitsthreadklasse, die dem [Workerarchetyp](../../atl/reference/worker-archetype.md) entspricht, der für die Verarbeitung von Anforderungen in der Warteschlange [von CThreadPool](../../atl/reference/cthreadpool-class.md)geeignet ist.

## <a name="members"></a>Member

### <a name="public-typedefs"></a>Öffentliche Typedefs

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CNonStatelessWorker::RequestType](#requesttype)|Implementierung von [WorkerArchetype::RequestType](worker-archetype.md#requesttype).|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CNonStatelessWorker::Ausführen](#execute)|Implementierung von [WorkerArchetype::Execute](worker-archetype.md#execute).|
|[CNonStatelessWorker::Initialisieren](#initialize)|Implementierung von [WorkerArchetype::Initialize](worker-archetype.md#initialize).|
|[CNonStatelessWorker::Beenden](#terminate)|Implementierung von [WorkerArchetype::Terminate](worker-archetype.md#terminate).|

## <a name="remarks"></a>Bemerkungen

Diese Klasse ist ein einfacher Arbeitsthread für die Verwendung mit [CThreadPool](../../atl/reference/cthreadpool-class.md). Diese Klasse bietet keine eigenen Funktionen zur Anforderungsverarbeitung. Stattdessen instanziiert es eine Instanz von *Worker* pro Anforderung und delegiert die Implementierung seiner Methoden an diese Instanz.

Der Vorteil dieser Klasse besteht darin, dass sie eine bequeme Möglichkeit bietet, das Zustandsmodell für vorhandene Arbeitsthreadklassen zu ändern. `CThreadPool`erstellt eine einzelne Arbeitskraft für die Lebensdauer des Threads. Wenn die Workerklasse den Status hält, wird sie über mehrere Anforderungen hinweg verwendet. Durch einfaches Umschließen `CNonStatelessWorker` dieser Klasse in `CThreadPool`der Vorlage vor der Verwendung mit ist die Lebensdauer der Arbeitskraft und des Status, den sie enthält, auf eine einzelne Anforderung beschränkt.

## <a name="requirements"></a>Requirements (Anforderungen)

**Kopfzeile:** atlutil.h

## <a name="cnonstatelessworkerexecute"></a><a name="execute"></a>CNonStatelessWorker::Ausführen

Implementierung von [WorkerArchetype::Execute](worker-archetype.md#execute).

```cpp
void Execute(
    Worker::RequestType request,
    void* pvWorkerParam,
    OVERLAPPED* pOverlapped);
```

### <a name="remarks"></a>Bemerkungen

Diese Methode erstellt eine Instanz der *Worker-Klasse* auf dem Stapel und ruft [Initialize](worker-archetype.md#initialize) für dieses Objekt auf. Wenn die Initialisierung erfolgreich ist, ruft diese Methode auch [Execute](worker-archetype.md#execute) und [Terminate](worker-archetype.md#terminate) für dasselbe Objekt auf.

## <a name="cnonstatelessworkerinitialize"></a><a name="initialize"></a>CNonStatelessWorker::Initialisieren

Implementierung von [WorkerArchetype::Initialize](worker-archetype.md#initialize).

```
BOOL Initialize(void* /* pvParam */) throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt immer TRUE zurück.

### <a name="remarks"></a>Bemerkungen

Diese Klasse führt keine Initialisierung in `Initialize`durch.

## <a name="cnonstatelessworkerrequesttype"></a><a name="requesttype"></a>CNonStatelessWorker::RequestType

Implementierung von [WorkerArchetype::RequestType](worker-archetype.md#requesttype).

```
typedef Worker::RequestType RequestType;
```

### <a name="remarks"></a>Bemerkungen

Diese Klasse behandelt denselben Arbeitsaufgabentyp wie die *Worker* Klasse, die für den Worker-Vorlagenparameter verwendet wird. Weitere Informationen finden Sie unter [CNonStatelessWorker Overview.](../../atl/reference/cnonstatelessworker-class.md)

## <a name="cnonstatelessworkerterminate"></a><a name="terminate"></a>CNonStatelessWorker::Beenden

Implementierung von [WorkerArchetype::Terminate](worker-archetype.md#terminate).

```cpp
void Terminate(void* /* pvParam */) throw();
```

### <a name="remarks"></a>Bemerkungen

Diese Klasse führt keine Bereinigung in `Terminate`durch.

## <a name="see-also"></a>Weitere Informationen

[CThreadPool-Klasse](../../atl/reference/cthreadpool-class.md)<br/>
[Worker Archetype](../../atl/reference/worker-archetype.md)<br/>
[Klassen](../../atl/reference/atl-classes.md)
