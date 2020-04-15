---
title: _mbclen, mblen, _mblen_l, _mbclen_l
description: Beschreibt die Funktionen Microsoft C Runtime Library (CRT) _mbclen, mblen, _mblen_l und _mbclen_l.
ms.date: 4/2/2020
api_name:
- _mbclen
- mblen
- _mblen_l
- _mbclen_l
- _o__mbclen
- _o__mbclen_l
- _o__mblen_l
- _o_mblen
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- mblen
- ftclen
- _mbclen
- _mbclen_l
- tclen
- _ftclen
- _tclen
- mbclen
helpviewer_keywords:
- tclen function
- _mblen_l function
- _tclen function
- mblen_l function
- _mbclen function
- _mbclen_l function
- mbclen function
- mblen function
ms.assetid: d5eb92a0-b7a3-464a-aaf7-9890a8e3ed70
ms.openlocfilehash: 76e8771898d8baa65f275304a9aefdcaeeb5b3bd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81341123"
---
# <a name="_mbclen-mblen-_mblen_l-_mbclen_l"></a>_mbclen, mblen, _mblen_l, _mbclen_l

Ruft die Länge ab und bestimmt die Gültigkeit eines Multibytezeichens.

> [!IMPORTANT]
> Diese API kann nicht in Anwendungen verwendet werden, die in Windows-Runtime ausgeführt werden. Weitere Informationen finden Sie im Artikel [CRT functions not supported in Universal Windows Platform apps (In Apps für die universelle Windows-Plattform nicht unterstützte CRT-Funktionen)](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntax

```C
size_t _mbclen(
   const unsigned char *c
);
size_t _mbclen_l(
   unsigned char const* c,
   _locale_t locale
);
int mblen(
   const char *mbstr,
   size_t count
);
int _mblen_l(
   const char *mbstr,
   size_t count,
   _locale_t locale
);
```

### <a name="parameters"></a>Parameter

*C*\
Multibytezeichen.

*mbstr*\
Adresse einer Multibytezeichen-Bytesequenz.

*Count*\
Anzahl zu überprüfender Bytes.

*locale*\
Zu verwendendes Gebietsschema.

## <a name="return-value"></a>Rückgabewert

**_mbclen** und **_mbclen_l** geben 1 oder 2 zurück, entsprechend der Länge des Multibyte-Zeichens *c*. Die Funktionen geben immer 1 für UTF-8 zurück, unabhängig davon, ob *c* Multibyte ist oder nicht. Es gibt keine Fehlerrückgabe für **_mbclen**.

Wenn *mbstr* nicht **NULL**ist, **geben** **mblen** und _mblen_l die Länge des Multibyte-Zeichens in Bytes zurück. Die **Funktionen mblen** und **_mblen_l** funktionieren auf UTF-8 korrekt und geben möglicherweise einen Wert zwischen 1 und 3 zurück. Wenn *mbstr* **NULL** ist (oder auf das Breitzeichen-NULL-Zeichen zeigt), geben **mblen** und **_mblen_l** 0 zurück. Das Objekt, auf das *mbstr* zeigt, muss ein gültiges Multibyte-Zeichen innerhalb der ersten *Zählzeichen* bilden, oder **mblen** und **_mblen_l** -1 zurückgeben.

## <a name="remarks"></a>Bemerkungen

Die **_mbclen-Funktion** gibt die Länge des Multibyte-Zeichens *c*in Bytes zurück. Wenn *c* nicht auf das Leadbyte eines Multibyte-Zeichens zeigt (wie durch einen impliziten Aufruf von [_ismbblead](ismbblead-ismbblead-l.md)bestimmt, ist das Ergebnis von **_mbclen** unvorhersehbar.

**mblen** gibt die Länge in Bytes von *mbstr* zurück, wenn es sich um ein gültiges Multibyte-Zeichen handelt. Außerdem wird die Gültigkeit von Multibyte-Zeichen bestimmt, die der Codepage zugeordnet ist. **mblen** untersucht *die Anzahl* oder weniger Bytes, die in *mbstr*enthalten sind, jedoch nicht mehr als **MB_CUR_MAX** Bytes.

Der Ausgabewert wird durch die **LC_CTYPE** Kategorieeinstellung des Gebietsschemas beeinflusst. Die Versionen dieser Funktionen ohne das **_l** Suffix verwenden das aktuelle Gebietsschema für dieses gebietsschemaabhängige Verhalten. Die **_l** Suffixed-Versionen verhalten sich gleich, verwenden jedoch den übergebenen Gebietsschemaparameter. Weitere Informationen finden Sie unter [setlocale](setlocale-wsetlocale.md) und [Locale](../../c-runtime-library/locale.md).

**_mbclen** **, _mblen_l**und **_mbclen_l** sind Microsoft-spezifisch und nicht Teil der Standard-C-Bibliothek. Wir empfehlen Ihnen nicht, sie dort zu verwenden, wo Sie portablen Code benötigen. Verwenden Sie stattdessen **mblen** oder **mbrlen** für Standard C-Kompatibilität.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|Tchar.h-Routine|_UNICODE und _MBCS nicht definiert|_MBCS definiert|_UNICODE definiert|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tclen**|Führt eine Zuordnung zum Makro oder zur Inlinefunktion aus|**_mbclen**|Führt eine Zuordnung zum Makro oder zur Inlinefunktion aus|

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**_mbclen**|\<mbstring.h>|
|**mblen**|\<stdlib.h>|
|**_mblen_l**|\<stdlib.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt_mblen.c
/* illustrates the behavior of the mblen function
*/

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
    int      i;
    char    *pmbc = (char *)malloc( sizeof( char ) );
    wchar_t  wc   = L'a';

    printf( "Convert wide character to multibyte character:\n" );
    wctomb_s( &i, pmbc, sizeof(char), wc );
    printf( "   Characters converted: %u\n", i );
    printf( "   Multibyte character: %x\n\n", *pmbc );

    i = mblen( pmbc, MB_CUR_MAX );
    printf( "Length in bytes of multibyte character %x: %u\n", *pmbc, i );

    pmbc = NULL;
    i = mblen( pmbc, MB_CUR_MAX );
    printf( "Length in bytes of NULL multibyte character %x: %u\n", pmbc, i );
}
```

```Output
Convert wide character to multibyte character:
   Characters converted: 1
   Multibyte character: 61

Length in bytes of multibyte character 61: 1
Length in bytes of NULL multibyte character 0: 0
```

## <a name="see-also"></a>Siehe auch

[Zeichenklassifizierung](../../c-runtime-library/character-classification.md)\
[Locale](../../c-runtime-library/locale.md)\
[Interpretation von Multibyte-Zeichensequenzen](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)\
[_mbccpy, _mbccpy_l](mbccpy-mbccpy-l.md)\
[mbrlen](mbrlen.md)\
[strlen, wcslen, _mbslen, _mbslen_l, _mbstrlen, _mbstrlen_l](strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)
