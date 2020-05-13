---
title: CHeapPtrList-Klasse
ms.date: 11/04/2016
f1_keywords:
- CHeapPtrList
- ATLCOLL/ATL::CHeapPtrList
- ATLCOLL/ATL::CHeapPtrList::CHeapPtrList
helpviewer_keywords:
- CHeapPtrList class
ms.assetid: cc70e585-362a-4007-81db-c705eb181226
ms.openlocfilehash: 0500ab8f76049aeaf1c89355ea5450a93243b734
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326859"
---
# <a name="cheapptrlist-class"></a>CHeapPtrList-Klasse

Diese Klasse stellt Methoden bereit, die beim Erstellen einer Liste von Heapzeigern nützlich sind.

> [!IMPORTANT]
> Diese Klasse und ihre Member können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

## <a name="syntax"></a>Syntax

```
template<typename E, class Allocator = ATL::CCRTAllocator>
class CHeapPtrList
   : public CAtlList<ATL::CHeapPtr<E, Allocator>,
                     CHeapPtrElementTraits<E, Allocator>>
```

#### <a name="parameters"></a>Parameter

*E*<br/>
Der Objekttyp, der in der Auflistungsklasse gespeichert werden soll.

*Zuweisung*<br/>
Die zu verwendende Speicherzuweisungsklasse. Der Standardwert ist [CCRTAllocator](../../atl/reference/ccrtallocator-class.md).

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CHeapPtrList::CHeapPtrList](#cheapptrlist)|Der Konstruktor.|

## <a name="remarks"></a>Bemerkungen

Diese Klasse stellt einen Konstruktor bereit und leitet Methoden von [CAtlList](../../atl/reference/catllist-class.md) und [CHeapPtrElementTraits](../../atl/reference/cheapptrelementtraits-class.md) ab, um die Erstellung eines Auflistungsklassenobjekts zu unterstützen, das Heapzeiger speichert.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CAtlList](../../atl/reference/catllist-class.md)

`CHeapPtrList`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlcoll.h

## <a name="cheapptrlistcheapptrlist"></a><a name="cheapptrlist"></a>CHeapPtrList::CHeapPtrList

Der Konstruktor.

```
CHeapPtrList(UINT nBlockSize = 10) throw();
```

### <a name="parameters"></a>Parameter

*nBlockSize*<br/>
Die Blockgröße.

### <a name="remarks"></a>Bemerkungen

Die Blockgröße ist ein Maß für die Speichermenge, die zugewiesen wird, wenn ein neues Element erforderlich ist. Größere Blockgrößen reduzieren Aufrufe von Speicherzuweisungsroutinen, verwenden jedoch mehr Ressourcen.

## <a name="see-also"></a>Siehe auch

[CAtlList-Klasse](../../atl/reference/catllist-class.md)<br/>
[CHeapPtr-Klasse](../../atl/reference/cheapptr-class.md)<br/>
[CHeapPtrElementTraits-Klasse](../../atl/reference/cheapptrelementtraits-class.md)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)
