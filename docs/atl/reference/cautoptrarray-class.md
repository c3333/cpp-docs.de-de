---
title: Cautoptrarray-Klasse
ms.date: 11/04/2016
f1_keywords:
- CAutoPtrArray
- ATLCOLL/ATL::CAutoPtrArray
- ATLCOLL/ATL::CAutoPtrArray::CAutoPtrArray
helpviewer_keywords:
- CAutoPtrArray class
ms.assetid: 880a70da-8c81-4427-8ac6-49aa8d424244
ms.openlocfilehash: 11f39eac8b8d080fd840f6454f393e33ebcb9e1c
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "82167661"
---
# <a name="cautoptrarray-class"></a>Cautoptrarray-Klasse

Diese Klasse stellt Methoden bereit, die beim Erstellen eines Arrays von intelligenten Zeigern hilfreich sind.

> [!IMPORTANT]
> Diese Klasse und ihre Member können in Anwendungen, die im Windows-Runtime ausgeführt werden, nicht verwendet werden.

## <a name="syntax"></a>Syntax

```cpp
template <typename E>
class CAutoPtrArray : public CAtlArray<
                        ATL::CAutoPtr<E>,
                        CAutoPtrElementTraits<E>>
```

### <a name="parameters"></a>Parameter

*Fresser*<br/>
Der Zeigertyp.

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[Cautoptrarray:: cautoptrarray](#cautoptrarray)|Der Konstruktor.|

## <a name="remarks"></a>Bemerkungen

Diese Klasse stellt einen Konstruktor bereit und leitet Methoden [von "](../../atl/reference/catlarray-class.md) " für "", "" und " [cautoptrelementtrait](../../atl/reference/cautoptrelementtraits-class.md) " ab, um die Erstellung eines Sammlungs Klassen Objekts zu unterstützen, das intelligente Zeiger

Weitere Informationen finden Sie unter [ATL](../../atl/atl-collection-classes.md)-Auflistungs Klassen.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`CAtlArray`

`CAutoPtrArray`

## <a name="requirements"></a>Anforderungen

**Header:** atlcoll. h

## <a name="cautoptrarraycautoptrarray"></a><a name="cautoptrarray"></a>Cautoptrarray:: cautoptrarray

Der Konstruktor.

```cpp
CAutoPtrArray() throw();
```

### <a name="remarks"></a>Bemerkungen

Initialisiert das Array intelligenter Zeiger.

## <a name="see-also"></a>Weitere Informationen:

[Asslarray-Klasse](../../atl/reference/catlarray-class.md)<br/>
[Cautoptrelementtrait-Klasse](../../atl/reference/cautoptrelementtraits-class.md)<br/>
[Cautoptrlist-Klasse](../../atl/reference/cautoptrlist-class.md)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)
