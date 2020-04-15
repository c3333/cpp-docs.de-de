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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: bfd339a38dd5df30ece72059525860603ee10748
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364184"
---
# <a name="_strncnt-_wcsncnt-_mbsnbcnt-_mbsnbcnt_l-_mbsnccnt-_mbsnccnt_l"></a>_strncnt, _wcsncnt, _mbsnbcnt, _mbsnbcnt_l, _mbsnccnt, _mbsnccnt_l

Gibt die Anzahl von Bytes oder Zeichen innerhalb einer angegebenen Zählers zurück.

> [!IMPORTANT]
> **_mbsnbcnt** **, _mbsnbcnt_l**, **_mbsnccnt**und **_mbsnccnt_l** können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden. Weitere Informationen finden Sie im Artikel [CRT functions not supported in Universal Windows Platform apps (In Apps für die universelle Windows-Plattform nicht unterstützte CRT-Funktionen)](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

*Str*<br/>
Zu untersuchende Zeichenfolge.

*count*<br/>
Anzahl der Zeichen oder Bytes, die in *str*untersucht werden sollen.

*locale*<br/>
Zu verwendendes Gebietsschema.

## <a name="return-value"></a>Rückgabewert

**_mbsnbcnt** und **_mbsnbcnt_l** die Anzahl der Bytes zurück, die in der ersten *Anzahl* von Multibyte-Zeichen von *str*gefunden wurden. **_mbsnccnt** und **_mbsnccnt_l** die Anzahl der Zeichen zurück, die in der ersten *Anzahl* von Bytes von *str*gefunden wurden. Wenn ein Nullzeichen vor Abschluss der Prüfung von *str* gefunden wird, geben sie die Anzahl der Bytes oder Zeichen zurück, die vor dem Nullzeichen gefunden wurden. Wenn *str* aus weniger als *Zählzeichen* oder Bytes besteht, geben sie die Anzahl der Zeichen oder Bytes in der Zeichenfolge zurück. Wenn *die Anzahl* kleiner als Null ist, geben sie 0 zurück. In früheren Versionen hatten diese Funktionen einen Rückgabewert vom Typ **int** statt **size_t**.

**_strncnt** gibt die Anzahl der Zeichen in den ersten *Zählbytes* der Single-Byte-Zeichenfolge *str*zurück. **_wcsncnt** gibt die Anzahl der Zeichen in den ersten *Anzahl* breit Zeichen der breit zeichenbreiten Zeichenfolge *str*zurück.

## <a name="remarks"></a>Bemerkungen

**_mbsnbcnt** und **_mbsnbcnt_l** die Anzahl der Bytes zählen, die in der ersten *Anzahl* von Multibyte-Zeichen von *str*gefunden wurden. **_mbsnbcnt** und **_mbsnbcnt_l** **mtob** ersetzen und sollte anstelle von **mtob**verwendet werden.

**_mbsnccnt** und **_mbsnccnt_l** die Anzahl der Zeichen zählen, die in der ersten *Anzahl* von Bytes von *str*gefunden wurden. Wenn **_mbsnccnt** und **_mbsnccnt_l** im zweiten Byte eines Doppelbytezeichens auf ein Nullzeichen stoßen, wird das erste Byte ebenfalls als NULL betrachtet und nicht im zurückgegebenen Zählwert enthalten. **_mbsnccnt** und **_mbsnccnt_l** **btom** ersetzen und sollte anstelle von **btom**verwendet werden.

Wenn *str* ein **NULL-Zeiger** ist oder *count* 0 ist, rufen diese Funktionen den ungültigen Parameterhandler auf, wie in [Parametervalidierung](../../c-runtime-library/parameter-validation.md)beschrieben, **errno** wird auf **EINVAL**gesetzt, und die Funktion gibt 0 zurück.

Der Ausgabewert ist von der Kategorieeinstellung **LC_CTYPE** des Gebietsschemas betroffen. Weitere Informationen finden Sie unter [setlocale](setlocale-wsetlocale.md). Die Versionen dieser Funktionen ohne das **_l**-Suffix verwenden das aktuelle Gebietsschema für dieses vom Gebietsschema abhängige Verhalten; die Versionen mit dem **_l**-Suffix sind beinahe identisch, verwenden jedoch stattdessen den ihnen übergebenen Gebietsschemaparameter. Weitere Informationen finden Sie unter [Locale](../../c-runtime-library/locale.md).

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|Routine|_UNICODE und _MBCS nicht definiert|_MBCS definiert|_UNICODE definiert|
|-------------|--------------------------------------|--------------------|-----------------------|
|**_tcsnbcnt**|**_strncnt**|**_mbsnbcnt**|**_wcsncnt**|
|**_tcsnccnt**|**_strncnt**|**_mbsnbcnt**|–|
|**_wcsncnt**|–|–|**_mbsnbcnt**|
|**_wcsncnt**|–|–|**_mbsnccnt**|
|–|–|**_mbsnbcnt_l**|**_mbsnccnt_l**|

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
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

[String-Manipulation](../../c-runtime-library/string-manipulation-crt.md)<br/>
[Locale](../../c-runtime-library/locale.md)<br/>
[Interpretation von Multibyte-Zeichensequenzen](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_mbsnbcat, _mbsnbcat_l](mbsnbcat-mbsnbcat-l.md)<br/>
