---
title: _strset, _strset_l, _wcsset, _wcsset_l, _mbsset, _mbsset_l
ms.date: 4/2/2020
api_name:
- _wcsset
- _mbsset
- _strset_l
- _strset
- _wcsset_l
- _mbsset_l
- _o__mbsset
- _o__mbsset_l
- _o__wcsset
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
- mbsset
- _strset_l
- _mbsset
- _strset
- mbsset_l
- strset_l
- _wcsset
- _ftcsset
- wcsset_l
- _tcsset_l
- _mbsset_l
- _wcsset_l
- _fstrset
- _tcsset
helpviewer_keywords:
- _wcsset_l function
- _tcsset function
- wcsset_l function
- _ftcsset function
- characters [C++], setting
- _strset function
- ftcsset function
- strings [C++], setting characters
- mbsset function
- tcsset_l function
- _fstrset function
- mbsset_l function
- strset_l function
- _wcsset function
- _mbsset function
- _mbsset_l function
- tcsset function
- _strset_l function
- fstrset function
- _tcsset_l function
ms.assetid: c42ded42-2ed9-4f06-a0a9-247ba305473a
ms.openlocfilehash: 53a4fa3fecd021b42ec2b69b804cde35570b1a6d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81316892"
---
# <a name="_strset-_strset_l-_wcsset-_wcsset_l-_mbsset-_mbsset_l"></a>_strset, _strset_l, _wcsset, _wcsset_l, _mbsset, _mbsset_l

Legt Zeichen einer Zeichenfolge auf ein Zeichen fest. Sicherere Versionen dieser Funktionen sind verfügbar. Informationen dazu finden Sie unter [_strset_s, _strset_s_l, _wcsset_s, _wcsset_s_l, _mbsset_s, _mbsset_s_l](strset-s-strset-s-l-wcsset-s-wcsset-s-l-mbsset-s-mbsset-s-l.md).

> [!IMPORTANT]
> **_mbsset** und **_mbsset_l** können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden. Weitere Informationen finden Sie im Artikel [CRT functions not supported in Universal Windows Platform apps (In Apps für die universelle Windows-Plattform nicht unterstützte CRT-Funktionen)](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntax

```C
char *_strset(
   char *str,
   int c
);
char *_strset_l(
   char *str,
   int c,
   locale_t locale
);
wchar_t *_wcsset(
   wchar_t *str,
   wchar_t c
);
wchar_t *_wcsset_l(
   wchar_t *str,
   wchar_t c,
   locale_t locale
);
unsigned char *_mbsset(
   unsigned char *str,
   unsigned int c
);
unsigned char *_mbsset_l(
   unsigned char *str,
   unsigned int c,
   _locale_t locale
);
```

### <a name="parameters"></a>Parameter

*Str*<br/>
Festzulegende mit NULL endende Zeichenfolge.

*C*<br/>
Zeicheneinstellung.

*locale*<br/>
Zu verwendendes Gebietsschema.

## <a name="return-value"></a>Rückgabewert

Gibt einen Zeiger zur geänderten Zeichenfolge zurück.

## <a name="remarks"></a>Bemerkungen

Die **_strset-Funktion** legt alle Zeichen (mit Ausnahme des beendenden Nullzeichens) von *str* auf *c*fest, konvertiert in **char**. **_wcsset** und **_mbsset_l** sind Breitzeichen- und Multibyte-Versionen von **_strset**, und die Datentypen der Argumente und Rückgabewerte variieren entsprechend. Anderenfalls verhalten sich diese Funktionen identisch.

**_mbsset** überprüft seine Parameter. Wenn *str* ein Nullzeiger ist, wird der ungültige Parameterhandler aufgerufen, wie unter [Parametervalidierung](../../c-runtime-library/parameter-validation.md)beschrieben. Wenn die Ausführung fortgesetzt werden darf, **gibt _mbsset** **NULL** zurück und setzt **errno** auf **EINVAL**. **_strset** und **_wcsset** überprüfen ihre Parameter nicht.

Der Ausgabewert wird durch die Einstellung der **LC_CTYPE** Kategorieeinstellung des Gebietsschemas beeinflusst. weitere Informationen finden Sie unter [setlocale, _wsetlocale.](setlocale-wsetlocale.md) Die Versionen dieser Funktionen sind identisch, mit der Ausnahme, dass die Versionen, die nicht über das **_l** Suffix verfügen, das aktuelle Gebietsschema verwenden und die, die über das **_l** Suffix verfügen, stattdessen den übergebenen Gebietsschemaparameter verwenden. Weitere Informationen finden Sie unter [Locale](../../c-runtime-library/locale.md).

> [!IMPORTANT]
> Diese Funktionen sind möglicherweise für Pufferüberlaufrisiken anfällig. Pufferüberläufe können für Systemangriffe eingesetzt werden, da sie zu einer unbefugten Ausweitung der Berechtigungen führen. Weitere Informationen finden Sie unter [Vermeiden von Pufferüberläufen](/windows/win32/SecBP/avoiding-buffer-overruns).

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|TCHAR.H-Routine|_UNICODE und _MBCS nicht definiert.|_MBCS definiert|_UNICODE definiert|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsset**|**_strset**|**_mbsset**|**_wcsset**|
|**_tcsset_l**|**_strset_l**|**_mbsset_l**|**_wcsset_l**|

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**_strset**|\<string.h>|
|**_strset_l**|\<tchar.h>|
|**_wcsset**|\<string.h> oder \<wchar.h>|
|**_wcsset_l**|\<tchar.h>|
|**_mbsset**, **_mbsset_l**|\<mbstring.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt_strset.c
// compile with: /W3

#include <string.h>
#include <stdio.h>

int main( void )
{
   char string[] = "Fill the string with something.";
   printf( "Before: %s\n", string );
   _strset( string, '*' ); // C4996
   // Note: _strset is deprecated; consider using _strset_s instead
   printf( "After:  %s\n", string );
}
```

```Output
Before: Fill the string with something.
After:  *******************************
```

## <a name="see-also"></a>Siehe auch

[String-Manipulation](../../c-runtime-library/string-manipulation-crt.md)<br/>
[Locale](../../c-runtime-library/locale.md)<br/>
[Interpretation von Multibyte-Zeichensequenzen](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_mbsnbset, _mbsnbset_l](mbsnbset-mbsnbset-l.md)<br/>
[memset, wmemset](memset-wmemset.md)<br/>
[strcat, wcscat, _mbscat](strcat-wcscat-mbscat.md)<br/>
[strcmp, wcscmp, _mbscmp](strcmp-wcscmp-mbscmp.md)<br/>
[strcpy, wcscpy, _mbscpy](strcpy-wcscpy-mbscpy.md)<br/>
[_strnset, _strnset_l, _wcsnset, _wcsnset_l, _mbsnset, _mbsnset_l](strnset-strnset-l-wcsnset-wcsnset-l-mbsnset-mbsnset-l.md)<br/>
