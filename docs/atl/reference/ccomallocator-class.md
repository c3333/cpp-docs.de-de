---
title: CComAllocator-Klasse
ms.date: 11/04/2016
f1_keywords:
- CComAllocator
- ATLBASE/ATL::CComAllocator
- ATLBASE/ATL::CComAllocator::Allocate
- ATLBASE/ATL::CComAllocator::Free
- ATLBASE/ATL::CComAllocator::Reallocate
helpviewer_keywords:
- CComAllocator class
ms.assetid: 0cd706fd-0c7b-42d3-9054-febe2966fc8e
ms.openlocfilehash: 165cdb8b0b16a4872214f4556c26ee141e6a4d89
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321143"
---
# <a name="ccomallocator-class"></a>CComAllocator-Klasse

Diese Klasse stellt Methoden zum Verwalten von Arbeitsspeicher mithilfe von COM-Speicherroutinen bereit.

## <a name="syntax"></a>Syntax

```
class CComAllocator
```

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CComAllocator::Zuweisen](#allocate)|Rufen Sie diese statische Methode auf, um Speicher zuzuweisen.|
|[CComAllocator::Kostenlos](#free)|Rufen Sie diese statische Methode auf, um zugewiesenen Speicher freizugeben.|
|[CComAllocator::Neuzuordnen](#reallocate)|Rufen Sie diese statische Methode auf, um Denspeicher neu zuzuweisen.|

## <a name="remarks"></a>Bemerkungen

Diese Klasse wird von [CComHeapPtr](../../atl/reference/ccomheapptr-class.md) verwendet, um die COM-Speicherzuweisungsroutinen bereitzustellen. Die Counterpartklasse [CCRTAllocator](../../atl/reference/ccrtallocator-class.md)stellt dieselben Methoden mit CRT-Routinen bereit.

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlbase.h

## <a name="ccomallocatorallocate"></a><a name="allocate"></a>CComAllocator::Zuweisen

Rufen Sie diese statische Funktion auf, um Arbeitsspeicher zu belegen.

```
static void* Allocate(size_t nBytes) throw();
```

### <a name="parameters"></a>Parameter

*nBytes*<br/>
Die Anzahl der zu belegenden Bytes.

### <a name="return-value"></a>Rückgabewert

Gibt einen void-Zeiger auf den belegten Speicherplatz oder NULL zurück, wenn nicht genügend Speicher verfügbar ist.

### <a name="remarks"></a>Bemerkungen

Belegt Arbeitsspeicher. Weitere Informationen finden Sie unter [CoTaskMemAlloc.](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemalloc)

## <a name="ccomallocatorfree"></a><a name="free"></a>CComAllocator::Kostenlos

Rufen Sie diese statische Funktion auf, um zugewiesenen Speicher freizugeben.

```
static void Free(void* p) throw();
```

### <a name="parameters"></a>Parameter

*P*<br/>
Zeiger auf zugewiesenen Speicher.

### <a name="remarks"></a>Bemerkungen

Gibt den zugewiesenen Speicher frei. Weitere Informationen finden Sie unter [CoTaskMemFree.](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemfree)

## <a name="ccomallocatorreallocate"></a><a name="reallocate"></a>CComAllocator::Neuzuordnen

Rufen Sie diese statischen Funktion auf, um Arbeitsspeicher neu zuzuordnen.

```
static void* Reallocate(void* p, size_t nBytes) throw();
```

### <a name="parameters"></a>Parameter

*P*<br/>
Zeiger auf zugewiesenen Speicher.

*nBytes*<br/>
Die Anzahl der zuzuordnenden Bytes.

### <a name="return-value"></a>Rückgabewert

Gibt einen leeren Zeiger auf den zugewiesenen Speicherplatz oder NULL zurück, wenn nicht genügend Arbeitsspeicher vorhanden ist.

### <a name="remarks"></a>Bemerkungen

Ändert die Größe des belegten Speichers. Weitere Informationen finden Sie unter [CoTaskMemRealloc.](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemrealloc)

## <a name="see-also"></a>Siehe auch

[CComHeapPtr-Klasse](../../atl/reference/ccomheapptr-class.md)<br/>
[CCRTAllocator-Klasse](../../atl/reference/ccrtallocator-class.md)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)
