---
title: COM-Zuordnungs Makros
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::BEGIN_COM_MAP
- atlcom/ATL::END_COM_MAP
helpviewer_keywords:
- COM interfaces, COM map macros
ms.assetid: 0f33656d-321f-4996-90cc-9a7f21ab73c3
ms.openlocfilehash: 100402e17ca1bee5f338c37f2315fbc4898a713e
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88833581"
---
# <a name="com-map-macros"></a>COM-Zuordnungs Makros

Diese Makros definieren com-Schnittstellen Zuordnungen.

|Makro|Beschreibung|
|-|-|
|[BEGIN_COM_MAP](#begin_com_map)|Markiert den Anfang der COM-Schnittstellen Zuordnungs Einträge.|
|[END_COM_MAP](#end_com_map)|Markiert das Ende der COM-Schnittstellen Zuordnungs Einträge.|

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** Atlcom. h

## <a name="begin_com_map"></a><a name="begin_com_map"></a> BEGIN_COM_MAP

Die com-Zuordnung ist der Mechanismus, der Schnittstellen für ein Objekt für einen Client über verfügbar macht `QueryInterface` .

```
BEGIN_COM_MAP(x)
```

### <a name="parameters"></a>Parameter

*x*<br/>
in Der Name des Klassen Objekts, für das Sie Schnittstellen verfügbar machen.

### <a name="remarks"></a>Bemerkungen

[CComObjectRootEx:: InternalQueryInterface](ccomobjectrootex-class.md#internalqueryinterface) gibt nur Zeiger für Schnittstellen in der com-Zuordnung zurück. Starten Sie Ihre Schnittstellen Zuordnung mit dem BEGIN_COM_MAP-Makro, fügen Sie mit dem [COM_INTERFACE_ENTRY](com-interface-entry-macros.md#com_interface_entry) -Makro oder einer der Varianten Einträge für jede Schnittstelle hinzu, und vervollständigen Sie die Zuordnung mit dem [END_COM_MAP](#end_com_map) -Makro.

### <a name="example"></a>Beispiel

Aus dem ATL- [Beeper](../../overview/visual-cpp-samples.md) -Beispiel:

[!code-cpp[NVC_ATL_COM#1](../../atl/codesnippet/cpp/com-map-macros_1.h)]

## <a name="end_com_map"></a><a name="end_com_map"></a> END_COM_MAP

Beendet die Definition der COM-Schnittstellen Zuordnung.

```
END_COM_MAP()
```

## <a name="see-also"></a>Weitere Informationen

[Makros](../../atl/reference/atl-macros.md)<br/>
[Globale com Map-Funktionen](../../atl/reference/com-map-global-functions.md)
