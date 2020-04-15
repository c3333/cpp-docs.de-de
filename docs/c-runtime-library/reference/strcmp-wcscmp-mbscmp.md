---
title: strcmp, wcscmp, _mbscmp, _mbscmp_l
ms.date: 4/2/2020
api_name:
- wcscmp
- _mbscmp
- _mbscmp_l
- strcmp
- _o__mbscmp
- _o__mbscmp_l
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
- _mbscmp
- _mbscmp_l
- wcscmp
- strcmp
- _tcscmp
- _ftcscmp
helpviewer_keywords:
- tcscmp function
- strcmp function
- strings [C++], comparing
- mbscmp function
- string comparison [C++]
- _mbscmp function
- _mbscmp_l function
- wcscmp function
- _tcscmp function
- _ftcscmp function
- ftcscmp function
ms.assetid: 5d216b57-7a5c-4cb3-abf0-0f4facf4396d
ms.openlocfilehash: 16bb294f7bbdc0b95b59b845d7b714f823f9d962
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81357282"
---
# <a name="strcmp-wcscmp-_mbscmp-_mbscmp_l"></a>strcmp, wcscmp, _mbscmp, _mbscmp_l

Vergleichen von Zeichenfolgen

> [!IMPORTANT]
> **_mbscmp** und **_mbscmp_l** können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden. Weitere Informationen finden Sie im Artikel [CRT functions not supported in Universal Windows Platform apps (In Apps für die universelle Windows-Plattform nicht unterstützte CRT-Funktionen)](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntax

```C
int strcmp(
   const char *string1,
   const char *string2
);
int wcscmp(
   const wchar_t *string1,
   const wchar_t *string2
);
int _mbscmp(
   const unsigned char *string1,
   const unsigned char *string2
);
int _mbscmp_l(
   const unsigned char *string1,
   const unsigned char *string2,
   _locale_t locale
);
```

### <a name="parameters"></a>Parameter

*string1*, *string2*<br/>
Zu vergleichende mit NULL endende Zeichenfolgen.

*locale*<br/>
Zu verwendendes Gebietsschema.

## <a name="return-value"></a>Rückgabewert

Der Rückgabewert für jede dieser Funktionen gibt die Ordinalbeziehung von *string1* zu *string2*an.

|Wert|Verhältnis von string1 zu string2|
|-----------|----------------------------------------|
|< 0|*String1* ist kleiner als *string2*|
|0|*string1* ist identisch mit *string2*|
|> 0|*String1* ist größer als *string2*|

Bei einem Parametervalidierungsfehler **geben _mbscmp** und **_mbscmp_l** **_NLSCMPERROR**zurück, der in \<string.h> und \<mbstring.h> definiert ist.

## <a name="remarks"></a>Bemerkungen

Die **strcmp-Funktion** führt einen ordinalen Vergleich von *string1* und *string2* durch und gibt einen Wert zurück, der ihre Beziehung angibt. **wcscmp** und **_mbscmp** sind jeweils Breitzeichen- bzw. Multibyte-Zeichenversionen von **strcmp**. **_mbscmp** erkennt Multibyte-Zeichensequenzen entsprechend der aktuellen Multibyte-Codepage und gibt **_NLSCMPERROR** bei einem Fehler zurück. **_mbscmp_l** hat das gleiche Verhalten, verwendet jedoch den Gebietsschemaparameter, der anstelle des aktuellen Gebietsschemas übergeben wird. Weitere Informationen finden Sie unter [Codepages](../../c-runtime-library/code-pages.md). Wenn *string1* oder *string2* ein NULL-Zeiger ist, ruft **_mbscmp** den ungültigen Parameterhandler auf, wie unter [Parametervalidierung](../../c-runtime-library/parameter-validation.md)beschrieben. Wenn die Ausführung fortgesetzt werden darf, **geben _mbscmp** und **_mbscmp_l** **_NLSCMPERROR** zurück und setzen **errno** auf **EINVAL**. **strcmp** und **wcscmp** validieren ihre Parameter nicht. Anderenfalls verhalten sich diese Funktionen identisch.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|TCHAR.H-Routine|_UNICODE und _MBCS nicht definiert.|_MBCS definiert|_UNICODE definiert|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcscmp**|**Strcmp**|**_mbscmp**|**wcscmp**|

Die **strcmp-Funktionen** unterscheiden sich von den **strcoll-Funktionen** dadurch, dass **strcmp-Vergleiche** ordinal sind und nicht vom Gebietsschema beeinflusst werden. **strcoll** vergleicht Strings lexikographisch, indem die **LC_COLLATE** Kategorie des aktuellen Gebietsschemas verwendet wird. Weitere Informationen zur **Kategorie LC_COLLATE** finden Sie unter [setlocale, _wsetlocale](setlocale-wsetlocale.md).

Im Gebietsschema "C" ist die Reihenfolge der Zeichen im Zeichensatz (ASCII-Zeichensatz) die gleiche wie die lexikografische Zeichenreihenfolge. In anderen Gebietsschemata kann die Reihenfolge der Zeichen im Zeichensatz jedoch von der lexikografischen Reihenfolge abweichen. In bestimmten europäischen Gebietsschemas steht im Zeichensatz das Zeichen "a" (Wert 0x61) vor dem Zeichen "ä" (Wert 0xE4), das Zeichen "ä" steht jedoch lexikografisch gesehen jedoch vor dem Zeichen "a".

In Gebietsschemas, für die sich der Zeichensatz und die lexikographische Zeichenreihenfolge unterscheiden, können Sie **Strcoll** anstelle von **strcmp** für den lexikographischen Vergleich von Zeichenfolgen verwenden. Alternativ können Sie **strxfrm** für die ursprünglichen Zeichenfolgen verwenden und dann **strcmp** für die resultierenden Zeichenfolgen verwenden.

Bei den **strcmp-Funktionen** wird die Groß-/Kleinschreibung berücksichtigt. stricmp , ** \_wcsicmp**und ** \_mbsicmp** vergleichen Zeichenfolgen, indem sie sie zuerst in ihre Kleinbuchstabenformen konvertieren. ** \_** Zwei Zeichenfolgen, die Zeichen enthalten, die sich in der ASCII-Tabelle zwischen\\'Z' und 'a' befinden ('[', ', ']', ''', '_', '_', und ' ')\`vergleichen je nach Fall unterschiedlich. Die beiden Zeichenfolgen "ABCDE" und "ABCD" vergleichen z. B. eine Möglichkeit, wenn der Vergleich Kleinbuchstaben ist ("abcde" > "abcd") und umgekehrt ("ABCDE" < "ABCD") wenn der Vergleich groß ist.

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**Strcmp**|\<string.h>|
|**wcscmp**|\<string.h> oder \<wchar.h>|
|**_mbscmp**|\<mbstring.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotheken

Alle Versionen [C-Laufzeitbibliotheken](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Beispiel

```C
// crt_strcmp.c

#include <string.h>
#include <stdio.h>
#include <stdlib.h>

char string1[] = "The quick brown dog jumps over the lazy fox";
char string2[] = "The QUICK brown dog jumps over the lazy fox";

int main( void )
{
   char tmp[20];
   int result;

   // Case sensitive
   printf( "Compare strings:\n   %s\n   %s\n\n", string1, string2 );
   result = strcmp( string1, string2 );
   if( result > 0 )
      strcpy_s( tmp, _countof(tmp), "greater than" );
   else if( result < 0 )
      strcpy_s( tmp, _countof (tmp), "less than" );
   else
      strcpy_s( tmp, _countof (tmp), "equal to" );
   printf( "   strcmp:   String 1 is %s string 2\n", tmp );

   // Case insensitive (could use equivalent _stricmp)
   result = _stricmp( string1, string2 );
   if( result > 0 )
      strcpy_s( tmp, _countof (tmp), "greater than" );
   else if( result < 0 )
      strcpy_s( tmp, _countof (tmp), "less than" );
   else
      strcpy_s( tmp, _countof (tmp), "equal to" );
   printf( "   _stricmp:  String 1 is %s string 2\n", tmp );
}
```

```Output
Compare strings:
   The quick brown dog jumps over the lazy fox
   The QUICK brown dog jumps over the lazy fox

   strcmp:   String 1 is greater than string 2
   _stricmp:  String 1 is equal to string 2
```

## <a name="see-also"></a>Siehe auch

[String-Manipulation](../../c-runtime-library/string-manipulation-crt.md)<br/>
[memcmp, wmemcmp](memcmp-wmemcmp.md)<br/>
[_memicmp, _memicmp_l](memicmp-memicmp-l.md)<br/>
[strcoll-Funktionen](../../c-runtime-library/strcoll-functions.md)<br/>
[_stricmp, _wcsicmp, _mbsicmp, _stricmp_l, _wcsicmp_l, _mbsicmp_l](stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md)<br/>
[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
[strrchr, wcsrchr, _mbsrchr, _mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
[strspn, wcsspn, _mbsspn, _mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
[strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l](strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)<br/>
