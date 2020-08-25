---
title: independent_bits_engine-Klasse
ms.date: 11/04/2016
f1_keywords:
- random/std::independent_bits_engine
helpviewer_keywords:
- independent_bits_engine class
ms.assetid: 889e9a82-f457-49a7-9d2e-26e0fc3cd907
ms.openlocfilehash: f9c1c97795e6d4eeff64ba8be8f22602f4f3fbd6
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88845769"
---
# <a name="independent_bits_engine-class"></a>independent_bits_engine-Klasse

Generiert eine zufällige Zahlensequenz mit einer angegebenen Anzahl von Bits, indem Bits aus von der Basis-Engine zurückgegebenen Werten erneut verpackt werden.

## <a name="syntax"></a>Syntax

```cpp
template <class Engine, size_t W, class UIntType>
class independent_bits_engine;
```

### <a name="parameters"></a>Parameter

*Ge*\
Der Typ der Basis-Engine.

*Löw*\
**Wortgröße**. Größe jeder generierten Zahl in Bits. **Vorbedingung**: `0 < W ≤ numeric_limits<UIntType>::digits`

*Uinttype*\
Der unsigned integer-Ergebnistyp. Informationen zu möglichen Typen finden Sie unter [\<random>](../standard-library/random.md) .

## <a name="members"></a>Member

`independent_bits_engine::independent_bits_engine`\
`independent_bits_engine::base`\
`independent_bits_engine::base_type`\
`independent_bits_engine::discard`\
`independent_bits_engine::operator()`\
`independent_bits_engine::seed`

Weitere Informationen zu Engine-Membern finden Sie unter [\<random>](../standard-library/random.md) .

## <a name="remarks"></a>Bemerkungen

Diese Klassen Vorlage beschreibt einen *Engine-Adapter* , der Werte erzeugt, indem Bits aus den Werten, die von der Basis-Engine zurückgegeben werden, wieder hergestellt werden, was zu *W*-Bit-Werten führt.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<random>

**Namespace:** std

## <a name="see-also"></a>Weitere Informationen

[\<random>](../standard-library/random.md)
