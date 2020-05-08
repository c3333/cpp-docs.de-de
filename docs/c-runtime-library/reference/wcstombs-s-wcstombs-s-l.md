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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 7254df673694bf4d91679f1a41837c10f61d28e2
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82910610"
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

*pReturnValue*<br/>
Die Größe der konvertierten Zeichenfolge in Bytes, einschließlich des NULL-Terminator.

*mbstr*<br/>
Die Pufferadresse für die resultierende konvertierte Multibyte-Zeichenfolge.

*sizeInBytes*<br/>
Die Größe des *mbstr* -Puffers in Bytes.

*wcstr*<br/>
Zeigt auf die zu konvertierende Breitzeichenfolge.

*count*<br/>
Die maximale Anzahl von Bytes, die im *mbstr* -Puffer gespeichert werden sollen, ohne das abschließende Null Zeichen oder [_TRUNCATE](../../c-runtime-library/truncate.md).

*locale*<br/>
Das zu verwendende Gebietsschema.

## <a name="return-value"></a>Rückgabewert

Null, wenn erfolgreich, Fehlercode bei Fehler.

|Fehlerzustand|Rückgabewert und **errno**|
|---------------------|------------------------------|
|*mbstr* ist **null** , und *sizeingebytes* > 0|**Eingabe**|
|*wcstr* ist **null**|**Eingabe**|
|Der Ziel Puffer ist zu klein, um die konvertierte Zeichenfolge zu enthalten (es sei denn, die *Anzahl* **_TRUNCATE**ist; siehe Hinweise unten)|**ERANGE**|

Wenn eine dieser Bedingungen auftritt, wird die Ausnahme für ungültige Parameter aufgerufen, wie in [Parametervalidierung](../../c-runtime-library/parameter-validation.md) beschrieben. Wenn die weitere Ausführung zugelassen wird, gibt die Funktion einen Fehlercode zurück und legt **errno** wie in der Tabelle angegeben fest.

## <a name="remarks"></a>Hinweise

Die **wcstombs_s** -Funktion konvertiert eine Zeichenfolge mit breit Zeichen, auf die von *wcstr* verwiesen wird, in Multibytezeichen, die im Puffer gespeichert sind, auf den von *mbstr*gezeigt Die Konvertierung wird für jedes Zeichen fortgesetzt, bis eine der folgenden Bedingungen eintritt:

- Ein Breitzeichen NULL wird erkannt.

- Ein Breitzeichen, das nicht konvertiert werden kann, wird erkannt.

- Die Anzahl der im *mbstr* -Puffer gespeicherten Bytes ist " *count*".

Die Zielzeichenfolge endet immer mit NULL, selbst bei einem Fehler.

Wenn *count* der besondere Wert [_TRUNCATE](../../c-runtime-library/truncate.md)ist, konvertiert **wcstombs_s** so viele der Zeichen folgen, wie in den Ziel Puffer passen, während ein NULL-Terminator weiterhin Platz bleibt. Wenn die Zeichenfolge abgeschnitten wird, ist der Rückgabewert " **ununcate**", und die Konvertierung wird als erfolgreich betrachtet.

Wenn **wcstombs_s** die Quell Zeichenfolge erfolgreich konvertiert, wird die Größe der konvertierten Zeichenfolge (einschließlich des NULL-Terminator) in den *&#42;pReturnValue* (vorausgesetzt, dass *pReturnValue* nicht **null**ist) in Byte eingefügt. Dies tritt auch dann auf, wenn das *mbstr* -Argument **null** ist und eine Möglichkeit bietet, die erforderliche Puffergröße zu bestimmen. Beachten Sie, dass die *Anzahl* ignoriert wird, wenn *mbstr* den Wert **null**hat.

Wenn **wcstombs_s** ein breit Zeichen erkennt, das nicht in ein Multibytezeichen konvertiert werden kann, wird 0 in *&#42;pReturnValue*eingefügt, der Ziel Puffer auf eine leere Zeichenfolge festgelegt, **errno** auf **EILSEQ**festgelegt und " **EILSEQ**" zurückgegeben.

Wenn die Sequenzen, auf die von *wcstr* und *mbstr* verwiesen wird, überlappen, ist das Verhalten von **wcstombs_s** nicht definiert.

> [!IMPORTANT]
> Stellen Sie sicher, dass sich *wcstr* und *mbstr* nicht überlappen und dass die Anzahl der zu konvertierenden breit *Zeichen korrekt ist* .

**wcstombs_s** verwendet das aktuelle Gebiets Schema für jedes vom Gebiets Schema abhängige Verhalten. **_wcstombs_s_l** ist mit **wcstomsb** identisch, mit dem Unterschied, dass es stattdessen das übergebene Gebiets Schema verwendet. Weitere Informationen finden Sie unter [Locale](../../c-runtime-library/locale.md).

In C++ wird die Verwendung dieser Funktionen durch Vorlagenüberladungen vereinfacht; die Überladungen können automatisch Rückschlüsse auf die Pufferlänge ziehen (wodurch kein Größenargument mehr angegeben werden muss), und sie können automatisch die älteren, nicht sicheren Funktionen durch ihre neueren, sicheren Entsprechungen ersetzen. Weitere Informationen finden Sie unter [Sichere Vorlagenüberladungen](../../c-runtime-library/secure-template-overloads.md).

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

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

## <a name="see-also"></a>Weitere Informationen

[Datenkonvertierung](../../c-runtime-library/data-conversion.md)<br/>
[Locale](../../c-runtime-library/locale.md)<br/>
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)<br/>
[mbstowcs, _mbstowcs_l](mbstowcs-mbstowcs-l.md)<br/>
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[wctomb_s, _wctomb_s_l](wctomb-s-wctomb-s-l.md)<br/>
[WideCharToMultiByte](/windows/win32/api/stringapiset/nf-stringapiset-widechartomultibyte)<br/>
