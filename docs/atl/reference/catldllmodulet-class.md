---
title: CAtlDllModuleT-Klasse
ms.date: 11/04/2016
f1_keywords:
- CAtlDllModuleT
- ATLBASE/ATL::CAtlDllModuleT
- ATLBASE/ATL::CAtlDllModuleT::CAtlDllModuleT
- ATLBASE/ATL::CAtlDllModuleT::DllCanUnloadNow
- ATLBASE/ATL::CAtlDllModuleT::DllGetClassObject
- ATLBASE/ATL::CAtlDllModuleT::DllMain
- ATLBASE/ATL::CAtlDllModuleT::DllRegisterServer
- ATLBASE/ATL::CAtlDllModuleT::DllUnregisterServer
- ATLBASE/ATL::CAtlDllModuleT::GetClassObject
helpviewer_keywords:
- CAtlDllModuleT class
ms.assetid: 351d5767-8257-4878-94be-45a85e31a72d
ms.openlocfilehash: 7a5f8e7e489c8e0d573569ac7c4a8fb63f652732
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319014"
---
# <a name="catldllmodulet-class"></a>CAtlDllModuleT-Klasse

Diese Klasse stellt das Modul für eine DLL dar.

## <a name="syntax"></a>Syntax

```
template <class T>
class ATL_NO_VTABLE CAtlDllModuleT : public CAtlModuleT<T>
```

#### <a name="parameters"></a>Parameter

*T*<br/>
Ihre Klasse `CAtlDllModuleT`abgeleitet von .

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAtlDllModuleT::CAtlDllModuleT](#catldllmodulet)|Der Konstruktor.|
|[CAtlDllModuleT::-CAtlDllModuleT](#dtor)|Der Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAtlDllModuleT::DllCanUnloadNow](#dllcanunloadnow)|Testet, ob die DLL entladen werden kann.|
|[CAtlDllModuleT::DllGetClassObject](#dllgetclassobject)|Gibt eine Klassenfabrik zurück.|
|[CAtlDllModuleT::DllMain](#dllmain)|Der optionale Einstiegspunkt in eine Dynamic-Link-Bibliothek (DLL).|
|[CAtlDllModuleT::DllRegisterServer](#dllregisterserver)|Fügt der Systemregistrierung Einträge für Objekte in der DLL hinzu.|
|[CAtlDllModuleT::DllUnregisterServer](#dllunregisterserver)|Entfernt Einträge in der Systemregistrierung für Objekte in der DLL.|
|[CAtlDllModuleT::GetClassObject](#getclassobject)|Gibt eine Klassenfabrik zurück. Aufruf von [DllGetClassObject](#dllgetclassobject).|

## <a name="remarks"></a>Bemerkungen

`CAtlDllModuleT`stellt das Modul für eine Dynamic-Link-Bibliothek (DLL) dar und stellt Funktionen bereit, die von allen DLL-Projekten verwendet werden. Diese Spezialisierung der [CAtlModuleT-Klasse](../../atl/reference/catlmodulet-class.md) umfasst unterstützungserhaltende Registrierung.

Weitere Informationen zu Modulen in ATL finden Sie unter [ATL-Modulklassen](../../atl/atl-module-classes.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[CAtlModule](../../atl/reference/catlmodule-class.md)

[CAtlModuleT](../../atl/reference/catlmodulet-class.md)

`CAtlDllModuleT`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlbase.h

## <a name="catldllmoduletcatldllmodulet"></a><a name="catldllmodulet"></a>CAtlDllModuleT::CAtlDllModuleT

Der Konstruktor.

```
CAtlDllModuleT() throw();
```

## <a name="catldllmoduletcatldllmodulet"></a><a name="dtor"></a>CAtlDllModuleT::-CAtlDllModuleT

Der Destruktor.

```
~CAtlDllModuleT() throw();
```

## <a name="catldllmoduletdllcanunloadnow"></a><a name="dllcanunloadnow"></a>CAtlDllModuleT::DllCanUnloadNow

Testet, ob die DLL entladen werden kann.

```
HRESULT DllCanUnloadNow() throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt S_OK zurück, wenn die DLL entladen werden kann, oder S_FALSE wenn dies nicht möglich ist.

## <a name="catldllmoduletdllgetclassobject"></a><a name="dllgetclassobject"></a>CAtlDllModuleT::DllGetClassObject

Gibt die Klassenfabrik zurück.

```
HRESULT DllGetClassObject(
    REFCLSID rclsid,
    REFIID riid,
    LPVOID* ppv) throw();
```

### <a name="parameters"></a>Parameter

*rclsid*<br/>
Die CLSID des zu erstellenden Objekts.

*riid*<br/>
Die IID der angeforderten Schnittstelle.

*Ppv*<br/>
Ein Zeiger auf den Schnittstellenzeiger, der von *riid*identifiziert wird. Wenn das Objekt diese Schnittstelle nicht unterstützt, wird *ppv* auf NULL gesetzt.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

## <a name="catldllmoduletdllmain"></a><a name="dllmain"></a>CAtlDllModuleT::DllMain

Der optionale Einstiegspunkt in eine Dynamic-Link-Bibliothek (DLL).

```
BOOL WINAPI DllMain(DWORD dwReason, LPVOID /* lpReserved*/) throw();
```

### <a name="parameters"></a>Parameter

*dwReason*<br/>
Wenn auf DLL_PROCESS_ATTACH festgelegt, werden die DLL_THREAD_ATTACH- und DLL_THREAD_DETACH Benachrichtigungsaufrufe deaktiviert.

*lpReserviert*<br/>
Reserviert.

### <a name="return-value"></a>Rückgabewert

Gibt immer TRUE zurück.

### <a name="remarks"></a>Bemerkungen

Das Deaktivieren der DLL_THREAD_ATTACH- und DLL_THREAD_DETACH-Benachrichtigungsaufrufe kann eine nützliche Optimierung für Multithreadanwendungen mit vielen DLLs sein, die häufig Threads erstellen und löschen und deren DLLs diese Benachrichtigungen auf Threadebene der Anlage/Ablösung nicht benötigen.

## <a name="catldllmoduletdllregisterserver"></a><a name="dllregisterserver"></a>CAtlDllModuleT::DllRegisterServer

Fügt der Systemregistrierung Einträge für Objekte in der DLL hinzu.

```
HRESULT DllRegisterServer(BOOL bRegTypeLib = TRUE) throw();
```

### <a name="parameters"></a>Parameter

*bRegTypeLib*<br/>
TRUE, wenn die Typbibliothek registriert werden soll. Der Standardwert ist TRUE.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

## <a name="catldllmoduletdllunregisterserver"></a><a name="dllunregisterserver"></a>CAtlDllModuleT::DllUnregisterServer

Entfernt Einträge in der Systemregistrierung für Objekte in der DLL.

```
HRESULT DllUnregisterServer(BOOL bUnRegTypeLib = TRUE) throw();
```

### <a name="parameters"></a>Parameter

*bUnRegTypeLib*<br/>
TRUE, wenn die Typbibliothek aus der Registrierung entfernt werden soll. Der Standardwert ist TRUE.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

## <a name="catldllmoduletgetclassobject"></a><a name="getclassobject"></a>CAtlDllModuleT::GetClassObject

Erstellt ein Objekt der angegebenen CLSID.

```
HRESULT GetClassObject(
    REFCLSID rclsid,
    REFIID riid,
    LPVOID* ppv) throw();
```

### <a name="parameters"></a>Parameter

*rclsid*<br/>
Die CLSID des zu erstellenden Objekts.

*riid*<br/>
Die IID der angeforderten Schnittstelle.

*Ppv*<br/>
Ein Zeiger auf den Schnittstellenzeiger, der von *riid*identifiziert wird. Wenn das Objekt diese Schnittstelle nicht unterstützt, wird *ppv* auf NULL gesetzt.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

### <a name="remarks"></a>Bemerkungen

Diese Methode wird von [CAtlDllModuleT::DllGetClassObject](#dllgetclassobject) aufgerufen und ist für die Abwärtskompatibilität enthalten.

## <a name="see-also"></a>Siehe auch

[CAtlModuleT-Klasse](../../atl/reference/catlmodulet-class.md)<br/>
[CAtlExeModuleT-Klasse](../../atl/reference/catlexemodulet-class.md)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)<br/>
[Modulklassen](../../atl/atl-module-classes.md)
