---
title: Globale Funktionen des Gerätekontexts
ms.date: 11/04/2016
f1_keywords:
- atlwin/ATL::AtlCreateTargetDC
ms.assetid: 08ec28f6-daff-4882-9544-e8a4639d05c4
ms.openlocfilehash: e640f310a1976c29a39f0ab7c2575dfd1073c889
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330154"
---
# <a name="device-context-global-functions"></a>Globale Funktionen des Gerätekontexts

Diese Funktion erstellt einen Gerätekontext für ein bestimmtes Gerät.

|||
|-|-|
|[AtlCreateTargetDC](#atlcreatetargetdc)|Erstellt einen Gerätekontext.|

## <a name="atlcreatetargetdc"></a><a name="atlcreatetargetdc"></a>AtlCreateTargetDC

Erstellt einen Gerätekontext für das in der [DVTARGETDEVICE-Struktur](/windows/win32/api/objidl/ns-objidl-dvtargetdevice) angegebene Gerät.

```
HDC AtlCreateTargetDC(HDC hdc, DVTARGETDEVICE* ptd);
```

### <a name="parameters"></a>Parameter

*Hdc*<br/>
[in] Das vorhandene Handle eines Gerätekontexts oder NULL.

*Ptd*<br/>
[in] Ein Zeiger auf `DVTARGETDEVICE` die Struktur, die Informationen über das Zielgerät enthält.

### <a name="return-value"></a>Rückgabewert

Gibt das Handle an einen Gerätekontext `DVTARGETDEVICE`für das gerät zurück, das im angegeben ist. Wenn kein Gerät angegeben ist, wird das Handle an das Standardanzeigegerät zurückgegeben.

### <a name="remarks"></a>Bemerkungen

Wenn die Struktur NULL und *hdc* NULL ist, wird ein Gerätekontext für das Standardanzeigegerät erstellt.

Wenn *hdc* nicht NULL und *ptd* NULL ist, gibt die Funktion die vorhandene *hdc*zurück.

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlwin.h

## <a name="see-also"></a>Siehe auch

[Functions](../../atl/reference/atl-functions.md)
