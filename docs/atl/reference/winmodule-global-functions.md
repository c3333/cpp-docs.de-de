---
title: WinModule Globale Funktionen
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::AtlWinModuleAddCreateWndData
- atlbase/ATL::AtlWinModuleExtractCreateWndData
ms.assetid: 8ce45a5b-26a7-491f-9096-c09ceca5f2c2
ms.openlocfilehash: 3d7d001a2835514cc5385a7069c0bcda58cdd88e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329359"
---
# <a name="winmodule-global-functions"></a>WinModule Globale Funktionen

Diese Funktionen unterstützen `_AtlCreateWndData` Strukturvorgänge.

> [!IMPORTANT]
> Die in der folgenden Tabelle aufgeführten Funktionen können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

|||
|-|-|
|[AtlWinModuleAddCreateWndData](#atlwinmoduleaddcreatewnddata)|Mit dieser Funktion wird eine `_AtlCreateWndData`-Struktur initialisiert und hinzugefügt.|
|[AtlWinModuleExtractCreateWndData](#atlwinmoduleextractcreatewnddata)|Mit dieser Funktion wird eine vorhandene `_AtlCreateWndData`-Struktur extrahiert.|

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlbase.h

## <a name="atlwinmoduleaddcreatewnddata"></a><a name="atlwinmoduleaddcreatewnddata"></a>AtlWinModuleAddCreateWndData

Mit dieser Funktion wird eine `_AtlCreateWndData`-Struktur initialisiert und hinzugefügt.

```
ATLINLINE ATLAPI_(void) AtlWinModuleAddCreateWndData(
    _ATL_WIN_MODULE* pWinModule,
    _AtlCreateWndData* pData,
    void* pObject);
```

### <a name="parameters"></a>Parameter

*pWinModule*<br/>
Zeiger auf [die _ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md) Struktur eines Moduls.

*pData*<br/>
Zeiger auf die [_AtlCreateWndData](../../atl/reference/atlcreatewnddata-structure.md) Struktur, die initialisiert und dem aktuellen Modul hinzugefügt werden soll.

*pObject*<br/>
Zeiger auf den **Zeiger** eines Objekts.

### <a name="remarks"></a>Bemerkungen

Initialisiert eine `_AtlCreateWndData` Struktur, die zum Speichern **des Zeigers** verwendet wird, der für den Verweis auf Klasseninstanzen verwendet wird, und fügt sie der Liste hinzu, auf die von der Struktur eines Moduls `_ATL_WIN_MODULE70` verwiesen wird. Aufgerufen von [CAtlWinModule::AddCreateWndData](catlwinmodule-class.md#addcreatewnddata).

## <a name="atlwinmoduleextractcreatewnddata"></a><a name="atlwinmoduleextractcreatewnddata"></a>AtlWinModuleExtractCreateWndData

Mit dieser Funktion wird eine vorhandene `_AtlCreateWndData`-Struktur extrahiert.

```
ATLINLINE ATLAPI_(void*) AtlWinModuleExtractCreateWndData(_ATL_WIN_MODULE* pWinModule);
```

### <a name="parameters"></a>Parameter

*pWinModule*<br/>
Zeiger auf [die _ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md) Struktur eines Moduls.

### <a name="return-value"></a>Rückgabewert

Gibt einen Zeiger auf die [_AtlCreateWndData-Struktur](../../atl/reference/atlcreatewnddata-structure.md) zurück.

### <a name="remarks"></a>Bemerkungen

Diese Funktion extrahiert `_AtlCreateWndData` eine vorhandene Struktur aus der Liste, auf die die Struktur eines Moduls `_ATL_WIN_MODULE70` verweist.

## <a name="see-also"></a>Siehe auch

[Functions](../../atl/reference/atl-functions.md)
