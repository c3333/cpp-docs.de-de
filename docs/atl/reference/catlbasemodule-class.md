---
title: Klasse von "-Klasse"
ms.date: 11/04/2016
f1_keywords:
- CAtlBaseModule
- ATLCORE/ATL::CAtlBaseModule
- ATLCORE/ATL::CAtlBaseModule::CAtlBaseModule
- ATLCORE/ATL::CAtlBaseModule::AddResourceInstance
- ATLCORE/ATL::CAtlBaseModule::GetHInstanceAt
- ATLCORE/ATL::CAtlBaseModule::GetModuleInstance
- ATLCORE/ATL::CAtlBaseModule::GetResourceInstance
- ATLCORE/ATL::CAtlBaseModule::RemoveResourceInstance
- ATLCORE/ATL::CAtlBaseModule::SetResourceInstance
- ATLCORE/ATL::CAtlBaseModule::m_bInitFailed
helpviewer_keywords:
- CAtlBaseModule class
ms.assetid: 55ade80c-9b0c-4c51-933e-2158436c1096
ms.openlocfilehash: d57d6e631cb287496a4ff5516e97e65ec0152e30
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168292"
---
# <a name="catlbasemodule-class"></a>Klasse von "-Klasse"

Diese Klasse wird in jedem ATL-Projekt instanziiert.

## <a name="syntax"></a>Syntax

```cpp
class CAtlBaseModule : public _ATL_BASE_MODULE
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|["", "", "".](#catlbasemodule)|Der Konstruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|["", "", "".](#addresourceinstance)|Fügt der Liste der gespeicherten Handles eine Ressourcen Instanz hinzu.|
|["" Für ""](#gethinstanceat)|Gibt ein Handle für eine angegebene Ressourcen Instanz zurück.|
|["": Getmoduleinstance](#getmoduleinstance)|Gibt die Modul Instanz aus einem `CAtlBaseModule` -Objekt zurück.|
|["" ("")](#getresourceinstance)|Gibt die Ressourcen Instanz aus einem `CAtlBaseModule` -Objekt zurück.|
|["", "", "", "".](#removeresourceinstance)|Entfernt eine Ressourcen Instanz aus der Liste der gespeicherten Handles.|
|["" ("") "":](#setresourceinstance)|Legt die Ressourcen Instanz eines- `CAtlBaseModule` Objekts fest.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|["": M_bInitFailed](#m_binitfailed)|Eine Variable, die angibt, ob die Modul Initialisierung fehlgeschlagen ist.|

## <a name="remarks"></a>Bemerkungen

Eine Instanz von `CAtlBaseModule` mit dem Namen _AtlBaseModule ist in jedem ATL-Projekt vorhanden, das ein Handle für die Modul Instanz enthält, ein Handle für das Modul, das Ressourcen enthält (standardmäßig ein und dasselbe), und ein Array von Handles für Module, die primäre Ressourcen bereitstellen. `CAtlBaseModule`kann über mehrere Threads sicher zugegriffen werden.

Diese Klasse ersetzt die veraltete [CComModule](../../atl/reference/ccommodule-class.md) -Klasse, die in früheren Versionen von ATL verwendet wurde.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[_ATL_BASE_MODULE](atl-typedefs.md#_atl_base_module)

`CAtlBaseModule`

## <a name="requirements"></a>Anforderungen

**Header:** atlcore. h

## <a name="catlbasemoduleaddresourceinstance"></a><a name="addresourceinstance"></a>"", "", "".

Fügt der Liste der gespeicherten Handles eine Ressourcen Instanz hinzu.

```cpp
bool AddResourceInstance(HINSTANCE hInst) throw();
```

### <a name="parameters"></a>Parameter

*hinst*<br/>
Die hinzu zufügende Ressourcen Instanz.

### <a name="return-value"></a>Rückgabewert

Gibt true zurück, wenn die Ressource erfolgreich hinzugefügt wurde, andernfalls false.

## <a name="catlbasemodulecatlbasemodule"></a><a name="catlbasemodule"></a>"", "", "".

Der Konstruktor.

```cpp
CAtlBaseModule() throw();
```

### <a name="remarks"></a>Bemerkungen

Erstellt das `CAtlBaseModule`-Objekt.

## <a name="catlbasemodulegethinstanceat"></a><a name="gethinstanceat"></a>"" Für ""

Gibt ein Handle für eine angegebene Ressourcen Instanz zurück.

```cpp
HINSTANCE GetHInstanceAt(int i) throw();
```

### <a name="parameters"></a>Parameter

*Ich*<br/>
Die Nummer der Ressourcen Instanz.

### <a name="return-value"></a>Rückgabewert

Gibt das Handle für die Ressourcen Instanz oder NULL zurück, wenn keine zugehörige Ressourcen Instanz vorhanden ist.

## <a name="catlbasemodulegetmoduleinstance"></a><a name="getmoduleinstance"></a>"": Getmoduleinstance

Gibt die Modul Instanz aus einem `CAtlBaseModule` -Objekt zurück.

```cpp
HINSTANCE GetModuleInstance() throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt die Modul Instanz zurück.

## <a name="catlbasemodulegetresourceinstance"></a><a name="getresourceinstance"></a>"" ("")

Gibt die Ressourcen Instanz zurück.

```cpp
HINSTANCE GetResourceInstance() throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt die Ressourcen Instanz zurück.

## <a name="catlbasemodulem_binitfailed"></a><a name="m_binitfailed"></a>"": M_bInitFailed

Eine Variable, die angibt, ob die Modul Initialisierung fehlgeschlagen ist.

```cpp
static bool m_bInitFailed;
```

### <a name="remarks"></a>Bemerkungen

True, wenn das Modul initialisiert wurde, false, wenn es nicht initialisiert werden konnte.

## <a name="catlbasemoduleremoveresourceinstance"></a><a name="removeresourceinstance"></a>"", "", "", "".

Entfernt eine Ressourcen Instanz aus der Liste der gespeicherten Handles.

```cpp
bool RemoveResourceInstance(HINSTANCE hInst) throw();
```

### <a name="parameters"></a>Parameter

*hinst*<br/>
Die zu entfern gende Ressourcen Instanz.

### <a name="return-value"></a>Rückgabewert

Gibt true zurück, wenn die Ressource erfolgreich entfernt wurde, andernfalls false.

## <a name="catlbasemodulesetresourceinstance"></a><a name="setresourceinstance"></a>"" ("") "":

Legt die Ressourcen Instanz eines- `CAtlBaseModule` Objekts fest.

```cpp
HINSTANCE SetResourceInstance(HINSTANCE hInst) throw();
```

### <a name="parameters"></a>Parameter

*hinst*<br/>
Die neue Ressourcen Instanz.

### <a name="return-value"></a>Rückgabewert

Gibt die aktualisierte Ressourcen Instanz zurück.

## <a name="see-also"></a>Weitere Informationen:

[Klassenübersicht](../../atl/atl-class-overview.md)<br/>
[Modul Klassen](../../atl/atl-module-classes.md)
