---
title: Klasse von "-Klasse"
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
ms.openlocfilehash: 5cdf13ebbb982ad8184a52dcf1a3e30d71e4e5b0
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "82167707"
---
# <a name="catlwinmodule-class"></a>Klasse von "-Klasse"

Diese Klasse bietet Unterstützung für ATL-windowingkomponenten.

> [!IMPORTANT]
> Diese Klasse und ihre Member können in Anwendungen, die im Windows-Runtime ausgeführt werden, nicht verwendet werden.

## <a name="syntax"></a>Syntax

```cpp
class CAtlWinModule : public _ATL_WIN_MODULE
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|["" Für ""](#catlwinmodule)|Der Konstruktor.|
|["" Für ""](#dtor)|Der Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|["": Addkreatewnddata](#addcreatewnddata)|Fügt ein Datenobjekt hinzu.|
|["": Extractkreatewnddata](#extractcreatewnddata)|Gibt einen Zeiger auf das Datenobjekt des Fenster Moduls zurück.|

## <a name="remarks"></a>Bemerkungen

Diese Klasse bietet Unterstützung für alle ATL-Klassen, für die windowingfunktionen erforderlich sind.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[_ATL_WIN_MODULE](atl-typedefs.md#_atl_win_module)

`CAtlWinModule`

## <a name="requirements"></a>Anforderungen

**Header:** atlbase. h

## <a name="catlwinmoduleaddcreatewnddata"></a><a name="addcreatewnddata"></a>"": Addkreatewnddata

Diese Methode initialisiert eine `_AtlCreateWndData` -Struktur und fügt diese hinzu.

```cpp
void AddCreateWndData(_AtlCreateWndData* pData, void* pObject);
```

### <a name="parameters"></a>Parameter

*pData*<br/>
Ein Zeiger auf `_AtlCreateWndData` die-Struktur, die initialisiert und dem aktuellen Modul hinzugefügt werden soll.

*pObject*<br/>
Zeiger auf den **this** -Zeiger eines Objekts.

### <a name="remarks"></a>Bemerkungen

Diese Methode ruft [atlwinmoduleaddkreatewnddata](winmodule-global-functions.md#atlwinmoduleaddcreatewnddata) auf, das eine [_AtlCreateWndData](../../atl/reference/atlcreatewnddata-structure.md) Struktur initialisiert. Diese-Struktur speichert den **this** -Zeiger, der zum Abrufen der Klasseninstanz in Fenster Prozeduren verwendet wird.

## <a name="catlwinmodulecatlwinmodule"></a><a name="catlwinmodule"></a>"" Für ""

Der Konstruktor.

```cpp
CAtlWinModule();
```

### <a name="remarks"></a>Bemerkungen

Wenn die Initialisierung fehlschlägt, wird eine **EXCEPTION_NONCONTINUABLE** Ausnahme ausgelöst.

## <a name="catlwinmodulecatlwinmodule"></a><a name="dtor"></a>"" Für ""

Der Destruktor.

```cpp
~CAtlWinModule();
```

### <a name="remarks"></a>Bemerkungen

Gibt alle zugeordneten Ressourcen frei.

## <a name="catlwinmoduleextractcreatewnddata"></a><a name="extractcreatewnddata"></a>"": Extractkreatewnddata

Diese Methode gibt einen Zeiger auf eine `_AtlCreateWndData` -Struktur zurück.

```cpp
void* ExtractCreateWndData();
```

### <a name="return-value"></a>Rückgabewert

Gibt einen Zeiger auf die `_AtlCreateWndData` -Struktur zurück, die zuvor mit "" "" "" "" "" "" "" " [" mit "](#addcreatewnddata)" "" "" ".

## <a name="see-also"></a>Weitere Informationen:

[_ATL_WIN_MODULE](atl-typedefs.md#_atl_win_module)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)<br/>
[Modul Klassen](../../atl/atl-module-classes.md)
