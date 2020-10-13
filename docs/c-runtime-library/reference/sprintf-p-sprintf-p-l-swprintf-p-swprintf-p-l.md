---
title: _sprintf_p, _sprintf_p_l, _swprintf_p, _swprintf_p_l
ms.date: 11/04/2016
api_name:
- _sprintf_p
- _swprintf_p_l
- _swprintf_p
- _sprintf_p_l
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
- _sprintf_p
- _swprintf_p_l
- _sprintf_p_l
- _swprintf_p
- sprintf_p
- swprint_p_l
- swprintf_p
- swprintf_p_l
helpviewer_keywords:
- sprintf_p_l function
- swprintf_p function
- swprintf_p_l function
- _sprintf_p function
- _sprintf_p_l function
- _swprintf_p function
- sprintf_p function
- _stprintf_p function
- stprintf_p function
- _swprintf_p_l function
- stprintf_p_l function
- formatted text [C++]
- _stprintf_p_l function
ms.assetid: a2ae78e8-6b0c-48d5-87a9-ea2365b0693d
ms.openlocfilehash: c694567aa7554319d5821678a18c3b5392f89965
ms.sourcegitcommit: 43cee7a0d41a062661229043c2f7cbc6ace17fa3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/13/2020
ms.locfileid: "92008846"
---
# <a name="_sprintf_p-_sprintf_p_l-_swprintf_p-_swprintf_p_l"></a>_sprintf_p, _sprintf_p_l, _swprintf_p, _swprintf_p_l

Schreiben Sie formatierte Daten in eine Zeichenfolge mit der Möglichkeit, die Reihenfolge anzugeben, in der die Parameter in der Formatzeichenfolge verwendet werden.

## <a name="syntax"></a>Syntax

```C
int _sprintf_p(
   char *buffer,
   size_t sizeOfBuffer,
   const char *format [,
   argument_list]
);
int _sprintf_p_l(
   char *buffer,
   size_t sizeOfBuffer,
   const char *format,
   locale_t locale [,
   argument_list]
);
int _swprintf_p(
   wchar_t *buffer,
   size_t sizeOfBuffer,
   const wchar_t *format [,
   argument_list]
);
int _swprintf_p_l(
   wchar_t *buffer,
   size_t sizeOfBuffer,
   const wchar_t *format,
   locale_t locale [,
   argument_list]
);
```

### <a name="parameters"></a>Parameter

*ert*<br/>
Speicherort für die Ausgabe

*sizeOfBuffer*<br/>
Die maximale Anzahl der zu speichernden Zeichen.

*format*<br/>
Formatsteuerzeichenfolge.

*argument_list*<br/>
Optionale Argumente für die Format Zeichenfolge.

*locale*<br/>
Das zu verwendende Gebietsschema.

Weitere Informationen finden Sie unter [Formatangaben](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).

## <a name="return-value"></a>Rückgabewert

Die Anzahl geschriebener Zeichen oder-1, wenn ein Fehler aufgetreten ist.

## <a name="remarks"></a>Bemerkungen

Die **_sprintf_p** -Funktion formatiert und speichert eine Reihe von Zeichen und Werten im *Puffer*. Jedes Argument im *argument_list* (sofern vorhanden) wird entsprechend der entsprechenden Format Spezifikation im- *Format*konvertiert und ausgegeben. Das *Format* -Argument verwendet die [formatspezifikations Syntax für printf-und wprintf-Funktionen](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md). Ein NULL-Zeichen wird nach dem letzten geschriebenen Zeichen angefügt. Wenn der Kopiervorgang zwischen Zeichenfolgen ausgeführt wird, die sich überschneiden, ist das Verhalten nicht definiert. Der Unterschied zwischen **_sprintf_p** und **sprintf_s** besteht darin, dass **_sprintf_p** Positions Parameter unterstützt, wodurch die Reihenfolge angegeben werden kann, in der die Argumente in der Format Zeichenfolge verwendet werden. Weitere Informationen finden Sie unter [printf_p-Positionsparameter](../../c-runtime-library/printf-p-positional-parameters.md).

**_swprintf_p** ist eine breit Zeichen Version von **_sprintf_p**. die Zeigerargumente für **_swprintf_p** sind Zeichen folgen mit breit Zeichen. Die Erkennung von Codierungs Fehlern in **_swprintf_p** kann sich von der in **_sprintf_p**unterscheiden. **_swprintf_p** und **fwprintf_p** Verhalten sich identisch, außer dass **_swprintf_p** Ausgabe in eine Zeichenfolge anstatt in ein Ziel vom Typ **File**schreibt, und **_swprintf_p** erfordert den *count* -Parameter, um die maximale Anzahl der zu schreibenden Zeichen anzugeben. Die Versionen dieser Funktionen mit dem **_l** -Suffix sind beinahe identisch, verwenden jedoch den Gebiets Schema Parameter, der anstelle des aktuellen Thread Gebiets Schemas übergeben wurde.

**_sprintf_p** gibt die Anzahl von Bytes zurück, die im *Puffer*gespeichert werden, wobei das abschließende Null-Zeichen nicht gezählt wird. **_swprintf_p** gibt die Anzahl der im *Puffer*gespeicherten breit Zeichen zurück, wobei das abschließende Null-breit Zeichen nicht gezählt wird. Wenn der *Puffer* oder das *Format* ein NULL-Zeiger ist oder wenn die Format Zeichenfolge ungültige Formatierungszeichen enthält, wird der Handler für ungültige Parameter aufgerufen, wie in [Parameter Validierung](../../c-runtime-library/parameter-validation.md)beschrieben. Wenn die weitere Ausführung zugelassen wird, geben diese Funktionen-1 zurück und legen **errno** auf **EINVAL**fest.

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|TCHAR.H-Routine|_UNICODE und _MBCS nicht definiert.|_MBCS definiert|_UNICODE definiert|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_stprintf_p**|**_sprintf_p**|**_sprintf_p**|**_swprintf_p**|
|**_stprintf_p_l**|**_sprintf_p_l**|**_sprintf_p_l**|**_swprintf_p_l**|

## <a name="requirements"></a>Anforderungen

|-Routine zurückgegebener Wert|Erforderlicher Header|
|-------------|---------------------|
|**_sprintf_p** **_sprintf_p_l**|\<stdio.h>|
|**_swprintf_p** **_swprintf_p_l**|\<stdio.h> oder \<wchar.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example-use-_sprintf_p-to-format-data"></a>Beispiel: Verwenden von _sprintf_p zum Formatieren von Daten

```C
// crt_sprintf_p.c
// This program uses _sprintf_p to format various
// data and place them in the string named buffer.
//

#include <stdio.h>

int main( void )
{
    char     buffer[200],
            s[] = "computer", c = 'l';
    int      i = 35,
            j;
    float    fp = 1.7320534f;

    // Format and print various data:
    j  = _sprintf_p( buffer, 200,
                     "   String:    %s\n", s );
    j += _sprintf_p( buffer + j, 200 - j,
                     "   Character: %c\n", c );
    j += _sprintf_p( buffer + j, 200 - j,
                     "   Integer:   %d\n", i );
    j += _sprintf_p( buffer + j, 200 - j,
                     "   Real:      %f\n", fp );

    printf( "Output:\n%s\ncharacter count = %d\n",
            buffer, j );
}
```

```Output
Output:
   String:    computer
   Character: l
   Integer:   35
   Real:      1.732053

character count = 79
```

## <a name="example-error-code-handling"></a>Beispiel: Behandlung von Fehlercodes

```C
// crt_swprintf_p.c
// This is the wide character example which
// also demonstrates _swprintf_p returning
// error code.
#include <stdio.h>

#define BUFFER_SIZE 100

int main( void )
{
    wchar_t buffer[BUFFER_SIZE];
    int     len;

    len = _swprintf_p(buffer, BUFFER_SIZE, L"%2$s %1$d",
                      0, L" marbles in your head.");
    _printf_p( "Wrote %d characters\n", len );

    // _swprintf_p fails because string contains WEOF (\xffff)
    len = _swprintf_p(buffer, BUFFER_SIZE, L"%s",
                      L"Hello\xffff world" );
    _printf_p( "Wrote %d characters\n", len );
}
```

```Output
Wrote 24 characters
Wrote -1 characters
```

## <a name="see-also"></a>Siehe auch

[Stream-E/A](../../c-runtime-library/stream-i-o.md)<br/>
[_fprintf_p, _fprintf_p_l, _fwprintf_p, _fwprintf_p_l](fprintf-p-fprintf-p-l-fwprintf-p-fwprintf-p-l.md)<br/>
[fprintf, _fprintf_l, fwprintf, _fwprintf_l](fprintf-fprintf-l-fwprintf-fwprintf-l.md)<br/>
[_printf_p, _printf_p_l, _wprintf_p, _wprintf_p_l](printf-p-printf-p-l-wprintf-p-wprintf-p-l.md)<br/>
[printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[sprintf, _sprintf_l, swprintf, _swprintf_l, __swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[scanf, _scanf_l, wscanf, _wscanf_l](scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[sscanf, _sscanf_l, swscanf, _swscanf_l](sscanf-sscanf-l-swscanf-swscanf-l.md)<br/>
[sscanf_s, _sscanf_s_l, swscanf_s, _swscanf_s_l](sscanf-s-sscanf-s-l-swscanf-s-swscanf-s-l.md)<br/>
[vprintf-Funktionen](../../c-runtime-library/vprintf-functions.md)<br/>
[Printf_p Positions Parameter](../../c-runtime-library/printf-p-positional-parameters.md)<br/>
