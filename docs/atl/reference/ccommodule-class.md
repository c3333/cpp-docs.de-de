---
title: CComModule-Klasse
ms.date: 08/19/2019
f1_keywords:
- CComModule
- ATLBASE/ATL::CComModule
- ATLBASE/ATL::CComModule::GetClassObject
- ATLBASE/ATL::CComModule::GetModuleInstance
- ATLBASE/ATL::CComModule::GetResourceInstance
- ATLBASE/ATL::CComModule::GetTypeLibInstance
- ATLBASE/ATL::CComModule::Init
- ATLBASE/ATL::CComModule::RegisterClassHelper
- ATLBASE/ATL::CComModule::RegisterClassObjects
- ATLBASE/ATL::CComModule::RegisterServer
- ATLBASE/ATL::CComModule::RegisterTypeLib
- ATLBASE/ATL::CComModule::RevokeClassObjects
- ATLBASE/ATL::CComModule::Term
- ATLBASE/ATL::CComModule::UnregisterClassHelper
- ATLBASE/ATL::CComModule::UnregisterServer
- ATLBASE/ATL::CComModule::UpdateRegistryClass
- ATLBASE/ATL::CComModule::UpdateRegistryFromResourceD
- ATLBASE/ATL::CComModule::UpdateRegistryFromResourceS
- ATLBASE/ATL::CComModule::m_csObjMap
- ATLBASE/ATL::CComModule::m_csTypeInfoHolder
- ATLBASE/ATL::CComModule::m_csWindowCreate
- ATLBASE/ATL::CComModule::m_hInst
- ATLBASE/ATL::CComModule::m_hInstResource
- ATLBASE/ATL::CComModule::m_hInstTypeLib
- ATLBASE/ATL::CComModule::m_pObjMap
helpviewer_keywords:
- CComModule class
- DLL modules [C++], ATL
ms.assetid: f5face2c-8fd8-40e6-9ec3-54ab74701769
ms.openlocfilehash: 652c5f078ddbaf8d3e333f7003d6515a94dd8f83
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327763"
---
# <a name="ccommodule-class"></a>CComModule-Klasse

Ab ATL 7.0 `CComModule` ist veraltet: siehe [ATL-Modulklassen](../../atl/atl-module-classes.md) für weitere Details.

> [!IMPORTANT]
> Diese Klasse und ihre Member können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

## <a name="syntax"></a>Syntax

```
class CComModule : public _ATL_MODULE
```

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CComModule::GetClassObject](#getclassobject)|Erstellt ein Objekt einer angegebenen CLSID. Nur für DLLs.|
|[CComModule::GetModuleInstance](#getmoduleinstance)|Gibt `m_hInst` zurück.|
|[CComModule::GetResourceInstance](#getresourceinstance)|Gibt `m_hInstResource` zurück.|
|[CComModule::GetTypeLibInstance](#gettypelibinstance)|Gibt `m_hInstTypeLib` zurück.|
|[CComModule::Init](#init)|Initialisiert Datenmember.|
|[CComModule::RegisterClassHelper](#registerclasshelper)|Gibt die Standardklassenregistrierung eines Objekts in der Systemregistrierung ein.|
|[CComModule::RegisterClassObjects](#registerclassobjects)|Registriert das Klassenobjekt. Nur für EXEs.|
|[CComModule::RegisterServer](#registerserver)|Aktualisiert die Systemregistrierung für jedes Objekt in der Objektzuordnung.|
|[CComModule::RegisterTypeLib](#registertypelib)|Registriert eine Typbibliothek.|
|[CComModule::RevokeClassObjects](#revokeclassobjects)|Das Klassenobjekt wird widerrufen. Nur für EXEs.|
|[CComModule::Term](#term)|Gibt Datenmember frei.|
|[CComModule::UnregisterClassHelper](#unregisterclasshelper)|Entfernt die Standardklassenregistrierung eines Objekts aus der Systemregistrierung.|
|[CComModule::UnregisterServer](#unregisterserver)|Entregistriert jedes Objekt in der Objektzuordnung.|
|[CComModule::UpdateRegistryClass](#updateregistryclass)|Registriert oder entsperrt die Registrierung der Standardklasseneines.|
|[CComModule::UpdateRegistryFromResourceD](#updateregistryfromresourced)|Führt das Skript aus, das in einer angegebenen Ressource enthalten ist, um ein Objekt zu registrieren oder aufzuheben.|
|[CComModule::UpdateRegistryFromResourceS](#updateregistryfromresources)|Statische Verknüpfungen mit der ATL-Registrierungskomponente. Führt das Skript aus, das in einer angegebenen Ressource enthalten ist, um ein Objekt zu registrieren oder aufzuheben.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CComModule::m_csObjMap](#m_csobjmap)|Gewährleistet den synchronisierten Zugriff auf die Objektzuordnungsinformationen.|
|[CComModule::m_csTypeInfoHolder](#m_cstypeinfoholder)|Gewährleistet den synchronisierten Zugriff auf die Typbibliotheksinformationen.|
|[CComModule::m_csWindowCreate](#m_cswindowcreate)|Gewährleistet den synchronisierten Zugriff auf Fensterklasseninformationen und statische Daten, die bei der Fenstererstellung verwendet werden.|
|[CComModule::m_hInst](#m_hinst)|Enthält das Handle für die Modulinstanz.|
|[CComModule::m_hInstResource](#m_hinstresource)|Enthält standardmäßig das Handle für die Modulinstanz.|
|[CComModule::m_hInstTypeLib](#m_hinsttypelib)|Enthält standardmäßig das Handle für die Modulinstanz.|
|[CComModule::m_pObjMap](#m_pobjmap)|Zeigt auf die Objektzuordnung, die von der Modulinstanz verwaltet wird.|

## <a name="remarks"></a>Bemerkungen

> [!NOTE]
> Diese Klasse ist veraltet, und die ATL-Codegenerierungsassistenten verwenden jetzt die abgeleiteten Klassen [CAtlAutoThreadModule](../../atl/reference/catlautothreadmodule-class.md) und [CAtlModule.](../../atl/reference/catlmodule-class.md) Weitere Informationen finden Sie unter [ATL-Modulklassen.](../../atl/atl-module-classes.md) Die folgenden Informationen sind für die Verwendung mit Anwendungen bestimmt, die mit älteren VERSIONEN von ATL erstellt wurden. `CComModule`ist immer noch Teil von ATL für Rückwärtsfähigkeit.

`CComModule`implementiert ein COM-Servermodul, sodass ein Client auf die Komponenten des Moduls zugreifen kann. `CComModule`unterstützt sowohl DLL-Module (in-Process) als auch EXE(local) Module.

Eine `CComModule` Instanz verwendet eine Objektzuordnung, um einen Satz von Klassenobjektdefinitionen beizubehalten. Diese Objektzuordnung wird als `_ATL_OBJMAP_ENTRY` Array von Strukturen implementiert und enthält Informationen für:

- Eingeben und Entfernen von Objektbeschreibungen in der Systemregistrierung.

- Instanziieren von Objekten durch eine Klassenfabrik.

- Herstellen der Kommunikation zwischen einem Client und dem Stammobjekt in der Komponente.

- Durchführen der lebenslangen Verwaltung von Klassenobjekten.

Wenn Sie den ATL COM AppWizard `_Module`ausführen, generiert `CComModule` der Assistent automatisch , eine globale Instanz oder eine daraus abgeleitete Klasse. Weitere Informationen zum ATL-Projekt-Assistenten finden Sie im Artikel [Erstellen eines ATL-Projekts](../../atl/reference/creating-an-atl-project.md).

Zusätzlich zu `CComModule`, atL bietet [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md), die ein Apartment-Modell-Modul für EXEs und Windows-Dienste implementiert. Leiten Sie Ihr `CComAutoThreadModule` Modul ab, wenn Sie Objekte in mehreren Wohnungen erstellen möchten.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[CAtlModule](../../atl/reference/catlmodule-class.md)

[CAtlModuleT](../../atl/reference/catlmodulet-class.md)

`CComModule`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlbase.h

## <a name="ccommodulegetclassobject"></a><a name="getclassobject"></a>CComModule::GetClassObject

Ab ATL 7.0 `CComModule` ist veraltet: siehe [ATL-Modulklassen](../../atl/atl-module-classes.md) für weitere Details.

```
HRESULT GetClassObject(
    REFCLSID rclsid,
    REFIID riid,
    LPVOID* ppv) throw();
```

### <a name="parameters"></a>Parameter

*rclsid*<br/>
[in] Die CLSID des zu erstellenden Objekts.

*riid*<br/>
[in] Die IID der angeforderten Schnittstelle.

*Ppv*<br/>
[out] Ein Zeiger auf den Schnittstellenzeiger, der von *riid*identifiziert wird. Wenn das Objekt diese Schnittstelle nicht unterstützt, wird *ppv* auf NULL gesetzt.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

### <a name="remarks"></a>Bemerkungen

Erstellt ein Objekt der angegebenen CLSID und ruft einen Schnittstellenzeiger für dieses Objekt ab.

`GetClassObject`ist nur für DLLs verfügbar.

## <a name="ccommodulegetmoduleinstance"></a><a name="getmoduleinstance"></a>CComModule::GetModuleInstance

Ab ATL 7.0 `CComModule` ist veraltet: siehe [ATL-Modulklassen](../../atl/atl-module-classes.md) für weitere Details.

```
HINSTANCE GetModuleInstance() throw();
```

### <a name="return-value"></a>Rückgabewert

Die HINSTANCE, die dieses Modul identifiziert.

### <a name="remarks"></a>Bemerkungen

Gibt das [m_hInst](#m_hinst) Datenmember zurück.

## <a name="ccommodulegetresourceinstance"></a><a name="getresourceinstance"></a>CComModule::GetResourceInstance

Ab ATL 7.0 `CComModule` ist veraltet: siehe [ATL-Modulklassen](../../atl/atl-module-classes.md) für weitere Details.

```
HINSTANCE GetResourceInstance() throw();
```

### <a name="return-value"></a>Rückgabewert

Eine HINSTANCE.

### <a name="remarks"></a>Bemerkungen

Gibt das [m_hInstResource](#m_hinstresource) Datenmember zurück.

## <a name="ccommodulegettypelibinstance"></a><a name="gettypelibinstance"></a>CComModule::GetTypeLibInstance

Ab ATL 7.0 `CComModule` ist veraltet: siehe [ATL-Modulklassen](../../atl/atl-module-classes.md) für weitere Details.

```
HINSTANCE GetTypeLibInstance() const throw();
```

### <a name="return-value"></a>Rückgabewert

Eine HINSTANCE.

### <a name="remarks"></a>Bemerkungen

Gibt das [m_hInstTypeLib](#m_hinsttypelib) Datenmember zurück.

## <a name="ccommoduleinit"></a><a name="init"></a>CComModule::Init

Ab ATL 7.0 `CComModule` ist veraltet: siehe [ATL-Modulklassen](../../atl/atl-module-classes.md) für weitere Details.

```
HRESULT Init(
    _ATL_OBJMAP_ENTRY* p,
    HINSTANCE h,
    const GUID* plibid = NULL) throw();
```

### <a name="parameters"></a>Parameter

*P*<br/>
[in] Ein Zeiger auf ein Array von Objektzuordnungseinträgen.

*H*<br/>
[in] Die HINSTANCE `DLLMain` an `WinMain`oder übergeben.

*plibid*<br/>
[in] Ein Zeiger auf die LIBID der dem Projekt zugeordneten Typbibliothek.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

### <a name="remarks"></a>Bemerkungen

Initialisiert alle Datenmember.

## <a name="ccommodulem_csobjmap"></a><a name="m_csobjmap"></a>CComModule::m_csObjMap

Ab ATL 7.0 `CComModule` ist veraltet: siehe [ATL-Modulklassen](../../atl/atl-module-classes.md) für weitere Details.

```
CRITICAL_SECTION m_csObjMap;
```

### <a name="remarks"></a>Bemerkungen

Gewährleistet den synchronisierten Zugriff auf die Objektzuordnung.

## <a name="ccommodulem_cstypeinfoholder"></a><a name="m_cstypeinfoholder"></a>CComModule::m_csTypeInfoHolder

Ab ATL 7.0 `CComModule` ist veraltet: siehe [ATL-Modulklassen](../../atl/atl-module-classes.md) für weitere Details.

```
CRITICAL_SECTION m_csTypeInfoHolder;
```

### <a name="remarks"></a>Bemerkungen

Gewährleistet den synchronisierten Zugriff auf die Typbibliothek.

## <a name="ccommodulem_cswindowcreate"></a><a name="m_cswindowcreate"></a>CComModule::m_csWindowCreate

Ab ATL 7.0 `CComModule` ist veraltet: siehe [ATL-Modulklassen](../../atl/atl-module-classes.md) für weitere Details.

```
CRITICAL_SECTION m_csWindowCreate;
```

### <a name="remarks"></a>Bemerkungen

Gewährleistet den synchronisierten Zugriff auf Fensterklasseninformationen und statische Daten, die bei der Fenstererstellung verwendet werden.

## <a name="ccommodulem_hinst"></a><a name="m_hinst"></a>CComModule::m_hInst

Ab ATL 7.0 `CComModule` ist veraltet: siehe [ATL-Modulklassen](../../atl/atl-module-classes.md) für weitere Details.

```
HINSTANCE m_hInst;
```

### <a name="remarks"></a>Bemerkungen

Enthält das Handle für die Modulinstanz.

Die [Init-Methode](#init) legt `m_hInst` das `DLLMain` `WinMain`Handle fest, das an oder übergeben wird.

## <a name="ccommodulem_hinstresource"></a><a name="m_hinstresource"></a>CComModule::m_hInstResource

Ab ATL 7.0 `CComModule` ist veraltet: siehe [ATL-Modulklassen](../../atl/atl-module-classes.md) für weitere Details.

```
HINSTANCE m_hInstResource;
```

### <a name="remarks"></a>Bemerkungen

Enthält standardmäßig das Handle für die Modulinstanz.

Die [Init-Methode](#init) legt `m_hInstResource` das `DLLMain` `WinMain`Handle fest, das an oder übergeben wird. Sie können `m_hInstResource` das Handle explizit auf eine Ressource festlegen.

Die [GetResourceInstance-Methode](#getresourceinstance) gibt `m_hInstResource`das in gespeicherte Handle zurück.

## <a name="ccommodulem_hinsttypelib"></a><a name="m_hinsttypelib"></a>CComModule::m_hInstTypeLib

Ab ATL 7.0 `CComModule` ist veraltet: siehe [ATL-Modulklassen](../../atl/atl-module-classes.md) für weitere Details.

```
HINSTANCE m_hInstTypeLib;
```

### <a name="remarks"></a>Bemerkungen

Enthält standardmäßig das Handle für die Modulinstanz.

Die [Init-Methode](#init) legt `m_hInstTypeLib` das `DLLMain` `WinMain`Handle fest, das an oder übergeben wird. Sie können `m_hInstTypeLib` explizit auf das Handle auf eine Typbibliothek festlegen.

Die [GetTypeLibInstance-Methode](#gettypelibinstance) gibt `m_hInstTypeLib`das in gespeicherte Handle zurück.

## <a name="ccommodulem_pobjmap"></a><a name="m_pobjmap"></a>CComModule::m_pObjMap

Ab ATL 7.0 `CComModule` ist veraltet: siehe [ATL-Modulklassen](../../atl/atl-module-classes.md) für weitere Details.

```
_ATL_OBJMAP_ENTRY* m_pObjMap;
```

### <a name="remarks"></a>Bemerkungen

Zeigt auf die Objektzuordnung, die von der Modulinstanz verwaltet wird.

## <a name="ccommoduleregisterclasshelper"></a><a name="registerclasshelper"></a>CComModule::RegisterClassHelper

Ab ATL 7.0 `CComModule` ist veraltet: siehe [ATL-Modulklassen](../../atl/atl-module-classes.md) für weitere Details.

```
ATL_DEPRECATED HRESULT RegisterClassHelper(
    const CLSID& clsid,
    LPCTSTR lpszProgID,
    LPCTSTR lpszVerIndProgID,
    UINT nDescID,
    DWORD dwFlags);
```

### <a name="parameters"></a>Parameter

*clsid*<br/>
[in] Die CLSID des zu registrierenden Objekts.

*lpszProgID*<br/>
[in] Die dem Objekt zugeordnete ProgID.

*lpszVerIndProgID*<br/>
[in] Die versionsunabhängige ProgID, die dem Objekt zugeordnet ist.

*nDescID*<br/>
[in] Der Bezeichner einer Zeichenfolgenressource für die Beschreibung des Objekts.

*dwFlags*<br/>
[in] Gibt das Threadingmodell an, das in die Registrierung eingegeben werden soll. Mögliche Werte sind THREADFLAGS_APARTMENT, THREADFLAGS_BOTH oder AUTPRXFLAG.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

### <a name="remarks"></a>Bemerkungen

Gibt die Standardklassenregistrierung eines Objekts in der Systemregistrierung ein.

Die [UpdateRegistryClass-Methode](#updateregistryclass) ruft auf. `RegisterClassHelper`

## <a name="ccommoduleregisterclassobjects"></a><a name="registerclassobjects"></a>CComModule::RegisterClassObjects

Ab ATL 7.0 `CComModule` ist veraltet: siehe [ATL-Modulklassen](../../atl/atl-module-classes.md) für weitere Details.

```
HRESULT RegisterClassObjects(DWORD dwClsContext, DWORD dwFlags) throw();
```

### <a name="parameters"></a>Parameter

*dwClsContext*<br/>
[in] Gibt den Kontext an, in dem das Klassenobjekt ausgeführt werden soll. Mögliche Werte sind CLSCTX_INPROC_SERVER, CLSCTX_INPROC_HANDLER oder CLSCTX_LOCAL_SERVER. Eine Beschreibung dieser Werte finden Sie unter [CLSCTX](/windows/win32/api/wtypesbase/ne-wtypesbase-clsctx) im Windows SDK.

*dwFlags*<br/>
[in] Bestimmt die Verbindungstypen zum Klassenobjekt. Mögliche Werte sind REGCLS_SINGLEUSE, REGCLS_MULTIPLEUSE oder REGCLS_MULTI_SEPARATE. Eine Beschreibung dieser Werte finden Sie unter [REGCLS](/windows/win32/api/combaseapi/ne-combaseapi-regcls) im Windows SDK.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

### <a name="remarks"></a>Bemerkungen

Registriert ein EXE-Klassenobjekt bei OLE, damit andere Anwendungen eine Verbindung herstellen können. Diese Methode ist nur für EXEs verfügbar.

## <a name="ccommoduleregisterserver"></a><a name="registerserver"></a>CComModule::RegisterServer

Ab ATL 7.0 `CComModule` ist veraltet: siehe [ATL-Modulklassen](../../atl/atl-module-classes.md) für weitere Details.

```
HRESULT RegisterServer(
    BOOL bRegTypeLib = FALSE,
    const CLSID* pCLSID = NULL) throw();
```

### <a name="parameters"></a>Parameter

*bRegTypeLib*<br/>
[in] Gibt an, ob die Typbibliothek registriert werden soll. Der Standardwert ist FALSE.

*pCLSID*<br/>
[in] Zeigt auf die CLSID des zu registrierenden Objekts. Wenn NULL (der Standardwert), werden alle Objekte in der Objektzuordnung registriert.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

### <a name="remarks"></a>Bemerkungen

Aktualisiert abhängig vom *pCLSID-Parameter* die Systemregistrierung für ein einzelnes Klassenobjekt oder für alle Objekte in der Objektzuordnung.

Wenn *bRegTypeLib* TRUE ist, werden auch die Typbibliotheksinformationen aktualisiert.

Informationen zum Hinzufügen eines Eintrags zur Objektzuordnung finden Sie [in OBJECT_ENTRY_AUTO.](object-map-macros.md#object_entry_auto)

`RegisterServer`wird automatisch von `DLLRegisterServer` für eine DLL oder von `WinMain` für `/RegServer` eine EXE-Ausführung mit der Befehlszeilenoption aufgerufen.

## <a name="ccommoduleregistertypelib"></a><a name="registertypelib"></a>CComModule::RegisterTypeLib

Ab ATL 7.0 `CComModule` ist veraltet: siehe [ATL-Modulklassen](../../atl/atl-module-classes.md) für weitere Details.

```
HRESULT RegisterTypeLib() throw();
HRESULT RegisterTypeLib(LPCTSTR lpszIndex) throw();
```

### <a name="parameters"></a>Parameter

*lpszIndex*<br/>
[in] Zeichenfolge im `"\\N"`Format `N` , wobei der Ganzzahlindex der TYPELIB-Ressource ist.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

### <a name="remarks"></a>Bemerkungen

Fügt der Systemregistrierung Informationen zu einer Typbibliothek hinzu.

Wenn die Modulinstanz mehrere Typbibliotheken enthält, verwenden Sie die zweite Version dieser Methode, um anzugeben, welche Typbibliothek verwendet werden soll.

## <a name="ccommodulerevokeclassobjects"></a><a name="revokeclassobjects"></a>CComModule::RevokeClassObjects

Ab ATL 7.0 `CComModule` ist veraltet: siehe [ATL-Modulklassen](../../atl/atl-module-classes.md) für weitere Details.

```
HRESULT RevokeClassObjects() throw();
```

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

### <a name="remarks"></a>Bemerkungen

Entfernt das Klassenobjekt. Diese Methode ist nur für EXEs verfügbar.

## <a name="ccommoduleterm"></a><a name="term"></a>CComModule::Term

Ab ATL 7.0 `CComModule` ist veraltet: siehe [ATL-Modulklassen](../../atl/atl-module-classes.md) für weitere Details.

```
void Term() throw();
```

### <a name="remarks"></a>Bemerkungen

Gibt alle Datenmember frei.

## <a name="ccommoduleunregisterclasshelper"></a><a name="unregisterclasshelper"></a>CComModule::UnregisterClassHelper

Ab ATL 7.0 `CComModule` ist veraltet: siehe [ATL-Modulklassen](../../atl/atl-module-classes.md) für weitere Details.

```
ATL_DEPRECATED HRESULT UnregisterClassHelper(
    const CLSID& clsid,
    LPCTSTR lpszProgID,
    LPCTSTR lpszVerIndProgID);
```

### <a name="parameters"></a>Parameter

*clsid*<br/>
[in] Die CLSID des objekts, das nicht registriert werden soll.

*lpszProgID*<br/>
[in] Die dem Objekt zugeordnete ProgID.

*lpszVerIndProgID*<br/>
[in] Die versionsunabhängige ProgID, die dem Objekt zugeordnet ist.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

### <a name="remarks"></a>Bemerkungen

Entfernt die Standardklassenregistrierung eines Objekts aus der Systemregistrierung.

Die [UpdateRegistryClass-Methode](#updateregistryclass) ruft auf. `UnregisterClassHelper`

## <a name="ccommoduleunregisterserver"></a><a name="unregisterserver"></a>CComModule::UnregisterServer

Ab ATL 7.0 `CComModule` ist veraltet: siehe [ATL-Modulklassen](../../atl/atl-module-classes.md) für weitere Details.

```
HRESULT UnregisterServer(const CLSID* pCLSID = NULL) throw ();
inline HRESULT UnregisterServer(BOOL bUnRegTypeLib, const CLSID* pCLSID = NULL) throw ();
```

### <a name="parameters"></a>Parameter

*bUnRegTypeLib*<br/>
Wenn TRUE, wird die Typbibliothek ebenfalls nicht registriert.

*pCLSID*<br/>
Zeigt auf die CLSID des objekts, das nicht registriert werden soll. Wenn NULL (der Standardwert), werden alle Objekte in der Objektzuordnung nicht registriert.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

### <a name="remarks"></a>Bemerkungen

Abhängig vom *pCLSID-Parameter* wird die Registrierung eines einzelnen Klassenobjekts oder aller Objekte in der Objektzuordnung aufheben.

`UnregisterServer`wird automatisch von `DLLUnregisterServer` für eine DLL oder von `WinMain` für `/UnregServer` eine EXE-Ausführung mit der Befehlszeilenoption aufgerufen.

Informationen zum Hinzufügen eines Eintrags zur Objektzuordnung finden Sie [in OBJECT_ENTRY_AUTO.](object-map-macros.md#object_entry_auto)

## <a name="ccommoduleupdateregistryclass"></a><a name="updateregistryclass"></a>CComModule::UpdateRegistryClass

Ab ATL 7.0 `CComModule` ist veraltet: siehe [ATL-Modulklassen](../../atl/atl-module-classes.md) für weitere Details.

```
ATL_DEPRECATED HRESULT UpdateRegistryClass(
    const CLSID& clsid,
    LPCTSTR lpszProgID,
    LPCTSTR lpszVerIndProgID,
    UINT nDescID,
    DWORD dwFlags,
    BOOL bRegister);

ATL_DEPRECATED HRESULT UpdateRegistryClass(
    const CLSID& clsid,
    LPCTSTR lpszProgID,
    LPCTSTR lpszVerIndProgID,
    LPCTSTR szDesc,
    DWORD dwFlags,
    BOOL bRegister);
```

### <a name="parameters"></a>Parameter

*clsid*<br/>
Die CLSID des zu registrierenden oder nicht registrierten Objekts.

*lpszProgID*<br/>
Die dem Objekt zugeordnete ProgID.

*lpszVerIndProgID*<br/>
Die versionsunabhängige ProgID, die dem Objekt zugeordnet ist.

*nDescID*<br/>
Der Bezeichner der Zeichenfolgenressource für die Beschreibung des Objekts.

*szDesc*<br/>
Eine Zeichenfolge, die die Beschreibung des Objekts enthält.

*dwFlags*<br/>
Gibt das Threadingmodell an, das in die Registrierung eingegeben werden soll. Mögliche Werte sind THREADFLAGS_APARTMENT, THREADFLAGS_BOTH oder AUTPRXFLAG.

*bRegister*<br/>
Gibt an, ob das Objekt registriert werden soll.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

### <a name="remarks"></a>Bemerkungen

Wenn *bRegister* TRUE ist, gibt diese Methode die Standardklassenregistrierung des Objekts in die Systemregistrierung ein.

Wenn *bRegister* FALSE ist, wird die Registrierung des Objekts entfernt.

Abhängig vom Wert von `UpdateRegistryClass` *bRegister*ruft entweder [RegisterClassHelper](#registerclasshelper) oder [UnregisterClassHelper](#unregisterclasshelper)auf.

Durch Die Angabe des `UpdateRegistryClass` [DECLARE_REGISTRY-Makros](registry-macros.md#declare_registry) wird automatisch aufgerufen, wenn die Objektzuordnung verarbeitet wird.

## <a name="ccommoduleupdateregistryfromresourced"></a><a name="updateregistryfromresourced"></a>CComModule::UpdateRegistryFromResourceD

Ab ATL 7.0 `CComModule` ist veraltet: siehe [ATL-Modulklassen](../../atl/atl-module-classes.md) für weitere Details.

```
virtual HRESULT UpdateRegistryFromResourceD(
    LPCTSTR lpszRes,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw();

virtual HRESULT UpdateRegistryFromResourceD(
    UINT nResID,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw ();
```

### <a name="parameters"></a>Parameter

*lpszRes*<br/>
[in] Ein Ressourcenname.

*nResID*<br/>
[in] Eine Ressourcen-ID.

*bRegister*<br/>
[in] Gibt an, ob das Objekt registriert werden soll.

*pMapEntries*<br/>
[in] Ein Zeiger auf die Ersatzzuordnung, in der Werte gespeichert werden, die den austauschbaren Parametern des Skripts zugeordnet sind. ATL verwendet `%MODULE%`automatisch . Weitere Informationen finden Sie unter Hinweise. Andernfalls verwenden Sie den NULL-Standardwert.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

### <a name="remarks"></a>Bemerkungen

Führt das Skript aus, das in der von *lpszRes* oder *nResID*angegebenen Ressource enthalten ist.

Wenn *bRegister* TRUE ist, registriert diese Methode das Objekt in der Systemregistrierung. Andernfalls wird die Registrierung des Objekts aufheben.

Durch Angabe der [DECLARE_REGISTRY_RESOURCE](registry-macros.md#declare_registry_resource) oder `UpdateRegistryFromResourceD` [DECLARE_REGISTRY_RESOURCEID](registry-macros.md#declare_registry_resourceid) Makros wird automatisch aufgerufen, wenn die Objektzuordnung verarbeitet wird.

> [!NOTE]
> Um Ersatzwerte zur Laufzeit zu ersetzen, geben Sie nicht die DECLARE_REGISTRY_RESOURCE oder DECLARE_REGISTRY_RESOURCEID-Makros an. Erstellen Sie stattdessen `_ATL_REGMAP_ENTRIES` ein Array von Strukturen, wobei jeder Eintrag einen variablen Platzhalter enthält, der mit einem Wert gekoppelt ist, um den Platzhalter zur Laufzeit zu ersetzen. Dann `UpdateRegistryFromResourceD`rufen Sie auf, das Array für den Parameter *pMapEntries* zu übergeben. Dadurch werden alle Ersatzwerte `_ATL_REGMAP_ENTRIES` in den Strukturen zur Ersatzkarte des Registrars hinzugefügt.

> [!NOTE]
> Informationen zum statischen Verknüpfen mit der ATL-Registrierungskomponente (Registrar) finden Sie unter [UpdateRegistryFromResourceS](#updateregistryfromresources).

Weitere Informationen zu austauschbaren Parametern und Skripts finden Sie im Artikel [The ATL Registry Component (Registrar)](../../atl/atl-registry-component-registrar.md).

## <a name="ccommoduleupdateregistryfromresources"></a><a name="updateregistryfromresources"></a>CComModule::UpdateRegistryFromResourceS

Ab ATL 7.0 `CComModule` ist veraltet: siehe [ATL-Modulklassen](../../atl/atl-module-classes.md) für weitere Details.

```
virtual HRESULT UpdateRegistryFromResourceS(
    LPCTSTR lpszRes,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw();

virtual HRESULT UpdateRegistryFromResourceS(
    UINT nResID,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw();
```

### <a name="parameters"></a>Parameter

*lpszRes*<br/>
[in] Ein Ressourcenname.

*nResID*<br/>
[in] Eine Ressourcen-ID.

*bRegister*<br/>
[in] Gibt an, ob das Ressourcenskript registriert werden soll.

*pMapEntries*<br/>
[in] Ein Zeiger auf die Ersatzzuordnung, in der Werte gespeichert werden, die den austauschbaren Parametern des Skripts zugeordnet sind. ATL verwendet `%MODULE%`automatisch . Weitere Informationen finden Sie unter Hinweise. Andernfalls verwenden Sie den NULL-Standardwert.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

### <a name="remarks"></a>Bemerkungen

Ähnlich [wie UpdateRegistryFromResourceD](#updateregistryfromresourced) erstellt außer `UpdateRegistryFromResourceS` eine statische Verknüpfung mit der ATL-Registrierungskomponente (Registrar).

`UpdateRegistryFromResourceS`wird automatisch aufgerufen, wenn ihre Objektzuordnung verarbeitet `#define _ATL_STATIC_REGISTRY` wird, vorausgesetzt, Sie fügen Ihrer *pch.h* (*stdafx.h* in Visual Studio 2017 und früher) hinzu.

> [!NOTE]
> Um Ersatzwerte zur Laufzeit zu ersetzen, geben Sie nicht die [DECLARE_REGISTRY_RESOURCE](registry-macros.md#declare_registry_resource) oder [DECLARE_REGISTRY_RESOURCEID-Makros](registry-macros.md#declare_registry_resourceid) an. Erstellen Sie stattdessen `_ATL_REGMAP_ENTRIES` ein Array von Strukturen, wobei jeder Eintrag einen variablen Platzhalter enthält, der mit einem Wert gekoppelt ist, um den Platzhalter zur Laufzeit zu ersetzen. Dann `UpdateRegistryFromResourceS`rufen Sie auf, das Array für den Parameter *pMapEntries* zu übergeben. Dadurch werden alle Ersatzwerte `_ATL_REGMAP_ENTRIES` in den Strukturen zur Ersatzkarte des Registrars hinzugefügt.

Weitere Informationen zu austauschbaren Parametern und Skripts finden Sie im Artikel [The ATL Registry Component (Registrar)](../../atl/atl-registry-component-registrar.md).

## <a name="see-also"></a>Siehe auch

[Klassenübersicht](../../atl/atl-class-overview.md)
