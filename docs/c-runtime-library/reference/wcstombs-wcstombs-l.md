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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 33c7554f1ab5c9822a1908a4b50d0ee0764615ae
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82910635"
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

*wcstr*<br/>
Adresse einer Breitzeichensequenz.

*count*<br/>
Die maximale Anzahl von Bytes, die in der Multibyte-Ausgabezeichenfolge gespeichert werden können.

*locale*<br/>
Das zu verwendende Gebietsschema.

## <a name="return-value"></a>Rückgabewert

Wenn **wcstomsb** die Multibytezeichenfolge erfolgreich konvertiert, wird die Anzahl von Bytes zurückgegeben, die in die Multibytezeichen-Ausgabe Zeichenfolge geschrieben werden, ohne den abschließenden NULL-Wert (sofern vorhanden) Wenn das *mbstr* -Argument **null**ist, gibt **wcstombs** die erforderliche Größe in Byte der Ziel Zeichenfolge zurück. Wenn **wcstomsb** ein breit Zeichen erkennt, das nicht in ein Multibytezeichen konvertiert werden kann, wird-1 in den Typ **size_t** umgewandelt und **errno** auf **EILSEQ**festgelegt.

## <a name="remarks"></a>Hinweise

Die **wcstomsb** -Funktion konvertiert die Zeichenfolge mit breit Zeichen, auf die von *wcstr* verwiesen wird, in die entsprechenden Multibytezeichen und speichert die Ergebnisse im *mbstr* -Array. Der *count* -Parameter gibt die maximale Anzahl von Bytes an, die in der Multibytezeichen-Ausgabe Zeichenfolge gespeichert werden können (d. h. die Größe von *mbstr*). Es ist allgemein nicht bekannt, wie viele Bytes bei der Konvertierung einer Breitzeichenfolge benötigt werden. Einige Breitzeichen benötigen nur ein Byte in der Ausgabezeichenfolge; andere erfordern zwei. Wenn in der Multibytezeichen-Ausgabe Zeichenfolge für jedes breit Zeichen in der Eingabe Zeichenfolge zwei Bytes vorhanden sind (einschließlich des breit Zeichens null), wird das Ergebnis garantiert angepasst.

Wenn **wcstomsb** das breit Zeichen NULL-Zeichen (L ' \ 0 ') erkennt, entweder vor oder wenn *count* auftritt, wird es in 8-Bit 0 konvertiert und beendet. Folglich ist die Multibytezeichenfolge bei *mbstr* nur dann NULL-terminiert, wenn **wcstomsb** bei der Konvertierung ein breit Zeichen NULL-Zeichen findet. Wenn die Sequenzen, auf die von *wcstr* und *mbstr* verwiesen wird, überlappen, ist das Verhalten von **wcstomsb** nicht definiert.

Wenn das *mbstr* -Argument **null**ist, gibt **wcstombs** die erforderliche Größe in Byte der Ziel Zeichenfolge zurück.

**wcstomsb** überprüft seine Parameter. Wenn *wcstr* **null**ist, oder wenn *count* größer als **INT_MAX**ist, ruft diese Funktion den Handler für ungültige Parameter auf, wie in [Parameter Validation (Parameter](../../c-runtime-library/parameter-validation.md) Überprüfung) beschrieben. Wenn die weitere Ausführung zugelassen wird, legt die Funktion **errno** auf **EINVAL** fest und gibt-1 zurück.

**wcstomsb** verwendet das aktuelle Gebiets Schema für jedes vom Gebiets Schema abhängige Verhalten. **_wcstombs_l** ist beinahe identisch, verwendet jedoch stattdessen das übergebene Gebiets Schema. Weitere Informationen finden Sie unter [Locale](../../c-runtime-library/locale.md).

In C++ haben diese Funktionen Vorlagenüberladungen, mit denen die neueren, sicheren Entsprechungen dieser Funktionen aufgerufen werden. Weitere Informationen finden Sie unter [Sichere Vorlagenüberladungen](../../c-runtime-library/secure-template-overloads.md).

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**wcstombs**|\<stdlib.h>|
|**_wcstombs_l**|\<stdlib.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

Dieses Programm veranschaulicht das Verhalten der **wcstomsb** -Funktion.

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

## <a name="see-also"></a>Weitere Informationen

[Datenkonvertierung](../../c-runtime-library/data-conversion.md)<br/>
[Locale](../../c-runtime-library/locale.md)<br/>
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)<br/>
[mbstowcs, _mbstowcs_l](mbstowcs-mbstowcs-l.md)<br/>
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[wctomb, _wctomb_l](wctomb-wctomb-l.md)<br/>
[WideCharToMultiByte](/windows/win32/api/stringapiset/nf-stringapiset-widechartomultibyte)<br/>
