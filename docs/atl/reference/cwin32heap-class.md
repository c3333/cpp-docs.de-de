---
title: CWin32Heap-Klasse
ms.date: 11/04/2016
f1_keywords:
- CWin32Heap
- ATLMEM/ATL::CWin32Heap
- ATLMEM/ATL::CWin32Heap::CWin32Heap
- ATLMEM/ATL::CWin32Heap::Allocate
- ATLMEM/ATL::CWin32Heap::Attach
- ATLMEM/ATL::CWin32Heap::Detach
- ATLMEM/ATL::CWin32Heap::Free
- ATLMEM/ATL::CWin32Heap::GetSize
- ATLMEM/ATL::CWin32Heap::Reallocate
- ATLMEM/ATL::CWin32Heap::m_bOwnHeap
- ATLMEM/ATL::CWin32Heap::m_hHeap
helpviewer_keywords:
- CWin32Heap class
ms.assetid: 69176022-ed98-4e3b-96d8-116b0c58ac95
ms.openlocfilehash: fbdb77e7f52e858401c87e1cd8782b59cc6ebcea
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330457"
---
# <a name="cwin32heap-class"></a>CWin32Heap-Klasse

Diese Klasse implementiert [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) mithilfe der Win32-Heapzuordnungsfunktionen.

> [!IMPORTANT]
> Diese Klasse und ihre Member können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

## <a name="syntax"></a>Syntax

```
class CWin32Heap : public IAtlMemMgr
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CWin32Heap::CWin32Heap](#cwin32heap)|Der Konstruktor.|
|[CWin32Heap::'CWin32Heap](#dtor)|Der Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CWin32Heap::Zuweisen](#allocate)|Führt eine Belegung eines Speicherblocks vom Heapobjekt durch.|
|[CWin32Heap::Anfügen](#attach)|Fügt das Heapobjekt an einen vorhandenen Heap an.|
|[CWin32Heap::Detach](#detach)|Trennt das Heapobjekt von einem vorhandenen Heap.|
|[CWin32Heap::Kostenlos](#free)|Gibt speicherfrei, der zuvor vom Heap zugewiesen wurde.|
|[CWin32Heap::GetSize](#getsize)|Gibt die Größe eines Speicherblocks zurück, der vom Heapobjekt zugewiesen wurde.|
|[CWin32Heap::Neuzuordnen](#reallocate)|Führt eine Neubelegung eines Speicherblocks vom Heapobjekt durch.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CWin32Heap::m_bOwnHeap](#m_bownheap)|Ein Flag, das verwendet wird, um den aktuellen Besitz des Heaphandles zu bestimmen.|
|[CWin32Heap::m_hHeap](#m_hheap)|Handle für das Heapobjekt.|

## <a name="remarks"></a>Bemerkungen

`CWin32Heap`implementiert Speicherzuweisungsmethoden mithilfe der Win32-Heapzuweisungsfunktionen, einschließlich [HeapAlloc](/windows/win32/api/heapapi/nf-heapapi-heapalloc) und [HeapFree](/windows/win32/api/heapapi/nf-heapapi-heapfree). Im Gegensatz zu `CWin32Heap` anderen Heap-Klassen muss ein gültiges Heaphandle bereitgestellt werden, bevor Speicher zugewiesen wird: Die anderen Klassen verwenden standardmäßig den Prozessheap. Das Handle kann dem Konstruktor oder der [CWin32Heap::Attach-Methode](#attach) bereitgestellt werden. Weitere Informationen finden Sie in der [CWin32Heap::CWin32Heap-Methode.](#cwin32heap)

## <a name="example"></a>Beispiel

Siehe Beispiel für [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`IAtlMemMgr`

`CWin32Heap`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlmem.h

## <a name="cwin32heapallocate"></a><a name="allocate"></a>CWin32Heap::Zuweisen

Führt eine Belegung eines Speicherblocks vom Heapobjekt durch.

```
virtual __declspec(allocator) void* Allocate(size_t nBytes) throw();
```

### <a name="parameters"></a>Parameter

*nBytes*<br/>
Die angeforderte Anzahl von Bytes im neuen Speicherblock.

### <a name="return-value"></a>Rückgabewert

Gibt einen Zeiger auf den neu belegten Speicherblock zurück.

### <a name="remarks"></a>Bemerkungen

Rufen Sie [CWin32Heap::Free](#free) oder [CWin32Heap::Reallocate](#reallocate) auf, um den von dieser Methode zugewiesenen Speicher freizugeben.

Implementiert mit [HeapAlloc](/windows/win32/api/heapapi/nf-heapapi-heapalloc).

## <a name="cwin32heapattach"></a><a name="attach"></a>CWin32Heap::Anfügen

Fügt das Heapobjekt an einen vorhandenen Heap an.

```
void Attach(HANDLE hHeap, bool bTakeOwnership) throw();
```

### <a name="parameters"></a>Parameter

*hHeap*<br/>
Ein vorhandener Heaphandle.

*bTakeOwnership*<br/>
Ein Flag, das `CWin32Heap` angibt, ob das Objekt den Besitz über die Ressourcen des Heaps übernehmen soll.

### <a name="remarks"></a>Bemerkungen

Wenn *bTakeOwnership* TRUE `CWin32Heap` ist, ist das Objekt für das Löschen des Heaphandles verantwortlich.

## <a name="cwin32heapcwin32heap"></a><a name="cwin32heap"></a>CWin32Heap::CWin32Heap

Der Konstruktor.

```
CWin32Heap() throw();
CWin32Heap( HANDLE  hHeap) throw();
CWin32Heap(
    DWORD  dwFlags,
    size_t nInitialSize,
    size_t nMaxSize = 0);
```

### <a name="parameters"></a>Parameter

*hHeap*<br/>
Ein vorhandenes Heapobjekt.

*dwFlags*<br/>
Bei der Erstellung des Heaps verwendete Flags.

*nInitialSize*<br/>
Die Anfangsgröße des Heaps.

*nMaxSize*<br/>
Die maximale Größe des Heaps.

### <a name="remarks"></a>Bemerkungen

Vor dem Zuordnen von Speicher muss das `CWin32Heap`-Objekt mit einem gültigen Heaphandle bereitgestellt werden. Das geht am einfachsten mit dem Prozessheap:

[!code-cpp[NVC_ATL_Utilities#92](../../atl/codesnippet/cpp/cwin32heap-class_1.cpp)]

Es ist auch möglich, ein vorhandenes Heaphandle an den Konstruktor auszugeben; in diesem Fall übernimmt das neue Objekt nicht Besitz des Heaps. Wenn das `CWin32Heap`-Objekt gelöscht wird, ist das ursprüngliche Heaphandle weiterhin gültig.

Ein vorhandener Heap kann auch mit [CWin32Heap::Attach](#attach)an das neue Objekt angefügt werden.

Wenn ein Heap erforderlich ist, in dem alle Operationen von einem einzigen Thread ausgeführt werden, empfiehlt es sich, das Objekt folgendermaßen zu erstellen:

[!code-cpp[NVC_ATL_Utilities#93](../../atl/codesnippet/cpp/cwin32heap-class_2.cpp)]

Der Parameter HEAP_NO_SERIALIZE gibt an, dass kein gegenseitiger Ausschluss verwendet wird, wenn die Heapfunktionen Arbeitsspeicher zuordnen und freigeben und sich die Leistung in entsprechendem Maße erhöht.

Der dritte Parameter beträgt standardmäßig 0; dadurch kann das Heap nach Bedarf vergrößert werden. Unter [HeapCreate](/windows/win32/api/heapapi/nf-heapapi-heapcreate) finden Sie eine Erläuterung der Speichergrößen und -flags.

## <a name="cwin32heapcwin32heap"></a><a name="dtor"></a>CWin32Heap::'CWin32Heap

Der Destruktor.

```
~CWin32Heap() throw();
```

### <a name="remarks"></a>Bemerkungen

Zerstört das Heaphandle, `CWin32Heap` wenn das Objekt eigentümer ist.

## <a name="cwin32heapdetach"></a><a name="detach"></a>CWin32Heap::Detach

Trennt das Heapobjekt von einem vorhandenen Heap.

```
HANDLE Detach() throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt das Handle an den Heap zurück, an den das Objekt zuvor angefügt wurde.

## <a name="cwin32heapfree"></a><a name="free"></a>CWin32Heap::Kostenlos

Gibt Speicher frei, der zuvor vom Heap von [CWin32Heap::Allocate](#allocate) oder [CWin32Heap::Reallocate](#reallocate)zugewiesen wurde.

```
virtual void Free(void* p) throw();
```

### <a name="parameters"></a>Parameter

*P*<br/>
Zeiger auf den speicherfreien Speicherblock. NULL ist ein gültiger Wert und tut nichts.

## <a name="cwin32heapgetsize"></a><a name="getsize"></a>CWin32Heap::GetSize

Gibt die Größe eines Speicherblocks zurück, der vom Heapobjekt zugewiesen wurde.

```
virtual size_t GetSize(void* p) throw();
```

### <a name="parameters"></a>Parameter

*P*<br/>
Zeiger auf den Speicherblock, dessen Größe die Methode erhält. Dies ist ein Zeiger, der von [CWin32Heap::Allocate](#allocate) oder [CWin32Heap::Reallocate](#reallocate)zurückgegeben wird.

### <a name="return-value"></a>Rückgabewert

Gibt die Größe des zugewiesenen Speicherblocks in Bytes zurück.

## <a name="cwin32heapm_bownheap"></a><a name="m_bownheap"></a>CWin32Heap::m_bOwnHeap

Ein Flag, das verwendet wird, um den aktuellen Besitz des Heaphandles zu bestimmen, das in [m_hHeap](#m_hheap)gespeichert ist.

```
bool m_bOwnHeap;
```

## <a name="cwin32heapm_hheap"></a><a name="m_hheap"></a>CWin32Heap::m_hHeap

Handle für das Heapobjekt.

```
HANDLE m_hHeap;
```

### <a name="remarks"></a>Bemerkungen

Eine Variable, die zum Speichern eines Handles im Heapobjekt verwendet wird.

## <a name="cwin32heapreallocate"></a><a name="reallocate"></a>CWin32Heap::Neuzuordnen

Führt eine Neubelegung eines Speicherblocks vom Heapobjekt durch.

```
virtual __declspec(allocator) void* Reallocate(void* p, size_t nBytes) throw();
```

### <a name="parameters"></a>Parameter

*P*<br/>
Zeiger auf den neu zu belegenden Speicherblock.

*nBytes*<br/>
Die neue Größe des belegten Blocks in Bytes. Der Block kann größer oder kleiner gemacht werden.

### <a name="return-value"></a>Rückgabewert

Gibt einen Zeiger auf den neu belegten Speicherblock zurück.

### <a name="remarks"></a>Bemerkungen

Wenn *p* NULL ist, wird davon ausgegangen, dass der Speicherblock noch nicht zugewiesen wurde und [CWin32Heap::Allocate](#allocate) aufgerufen wird, mit dem Argument *nBytes*.

## <a name="see-also"></a>Siehe auch

[Klassenübersicht](../../atl/atl-class-overview.md)<br/>
[IAtlMemMgr-Klasse](../../atl/reference/iatlmemmgr-class.md)<br/>
[CLocalHeap-Klasse](../../atl/reference/clocalheap-class.md)<br/>
[CGlobalHeap-Klasse](../../atl/reference/cglobalheap-class.md)<br/>
[CCRTHeap-Klasse](../../atl/reference/ccrtheap-class.md)<br/>
[CComHeap-Klasse](../../atl/reference/ccomheap-class.md)
