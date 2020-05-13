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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- mbrtowc
helpviewer_keywords:
- mbrtowc function
ms.assetid: a1e87fcc-6de0-4ca1-bf26-508d28490286
ms.openlocfilehash: a77049edba9a98d9e3e4df93ee2ba007a3eb7381
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919190"
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
Adresse eines breit Zeichens, das die konvertierte Zeichenfolge mit breit Zeichen (Type **wchar_t**) empfangen soll. Dieser Wert kann ein NULL-Zeiger sein, wenn keine Rückgabebreitzeichen erforderlich ist.

*mbchar*<br/>
Adresse einer Sequenz von Bytes (ein Multibytezeichen).

*count*<br/>
Anzahl zu überprüfender Bytes.

*mbstate*<br/>
Zeiger auf das Konvertierungzustandsobjekt. Wenn dieser Wert ein NULL-Zeiger ist, verwendet die Funktion ein statisches internes Konvertierungszustandsobjekt. Da das interne **mbstate_t** Objekt nicht Thread sicher ist, wird empfohlen, immer Ihr eigenes *mbstate* -Argument zu übergeben.

## <a name="return-value"></a>Rückgabewert

Einer der folgenden Werte:

0 die nächste *Anzahl* oder weniger Bytes vervollständigen das Multibytezeichen, das das NULL-breit Zeichen darstellt, das in *WCHAR*gespeichert wird, wenn *WCHAR* kein NULL-Zeiger ist.

1 zum *zählen*, einschließlich der nächsten *Anzahl* oder weniger Bytes, vervollständigen Sie ein gültiges Multibytezeichen. Der zurückgegebene Wert ist die Anzahl der Bytes, die das Multybytezeichen abschließen. Die Entsprechung für breit Zeichen wird in *WCHAR*gespeichert, wenn *WCHAR* kein NULL-Zeiger ist.

(size_t) (-1) Codierungsfehler. Die nächste *Anzahl* oder weniger Bytes tragen nicht zu einem kompletten und gültigen Multibytezeichen bei. In diesem Fall wird **errno** auf EILSEQ festgelegt, und der Konvertierungs Verschiebungs Zustand in *mbstate* ist nicht angegeben.

(size_t) (-2) Die nächsten *Anzahl* Bytes tragen zu einem unvollständigen, aber potenziell gültigen Multibytezeichen bei, und alle *Anzahl* Bytes wurden verarbeitet. In *WCHAR*ist kein Wert gespeichert, aber *mbstate* wird aktualisiert, um die Funktion neu zu starten.

## <a name="remarks"></a>Hinweise

Wenn *mbchar* ein NULL-Zeiger ist, entspricht die Funktion dem-Befehl:

`mbrtowc(NULL, "", 1, &mbstate)`

In diesem Fall werden der Wert der Argumente " *WCHAR* " und " *count* " ignoriert.

Wenn *mbchar* kein NULL-Zeiger ist, untersucht die Funktion *count* Bytes aus *mbchar* , um die erforderliche Anzahl von Bytes zu bestimmen, die zum Vervollständigen des nächsten multibytezeichens erforderlich sind. Wenn das nächste Zeichen gültig ist, wird das entsprechende Multibytezeichen in *WCHAR* gespeichert, wenn es kein NULL-Zeiger ist. Wenn das Zeichen das entsprechende Breite Null-Zeichen ist, ist der resultierende Zustand von *mbstate* der anfängliche Konvertierungs Zustand.

Die **mbrtowc** -Funktion unterscheidet [sich von mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md) durch die neustarbarkeit. Der Konvertierungs Zustand wird für nachfolgende Aufrufe der gleichen oder anderer Neu startbarer Funktionen in *mbstate* gespeichert. Wenn sowohl Funktionen, die neu gestartet werden können, als auch Funktionen, die nicht neu gestartet werden könnnen, verwendet werden, sind die Ergebnisse undefiniert.  Beispielsweise sollte eine Anwendung **wcsrlen** anstelle von **wcslen** verwenden, wenn ein nachfolgender **wcsr-** aufrufsausdruck anstelle von **wcstomb**verwendet wird.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

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

## <a name="see-also"></a>Weitere Informationen

[Datenkonvertierung](../../c-runtime-library/data-conversion.md)<br/>
[Locale](../../c-runtime-library/locale.md)<br/>
[Interpretation von Multibyte-Zeichensequenzen](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
