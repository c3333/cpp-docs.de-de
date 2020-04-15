---
title: IConnectionPointContainerImpl-Klasse
ms.date: 11/04/2016
f1_keywords:
- IConnectionPointContainerImpl
- ATLCOM/ATL::IConnectionPointContainerImpl
- ATLCOM/ATL::IConnectionPointContainerImpl::EnumConnectionPoints
- ATLCOM/ATL::IConnectionPointContainerImpl::FindConnectionPoint
helpviewer_keywords:
- connectable objects
- connection points [C++], container
- IConnectionPointContainerImpl class
ms.assetid: 10db5a8d-8be9-4d9d-8a82-8ab9ffe3e9d6
ms.openlocfilehash: f6009a1341d6715d6d2f170d3ff2aa1aa4ffcb96
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329862"
---
# <a name="iconnectionpointcontainerimpl-class"></a>IConnectionPointContainerImpl-Klasse

Diese Klasse implementiert einen Verbindungspunktcontainer, um eine Auflistung von [IConnectionPointImpl-Objekten](../../atl/reference/iconnectionpointimpl-class.md) zu verwalten.

## <a name="syntax"></a>Syntax

```
template<class T>
class ATL_NO_VTABLE IConnectionPointContainerImpl
   : public IConnectionPointContainer
```

#### <a name="parameters"></a>Parameter

*T*<br/>
Ihre Klasse, `IConnectionPointContainerImpl`abgeleitet von .

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[IConnectionPointContainerImpl::EnumConnectionPoints](#enumconnectionpoints)|Erstellt einen Enumerator, der durch die im verbindenden Objekt unterstützten Verbindungspunkte durchlaufen soll.|
|[IConnectionPointContainerImpl::FindConnectionPoint](#findconnectionpoint)|Ruft einen Schnittstellenzeiger auf den Verbindungspunkt ab, der die angegebene IID unterstützt.|

## <a name="remarks"></a>Bemerkungen

`IConnectionPointContainerImpl`implementiert einen Verbindungspunktcontainer, um eine Auflistung von [IConnectionPointImpl-Objekten](../../atl/reference/iconnectionpointimpl-class.md) zu verwalten. `IConnectionPointContainerImpl`stellt zwei Methoden bereit, die ein Client aufrufen kann, um weitere Informationen zu einem verbindenden Objekt abzurufen:

- `EnumConnectionPoints`ermöglicht es dem Client zu bestimmen, welche ausgehenden Schnittstellen das Objekt unterstützt.

- `FindConnectionPoint`ermöglicht es dem Client zu bestimmen, ob das Objekt eine bestimmte ausgehende Schnittstelle unterstützt.

Informationen zur Verwendung von Verbindungspunkten in ATL finden Sie im Artikel [Verbindungspunkte](../../atl/atl-connection-points.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`IConnectionPointContainer`

`IConnectionPointContainerImpl`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlcom.h

## <a name="iconnectionpointcontainerimplenumconnectionpoints"></a><a name="enumconnectionpoints"></a>IConnectionPointContainerImpl::EnumConnectionPoints

Erstellt einen Enumerator, der durch die im verbindenden Objekt unterstützten Verbindungspunkte durchlaufen soll.

```
STDMETHOD(EnumConnectionPoints)(IEnumConnectionPoints** ppEnum);
```

### <a name="remarks"></a>Bemerkungen

Siehe [IConnectionPointContainer::EnumConnectionPoints](/windows/win32/api/ocidl/nf-ocidl-iconnectionpointcontainer-enumconnectionpoints) im Windows SDK.

## <a name="iconnectionpointcontainerimplfindconnectionpoint"></a><a name="findconnectionpoint"></a>IConnectionPointContainerImpl::FindConnectionPoint

Ruft einen Schnittstellenzeiger auf den Verbindungspunkt ab, der die angegebene IID unterstützt.

```
STDMETHOD(FindConnectionPoint)(REFIID riid, IConnectionPoint** ppCP);
```

### <a name="remarks"></a>Bemerkungen

Siehe [IConnectionPointContainer::FindConnectionPoint](/windows/win32/api/ocidl/nf-ocidl-iconnectionpointcontainer-findconnectionpoint) im Windows SDK.

## <a name="see-also"></a>Siehe auch

[Iconnectionpointcontainer](/windows/win32/api/ocidl/nn-ocidl-iconnectionpointcontainer)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)
