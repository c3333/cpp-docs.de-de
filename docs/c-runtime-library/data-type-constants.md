---
title: Datentypkonstanten
ms.date: 06/25/2018
f1_keywords:
- FLT_MIN
- SHRT_MAX
- CHAR_MIN
- MB_LEN_MAX
- DBL_EPSILON
- SHRT_MIN
- _FLT_RADIX
- FLT_DIG
- FLT_MAX_10_EXP
- FLT_MANT_DIG
- DBL_MAX_EXP
- SCHAR_MIN
- SCHAR_MAX
- DBL_MIN
- FLT_MIN_10_EXP
- _DBL_ROUNDS
- USHRT_MAX
- FLT_MAX_EXP
- LONG_MAX
- DBL_MAX
- DBL_DIG
- FLT_MIN_EXP
- INT_MIN
- DBL_MIN_10_EXP
- CHAR_BIT
- INT_MAX
- ULONG_MAX
- DBL_MIN_EXP
- LONG_MIN
- _FLT_ROUNDS
- DBL_MANT_DIG
- _DBL_RADIX
- CHAR_MAX
- FLT_MAX
- DBL_MAX_10_EXP
- UCHAR_MAX
- FLT_EPSILON
- UINT_MAX
- LLONG_MIN
- LLONG_MAX
- ULLONG_MAX
- _I8_MIN
- _I8_MAX
- _UI8_MAX
- _I16_MIN
- _I16_MAX
- _UI16_MAX
- _I32_MIN
- _I32_MAX
- _UI32_MAX
- _I64_MIN
- _I64_MAX
- _UI64_MAX
- _I128_MIN
- _I128_MAX
- _UI128_MAX
- SIZE_MAX
- RSIZE_MAX
- LDBL_DIG
- LDBL_EPSILON
- LDBL_HAS_SUBNORM
- LDBL_MANT_DIG
- LDBL_MAX
- LDBL_MAX_10_EXP
- LDBL_MAX_EXP
- LDBL_MIN
- LDBL_MIN_10_EXP
- LDBL_MIN_EXP
- _LDBL_RADIX
- LDBL_TRUE_MIN
- DECIMAL_DIG
helpviewer_keywords:
- DBL_MAX_EXP constant
- _DBL_RADIX constant
- FLT_MIN_EXP constant
- DBL_EPSILON constant
- INT_MIN constant
- FLT_EPSILON constant
- DBL_MANT_DIG constant
- _FLT_RADIX constant
- DBL_MIN constant
- USHRT_MAX constant
- FLT_MAX_10_EXP constant
- _FLT_ROUNDS constant
- data type constants [C++]
- _DBL_ROUNDS constant
- CHAR_MAX constant
- FLT_MAX_EXP constant
- FLT_MIN constant
- CHAR_MIN constant
- FLT_MIN_10_EXP constant
- DBL_MIN_EXP constant
- SCHAR_MAX constant
- FLT_RADIX constant
- CHAR_BIT constant
- UCHAR_MAX constant
- DBL_RADIX constant
- FLT_ROUNDS constant
- LONG_MIN constant
- SHRT_MAX constant
- LONG_MAX constant
- DBL_MAX_10_EXP constant
- DBL_MIN_10_EXP constant
- INT_MAX constant
- constants [C++], data type
- ULONG_MAX constant
- FLT_DIG constant
- MB_LEN_MAX constant
- DBL_DIG constant
- SHRT_MIN constant
- DBL_MAX constant
- DBL_ROUNDS constant
- FLT_MAX constant
- UINT_MAX constant
- FLT_MANT_DIG constant
- SCHAR_MIN constant
- LLONG_MIN constant
- LLONG_MAX constant
- ULLONG_MAX constant
- _I8_MIN constant
- _I8_MAX constant
- _UI8_MAX constant
- _I16_MIN constant
- _I16_MAX constant
- _UI16_MAX constant
- _I32_MIN constant
- _I32_MAX constant
- _UI32_MAX constant
- _I64_MIN constant
- _I64_MAX constant
- _UI64_MAX constant
- _I128_MIN constant
- _I128_MAX constant
- _UI128_MAX constant
- SIZE_MAX constant
- RSIZE_MAX constant
ms.assetid: c0f1c405-0465-41d5-b5ff-e81cdb6f1622
ms.openlocfilehash: d9d053611fb733d55424d01be2bab030fc49e6e0
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215165"
---
# <a name="data-type-constants"></a>Datentypkonstanten

Datentypkonstanten sind von der Implementierung abhängige Wertbereiche, die für integrale und Gleitkommadatentypen zulässig sind.

## <a name="integral-type-constants"></a>Konstanten integraler Datentypen

Diese Konstanten geben den Bereich für die integralen Datentypen an. Um diese Konstanten zu verwenden, schließen Sie den „limits.h“-Header in Ihre Quelldatei ein:

```C
#include <limits.h>
```

> [!NOTE]
> Mit der- [`/J`](../build/reference/j-default-char-type-is-unsigned.md) Compileroption wird der **`char`** Standardtyp von **`signed char`** in geändert **`unsigned char`** .

|Konstante|Wert|BESCHREIBUNG|
|--------------|-----------|-------------|
|**CHAR_BIT**|8|Anzahl von Bits in einem**`char`**|
|**SCHAR_MIN**|(–128)|Minimal **`signed char`** Wert|
|**SCHAR_MAX**|127|Maximal **`signed char`** Wert|
|**UCHAR_MAX**|255 (0xff)|Maximal **`unsigned char`** Wert|
|**CHAR_MIN**|(-128) (0, wenn die **`/J`** Option verwendet wird)|Minimal **`char`** Wert|
|**CHAR_MAX**|127 (255 if- **`/J`** Option)|Maximal **`char`** Wert|
|**MB_LEN_MAX**|5|Maximale Anzahl von Bytes in Multibytezeichen**`char`**|
|**SHRT_MIN**|-32768|Minimal **`signed short`** Wert|
|**SHRT_MAX**|32767|Maximal **`signed short`** Wert|
|**USHRT_MAX**|65535 (0xffff)|Maximal **`unsigned short`** Wert|
|**INT_MIN**|(–2147483647 – 1)|Minimal **`signed int`** Wert|
|**INT_MAX**|2147483647|Maximal **`signed int`** Wert|
|**UINT_MAX**|4294967295 (0xffffffff)|Maximal **`unsigned int`** Wert|
|**LONG_MIN**|(–2147483647L – 1)|Minimal **`signed long`** Wert|
|**LONG_MAX**|2147483647L|Maximal **`signed long`** Wert|
|**ULONG_MAX**|4294967295UL (0xfffffffful)|Maximal **`unsigned long`** Wert|
|**LLONG_MIN**|(–9223372036854775807LL – 1)|Minimal **`signed long long`** oder **`__int64`** Wert|
|**LLONG_MAX**|9223372036854775807LL|Maximum **`signed long long`** oder **`__int64`** Wert|
|**ULLONG_MAX**|0xffffffffffffffffull|Maximal **`unsigned long long`** Wert|
|**_I8_MIN**|(-127i8 - 1)|8-Bit-Mindestwert (signed)|
|**_I8_MAX**|127i8|8-Bit-Höchstwert (signed)|
|**_UI8_MAX**|0xffui8|8-Bit-Höchstwert (unsigned)|
|**_I16_MIN**|(-32767i16 - 1)|16-Bit-Mindestwert (signed)|
|**_I16_MIN**|32767i16|16-Bit-Höchstwert (signed)|
|**_UI16_MAX**|0xffffui16|16-Bit-Höchstwert (unsigned)|
|**_I32_MIN**|(-2147483647i32 - 1)|32-Bit-Mindestwert (signed)|
|**_I32_MAX**|2147483647i32|32-Bit-Höchstwert (signed)|
|**_UI32_MAX**|0xffffffffui32|32-Bit-Höchstwert (unsigned)|
|**_I64_MIN**|(-9223372036854775807 - 1)|64-Bit-Mindestwert (signed)|
|**_I64_MAX**|9223372036854775807|64-Bit-Höchstwert (signed)|
|**_UI64_MAX**|0xffffffffffffffffui64|64-Bit-Höchstwert (unsigned)|
|**_I128_MIN**|(-170141183460469231731687303715884105727i128 - 1)|128-Bit-Mindestwert (signed)|
|**_I128_MAX**|170141183460469231731687303715884105727i128|128-Bit-Höchstwert (signed)|
|**_UI128_MAX**|0xffffffffffffffffffffffffffffffffui128|128-Bit-Höchstwert (unsigned)|
|**SIZE_MAX**|das gleiche wie **_UI64_MAX**, wenn **_WIN64** definiert ist, oder **UINT_MAX**|Maximale Größe eines nativen Integerwerts|
|**RSIZE_MAX**|das gleich wie (**SIZE_MAX** >> 1)|Maximale Größe eines sicheren Bibliotheksintegers|

## <a name="floating-point-type-constants"></a>Gleitkommatypkonstanten

Die folgenden Konstanten gibt den Bereich und andere Eigenschaften der **`long double`** **`double`** Datentypen, und an **`float`** . Um diese Konstanten zu verwenden, schließen Sie den „float.h“-Header in Ihre Quelldatei ein:

```C
#include <float.h>
```

|Konstante|Wert|BESCHREIBUNG|
|--------------|-----------|-----------------|
|**DBL_DECIMAL_DIG**|17|Anzahl der Dezimalstellen der Rundungsgenauigkeit|
|**DBL_DIG**|15|Anzahl der Dezimalstellen der Genauigkeit|
|**DBL_EPSILON**|2.2204460492503131e-016|Am kleinsten, sodass 1.0 + **DBL_EPSILON** != 1.0|
|**DBL_HAS_SUBNORM**|1|Der Typ unterstützt subnormale (denormale) Zahlen|
|**DBL_MANT_DIG**|53|Anzahl der Bits in Signifikanden (Mantissen)|
|**DBL_MAX**|1.7976931348623158e+308|Maximalwert|
|**DBL_MAX_10_EXP**|308|Der höchstmögliche dezimale Exponent|
|**DBL_MAX_EXP**|1024|Der höchstmögliche binäre Exponent|
|**DBL_MIN**|2.2250738585072014e-308|Regulärer positiver Mindestwert|
|**DBL_MIN_10_EXP**|(-307)|Der dezimale Mindestwert|
|**DBL_MIN_EXP**|(-1021)|Der binäre Mindestwert|
|**_DBL_RADIX**|2|Die Exponentenbasis|
|**DBL_TRUE_MIN**|4.9406564584124654e-324|Positiver subnormaler Mindestwert|
|**FLT_DECIMAL_DIG**|9|Anzahl der Dezimalstellen der Rundungsgenauigkeit|
|**FLT_DIG**|6|Anzahl der Dezimalstellen der Genauigkeit|
|**FLT_EPSILON**|1.192092896e-07F|Am kleinsten, sodass 1.0 + **FLT_EPSILON** != 1.0|
|**FLT_HAS_SUBNORM**|1|Der Typ unterstützt subnormale (denormale) Zahlen|
|**FLT_MANT_DIG**|24|Anzahl der Bits in Signifikanden (Mantissen)|
|**FLT_MAX**|3.402823466e+38F|Maximalwert|
|**FLT_MAX_10_EXP**|38|Der höchstmögliche dezimale Exponent|
|**FLT_MAX_EXP**|128|Der höchstmögliche binäre Exponent|
|**FLT_MIN**|1.175494351e-38F|Regulärer positiver Mindestwert|
|**FLT_MIN_10_EXP**|(-37)|Der dezimale Mindestwert|
|**FLT_MIN_EXP**|(-125)|Der binäre Mindestwert|
|**FLT_RADIX**|2|Die Exponentenbasis|
|**FLT_TRUE_MIN**|1.401298464e-45F|Positiver subnormaler Mindestwert|
|**LDBL_DIG**|15|Anzahl der Dezimalstellen der Genauigkeit|
|**LDBL_EPSILON**|2.2204460492503131e-016|Am kleinsten, sodass 1.0 + **LDBL_EPSILON** != 1.0|
|**LDBL_HAS_SUBNORM**|1|Der Typ unterstützt subnormale (denormale) Zahlen|
|**LDBL_MANT_DIG**|53|Anzahl der Bits in Signifikanden (Mantissen)|
|**LDBL_MAX**|1.7976931348623158e+308|Maximalwert|
|**LDBL_MAX_10_EXP**|308|Der höchstmögliche dezimale Exponent|
|**LDBL_MAX_EXP**|1024|Der höchstmögliche binäre Exponent|
|**LDBL_MIN**|2.2250738585072014e-308|Regulärer positiver Mindestwert|
|**LDBL_MIN_10_EXP**|(-307)|Der dezimale Mindestwert|
|**LDBL_MIN_EXP**|(-1021)|Der binäre Mindestwert|
|**_LDBL_RADIX**|2|Die Exponentenbasis|
|**LDBL_TRUE_MIN**|4.9406564584124654e-324|Positiver subnormaler Mindestwert|
|**DECIMAL_DIG**|das gleiche wie **DBL_DECIMAL_DIG**|Standard (doppelte) Dezimalstellen der Rundungsgenauigkeit|

## <a name="see-also"></a>Weitere Informationen

[Globale Konstanten](../c-runtime-library/global-constants.md)
