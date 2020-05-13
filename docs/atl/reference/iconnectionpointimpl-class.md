---
title: IConnectionPointImpl-Klasse
ms.date: 11/04/2016
f1_keywords:
- IConnectionPointImpl
- ATLCOM/ATL::IConnectionPointImpl
- ATLCOM/ATL::IConnectionPointImpl::Advise
- ATLCOM/ATL::IConnectionPointImpl::EnumConnections
- ATLCOM/ATL::IConnectionPointImpl::GetConnectionInterface
- ATLCOM/ATL::IConnectionPointImpl::GetConnectionPointContainer
- ATLCOM/ATL::IConnectionPointImpl::Unadvise
- ATLCOM/ATL::IConnectionPointImpl::m_vec
helpviewer_keywords:
- connection points [C++], implementing
- IConnectionPointImpl class
ms.assetid: 27992115-3b86-45dd-bc9e-54f32876c557
ms.openlocfilehash: c62ac3310a579379674674a7a9a517e3f2fd60e5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329851"
---
# <a name="iconnectionpointimpl-class"></a>IConnectionPointImpl-Klasse

Diese Klasse implementiert einen Verbindungspunkt.

## <a name="syntax"></a>Syntax

```
template<class T, const IID* piid, class CDV = CComDynamicUnkArray>
class ATL_NO_VTABLE IConnectionPointImpl : public _ICPLocator<piid>
```

#### <a name="parameters"></a>Parameter

*T*<br/>
Ihre Klasse, `IConnectionPointImpl`abgeleitet von .

*piid*<br/>
Ein Zeiger auf die IID der Schnittstelle, die durch das Verbindungspunktobjekt dargestellt wird.

*Cdv*<br/>
Eine Klasse, die die Verbindungen verwaltet. Der Standardwert ist [CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md), der unbegrenzte Verbindungen zulässt. Sie können auch [CComUnkArray](../../atl/reference/ccomunkarray-class.md)verwenden, das eine feste Anzahl von Verbindungen angibt.

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[IConnectionPointImpl::Beratung](#advise)|Stellt eine Verbindung zwischen dem Verbindungspunkt und einer Senke her.|
|[IConnectionPointImpl::EnumConnections](#enumconnections)|Erstellt einen Enumerator, der durch die Verbindungen für den Verbindungspunkt durchlaufen soll.|
|[IConnectionPointImpl::GetConnectionInterface](#getconnectioninterface)|Ruft die IID der Schnittstelle ab, die durch den Verbindungspunkt dargestellt wird.|
|[IConnectionPointImpl::GetConnectionPointContainer](#getconnectionpointcontainer)|Ruft einen Schnittstellenzeiger zum verbindenden Objekt ab.|
|[IConnectionPointImpl::Unadvise](#unadvise)|Beendet eine zuvor über `Advise`hergestellte Verbindung .|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[IConnectionPointImpl::m_vec](#m_vec)|Verwaltet die Verbindungen für den Verbindungspunkt.|

## <a name="remarks"></a>Bemerkungen

`IConnectionPointImpl`implementiert einen Verbindungspunkt, der es einem Objekt ermöglicht, eine ausgehende Schnittstelle für den Client verfügbar zu machen. Der Client implementiert diese Schnittstelle für ein Objekt, das als Senken bezeichnet wird.

ATL verwendet [IConnectionPointContainerImpl,](../../atl/reference/iconnectionpointcontainerimpl-class.md) um das verbindende Objekt zu implementieren. Jeder Verbindungspunkt innerhalb des verbindenden Objekts stellt eine ausgehende Schnittstelle dar, die durch *piid*identifiziert wird. Die Klasse *CDV* verwaltet die Verbindungen zwischen dem Verbindungspunkt und einer Senke. Jede Verbindung wird durch ein "Cookie" eindeutig identifiziert.

Weitere Informationen zur Verwendung von Verbindungspunkten in ATL finden Sie im Artikel [Verbindungspunkte](../../atl/atl-connection-points.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`_ICPLocator`

`IConnectionPointImpl`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlcom.h

## <a name="iconnectionpointimpladvise"></a><a name="advise"></a>IConnectionPointImpl::Beratung

Stellt eine Verbindung zwischen dem Verbindungspunkt und einer Senke her.

```
STDMETHOD(Advise)(
    IUnknown* pUnkSink,
    DWORD* pdwCookie);
```

### <a name="remarks"></a>Bemerkungen

Verwenden Sie [Unadvise,](#unadvise) um den Verbindungsanruf zu beenden.

Weitere Informationen finden Sie unter [IConnectionPoint::Advise](/windows/win32/api/ocidl/nf-ocidl-iconnectionpoint-advise) im Windows SDK.

## <a name="iconnectionpointimplenumconnections"></a><a name="enumconnections"></a>IConnectionPointImpl::EnumConnections

Erstellt einen Enumerator, der durch die Verbindungen für den Verbindungspunkt durchlaufen soll.

```
STDMETHOD(EnumConnections)(IEnumConnections** ppEnum);
```

### <a name="remarks"></a>Bemerkungen

Siehe [IConnectionPoint:EnumConnections](/windows/win32/api/ocidl/nf-ocidl-iconnectionpoint-enumconnections) im Windows SDK.

## <a name="iconnectionpointimplgetconnectioninterface"></a><a name="getconnectioninterface"></a>IConnectionPointImpl::GetConnectionInterface

Ruft die IID der Schnittstelle ab, die durch den Verbindungspunkt dargestellt wird.

```
STDMETHOD(GetConnectionInterface)(IID* piid2);
```

### <a name="remarks"></a>Bemerkungen

Siehe [IConnectionPoint::GetConnectionInterface](/windows/win32/api/ocidl/nf-ocidl-iconnectionpoint-getconnectioninterface) im Windows SDK.

## <a name="iconnectionpointimplgetconnectionpointcontainer"></a><a name="getconnectionpointcontainer"></a>IConnectionPointImpl::GetConnectionPointContainer

Ruft einen Schnittstellenzeiger zum verbindenden Objekt ab.

```
STDMETHOD(GetConnectionPointContainer)(IConnectionPointContainer** ppCPC);
```

### <a name="remarks"></a>Bemerkungen

Siehe [IConnectionPoint::GetConnectionPointContainer](/windows/win32/api/ocidl/nf-ocidl-iconnectionpoint-getconnectionpointcontainer) im Windows SDK.

## <a name="iconnectionpointimplm_vec"></a><a name="m_vec"></a>IConnectionPointImpl::m_vec

Verwaltet die Verbindungen zwischen dem Verbindungspunktobjekt und einer Senke.

```
CDV m_vec;
```

### <a name="remarks"></a>Bemerkungen

Standardmäßig `m_vec` ist vom Typ [CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md).

## <a name="iconnectionpointimplunadvise"></a><a name="unadvise"></a>IConnectionPointImpl::Unadvise

Beendet eine zuvor über [Advise](#advise)hergestellte Verbindung .

```
STDMETHOD(Unadvise)(DWORD dwCookie);
```

### <a name="remarks"></a>Bemerkungen

Siehe [IConnectionPoint::Unadvise](/windows/win32/api/ocidl/nf-ocidl-iconnectionpoint-unadvise) im Windows SDK.

## <a name="see-also"></a>Siehe auch

[IConnectionPoint](/windows/win32/api/ocidl/nn-ocidl-iconnectionpoint)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)
