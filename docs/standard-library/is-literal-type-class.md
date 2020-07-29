---
title: is_literal_type-Klasse
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_literal_type
helpviewer_keywords:
- is_literal_type
ms.assetid: a03a4ebb-ee66-48d6-91bb-41cf72b2401f
ms.openlocfilehash: d5b750755f2499c89e91e497ed03244a11484871
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212253"
---
# <a name="is_literal_type-class"></a>is_literal_type-Klasse

Testet, ob ein Typ als **`constexpr`** Variable verwendet oder von Funktionen erstellt, verwendet oder zurückgegeben werden kann **`constexpr`** .

## <a name="syntax"></a>Syntax

```cpp
template <class T>
struct is_literal_type;
```

### <a name="parameters"></a>Parameter

*Bund*\
Der abzufragende Typ.

## <a name="remarks"></a>Bemerkungen

Eine Instanz des typprädikats ist "true", wenn der Typ " *T* " ein *Literaltyp*ist; andernfalls "false". Ein Literaltyp ist entweder **`void`** ein Skalartyp, ein Verweistyp, ein Array eines Literaltyps oder ein literalklassentyp. Ein literalklassentyp ist ein Klassentyp, der einen trivialen Dekonstruktor aufweist, entweder ein Aggregations Typ ist oder mindestens einen nicht verschiebbaren **`constexpr`** Konstruktor aufweist, und alle seine Basisklassen und nicht statischen Datenmember sind nicht flüchtige Literaltypen. Während der Typ eines Literals immer ein Literaltyp ist, enthält das Konzept eines Literaltyps alle Elemente, die der Compiler **`constexpr`** zur Kompilierzeit als ein auswerten kann.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<type_traits>

**Namespace:** std

## <a name="see-also"></a>Weitere Informationen

[<type_traits>](../standard-library/type-traits.md)
