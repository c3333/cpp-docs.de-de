---
title: COM-Kartenmakros
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::BEGIN_COM_MAP
- atlcom/ATL::END_COM_MAP
helpviewer_keywords:
- COM interfaces, COM map macros
ms.assetid: 0f33656d-321f-4996-90cc-9a7f21ab73c3
ms.openlocfilehash: 191a0ba0aeda6ad18cdac7ba14f7ab5f3b2282f7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326605"
---
# <a name="com-map-macros"></a>COM-Kartenmakros

Diese Makros definieren COM-Schnittstellenzuordnungen.

|||
|-|-|
|[BEGIN_COM_MAP](#begin_com_map)|Markiert den Anfang der COM-Schnittstellenzuordnungseinträge.|
|[END_COM_MAP](#end_com_map)|Markiert das Ende der COM-Schnittstellenzuordnungseinträge.|

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlcom.h

## <a name="begin_com_map"></a><a name="begin_com_map"></a>BEGIN_COM_MAP

Die COM-Zuordnung ist der Mechanismus, der Schnittstellen für `QueryInterface`ein Objekt für einen Client über verfügbar macht.

```
BEGIN_COM_MAP(x)
```

### <a name="parameters"></a>Parameter

*X*<br/>
[in] Der Name des Klassenobjekts, für das Sie Schnittstellen aussetzen.

### <a name="remarks"></a>Bemerkungen

[CComObjectRootEx::InternalQueryInterface](ccomobjectrootex-class.md#internalqueryinterface) gibt nur Zeiger für Schnittstellen in der COM-Zuordnung zurück. Starten Sie die Schnittstellenzuordnung mit dem BEGIN_COM_MAP-Makro, fügen Sie Einträge für jede Ihrer Schnittstellen mit dem [COM_INTERFACE_ENTRY](com-interface-entry-macros.md#com_interface_entry) Makro oder einer seiner Varianten hinzu, und vervollständigen Sie die Karte mit dem [END_COM_MAP-Makro.](#end_com_map)

### <a name="example"></a>Beispiel

Aus dem ATL [BEEPER-Beispiel:](../../overview/visual-cpp-samples.md)

[!code-cpp[NVC_ATL_COM#1](../../atl/codesnippet/cpp/com-map-macros_1.h)]

## <a name="end_com_map"></a><a name="end_com_map"></a>END_COM_MAP

Beendet die Definition der COM-Schnittstellenzuordnung.

```
END_COM_MAP()
```

## <a name="see-also"></a>Siehe auch

[Makros](../../atl/reference/atl-macros.md)<br/>
[COM Map Globale Funktionen](../../atl/reference/com-map-global-functions.md)
