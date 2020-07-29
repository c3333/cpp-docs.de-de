---
title: alignment_of-Klasse
ms.date: 12/11/2019
f1_keywords:
- type_traits/std::alignment_of
helpviewer_keywords:
- alignment_of class
- alignment_of
ms.assetid: 4141c59a-f94e-41c4-93fd-9ea578b27387
ms.openlocfilehash: 5a90f481c33431d92f0f28405e6226863d2b3913
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87205014"
---
# <a name="alignment_of-class"></a>alignment_of-Klasse

Ruft die Ausrichtung des angegebenen Typs ab. Diese Struktur wird in Bezug auf implementiert [`alignof`](../cpp/alignment-cpp-declarations.md) . Verwenden **`alignof`** Sie direkt, wenn Sie einen Ausrichtungs Wert einfach Abfragen müssen. Verwenden `alignment_of` Sie, wenn Sie eine ganzzahlige Konstante benötigen, z. b. bei der tagverteilung.

## <a name="syntax"></a>Syntax

```cpp
template <class Ty>
struct alignment_of;
```

### <a name="parameters"></a>Parameter

*Genossenschaft*\
Der abzufragende Typ.

## <a name="remarks"></a>Bemerkungen

Die typabfrage enthält den Wert der Ausrichtung der *typität*.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<type_traits>

**Namespace:** std

## <a name="see-also"></a>Weitere Informationen

[`<type_traits>`](type-traits.md)\
[`aligned_storage`Klassi](aligned-storage-class.md)
