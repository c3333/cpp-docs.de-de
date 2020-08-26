---
title: mbrlen
ms.date: 4/2/2020
api_name:
- mbrlen
- _o_mbrlen
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
- api-ms-win-crt-string-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- mbrlen
helpviewer_keywords:
- mbrlen function
ms.assetid: dde8dee9-e091-4c4c-81b3-639808885ae1
ms.openlocfilehash: 2e0e0ec9d92744fc904bae5ac7f91db8049de4cd
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88842116"
---
# <a name="mbrlen"></a>mbrlen

Bestimmen der Anzahl der Bytes, die zum Ausführen eines Multibytezeichens im aktuellen Gebietsschemas erforderlich sind, mit der Möglichkeit des Neustarts in der Mitte eines Multibytezeichens.

## <a name="syntax"></a>Syntax

```C
size_t mbrlen(
   const char * str,
   size_t count,
   mbstate_t * mbstate
);
```

### <a name="parameters"></a>Parameter

*SRT*<br/>
Zeiger auf das nächste Byte, das in einer Multibytezeichenfolge überprüft werden soll.

*count*<br/>
Die maximale Anzahl der zu überprüfenden Bytes.

*mbstate*<br/>
Zeiger auf den aktuellen UMSCHALT Zustand des ersten Bytes von *Str*.

## <a name="return-value"></a>Rückgabewert

Einer der folgenden Werte:

| Wert | Beschreibung |
|--|--|
| 0 | Die nächste *Anzahl* oder weniger Bytes vervollständigen das Multibytezeichen, das das breite NULL-Zeichen darstellt. |
| 1 zum *zählen*, inklusiv | Die nächste *Anzahl* oder weniger Bytes vervollständigen ein gültiges Multibytezeichen. Der zurückgegebene Wert ist die Anzahl der Bytes, die das Multybytezeichen abschließen. |
| (size_t)(-2) | Die nächsten *Anzahl* Bytes tragen zu einem unvollständigen, aber potenziell gültigen Multibytezeichen bei, und alle *Anzahl* Bytes wurden verarbeitet. |
| (size_t)(-1) | Es ist ein Codierungsfehler aufgetreten. Die nächste *Anzahl* oder weniger Bytes tragen nicht zu einem kompletten und gültigen Multibytezeichen bei. In diesem Fall wird **errno** auf EILSEQ festgelegt, und der Konvertierungs Zustand in *mbstate* ist nicht angegeben. |

## <a name="remarks"></a>Bemerkungen

Die **mbrlen** -Funktion unter *sucht höchstens Anzahl Bytes beginnend* mit dem Byte, auf das *Str* zeigt, um die Anzahl von Bytes zu bestimmen, die zum Vervollständigen des nächsten multibytezeichens erforderlich sind, einschließlich der Verschiebe Sequenzen. Dies entspricht dem-Befehl `mbrtowc(NULL, str, count, &mbstate)` , bei dem *mbstate* entweder ein vom Benutzer bereitgestelltes **mbstate_t** Objekt oder ein statisches internes Objekt ist, das von der Bibliothek bereitgestellt wird.

Die **mbrlen** -Funktion speichert und verwendet den UMSCHALT Zustand eines unvollständigen multibytezeichens im *mbstate* -Parameter. Dies ermöglicht es **mbrlen** , bei Bedarf in der Mitte eines multibytezeichens neu zu starten, wobei höchstens *Anzahl* Bytes untersucht werden. Wenn *mbstate* ein NULL-Zeiger ist, verwendet **mbrlen** ein internes, statisches **mbstate_t** Objekt zum Speichern des UMSCHALT Zustands. Da das interne **mbstate_t** Objekt nicht Thread sicher ist, wird empfohlen, immer ihren eigenen *mbstate* -Parameter zuzuordnen und zu übergeben.

Die **mbrlen** -Funktion unterscheidet sich von [_mbclen, Mblen, _mblen_l](mbclen-mblen-mblen-l.md) durch die neustarbarkeit. Der Verschiebungs Zustand wird für nachfolgende Aufrufe der gleichen oder anderer Neu startbarer Funktionen in *mbstate* gespeichert. Wenn sowohl Funktionen, die neu gestartet werden können, als auch Funktionen, die nicht neu gestartet werden könnnen, verwendet werden, sind die Ergebnisse undefiniert.  Beispielsweise sollte eine Anwendung **wcsrlen** anstelle von **wcslen** verwenden, wenn ein nachfolgender **wcsr-** aufrufsausdruck anstelle von **wcstomb**verwendet wird.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|TCHAR.H-Routine|_UNICODE und _MBCS nicht definiert.|_MBCS definiert|_UNICODE definiert|
|---------------------|------------------------------------|--------------------|-----------------------|
|nicht zutreffend|nicht zutreffend|**mbrlen**|nicht zutreffend|

## <a name="requirements"></a>Anforderungen

|-Routine zurückgegebener Wert|Erforderlicher Header|
|-------------|---------------------|
|**mbrlen**|\<wchar.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

Dieses Beispiel zeigt, wie die Interpretation von Multibytezeichen von der aktuellen Codepage abhängt, und veranschaulicht die fort Setz **barkeit von mbrlen**.

```C
// crt_mbrlen.c
// Compile by using: cl crt_mbrlen.c
#include <stdlib.h>
#include <stdio.h>
#include <string.h>
#include <locale.h>
#include <wchar.h>

size_t Example(const char * pStr)
{
    size_t      charLen = 0;
    size_t      charCount = 0;
    mbstate_t   mbState = {0};

    while ((charLen = mbrlen(pStr++, 1, &mbState)) != 0 &&
            charLen != (size_t)-1)
    {
        if (charLen != (size_t)-2) // if complete mbcs char,
        {
            charCount++;
        }
    }
    return (charCount);
}

int main( void )
{
    int         cp;
    size_t      charCount = 0;
    const char  *pSample =
        "\x82\xD0\x82\xE7\x82\xAA\x82\xC8: Shift-jis hiragana.";

    cp = _getmbcp();
    charCount = Example(pSample);
    printf("\nCode page: %d\n%s\nCharacter count: %d\n",
        cp, pSample, charCount);

    setlocale(LC_ALL, "ja-JP"); // Set Japanese locale
    _setmbcp(932); // and Japanese multibyte code page
    cp = _getmbcp();
    charCount = Example(pSample);
    printf("\nCode page: %d\n%s\nCharacter count: %d\n",
        cp, pSample, charCount);
}
```

```Output

Code page: 0
é╨éτé¬é╚: Shift-jis hiragana.
Character count: 29

Code page: 932
????: Shift-jis hiragana.
Character count: 25
```

## <a name="see-also"></a>Weitere Informationen

[Zeichen folgen Bearbeitung](../../c-runtime-library/string-manipulation-crt.md)<br/>
[Gebietsschema](../../c-runtime-library/locale.md)<br/>
