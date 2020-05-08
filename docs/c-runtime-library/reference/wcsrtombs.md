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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: cad31f28c5542a96eae9f144344882b71806052a
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82910619"
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

*wcstr*<br/>
Indirekter Zeiger auf den Speicherort der Breitzeichenfolge, die konvertiert werden soll.

*count*<br/>
Die Anzahl der zu konvertierenden Zeichen.

*mbstate*<br/>
Ein Zeiger auf ein **mbstate_t** Konvertierungs Zustands Objekt.

## <a name="return-value"></a>Rückgabewert

Gibt die Anzahl der erfolgreich konvertierten Bytes zurück, wobei das abschließende NULL-Byte (falls vorhanden) nicht eingeschlossen ist. Andernfalls wird bei einem Fehler -1 zurückgegeben.

## <a name="remarks"></a>Hinweise

Die **wcsrgräber** -Funktion konvertiert eine Zeichenfolge mit breit Zeichen, beginnend mit dem angegebenen Konvertierungs Zustand, der in *mbstate*enthalten ist, von den Werten, auf die in *wcstr*verwiesen wird, in die Adresse von *mbstr*. Die Konvertierung wird für jedes Zeichen fortgesetzt, bis: nach einem NULL abschließenden breit Zeichen, wenn ein nicht entsprechendes Zeichen gefunden wird oder wenn das nächste Zeichen das in *count*enthaltene Limit überschreiten würde. Wenn **wcsrgräber** das breit Zeichen NULL-Zeichen (L ' \ 0 ') erkennt, entweder vor oder wenn *count* auftritt, wird es in 8-Bit 0 konvertiert und beendet.

Folglich ist die Multibytezeichenfolge bei *mbstr* nur dann NULL-terminiert, wenn **wcsrgräber** bei der Konvertierung ein breit Zeichen NULL-Zeichen trifft. Wenn die Sequenzen, auf die von *wcstr* und *mbstr* verwiesen wird, überlappen, ist das Verhalten von **wcsrgrabeln** nicht definiert. **wcsrgräbern** ist von der LC_TYPE Kategorie des aktuellen Gebiets Schemas betroffen.

Die **wcsrgräber** -Funktion unterscheidet [sich von wcstomsb, _wcstombs_l](wcstombs-wcstombs-l.md) durch die neustarthabilität. Der Konvertierungs Zustand wird für nachfolgende Aufrufe der gleichen oder anderer Neu startbarer Funktionen in *mbstate* gespeichert. Wenn sowohl Funktionen, die neu gestartet werden können, als auch Funktionen, die nicht neu gestartet werden könnnen, verwendet werden, sind die Ergebnisse undefiniert.  Beispielsweise würde eine Anwendung **wcsrlen** anstelle von **wcsnlen**verwenden, wenn ein nachfolgender **wcsr-** aufrufsausdruck anstelle von **wcstomsb**verwendet würde.

Wenn das *mbstr* -Argument **null**ist, gibt **wcsrgrabeln** die erforderliche Größe in Byte der Ziel Zeichenfolge zurück. Wenn *mbstate* den Wert NULL aufweist, wird der interne **mbstate_t** Konvertierungs Status verwendet. Wenn die Zeichenfolge *WCHAR* nicht über eine entsprechende Multibytezeichen-Zeichen Darstellung verfügt, wird-1 zurückgegeben, und der **errno** -Wert wird auf **EILSEQ**festgelegt.

In C++ hat diese Funktion eine Vorlagenüberladung, mit der die neuere, sichere Entsprechung dieser Funktion aufgerufen wird. Weitere Informationen finden Sie unter [Sichere Vorlagenüberladungen](../../c-runtime-library/secure-template-overloads.md).

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="exceptions"></a>Ausnahmen

Die **wcsrgräber** -Funktion ist multithreadsicher, solange keine Funktion im aktuellen Thread **setlocale** aufruft, während diese Funktion ausgeführt wird und *mbstate* nicht NULL ist.

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

## <a name="see-also"></a>Weitere Informationen

[Datenkonvertierung](../../c-runtime-library/data-conversion.md)<br/>
[Locale](../../c-runtime-library/locale.md)<br/>
[Interpretation von Multibyte-Zeichensequenzen](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[wcrtomb](wcrtomb.md)<br/>
[wcrtomb_s](wcrtomb-s.md)<br/>
[wctomb, _wctomb_l](wctomb-wctomb-l.md)<br/>
[wcstombs, _wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[mbsinit](mbsinit.md)<br/>
