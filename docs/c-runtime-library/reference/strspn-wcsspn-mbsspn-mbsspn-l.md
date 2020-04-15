---
title: strspn, wcsspn, _mbsspn, _mbsspn_l
ms.date: 4/2/2020
api_name:
- _mbsspn_l
- wcsspn
- strspn
- _mbsspn
- _o__mbsspn
- _o__mbsspn_l
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
- _ftcsspn
- wcsspn
- _mbsspn
- _tcsspn
- strspn
helpviewer_keywords:
- wcsspn function
- strings [C++], searching
- mbsspn function
- tcsspn function
- strspn function
- substrings, finding
- _mbsspn_l function
- ftcsspn function
- _mbsspn function
- _ftcsspn function
- mbsspn_l function
- _tcsspn function
ms.assetid: d077284a-809f-4068-959e-c6d6262677eb
ms.openlocfilehash: 8bd8837f2e1f6cb92c5b7e2e819da56408273810
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317031"
---
# <a name="strspn-wcsspn-_mbsspn-_mbsspn_l"></a>strspn, wcsspn, _mbsspn, _mbsspn_l

Gibt den Index des ersten Zeichens in einer Zeichenfolge zurück, die keinem Zeichensatz angehört.

> [!IMPORTANT]
> **_mbsspn** und **_mbsspn_l** können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden. Weitere Informationen finden Sie im Artikel [CRT functions not supported in Universal Windows Platform apps (In Apps für die universelle Windows-Plattform nicht unterstützte CRT-Funktionen)](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntax

```C
size_t strspn(
   const char *str,
   const char *strCharSet
);
size_t wcsspn(
   const wchar_t *str,
   const wchar_t *strCharSet
);
size_t _mbsspn(
   const unsigned char *str,
   const unsigned char *strCharSet
);
size_t _mbsspn_l(
   const unsigned char *str,
   const unsigned char *strCharSet,
   _locale_t locale
);
```

### <a name="parameters"></a>Parameter

*Str*<br/>
Zu suchende mit NULL endende Zeichenfolge.

*strCharSet*<br/>
Mit NULL endender Zeichensatz.

*locale*<br/>
Zu verwendendes Gebietsschema.

## <a name="return-value"></a>Rückgabewert

Gibt einen Ganzzahlwert zurück, der die Länge der Teilzeichenfolge in *str* angibt, die vollständig aus Zeichen in *strCharSet*besteht. Wenn *str* mit einem Zeichen beginnt, das nicht in *strCharSet*ist, gibt die Funktion 0 zurück.

## <a name="remarks"></a>Bemerkungen

Die **strspn-Funktion** gibt den Index des ersten Zeichens in *str* zurück, das nicht zum Satz von Zeichen in *strCharSet*gehört. Die Suche umfasst keine abschließenden Nullzeichen.

**wcsspn** und **_mbsspn** sind breit- und multibyte-Zeichenversionen von **strspn**. Die Argumente von **wcsspn** sind Zeichenfolgen mit großen Zeichen. bei **_mbsspn** sind Zeichenfolgen mit mehreren Bytezeichen. **_mbsspn** überprüft seine Parameter. Wenn *str* oder *strCharSet* **NULL**ist, wird der ungültige Parameterhandler aufgerufen, wie unter [Parametervalidierung](../../c-runtime-library/parameter-validation.md) beschrieben. Wenn die Ausführung fortgesetzt werden darf, **setzt _mbspn** **errno** auf **EINVAL** und gibt 0 zurück. **strspn** und **wcsspn** überprüfen ihre Parameter nicht. Diese drei Funktionen verhalten sich andernfalls identisch.

Der Ausgabewert ist von der Kategorieeinstellung **LC_CTYPE** des Gebietsschemas betroffen. Weitere Informationen finden Sie unter [setlocale](setlocale-wsetlocale.md). Die Versionen dieser Funktionen ohne das **_l**-Suffix verwenden das aktuelle Gebietsschema für dieses vom Gebietsschema abhängige Verhalten; die Versionen mit dem **_l**-Suffix sind beinahe identisch, verwenden jedoch stattdessen den ihnen übergebenen Gebietsschemaparameter. Weitere Informationen finden Sie unter [Locale](../../c-runtime-library/locale.md).

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|TCHAR.H-Routine|_UNICODE und _MBCS nicht definiert.|_MBCS definiert|_UNICODE definiert|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsspn**|**strspn**|**_mbsspn**|**wcsspn**|
|**k.A.**|**k.A.**|**_mbsspn_l**|**k.A.**|

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**strspn**|\<string.h>|
|**wcsspn**|\<string.h> oder \<wchar.h>|
|**_mbsspn**, **_mbsspn_l**|\<mbstring.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt_strspn.c
// This program uses strspn to determine
// the length of the segment in the string "cabbage"
// consisting of a's, b's, and c's. In other words,
// it finds the first non-abc letter.
//

#include <string.h>
#include <stdio.h>

int main( void )
{
   char string[] = "cabbage";
   int  result;
   result = strspn( string, "abc" );
   printf( "The portion of '%s' containing only a, b, or c "
           "is %d bytes long\n", string, result );
}
```

```Output
The portion of 'cabbage' containing only a, b, or c is 5 bytes long
```

## <a name="see-also"></a>Siehe auch

[String-Manipulation](../../c-runtime-library/string-manipulation-crt.md)<br/>
[Locale](../../c-runtime-library/locale.md)<br/>
[Interpretation von Multibyte-Zeichensequenzen](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_strspnp, _wcsspnp, _mbsspnp, _mbsspnp_l](strspnp-wcsspnp-mbsspnp-mbsspnp-l.md)<br/>
[strcspn, wcscspn, _mbscspn, _mbscspn_l](strcspn-wcscspn-mbscspn-mbscspn-l.md)<br/>
[strncat, _strncat_l, wcsncat, _wcsncat_l, _mbsncat, _mbsncat_l](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)<br/>
[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[strncpy, _strncpy_l, wcsncpy, _wcsncpy_l, _mbsncpy, _mbsncpy_l](strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)<br/>
[_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
[strrchr, wcsrchr, _mbsrchr, _mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
