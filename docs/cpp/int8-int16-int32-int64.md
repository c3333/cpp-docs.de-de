---
title: __int8, __int16, __int32, __int64
ms.date: 10/09/2018
f1_keywords:
- __int8_cpp
- __int16_cpp
- __int32_cpp
- __int64_cpp
- __int8
- __int16
- __int32
- __int64
- _int8
- _int16
- _int32
- _int64
helpviewer_keywords:
- __int16 keyword [C++]
- integer data type [C++], integer types in C++
- __int32 keyword [C++]
- integer types [C++]
- __int8 keyword [C++]
- __int64 keyword [C++]
ms.assetid: 8e384602-2578-4980-8cc8-da63842356b2
ms.openlocfilehash: 7888a282fffbaa2a23783c3875e02838fd0b1826
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227399"
---
# <a name="__int8-__int16-__int32-__int64"></a>__int8, __int16, __int32, __int64

**Microsoft-spezifisch**

Microsoft C/C++ bietet Unterstützung für ganzzahlige Typen mit angegebener Größe. Sie können 8-, 16-, 32-oder 64-Bit-ganzzahlige Variablen deklarieren, indem Sie den **`__intN`** Typspezifizierer verwenden, wobei ***`N`*** 8, 16, 32 oder 64 ist.

Im folgenden Beispiel wird eine Variable für jeden dieser Typen von ganzen Zahlen mit angegebener Größe deklariert:

```cpp
__int8 nSmall;      // Declares 8-bit integer
__int16 nMedium;    // Declares 16-bit integer
__int32 nLarge;     // Declares 32-bit integer
__int64 nHuge;      // Declares 64-bit integer
```

Die Typen **`__int8`** , **`__int16`** und **`__int32`** sind Synonyme für die ANSI-Typen, die die gleiche Größe aufweisen, und eignen sich zum Schreiben von portablen Code, der sich auf mehreren Plattformen identisch verhält. Der **`__int8`** -Datentyp ist ein Synonym für den Typ **`char`** , **`__int16`** ist mit dem Typ Synonym **`short`** und **`__int32`** ist mit dem Typ Synonym **`int`** . Der **`__int64`** Typ ist ein Synonym für den Typ **`long long`** .

Aus Kompatibilitätsgründen mit früheren **`_int8`** Versionen **`_int16`** sind,, **`_int32`** und **`_int64`** Synonyme für **`__int8`** , **`__int16`** , und, **`__int32`** **`__int64`** es sei denn, die Compileroption [ `/Za` \( Spracherweiterungen deaktivieren)](../build/reference/za-ze-disable-language-extensions.md) ist angegeben.

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt, dass ein `__intN` Parameter zu herauf gestuft wird **`int`** :

```cpp
// sized_int_types.cpp

#include <stdio.h>

void func(int i) {
    printf_s("%s\n", __FUNCTION__);
}

int main()
{
    __int8 i8 = 100;
    func(i8);   // no void func(__int8 i8) function
                // __int8 will be promoted to int
}
```

```Output
func
```

## <a name="see-also"></a>Siehe auch

[Schlüsselwörter](../cpp/keywords-cpp.md)<br/>
[Integrierte Typen](../cpp/fundamental-types-cpp.md)<br/>
[Datentypbereiche](../cpp/data-type-ranges.md)<br/>
