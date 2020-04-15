---
title: CSimpleArrayEqualHelper-Klasse
ms.date: 11/04/2016
f1_keywords:
- CSimpleArrayEqualHelper
- ATLSIMPCOLL/ATL::CSimpleArrayEqualHelper
- ATLSIMPCOLL/ATL::CSimpleArrayEqualHelper::IsEqual
helpviewer_keywords:
- CSimpleArrayEqualHelper class
ms.assetid: a2b55d89-78c9-42ef-842c-5304c6d20ad6
ms.openlocfilehash: 386b005777b3e31dd74916a41bc5af2ab82df210
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330878"
---
# <a name="csimplearrayequalhelper-class"></a>CSimpleArrayEqualHelper-Klasse

Diese Klasse ist ein Helfer für die [CSimpleArray-Klasse.](../../atl/reference/csimplearray-class.md)

## <a name="syntax"></a>Syntax

```
template <class T>
class CSimpleArrayEqualHelper
```

#### <a name="parameters"></a>Parameter

*T*<br/>
Eine abgeleitete Klasse.

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CSimpleArrayEqualHelper::IsEqual](#isequal)|(Statisch) Testet `CSimpleArray` zwei Objektelemente auf Gleichheit.|

## <a name="remarks"></a>Bemerkungen

Diese Merkmalsklasse ist eine `CSimpleArray` Ergänzung zur Klasse. Es stellt eine Methode zum Vergleichen `CSimpleArray` von zwei Elementen bereit, die in einem Objekt gespeichert sind. Standardmäßig werden die Elemente mit **operator=()** verglichen, aber wenn das Array komplexe Datentypen enthält, denen ein eigener Gleichheitsoperator fehlt, müssen Sie diese Klasse überschreiben.

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlsimpcoll.h

## <a name="csimplearrayequalhelperisequal"></a><a name="isequal"></a>CSimpleArrayEqualHelper::IsEqual

Testet `CSimpleArray` zwei Objektelemente auf Gleichheit.

```
static bool IsEqual(
    const T& t1,
    const T& t2);
```

### <a name="parameters"></a>Parameter

*T1*<br/>
Ein Objekt des Typs T.

*t2*<br/>
Ein Objekt des Typs T.

### <a name="return-value"></a>Rückgabewert

Gibt true zurück, wenn die Elemente gleich sind, andernfalls false.

## <a name="see-also"></a>Siehe auch

[CSimpleArray-Klasse](../../atl/reference/csimplearray-class.md)<br/>
[CSimpleArrayEqualHelperFalse-Klasse](../../atl/reference/csimplearrayequalhelperfalse-class.md)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)
