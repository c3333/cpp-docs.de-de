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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 162585ea866b4fb26cfaae3bc94345dadaba0baa
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367404"
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

*Mbchar*<br/>
Die Adresse eines Multibytezeichens.

*wchar*<br/>
Ein Breitzeichen.

## <a name="return-value"></a>Rückgabewert

Wenn **wctomb** das breite Zeichen in ein Multibyte-Zeichen konvertiert, gibt es die Anzahl der Bytes (die nie größer als **MB_CUR_MAX**ist) im Breitzeichen zurück. Wenn *wchar* das Nullzeichen mit einem breitzeichenden Zeichen (L''0') ist, gibt **wctomb** 1 zurück. Wenn der Zielzeiger *mbchar* **NULL**ist, gibt **wctomb** 0 zurück. Wenn die Konvertierung im aktuellen Gebietsschema nicht möglich ist, gibt **wctomb** -1 zurück und **errno** wird auf **EILSEQ**gesetzt.

## <a name="remarks"></a>Bemerkungen

Die **wctomb-Funktion** konvertiert ihr *wchar-Argument* in das entsprechende Multibyte-Zeichen und speichert das Ergebnis bei *mbchar*. Sie können die Funktion von einem beliebigen Punkt in einem beliebigen Programm aufrufen. **wctomb** verwendet das aktuelle Gebietsschema für jedes gebietsschemaabhängige Verhalten. **_wctomb_l** ist identisch mit **wctomb,** außer dass es stattdessen das übergebene Gebietsschema verwendet. Weitere Informationen finden Sie unter [Locale](../../c-runtime-library/locale.md).

**wctomb** überprüft seine Parameter. Wenn *mbchar* **NULL**ist, wird der ungültige Parameterhandler aufgerufen, wie unter [Parametervalidierung](../../c-runtime-library/parameter-validation.md)beschrieben. Wenn die Ausführung fortgesetzt werden darf, wird **errno** auf **EINVAL** gesetzt und die Funktion gibt -1 zurück.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

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

## <a name="see-also"></a>Siehe auch

[Datenkonvertierung](../../c-runtime-library/data-conversion.md)<br/>
[Locale](../../c-runtime-library/locale.md)<br/>
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)<br/>
[mbstowcs, _mbstowcs_l](mbstowcs-mbstowcs-l.md)<br/>
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[wcstombs, _wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[WideCharToMultiByte](/windows/win32/api/stringapiset/nf-stringapiset-widechartomultibyte)<br/>
