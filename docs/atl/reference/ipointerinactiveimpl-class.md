---
title: IPointerInactiveImpl-Klasse
ms.date: 11/04/2016
f1_keywords:
- IPointerInactiveImpl
- ATLCTL/ATL::IPointerInactiveImpl
- ATLCTL/ATL::IPointerInactiveImpl::GetActivationPolicy
- ATLCTL/ATL::IPointerInactiveImpl::OnInactiveMouseMove
- ATLCTL/ATL::IPointerInactiveImpl::OnInactiveSetCursor
helpviewer_keywords:
- IPointerInactive ATL implementation
- inactive objects
- IPointerInactiveImpl class
ms.assetid: e1fe9ea6-d38a-4527-9112-eb344771e0b7
ms.openlocfilehash: 229b8c6803aa7b3817cb3d95474bde0502829f8b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326447"
---
# <a name="ipointerinactiveimpl-class"></a>IPointerInactiveImpl-Klasse

Diese Klasse `IUnknown` implementiert und die [IPointerInactive-Schnittstellenmethoden.](/windows/win32/api/ocidl/nn-ocidl-ipointerinactive)

> [!IMPORTANT]
> Diese Klasse und ihre Member können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

## <a name="syntax"></a>Syntax

```
template<class T>
class IPointerInactiveImpl
```

#### <a name="parameters"></a>Parameter

*T*<br/>
Ihre Klasse, `IPointerInactiveImpl`abgeleitet von .

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[IPointerInactiveImpl::GetActivationPolicy](#getactivationpolicy)|Ruft die aktuelle Aktivierungsrichtlinie für das Objekt ab. Die ATL-Implementierung gibt E_NOTIMPL zurück.|
|[IPointerInactiveImpl::OnInactiveMouseMove](#oninactivemousemove)|Benachrichtigt das Objekt, dass der Mauszeiger darüber bewegt wurde, und gibt an, dass das Objekt Mausereignisse ausgelöst werden kann. Die ATL-Implementierung gibt E_NOTIMPL zurück.|
|[IPointerInactiveImpl::OnInactiveSetCursor](#oninactivesetcursor)|Legt den Mauszeiger für das inaktive Objekt fest. Die ATL-Implementierung gibt E_NOTIMPL zurück.|

## <a name="remarks"></a>Bemerkungen

Ein inaktives Objekt ist ein Objekt, das einfach geladen oder ausgeführt wird. Im Gegensatz zu einem aktiven Objekt kann ein inaktives Objekt keine Windows-Maus- und Tastaturnachrichten empfangen. Daher verbrauchen inaktive Objekte weniger Ressourcen und sind in der Regel effizienter.

Die [IPointerInactive-Schnittstelle](/windows/win32/api/ocidl/nn-ocidl-ipointerinactive) ermöglicht es einem Objekt, eine minimale Mausinteraktion zu unterstützen, während es inaktiv bleibt. Diese Funktionalität ist besonders nützlich für Steuerelemente.

Die `IPointerInactiveImpl` Klasse `IPointerInactive` implementiert die Methoden, indem sie einfach E_NOTIMPL zurückgibt. Es wird `IUnknown` jedoch implementiert, indem Informationen an das Dump-Gerät in Debugbuilds gesendet werden.

**Verwandte Artikel** [ATL Tutorial](../../atl/active-template-library-atl-tutorial.md), Erstellen eines [ATL-Projekts](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`IPointerInactive`

`IPointerInactiveImpl`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlctl.h

## <a name="ipointerinactiveimplgetactivationpolicy"></a><a name="getactivationpolicy"></a>IPointerInactiveImpl::GetActivationPolicy

Ruft die aktuelle Aktivierungsrichtlinie für das Objekt ab.

```
HRESULT GetActivationPolicy(DWORD* pdwPolicy);
```

### <a name="return-value"></a>Rückgabewert

Gibt E_NOTIMPL zurück.

### <a name="remarks"></a>Bemerkungen

Siehe [IPointerInactive::GetActivationPolicy](/windows/win32/api/ocidl/nf-ocidl-ipointerinactive-getactivationpolicy) im Windows SDK.

## <a name="ipointerinactiveimploninactivemousemove"></a><a name="oninactivemousemove"></a>IPointerInactiveImpl::OnInactiveMouseMove

Benachrichtigt das Objekt, dass der Mauszeiger darüber bewegt wurde, und gibt an, dass das Objekt Mausereignisse ausgelöst werden kann.

```
HRESULT OnInactiveMouseMove(
    LPCRECT pRectBounds,
    long x,
    long y,
    DWORD dwMouseMsg);
```

### <a name="return-value"></a>Rückgabewert

Gibt E_NOTIMPL zurück.

### <a name="remarks"></a>Bemerkungen

Siehe [IPointerInactive::OnInactiveMouseMove](/windows/win32/api/ocidl/nf-ocidl-ipointerinactive-oninactivemousemove) im Windows SDK.

## <a name="ipointerinactiveimploninactivesetcursor"></a><a name="oninactivesetcursor"></a>IPointerInactiveImpl::OnInactiveSetCursor

Legt den Mauszeiger für das inaktive Objekt fest.

```
HRESULT OnInactiveSetCursor(
    LPCRECT pRectBounds,
    long x,
    long y,
    DWORD dwMouseMsg,
    BOOL fSetAlways);
```

### <a name="return-value"></a>Rückgabewert

Gibt E_NOTIMPL zurück.

### <a name="remarks"></a>Bemerkungen

Siehe [IPointerInactive::OnInactiveSetCursor](/windows/win32/api/ocidl/nf-ocidl-ipointerinactive-oninactivesetcursor) im Windows SDK.

## <a name="see-also"></a>Siehe auch

[Klassenübersicht](../../atl/atl-class-overview.md)
