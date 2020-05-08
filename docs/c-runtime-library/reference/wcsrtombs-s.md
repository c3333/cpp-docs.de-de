---
title: wcsrtombs_s
ms.date: 4/2/2020
api_name:
- wcsrtombs_s
- _o_wcsrtombs_s
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
- wcsrtombs_s
helpviewer_keywords:
- string conversion, wide characters
- wcsrtombs_s function
- wide characters, strings
ms.assetid: 9dccb766-113c-44bb-9b04-07a634dddec8
ms.openlocfilehash: c804d232dbcce67b8d467eaa37ccf2b15282881a
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82910598"
---
# <a name="wcsrtombs_s"></a>wcsrtombs_s

Konvertieren von Breitzeichen in die Multibyte-Zeichenfolgendarstellung. Eine Version von [wcsrtombs](wcsrtombs.md) mit Sicherheitserweiterungen, wie unter [Sicherheitsfunktionen in der CRT](../../c-runtime-library/security-features-in-the-crt.md) beschrieben.

## <a name="syntax"></a>Syntax

```C
errno_t wcsrtombs_s(
   size_t *pReturnValue,
   char *mbstr,
   size_t sizeInBytes,
   const wchar_t **wcstr,
   sizeof count,
   mbstate_t *mbstate
);
template <size_t size>
errno_t wcsrtombs_s(
   size_t *pReturnValue,
   char (&mbstr)[size],
   const wchar_t **wcstr,
   sizeof count,
   mbstate_t *mbstate
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
Die maximale Anzahl von Bytes, die im *mbstr* -Puffer gespeichert werden sollen, oder [_TRUNCATE](../../c-runtime-library/truncate.md).

*mbstate*<br/>
Ein Zeiger auf ein **mbstate_t** Konvertierungs Zustands Objekt.

## <a name="return-value"></a>Rückgabewert

Null, wenn erfolgreich, Fehlercode bei Fehler.

|Fehlerzustand|Rückgabewert und **errno**|
|---------------------|------------------------------|
|*mbstr* ist **null** , und *sizeingebytes* > 0|**Eingabe**|
|*wcstr* ist **null**|**Eingabe**|
|Der Ziel Puffer ist zu klein, um die konvertierte Zeichenfolge zu enthalten (es sei denn, die *Anzahl* **_TRUNCATE**ist; siehe Hinweise unten)|**ERANGE**|

Wenn eine dieser Bedingungen auftritt, wird die Ausnahme für ungültige Parameter aufgerufen, wie in [Parametervalidierung](../../c-runtime-library/parameter-validation.md) beschrieben. Wenn die weitere Ausführung zugelassen wird, gibt die Funktion einen Fehlercode zurück und legt **errno** wie in der Tabelle angegeben fest.

## <a name="remarks"></a>Hinweise

Die **wcsrtombs_s** -Funktion konvertiert eine Zeichenfolge mit breit Zeichen, auf die von *wcstr* verwiesen wird, in Multibytezeichen, die im Puffer gespeichert sind, auf den *mbstr*zeigt, unter Verwendung des in *mbstate*enthaltenen Konvertierungs Zustands. Die Konvertierung wird für jedes Zeichen fortgesetzt, bis eine der folgenden Bedingungen eintritt:

- Ein Breitzeichen NULL wird erkannt.

- Ein Breitzeichen, das nicht konvertiert werden kann, wird erkannt.

- Die Anzahl der im *mbstr* -Puffer gespeicherten Bytes ist " *count*".

Die Zielzeichenfolge endet immer mit NULL, selbst bei einem Fehler.

Wenn *count* der besondere Wert [_TRUNCATE](../../c-runtime-library/truncate.md)ist, konvertiert **wcsrtombs_s** so viele der Zeichen folgen, wie in den Ziel Puffer passen, während ein NULL-Terminator weiterhin Platz bleibt.

Wenn **wcsrtombs_s** die Quell Zeichenfolge erfolgreich konvertiert, wird die Größe der konvertierten Zeichenfolge (einschließlich des NULL-Terminator) in den *&#42;pReturnValue* (vorausgesetzt, dass *pReturnValue* nicht **null**ist) in Byte eingefügt. Dies tritt auch dann auf, wenn das *mbstr* -Argument **null** ist und eine Möglichkeit bietet, die erforderliche Puffergröße zu bestimmen. Beachten Sie, dass die *Anzahl* ignoriert wird, wenn *mbstr* den Wert **null**hat.

Wenn **wcsrtombs_s** ein breit Zeichen erkennt, das nicht in ein Multibytezeichen konvertiert werden kann, wird-1 in * \*pReturnValue*eingefügt, der Ziel Puffer auf eine leere Zeichenfolge festgelegt, **errno** auf **EILSEQ**festgelegt und " **EILSEQ**" zurückgegeben.

Wenn die Sequenzen, auf die von *wcstr* und *mbstr* verwiesen wird, überlappen, ist das Verhalten von **wcsrtombs_s** nicht definiert. **wcsrtombs_s** wird von der LC_TYPE Kategorie des aktuellen Gebiets Schemas beeinflusst.

> [!IMPORTANT]
> Stellen Sie sicher, dass sich *wcstr* und *mbstr* nicht überlappen und dass die Anzahl der zu konvertierenden breit *Zeichen korrekt ist* .

Die **wcsrtombs_s** -Funktion unterscheidet [sich von wcstombs_s, _wcstombs_s_l](wcstombs-s-wcstombs-s-l.md) durch die Neustart Fähigkeit. Der Konvertierungs Zustand wird für nachfolgende Aufrufe der gleichen oder anderer Neu startbarer Funktionen in *mbstate* gespeichert. Wenn sowohl Funktionen, die neu gestartet werden können, als auch Funktionen, die nicht neu gestartet werden könnnen, verwendet werden, sind die Ergebnisse undefiniert. Beispielsweise würde eine Anwendung **wcsrlen** anstelle von **wcslen**verwenden, wenn ein nachfolgende **wcsrtombs_s** anstelle von **wcstombs_s**verwendet würde.

In C++ wird die Verwendung dieser Funktionen durch Vorlagenüberladungen vereinfacht; die Überladungen können automatisch Rückschlüsse auf die Pufferlänge ziehen (wodurch kein Größenargument mehr angegeben werden muss), und sie können automatisch die älteren, nicht sicheren Funktionen durch ihre neueren, sicheren Entsprechungen ersetzen. Weitere Informationen finden Sie unter [Sichere Vorlagenüberladungen](../../c-runtime-library/secure-template-overloads.md).

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="exceptions"></a>Ausnahmen

Die **wcsrtombs_s** -Funktion ist multithreadsicher, solange keine Funktion im aktuellen Thread **setlocale** aufruft, während diese Funktion ausgeführt wird und *mbstate* gleich NULL ist.

## <a name="example"></a>Beispiel

```cpp
// crt_wcsrtombs_s.cpp
//
// This code example converts a wide
// character string into a multibyte
// character string.
//

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
    errno_t         err;
    mbstate_t       mbstate;

    // Reset to initial shift state
    ::memset((void*)&mbstate, 0, sizeof(mbstate));

    err = wcsrtombs_s(&countConverted, mbString, MB_BUFFER_SIZE,
                      &wcsIndirectString, MB_BUFFER_SIZE, &mbstate);
    if (err == EILSEQ)
    {
        printf( "An encoding error was detected in the string.\n" );
    }
    else
    {
        printf( "The string was successfully converted.\n" );
    }
}
```

```Output
The string was successfully converted.
```

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**wcsrtombs_s**|\<wchar.h>|

## <a name="see-also"></a>Weitere Informationen

[Datenkonvertierung](../../c-runtime-library/data-conversion.md)<br/>
[Locale](../../c-runtime-library/locale.md)<br/>
[Interpretation von Multibyte-Zeichensequenzen](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[wcrtomb](wcrtomb.md)<br/>
[wcrtomb_s](wcrtomb-s.md)<br/>
[wctomb, _wctomb_l](wctomb-wctomb-l.md)<br/>
[wcstombs, _wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[mbsinit](mbsinit.md)<br/>
