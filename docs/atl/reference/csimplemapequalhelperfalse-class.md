---
title: CSimpleMapEqualHelperFalse-Klasse
ms.date: 11/04/2016
f1_keywords:
- CSimpleMapEqualHelperFalse
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelperFalse
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelperFalse::IsEqualKey
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelperFalse::IsEqualValue
helpviewer_keywords:
- CSimpleMapEqualHelperFalse class
ms.assetid: a873eea3-e130-45cc-a476-61ee79511c3b
ms.openlocfilehash: b6bf1d4e3be849004e13e593fb5f4b5cb87f8123
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330735"
---
# <a name="csimplemapequalhelperfalse-class"></a>CSimpleMapEqualHelperFalse-Klasse

Diese Klasse ist ein Helfer für die [CSimpleMap-Klasse.](../../atl/reference/csimplemap-class.md)

## <a name="syntax"></a>Syntax

```
template <class TKey, class TVal>
class CSimpleMapEqualHelperFalse
```

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CSimpleMapEqualHelperFalse::IsEqualKey](#isequalkey)|(Statisch) Testet zwei Schlüssel für die Gleichheit.|
|[CSimpleMapEqualHelperFalse::IsEqualValue](#isequalvalue)|(Statisch) Gibt false zurück.|

## <a name="remarks"></a>Bemerkungen

Diese Merkmalsklasse ist eine `CSimpleMap` Ergänzung zur Klasse. Es bietet eine Methode zum Vergleichen `CSimpleMap` von zwei Elementen, die im Objekt enthalten sind, insbesondere zwei Wertelemente oder zwei Schlüsselelemente.

Der Wertvergleich gibt immer false zurück und `ATLASSERT` ruft darüber hinaus mit einem Argument von false auf, wenn jemals darauf verwiesen wird. In Situationen, in denen der Gleichheitstest nicht ausreichend definiert ist, ermöglicht diese Klasse, dass eine Karte mit Schlüssel-Wert-Paaren für die meisten Methoden ordnungsgemäß funktioniert, aber in einer genau definierten Weise für Methoden fehlschlägt, die von Vergleichen wie [CSimpleMap::FindVal](../../atl/reference/csimplemap-class.md#findval)abhängen.

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlsimpcoll.h

## <a name="csimplemapequalhelperfalseisequalkey"></a><a name="isequalkey"></a>CSimpleMapEqualHelperFalse::IsEqualKey

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

### <a name="remarks"></a>Bemerkungen

Diese Methode ruft [CSimpleArrayEqualHelper](../../atl/reference/csimplearrayequalhelper-class.md)auf.

## <a name="csimplemapequalhelperfalseisequalvalue"></a><a name="isequalvalue"></a>CSimpleMapEqualHelperFalse::IsEqualValue

Gibt false zurück.

```
static bool IsEqualValue(const TVal&, const TVal&);
```

### <a name="return-value"></a>Rückgabewert

Gibt false zurück.

### <a name="remarks"></a>Bemerkungen

Diese Methode gibt immer false `ATLASSERT` zurück und ruft mit dem Argument false auf, wenn jemals darauf verwiesen wird. Ziel ist `CSimpleMapEqualHelperFalse::IsEqualValue` es, Methoden mit Vergleichen zu zwingen, in einer genau definierten Weise fehlzuschlagen, wenn Gleichheitstests nicht ausreichend definiert wurden.

## <a name="see-also"></a>Siehe auch

[CSimpleMapEqualHelper-Klasse](../../atl/reference/csimplemapequalhelper-class.md)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)
