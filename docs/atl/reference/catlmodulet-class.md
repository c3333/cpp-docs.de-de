---
title: Klasse von "Klasse"
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
ms.openlocfilehash: b07e60265570e66337a2d13007e9ad57c6f369e4
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "82167863"
---
# <a name="catlmodulet-class"></a>Klasse von "Klasse"

Diese Klasse implementiert ein ATL-Modul.

## <a name="syntax"></a>Syntax

```cpp
template <class T>
class ATL_NO_VTABLE CAtlModuleT : public CAtlModule
```

### <a name="parameters"></a>Parameter

*T*<br/>
Die von `CAtlModuleT`abgeleitete Klasse.

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|["-Module":](#catlmodulet)|Der Konstruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|["-Module": initlibid](#initlibid)|Initialisiert den Datenmember, der die GUID des aktuellen Moduls enthält.|
|["Sinlmodulet:: registerappid"](#registerappid)|Fügt die exe der Registrierung hinzu.|
|[Catlmodulet:: Register Server](#registerserver)|Fügt den Dienst der Registrierung hinzu.|
|["Sinlmodulet:: unregisterappid"](#unregisterappid)|Entfernt die exe-aus der Registrierung.|
|[Catlmodulet:: unregisterserver](#unregisterserver)|Entfernt den Dienst aus der Registrierung.|
|["Update Module:: updateregistryappid"](#updateregistryappid)|Aktualisiert die exe-Informationen in der Registrierung.|

## <a name="remarks"></a>Bemerkungen

`CAtlModuleT`, abgeleitet von "| [Module](../../atl/reference/catlmodule-class.md)", implementiert ein ausführbares ATL-Modul (exe) oder eines Dienstanbieter (exe). Ein ausführbares Modul ist ein lokaler, Prozess interner Server, während ein Dienst Modul eine Windows-Anwendung ist, die beim Start von Windows im Hintergrund ausgeführt wird.

`CAtlModuleT`bietet Unterstützung für das Initialisieren, registrieren und Aufheben der Registrierung des Moduls.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[_ATL_MODULE](atl-typedefs.md#_atl_module)

["-Module"](../../atl/reference/catlmodule-class.md)

`CAtlModuleT`

## <a name="requirements"></a>Anforderungen

**Header:** atlbase. h

## <a name="catlmoduletcatlmodulet"></a><a name="catlmodulet"></a>"-Module":

Der Konstruktor.

```cpp
CAtlModuleT() throw();
```

### <a name="remarks"></a>Bemerkungen

Ruft ["](#initlibid)" "" auf.

## <a name="catlmoduletinitlibid"></a><a name="initlibid"></a>"-Module": initlibid

Initialisiert den Datenmember, der die GUID des aktuellen Moduls enthält.

```cpp
static void InitLibId() throw();
```

### <a name="remarks"></a>Bemerkungen

Wird vom Konstruktor "-Erteilungs- [modulet::](#catlmodulet)" aufgerufen.

## <a name="catlmoduletregisterappid"></a><a name="registerappid"></a>"Sinlmodulet:: registerappid"

Fügt die exe der Registrierung hinzu.

```cpp
HRESULT RegisterAppId() throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg S_OK oder bei einem Fehler HRESULT zurück.

## <a name="catlmoduletregisterserver"></a><a name="registerserver"></a>Catlmodulet:: Register Server

Fügt den Dienst der Registrierung hinzu.

```cpp
HRESULT RegisterServer(
    BOOL bRegTypeLib = FALSE,
    const CLSID* pCLSID = NULL) throw();
```

### <a name="parameters"></a>Parameter

*bregtypelib*<br/>
TRUE, wenn die Typbibliothek registriert werden soll. Der Standardwert ist FALSE.

*pclsid*<br/>
Verweist auf die CLSID des zu registrierenden Objekts. Wenn der Wert NULL (der Standardwert) ist, werden alle Objekte in der Objekt Zuordnung registriert.

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg S_OK oder bei einem Fehler HRESULT zurück.

## <a name="catlmoduletunregisterappid"></a><a name="unregisterappid"></a>"Sinlmodulet:: unregisterappid"

Entfernt die exe-aus der Registrierung.

```cpp
HRESULT UnregisterAppId() throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg S_OK oder bei einem Fehler HRESULT zurück.

## <a name="catlmoduletunregisterserver"></a><a name="unregisterserver"></a>Catlmodulet:: unregisterserver

Entfernt den Dienst aus der Registrierung.

```cpp
HRESULT UnregisterServer(
    BOOL bUnRegTypeLib,
    const CLSID* pCLSID = NULL) throw();
```

### <a name="parameters"></a>Parameter

*bunregtypelib*<br/>
TRUE, wenn die Registrierung der Typbibliothek ebenfalls aufgehoben werden soll.

*pclsid*<br/>
Verweist auf die CLSID des Objekts, dessen Registrierung aufgehoben werden soll. Wenn der Wert NULL (der Standardwert) ist, wird die Registrierung aller Objekte in der Objekt Zuordnung aufgehoben.

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg S_OK oder bei einem Fehler HRESULT zurück.

## <a name="catlmoduletupdateregistryappid"></a><a name="updateregistryappid"></a>"Update Module:: updateregistryappid"

Aktualisiert die exe-Informationen in der Registrierung.

```cpp
static HRESULT WINAPI UpdateRegistryAppId(BOOL /* bRegister*/) throw();
```

### <a name="parameters"></a>Parameter

*bregister*<br/>
Reserviert.

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg S_OK oder bei einem Fehler HRESULT zurück.

## <a name="see-also"></a>Weitere Informationen:

[Klasse von "Klasse"](../../atl/reference/catlmodule-class.md)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)<br/>
[Modul Klassen](../../atl/atl-module-classes.md)
