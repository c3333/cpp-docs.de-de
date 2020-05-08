---
title: _strnset, _strnset_l, _wcsnset, _wcsnset_l, _mbsnset, _mbsnset_l
ms.date: 4/2/2020
api_name:
- _mbsnset
- _strnset
- _mbsnset_l
- _wcsnset_l
- _wcsnset
- _strnset_l
- _o__mbsnset
- _o__mbsnset_l
- _o__wcsnset
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
- _tcsncset_l
- mbsnset_l
- _tcsnset_l
- _fstrnset
- _wcsnset_l
- _ftcsnset
- wcsnset_l
- _mbsnset_l
- _strnset
- _tcsnset
- _strnset_l
- mbsnset
- strnset_l
- _mbsnset
- _wcsnset
- _tcsncset
helpviewer_keywords:
- _wcsnset function
- strnset_l function
- tcsnset function
- tcsncset function
- characters [C++], initializing to formats
- mbsnset function
- _tcsnset_l function
- _mbsnset function
- _strnset function
- _tcsncset_l function
- mbsnset_l function
- _tcsnset function
- initializing characters
- _tcsncset function
- ftcsnset function
- wcsnset_l function
- _ftcsnset function
- _wcsnset_l function
- _fstrnset function
- _mbsnset_l function
- _strnset_l function
- fstrnset function
- strings [C++], initializing
- tcsnset_l function
ms.assetid: 3f306489-5763-48e5-b939-aefee7c94ef5
ms.openlocfilehash: 2bd0c31b025b9a11cbdb10e8607a283d6ae1f84b
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82911199"
---
# <a name="_strnset-_strnset_l-_wcsnset-_wcsnset_l-_mbsnset-_mbsnset_l"></a>_strnset, _strnset_l, _wcsnset, _wcsnset_l, _mbsnset, _mbsnset_l

Initialisiert Zeichen einer Zeichenfolge auf ein angegebenes Zeichen. Sicherere Versionen dieser Funktionen sind vorhanden. Weitere Informationen finden Sie unter [_strnset_s, _strnset_s_l, _wcsnset_s, _wcsnset_s_l, _mbsnset_s, _mbsnset_s_l](strnset-s-strnset-s-l-wcsnset-s-wcsnset-s-l-mbsnset-s-mbsnset-s-l.md).

> [!IMPORTANT]
> **_mbsnset** und **_mbsnset_l** können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden. Weitere Informationen finden Sie im Artikel [CRT functions not supported in Universal Windows Platform apps (In Apps für die universelle Windows-Plattform nicht unterstützte CRT-Funktionen)](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntax

```C
char *_strnset(
   char *str,
   int c,
   size_t count
);
char *_strnset_l(
   char *str,
   int c,
   size_t count,
   locale_t locale
);
wchar_t *_wcsnset(
   wchar_t *str,
   wchar_t c,
   size_t count
);
wchar_t *_wcsnset_l(
   wchar_t *str,
   wchar_t c,
   size_t count,
   _locale_t locale
);
unsigned char *_mbsnset(
   unsigned char *str,
   unsigned int c,
   size_t count
);
unsigned char *_mbsnset_l(
   unsigned char *str,
   unsigned int c,
   size_t count,
   _locale_t locale
);
```

### <a name="parameters"></a>Parameter

*SRT*<br/>
Zu ändernde Zeichenfolge.

*scher*<br/>
Zeicheneinstellung.

*count*<br/>
Zahl der festzulegenden Zeichen.

*locale*<br/>
Zu verwendendes Gebietsschema.

## <a name="return-value"></a>Rückgabewert

Gibt einen Zeiger zur geänderten Zeichenfolge zurück.

## <a name="remarks"></a>Hinweise

Die **_strnset** -Funktion legt höchstens die ersten *count* -Zeichen von *Str* bis *c* (konvertiert in **char**) fest. Wenn *count* größer als die Länge von *Str*ist, wird die Länge von *Str* anstelle von *count*verwendet.

**_wcsnset** und **_mbsnset** sind breit Zeichen-und multibytezeichenversionen von **_strnset**. Die Zeichen folgen Argumente und der Rückgabewert von **_wcsnset** sind Zeichen folgen mit breit Zeichen. bei den **_mbsnset** handelt es sich um Multibyte-Zeichen folgen. Diese drei Funktionen verhalten sich andernfalls identisch.

**_mbsnset** überprüft seine Parameter. Wenn *Str* ein NULL-Zeiger ist, wird der Handler für ungültige Parameter aufgerufen, wie in [Parameter Validation (Parameter](../../c-runtime-library/parameter-validation.md) Überprüfung) beschrieben. Wenn die weitere Ausführung zugelassen wird, **_mbsnset** gibt _mbsnset **null** zurück und legt **errno** auf **EINVAL**fest. **_strnset** und **_wcsnset** überprüfen Ihre Parameter nicht.

Der Ausgabewert ist von der Kategorieeinstellung **LC_CTYPE** des Gebietsschemas betroffen. Weitere Informationen finden Sie unter [setlocale](setlocale-wsetlocale.md). Die Versionen dieser Funktionen ohne das **_l**-Suffix verwenden das aktuelle Gebietsschema für dieses vom Gebietsschema abhängige Verhalten; die Versionen mit dem **_l**-Suffix sind beinahe identisch, verwenden jedoch stattdessen den ihnen übergebenen Gebietsschemaparameter. Weitere Informationen finden Sie unter [Locale](../../c-runtime-library/locale.md).

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|TCHAR.H-Routine|_UNICODE und _MBCS nicht definiert.|_MBCS definiert|_UNICODE definiert|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsnset**|**_strnset**|**_mbsnbset**|**_wcsnset**|
|**_tcsnset_l**|**_strnset_l**|**_mbsnbset_l**|**_wcsnset_l**|

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**_strnset**|\<string.h>|
|**_strnset_l**|\<tchar.h>|
|**_wcsnset**|\<string.h> oder \<wchar.h>|
|**_wcsnset_l**|\<tchar.h>|
|**_mbsnset** **_mbsnset_l**|\<mbstring.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt_strnset.c
// compile with: /W3
#include <string.h>
#include <stdio.h>

int main( void )
{
   char string[15] = "This is a test";
   /* Set not more than 4 characters of string to be *'s */
   printf( "Before: %s\n", string );
   _strnset( string, '*', 4 ); // C4996
   // Note: _strnset is deprecated; consider using _strnset_s
   printf( "After:  %s\n", string );
}
```

```Output
Before: This is a test
After:  **** is a test
```

## <a name="see-also"></a>Weitere Informationen

[Zeichen folgen Bearbeitung](../../c-runtime-library/string-manipulation-crt.md)<br/>
[Locale](../../c-runtime-library/locale.md)<br/>
[Interpretation von Multibyte-Zeichensequenzen](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[strcat, wcscat, _mbscat](strcat-wcscat-mbscat.md)<br/>
[strcmp, wcscmp, _mbscmp](strcmp-wcscmp-mbscmp.md)<br/>
[strcpy, wcscpy, _mbscpy](strcpy-wcscpy-mbscpy.md)<br/>
[_strset, _strset_l, _wcsset, _wcsset_l, _mbsset, _mbsset_l](strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)<br/>
