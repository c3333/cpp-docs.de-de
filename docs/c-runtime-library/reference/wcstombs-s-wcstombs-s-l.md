---
title: wcstombs_s, _wcstombs_s_l
ms.date: 4/2/2020
api_name:
- _wcstombs_s_l
- wcstombs_s
- _o__wcstombs_s_l
- _o_wcstombs_s
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
- wcstombs_s
- _wcstombs_s_l
helpviewer_keywords:
- wcstombs_s function
- string conversion, wide characters
- wide characters, converting
- _wcstombs_s_l function
- wcstombs_s_l function
- characters, converting
- string conversion, multibyte character strings
ms.assetid: 105f2d33-221a-4f6d-864c-23c1865c42af
ms.openlocfilehash: c20066cddb3f28d31d2964ec720b64ed49836f65
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328044"
---
# <a name="wcstombs_s-_wcstombs_s_l"></a>wcstombs_s, _wcstombs_s_l

Konvertiert eine Breitzeichensequenz in eine entsprechende Multibyte-Zeichensequenz. Dies ist eine sicherere Version von [wcstombs, _wcstombs_l](wcstombs-wcstombs-l.md), wie unter [Sicherheitsfunktionen in der CRT](../../c-runtime-library/security-features-in-the-crt.md) beschrieben.

## <a name="syntax"></a>Syntax

```C
errno_t wcstombs_s(
   size_t *pReturnValue,
   char *mbstr,
   size_t sizeInBytes,
   const wchar_t *wcstr,
   size_t count
);

errno_t _wcstombs_s_l(
   size_t *pReturnValue,
   char *mbstr,
   size_t sizeInBytes,
   const wchar_t *wcstr,
   size_t count,
   _locale_t locale
);

template <size_t size>
errno_t wcstombs_s(
   size_t *pReturnValue,
   char (&mbstr)[size],
   const wchar_t *wcstr,
   size_t count
); // C++ only

template <size_t size>
errno_t _wcstombs_s_l(
   size_t *pReturnValue,
   char (&mbstr)[size],
   const wchar_t *wcstr,
   size_t count,
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>Parameter

*Preturnvalue*<br/>
Die Größe in Bytes der konvertierten Zeichenfolge, einschließlich des Nullabschlusses.

*mbstr*<br/>
Die Pufferadresse für die resultierende konvertierte Multibyte-Zeichenfolge.

*sizeInBytes*<br/>
Die Größe in *mbstr* Bytes des mbstr-Puffers.

*Wcstr*<br/>
Zeigt auf die zu konvertierende Breitzeichenfolge.

*count*<br/>
Die maximale Anzahl von Bytes, die im *mbstr-Puffer* gespeichert werden sollen, ohne das beendende NULL-Zeichen oder [_TRUNCATE](../../c-runtime-library/truncate.md).

*locale*<br/>
Das zu verwendende Gebietsschema.

## <a name="return-value"></a>Rückgabewert

Null, wenn erfolgreich, Fehlercode bei Fehler.

|Fehlerzustand|Rückgabewert und **errno**|
|---------------------|------------------------------|
|*mbstr* ist **NULL** und *sizeInBytes* > 0|**Einval**|
|*wcstr* ist **NULL**|**Einval**|
|Der Zielpuffer ist zu klein, um die konvertierte Zeichenfolge zu enthalten (es sei denn, *die Anzahl* ist **_TRUNCATE**; siehe Hinweise unten)|**ERANGE**|

Wenn eine dieser Bedingungen auftritt, wird die Ausnahme für ungültige Parameter aufgerufen, wie in [Parametervalidierung](../../c-runtime-library/parameter-validation.md) beschrieben. Wenn die Ausführung fortgesetzt werden darf, gibt die Funktion einen Fehlercode zurück und setzt **errno,** wie in der Tabelle angegeben.

## <a name="remarks"></a>Bemerkungen

Die **wcstombs_s-Funktion** konvertiert eine Zeichenfolge mit breiten Zeichen, auf die von *wcstr* verwiesen wird, in Multibyte-Zeichen, die im Puffer gespeichert sind, auf den *mbstr*zeigt. Die Konvertierung wird für jedes Zeichen fortgesetzt, bis eine der folgenden Bedingungen eintritt:

- Ein Breitzeichen NULL wird erkannt.

- Ein Breitzeichen, das nicht konvertiert werden kann, wird erkannt.

- Die Anzahl der im *mbstr-Puffer* gespeicherten Bytes entspricht *der Anzahl*.

Die Zielzeichenfolge endet immer mit NULL, selbst bei einem Fehler.

Wenn *count* der sonderwert [_TRUNCATE](../../c-runtime-library/truncate.md)ist, dann **konvertiert wcstombs_s** so viel von der Zeichenfolge, wie in den Zielpuffer passt, während dennoch Platz für einen Nullabschluss bleibt. Wenn die Zeichenfolge abgeschnitten wird, lautet der Rückgabewert **STRUNCATE**, und die Konvertierung wird als erfolgreich betrachtet.

Wenn **wcstombs_s** die Quellzeichenfolge erfolgreich konvertiert, wird die Größe in Bytes der konvertierten Zeichenfolge, einschließlich des NULL-Terminators, in *&#42;pReturnValue (vorausgesetzt,* *pReturnValue* ist nicht **NULL**). Dies tritt auch dann auf, wenn das *mbstr-Argument* **NULL** ist und eine Möglichkeit bietet, die erforderliche Puffergröße zu bestimmen. Beachten Sie, dass, wenn *mbstr* **NULL**ist, *die Anzahl* ignoriert wird.

Wenn **wcstombs_s** auf ein breites Zeichen trifft, kann es nicht in ein Multibyte-Zeichen konvertiert werden, es setzt 0 in *&#42;pReturnValue*, legt den Zielpuffer auf eine leere Zeichenfolge fest, setzt **errno** auf **EILSEQ**und gibt **EILSEQ**zurück.

Wenn sich die Sequenzen, auf die *wcstr* und *mbstr* zeigten, überlappen, ist das Verhalten von **wcstombs_s** nicht definiert.

> [!IMPORTANT]
> Stellen Sie sicher, dass sich *wcstr* und *mbstr* nicht überlappen und diese *Anzahl* die Anzahl der zu konvertierenden breiten Zeichen korrekt wiedergibt.

**wcstombs_s** verwendet das aktuelle Gebietsschema für jedes gebietsschemaabhängige Verhalten. **_wcstombs_s_l** ist identisch mit **wcstombs,** außer dass es stattdessen das übergebene Gebietsschema verwendet. Weitere Informationen finden Sie unter [Locale](../../c-runtime-library/locale.md).

In C++ wird die Verwendung dieser Funktionen durch Vorlagenüberladungen vereinfacht; die Überladungen können automatisch Rückschlüsse auf die Pufferlänge ziehen (wodurch kein Größenargument mehr angegeben werden muss), und sie können automatisch die älteren, nicht sicheren Funktionen durch ihre neueren, sicheren Entsprechungen ersetzen. Weitere Informationen finden Sie unter [Sichere Vorlagenüberladungen](../../c-runtime-library/secure-template-overloads.md).

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**wcstombs_s**|\<stdlib.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

Dieses Programm veranschaulicht das Verhalten der **wcstombs_s** Funktion.

```C
// crt_wcstombs_s.c
// This example converts a wide character
// string to a multibyte character string.
#include <stdio.h>
#include <stdlib.h>
#include <assert.h>

#define BUFFER_SIZE 100

int main( void )
{
    size_t   i;
    char      *pMBBuffer = (char *)malloc( BUFFER_SIZE );
    wchar_t*pWCBuffer = L"Hello, world.";

    printf( "Convert wide-character string:\n" );

    // Conversion
    wcstombs_s(&i, pMBBuffer, (size_t)BUFFER_SIZE,
               pWCBuffer, (size_t)BUFFER_SIZE );

    // Output
    printf("   Characters converted: %u\n", i);
    printf("    Multibyte character: %s\n\n",
     pMBBuffer );

    // Free multibyte character buffer
    if (pMBBuffer)
    {
    free(pMBBuffer);
    }
}
```

```Output
Convert wide-character string:
   Characters converted: 14
    Multibyte character: Hello, world.
```

## <a name="see-also"></a>Siehe auch

[Datenkonvertierung](../../c-runtime-library/data-conversion.md)<br/>
[Locale](../../c-runtime-library/locale.md)<br/>
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)<br/>
[mbstowcs, _mbstowcs_l](mbstowcs-mbstowcs-l.md)<br/>
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[wctomb_s, _wctomb_s_l](wctomb-s-wctomb-s-l.md)<br/>
[WideCharToMultiByte](/windows/win32/api/stringapiset/nf-stringapiset-widechartomultibyte)<br/>
