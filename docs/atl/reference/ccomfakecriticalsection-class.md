---
title: Ccomfakecriticalsection-Klasse
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
ms.openlocfilehash: 5ada0fbed705af34391709653dbd3638fed32bf7
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226580"
---
# <a name="ccomfakecriticalsection-class"></a>Ccomfakecriticalsection-Klasse

Diese Klasse stellt die gleichen Methoden wie [ccomcriticalsection](../../atl/reference/ccomcriticalsection-class.md) bereit, stellt jedoch keinen kritischen Abschnitt bereit.

## <a name="syntax"></a>Syntax

```
class CComFakeCriticalSection
```

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|name|Beschreibung|
|----------|-----------------|
|[Ccomfakecriticalsection:: init](#init)|Führt keine Aktion aus, da kein kritischer Abschnitt vorhanden ist.|
|[Ccomfakecriticalsection:: Lock](#lock)|Führt keine Aktion aus, da kein kritischer Abschnitt vorhanden ist.|
|[Ccomfakecriticalsection:: Term](#term)|Führt keine Aktion aus, da kein kritischer Abschnitt vorhanden ist.|
|[Ccomfakecriticalsection:: Unlock](#unlock)|Führt keine Aktion aus, da kein kritischer Abschnitt vorhanden ist.|

## <a name="remarks"></a>Bemerkungen

`CComFakeCriticalSection`spiegelt die in [ccomcriticalsection](../../atl/reference/ccomcriticalsection-class.md)gefundenen Methoden wider. Stellt jedoch `CComFakeCriticalSection` keinen kritischen Abschnitt bereit. Daher führen seine Methoden keine Aktionen aus.

In der Regel verwenden Sie `CComFakeCriticalSection` einen **`typedef`** Namen, entweder `AutoCriticalSection` oder `CriticalSection` . Bei Verwendung von [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) oder [ccommultithreadmodelnocs](../../atl/reference/ccommultithreadmodelnocs-class.md) **`typedef`** verweisen beide Namen auf `CComFakeCriticalSection` . Wenn Sie [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)verwenden, verweisen Sie auf [ccomautocriticalsection](../../atl/reference/ccomautocriticalsection-class.md) `CComCriticalSection` bzw..

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atlcore. h

## <a name="ccomfakecriticalsectioninit"></a><a name="init"></a>Ccomfakecriticalsection:: init

Führt keine Aktion aus, da kein kritischer Abschnitt vorhanden ist.

```
HRESULT Init() throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt S_OK zurück.

## <a name="ccomfakecriticalsectionlock"></a><a name="lock"></a>Ccomfakecriticalsection:: Lock

Führt keine Aktion aus, da kein kritischer Abschnitt vorhanden ist.

```
HRESULT Lock() throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt S_OK zurück.

## <a name="ccomfakecriticalsectionterm"></a><a name="term"></a>Ccomfakecriticalsection:: Term

Führt keine Aktion aus, da kein kritischer Abschnitt vorhanden ist.

```
HRESULT Term() throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt S_OK zurück.

## <a name="ccomfakecriticalsectionunlock"></a><a name="unlock"></a>Ccomfakecriticalsection:: Unlock

Führt keine Aktion aus, da kein kritischer Abschnitt vorhanden ist.

```
HRESULT Unlock() throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt S_OK zurück.

## <a name="see-also"></a>Siehe auch

[Klassenübersicht](../../atl/atl-class-overview.md)
