---
title: wctomb_s, _wctomb_s_l
ms.date: 4/2/2020
api_name:
- _wctomb_s_l
- wctomb_s
- _o__wctomb_s_l
- _o_wctomb_s
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wctomb_s
- _wctomb_s_l
helpviewer_keywords:
- wctomb_s function
- wctomb_s_l function
- string conversion, wide characters
- wide characters, converting
- _wctomb_s_l function
- characters, converting
- string conversion, multibyte character strings
ms.assetid: 7e94a888-deed-4dbd-b5e9-d4a0455538b8
ms.openlocfilehash: 1ddc9a991f28c4a2ea491f3ddd04d78f6345e255
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367250"
---
# <a name="wctomb_s-_wctomb_s_l"></a>wctomb_s, _wctomb_s_l

Konvertiert ein Breitzeichen in das entsprechende Multibytezeichen. Eine Version von [wctomb, _wctomb_l](wctomb-wctomb-l.md) mit Sicherheitserweiterungen, wie unter [Sicherheitsfunktionen in der CRT](../../c-runtime-library/security-features-in-the-crt.md) beschrieben.

## <a name="syntax"></a>Syntax

```C
errno_t wctomb_s(
   int *pRetValue,
   char *mbchar,
   size_t sizeInBytes,
   wchar_t wchar
);
errno_t _wctomb_s_l(
   int *pRetValue,
   char *mbchar,
   size_t sizeInBytes,
   wchar_t wchar,
   _locale_t locale
);
```

### <a name="parameters"></a>Parameter

*pRetValue*<br/>
Die Anzahl von Bytes oder ein Code, der das Ergebnis angibt.

*Mbchar*<br/>
Die Adresse eines Multibytezeichens.

*sizeInBytes*<br/>
Größe des *Puffers mbchar*.

*wchar*<br/>
Ein Breitzeichen.

*locale*<br/>
Das zu verwendende Gebietsschema.

## <a name="return-value"></a>Rückgabewert

Null, wenn erfolgreich, Fehlercode bei Fehler.

Fehlerbedingungen

|*Mbchar*|*sizeInBytes*|Rückgabewert|*pRetValue*|
|--------------|-------------------|------------------|-----------------|
|**Null**|>0|**Einval**|nicht geändert|
|any|>**Int_max**|**Einval**|nicht geändert|
|any|zu klein|**Einval**|nicht geändert|

Wenn eine der oben genannten Fehlerbedingungen auftritt, wird ein Handler für ungültige Parameter aufgerufen (siehe [Parametervalidierung](../../c-runtime-library/parameter-validation.md)). Wenn die Ausführung fortgesetzt werden darf, gibt **wctomb** **EINVAL** zurück und setzt **errno** auf **EINVAL**.

## <a name="remarks"></a>Bemerkungen

Die **wctomb_s-Funktion** konvertiert ihr *wchar-Argument* in das entsprechende Multibyte-Zeichen und speichert das Ergebnis bei *mbchar*. Sie können die Funktion von einem beliebigen Punkt in einem beliebigen Programm aufrufen.

Wenn **wctomb_s** das breite Zeichen in ein Multibyte-Zeichen konvertiert, setzt es die Anzahl der Bytes (die nie größer als **MB_CUR_MAX**ist) im breiten Zeichen in die ganze Zahl, auf die *pRetValue*zeigt. Wenn *wchar* das Breitzeichen-Nullzeichen ist (L''0'), füllt **wctomb_s** *pRetValue* mit 1. Wenn der Zielzeiger *mbchar* **NULL**ist, **setzt wctomb_s** 0 in *pRetValue*. Wenn die Konvertierung im aktuellen Gebietsschema nicht möglich ist, **setzt wctomb_s** -1 in *pRetValue*.

**wctomb_s** verwendet das aktuelle Gebietsschema für gebietsschemaabhängige Informationen. **_wctomb_s_l** ist identisch, außer dass es stattdessen das übergebene Gebietsschema verwendet. Weitere Informationen finden Sie unter [Locale](../../c-runtime-library/locale.md).

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**wctomb_s**|\<stdlib.h>|
|**_wctomb_s_l**|\<stdlib.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

Dieses Programm veranschaulicht das Verhalten der **wctomb-Funktion.**

```cpp
// crt_wctomb_s.cpp
#include <stdio.h>
#include <stdlib.h>

int main( void )
{
    int i;
    wchar_t wc = L'a';
    char *pmb = (char *)malloc( MB_CUR_MAX );

    printf_s( "Convert a wide character:\n" );
    wctomb_s( &i, pmb, MB_CUR_MAX, wc );
    printf_s( "   Characters converted: %u\n", i );
    printf_s( "   Multibyte character: %.1s\n\n", pmb );
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
