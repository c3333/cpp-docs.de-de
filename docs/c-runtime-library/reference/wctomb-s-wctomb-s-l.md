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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 63839f70fa334fadd961eb173343d1b406268cfd
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82910445"
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

*mbchar*<br/>
Die Adresse eines Multibytezeichens.

*sizeInBytes*<br/>
Größe des Puffers *mbchar*.

*wchar*<br/>
Ein Breitzeichen.

*locale*<br/>
Das zu verwendende Gebietsschema.

## <a name="return-value"></a>Rückgabewert

Null, wenn erfolgreich, Fehlercode bei Fehler.

Fehlerbedingungen

|*mbchar*|*sizeInBytes*|Rückgabewert|*pRetValue*|
|--------------|-------------------|------------------|-----------------|
|**Normal**|>0|**Eingabe**|nicht geändert|
|any|>**INT_MAX**|**Eingabe**|nicht geändert|
|any|zu klein|**Eingabe**|nicht geändert|

Wenn eine der oben genannten Fehlerbedingungen auftritt, wird ein Handler für ungültige Parameter aufgerufen (siehe [Parametervalidierung](../../c-runtime-library/parameter-validation.md)). Wenn die weitere Ausführung zugelassen wird, gibt **wctomb** **EINVAL** zurück und legt **errno** auf **EINVAL**fest.

## <a name="remarks"></a>Hinweise

Die **wctomb_s** -Funktion konvertiert das *WCHAR* -Argument in das entsprechende Multibytezeichen und speichert das Ergebnis bei *mbchar*. Sie können die Funktion von einem beliebigen Punkt in einem beliebigen Programm aufrufen.

Wenn **wctomb_s** das breit Zeichen in ein Multibytezeichen konvertiert, wird die Anzahl von Bytes (die nie größer als **MB_CUR_MAX**ist) im breit Zeichen in die ganze Zahl eingefügt, auf die von *pRetValue*verwiesen wird. Wenn *WCHAR* das breit Zeichen NULL-Zeichen (L ' \ 0 ') ist, **wctomb_s** füllt wctomb_s *pRetValue* mit 1. Wenn der Ziel Zeiger *mbchar* **null**ist, gibt **wctomb_s** 0 in *pRetValue*ein. Wenn die Konvertierung im aktuellen Gebiets Schema nicht möglich ist, **wctomb_s** den Wert-1 in *pRetValue*.

**wctomb_s** verwendet das aktuelle Gebiets Schema für Gebiets Schema abhängige Informationen. **_wctomb_s_l** ist beinahe identisch, verwendet jedoch stattdessen das übergebene Gebiets Schema. Weitere Informationen finden Sie unter [Locale](../../c-runtime-library/locale.md).

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**wctomb_s**|\<stdlib.h>|
|**_wctomb_s_l**|\<stdlib.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

Dieses Programm veranschaulicht das Verhalten der **wctomb** -Funktion.

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

## <a name="see-also"></a>Weitere Informationen

[Datenkonvertierung](../../c-runtime-library/data-conversion.md)<br/>
[Locale](../../c-runtime-library/locale.md)<br/>
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)<br/>
[mbstowcs, _mbstowcs_l](mbstowcs-mbstowcs-l.md)<br/>
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[wcstombs, _wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[WideCharToMultiByte](/windows/win32/api/stringapiset/nf-stringapiset-widechartomultibyte)<br/>
