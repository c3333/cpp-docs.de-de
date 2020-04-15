---
title: IPerPropertyBrowsingImpl-Klasse
ms.date: 11/04/2016
f1_keywords:
- IPerPropertyBrowsingImpl
- ATLCTL/ATL::IPerPropertyBrowsingImpl
- ATLCTL/ATL::IPerPropertyBrowsingImpl::GetDisplayString
- ATLCTL/ATL::IPerPropertyBrowsingImpl::GetPredefinedStrings
- ATLCTL/ATL::IPerPropertyBrowsingImpl::GetPredefinedValue
- ATLCTL/ATL::IPerPropertyBrowsingImpl::MapPropertyToPage
helpviewer_keywords:
- IPerPropertyBrowsingImpl class
- property pages, accessing information
- IPerPropertyBrowsing, ATL implementation
ms.assetid: 0b1a9be3-d242-4767-be69-663a21e4b728
ms.openlocfilehash: f8fb80cc38e775b9b26afa033647faac694e968a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326515"
---
# <a name="iperpropertybrowsingimpl-class"></a>IPerPropertyBrowsingImpl-Klasse

Diese Klasse `IUnknown` implementiert und ermöglicht einem Client den Zugriff auf die Informationen auf den Eigenschaftenseiten eines Objekts.

> [!IMPORTANT]
> Diese Klasse und ihre Member können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

## <a name="syntax"></a>Syntax

```

template <class T>
class ATL_NO_VTABLE IPerPropertyBrowsingImpl :
    public IPerPropertyBrowsing
```

#### <a name="parameters"></a>Parameter

*T*<br/>
Ihre Klasse, `IPerPropertyBrowsingImpl`abgeleitet von .

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[IPerPropertyBrowsingImpl::GetDisplayString](#getdisplaystring)|Ruft eine Zeichenfolge ab, die eine bestimmte Eigenschaft beschreibt.|
|[IPerPropertyBrowsingImpl::GetPredefinedStrings](#getpredefinedstrings)|Ruft ein Array von Zeichenfolgen ab, das den Werten entspricht, die eine bestimmte Eigenschaft akzeptieren kann.|
|[IPerPropertyBrowsingImpl::GetPredefinedValue](#getpredefinedvalue)|Ruft einen VARIANT ab, der den Wert einer Eigenschaft enthält, die von einer bestimmten DISPID identifiziert wurde. Die DISPID ist dem Zeichenfolgennamen zugeordnet, der aus `GetPredefinedStrings`abgerufen wurde. Die ATL-Implementierung gibt E_NOTIMPL zurück.|
|[IPerPropertyBrowsingImpl::MapPropertyToPage](#mappropertytopage)|Ruft die CLSID der Eigenschaftenseite ab, die einer bestimmten Eigenschaft zugeordnet ist.|

## <a name="remarks"></a>Bemerkungen

Die [IPerPropertyBrowsing-Schnittstelle](/windows/win32/api/ocidl/nn-ocidl-iperpropertybrowsing) ermöglicht einem Client den Zugriff auf die Informationen in den Eigenschaftenseiten eines Objekts. Die `IPerPropertyBrowsingImpl` Klasse stellt eine Standardimplementierung `IUnknown` dieser Schnittstelle bereit und implementiert, indem Informationen in Debugbuilds an das Dumpgerät gesendet werden.

> [!NOTE]
> Wenn Sie Microsoft Access als Containeranwendung verwenden, müssen `IPerPropertyBrowsingImpl`Sie Ihre Klasse von ableiten. Andernfalls lädt Access das Steuerelement nicht.

**Verwandte Artikel** [ATL Tutorial](../../atl/active-template-library-atl-tutorial.md), Erstellen eines [ATL-Projekts](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`IPerPropertyBrowsing`

`IPerPropertyBrowsingImpl`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlctl.h

## <a name="iperpropertybrowsingimplgetdisplaystring"></a><a name="getdisplaystring"></a>IPerPropertyBrowsingImpl::GetDisplayString

Ruft eine Zeichenfolge ab, die eine bestimmte Eigenschaft beschreibt.

```
STDMETHOD(GetDisplayString)(
    DISPID dispID,
    BSTR* pBstr);
```

### <a name="remarks"></a>Bemerkungen

Siehe [IPerPropertyBrowsing::GetDisplayString](/windows/win32/api/ocidl/nf-ocidl-iperpropertybrowsing-getdisplaystring) im Windows SDK.

## <a name="iperpropertybrowsingimplgetpredefinedstrings"></a><a name="getpredefinedstrings"></a>IPerPropertyBrowsingImpl::GetPredefinedStrings

Füllt jedes Array mit Null-Elementen.

```
STDMETHOD(GetPredefinedStrings)(
    DISPID dispID,
    CALPOLESTR* pCaStringsOut,
    CADWORD* pCaCookiesOut);
```

### <a name="return-value"></a>Rückgabewert

Die Implementierung von [GetPredefinedValue](#getpredefinedvalue) durch ATL gibt E_NOTIMPL zurück.

### <a name="remarks"></a>Bemerkungen

Siehe [IPerPropertyBrowsing::GetPredefinedStrings](/windows/win32/api/ocidl/nf-ocidl-iperpropertybrowsing-getpredefinedstrings) im Windows SDK.

## <a name="iperpropertybrowsingimplgetpredefinedvalue"></a><a name="getpredefinedvalue"></a>IPerPropertyBrowsingImpl::GetPredefinedValue

Ruft einen VARIANT ab, der den Wert einer Eigenschaft enthält, die von einer bestimmten DISPID identifiziert wurde. Die DISPID ist dem Zeichenfolgennamen zugeordnet, der aus `GetPredefinedStrings`abgerufen wurde.

```
STDMETHOD(GetPredefinedValue)(
    DISPID dispID,
    DWORD dwCookie,
    VARIANT* pVarOut);
```

### <a name="return-value"></a>Rückgabewert

Gibt E_NOTIMPL zurück.

### <a name="remarks"></a>Bemerkungen

Die ATL-Implementierung von [GetPredefinedStrings](#getpredefinedstrings) ruft keine entsprechenden Zeichenfolgen ab.

Siehe [IPerPropertyBrowsing::GetPredefinedValue](/windows/win32/api/ocidl/nf-ocidl-iperpropertybrowsing-getpredefinedvalue) im Windows SDK.

## <a name="iperpropertybrowsingimplmappropertytopage"></a><a name="mappropertytopage"></a>IPerPropertyBrowsingImpl::MapPropertyToPage

Ruft die CLSID der Eigenschaftenseite ab, die der angegebenen Eigenschaft zugeordnet ist.

```
STDMETHOD(MapPropertyToPage)(
    DISPID dispID,
    CLSID* pClsid);
```

### <a name="remarks"></a>Bemerkungen

ATL verwendet die Eigenschaftenzuordnung des Objekts, um diese Informationen abzuerhalten.

Siehe [IPerPropertyBrowsing::MapPropertyToPage](/windows/win32/api/ocidl/nf-ocidl-iperpropertybrowsing-mappropertytopage) im Windows SDK.

## <a name="see-also"></a>Siehe auch

[IPropertyPageImpl-Klasse](../../atl/reference/ipropertypageimpl-class.md)<br/>
[ISpecifyPropertyPagesImpl-Klasse](../../atl/reference/ispecifypropertypagesimpl-class.md)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)
