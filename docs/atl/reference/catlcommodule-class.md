---
title: Klasse von "-Klasse"
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
ms.openlocfilehash: 09adcb33ca9e6f8524063130d6aedca044d6ecb5
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2020
ms.locfileid: "79423453"
---
# <a name="catlcommodule-class"></a>Klasse von "-Klasse"

Diese Klasse implementiert ein com-Servermodul.

## <a name="syntax"></a>Syntax

```
class CAtlComModule : public _ATL_COM_MODULE
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|Beschreibung|
|----------|-----------------|
|["" Für ""](#catlcommodule)|Der Konstruktor.|
|["-Com-commodule:: ~"](#dtor)|Der Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|Beschreibung|
|----------|-----------------|
|[Catlcommodule:: RegisterServer](#registerserver)|Diese Methode wird aufgerufen, um die Systemregistrierung für jedes Objekt in der Objekt Zuordnung zu aktualisieren.|
|["" Für ""](#registertypelib)|Mit dieser Methode können Sie eine Typbibliothek registrieren.|
|[Catlcommodule:: unregisterserver](#unregisterserver)|Diese Methode wird aufgerufen, um die Registrierung der einzelnen Objekte in der Objekt Zuordnung aufzuheben.|
|["" Für "".](#unregistertypelib)|Mit dieser Methode können Sie die Registrierung einer Typbibliothek aufheben.|

## <a name="remarks"></a>Hinweise

`CAtlComModule` implementiert ein com-Servermodul, das einem Client den Zugriff auf die Komponenten des Moduls ermöglicht.

Diese Klasse ersetzt die veraltete [CComModule](../../atl/reference/ccommodule-class.md) -Klasse, die in früheren Versionen von ATL verwendet wurde. Weitere Informationen finden Sie unter [ATL-Modul Klassen](../../atl/atl-module-classes.md) .

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[_ATL_COM_MODULE](atl-typedefs.md#_atl_com_module)

`CAtlComModule`

## <a name="requirements"></a>Voraussetzungen

**Header:** atlbase. h

##  <a name="catlcommodule"></a>"" Für ""

Der Konstruktor.

```
CAtlComModule() throw();
```

### <a name="remarks"></a>Hinweise

Initialisiert das Modul.

##  <a name="dtor"></a>"-Com-commodule:: ~"

Der Destruktor.

```
~CAtlComModule();
```

### <a name="remarks"></a>Hinweise

Gibt alle Klassenfactorys frei

##  <a name="registerserver"></a>Catlcommodule:: RegisterServer

Diese Methode wird aufgerufen, um die Systemregistrierung für jedes Objekt in der Objekt Zuordnung zu aktualisieren.

```
HRESULT RegisterServer(BOOL bRegTypeLib = FALSE, const CLSID* pCLSID = NULL);
```

### <a name="parameters"></a>Parameter

*bregtypelib*<br/>
TRUE, wenn die Typbibliothek registriert werden soll. Der Standardwert lautet "FALSE".

*pclsid*<br/>
Verweist auf die CLSID des zu registrierenden Objekts. Wenn der Wert NULL (der Standardwert) ist, werden alle Objekte in der Objekt Zuordnung registriert.

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg S_OK oder bei einem Fehler HRESULT zurück.

### <a name="remarks"></a>Hinweise

Ruft die globale Funktion [atlcommoduleregisterserver](server-registration-global-functions.md#atlcommoduleregisterserver)auf.

##  <a name="registertypelib"></a>"" Für ""

Mit dieser Methode können Sie eine Typbibliothek registrieren.

```
HRESULT RegisterTypeLib(LPCTSTR lpszIndex);
HRESULT RegisterTypeLib();
```

### <a name="parameters"></a>Parameter

*lpszindex*<br/>
Zeichenfolge im Format "\\\n", wobei "N" der ganzzahlige Index der Ressource "TypeLib" ist.

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg S_OK oder bei einem Fehler HRESULT zurück.

### <a name="remarks"></a>Hinweise

Fügt der Systemregistrierung Informationen zu einer Typbibliothek hinzu. Wenn die Modul Instanz mehrere Typbibliotheken enthält, verwenden Sie die erste Version dieser Methode, um anzugeben, welche Typbibliothek verwendet werden soll.

##  <a name="unregisterserver"></a>Catlcommodule:: unregisterserver

Diese Methode wird aufgerufen, um die Registrierung der einzelnen Objekte in der Objekt Zuordnung aufzuheben.

```
HRESULT UnregisterServer(
    BOOL bRegTypeLib = FALSE,
    const CLSID* pCLSID = NULL);
```

### <a name="parameters"></a>Parameter

*bregtypelib*<br/>
TRUE, wenn die Registrierung der Typbibliothek aufgehoben werden soll. Der Standardwert lautet "FALSE".

*pclsid*<br/>
Verweist auf die CLSID des Objekts, dessen Registrierung aufgehoben werden soll. Wenn der Wert NULL (der Standardwert) ist, wird die Registrierung aller Objekte in der Objekt Zuordnung aufgehoben.

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg S_OK oder bei einem Fehler HRESULT zurück.

### <a name="remarks"></a>Hinweise

Ruft die globale Funktion [atlcommoduleunregisterserver](server-registration-global-functions.md#atlcommoduleunregisterserver)auf.

##  <a name="unregistertypelib"></a>"" Für "".

Mit dieser Methode können Sie die Registrierung einer Typbibliothek aufheben.

```
HRESULT UnRegisterTypeLib(LPCTSTR lpszIndex);
HRESULT UnRegisterTypeLib();
```

### <a name="parameters"></a>Parameter

*lpszindex*<br/>
Zeichenfolge im Format "\\\n", wobei "N" der ganzzahlige Index der Ressource "TypeLib" ist.

### <a name="remarks"></a>Hinweise

Entfernt Informationen zu einer Typbibliothek aus der Systemregistrierung. Wenn die Modul Instanz mehrere Typbibliotheken enthält, verwenden Sie die erste Version dieser Methode, um anzugeben, welche Typbibliothek verwendet werden soll.

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg S_OK oder bei einem Fehler HRESULT zurück.

## <a name="see-also"></a>Siehe auch

[_ATL_COM_MODULE](atl-typedefs.md#_atl_com_module)<br/>
[Klassen Übersicht](../../atl/atl-class-overview.md)
