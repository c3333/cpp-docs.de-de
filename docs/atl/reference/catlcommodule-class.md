---
title: CAtlComModule-Klasse
ms.date: 11/04/2016
f1_keywords:
- CAtlComModule
- ATLBASE/ATL::CAtlComModule
- ATLBASE/ATL::CAtlComModule::CAtlComModule
- ATLBASE/ATL::CAtlComModule::RegisterServer
- ATLBASE/ATL::CAtlComModule::RegisterTypeLib
- ATLBASE/ATL::CAtlComModule::UnregisterServer
- ATLBASE/ATL::CAtlComModule::UnRegisterTypeLib
helpviewer_keywords:
- CAtlComModule class
ms.assetid: af5dd71a-a0d1-4a2e-9a24-154a03381c75
ms.openlocfilehash: 68fdb48edc9304d9d74df6f36bd208cfd35ff307
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321484"
---
# <a name="catlcommodule-class"></a>CAtlComModule-Klasse

Diese Klasse implementiert ein COM-Servermodul.

## <a name="syntax"></a>Syntax

```
class CAtlComModule : public _ATL_COM_MODULE
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAtlComModule::CAtlComModule](#catlcommodule)|Der Konstruktor.|
|[CAtlComModule::-CAtlComModule](#dtor)|Der Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAtlComModule::RegisterServer](#registerserver)|Rufen Sie diese Methode auf, um die Systemregistrierung für jedes Objekt in der Objektzuordnung zu aktualisieren.|
|[CAtlComModule::RegisterTypeLib](#registertypelib)|Rufen Sie diese Methode auf, um eine Typbibliothek zu registrieren.|
|[CAtlComModule::UnregisterServer](#unregisterserver)|Rufen Sie diese Methode auf, um die Registrierung jedes Objekts in der Objektzuordnung aufzuheben.|
|[CAtlComModule::UnRegisterTypeLib](#unregistertypelib)|Rufen Sie diese Methode auf, um die Registrierung einer Typbibliothek aufzuheben.|

## <a name="remarks"></a>Bemerkungen

`CAtlComModule`implementiert ein COM-Servermodul, sodass ein Client auf die Komponenten des Moduls zugreifen kann.

Diese Klasse ersetzt die veraltete [CComModule-Klasse,](../../atl/reference/ccommodule-class.md) die in früheren Versionen von ATL verwendet wurde. Weitere Informationen finden Sie unter [ATL-Modulklassen.](../../atl/atl-module-classes.md)

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[_ATL_COM_MODULE](atl-typedefs.md#_atl_com_module)

`CAtlComModule`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlbase.h

## <a name="catlcommodulecatlcommodule"></a><a name="catlcommodule"></a>CAtlComModule::CAtlComModule

Der Konstruktor.

```
CAtlComModule() throw();
```

### <a name="remarks"></a>Bemerkungen

Initialisiert das Modul.

## <a name="catlcommodulecatlcommodule"></a><a name="dtor"></a>CAtlComModule::-CAtlComModule

Der Destruktor.

```
~CAtlComModule();
```

### <a name="remarks"></a>Bemerkungen

Befreit alle Klassenfabriken.

## <a name="catlcommoduleregisterserver"></a><a name="registerserver"></a>CAtlComModule::RegisterServer

Rufen Sie diese Methode auf, um die Systemregistrierung für jedes Objekt in der Objektzuordnung zu aktualisieren.

```
HRESULT RegisterServer(BOOL bRegTypeLib = FALSE, const CLSID* pCLSID = NULL);
```

### <a name="parameters"></a>Parameter

*bRegTypeLib*<br/>
TRUE, wenn die Typbibliothek registriert werden soll. Der Standardwert ist FALSE.

*pCLSID*<br/>
Zeigt auf die CLSID des zu registrierenden Objekts. Wenn NULL (der Standardwert), werden alle Objekte in der Objektzuordnung registriert.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

### <a name="remarks"></a>Bemerkungen

Ruft die globale Funktion [AtlComModuleRegisterServer](server-registration-global-functions.md#atlcommoduleregisterserver)auf.

## <a name="catlcommoduleregistertypelib"></a><a name="registertypelib"></a>CAtlComModule::RegisterTypeLib

Rufen Sie diese Methode auf, um eine Typbibliothek zu registrieren.

```
HRESULT RegisterTypeLib(LPCTSTR lpszIndex);
HRESULT RegisterTypeLib();
```

### <a name="parameters"></a>Parameter

*lpszIndex*<br/>
Zeichenfolge im Format\\"N", wobei N der Ganzzahlindex der TYPELIB-Ressource ist.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

### <a name="remarks"></a>Bemerkungen

Fügt der Systemregistrierung Informationen zu einer Typbibliothek hinzu. Wenn die Modulinstanz mehrere Typbibliotheken enthält, verwenden Sie die erste Version dieser Methode, um anzugeben, welche Typbibliothek verwendet werden soll.

## <a name="catlcommoduleunregisterserver"></a><a name="unregisterserver"></a>CAtlComModule::UnregisterServer

Rufen Sie diese Methode auf, um die Registrierung jedes Objekts in der Objektzuordnung aufzuheben.

```
HRESULT UnregisterServer(
    BOOL bRegTypeLib = FALSE,
    const CLSID* pCLSID = NULL);
```

### <a name="parameters"></a>Parameter

*bRegTypeLib*<br/>
TRUE, wenn die Typbibliothek nicht registriert werden soll. Der Standardwert ist FALSE.

*pCLSID*<br/>
Zeigt auf die CLSID des objekts, das nicht registriert werden soll. Wenn NULL (der Standardwert), werden alle Objekte in der Objektzuordnung nicht registriert.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

### <a name="remarks"></a>Bemerkungen

Ruft die globale Funktion [AtlComModuleUnregisterServer](server-registration-global-functions.md#atlcommoduleunregisterserver)auf.

## <a name="catlcommoduleunregistertypelib"></a><a name="unregistertypelib"></a>CAtlComModule::UnRegisterTypeLib

Rufen Sie diese Methode auf, um die Registrierung einer Typbibliothek aufzuheben.

```
HRESULT UnRegisterTypeLib(LPCTSTR lpszIndex);
HRESULT UnRegisterTypeLib();
```

### <a name="parameters"></a>Parameter

*lpszIndex*<br/>
Zeichenfolge im Format\\"N", wobei N der Ganzzahlindex der TYPELIB-Ressource ist.

### <a name="remarks"></a>Bemerkungen

Entfernt Informationen zu einer Typbibliothek aus der Systemregistrierung. Wenn die Modulinstanz mehrere Typbibliotheken enthält, verwenden Sie die erste Version dieser Methode, um anzugeben, welche Typbibliothek verwendet werden soll.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

## <a name="see-also"></a>Siehe auch

[_ATL_COM_MODULE](atl-typedefs.md#_atl_com_module)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)
