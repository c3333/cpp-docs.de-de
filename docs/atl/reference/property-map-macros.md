---
title: Eigenschaften Zuordnungs Makros
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
ms.openlocfilehash: 1e2e7235dd924467d9d5e0613a704fedf8340ae4
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2020
ms.locfileid: "79422973"
---
# <a name="property-map-macros"></a>Eigenschaften Zuordnungs Makros

Diese Makros definieren Eigenschaften Zuordnungen und Einträge.

|||
|-|-|
|[BEGIN_PROP_MAP](#begin_prop_map)|Markiert den Anfang der ATL-Eigenschaften Zuordnung.|
|[PROP_DATA_ENTRY](#prop_data_entry)|Gibt den Block oder die Dimensionen eines ActiveX-Steuer Elements an.|
|[PROP_ENTRY_TYPE](#prop_entry_type)|Gibt eine Eigenschafts Beschreibung, eine Eigenschaften-DISPID und eine CLSID der Eigenschaften Seite in die Eigenschaften Zuordnung ein.|
|[PROP_ENTRY_TYPE_EX](#prop_entry_type_ex)|Gibt eine Eigenschafts Beschreibung, eine Eigenschaft "DISPID", eine Eigenschafts Seiten-CLSID und eine `IDispatch` IID in die Eigenschaften Zuordnung ein.|
|[PROP_PAGE](#prop_page)|Gibt eine CLSID einer Eigenschaften Seite in die Eigenschaften Zuordnung ein.|
|[END_PROP_MAP](#end_prop_map)|Markiert das Ende der ATL-Eigenschafts Zuordnung.|

## <a name="requirements"></a>Voraussetzungen

**Header:** Atlcom. h

##  <a name="begin_prop_map"></a>BEGIN_PROP_MAP

Markiert den Anfang der Eigenschaften Zuordnung des Objekts.

```
BEGIN_PROP_MAP(theClass)
```

### <a name="parameters"></a>Parameter

*spiegeln*<br/>
in Gibt die Klasse an, die die Eigenschaften Zuordnung enthält.

### <a name="remarks"></a>Hinweise

Die Eigenschaften Zuordnung speichert Eigenschafts Beschreibungen, Eigenschaften-DispIds, Eigenschaften Seiten-CLSIDs und `IDispatch` IIDs. Die Klassen [iperpropertybrowsingimpl](../../atl/reference/iperpropertybrowsingimpl-class.md), [ipersistpropertybagimpl](../../atl/reference/ipersistpropertybagimpl-class.md), [ipersiststreaminitimpl](../../atl/reference/ipersiststreaminitimpl-class.md)und [ISpecifyPropertyPagesImpl](../../atl/reference/ispecifypropertypagesimpl-class.md) verwenden die Eigenschaften Zuordnung, um diese Informationen abzurufen und festzulegen.

Wenn Sie ein Objekt mit dem ATL-Projekt-Assistenten erstellen, erstellt der Assistent eine leere Eigenschaften Zuordnung, indem BEGIN_PROP_MAP gefolgt von [END_PROP_MAP](#end_prop_map)angegeben wird.

BEGIN_PROP_MAP speichert den Block (d. h. die Dimensionen) einer Eigenschaften Zuordnung nicht, da ein Objekt, das eine Eigenschaften Zuordnung verwendet, möglicherweise keine Benutzeroberfläche hat, sodass es keinen Block hat. Wenn das Objekt ein ActiveX-Steuerelement mit einer Benutzeroberfläche ist, verfügt es über einen Block. In diesem Fall müssen Sie [PROP_DATA_ENTRY](#prop_data_entry) in der Eigenschaften Zuordnung angeben, um den Wertebereich bereitzustellen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Windowing#103](../../atl/codesnippet/cpp/property-map-macros_1.h)]

##  <a name="prop_data_entry"></a>PROP_DATA_ENTRY

Gibt den Block oder die Dimensionen eines ActiveX-Steuer Elements an.

```
PROP_DATA_ENTRY( szDesc, member, vt)
```

### <a name="parameters"></a>Parameter

*szdäsc*<br/>
in Die Eigenschafts Beschreibung.

*member*<br/>
in Der Datenmember, der den Block enthält. beispielsweise `m_sizeExtent`.

*vt*<br/>
in Gibt den Varianttyp der Eigenschaft an.

### <a name="remarks"></a>Hinweise

Dieses Makro bewirkt, dass der angegebene Datenmember persistent ist.

Wenn Sie ein ActiveX-Steuerelement erstellen, fügt der Assistent dieses Makro nach dem Eigenschafts Zuordnungs Makro [BEGIN_PROP_MAP](#begin_prop_map) und vor dem [END_PROP_MAP](#end_prop_map)der Eigenschaften Zuordnung ein.

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird der Umfang des-Objekts (`m_sizeExtent`) persistent gespeichert.

[!code-cpp[NVC_ATL_Windowing#131](../../atl/codesnippet/cpp/property-map-macros_2.h)]

[!code-cpp[NVC_ATL_Windowing#132](../../atl/codesnippet/cpp/property-map-macros_3.h)]

##  <a name="prop_entry_type"></a>PROP_ENTRY_TYPE

Verwenden Sie dieses Makro, um eine Eigenschafts Beschreibung, eine Eigenschaften-DISPID und eine CLSID der Eigenschaften Seite in die Eigenschaften Zuordnung des Objekts einzugeben.

```
PROP_ENTRY_TYPE( szDesc, dispid, clsid, vt)
```

### <a name="parameters"></a>Parameter

*szdäsc*<br/>
in Die Eigenschafts Beschreibung.

*DISPID*<br/>
in Die DispID der Eigenschaft.

*CLSID*<br/>
in Die CLSID der zugeordneten Eigenschaften Seite. Verwenden Sie den speziellen Wert CLSID_NULL für eine Eigenschaft, die nicht über eine zugeordnete Eigenschaften Seite verfügt.

*vt*<br/>
in Der Typ der Eigenschaft.

### <a name="remarks"></a>Hinweise

Das PROP_ENTRY-Makro war unsicher und veraltet. Sie wurde durch PROP_ENTRY_TYPE ersetzt.

Das [BEGIN_PROP_MAP](#begin_prop_map) -Makro markiert den Anfang der Eigenschaften Zuordnung. Das [END_PROP_MAP](#end_prop_map) -Makro markiert das Ende.

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie im Beispiel für [BEGIN_PROP_MAP](#begin_prop_map).

##  <a name="prop_entry_type_ex"></a>PROP_ENTRY_TYPE_EX

Ähnlich wie [PROP_ENTRY_TYPE](#prop_entry_type), ermöglicht Ihnen jedoch, eine bestimmte IID anzugeben, wenn das Objekt mehrere duale Schnittstellen unterstützt.

```
PROP_ENTRY_TYPE_EX( szDesc, dispid, clsid, iidDispatch, vt)
```

### <a name="parameters"></a>Parameter

*szdäsc*<br/>
in Die Eigenschafts Beschreibung.

*DISPID*<br/>
in Die DispID der Eigenschaft.

*CLSID*<br/>
in Die CLSID der zugeordneten Eigenschaften Seite. Verwenden Sie den speziellen Wert CLSID_NULL für eine Eigenschaft, die nicht über eine zugeordnete Eigenschaften Seite verfügt.

*iiddispatch*<br/>
in Die IID der Dual-Schnittstelle, die die Eigenschaft definiert.

*vt*<br/>
in Der Typ der Eigenschaft.

### <a name="remarks"></a>Hinweise

Das PROP_ENTRY_EX-Makro war unsicher und veraltet. Sie wurde durch PROP_ENTRY_TYPE_EX ersetzt.

Das [BEGIN_PROP_MAP](#begin_prop_map) -Makro markiert den Anfang der Eigenschaften Zuordnung. Das [END_PROP_MAP](#end_prop_map) -Makro markiert das Ende.

### <a name="example"></a>Beispiel

Im folgenden Beispiel werden Einträge für `IMyDual1` gruppiert, gefolgt von einem Eintrag für `IMyDual2`. Durch die Gruppierung durch Dual Interface wird die Leistung verbessert.

[!code-cpp[NVC_ATL_Windowing#133](../../atl/codesnippet/cpp/property-map-macros_4.h)]

##  <a name="prop_page"></a>PROP_PAGE

Verwenden Sie dieses Makro, um eine CLSID einer Eigenschaften Seite in die Eigenschaften Zuordnung des Objekts einzugeben.

```
PROP_PAGE(clsid)
```

### <a name="parameters"></a>Parameter

*CLSID*<br/>
in Die CLSID einer Eigenschaften Seite.

### <a name="remarks"></a>Hinweise

PROP_PAGE ähnelt [PROP_ENTRY_TYPE](#prop_entry_type), erfordert jedoch keine Eigenschafts Beschreibung oder DISPID.

> [!NOTE]
>  Wenn Sie bereits eine CLSID mit PROP_ENTRY_TYPE oder [PROP_ENTRY_TYPE_EX](#prop_entry_type_ex)eingegeben haben, müssen Sie keinen zusätzlichen Eintrag mit PROP_PAGE erstellen.

Das [BEGIN_PROP_MAP](#begin_prop_map) -Makro markiert den Anfang der Eigenschaften Zuordnung. Das [END_PROP_MAP](#end_prop_map) -Makro markiert das Ende.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Windowing#134](../../atl/codesnippet/cpp/property-map-macros_5.h)]

##  <a name="end_prop_map"></a>END_PROP_MAP

Markiert das Ende der Eigenschaften Zuordnung des Objekts.

```
END_PROP_MAP()
```

### <a name="remarks"></a>Hinweise

Wenn Sie ein Objekt mit dem ATL-Projekt-Assistenten erstellen, erstellt der Assistent eine leere Eigenschaften Zuordnung, indem [BEGIN_PROP_MAP](#begin_prop_map) gefolgt von END_PROP_MAP angegeben wird.

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie im Beispiel für [BEGIN_PROP_MAP](#begin_prop_map).

## <a name="see-also"></a>Siehe auch

[Makros](../../atl/reference/atl-macros.md)
