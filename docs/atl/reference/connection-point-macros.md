---
title: Verbindungspunktmakros
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::BEGIN_CONNECTION_POINT_MAP
- atlcom/ATL::END_CONNECTION_POINT_MAP
helpviewer_keywords:
- connection points [C++], macros
ms.assetid: cc3a6dd3-5538-45df-b027-1f34963c31e5
ms.openlocfilehash: 361cf6ab2c7af142c1d57c002681ccf6e4a87bda
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81331496"
---
# <a name="connection-point-macros"></a>Verbindungspunktmakros

Diese Makros definieren Verbindungspunktkarten und Einträge.

|||
|-|-|
|[BEGIN_CONNECTION_POINT_MAP](#begin_connection_point_map)|Markiert den Anfang der Verbindungspunktzuordnungseinträge.|
|[CONNECTION_POINT_ENTRY](#connection_point_entry)|Gibt Verbindungspunkte in die Karte ein.|
|[CONNECTION_POINT_ENTRY_P](#connection_point_entry)| (Visual Studio 2017) Ähnlich wie CONNECTION_POINT_ENTRY, nimmt aber einen Zeiger auf iid.|
|[END_CONNECTION_POINT_MAP](#end_connection_point_map)|Markiert das Ende der Verbindungspunktzuordnungseinträge.|

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlcom.h

## <a name="begin_connection_point_map"></a><a name="begin_connection_point_map"></a>BEGIN_CONNECTION_POINT_MAP

Markiert den Anfang der Verbindungspunktzuordnungseinträge.

```
BEGIN_CONNECTION_POINT_MAP(x)
```

### <a name="parameters"></a>Parameter

*X*<br/>
[in] Der Name der Klasse, die die Verbindungspunkte enthält.

### <a name="remarks"></a>Bemerkungen

Starten Sie die Verbindungspunktzuordnung mit dem BEGIN_CONNECTION_POINT_MAP-Makro, fügen Sie Einträge für jeden Ihrer Verbindungspunkte mit dem [CONNECTION_POINT_ENTRY-Makro](#connection_point_entry) hinzu, und vervollständigen Sie die Karte mit dem [END_CONNECTION_POINT_MAP-Makro.](#end_connection_point_map)

Weitere Informationen zu Verbindungspunkten in ATL finden Sie im Artikel [Verbindungspunkte](../../atl/atl-connection-points.md).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Windowing#101](../../atl/codesnippet/cpp/connection-point-macros_1.h)]

## <a name="connection_point_entry-and-connection_point_entry_p"></a><a name="connection_point_entry"></a>CONNECTION_POINT_ENTRY und CONNECTION_POINT_ENTRY_P

Gibt einen Verbindungspunkt für die angegebene Schnittstelle in die Verbindungspunktzuordnung ein, damit darauf zugegriffen werden kann.

```
CONNECTION_POINT_ENTRY(iid)
CONNECTION_POINT_ENTRY_P(piid) // (Visual Studio 2017)
```

### <a name="parameters"></a>Parameter

*Iid*<br/>
[in] Die GUID der Schnittstelle, die der Verbindungspunktzuordnung hinzugefügt wird.

*piid*<br/>
[in] Zeiger auf die GUID der schnittstelle, die hinzugefügt wird.

### <a name="remarks"></a>Bemerkungen

Verbindungspunkteinträge in der Karte werden von [IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md)verwendet. Die Klasse, die die Verbindungspunktzuordnung `IConnectionPointContainerImpl`enthält, muss von erben.

Starten Sie die Verbindungspunktzuordnung mit dem [BEGIN_CONNECTION_POINT_MAP-Makro,](#begin_connection_point_map) fügen Sie Einträge für jeden Ihrer Verbindungspunkte mit dem Makro CONNECTION_POINT_ENTRY hinzu, und vervollständigen Sie die Karte mit dem [END_CONNECTION_POINT_MAP-Makro.](#end_connection_point_map)

Weitere Informationen zu Verbindungspunkten in ATL finden Sie im Artikel [Verbindungspunkte](../../atl/atl-connection-points.md).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Windowing#120](../../atl/codesnippet/cpp/connection-point-macros_2.h)]

## <a name="end_connection_point_map"></a><a name="end_connection_point_map"></a>END_CONNECTION_POINT_MAP

Markiert das Ende der Verbindungspunktzuordnungseinträge.

```
END_CONNECTION_POINT_MAP()
```

### <a name="remarks"></a>Bemerkungen

Starten Sie die Verbindungspunktzuordnung mit dem [BEGIN_CONNECTION_POINT_MAP-Makro,](#begin_connection_point_map) fügen Sie Einträge für jeden Ihrer Verbindungspunkte mit dem [CONNECTION_POINT_ENTRY-Makro](#connection_point_entry) hinzu, und vervollständigen Sie die Karte mit dem END_CONNECTION_POINT_MAP-Makro.

Weitere Informationen zu Verbindungspunkten in ATL finden Sie im Artikel [Verbindungspunkte](../../atl/atl-connection-points.md).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Windowing#128](../../atl/codesnippet/cpp/connection-point-macros_3.h)]

## <a name="see-also"></a>Siehe auch

[Makros](../../atl/reference/atl-macros.md)<br/>
[Globale Funktionen des Verbindungspunkts](../../atl/reference/connection-point-global-functions.md)
