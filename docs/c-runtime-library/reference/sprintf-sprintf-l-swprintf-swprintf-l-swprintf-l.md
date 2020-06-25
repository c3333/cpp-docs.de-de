---
title: sprintf, _sprintf_l, swprintf, _swprintf_l, __swprintf_l
ms.date: 06/23/2020
api_name:
- __swprintf_l
- sprintf
- _sprintf_l
- _swprintf_l
- swprintf
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
- ntdll.dll
- ucrtbase.dll
- ntoskrnl.exe
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _stprintf_l
- __swprintf_l
- sprintf_l
- swprintf
- _sprintf_l
- sprintf
- _stprintf
- stprintf_l
helpviewer_keywords:
- _swprintf_l function
- _stprintf function
- __swprintf_l function
- stprintf function
- sprintf function
- _sprintf_l function
- _stprintf_l function
- swprintf function
- strings [C++], writing to
- _CRT_NON_CONFORMING_SWPRINTFS
- swprintf_l function
- stprintf_l function
- sprintf_l function
- formatted text [C++]
ms.assetid: f6efe66f-3563-4c74-9455-5411ed939b81
ms.openlocfilehash: 9a3f10fc89d93717edfb032dea910040589c1254
ms.sourcegitcommit: 8645408c7929558b8162f781776d0908d790a41c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/24/2020
ms.locfileid: "85334950"
---
# <a name="sprintf-_sprintf_l-swprintf-_swprintf_l-__swprintf_l"></a>sprintf, _sprintf_l, swprintf, _swprintf_l, __swprintf_l

Schreiben Sie formatierte Daten in eine Zeichenfolge. Sicherere Versionen einiger dieser Funktionen sind verfügbar; siehe [sprintf_s, _sprintf_s_l, swprintf_s, _swprintf_s_l](sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md). Die sicheren Versionen von " **tauprintf** " und " **_swprintf_l** " übernehmen die Größe des Puffers als Parameter.

## <a name="syntax"></a>Syntax

```C
int sprintf(
   char *buffer,
   const char *format [,
   argument] ...
);
int _sprintf_l(
   char *buffer,
   const char *format,
   locale_t locale [,
   argument] ...
);
int swprintf(
   wchar_t *buffer,
   size_t count,
   const wchar_t *format [,
   argument]...
);
int _swprintf_l(
   wchar_t *buffer,
   size_t count,
   const wchar_t *format,
   locale_t locale [,
   argument] ...
);
int __swprintf_l(
   wchar_t *buffer,
   const wchar_t *format,
   locale_t locale [,
   argument] ...
);
template <size_t size>
int sprintf(
   char (&buffer)[size],
   const char *format [,
   argument] ...
); // C++ only
template <size_t size>
int _sprintf_l(
   char (&buffer)[size],
   const char *format,
   locale_t locale [,
   argument] ...
); // C++ only
```

### <a name="parameters"></a>Parameter

*ert*<br/>
Speicherort für die Ausgabe

*count*<br/>
Maximale Anzahl, der in der Unicode-Version dieser Funktion zu speichernde Zeichen.

*format*<br/>
Formatsteuerzeichenfolge

*argument*<br/>
Optionale Argumente

*locale*<br/>
Das zu verwendende Gebietsschema.

Weitere Informationen finden Sie unter [Formatangaben](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).

## <a name="return-value"></a>Rückgabewert

Die Anzahl geschriebener Zeichen oder-1, wenn ein Fehler aufgetreten ist. Wenn *buffer* oder *Format* ein NULL-Zeiger ist, wird der Handler für ungültige Parameter aufgerufen, wie in [Parameter Validation (Parameter](../../c-runtime-library/parameter-validation.md)Überprüfung) beschrieben. Wenn die weitere Ausführung zugelassen wird, geben diese Funktionen-1 zurück und legen **errno** auf **EINVAL**fest.

**sprintf** gibt die Anzahl von Bytes zurück, die im *Puffer*gespeichert werden, wobei das abschließende Null-Zeichen nicht gezählt wird. " **tauprintf** " gibt die Anzahl der im *Puffer*gespeicherten breit Zeichen zurück, wobei das abschließende Null-breit Zeichen nicht gezählt wird.

## <a name="remarks"></a>Hinweise

Die **sprintf** -Funktion formatiert und speichert eine Reihe von Zeichen und Werten im *Puffer*. Jedes *Argument* (sofern vorhanden) wird entsprechend der entsprechenden Format Spezifikation im- *Format*konvertiert und ausgegeben. Das Format besteht aus normalen Zeichen und hat die gleiche Form und Funktion wie das *Format* -Argument für [printf](printf-printf-l-wprintf-wprintf-l.md). Ein NULL-Zeichen wird nach dem letzten geschriebenen Zeichen angefügt. Wenn der Kopiervorgang zwischen Zeichenfolgen ausgeführt wird, die sich überschneiden, ist das Verhalten nicht definiert.

> [!IMPORTANT]
> Mithilfe von **sprintf**gibt es keine Möglichkeit, die Anzahl der geschriebenen Zeichen einzuschränken. Dies bedeutet, dass der Code, der **sprintf** verwendet, für Pufferüberläufe anfällig ist. Verwenden Sie ggf. die verwandte Funktion [_snprintf](snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md), die eine maximale Anzahl von Zeichen angibt, die in den *Puffer*geschrieben werden sollen, oder verwenden Sie [_scprintf](scprintf-scprintf-l-scwprintf-scwprintf-l.md) , um zu bestimmen, wie groß ein Puffer ist. Stellen Sie außerdem sicher, dass das *Format* keine benutzerdefinierte Zeichenfolge ist.

" **tauprintf** " ist eine breit Zeichen Version von **sprintf**. die Zeigerargumente für " **tauprintf** " sind Zeichen folgen mit breit Zeichen. Die Erkennung von Codierungs Fehlern in " **tauprintf** " kann von **sprintf**abweichen. " **tauprintf** " und " **fwprintf** " Verhalten sich identisch, außer dass die Ausgabe von " **tauprintf** " in eine Zeichenfolge anstatt in ein Ziel vom Typ " **File**" geschrieben wird, und "WS- **f** " erfordert, dass der *count* -Parameter die maximale Anzahl von Zeichen Die Versionen dieser Funktionen mit dem **_l** -Suffix sind beinahe identisch, verwenden jedoch den Gebiets Schema Parameter, der anstelle des aktuellen Thread Gebiets Schemas übergeben wurde.

" **tauprintf** " entspricht dem ISO-C-Standard, der den zweiten Parameter " *count*" vom Typ " **size_t**" erfordert. Um das alte, nicht dem Standard entsprechende Verhalten zu erzwingen, definieren Sie **_CRT_NON_CONFORMING_SWPRINTFS**. In einer zukünftigen Version wird das alte Verhalten möglicherweise entfernt. Daher sollte Code so geändert werden, dass das neue konforme Verhalten verwendet wird.

In C++ haben diese Funktionen Vorlagenüberladungen, mit denen die neueren, sicheren Entsprechungen dieser Funktionen aufgerufen werden. Weitere Informationen finden Sie unter [Sichere Vorlagenüberladungen](../../c-runtime-library/secure-template-overloads.md).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|TCHAR.H-Routine|_UNICODE und _MBCS nicht definiert.|_MBCS definiert|_UNICODE definiert|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_stprintf**|**sprintf**|**sprintf**|**_swprintf**|
|**_stprintf_l**|**_sprintf_l**|**_sprintf_l**|**__swprintf_l**|

## <a name="requirements"></a>Anforderungen

|-Routine zurückgegebener Wert|Erforderlicher Header|
|-------------|---------------------|
|**sprintf**, **_sprintf_l**|\<stdio.h>|
|**swprintf** **_swprintf_l**|\<stdio.h> oder \<wchar.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt_sprintf.c
// compile with: /W3
// This program uses sprintf to format various
// data and place them in the string named buffer.

#include <stdio.h>

int main( void )
{
   char  buffer[200], s[] = "computer", c = 'l';
   int   i = 35, j;
   float fp = 1.7320534f;

   // Format and print various data:
   j  = sprintf( buffer,     "   String:    %s\n", s ); // C4996
   j += sprintf( buffer + j, "   Character: %c\n", c ); // C4996
   j += sprintf( buffer + j, "   Integer:   %d\n", i ); // C4996
   j += sprintf( buffer + j, "   Real:      %f\n", fp );// C4996
   // Note: sprintf is deprecated; consider using sprintf_s instead

   printf( "Output:\n%s\ncharacter count = %d\n", buffer, j );
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

## <a name="example"></a>Beispiel

```C
// crt_swprintf.c
// wide character example
// also demonstrates swprintf returning error code
#include <stdio.h>

int main( void )
{
   wchar_t buf[100];
   int len = swprintf( buf, 100, L"%s", L"Hello world" );
   printf( "wrote %d characters\n", len );
   len = swprintf( buf, 100, L"%s", L"Hello\xffff world" );
   // swprintf fails because string contains WEOF (\xffff)
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
[scanf, _scanf_l, wscanf, _wscanf_l](scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[sscanf, _sscanf_l, swscanf, _swscanf_l](sscanf-sscanf-l-swscanf-swscanf-l.md)<br/>
[vprintf-Funktionen](../../c-runtime-library/vprintf-functions.md)<br/>
