---
title: _STATIC_ASSERT-Makro
ms.date: 11/04/2016
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _STATIC_ASSERT
helpviewer_keywords:
- _STATIC_ASSERT macro
ms.assetid: 89b0350c-2c2f-4be6-9786-8b1f0780a5da
ms.openlocfilehash: 78544424b727797158109fa3000ee2ebf8066cf7
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229323"
---
# <a name="_static_assert-macro"></a>_STATIC_ASSERT-Makro

Wertet einen Ausdruck zur Kompilierzeit aus und generiert einen Fehler, wenn das Ergebnis " **false**" ist.

## <a name="syntax"></a>Syntax

```C
_STATIC_ASSERT(
    booleanExpression
);
```

### <a name="parameters"></a>Parameter

*booleanExpression*<br/>
Ausdruck (einschließlich Zeiger), der zu ungleich NULL (**true**) oder 0 (**false**) ausgewertet wird.

## <a name="remarks"></a>Bemerkungen

Dieses Makro ähnelt dem [_ASSERT und _ASSERTE Makros](assert-asserte-assert-expr-macros.md), mit dem Unterschied, dass *booleanExpression* zur Kompilierzeit statt zur Laufzeit ausgewertet wird. Wenn *booleanExpression* als **false** (0) ausgewertet wird, wird der [Compilerfehler C2466](../../error-messages/compiler-errors-1/compiler-error-c2466.md) generiert.

## <a name="example"></a>Beispiel

In diesem Beispiel überprüfen wir, ob der [sizeof](../../c-language/sizeof-operator-c.md) eines **`int`** größer oder gleich 2 Bytes ist und ob [sizeof](../../c-language/sizeof-operator-c.md) a **`long`** 1 Byte ist. Das Programm wird nicht kompiliert, und es wird ein [Compilerfehler generiert C2466](../../error-messages/compiler-errors-1/compiler-error-c2466.md) da ein **`long`** größer als 1 Byte ist.

```C
// crt__static_assert.c

#include <crtdbg.h>
#include <stdio.h>

_STATIC_ASSERT(sizeof(int) >= 2);
_STATIC_ASSERT(sizeof(long) == 1);  // C2466

int main()
{
    printf("I am sure that sizeof(int) will be >= 2: %d\n",
        sizeof(int));
    printf("I am not so sure that sizeof(long) == 1: %d\n",
        sizeof(long));
}
```

## <a name="requirements"></a>Requirements (Anforderungen)

|Makro|Erforderlicher Header|
|-----------|---------------------|
|**_STATIC_ASSERT**|\<crtdbg.h>|

## <a name="see-also"></a>Siehe auch

[Alphabetische Funktionsreferenz](crt-alphabetical-function-reference.md)<br/>
[_ASSERT, _ASSERTE _ASSERT_EXPR Makros](assert-asserte-assert-expr-macros.md)<br/>
