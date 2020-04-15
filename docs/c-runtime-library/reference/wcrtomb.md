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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: eda857b80404aebe46b090741e0b56d4fe692f34
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328096"
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

*Mbchar*<br/>
Das resultierende in Multibyte konvertierte Zeichen.

*wchar*<br/>
Ein zu konvertierendes Breitzeichen.

*mbstate*<br/>
Ein Zeiger auf ein **mbstate_t** Objekt.

## <a name="return-value"></a>Rückgabewert

Gibt die Anzahl der Bytes zurück, die erforderlich sind, um das konvertierte Multibytezeichen darzustellen, oder andernfalls -1, wenn ein Fehler auftritt.

## <a name="remarks"></a>Bemerkungen

Die **wcrtomb-Funktion** konvertiert ein breites Zeichen, beginnend mit dem angegebenen Konvertierungszustand in *mbstate*, von dem in *wchar*enthaltenen Wert in die von *mbchar*dargestellte Adresse . Der Rückgabewert ist die Anzahl der Bytes, die erforderlich sind, um das entsprechende Multibyte-Zeichen darzustellen, gibt jedoch nicht mehr als **MB_CUR_MAX** Bytes zurück.

Wenn *mbstate* null ist, wird das interne **mbstate_t-Objekt** verwendet, das den Konvertierungsstatus von *mbchar* enthält. Wenn die Zeichensequenz *wchar* keine entsprechende Multibyte-Zeichendarstellung hat, wird eine -1 zurückgegeben und der **Errno** auf **EILSEQ**gesetzt.

Die **wcrtomb-Funktion** unterscheidet sich von [wctomb, _wctomb_l](wctomb-wctomb-l.md) durch ihre Neustartfähigkeit. Der Konvertierungsstatus wird in *mbstate* für nachfolgende Aufrufe derselben oder anderer neustartbarer Funktionen gespeichert. Wenn sowohl Funktionen, die neu gestartet werden können, als auch Funktionen, die nicht neu gestartet werden könnnen, verwendet werden, sind die Ergebnisse undefiniert. Eine Anwendung würde z. B. **wcsrlen** anstelle von **wcsnlen**verwenden, wenn anstelle von **wcstombs**ein nachfolgender Aufruf von **wcsrtombs** verwendet würde.

In C++ hat diese Funktion eine Vorlagenüberladung, mit der die neuere, sichere Entsprechung dieser Funktion aufgerufen wird. Weitere Informationen finden Sie unter [Sichere Vorlagenüberladungen](../../c-runtime-library/secure-template-overloads.md).

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

## <a name="exceptions"></a>Ausnahmen

Die **wcrtomb-Funktion** ist multithreadsicher, solange keine Funktion im aktuellen Thread **setlocale** aufruft, während diese Funktion ausgeführt wird und der *mbstate* null ist.

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

## <a name="see-also"></a>Siehe auch

[Datenkonvertierung](../../c-runtime-library/data-conversion.md)<br/>
[Locale](../../c-runtime-library/locale.md)<br/>
[Interpretation von Multibyte-Zeichensequenzen](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[mbsinit](mbsinit.md)<br/>
