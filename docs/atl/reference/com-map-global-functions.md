---
title: COM Map Globale Funktionen
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::AtlInternalQueryInterface
- atlbase/ATL::InlineIsEqualIUnknown
helpviewer_keywords:
- COM interfaces, COM map global functions
ms.assetid: b9612d30-eb23-46ef-8093-d56f237d3cf1
ms.openlocfilehash: c4ce7c7a68c0744ad65ef4914088fa12d3340628
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326697"
---
# <a name="com-map-global-functions"></a>COM Map Globale Funktionen

Diese Funktionen unterstützen COM `IUnknown` Map-Implementierungen.

|||
|-|-|
|[AtlInternalQueryInterface](#atlinternalqueryinterface)|Delegiert `IUnknown` an das eines nicht aggregierten Objekts.|
|[InlineIsEqualIUnknown](#inlineisequaliunknown)|Generiert effizienten Code zum Vergleichen `IUnknown`von Schnittstellen mit .|

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlbase.h

## <a name="atlinternalqueryinterface"></a><a name="atlinternalqueryinterface"></a>AtlInternalQueryInterface

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
[in] Ein Zeiger auf das Objekt, das die COM-Zuordnung der Schnittstellen enthält, die für `QueryInterface`verfügbar gemacht werden.

*pEntries*<br/>
[in] Ein Array `_ATL_INTMAP_ENTRY` von Strukturen, die auf eine Karte verfügbarer Schnittstellen zugreifen.

*Iid*<br/>
[in] Die GUID der angeforderten Schnittstelle.

*ppvObject*<br/>
[out] Ein Zeiger auf den in *iid*, oder NULL angegebenen Schnittstellenzeiger, wenn die Schnittstelle nicht gefunden wird.

### <a name="return-value"></a>Rückgabewert

Einer der Standard-HRESULT-Werte.

### <a name="remarks"></a>Bemerkungen

`AtlInternalQueryInterface`verarbeitet nur Schnittstellen in der COM-Map-Tabelle. Wenn Ihr Objekt aggregiert `AtlInternalQueryInterface` ist, wird nicht an das äußere Unbekannte delegiert. Sie können Schnittstellen in die COM-Map-Tabelle mit dem Makro [COM_INTERFACE_ENTRY](com-interface-entry-macros.md#com_interface_entry) oder einer seiner Varianten eingeben.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Windowing#94](../../atl/codesnippet/cpp/com-map-global-functions_1.cpp)]

## <a name="inlineisequaliunknown"></a><a name="inlineisequaliunknown"></a>InlineIsEqualIUnbekannt

Rufen Sie diese Funktion auf, `IUnknown`für den speziellen Fall von Tests für .

```
BOOL InlineIsEqualUnknown(REFGUID rguid1);
```

### <a name="parameters"></a>Parameter

*rguid1*<br/>
[in] Die GUID, `IID_IUnknown`die mit verglichen werden soll.

## <a name="see-also"></a>Siehe auch

[Functions](../../atl/reference/atl-functions.md)<br/>
[COM-Kartenmakros](../../atl/reference/com-map-macros.md)
