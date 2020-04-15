---
title: strncmp, wcsncmp, _mbsncmp, _mbsncmp_l
ms.date: 4/2/2020
api_name:
- strncmp
- _mbsncmp
- wcsncmp
- _mbsncmp_l
- _o__mbsncmp
- _o__mbsncmp_l
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
- api-ms-win-crt-string-l1-1-0.dll
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _ftcsnccmp
- _ftcsncmp
- _tcsncmp
- _tcsnccmp
- strncmp
- _mbsncmp
- wcsncmp
helpviewer_keywords:
- _tcsnccmp function
- ftcsncmp function
- wcsncmp function
- _ftcsncmp function
- _mbsncmp function
- tcsncmp function
- mbsncmp function
- _mbsncmp_l function
- mbsncmp_l function
- strncmp function
- strings [C++], comparing characters of
- string comparison [C++], strncmp function
- _tcsncmp function
- tcsnccmp function
- ftcsnccmp function
- characters [C++], comparing
- _ftcsnccmp function
ms.assetid: 2fdbf4e6-77da-4b59-9086-488f6066b8af
ms.openlocfilehash: fa253bbf7b0ea2ae9993edb12843245b2a1065ca
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364190"
---
# <a name="strncmp-wcsncmp-_mbsncmp-_mbsncmp_l"></a>strncmp, wcsncmp, _mbsncmp, _mbsncmp_l

Vergleicht die angegebene Anzahl von Zeichen zweier Zeichenfolgen.

> [!IMPORTANT]
> **_mbsncmp** und **_mbsncmp_l** können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden. Weitere Informationen finden Sie im Artikel [CRT functions not supported in Universal Windows Platform apps (In Apps für die universelle Windows-Plattform nicht unterstützte CRT-Funktionen)](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntax

```C
int strncmp(
   const char *string1,
   const char *string2,
   size_t count
);
int wcsncmp(
   const wchar_t *string1,
   const wchar_t *string2,
   size_t count
);
int _mbsncmp(
   const unsigned char *string1,
   const unsigned char *string2,
   size_t count
);
int _mbsncmp_l(
   const unsigned char *string1,
   const unsigned char *string2,
   size_t count,
   _locale_t locale
);int _mbsnbcmp(
   const unsigned char *string1,
   const unsigned char *string2,
   size_t count
);
```

### <a name="parameters"></a>Parameter

*string1*, *string2*<br/>
Zu vergleichende Zeichenfolgen.

*count*<br/>
Anzahl der zu vergleichenden Zeichen.

*locale*<br/>
Zu verwendendes Gebietsschema.

## <a name="return-value"></a>Rückgabewert

Der Rückgabewert gibt die Beziehung der Teilzeichenfolgen von *string1* und *string2* wie folgt an.

|Rückgabewert|BESCHREIBUNG|
|------------------|-----------------|
|< 0|*String1-Teilzeichenfolge* kleiner als *String2-Teilzeichenfolge*|
|0|*String1-Teilzeichenfolge* identisch mit *string2-Teilzeichenfolge*|
|> 0|*String1-Teilzeichenfolge* größer als *String2-Teilzeichenfolge*|

Bei einem Parametervalidierungsfehler **geben _mbsncmp** und **_mbsncmp_l** **_NLSCMPERROR**zurück, der in \<string.h> und \<mbstring.h> definiert ist.

## <a name="remarks"></a>Bemerkungen

Die **strncmp-Funktion** führt einen Ordinalvergleich der höchstens ersten *Zählzeichen* in *string1* und *string2* durch und gibt einen Wert zurück, der die Beziehung zwischen den Teilzeichenfolgen angibt. **strncmp** ist eine Groß-/Kleinschreibung von **_strnicmp**. **wcsncmp** und **_mbsncmp** sind **_wcsnicmp** Groß-/Kleinschreibung s/_mbsnicmp . **_mbsnicmp**

**wcsncmp-** und **_mbsncmp** sind Breitzeichen- und Multibyte-Versionen von **strncmp**. Die Argumente von **wcsncmp** sind Zeichenfolgen mit großen Zeichen. bei **_mbsncmp** sind Zeichenfolgen mit mehreren Bytezeichen. **_mbsncmp** erkennt Multibyte-Zeichensequenzen gemäß einer Multibyte-Codepage und gibt **_NLSCMPERROR** auf einen Fehler zurück.

Außerdem **_mbsncmp** und **_mbsncmp_l** Parameter validieren. Wenn *string1* oder *string2* ein NULL-Zeiger ist, wird der ungültige Parameterhandler aufgerufen, wie unter [Parametervalidierung](../../c-runtime-library/parameter-validation.md)beschrieben. Wenn die Ausführung fortgesetzt werden darf, **geben _mbsncmp** und **_mbsncmp_l** **_NLSCMPERROR** zurück und setzen **errno** auf **EINVAL**. **strncmp** und **wcsncmp** überprüfen ihre Parameter nicht. Anderenfalls verhalten sich diese Funktionen identisch.

Das Vergleichsverhalten von **_mbsncmp** und **_mbsncmp_l** wird durch die Einstellung der **LC_CTYPE** Kategorieeinstellung des Gebietsschemas beeinflusst. Hierdurch wird die Erkennung von vorangestellten und nachfolgenden Bytes von Multibytezeichen gesteuert. Weitere Informationen finden Sie unter [setlocale](setlocale-wsetlocale.md). Die **_mbsncmp-Funktion** verwendet das aktuelle Gebietsschema für dieses gebietsschemaabhängige Verhalten. Die **_mbsncmp_l** Funktion identisch ist, außer dass sie stattdessen den *Locale-Parameter* verwendet. Weitere Informationen finden Sie unter [Locale](../../c-runtime-library/locale.md). Wenn es sich bei dem Gebietsschema um ein Einzelbyte-Gebietsschema handelt, ist das Verhalten dieser Funktionen mit **strncmp**identisch.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|TCHAR.H-Routine|_UNICODE und _MBCS nicht definiert.|_MBCS definiert|_UNICODE definiert|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsnccmp**|**strncmp**|**_mbsncmp**|**wcsncmp**|
|**_tcsncmp**|**strncmp**|**_mbsnbcmp**|**wcsncmp**|
|**_tccmp**|Führt eine Zuordnung zum Makro oder zur Inlinefunktion aus|**_mbsncmp**|Führt eine Zuordnung zum Makro oder zur Inlinefunktion aus|
|**nicht anwendbar**|**nicht anwendbar**|**_mbsncmp_l**|**nicht anwendbar**|

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**strncmp**|\<string.h>|
|**wcsncmp**|\<string.h> oder \<wchar.h>|
|**_mbsncmp**, **_mbsncmp_l**|\<mbstring.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt_strncmp.c
#include <string.h>
#include <stdio.h>

char string1[] = "The quick brown dog jumps over the lazy fox";
char string2[] = "The QUICK brown fox jumps over the lazy dog";

int main( void )
{
   char tmp[20];
   int result;
   printf( "Compare strings:\n      %s\n      %s\n\n",
           string1, string2 );
   printf( "Function:   strncmp (first 10 characters only)\n" );
   result = strncmp( string1, string2 , 10 );
   if( result > 0 )
      strcpy_s( tmp, sizeof(tmp), "greater than" );
   else if( result < 0 )
      strcpy_s( tmp, sizeof(tmp), "less than" );
   else
      strcpy_s( tmp, sizeof(tmp), "equal to" );
   printf( "Result:      String 1 is %s string 2\n\n", tmp );
   printf( "Function:   strnicmp _strnicmp (first 10 characters only)\n" );
   result = _strnicmp( string1, string2, 10 );
   if( result > 0 )
      strcpy_s( tmp, sizeof(tmp), "greater than" );
   else if( result < 0 )
      strcpy_s( tmp, sizeof(tmp), "less than" );
   else
      strcpy_s( tmp, sizeof(tmp), "equal to" );
   printf( "Result:      String 1 is %s string 2\n", tmp );
}
```

```Output
Compare strings:
      The quick brown dog jumps over the lazy fox
      The QUICK brown fox jumps over the lazy dog

Function:   strncmp (first 10 characters only)
Result:      String 1 is greater than string 2

Function:   strnicmp _strnicmp (first 10 characters only)
Result:      String 1 is equal to string 2
```

## <a name="see-also"></a>Siehe auch

[String-Manipulation](../../c-runtime-library/string-manipulation-crt.md)<br/>
[Locale](../../c-runtime-library/locale.md)<br/>
[Interpretation von Multibyte-Zeichensequenzen](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_mbsnbcmp, _mbsnbcmp_l](mbsnbcmp-mbsnbcmp-l.md)<br/>
[_mbsnbicmp, _mbsnbicmp_l](mbsnbicmp-mbsnbicmp-l.md)<br/>
[strcmp, wcscmp, _mbscmp](strcmp-wcscmp-mbscmp.md)<br/>
[strcoll-Funktionen](../../c-runtime-library/strcoll-functions.md)<br/>
[_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
[strrchr, wcsrchr, _mbsrchr, _mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
[_strset, _strset_l, _wcsset, _wcsset_l, _mbsset, _mbsset_l](strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)<br/>
[strspn, wcsspn, _mbsspn, _mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
