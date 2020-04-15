---
title: IOleControlImpl-Klasse
ms.date: 11/04/2016
f1_keywords:
- IOleControlImpl
- ATLCTL/ATL::IOleControlImpl
- ATLCTL/ATL::IOleControlImpl::FreezeEvents
- ATLCTL/ATL::IOleControlImpl::GetControlInfo
- ATLCTL/ATL::IOleControlImpl::OnAmbientPropertyChange
- ATLCTL/ATL::IOleControlImpl::OnMnemonic
helpviewer_keywords:
- IOleControlImpl class
ms.assetid: 5a4255ad-ede4-49ca-ba9a-07c2e919fa85
ms.openlocfilehash: 947ec16e91b99cc42cff90abe7df4a5d13576e98
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329619"
---
# <a name="iolecontrolimpl-class"></a>IOleControlImpl-Klasse

Diese Klasse stellt eine `IOleControl` Standardimplementierung der `IUnknown`Schnittstelle bereit und implementiert .

> [!IMPORTANT]
> Diese Klasse und ihre Member können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

## <a name="syntax"></a>Syntax

```
template<class T>
class IOleControlImpl
```

#### <a name="parameters"></a>Parameter

*T*<br/>
Ihre Klasse, `IOleControlImpl`abgeleitet von .

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[IOleControlImpl::FreezeEvents](#freezeevents)|Gibt an, ob der Container Ereignisse aus dem Steuerelement ignoriert oder akzeptiert.|
|[IOleControlImpl::GetControlInfo](#getcontrolinfo)|Füllt Informationen über das Tastaturverhalten des Steuerelements aus. Die ATL-Implementierung gibt E_NOTIMPL zurück.|
|[IOleControlImpl::OnAmbientPropertyChange](#onambientpropertychange)|Informiert ein Steuerelement, dass sich eine oder mehrere Umgebungseigenschaften des Containers geändert haben. Die ATL-Implementierung gibt S_OK zurück.|
|[IOleControlImpl::OnMnemonic](#onmnemonic)|Informiert das Steuerelement, dass ein Benutzer einen angegebenen Tastenanschlag gedrückt hat. Die ATL-Implementierung gibt E_NOTIMPL zurück.|

## <a name="remarks"></a>Bemerkungen

Die `IOleControlImpl` Klasse stellt eine Standardimplementierung der [IOleControl-Schnittstelle](/windows/win32/api/ocidl/nn-ocidl-iolecontrol) bereit und implementiert, `IUnknown` indem Informationen in Debugbuilds an das Dumpgerät gesendet werden.

**Verwandte Artikel** [ATL Tutorial](../../atl/active-template-library-atl-tutorial.md), Erstellen eines [ATL-Projekts](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`IOleControl`

`IOleControlImpl`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlctl.h

## <a name="iolecontrolimplfreezeevents"></a><a name="freezeevents"></a>IOleControlImpl::FreezeEvents

In der ATL-Implementierung wird `FreezeEvents` der `m_nFreezeEvents` Datenmember der `bFreeze` Steuerelementklasse erhöht, `m_nFreezeEvents` wenn `bFreeze` er TRUE ist, und Dekremente, wenn FALSE ist.

```
HRESULT FreezeEvents(BOOL bFreeze);
```

### <a name="remarks"></a>Bemerkungen

`FreezeEvents`kehrt dann S_OK zurück.

Siehe [IOleControl::FreezeEvents](/windows/win32/api/ocidl/nf-ocidl-iolecontrol-freezeevents) im Windows SDK.

## <a name="iolecontrolimplgetcontrolinfo"></a><a name="getcontrolinfo"></a>IOleControlImpl::GetControlInfo

Füllt Informationen über das Tastaturverhalten des Steuerelements aus.

```
HRESULT GetControlInfo(LPCONTROLINFO pCI);
```

### <a name="remarks"></a>Bemerkungen

Siehe [IOleControl:GetControlInfo](/windows/win32/api/ocidl/nf-ocidl-iolecontrol-getcontrolinfo) im Windows SDK.

### <a name="return-value"></a>Rückgabewert

Gibt E_NOTIMPL zurück.

## <a name="iolecontrolimplonambientpropertychange"></a><a name="onambientpropertychange"></a>IOleControlImpl::OnAmbientPropertyChange

Informiert ein Steuerelement, dass sich eine oder mehrere Umgebungseigenschaften des Containers geändert haben.

```
HRESULT OnAmbientPropertyChange(DISPID dispid);
```

### <a name="return-value"></a>Rückgabewert

Gibt S_OK zurück.

### <a name="remarks"></a>Bemerkungen

Siehe [IOleControl::OnAmbientPropertyChange](/windows/win32/api/ocidl/nf-ocidl-iolecontrol-onambientpropertychange) im Windows SDK.

## <a name="iolecontrolimplonmnemonic"></a><a name="onmnemonic"></a>IOleControlImpl::OnMnemonic

Informiert das Steuerelement, dass ein Benutzer einen angegebenen Tastenanschlag gedrückt hat.

```
HRESULT OnMnemonic(LPMSG pMsg);
```

### <a name="return-value"></a>Rückgabewert

Gibt E_NOTIMPL zurück.

### <a name="remarks"></a>Bemerkungen

Siehe [IOleControl::OnMnemonic](/windows/win32/api/ocidl/nf-ocidl-iolecontrol-onmnemonic) im Windows SDK.

## <a name="see-also"></a>Siehe auch

[IOleObjectImpl-Klasse](../../atl/reference/ioleobjectimpl-class.md)<br/>
[ActiveX-Steuerelementschnittstellen](/windows/win32/com/activex-controls-interfaces)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)
