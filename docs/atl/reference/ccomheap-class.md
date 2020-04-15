---
title: CComHeap-Klasse
ms.date: 11/04/2016
f1_keywords:
- CComHeap
- ATLCOMMEM/ATL::CComHeap
- ATLCOMMEM/ATL::CComHeap::Allocate
- ATLCOMMEM/ATL::CComHeap::Free
- ATLCOMMEM/ATL::CComHeap::GetSize
- ATLCOMMEM/ATL::CComHeap::Reallocate
helpviewer_keywords:
- CComHeap class
ms.assetid: c74183ce-98ae-46fb-b186-93ea4cf0222b
ms.openlocfilehash: a38d1147e718870c03af84ec1487e226805b956e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327822"
---
# <a name="ccomheap-class"></a>CComHeap-Klasse

Diese Klasse implementiert [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) mithilfe der COM-Speicherzuweisungsfunktionen.

> [!IMPORTANT]
> Diese Klasse und ihre Member können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

## <a name="syntax"></a>Syntax

```
class CComHeap : public IAtlMemMgr
```

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CComHeap::Zuweisen](#allocate)|Rufen Sie diese Methode auf, um einen Speicherblock zu belegen.|
|[CComHeap::Kostenlos](#free)|Rufen Sie diese Methode auf, um einen Speicherblock freizugeben, der von diesem Speicher-Manager zugewiesen wurde.|
|[CComHeap::GetSize](#getsize)|Rufen Sie diese Methode auf, um die zugewiesene Größe eines Speicherblocks abzurufen, der von diesem Speicher-Manager zugewiesen wurde.|
|[CComHeap::Neuzuordnen](#reallocate)|Rufen Sie diese Methode auf, um den von diesem Speicher-Manager zugeordneten Arbeitsspeicher neu zuzuordnen.|

## <a name="remarks"></a>Bemerkungen

`CComHeap`implementiert Speicherzuweisungsfunktionen mithilfe der COM-Zuweisungsfunktionen, einschließlich [CoTaskMemAlloc](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemalloc), [CoTaskMemFree](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemfree), [IMalloc::GetSize](/windows/win32/api/objidlbase/nf-objidlbase-imalloc-getsize)und [CoTaskMemRealloc](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemrealloc). Die maximale Speichermenge, die zugewiesen werden kann, entspricht INT_MAX (2147483647) Bytes.

## <a name="example"></a>Beispiel

Siehe Beispiel für [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`IAtlMemMgr`

`CComHeap`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** ATLComMem.h

## <a name="ccomheapallocate"></a><a name="allocate"></a>CComHeap::Zuweisen

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

Rufen Sie [CComHeap::Free](#free) oder [CComHeap::Reallocate](#reallocate) auf, um den von dieser Methode zugewiesenen Speicher freizugeben.

Implementiert mit [CoTaskMemAlloc](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemalloc).

## <a name="ccomheapfree"></a><a name="free"></a>CComHeap::Kostenlos

Rufen Sie diese Methode auf, um einen Speicherblock freizugeben, der von diesem Speicher-Manager zugewiesen wurde.

```
virtual void Free(void* p) throw();
```

### <a name="parameters"></a>Parameter

*P*<br/>
Ein Zeiger auf den Arbeitsspeicher, der zuvor von diesem Speicher-Manager zugeordnet wurde. NULL ist ein gültiger Wert und tut nichts.

### <a name="remarks"></a>Bemerkungen

Implementiert mit [CoTaskMemFree](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemfree).

## <a name="ccomheapgetsize"></a><a name="getsize"></a>CComHeap::GetSize

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

Implementiert mit [IMalloc::GetSize](/windows/win32/api/objidlbase/nf-objidlbase-imalloc-getsize).

## <a name="ccomheapreallocate"></a><a name="reallocate"></a>CComHeap::Neuzuordnen

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

Rufen Sie [CComHeap::Free](#free) auf, um den von dieser Methode zugewiesenen Speicher freizugeben.

Implementiert mit [CoTaskMemRealloc](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemrealloc).

## <a name="see-also"></a>Siehe auch

[DynamicConsumer-Beispiel](../../overview/visual-cpp-samples.md)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)<br/>
[CWin32Heap-Klasse](../../atl/reference/cwin32heap-class.md)<br/>
[CLocalHeap-Klasse](../../atl/reference/clocalheap-class.md)<br/>
[CGlobalHeap-Klasse](../../atl/reference/cglobalheap-class.md)<br/>
[CCRTHeap-Klasse](../../atl/reference/ccrtheap-class.md)<br/>
[IAtlMemMgr-Klasse](../../atl/reference/iatlmemmgr-class.md)
