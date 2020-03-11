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
ms.openlocfilehash: 482f29bae28841ab40ca8a8f80ab7f0df42ddc8b
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78863189"
---
# <a name="ccommodule-class"></a>CComModule-Klasse

Ab ATL 7,0 ist `CComModule` veraltet: Weitere Informationen finden Sie unter [ATL-Modul Klassen](../../atl/atl-module-classes.md) .

> [!IMPORTANT]
>  Diese Klasse und ihre Member können in Anwendungen, die im Windows-Runtime ausgeführt werden, nicht verwendet werden.

## <a name="syntax"></a>Syntax

```
class CComModule : public _ATL_MODULE
```

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|-Name|Beschreibung|
|----------|-----------------|
|[CComModule::GetClassObject](#getclassobject)|Erstellt ein Objekt einer angegebenen CLSID. Nur für DLLs.|
|[CComModule::GetModuleInstance](#getmoduleinstance)|Gibt `m_hInst`zurück.|
|[CComModule::GetResourceInstance](#getresourceinstance)|Gibt `m_hInstResource`zurück.|
|[CComModule::GetTypeLibInstance](#gettypelibinstance)|Gibt `m_hInstTypeLib`zurück.|
|[CComModule:: init](#init)|Initialisiert Datenmember.|
|[CComModule:: registerclasshelper](#registerclasshelper)|Gibt die Standard-Klassen Registrierung eines Objekts in der Systemregistrierung ein.|
|[CComModule:: RegisterClassObjects](#registerclassobjects)|Registriert das Klassenobjekt. Nur für exe-Datei.|
|[CComModule:: RegisterServer](#registerserver)|Aktualisiert die Systemregistrierung für jedes Objekt in der Objekt Zuordnung.|
|[CComModule::RegisterTypeLib](#registertypelib)|Registriert eine Typbibliothek.|
|[CComModule:: revokeclassobjects](#revokeclassobjects)|Widerruft das Klassenobjekt. Nur für exe-Datei.|
|[CComModule:: Term](#term)|Gibt Datenmember frei.|
|[CComModule:: unregisterclasshelper](#unregisterclasshelper)|Entfernt die standardmäßige Klassen Registrierung eines Objekts aus der Systemregistrierung.|
|[CComModule:: unregisterserver](#unregisterserver)|Hebt die Registrierung der einzelnen Objekte in der Objekt Zuordnung auf.|
|[CComModule::UpdateRegistryClass](#updateregistryclass)|Registriert oder hebt die Registrierung der Standardklassen Registrierung eines Objekts auf.|
|[CComModule::UpdateRegistryFromResourceD](#updateregistryfromresourced)|Führt das in einer angegebenen Ressource enthaltene Skript aus, um ein Objekt zu registrieren oder die Registrierung aufzuheben.|
|[CComModule::UpdateRegistryFromResourceS](#updateregistryfromresources)|Verknüpft statisch mit der ATL-Registrierungs Komponente. Führt das in einer angegebenen Ressource enthaltene Skript aus, um ein Objekt zu registrieren oder die Registrierung aufzuheben.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|Beschreibung|
|----------|-----------------|
|[CComModule::m_csObjMap](#m_csobjmap)|Gewährleistet den synchronisierten Zugriff auf die Objekt Zuordnungs Informationen.|
|[CComModule::m_csTypeInfoHolder](#m_cstypeinfoholder)|Stellt den synchronisierten Zugriff auf die Typbibliotheks Informationen sicher.|
|[CComModule::m_csWindowCreate](#m_cswindowcreate)|Gewährleistet den synchronisierten Zugriff auf Fenster Klassen Informationen und statische Daten, die während der Fenster Erstellung verwendet werden.|
|[CComModule::m_hInst](#m_hinst)|Enthält das Handle für die Modul Instanz.|
|[CComModule::m_hInstResource](#m_hinstresource)|Standardmäßig enthält das Handle für die Modul Instanz.|
|[CComModule::m_hInstTypeLib](#m_hinsttypelib)|Standardmäßig enthält das Handle für die Modul Instanz.|
|[CComModule::m_pObjMap](#m_pobjmap)|Verweist auf die Objekt Zuordnung, die von der Modul Instanz verwaltet wird.|

## <a name="remarks"></a>Hinweise

> [!NOTE]
>  Diese Klasse ist veraltet, und Assistenten für die Generierung von ATL-Code verwenden nun die abgeleiteten Klassen [CAtlAutoThreadModule](../../atl/reference/catlautothreadmodule-class.md) und [CAtlModule](../../atl/reference/catlmodule-class.md). Weitere Informationen finden Sie unter [ATL-Modul Klassen](../../atl/atl-module-classes.md) . Die folgenden Informationen gelten für die Verwendung mit Anwendungen, die mit älteren Versionen von ATL erstellt wurden. `CComModule` ist noch Teil von ATL für abwärts Funktion.

`CComModule` implementiert ein com-Servermodul, das einem Client den Zugriff auf die Komponenten des Moduls ermöglicht. `CComModule` unterstützt sowohl dll-(in-Process) als auch exe-Module (local).

Eine `CComModule`-Instanz verwendet eine Objekt Zuordnung, um einen Satz von Klassenobjekt Definitionen beizubehalten. Diese Objekt Zuordnung wird als Array von `_ATL_OBJMAP_ENTRY` Strukturen implementiert und enthält Informationen für:

- Eingeben und Entfernen von Objektbeschreibungen in der Systemregistrierung.

- Instanziieren von Objekten über eine Klassenfactory.

- Einrichten der Kommunikation zwischen einem Client und dem Stamm Objekt in der Komponente.

- Die Lebensdauer Verwaltung von Klassen Objekten wird durchgeführt.

Wenn Sie den ATL COM AppWizard ausführen, generiert der Assistent automatisch `_Module`, eine globale Instanz von `CComModule` oder eine davon abgeleitete Klasse. Weitere Informationen zum ATL-Projekt-Assistenten finden Sie im Artikel [Erstellen eines ATL-Projekts](../../atl/reference/creating-an-atl-project.md).

Zusätzlich zu `CComModule`bietet ATL [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md), das ein Apartment Modell Modul für exe-und Windows-Dienste implementiert. Leiten Sie das Modul von `CComAutoThreadModule` ab, wenn Sie Objekte in mehreren Apartments erstellen möchten.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[CAtlModule](../../atl/reference/catlmodule-class.md)

[CAtlModuleT](../../atl/reference/catlmodulet-class.md)

`CComModule`

## <a name="requirements"></a>Anforderungen

**Header:** atlbase. h

##  <a name="getclassobject"></a>CComModule:: GetClassObject

Ab ATL 7,0 ist `CComModule` veraltet: Weitere Informationen finden Sie unter [ATL-Modul Klassen](../../atl/atl-module-classes.md) .

```
HRESULT GetClassObject(
    REFCLSID rclsid,
    REFIID riid,
    LPVOID* ppv) throw();
```

### <a name="parameters"></a>Parameter

*rclsid*<br/>
in Die CLSID des zu erstellenden Objekts.

*riid*<br/>
in Die IID der angeforderten Schnittstelle.

*ppv*<br/>
vorgenommen Ein Zeiger auf den Schnittstellen Zeiger, der durch *riid*identifiziert wird. Wenn das Objekt diese Schnittstelle nicht unterstützt, wird *PPV* auf NULL festgelegt.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standardwert.

### <a name="remarks"></a>Hinweise

Erstellt ein Objekt der angegebenen CLSID und Ruft einen Schnittstellen Zeiger auf dieses Objekt ab.

`GetClassObject` ist nur für DLLs verfügbar.

##  <a name="getmoduleinstance"></a>CComModule:: getmoduleinstance

Ab ATL 7,0 ist `CComModule` veraltet: Weitere Informationen finden Sie unter [ATL-Modul Klassen](../../atl/atl-module-classes.md) .

```
HINSTANCE GetModuleInstance() throw();
```

### <a name="return-value"></a>Rückgabewert

Die HINSTANCE, die dieses Modul identifiziert.

### <a name="remarks"></a>Hinweise

Gibt den [m_hInst](#m_hinst) Datenmember zurück.

##  <a name="getresourceinstance"></a>CComModule:: getresourceingestance

Ab ATL 7,0 ist `CComModule` veraltet: Weitere Informationen finden Sie unter [ATL-Modul Klassen](../../atl/atl-module-classes.md) .

```
HINSTANCE GetResourceInstance() throw();
```

### <a name="return-value"></a>Rückgabewert

Eine HINSTANCE.

### <a name="remarks"></a>Hinweise

Gibt den [m_hInstResource](#m_hinstresource) Datenmember zurück.

##  <a name="gettypelibinstance"></a>CComModule:: gettypelibinstance

Ab ATL 7,0 ist `CComModule` veraltet: Weitere Informationen finden Sie unter [ATL-Modul Klassen](../../atl/atl-module-classes.md) .

```
HINSTANCE GetTypeLibInstance() const throw();
```

### <a name="return-value"></a>Rückgabewert

Eine HINSTANCE.

### <a name="remarks"></a>Hinweise

Gibt den [m_hInstTypeLib](#m_hinsttypelib) Datenmember zurück.

##  <a name="init"></a>CComModule:: init

Ab ATL 7,0 ist `CComModule` veraltet: Weitere Informationen finden Sie unter [ATL-Modul Klassen](../../atl/atl-module-classes.md) .

```
HRESULT Init(
    _ATL_OBJMAP_ENTRY* p,
    HINSTANCE h,
    const GUID* plibid = NULL) throw();
```

### <a name="parameters"></a>Parameter

*p*<br/>
in Ein Zeiger auf ein Array von Objekt Zuordnungs Einträgen.

*h*<br/>
in Die an `DLLMain` oder `WinMain`über gegebene HINSTANCE.

*plibid*<br/>
in Ein Zeiger auf die LIBID der Typbibliothek, die dem Projekt zugeordnet ist.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standardwert.

### <a name="remarks"></a>Hinweise

Initialisiert alle Datenmember.

##  <a name="m_csobjmap"></a>CComModule:: m_csObjMap

Ab ATL 7,0 ist `CComModule` veraltet: Weitere Informationen finden Sie unter [ATL-Modul Klassen](../../atl/atl-module-classes.md) .

```
CRITICAL_SECTION m_csObjMap;
```

### <a name="remarks"></a>Hinweise

Gewährleistet den synchronisierten Zugriff auf die Objekt Zuordnung.

##  <a name="m_cstypeinfoholder"></a>CComModule:: m_csTypeInfoHolder

Ab ATL 7,0 ist `CComModule` veraltet: Weitere Informationen finden Sie unter [ATL-Modul Klassen](../../atl/atl-module-classes.md) .

```
CRITICAL_SECTION m_csTypeInfoHolder;
```

### <a name="remarks"></a>Hinweise

Gewährleistet den synchronisierten Zugriff auf die Typbibliothek.

##  <a name="m_cswindowcreate"></a>CComModule:: m_csWindowCreate

Ab ATL 7,0 ist `CComModule` veraltet: Weitere Informationen finden Sie unter [ATL-Modul Klassen](../../atl/atl-module-classes.md) .

```
CRITICAL_SECTION m_csWindowCreate;
```

### <a name="remarks"></a>Hinweise

Gewährleistet den synchronisierten Zugriff auf Fenster Klassen Informationen und statische Daten, die während der Fenster Erstellung verwendet werden.

##  <a name="m_hinst"></a>CComModule:: m_hInst

Ab ATL 7,0 ist `CComModule` veraltet: Weitere Informationen finden Sie unter [ATL-Modul Klassen](../../atl/atl-module-classes.md) .

```
HINSTANCE m_hInst;
```

### <a name="remarks"></a>Hinweise

Enthält das Handle für die Modul Instanz.

Die [Init](#init) -Methode legt `m_hInst` auf das Handle fest, das an `DLLMain` oder `WinMain`übertragen wird.

##  <a name="m_hinstresource"></a>CComModule:: m_hInstResource

Ab ATL 7,0 ist `CComModule` veraltet: Weitere Informationen finden Sie unter [ATL-Modul Klassen](../../atl/atl-module-classes.md) .

```
HINSTANCE m_hInstResource;
```

### <a name="remarks"></a>Hinweise

Standardmäßig enthält das Handle für die Modul Instanz.

Die [Init](#init) -Methode legt `m_hInstResource` auf das Handle fest, das an `DLLMain` oder `WinMain`übertragen wird. Sie können `m_hInstResource` explizit auf das Handle einer Ressource festlegen.

Die [getresourceinstance](#getresourceinstance) -Methode gibt das in `m_hInstResource`gespeicherte Handle zurück.

##  <a name="m_hinsttypelib"></a>CComModule:: m_hInstTypeLib

Ab ATL 7,0 ist `CComModule` veraltet: Weitere Informationen finden Sie unter [ATL-Modul Klassen](../../atl/atl-module-classes.md) .

```
HINSTANCE m_hInstTypeLib;
```

### <a name="remarks"></a>Hinweise

Standardmäßig enthält das Handle für die Modul Instanz.

Die [Init](#init) -Methode legt `m_hInstTypeLib` auf das Handle fest, das an `DLLMain` oder `WinMain`übertragen wird. Sie können `m_hInstTypeLib` explizit auf das Handle einer Typbibliothek festlegen.

Die [gettypelibinstance](#gettypelibinstance) -Methode gibt das in `m_hInstTypeLib`gespeicherte Handle zurück.

##  <a name="m_pobjmap"></a>CComModule:: m_pObjMap

Ab ATL 7,0 ist `CComModule` veraltet: Weitere Informationen finden Sie unter [ATL-Modul Klassen](../../atl/atl-module-classes.md) .

```
_ATL_OBJMAP_ENTRY* m_pObjMap;
```

### <a name="remarks"></a>Hinweise

Verweist auf die Objekt Zuordnung, die von der Modul Instanz verwaltet wird.

##  <a name="registerclasshelper"></a>CComModule:: registerclasshelper

Ab ATL 7,0 ist `CComModule` veraltet: Weitere Informationen finden Sie unter [ATL-Modul Klassen](../../atl/atl-module-classes.md) .

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
in Die CLSID des zu registrierenden Objekts.

*lpszProgID*<br/>
in Die ProgID, die dem-Objekt zugeordnet ist.

*lpszVerIndProgID*<br/>
in Die Versions unabhängige ProgID, die dem-Objekt zugeordnet ist.

*nDescID*<br/>
in Der Bezeichner einer Zeichen folgen Ressource für die Beschreibung des Objekts.

*dwFlags*<br/>
in Gibt das Threading Modell an, das in die Registrierung eingegeben werden soll. Mögliche Werte sind THREADFLAGS_APARTMENT, THREADFLAGS_BOTH oder autprxflag.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standardwert.

### <a name="remarks"></a>Hinweise

Gibt die Standard-Klassen Registrierung eines Objekts in der Systemregistrierung ein.

Die [updateregistryclass](#updateregistryclass) -Methode ruft `RegisterClassHelper`auf.

##  <a name="registerclassobjects"></a>CComModule:: RegisterClassObjects

Ab ATL 7,0 ist `CComModule` veraltet: Weitere Informationen finden Sie unter [ATL-Modul Klassen](../../atl/atl-module-classes.md) .

```
HRESULT RegisterClassObjects(DWORD dwClsContext, DWORD dwFlags) throw();
```

### <a name="parameters"></a>Parameter

*dwClsContext*<br/>
in Gibt den Kontext an, in dem das Klassenobjekt ausgeführt werden soll. Mögliche Werte sind CLSCTX_INPROC_SERVER, CLSCTX_INPROC_HANDLER oder CLSCTX_LOCAL_SERVER. Eine Beschreibung dieser Werte finden Sie unter [CLSCTX](/windows/win32/api/wtypesbase/ne-wtypesbase-clsctx) in der Windows SDK.

*dwFlags*<br/>
in Bestimmt die Verbindungstypen für das-Klassenobjekt. Mögliche Werte sind REGCLS_SINGLEUSE, REGCLS_MULTIPLEUSE oder REGCLS_MULTI_SEPARATE. Eine Beschreibung dieser Werte finden Sie unter [REGCLS](/windows/win32/api/combaseapi/ne-combaseapi-regcls) in der Windows SDK.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standardwert.

### <a name="remarks"></a>Hinweise

Registriert ein exe-Klassenobjekt bei OLE, damit andere Anwendungen eine Verbindung damit herstellen können. Diese Methode ist nur für exe-Datei verfügbar.

##  <a name="registerserver"></a>CComModule:: RegisterServer

Ab ATL 7,0 ist `CComModule` veraltet: Weitere Informationen finden Sie unter [ATL-Modul Klassen](../../atl/atl-module-classes.md) .

```
HRESULT RegisterServer(
    BOOL bRegTypeLib = FALSE,
    const CLSID* pCLSID = NULL) throw();
```

### <a name="parameters"></a>Parameter

*bRegTypeLib*<br/>
in Gibt an, ob die Typbibliothek registriert wird. Der Standardwert lautet "FALSE".

*pCLSID*<br/>
in Verweist auf die CLSID des zu registrierenden Objekts. Wenn der Wert NULL (der Standardwert) ist, werden alle Objekte in der Objekt Zuordnung registriert.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standardwert.

### <a name="remarks"></a>Hinweise

Aktualisiert abhängig vom *pclsid* -Parameter die Systemregistrierung für ein einzelnes Klassenobjekt oder für alle Objekte in der Objekt Zuordnung.

Wenn " *bregtypelib* " auf "true" gesetzt ist, werden die Typbibliotheks Informationen ebenfalls aktualisiert.

Informationen dazu, wie Sie der Objekt Zuordnung einen Eintrag hinzufügen, finden Sie unter [OBJECT_ENTRY_AUTO](object-map-macros.md#object_entry_auto) .

`RegisterServer` wird automatisch durch `DLLRegisterServer` für eine DLL oder durch `WinMain` für eine exe aufgerufen, die mit der `/RegServer`-Befehlszeilenoption ausgeführt wird.

##  <a name="registertypelib"></a>CComModule:: RegisterTypeLib

Ab ATL 7,0 ist `CComModule` veraltet: Weitere Informationen finden Sie unter [ATL-Modul Klassen](../../atl/atl-module-classes.md) .

```
HRESULT RegisterTypeLib() throw();
HRESULT RegisterTypeLib(LPCTSTR lpszIndex) throw();
```

### <a name="parameters"></a>Parameter

*lpszIndex*<br/>
in Zeichenfolge im Format `"\\N"`, wobei `N` der ganzzahlige Index der TypeLib-Ressource ist.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standardwert.

### <a name="remarks"></a>Hinweise

Fügt der Systemregistrierung Informationen zu einer Typbibliothek hinzu.

Wenn die Modul Instanz mehrere Typbibliotheken enthält, verwenden Sie die zweite Version dieser Methode, um anzugeben, welche Typbibliothek verwendet werden soll.

##  <a name="revokeclassobjects"></a>CComModule:: revokeclassobjects

Ab ATL 7,0 ist `CComModule` veraltet: Weitere Informationen finden Sie unter [ATL-Modul Klassen](../../atl/atl-module-classes.md) .

```
HRESULT RevokeClassObjects() throw();
```

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standardwert.

### <a name="remarks"></a>Hinweise

Entfernt das-Klassenobjekt. Diese Methode ist nur für exe-Datei verfügbar.

##  <a name="term"></a>CComModule:: Term

Ab ATL 7,0 ist `CComModule` veraltet: Weitere Informationen finden Sie unter [ATL-Modul Klassen](../../atl/atl-module-classes.md) .

```
void Term() throw();
```

### <a name="remarks"></a>Hinweise

Gibt alle Datenmember frei.

##  <a name="unregisterclasshelper"></a>CComModule:: unregisterclasshelper

Ab ATL 7,0 ist `CComModule` veraltet: Weitere Informationen finden Sie unter [ATL-Modul Klassen](../../atl/atl-module-classes.md) .

```
ATL_DEPRECATED HRESULT UnregisterClassHelper(
    const CLSID& clsid,
    LPCTSTR lpszProgID,
    LPCTSTR lpszVerIndProgID);
```

### <a name="parameters"></a>Parameter

*clsid*<br/>
in Die CLSID des Objekts, dessen Registrierung aufgehoben werden soll.

*lpszProgID*<br/>
in Die ProgID, die dem-Objekt zugeordnet ist.

*lpszVerIndProgID*<br/>
in Die Versions unabhängige ProgID, die dem-Objekt zugeordnet ist.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standardwert.

### <a name="remarks"></a>Hinweise

Entfernt die standardmäßige Klassen Registrierung eines Objekts aus der Systemregistrierung.

Die [updateregistryclass](#updateregistryclass) -Methode ruft `UnregisterClassHelper`auf.

##  <a name="unregisterserver"></a>CComModule:: unregisterserver

Ab ATL 7,0 ist `CComModule` veraltet: Weitere Informationen finden Sie unter [ATL-Modul Klassen](../../atl/atl-module-classes.md) .

```
HRESULT UnregisterServer(const CLSID* pCLSID = NULL) throw ();
inline HRESULT UnregisterServer(BOOL bUnRegTypeLib, const CLSID* pCLSID = NULL) throw ();
```

### <a name="parameters"></a>Parameter

*bUnRegTypeLib*<br/>
TRUE gibt an, dass die Registrierung der Typbibliothek ebenfalls aufgehoben wird.

*pCLSID*<br/>
Verweist auf die CLSID des Objekts, dessen Registrierung aufgehoben werden soll. Wenn der Wert NULL (der Standardwert) ist, wird die Registrierung aller Objekte in der Objekt Zuordnung aufgehoben.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standardwert.

### <a name="remarks"></a>Hinweise

In Abhängigkeit vom *pclsid* -Parameter wird die Registrierung eines einzelnen Klassen Objekts oder aller Objekte in der Objekt Zuordnung aufgehoben.

`UnregisterServer` wird automatisch durch `DLLUnregisterServer` für eine DLL oder durch `WinMain` für eine exe aufgerufen, die mit der `/UnregServer`-Befehlszeilenoption ausgeführt wird.

Informationen dazu, wie Sie der Objekt Zuordnung einen Eintrag hinzufügen, finden Sie unter [OBJECT_ENTRY_AUTO](object-map-macros.md#object_entry_auto) .

##  <a name="updateregistryclass"></a>CComModule:: updateregistryclass

Ab ATL 7,0 ist `CComModule` veraltet: Weitere Informationen finden Sie unter [ATL-Modul Klassen](../../atl/atl-module-classes.md) .

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
Die CLSID des Objekts, das registriert oder dessen Registrierung aufgehoben werden soll.

*lpszProgID*<br/>
Die ProgID, die dem-Objekt zugeordnet ist.

*lpszVerIndProgID*<br/>
Die Versions unabhängige ProgID, die dem-Objekt zugeordnet ist.

*nDescID*<br/>
Der Bezeichner der Zeichen folgen Ressource für die Beschreibung des Objekts.

*szDesc*<br/>
Eine Zeichenfolge, die die Beschreibung des Objekts enthält.

*dwFlags*<br/>
Gibt das Threading Modell an, das in die Registrierung eingegeben werden soll. Mögliche Werte sind THREADFLAGS_APARTMENT, THREADFLAGS_BOTH oder autprxflag.

*bRegister*<br/>
Gibt an, ob das Objekt registriert werden soll.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standardwert.

### <a name="remarks"></a>Hinweise

Wenn *bregister* den Wert true hat, gibt diese Methode die Standardklassen Registrierung des Objekts in der Systemregistrierung ein.

Wenn *bregister* den Wert false hat, wird die Registrierung des Objekts entfernt.

Abhängig vom Wert von *bregister*ruft `UpdateRegistryClass` entweder [registerclasshelper](#registerclasshelper) oder [unregisterclasshelper](#unregisterclasshelper)auf.

Wenn Sie das [DECLARE_REGISTRY](registry-macros.md#declare_registry) -Makro angeben, wird `UpdateRegistryClass` automatisch aufgerufen, wenn die Objekt Zuordnung verarbeitet wird.

##  <a name="updateregistryfromresourced"></a>CComModule:: UpdateRegistryFromResource

Ab ATL 7,0 ist `CComModule` veraltet: Weitere Informationen finden Sie unter [ATL-Modul Klassen](../../atl/atl-module-classes.md) .

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
in Ein Ressourcen Name.

*nResID*<br/>
in Eine Ressourcen-ID.

*bRegister*<br/>
in Gibt an, ob das Objekt registriert werden soll.

*pmapentries*<br/>
in Ein Zeiger auf die Ersatz Zuordnung, die Werte speichert, die den ersetzbaren Parametern des Skripts zugeordnet sind. ATL verwendet automatisch `%MODULE%`. Informationen zur Verwendung zusätzlicher ersetzbarer Parameter finden Sie in den hinweisen. Andernfalls verwenden Sie den Standardwert NULL.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standardwert.

### <a name="remarks"></a>Hinweise

Führt das Skript aus, das in der durch *lpszres* oder *nresid*angegebenen Ressource enthalten ist.

Wenn *bregister* den Wert true hat, registriert diese Methode das Objekt in der Systemregistrierung. Andernfalls wird die Registrierung des Objekts aufgehoben.

Wenn Sie die [DECLARE_REGISTRY_RESOURCE](registry-macros.md#declare_registry_resource) oder [DECLARE_REGISTRY_RESOURCEID](registry-macros.md#declare_registry_resourceid) -Makro angeben, werden `UpdateRegistryFromResourceD` automatisch aufgerufen, wenn die Objekt Zuordnung verarbeitet wird.

> [!NOTE]
>  Wenn Sie Ersatzwerte zur Laufzeit ersetzen möchten, geben Sie nicht die DECLARE_REGISTRY_RESOURCE oder DECLARE_REGISTRY_RESOURCEID-Makro an. Erstellen Sie stattdessen ein Array von `_ATL_REGMAP_ENTRIES` Strukturen, wobei jeder Eintrag einen Variablen Platzhalter enthält, der mit einem Wert gekoppelt ist, um den Platzhalter zur Laufzeit zu ersetzen. Anschließend wird `UpdateRegistryFromResourceD`aufgerufen, wobei das Array für den *pmapentries* -Parameter übergeben wird. Dadurch werden alle Ersetzungs Werte in den `_ATL_REGMAP_ENTRIES` Strukturen der Registrierungskarte der Registrierungsstelle hinzugefügt.

> [!NOTE]
>  Informationen zur statischen Verknüpfung mit der ATL-Registrierungs Komponente (Registrierungs Komponente, Registrierungs Komponente) finden Sie unter [updateregistryfromresources](#updateregistryfromresources).

Weitere Informationen zu ersetzbaren Parametern und zur Skripterstellung finden Sie im Artikel [zur ATL-Registrierungs Komponente (Registrierungs Komponente, Registrierungs Komponente)](../../atl/atl-registry-component-registrar.md).

##  <a name="updateregistryfromresources"></a>CComModule:: updateregistryfromresources

Ab ATL 7,0 ist `CComModule` veraltet: Weitere Informationen finden Sie unter [ATL-Modul Klassen](../../atl/atl-module-classes.md) .

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
in Ein Ressourcen Name.

*nResID*<br/>
in Eine Ressourcen-ID.

*bRegister*<br/>
in Gibt an, ob das Ressourcen Skript registriert werden soll.

*pmapentries*<br/>
in Ein Zeiger auf die Ersatz Zuordnung, die Werte speichert, die den ersetzbaren Parametern des Skripts zugeordnet sind. ATL verwendet automatisch `%MODULE%`. Informationen zur Verwendung zusätzlicher ersetzbarer Parameter finden Sie in den hinweisen. Andernfalls verwenden Sie den Standardwert NULL.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standardwert.

### <a name="remarks"></a>Hinweise

Ähnlich wie bei [UpdateRegistryFromResource](#updateregistryfromresourced) mit Ausnahme von `UpdateRegistryFromResourceS` erstellt einen statischen Link zur ATL-Registrierungs Komponente (Registrierungs Komponente, Registrierungs Komponente).

`UpdateRegistryFromResourceS` werden automatisch aufgerufen, wenn die Objekt Zuordnung verarbeitet wird, sofern Sie `#define _ATL_STATIC_REGISTRY` der Datei " *PCH. h* " (*stdafx. h* in Visual Studio 2017 und früher) hinzufügen.

> [!NOTE]
>  Wenn Sie Ersatzwerte zur Laufzeit ersetzen möchten, geben Sie nicht die [DECLARE_REGISTRY_RESOURCE](registry-macros.md#declare_registry_resource) oder [DECLARE_REGISTRY_RESOURCEID](registry-macros.md#declare_registry_resourceid) -Makro an. Erstellen Sie stattdessen ein Array von `_ATL_REGMAP_ENTRIES` Strukturen, wobei jeder Eintrag einen Variablen Platzhalter enthält, der mit einem Wert gekoppelt ist, um den Platzhalter zur Laufzeit zu ersetzen. Anschließend wird `UpdateRegistryFromResourceS`aufgerufen, wobei das Array für den *pmapentries* -Parameter übergeben wird. Dadurch werden alle Ersetzungs Werte in den `_ATL_REGMAP_ENTRIES` Strukturen der Registrierungskarte der Registrierungsstelle hinzugefügt.

Weitere Informationen zu ersetzbaren Parametern und zur Skripterstellung finden Sie im Artikel [zur ATL-Registrierungs Komponente (Registrierungs Komponente, Registrierungs Komponente)](../../atl/atl-registry-component-registrar.md).

## <a name="see-also"></a>Siehe auch

[Klassen Übersicht](../../atl/atl-class-overview.md)
