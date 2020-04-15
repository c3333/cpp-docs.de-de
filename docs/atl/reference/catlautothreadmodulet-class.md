---
title: CAtlAutoThreadModuleT-Klasse
ms.date: 11/04/2016
f1_keywords:
- CAtlAutoThreadModuleT
- ATLBASE/ATL::CAtlAutoThreadModuleT
- ATLBASE/ATL::CAtlAutoThreadModuleT::GetDefaultThreads
helpviewer_keywords:
- CAtlAutoThreadModuleT class
ms.assetid: ae1667c6-3fb8-47bc-b35d-9ea5e9896d7f
ms.openlocfilehash: e7b7a327d7c47c4472b43ed58fbe9ad0556a7620
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321544"
---
# <a name="catlautothreadmodulet-class"></a>CAtlAutoThreadModuleT-Klasse

Diese Klasse stellt Methoden zum Implementieren eines COM-Servers mit Threadpool,Apartmentmodell bereit.

> [!IMPORTANT]
> Diese Klasse und ihre Member können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

## <a name="syntax"></a>Syntax

```
template <class T,
         class ThreadAllocator = CComSimpleThreadAllocator,
         DWORD dwWait = INFINITE>
class ATL_NO_VTABLE CAtlAutoThreadModuleT : public IAtlAutoThreadModule
```

#### <a name="parameters"></a>Parameter

*T*<br/>
Die Klasse, die den COM-Server implementiert.

*ThreadAllocator*<br/>
Die Klassenverwaltung threadauswahl. Der Standardwert ist [CComSimpleThreadAllocator](../../atl/reference/ccomsimplethreadallocator-class.md).

*dwWait*<br/>
Gibt das Timeoutintervall in Millisekunden an. Der Standardwert ist INFINITE, d. h. das Timeoutintervall der Methode verstreicht nie.

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAtlAutoThreadModuleT::GetDefaultThreads](#getdefaultthreads)|Diese statische Funktion berechnet dynamisch und gibt die maximale Anzahl von Threads für das EXE-Modul basierend auf der Anzahl der Prozessoren zurück.|

## <a name="remarks"></a>Bemerkungen

Die Klasse [CAtlAutoThreadModule](../../atl/reference/catlautothreadmodule-class.md) leitet `CAtlAutoThreadModuleT` sich ab, um einen threadgepoolten COM-Server mit Apartmentmodell zu implementieren. Es ersetzt die veraltete Klasse [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md).

> [!NOTE]
> Diese Klasse sollte nicht in einer DLL verwendet werden, da der standardmäßige *dwWait-Wert* von INFINITE einen Deadlock verursacht, wenn die DLL entladen wird.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`IAtlAutoThreadModule`

`CAtlAutoThreadModuleT`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlbase.h

## <a name="catlautothreadmoduletgetdefaultthreads"></a><a name="getdefaultthreads"></a>CAtlAutoThreadModuleT::GetDefaultThreads

Diese statische Funktion berechnet dynamisch und gibt die maximale Anzahl von Threads für das EXE-Modul basierend auf der Anzahl der Prozessoren zurück.

```
static int GetDefaultThreads();
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Threads, die im EXE-Modul erstellt werden sollen.

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Methode, wenn Sie eine andere Methode zum Berechnen der Anzahl von Threads verwenden möchten. Standardmäßig basiert die Anzahl der Threads auf der Anzahl der Prozessoren.

## <a name="see-also"></a>Siehe auch

[IAtlAutoThreadModule-Klasse](../../atl/reference/iatlautothreadmodule-class.md)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)<br/>
[IAtlAutoThreadModule-Klasse](../../atl/reference/iatlautothreadmodule-class.md)<br/>
[Modulklassen](../../atl/atl-module-classes.md)
