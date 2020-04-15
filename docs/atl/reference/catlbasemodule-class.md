---
title: CAtlBaseModule-Klasse
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
ms.openlocfilehash: a55412eff18fd04ac4e41c0f001991c1cf725b9f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321509"
---
# <a name="catlbasemodule-class"></a>CAtlBaseModule-Klasse

Diese Klasse wird in jedem ATL-Projekt instanziiert.

## <a name="syntax"></a>Syntax

```
class CAtlBaseModule : public _ATL_BASE_MODULE
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAtlBaseModule::CAtlBaseModule](#catlbasemodule)|Der Konstruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAtlBaseModule::AddResourceInstance](#addresourceinstance)|Fügt der Liste der gespeicherten Handles eine Ressourceninstanz hinzu.|
|[CAtlBaseModule::GetHInstanceAt](#gethinstanceat)|Gibt ein Handle an eine angegebene Ressourceninstanz zurück.|
|[CAtlBaseModule::GetModuleInstance](#getmoduleinstance)|Gibt die Modulinstanz `CAtlBaseModule` von einem Objekt zurück.|
|[CAtlBaseModule::GetResourceInstance](#getresourceinstance)|Gibt die Ressourceninstanz `CAtlBaseModule` aus einem Objekt zurück.|
|[CAtlBaseModule::RemoveResourceInstance](#removeresourceinstance)|Entfernt eine Ressourceninstanz aus der Liste der gespeicherten Handles.|
|[CAtlBaseModule::SetResourceInstance](#setresourceinstance)|Legt die Ressourceninstanz `CAtlBaseModule` eines Objekts fest.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAtlBaseModule::m_bInitFailed](#m_binitfailed)|Eine Variable, die angibt, ob die Modulinitialisierung fehlgeschlagen ist.|

## <a name="remarks"></a>Bemerkungen

In jedem `CAtlBaseModule` ATL-Projekt ist eine Instanz mit benannten _AtlBaseModule vorhanden, die ein Handle für die Modulinstanz, ein Handle für das Modul mit Ressourcen (die standardmäßig ein und dasselbe sind) und ein Array von Handles für Module, die primäre Ressourcen bereitstellen, enthält. `CAtlBaseModule`sicher von mehreren Threads aus zugegriffen werden kann.

Diese Klasse ersetzt die veraltete [CComModule-Klasse,](../../atl/reference/ccommodule-class.md) die in früheren Versionen von ATL verwendet wurde.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[_ATL_BASE_MODULE](atl-typedefs.md#_atl_base_module)

`CAtlBaseModule`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlcore.h

## <a name="catlbasemoduleaddresourceinstance"></a><a name="addresourceinstance"></a>CAtlBaseModule::AddResourceInstance

Fügt der Liste der gespeicherten Handles eine Ressourceninstanz hinzu.

```
bool AddResourceInstance(HINSTANCE hInst) throw();
```

### <a name="parameters"></a>Parameter

*hInst*<br/>
Die hinzuzufügende Ressourceninstanz.

### <a name="return-value"></a>Rückgabewert

Gibt true zurück, wenn die Ressource erfolgreich hinzugefügt wurde, andernfalls false.

## <a name="catlbasemodulecatlbasemodule"></a><a name="catlbasemodule"></a>CAtlBaseModule::CAtlBaseModule

Der Konstruktor.

```
CAtlBaseModule() throw();
```

### <a name="remarks"></a>Bemerkungen

Erstellt das `CAtlBaseModule`-Objekt.

## <a name="catlbasemodulegethinstanceat"></a><a name="gethinstanceat"></a>CAtlBaseModule::GetHInstanceAt

Gibt ein Handle an eine angegebene Ressourceninstanz zurück.

```
HINSTANCE GetHInstanceAt(int i) throw();
```

### <a name="parameters"></a>Parameter

*Ⅰ*<br/>
Die Nummer der Ressourceninstanz.

### <a name="return-value"></a>Rückgabewert

Gibt das Handle an die Ressourceninstanz oder NULL zurück, wenn keine entsprechende Ressourceninstanz vorhanden ist.

## <a name="catlbasemodulegetmoduleinstance"></a><a name="getmoduleinstance"></a>CAtlBaseModule::GetModuleInstance

Gibt die Modulinstanz `CAtlBaseModule` von einem Objekt zurück.

```
HINSTANCE GetModuleInstance() throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt die Modulinstanz zurück.

## <a name="catlbasemodulegetresourceinstance"></a><a name="getresourceinstance"></a>CAtlBaseModule::GetResourceInstance

Gibt die Ressourceninstanz zurück.

```
HINSTANCE GetResourceInstance() throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt die Ressourceninstanz zurück.

## <a name="catlbasemodulem_binitfailed"></a><a name="m_binitfailed"></a>CAtlBaseModule::m_bInitFailed

Eine Variable, die angibt, ob die Modulinitialisierung fehlgeschlagen ist.

```
static bool m_bInitFailed;
```

### <a name="remarks"></a>Bemerkungen

True, wenn das Modul initialisiert wurde, false, wenn es nicht initialisiert werden konnte.

## <a name="catlbasemoduleremoveresourceinstance"></a><a name="removeresourceinstance"></a>CAtlBaseModule::RemoveResourceInstance

Entfernt eine Ressourceninstanz aus der Liste der gespeicherten Handles.

```
bool RemoveResourceInstance(HINSTANCE hInst) throw();
```

### <a name="parameters"></a>Parameter

*hInst*<br/>
Die zu entfernende Ressourceninstanz.

### <a name="return-value"></a>Rückgabewert

Gibt true zurück, wenn die Ressource erfolgreich entfernt wurde, andernfalls false.

## <a name="catlbasemodulesetresourceinstance"></a><a name="setresourceinstance"></a>CAtlBaseModule::SetResourceInstance

Legt die Ressourceninstanz `CAtlBaseModule` eines Objekts fest.

```
HINSTANCE SetResourceInstance(HINSTANCE hInst) throw();
```

### <a name="parameters"></a>Parameter

*hInst*<br/>
Die neue Ressourceninstanz.

### <a name="return-value"></a>Rückgabewert

Gibt die aktualisierte Ressourceninstanz zurück.

## <a name="see-also"></a>Siehe auch

[Klassenübersicht](../../atl/atl-class-overview.md)<br/>
[Modulklassen](../../atl/atl-module-classes.md)
