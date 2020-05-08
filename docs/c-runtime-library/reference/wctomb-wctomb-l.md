---
title: wctomb, _wctomb_l
ms.date: 4/2/2020
api_name:
- _wctomb_l
- wctomb
- _o__wctomb_l
- _o_wctomb
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
- api-ms-win-crt-convert-l1-1-0.dll
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wctomb
helpviewer_keywords:
- string conversion, wide characters
- wide characters, converting
- _wctomb_l function
- wctomb function
- wctomb_l function
- characters, converting
- string conversion, multibyte character strings
ms.assetid: 4a543f0e-5516-4d81-8ff2-3c5206f02ed5
ms.openlocfilehash: 0a95d61c50af5f49e69df8ae20efccfd3fb8ff5f
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82910429"
---
# <a name="wctomb-_wctomb_l"></a>wctomb, _wctomb_l

Konvertiert ein Breitzeichen in das entsprechende Multibytezeichen. Sicherere Versionen dieser Funktionen sind verfügbar. Informationen dazu finden Sie unter [wctomb_s, _wctomb_s_l](wctomb-s-wctomb-s-l.md).

## <a name="syntax"></a>Syntax

```C
int wctomb(
   char *mbchar,
   wchar_t wchar
);
int _wctomb_l(
   char *mbchar,
   wchar_t wchar,
   _locale_t locale
);
```

### <a name="parameters"></a>Parameter

*mbchar*<br/>
Die Adresse eines Multibytezeichens.

*wchar*<br/>
Ein Breitzeichen.

## <a name="return-value"></a>Rückgabewert

Wenn **wctomb** das breit Zeichen in ein Multibytezeichen konvertiert, wird die Anzahl von Bytes (die nie größer als **MB_CUR_MAX**ist) im breit Zeichen zurückgegeben. Wenn *WCHAR* das breit Zeichen NULL-Zeichen (L ' \ 0 ') ist, gibt **wcgrab** 1 zurück. Wenn der Ziel Zeiger *mbchar* **null**ist, gibt **wctomb** 0 zurück. Wenn die Konvertierung im aktuellen Gebiets Schema nicht möglich ist, gibt **wctomb** -1 zurück, und **errno** ist auf **EILSEQ**festgelegt.

## <a name="remarks"></a>Hinweise

Die **wctomb** -Funktion konvertiert das *WCHAR* -Argument in das entsprechende Multibytezeichen und speichert das Ergebnis bei *mbchar*. Sie können die Funktion von einem beliebigen Punkt in einem beliebigen Programm aufrufen. **wctomb** verwendet das aktuelle Gebiets Schema für jedes vom Gebiets Schema abhängige Verhalten. **_wctomb_l** ist mit **wctomb** identisch, mit dem Unterschied, dass es stattdessen das übergebene Gebiets Schema verwendet. Weitere Informationen finden Sie unter [Locale](../../c-runtime-library/locale.md).

**wctomb** überprüft seine Parameter. Wenn *mbchar* **null**ist, wird der Handler für ungültige Parameter aufgerufen, wie in [Parameter Validation (Parameter](../../c-runtime-library/parameter-validation.md)Überprüfung) beschrieben. Wenn die weitere Ausführung zugelassen wird, wird **errno** auf **EINVAL** festgelegt, und die Funktion gibt-1 zurück.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**wctomb**|\<stdlib.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

Dieses Programm stellt das Verhalten der Funktion „wctomb“ dar.

```cpp
// crt_wctomb.cpp
// compile with: /W3
#include <stdio.h>
#include <stdlib.h>

int main( void )
{
   int i;
   wchar_t wc = L'a';
   char *pmb = (char *)malloc( MB_CUR_MAX );

   printf( "Convert a wide character:\n" );
   i = wctomb( pmb, wc ); // C4996
   // Note: wctomb is deprecated; consider using wctomb_s
   printf( "   Characters converted: %u\n", i );
   printf( "   Multibyte character: %.1s\n\n", pmb );
}
```

```Output
Convert a wide character:
   Characters converted: 1
   Multibyte character: a
```

## <a name="see-also"></a>Weitere Informationen

[Datenkonvertierung](../../c-runtime-library/data-conversion.md)<br/>
[Locale](../../c-runtime-library/locale.md)<br/>
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)<br/>
[mbstowcs, _mbstowcs_l](mbstowcs-mbstowcs-l.md)<br/>
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[wcstombs, _wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[WideCharToMultiByte](/windows/win32/api/stringapiset/nf-stringapiset-widechartomultibyte)<br/>
