---
title: IObjectWithSiteImpl-Klasse
ms.date: 11/04/2016
f1_keywords:
- IObjectWithSiteImpl
- ATLCOM/ATL::IObjectWithSiteImpl
- ATLCOM/ATL::IObjectWithSiteImpl::GetSite
- ATLCOM/ATL::IObjectWithSiteImpl::SetChildSite
- ATLCOM/ATL::IObjectWithSiteImpl::SetSite
- ATLCOM/ATL::IObjectWithSiteImpl::m_spUnkSite
helpviewer_keywords:
- IObjectWithSiteImpl class
ms.assetid: 4e1f774f-bc3d-45ee-9a1c-c3533a511588
ms.openlocfilehash: 034e5dd42f6e10286520bb2a08effc40b0aca71a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329645"
---
# <a name="iobjectwithsiteimpl-class"></a>IObjectWithSiteImpl-Klasse

Diese Klasse stellt Methoden bereit, mit denen ein Objekt mit seiner Site kommunizieren kann.

## <a name="syntax"></a>Syntax

```
template <class T>
    class ATL_NO_VTABLE IObjectWithSiteImpl :
    public IObjectWithSite
```

#### <a name="parameters"></a>Parameter

*T*<br/>
Ihre Klasse, `IObjectWithSiteImpl`abgeleitet von .

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[IObjectWithSiteImpl::GetSite](#getsite)|Fragt die Site nach einem Schnittstellenzeiger ab.|
|[IObjectWithSiteImpl::SetChildSite](#setchildsite)|Stellt das Objekt mit `IUnknown` dem Zeiger der Website bereit.|
|[IObjectWithSiteImpl::SetSite](#setsite)|Stellt das Objekt mit `IUnknown` dem Zeiger der Website bereit.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[IObjectWithSiteImpl::m_spUnkSite](#m_spunksite)|Verwaltet den `IUnknown` Zeiger der Website.|

## <a name="remarks"></a>Bemerkungen

Die [IObjectWithSite-Schnittstelle](/windows/win32/api/ocidl/nn-ocidl-iobjectwithsite) ermöglicht einem Objekt die Kommunikation mit seiner Site. Die `IObjectWithSiteImpl` Klasse stellt eine Standardimplementierung `IUnknown` dieser Schnittstelle bereit und implementiert, indem Informationen in Debugbuilds an das Dumpgerät gesendet werden.

`IObjectWithSiteImpl`gibt zwei Methoden an. Der Client `SetSite`ruft zuerst auf, `IUnknown` um den Zeiger der Site zu übergeben. Dieser Zeiger wird im Objekt gespeichert und kann später `GetSite`über einen Aufruf von abgerufen werden.

In der Regel leiten `IObjectWithSiteImpl` Sie Ihre Klasse ab, wenn Sie ein Objekt erstellen, das kein Steuerelement ist. Leiten Sie für Steuerelemente Ihre Klasse von [IOleObjectImpl](../../atl/reference/ioleobjectimpl-class.md)ab, das auch einen Sitezeiger bereitstellt. Leiten Sie Ihre Klasse `IObjectWithSiteImpl` nicht `IOleObjectImpl`von beiden und ab.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`IObjectWithSite`

`IObjectWithSiteImpl`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlcom.h

## <a name="iobjectwithsiteimplgetsite"></a><a name="getsite"></a>IObjectWithSiteImpl::GetSite

Fragt die Site nach einem Zeiger `riid`auf die schnittstelle ab, die durch identifiziert wurde.

```
STDMETHOD(GetSite)(
    REFIID riid,
    void** ppvSite);
```

### <a name="remarks"></a>Bemerkungen

Wenn die Site diese Schnittstelle unterstützt, `ppvSite`wird der Zeiger über zurückgegeben. Andernfalls `ppvSite` wird auf NULL gesetzt.

Siehe [iObjectWithSite::GetSite](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-getsite) im Windows SDK.

## <a name="iobjectwithsiteimplm_spunksite"></a><a name="m_spunksite"></a>IObjectWithSiteImpl::m_spUnkSite

Verwaltet den `IUnknown` Zeiger der Website.

```
CComPtr<IUnknown> m_spUnkSite;
```

### <a name="remarks"></a>Bemerkungen

`m_spUnkSite`empfängt diesen Zeiger zunächst über einen Aufruf von [SetSite](#setsite).

## <a name="iobjectwithsiteimplsetchildsite"></a><a name="setchildsite"></a>IObjectWithSiteImpl::SetChildSite

Stellt das Objekt mit `IUnknown` dem Zeiger der Website bereit.

```
HRESULT SetChildSite(IUnknown* pUnkSite);
```

### <a name="parameters"></a>Parameter

*pUnkSite*<br/>
[in] Zeiger auf `IUnknown` den Schnittstellenzeiger der Site, die dieses Objekt verwaltet. Wenn NULL, sollte `IUnknown::Release` das Objekt auf jede vorhandene Site aufrufen, an der das Objekt seine Site nicht mehr kennt.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK zurück.

## <a name="iobjectwithsiteimplsetsite"></a><a name="setsite"></a>IObjectWithSiteImpl::SetSite

Stellt das Objekt mit `IUnknown` dem Zeiger der Website bereit.

```
STDMETHOD(SetSite)(IUnknown* pUnkSite);
```

### <a name="remarks"></a>Bemerkungen

Siehe [iObjectWithSite::SetSite](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-setsite) im Windows SDK.

## <a name="see-also"></a>Siehe auch

[Klassenübersicht](../../atl/atl-class-overview.md)
