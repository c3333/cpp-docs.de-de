---
title: Verbindungspunkt Makros
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::BEGIN_CONNECTION_POINT_MAP
- atlcom/ATL::END_CONNECTION_POINT_MAP
helpviewer_keywords:
- connection points [C++], macros
ms.assetid: cc3a6dd3-5538-45df-b027-1f34963c31e5
ms.openlocfilehash: cb8d6f696980ef91d7b43c960dc50289ea8500a6
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2020
ms.locfileid: "79423153"
---
# <a name="connection-point-macros"></a>Verbindungspunkt Makros

Diese Makros definieren Verbindungspunkt Zuordnungen und-Einträge.

|||
|-|-|
|[BEGIN_CONNECTION_POINT_MAP](#begin_connection_point_map)|Markiert den Anfang der Verbindungspunkt-Zuordnungs Einträge.|
|[CONNECTION_POINT_ENTRY](#connection_point_entry)|Gibt Verbindungspunkte in die Zuordnung ein.|
|[CONNECTION_POINT_ENTRY_P](#connection_point_entry)| (Visual Studio 2017) Ähnlich wie CONNECTION_POINT_ENTRY, aber einen Zeiger auf IID.|
|[END_CONNECTION_POINT_MAP](#end_connection_point_map)|Markiert das Ende der Zuordnungs Einträge für Verbindungspunkte.|

## <a name="requirements"></a>Voraussetzungen

**Header:** Atlcom. h

##  <a name="begin_connection_point_map"></a>BEGIN_CONNECTION_POINT_MAP

Markiert den Anfang der Verbindungspunkt-Zuordnungs Einträge.

```
BEGIN_CONNECTION_POINT_MAP(x)
```

### <a name="parameters"></a>Parameter

*x*<br/>
in Der Name der Klasse, die die Verbindungspunkte enthält.

### <a name="remarks"></a>Hinweise

Starten Sie die Verbindungspunkt Zuordnung mit dem BEGIN_CONNECTION_POINT_MAP-Makro, fügen Sie dem [CONNECTION_POINT_ENTRY](#connection_point_entry) -Makro Einträge für jeden der Verbindungspunkte hinzu, und vervollständigen Sie die Zuordnung mit dem [END_CONNECTION_POINT_MAP](#end_connection_point_map) -Makro.

Weitere Informationen zu Verbindungs Punkten in ATL finden Sie im Artikel [Verbindungspunkte](../../atl/atl-connection-points.md).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Windowing#101](../../atl/codesnippet/cpp/connection-point-macros_1.h)]

##  <a name="connection_point_entry"></a>CONNECTION_POINT_ENTRY und CONNECTION_POINT_ENTRY_P

Gibt einen Verbindungspunkt für die angegebene Schnittstelle in die Verbindungspunkt Zuordnung ein, sodass darauf zugegriffen werden kann.

```
CONNECTION_POINT_ENTRY(iid)
CONNECTION_POINT_ENTRY_P(piid) // (Visual Studio 2017)
```

### <a name="parameters"></a>Parameter

*IID*<br/>
in Die GUID der Schnittstelle, die der Verbindungspunkt Zuordnung hinzugefügt wird.

*piid*<br/>
in Zeiger auf die GUID der Schnittstelle, die ADDE ist.

### <a name="remarks"></a>Hinweise

Verbindungspunkt Einträge in der Zuordnung werden von [IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md)verwendet. Die Klasse, die die Verbindungspunkt Zuordnung enthält, muss von `IConnectionPointContainerImpl`erben.

Starten Sie die Verbindungspunkt Zuordnung mit dem [BEGIN_CONNECTION_POINT_MAP](#begin_connection_point_map) -Makro, fügen Sie dem CONNECTION_POINT_ENTRY-Makro Einträge für jeden der Verbindungspunkte hinzu, und vervollständigen Sie die Zuordnung mit dem [END_CONNECTION_POINT_MAP](#end_connection_point_map) -Makro.

Weitere Informationen zu Verbindungs Punkten in ATL finden Sie im Artikel [Verbindungspunkte](../../atl/atl-connection-points.md).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Windowing#120](../../atl/codesnippet/cpp/connection-point-macros_2.h)]

##  <a name="end_connection_point_map"></a>END_CONNECTION_POINT_MAP

Markiert das Ende der Zuordnungs Einträge für Verbindungspunkte.

```
END_CONNECTION_POINT_MAP()
```

### <a name="remarks"></a>Hinweise

Starten Sie die Verbindungspunkt Zuordnung mit dem [BEGIN_CONNECTION_POINT_MAP](#begin_connection_point_map) -Makro, fügen Sie dem [CONNECTION_POINT_ENTRY](#connection_point_entry) -Makro Einträge für jeden der Verbindungspunkte hinzu, und vervollständigen Sie die Zuordnung mit dem END_CONNECTION_POINT_MAP-Makro.

Weitere Informationen zu Verbindungs Punkten in ATL finden Sie im Artikel [Verbindungspunkte](../../atl/atl-connection-points.md).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Windowing#128](../../atl/codesnippet/cpp/connection-point-macros_3.h)]

## <a name="see-also"></a>Siehe auch

[Makros](../../atl/reference/atl-macros.md)<br/>
[Globale Verbindungspunkt-Funktionen](../../atl/reference/connection-point-global-functions.md)
