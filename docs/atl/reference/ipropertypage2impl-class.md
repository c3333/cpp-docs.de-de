---
title: IPropertyPage2Impl-Klasse
ms.date: 11/04/2016
f1_keywords:
- IPropertyPage2Impl
- ATLCTL/ATL::IPropertyPage2Impl
- ATLCTL/ATL::IPropertyPage2Impl::EditProperty
helpviewer_keywords:
- property pages
- IPropertyPage2 ATL implementation
- IPropertyPage2Impl class
ms.assetid: e89fbe90-203a-47f0-a5de-23616697e1ce
ms.openlocfilehash: d112a2411a9debbf2eb77e6b851f4500e8d32ab8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329589"
---
# <a name="ipropertypage2impl-class"></a>IPropertyPage2Impl-Klasse

Diese Klasse `IUnknown` implementiert und erbt die Standardimplementierung von [IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md).

> [!IMPORTANT]
> Diese Klasse und ihre Member können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

## <a name="syntax"></a>Syntax

```
template<class T>
class IPropertyPage2Impl : public IPropertyPageImpl<T>
```

#### <a name="parameters"></a>Parameter

*T*<br/>
Ihre Klasse, `IPropertyPage2Impl`abgeleitet von .

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[IPropertyPage2Impl::EditProperty](#editproperty)|Gibt an, welches Eigenschaftensteuerelement den Fokus erhält, wenn die Eigenschaftenseite aktiviert wird. Die ATL-Implementierung gibt E_NOTIMPL zurück.|

## <a name="remarks"></a>Bemerkungen

Die [IPropertyPage2-Schnittstelle](/windows/win32/api/ocidl/nn-ocidl-ipropertypage2) erweitert [IPropertyPage](/windows/win32/api/ocidl/nn-ocidl-ipropertypage) durch Hinzufügen der `EditProperty` Methode. Mit dieser Methode kann ein Client eine bestimmte Eigenschaft in einem Eigenschaftenseitenobjekt auswählen.

Die `IPropertyPage2Impl` Klasse gibt `IPropertyPage2::EditProperty`einfach E_NOTIMPL für zurück. Es erbt jedoch die Standardimplementierung von [IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md) und implementiert, `IUnknown` indem Informationen an das Dump-Gerät in Debugbuilds gesendet werden.

Wenn Sie eine Eigenschaftenseite erstellen, wird `IPropertyPageImpl`Ihre Klasse in der Regel von abgeleitet. Um die zusätzliche `IPropertyPage2`Unterstützung von bereitzustellen, ändern `EditProperty` Sie ihre Klassendefinition, und überschreiben Sie die Methode.

**Verwandte Artikel** [ATL Tutorial](../../atl/active-template-library-atl-tutorial.md), Erstellen eines [ATL-Projekts](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`IPropertyPage`

[IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md)

`IPropertyPage2Impl`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlctl.h

## <a name="ipropertypage2impleditproperty"></a><a name="editproperty"></a>IPropertyPage2Impl::EditProperty

Gibt an, welches Eigenschaftensteuerelement den Fokus erhält, wenn die Eigenschaftenseite aktiviert wird.

```
HRESULT EditProperty(DISPID dispID);
```

### <a name="return-value"></a>Rückgabewert

Gibt E_NOTIMPL zurück.

### <a name="remarks"></a>Bemerkungen

Siehe [IPropertyPage2::EditProperty](/windows/win32/api/ocidl/nf-ocidl-ipropertypage2-editproperty) im Windows SDK.

## <a name="see-also"></a>Siehe auch

[IPerPropertyBrowsingImpl-Klasse](../../atl/reference/iperpropertybrowsingimpl-class.md)<br/>
[ISpecifyPropertyPagesImpl-Klasse](../../atl/reference/ispecifypropertypagesimpl-class.md)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)
