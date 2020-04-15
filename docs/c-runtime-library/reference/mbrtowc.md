---
title: mbrtowc
ms.date: 4/2/2020
api_name:
- mbrtowc
- _o_mbrtowc
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
- mbrtowc
helpviewer_keywords:
- mbrtowc function
ms.assetid: a1e87fcc-6de0-4ca1-bf26-508d28490286
ms.openlocfilehash: be46c3f3c728b70c7cbf060572acc24662637a81
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81340928"
---
# <a name="mbrtowc"></a>mbrtowc

Konvertieren eines Multibytezeichens im aktuellen Gebietsschema in das entsprechende Breitzeichen mit der Möglichkeit des Neustarts in der Mitte eines Multibytezeichens.

## <a name="syntax"></a>Syntax

```C
size_t mbrtowc(
   wchar_t *wchar,
   const char *mbchar,
   size_t count,
   mbstate_t *mbstate
);
```

### <a name="parameters"></a>Parameter

*wchar*<br/>
Adresse eines breiten Zeichens zum Empfangen der konvertierten Breitzeichenzeichenfolge (Typ **wchar_t**). Dieser Wert kann ein NULL-Zeiger sein, wenn keine Rückgabebreitzeichen erforderlich ist.

*Mbchar*<br/>
Adresse einer Sequenz von Bytes (ein Multibytezeichen).

*count*<br/>
Anzahl zu überprüfender Bytes.

*mbstate*<br/>
Zeiger auf das Konvertierungzustandsobjekt. Wenn dieser Wert ein NULL-Zeiger ist, verwendet die Funktion ein statisches internes Konvertierungszustandsobjekt. Da das interne **mbstate_t** Objekt nicht threadsicher ist, wird empfohlen, immer ein eigenes *mbstate-Argument* zu übergeben.

## <a name="return-value"></a>Rückgabewert

Einer der folgenden Werte:

0 Die nächste *Anzahl* oder weniger Bytes vervollständigen das Multibyte-Zeichen, das das NULL-Breitzeichen darstellt, das in *wchar*gespeichert ist, wenn *wchar* kein Nullzeiger ist.

1 zu *zählen*, einschließlich Die nächste *Anzahl* oder weniger Bytes vervollständigen ein gültiges Multibyte-Zeichen. Der zurückgegebene Wert ist die Anzahl der Bytes, die das Multybytezeichen abschließen. Das Wide-Zeichen-Äquivalent wird in *wchar*gespeichert, wenn *wchar* kein Nullzeiger ist.

(size_t) (-1) Ein Codierungsfehler ist aufgetreten. Die nächste *Anzahl* oder weniger Bytes tragen nicht zu einem vollständigen und gültigen Multibyte-Zeichen bei. In diesem Fall wird **errno** auf EILSEQ gesetzt, und der Konvertierungsverschiebungsstatus in *mbstate* ist nicht angegeben.

(size_t) (-2) Die nächsten *Zählbytes* tragen zu einem unvollständigen, aber potenziell gültigen Multibyte-Zeichen bei, und alle *Zählbytes* wurden verarbeitet. In *wchar*wird kein Wert gespeichert, aber *mbstate* wird aktualisiert, um die Funktion neu zu starten.

## <a name="remarks"></a>Bemerkungen

Wenn *mbchar* ein Nullzeiger ist, entspricht die Funktion dem Aufruf:

`mbrtowc(NULL, "", 1, &mbstate)`

In diesem Fall werden der Wert der Argumente *wchar* und *count* ignoriert.

Wenn *mbchar* kein Nullzeiger ist, untersucht die Funktion *Zählbytes* von *mbchar,* um die erforderliche Anzahl von Bytes zu ermitteln, die erforderlich sind, um das nächste Multibyte-Zeichen abzuschließen. Wenn das nächste Zeichen gültig ist, wird das entsprechende Multibyte-Zeichen in *wchar* gespeichert, wenn es sich nicht um einen Nullzeiger handelt. Wenn das Zeichen das entsprechende wide NULL-Zeichen ist, ist der resultierende Zustand von *mbstate* der anfängliche Konvertierungszustand.

Die **mbrtowc-Funktion** unterscheidet sich von [mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md) durch ihre Neustartbarkeit. Der Konvertierungsstatus wird in *mbstate* für nachfolgende Aufrufe derselben oder anderer neustartbarer Funktionen gespeichert. Wenn sowohl Funktionen, die neu gestartet werden können, als auch Funktionen, die nicht neu gestartet werden könnnen, verwendet werden, sind die Ergebnisse undefiniert.  Beispielsweise sollte eine Anwendung **wcsrlen** anstelle von **wcslen** verwenden, wenn ein nachfolgender Aufruf von **wcsrtombs** anstelle von **wcstombs**verwendet wird.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

## <a name="example"></a>Beispiel

Konvertiert ein Multibytezeichen in das entsprechende Breitzeichen.

```cpp
// crt_mbrtowc.cpp

#include <stdio.h>
#include <mbctype.h>
#include <string.h>
#include <locale.h>
#include <wchar.h>

#define BUF_SIZE 100

int Sample(char* szIn, wchar_t* wcOut, int nMax)
{
    mbstate_t   state = {0}; // Initial state
    size_t      nConvResult,
                nmbLen = 0,
                nwcLen = 0;
    wchar_t*    wcCur = wcOut;
    wchar_t*    wcEnd = wcCur + nMax;
    const char* mbCur = szIn;
    const char* mbEnd = mbCur + strlen(mbCur) + 1;
    char*       szLocal;

    // Sets all locale to French_Canada.1252
    szLocal = setlocale(LC_ALL, "French_Canada.1252");
    if (!szLocal)
    {
        printf("The fuction setlocale(LC_ALL, \"French_Canada.1252\") failed!\n");
        return 1;
    }

    printf("Locale set to: \"%s\"\n", szLocal);

    // Sets the code page associated current locale's code page
    // from a previous call to setlocale.
    if (_setmbcp(_MB_CP_SBCS) == -1)
    {
        printf("The fuction _setmbcp(_MB_CP_SBCS) failed!");
        return 1;
    }

    while ((mbCur < mbEnd) && (wcCur < wcEnd))
    {
        //
        nConvResult = mbrtowc(wcCur, mbCur, 1, &state);
        switch (nConvResult)
        {
            case 0:
            {  // done
                printf("Conversion succeeded!\nMultibyte String: ");
                printf(szIn);
                printf("\nWC String: ");
                wprintf(wcOut);
                printf("\n");
                mbCur = mbEnd;
                break;
            }

            case -1:
            {  // encoding error
                printf("The call to mbrtowc has detected an encoding error.\n");
                mbCur = mbEnd;
                break;
            }

            case -2:
            {  // incomplete character
                if   (!mbsinit(&state))
                {
                    printf("Currently in middle of mb conversion, state = %x\n", state);
                    // state will contain data regarding lead byte of mb character
                }

                ++nmbLen;
                ++mbCur;
                break;
            }

            default:
            {
                if   (nConvResult > 2) // The multibyte should never be larger than 2
                {
                    printf("Error: The size of the converted multibyte is %d.\n", nConvResult);
                }

                ++nmbLen;
                ++nwcLen;
                ++wcCur;
                ++mbCur;
            break;
            }
        }
    }

   return 0;
}

int main(int argc, char* argv[])
{
    char    mbBuf[BUF_SIZE] = "AaBbCc\x9A\x8B\xE0\xEF\xF0xXyYzZ";
    wchar_t wcBuf[BUF_SIZE] = {L''};

    return Sample(mbBuf, wcBuf, BUF_SIZE);
}
```

### <a name="sample-output"></a>Beispielausgabe

```Output
Locale set to: "French_Canada.1252"
Conversion succeeded!
Multibyte String: AaBbCcÜïα∩≡xXyYzZ
WC String: AaBbCcÜïα∩≡xXyYzZ
```

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**mbrtowc**|\<wchar.h>|

## <a name="see-also"></a>Siehe auch

[Datenkonvertierung](../../c-runtime-library/data-conversion.md)<br/>
[Locale](../../c-runtime-library/locale.md)<br/>
[Interpretation von Multibyte-Zeichensequenzen](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
