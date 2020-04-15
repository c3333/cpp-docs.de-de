---
title: CCRTAllocator-Klasse
ms.date: 11/04/2016
f1_keywords:
- CCRTAllocator
- ATLCORE/ATL::CCRTAllocator
- ATLCORE/ATL::CCRTAllocator::Allocate
- ATLCORE/ATL::CCRTAllocator::Free
- ATLCORE/ATL::CCRTAllocator::Reallocate
helpviewer_keywords:
- CCRTAllocator class
ms.assetid: 3e1b8cb0-859a-41ab-8e93-6f0b5ceca49d
ms.openlocfilehash: 2f6bae3818fa0f1639e0e3cee4e09121580da768
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327169"
---
# <a name="ccrtallocator-class"></a>CCRTAllocator-Klasse

Diese Klasse stellt Methoden zum Verwalten von Arbeitsspeicher mithilfe von CRT-Speicherroutinen bereit.

## <a name="syntax"></a>Syntax

```
class ATL::CCRTAllocator
```

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CCRTAllocator::Zuweisen](#allocate)|(Statisch) Rufen Sie diese Methode auf, um Speicher zuzuweisen.|
|[CCRTAllocator::Kostenlos](#free)|(Statisch) Rufen Sie diese Methode auf, um Speicher freizugeben.|
|[CCRTAllocator::Neuzuordnen](#reallocate)|(Statisch) Rufen Sie diese Methode auf, um Denspeicher neu zuzuweisen.|

## <a name="remarks"></a>Bemerkungen

Diese Klasse wird von [CHeapPtr](../../atl/reference/cheapptr-class.md) verwendet, um die CRT-Speicherzuweisungsroutinen bereitzustellen. Die Counterpartklasse [CComAllocator](../../atl/reference/ccomallocator-class.md)stellt dieselben Methoden mithilfe von COM-Routinen bereit.

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlcore.h

## <a name="ccrtallocatorallocate"></a><a name="allocate"></a>CCRTAllocator::Zuweisen

Rufen Sie diese statische Funktion auf, um Arbeitsspeicher zu belegen.

```
static __declspec(allocator) void* Allocate(size_t nBytes) throw();
```

### <a name="parameters"></a>Parameter

*nBytes*<br/>
Die Anzahl der zu belegenden Bytes.

### <a name="return-value"></a>Rückgabewert

Gibt einen void-Zeiger auf den belegten Speicherplatz oder NULL zurück, wenn nicht genügend Speicher verfügbar ist.

### <a name="remarks"></a>Bemerkungen

Belegt Arbeitsspeicher. Siehe [malloc](../../c-runtime-library/reference/malloc.md) für weitere Details.

## <a name="ccrtallocatorfree"></a><a name="free"></a>CCRTAllocator::Kostenlos

Rufen Sie diese statische Funktion auf, um Speicher freizugeben.

```
static void Free(void* p) throw();
```

### <a name="parameters"></a>Parameter

*P*<br/>
Zeiger auf zugewiesenen Speicher.

### <a name="remarks"></a>Bemerkungen

Gibt den zugewiesenen Speicher frei. Weitere Informationen finden Sie [unter freiem Bedarf.](../../c-runtime-library/reference/free.md)

## <a name="ccrtallocatorreallocate"></a><a name="reallocate"></a>CCRTAllocator::Neuzuordnen

Rufen Sie diese statischen Funktion auf, um Arbeitsspeicher neu zuzuordnen.

```
static __declspec(allocator) void* Reallocate(void* p, size_t nBytes) throw();
```

### <a name="parameters"></a>Parameter

*P*<br/>
Zeiger auf zugewiesenen Speicher.

*nBytes*<br/>
Die Anzahl der zuzuordnenden Bytes.

### <a name="return-value"></a>Rückgabewert

Gibt einen void-Zeiger auf den zugeordneten Speicherplatz oder NULL zurück, wenn nicht genügend Speicher verfügbar ist.

### <a name="remarks"></a>Bemerkungen

Ändert die Größe des belegten Speichers. Weitere Informationen finden Sie unter [realloc.](../../c-runtime-library/reference/realloc.md)

## <a name="see-also"></a>Siehe auch

[CHeapPtr-Klasse](../../atl/reference/cheapptr-class.md)<br/>
[CComAllocator-Klasse](../../atl/reference/ccomallocator-class.md)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)
