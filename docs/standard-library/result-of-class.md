---
title: result_of-Klasse
ms.date: 02/21/2019
f1_keywords:
- type_traits/std::result_of
- type_traits/std::result_of_t
- type_traits/std::result_of::type
helpviewer_keywords:
- std::result_of
- std::result_of_t
- std::result_of::type
ms.assetid: 5374a096-4b4a-4712-aa97-6852c5cdd6be
ms.openlocfilehash: 54806f965cc46058e3c82b4863bb45782abe079e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87202310"
---
# <a name="result_of-class"></a>result_of-Klasse

Bestimmt den Rückgabetyp des aufrufbaren Typs, der die angegebenen Argumenttypen akzeptiert. In c++ 14 hinzugefügt, veraltet in c++ 17.

## <a name="syntax"></a>Syntax

```cpp
template<class>
struct result_of; // Causes a static assert

template <class Fn, class... ArgTypes>
struct result_of<Fn(ArgTypes...)>;

// Helper type
template<class T>
   using result_of_t = typename result_of<T>::type;
```

### <a name="parameters"></a>Parameter

*Extreme*\
Der abzufragende, aufgerufene Typ.

*ArgTypes*\
Die Typen der Argumentliste für den aufrufbaren, abzufragenden Typ.

## <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Vorlage, um zur Kompilierzeit den Ergebnistyp `Fn` () zu bestimmen `ArgTypes` , bei dem *FN* ein Aufruf barer Typ ist, ein Verweis auf eine Funktion oder ein Verweis auf einen Aufruf baren Typ, der mit einer Argumentliste der Typen in *ArgTypes*aufgerufen wird. Der- `type` Member der Klassen Vorlage benennt den Ergebnistyp von, `decltype(std::invoke(declval<Fn>(), declval<ArgTypes>()...))` Wenn der nicht ausgewertete Ausdruck `std::invoke(declval<Fn>(), declval<ArgTypes>()...)` wohl geformt ist. Andernfalls hat die Klassen Vorlage keinen Member `type` . Der Typ *FN* und alle Typen im Parameter Paket " *ArgTypes* " müssen vollständige Typen sein, **`void`** oder Arrays mit unbekannter Grenze. Wird zugunsten von [invoke_result](invoke-result-class.md) in c++ 17 als veraltet markiert.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<type_traits>

**Namespace:** std

## <a name="see-also"></a>Weitere Informationen

[<type_traits>](../standard-library/type-traits.md)\
[invoke_result-Klasse](invoke-result-class.md)
