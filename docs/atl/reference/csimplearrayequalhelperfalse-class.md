---
title: CSimpleArrayEqualHelperFalse-Klasse
ms.date: 11/04/2016
f1_keywords:
- CSimpleArrayEqualHelperFalse
- ATLSIMPCOLL/ATL::CSimpleArrayEqualHelperFalse
- ATLSIMPCOLL/ATL::CSimpleArrayEqualHelperFalse::IsEqual
helpviewer_keywords:
- CSimpleArrayEqualHelperFalse class
ms.assetid: 6918af6f-d23d-49eb-8482-c44272f5ffeb
ms.openlocfilehash: 5eca3145d64895e34b599fbf83834af142b65973
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330891"
---
# <a name="csimplearrayequalhelperfalse-class"></a>CSimpleArrayEqualHelperFalse-Klasse

Diese Klasse ist ein Helfer für die [CSimpleArray-Klasse.](../../atl/reference/csimplearray-class.md)

## <a name="syntax"></a>Syntax

```
template <class T>
class CSimpleArrayEqualHelperFalse
```

#### <a name="parameters"></a>Parameter

*T*<br/>
Eine abgeleitete Klasse.

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CSimpleArrayEqualHelperFalse::IsEqual](#isequal)|(Statisch) Gibt false zurück.|

## <a name="remarks"></a>Bemerkungen

Diese Merkmalsklasse ist eine `CSimpleArray` Ergänzung zur Klasse. Es gibt immer false zurück und `ATLASSERT` ruft darüber hinaus mit einem Argument von false auf, wenn jemals darauf verwiesen wird. In Situationen, in denen der Gleichheitstest nicht ausreichend definiert ist, ermöglicht diese Klasse, dass ein Array, das Elemente enthält, für die meisten Methoden ordnungsgemäß funktioniert, aber in einer genau definierten Weise für Methoden fehlschlägt, die von Vergleichen wie [CSimpleArray::Find](../../atl/reference/csimplearray-class.md#find)abhängen.

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlsimpcoll.h

## <a name="csimplearrayequalhelperfalseisequal"></a><a name="isequal"></a>CSimpleArrayEqualHelperFalse::IsEqual

Gibt false zurück.

```
static bool IsEqual(const T&, const T&);
```

### <a name="return-value"></a>Rückgabewert

Gibt false zurück.

### <a name="remarks"></a>Bemerkungen

Diese Methode gibt immer false `ATLASSERT` zurück und ruft mit einem Argument von false auf, wenn auf sie verwiesen wird. Ziel ist `CSimpleArrayEqualHelperFalse::IsEqual` es, Methoden mit Vergleichen zu zwingen, in einer genau definierten Weise fehlzuschlagen, wenn Gleichheitstests nicht ausreichend definiert wurden.

## <a name="see-also"></a>Siehe auch

[CSimpleArrayEqualHelper-Klasse](../../atl/reference/csimplearrayequalhelper-class.md)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)
