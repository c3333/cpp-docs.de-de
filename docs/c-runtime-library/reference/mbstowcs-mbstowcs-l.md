---
title: mbstowcs, _mbstowcs_l
ms.date: 4/2/2020
api_name:
- mbstowcs
- _mbstowcs_l
- _o__mbstowcs_l
- _o_mbstowcs
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
- api-ms-win-crt-convert-l1-1-0.dll
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- mbstowcs
helpviewer_keywords:
- _mbstowcs_l function
- mbstowcs_l function
- mbstowcs function
ms.assetid: 96696b27-e068-4eeb-8006-3f7a0546ae6d
ms.openlocfilehash: 11ff6920ea5f1dad2925a8010c9202e012fad87a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338850"
---
# <a name="mbstowcs-_mbstowcs_l"></a>mbstowcs, _mbstowcs_l

Konvertiert eine Multibyte-Zeichensequenz in eine entsprechende Breitzeichensequenz. Sicherere Versionen dieser Funktionen sind verfügbar. Informationen dazu finden Sie unter [_mbsnbcpy_s, _mbsnbcpy_s_l](mbstowcs-s-mbstowcs-s-l.md).

## <a name="syntax"></a>Syntax

```C
size_t mbstowcs(
   wchar_t *wcstr,
   const char *mbstr,
   size_t count
);
size_t _mbstowcs_l(
   wchar_t *wcstr,
   const char *mbstr,
   size_t count,
   _locale_t locale
);
template <size_t size>
size_t mbstowcs(
   wchar_t (&wcstr)[size],
   const char *mbstr,
   size_t count
); // C++ only
template <size_t size>
size_t _mbstowcs_l(
   wchar_t (&wcstr)[size],
   const char *mbstr,
   size_t count,
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>Parameter

*Wcstr*<br/>
Adresse einer Breitzeichensequenz.

*mbstr*<br/>
Adresse einer Multibyte-Zeichensequenz.

*count*<br/>
Die maximale Anzahl zu konvertierender Multibytezeichen.

*locale*<br/>
Das zu verwendende Gebietsschema.

## <a name="return-value"></a>Rückgabewert

Wenn **mbstowcs** die Quellzeichenfolge erfolgreich konvertiert, wird die Anzahl der konvertierten Multibyte-Zeichen zurückgegeben. Wenn das *wcstr-Argument* **NULL**ist, gibt die Funktion die erforderliche Größe (in breiten Zeichen) der Zielzeichenfolge zurück. Wenn **mbstowcs** auf ein ungültiges Multibyte-Zeichen trifft, wird -1 zurückgegeben. Wenn der Rückgabewert *count*ist, wird die Zeichenfolge mit großen Zeichen nicht null-beendet.

> [!IMPORTANT]
> Stellen Sie sicher, dass *sich wcstr* und *mbstr* nicht überlappen und diese *Anzahl* die Anzahl der zu konvertierenden Multibyte-Zeichen korrekt wiedergibt.

## <a name="remarks"></a>Bemerkungen

Die **mbstowcs-Funktion** konvertiert bis zu einer maximalen Anzahl von Zähl-Multibyte-Zeichen, auf die *mbstr* zeigt, in eine Zeichenfolge mit entsprechenden breiten Zeichen, die durch das aktuelle Gebietsschema bestimmt werden. *count* Es speichert die resultierende Breitzeichenzeichenfolge an der Adresse, die durch *wcstr*dargestellt wird. Das Ergebnis ähnelt einer Reihe von Aufrufen von [mbtowc](mbtowc-mbtowc-l.md). Wenn **mbstowcs** das Nullzeichen single-byte ('''''' vor oder wenn *die Anzahl* stattfindet) findet, konvertiert es das Nullzeichen in ein Breitzeichen-NULLzeichen (L'''0') und wird beendet. Daher ist die Breitzeichenzeichenfolge bei *wcstr* nur dann null-beendet, wenn während der Konvertierung ein Nullzeichen gefunden wird. Wenn sich die Sequenzen, auf die *wcstr* und *mbstr* zeigten, überlappen, ist das Verhalten nicht definiert.

Wenn das *wcstr-Argument* **NULL**ist, gibt **mbstowcs** die Anzahl der breiten Zeichen zurück, die sich aus der Konvertierung ergeben würden, ohne einen Nullabschluss. Die Quellzeichenfolge muss auf NULL enden, damit der korrekte Wert zurückgegeben wird. Wenn Sie wollen, dass die resultierende Breitzeichenfolge auf NULL endet, fügen Sie dem Rückgabewert 1 hinzu.

Wenn das *mbstr-Argument* **NULL**ist oder wenn *count* > **INT_MAX**ist, wird der ungültige Parameterhandler aufgerufen, wie unter [Parametervalidierung](../../c-runtime-library/parameter-validation.md) beschrieben. Wenn die Ausführung fortgesetzt werden darf, wird errno auf **EINVAL** gesetzt und die Funktion gibt -1 zurück.

**mbstowcs** verwendet das aktuelle Gebietsschema für jedes gebietsschemaabhängige Verhalten. **_mbstowcs_l** identisch ist, außer dass es stattdessen das übergebene Gebietsschema verwendet. Weitere Informationen finden Sie unter [Locale](../../c-runtime-library/locale.md).

In C++ haben diese Funktionen Vorlagenüberladungen, mit denen die neueren, sicheren Entsprechungen dieser Funktionen aufgerufen werden. Weitere Informationen finden Sie unter [Sichere Vorlagenüberladungen](../../c-runtime-library/secure-template-overloads.md).

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**mbstowcs**|\<stdlib.h>|
|**_mbstowcs_l**|\<stdlib.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt_mbstowcs.c
// compile with: /W3
// illustrates the behavior of the mbstowcs function

#include <stdlib.h>
#include <stdio.h>
#include <locale.h>

int main( void )
{
    size_t size;
    int nChar = 2; // number of characters to convert
    int requiredSize;

    unsigned char    *pmbnull  = NULL;
    unsigned char    *pmbhello = NULL;
    char* localeInfo;

    wchar_t *pwchello = L"\x3042\x3043"; // 2 Hiragana characters
    wchar_t *pwc;

    /* Enable the Japanese locale and codepage */
    localeInfo = setlocale(LC_ALL, "Japanese_Japan.932");
    printf("Locale information set to %s\n", localeInfo);

    printf( "Convert to multibyte string:\n" );

    requiredSize = wcstombs( NULL, pwchello, 0); // C4996
    // Note: wcstombs is deprecated; consider using wcstombs_s
    printf("   Required Size: %d\n", requiredSize);

    /* Add one to leave room for the null terminator. */
    pmbhello = (unsigned char *)malloc( requiredSize + 1);
    if (! pmbhello)
    {
        printf("Memory allocation failure.\n");
        return 1;
    }
    size = wcstombs( pmbhello, pwchello, requiredSize + 1); // C4996
    // Note: wcstombs is deprecated; consider using wcstombs_s
    if (size == (size_t) (-1))
    {
        printf("Couldn't convert string. Code page 932 may"
                " not be available.\n");
        return 1;
    }
    printf( "   Number of bytes written to multibyte string: %u\n",
            (unsigned int) size );
    printf( "   Hex values of the" );
    printf( " multibyte characters: %#.2x %#.2x %#.2x %#.2x\n",
            pmbhello[0], pmbhello[1], pmbhello[2], pmbhello[3] );
    printf( "   Codepage 932 uses 0x81 to 0x9f as lead bytes.\n\n");

    printf( "Convert back to wide-character string:\n" );

    /* Assume we don't know the length of the multibyte string.
     Get the required size in characters, and allocate enough space. */

    requiredSize = mbstowcs(NULL, pmbhello, 0); // C4996
    /* Add one to leave room for the null terminator */
    pwc = (wchar_t *)malloc( (requiredSize + 1) * sizeof( wchar_t ));
    if (! pwc)
    {
        printf("Memory allocation failure.\n");
        return 1;
    }
    size = mbstowcs( pwc, pmbhello, requiredSize + 1); // C4996
    if (size == (size_t) (-1))
    {
       printf("Couldn't convert string--invalid multibyte character.\n");
    }
    printf( "   Characters converted: %u\n", (unsigned int)size );
    printf( "   Hex value of first 2" );
    printf( " wide characters: %#.4x %#.4x\n\n", pwc[0], pwc[1] );
    free(pwc);
    free(pmbhello);
}
```

```Output
Locale information set to Japanese_Japan.932
Convert to multibyte string:
   Required Size: 4
   Number of bytes written to multibyte string: 4
   Hex values of the  multibyte characters: 0x82 0xa0 0x82 0xa1
   Codepage 932 uses 0x81 to 0x9f as lead bytes.

Convert back to wide-character string:
   Characters converted: 2
   Hex value of first 2 wide characters: 0x3042 0x3043
```

## <a name="see-also"></a>Siehe auch

[Datenkonvertierung](../../c-runtime-library/data-conversion.md)<br/>
[Locale](../../c-runtime-library/locale.md)<br/>
[Interpretation von Multibyte-Zeichensequenzen](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)<br/>
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[wcstombs, _wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[wctomb, _wctomb_l](wctomb-wctomb-l.md)<br/>
[MultiByteToWideChar](/windows/win32/api/stringapiset/nf-stringapiset-multibytetowidechar)<br/>
