---
title: Snap-in-Objekt Makros
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
ms.openlocfilehash: 7e006a17ad480ea79f6aeec224278815c8c3f164
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88835193"
---
# <a name="snap-in-object-macros"></a>Snap-in-Objekt Makros

Diese Makros bieten Unterstützung für Snap-in-Erweiterungen.

|Name|Beschreibung|
|-|-|
|[BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map)|Markiert den Anfang der Daten Klassen Zuordnung der Snap-in-Erweiterung für ein Snap-in-Objekt.|
|[BEGIN_SNAPINTOOLBARID_MAP](#begin_snapintoolbarid_map)|Markiert den Anfang der Symbolleisten Zuordnung für ein Snap-in-Objekt.|
|[END_EXTENSION_SNAPIN_NODEINFO_MAP](#end_extension_snapin_nodeinfo_map)|Markiert das Ende der Daten Klassen Zuordnung für die Snap-in-Erweiterung für ein Snap-in-Objekt.|
|[END_SNAPINTOOLBARID_MAP](#end_snapintoolbarid_map)|Markiert das Ende der Symbolleisten Zuordnung für ein Snap-in-Objekt.|
|[EXTENSION_SNAPIN_DATACLASS](#extension_snapin_dataclass)|Erstellt ein Datenmember für die Datenklasse der Snap-in-Erweiterung.|
|[EXTENSION_SNAPIN_NODEINFO_ENTRY](#extension_snapin_nodeinfo_entry)|Gibt eine Datenklasse der Snap-in-Erweiterungs Daten in die Daten Klassen Zuordnung der Snap-in-Erweiterung des Snap-in-Objekts ein.|
|[Snapinmenuid](#snapinmenuid)|Deklariert die ID des Kontextmenüs, das vom Snap-in-Objekt verwendet wird.|
|[SNAPINTOOLBARID_ENTRY](#snapintoolbarid_entry)|Gibt eine Symbolleiste in die Symbolleisten Zuordnung des Snap-in-Objekts ein.|

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atlsnap. h

## <a name="begin_extension_snapin_nodeinfo_map"></a><a name="begin_extension_snapin_nodeinfo_map"></a> BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP

Markiert den Anfang der Daten Klassen Zuordnung für die Snap-in-Erweiterung.

```
BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP(classname)
```

### <a name="parameters"></a>Parameter

*classname*<br/>
in Der Name der Datenklasse der Snap-in-Erweiterungs Daten.

### <a name="remarks"></a>Bemerkungen

Starten Sie die Snap-in-Erweiterungs Zuordnung mit dem BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP-Makro, fügen Sie mit dem [EXTENSION_SNAPIN_NODEINFO_ENTRY](#extension_snapin_nodeinfo_entry) -Makro Einträge für jeden der Snap-in-Erweiterungs Datentypen hinzu, und vervollständigen Sie die Zuordnung mit dem [END_EXTENSION_SNAPIN_NODEINFO_MAP](#end_extension_snapin_nodeinfo_map) -Makro.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Windowing#105](../../atl/codesnippet/cpp/snap-in-object-macros_1.h)]

## <a name="begin_snapintoolbarid_map"></a><a name="begin_snapintoolbarid_map"></a> BEGIN_SNAPINTOOLBARID_MAP

Deklariert den Anfang der Symbolleisten-ID-Zuordnung für das Snap-in-Objekt.

```
BEGIN_SNAPINTOOLBARID_MAP(_class)
```

### <a name="parameters"></a>Parameter

*_class*<br/>
in Gibt die Snap-in-Objektklasse an.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Windowing#106](../../atl/codesnippet/cpp/snap-in-object-macros_2.h)]

## <a name="end_extension_snapin_nodeinfo_map"></a><a name="end_extension_snapin_nodeinfo_map"></a> END_EXTENSION_SNAPIN_NODEINFO_MAP

Markiert das Ende der Daten Klassen Zuordnung für die Snap-in-Erweiterung.

```
END_EXTENSION_SNAPIN_NODEINFO_MAP()
```

### <a name="remarks"></a>Bemerkungen

Starten Sie die Snap-in-Erweiterungs Zuordnung mit dem [BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map) -Makro, fügen Sie mit dem [EXTENSION_SNAPIN_NODEINFO_ENTRY](#extension_snapin_nodeinfo_entry) -Makro Einträge für jeden der Erweiterungs-Snap-in-Datentypen hinzu, und vervollständigen Sie die Zuordnung mit dem END_EXTENSION_SNAPIN_NODEINFO_MAP-Makro.

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie im Beispiel für [BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map).

## <a name="end_snapintoolbarid_map"></a><a name="end_snapintoolbarid_map"></a> END_SNAPINTOOLBARID_MAP

Deklariert das Ende der Symbolleisten-ID-Zuordnung für das Snap-in-Objekt.

```
END_SNAPINTOOLBARID_MAP( _class )
```

### <a name="parameters"></a>Parameter

*_class*<br/>
in Gibt die Snap-in-Objektklasse an.

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie im Beispiel für [BEGIN_SNAPINTOOLBARID_MAP](#begin_snapintoolbarid_map).

## <a name="extension_snapin_dataclass"></a><a name="extension_snapin_dataclass"></a> EXTENSION_SNAPIN_DATACLASS

Fügt der Snap-in-Erweiterungs Datenklasse für eine von **isnapinitemimpl**abgeleitete Klasse einen Datenmember hinzu.

```
EXTENSION_SNAPIN_DATACLASS(dataClass )
```

### <a name="parameters"></a>Parameter

*dataClass*<br/>
in Die Datenklasse der Snap-in-Erweiterung.

### <a name="remarks"></a>Bemerkungen

Diese Klasse sollte auch in eine Daten Klassen Zuordnung für die Snap-in-Erweiterung eingegeben werden. Starten Sie die Daten Klassen Zuordnung für die Snap-in-Erweiterung mit dem [BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map) -Makro, fügen Sie Einträge für jeden der Snap-in-Erweiterungs Datentypen mit dem [EXTENSION_SNAPIN_NODEINFO_ENTRY](#extension_snapin_nodeinfo_entry) -Makro hinzu, und vervollständigen Sie die Zuordnung mit dem [END_EXTENSION_SNAPIN_NODEINFO_MAP](#end_extension_snapin_nodeinfo_map) -Makro.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Windowing#105](../../atl/codesnippet/cpp/snap-in-object-macros_1.h)]

## <a name="extension_snapin_nodeinfo_entry"></a><a name="extension_snapin_nodeinfo_entry"></a> EXTENSION_SNAPIN_NODEINFO_ENTRY

Fügt der Daten Klassen Zuordnung der Snap-in-Erweiterung eine Datenklasse für Snap-in-Erweiterungen hinzu.

```
EXTENSION_SNAPIN_NODEINFO_ENTRY( dataClass )
```

### <a name="parameters"></a>Parameter

*dataClass*<br/>
in Die Datenklasse der Snap-in-Erweiterung.

### <a name="remarks"></a>Bemerkungen

Starten Sie die Daten Klassen Zuordnung für die Snap-in-Erweiterung mit dem [BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map) -Makro, fügen Sie Einträge für jeden der Snap-in-Erweiterungs Datentypen mit dem EXTENSION_SNAPIN_NODEINFO_ENTRY-Makro hinzu, und vervollständigen Sie die Zuordnung mit dem [END_EXTENSION_SNAPIN_NODEINFO_MAP](#end_extension_snapin_nodeinfo_map) -Makro.

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie im Beispiel für [BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map).

## <a name="snapinmenuid"></a><a name="snapinmenuid"></a> Snapinmenuid

Verwenden Sie dieses Makro, um die Kontextmenü Ressource des Snap-in-Objekts zu deklarieren.

```
SNAPINMENUID( id )
```

### <a name="parameters"></a>Parameter

*id*<br/>
in Identifiziert das Kontextmenü des Snap-in-Objekts.

## <a name="snapintoolbarid_entry"></a><a name="snapintoolbarid_entry"></a> SNAPINTOOLBARID_ENTRY

Verwenden Sie dieses Makro, um eine Symbolleisten-ID in die Symbolleisten-ID-Zuordnung des Snap-in-Objekts einzugeben.

```
SNAPINTOOLBARID_ENTRY( id )
```

### <a name="parameters"></a>Parameter

*id*<br/>
in Identifiziert das Symbolleisten-Steuerelement.

### <a name="remarks"></a>Bemerkungen

Das [BEGIN_SNAPINTOOLBARID_MAP](#begin_snapintoolbarid_map) -Makro markiert den Anfang der Symbolleisten-ID-Zuordnung. Das [END_SNAPINTOOLBARID_MAP](#end_snapintoolbarid_map) -Makro markiert das Ende.

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie im Beispiel für [BEGIN_SNAPINTOOLBARID_MAP](#begin_snapintoolbarid_map).

## <a name="see-also"></a>Weitere Informationen

[Makros](../../atl/reference/atl-macros.md)
