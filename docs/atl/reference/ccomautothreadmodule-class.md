---
title: CComAutoThreadModule-Klasse
ms.date: 11/04/2016
f1_keywords:
- CComAutoThreadModule
- ATLBASE/ATL::CComAutoThreadModule
- ATLBASE/ATL::CreateInstance
- ATLBASE/ATL::GetDefaultThreads
- ATLBASE/ATL::Init
- ATLBASE/ATL::Lock
- ATLBASE/ATL::Unlock
- ATLBASE/ATL::dwThreadID
- ATLBASE/ATL::m_Allocator
- ATLBASE/ATL::m_nThreads
- ATLBASE/ATL::m_pApartments
helpviewer_keywords:
- CComAutoThreadModule class
- apartment model modules
ms.assetid: 13063ea5-a57e-4aac-97d3-227137262811
ms.openlocfilehash: 391354c5672cf15c0286491619a13c6005493cfa
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321063"
---
# <a name="ccomautothreadmodule-class"></a>CComAutoThreadModule-Klasse

Ab ATL 7.0 `CComAutoThreadModule` ist veraltet: siehe [ATL-Modulklassen](../../atl/atl-module-classes.md) für weitere Details.

> [!IMPORTANT]
> Diese Klasse und ihre Member können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

## <a name="syntax"></a>Syntax

```
template <class ThreadAllocator = CComSimpleThreadAllocator>
class CComAutoThreadModule : public CComModule
```

#### <a name="parameters"></a>Parameter

*ThreadAllocator*<br/>
[in] Die Klassenverwaltung threadauswahl. Der Standardwert ist [CComSimpleThreadAllocator](../../atl/reference/ccomsimplethreadallocator-class.md).

## <a name="members"></a>Member

### <a name="methods"></a>Methoden

|||
|-|-|
|[CreateInstance](#createinstance)|Wählt einen Thread aus und erstellt dann ein Objekt in der zugeordneten Wohnung.|
|[GetDefaultThreads](#getdefaultthreads)|(Statisch) Berechnet dynamisch die Anzahl der Threads für das Modul basierend auf der Anzahl der Prozessoren.|
|[Init](#init)|Erstellt die Threads des Moduls.|
|[Sperre](#lock)|Erhöht die Sperranzahl für das Modul und für den aktuellen Thread.|
|[Entsperren](#unlock)|Dekremente die Sperre zählen auf das Modul und auf den aktuellen Thread.|

### <a name="data-members"></a>Datenelemente

### <a name="data-members"></a>Datenelemente

|||
|-|-|
|[dwThreadID](#dwthreadid)|Enthält den Bezeichner des aktuellen Threads.|
|[m_Allocator](#m_allocator)|Verwaltet die Threadauswahl.|
|[m_nThreads](#m_nthreads)|Enthält die Anzahl der Threads im Modul.|
|[m_pApartments](#m_papartments)|Verwaltet die Wohnungen des Moduls.|

## <a name="remarks"></a>Bemerkungen

> [!NOTE]
> Diese Klasse ist veraltet, da sie durch die abgeleiteten Klassen [CAtlAutoThreadModule](../../atl/reference/catlautothreadmodule-class.md) und [CAtlModule](../../atl/reference/catlmodule-class.md) ersetzt wurde. Die folgenden Informationen sind für die Verwendung mit älteren Versionen von ATL bestimmt.

`CComAutoThreadModule`von [CComModule](../../atl/reference/ccommodule-class.md) ableitet, um einen threadgepoolten COM-Server mit Apartmentmodell für EXEs und Windows-Dienste zu implementieren. `CComAutoThreadModule`verwendet [CComApartment,](../../atl/reference/ccomapartment-class.md) um eine Wohnung für jeden Thread im Modul zu verwalten.

Leiten Sie Ihr `CComAutoThreadModule` Modul ab, wenn Sie Objekte in mehreren Wohnungen erstellen möchten. Sie müssen auch [DECLARE_CLASSFACTORY_AUTO_THREAD](aggregation-and-class-factory-macros.md#declare_classfactory_auto_thread) das DECLARE_CLASSFACTORY_AUTO_THREAD-Makros in die Klassendefinition Ihres Objekts aufnehmen, um [CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md) als Klassenfactory anzugeben.

Standardmäßig leitet der ATL COM AppWizard (der ATL-Projekt-Assistent in Visual `CComModule`Studio .NET) Ihr Modul von ab. Um `CComAutoThreadModule`sie zu verwenden, ändern Sie die Klassendefinition. Beispiel:

[!code-cpp[NVC_ATL_AxHost#2](../../atl/codesnippet/cpp/ccomautothreadmodule-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[CAtlModule](../../atl/reference/catlmodule-class.md)

`IAtlAutoThreadModule`

[CAtlModuleT](../../atl/reference/catlmodulet-class.md)

[CAtlAutoThreadModuleT](../../atl/reference/catlautothreadmodulet-class.md)

[CComModule](../../atl/reference/ccommodule-class.md)

`CComAutoThreadModule`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlbase.h

## <a name="ccomautothreadmodulecreateinstance"></a><a name="createinstance"></a>CComAutoThreadModule::CreateInstance

Ab ATL 7.0 `CComAutoThreadModule` ist veraltet: siehe [ATL-Modulklassen](../../atl/atl-module-classes.md) für weitere Details.

```
HRESULT CreateInstance(
    void* pfnCreateInstance,
    REFIID riid,
    void** ppvObj);
```

### <a name="parameters"></a>Parameter

*pfnCreateInstance*<br/>
[in] Ein Zeiger auf eine Erstellerfunktion.

*riid*<br/>
[in] Die IID der angeforderten Schnittstelle.

*ppvObj*<br/>
[out] Ein Zeiger auf den Schnittstellenzeiger, der von *riid*identifiziert wird. Wenn das Objekt diese Schnittstelle nicht unterstützt, wird *ppvObj* auf NULL gesetzt.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

### <a name="remarks"></a>Bemerkungen

Wählt einen Thread aus und erstellt dann ein Objekt in der zugeordneten Wohnung.

## <a name="ccomautothreadmoduledwthreadid"></a><a name="dwthreadid"></a>CComAutoThreadModule::dwThreadID

Ab ATL 7.0 `CComAutoThreadModule` ist veraltet: siehe [ATL-Modulklassen](../../atl/atl-module-classes.md) für weitere Details.

```
DWORD dwThreadID;
```

### <a name="remarks"></a>Bemerkungen

Enthält den Bezeichner des aktuellen Threads.

## <a name="ccomautothreadmodulegetdefaultthreads"></a><a name="getdefaultthreads"></a>CComAutoThreadModule::GetDefaultThreads

Ab ATL 7.0 `CComAutoThreadModule` ist veraltet: siehe [ATL-Modulklassen](../../atl/atl-module-classes.md) für weitere Details.

```
static int GetDefaultThreads();
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Threads, die im EXE-Modul erstellt werden sollen.

### <a name="remarks"></a>Bemerkungen

Diese statische Funktion berechnet dynamisch die maximale Anzahl von Threads für das EXE-Modul, basierend auf der Anzahl der Prozessoren. Standardmäßig wird dieser Rückgabewert an die [Init-Methode](#init) übergeben, um die Threads zu erstellen.

## <a name="ccomautothreadmoduleinit"></a><a name="init"></a>CComAutoThreadModule::Init

Ab ATL 7.0 `CComAutoThreadModule` ist veraltet: siehe [ATL-Modulklassen](../../atl/atl-module-classes.md) für weitere Details.

```
HRESULT Init(
    _ATL_OBJMAP_ENTRY* p,
    HINSTANCE h,
    const GUID* plibid = NULL,
    int nThreads = GetDefaultThreads());
```

### <a name="parameters"></a>Parameter

*P*<br/>
[in] Ein Zeiger auf ein Array von Objektzuordnungseinträgen.

*H*<br/>
[in] Die HINSTANCE `DLLMain` an `WinMain`oder übergeben.

*plibid*<br/>
[in] Ein Zeiger auf die LIBID der dem Projekt zugeordneten Typbibliothek.

*nThreads*<br/>
[in] Die Anzahl der zu erstellenden Threads. Standardmäßig ist *nThreads* der von [GetDefaultThreads](#getdefaultthreads)zurückgegebene Wert .

### <a name="remarks"></a>Bemerkungen

Initialisiert Datenmember und erstellt die Anzahl der Threads, die von *nThreads*angegeben werden.

## <a name="ccomautothreadmodulelock"></a><a name="lock"></a>CComAutoThreadModule::Sperren

Ab ATL 7.0 `CComAutoThreadModule` ist veraltet: siehe [ATL-Modulklassen](../../atl/atl-module-classes.md) für weitere Details.

```
LONG Lock();
```

### <a name="return-value"></a>Rückgabewert

Ein Wert, der für Diagnosen oder Tests nützlich sein kann.

### <a name="remarks"></a>Bemerkungen

Führt ein atomares Inkrement für die Sperranzahl für das Modul und für den aktuellen Thread aus. `CComAutoThreadModule`verwendet die Modulsperranzahl, um zu bestimmen, ob Clients auf das Modul zugreifen. Die Sperranzahl für den aktuellen Thread wird für statistische Zwecke verwendet.

## <a name="ccomautothreadmodulem_allocator"></a><a name="m_allocator"></a>CComAutoThreadModule::m_Allocator

Ab ATL 7.0 `CComAutoThreadModule` ist veraltet: siehe [ATL-Modulklassen](../../atl/atl-module-classes.md) für weitere Details.

```
ThreadAllocator  m_Allocator;
```

### <a name="remarks"></a>Bemerkungen

Das Objekt, das die Threadauswahl verwaltet. Standardmäßig ist `ThreadAllocator` der Klassenvorlagenparameter [CComSimpleThreadAllocator](../../atl/reference/ccomsimplethreadallocator-class.md).

## <a name="ccomautothreadmodulem_nthreads"></a><a name="m_nthreads"></a>CComAutoThreadModule::m_nThreads

Ab ATL 7.0 `CComAutoThreadModule` ist veraltet: siehe [ATL-Modulklassen](../../atl/atl-module-classes.md) für weitere Details.

```
int m_nThreads;
```

### <a name="remarks"></a>Bemerkungen

Enthält die Anzahl der Threads im EXE-Modul. Wenn [Init](#init) aufgerufen `m_nThreads` wird, wird auf den *nThreads-Parameterwert* gesetzt. Die zugehörige Wohnung jedes Threads wird von einem [CComApartment-Objekt](../../atl/reference/ccomapartment-class.md) verwaltet.

## <a name="ccomautothreadmodulem_papartments"></a><a name="m_papartments"></a>CComAutoThreadModule::m_pApartments

Ab ATL 7.0 `CComAutoThreadModule` ist veraltet: siehe [ATL-Modulklassen](../../atl/atl-module-classes.md) für weitere Details.

```
CComApartment* m_pApartments;
```

### <a name="remarks"></a>Bemerkungen

Verweist auf ein Array von [CComApartment-Objekten,](../../atl/reference/ccomapartment-class.md) von denen jedes eine Wohnung im Modul verwaltet. Die Anzahl der Elemente im Array [m_nThreads](#m_nthreads) basiert auf dem m_nThreads-Member.

## <a name="ccomautothreadmoduleunlock"></a><a name="unlock"></a>CComAutoThreadModule::Entsperren

Ab ATL 7.0 `CComAutoThreadModule` ist veraltet: siehe [ATL-Modulklassen](../../atl/atl-module-classes.md) für weitere Details.

```
LONG Unlock();
```

### <a name="return-value"></a>Rückgabewert

Ein Wert, der für Diagnosen oder Tests nützlich sein kann.

### <a name="remarks"></a>Bemerkungen

Führt eine atomare Dekrementierung für die Sperranzahl für das Modul und für den aktuellen Thread aus. `CComAutoThreadModule`verwendet die Modulsperranzahl, um zu bestimmen, ob Clients auf das Modul zugreifen. Die Sperranzahl für den aktuellen Thread wird für statistische Zwecke verwendet.

Wenn die Modulsperranzahl Null erreicht, kann das Modul entladen werden.

## <a name="see-also"></a>Siehe auch

[Klassenübersicht](../../atl/atl-class-overview.md)<br/>
[Modulklassen](../../atl/atl-module-classes.md)
