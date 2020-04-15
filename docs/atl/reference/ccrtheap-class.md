---
title: CCRTHeap-Klasse
ms.date: 11/04/2016
f1_keywords:
- CCRTHeap
- ATLMEM/ATL::CCRTHeap
- ATLMEM/ATL::CCRTHeap::Allocate
- ATLMEM/ATL::CCRTHeap::Free
- ATLMEM/ATL::CCRTHeap::GetSize
- ATLMEM/ATL::CCRTHeap::Reallocate
helpviewer_keywords:
- CCRTHeap class
ms.assetid: 321bd6c5-1856-4ff7-8590-95044a1209f7
ms.openlocfilehash: caf5508079332689c2fff42f130951375dc35512
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327160"
---
# <a name="ccrtheap-class"></a>CCRTHeap-Klasse

Diese Klasse implementiert [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) mithilfe der CRT-Heapfunktionen.

## <a name="syntax"></a>Syntax

```
class CCRTHeap : public IAtlMemMgr
```

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CCRTHeap::Zuweisen](#allocate)|Rufen Sie diese Methode auf, um einen Speicherblock zu belegen.|
|[CCRTHeap::Kostenlos](#free)|Rufen Sie diese Methode auf, um einen Speicherblock freizugeben, der von diesem Speicher-Manager zugewiesen wurde.|
|[CCRTHeap::GetSize](#getsize)|Rufen Sie diese Methode auf, um die zugewiesene Größe eines Speicherblocks abzurufen, der von diesem Speicher-Manager zugewiesen wurde.|
|[CCRTHeap::Neuzuordnen](#reallocate)|Rufen Sie diese Methode auf, um den von diesem Speicher-Manager zugeordneten Arbeitsspeicher neu zuzuordnen.|

## <a name="remarks"></a>Bemerkungen

`CCRTHeap`implementiert Speicherzuweisungsfunktionen mithilfe der CRT-Heapfunktionen, einschließlich [malloc](../../c-runtime-library/reference/malloc.md), [free](../../c-runtime-library/reference/free.md), [realloc](../../c-runtime-library/reference/realloc.md)und [_msize](../../c-runtime-library/reference/msize.md).

## <a name="example"></a>Beispiel

Siehe Beispiel für [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`IAtlMemMgr`

`CCRTHeap`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlmem.h

## <a name="ccrtheapallocate"></a><a name="allocate"></a>CCRTHeap::Zuweisen

Rufen Sie diese Methode auf, um einen Speicherblock zu belegen.

```
virtual __declspec(allocator) void* Allocate(size_t nBytes) throw();
```

### <a name="parameters"></a>Parameter

*nBytes*<br/>
Die angeforderte Anzahl von Bytes im neuen Speicherblock.

### <a name="return-value"></a>Rückgabewert

Gibt einen Zeiger auf den Anfang des neu belegten Speicherblocks zurück.

### <a name="remarks"></a>Bemerkungen

Rufen Sie [CCRTHeap::Free](#free) oder [CCRTHeap::Reallocate](#reallocate) auf, um den von dieser Methode zugewiesenen Speicher freizugeben.

Implementiert mit [malloc](../../c-runtime-library/reference/malloc.md).

## <a name="ccrtheapfree"></a><a name="free"></a>CCRTHeap::Kostenlos

Rufen Sie diese Methode auf, um einen Speicherblock freizugeben, der von diesem Speicher-Manager zugewiesen wurde.

```
virtual void Free(void* p) throw();
```

### <a name="parameters"></a>Parameter

*P*<br/>
Ein Zeiger auf den Arbeitsspeicher, der zuvor von diesem Speicher-Manager zugeordnet wurde. NULL ist ein gültiger Wert und tut nichts.

### <a name="remarks"></a>Bemerkungen

Implementiert mit [free](../../c-runtime-library/reference/free.md).

## <a name="ccrtheapgetsize"></a><a name="getsize"></a>CCRTHeap::GetSize

Rufen Sie diese Methode auf, um die zugewiesene Größe eines Speicherblocks abzurufen, der von diesem Speicher-Manager zugewiesen wurde.

```
virtual size_t GetSize(void* p) throw();
```

### <a name="parameters"></a>Parameter

*P*<br/>
Ein Zeiger auf den Arbeitsspeicher, der zuvor von diesem Speicher-Manager zugeordnet wurde.

### <a name="return-value"></a>Rückgabewert

Gibt die Größe des zugewiesenen Speicherblocks in Bytes zurück.

### <a name="remarks"></a>Bemerkungen

Implementiert mit [_msize](../../c-runtime-library/reference/msize.md).

## <a name="ccrtheapreallocate"></a><a name="reallocate"></a>CCRTHeap::Neuzuordnen

Rufen Sie diese Methode auf, um den von diesem Speicher-Manager zugeordneten Arbeitsspeicher neu zuzuordnen.

```
virtual __declspec(allocator) void* Reallocate(void* p, size_t nBytes) throw();
```

### <a name="parameters"></a>Parameter

*P*<br/>
Ein Zeiger auf den Arbeitsspeicher, der zuvor von diesem Speicher-Manager zugeordnet wurde.

*nBytes*<br/>
Die angeforderte Anzahl von Bytes im neuen Speicherblock.

### <a name="return-value"></a>Rückgabewert

Gibt einen Zeiger auf den Anfang des neu belegten Speicherblocks zurück.

### <a name="remarks"></a>Bemerkungen

Rufen Sie [CCRTHeap::Free](#free) auf, um den von dieser Methode zugewiesenen Speicher freizugeben. Implementiert mit [realloc](../../c-runtime-library/reference/realloc.md).

## <a name="see-also"></a>Siehe auch

[Klassenübersicht](../../atl/atl-class-overview.md)<br/>
[CComHeap-Klasse](../../atl/reference/ccomheap-class.md)<br/>
[CWin32Heap-Klasse](../../atl/reference/cwin32heap-class.md)<br/>
[CLocalHeap-Klasse](../../atl/reference/clocalheap-class.md)<br/>
[CGlobalHeap-Klasse](../../atl/reference/cglobalheap-class.md)<br/>
[IAtlMemMgr-Klasse](../../atl/reference/iatlmemmgr-class.md)
