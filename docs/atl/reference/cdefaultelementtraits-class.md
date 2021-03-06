---
title: CDefaultElementTraits-Klasse
ms.date: 11/04/2016
f1_keywords:
- CDefaultElementTraits
- atlcoll/ATL::CDefaultElementTraits
helpviewer_keywords:
- CDefaultElementTraits class
ms.assetid: ac5ee610-7957-4b7c-92b6-38ff72e4118e
ms.openlocfilehash: 0ee076af5fc4a1c2145162ac510b3a4460e251e0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62245920"
---
# <a name="cdefaultelementtraits-class"></a>CDefaultElementTraits-Klasse

Diese Klasse stellt die Standardmethoden und -Funktionen, damit eine Auflistungsklasse.

## <a name="syntax"></a>Syntax

```
template <typename T>
class CDefaultElementTraits : public CElementTraitsBase<T>,
    public CDefaultHashTraits<T>,
    public CDefaultCompareTraits<T>
```

#### <a name="parameters"></a>Parameter

*T*<br/>
Der Typ der Daten in der Auflistung gespeichert werden.

## <a name="remarks"></a>Hinweise

Diese Klasse stellt statische Standard-Funktionen und Methoden für das Verschieben, kopieren, vergleichen und hashing in ein Klassenobjekt Auflistung gespeicherten Elementen an. Diese Klasse abgeleitet wird, seine Funktionen und Methoden aus [CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md), [CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md), und [CDefaultCompareTraits](../../atl/reference/cdefaultcomparetraits-class.md), und wird verwendet, indem [ CElementTraits](../../atl/reference/celementtraits-class.md), [CPrimitiveElementTraits](../../atl/reference/cprimitiveelementtraits-class.md), und [CHeapPtrElementTraits](../../atl/reference/cheapptrelementtraits-class.md).

Weitere Informationen finden Sie unter [ATL-Auflistungsklassen](../../atl/atl-collection-classes.md).

## <a name="requirements"></a>Anforderungen

**Header:** atlcoll.h

## <a name="see-also"></a>Siehe auch

[Übersicht über die Klasse](../../atl/atl-class-overview.md)
