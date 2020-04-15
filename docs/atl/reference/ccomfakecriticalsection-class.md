---
title: CComFakeCriticalSection-Klasse
ms.date: 11/04/2016
f1_keywords:
- CComFakeCriticalSection
- ATLCORE/ATL::CComFakeCriticalSection
- ATLCORE/ATL::CComFakeCriticalSection::Init
- ATLCORE/ATL::CComFakeCriticalSection::Lock
- ATLCORE/ATL::CComFakeCriticalSection::Term
- ATLCORE/ATL::CComFakeCriticalSection::Unlock
helpviewer_keywords:
- CComFakeCriticalSection class
ms.assetid: a4811b97-96bb-493b-ab9f-62822aeddb10
ms.openlocfilehash: 4a5b9ba3551397a9c3d59a343e9c6b55b1c1207e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327853"
---
# <a name="ccomfakecriticalsection-class"></a>CComFakeCriticalSection-Klasse

Diese Klasse stellt die gleichen Methoden wie [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md) bereit, bietet jedoch keinen kritischen Abschnitt.

## <a name="syntax"></a>Syntax

```
class CComFakeCriticalSection
```

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CComFakeCriticalSection::Init](#init)|Tut nichts, da es keinen kritischen Abschnitt gibt.|
|[CComFakeCriticalSection::Lock](#lock)|Tut nichts, da es keinen kritischen Abschnitt gibt.|
|[CComFakeCriticalSection::Term](#term)|Tut nichts, da es keinen kritischen Abschnitt gibt.|
|[CComFakeCriticalSection::Entsperren](#unlock)|Tut nichts, da es keinen kritischen Abschnitt gibt.|

## <a name="remarks"></a>Bemerkungen

`CComFakeCriticalSection`spiegelt die Methoden in [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)wider. `CComFakeCriticalSection` Enthält jedoch keinen kritischen Abschnitt. daher tun seine Methoden nichts.

In der `CComFakeCriticalSection` Regel `typedef` verwenden Sie `AutoCriticalSection` `CriticalSection`einen Namen, entweder oder . Bei Verwendung von [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) oder [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)verweisen `typedef` `CComFakeCriticalSection`beide Namen auf . Bei Verwendung von [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)verweisen sie `CComCriticalSection`auf [CComAutoCriticalSection](../../atl/reference/ccomautocriticalsection-class.md) bzw. .

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlcore.h

## <a name="ccomfakecriticalsectioninit"></a><a name="init"></a>CComFakeCriticalSection::Init

Tut nichts, da es keinen kritischen Abschnitt gibt.

```
HRESULT Init() throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt S_OK zurück.

## <a name="ccomfakecriticalsectionlock"></a><a name="lock"></a>CComFakeCriticalSection::Lock

Tut nichts, da es keinen kritischen Abschnitt gibt.

```
HRESULT Lock() throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt S_OK zurück.

## <a name="ccomfakecriticalsectionterm"></a><a name="term"></a>CComFakeCriticalSection::Term

Tut nichts, da es keinen kritischen Abschnitt gibt.

```
HRESULT Term() throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt S_OK zurück.

## <a name="ccomfakecriticalsectionunlock"></a><a name="unlock"></a>CComFakeCriticalSection::Entsperren

Tut nichts, da es keinen kritischen Abschnitt gibt.

```
HRESULT Unlock() throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt S_OK zurück.

## <a name="see-also"></a>Siehe auch

[Klassenübersicht](../../atl/atl-class-overview.md)
