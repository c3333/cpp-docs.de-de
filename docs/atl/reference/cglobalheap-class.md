---
title: CGlobalHeap-Klasse
ms.date: 11/04/2016
f1_keywords:
- CGlobalHeap
- ATLMEM/ATL::CGlobalHeap
- ATLMEM/ATL::CGlobalHeap::Allocate
- ATLMEM/ATL::CGlobalHeap::Free
- ATLMEM/ATL::CGlobalHeap::GetSize
- ATLMEM/ATL::CGlobalHeap::Reallocate
helpviewer_keywords:
- CGlobalHeap class
ms.assetid: e348d838-3aa7-4bee-a1b3-cd000c99f834
ms.openlocfilehash: d596fd51c1bf33f606c1f14c9e8dbd2f1926c7f8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326940"
---
# <a name="cglobalheap-class"></a>CGlobalHeap-Klasse

Diese Klasse implementiert [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) mithilfe der globalen Heapfunktionen Von32.

> [!IMPORTANT]
> Diese Klasse und ihre Member können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

## <a name="syntax"></a>Syntax

```
class CGlobalHeap : public IAtlMemMgr
```

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CGlobalHeap::Zuweisen](#allocate)|Rufen Sie diese Methode auf, um einen Speicherblock zu belegen.|
|[CGlobalHeap::Kostenlos](#free)|Rufen Sie diese Methode auf, um einen Speicherblock freizugeben, der von diesem Speicher-Manager zugewiesen wurde.|
|[CGlobalHeap::GetSize](#getsize)|Rufen Sie diese Methode auf, um die zugewiesene Größe eines Speicherblocks abzurufen, der von diesem Speicher-Manager zugewiesen wurde.|
|[CGlobalHeap::Neuzuordnen](#reallocate)|Rufen Sie diese Methode auf, um den von diesem Speicher-Manager zugeordneten Arbeitsspeicher neu zuzuordnen.|

## <a name="remarks"></a>Bemerkungen

`CGlobalHeap`implementiert Speicherzuweisungsfunktionen mithilfe der globalen Heapfunktionen Von32.

> [!NOTE]
> Die globalen Heapfunktionen sind langsamer als andere Speicherverwaltungsfunktionen und bieten nicht so viele Funktionen. Daher sollten neue Anwendungen die [Heapfunktionen](/windows/win32/Memory/heap-functions)verwenden. Diese sind in der [CWin32Heap-Klasse](../../atl/reference/cwin32heap-class.md) verfügbar. Globale Funktionen werden weiterhin von DDE und den Zwischenablagefunktionen verwendet.

## <a name="example"></a>Beispiel

Siehe Beispiel für [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`IAtlMemMgr`

`CGlobalHeap`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlmem.h

## <a name="cglobalheapallocate"></a><a name="allocate"></a>CGlobalHeap::Zuweisen

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

Rufen Sie [CGlobalHeap::Free](#free) oder [CGlobalHeap::Reallocate](#reallocate) auf, um den von dieser Methode zugewiesenen Speicher freizugeben.

Implementiert mit [GlobalAlloc](/windows/win32/api/winbase/nf-winbase-globalalloc) mit einem Flag-Parameter von GMEM_FIXED.

## <a name="cglobalheapfree"></a><a name="free"></a>CGlobalHeap::Kostenlos

Rufen Sie diese Methode auf, um einen Speicherblock freizugeben, der von diesem Speicher-Manager zugewiesen wurde.

```
virtual void Free(void* p) throw();
```

### <a name="parameters"></a>Parameter

*P*<br/>
Ein Zeiger auf den Arbeitsspeicher, der zuvor von diesem Speicher-Manager zugeordnet wurde. NULL ist ein gültiger Wert und tut nichts.

### <a name="remarks"></a>Bemerkungen

Implementiert mit [GlobalFree](/windows/win32/api/winbase/nf-winbase-globalfree).

## <a name="cglobalheapgetsize"></a><a name="getsize"></a>CGlobalHeap::GetSize

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

Implementiert mit [GlobalSize](/windows/win32/api/winbase/nf-winbase-globalsize).

## <a name="cglobalheapreallocate"></a><a name="reallocate"></a>CGlobalHeap::Neuzuordnen

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

Rufen Sie [CGlobalHeap::Free](#free) auf, um den von dieser Methode zugewiesenen Speicher freizugeben.

Implementiert mit [GlobalReAlloc](/windows/win32/api/winbase/nf-winbase-globalrealloc).

## <a name="see-also"></a>Siehe auch

[Klassenübersicht](../../atl/atl-class-overview.md)<br/>
[CComHeap-Klasse](../../atl/reference/ccomheap-class.md)<br/>
[CWin32Heap-Klasse](../../atl/reference/cwin32heap-class.md)<br/>
[CLocalHeap-Klasse](../../atl/reference/clocalheap-class.md)<br/>
[CCRTHeap-Klasse](../../atl/reference/ccrtheap-class.md)<br/>
[IAtlMemMgr-Klasse](../../atl/reference/iatlmemmgr-class.md)
