---
title: Globale winmodule-Funktionen
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::AtlWinModuleAddCreateWndData
- atlbase/ATL::AtlWinModuleExtractCreateWndData
ms.assetid: 8ce45a5b-26a7-491f-9096-c09ceca5f2c2
ms.openlocfilehash: 1a929fd0f583150e84ce5b1efa7e896bc16e4247
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229934"
---
# <a name="winmodule-global-functions"></a>Globale winmodule-Funktionen

Diese Funktionen bieten Unterstützung für `_AtlCreateWndData` Struktur Vorgänge.

> [!IMPORTANT]
> Die in der folgenden Tabelle aufgeführten Funktionen können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

|||
|-|-|
|[AtlWinModuleAddCreateWndData](#atlwinmoduleaddcreatewnddata)|Mit dieser Funktion wird eine `_AtlCreateWndData`-Struktur initialisiert und hinzugefügt.|
|[AtlWinModuleExtractCreateWndData](#atlwinmoduleextractcreatewnddata)|Mit dieser Funktion wird eine vorhandene `_AtlCreateWndData`-Struktur extrahiert.|

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atlbase. h

## <a name="atlwinmoduleaddcreatewnddata"></a><a name="atlwinmoduleaddcreatewnddata"></a>Atlwinmoduleaddkreatewnddata

Mit dieser Funktion wird eine `_AtlCreateWndData`-Struktur initialisiert und hinzugefügt.

```
ATLINLINE ATLAPI_(void) AtlWinModuleAddCreateWndData(
    _ATL_WIN_MODULE* pWinModule,
    _AtlCreateWndData* pData,
    void* pObject);
```

### <a name="parameters"></a>Parameter

*pwinmodule*<br/>
Zeiger auf die [_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md) Struktur eines Moduls.

*pData*<br/>
Ein Zeiger auf die [_AtlCreateWndData](../../atl/reference/atlcreatewnddata-structure.md) -Struktur, die initialisiert und dem aktuellen Modul hinzugefügt werden soll.

*pObject*<br/>
Zeiger auf den Zeiger eines Objekts **`this`** .

### <a name="remarks"></a>Bemerkungen

Initialisiert eine- `_AtlCreateWndData` Struktur, die zum Speichern des Zeigers verwendet wird, der zum **`this`** verweisen auf Klassen Instanzen verwendet wird, und fügt ihn der Liste hinzu, auf die durch die Struktur eines Moduls verwiesen wird `_ATL_WIN_MODULE70` . [Wird von](catlwinmodule-class.md#addcreatewnddata)"" mit "" von "" für "" aufgerufen.

## <a name="atlwinmoduleextractcreatewnddata"></a><a name="atlwinmoduleextractcreatewnddata"></a>Atlwinmoduleextractkreatewnddata

Mit dieser Funktion wird eine vorhandene `_AtlCreateWndData`-Struktur extrahiert.

```
ATLINLINE ATLAPI_(void*) AtlWinModuleExtractCreateWndData(_ATL_WIN_MODULE* pWinModule);
```

### <a name="parameters"></a>Parameter

*pwinmodule*<br/>
Zeiger auf die [_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md) Struktur eines Moduls.

### <a name="return-value"></a>Rückgabewert

Gibt einen Zeiger auf die [_AtlCreateWndData](../../atl/reference/atlcreatewnddata-structure.md) -Struktur zurück.

### <a name="remarks"></a>Bemerkungen

Diese Funktion extrahiert eine vorhandene `_AtlCreateWndData` Struktur aus der Liste, auf die durch die Struktur eines Moduls verwiesen wird `_ATL_WIN_MODULE70` .

## <a name="see-also"></a>Siehe auch

[Funktionen](../../atl/reference/atl-functions.md)
