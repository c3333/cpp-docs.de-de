---
title: wcstombs, _wcstombs_l
ms.date: 4/2/2020
api_name:
- wcstombs
- _wcstombs_l
- _o__wcstombs_l
- _o_wcstombs
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
- wcstombs
- _wcstombs_l
helpviewer_keywords:
- _wcstombs_l function
- wcstombs function
- string conversion, wide characters
- wide characters, converting
- wcstombs_l function
- characters, converting
- string conversion, multibyte character strings
ms.assetid: 91234252-9ea1-423a-af99-e9d0ce4a40e3
ms.openlocfilehash: fb95c6d73a3979a39995b9104a76fc42ca9e8535
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366709"
---
# <a name="wcstombs-_wcstombs_l"></a>wcstombs, _wcstombs_l

Konvertiert eine Breitzeichensequenz in eine entsprechende Multibyte-Zeichensequenz. Sicherere Versionen dieser Funktionen sind verfügbar. Informationen dazu finden Sie unter [wcstombs_s, _wcstombs_s_l](wcstombs-s-wcstombs-s-l.md).

## <a name="syntax"></a>Syntax

```C
size_t wcstombs(
   char *mbstr,
   const wchar_t *wcstr,
   size_t count
);
size_t _wcstombs_l(
   char *mbstr,
   const wchar_t *wcstr,
   size_t count,
   _locale_t locale
);
template <size_t size>
size_t wcstombs(
   char (&mbstr)[size],
   const wchar_t *wcstr,
   size_t count
); // C++ only
template <size_t size>
size_t _wcstombs_l(
   char (&mbstr)[size],
   const wchar_t *wcstr,
   size_t count,
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>Parameter

*mbstr*<br/>
Die Adresse einer Multibyte-Zeichensequenz.

*Wcstr*<br/>
Adresse einer Breitzeichensequenz.

*count*<br/>
Die maximale Anzahl von Bytes, die in der Multibyte-Ausgabezeichenfolge gespeichert werden können.

*locale*<br/>
Das zu verwendende Gebietsschema.

## <a name="return-value"></a>Rückgabewert

Wenn **wcstombs** die Multibyte-Zeichenfolge erfolgreich konvertiert, gibt es die Anzahl der Bytes zurück, die in die Multibyte-Ausgabezeichenfolge geschrieben wurden, ohne die beendende NULL (falls vorhanden). Wenn das *mbstr-Argument* **NULL**ist, gibt **wcstombs** die erforderliche Größe in Bytes der Zielzeichenfolge zurück. Wenn **wcstombs** auf ein breites Zeichen trifft, das nicht in ein Multibyte-Zeichen konvertiert werden kann, gibt es -1-Umwandlung zurück, um **size_t** einzugeben, und setzt **errno** auf **EILSEQ**.

## <a name="remarks"></a>Bemerkungen

Die **funktion wcstombs** konvertiert die Breitzeichenzeichenfolge, auf die von *wcstr* verwiesen wird, in die entsprechenden Multibyte-Zeichen und speichert die Ergebnisse im *mbstr-Array.* Der *Parameter count* gibt die maximale Anzahl von Bytes an, die in der Multibyte-Ausgabezeichenfolge gespeichert werden können (d. h. die Größe von *mbstr*). Es ist allgemein nicht bekannt, wie viele Bytes bei der Konvertierung einer Breitzeichenfolge benötigt werden. Einige Breitzeichen benötigen nur ein Byte in der Ausgabezeichenfolge; andere erfordern zwei. Wenn die Multibyte-Ausgabezeichenfolge für jedes breite Zeichen in der Eingabezeichenfolge (einschließlich des Breitzeichen-Nullzeichens) zwei Bytes enthält, ist das Ergebnis garantiert passend.

Wenn **wcstombs** auf das Breitzeichen-NULL-Zeichen (L'-0') trifft, entweder vor oder wenn *die Anzahl* erfolgt, konvertiert es in eine 8-Bit-0 und stoppt. Daher wird die Multibyte-Zeichenfolge bei *mbstr* nur dann null beendet, wenn **wcstombs** während der Konvertierung auf ein Breitzeichen-Nullzeichen trifft. Wenn sich die Sequenzen, auf die *wcstr* und *mbstr* zeigten, überlappen, ist das Verhalten von **wcstombs** nicht definiert.

Wenn das *mbstr-Argument* **NULL**ist, gibt **wcstombs** die erforderliche Größe in Bytes der Zielzeichenfolge zurück.

**wcstombs** überprüft seine Parameter. Wenn *wcstr* **NULL**ist oder wenn die *Anzahl* größer als **INT_MAX**ist, ruft diese Funktion den ungültigen Parameterhandler auf, wie unter [Parametervalidierung](../../c-runtime-library/parameter-validation.md) beschrieben. Wenn die Ausführung fortgesetzt werden darf, setzt die Funktion **errno** auf **EINVAL** und gibt -1 zurück.

**wcstombs** verwendet das aktuelle Gebietsschema für jedes gebietsschemaabhängige Verhalten. **_wcstombs_l** identisch ist, außer dass es stattdessen das übergebene Gebietsschema verwendet. Weitere Informationen finden Sie unter [Locale](../../c-runtime-library/locale.md).

In C++ haben diese Funktionen Vorlagenüberladungen, mit denen die neueren, sicheren Entsprechungen dieser Funktionen aufgerufen werden. Weitere Informationen finden Sie unter [Sichere Vorlagenüberladungen](../../c-runtime-library/secure-template-overloads.md).

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**wcstombs**|\<stdlib.h>|
|**_wcstombs_l**|\<stdlib.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

Dieses Programm veranschaulicht das Verhalten der **wcstombs-Funktion.**

```C
// crt_wcstombs.c
// compile with: /W3
// This example demonstrates the use
// of wcstombs, which converts a string
// of wide characters to a string of
// multibyte characters.

#include <stdlib.h>
#include <stdio.h>

#define BUFFER_SIZE 100

int main( void )
{
    size_t  count;
    char    *pMBBuffer = (char *)malloc( BUFFER_SIZE );
    wchar_t *pWCBuffer = L"Hello, world.";

    printf("Convert wide-character string:\n" );

    count = wcstombs(pMBBuffer, pWCBuffer, BUFFER_SIZE ); // C4996
    // Note: wcstombs is deprecated; consider using wcstombs_s instead
    printf("   Characters converted: %u\n",
            count );
    printf("    Multibyte character: %s\n\n",
           pMBBuffer );

    free(pMBBuffer);
}
```

```Output
Convert wide-character string:
   Characters converted: 13
    Multibyte character: Hello, world.
```

## <a name="see-also"></a>Siehe auch

[Datenkonvertierung](../../c-runtime-library/data-conversion.md)<br/>
[Locale](../../c-runtime-library/locale.md)<br/>
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)<br/>
[mbstowcs, _mbstowcs_l](mbstowcs-mbstowcs-l.md)<br/>
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[wctomb, _wctomb_l](wctomb-wctomb-l.md)<br/>
[WideCharToMultiByte](/windows/win32/api/stringapiset/nf-stringapiset-widechartomultibyte)<br/>
