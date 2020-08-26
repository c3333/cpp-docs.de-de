---
title: subtract_with_carry_engine-Klasse
ms.date: 11/04/2016
f1_keywords:
- random/std::subtract_with_carry_engine
- random/std::subtract_with_carry_engine::default_seed
- random/std::subtract_with_carry_engine::discard
- random/std::subtract_with_carry_engine::min
- random/std::subtract_with_carry_engine::max
- random/std::subtract_with_carry_engine::seed
helpviewer_keywords:
- std::subtract_with_carry_engine [C++]
- std::subtract_with_carry_engine [C++], default_seed
- std::subtract_with_carry_engine [C++], discard
- std::subtract_with_carry_engine [C++], min
- std::subtract_with_carry_engine [C++], max
- std::subtract_with_carry_engine [C++], seed
ms.assetid: 94a055f2-a620-4a22-ac34-c156924bab31
ms.openlocfilehash: cf82c4ca3ce995fa9a53dbea21293dc8515ff491
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88840907"
---
# <a name="subtract_with_carry_engine-class"></a>subtract_with_carry_engine-Klasse

Generiert eine zufällige Sequenz mithilfe des (verzögerten Fibonacci-)Algorithmus "subtract with carry".

## <a name="syntax"></a>Syntax

```cpp
template <class UIntType, size_t W, size_t S, size_t R>
class subtract_with_carry_engine;
```

### <a name="parameters"></a>Parameter

*Uinttype*\
Der unsigned integer-Ergebnistyp. Informationen zu möglichen Typen finden Sie unter [\<random>](../standard-library/random.md) .

*Löw*\
**Wortgröße**. Größe jedes einzelnen Wortes der Zustandssequenz in Bits. **Vorbedingung**: `0 < W ≤ numeric_limits<UIntType>::digits`

*Hymnen*\
**Kurze Verzögerung**. Anzahl der Ganzzahlwerte. **Vorbedingung**: `0 < S < R`

*R*\
**Lange Verzögerung**. Bestimmt die Wiederholungsrate in der generierten Serie.

## <a name="members"></a>Member

`subtract_with_carry_engine::subtract_with_carry_engine`
`subtract_with_carry_engine::max`\
`subtract_with_carry_engine::min`\
`subtract_with_carry_engine::discard`\
`subtract_with_carry_engine::operator()`\
`subtract_with_carry_engine::seed`

`default_seed` ist eine als `19780503u` definierte Memberkonstante, die als Standardparameterwert für `subtract_with_carry_engine::seed` und den Einzelwertkonstruktor verwendet wird.

Weitere Informationen zu Engine-Membern finden Sie unter [\<random>](../standard-library/random.md) .

## <a name="remarks"></a>Bemerkungen

Die `substract_with_carry_engine` Klassen Vorlage ist eine Verbesserung gegenüber der [linear_congruential_engine](../standard-library/linear-congruential-engine-class.md). Keines dieser Module ist so schnell oder gibt so hochqualitative Ergebnisse zurück wie das [mersenne_twister_engine](../standard-library/mersenne-twister-engine-class.md).

Diese Engine erzeugt Werte eines benutzerdefinierten ganzzahligen Typs ohne Vorzeichen unter Verwendung der Wiederholungs Beziehung ( *Period*) `x(i) = (x(i - R) - x(i - S) - cy(i - 1)) mod M` , wobei `cy(i)` den Wert hat, `1` `x(i - S) - x(i - R) - cy(i - 1) < 0` andernfalls `0` und `M` den Wert `2` <sup>W</sup>. Der Zustand der Engine ist ein Carry-Indikator Plus *R* -Werte. Diese Werte bestehen aus den letzten *r* -Werten, die zurückgegeben werden, wenn mindestens `operator()` *r* -Mal aufgerufen wurde, andernfalls den Werten, die `N` zurückgegeben wurden, und den letzten `R - N` Werten des Start Werts.

Das Vorlagenargument `UIntType` muss groß genug sein, um Werte bis zu `M - 1` zu enthalten.

Obwohl Sie direkt aus dieser Engine einen Generator konstruieren können, können Sie auch eine der voreingestellten Typdefinitionen verwenden:

`ranlux24_base`: Wird als Grundlage für `ranlux24` verwendet.
`typedef subtract_with_carry_engine<unsigned int, 24, 10, 24> ranlux24_base;`

`ranlux48_base`: Wird als Grundlage für `ranlux48` verwendet.
`typedef subtract_with_carry_engine<unsigned long long, 48, 5, 12> ranlux48_base;`

Ausführliche Informationen über den Algorithmus „subtract with carry engine“ erhalten Sie im Wikipedia-Artikel [Lagged Fibonacci generator (Kongruenzgenerator, in englischer Sprache)](https://en.wikipedia.org/wiki/Lagged_Fibonacci_generator).

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<random>

**Namespace:** std

## <a name="see-also"></a>Weitere Informationen

[\<random>](../standard-library/random.md)
