---
title: _strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l
ms.date: 4/2/2020
api_name:
- _wcsnicmp
- _strnicmp_l
- _wcsnicmp_l
- _strnicmp
- _mbsnicmp
- _mbsnicmp_l
- _o__mbsnicmp
- _o__mbsnicmp_l
- _o__strnicmp
- _o__strnicmp_l
- _o__wcsnicmp
- _o__wcsnicmp_l
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
- wcsnicmp_l
- _strnicmp
- _ftcsnicmp
- mbsnicmp_l
- _ftcsncicmp
- mbsnicmp
- _tcsncicmp
- _mbsnicmp
- _tcsnicmp
- strnicmp_l
- _wcsnicmp
- _wcsnicmp_l
- CORECRT_WSTRING/_wcsnicmp
- CORECRT_WSTRING/_wcsnicmp_l
- string/_strnicmp
- string/_strnicmp_l
helpviewer_keywords:
- tcsnicmp function
- _tcsncicmp function
- _mbsnicmp_l function
- mbsnicmp_l function
- wcsnicmp_l function
- wcsnicmp function
- string comparison [C++], lowercase
- ftcsnicmp function
- strnicmp_l function
- strncmp function
- _strnicmp function
- strings [C++], comparing characters of
- _wcsnicmp_l function
- tcsncicmp function
- string comparison [C++], strncmp function
- _mbsnicmp function
- ftcsncicmp function
- _tcsnicmp function
- _ftcsncicmp function
- _strnicmp_l function
- _ftcsnicmp function
- characters [C++], comparing
- mbsnicmp function
- _wcsnicmp function
ms.assetid: df6e5037-4039-4c85-a0a6-21d4ef513966
ms.openlocfilehash: b0bde60a230f1fd428716073471cd85b2728a614
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364829"
---
# <a name="_strnicmp-_wcsnicmp-_mbsnicmp-_strnicmp_l-_wcsnicmp_l-_mbsnicmp_l"></a>_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l

Vergleicht die angegebene Anzahl von Zeichen zweier Zeichenfolgen ohne Berücksichtigung von Groß-/Kleinbuchstaben.

> [!IMPORTANT]
> **_mbsnicmp** und **_mbsnicmp_l** können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden. Weitere Informationen finden Sie im Artikel [CRT functions not supported in Universal Windows Platform apps (In Apps für die universelle Windows-Plattform nicht unterstützte CRT-Funktionen)](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntax

```C
int _strnicmp(
   const char *string1,
   const char *string2,
   size_t count
);
int _wcsnicmp(
   const wchar_t *string1,
   const wchar_t *string2,
   size_t count
);
int _mbsnicmp(
   const unsigned char *string1,
   const unsigned char *string2,
   size_t count
);
int _strnicmp_l(
   const char *string1,
   const char *string2,
   size_t count,
   _locale_t locale
);
int _wcsnicmp_l(
   const wchar_t *string1,
   const wchar_t *string2,
   size_t count,
   _locale_t locale
);
int _mbsnicmp_l(
   const unsigned char *string1,
   const unsigned char *string2,
   size_t count,
   _locale_t locale
);
```

### <a name="parameters"></a>Parameter

*string1*, *string2*<br/>
Zu vergleichende mit NULL endende Zeichenfolgen.

*count*<br/>
Anzahl der zu vergleichenden Zeichen.

*locale*<br/>
Zu verwendendes Gebietsschema.

## <a name="return-value"></a>Rückgabewert

Gibt die Beziehung zwischen den untergeordneten Zeichenfolgen wie folgt an.

|Rückgabewert|BESCHREIBUNG|
|------------------|-----------------|
|< 0|*String1-Teilzeichenfolge* ist kleiner als *string2-Teilzeichenfolge.*|
|0|*string1-Teilzeichenfolge* ist identisch mit *der Zeichenfolge2.*|
|> 0|*String1-Teilzeichenfolge* ist größer als *string2-Teilzeichenfolge.*|

Bei einem Parametervalidierungsfehler **_NLSCMPERROR**geben diese Funktionen \<_NLSCMPERROR zurück, \<der in string.h> und mbstring.h> definiert ist.

## <a name="remarks"></a>Bemerkungen

Die **_strnicmp-Funktion** vergleicht höchstens die ersten *Zählzeichen* von *string1* und *string2*. Der Vergleich erfolgt ohne Berücksichtigung der Groß-/Kleinschreibung, indem jedes Zeichen in Kleinbuchstaben konvertiert wird. **_strnicmp** ist eine Groß-/Kleinschreibung von **strncmp**. Der Vergleich endet, wenn ein beendendes Nullzeichen in einer der beiden Zeichenfolgen erreicht wird, bevor *Zählzeichen* verglichen werden. Wenn die Zeichenfolgen gleich sind, wenn ein beendendes NULL-Zeichen in einer der beiden Zeichenfolgen erreicht wird, bevor *Zählzeichen* verglichen werden, ist die kürzere Zeichenfolge kleiner.

Die Zeichen von 91 bis 96 in der ASCII-Tabelle ('[', '\\', ']', '^', '_' und '\`') werden als kleiner als jedes beliebige alphabetische Zeichen ausgewertet. Diese Reihenfolge ist identisch mit der von **stricmp**.

**_wcsnicmp** und **_mbsnicmp** sind breit- und multibyte-Zeichen-Versionen von **_strnicmp**. Die Argumente von **_wcsnicmp** sind Zeichenfolgen mit großen Zeichen; bei **_mbsnicmp** sind Zeichenfolgen mit mehreren Bytezeichen. **_mbsnicmp** erkennt Multibyte-Zeichensequenzen entsprechend der aktuellen Multibyte-Codepage und gibt **_NLSCMPERROR** bei einem Fehler zurück. Weitere Informationen finden Sie unter [Codepages](../../c-runtime-library/code-pages.md). Diese drei Funktionen verhalten sich andernfalls identisch. Diese Funktionen werden von der Gebietsschemaeinstellung beeinflusst – die Versionen, die nicht über das **_l** Suffix verfügen, verwenden das aktuelle Gebietsschema für ihr gebietsschemaabhängiges Verhalten. Die Versionen, die über das **_l** Suffix verfügen, verwenden stattdessen das *übergebene Gebietsschema.* Weitere Informationen finden Sie unter [Locale](../../c-runtime-library/locale.md).

Mit allen diesen Funktionen werden ihre Parameter überprüft. Wenn *string1* oder *string2* ein NULL-Zeiger ist, wird der ungültige Parameterhandler aufgerufen, wie unter [Parametervalidierung](../../c-runtime-library/parameter-validation.md)beschrieben. Wenn die Ausführung fortgesetzt werden darf, geben diese Funktionen **_NLSCMPERROR** zurück und setzen **errno** auf **EINVAL**.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|TCHAR.H-Routine|_UNICODE und _MBCS nicht definiert.|_MBCS definiert|_UNICODE definiert|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsncicmp**|**_strnicmp**|**_mbsnicmp**|**_wcsnicmp**|
|**_tcsnicmp**|**_strnicmp**|**_mbsnbicmp**|**_wcsnicmp**|
|**_tcsncicmp_l**|**_strnicmp_l**|**_mbsnicmp_l**|**_wcsnicmp_l**|

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**_strnicmp**, **_strnicmp_l**|\<string.h>|
|**_wcsnicmp**, **_wcsnicmp_l**|\<string.h> oder \<wchar.h>|
|**_mbsnicmp**, **_mbsnicmp_l**|\<mbstring.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

Ein Beispiel hierfür finden Sie unter [strncmp](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md).

## <a name="see-also"></a>Siehe auch

[String-Manipulation](../../c-runtime-library/string-manipulation-crt.md)<br/>
[strcat, wcscat, _mbscat](strcat-wcscat-mbscat.md)<br/>
[strcmp, wcscmp, _mbscmp](strcmp-wcscmp-mbscmp.md)<br/>
[strcpy, wcscpy, _mbscpy](strcpy-wcscpy-mbscpy.md)<br/>
[strncat, _strncat_l, wcsncat, _wcsncat_l, _mbsncat, _mbsncat_l](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)<br/>
[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[strncpy, _strncpy_l, wcsncpy, _wcsncpy_l, _mbsncpy, _mbsncpy_l](strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)<br/>
[strrchr, wcsrchr, _mbsrchr, _mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
[_strset, _strset_l, _wcsset, _wcsset_l, _mbsset, _mbsset_l](strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)<br/>
[strspn, wcsspn, _mbsspn, _mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
