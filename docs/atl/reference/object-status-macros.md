---
title: Objektstatusmakros
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::DECLARE_OLEMISC_STATUS
ms.assetid: 727dbef2-a342-4157-9d64-a421805d9747
ms.openlocfilehash: 5617ce7fb972c98775072f72244f91052d41ece3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326176"
---
# <a name="object-status-macros"></a>Objektstatusmakros

Dieses Makro legt Flags fest, die zu ActiveX-Steuerelementen gehören.

|||
|-|-|
|[DECLARE_OLEMISC_STATUS](#declare_olemisc_status)|Wird in ATL ActiveX-Steuerelementen verwendet, um die OLEMISC-Flags festzulegen.|

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlcom.h

## <a name="declare_olemisc_status"></a><a name="declare_olemisc_status"></a>DECLARE_OLEMISC_STATUS

Wird in ATL ActiveX-Steuerelementen verwendet, um die OLEMISC-Flags festzulegen.

```
DECLARE_OLEMISC_STATUS( miscstatus )
```

### <a name="parameters"></a>Parameter

*miscstatus*<br/>
Alle anwendbaren OLEMISC-Flags.

### <a name="remarks"></a>Bemerkungen

Dieses Makro wird verwendet, um die OLEMISC-Flags für ein ActiveX-Steuerelement festzulegen. Weitere Informationen finden Sie unter [IOleObject::GetMiscStatus.](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getmiscstatus)

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Windowing#124](../../atl/codesnippet/cpp/object-status-macros_1.h)]

## <a name="see-also"></a>Siehe auch

[Makros](../../atl/reference/atl-macros.md)
