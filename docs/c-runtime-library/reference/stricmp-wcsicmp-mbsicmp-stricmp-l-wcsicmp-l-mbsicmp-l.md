---
title: _stricmp, _wcsicmp, _mbsicmp, _stricmp_l, _wcsicmp_l, _mbsicmp_l
ms.date: 4/2/2020
api_name:
- _stricmp_l
- _mbsicmp
- _wcsicmp
- _mbsicmp_l
- _stricmp
- _wcsicmp_l
- _o__mbsicmp
- _o__mbsicmp_l
- _o__stricmp
- _o__stricmp_l
- _o__wcsicmp
- _o__wcsicmp_l
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
- ntoskrnl.exe
- ucrtbase.dll
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-string-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _ftcsicmp
- _stricmp
- wcsicmp_l
- _wcsicmp
- _tcsicmp
- _strcmpi
- stricmp_l
- _mbsicmp
- _fstricmp
- mbsicmp_l
- mbsicmp
helpviewer_keywords:
- _wcsicmp function
- _stricmp_l function
- fstricmp function
- _tcsicmp function
- ftcsicmp function
- string comparison [C++], lowercase
- _wcsicmp_l function
- _fstricmp function
- strings [C++], comparing
- mbsicmp function
- _ftcsicmp function
- _mbsicmp_l function
- wcsicmp_l function
- _stricmp function
- _mbsicmp function
- tcsicmp function
- stricmp_l function
- mbsicmp_l function
- _strcmpi function
ms.assetid: 0e1ee515-0d75-435a-a445-8875d4669b50
ms.openlocfilehash: 786c2bd2738bb82b3edac5c811ccfd3f9f8bc854
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82920007"
---
# <a name="_stricmp-_wcsicmp-_mbsicmp-_stricmp_l-_wcsicmp_l-_mbsicmp_l"></a>_stricmp, _wcsicmp, _mbsicmp, _stricmp_l, _wcsicmp_l, _mbsicmp_l

Führt einen Vergleich von Zeichenfolgen ohne Beachtung der Groß-/Kleinschreibung durch.

> [!IMPORTANT]
> **_mbsicmp** und **_mbsicmp_l** können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden. Weitere Informationen finden Sie im Artikel [CRT functions not supported in Universal Windows Platform apps (In Apps für die universelle Windows-Plattform nicht unterstützte CRT-Funktionen)](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntax

```C
int _stricmp(
   const char *string1,
   const char *string2
);
int _wcsicmp(
   const wchar_t *string1,
   const wchar_t *string2
);
int _mbsicmp(
   const unsigned char *string1,
   const unsigned char *string2
);
int _stricmp_l(
   const char *string1,
   const char *string2,
   _locale_t locale
);
int _wcsicmp_l(
   const wchar_t *string1,
   const wchar_t *string2,
   _locale_t locale
);
int _mbsicmp_l(
   const unsigned char *string1,
   const unsigned char *string2,
   _locale_t locale
);
```

### <a name="parameters"></a>Parameter

*Zeichenfolge1*, *Zeichenfolge2*<br/>
Zu vergleichende mit NULL endende Zeichenfolgen.

*locale*<br/>
Zu verwendendes Gebietsschema.

## <a name="return-value"></a>Rückgabewert

Der Rückgabewert gibt die Beziehung zwischen *Zeichenfolge1* und *Zeichenfolge2* wie folgt an.

|Rückgabewert|Beschreibung|
|------------------|-----------------|
|< 0|*Zeichenfolge1* kleiner als *Zeichenfolge2*|
|0|*Zeichenfolge1* identisch mit *Zeichenfolge2*|
|> 0|*Zeichenfolge1* größer als *Zeichenfolge2*|

Bei einem Fehler gibt **_mbsicmp** **_NLSCMPERROR**zurück, das in \<String. h> und \<mbstring. h> definiert ist.

## <a name="remarks"></a>Hinweise

Die **_stricmp** -Funktion vergleicht *Zeichenfolge1* und *Zeichenfolge2* nach dem umwandeln jedes Zeichens in Kleinbuchstaben ordnungsgemäß und gibt einen Wert zurück, der Ihre Beziehung angibt. **_stricmp** unterscheidet sich insofern von der **_stricoll** , dass der **_stricmp** -Vergleich nur von **LC_CTYPE**betroffen ist, die bestimmen, welche Zeichen in Groß-und Kleinbuchstaben vorliegen. Die **_stricoll** -Funktion vergleicht Zeichen folgen gemäß der Kategorien **LC_CTYPE** und **LC_COLLATE** des Gebiets Schemas, das sowohl die Groß-/Kleinschreibung als auch die Sortierreihenfolge enthält. Weitere Informationen zur **LC_COLLATE** Kategorie finden Sie unter [setlocale](setlocale-wsetlocale.md) und Gebiets Schema [Kategorien](../../c-runtime-library/locale-categories.md). Die Versionen dieser Funktionen ohne das **_l** -Suffix verwenden das aktuelle Gebiets Schema für vom Gebiets Schema abhängiges Verhalten. Die Versionen mit dem Suffix sind identisch, verwenden allerdings das übergebene Gebietsschema. Wenn das Gebietsschema nicht festgelegt wurde, wird das C-Gebietsschema verwendet. Weitere Informationen finden Sie unter [Locale](../../c-runtime-library/locale.md).

> [!NOTE]
> **_stricmp** entspricht **_strcmpi**. Sie können austauschbar verwendet werden, **_stricmp** jedoch der bevorzugte Standard ist.

Die **_strcmpi** -Funktion entspricht **_stricmp** und wird nur aus Gründen der Abwärtskompatibilität bereitgestellt.

Da **_stricmp** Kleinbuchstaben vergleicht, kann dies zu unerwartetem Verhalten führen.

Um zu veranschaulichen, wann die Groß-/Kleinschreibung durch **_stricmp** das Ergebnis eines Vergleichs beeinflusst, gehen Sie davon aus, dass Sie die beiden Zeichen folgen Johnston und JOHN_HENRY haben Die Zeichenfolge JOHN_HENRY wird als kleiner als JOHNSTON angesehen, da das Zeichen „_“ einen niedrigeren ASCII-Wert hat als der Kleinbuchstabe „s“. Jedes Zeichen mit einem ASCII-Wert zwischen 91 und 96 wird als kleiner als jeder Buchstabe angesehen.

Wenn die Funktion " [Strauch](strcmp-wcscmp-mbscmp.md) " anstelle von " **_stricmp**" verwendet wird, ist JOHN_HENRY größer als Johnston.

**_wcsicmp** und **_mbsicmp** sind breit Zeichen-und multibytezeichenversionen von **_stricmp**. Die Argumente und der Rückgabewert von **_wcsicmp** sind Zeichen folgen mit breit Zeichen. bei den **_mbsicmp** handelt es sich um Multibyte-Zeichen folgen. **_mbsicmp** erkennt multibytezeichensequenzen entsprechend der aktuellen Multibytezeichen-Codepage und gibt **_NLSCMPERROR** bei einem Fehler zurück. Weitere Informationen finden Sie unter [Codepages](../../c-runtime-library/code-pages.md). Diese drei Funktionen verhalten sich andernfalls identisch.

**_wcsicmp** und **wcscmp** Verhalten sich identisch, mit dem Unterschied, dass **wcscmp** seine Argumente nicht in Kleinbuchstaben konvertiert, bevor diese verglichen werden. **_mbsicmp** und **_mbscmp** Verhalten sich identisch, mit dem Unterschied, dass **_mbscmp** seine Argumente nicht in Kleinbuchstaben konvertiert, bevor diese verglichen werden.

Sie müssen [setlocale](setlocale-wsetlocale.md) für **_wcsicmp** aufrufen, um mit lateinischen 1 Zeichen arbeiten zu können. Das C-Gebietsschema ist standardmäßig aktiviert, deshalb ist z. B. "ä" nicht identisch mit "Ä". Aufrufen von **setlocale** mit einem anderen Gebiets Schema als dem C-Gebiets Schema vor dem Aufrufen von **_wcsicmp**. Im folgenden Beispiel wird veranschaulicht, wie **_wcsicmp** vom Gebiets Schema abhängig ist:

```C
// crt_stricmp_locale.c
By default, this function's global state is scoped to the application. To change this, see [Global state in the CRT](../global-state.md).

#include <string.h>
#include <stdio.h>
#include <locale.h>

int main() {
   setlocale(LC_ALL,"C");   // in effect by default
   printf("\n%d",_wcsicmp(L"ä", L"Ä"));   // compare fails
   setlocale(LC_ALL,"");
   printf("\n%d",_wcsicmp(L"ä", L"Ä"));   // compare succeeds
}
```

Eine Alternative besteht darin, [_create_locale _wcreate_locale](create-locale-wcreate-locale.md) aufzurufen und das zurückgegebene Gebiets Schema Objekt als Parameter an **_wcsicmp_l**zu übergeben.

Mit allen diesen Funktionen werden ihre Parameter überprüft. Wenn entweder *Zeichenfolge1* oder *Zeichenfolge2* NULL-Zeiger sind, wird der Handler für ungültige Parameter aufgerufen, wie in [Parameter Validation (Parameter](../../c-runtime-library/parameter-validation.md) Überprüfung) beschrieben. Wenn die weitere Ausführung zugelassen wird, geben diese Funktionen **_NLSCMPERROR** zurück und legen **errno** auf **EINVAL**fest.

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|TCHAR.H-Routine|_UNICODE und _MBCS nicht definiert.|_MBCS definiert|_UNICODE definiert|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsicmp**|**_stricmp**|**_mbsicmp**|**_wcsicmp**|

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**_stricmp** **_stricmp_l**|\<string.h>|
|**_wcsicmp** **_wcsicmp_l**|\<string.h> oder \<wchar.h>|
|**_mbsicmp** **_mbsicmp_l**|\<mbstring.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt_stricmp.c

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
      strcpy_s( tmp, _countof(tmp), "less than" );
   else
      strcpy_s( tmp, _countof(tmp), "equal to" );
   printf( "   strcmp:   String 1 is %s string 2\n", tmp );

   // Case insensitive (could use equivalent _stricmp)
   result = _stricmp( string1, string2 );
   if( result > 0 )
      strcpy_s( tmp, _countof(tmp), "greater than" );
   else if( result < 0 )
      strcpy_s( tmp, _countof(tmp), "less than" );
   else
      strcpy_s( tmp, _countof(tmp), "equal to" );
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

## <a name="see-also"></a>Weitere Informationen

[Zeichen folgen Bearbeitung](../../c-runtime-library/string-manipulation-crt.md)<br/>
[memcmp, wmemcmp](memcmp-wmemcmp.md)<br/>
[_memicmp, _memicmp_l](memicmp-memicmp-l.md)<br/>
[strcmp, wcscmp, _mbscmp](strcmp-wcscmp-mbscmp.md)<br/>
[Funktionen von "strecoll"](../../c-runtime-library/strcoll-functions.md)<br/>
[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
[strrchr, wcsrchr, _mbsrchr, _mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
[_strset, _strset_l, _wcsset, _wcsset_l, _mbsset, _mbsset_l](strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)<br/>
[strspn, wcsspn, _mbsspn, _mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
