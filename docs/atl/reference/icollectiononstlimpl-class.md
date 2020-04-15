---
title: ICollectionOnSTLImpl-Klasse
ms.date: 11/04/2016
f1_keywords:
- ICollectionOnSTLImpl
- ATLCOM/ATL::ICollectionOnSTLImpl
- ATLCOM/ATL::ICollectionOnSTLImpl::get__NewEnum
- ATLCOM/ATL::ICollectionOnSTLImpl::getcount
- ATLCOM/ATL::ICollectionOnSTLImpl::get_Item
- ATLCOM/ATL::ICollectionOnSTLImpl::m_coll
helpviewer_keywords:
- ICollectionOnSTLImpl class
ms.assetid: 683c88b0-0d97-4779-a762-e493334ba7f9
ms.openlocfilehash: a8ccab08b89da8c1b8ef56c8932e27a6c74e62aa
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329909"
---
# <a name="icollectiononstlimpl-class"></a>ICollectionOnSTLImpl-Klasse

Diese Klasse stellt Methoden bereit, die von einer Auflistungsklasse verwendet werden.

## <a name="syntax"></a>Syntax

```
template <class T, class CollType, class ItemType, class CopyItem, class EnumType>
class ICollectionOnSTLImpl : public T
```

#### <a name="parameters"></a>Parameter

*T*<br/>
Eine COM-Auflistungsschnittstelle.

*CollType*<br/>
Eine C++-Standardbibliothekscontainerklasse.

*ItemType*<br/>
Der Typ des Elements, das von der Containerschnittstelle verfügbar gemacht wird.

*CopyItem*<br/>
Eine [Kopierrichtlinienklasse](../../atl/atl-copy-policy-classes.md).

*Enumtype*<br/>
Eine [CComEnumOnSTL-kompatible](../../atl/reference/ccomenumonstl-class.md)Enumeratorklasse.

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[ICollectionOnSTLImpl::get__NewEnum](#newenum)|Gibt ein Enumeratorobjekt für die Auflistung zurück.|
|[ICollectionOnSTLImpl::getcount](#get_count)|Gibt die Anzahl der Elemente in der Auflistung zurück.|
|[ICollectionOnSTLImpl::get_Item](#get_item)|Gibt das angeforderte Element aus der Auflistung zurück.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[ICollectionOnSTLImpl::m_coll](#m_coll)|Die Auflistung.|

## <a name="remarks"></a>Bemerkungen

Diese Klasse stellt die Implementierung für drei Methoden einer Auflistungsschnittstelle bereit: [getcount](#get_count), [get_Item](#get_item)und [get__NewEnum](#newenum).

So verwenden Sie diese Klasse:

- Definieren (oder ausleihen) Sie eine Sammlungsschnittstelle, die Sie implementieren möchten.

- Leiten Sie Ihre Klasse von `ICollectionOnSTLImpl` einer Spezialisierung basierend auf dieser Sammlungsschnittstelle ab.

- Verwenden Sie die abgeleitete Klasse, um Methoden `ICollectionOnSTLImpl`aus der Auflistungsschnittstelle zu implementieren, die nicht von behandelt werden.

> [!NOTE]
> Wenn es sich bei der Auflistungsschnittstelle um eine duale `ICollectionOnSTLImpl` Schnittstelle handelt, leiten Sie Ihre Klasse von [IDispatchImpl](../../atl/reference/idispatchimpl-class.md)ab, und übergeben Sie die Spezialisierung als ersten Vorlagenparameter, wenn ATL die Implementierung der `IDispatch` Methoden bereitstellen soll.

- Fügen Sie dem [m_coll-Member](#m_coll) Elemente hinzu, um die Auflistung aufzufüllen.

Weitere Informationen und Beispiele finden Sie unter [ATL-Sammlungen und -Enumeratoren](../../atl/atl-collections-and-enumerators.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`T`

`ICollectionOnSTLImpl`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlcom.h

## <a name="icollectiononstlimplgetcount"></a><a name="get_count"></a>ICollectionOnSTLImpl::getcount

Diese Methode gibt die Anzahl der Elemente in der Auflistung zurück.

```
STDMETHOD(getcount)(long* pcount);
```

### <a name="parameters"></a>Parameter

*pcount*<br/>
[out] Die Anzahl der Elemente in der Auflistung.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

## <a name="icollectiononstlimplget_item"></a><a name="get_item"></a>ICollectionOnSTLImpl::get_Item

Diese Methode gibt das angegebene Element aus der Auflistung zurück.

```
STDMETHOD(get_Item)(long Index, ItemType* pvar);
```

### <a name="parameters"></a>Parameter

*Index*<br/>
[in] Der 1-basierte Index eines Elements in der Auflistung.

*pvar*<br/>
[out] Das Element, das *Index*entspricht.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

### <a name="remarks"></a>Bemerkungen

Das Element wird erhalten, indem die Daten an der angegebenen Position in [m_coll](#m_coll) kopiert werden, indem die Kopiermethode der [Kopierrichtlinienklasse](../../atl/atl-copy-policy-classes.md) verwendet wird, die als Vorlagenargument in der `ICollectionOnSTLImpl` Spezialisierung übergeben wird.

## <a name="icollectiononstlimplget__newenum"></a><a name="newenum"></a>ICollectionOnSTLImpl::get__NewEnum

Gibt ein Enumeratorobjekt für die Auflistung zurück.

```
STDMETHOD(get__NewEnum)(IUnknown** ppUnk);
```

### <a name="parameters"></a>Parameter

*ppUnk*<br/>
[out] Der **IUnknown-Zeiger** eines neu erstellten Enumeratorobjekts.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

### <a name="remarks"></a>Bemerkungen

Der neu erstellte Enumerator verwaltet einen Iterator für die ursprüngliche Auflistung , `m_coll`(damit keine Kopie erstellt wird) und enthält einen COM-Verweis auf das Auflistungsobjekt, um sicherzustellen, dass die Auflistung erhalten bleibt, während hervorragende Enumeratoren vorhanden sind.

## <a name="icollectiononstlimplm_coll"></a><a name="m_coll"></a>ICollectionOnSTLImpl::m_coll

Dieses Element enthält die Elemente, die von der Auflistung dargestellt werden.

```
CollType m_coll;
```

## <a name="see-also"></a>Siehe auch

[ATLCollections-Beispiel](../../overview/visual-cpp-samples.md)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)
