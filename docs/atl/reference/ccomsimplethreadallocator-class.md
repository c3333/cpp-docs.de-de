---
title: CComSimpleThreadAllocator-Klasse
ms.date: 11/04/2016
f1_keywords:
- CComSimpleThreadAllocator
- ATLBASE/ATL::CComSimpleThreadAllocator
- ATLBASE/ATL::CComSimpleThreadAllocator::GetThread
helpviewer_keywords:
- threading [ATL], selecting threads
- ATL threads
- CComSimpleThreadAllocator class
- ATL threads, allocating
ms.assetid: 66b2166a-8c50-49fd-b8e4-7f293470327d
ms.openlocfilehash: 4a3cce492db4db9f46aeb4efe738ee6a594ddcfc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327344"
---
# <a name="ccomsimplethreadallocator-class"></a>CComSimpleThreadAllocator-Klasse

Diese Klasse verwaltet die `CComAutoThreadModule`Threadauswahl für die Klasse .

## <a name="syntax"></a>Syntax

```
class CComSimpleThreadAllocator
```

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CComSimpleThreadAllocator::GetThread](#getthread)|Wählt einen Thread aus.|

## <a name="remarks"></a>Bemerkungen

`CComSimpleThreadAllocator`verwaltet die Threadauswahl für [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md). `CComSimpleThreadAllocator::GetThread`durchläuft einfach jeden Thread und gibt den nächsten in der Sequenz zurück.

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlbase.h

## <a name="ccomsimplethreadallocatorgetthread"></a><a name="getthread"></a>CComSimpleThreadAllocator::GetThread

Wählt einen Thread aus, indem der nächste Thread in der Sequenz angegeben wird.

```
int GetThread(CComApartment* /* pApt */, int nThreads);
```

### <a name="parameters"></a>Parameter

*pApt*<br/>
Wird in der Standardimplementierung von ATL nicht verwendet.

*nThreads*<br/>
Die maximale Anzahl von Threads im EXE-Modul.

### <a name="return-value"></a>Rückgabewert

Eine ganze Zahl zwischen Null und (*nThreads* - 1). Identifiziert einen der Threads im EXE-Modul.

### <a name="remarks"></a>Bemerkungen

Sie können `GetThread` überschreiben, um eine andere Auswahlmethode bereitzustellen oder den *Parameter pApt* zu verwenden.

`GetThread`wird von [CComAutoThreadModule::CreateInstance](../../atl/reference/ccomautothreadmodule-class.md#createinstance)aufgerufen.

## <a name="see-also"></a>Siehe auch

[CComApartment-Klasse](../../atl/reference/ccomapartment-class.md)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)
