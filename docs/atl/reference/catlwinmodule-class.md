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
ms.openlocfilehash: 04dc7e5b8c0c5dd21567f23395b4bafd4ae839dc
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229986"
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

|name|BESCHREIBUNG|
|----------|-----------------|
|["": Addkreatewnddata](#addcreatewnddata)|Fügt ein Datenobjekt hinzu.|
|["": Extractkreatewnddata](#extractcreatewnddata)|Gibt einen Zeiger auf das Datenobjekt des Fenster Moduls zurück.|

## <a name="remarks"></a>Bemerkungen

Diese Klasse bietet Unterstützung für alle ATL-Klassen, für die windowingfunktionen erforderlich sind.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[_ATL_WIN_MODULE](atl-typedefs.md#_atl_win_module)

`CAtlWinModule`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atlbase. h

## <a name="catlwinmoduleaddcreatewnddata"></a><a name="addcreatewnddata"></a>"": Addkreatewnddata

Diese Methode initialisiert eine-Struktur und fügt diese hinzu `_AtlCreateWndData` .

```cpp
void AddCreateWndData(_AtlCreateWndData* pData, void* pObject);
```

### <a name="parameters"></a>Parameter

*pData*<br/>
Ein Zeiger auf die `_AtlCreateWndData` -Struktur, die initialisiert und dem aktuellen Modul hinzugefügt werden soll.

*pObject*<br/>
Zeiger auf den Zeiger eines Objekts **`this`** .

### <a name="remarks"></a>Bemerkungen

Diese Methode ruft [atlwinmoduleaddkreatewnddata](winmodule-global-functions.md#atlwinmoduleaddcreatewnddata) auf, das eine [_AtlCreateWndData](../../atl/reference/atlcreatewnddata-structure.md) Struktur initialisiert. Diese Struktur speichert den **`this`** Zeiger, der zum Abrufen der Klasseninstanz in Fenster Prozeduren verwendet wird.

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

Diese Methode gibt einen Zeiger auf eine- `_AtlCreateWndData` Struktur zurück.

```cpp
void* ExtractCreateWndData();
```

### <a name="return-value"></a>Rückgabewert

Gibt einen Zeiger auf die- `_AtlCreateWndData` Struktur zurück, [CAtlWinModule::AddCreateWndData](#addcreatewnddata)die zuvor mit "" "" "" "" "" "" "" "" mit "" "" "" ".

## <a name="see-also"></a>Weitere Informationen

[_ATL_WIN_MODULE](atl-typedefs.md#_atl_win_module)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)<br/>
[Modul Klassen](../../atl/atl-module-classes.md)
