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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- mbrlen
helpviewer_keywords:
- mbrlen function
ms.assetid: dde8dee9-e091-4c4c-81b3-639808885ae1
ms.openlocfilehash: 7503de22a8310335ddd678335916d3e74dab6e70
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81340991"
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

*Str*<br/>
Zeiger auf das nächste Byte, das in einer Multibytezeichenfolge überprüft werden soll.

*count*<br/>
Die maximale Anzahl der zu überprüfenden Bytes.

*mbstate*<br/>
Zeiger auf den aktuellen Verschiebungszustand des anfangs entersten Bytes von *str*.

## <a name="return-value"></a>Rückgabewert

Einer der folgenden Werte:

|||
|-|-|
0|Die nächste *Anzahl* oder weniger Bytes vervollständigen das Multibyte-Zeichen, das das breite Nullzeichen darstellt.
1 zu *zählen*, inklusive|Die nächste *Anzahl* oder weniger Bytes vervollständigen ein gültiges Multibyte-Zeichen. Der zurückgegebene Wert ist die Anzahl der Bytes, die das Multybytezeichen abschließen.
(size_t)(-2)|Die nächsten *Zählbytes* tragen zu einem unvollständigen, aber potenziell gültigen Multibyte-Zeichen bei, und alle *Zählbytes* wurden verarbeitet.
(size_t)(-1)|Es ist ein Codierungsfehler aufgetreten. Die nächste *Anzahl* oder weniger Bytes tragen nicht zu einem vollständigen und gültigen Multibyte-Zeichen bei. In diesem Fall wird **errno** auf EILSEQ gesetzt, und der Konvertierungsstatus in *mbstate* ist nicht angegeben.

## <a name="remarks"></a>Bemerkungen

Die **mbrlen-Funktion** überprüft höchstens *Diebys,* beginnend mit dem Byte, auf das durch *str* verwiesen wird, um die Anzahl der Bytes zu bestimmen, die erforderlich sind, um das nächste Multibyte-Zeichen abzuschließen, einschließlich aller Verschiebungssequenzen. Sie entspricht dem `mbrtowc(NULL, str, count, &mbstate)` Aufruf, bei dem *mbstate* entweder ein vom Benutzer bereitgestelltes **mbstate_t** Objekt oder ein statisches internes Objekt ist, das von der Bibliothek bereitgestellt wird.

Die **mbrlen-Funktion** speichert und verwendet den Verschiebungszustand eines unvollständigen Multibyte-Zeichens im *mbstate-Parameter.* Dies gibt **mbrlen** die Möglichkeit, bei Bedarf in der Mitte eines Multibyte-Zeichens neu zu starten und höchstens *Zählbytes* zu untersuchen. Wenn *mbstate* ein Nullzeiger ist, verwendet **mbrlen** ein internes, statisches **mbstate_t** Objekt, um den Verschiebungszustand zu speichern. Da das interne **mbstate_t** Objekt nicht threadsicher ist, wird empfohlen, dass Sie immer Ihren eigenen *mbstate-Parameter* zuweisen und übergeben.

Die **mbrlen-Funktion** unterscheidet sich von [_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md) durch ihre Neustartfähigkeit. Der Verschiebungsstatus wird in *mbstate* für nachfolgende Aufrufe derselben oder anderer neustartbarer Funktionen gespeichert. Wenn sowohl Funktionen, die neu gestartet werden können, als auch Funktionen, die nicht neu gestartet werden könnnen, verwendet werden, sind die Ergebnisse undefiniert.  Beispielsweise sollte eine Anwendung **wcsrlen** anstelle von **wcslen** verwenden, wenn ein nachfolgender Aufruf von **wcsrtombs** anstelle von **wcstombs**verwendet wird.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|TCHAR.H-Routine|_UNICODE und _MBCS nicht definiert.|_MBCS definiert|_UNICODE definiert|
|---------------------|------------------------------------|--------------------|-----------------------|
|nicht zutreffend|nicht zutreffend|**mbrlen**|nicht zutreffend|

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**mbrlen**|\<wchar.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

Dieses Beispiel zeigt, wie die Interpretation von Mehrbytezeichen von der aktuellen Codepage abhängt, und veranschaulicht die Wiederaufnahmefunktion von **mbrlen**.

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

## <a name="see-also"></a>Siehe auch

[String-Manipulation](../../c-runtime-library/string-manipulation-crt.md)<br/>
[Locale](../../c-runtime-library/locale.md)<br/>
