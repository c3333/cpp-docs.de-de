---
title: CAtlModule-Klasse
ms.date: 11/04/2016
f1_keywords:
- CAtlModule
- ATLBASE/ATL::CAtlModule
- ATLBASE/ATL::CAtlModule::CAtlModule
- ATLBASE/ATL::CAtlModule::AddCommonRGSReplacements
- ATLBASE/ATL::CAtlModule::AddTermFunc
- ATLBASE/ATL::CAtlModule::GetGITPtr
- ATLBASE/ATL::CAtlModule::GetLockCount
- ATLBASE/ATL::CAtlModule::Lock
- ATLBASE/ATL::CAtlModule::Term
- ATLBASE/ATL::CAtlModule::Unlock
- ATLBASE/ATL::CAtlModule::UpdateRegistryFromResourceD
- ATLBASE/ATL::CAtlModule::UpdateRegistryFromResourceDHelper
- ATLBASE/ATL::CAtlModule::UpdateRegistryFromResourceS
- ATLBASE/ATL::CAtlModule::m_libid
- ATLBASE/ATL::CAtlModule::m_pGIT
helpviewer_keywords:
- CAtlModule class
ms.assetid: 63fe02f1-4c4b-4e7c-ae97-7ad7b4252415
ms.openlocfilehash: cfc11a95a8d5d9354279f4c71698a6bc35c7aca7
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81748618"
---
# <a name="catlmodule-class"></a>CAtlModule-Klasse

Diese Klasse stellt Methoden bereit, die von mehreren ATL-Modulklassen verwendet werden.

## <a name="syntax"></a>Syntax

```
class ATL_NO_VTABLE CAtlModule : public _ATL_MODULE
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAtlModule::CAtlModule](#catlmodule)|Der Konstruktor.|
|[CAtlModule::-CAtlModule](#dtor)|Der Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAtlModule::AddCommonRGSReplacements](#addcommonrgsreplacements)|Überschreiben Sie diese Methode, um der AtL Registry Component (Registrar)-Ersatzzuordnung Parameter hinzuzufügen.|
|[CAtlModule::AddTermFunc](#addtermfunc)|Fügt eine neue Funktion hinzu, die aufgerufen werden soll, wenn das Modul beendet wird.|
|[CAtlModule::GetGITPtr](#getgitptr)|Gibt den globalen Schnittstellenzeiger zurück.|
|[CAtlModule::GetLockCount](#getlockcount)|Gibt die Sperranzahl zurück.|
|[CAtlModule::Lock](#lock)|Erhöht die Sperranzahl.|
|[CAtlModule::Term](#term)|Gibt alle Datenmember frei.|
|[CAtlModule::Entsperren](#unlock)|Verringert die Sperrenanzahl.|
|[CAtlModule::UpdateRegistryFromResourceD](#updateregistryfromresourced)|Führt das Skript aus, das in einer angegebenen Ressource enthalten ist, um ein Objekt zu registrieren oder aufzuheben.|
|[CAtlModule::UpdateRegistryFromResourceDHelper](#updateregistryfromresourcedhelper)|Diese Methode wird `UpdateRegistryFromResourceD` aufgerufen, um die Registrierungsaktualisierung auszuführen.|
|[CAtlModule::UpdateRegistryFromResourceS](#updateregistryfromresources)|Führt das Skript aus, das in einer angegebenen Ressource enthalten ist, um ein Objekt zu registrieren oder aufzuheben. Diese Methode verknüpft statisch mit der ATL-Registrierungskomponente.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAtlModule::m_libid](#m_libid)|Enthält die GUID des aktuellen Moduls.|
|[CAtlModule::m_pGIT](#m_pgit)|Zeiger auf die globale Schnittstellentabelle.|

## <a name="remarks"></a>Bemerkungen

Diese Klasse wird von [cAtlDllModuleT Class](../../atl/reference/catldllmodulet-class.md), [CAtlExeModuleT Class](../../atl/reference/catlexemodulet-class.md)und [CAtlServiceModuleT Class](../../atl/reference/catlservicemodulet-class.md) verwendet, um Unterstützung für DLL-Anwendungen, EXE-Anwendungen und Windows-Dienste bereitzustellen.

Weitere Informationen zu Modulen in ATL finden Sie unter [ATL-Modulklassen](../../atl/atl-module-classes.md).

Diese Klasse ersetzt die veraltete [CComModule-Klasse,](../../atl/reference/ccommodule-class.md) die in früheren Versionen von ATL verwendet wurde.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[_ATL_MODULE](atl-typedefs.md#_atl_module)

`CAtlModule`

## <a name="requirements"></a>Requirements (Anforderungen)

**Kopfzeile:** atlbase.h

## <a name="catlmoduleaddcommonrgsreplacements"></a><a name="addcommonrgsreplacements"></a>CAtlModule::AddCommonRGSReplacements

Überschreiben Sie diese Methode, um der AtL Registry Component (Registrar)-Ersatzzuordnung Parameter hinzuzufügen.

```
virtual HRESULT AddCommonRGSReplacements(IRegistrarBase* /* pRegistrar*/) throw() = 0;
```

### <a name="parameters"></a>Parameter

*pRegistrar*<br/>
Reserviert.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

### <a name="remarks"></a>Bemerkungen

Ersetzbare Parameter ermöglichen es dem Client eines Registrars, Laufzeitdaten anzugeben. Zu diesem Thema verwaltet der Registrar eine Ersatzzuordnung, in die er die Werte eingibt, die den austauschbaren Parametern in Ihrem Skript zugeordnet sind. Der Registrar macht diese Einträge zur Laufzeit.

Weitere Informationen finden Sie im Thema [Verwenden ersetzbarer Parameter (Präprozessor des Registrars).](../../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md)

## <a name="catlmoduleaddtermfunc"></a><a name="addtermfunc"></a>CAtlModule::AddTermFunc

Fügt eine neue Funktion hinzu, die aufgerufen werden soll, wenn das Modul beendet wird.

```
HRESULT AddTermFunc(_ATL_TERMFUNC* pFunc, DWORD_PTR dw) throw();
```

### <a name="parameters"></a>Parameter

*pFunc*<br/>
Zeiger auf die hinzuzufügende Funktion.

*dw*<br/>
Benutzerdefinierte Daten, die an die Funktion übergeben werden.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

## <a name="catlmodulecatlmodule"></a><a name="catlmodule"></a>CAtlModule::CAtlModule

Der Konstruktor.

```
CAtlModule() throw();
```

### <a name="remarks"></a>Bemerkungen

Initialisiert Datenmember und initiiert einen kritischen Abschnitt um den Thread des Moduls.

## <a name="catlmodulecatlmodule"></a><a name="dtor"></a>CAtlModule::-CAtlModule

Der Destruktor.

```
~CAtlModule() throw();
```

### <a name="remarks"></a>Bemerkungen

Gibt alle Datenmember frei.

## <a name="catlmodulegetgitptr"></a><a name="getgitptr"></a>CAtlModule::GetGITPtr

Ruft einen Zeiger auf die globale Schnittstellentabelle ab.

```
virtual HRESULT GetGITPtr(IGlobalInterfaceTable** ppGIT) throw();
```

### <a name="parameters"></a>Parameter

*ppGIT*<br/>
Zeiger auf die Variable, die den Zeiger auf die globale Schnittstellentabelle empfängt.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK auf Erfolg oder einen Fehlercode bei einem Fehler zurück. E_POINTER wird zurückgegeben, wenn *ppGIT* gleich NULL ist.

### <a name="remarks"></a>Bemerkungen

Wenn das Global Interface Table-Objekt nicht vorhanden ist, wird es erstellt, und seine Adresse wird in der Membervariablen [CAtlModule::m_pGIT](#m_pgit)gespeichert.

In Debugbuilds tritt ein Assertionsfehler auf, wenn *ppGIT* gleich NULL ist oder wenn der Zeiger globale Schnittstellentabelle nicht abgerufen werden kann.

Informationen zur globalen Schnittstellentabelle finden Sie unter [IGlobalInterfaceTable.](/windows/win32/api/objidl/nn-objidl-iglobalinterfacetable)

## <a name="catlmodulegetlockcount"></a><a name="getlockcount"></a>CAtlModule::GetLockCount

Gibt die Sperranzahl zurück.

```
virtual LONG GetLockCount() throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt die Sperranzahl zurück. Dieser Wert kann für die Diagnose und das Debuggen nützlich sein.

## <a name="catlmodulelock"></a><a name="lock"></a>CAtlModule::Lock

Erhöht die Sperranzahl.

```
virtual LONG Lock() throw();
```

### <a name="return-value"></a>Rückgabewert

Erhöht die Sperranzahl und gibt den aktualisierten Wert zurück. Dieser Wert kann für die Diagnose und das Debuggen nützlich sein.

## <a name="catlmodulem_libid"></a><a name="m_libid"></a>CAtlModule::m_libid

Enthält die GUID des aktuellen Moduls.

```
static GUID m_libid;
```

## <a name="catlmodulem_pgit"></a><a name="m_pgit"></a>CAtlModule::m_pGIT

Zeiger auf die globale Schnittstellentabelle.

```
IGlobalInterfaceTable* m_pGIT;
```

## <a name="catlmoduleterm"></a><a name="term"></a>CAtlModule::Term

Gibt alle Datenmember frei.

```cpp
void Term() throw();
```

### <a name="remarks"></a>Bemerkungen

Gibt alle Datenmember frei. Diese Methode wird vom Destruktor aufgerufen.

## <a name="catlmoduleunlock"></a><a name="unlock"></a>CAtlModule::Entsperren

Verringert die Sperrenanzahl.

```
virtual LONG Unlock() throw();
```

### <a name="return-value"></a>Rückgabewert

Dekrementiert die Sperranzahl und gibt den aktualisierten Wert zurück. Dieser Wert kann für die Diagnose und das Debuggen nützlich sein.

## <a name="catlmoduleupdateregistryfromresourced"></a><a name="updateregistryfromresourced"></a>CAtlModule::UpdateRegistryFromResourceD

Führt das Skript aus, das in einer angegebenen Ressource enthalten ist, um ein Objekt zu registrieren oder aufzuheben.

```
HRESULT WINAPI UpdateRegistryFromResourceD(
    UINT nResID,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw();

HRESULT WINAPI UpdateRegistryFromResourceD(
    LPCTSTR lpszRes,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw();
```

### <a name="parameters"></a>Parameter

*lpszRes*<br/>
Ein Ressourcenname.

*nResID*<br/>
Eine Ressourcen-ID.

*bRegister*<br/>
TRUE, wenn das Objekt registriert werden soll; FALSE sonst.

*pMapEntries*<br/>
Ein Zeiger auf die Ersatzzuordnung, in der Werte gespeichert werden, die den austauschbaren Parametern des Skripts zugeordnet sind. ATL verwendet automatisch %MODULE%. Weitere austauschbare Parameter finden Sie unter [CAtlModule::AddCommonRGSReplacements](#addcommonrgsreplacements). Andernfalls verwenden Sie den NULL-Standardwert.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

### <a name="remarks"></a>Bemerkungen

Führt das Skript aus, das in der von *lpszRes oder nResID*angegebenen Ressource enthalten ist. Wenn *bRegister* TRUE ist, registriert diese Methode das Objekt in der Systemregistrierung. Andernfalls wird das Objekt aus der Registrierung entfernt.

Informationen zum statischen Verknüpfen mit der ATL-Registrierungskomponente (Registrar) finden Sie unter [CAtlModule::UpdateRegistryFromResourceS](#updateregistryfromresources).

Diese Methode ruft [CAtlModule::UpdateRegistryFromResourceDHelper](#updateregistryfromresourcedhelper) und [IRegistrar::ResourceUnregister](iregistrar-class.md#resourceunregister)auf.

## <a name="catlmoduleupdateregistryfromresourcedhelper"></a><a name="updateregistryfromresourcedhelper"></a>CAtlModule::UpdateRegistryFromResourceDHelper

Diese Methode wird `UpdateRegistryFromResourceD` aufgerufen, um die Registrierungsaktualisierung auszuführen.

```
inline HRESULT WINAPI UpdateRegistryFromResourceDHelper(
    LPCOLESTR lpszRes,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw();
```

### <a name="parameters"></a>Parameter

*lpszRes*<br/>
Ein Ressourcenname.

*bRegister*<br/>
Gibt an, ob das Objekt registriert werden soll.

*pMapEntries*<br/>
Ein Zeiger auf die Ersatzzuordnung, in der Werte gespeichert werden, die den austauschbaren Parametern des Skripts zugeordnet sind. ATL verwendet automatisch %MODULE%. Weitere austauschbare Parameter finden Sie unter [CAtlModule::AddCommonRGSReplacements](#addcommonrgsreplacements). Andernfalls verwenden Sie den NULL-Standardwert.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

### <a name="remarks"></a>Bemerkungen

Diese Methode stellt die Implementierung von [CAtlModule::UpdateRegistryFromResourceD](#updateregistryfromresourced)bereit.

## <a name="catlmoduleupdateregistryfromresources"></a><a name="updateregistryfromresources"></a>CAtlModule::UpdateRegistryFromResourceS

Führt das Skript aus, das in einer angegebenen Ressource enthalten ist, um ein Objekt zu registrieren oder aufzuheben. Diese Methode verknüpft statisch mit der ATL-Registrierungskomponente.

```
HRESULT WINAPI UpdateRegistryFromResourceS(
    UINT nResID,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw();

HRESULT WINAPI UpdateRegistryFromResourceS(
    LPCTSTR lpszRes,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw();
```

### <a name="parameters"></a>Parameter

*nResID*<br/>
Eine Ressourcen-ID.

*lpszRes*<br/>
Ein Ressourcenname.

*bRegister*<br/>
Gibt an, ob das Ressourcenskript registriert werden soll.

*pMapEntries*<br/>
Ein Zeiger auf die Ersatzzuordnung, in der Werte gespeichert werden, die den austauschbaren Parametern des Skripts zugeordnet sind. ATL verwendet automatisch %MODULE%. Weitere austauschbare Parameter finden Sie unter [CAtlModule::AddCommonRGSReplacements](#addcommonrgsreplacements). Andernfalls verwenden Sie den NULL-Standardwert.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

### <a name="remarks"></a>Bemerkungen

Ähnlich wie [CAtlModule::UpdateRegistryFromResourceD](#updateregistryfromresourced) außer `CAtlModule::UpdateRegistryFromResourceS` erstellt eine statische Verknüpfung mit der ATL-Registrierungskomponente (Registrar).

## <a name="see-also"></a>Weitere Informationen

[_ATL_MODULE](atl-typedefs.md#_atl_module)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)<br/>
[Modulklassen](../../atl/atl-module-classes.md)<br/>
[Registrierungskomponente (Registrar)](../../atl/atl-registry-component-registrar.md)
