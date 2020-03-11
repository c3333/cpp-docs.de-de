---
title: Iolecontrolimpl-Klasse
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
ms.openlocfilehash: 3bdb501d8210c98ce982719358564c4937991e12
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78864954"
---
# <a name="iolecontrolimpl-class"></a>Iolecontrolimpl-Klasse

Diese Klasse stellt eine Standard Implementierung der `IOleControl`-Schnittstelle bereit und implementiert `IUnknown`.

> [!IMPORTANT]
>  Diese Klasse und ihre Member können in Anwendungen, die im Windows-Runtime ausgeführt werden, nicht verwendet werden.

## <a name="syntax"></a>Syntax

```
template<class T>
class IOleControlImpl
```

#### <a name="parameters"></a>Parameter

*T*<br/>
Die von `IOleControlImpl`abgeleitete Klasse.

## <a name="members"></a>Members

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[Iolecontrolimpl:: frezeevents](#freezeevents)|Gibt an, ob der Container Ereignisse vom Steuerelement ignoriert oder annimmt.|
|[Iolecontrolimpl:: GetControlInfo](#getcontrolinfo)|Füllt Informationen über das Tastatur Verhalten des Steuer Elements aus. Die ATL-Implementierung gibt E_NOTIMPL zurück.|
|[Iolecontrolimpl:: OnAmbientPropertyChange](#onambientpropertychange)|Teilt einem-Steuerelement mit, dass sich mindestens eine der Ambient-Eigenschaften des Containers geändert hat. Die ATL-Implementierung gibt S_OK zurück.|
|[Iolecontrolimpl:: onmnetmonic](#onmnemonic)|Informiert das-Steuerelement darüber, dass ein Benutzer einen angegebenen Tastatur Strich gedrückt hat. Die ATL-Implementierung gibt E_NOTIMPL zurück.|

## <a name="remarks"></a>Bemerkungen

Class `IOleControlImpl` stellt eine Standard Implementierung der [IOleControl](/windows/win32/api/ocidl/nn-ocidl-iolecontrol) -Schnittstelle bereit und implementiert `IUnknown`, indem Informationen in Debugbuilds an das dumpgerät gesendet werden.

**Zugehörige Artikel** [ATL-Tutorial](../../atl/active-template-library-atl-tutorial.md), [Erstellen eines ATL-Projekts](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`IOleControl`

`IOleControlImpl`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atlctl. h

##  <a name="freezeevents"></a>Iolecontrolimpl:: frezeevents

In der ATL-Implementierung erhöht `FreezeEvents` den `m_nFreezeEvents` Datenmember der Steuerelement Klasse, wenn `bFreeze` true ist, und dekrementierungen `m_nFreezeEvents`, wenn `bFreeze` false ist.

```
HRESULT FreezeEvents(BOOL bFreeze);
```

### <a name="remarks"></a>Bemerkungen

`FreezeEvents` gibt dann S_OK zurück.

Weitere Informationen finden Sie unter [IOleControl:: frezeevents](/windows/win32/api/ocidl/nf-ocidl-iolecontrol-freezeevents) in der Windows SDK.

##  <a name="getcontrolinfo"></a>Iolecontrolimpl:: GetControlInfo

Füllt Informationen über das Tastatur Verhalten des Steuer Elements aus.

```
HRESULT GetControlInfo(LPCONTROLINFO pCI);
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [IOleControl: GetControlInfo](/windows/win32/api/ocidl/nf-ocidl-iolecontrol-getcontrolinfo) im Windows SDK.

### <a name="return-value"></a>Rückgabewert

Gibt E_NOTIMPL zurück.

##  <a name="onambientpropertychange"></a>Iolecontrolimpl:: OnAmbientPropertyChange

Teilt einem-Steuerelement mit, dass sich mindestens eine der Ambient-Eigenschaften des Containers geändert hat.

```
HRESULT OnAmbientPropertyChange(DISPID dispid);
```

### <a name="return-value"></a>Rückgabewert

Gibt S_OK zurück.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [IOleControl:: OnAmbientPropertyChange](/windows/win32/api/ocidl/nf-ocidl-iolecontrol-onambientpropertychange) in der Windows SDK.

##  <a name="onmnemonic"></a>Iolecontrolimpl:: onmnetmonic

Informiert das-Steuerelement darüber, dass ein Benutzer einen angegebenen Tastatur Strich gedrückt hat.

```
HRESULT OnMnemonic(LPMSG pMsg);
```

### <a name="return-value"></a>Rückgabewert

Gibt E_NOTIMPL zurück.

### <a name="remarks"></a>Bemerkungen

Siehe [IOleControl:: onmnetmonic](/windows/win32/api/ocidl/nf-ocidl-iolecontrol-onmnemonic) in der Windows SDK.

## <a name="see-also"></a>Weitere Informationen

[IOleObjectImpl-Klasse](../../atl/reference/ioleobjectimpl-class.md)<br/>
[ActiveX-Steuerelement Schnittstellen](/windows/win32/com/activex-controls-interfaces)<br/>
[Klassen Übersicht](../../atl/atl-class-overview.md)
