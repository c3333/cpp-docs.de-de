---
title: CLocalHeap-Klasse
ms.date: 11/04/2016
f1_keywords:
- CLocalHeap
- ATLMEM/ATL::CLocalHeap
- ATLMEM/ATL::CLocalHeap::Allocate
- ATLMEM/ATL::CLocalHeap::Free
- ATLMEM/ATL::CLocalHeap::GetSize
- ATLMEM/ATL::CLocalHeap::Reallocate
helpviewer_keywords:
- CLocalHeap class
ms.assetid: 1ffa87a5-5fc8-4f8d-8809-58e87e963bd2
ms.openlocfilehash: 303e3b85ad11c309f862f59d6ec610701c4ef6db
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326759"
---
# <a name="clocalheap-class"></a>CLocalHeap-Klasse

Diese Klasse implementiert [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) mithilfe der lokalen Heapfunktionen Win32.

> [!IMPORTANT]
> Diese Klasse und ihre Member können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

## <a name="syntax"></a>Syntax

```
class CLocalHeap : public IAtlMemMgr
```

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CLocalHeap::Zuweisen](#allocate)|Rufen Sie diese Methode auf, um einen Speicherblock zu belegen.|
|[CLocalHeap::Kostenlos](#free)|Rufen Sie diese Methode auf, um einen Speicherblock freizugeben, der von diesem Speicher-Manager zugewiesen wurde.|
|[CLocalHeap::GetSize](#getsize)|Rufen Sie diese Methode auf, um die zugewiesene Größe eines Speicherblocks abzurufen, der von diesem Speicher-Manager zugewiesen wurde.|
|[CLocalHeap::Neuzuordnen](#reallocate)|Rufen Sie diese Methode auf, um den von diesem Speicher-Manager zugeordneten Arbeitsspeicher neu zuzuordnen.|

## <a name="remarks"></a>Bemerkungen

`CLocalHeap`implementiert Speicherzuweisungsfunktionen mithilfe der lokalen Heapfunktionen Win32.

> [!NOTE]
> Die lokalen Heapfunktionen sind langsamer als andere Speicherverwaltungsfunktionen und bieten nicht so viele Funktionen. Daher sollten neue Anwendungen die [Heapfunktionen](/windows/win32/Memory/heap-functions)verwenden. Diese sind in der [CWin32Heap-Klasse](../../atl/reference/cwin32heap-class.md) verfügbar.

## <a name="example"></a>Beispiel

Siehe Beispiel für [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`IAtlMemMgr`

`CLocalHeap`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlmem.h

## <a name="clocalheapallocate"></a><a name="allocate"></a>CLocalHeap::Zuweisen

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

Rufen Sie [CLocalHeap::Free](#free) oder [CLocalHeap::Reallocate](#reallocate) auf, um den von dieser Methode zugewiesenen Speicher freizugeben.

Implementiert mit [LocalAlloc](/windows/win32/api/winbase/nf-winbase-localalloc) mit einem Flag-Parameter von LMEM_FIXED.

## <a name="clocalheapfree"></a><a name="free"></a>CLocalHeap::Kostenlos

Rufen Sie diese Methode auf, um einen Speicherblock freizugeben, der von diesem Speicher-Manager zugewiesen wurde.

```
virtual void Free(void* p) throw();
```

### <a name="parameters"></a>Parameter

*P*<br/>
Ein Zeiger auf den Arbeitsspeicher, der zuvor von diesem Speicher-Manager zugeordnet wurde. NULL ist ein gültiger Wert und tut nichts.

### <a name="remarks"></a>Bemerkungen

Implementiert mit [LocalFree](/windows/win32/api/winbase/nf-winbase-localfree).

## <a name="clocalheapgetsize"></a><a name="getsize"></a>CLocalHeap::GetSize

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

Implementiert mit [LocalSize](/windows/win32/api/winbase/nf-winbase-localsize).

## <a name="clocalheapreallocate"></a><a name="reallocate"></a>CLocalHeap::Neuzuordnen

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

Rufen Sie [CLocalHeap::Free](#free) auf, um den von dieser Methode zugewiesenen Speicher freizugeben.

Implementiert mit [LocalReAlloc](/windows/win32/api/winbase/nf-winbase-localrealloc).

## <a name="see-also"></a>Siehe auch

[Klassenübersicht](../../atl/atl-class-overview.md)<br/>
[CComHeap-Klasse](../../atl/reference/ccomheap-class.md)<br/>
[CWin32Heap-Klasse](../../atl/reference/cwin32heap-class.md)<br/>
[CGlobalHeap-Klasse](../../atl/reference/cglobalheap-class.md)<br/>
[CCRTHeap-Klasse](../../atl/reference/ccrtheap-class.md)<br/>
[IAtlMemMgr-Klasse](../../atl/reference/iatlmemmgr-class.md)
