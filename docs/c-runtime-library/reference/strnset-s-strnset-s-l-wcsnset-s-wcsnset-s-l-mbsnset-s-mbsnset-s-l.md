---
title: _strnset_s, _strnset_s_l, _wcsnset_s, _wcsnset_s_l, _mbsnset_s, _mbsnset_s_l
ms.date: 4/2/2020
api_name:
- _mbsnset_s_l
- _strnset_s
- _mbsnset_s
- _strnset_s_l
- _wcsnset_s_l
- _wcsnset_s
- _o__mbsnset_s
- _o__mbsnset_s_l
- _o__strnset_s
- _o__wcsnset_s
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
- _mbsnset_s_l
- wcsnset_s
- _tcsnset_s_l
- _wcsnset_s
- _mbsnset_s
- _wcsnset_s_l
- _strnset_s_l
- strnset_s_l
- _tcsnset_s
- _strnset_s
- strnset_s
- mbsnset_s_l
- mbsnset_s
- wcsnset_s_l
helpviewer_keywords:
- tcsnset_s function
- mbsnset_s_l function
- initializing characters
- wcsnset_s function
- mbsnset_s function
- _tcsnset_s_l function
- _strnset_s_l function
- _mbsnset_s function
- strnset_s_l function
- _tcsnset_s function
- _strnset_s function
- tcsnset_s_l function
- _mbsnset_s_l function
- strnset_s function
- _wcsnset_s function
ms.assetid: 9cf1b321-b5cb-4469-b285-4c07cfbd8813
ms.openlocfilehash: 62b0ecdc7d9e1afb93c4b15c37016ac687dc80d6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364458"
---
# <a name="_strnset_s-_strnset_s_l-_wcsnset_s-_wcsnset_s_l-_mbsnset_s-_mbsnset_s_l"></a>_strnset_s, _strnset_s_l, _wcsnset_s, _wcsnset_s_l, _mbsnset_s, _mbsnset_s_l

Initialisiert Zeichen einer Zeichenfolge auf ein angegebenes Zeichen. Diese Versionen von [_strnset, _strnset_l, _wcsnset, _wcsnset_l, _mbsnset, _mbsnset_l](strnset-strnset-l-wcsnset-wcsnset-l-mbsnset-mbsnset-l.md) enthalten Sicherheitsverbesserungen, wie unter [Sicherheitsfunktionen in der CRT](../../c-runtime-library/security-features-in-the-crt.md) beschrieben.

> [!IMPORTANT]
> **_mbsnset_s** und **_mbsnset_s_l** können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden. Weitere Informationen finden Sie im Artikel [CRT functions not supported in Universal Windows Platform apps (In Apps für die universelle Windows-Plattform nicht unterstützte CRT-Funktionen)](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntax

```C
errno_t _strnset_s(
   char *str,
   size_t numberOfElements,
   int c,
   size_t count
);
errno_t _strnset_s_l(
   char *str,
   size_t numberOfElements,
   int c,
   size_t count,
   locale_t locale
);
errno_t _wcsnset_s(
   wchar_t *str,
   size_t numberOfElements,
   wchar_t c,
   size_t count
);
errno_t _wcsnset_s_l(
   wchar_t *str,
   size_t numberOfElements,
   wchar_t c,
   size_t count,
   _locale_t locale
);
errno_t _mbsnset_s(
   unsigned char *str,
   size_t numberOfElements,
   unsigned int c,
   size_t count
);
errno_t _mbsnset_s_l(
   unsigned char *str,
   size_t numberOfElements,
   unsigned int c,
   size_t count,
   _locale_t locale
);
```

### <a name="parameters"></a>Parameter

*Str*<br/>
Zu ändernde Zeichenfolge.

*Sizeinbytes*<br/>
Die Größe *str* des str-Puffers.

*C*<br/>
Zeicheneinstellung.

*count*<br/>
Zahl der festzulegenden Zeichen.

*locale*<br/>
Zu verwendendes Gebietsschema.

## <a name="return-value"></a>Rückgabewert

Null, wenn erfolgreich, andernfalls ein Fehlercode.

Diese Funktionen überprüfen ihre Argumente. Wenn *str* keine gültige NULL-Termin-Zeichenfolge ist oder das Size-Argument kleiner oder gleich 0 ist, wird der ungültige Parameterhandler aufgerufen, wie unter [Parametervalidierung](../../c-runtime-library/parameter-validation.md)beschrieben. Wenn die Ausführung fortgesetzt werden darf, geben diese Funktionen einen Fehlercode zurück und setzen **errno** auf diesen Fehlercode. Der Standardfehlercode ist **EINVAL,** wenn kein spezifischerer Wert angewendet wird.

## <a name="remarks"></a>Bemerkungen

Diese Funktionen legen höchstens die ersten *Zählzeichen* von *str* bis *c*fest. Wenn die *Anzahl* größer als die Größe von *str*ist, wird die Größe von *str* anstelle von *count*verwendet. Ein Fehler tritt auf, wenn die *Anzahl* größer als *numberOfElements* ist und beide Parameter größer als die Größe von *str*sind.

**_wcsnset_s** und **_mbsnset_s** sind breit- und multibyte-Zeichen-Versionen von **_strnset_s**. Das Zeichenfolgenargument **von _wcsnset_s** ist eine Zeichenfolge mit großen Zeichen. die von **_mbsnset_s** ist eine Zeichenfolge mit mehreren Bytezeichen. Diese drei Funktionen verhalten sich andernfalls identisch.

Der Ausgabewert ist von der Kategorieeinstellung **LC_CTYPE** des Gebietsschemas betroffen. Weitere Informationen finden Sie unter [setlocale](setlocale-wsetlocale.md). Die Versionen dieser Funktionen ohne das **_l**-Suffix verwenden das aktuelle Gebietsschema für dieses vom Gebietsschema abhängige Verhalten; die Versionen mit dem **_l**-Suffix sind beinahe identisch, verwenden jedoch stattdessen den ihnen übergebenen Gebietsschemaparameter. Weitere Informationen finden Sie unter [Locale](../../c-runtime-library/locale.md).

Die Debugbibliotheksversionen dieser Funktionen füllen zunächst den Puffer mit 0xFE. Um dieses Verhalten zu deaktivieren, verwenden Sie [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|TCHAR.H-Routine|_UNICODE und _MBCS nicht definiert.|_MBCS definiert|_UNICODE definiert|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsnset_s**|**_strnset_s**|**_mbsnbset_s**|**_wcsnset_s**|
|**_tcsnset_s_l**|**_strnset_s_l**|**_mbsnbset_s_l**|**_wcsnset_s_l**|

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**_strnset_s**|\<string.h>|
|**_strnset_s_l**|\<tchar.h>|
|**_wcsnset_s**|\<string.h> oder \<wchar.h>|
|**_wcsnset_s_l**|\<tchar.h>|
|**_mbsnset_s**, **_mbsnset_s_l**|\<mbstring.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt_strnset_s.c
#include <string.h>
#include <stdio.h>

int main( void )
{
   char string[15] = "This is a test";
   /* Set not more than 4 characters of string to be *'s */
   printf( "Before: %s\n", string );
   _strnset_s( string, sizeof(string), '*', 4 );
   printf( "After:  %s\n", string );
}
```

```Output
Before: This is a test
After:  **** is a test
```

## <a name="see-also"></a>Siehe auch

[String-Manipulation](../../c-runtime-library/string-manipulation-crt.md)<br/>
[Locale](../../c-runtime-library/locale.md)<br/>
[Interpretation von Multibyte-Zeichensequenzen](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[strcat, wcscat, _mbscat](strcat-wcscat-mbscat.md)<br/>
[strcmp, wcscmp, _mbscmp](strcmp-wcscmp-mbscmp.md)<br/>
[strcpy, wcscpy, _mbscpy](strcpy-wcscpy-mbscpy.md)<br/>
[_strset, _strset_l, _wcsset, _wcsset_l, _mbsset, _mbsset_l](strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)<br/>
