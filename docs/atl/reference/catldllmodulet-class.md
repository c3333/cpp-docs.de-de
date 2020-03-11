---
title: Klasse von "-Klasse"
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
ms.openlocfilehash: be42915c6c2e941bc5fc1de78c5c7ac26ccca6e2
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78863182"
---
# <a name="catldllmodulet-class"></a>Klasse von "-Klasse"

Diese Klasse stellt das Modul für eine DLL dar.

## <a name="syntax"></a>Syntax

```
template <class T>
class ATL_NO_VTABLE CAtlDllModuleT : public CAtlModuleT<T>
```

#### <a name="parameters"></a>Parameter

*T*<br/>
Die von `CAtlDllModuleT`abgeleitete Klasse.

## <a name="members"></a>Members

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|["", "":](#catldllmodulet)|Der Konstruktor.|
|["", "", "".](#dtor)|Der Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ':D](#dllcanunloadnow)|Testet, ob die DLL entladen werden kann.|
|["Cmdlet"::D llgetclassobject](#dllgetclassobject)|Gibt eine Klassenfactory zurück.|
|[""::D llmain](#dllmain)|Der optionale Einstiegspunkt in eine Dynamic Link Library (dll).|
|[CAtlDllModuleT::D llregisterserver](#dllregisterserver)|Fügt der Systemregistrierung Einträge für Objekte in der dll hinzu.|
|[CAtlDllModuleT::D llunregisterserver](#dllunregisterserver)|Entfernt Einträge in der Systemregistrierung für Objekte in der dll.|
|["Cmdlet: GetClassObject"](#getclassobject)|Gibt eine Klassenfactory zurück. Wird von [DllGetClassObject](#dllgetclassobject)aufgerufen.|

## <a name="remarks"></a>Bemerkungen

`CAtlDllModuleT` das Modul für eine Dynamic Link Library (dll) darstellt und Funktionen bereitstellt, die von allen DLL-Projekten verwendet werden. Diese [Spezialisierung der Klasse](../../atl/reference/catlmodulet-class.md) "" von "Klasse" umfasst Unterstützung für die Registrierung.

Weitere Informationen zu Modulen in ATL finden Sie unter [ATL-Modul Klassen](../../atl/atl-module-classes.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[_ATL_MODULE](atl-typedefs.md#_atl_module)

["-Module"](../../atl/reference/catlmodule-class.md)

["-Modulet"](../../atl/reference/catlmodulet-class.md)

`CAtlDllModuleT`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atlbase. h

##  <a name="catldllmodulet"></a>"", "":

Der Konstruktor.

```
CAtlDllModuleT() throw();
```

##  <a name="dtor"></a>"", "", "".

Der Destruktor.

```
~CAtlDllModuleT() throw();
```

##  <a name="dllcanunloadnow"></a>' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ':D

Testet, ob die DLL entladen werden kann.

```
HRESULT DllCanUnloadNow() throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt S_OK zurück, wenn die DLL entladen werden kann, oder S_FALSE, wenn dies nicht möglich ist.

##  <a name="dllgetclassobject"></a>"Cmdlet"::D llgetclassobject

Gibt die Klassenfactory zurück.

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

*PPV*<br/>
Ein Zeiger auf den Schnittstellen Zeiger, der durch *riid*identifiziert wird. Wenn das Objekt diese Schnittstelle nicht unterstützt, wird *PPV* auf NULL festgelegt.

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg S_OK oder bei einem Fehler HRESULT zurück.

##  <a name="dllmain"></a>""::D llmain

Der optionale Einstiegspunkt in eine Dynamic Link Library (dll).

```
BOOL WINAPI DllMain(DWORD dwReason, LPVOID /* lpReserved*/) throw();
```

### <a name="parameters"></a>Parameter

*dwReason*<br/>
Wenn DLL_PROCESS_ATTACH festgelegt ist, sind die Aufrufe DLL_THREAD_ATTACH und DLL_THREAD_DETACH Benachrichtigungen deaktiviert.

*lpReserved*<br/>
Reserviert.

### <a name="return-value"></a>Rückgabewert

Gibt immer true zurück.

### <a name="remarks"></a>Bemerkungen

Das Deaktivieren des DLL_THREAD_ATTACH-und DLL_THREAD_DETACH Benachrichtigungs Aufrufs kann eine sinnvolle Optimierung für Multithreadanwendungen mit vielen DLLs sein, die häufig Threads erstellen und löschen und deren DLLs diese Benachrichtigungen auf der Basis von Anlage/Trennung auf Thread Ebene nicht benötigen.

##  <a name="dllregisterserver"></a>CAtlDllModuleT::D llregisterserver

Fügt der Systemregistrierung Einträge für Objekte in der dll hinzu.

```
HRESULT DllRegisterServer(BOOL bRegTypeLib = TRUE) throw();
```

### <a name="parameters"></a>Parameter

*bregtypelib*<br/>
TRUE, wenn die Typbibliothek registriert werden soll. Der Standardwert ist TRUE.

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg S_OK oder bei einem Fehler HRESULT zurück.

##  <a name="dllunregisterserver"></a>CAtlDllModuleT::D llunregisterserver

Entfernt Einträge in der Systemregistrierung für Objekte in der dll.

```
HRESULT DllUnregisterServer(BOOL bUnRegTypeLib = TRUE) throw();
```

### <a name="parameters"></a>Parameter

*bunregtypelib*<br/>
TRUE, wenn die Typbibliothek aus der Registrierung entfernt werden soll. Der Standardwert ist TRUE.

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg S_OK oder bei einem Fehler HRESULT zurück.

##  <a name="getclassobject"></a>"Cmdlet: GetClassObject"

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

*PPV*<br/>
Ein Zeiger auf den Schnittstellen Zeiger, der durch *riid*identifiziert wird. Wenn das Objekt diese Schnittstelle nicht unterstützt, wird *PPV* auf NULL festgelegt.

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg S_OK oder bei einem Fehler HRESULT zurück.

### <a name="remarks"></a>Bemerkungen

Diese Methode wird von " [Cmdlet::D llgetclassobject](#dllgetclassobject) " aufgerufen und ist aus Gründen der Abwärtskompatibilität eingeschlossen.

## <a name="see-also"></a>Weitere Informationen

[CAtlModuleT-Klasse](../../atl/reference/catlmodulet-class.md)<br/>
[CAtlExeModuleT-Klasse](../../atl/reference/catlexemodulet-class.md)<br/>
[Klassen Übersicht](../../atl/atl-class-overview.md)<br/>
[Modul Klassen](../../atl/atl-module-classes.md)
