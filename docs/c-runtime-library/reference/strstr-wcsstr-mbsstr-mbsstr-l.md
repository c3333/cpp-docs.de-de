---
title: strstr, wcsstr, _mbsstr, _mbsstr_l
ms.date: 4/2/2020
api_name:
- _mbsstr
- wcsstr
- _mbsstr_l
- strstr
- _o__mbsstr
- _o__mbsstr_l
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
- api-ms-win-crt-multibyte-l1-1-0.dll
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _fstrstr
- _ftcsstr
- strstr
- wcsstr
- _mbsstr
- _tcsstr
helpviewer_keywords:
- strings [C++], searching
- mbsstr function
- _ftcsstr function
- ftcsstr function
- fstrstr function
- _tcsstr function
- substrings, finding
- mbsstr_l function
- tcsstr function
- _mbsstr function
- wcsstr function
- _fstrstr function
- _mbsstr_l function
- strstr function
ms.assetid: 03d70c3f-2473-45cb-a5f8-b35beeb2748a
ms.openlocfilehash: 3ac4df470e40b35257495d51c5d2d0efdb9310af
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233989"
---
# <a name="strstr-wcsstr-_mbsstr-_mbsstr_l"></a>strstr, wcsstr, _mbsstr, _mbsstr_l

Gibt einen Zeiger auf das erste Vorkommen einer Suchzeichenfolge in einer Zeichenfolge zurück.

> [!IMPORTANT]
> `_mbsstr` und `_mbsstr_l` können nicht in Anwendungen verwendet werden, die in Windows-Runtime ausgeführt werden. Weitere Informationen finden Sie im Artikel [CRT functions not supported in Universal Windows Platform apps (In Apps für die universelle Windows-Plattform nicht unterstützte CRT-Funktionen)](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntax

```C
char *strstr(
   const char *str,
   const char *strSearch
); // C only
char *strstr(
   char *str,
   const char *strSearch
); // C++ only
const char *strstr(
   const char *str,
   const char *strSearch
); // C++ only
wchar_t *wcsstr(
   const wchar_t *str,
   const wchar_t *strSearch
); // C only
wchar_t *wcsstr(
   wchar_t *str,
   const wchar_t *strSearch
); // C++ only
const wchar_t *wcsstr(
   const wchar_t *str,
   const wchar_t *strSearch
); // C++ only
unsigned char *_mbsstr(
   const unsigned char *str,
   const unsigned char *strSearch
); // C only
unsigned char *_mbsstr(
   unsigned char *str,
   const unsigned char *strSearch
); // C++ only
const unsigned char *_mbsstr(
   const unsigned char *str,
   const unsigned char *strSearch
); // C++ only
unsigned char *_mbsstr_l(
   const unsigned char *str,
   const unsigned char *strSearch,
   _locale_t locale
); // C only
unsigned char *_mbsstr_l(
   unsigned char *str,
   const unsigned char *strSearch,
   _locale_t locale
); // C++ only
const unsigned char *_mbsstr_l(
   const unsigned char *str,
   const unsigned char *strSearch,
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>Parameter

*str*<br/>
Zu suchende mit NULL endende Zeichenfolge.

*Trend*<br/>
Zu suchende mit NULL endende Zeichenfolge.

*locale*<br/>
Zu verwendendes Gebietsschema.

## <a name="return-value"></a>Rückgabewert

Gibt einen Zeiger auf das erste Vorkommen von " *tresearch* " in *Str*oder "Null" zurück, wenn " *tresearch* " nicht in *Str*angezeigt wird. Wenn " *strinsearch* " auf eine Zeichenfolge mit der Länge Null zeigt, gibt die Funktion *Str*zurück.

## <a name="remarks"></a>Bemerkungen

Die- `strstr` Funktion gibt einen Zeiger auf das erste Vorkommen von " *tresearch* " in *Str*zurück. Die Suche umfasst keine abschließenden Nullzeichen. `wcsstr` ist die Breitzeichenversion von `strstr`, und `_mbsstr` ist die Multibytezeichenversion. Die Argumente und der Rückgabewert von `wcsstr` sind Breitzeichen-Zeichenfolgen; die von `_mbsstr` sind Mehrbyte-Zeichenfolgen. `_mbsstr` überprüft die eigenen Parameter. Wenn *Str* oder *strinsearch* NULL ist, wird der Handler für ungültige Parameter aufgerufen, wie in [Parameter Validation (Parameter](../../c-runtime-library/parameter-validation.md) Überprüfung) beschrieben. Wenn die weitere Ausführung zugelassen wird, `_mbsstr` legt `errno` auf EINVAL fest und gibt 0 zurück. `strstr` und `wcsstr` überprüfen ihre Parameter nicht. Diese drei Funktionen verhalten sich andernfalls identisch.

> [!IMPORTANT]
> Diese Funktionen können eine Bedrohung aufgrund eines Pufferüberlaufproblems darstellen. Pufferüberlaufprobleme können für Angriffe auf ein System eingesetzt werden, da sie die Ausführung von willkürlichem Code ermöglichen können, was zur einer unbefugten Ausweitung der Berechtigungen führen kann. Weitere Informationen finden Sie unter [Vermeiden von Pufferüberläufen](/windows/win32/SecBP/avoiding-buffer-overruns).

In C akzeptieren diese Funktionen einen **`const`** Zeiger auf das erste Argument. In C++ sind zwei Überladungen verfügbar. Die-Überladung, die einen Zeiger auf annimmt, **`const`** gibt einen Zeiger auf zurück **`const`** . die Version, die einen Zeiger auf nicht-zurücknimmt, **`const`** gibt einen Zeiger auf nicht-zurück **`const`** . Das Makro _CRT_CONST_CORRECT_OVERLOADS wird definiert, wenn sowohl die **`const`** -Version als auch die nicht-- **`const`** Version dieser Funktionen verfügbar sind. Wenn Sie das nicht-- **`const`** Verhalten für beide C++-über Ladungen benötigen, definieren Sie das Symbol _CONST_RETURN.

Der Ausgabewert wird von der locale-Category-Einstellung LC_CTYPE; Weitere Informationen finden Sie unter [setlocale, _wsetlocale](setlocale-wsetlocale.md). Die Versionen dieser Funktionen, die nicht über das **_l** -Suffix verfügen, verwenden das aktuelle Gebiets Schema für dieses vom Gebiets Schema abhängige Verhalten. die Versionen mit dem **_l** -Suffix sind beinahe identisch, verwenden jedoch stattdessen den übergebenen Gebiets Schema Parameter. Weitere Informationen finden Sie unter [Locale](../../c-runtime-library/locale.md).

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|TCHAR.H-Routine|_UNICODE und _MBCS nicht definiert.|_MBCS definiert|_UNICODE definiert|
|---------------------|------------------------------------|--------------------|-----------------------|
|`_tcsstr`|`strstr`|`_mbsstr`|`wcsstr`|
|**Nicht zutreffend**|**Nicht zutreffend**|`_mbsstr_l`|**Nicht zutreffend**|

## <a name="requirements"></a>Anforderungen

|-Routine zurückgegebener Wert|Erforderlicher Header|
|-------------|---------------------|
|`strstr`|\<string.h>|
|`wcsstr`|\<string.h> oder \<wchar.h>|
|`_mbsstr`, `_mbsstr_l`|\<mbstring.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Kompatibilität](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt_strstr.c

#include <string.h>
#include <stdio.h>

char str[] =    "lazy";
char string[] = "The quick brown dog jumps over the lazy fox";
char fmt1[] =   "         1         2         3         4         5";
char fmt2[] =   "12345678901234567890123456789012345678901234567890";

int main( void )
{
   char *pdest;
   int  result;
   printf( "String to be searched:\n   %s\n", string );
   printf( "   %s\n   %s\n\n", fmt1, fmt2 );
   pdest = strstr( string, str );
   result = (int)(pdest - string + 1);
   if ( pdest != NULL )
      printf( "%s found at position %d\n", str, result );
   else
      printf( "%s not found\n", str );
}
```

```Output
String to be searched:
   The quick brown dog jumps over the lazy fox
            1         2         3         4         5
   12345678901234567890123456789012345678901234567890

lazy found at position 36
```

## <a name="see-also"></a>Siehe auch

[Zeichen folgen Bearbeitung](../../c-runtime-library/string-manipulation-crt.md)<br/>
[Gebietsschema](../../c-runtime-library/locale.md)<br/>
[Interpretation von Multibyte-Zeichensequenzen](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[strcspn, wcscspn, _mbscspn, _mbscspn_l](strcspn-wcscspn-mbscspn-mbscspn-l.md)<br/>
[strcmp, wcscmp, _mbscmp](strcmp-wcscmp-mbscmp.md)<br/>
[strpbrk, wcspbrk, _mbspbrk, _mbspbrk_l](strpbrk-wcspbrk-mbspbrk-mbspbrk-l.md)<br/>
[strrchr, wcsrchr, _mbsrchr, _mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
[strspn, wcsspn, _mbsspn, _mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
[basic_string:: Find](../../standard-library/basic-string-class.md#find)<br/>
