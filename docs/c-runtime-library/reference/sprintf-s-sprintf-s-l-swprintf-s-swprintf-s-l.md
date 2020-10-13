---
title: sprintf_s, _sprintf_s_l, swprintf_s, _swprintf_s_l
ms.date: 11/04/2016
api_name:
- _swprintf_s_l
- _sprintf_s_l
- swprintf_s
- sprintf_s
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
- ntoskrnl.exe
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- swprintf_s
- sprintf_s
- stdio/sprintf_s
- stdio/swprintf_s
- stdio/_sprintf_s_l
- stdio/_swprintf_s_l
- _sprintf_s_l
- _swprintf_s_l
helpviewer_keywords:
- stprintf_s function
- stprintf_s_l function
- swprintf_s_l function
- sprintf_s function
- swprintf_s function
- _swprintf_s_l function
- sprintf_s_l function
- _stprintf_s_l function
- _stprintf_s function
- _sprintf_s_l function
- formatted text [C++]
ms.assetid: 424f0a29-22ef-40e8-b565-969f5f57782f
ms.openlocfilehash: 006b0f84494466b5c23a8c86f586774b66839b03
ms.sourcegitcommit: 43cee7a0d41a062661229043c2f7cbc6ace17fa3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/13/2020
ms.locfileid: "92008834"
---
# <a name="sprintf_s-_sprintf_s_l-swprintf_s-_swprintf_s_l"></a>sprintf_s, _sprintf_s_l, swprintf_s, _swprintf_s_l

Schreiben Sie formatierte Daten in eine Zeichenfolge. Dies sind Versionen von [sprintf, _sprintf_l, swprintf, _swprintf_l, \__swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md) mit Sicherheitsverbesserungen, wie in [Sicherheitsfunktionen in der CRT](../../c-runtime-library/security-features-in-the-crt.md) beschrieben.

## <a name="syntax"></a>Syntax

```C
int sprintf_s(
   char *buffer,
   size_t sizeOfBuffer,
   const char *format,
   ...
);
int _sprintf_s_l(
   char *buffer,
   size_t sizeOfBuffer,
   const char *format,
   locale_t locale,
   ...
);
int swprintf_s(
   wchar_t *buffer,
   size_t sizeOfBuffer,
   const wchar_t *format,
   ...
);
int _swprintf_s_l(
   wchar_t *buffer,
   size_t sizeOfBuffer,
   const wchar_t *format,
   locale_t locale,
   ...
);
template <size_t size>
int sprintf_s(
   char (&buffer)[size],
   const char *format,
   ...
); // C++ only
template <size_t size>
int swprintf_s(
   wchar_t (&buffer)[size],
   const wchar_t *format,
   ...
); // C++ only
```

### <a name="parameters"></a>Parameter

*ert*<br/>
Speicherort für die Ausgabe

*sizeOfBuffer*<br/>
Die maximale Anzahl der zu speichernden Zeichen.

*format*<br/>
Formatsteuerzeichenfolge

*...*<br/>
Optionale Argumente, die formatiert werden müssen

*locale*<br/>
Das zu verwendende Gebietsschema.

Weitere Informationen finden Sie unter [Formatangaben](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).

## <a name="return-value"></a>Rückgabewert

Die Anzahl geschriebener Zeichen oder-1, wenn ein Fehler aufgetreten ist. Wenn der *Puffer* oder das *Format* ein NULL-Zeiger ist, geben **sprintf_s** und **swprintf_s** -1 zurück und legen **errno** auf **EINVAL**fest.

**sprintf_s** gibt die Anzahl von Bytes zurück, die im *Puffer*gespeichert werden, wobei das abschließende Null-Zeichen nicht gezählt wird. **swprintf_s** gibt die Anzahl der im *Puffer*gespeicherten breit Zeichen zurück, wobei das abschließende Null-breit Zeichen nicht gezählt wird.

## <a name="remarks"></a>Bemerkungen

Die **sprintf_s** -Funktion formatiert und speichert eine Reihe von Zeichen und Werten im *Puffer*. Jedes *Argument* (sofern vorhanden) wird entsprechend der entsprechenden Format Spezifikation im- *Format*konvertiert und ausgegeben. Das Format besteht aus normalen Zeichen und hat die gleiche Form und Funktion wie das *Format* -Argument für [printf](printf-printf-l-wprintf-wprintf-l.md). Ein NULL-Zeichen wird nach dem letzten geschriebenen Zeichen angefügt. Wenn der Kopiervorgang zwischen Zeichenfolgen ausgeführt wird, die sich überschneiden, ist das Verhalten nicht definiert.

Ein Hauptunterschied zwischen **sprintf_s** und [sprintf](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md) besteht darin, dass **sprintf_s** die Format Zeichenfolge auf gültige Formatierungszeichen überprüft, während [sprintf](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md) nur überprüft, ob die Format Zeichenfolge oder der Puffer **null** -Zeiger sind. Wenn bei einer der beiden Überprüfungen ein Fehler auftritt, wird der Handler für ungültige Parameter aufgerufen, wie in [Parameter Validation](../../c-runtime-library/parameter-validation.md)beschrieben. Wenn die weitere Ausführung zugelassen wird, gibt die Funktion-1 zurück und legt **errno** auf **EINVAL**fest.

Der andere Hauptunterschied zwischen **sprintf_s** und [sprintf](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md) besteht darin, dass **sprintf_s** einen length-Parameter annimmt, der die Größe des Ausgabepuffers in Zeichen angibt. Wenn der Puffer für den formatierten Text zu klein ist, einschließlich des abschließenden NULL-Werts, wird der Puffer auf eine leere Zeichenfolge festgelegt, indem ein NULL-Zeichen im *Puffer*[0] platziert wird, und der Handler für ungültige Parameter wird aufgerufen. Im Gegensatz zu **_snprintf**gewährleistet **sprintf_s** , dass der Puffer mit NULL endet, es sei denn, die Puffergröße ist 0 (null).

**swprintf_s** ist eine breit Zeichen Version von **sprintf_s**. die Zeigerargumente für **swprintf_s** sind Zeichen folgen mit breit Zeichen. Die Erkennung von Codierungs Fehlern in **swprintf_s** kann sich von der in **sprintf_s**unterscheiden. Die Versionen dieser Funktionen mit dem **_l** -Suffix sind beinahe identisch, verwenden jedoch den Gebiets Schema Parameter, der anstelle des aktuellen Thread Gebiets Schemas übergeben wurde.

In C++ wird die Verwendung dieser Funktionen durch Vorlagenüberladungen vereinfacht. Die Überladungen können automatisch Rückschlüsse auf die Pufferlänge ziehen (wodurch kein Größenargument mehr angegeben werden muss), und sie können automatisch die älteren, nicht sicheren Funktionen durch ihre neueren, sicheren Entsprechungen ersetzen. Weitere Informationen finden Sie unter [Sichere Vorlagenüberladungen](../../c-runtime-library/secure-template-overloads.md).

Es gibt Versionen von **sprintf_s** , die eine zusätzliche Kontrolle darüber bieten, was geschieht, wenn der Puffer zu klein ist. Weitere Informationen finden Sie unter [_snprintf_s, _snprintf_s_l, _snwprintf_s, _snwprintf_s_l](snprintf-s-snprintf-s-l-snwprintf-s-snwprintf-s-l.md).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|TCHAR.H-Routine|_UNICODE und _MBCS nicht definiert.|_MBCS definiert|_UNICODE definiert|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_stprintf_s**|**sprintf_s**|**sprintf_s**|**swprintf_s**|
|**_stprintf_s_l**|**_sprintf_s_l**|**_sprintf_s_l**|**_swprintf_s_l**|

## <a name="requirements"></a>Anforderungen

|-Routine zurückgegebener Wert|Erforderlicher Header|
|-------------|---------------------|
|**sprintf_s** **_sprintf_s_l**|Scher \<stdio.h><br /><br /> C++: \<cstdio> oder \<stdio.h>|
|**swprintf_s** **_swprintf_s_l**|C: \<stdio.h> oder \<wchar.h><br /><br /> C++: \<cstdio> , \<cwchar> \<stdio.h> oder \<wchar.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example-use-sprintf_s-to-format-data"></a>Beispiel: Verwenden von sprintf_s zum Formatieren von Daten

```C
// crt_sprintf_s.c
// This program uses sprintf_s to format various
// data and place them in the string named buffer.
//

#include <stdio.h>

int main( void )
{
   char  buffer[200], s[] = "computer", c = 'l';
   int   i = 35, j;
   float fp = 1.7320534f;

   // Format and print various data:
   j  = sprintf_s( buffer, 200,     "   String:    %s\n", s );
   j += sprintf_s( buffer + j, 200 - j, "   Character: %c\n", c );
   j += sprintf_s( buffer + j, 200 - j, "   Integer:   %d\n", i );
   j += sprintf_s( buffer + j, 200 - j, "   Real:      %f\n", fp );

   printf_s( "Output:\n%s\ncharacter count = %d\n", buffer, j );
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
// crt_swprintf_s.c
// wide character example
// also demonstrates swprintf_s returning error code
#include <stdio.h>

int main( void )
{
   wchar_t buf[100];
   int len = swprintf_s( buf, 100, L"%s", L"Hello world" );
   printf( "wrote %d characters\n", len );
   len = swprintf_s( buf, 100, L"%s", L"Hello\xffff world" );
   // swprintf_s fails because string contains WEOF (\xffff)
   printf( "wrote %d characters\n", len );
}
```

```Output
wrote 11 characters
wrote -1 characters
```

## <a name="see-also"></a>Siehe auch

[Stream-E/A](../../c-runtime-library/stream-i-o.md)<br/>
[fprintf, _fprintf_l, fwprintf, _fwprintf_l](fprintf-fprintf-l-fwprintf-fwprintf-l.md)<br/>
[printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[sprintf, _sprintf_l, swprintf, _swprintf_l, __swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[scanf, _scanf_l, wscanf, _wscanf_l](scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[sscanf, _sscanf_l, swscanf, _swscanf_l](sscanf-sscanf-l-swscanf-swscanf-l.md)<br/>
[vprintf-Funktionen](../../c-runtime-library/vprintf-functions.md)<br/>
