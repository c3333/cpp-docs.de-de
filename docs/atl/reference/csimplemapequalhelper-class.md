---
title: CSimpleMapEqualHelper-Klasse
ms.date: 11/04/2016
f1_keywords:
- CSimpleMapEqualHelper
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelper
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelper::IsEqualKey
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelper::IsEqualValue
helpviewer_keywords:
- CSimpleMapEqualHelper class
ms.assetid: 9bb2968a-d609-405c-8272-ff3b42df6164
ms.openlocfilehash: d137a35a517ea93139f036f6e9a7a8de06d518a7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330748"
---
# <a name="csimplemapequalhelper-class"></a>CSimpleMapEqualHelper-Klasse

Diese Klasse ist ein Helfer für die [CSimpleMap-Klasse.](../../atl/reference/csimplemap-class.md)

## <a name="syntax"></a>Syntax

```
template <class TKey, class TVal>
class CSimpleMapEqualHelper
```

#### <a name="parameters"></a>Parameter

*TKey*<br/>
Das Schlüsselelement.

*TVal*<br/>
Das Wertelement.

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CSimpleMapEqualHelper::IsEqualKey](#isequalkey)|(Statisch) Testet zwei Schlüssel für die Gleichheit.|
|[CSimpleMapEqualHelper::IsEqualValue](#isequalvalue)|(Statisch) Testet zwei Werte für Gleichheit.|

## <a name="remarks"></a>Bemerkungen

Diese Merkmalsklasse ist eine `CSimpleMap` Ergänzung zur Klasse. Es bietet Methoden zum `CSimpleMap` Vergleichen von zwei Objektelementen (insbesondere der Schlüssel- und Wertkomponenten) für die Gleichheit. Standardmäßig werden die Schlüssel und Werte mit **operator==()** verglichen, aber wenn die Zuordnung komplexe Datentypen enthält, denen ein eigener Gleichheitsoperator fehlt, kann diese Klasse überschrieben werden, um die zusätzliche erforderliche Funktionalität bereitzustellen.

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlsimpcoll.h

## <a name="csimplemapequalhelperisequalkey"></a><a name="isequalkey"></a>CSimpleMapEqualHelper::IsEqualKey

Testet zwei Schlüssel für die Gleichheit.

```
static bool IsEqualKey(const TKey& k1, const TKey& k2);
```

### <a name="parameters"></a>Parameter

*k1*<br/>
Der erste Schlüssel.

*k2*<br/>
Der zweite Schlüssel.

### <a name="return-value"></a>Rückgabewert

Gibt true zurück, wenn die Schlüssel gleich und andernfalls false sind.

## <a name="csimplemapequalhelperisequalvalue"></a><a name="isequalvalue"></a>CSimpleMapEqualHelper::IsEqualValue

Testet zwei Werte für Gleichheit.

```
static bool IsEqualValue(const TVal& v1, const TVal& v2);
```

### <a name="parameters"></a>Parameter

*v1*<br/>
Der erste Wert.

*V2*<br/>
Der zweite Wert.

### <a name="return-value"></a>Rückgabewert

Gibt true zurück, wenn die Werte gleich sind, andernfalls false.

## <a name="see-also"></a>Siehe auch

[CSimpleMapEqualHelperFalse-Klasse](../../atl/reference/csimplemapequalhelperfalse-class.md)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)
