---
title: ISpecifyPropertyPagesImpl-Klasse
ms.date: 11/04/2016
f1_keywords:
- ISpecifyPropertyPagesImpl
- ATLCOM/ATL::ISpecifyPropertyPagesImpl
- ATLCOM/ATL::ISpecifyPropertyPagesImpl::GetPages
helpviewer_keywords:
- property pages, CLSIDs associated with
- ISpecifyPropertyPages
- ISpecifyPropertyPagesImpl class
ms.assetid: 4e4b9795-b656-4d56-9b8c-85941e7731f9
ms.openlocfilehash: 06b6b60227a659bd35e042952c7464971fc40bdc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326411"
---
# <a name="ispecifypropertypagesimpl-class"></a>ISpecifyPropertyPagesImpl-Klasse

Diese Klasse `IUnknown` implementiert und stellt eine Standardimplementierung der [ISpecifyPropertyPages-Schnittstelle](/windows/win32/api/ocidl/nn-ocidl-ispecifypropertypages) bereit.

> [!IMPORTANT]
> Diese Klasse und ihre Member können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

## <a name="syntax"></a>Syntax

```
template<class T>
class ATL_NO_VTABLE ISpecifyPropertyPagesImpl
   : public ISpecifyPropertyPages
```

#### <a name="parameters"></a>Parameter

*T*<br/>
Ihre Klasse, `ISpecifyPropertyPagesImpl`abgeleitet von .

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[ISpecifyPropertyPagesImpl::GetPages](#getpages)|Füllt ein gezähltes Array von UUID-Werten. Jede UUID entspricht der CLSID für eine der Eigenschaftenseiten, die im Eigenschaftenblatt des Objekts angezeigt werden können.|

## <a name="remarks"></a>Bemerkungen

Die [ISpecifyPropertyPages-Schnittstelle](/windows/win32/api/ocidl/nn-ocidl-ispecifypropertypages) ermöglicht es einem Client, eine Liste von CLSIDs für die von einem Objekt unterstützten Eigenschaftenseiten abzusuchen. Die `ISpecifyPropertyPagesImpl` Klasse stellt eine Standardimplementierung `IUnknown` dieser Schnittstelle bereit und implementiert, indem Informationen in Debugbuilds an das Dumpgerät gesendet werden.

> [!NOTE]
> Machen Sie `ISpecifyPropertyPages` die Schnittstelle nicht verfügbar, wenn das Objekt keine Eigenschaftenseiten unterstützt.

**Verwandte Artikel** [ATL Tutorial](../../atl/active-template-library-atl-tutorial.md), Erstellen eines [ATL-Projekts](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`ISpecifyPropertyPages`

`ISpecifyPropertyPagesImpl`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlcom.h

## <a name="ispecifypropertypagesimplgetpages"></a><a name="getpages"></a>ISpecifyPropertyPagesImpl::GetPages

Füllt das Array in der [CAUUID-Struktur](/windows/win32/api/ocidl/ns-ocidl-cauuid) mit den CLSIDs für die Eigenschaftenseiten, die im Eigenschaftenblatt des Objekts angezeigt werden können.

```
STDMETHOD(GetPages)(CAUUID* pPages);
```

### <a name="remarks"></a>Bemerkungen

ATL verwendet die Eigenschaftszuordnung des Objekts, um jede CLSID abzurufen.

Weitere Informationen finden Sie unter [ISpecifyPropertyPages::GetPages](/windows/win32/api/ocidl/nf-ocidl-ispecifypropertypages-getpages) im Windows SDK.

## <a name="see-also"></a>Siehe auch

[IPropertyPageImpl-Klasse](../../atl/reference/ipropertypageimpl-class.md)<br/>
[IPerPropertyBrowsingImpl-Klasse](../../atl/reference/iperpropertybrowsingimpl-class.md)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)
