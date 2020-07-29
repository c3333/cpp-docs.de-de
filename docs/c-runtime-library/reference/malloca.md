---
title: _malloca
ms.date: 11/04/2016
api_name:
- _malloca
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
- malloca
- _malloca
helpviewer_keywords:
- memory allocation, stack
- malloca function
- _malloca function
ms.assetid: 293992df-cfca-4bc9-b313-0a733a6bb936
ms.openlocfilehash: d4604a6e2dfb00502e3c942c9735a077e1632843
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232494"
---
# <a name="_malloca"></a>_malloca

Belegt Speicher für den Stapel. Dies ist eine sicherere Version von [_alloca](alloca.md), wie in [Sicherheitsfunktionen in der CRT](../../c-runtime-library/security-features-in-the-crt.md) beschrieben wird.

## <a name="syntax"></a>Syntax

```C
void *_malloca(
   size_t size
);
```

### <a name="parameters"></a>Parameter

*size*<br/>
Bytes, die vom Stapel zugeordnet werden.

## <a name="return-value"></a>Rückgabewert

Die **_malloca** -Routine gibt einen **`void`** Zeiger auf den zugewiesenen Platz zurück, der für die Speicherung eines beliebigen Objekt Typs geeignet ist. Wenn die *Größe* 0 ist, weist **_malloca** ein Element der Länge 0 zu und gibt einen gültigen Zeiger auf dieses Element zurück.

Wenn die *Größe* größer als **_ALLOCA_S_THRESHOLD**ist, versucht **_malloca** , dem Heap zuzuordnen, und gibt einen NULL-Zeiger zurück, wenn der Speicherplatz nicht zugeordnet werden kann. Wenn die *Größe* kleiner oder gleich **_ALLOCA_S_THRESHOLD**ist, versucht **_malloca** , auf dem Stapel zuzuordnen, und es wird eine Stapelüberlauf Ausnahme generiert, wenn der Speicherplatz nicht zugeordnet werden kann. Die Stapelüberlauf Ausnahme ist keine C++-Ausnahme. Es handelt sich um eine strukturierte Ausnahme. Anstatt die C++-Ausnahmebehandlung zu verwenden, müssen Sie die [strukturierte Ausnahmebehandlung](../../cpp/structured-exception-handling-c-cpp.md) (SEH) verwenden, um diese Ausnahme abzufangen.

## <a name="remarks"></a>Bemerkungen

**_malloca** weist die *Größe* von Bytes aus dem Programm Stapel oder dem Heap zu, wenn die Anforderung eine bestimmte Größe in Bytes überschreitet, die von **_ALLOCA_S_THRESHOLD**angegeben wird. Der Unterschied zwischen **_malloca** und **_alloca** besteht darin, dass **_alloca** unabhängig von der Größe immer auf dem Stapel zugeordnet wird. Anders als bei **_alloca**, bei der **der frei** zugeordnete Speicher freigegeben werden kann, ist für **_malloca** die Verwendung von [_freea](freea.md) erforderlich, um Arbeitsspeicher freizugeben. Im Debugmodus weist **_malloca** immer Arbeitsspeicher vom Heap zu.

Es gibt Einschränkungen beim expliziten Aufrufen von **_malloca** in einem Ausnahmehandler (eh). EH-Routinen, die auf x86-Klasse-Prozessoren ausgeführt werden, arbeiten in ihrem eigenen Speicherrahmen: Sie führen Ihre Tasks im Speicherplatz aus, der nicht auf der aktuellen Position des Stapelzeigers der einschließenden Funktion basiert. Die am häufigsten verwendeten Implementierungen umfassen die strukturierte Windows NT-Ausnahmebehandlung (SEH) und C++-Catch-Klauselausdrücke. Daher führt das explizite Aufrufen von **_malloca** in einem der folgenden Szenarien zu einem Programmfehler während der Rückgabe an die aufrufenden eh-Routine:

- Ausnahme Filter Ausdruck für Windows NT SEH: **`__except`** ( `_malloca ()` )

- Abschließender Ausnahmehandler für Windows NT SEH: **`__finally`** { `_malloca ()` }

- C++-EH-Catch-Klauselausdruck

**_Malloca** können jedoch direkt innerhalb einer eh-Routine oder von einem von der Anwendung bereitgestellten Rückruf aufgerufen werden, der von einem der zuvor aufgelisteten eh-Szenarien aufgerufen wird.

> [!IMPORTANT]
> Wenn **_malloca** in Windows XP innerhalb eines try/catch-Blocks aufgerufen wird, müssen Sie [_resetstkoflw](resetstkoflw.md) im catch-Block aufrufen.

Zusätzlich zu den oben genannten Einschränkungen können **_malloca** nicht in-Blöcken verwendet werden, wenn die/CLR-Option [(Common Language Runtime-Kompilierung)](../../build/reference/clr-common-language-runtime-compilation.md) verwendet wird **`__except`** . Weitere Informationen finden Sie unter [/clr Restrictions](../../build/reference/clr-restrictions.md).

## <a name="requirements"></a>Anforderungen

|-Routine zurückgegebener Wert|Erforderlicher Header|
|-------------|---------------------|
|**_malloca**|\<malloc.h>|

## <a name="example"></a>Beispiel

```C
// crt_malloca_simple.c
#include <stdio.h>
#include <malloc.h>

void Fn()
{
   char * buf = (char *)_malloca( 100 );
   // do something with buf
   _freea( buf );
}

int main()
{
   Fn();
}
```

## <a name="example"></a>Beispiel

```C
// crt_malloca_exception.c
// This program demonstrates the use of
// _malloca and trapping any exceptions
// that may occur.

#include <windows.h>
#include <stdio.h>
#include <malloc.h>

int main()
{
    int     size;
    int     numberRead = 0;
    int     errcode = 0;
    void    *p = NULL;
    void    *pMarker = NULL;

    while (numberRead == 0)
    {
        printf_s("Enter the number of bytes to allocate "
                 "using _malloca: ");
        numberRead = scanf_s("%d", &size);
    }

    // Do not use try/catch for _malloca,
    // use __try/__except, since _malloca throws
    // Structured Exceptions, not C++ exceptions.

    __try
    {
        if (size > 0)
        {
            p =  _malloca( size );
        }
        else
        {
            printf_s("Size must be a positive number.");
        }
        _freea( p );
    }

    // Catch any exceptions that may occur.
    __except( GetExceptionCode() == STATUS_STACK_OVERFLOW )
    {
        printf_s("_malloca failed!\n");

        // If the stack overflows, use this function to restore.
        errcode = _resetstkoflw();
        if (errcode)
        {
            printf("Could not reset the stack!");
            _exit(1);
        }
    };
}
```

### <a name="input"></a>Eingabe

```Input
1000
```

### <a name="sample-output"></a>Beispielausgabe

```Output
Enter the number of bytes to allocate using _malloca: 1000
```

## <a name="see-also"></a>Weitere Informationen

[Speicher Belegung](../../c-runtime-library/memory-allocation.md)<br/>
[calloc](calloc.md)<br/>
[malloc](malloc.md)<br/>
[realloc](realloc.md)<br/>
[_resetstkoflw](resetstkoflw.md)<br/>
