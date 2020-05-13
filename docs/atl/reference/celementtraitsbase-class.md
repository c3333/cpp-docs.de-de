---
title: CElementTraitsBase-Klasse
ms.date: 11/04/2016
f1_keywords:
- CElementTraitsBase
- ATLCOLL/ATL::CElementTraitsBase
- ATLCOLL/ATL::CElementTraitsBase::INARGTYPE
- ATLCOLL/ATL::CElementTraitsBase::OUTARGTYPE
- ATLCOLL/ATL::CElementTraitsBase::CopyElements
- ATLCOLL/ATL::CElementTraitsBase::RelocateElements
helpviewer_keywords:
- CElementTraitsBase class
ms.assetid: 75284caf-347e-4355-a7d8-efc708dd514a
ms.openlocfilehash: 5a29e8778cf2f3400df25b55574950a005bad995
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327007"
---
# <a name="celementtraitsbase-class"></a>CElementTraitsBase-Klasse

Diese Klasse stellt standardmäßige Kopier- und Verschiebungsmethoden für eine Auflistungsklasse bereit.

## <a name="syntax"></a>Syntax

```
template<typename T>
class CElementTraitsBase
```

#### <a name="parameters"></a>Parameter

*T*<br/>
Der Typ der Daten, die in der Auflistung gespeichert werden sollen.

## <a name="members"></a>Member

### <a name="public-typedefs"></a>Öffentliche Typedefs

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CElementTraitsBase::INARGTYPE](#inargtype)|Der Datentyp, der zum Hinzufügen von Elementen zum Auflistungsklassenobjekt verwendet werden soll.|
|[CElementTraitsBase::OUTARGTYPE](#outargtype)|Der Datentyp, der zum Abrufen von Elementen aus dem Auflistungsklassenobjekt verwendet werden soll.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CElementTraitsBase::CopyElements](#copyelements)|Rufen Sie diese Methode auf, um Elemente zu kopieren, die in einem Auflistungsklassenobjekt gespeichert sind.|
|[CElementTraitsBase::RelocateElements](#relocateelements)|Rufen Sie diese Methode auf, um Elemente zu verschieben, die in einem Auflistungsklassenobjekt gespeichert sind.|

## <a name="remarks"></a>Bemerkungen

Diese Basisklasse definiert Methoden zum Kopieren und Verschieben von Elementen in einer Auflistungsklasse. Es wird von den Klassen [CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md), [CStringRefElementTraits](../../atl/reference/cstringrefelementtraits-class.md)und [CStringElementTraitsI](../../atl/reference/cstringelementtraitsi-class.md)verwendet.

Weitere Informationen finden Sie unter [ATL-Auflistungsklassen](../../atl/atl-collection-classes.md).

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlcoll.h

## <a name="celementtraitsbasecopyelements"></a><a name="copyelements"></a>CElementTraitsBase::CopyElements

Rufen Sie diese Methode auf, um Elemente zu kopieren, die in einem Auflistungsklassenobjekt gespeichert sind.

```
static void CopyElements(
    T* pDest,
    const T* pSrc,
    size_t nElements);
```

### <a name="parameters"></a>Parameter

*pDest*<br/>
Zeigen Sie mit dem Zeiger auf das erste Element, das die kopierten Daten empfängt.

*pSrc*<br/>
Zeigen Sie mit dem Zeiger auf das erste zu kopierende Element.

*nElements*<br/>
Die Anzahl der zu kopierenden Elemente.

### <a name="remarks"></a>Bemerkungen

Die Quell- und Zielelemente sollten sich nicht überlappen.

## <a name="celementtraitsbaseinargtype"></a><a name="inargtype"></a>CElementTraitsBase::INARGTYPE

Der Datentyp, der zum Hinzufügen von Elementen zur Auflistung verwendet werden soll.

```
typedef const T& INARGTYPE;
```

## <a name="celementtraitsbaseoutargtype"></a><a name="outargtype"></a>CElementTraitsBase::OUTARGTYPE

Der Datentyp, der zum Abrufen von Elementen aus der Auflistung verwendet werden soll.

```
typedef T& OUTARGTYPE;
```

## <a name="celementtraitsbaserelocateelements"></a><a name="relocateelements"></a>CElementTraitsBase::RelocateElements

Rufen Sie diese Methode auf, um Elemente zu verschieben, die in einem Auflistungsklassenobjekt gespeichert sind.

```
static void RelocateElements(
    T* pDest,
    T* pSrc,
    size_t nElements);
```

### <a name="parameters"></a>Parameter

*pDest*<br/>
Zeigen Sie mit dem Zeiger auf das erste Element, das die zurückgesierten Daten empfängt.

*pSrc*<br/>
Zeigen Sie mit dem Zeiger auf das erste zu verschiebende Element.

*nElements*<br/>
Die Anzahl der zu verschiebenden Elemente.

### <a name="remarks"></a>Bemerkungen

Diese Methode ruft [memmove](../../c-runtime-library/reference/memmove-wmemmove.md)auf, was für die meisten Datentypen ausreicht. Wenn die verschobenen Objekte Zeiger auf ihre eigenen Member enthalten, muss diese Methode überschrieben werden.

## <a name="see-also"></a>Siehe auch

[Klassenübersicht](../../atl/atl-class-overview.md)
