---
title: Snap-In-Objektmakros
ms.date: 11/04/2016
f1_keywords:
- atlsnap/ATL::BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP
- atlsnap/ATL::BEGIN_SNAPINTOOLBARID_MAP
- atlsnap/ATL::END_EXTENSION_SNAPIN_NODEINFO_MAP
- atlsnap/ATL::END_SNAPINTOOLBARID_MAP
- atlsnap/ATL::EXTENSION_SNAPIN_DATACLASS
- atlsnap/ATL::EXTENSION_SNAPIN_NODEINFO_ENTRY
- atlsnap/ATL::SNAPINMENUID
- atlsnap/ATL::SNAPINTOOLBARID_ENTRY
ms.assetid: 4e9850c0-e395-4929-86c9-584a81828053
ms.openlocfilehash: 6a57cdb3c9b6a4448bc954ff754ac9b18fa0b393
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325856"
---
# <a name="snap-in-object-macros"></a>Snap-In-Objektmakros

Diese Makros bieten Unterstützung für Snap-In-Erweiterungen.

|||
|-|-|
|[BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map)|Markiert den Anfang der Snap-In-Erweiterungsdatenklassenzuordnung für ein Snap-In-Objekt.|
|[BEGIN_SNAPINTOOLBARID_MAP](#begin_snapintoolbarid_map)|Markiert den Anfang der Symbolleistenzuordnung für ein Snap-In-Objekt.|
|[END_EXTENSION_SNAPIN_NODEINFO_MAP](#end_extension_snapin_nodeinfo_map)|Markiert das Ende der Snap-In-Erweiterungsdatenklassenzuordnung für ein Snap-In-Objekt.|
|[END_SNAPINTOOLBARID_MAP](#end_snapintoolbarid_map)|Markiert das Ende der Symbolleistenzuordnung für ein Snap-In-Objekt.|
|[EXTENSION_SNAPIN_DATACLASS](#extension_snapin_dataclass)|Erstellt einen Datenmember für die Datenklasse der Snap-In-Erweiterung.|
|[EXTENSION_SNAPIN_NODEINFO_ENTRY](#extension_snapin_nodeinfo_entry)|Gibt eine Snap-In-Erweiterungsdatenklasse in die Snap-In-Erweiterungsdatenklassenzuordnung des Snap-In-Objekts ein.|
|[SNAPINMENUID](#snapinmenuid)|Deklariert die ID des Kontextmenüs, das vom Snap-In-Objekt verwendet wird.|
|[SNAPINTOOLBARID_ENTRY](#snapintoolbarid_entry)|Betritt eine Symbolleiste in die Symbolleistenzuordnung des Snap-In-Objekts.|

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlsnap.h

## <a name="begin_extension_snapin_nodeinfo_map"></a><a name="begin_extension_snapin_nodeinfo_map"></a>BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP

Markiert den Anfang der Snap-In-Erweiterungsdatenklassenzuordnung.

```
BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP(classname)
```

### <a name="parameters"></a>Parameter

*Classname*<br/>
[in] Der Name der Snap-In-Erweiterungsdatenklasse.

### <a name="remarks"></a>Bemerkungen

Starten Sie die Snap-In-Erweiterungszuordnung mit dem BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP-Makro, fügen Sie Einträge für jeden Ihrer Snap-In-Erweiterungsdatentypen mit dem [EXTENSION_SNAPIN_NODEINFO_ENTRY-Makro](#extension_snapin_nodeinfo_entry) hinzu, und vervollständigen Sie die Karte mit dem [END_EXTENSION_SNAPIN_NODEINFO_MAP-Makro.](#end_extension_snapin_nodeinfo_map)

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Windowing#105](../../atl/codesnippet/cpp/snap-in-object-macros_1.h)]

## <a name="begin_snapintoolbarid_map"></a><a name="begin_snapintoolbarid_map"></a>BEGIN_SNAPINTOOLBARID_MAP

Deklariert den Anfang der Symbolleisten-ID-Zuordnung für das Snap-In-Objekt.

```
BEGIN_SNAPINTOOLBARID_MAP(_class)
```

### <a name="parameters"></a>Parameter

*_class*<br/>
[in] Gibt die Snap-In-Objektklasse an.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Windowing#106](../../atl/codesnippet/cpp/snap-in-object-macros_2.h)]

## <a name="end_extension_snapin_nodeinfo_map"></a><a name="end_extension_snapin_nodeinfo_map"></a>END_EXTENSION_SNAPIN_NODEINFO_MAP

Markiert das Ende der Snap-In-Erweiterungsdatenklassenzuordnung.

```
END_EXTENSION_SNAPIN_NODEINFO_MAP()
```

### <a name="remarks"></a>Bemerkungen

Starten Sie die Snap-In-Erweiterungszuordnung mit dem [BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP-Makro,](#begin_extension_snapin_nodeinfo_map) fügen Sie Einträge für jeden Ihrer Erweiterungs-Snap-In-Datentypen mit dem [EXTENSION_SNAPIN_NODEINFO_ENTRY-Makro](#extension_snapin_nodeinfo_entry) hinzu, und vervollständigen Sie die Karte mit dem END_EXTENSION_SNAPIN_NODEINFO_MAP-Makro.

### <a name="example"></a>Beispiel

Siehe Beispiel für [BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map).

## <a name="end_snapintoolbarid_map"></a><a name="end_snapintoolbarid_map"></a>END_SNAPINTOOLBARID_MAP

Deklariert das Ende der Symbolleisten-ID-Zuordnung für das Snap-In-Objekt.

```
END_SNAPINTOOLBARID_MAP( _class )
```

### <a name="parameters"></a>Parameter

*_class*<br/>
[in] Gibt die Snap-In-Objektklasse an.

### <a name="example"></a>Beispiel

Siehe Beispiel für [BEGIN_SNAPINTOOLBARID_MAP](#begin_snapintoolbarid_map).

## <a name="extension_snapin_dataclass"></a><a name="extension_snapin_dataclass"></a>EXTENSION_SNAPIN_DATACLASS

Fügt der Snap-In-Erweiterungsdatenklasse für eine **ISnapInItemImpl-abgeleitete**Klasse einen Datenmember hinzu.

```
EXTENSION_SNAPIN_DATACLASS(dataClass )
```

### <a name="parameters"></a>Parameter

*dataClass*<br/>
[in] Die Datenklasse der Snap-In-Erweiterung.

### <a name="remarks"></a>Bemerkungen

Diese Klasse sollte auch in eine Snap-In-Erweiterungsdatenklassenzuordnung eingegeben werden. Starten Sie die Datenklassenzuordnung der [BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map) Snap-In-Erweiterung mit dem BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP-Makro, fügen Sie Einträge für jeden Ihrer Snap-In-Erweiterungsdatentypen mit dem [EXTENSION_SNAPIN_NODEINFO_ENTRY-Makro](#extension_snapin_nodeinfo_entry) hinzu, und vervollständigen Sie die Karte mit dem [END_EXTENSION_SNAPIN_NODEINFO_MAP-Makro.](#end_extension_snapin_nodeinfo_map)

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Windowing#105](../../atl/codesnippet/cpp/snap-in-object-macros_1.h)]

## <a name="extension_snapin_nodeinfo_entry"></a><a name="extension_snapin_nodeinfo_entry"></a>EXTENSION_SNAPIN_NODEINFO_ENTRY

Fügt der Snap-In-Erweiterungsdatenklassenzuordnung eine Snap-In-Erweiterungsdatenklasse hinzu.

```
EXTENSION_SNAPIN_NODEINFO_ENTRY( dataClass )
```

### <a name="parameters"></a>Parameter

*dataClass*<br/>
[in] Die Datenklasse der Snap-In-Erweiterung.

### <a name="remarks"></a>Bemerkungen

Starten Sie die Datenklassenzuordnung der [BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map) Snap-In-Erweiterung mit dem BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP-Makro, fügen Sie Einträge für jeden Ihrer Snap-In-Erweiterungsdatentypen mit dem EXTENSION_SNAPIN_NODEINFO_ENTRY-Makro hinzu, und vervollständigen Sie die Karte mit dem [END_EXTENSION_SNAPIN_NODEINFO_MAP-Makro.](#end_extension_snapin_nodeinfo_map)

### <a name="example"></a>Beispiel

Siehe Beispiel für [BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map).

## <a name="snapinmenuid"></a><a name="snapinmenuid"></a>SNAPINMENUID

Verwenden Sie dieses Makro, um die Kontextmenüressource des Snap-In-Objekts zu deklarieren.

```
SNAPINMENUID( id )
```

### <a name="parameters"></a>Parameter

*id*<br/>
[in] Identifiziert das Kontextmenü des Snap-In-Objekts.

## <a name="snapintoolbarid_entry"></a><a name="snapintoolbarid_entry"></a>SNAPINTOOLBARID_ENTRY

Verwenden Sie dieses Makro, um eine Symbolleisten-ID in die Symbolleisten-ID-Zuordnung des Snap-In-Objekts einzugeben.

```
SNAPINTOOLBARID_ENTRY( id )
```

### <a name="parameters"></a>Parameter

*id*<br/>
[in] Identifiziert das Symbolleistensteuerelement.

### <a name="remarks"></a>Bemerkungen

Das [BEGIN_SNAPINTOOLBARID_MAP](#begin_snapintoolbarid_map) Makro markiert den Anfang der Symbolleisten-ID-Zuordnung; das [END_SNAPINTOOLBARID_MAP-Makro](#end_snapintoolbarid_map) markiert das Ende.

### <a name="example"></a>Beispiel

Siehe Beispiel für [BEGIN_SNAPINTOOLBARID_MAP](#begin_snapintoolbarid_map).

## <a name="see-also"></a>Siehe auch

[Makros](../../atl/reference/atl-macros.md)
