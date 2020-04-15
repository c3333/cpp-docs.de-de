---
title: CnoWorkerThread-Klasse
ms.date: 11/04/2016
f1_keywords:
- CNoWorkerThread
- ATLUTIL/ATL::CNoWorkerThread
- ATLUTIL/ATL::CNoWorkerThread::AddHandle
- ATLUTIL/ATL::CNoWorkerThread::AddTimer
- ATLUTIL/ATL::CNoWorkerThread::GetThreadHandle
- ATLUTIL/ATL::CNoWorkerThread::GetThreadId
- ATLUTIL/ATL::CNoWorkerThread::Initialize
- ATLUTIL/ATL::CNoWorkerThread::RemoveHandle
- ATLUTIL/ATL::CNoWorkerThread::Shutdown
helpviewer_keywords:
- CNoWorkerThread class
ms.assetid: 29f06bae-b658-4aac-9c14-331e996d25d1
ms.openlocfilehash: 90056e648a53218ac06083d43ca34870e1ca72fc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326707"
---
# <a name="cnoworkerthread-class"></a>CnoWorkerThread-Klasse

Verwenden Sie diese Klasse `MonitorClass` als Argument für den Vorlagenparameter für Cacheklassen, wenn Sie die dynamische Cachewartung deaktivieren möchten.

> [!IMPORTANT]
> Diese Klasse und ihre Member können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

## <a name="syntax"></a>Syntax

```
class CNoWorkerThread
```

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CnoWorkerThread::AddHandle](#addhandle)|Nicht-funktionales Äquivalent von [CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle).|
|[CNoWorkerThread::AddTimer](#addtimer)|Nicht-funktionales Äquivalent von [CWorkerThread::AddTimer](../../atl/reference/cworkerthread-class.md#addtimer).|
|[CnoWorkerThread::GetThreadHandle](#getthreadhandle)|Nicht-funktionales Äquivalent von [CWorkerThread::GetThreadHandle](../../atl/reference/cworkerthread-class.md#getthreadhandle).|
|[CnoWorkerThread::GetThreadId](#getthreadid)|Nicht-funktionales Äquivalent von [CWorkerThread::GetThreadId](../../atl/reference/cworkerthread-class.md#getthreadid).|
|[CNoWorkerThread::Initialisieren](#initialize)|Nicht-funktionales Äquivalent von [CWorkerThread::Initialize](../../atl/reference/cworkerthread-class.md#initialize).|
|[CNoWorkerThread::RemoveHandle](#removehandle)|Nicht-funktionales Äquivalent von [CWorkerThread::RemoveHandle](../../atl/reference/cworkerthread-class.md#removehandle).|
|[CNoWorkerThread::Shutdown](#shutdown)|Nicht-funktionales Äquivalent von [CWorkerThread::Shutdown](../../atl/reference/cworkerthread-class.md#shutdown).|

## <a name="remarks"></a>Bemerkungen

Diese Klasse bietet dieselbe öffentliche Schnittstelle wie [CWorkerThread](../../atl/reference/cworkerthread-class.md). Es wird erwartet, dass `MonitorClass` diese Schnittstelle vom Vorlagenparameter für Cacheklassen bereitgestellt wird.

Die Methoden in dieser Klasse werden implementiert, um nichts zu tun. Die Methoden, die ein HRESULT zurückgeben, geben immer S_OK zurück, und die Methoden, die eine HANDLE- oder Thread-ID zurückgeben, geben immer 0 zurück.

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlutil.h

## <a name="cnoworkerthreadaddhandle"></a><a name="addhandle"></a>CnoWorkerThread::AddHandle

Nicht-funktionales Äquivalent von [CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle).

```
HRESULT AddHandle(HANDLE /* hObject */,
    IWorkerThreadClient* /* pClient */,
    DWORD_PTR /* dwParam */) throw();
```

### <a name="return-value"></a>Rückgabewert

Immer S_OK zurück.

### <a name="remarks"></a>Bemerkungen

Die von dieser Klasse bereitgestellte Implementierung bringt nichts.

## <a name="cnoworkerthreadaddtimer"></a><a name="addtimer"></a>CNoWorkerThread::AddTimer

Nicht-funktionales Äquivalent von [CWorkerThread::AddTimer](../../atl/reference/cworkerthread-class.md#addtimer).

```
HRESULT AddTimer(DWORD /* dwInterval */,
    IWorkerThreadClient* /* pClient */,
    DWORD_PTR /* dwParam */,
    HANDLE* /* phTimer */) throw();
```

### <a name="return-value"></a>Rückgabewert

Immer S_OK zurück.

### <a name="remarks"></a>Bemerkungen

Die von dieser Klasse bereitgestellte Implementierung bringt nichts.

## <a name="cnoworkerthreadgetthreadhandle"></a><a name="getthreadhandle"></a>CnoWorkerThread::GetThreadHandle

Nicht-funktionales Äquivalent von [CWorkerThread::GetThreadHandle](../../atl/reference/cworkerthread-class.md#getthreadhandle).

```
HANDLE GetThreadHandle() throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt immer NULL zurück.

### <a name="remarks"></a>Bemerkungen

Die von dieser Klasse bereitgestellte Implementierung bringt nichts.

## <a name="cnoworkerthreadgetthreadid"></a><a name="getthreadid"></a>CnoWorkerThread::GetThreadId

Nicht-funktionales Äquivalent von [CWorkerThread::GetThreadId](../../atl/reference/cworkerthread-class.md#getthreadid).

```
DWORD GetThreadId() throw();
```

### <a name="return-value"></a>Rückgabewert

Es wird immer 0 zurückgegeben.

### <a name="remarks"></a>Bemerkungen

Die von dieser Klasse bereitgestellte Implementierung bringt nichts.

## <a name="cnoworkerthreadinitialize"></a><a name="initialize"></a>CNoWorkerThread::Initialisieren

Nicht-funktionales Äquivalent von [CWorkerThread::Initialize](../../atl/reference/cworkerthread-class.md#initialize).

```
HRESULT Initialize() throw();
```

### <a name="return-value"></a>Rückgabewert

Immer S_OK zurück.

### <a name="remarks"></a>Bemerkungen

Die von dieser Klasse bereitgestellte Implementierung bringt nichts.

## <a name="cnoworkerthreadremovehandle"></a><a name="removehandle"></a>CNoWorkerThread::RemoveHandle

Nicht-funktionales Äquivalent von [CWorkerThread::RemoveHandle](../../atl/reference/cworkerthread-class.md#removehandle).

```
HRESULT RemoveHandle(HANDLE /* hObject */) throw();
```

### <a name="return-value"></a>Rückgabewert

Immer S_OK zurück.

### <a name="remarks"></a>Bemerkungen

Die von dieser Klasse bereitgestellte Implementierung bringt nichts.

## <a name="cnoworkerthreadshutdown"></a><a name="shutdown"></a>CNoWorkerThread::Shutdown

Nicht-funktionales Äquivalent von [CWorkerThread::Shutdown](../../atl/reference/cworkerthread-class.md#shutdown).

```
HRESULT Shutdown(DWORD dwWait = ATL_WORKER_THREAD_WAIT) throw();
```

### <a name="return-value"></a>Rückgabewert

Immer S_OK zurück.

### <a name="remarks"></a>Bemerkungen

Die von dieser Klasse bereitgestellte Implementierung bringt nichts.
