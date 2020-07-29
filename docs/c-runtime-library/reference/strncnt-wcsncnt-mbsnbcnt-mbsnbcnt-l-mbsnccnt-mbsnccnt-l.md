---
title: _strncnt, _wcsncnt, _mbsnbcnt, _mbsnbcnt_l, _mbsnccnt, _mbsnccnt_l
ms.date: 4/2/2020
api_name:
- _mbsnbcnt_l
- _mbsnccnt
- _wcsncnt
- _strncnt
- _mbsnccnt_l
- _mbsnbcnt
- _o__mbsnbcnt
- _o__mbsnbcnt_l
- _o__mbsnccnt
- _o__mbsnccnt_l
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _mbsnbcnt
- wcsncnt
- _tcsnbcnt
- _mbsnccnt
- _ftcsnbcnt
- mbsnbcnt
- strncnt
- mbsnbcnt_l
- mbsnccnt_l
- mbsnccnt
- _strncnt
- _wcsncnt
helpviewer_keywords:
- _strncnt function
- _mbsnbcnt function
- _mbsnbcnt_l function
- _mbsnccnt_l function
- mbsnbcnt_l function
- mbsnbcnt function
- tcsnbcnt function
- mbsnccnt_l function
- strncnt function
- _tcsnbcnt function
- mbsnccnt function
- wcsncnt function
- _mbsnccnt function
- _wcsncnt function
ms.assetid: 2a022e9e-a307-4acb-a66b-e56e5357f848
ms.openlocfilehash: 77746af98e5d62b80d5a0d2d93eb1f717c74b33e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231337"
---
# <a name="_strncnt-_wcsncnt-_mbsnbcnt-_mbsnbcnt_l-_mbsnccnt-_mbsnccnt_l"></a>_strncnt, _wcsncnt, _mbsnbcnt, _mbsnbcnt_l, _mbsnccnt, _mbsnccnt_l

Gibt die Anzahl von Bytes oder Zeichen innerhalb einer angegebenen Zählers zurück.

> [!IMPORTANT]
> **_mbsnbcnt**, **_mbsnbcnt_l**, **_mbsnccnt**und **_mbsnccnt_l** können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden. Weitere Informationen finden Sie im Artikel [CRT functions not supported in Universal Windows Platform apps (In Apps für die universelle Windows-Plattform nicht unterstützte CRT-Funktionen)](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntax

```C
size_t _strncnt(
   const char *str,
   size_t count
);
size_t _wcsncnt(
   const wchar_t *str,
   size_t count
);
size_t _mbsnbcnt(
   const unsigned char *str,
   size_t count
);
size_t _mbsnbcnt_l(
   const unsigned char *str,
   size_t count,
   _locale_t locale
);
size_t _mbsnccnt(
   const unsigned char *str,
   size_t count
);
size_t _mbsnccnt_l(
   const unsigned char *str,
   size_t count,
   _locale_t locale
);
```

### <a name="parameters"></a>Parameter

*str*<br/>
Zu untersuchende Zeichenfolge.

*count*<br/>
Anzahl von Zeichen oder bytes, die in *Str*untersucht werden sollen.

*locale*<br/>
Zu verwendendes Gebietsschema.

## <a name="return-value"></a>Rückgabewert

**_mbsnbcnt** und **_mbsnbcnt_l** geben die Anzahl der Bytes zurück, die in der ersten *Anzahl* von Multibytezeichen-Zeichen von *Str*gefunden wurden. **_mbsnccnt** und **_mbsnccnt_l** geben die Anzahl der Zeichen zurück, die in der ersten *Anzahl* der Bytes von *Str*gefunden wurden. Wenn ein NULL-Zeichen gefunden wird, bevor die Untersuchung von *Str* abgeschlossen ist, geben Sie die Anzahl von Bytes oder Zeichen zurück, die vor dem NULL-Zeichen gefunden wurden. Wenn *Str* weniger als *Anzahl* Zeichen oder Bytes umfasst, wird die Anzahl der Zeichen oder Bytes in der Zeichenfolge zurückgegeben. Wenn *count* kleiner als 0 (null) ist, wird 0 zurückgegeben. In früheren Versionen hatten diese Funktionen einen Rückgabewert vom Typ **`int`** statt **size_t**.

**_strncnt** gibt die Anzahl von Zeichen in den ersten *Anzahl* Bytes der Einzel Byte Zeichenfolge *Str*zurück. **_wcsncnt** gibt die Anzahl der Zeichen in der ersten *Anzahl* von breit Zeichen der breit Zeichen-Zeichenfolge *Str*zurück.

## <a name="remarks"></a>Bemerkungen

**_mbsnbcnt** und **_mbsnbcnt_l** zählen die Anzahl der Bytes, die in der ersten *Anzahl* von Multibytezeichen-Zeichen von *Str*gefunden wurden. **_mbsnbcnt** und **_mbsnbcnt_l** ersetzen Sie **mtob** und sollten anstelle von **mtob**verwendet werden.

**_mbsnccnt** und **_mbsnccnt_l** zählt die Anzahl der Zeichen, die in der ersten *Anzahl* von Bytes von *Str*gefunden werden. Wenn **_mbsnccnt** und **_mbsnccnt_l** im zweiten Byte eines Doppelbyte Zeichens auf ein NULL-Zeichen stoßen, wird das erste Byte auch als null betrachtet und ist nicht im zurückgegebenen Zählwert enthalten. **_mbsnccnt** und **_mbsnccnt_l** ersetzen Sie **btom** und sollten anstelle von **btom**verwendet werden.

Wenn *Str* ein **null** -Zeiger ist oder *count* auf 0 festgelegt ist, rufen diese Funktionen den Handler für ungültige Parameter auf, wie in [Parameter Validierung](../../c-runtime-library/parameter-validation.md)beschrieben, **errno** ist auf **EINVAL**festgelegt, und die Funktion gibt 0 zurück.

Der Ausgabewert ist von der Kategorieeinstellung **LC_CTYPE** des Gebietsschemas betroffen. Weitere Informationen finden Sie unter [setlocale](setlocale-wsetlocale.md). Die Versionen dieser Funktionen ohne das **_l**-Suffix verwenden das aktuelle Gebietsschema für dieses vom Gebietsschema abhängige Verhalten; die Versionen mit dem **_l**-Suffix sind beinahe identisch, verwenden jedoch stattdessen den ihnen übergebenen Gebietsschemaparameter. Weitere Informationen finden Sie unter [Locale](../../c-runtime-library/locale.md).

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|-Routine zurückgegebener Wert|_UNICODE und _MBCS nicht definiert|_MBCS definiert|_UNICODE definiert|
|-------------|--------------------------------------|--------------------|-----------------------|
|**_tcsnbcnt**|**_strncnt**|**_mbsnbcnt**|**_wcsncnt**|
|**_tcsnccnt**|**_strncnt**|**_mbsnbcnt**|–|
|**_wcsncnt**|–|–|**_mbsnbcnt**|
|**_wcsncnt**|–|–|**_mbsnccnt**|
|–|–|**_mbsnbcnt_l**|**_mbsnccnt_l**|

## <a name="requirements"></a>Anforderungen

|-Routine zurückgegebener Wert|Erforderlicher Header|
|-------------|---------------------|
|**_mbsnbcnt**|\<mbstring.h>|
|**_mbsnbcnt_l**|\<mbstring.h>|
|**_mbsnccnt**|\<mbstring.h>|
|**_mbsnccnt_l**|\<mbstring.h>|
|**_strncnt**|\<tchar.h>|
|**_wcsncnt**|\<tchar.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt_mbsnbcnt.c

#include  <mbstring.h>
#include  <stdio.h>

int main( void )
{
   unsigned char str[] = "This is a multibyte-character string.";
   unsigned int char_count, byte_count;
   char_count = _mbsnccnt( str, 10 );
   byte_count = _mbsnbcnt( str, 10 );
   if ( byte_count - char_count )
      printf( "The first 10 characters contain %d multibyte characters\n", char_count );
   else
      printf( "The first 10 characters are single-byte.\n");
}
```

### <a name="output"></a>Output

```Output
The first 10 characters are single-byte.
```

## <a name="see-also"></a>Siehe auch

[Zeichen folgen Bearbeitung](../../c-runtime-library/string-manipulation-crt.md)<br/>
[Gebietsschema](../../c-runtime-library/locale.md)<br/>
[Interpretation von Multibyte-Zeichensequenzen](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_mbsnbcat, _mbsnbcat_l](mbsnbcat-mbsnbcat-l.md)<br/>
