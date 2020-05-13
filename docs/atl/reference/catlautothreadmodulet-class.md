---
title: Klasse von "-Klasse"
ms.date: 11/04/2016
f1_keywords:
- CAtlAutoThreadModuleT
- ATLBASE/ATL::CAtlAutoThreadModuleT
- ATLBASE/ATL::CAtlAutoThreadModuleT::GetDefaultThreads
helpviewer_keywords:
- CAtlAutoThreadModuleT class
ms.assetid: ae1667c6-3fb8-47bc-b35d-9ea5e9896d7f
ms.openlocfilehash: 7308e3a51c531fbe942e2df326c03273eeb326e2
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168722"
---
# <a name="catlautothreadmodulet-class"></a>Klasse von "-Klasse"

Diese Klasse stellt Methoden zum Implementieren eines Thread Pool-com-Servers mit einem Thread Pool bereit.

> [!IMPORTANT]
> Diese Klasse und ihre Member können in Anwendungen, die im Windows-Runtime ausgeführt werden, nicht verwendet werden.

## <a name="syntax"></a>Syntax

```cpp
template <class T,
         class ThreadAllocator = CComSimpleThreadAllocator,
         DWORD dwWait = INFINITE>
class ATL_NO_VTABLE CAtlAutoThreadModuleT : public IAtlAutoThreadModule
```

### <a name="parameters"></a>Parameter

*T*<br/>
Die Klasse, mit der der com-Server implementiert wird.

*Thread Zuordnung*<br/>
Die Klasse, die die Thread Auswahl verwaltet. Der Standardwert ist [ccomsimplethreadzuweisung](../../atl/reference/ccomsimplethreadallocator-class.md).

*dwwait*<br/>
Gibt das Timeout Intervall in Millisekunden an. Der Standardwert ist unendlich. Dies bedeutet, dass das Timeout Intervall der Methode nie abläuft.

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|["": Getdefaultthreads](#getdefaultthreads)|Diese statische Funktion berechnet die maximale Anzahl von Threads für das exe-Modul basierend auf der Anzahl der Prozessoren dynamisch und gibt Sie zurück.|

## <a name="remarks"></a>Bemerkungen

Die Klasse [catlaudethreadmodule](../../atl/reference/catlautothreadmodule-class.md) wird von `CAtlAutoThreadModuleT` abgeleitet, um einen in einem Thread zusammengefassten com-Server mit einem Thread Pool zu implementieren. Es ersetzt die veraltete [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md)-Klasse.

> [!NOTE]
> Diese Klasse sollte nicht in einer DLL verwendet werden, da der Standardwert von " *dwwait* " unbegrenzt zu einem Deadlock führt, wenn die DLL entladen wird.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`IAtlAutoThreadModule`

`CAtlAutoThreadModuleT`

## <a name="requirements"></a>Anforderungen

**Header:** atlbase. h

## <a name="catlautothreadmoduletgetdefaultthreads"></a><a name="getdefaultthreads"></a>"": Getdefaultthreads

Diese statische Funktion berechnet die maximale Anzahl von Threads für das exe-Modul basierend auf der Anzahl der Prozessoren dynamisch und gibt Sie zurück.

```cpp
static int GetDefaultThreads();
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Threads, die im exe-Modul erstellt werden sollen.

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Methode, wenn Sie eine andere Methode zum Berechnen der Anzahl von Threads verwenden möchten. Standardmäßig basiert die Anzahl der Threads auf der Anzahl der Prozessoren.

## <a name="see-also"></a>Weitere Informationen:

[Iatlaudethreadmodule-Klasse](../../atl/reference/iatlautothreadmodule-class.md)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)<br/>
[Iatlaudethreadmodule-Klasse](../../atl/reference/iatlautothreadmodule-class.md)<br/>
[Modul Klassen](../../atl/atl-module-classes.md)
