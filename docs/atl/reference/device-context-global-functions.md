---
title: Globale Funktionen des Geräte Kontexts
ms.date: 11/04/2016
f1_keywords:
- atlwin/ATL::AtlCreateTargetDC
ms.assetid: 08ec28f6-daff-4882-9544-e8a4639d05c4
ms.openlocfilehash: d2d25660083f074683a3f42f878497ce14a008b8
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88833464"
---
# <a name="device-context-global-functions"></a>Globale Funktionen des Geräte Kontexts

Diese Funktion erstellt einen Gerätekontext für ein bestimmtes Gerät.

|Name|Beschreibung|
|-|-|
|[AtlCreateTargetDC](#atlcreatetargetdc)|Erstellt einen Gerätekontext.|

## <a name="atlcreatetargetdc"></a><a name="atlcreatetargetdc"></a> Atlkreatetargetdc

Erstellt einen Gerätekontext für das Gerät, das in der [DVTARGETDEVICE](/windows/win32/api/objidl/ns-objidl-dvtargetdevice) -Struktur angegeben ist.

```
HDC AtlCreateTargetDC(HDC hdc, DVTARGETDEVICE* ptd);
```

### <a name="parameters"></a>Parameter

*HDC*<br/>
in Das vorhandene Handle eines Geräte Kontexts oder NULL.

*ptd*<br/>
in Ein Zeiger auf die- `DVTARGETDEVICE` Struktur, die Informationen über das Zielgerät enthält.

### <a name="return-value"></a>Rückgabewert

Gibt das Handle für einen Gerätekontext für das Gerät zurück, das in angegeben ist `DVTARGETDEVICE` . Wenn kein Gerät angegeben ist, wird das Handle an das Standard Anzeigegerät zurückgegeben.

### <a name="remarks"></a>Bemerkungen

Wenn die-Struktur NULL ist und *hdc* NULL ist, erstellt einen Gerätekontext für das Standard Anzeigegerät.

Wenn *hdc* nicht NULL ist und *ptd* NULL ist, gibt die Funktion den vorhandenen *hdc*zurück.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atlwin. h

## <a name="see-also"></a>Siehe auch

[Funktionen](../../atl/reference/atl-functions.md)
