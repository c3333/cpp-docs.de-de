---
title: CComApartment-Klasse
ms.date: 11/04/2016
f1_keywords:
- CComApartment
- ATLBASE/ATL::CComApartment
- ATLBASE/ATL::CComApartment::CComApartment
- ATLBASE/ATL::CComApartment::Apartment
- ATLBASE/ATL::CComApartment::GetLockCount
- ATLBASE/ATL::CComApartment::Lock
- ATLBASE/ATL::CComApartment::Unlock
- ATLBASE/ATL::CComApartment::m_dwThreadID
- ATLBASE/ATL::CComApartment::m_hThread
- ATLBASE/ATL::CComApartment::m_nLockCnt
helpviewer_keywords:
- apartments in ATL EXE modules
- CComApartment class
ms.assetid: dbc177d7-7ee4-45f2-b563-d578a467ca93
ms.openlocfilehash: 13141d27592f6f40ea7b0529c61baba2fe83a10a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321118"
---
# <a name="ccomapartment-class"></a>CComApartment-Klasse

Diese Klasse bietet Unterstützung für die Verwaltung einer Wohnung in einem EXE-Modul mit Threadpool.

> [!IMPORTANT]
> Diese Klasse und ihre Member können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

## <a name="syntax"></a>Syntax

```
class CComApartment
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CComApartment::CComApartment](#ccomapartment)|Der Konstruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CComApartment::Wohnung](#apartment)|Markiert die Startadresse des Threads.|
|[CComApartment::GetLockCount](#getlockcount)|Gibt die aktuelle Sperranzahl des Threads zurück.|
|[CComApartment::Sperre](#lock)|Erhöht die Sperranzahl des Threads.|
|[CComApartment::Entsperren](#unlock)|Dekrementiert die Anzahl der Faden.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CComApartment::m_dwThreadID](#m_dwthreadid)|Enthält den Bezeichner des Threads.|
|[CComApartment::m_hThread](#m_hthread)|Enthält das Handle des Threads.|
|[CComApartment::m_nLockCnt](#m_nlockcnt)|Enthält die aktuelle Sperranzahl des Threads.|

## <a name="remarks"></a>Bemerkungen

`CComApartment`wird von [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md) verwendet, um eine Wohnung in einem mit Einem Thread gepoolten EXE-Modul zu verwalten. `CComApartment`bietet Methoden zum Erhöhen und Dekrementieren der Sperranzahl in einem Thread.

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlbase.h

## <a name="ccomapartmentapartment"></a><a name="apartment"></a>CComApartment::Wohnung

Markiert die Startadresse des Threads.

```
DWORD Apartment();
```

### <a name="return-value"></a>Rückgabewert

Immer 0.

### <a name="remarks"></a>Bemerkungen

Automatisch während [CComAutoThreadModule::Init](../../atl/reference/ccomautothreadmodule-class.md#init)eingestellt.

## <a name="ccomapartmentccomapartment"></a><a name="ccomapartment"></a>CComApartment::CComApartment

Der Konstruktor.

```
CComApartment();
```

### <a name="remarks"></a>Bemerkungen

Initialisiert die `CComApartment` Datenmember [m_nLockCnt](#m_nlockcnt) und [m_hThread](#m_hthread).

## <a name="ccomapartmentgetlockcount"></a><a name="getlockcount"></a>CComApartment::GetLockCount

Gibt die aktuelle Sperranzahl des Threads zurück.

```
LONG GetLockCount();
```

### <a name="return-value"></a>Rückgabewert

Die Sperre zählt für den Thread.

## <a name="ccomapartmentlock"></a><a name="lock"></a>CComApartment::Sperre

Erhöht die Sperranzahl des Threads.

```
LONG Lock();
```

### <a name="return-value"></a>Rückgabewert

Ein Wert, der für Diagnosen oder Tests nützlich sein kann.

### <a name="remarks"></a>Bemerkungen

Wird von [CComAutoThreadModule::Lock](../../atl/reference/ccomautothreadmodule-class.md#lock)aufgerufen.

Die Sperranzahl des Threads wird für statistische Zwecke verwendet.

## <a name="ccomapartmentm_dwthreadid"></a><a name="m_dwthreadid"></a>CComApartment::m_dwThreadID

Enthält den Bezeichner des Threads.

```
DWORD m_dwThreadID;
```

## <a name="ccomapartmentm_hthread"></a><a name="m_hthread"></a>CComApartment::m_hThread

Enthält das Handle des Threads.

```
HANDLE m_hThread;
```

## <a name="ccomapartmentm_nlockcnt"></a><a name="m_nlockcnt"></a>CComApartment::m_nLockCnt

Enthält die aktuelle Sperranzahl des Threads.

```
LONG m_nLockCnt;
```

## <a name="ccomapartmentunlock"></a><a name="unlock"></a>CComApartment::Entsperren

Dekrementiert die Anzahl der Faden.

```
LONG Unlock();
```

### <a name="return-value"></a>Rückgabewert

Ein Wert, der für Diagnosen oder Tests nützlich sein kann.

### <a name="remarks"></a>Bemerkungen

Aufgerufen von [CComAutoThreadModule::Unlock](../../atl/reference/ccomautothreadmodule-class.md#lock).

Die Sperranzahl des Threads wird für statistische Zwecke verwendet.

## <a name="see-also"></a>Siehe auch

[Klassenübersicht](../../atl/atl-class-overview.md)
