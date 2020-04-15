---
title: Globale Funktionen der Serverregistrierung
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::AtlComModuleRegisterServer
- atlbase/ATL::AtlComModuleUnregisterServer
- atlbase/ATL::AtlComModuleRegisterClassObjects
- atlbase/ATL::AtlComModuleRevokeClassObjects
- atlbase/ATL::AtlComModuleGetClassObject
ms.assetid: c2f0a35d-857c-4538-a44d-c4ea0db63b06
ms.openlocfilehash: fb6353b52f487d0511c54223fe9e31dab88704b2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325930"
---
# <a name="server-registration-global-functions"></a>Globale Funktionen der Serverregistrierung

Diese Funktionen bieten Unterstützung für das Registrieren und Aufheben der Registrierung von Serverobjekten in der Objektzuordnung.

> [!IMPORTANT]
> Die in der folgenden Tabelle aufgeführten Funktionen können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

|||
|-|-|
|[AtlComModuleRegisterServer](#atlcommoduleregisterserver)|Diese Funktion wird aufgerufen, um alle Objekte in der Objektzuordnung zu registrieren.|
|[AtlComModuleUnregisterServer](#atlcommoduleunregisterserver)|Diese Funktion wird aufgerufen, um die Registrierung aller Objekte in der Objektzuordnung aufzuheben.|
|[AtlComModuleRegisterClassObjects](#atlcommoduleregisterclassobjects)|Diese Funktion wird aufgerufen, um Klassenobjekte zu registrieren.|
|[AtlComModuleRevokeClassObjects](#atlcommodulerevokeclassobjects)|Diese Funktion wird aufgerufen, um Klassenobjekte von einem COM-Modul zu widerrufen.|
|[AtlComModuleGetClassObject](#atlcommodulegetclassobject)|Diese Funktion wird aufgerufen, um das Klassenobjekt abzubekommen.|

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlbase.h

## <a name="atlcommoduleregisterserver"></a><a name="atlcommoduleregisterserver"></a>AtlComModuleRegisterServer

Diese Funktion wird aufgerufen, um alle Objekte in der Objektzuordnung zu registrieren.

```
ATLINLINE ATLAPI AtlComModuleRegisterServer(
    _ATL_COM_MODULE* pComModule,
    BOOL bRegTypeLib,
    const CLSID* pCLSID);
```

### <a name="parameters"></a>Parameter

*pComModule*<br/>
Zeiger auf das COM-Modul.

*bRegTypeLib*<br/>
TRUE, wenn die Typbibliothek registriert werden soll.

*pCLSID*<br/>
Zeigt auf die CLSID des zu registrierenden Objekts. Wenn NULL, werden alle Objekte in der Objektzuordnung registriert.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

### <a name="remarks"></a>Bemerkungen

`AtlComModuleRegisterServer`führt die automatisch generierte ATL-Objektzuordnung und registriert jedes Objekt in der Karte. Wenn *pCLSID* nicht NULL ist, wird nur das Objekt registriert, auf das von *pCLSID* verwiesen wird. Andernfalls werden alle Objekte registriert.

Diese Funktion wird von [CAtlComModule::RegisterServer](catlcommodule-class.md#registerserver)aufgerufen.

## <a name="atlcommoduleunregisterserver"></a><a name="atlcommoduleunregisterserver"></a>AtlComModuleUnregisterServer

Diese Funktion wird aufgerufen, um die Registrierung aller Objekte in der Objektzuordnung aufzuheben.

```
ATLINLINE ATLAPI AtlComModuleUnregisterServer(
    _ATL_COM_MODULE* pComModule,
    BOOL bUnRegTypeLib,
    const CLSID* pCLSID);
```

### <a name="parameters"></a>Parameter

*pComModule*<br/>
Zeiger auf das COM-Modul.

*bUnRegTypeLib*<br/>
TRUE, wenn die Typbibliothek registriert werden soll.

*pCLSID*<br/>
Zeigt auf die CLSID des objekts, das nicht registriert werden soll. Wenn NULL alle Objekte in der Objektzuordnung nicht registriert werden.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

### <a name="remarks"></a>Bemerkungen

`AtlComModuleUnregisterServer`führt die ATL-Objektzuordnung und entregistriert jedes Objekt in der Karte. Wenn *pCLSID* nicht NULL ist, wird nur das Objekt, auf das von *pCLSID* verwiesen wird, nicht registriert. Andernfalls werden alle Objekte nicht registriert.

Diese Funktion wird von [CAtlComModule::UnregisterServer](catlcommodule-class.md#unregisterserver)aufgerufen.

## <a name="atlcommoduleregisterclassobjects"></a><a name="atlcommoduleregisterclassobjects"></a>AtlComModuleRegisterClassObjects

Diese Funktion wird aufgerufen, um Klassenobjekte zu registrieren.

```
ATLINLINE ATLAPI AtlComModuleRegisterClassObjects(
    _ATL_COM_MODULE* pComModule,
    DWORD dwClsContext,
    DWORD dwFlags);
```

### <a name="parameters"></a>Parameter

*pComModule*<br/>
Zeiger auf das COM-Modul.

*dwClsContext*<br/>
Gibt den Kontext an, in dem das Klassenobjekt ausgeführt werden soll. Mögliche Werte sind CLSCTX_INPROC_SERVER, CLSCTX_INPROC_HANDLER oder CLSCTX_LOCAL_SERVER. Weitere Informationen finden Sie unter [CLSCTX.](/windows/win32/api/wtypesbase/ne-wtypesbase-clsctx)

*dwFlags*<br/>
Bestimmt die Verbindungstypen zum Klassenobjekt. Mögliche Werte sind REGCLS_SINGLEUSE, REGCLS_MULTIPLEUSE oder REGCLS_MULTI_SEPARATE. Weitere Informationen finden Sie unter [REGCLS.](/windows/win32/api/combaseapi/ne-combaseapi-regcls)

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

### <a name="remarks"></a>Bemerkungen

Diese Hilfsfunktion wird von [CComModule::RegisterClassObjects](ccommodule-class.md#registerclassobjects) (veraltet in ATL 7.0) und [CAtlExeModuleT::RegisterClassObjects](catlexemodulet-class.md#registerclassobjects)verwendet.

## <a name="atlcommodulerevokeclassobjects"></a><a name="atlcommodulerevokeclassobjects"></a>AtlComModuleRevokeClassObjects

Diese Funktion wird aufgerufen, um eine oder mehrere Klassenfactorys aus der ROT (Running Object Table) zu entfernen.

```
ATLINLINE ATLAPI AtlComModuleRevokeClassObjects(_ATL_COM_MODULE* pComModule);
```

### <a name="parameters"></a>Parameter

*pComModule*<br/>
Zeiger auf das COM-Modul.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

### <a name="remarks"></a>Bemerkungen

Diese Hilfsfunktion wird von [CComModule::RevokeClassObjects](ccommodule-class.md#revokeclassobjects) (veraltet in ATL 7.0) und [CAtlExeModuleT::RevokeClassObjects](catlexemodulet-class.md#revokeclassobjects)verwendet.

## <a name="atlcommodulegetclassobject"></a><a name="atlcommodulegetclassobject"></a>AtlComModuleGetClassObject

Diese Funktion wird aufgerufen, um die Klassenfactory zurückzugeben.

```
ATLINLINE ATLAPI AtlComModuleGetClassObject(
    _ATL_COM_MODULE* pComModule,
    REFCLSID rclsid,
    REFIID riid,
    LPVOID* ppv);
```

### <a name="parameters"></a>Parameter

*pComModule*<br/>
Zeiger auf das COM-Modul.

*rclsid*<br/>
Die CLSID des zu erstellenden Objekts.

*riid*<br/>
Die IID der angeforderten Schnittstelle.

*Ppv*<br/>
Ein Zeiger auf den Schnittstellenzeiger, der von *riid*identifiziert wird. Wenn das Objekt diese Schnittstelle nicht unterstützt, wird *ppv* auf NULL gesetzt.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

### <a name="remarks"></a>Bemerkungen

Diese Hilfsfunktion wird von [CComModule::GetClassObject](ccommodule-class.md#getclassobject) (veraltet in ATL 7.0) und [CAtlDllModuleT::GetClassObject](catldllmodulet-class.md#getclassobject)verwendet.

## <a name="see-also"></a>Siehe auch

[Functions](../../atl/reference/atl-functions.md)
