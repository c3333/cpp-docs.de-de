---
title: goto-Anweisung (C++)
ms.date: 11/04/2016
f1_keywords:
- goto_cpp
helpviewer_keywords:
- goto keyword [C++]
ms.assetid: 724c5deb-2de1-42d8-8ef1-23589d9bf5ed
ms.openlocfilehash: e56ebfadea0d643ac68e2ace722a39587bd01312
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223706"
---
# <a name="goto-statement-c"></a>goto-Anweisung (C++)

Die **`goto`** Anweisung überträgt die Steuerung bedingungslos an die Anweisung, die mit dem angegebenen Bezeichner bezeichnet wird.

## <a name="syntax"></a>Syntax

```
goto identifier;
```

## <a name="remarks"></a>Bemerkungen

Die bezeichnete Anweisung, die durch `identifier` angegeben wird, muss sich in der aktuellen Funktion befinden. Alle `identifier`-Namen sind Member eines internen Namespace und beeinträchtigen daher andere Bezeichner nicht.

Eine Anweisungsbezeichnung ist nur für eine- **`goto`** Anweisung sinnvoll; andernfalls werden Anweisungs Bezeichnungen ignoriert. Bezeichnungen können nicht erneut deklariert werden.

Eine- **`goto`** Anweisung darf die Steuerung nicht an einen Speicherort übertragen, der die Initialisierung einer Variablen überspringt, die sich im Gültigkeitsbereich dieses Speicher Orts befindet. Im folgenden Beispiel wird C2362 ausgelöst:

```cpp
int goto_fn(bool b)
{
    if (!b)
    {
        goto exit;  // C2362
    }
    else
    { /*...*/ }

    int error_code = 42;

exit:
    return error_code;
}
```

Es ist ein guter Programmierstil, die **`break`** **`continue`** -,-und-Anweisungen anstelle der-Anweisung zu verwenden, **`return`** **`goto`** Wenn dies möglich ist. Da die- **`break`** Anweisung jedoch nur von einer Ebene einer Schleife beendet wird, müssen Sie möglicherweise eine- **`goto`** Anweisung verwenden, um eine tief geschachtelte Schleife zu beenden.

Weitere Informationen zu Bezeichnungen und zur- **`goto`** Anweisung finden Sie unter [bezeichnete Anweisungen](../cpp/labeled-statements.md).

## <a name="example"></a>Beispiel

In diesem Beispiel überträgt eine- **`goto`** Anweisung die Steuerung an den Punkt mit der Bezeichnung, `stop` Wenn `i` 3 entspricht.

```cpp
// goto_statement.cpp
#include <stdio.h>
int main()
{
    int i, j;

    for ( i = 0; i < 10; i++ )
    {
        printf_s( "Outer loop executing. i = %d\n", i );
        for ( j = 0; j < 2; j++ )
        {
            printf_s( " Inner loop executing. j = %d\n", j );
            if ( i == 3 )
                goto stop;
        }
    }

    // This message does not print:
    printf_s( "Loop exited. i = %d\n", i );

    stop:
    printf_s( "Jumped to stop. i = %d\n", i );
}
```

```Output
Outer loop executing. i = 0
Inner loop executing. j = 0
Inner loop executing. j = 1
Outer loop executing. i = 1
Inner loop executing. j = 0
Inner loop executing. j = 1
Outer loop executing. i = 2
Inner loop executing. j = 0
Inner loop executing. j = 1
Outer loop executing. i = 3
Inner loop executing. j = 0
Jumped to stop. i = 3
```

## <a name="see-also"></a>Siehe auch

[Sprunganweisungen](../cpp/jump-statements-cpp.md)<br/>
[Schlüsselwörter](../cpp/keywords-cpp.md)
