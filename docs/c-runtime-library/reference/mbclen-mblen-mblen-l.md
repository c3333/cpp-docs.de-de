---
title: _mbclen, mblen, _mblen_l, _mbclen_l
description: Beschreibt die Funktionen der Microsoft C-Lauf Zeit Bibliothek (CRT) _mbclen, Mblen, _mblen_l und _mbclen_l.
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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: b004babc9e7c82d25cd52ec036c3061c99b5f367
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82914361"
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

*scher*\
Multibytezeichen.

*mbstr*\
Adresse einer Multibytezeichen-Bytesequenz.

*count*\
Anzahl zu überprüfender Bytes.

*Konfigurations*\
Zu verwendendes Gebietsschema.

## <a name="return-value"></a>Rückgabewert

**_mbclen** und **_mbclen_l** gibt 1 oder 2 zurück, gemäß der Länge des multibytezeichens *c*. Die Funktionen geben immer 1 für UTF-8 zurück, unabhängig davon, ob *c* Multibytezeichen ist oder nicht. Es gibt keine Fehlerrückgabe für **_mbclen**.

Wenn *mbstr* nicht **null**ist, geben **mblen** und **_mblen_l** die Länge des multibytezeichens in Byte zurück. Die **mblen** -und **_mblen_l** -Funktionen funktionieren ordnungsgemäß für UTF-8 und geben möglicherweise einen Wert zwischen 1 und 3 zurück. Wenn *mbstr* **null** ist (oder auf das breit Zeichen NULL zeigt), geben **mblen** und **_mblen_l** 0 zurück. Das Objekt, auf das *mbstr* zeigt, muss ein gültiges Multibytezeichen innerhalb der ersten *Anzahl* von Zeichen oder **mblen** und **_mblen_l** Rückgabe-1 bilden.

## <a name="remarks"></a>Hinweise

Die **_mbclen** -Funktion gibt die Länge des multibytezeichens *c*in Byte zurück. Wenn *c* nicht auf das führende Byte eines multibytezeichens zeigt (wie durch einen impliziten- [_ismbblead](ismbblead-ismbblead-l.md)festgelegt, ist das Ergebnis von **_mbclen** unvorhersehbar.

**mblen** gibt die Länge von *mbstr* in Byte zurück, wenn es sich um ein gültiges Multibytezeichen handelt. Außerdem wird die mit der Codepage verknüpfte Multibyte-Zeichen Gültigkeit bestimmt. **mblen** untersucht *Anzahl* oder weniger Bytes, die in *mbstr*enthalten sind, jedoch nicht mehr als **MB_CUR_MAX** bytes.

Der Ausgabewert wird von der **LC_CTYPE** Kategorieeinstellung des Gebiets Schemas beeinflusst. Die Versionen dieser Funktionen ohne das **_l** -Suffix verwenden das aktuelle Gebiets Schema für dieses vom Gebiets Schema abhängige Verhalten. Die **_l** suffittversionen Verhalten sich identisch, verwenden jedoch stattdessen den übergebenen Gebiets Schema Parameter. Weitere Informationen finden Sie unter [setlocale](setlocale-wsetlocale.md) und [locale](../../c-runtime-library/locale.md).

**_mbclen**, **_mblen_l**und **_mbclen_l** sind Microsoft-spezifisch, nicht Teil der Standard-C-Bibliothek. Wir empfehlen Ihnen nicht, Sie zu verwenden, wenn Sie portablen Code verwenden möchten. Verwenden Sie für die Standard-C-Kompatibilität stattdessen **mblen** oder **mbrlen** .

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

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

## <a name="see-also"></a>Weitere Informationen

[Zeichen Klassifizierung](../../c-runtime-library/character-classification.md)\
[Konfigurations](../../c-runtime-library/locale.md)\
[Interpretation von Multibyte-Zeichensequenzen](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)\
[_mbccpy _mbccpy_l](mbccpy-mbccpy-l.md)\
[mbrlen](mbrlen.md)\
[strlen, wcslen, _mbslen, _mbslen_l, _mbstrlen, _mbstrlen_l](strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)
