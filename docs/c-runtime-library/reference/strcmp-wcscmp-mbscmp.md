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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 805e355fe12cb2f7ead6180edd45ad0748570141
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82920381"
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

*Zeichenfolge1*, *Zeichenfolge2*<br/>
Zu vergleichende mit NULL endende Zeichenfolgen.

*locale*<br/>
Zu verwendendes Gebietsschema.

## <a name="return-value"></a>Rückgabewert

Der Rückgabewert für jede dieser Funktionen gibt die ordinalbeziehung von *Zeichenfolge1* zu *Zeichenfolge2*an.

|Value|Verhältnis von string1 zu string2|
|-----------|----------------------------------------|
|< 0|*Zeichenfolge1* ist kleiner als *Zeichenfolge2*|
|0|*Zeichenfolge1* ist mit *Zeichenfolge2* identisch.|
|> 0|*Zeichenfolge1* ist größer als *Zeichenfolge2*|

Bei einem Parameter Validierungs Fehler geben **_mbscmp** und **_mbscmp_l** **_NLSCMPERROR**zurück, das in \<String. h> und \<mbstring. h> definiert ist.

## <a name="remarks"></a>Hinweise

Die Funktion " **straucmp** " führt einen Ordinalvergleich von *Zeichenfolge1* und *Zeichenfolge2* aus und gibt einen Wert zurück, der Ihre Beziehung angibt. **wcscmp** und **_mbscmp** sind bzw. breit Zeichen-und multibytezeichenversionen von " **straucmp**". **_mbscmp** erkennt multibytezeichensequenzen entsprechend der aktuellen Multibytezeichen-Codepage und gibt **_NLSCMPERROR** bei einem Fehler zurück. **_mbscmp_l** weist das gleiche Verhalten auf, verwendet jedoch den Gebiets Schema Parameter, der anstelle des aktuellen Gebiets Schemas übergeben wurde. Weitere Informationen finden Sie unter [Codepages](../../c-runtime-library/code-pages.md). Wenn *Zeichenfolge1* oder *Zeichenfolge2* ein NULL-Zeiger ist, ruft **_mbscmp** den Handler für ungültige Parameter auf, wie in [Parameter Validation (Parameter](../../c-runtime-library/parameter-validation.md)Überprüfung) beschrieben. Wenn die weitere Ausführung zugelassen wird, **_mbscmp** und **_mbscmp_l** **_NLSCMPERROR** zurückgeben und **errno** auf **EINVAL**festlegen. die Parameter werden von " **straucmp** " und " **wcscmp** " nicht überprüft. Anderenfalls verhalten sich diese Funktionen identisch.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|TCHAR.H-Routine|_UNICODE und _MBCS nicht definiert.|_MBCS definiert|_UNICODE definiert|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcscmp**|**strcmp**|**_mbscmp**|**wcscmp**|

Die Funktionen von " **strecmp** " unterscheiden sich von den Funktionen **strcmp** in **"stringenal** " und "nicht vom Gebiets Schema". **strcoll** vergleicht Zeichen folgen lexikografisch mithilfe der **LC_COLLATE** Kategorie des aktuellen Gebiets Schemas. Weitere Informationen zur **LC_COLLATE** Kategorie finden Sie unter [setlocale, _wsetlocale](setlocale-wsetlocale.md).

Im Gebietsschema "C" ist die Reihenfolge der Zeichen im Zeichensatz (ASCII-Zeichensatz) die gleiche wie die lexikografische Zeichenreihenfolge. In anderen Gebietsschemata kann die Reihenfolge der Zeichen im Zeichensatz jedoch von der lexikografischen Reihenfolge abweichen. In bestimmten europäischen Gebietsschemas steht im Zeichensatz das Zeichen "a" (Wert 0x61) vor dem Zeichen "ä" (Wert 0xE4), das Zeichen "ä" steht jedoch lexikografisch gesehen jedoch vor dem Zeichen "a".

In Gebiets Schemas, für die der Zeichensatz und die lexikografische Zeichen Reihenfolge unterschiedlich sind, können Sie **strcoll** anstelle von **strcmp** für den lexikografischen Vergleich von Zeichen folgen verwenden. Alternativ können Sie **strxfrm** für die ursprünglichen Zeichen folgen verwenden und dann **strcmp** für die resultierenden Zeichen folgen verwenden.

Bei den Funktionen von " **strecmp** " wird Groß-/Kleinschreibung striCmp, ** \_wcsicmp**und ** \_mbsicmp** vergleichen Zeichen folgen, indem Sie Sie zuerst in Ihre Kleinbuchstaben umwandeln. ** \_** Zwei Zeichen folgen, die Zeichen zwischen "Z" und "a" in der ASCII-Tabelle (' [', '\\', '] ', ' ^ ', ' _ ' und '\`') enthalten, vergleichen je nach Groß-/Kleinschreibung anders. Beispielsweise vergleichen die beiden Zeichen folgen "abcde" und "abcd ^" eine Richtung, wenn der Vergleich klein geschrieben ist ("abcde" > "abcd ^") und die andere Methode ("abcde" < "abcd ^"), wenn der Vergleich ein Großbuchstabe ist.

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**strcmp**|\<string.h>|
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

## <a name="see-also"></a>Weitere Informationen

[Zeichen folgen Bearbeitung](../../c-runtime-library/string-manipulation-crt.md)<br/>
[memcmp, wmemcmp](memcmp-wmemcmp.md)<br/>
[_memicmp, _memicmp_l](memicmp-memicmp-l.md)<br/>
[Funktionen von "strecoll"](../../c-runtime-library/strcoll-functions.md)<br/>
[_stricmp, _wcsicmp, _mbsicmp, _stricmp_l, _wcsicmp_l, _mbsicmp_l](stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md)<br/>
[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
[strrchr, wcsrchr, _mbsrchr, _mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
[strspn, wcsspn, _mbsspn, _mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
[strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l](strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)<br/>
