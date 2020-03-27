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
ms.openlocfilehash: 9b0fa685bf9a7de94b158bd62b00161c1b58562d
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2020
ms.locfileid: "79423315"
---
# <a name="ccomautothreadmodule-class"></a>CComAutoThreadModule-Klasse

Ab ATL 7,0 ist `CComAutoThreadModule` veraltet: Weitere Informationen finden Sie unter [ATL-Modul Klassen](../../atl/atl-module-classes.md) .

> [!IMPORTANT]
>  Diese Klasse und ihre Member können in Anwendungen, die im Windows-Runtime ausgeführt werden, nicht verwendet werden.

## <a name="syntax"></a>Syntax

```
template <class ThreadAllocator = CComSimpleThreadAllocator>
class CComAutoThreadModule : public CComModule
```

#### <a name="parameters"></a>Parameter

*ThreadAllocator*<br/>
in Die Klasse, die die Thread Auswahl verwaltet. Der Standardwert ist [ccomsimplethreadzuweisung](../../atl/reference/ccomsimplethreadallocator-class.md).

## <a name="members"></a>Member

### <a name="methods"></a>Methoden

|||
|-|-|
|[CreateInstance](#createinstance)|Wählt einen Thread aus und erstellt dann ein-Objekt im zugeordneten Apartment.|
|[GetDefaultThreads](#getdefaultthreads)|Kum Berechnet dynamisch die Anzahl der Threads für das Modul basierend auf der Anzahl der Prozessoren.|
|[Init](#init)|Erstellt die Threads des Moduls.|
|[Sperre](#lock)|Erhöht die Sperrenanzahl für das Modul und den aktuellen Thread.|
|[Entsperren](#unlock)|Dekremente die Sperrenanzahl für das Modul und den aktuellen Thread.|

### <a name="data-members"></a>Datenmember

### <a name="data-members"></a>Datenmember

|||
|-|-|
|[dwThreadID](#dwthreadid)|Enthält den Bezeichner des aktuellen Threads.|
|[m_Allocator](#m_allocator)|Verwaltet die Thread Auswahl.|
|[m_nThreads](#m_nthreads)|Enthält die Anzahl der Threads im Modul.|
|[m_pApartments](#m_papartments)|Verwaltet die Apartments des Moduls.|

## <a name="remarks"></a>Hinweise

> [!NOTE]
>  Diese Klasse ist veraltet und wurde durch die abgeleiteten Klassen [CAtlAutoThreadModule](../../atl/reference/catlautothreadmodule-class.md) and [CAtlModule](../../atl/reference/catlmodule-class.md)" Die folgenden Informationen sind für die Verwendung mit älteren Versionen von ATL vorgesehen.

`CComAutoThreadModule` von [CComModule](../../atl/reference/ccommodule-class.md) abgeleitet, um einen auf einem Thread zusammengefassten com-Server für EXEs-und Windows-Dienste zu implementieren. `CComAutoThreadModule` verwendet [ccomapartment](../../atl/reference/ccomapartment-class.md) , um ein Apartment für jeden Thread im Modul zu verwalten.

Leiten Sie das Modul von `CComAutoThreadModule` ab, wenn Sie Objekte in mehreren Apartments erstellen möchten. Sie müssen auch das [DECLARE_CLASSFACTORY_AUTO_THREAD](aggregation-and-class-factory-macros.md#declare_classfactory_auto_thread) -Makro in die Klassendefinition Ihres Objekts einschließen, um [ccomclassfactoryautothread](../../atl/reference/ccomclassfactoryautothread-class.md) als Klassenfactory anzugeben.

Standardmäßig leitet der ATL COM AppWizard (der ATL-Projekt-Assistent in Visual Studio .net) das Modul von `CComModule`ab. Um `CComAutoThreadModule`zu verwenden, ändern Sie die Klassendefinition. Zum Beispiel:

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

**Header:** atlbase. h

##  <a name="ccomautothreadmodulecreateinstance"></a><a name="createinstance"></a>CComAutoThreadModule:: "kreateingestance"

Ab ATL 7,0 ist `CComAutoThreadModule` veraltet: Weitere Informationen finden Sie unter [ATL-Modul Klassen](../../atl/atl-module-classes.md) .

```
HRESULT CreateInstance(
    void* pfnCreateInstance,
    REFIID riid,
    void** ppvObj);
```

### <a name="parameters"></a>Parameter

*pfnCreateInstance*<br/>
in Ein Zeiger auf eine erstellerfunktion.

*riid*<br/>
in Die IID der angeforderten Schnittstelle.

*ppvObj*<br/>
vorgenommen Ein Zeiger auf den Schnittstellen Zeiger, der durch *riid*identifiziert wird. Wenn das Objekt diese Schnittstelle nicht unterstützt, wird *ppvObj* auf NULL festgelegt.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standardwert.

### <a name="remarks"></a>Hinweise

Wählt einen Thread aus und erstellt dann ein-Objekt im zugeordneten Apartment.

##  <a name="ccomautothreadmoduledwthreadid"></a><a name="dwthreadid"></a>CComAutoThreadModule::d wthreadid

Ab ATL 7,0 ist `CComAutoThreadModule` veraltet: Weitere Informationen finden Sie unter [ATL-Modul Klassen](../../atl/atl-module-classes.md) .

```
DWORD dwThreadID;
```

### <a name="remarks"></a>Hinweise

Enthält den Bezeichner des aktuellen Threads.

##  <a name="ccomautothreadmodulegetdefaultthreads"></a><a name="getdefaultthreads"></a>CComAutoThreadModule:: getdefaultthreads

Ab ATL 7,0 ist `CComAutoThreadModule` veraltet: Weitere Informationen finden Sie unter [ATL-Modul Klassen](../../atl/atl-module-classes.md) .

```
static int GetDefaultThreads();
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Threads, die im exe-Modul erstellt werden sollen.

### <a name="remarks"></a>Hinweise

Diese statische Funktion berechnet dynamisch die maximale Anzahl von Threads für das exe-Modul, basierend auf der Anzahl der Prozessoren. Standardmäßig wird dieser Rückgabewert an die [Init](#init) -Methode zum Erstellen der Threads übermittelt.

##  <a name="ccomautothreadmoduleinit"></a><a name="init"></a>CComAutoThreadModule:: init

Ab ATL 7,0 ist `CComAutoThreadModule` veraltet: Weitere Informationen finden Sie unter [ATL-Modul Klassen](../../atl/atl-module-classes.md) .

```
HRESULT Init(
    _ATL_OBJMAP_ENTRY* p,
    HINSTANCE h,
    const GUID* plibid = NULL,
    int nThreads = GetDefaultThreads());
```

### <a name="parameters"></a>Parameter

*p*<br/>
in Ein Zeiger auf ein Array von Objekt Zuordnungs Einträgen.

*h*<br/>
in Die an `DLLMain` oder `WinMain`über gegebene HINSTANCE.

*plibid*<br/>
in Ein Zeiger auf die LIBID der Typbibliothek, die dem Projekt zugeordnet ist.

*nThreads*<br/>
in Die Anzahl der zu erstellenden Threads. Standardmäßig ist *nthreads* der von [getdefaultthreads](#getdefaultthreads)zurückgegebene Wert.

### <a name="remarks"></a>Hinweise

Initialisiert Datenmember und erstellt die Anzahl der Threads, die von *nthreads*angegeben werden.

##  <a name="ccomautothreadmodulelock"></a><a name="lock"></a>CComAutoThreadModule:: Lock

Ab ATL 7,0 ist `CComAutoThreadModule` veraltet: Weitere Informationen finden Sie unter [ATL-Modul Klassen](../../atl/atl-module-classes.md) .

```
LONG Lock();
```

### <a name="return-value"></a>Rückgabewert

Ein Wert, der für die Diagnose oder das Testen nützlich sein kann.

### <a name="remarks"></a>Hinweise

Führt ein atomarische Inkrement für die Sperrenanzahl für das Modul und für den aktuellen Thread aus. `CComAutoThreadModule` verwendet die Modul Sperr Anzahl, um zu bestimmen, ob Clients auf das Modul zugreifen. Die Sperrenanzahl für den aktuellen Thread wird für statistische Zwecke verwendet.

##  <a name="ccomautothreadmodulem_allocator"></a><a name="m_allocator"></a>CComAutoThreadModule:: m_Allocator

Ab ATL 7,0 ist `CComAutoThreadModule` veraltet: Weitere Informationen finden Sie unter [ATL-Modul Klassen](../../atl/atl-module-classes.md) .

```
ThreadAllocator  m_Allocator;
```

### <a name="remarks"></a>Hinweise

Das Objekt, das die Thread Auswahl verwaltet. Standardmäßig ist der `ThreadAllocator` Klassen Vorlagen Parameter [ccomsimplethreadzuweisung](../../atl/reference/ccomsimplethreadallocator-class.md).

##  <a name="ccomautothreadmodulem_nthreads"></a><a name="m_nthreads"></a>CComAutoThreadModule:: m_nThreads

Ab ATL 7,0 ist `CComAutoThreadModule` veraltet: Weitere Informationen finden Sie unter [ATL-Modul Klassen](../../atl/atl-module-classes.md) .

```
int m_nThreads;
```

### <a name="remarks"></a>Hinweise

Enthält die Anzahl der Threads im exe-Modul. Wenn [Init](#init) aufgerufen wird, wird `m_nThreads` auf den *nthreads* -Parameterwert festgelegt. Das zugehörige Apartment jedes Threads wird von einem [ccomapartment](../../atl/reference/ccomapartment-class.md) -Objekt verwaltet.

##  <a name="ccomautothreadmodulem_papartments"></a><a name="m_papartments"></a>CComAutoThreadModule:: m_pApartments

Ab ATL 7,0 ist `CComAutoThreadModule` veraltet: Weitere Informationen finden Sie unter [ATL-Modul Klassen](../../atl/atl-module-classes.md) .

```
CComApartment* m_pApartments;
```

### <a name="remarks"></a>Hinweise

Verweist auf ein Array von [ccomapartment](../../atl/reference/ccomapartment-class.md) -Objekten, von denen jedes ein Apartment im Modul verwaltet. Die Anzahl der Elemente im Array basiert auf dem [m_nThreads](#m_nthreads) -Member.

##  <a name="ccomautothreadmoduleunlock"></a><a name="unlock"></a>CComAutoThreadModule:: Unlock

Ab ATL 7,0 ist `CComAutoThreadModule` veraltet: Weitere Informationen finden Sie unter [ATL-Modul Klassen](../../atl/atl-module-classes.md) .

```
LONG Unlock();
```

### <a name="return-value"></a>Rückgabewert

Ein Wert, der für die Diagnose oder das Testen nützlich sein kann.

### <a name="remarks"></a>Hinweise

Führt eine atomarische Dekrement für die Sperrenanzahl für das Modul und für den aktuellen Thread aus. `CComAutoThreadModule` verwendet die Modul Sperr Anzahl, um zu bestimmen, ob Clients auf das Modul zugreifen. Die Sperrenanzahl für den aktuellen Thread wird für statistische Zwecke verwendet.

Wenn die Anzahl der Modul Sperren Null erreicht, kann das Modul entladen werden.

## <a name="see-also"></a>Siehe auch

[Klassen Übersicht](../../atl/atl-class-overview.md)<br/>
[Modul Klassen](../../atl/atl-module-classes.md)
