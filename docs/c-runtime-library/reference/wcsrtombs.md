---
title: wcsrtombs
ms.date: 4/2/2020
api_name:
- wcsrtombs
- _o_wcsrtombs
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
- wcsrtombs
helpviewer_keywords:
- wcsrtombs function
- string conversion, wide characters
- wide characters, strings
ms.assetid: a8d21fec-0d36-4085-9d81-9b1c61c7259d
ms.openlocfilehash: af22a7d55c5f4958db6962e98f212fb5bb89e61e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328055"
---
# <a name="wcsrtombs"></a>wcsrtombs

Konvertieren von Breitzeichen in die Multibyte-Zeichenfolgendarstellung. Es ist eine sicherere Version dieser Funktion verfügbar. Informationen dazu finden Sie unter [wcsrtombs_s](wcsrtombs-s.md).

## <a name="syntax"></a>Syntax

```C
size_t wcsrtombs(
   char *mbstr,
   const wchar_t **wcstr,
   sizeof count,
   mbstate_t *mbstate
);
template <size_t size>
size_t wcsrtombs(
   char (&mbstr)[size],
   const wchar_t **wcstr,
   sizeof count,
   mbstate_t *mbstate
); // C++ only
```

### <a name="parameters"></a>Parameter

*mbstr*<br/>
Der Adressspeicherort der resultierenden konvertierten Multibyte-Zeichenfolge.

*Wcstr*<br/>
Indirekter Zeiger auf den Speicherort der Breitzeichenfolge, die konvertiert werden soll.

*count*<br/>
Die Anzahl der zu konvertierenden Zeichen.

*mbstate*<br/>
Ein Zeiger auf ein **mbstate_t** Konvertierungsstatusobjekt.

## <a name="return-value"></a>Rückgabewert

Gibt die Anzahl der erfolgreich konvertierten Bytes zurück, wobei das abschließende NULL-Byte (falls vorhanden) nicht eingeschlossen ist. Andernfalls wird bei einem Fehler -1 zurückgegeben.

## <a name="remarks"></a>Bemerkungen

Die **funktion wcsrtombs** konvertiert eine Zeichenfolge mit breiten Zeichen, beginnend mit dem angegebenen Konvertierungszustand in *mbstate*, von den Werten indirekt, auf die in *wcstr*verwiesen wird, in die Adresse von *mbstr*. Die Konvertierung wird für jedes Zeichen fortgesetzt, bis: nachdem ein Null-Ende-Breitzeichen gefunden wurde, wenn ein nicht entsprechendes Zeichen gefunden wird oder wenn das nächste Zeichen den in *Count*enthaltenen Grenzwert überschreiten würde. Wenn **wcsrtombs** auf das Breitzeichen-NULL-Zeichen (L'-0') trifft, entweder vor oder wenn *die Anzahl* erfolgt, konvertiert es in eine 8-Bit-0 und stoppt.

Daher wird die Multibyte-Zeichenfolge bei *mbstr* nur dann null beendet, wenn **wcsrtombs** während der Konvertierung auf ein breites Zeichen-NULL-Zeichen trifft. Wenn sich die Sequenzen, auf die *wcstr* und *mbstr* zeigten, überlappen, ist das Verhalten von **wcsrtombs** nicht definiert. **wcsrtombs** wird von der kategorie LC_TYPE des aktuellen Gebietsschemas betroffen.

Die **wcsrtombs-Funktion** unterscheidet sich von [wcstombs, _wcstombs_l](wcstombs-wcstombs-l.md) durch ihre Neustartfähigkeit. Der Konvertierungsstatus wird in *mbstate* für nachfolgende Aufrufe derselben oder anderer neustartbarer Funktionen gespeichert. Wenn sowohl Funktionen, die neu gestartet werden können, als auch Funktionen, die nicht neu gestartet werden könnnen, verwendet werden, sind die Ergebnisse undefiniert.  Eine Anwendung würde z. B. **wcsrlen** anstelle von **wcsnlen**verwenden, wenn anstelle von **wcstombs**ein nachfolgender Aufruf von **wcsrtombs** verwendet würde.

Wenn das *mbstr-Argument* **NULL**ist, gibt **wcsrtombs** die erforderliche Größe in Bytes der Zielzeichenfolge zurück. Wenn *mbstate* null ist, wird der interne **mbstate_t** Konvertierungsstatus verwendet. Wenn die Zeichensequenz *wchar* keine entsprechende Multibyte-Zeichendarstellung hat, wird eine -1 zurückgegeben und der **Errno** auf **EILSEQ**gesetzt.

In C++ hat diese Funktion eine Vorlagenüberladung, mit der die neuere, sichere Entsprechung dieser Funktion aufgerufen wird. Weitere Informationen finden Sie unter [Sichere Vorlagenüberladungen](../../c-runtime-library/secure-template-overloads.md).

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

## <a name="exceptions"></a>Ausnahmen

Die **funktion wcsrtombs** ist multithreadsicher, solange keine Funktion im aktuellen Thread **setlocale** aufruft, während diese Funktion ausgeführt wird und der *mbstate* nicht null ist.

## <a name="example"></a>Beispiel

```cpp
// crt_wcsrtombs.cpp
// compile with: /W3
// This code example converts a wide
// character string into a multibyte
// character string.

#include <stdio.h>
#include <memory.h>
#include <wchar.h>
#include <errno.h>

#define MB_BUFFER_SIZE 100

int main()
{
    const wchar_t   wcString[] =
                    {L"Every good boy does fine."};
    const wchar_t   *wcsIndirectString = wcString;
    char            mbString[MB_BUFFER_SIZE];
    size_t          countConverted;
    mbstate_t       mbstate;

    // Reset to initial shift state
    ::memset((void*)&mbstate, 0, sizeof(mbstate));

    countConverted = wcsrtombs(mbString, &wcsIndirectString,
                               MB_BUFFER_SIZE, &mbstate); // C4996
    // Note: wcsrtombs is deprecated; consider using wcsrtombs_s
    if (errno == EILSEQ)
    {
        printf( "An encoding error was detected in the string.\n" );
    }
    else
    {
        printf( "The string was successfuly converted.\n" );
    }
}
```

```Output
The string was successfuly converted.
```

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**wcsrtombs**|\<wchar.h>|

## <a name="see-also"></a>Siehe auch

[Datenkonvertierung](../../c-runtime-library/data-conversion.md)<br/>
[Locale](../../c-runtime-library/locale.md)<br/>
[Interpretation von Multibyte-Zeichensequenzen](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[wcrtomb](wcrtomb.md)<br/>
[wcrtomb_s](wcrtomb-s.md)<br/>
[wctomb, _wctomb_l](wctomb-wctomb-l.md)<br/>
[wcstombs, _wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[mbsinit](mbsinit.md)<br/>
