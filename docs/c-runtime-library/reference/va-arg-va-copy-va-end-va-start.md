---
title: va_arg, va_copy, va_end, va_start
ms.date: 11/04/2016
api_name:
- va_arg
- va_end
- va_copy
- va_start
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
- va_arg
- va_start
- va_list
- va_alist
- va_dcl
- va_copy
- va_end
helpviewer_keywords:
- variable argument lists, accessing
- va_start macro
- va_arg macro
- va_end macro
- arguments [C++], argument lists
- va_list macro
- va_dcl macro
- va_alist macro
- va_copy macro
ms.assetid: a700dbbd-bfe5-4077-87b6-3a07af74a907
ms.openlocfilehash: d35cf3aea99b7e832afb7d2a8e0aaa9d008226fa
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231285"
---
# <a name="va_arg-va_copy-va_end-va_start"></a>va_arg, va_copy, va_end, va_start

Greift auf Variablenargumentelisten zu.

## <a name="syntax"></a>Syntax

```C
type va_arg(
   va_list arg_ptr,
   type
);
void va_copy(
   va_list dest,
   va_list src
); // (ISO C99 and later)
void va_end(
   va_list arg_ptr
);
void va_start(
   va_list arg_ptr,
   prev_param
); // (ANSI C89 and later)
void va_start(
   arg_ptr
);  // (deprecated Pre-ANSI C89 standardization version)
```

### <a name="parameters"></a>Parameter

*type*<br/>
Typ des abzurufenden Arguments.

*arg_ptr*<br/>
Zeiger auf die Liste der Argumente.

*dest*<br/>
Zeiger auf die Liste von Argumenten, die von *src* initialisiert werden sollen.

*src*<br/>
Ein Zeiger auf die initialisierte Liste von Argumenten, die nach " *dest*" kopiert werden sollen.

*prev_param*<br/>
Parameter, der dem ersten optionalen Argument vorausgeht.

## <a name="return-value"></a>Rückgabewert

**va_arg** gibt das aktuelle Argument zurück. **va_copy**, **va_start** und **va_end** geben keine Werte zurück.

## <a name="remarks"></a>Bemerkungen

Die Makros " **va_arg**", " **va_copy**", " **va_end**" und " **va_start** " bieten eine portablen Möglichkeit, auf die Argumente einer Funktion zuzugreifen, wenn die Funktion eine Variable Anzahl von Argumenten annimmt. Es gibt zwei Versionen der Makros: Die in STDARG.H definierten Makros, die mit dem ISO-Standard C99 konform sind, und die in VARARGS.H definierten Makros, die zwar als veraltet markiert sind, aber beibehalten werden, da sie für Code abwärts kompatibel sind, der vor dem ANSI-Standard C89 geschrieben wurde.

Diese Makros setzen voraus, dass die Funktion eine feste Anzahl von erforderlichen Argumenten akzeptiert, gefolgt von einer variablen Anzahl von optionalen Argumenten. Die erforderlichen Argumente werden als gewöhnliche Parameter für die Funktion deklariert und können über die Parameternamen aufgerufen werden. Die optionalen Argumente werden über Makros in STDARG.H (oder in VARARGS.H für Code, der vor dem ANSI-Standard C89 geschrieben wurde) aufgerufen, wodurch ein Zeiger auf das erste optionale Argument in der Argumentliste festgelegt wird und zurückgesetzt wird, nachdem das Verarbeiten der Argumente abgeschlossen ist.

Die in STDARG.H definierten C-Standardmakros werden wie folgt verwendet:

- **va_start** legt *arg_ptr* auf das erste optionale Argument in der Liste der Argumente fest, die an die Funktion übermittelt werden. Das Argument *arg_ptr* muss den **va_list** -Typ aufweisen. Das Argument *prev_param* ist der Name des erforderlichen Parameters, der dem ersten optionalen Argument in der Argumentliste direkt vorausgeht. Wenn *prev_param* mit der Register Speicher Klasse deklariert wird, ist das Verhalten des Makros nicht definiert. **va_start** müssen verwendet werden, bevor **va_arg** zum ersten Mal verwendet wird.

- **va_arg** Ruft einen Wert vom *Typ* aus dem Speicherort ab, der von *arg_ptr*angegeben wird, und Inkremente *arg_ptr* , um auf das nächste Argument in der Liste zu verweisen, indem die Größe des *Typs* verwendet wird, um zu bestimmen, wo das nächste Argument beginnt. **va_arg** können beliebig oft in der-Funktion verwendet werden, um Argumente aus der Liste abzurufen.

- **va_copy** erstellt eine Kopie einer Liste von Argumenten im aktuellen Zustand. Der *src* -Parameter muss bereits mit **va_start**initialisiert werden. Möglicherweise wurde Sie mit **va_arg** aufrufen aktualisiert, aber Sie darf nicht mit **va_end**zurückgesetzt worden sein. Das nächste Argument, das von **va_arg** vom *dest* abgerufen wird, ist das gleiche wie das nächste Argument, das von *src*abgerufen wird.

- Nachdem alle Argumente abgerufen wurden, setzt **va_end** den Zeiger auf **null**zurück. **va_end** müssen für jede Argumentliste aufgerufen werden, die mit **va_start** oder **va_copy** initialisiert wird, bevor die Funktion zurückgegeben wird.

> [!NOTE]
> Die in VARARGS.H definierten Makros sind als veraltet markiert und werden nur beibehalten, weil sie für Code abwärts kompatibel sind, der vor dem ANSI-Standard C89 geschrieben wurde. Verwenden Sie in allen anderen Fällen die Makros in STDARGS.H.

Da sie mithilfe von [/clr (CLR-Kompilierung, Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md) kompiliert werden, generieren Programme, die diese Makros verwenden, möglicherweise unerwartete Ergebnisse. Dies liegt an den Unterschieden zwischen nativen und CLR-Typsystemen (Common Language Runtime). Beachten Sie dieses Programm:

```C
#include <stdio.h>
#include <stdarg.h>

void testit (int i, ...)
{
    va_list argptr;
    va_start(argptr, i);

    if (i == 0)
    {
        int n = va_arg(argptr, int);
        printf("%d\n", n);
    }
    else
    {
        char *s = va_arg(argptr, char*);
        printf("%s\n", s);
    }

    va_end(argptr);
}

int main()
{
    testit(0, 0xFFFFFFFF); // 1st problem: 0xffffffff is not an int
    testit(1, NULL);       // 2nd problem: NULL is not a char*
}
```

Beachten Sie, dass **testit** erwartet, dass der zweite Parameter entweder ein **`int`** oder ein ist **`char*`** . Die zu über gebenden Argumente sind 0xFFFFFFFF ( **`unsigned int`** , nicht ein **`int`** ) und **null** (tatsächlich ein **`int`** , nicht ein **`char*`** ). Wenn das Programm für nativen Code kompiliert wird, erzeugt es diese Ausgabe:

```Output
-1

(null)
```

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** \<stdio.h> immer\<stdarg.h>

**Deprecated-Header:**\<varargs.h>

## <a name="libraries"></a>Bibliotheken

Alle Versionen [C-Laufzeitbibliotheken](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Beispiel

```C
// crt_va.c
// Compile with: cl /W3 /Tc crt_va.c
// The program below illustrates passing a variable
// number of arguments using the following macros:
//      va_start            va_arg              va_copy
//      va_end              va_list

#include <stdio.h>
#include <stdarg.h>
#include <math.h>

double deviation(int first, ...);

int main( void )
{
    /* Call with 3 integers (-1 is used as terminator). */
    printf("Deviation is: %f\n", deviation(2, 3, 4, -1 ));

    /* Call with 4 integers. */
    printf("Deviation is: %f\n", deviation(5, 7, 9, 11, -1));

    /* Call with just -1 terminator. */
    printf("Deviation is: %f\n", deviation(-1));
}

/* Returns the standard deviation of a variable list of integers. */
double deviation(int first, ...)
{
    int count = 0, i = first;
    double mean = 0.0, sum = 0.0;
    va_list marker;
    va_list copy;

    va_start(marker, first);     /* Initialize variable arguments. */
    va_copy(copy, marker);       /* Copy list for the second pass */
    while (i != -1)
    {
        sum += i;
        count++;
        i = va_arg(marker, int);
    }
    va_end(marker);              /* Reset variable argument list. */
    mean = sum ? (sum / count) : 0.0;

    i = first;                  /* reset to calculate deviation */
    sum = 0.0;
    while (i != -1)
    {
        sum += (i - mean)*(i - mean);
        i = va_arg(copy, int);
    }
    va_end(copy);               /* Reset copy of argument list. */
    return count ? sqrt(sum / count) : 0.0;
}
```

```Output
Deviation is: 0.816497
Deviation is: 2.236068
Deviation is: 0.000000
```

## <a name="see-also"></a>Weitere Informationen

[Argument Zugriff](../../c-runtime-library/argument-access.md)<br/>
[vfprintf, _vfprintf_l, vfwprintf, _vfwprintf_l](vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md)<br/>
