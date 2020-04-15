---
title: Eigenschaftenzuordnungsmakros
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::BEGIN_PROP_MAP
- atlcom/ATL::PROP_DATA_ENTRY
- atlcom/ATL::PROP_ENTRY_TYPE
- atlcom/ATL::PROP_ENTRY_TYPE_EX
- atlcom/ATL::PROP_PAGE
- atlcom/ATL::END_PROP_MAP
helpviewer_keywords:
- property maps
ms.assetid: 128bc742-2b98-4b97-a243-684dbb83db77
ms.openlocfilehash: 56fdb02939a99e396b9000705753e2475b80f6dc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326093"
---
# <a name="property-map-macros"></a>Eigenschaftenzuordnungsmakros

Diese Makros definieren Eigenschaftenzuordnungen und Einträge.

|||
|-|-|
|[BEGIN_PROP_MAP](#begin_prop_map)|Markiert den Anfang der ATL-Eigenschaftszuordnung.|
|[PROP_DATA_ENTRY](#prop_data_entry)|Gibt die Ausdehnung oder Dimensionen eines ActiveX-Steuerelements an.|
|[PROP_ENTRY_TYPE](#prop_entry_type)|Gibt eine Eigenschaftenbeschreibung, eine Eigenschaft DISPID und die Eigenschaftenseite CLSID in die Eigenschaftenzuordnung ein.|
|[PROP_ENTRY_TYPE_EX](#prop_entry_type_ex)|Gibt eine Eigenschaftenbeschreibung, eine Eigenschaft DISPID, `IDispatch` die Eigenschaftenseite CLSID und IID in die Eigenschaftenzuordnung ein.|
|[PROP_PAGE](#prop_page)|Gibt eine Eigenschaftenseite CLSID in die Eigenschaftenzuordnung ein.|
|[END_PROP_MAP](#end_prop_map)|Markiert das Ende der ATL-Eigenschaftszuordnung.|

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlcom.h

## <a name="begin_prop_map"></a><a name="begin_prop_map"></a>BEGIN_PROP_MAP

Markiert den Anfang der Eigenschaftszuordnung des Objekts.

```
BEGIN_PROP_MAP(theClass)
```

### <a name="parameters"></a>Parameter

*theClass*<br/>
[in] Gibt die Klasse an, die die Eigenschaftenzuordnung enthält.

### <a name="remarks"></a>Bemerkungen

Die Eigenschaftenzuordnung speichert Eigenschaftenbeschreibungen, EigenschaftenDISPIDs, Eigenschaftenseite CLSIDs und `IDispatch` IIDs. Die Klassen [IPerPropertyBrowsingImpl](../../atl/reference/iperpropertybrowsingimpl-class.md), [IPersistPropertyBagImpl](../../atl/reference/ipersistpropertybagimpl-class.md), [IPersistStreamInitImpl](../../atl/reference/ipersiststreaminitimpl-class.md)und [ISpecifyPropertyPagesImpl](../../atl/reference/ispecifypropertypagesimpl-class.md) verwenden die Eigenschaftenzuordnung, um diese Informationen abzurufen und festzulegen.

Wenn Sie ein Objekt mit dem ATL-Projekt-Assistenten erstellen, erstellt der Assistent eine leere Eigenschaftenzuordnung, indem er BEGIN_PROP_MAP gefolgt von [END_PROP_MAP](#end_prop_map)angibt.

BEGIN_PROP_MAP speichert nicht die Ausdehnung (d. h. die Dimensionen) einer Eigenschaftenzuordnung, da ein Objekt, das eine Eigenschaftenzuordnung verwendet, möglicherweise keine Benutzeroberfläche hat, sodass es keine Ausdehnung hätte. Wenn es sich bei dem Objekt um ein ActiveX-Steuerelement mit einer Benutzeroberfläche handelt, hat es eine Ausdehnung. In diesem Fall müssen Sie [PROP_DATA_ENTRY](#prop_data_entry) in der Eigenschaftenzuordnung angeben, um die Ausdehnung anzugeben.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Windowing#103](../../atl/codesnippet/cpp/property-map-macros_1.h)]

## <a name="prop_data_entry"></a><a name="prop_data_entry"></a>PROP_DATA_ENTRY

Gibt die Ausdehnung oder Dimensionen eines ActiveX-Steuerelements an.

```
PROP_DATA_ENTRY( szDesc, member, vt)
```

### <a name="parameters"></a>Parameter

*szDesc*<br/>
[in] Die Eigenschaftenbeschreibung.

*Mitglied*<br/>
[in] Das Datenelement, das den Umfang enthält; z. `m_sizeExtent`B. .

*vt*<br/>
[in] Gibt den VARIANT-Typ der Eigenschaft an.

### <a name="remarks"></a>Bemerkungen

Dieses Makro bewirkt, dass das angegebene Datenelement beibehalten wird.

Wenn Sie ein ActiveX-Steuerelement erstellen, fügt der Assistent dieses Makro ein, nachdem das Eigenschaftenzuordnungsmakro [BEGIN_PROP_MAP](#begin_prop_map) und vor dem Eigenschaftenzuordnungsmakro [END_PROP_MAP](#end_prop_map).

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird die Ausdehnung des Objekts (`m_sizeExtent`) beibehalten.

[!code-cpp[NVC_ATL_Windowing#131](../../atl/codesnippet/cpp/property-map-macros_2.h)]

[!code-cpp[NVC_ATL_Windowing#132](../../atl/codesnippet/cpp/property-map-macros_3.h)]

## <a name="prop_entry_type"></a><a name="prop_entry_type"></a>PROP_ENTRY_TYPE

Verwenden Sie dieses Makro, um eine Eigenschaftenbeschreibung, Eine EigenschaftdisPID und eine Eigenschaftenseite CLSID in die Eigenschaftenzuordnung des Objekts einzugeben.

```
PROP_ENTRY_TYPE( szDesc, dispid, clsid, vt)
```

### <a name="parameters"></a>Parameter

*szDesc*<br/>
[in] Die Eigenschaftenbeschreibung.

*Dispid*<br/>
[in] Die DISPID der Eigenschaft.

*clsid*<br/>
[in] Die CLSID der zugehörigen Eigenschaftenseite. Verwenden Sie den sonderwert CLSID_NULL für eine Eigenschaft, der keine Eigenschaftenseite zugeordnet ist.

*vt*<br/>
[in] Der Typ der Eigenschaft.

### <a name="remarks"></a>Bemerkungen

Das PROP_ENTRY Makro war unsicher und veraltet. Es wurde durch PROP_ENTRY_TYPE ersetzt.

Das [BEGIN_PROP_MAP-Makro](#begin_prop_map) markiert den Anfang der Eigenschaftenzuordnung. das [END_PROP_MAP-Makro](#end_prop_map) markiert das Ende.

### <a name="example"></a>Beispiel

Siehe Beispiel für [BEGIN_PROP_MAP](#begin_prop_map).

## <a name="prop_entry_type_ex"></a><a name="prop_entry_type_ex"></a>PROP_ENTRY_TYPE_EX

Ähnlich wie [PROP_ENTRY_TYPE](#prop_entry_type), können Sie jedoch eine bestimmte IID angeben, wenn Ihr Objekt mehrere duale Schnittstellen unterstützt.

```
PROP_ENTRY_TYPE_EX( szDesc, dispid, clsid, iidDispatch, vt)
```

### <a name="parameters"></a>Parameter

*szDesc*<br/>
[in] Die Eigenschaftenbeschreibung.

*Dispid*<br/>
[in] Die DISPID der Eigenschaft.

*clsid*<br/>
[in] Die CLSID der zugehörigen Eigenschaftenseite. Verwenden Sie den sonderwert CLSID_NULL für eine Eigenschaft, der keine Eigenschaftenseite zugeordnet ist.

*iidDispatch*<br/>
[in] Die IID der dualen Schnittstelle, die die Eigenschaft definiert.

*vt*<br/>
[in] Der Typ der Eigenschaft.

### <a name="remarks"></a>Bemerkungen

Das PROP_ENTRY_EX Makro war unsicher und veraltet. Es wurde durch PROP_ENTRY_TYPE_EX ersetzt.

Das [BEGIN_PROP_MAP-Makro](#begin_prop_map) markiert den Anfang der Eigenschaftenzuordnung. das [END_PROP_MAP-Makro](#end_prop_map) markiert das Ende.

### <a name="example"></a>Beispiel

Im folgenden Beispiel `IMyDual1` werden Einträge für `IMyDual2`gefolgt von einem Eintrag für gruppiert. Die Gruppierung nach dualer Schnittstelle verbessert die Leistung.

[!code-cpp[NVC_ATL_Windowing#133](../../atl/codesnippet/cpp/property-map-macros_4.h)]

## <a name="prop_page"></a><a name="prop_page"></a>PROP_PAGE

Verwenden Sie dieses Makro, um eine Eigenschaftenseite CLSID in die Eigenschaftenzuordnung des Objekts einzugeben.

```
PROP_PAGE(clsid)
```

### <a name="parameters"></a>Parameter

*clsid*<br/>
[in] Die CLSID einer Eigenschaftenseite.

### <a name="remarks"></a>Bemerkungen

PROP_PAGE ist [ähnlich wie PROP_ENTRY_TYPE](#prop_entry_type), erfordert jedoch keine Eigenschaftenbeschreibung oder DISPID.

> [!NOTE]
> Wenn Sie bereits eine CLSID mit PROP_ENTRY_TYPE oder [PROP_ENTRY_TYPE_EX](#prop_entry_type_ex)eingegeben haben, müssen Sie keinen zusätzlichen Eintrag mit PROP_PAGE vornehmen.

Das [BEGIN_PROP_MAP-Makro](#begin_prop_map) markiert den Anfang der Eigenschaftenzuordnung. das [END_PROP_MAP-Makro](#end_prop_map) markiert das Ende.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Windowing#134](../../atl/codesnippet/cpp/property-map-macros_5.h)]

## <a name="end_prop_map"></a><a name="end_prop_map"></a>END_PROP_MAP

Markiert das Ende der Eigenschaftszuordnung des Objekts.

```
END_PROP_MAP()
```

### <a name="remarks"></a>Bemerkungen

Wenn Sie ein Objekt mit dem ATL-Projekt-Assistenten erstellen, erstellt der Assistent eine leere Eigenschaftenzuordnung, indem [er BEGIN_PROP_MAP](#begin_prop_map) gefolgt von END_PROP_MAP angibt.

### <a name="example"></a>Beispiel

Siehe Beispiel für [BEGIN_PROP_MAP](#begin_prop_map).

## <a name="see-also"></a>Siehe auch

[Makros](../../atl/reference/atl-macros.md)
