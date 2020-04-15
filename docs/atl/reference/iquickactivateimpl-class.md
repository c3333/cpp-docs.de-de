---
title: IQuickActivateImpl-Klasse
ms.date: 11/04/2016
f1_keywords:
- IQuickActivateImpl
- ATLCTL/ATL::IQuickActivateImpl
- ATLCTL/ATL::IQuickActivateImpl::GetContentExtent
- ATLCTL/ATL::IQuickActivateImpl::QuickActivate
- ATLCTL/ATL::IQuickActivateImpl::SetContentExtent
helpviewer_keywords:
- activating ATL controls
- controls [ATL], activating
- IQuickActivateImpl class
- IQuickActivate ATL implementation
ms.assetid: aa80c056-1041-494e-b21d-2acca7dc27ea
ms.openlocfilehash: 7e1984249caf66e2986341f9c9f7a939d7039125
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329556"
---
# <a name="iquickactivateimpl-class"></a>IQuickActivateImpl-Klasse

Diese Klasse kombiniert die Steuerelementinitialisierung von Containern in einem einzigen Aufruf.

> [!IMPORTANT]
> Diese Klasse und ihre Member können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

## <a name="syntax"></a>Syntax

```
template <class T>
class ATL_NO_VTABLE IQuickActivateImpl : public IQuickActivate
```

#### <a name="parameters"></a>Parameter

*T*<br/>
Ihre Klasse, `IQuickActivateImpl`abgeleitet von .

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[IQuickActivateImpl::GetContentExtent](#getcontentextent)|Ruft die aktuelle Anzeigegröße für ein ausgeführtes Steuerelement ab.|
|[IQuickActivateImpl::QuickActivate](#quickactivate)|Führt eine schnelle Initialisierung der geladenen Steuerelemente durch.|
|[IQuickActivateImpl::SetContentExtent](#setcontentextent)|Informiert das Steuerelement darüber, wie viel Anzeigefläche der Container ihm zugewiesen hat.|

## <a name="remarks"></a>Bemerkungen

Die [IQuickActivate-Schnittstelle](/windows/win32/api/ocidl/nn-ocidl-iquickactivate) hilft Containern, Verzögerungen beim Laden von Steuerelementen zu vermeiden, indem die Initialisierung in einem einzelnen Aufruf kombiniert wird. Die `QuickActivate` Methode ermöglicht es dem Container, einen Zeiger an eine [QACONTAINER-Struktur](/windows/win32/api/ocidl/ns-ocidl-qacontainer) zu übergeben, die Zeiger auf alle Schnittstellen enthält, die das Steuerelement benötigt. Bei der Rückgabe gibt das Steuerelement einen Zeiger an eine [QACONTROL-Struktur](/windows/win32/api/ocidl/ns-ocidl-qacontrol) zurück, die Zeiger auf ihre eigenen Schnittstellen enthält, die vom Container verwendet werden. Die `IQuickActivateImpl` Klasse stellt `IQuickActivate` eine Standardimplementierung von und implementiert, `IUnknown` indem Informationen an das Dump-Gerät in Debugbuilds gesendet werden.

**Verwandte Artikel** [ATL Tutorial](../../atl/active-template-library-atl-tutorial.md), Erstellen eines [ATL-Projekts](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`IQuickActivate`

`IQuickActivateImpl`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlctl.h

## <a name="iquickactivateimplgetcontentextent"></a><a name="getcontentextent"></a>IQuickActivateImpl::GetContentExtent

Ruft die aktuelle Anzeigegröße für ein ausgeführtes Steuerelement ab.

```
STDMETHOD(GetContentExtent)(LPSIZEL pSize);
```

### <a name="remarks"></a>Bemerkungen

Die Größe ist für ein vollständiges Rendern des Steuerelements und wird in HIMETRIC-Einheiten angegeben.

Siehe [IQuickActivate::GetContentExtent](/windows/win32/api/ocidl/nf-ocidl-iquickactivate-getcontentextent) im Windows SDK.

## <a name="iquickactivateimplquickactivate"></a><a name="quickactivate"></a>IQuickActivateImpl::QuickActivate

Führt eine schnelle Initialisierung der geladenen Steuerelemente durch.

```
STDMETHOD(QuickActivate)(
    QACONTAINER* pQACont,
    QACONTROL* pQACtrl);
```

### <a name="remarks"></a>Bemerkungen

Die Struktur enthält Zeiger auf Schnittstellen, die vom Steuerelement benötigt werden, und die Werte einiger Umgebungseigenschaften. Bei der Rückgabe übergibt das Steuerelement einen Zeiger an eine [QACONTROL-Struktur,](/windows/win32/api/ocidl/ns-ocidl-qacontrol) die Zeiger auf die eigenen Schnittstellen enthält, die der Container benötigt, sowie zusätzliche Statusinformationen.

Siehe [IQuickActivate::QuickActivate](/windows/win32/api/ocidl/nf-ocidl-iquickactivate-quickactivate) im Windows SDK.

## <a name="iquickactivateimplsetcontentextent"></a><a name="setcontentextent"></a>IQuickActivateImpl::SetContentExtent

Informiert das Steuerelement darüber, wie viel Anzeigefläche der Container ihm zugewiesen hat.

```
STDMETHOD(SetContentExtent)(LPSIZEL pSize);
```

### <a name="remarks"></a>Bemerkungen

Die Größe wird in HIMETRIC-Einheiten angegeben.

Siehe [IQuickActivate::SetContentExtent](/windows/win32/api/ocidl/nf-ocidl-iquickactivate-setcontentextent) im Windows SDK.

## <a name="see-also"></a>Siehe auch

[CComControl-Klasse](../../atl/reference/ccomcontrol-class.md)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)
