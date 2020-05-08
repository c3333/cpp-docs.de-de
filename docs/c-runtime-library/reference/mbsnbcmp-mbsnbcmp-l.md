---
title: _mbsnbcmp, _mbsnbcmp_l
ms.date: 4/2/2020
api_name:
- _mbsnbcmp
- _mbsnbcmp_l
- _o__mbsnbcmp
- _o__mbsnbcmp_l
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
- mbsnbcmp
- tcsnbmp
- _mbsnbcmp_l
- mbsnbcmp_l
- _mbsnbcmp
helpviewer_keywords:
- mbsnbcmp_l function
- mbsnbcmp function
- tcsncmp function
- _mbsnbcmp_l function
- _tcsncmp function
- _mbsnbcmp function
ms.assetid: dbc99e50-cf85-4e57-a13f-067591f18ac8
ms.openlocfilehash: edba674a0873b1f0a5f37457235c0dc1a8210ded
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82911975"
---
# <a name="_mbsnbcmp-_mbsnbcmp_l"></a>_mbsnbcmp, _mbsnbcmp_l

Vergleicht die ersten **n** Bytes von zwei Multibyte-Zeichen folgen.

> [!IMPORTANT]
> Diese API kann nicht in Anwendungen verwendet werden, die in Windows-Runtime ausgeführt werden. Weitere Informationen finden Sie im Artikel [CRT functions not supported in Universal Windows Platform apps (In Apps für die universelle Windows-Plattform nicht unterstützte CRT-Funktionen)](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntax

```C
int _mbsnbcmp(
   const unsigned char *string1,
   const unsigned char *string2,
   size_t count
);
int _mbsnbcmp_l(
   const unsigned char *string1,
   const unsigned char *string2,
   size_t count,
   _locale_t locale
);
```

### <a name="parameters"></a>Parameter

*Zeichenfolge1*, *Zeichenfolge2*<br/>
Die zu vergleichende Zeichenfolgen.

*count*<br/>
Die Anzahl der zu kopierenden Bytes.

*locale*<br/>
Das zu verwendende Gebietsschema.

## <a name="return-value"></a>Rückgabewert

Der Rückgabewert gibt die ordinalbeziehung zwischen den Teil Zeichenfolgen von *Zeichenfolge1* und *Zeichenfolge2*an.

|Rückgabewert|Beschreibung|
|------------------|-----------------|
|< 0|*Zeichenfolge1* Teil Zeichenfolge ist kleiner als *Zeichenfolge2* Teil Zeichenfolge.|
|0|*Zeichenfolge1* Teil Zeichenfolge ist mit *Zeichenfolge2* Teil Zeichenfolge identisch.|
|> 0|*Zeichenfolge1* Teil Zeichenfolge ist größer als *Zeichenfolge2* Teil Zeichenfolge.|

Bei einem Parameter Validierungs Fehler geben **_mbsnbcmp** und **_mbsnbcmp_l** **_NLSCMPERROR**zurück, das in \<String. h> und \<mbstring. h> definiert ist.

## <a name="remarks"></a>Hinweise

Die **_mbsnbcmp** Funktionen vergleichen höchstens die ersten *Anzahl* Bytes in *Zeichenfolge1* und *Zeichenfolge2* und geben einen Wert zurück, der die Beziehung zwischen den untergeordneten Zeichen folgen angibt. **_mbsnbcmp** ist eine Version von **_mbsnbicmp**, die Groß-/Kleinschreibung beachtet. Im Gegensatz zu **_mbsnbcoll**wird **_mbsnbcmp** nicht von der Sortierreihenfolge des Gebiets Schemas beeinflusst. **_mbsnbcmp** erkennt multibytezeichensequenzen entsprechend der aktuellen Multibytezeichen- [Codepage](../../c-runtime-library/code-pages.md).

**_mbsnbcmp** ähnelt **_mbsncmp**, außer dass **_mbsncmp** Zeichen folgen nach Zeichen und nicht nach Bytes vergleicht.

Der Ausgabewert wird von der **LC_CTYPE** Kategorieeinstellung des Gebiets Schemas beeinflusst, das die führenden Bytes und nachfolgenden Bytes von Multibytezeichen angibt. Weitere Informationen finden Sie unter [setlocale](setlocale-wsetlocale.md). Die **_mbsnbcmp** -Funktion verwendet das aktuelle Gebiets Schema für dieses vom Gebiets Schema abhängige Verhalten. Die **_mbsnbcmp_l** -Funktion ist beinahe identisch, verwendet jedoch stattdessen den *locale* -Parameter. Weitere Informationen finden Sie unter [Locale](../../c-runtime-library/locale.md).

Wenn entweder *Zeichenfolge1* oder *Zeichenfolge2* ein NULL-Zeiger ist, rufen diese Funktionen den Handler für ungültige Parameter auf, wie in [Parameter Validation (Parameter](../../c-runtime-library/parameter-validation.md)Überprüfung) beschrieben. Wenn die weitere Ausführung zugelassen wird, geben die Funktionen **_NLSCMPERROR** und **errno** auf **EINVAL**fest.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|Tchar.h-Routine|_UNICODE und _MBCS nicht definiert|_MBCS definiert|_UNICODE definiert|
|---------------------|---------------------------------------|--------------------|-----------------------|
|**_tcsncmp**|[strncmp](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)|**_mbsnbcmp**|[wcsncmp](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)|
|**_tcsncmp_l**|[strncmp](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)|**_mbsnbcml**|[wcsncmp](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)|

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**_mbsnbcmp**|\<mbstring.h>|
|**_mbsnbcmp_l**|\<mbstring.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt_mbsnbcmp.c
#include <mbstring.h>
#include <stdio.h>

char string1[] = "The quick brown dog jumps over the lazy fox";
char string2[] = "The QUICK brown fox jumps over the lazy dog";

int main( void )
{
   char tmp[20];
   int result;
   printf( "Compare strings:\n          %s\n", string1 );
   printf( "          %s\n\n", string2 );
   printf( "Function: _mbsnbcmp (first 10 characters only)\n" );
   result = _mbsncmp( string1, string2 , 10 );
   if( result > 0 )
      _mbscpy_s( tmp, sizeof(tmp), "greater than" );
   else if( result < 0 )
      _mbscpy_s( tmp, sizeof(tmp), "less than" );
   else
      _mbscpy_s( tmp, sizeof(tmp), "equal to" );
   printf( "Result:   String 1 is %s string 2\n\n", tmp );
   printf( "Function: _mbsnicmp _mbsnicmp (first 10 characters only)\n" );
   result = _mbsnicmp( string1, string2, 10 );
   if( result > 0 )
      _mbscpy_s( tmp, sizeof(tmp), "greater than" );
   else if( result < 0 )
      _mbscpy_s( tmp, sizeof(tmp), "less than" );
   else
      _mbscpy_s( tmp, sizeof(tmp), "equal to" );
   printf( "Result:   String 1 is %s string 2\n\n", tmp );
}
```

### <a name="output"></a>Output

```Output
Compare strings:
          The quick brown dog jumps over the lazy fox
          The QUICK brown fox jumps over the lazy dog

Function: _mbsnbcmp (first 10 characters only)
Result:   String 1 is greater than string 2

Function: _mbsnicmp _mbsnicmp (first 10 characters only)
Result:   String 1 is equal to string 2
```

## <a name="see-also"></a>Siehe auch

[Zeichen folgen Bearbeitung](../../c-runtime-library/string-manipulation-crt.md)<br/>
[_mbsnbcat, _mbsnbcat_l](mbsnbcat-mbsnbcat-l.md)<br/>
[_mbsnbicmp, _mbsnbicmp_l](mbsnbicmp-mbsnbicmp-l.md)<br/>
[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
[Locale](../../c-runtime-library/locale.md)<br/>
[Interpretation von Multibyte-Zeichensequenzen](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
