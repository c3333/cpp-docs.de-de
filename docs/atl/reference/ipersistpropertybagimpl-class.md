---
title: IPersistPropertyBagImpl-Klasse
ms.date: 11/04/2016
f1_keywords:
- IPersistPropertyBagImpl
- ATLCOM/ATL::IPersistPropertyBagImpl
- ATLCOM/ATL::IPersistPropertyBagImpl::GetClassID
- ATLCOM/ATL::IPersistPropertyBagImpl::InitNew
- ATLCOM/ATL::IPersistPropertyBagImpl::Load
- ATLCOM/ATL::IPersistPropertyBagImpl::Save
helpviewer_keywords:
- IPersistPropertyBagImpl class
ms.assetid: 712af24d-99f8-40f2-9811-53b3ff6e5b19
ms.openlocfilehash: f656ecc76b175eae523059c60bb8a3efc6f0b312
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326484"
---
# <a name="ipersistpropertybagimpl-class"></a>IPersistPropertyBagImpl-Klasse

Diese Klasse `IUnknown` implementiert und ermöglicht es einem Objekt, seine Eigenschaften in einem vom Client bereitgestellten Eigenschaftenbeutel zu speichern.

> [!IMPORTANT]
> Diese Klasse und ihre Member können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

## <a name="syntax"></a>Syntax

```
template <class T>
class ATL_NO_VTABLE IPersistPropertyBagImpl : public IPersistPropertyBag
```

#### <a name="parameters"></a>Parameter

*T*<br/>
Ihre Klasse, `IPersistPropertyBagImpl`abgeleitet von .

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[IPersistPropertyBagImpl::GetClassID](#getclassid)|Ruft die CLSID des Objekts ab.|
|[IPersistPropertyBagImpl::InitNew](#initnew)|Initialisiert ein neu erstelltes Objekt. Die ATL-Implementierung gibt S_OK zurück.|
|[IPersistPropertyBagImpl::Laden](#load)|Lädt die Eigenschaften des Objekts aus einer vom Client bereitgestellten Eigenschaftentasche.|
|[IPersistPropertyBagImpl::Speichern](#save)|Speichert die Eigenschaften des Objekts in einer vom Client bereitgestellten Eigenschaftentasche.|

## <a name="remarks"></a>Bemerkungen

Die [IPersistPropertyBag-Schnittstelle](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768205\(v=vs.85\)) ermöglicht es einem Objekt, seine Eigenschaften in einer vom Client bereitgestellten Eigenschaftentasche zu speichern. Die `IPersistPropertyBagImpl` Klasse stellt eine Standardimplementierung `IUnknown` dieser Schnittstelle bereit und implementiert, indem Informationen in Debugbuilds an das Dumpgerät gesendet werden.

`IPersistPropertyBag`arbeitet in Verbindung mit [IPropertyBag](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768196\(v=vs.85\)) und [IErrorLog](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768231\(v=vs.85\)). Diese beiden letztgenannten Schnittstellen müssen vom Client implementiert werden. Durch `IPropertyBag`speichert und lädt der Client die einzelnen Eigenschaften des Objekts. Durch `IErrorLog`können sowohl das Objekt als auch der Client aufgetretene Fehler melden.

**Verwandte Artikel** [ATL Tutorial](../../atl/active-template-library-atl-tutorial.md), Erstellen eines [ATL-Projekts](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`IPersistPropertyBag`

`IPersistPropertyBagImpl`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlcom.h

## <a name="ipersistpropertybagimplgetclassid"></a><a name="getclassid"></a>IPersistPropertyBagImpl::GetClassID

Ruft die CLSID des Objekts ab.

```
STDMETHOD(GetClassID)(CLSID* pClassID);
```

### <a name="remarks"></a>Bemerkungen

Siehe [IPersist::GetClassID](/windows/win32/api/objidl/nf-objidl-ipersist-getclassid) im Windows SDK.

## <a name="ipersistpropertybagimplinitnew"></a><a name="initnew"></a>IPersistPropertyBagImpl::InitNew

Initialisiert ein neu erstelltes Objekt.

```
STDMETHOD(InitNew)();
```

### <a name="return-value"></a>Rückgabewert

Gibt S_OK zurück.

### <a name="remarks"></a>Bemerkungen

Siehe [IPersistPropertyBag::InitNew](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768204\(v=vs.85\)) im Windows SDK.

## <a name="ipersistpropertybagimplload"></a><a name="load"></a>IPersistPropertyBagImpl::Laden

Lädt die Eigenschaften des Objekts aus einer vom Client bereitgestellten Eigenschaftentasche.

```
STDMETHOD(Load)(LPPROPERTYBAG pPropBag, LPERRORLOG pErrorLog);
```

### <a name="remarks"></a>Bemerkungen

ATL verwendet die Eigenschaftenzuordnung des Objekts, um diese Informationen abzurufen.

Siehe [IPersistPropertyBag::Load](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768206\(v=vs.85\)) im Windows SDK.

## <a name="ipersistpropertybagimplsave"></a><a name="save"></a>IPersistPropertyBagImpl::Speichern

Speichert die Eigenschaften des Objekts in einer vom Client bereitgestellten Eigenschaftentasche.

```
STDMETHOD(Save)(
    LPPROPERTYBAG pPropBag,
    BOOL fClearDirty,
    BOOL fSaveAllProperties);
```

### <a name="remarks"></a>Bemerkungen

ATL verwendet die Eigenschaftenzuordnung des Objekts, um diese Informationen zu speichern. Standardmäßig speichert diese Methode alle Eigenschaften, unabhängig vom Wert von *fSaveAllProperties*.

Siehe [IPersistPropertyBag::Speichern](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768207\(v=vs.85\)) im Windows SDK.

## <a name="see-also"></a>Siehe auch

[BEGIN_PROP_MAP](property-map-macros.md#begin_prop_map)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)
