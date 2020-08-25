---
title: Globale com Map-Funktionen
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::AtlInternalQueryInterface
- atlbase/ATL::InlineIsEqualIUnknown
helpviewer_keywords:
- COM interfaces, COM map global functions
ms.assetid: b9612d30-eb23-46ef-8093-d56f237d3cf1
ms.openlocfilehash: adf4e06eb46aed74d08071dccce1db549ca31226
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88833594"
---
# <a name="com-map-global-functions"></a>Globale com Map-Funktionen

Diese Funktionen bieten Unterstützung für com-Zuordnungs `IUnknown` Implementierungen.

|Funktion|Beschreibung|
|-|-|
|[AtlInternalQueryInterface](#atlinternalqueryinterface)|Delegiert an den `IUnknown` eines nicht aggregierten Objekts.|
|[InlineIsEqualIUnknown](#inlineisequaliunknown)|Generiert effizienten Code zum Vergleichen von Schnittstellen mit `IUnknown` .|

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atlbase. h

## <a name="atlinternalqueryinterface"></a><a name="atlinternalqueryinterface"></a> Atlinternalqueryinterface

Ruft einen Zeiger auf die angeforderte Schnittstelle ab.

```
HRESULT AtlInternalQueryInterface(
    void* pThis,
    const _ATL_INTMAP_ENTRY* pEntries,
    REFIID iid,
    void** ppvObject);
```

### <a name="parameters"></a>Parameter

*pThis*<br/>
in Ein Zeiger auf das-Objekt, das die com-Zuordnung der Schnittstellen enthält, die für verfügbar sind `QueryInterface` .

*pentries*<br/>
in Ein Array von- `_ATL_INTMAP_ENTRY` Strukturen, die auf eine Karte der verfügbaren Schnittstellen zugreifen.

*IID*<br/>
in Der GUID der angeforderten Schnittstelle.

*ppvObject*<br/>
vorgenommen Ein Zeiger auf den in *IID*angegebenen Schnittstellen Zeiger oder NULL, wenn die Schnittstelle nicht gefunden wurde.

### <a name="return-value"></a>Rückgabewert

Einer der HRESULT-Standardwerte.

### <a name="remarks"></a>Bemerkungen

`AtlInternalQueryInterface` behandelt nur Schnittstellen in der com-Zuordnungs Tabelle. Wenn das Objekt aggregiert wird, `AtlInternalQueryInterface` delegiert nicht an das äußere unbekannte. Sie können Schnittstellen in die com-Zuordnungs Tabelle mit dem Makro [COM_INTERFACE_ENTRY](com-interface-entry-macros.md#com_interface_entry) oder einer der Varianten eingeben.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Windowing#94](../../atl/codesnippet/cpp/com-map-global-functions_1.cpp)]

## <a name="inlineisequaliunknown"></a><a name="inlineisequaliunknown"></a> Inlineiabqualiunknown

Diese Funktion wird für den Sonderfall von Tests für aufgerufen `IUnknown` .

```
BOOL InlineIsEqualUnknown(REFGUID rguid1);
```

### <a name="parameters"></a>Parameter

*rguid1*<br/>
in Die GUID, die mit verglichen werden soll `IID_IUnknown` .

## <a name="see-also"></a>Siehe auch

[Funktionen](../../atl/reference/atl-functions.md)<br/>
[COM-Zuordnungs Makros](../../atl/reference/com-map-macros.md)
