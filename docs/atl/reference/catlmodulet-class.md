---
title: CAtlModuleT-Klasse
ms.date: 11/04/2016
f1_keywords:
- CAtlModuleT
- ATLBASE/ATL::CAtlModuleT
- ATLBASE/ATL::CAtlModuleT::CAtlModuleT
- ATLBASE/ATL::CAtlModuleT::InitLibId
- ATLBASE/ATL::CAtlModuleT::RegisterAppId
- ATLBASE/ATL::CAtlModuleT::RegisterServer
- ATLBASE/ATL::CAtlModuleT::UnregisterAppId
- ATLBASE/ATL::CAtlModuleT::UnregisterServer
- ATLBASE/ATL::CAtlModuleT::UpdateRegistryAppId
helpviewer_keywords:
- CAtlModuleT class
ms.assetid: 9b74d02f-9117-47b1-a05e-c5945f83dd2b
ms.openlocfilehash: bf64c073249b7426fafb430a708573d9d06d11fd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321413"
---
# <a name="catlmodulet-class"></a>CAtlModuleT-Klasse

Diese Klasse implementiert ein ATL-Modul.

## <a name="syntax"></a>Syntax

```
template <class T>
class ATL_NO_VTABLE CAtlModuleT : public CAtlModule
```

#### <a name="parameters"></a>Parameter

*T*<br/>
Ihre Klasse `CAtlModuleT`abgeleitet von .

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAtlModuleT::CAtlModuleT](#catlmodulet)|Der Konstruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAtlModuleT::InitLibId](#initlibid)|Initialisiert das Datenelement, das die GUID des aktuellen Moduls enthält.|
|[CAtlModuleT::RegisterAppId](#registerappid)|Fügt die EXE zur Registrierung hinzu.|
|[CAtlModuleT::RegisterServer](#registerserver)|Fügt den Dienst zur Registrierung hinzu.|
|[CAtlModuleT::UnregisterAppId](#unregisterappid)|Entfernt die EXE aus der Registrierung.|
|[CAtlModuleT::UnregisterServer](#unregisterserver)|Entfernt den Dienst aus der Registrierung.|
|[CAtlModuleT::UpdateRegistryAppId](#updateregistryappid)|Aktualisiert die EXE-Informationen in der Registrierung.|

## <a name="remarks"></a>Bemerkungen

`CAtlModuleT`, abgeleitet von [CAtlModule](../../atl/reference/catlmodule-class.md), implementiert ein ausführbares (EXE) oder ein Service (EXE) ATL-Modul. Ein ausführbares Modul ist ein lokaler Server a-process, während ein Dienstmodul eine Windows-Anwendung ist, die beim Starten von Windows im Hintergrund ausgeführt wird.

`CAtlModuleT`bietet Unterstützung beim Initialisieren, Registrieren und Aufheben der Registrierung des Moduls.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[CAtlModule](../../atl/reference/catlmodule-class.md)

`CAtlModuleT`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlbase.h

## <a name="catlmoduletcatlmodulet"></a><a name="catlmodulet"></a>CAtlModuleT::CAtlModuleT

Der Konstruktor.

```
CAtlModuleT() throw();
```

### <a name="remarks"></a>Bemerkungen

Ruft [CAtlModuleT::InitLibId](#initlibid)auf.

## <a name="catlmoduletinitlibid"></a><a name="initlibid"></a>CAtlModuleT::InitLibId

Initialisiert das Datenelement, das die GUID des aktuellen Moduls enthält.

```
static void InitLibId() throw();
```

### <a name="remarks"></a>Bemerkungen

Wird vom Konstruktor [CAtlModuleT::CAtlModuleT](#catlmodulet)aufgerufen.

## <a name="catlmoduletregisterappid"></a><a name="registerappid"></a>CAtlModuleT::RegisterAppId

Fügt die EXE zur Registrierung hinzu.

```
HRESULT RegisterAppId() throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

## <a name="catlmoduletregisterserver"></a><a name="registerserver"></a>CAtlModuleT::RegisterServer

Fügt den Dienst zur Registrierung hinzu.

```
HRESULT RegisterServer(
    BOOL bRegTypeLib = FALSE,
    const CLSID* pCLSID = NULL) throw();
```

### <a name="parameters"></a>Parameter

*bRegTypeLib*<br/>
TRUE, wenn die Typbibliothek registriert werden soll. Der Standardwert ist FALSE.

*pCLSID*<br/>
Zeigt auf die CLSID des zu registrierenden Objekts. Wenn NULL (der Standardwert), werden alle Objekte in der Objektzuordnung registriert.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

## <a name="catlmoduletunregisterappid"></a><a name="unregisterappid"></a>CAtlModuleT::UnregisterAppId

Entfernt die EXE aus der Registrierung.

```
HRESULT UnregisterAppId() throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

## <a name="catlmoduletunregisterserver"></a><a name="unregisterserver"></a>CAtlModuleT::UnregisterServer

Entfernt den Dienst aus der Registrierung.

```
HRESULT UnregisterServer(
    BOOL bUnRegTypeLib,
    const CLSID* pCLSID = NULL) throw();
```

### <a name="parameters"></a>Parameter

*bUnRegTypeLib*<br/>
TRUE, wenn die Typbibliothek ebenfalls nicht registriert werden soll.

*pCLSID*<br/>
Zeigt auf die CLSID des objekts, das nicht registriert werden soll. Wenn NULL (der Standardwert), werden alle Objekte in der Objektzuordnung nicht registriert.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

## <a name="catlmoduletupdateregistryappid"></a><a name="updateregistryappid"></a>CAtlModuleT::UpdateRegistryAppId

Aktualisiert die EXE-Informationen in der Registrierung.

```
static HRESULT WINAPI UpdateRegistryAppId(BOOL /* bRegister*/) throw();
```

### <a name="parameters"></a>Parameter

*bRegister*<br/>
Reserviert.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

## <a name="see-also"></a>Siehe auch

[CAtlModule-Klasse](../../atl/reference/catlmodule-class.md)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)<br/>
[Modulklassen](../../atl/atl-module-classes.md)
