---
title: Schlüsselwort „_Static_assert“ und Makro „static_assert“ (C11)
description: In diesem Artikel werden das C11-Schlüsselwort „_Static_assert“ und das C11-Makro „static_assert“ beschrieben.
ms.date: 10/13/2020
f1_keywords:
- static_assert_c
- _Static_assert
helpviewer_keywords:
- assertions [C], _Static_assert, static_assert
ms.openlocfilehash: dbe49b1dcbb8dd4e0d9df678f4456bc605e01c3f
ms.sourcegitcommit: 651348f8cd92ab0d52f09e9225a7eb41562559db
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/14/2020
ms.locfileid: "92060976"
---
# <a name="_static_assert-keyword-and-static_assert-macro-c11"></a>Schlüsselwort „_Static_assert“ und Makro „static_assert“ (C11)

Hiermit wird eine Assertion zur Kompilierzeit getestet. Wenn der angegebene konstante Ausdruck **`false`** ist, zeigt der Compiler die angegebene Meldung an, und bei der Kompilierung tritt der Fehler C2338 auf. Andernfalls passiert nichts. Neu in C11.

**`_Static_assert`** ist ein Schlüsselwort, das in C11 eingeführt wurde.
**`static_assert`** ist ein in C11 eingeführtes Makro, das dem Schlüsselwort **`_Static_assert`** zugeordnet ist.

## <a name="syntax"></a>Syntax

```C
_Static_assert(constant-expression, string-literal);
static_assert(constant-expression, string-literal);
```

### <a name="parameters"></a>Parameter

*constant-expression* (konstanter Ausdruck)\
Hierbei handelt es sich um einen integralen konstanten Ausdruck, der zur Kompilierzeit ausgewertet werden kann. Wenn der Ausdruck 0 (false) ist, wird der *Zeichenfolgenliteral* -Parameter angezeigt, und bei der Kompilierung tritt ein Fehler auf. Wenn der Ausdruck nicht 0 (true) ist, passiert nichts.

*string-literal*\ (Zeichenfolgenliteral)
Hierbei handelt es sich um die Meldung, die angezeigt wird, wenn der *konstante Ausdruck* als 0 (false) ausgewertet wird. Sie muss mit dem [Basiszeichensatz](../c-language/ascii-character-set.md) des Compilers erstellt werden. Es dürfen keine [Multibyte-Zeichen oder Breitzeichen](../c-language/multibyte-and-wide-characters.md) verwendet werden.

## <a name="remarks"></a>Bemerkungen

Mit dem Schlüsselwort **`_Static_assert`** und dem Makro **`static_assert`** wird eine Softwareassertion zur Kompilierzeit getestet. Sie können für einen globalen Bereich oder einen Funktionsbereich verwendet werden.

Im Gegensatz dazu testen [das Makro „assert“und die Funktionen „_assert“ und „_wassert“](../c-runtime-library/reference/assert-macro-assert-wassert.md) Softwareassertionen zur Laufzeit und verursachen Laufzeitkosten.

**Microsoft-spezifisches Verhalten**

Wenn Sie in C kein `<assert.h>`-Element verwenden, behandelt der Microsoft Visual C/C++-Compiler **`static_assert`** als Schlüsselwort, das **`_Static_assert`** zugeordnet ist. Die Verwendung von **`static_assert`** wird bevorzugt, da derselbe Code dann sowohl in C als auch in C++ funktioniert.

## <a name="example-of-a-compile-time-assert"></a>Beispiel mit „assert“ zur Kompilierzeit

Im folgenden Beispiel werden **`static_assert`** und **`_Static_assert`** verwendet, um zu überprüfen, wie viele Elemente sich in einer Enumeration befinden und ob ganze Zahlen 32 Bit breit sind.

```C
// requires /std:c11 or higher
#include <assert.h>

enum Items
{
    A,
    B,
    C,
    LENGTH
};

int main()
{
    // _Static_assert is a C11 keyword
    _Static_assert(LENGTH == 3, "Expected Items enum to have three elements");

    // Preferred: static_assert maps to _Static_Assert and is compatible with C++
    static_assert(sizeof(int) == 4, "Expecting 32 bit integers"); 

    return 0;
}
```

## <a name="requirements"></a>Anforderungen

|Makro|Erforderlicher Header|
|-------------|---------------------|
|**`static_assert`**|\<assert.h>|

## <a name="see-also"></a>Siehe auch

[Makro „_STATIC_ASSERT“](../c-runtime-library/reference/static-assert-macro.md)\
[Makro „assert“ und Funktionen „_assert“ und „_wassert“](../c-runtime-library/reference/assert-macro-assert-wassert.md)
[/std (Angeben der Standardsprachversion)](../build/reference/std-specify-language-standard-version.md)