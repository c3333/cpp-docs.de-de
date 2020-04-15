---
title: CComHeapPtr-Klasse
ms.date: 11/04/2016
f1_keywords:
- CComHeapPtr
- ATLBASE/ATL::CComHeapPtr
- ATLBASE/ATL::CComHeapPtr::CComHeapPtr
helpviewer_keywords:
- CComHeapPtr class
ms.assetid: bd08b53d-da2b-43ab-a79c-e7c8dbbc5994
ms.openlocfilehash: 78cadfff9a278cf080393ab919f3891b201c91aa
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327777"
---
# <a name="ccomheapptr-class"></a>CComHeapPtr-Klasse

Eine intelligente Zeigerklasse zum Verwalten von Heapzeigern.

## <a name="syntax"></a>Syntax

```
template<typename T>
class CComHeapPtr : public CHeapPtr<T, CComAllocator>
```

#### <a name="parameters"></a>Parameter

*T*<br/>
Der Objekttyp, der auf dem Heap gespeichert werden soll.

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CComHeapPtr::CComHeapPtr](#ccomheapptr)|Der Konstruktor.|

## <a name="remarks"></a>Bemerkungen

`CComHeapPtr`leitet sich `CHeapPtr`von ab, verwendet jedoch [CComAllocator,](../../atl/reference/ccomallocator-class.md) um Speicher mithilfe von COM-Routinen zuzuweisen. Die verfügbaren Methoden finden Sie unter [CHeapPtr](../../atl/reference/cheapptr-class.md) und [CHeapPtrBase.](../../atl/reference/cheapptrbase-class.md)

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CHeapPtrBase](../../atl/reference/cheapptrbase-class.md)

[CHeapPtr](../../atl/reference/cheapptr-class.md)

`CComHeapPtr`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlbase.h

## <a name="ccomheapptrccomheapptr"></a><a name="ccomheapptr"></a>CComHeapPtr::CComHeapPtr

Der Konstruktor.

```
CComHeapPtr() throw();
explicit CComHeapPtr(T* pData) throw();
```

### <a name="parameters"></a>Parameter

*pData*<br/>
Ein vorhandenes `CComHeapPtr`-Objekt.

### <a name="remarks"></a>Bemerkungen

Der Heapzeiger kann optional mit einem `CComHeapPtr` vorhandenen Objekt erstellt werden. Wenn dies `CComHeapPtr` der Zuspruch bereits der Falle ist, übernimmt das neue Objekt die Verantwortung für die Verwaltung des neuen Zeigers und der neuen Ressourcen.

## <a name="see-also"></a>Siehe auch

[CHeapPtr-Klasse](../../atl/reference/cheapptr-class.md)<br/>
[CHeapPtrBase-Klasse](../../atl/reference/cheapptrbase-class.md)<br/>
[CComAllocator-Klasse](../../atl/reference/ccomallocator-class.md)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)
