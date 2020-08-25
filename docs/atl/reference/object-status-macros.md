---
title: Objektstatusmakros
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::DECLARE_OLEMISC_STATUS
ms.assetid: 727dbef2-a342-4157-9d64-a421805d9747
ms.openlocfilehash: d9e2223739dc3d0636337e2e2f713c80dff50131
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88835232"
---
# <a name="object-status-macros"></a>Objektstatusmakros

Dieses Makro legt Flags fest, die zu ActiveX-Steuerelementen gehören.

|Name|Beschreibung|
|-|-|
|[DECLARE_OLEMISC_STATUS](#declare_olemisc_status)|Wird in ATL-ActiveX-Steuerelementen zum Festlegen der OLEMISC-Flags verwendet.|

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** Atlcom. h

## <a name="declare_olemisc_status"></a><a name="declare_olemisc_status"></a> DECLARE_OLEMISC_STATUS

Wird in ATL-ActiveX-Steuerelementen zum Festlegen der OLEMISC-Flags verwendet.

```
DECLARE_OLEMISC_STATUS( miscstatus )
```

### <a name="parameters"></a>Parameter

*fehlstatus*<br/>
Alle anwendbaren OLEMISC-Flags.

### <a name="remarks"></a>Bemerkungen

Dieses Makro wird verwendet, um die OLEMISC-Flags für ein ActiveX-Steuerelement festzulegen. Weitere Informationen finden Sie unter [IOleObject:: getfehlstatus](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getmiscstatus) .

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Windowing#124](../../atl/codesnippet/cpp/object-status-macros_1.h)]

## <a name="see-also"></a>Weitere Informationen

[Makros](../../atl/reference/atl-macros.md)
