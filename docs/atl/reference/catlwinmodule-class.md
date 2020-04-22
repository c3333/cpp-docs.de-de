---
title: CAtlWinModule-Klasse
ms.date: 11/04/2016
f1_keywords:
- CAtlWinModule
- ATLBASE/ATL::CAtlWinModule
- ATLBASE/ATL::CAtlWinModule::CAtlWinModule
- ATLBASE/ATL::CAtlWinModule::AddCreateWndData
- ATLBASE/ATL::CAtlWinModule::ExtractCreateWndData
helpviewer_keywords:
- CAtlWinModule class
ms.assetid: 7ec844af-0f68-4a34-b0c8-9de50a025df0
ms.openlocfilehash: e131ca1b4eb6e320d533ad1292c23add6ffa46e5
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81748557"
---
# <a name="catlwinmodule-class"></a>CAtlWinModule-Klasse

Diese Klasse bietet Unterstützung für ATL-Fensterkomponenten.

> [!IMPORTANT]
> Diese Klasse und ihre Member können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

## <a name="syntax"></a>Syntax

```
class CAtlWinModule : public _ATL_WIN_MODULE
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAtlWinModule::CAtlWinModule](#catlwinmodule)|Der Konstruktor.|
|[CAtlWinModule::-CAtlWinModule](#dtor)|Der Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAtlWinModule::AddCreateWndData](#addcreatewnddata)|Fügt ein Datenobjekt hinzu.|
|[CAtlWinModule::ExtractCreateWndData](#extractcreatewnddata)|Gibt einen Zeiger auf das Datenobjekt des Fenstermoduls zurück.|

## <a name="remarks"></a>Bemerkungen

Diese Klasse bietet Unterstützung für alle ATL-Klassen, die Fensterfunktionen erfordern.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[_ATL_WIN_MODULE](atl-typedefs.md#_atl_win_module)

`CAtlWinModule`

## <a name="requirements"></a>Requirements (Anforderungen)

**Kopfzeile:** atlbase.h

## <a name="catlwinmoduleaddcreatewnddata"></a><a name="addcreatewnddata"></a>CAtlWinModule::AddCreateWndData

Diese Methode initialisiert und `_AtlCreateWndData` fügt eine Struktur hinzu.

```cpp
void AddCreateWndData(_AtlCreateWndData* pData, void* pObject);
```

### <a name="parameters"></a>Parameter

*pData*<br/>
Zeiger auf `_AtlCreateWndData` die zu initialisierende Struktur, die dem aktuellen Modul hinzugefügt werden soll.

*pObject*<br/>
Zeiger auf den **Zeiger** eines Objekts.

### <a name="remarks"></a>Bemerkungen

Diese Methode ruft [AtlWinModuleAddCreateWndData](winmodule-global-functions.md#atlwinmoduleaddcreatewnddata) auf, das eine [_AtlCreateWndData-Struktur](../../atl/reference/atlcreatewnddata-structure.md) initialisiert. Diese Struktur speichert den **zeiger,** der zum Abrufen der Klasseninstanz in Fensterprozeduren verwendet wird.

## <a name="catlwinmodulecatlwinmodule"></a><a name="catlwinmodule"></a>CAtlWinModule::CAtlWinModule

Der Konstruktor.

```
CAtlWinModule();
```

### <a name="remarks"></a>Bemerkungen

Wenn die Initialisierung fehlschlägt, wird eine **EXCEPTION_NONCONTINUABLE** Ausnahme ausgelöst.

## <a name="catlwinmodulecatlwinmodule"></a><a name="dtor"></a>CAtlWinModule::-CAtlWinModule

Der Destruktor.

```
~CAtlWinModule();
```

### <a name="remarks"></a>Bemerkungen

Gibt alle zugewiesenen Ressourcen frei.

## <a name="catlwinmoduleextractcreatewnddata"></a><a name="extractcreatewnddata"></a>CAtlWinModule::ExtractCreateWndData

Diese Methode gibt einen `_AtlCreateWndData` Zeiger auf eine Struktur zurück.

```cpp
void* ExtractCreateWndData();
```

### <a name="return-value"></a>Rückgabewert

Gibt einen Zeiger `_AtlCreateWndData` auf die Struktur zurück, die zuvor mit [CAtlWinModule::AddCreateWndData](#addcreatewnddata)oder NULL hinzugefügt wurde, wenn kein Objekt verfügbar ist.

## <a name="see-also"></a>Weitere Informationen

[_ATL_WIN_MODULE](atl-typedefs.md#_atl_win_module)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)<br/>
[Modulklassen](../../atl/atl-module-classes.md)
