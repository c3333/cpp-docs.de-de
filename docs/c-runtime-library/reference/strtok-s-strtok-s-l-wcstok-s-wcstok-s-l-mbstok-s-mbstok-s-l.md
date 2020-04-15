---
title: strtok_s, _strtok_s_l, wcstok_s, _wcstok_s_l, _mbstok_s, _mbstok_s_l
ms.date: 4/2/2020
api_name:
- _wcstok_s_l
- _mbstok_s_l
- _mbstok_s
- strtok_s
- wcstok_s
- _strtok_s_l
- _o__mbstok_s
- _o__mbstok_s_l
- _o_strtok_s
- _o_wcstok_s
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
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-string-l1-1-0.dll
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _tcstok_s_l
- _wcstok_s_l
- _tcstok_s
- _mbstok_s_l
- strtok_s
- wcstok_s
- _mbstok_s
- _strtok_s_l
helpviewer_keywords:
- _strtok_s_l function
- _mbstok_s_l function
- strings [C++], searching
- mbstok_s_l function
- wcstok_s_l function
- _wcstok_s_l function
- _tcstok_s function
- _tcstok_s_l function
- strtok_s_l function
- wcstok_s function
- tokens, finding in strings
- mbstok_s function
- _mbstok_s function
- strtok_s function
ms.assetid: 7696c972-f83b-4617-8c82-95973e9fdb46
ms.openlocfilehash: 9fe89fb897a5459b16c49060359b4bb40bc062a7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365219"
---
# <a name="strtok_s-_strtok_s_l-wcstok_s-_wcstok_s_l-_mbstok_s-_mbstok_s_l"></a>strtok_s, _strtok_s_l, wcstok_s, _wcstok_s_l, _mbstok_s, _mbstok_s_l

Sucht das nächste Token in einer Zeichenfolge unter Verwendung des aktuellen Gebietsschemas oder eines Gebietsschemas, das übergeben wird. Diese Versionen von [strtok, _strtok_l, wcstok, _wcstok_l, _mbstok, _mbstok_l](strtok-strtok-l-wcstok-wcstok-l-mbstok-mbstok-l.md) enthalten Sicherheitsverbesserungen, wie unter [Sicherheitsfunktionen in der CRT](../../c-runtime-library/security-features-in-the-crt.md) beschrieben.

> [!IMPORTANT]
> **_mbstok_s** und **_mbstok_s_l** können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden. Weitere Informationen finden Sie im Artikel [CRT functions not supported in Universal Windows Platform apps (In Apps für die universelle Windows-Plattform nicht unterstützte CRT-Funktionen)](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntax

```C
char* strtok_s(
   char* str,
   const char* delimiters,
   char** context
);

char* _strtok_s_l(
   char* str,
   const char* delimiters,
   char** context,
   _locale_t locale
);

wchar_t* wcstok_s(
   wchar_t* str,
   const wchar_t* delimiters,
   wchar_t** context
);

wchar_t *_wcstok_s_l(
   wchar_t* str,
   const wchar_t* delimiters,
   wchar_t** context,
   _locale_t locale
);

unsigned char* _mbstok_s(
   unsigned char* str,
   const unsigned char* delimiters,
   char** context
);

unsigned char* _mbstok_s_l(
   unsigned char* str,
   const unsigned char* delimiters,
   char** context,
   _locale_t locale
);
```

### <a name="parameters"></a>Parameter

*Str*<br/>
Eine Zeichenfolge, die das zu findende Token oder Token enthält.

*delimiters*<br/>
Der Satz von Trennzeichen, die verwendet werden sollen.

*context*<br/>
Wird verwendet, um Positionsinformationen zwischen Aufrufen der Funktion zu speichern.

*locale*<br/>
Das zu verwendende Gebietsschema.

## <a name="return-value"></a>Rückgabewert

Gibt einen Zeiger auf das nächste Token *zurück,* das in str gefunden wurde. Gibt **NULL** zurück, wenn keine weiteren Token gefunden werden. Jeder Aufruf ändert *str,* indem ein Nullzeichen durch das erste Trennzeichen ersetzt wird, das nach dem zurückgegebenen Token auftritt.

### <a name="error-conditions"></a>Fehlerbedingungen

|*Str*|*delimiters*|*context*|Rückgabewert|**errno**|
|----------------|------------------|---------------|------------------|-------------|
|**Null**|any|Zeiger auf einen NULL-Zeiger|**Null**|**Einval**|
|any|**Null**|any|**Null**|**Einval**|
|any|any|**Null**|**Null**|**Einval**|

Wenn *str* **NULL** ist, aber *Kontext* ein Zeiger auf einen gültigen Kontextzeiger ist, gibt es keinen Fehler.

## <a name="remarks"></a>Bemerkungen

Die **strtok_s** Funktionsfamilie findet das nächste Token in *str*. Der Satz von Zeichen in *Trennzeichen* gibt mögliche Trennzeichen des Tokens an, die im aktuellen Aufruf in *str* zu finden sind. **wcstok_s** und **_mbstok_s** sind breit- und multibyte-Versionen von **strtok_s**. Die Argumente und Rückgabewerte von **wcstok_s** und **_wcstok_s_l** sind Zeichenfolgen mit großen Zeichen. _mbstok_s **und** **_mbstok_s_l** sind Zeichenfolgen mit mehreren Bytezeichen. Anderenfalls verhalten sich diese Funktionen identisch.

Diese Funktion überprüft ihre Parameter. Wenn eine Fehlerbedingung auftritt, wie in der Tabelle Fehlerbedingungen, wird der ungültige Parameterhandler aufgerufen, wie unter [Parametervalidierung](../../c-runtime-library/parameter-validation.md)beschrieben. Wenn die Ausführung fortgesetzt werden darf, legen diese Funktionen **errno** auf **EINVAL** fest und geben **NULL**zurück.

Beim ersten Aufruf **von strtok_s**überspringt die Funktion führende Trennzeichen und gibt einen Zeiger auf das erste Token in *str*zurück, wodurch das Token mit einem Nullzeichen beendet wird. Weitere Token können aus dem Rest der *Str* durch eine Reihe von Aufrufen an **strtok_s**. Jeder Aufruf von **strtok_s** ändert *str,* indem ein Nullzeichen nach dem von diesem Aufruf zurückgegebenen Token eingefügt wird. Der *Kontextzeiger* verfolgt, welche Zeichenfolge gelesen wird und wo in der Zeichenfolge das nächste Token gelesen werden soll. Um das nächste Token aus *str*zu lesen, rufen Sie **strtok_s** mit einem **NULL-Wert** für das *Argument str* auf und übergeben denselben *Kontextparameter.* Das Argument **NULL** *str* bewirkt, dass **strtok_s** nach dem nächsten Token in der geänderten *str*suchen. Das *Trennzeichenargument* kann einen beliebigen Wert von einem Aufruf zum nächsten annehmen, sodass der Satz von Trennzeichen variieren kann.

Da der *Kontextparameter* die statischen Puffer ersetzt, die in **strtok** und **_strtok_l**verwendet werden, ist es möglich, zwei Zeichenfolgen gleichzeitig im gleichen Thread zu analysieren.

Der Ausgabewert wird durch die Einstellung der **LC_CTYPE** Kategorieeinstellung des Gebietsschemas beeinflusst. Weitere Informationen finden Sie unter [setlocale](setlocale-wsetlocale.md).

Die Versionen dieser Funktionen ohne das **suffix _l** verwenden das aktuelle Threadgebietsschema für dieses gebietsschemaabhängige Verhalten. Die Versionen mit dem **Suffix _l** sind identisch, außer sie verwenden stattdessen das durch den *Gebietsschemaparameter* angegebene Gebietsschema. Weitere Informationen finden Sie unter [Locale](../../c-runtime-library/locale.md).

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**strtok_s**|\<string.h>|
|**_strtok_s_l**|\<string.h>|
|**wcstok_s**,<br />**_wcstok_s_l**|\<string.h> oder \<wchar.h>|
|**_mbstok_s**,<br />**_mbstok_s_l**|\<mbstring.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|TCHAR.H-Routine|\_UNICODE \_& MBCS nicht definiert|\_MBCS definiert|_UNICODE definiert|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstok_s**|**strtok_s**|**_mbstok_s**|**wcstok_s**|
|**_tcstok_s_l**|**_strtok_s_l**|**_mbstok_s_l**|**_wcstok_s_l**|

## <a name="example"></a>Beispiel

```C
// crt_strtok_s.c
// In this program, a loop uses strtok_s
// to print all the tokens (separated by commas
// or blanks) in two strings at the same time.

#include <string.h>
#include <stdio.h>

char string1[] =
    "A string\tof ,,tokens\nand some  more tokens";
char string2[] =
    "Another string\n\tparsed at the same time.";
char seps[]   = " ,\t\n";
char *token1 = NULL;
char *token2 = NULL;
char *next_token1 = NULL;
char *next_token2 = NULL;

int main(void)
{
    printf("Tokens:\n");

    // Establish string and get the first token:
    token1 = strtok_s(string1, seps, &next_token1);
    token2 = strtok_s(string2, seps, &next_token2);

    // While there are tokens in "string1" or "string2"
    while ((token1 != NULL) || (token2 != NULL))
    {
        // Get next token:
        if (token1 != NULL)
        {
            printf(" %s\n", token1);
            token1 = strtok_s(NULL, seps, &next_token1);
        }
        if (token2 != NULL)
        {
            printf("        %s\n", token2);
            token2 = strtok_s(NULL, seps, &next_token2);
        }
    }
}
```

```Output
Tokens:
A
        Another
string
        string
of
        parsed
tokens
        at
and
        the
some
        same
more
        time.
tokens
```

## <a name="see-also"></a>Siehe auch

[String-Manipulation](../../c-runtime-library/string-manipulation-crt.md)<br/>
[Locale](../../c-runtime-library/locale.md)<br/>
[Interpretation von Multibyte-Zeichensequenzen](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[strcspn, wcscspn, _mbscspn, _mbscspn_l](strcspn-wcscspn-mbscspn-mbscspn-l.md)<br/>
[strspn, wcsspn, _mbsspn, _mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
