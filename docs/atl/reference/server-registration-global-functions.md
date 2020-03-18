---
title: Globale Funktionen der Server Registrierung
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::AtlComModuleRegisterServer
- atlbase/ATL::AtlComModuleUnregisterServer
- atlbase/ATL::AtlComModuleRegisterClassObjects
- atlbase/ATL::AtlComModuleRevokeClassObjects
- atlbase/ATL::AtlComModuleGetClassObject
ms.assetid: c2f0a35d-857c-4538-a44d-c4ea0db63b06
ms.openlocfilehash: f9c3697259e1cee2b1107ded785ca583d730b55e
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2020
ms.locfileid: "79422943"
---
# <a name="server-registration-global-functions"></a>Globale Funktionen der Server Registrierung

Diese Funktionen bieten Unterstützung für das registrieren und Aufheben der Registrierung von Server Objekten in der Objekt Zuordnung.

> [!IMPORTANT]
>  Die in der folgenden Tabelle aufgeführten Funktionen können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

|||
|-|-|
|[Atlcommoduleregisterserver](#atlcommoduleregisterserver)|Diese Funktion wird aufgerufen, um alle Objekte in der Objektzuordnung zu registrieren.|
|[Atlcommoduleunregisterserver](#atlcommoduleunregisterserver)|Diese Funktion wird aufgerufen, um die Registrierung aller Objekte in der Objektzuordnung aufzuheben.|
|[Atlcommoduleregisterclassobjects](#atlcommoduleregisterclassobjects)|Diese Funktion wird aufgerufen, um Klassenobjekte zu registrieren.|
|[Atlcommodulerevokeclassobjects](#atlcommodulerevokeclassobjects)|Diese Funktion wird aufgerufen, um Klassen Objekte von einem com-Modul zu widerrufen.|
|[Atlcommodulegetclassobject](#atlcommodulegetclassobject)|Diese Funktion wird aufgerufen, um das Klassenobjekt zu erhalten.|

## <a name="requirements"></a>Voraussetzungen

**Header:** atlbase. h

##  <a name="atlcommoduleregisterserver"></a>Atlcommoduleregisterserver

Diese Funktion wird aufgerufen, um alle Objekte in der Objektzuordnung zu registrieren.

```
ATLINLINE ATLAPI AtlComModuleRegisterServer(
    _ATL_COM_MODULE* pComModule,
    BOOL bRegTypeLib,
    const CLSID* pCLSID);
```

### <a name="parameters"></a>Parameter

*pcommodule*<br/>
Zeiger auf das com-Modul.

*bregtypelib*<br/>
TRUE, wenn die Typbibliothek registriert werden soll.

*pclsid*<br/>
Verweist auf die CLSID des zu registrierenden Objekts. Wenn der Wert NULL ist, werden alle Objekte in der Objekt Zuordnung registriert.

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg S_OK oder bei einem Fehler HRESULT zurück.

### <a name="remarks"></a>Hinweise

`AtlComModuleRegisterServer` durchläuft die ATL-Objekt Zuordnung, die automatisch generiert wird, und registriert jedes Objekt in der Zuordnung. Wenn *pclsid* nicht NULL ist, wird nur das Objekt, auf das *pclsid* verweist, registriert. Andernfalls werden alle-Objekte registriert.

Diese Funktion wird von [catlcommodule:: RegisterServer](catlcommodule-class.md#registerserver)aufgerufen.

##  <a name="atlcommoduleunregisterserver"></a>Atlcommoduleunregisterserver

Diese Funktion wird aufgerufen, um die Registrierung aller Objekte in der Objektzuordnung aufzuheben.

```
ATLINLINE ATLAPI AtlComModuleUnregisterServer(
    _ATL_COM_MODULE* pComModule,
    BOOL bUnRegTypeLib,
    const CLSID* pCLSID);
```

### <a name="parameters"></a>Parameter

*pcommodule*<br/>
Zeiger auf das com-Modul.

*bunregtypelib*<br/>
TRUE, wenn die Typbibliothek registriert werden soll.

*pclsid*<br/>
Verweist auf die CLSID des Objekts, dessen Registrierung aufgehoben werden soll. Wenn der Wert NULL ist, wird die Registrierung aller Objekte in der Objekt Zuordnung aufgehoben.

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg S_OK oder bei einem Fehler HRESULT zurück.

### <a name="remarks"></a>Hinweise

`AtlComModuleUnregisterServer` durchläuft die ATL-Objekt Zuordnung und hebt die Registrierung der einzelnen Objekte in der Zuordnung auf. Wenn *pclsid* nicht NULL ist, wird nur das Objekt, auf das von *pclsid* verwiesen wird, nicht registriert. Andernfalls wird die Registrierung aller Objekte aufgehoben.

Diese Funktion wird von [catlcommodule:: unregisterserver](catlcommodule-class.md#unregisterserver)aufgerufen.

##  <a name="atlcommoduleregisterclassobjects"></a>Atlcommoduleregisterclassobjects

Diese Funktion wird aufgerufen, um Klassenobjekte zu registrieren.

```
ATLINLINE ATLAPI AtlComModuleRegisterClassObjects(
    _ATL_COM_MODULE* pComModule,
    DWORD dwClsContext,
    DWORD dwFlags);
```

### <a name="parameters"></a>Parameter

*pcommodule*<br/>
Zeiger auf das com-Modul.

*dwClsContext*<br/>
Gibt den Kontext an, in dem das Klassenobjekt ausgeführt werden soll. Mögliche Werte sind CLSCTX_INPROC_SERVER, CLSCTX_INPROC_HANDLER oder CLSCTX_LOCAL_SERVER. Weitere Informationen finden Sie unter [CLSCTX](/windows/win32/api/wtypesbase/ne-wtypesbase-clsctx) .

*dwFlags*<br/>
Bestimmt die Verbindungstypen für das-Klassenobjekt. Mögliche Werte sind REGCLS_SINGLEUSE, REGCLS_MULTIPLEUSE oder REGCLS_MULTI_SEPARATE. Weitere Informationen finden Sie unter [REGCLS](/windows/win32/api/combaseapi/ne-combaseapi-regcls) .

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg S_OK oder bei einem Fehler HRESULT zurück.

### <a name="remarks"></a>Hinweise

Diese Hilfsfunktion wird von [CComModule:: RegisterClassObjects](ccommodule-class.md#registerclassobjects) (veraltet in ATL 7,0) und von "CComModule:: [RegisterClassObjects](catlexemodulet-class.md#registerclassobjects)" verwendet.

##  <a name="atlcommodulerevokeclassobjects"></a>Atlcommodulerevokeclassobjects

Diese Funktion wird aufgerufen, um eine oder mehrere Klassenfactorys aus der ROT (Running Object Table) zu entfernen.

```
ATLINLINE ATLAPI AtlComModuleRevokeClassObjects(_ATL_COM_MODULE* pComModule);
```

### <a name="parameters"></a>Parameter

*pcommodule*<br/>
Zeiger auf das com-Modul.

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg S_OK oder bei einem Fehler HRESULT zurück.

### <a name="remarks"></a>Hinweise

Diese Hilfsfunktion wird von [CComModule:: revokeclassobjects](ccommodule-class.md#revokeclassobjects) (veraltet in ATL 7,0) und von "CComModule:: [revokeclassobjects](catlexemodulet-class.md#revokeclassobjects)" verwendet.

##  <a name="atlcommodulegetclassobject"></a>Atlcommodulegetclassobject

Diese Funktion wird aufgerufen, um die Klassenfactory zurückzugeben.

```
ATLINLINE ATLAPI AtlComModuleGetClassObject(
    _ATL_COM_MODULE* pComModule,
    REFCLSID rclsid,
    REFIID riid,
    LPVOID* ppv);
```

### <a name="parameters"></a>Parameter

*pcommodule*<br/>
Zeiger auf das com-Modul.

*rclsid*<br/>
Die CLSID des zu erstellenden Objekts.

*riid*<br/>
Die IID der angeforderten Schnittstelle.

*PPV*<br/>
Ein Zeiger auf den Schnittstellen Zeiger, der durch *riid*identifiziert wird. Wenn das Objekt diese Schnittstelle nicht unterstützt, wird *PPV* auf NULL festgelegt.

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg S_OK oder bei einem Fehler HRESULT zurück.

### <a name="remarks"></a>Hinweise

Diese Hilfsfunktion wird von [CComModule:: GetClassObject](ccommodule-class.md#getclassobject) (veraltet in ATL 7,0) und von "CComModule:: [GetClassObject](catldllmodulet-class.md#getclassobject)" verwendet.

## <a name="see-also"></a>Siehe auch

[Funktionen](../../atl/reference/atl-functions.md)
