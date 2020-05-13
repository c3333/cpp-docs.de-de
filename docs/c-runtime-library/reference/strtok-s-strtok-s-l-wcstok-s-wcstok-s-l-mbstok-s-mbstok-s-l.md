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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 52c998f14fee080efc1d288abbba012752757632
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82912678"
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

*SRT*<br/>
Eine Zeichenfolge, die das zu suchende Token enthält.

*delimiters*<br/>
Der Satz von Trennzeichen, die verwendet werden sollen.

*context*<br/>
Wird verwendet, um Positionsinformationen zwischen Aufrufen der Funktion zu speichern.

*locale*<br/>
Das zu verwendende Gebietsschema.

## <a name="return-value"></a>Rückgabewert

Gibt einen Zeiger auf das nächste Token zurück, das in *Str*gefunden wurde. Gibt **null** zurück, wenn keine weiteren Token gefunden werden. Jeder-Befehl ändert *Str* , indem er das erste Trennzeichen, das nach dem zurückgegebenen Token auftritt, durch ein NULL-Zeichen ersetzt.

### <a name="error-conditions"></a>Fehlerbedingungen

|*SRT*|*delimiters*|*context*|Rückgabewert|**errno**|
|----------------|------------------|---------------|------------------|-------------|
|**Normal**|any|Zeiger auf einen NULL-Zeiger|**Normal**|**Eingabe**|
|any|**Normal**|any|**Normal**|**Eingabe**|
|any|any|**Normal**|**Normal**|**Eingabe**|

Wenn *Str* **null** ist, aber der *Kontext* ein Zeiger auf einen gültigen Kontext Zeiger ist, gibt es keinen Fehler.

## <a name="remarks"></a>Hinweise

Die **strtok_s** -Funktions Familie findet das nächste Token in *Str*. Der Zeichensatz in *Trenn* Zeichen gibt mögliche Trennzeichen des Tokens an, das in *Str* auf dem aktuellen-Befehl zu finden ist. **wcstok_s** und **_mbstok_s** sind breit Zeichen-und multibytezeichenversionen von **strtok_s**. Die Argumente und Rückgabewerte von **wcstok_s** und **_wcstok_s_l** sind Zeichen folgen mit breit Zeichen. bei den **_mbstok_s** und **_mbstok_s_l** handelt es sich um Multibyte-Zeichen folgen. Anderenfalls verhalten sich diese Funktionen identisch.

Diese Funktion überprüft ihre Parameter. Wenn ein Fehlerzustand auftritt, wie in der Tabelle Fehlerbedingungen, wird der Handler für ungültige Parameter aufgerufen, wie in [Parameter Validation (Parameter](../../c-runtime-library/parameter-validation.md)Überprüfung) beschrieben. Wenn die weitere Ausführung zugelassen wird, legen diese Funktionen **errno** auf **EINVAL** fest und geben **null**zurück.

Beim ersten **strtok_s**-Aufrufe überspringt die Funktion führende Trennzeichen und gibt einen Zeiger auf das erste Token in *Str*zurück, wobei das Token mit einem NULL-Zeichen beendet wird. Weitere Token können aus dem Rest von *Str* durch eine Reihe von Aufrufen an **strtok_s**aufgeteilt werden. Jeder **strtok_s** -Aufrufe ändert *Str* , indem er ein NULL-Zeichen nach dem Token einfügt, das von diesem-Befehl zurückgegeben wird. Der *Kontext* Zeiger verfolgt, welche Zeichenfolge gelesen wird und an welcher Stelle in der Zeichenfolge das nächste Token gelesen werden soll. Um das nächste Token aus *Str*zu lesen, wenden Sie **strtok_s** mit einem **null** -Wert für das *Str* -Argument an, und übergeben Sie denselben *Kontext* Parameter. Das **null** *Str* -Argument bewirkt, dass **strtok_s** im geänderten *Str*nach dem nächsten Token sucht. Das *Trenn* Zeichen Argument kann einen beliebigen Wert von einem der nächsten Aufrufe annehmen, sodass der Satz von Trennzeichen variieren kann.

Da der *Kontext* Parameter die in **strtok** und **_strtok_l**verwendeten statischen Puffer ersetzt, können zwei Zeichen folgen gleichzeitig im selben Thread analysiert werden.

Der Ausgabewert wird von der Einstellung der Einstellung der **LC_CTYPE** -Kategorie des Gebiets Schemas beeinflusst. Weitere Informationen finden Sie unter [setlocale](setlocale-wsetlocale.md).

Die Versionen dieser Funktionen ohne das **_l** -Suffix verwenden das aktuelle Thread Gebiets Schema für dieses vom Gebiets Schema abhängige Verhalten. Die Versionen mit dem **_l** -Suffix sind beinahe identisch, verwenden jedoch stattdessen das durch den *locale* -Parameter angegebene Gebiets Schema. Weitere Informationen finden Sie unter [Locale](../../c-runtime-library/locale.md).

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**strtok_s**|\<string.h>|
|**_strtok_s_l**|\<string.h>|
|**wcstok_s**,<br />**_wcstok_s_l**|\<string.h> oder \<wchar.h>|
|**_mbstok_s**,<br />**_mbstok_s_l**|\<mbstring.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|TCHAR.H-Routine|\_Unicode- \_& MBCS nicht definiert|\_Definierte MBCS|_UNICODE definiert|
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

## <a name="see-also"></a>Weitere Informationen

[Zeichen folgen Bearbeitung](../../c-runtime-library/string-manipulation-crt.md)<br/>
[Locale](../../c-runtime-library/locale.md)<br/>
[Interpretation von Multibyte-Zeichensequenzen](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[strcspn, wcscspn, _mbscspn, _mbscspn_l](strcspn-wcscspn-mbscspn-mbscspn-l.md)<br/>
[strspn, wcsspn, _mbsspn, _mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
