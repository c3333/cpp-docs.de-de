---
title: wcrtomb
ms.date: 4/2/2020
api_name:
- wcrtomb
- _o_wcrtomb
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
- wcrtomb
helpviewer_keywords:
- wide characters, converting
- wcrtomb function
- multibyte characters
- characters, converting
ms.assetid: 717f1b21-2705-4b7f-b6d0-82adc5224340
ms.openlocfilehash: 4107ae6cb6366fa8ad80251ce94ee35ca59501bd
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82910643"
---
# <a name="wcrtomb"></a>wcrtomb

Konvertieren von Breitzeichen in die Multibyte-Zeichendarstellung. Es ist eine sicherere Version dieser Funktion verfügbar. Informationen dazu finden Sie unter [wcrtomb_s](wcrtomb-s.md).

## <a name="syntax"></a>Syntax

```C
size_t wcrtomb(
   char *mbchar,
   wchar_t wchar,
   mbstate_t *mbstate
);
template <size_t size>
size_t wcrtomb(
   char (&mbchar)[size],
   wchar_t wchar,
   mbstate_t *mbstate
); // C++ only
```

### <a name="parameters"></a>Parameter

*mbchar*<br/>
Das resultierende in Multibyte konvertierte Zeichen.

*wchar*<br/>
Ein zu konvertierendes Breitzeichen.

*mbstate*<br/>
Ein Zeiger auf ein **mbstate_t** Objekt.

## <a name="return-value"></a>Rückgabewert

Gibt die Anzahl der Bytes zurück, die erforderlich sind, um das konvertierte Multibytezeichen darzustellen, oder andernfalls -1, wenn ein Fehler auftritt.

## <a name="remarks"></a>Hinweise

Die **wcrtomb** -Funktion konvertiert ein breit Zeichen, beginnend mit dem angegebenen Konvertierungs Zustand in *mbstate*, von dem in *WCHAR*enthaltenen Wert in die von *mbchar*dargestellte Adresse. Der Rückgabewert ist die Anzahl der Bytes, die erforderlich sind, um das entsprechende Multibytezeichen darzustellen, aber es werden nicht mehr als **MB_CUR_MAX** Bytes zurückgegeben.

Wenn *mbstate* den Wert NULL aufweist, wird das interne **mbstate_t** Objekt verwendet, das den Konvertierungs Status von *mbchar* enthält. Wenn die Zeichenfolge *WCHAR* nicht über eine entsprechende Multibytezeichen-Zeichen Darstellung verfügt, wird-1 zurückgegeben, und der **errno** -Wert wird auf **EILSEQ**festgelegt.

Die **wcrtomb** -Funktion unterscheidet [sich von wctomb, _wctomb_l](wctomb-wctomb-l.md) durch die neustarbarkeit. Der Konvertierungs Zustand wird für nachfolgende Aufrufe der gleichen oder anderer Neu startbarer Funktionen in *mbstate* gespeichert. Wenn sowohl Funktionen, die neu gestartet werden können, als auch Funktionen, die nicht neu gestartet werden könnnen, verwendet werden, sind die Ergebnisse undefiniert. Beispielsweise würde eine Anwendung **wcsrlen** anstelle von **wcsnlen**verwenden, wenn ein nachfolgender **wcsr-** aufrufsausdruck anstelle von **wcstomsb**verwendet würde.

In C++ hat diese Funktion eine Vorlagenüberladung, mit der die neuere, sichere Entsprechung dieser Funktion aufgerufen wird. Weitere Informationen finden Sie unter [Sichere Vorlagenüberladungen](../../c-runtime-library/secure-template-overloads.md).

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="exceptions"></a>Ausnahmen

Die **wcrtomb** -Funktion ist multithreadsicher, solange keine Funktion im aktuellen Thread **setlocale** aufruft, während diese Funktion ausgeführt wird und der *mbstate* gleich NULL ist.

## <a name="example"></a>Beispiel

```C
// crt_wcrtomb.c
// compile with: /W3
// This program converts a wide character
// to its corresponding multibyte character.

#include <string.h>
#include <stdio.h>
#include <wchar.h>

int main( void )
{
    size_t      sizeOfCovertion = 0;
    mbstate_t   mbstate;
    char        mbStr = 0;
    wchar_t*    wcStr = L"Q";

    // Reset to initial conversion state
    memset(&mbstate, 0, sizeof(mbstate));

    sizeOfCovertion = wcrtomb(&mbStr, *wcStr, &mbstate); // C4996
    // Note: wcrtomb is deprecated; consider using wcrtomb_s instead
    if (sizeOfCovertion > 0)
    {
        printf("The corresponding wide character \"");
        wprintf(L"%s\"", wcStr);
        printf(" was converted to the \"%c\" ", mbStr);
        printf("multibyte character.\n");
    }
    else
    {
        printf("No corresponding multibyte character "
               "was found.\n");
    }
}
```

```Output
The corresponding wide character "Q" was converted to the "Q" multibyte character.
```

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**wcrtomb**|\<wchar.h>|

## <a name="see-also"></a>Weitere Informationen

[Datenkonvertierung](../../c-runtime-library/data-conversion.md)<br/>
[Locale](../../c-runtime-library/locale.md)<br/>
[Interpretation von Multibyte-Zeichensequenzen](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[mbsinit](mbsinit.md)<br/>
