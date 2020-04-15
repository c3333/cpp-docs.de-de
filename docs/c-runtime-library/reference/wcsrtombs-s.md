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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 71a2206df9d3afb64fcaf62848988cf116d9071f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328104"
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

*Preturnvalue*<br/>
Die Größe in Bytes der konvertierten Zeichenfolge, einschließlich des Nullabschlusses.

*mbstr*<br/>
Die Pufferadresse für die resultierende konvertierte Multibyte-Zeichenfolge.

*sizeInBytes*<br/>
Die Größe in *mbstr* Bytes des mbstr-Puffers.

*Wcstr*<br/>
Zeigt auf die zu konvertierende Breitzeichenfolge.

*count*<br/>
Die maximale Anzahl von Bytes, die im *mbstr-Puffer* oder [_TRUNCATE](../../c-runtime-library/truncate.md)gespeichert werden sollen.

*mbstate*<br/>
Ein Zeiger auf ein **mbstate_t** Konvertierungsstatusobjekt.

## <a name="return-value"></a>Rückgabewert

Null, wenn erfolgreich, Fehlercode bei Fehler.

|Fehlerzustand|Rückgabewert und **errno**|
|---------------------|------------------------------|
|*mbstr* ist **NULL** und *sizeInBytes* > 0|**Einval**|
|*wcstr* ist **NULL**|**Einval**|
|Der Zielpuffer ist zu klein, um die konvertierte Zeichenfolge zu enthalten (es sei denn, *die Anzahl* ist **_TRUNCATE**; siehe Hinweise unten)|**ERANGE**|

Wenn eine dieser Bedingungen auftritt, wird die Ausnahme für ungültige Parameter aufgerufen, wie in [Parametervalidierung](../../c-runtime-library/parameter-validation.md) beschrieben. Wenn die Ausführung fortgesetzt werden darf, gibt die Funktion einen Fehlercode zurück und setzt **errno,** wie in der Tabelle angegeben.

## <a name="remarks"></a>Bemerkungen

Die **wcsrtombs_s-Funktion** konvertiert eine Zeichenfolge mit breiten Zeichen, auf die von *wcstr* verwiesen wird, in Multibyte-Zeichen, die im Puffer gespeichert sind, auf den *mbstr*zeigt, und verwendet den Konvertierungsstatus, der in *mbstate*enthalten ist. Die Konvertierung wird für jedes Zeichen fortgesetzt, bis eine der folgenden Bedingungen eintritt:

- Ein Breitzeichen NULL wird erkannt.

- Ein Breitzeichen, das nicht konvertiert werden kann, wird erkannt.

- Die Anzahl der im *mbstr-Puffer* gespeicherten Bytes entspricht *der Anzahl*.

Die Zielzeichenfolge endet immer mit NULL, selbst bei einem Fehler.

Wenn *count* der sonderwert [_TRUNCATE](../../c-runtime-library/truncate.md)ist, konvertiert **wcsrtombs_s** so viel von der Zeichenfolge, wie in den Zielpuffer passt, während er dennoch Platz für einen Nullabschluss lässt.

Wenn **wcsrtombs_s** die Quellzeichenfolge erfolgreich konvertiert, wird die Größe in Bytes der konvertierten Zeichenfolge, einschließlich des NULL-Terminators, in *&#42;pReturnValue (vorausgesetzt,* *pReturnValue* ist nicht **NULL**). Dies tritt auch dann auf, wenn das *mbstr-Argument* **NULL** ist und eine Möglichkeit bietet, die erforderliche Puffergröße zu bestimmen. Beachten Sie, dass, wenn *mbstr* **NULL**ist, *die Anzahl* ignoriert wird.

Wenn **wcsrtombs_s** auf ein breites Zeichen trifft, kann es nicht in ein Multibyte-Zeichen konvertiert werden, es setzt -1 in * \*pReturnValue*, legt den Zielpuffer auf eine leere Zeichenfolge fest, setzt **errno** auf **EILSEQ**und gibt **EILSEQ**zurück.

Wenn sich die Sequenzen, auf die *wcstr* und *mbstr* zeigten, überlappen, ist das Verhalten von **wcsrtombs_s** nicht definiert. **wcsrtombs_s** wird von der Kategorie LC_TYPE des aktuellen Gebietsschemas beeinflusst.

> [!IMPORTANT]
> Stellen Sie sicher, dass sich *wcstr* und *mbstr* nicht überlappen und diese *Anzahl* die Anzahl der zu konvertierenden breiten Zeichen korrekt wiedergibt.

Die **wcsrtombs_s-Funktion** unterscheidet sich von [wcstombs_s, _wcstombs_s_l](wcstombs-s-wcstombs-s-l.md) durch ihre Neustartfähigkeit. Der Konvertierungsstatus wird in *mbstate* für nachfolgende Aufrufe derselben oder anderer neustartbarer Funktionen gespeichert. Wenn sowohl Funktionen, die neu gestartet werden können, als auch Funktionen, die nicht neu gestartet werden könnnen, verwendet werden, sind die Ergebnisse undefiniert. Eine Anwendung würde z. B. **wcsrlen** anstelle von **wcslen**verwenden, wenn anstelle von **wcstombs_s**ein nachfolgender Aufruf **von wcsrtombs_s** verwendet würde.

In C++ wird die Verwendung dieser Funktionen durch Vorlagenüberladungen vereinfacht; die Überladungen können automatisch Rückschlüsse auf die Pufferlänge ziehen (wodurch kein Größenargument mehr angegeben werden muss), und sie können automatisch die älteren, nicht sicheren Funktionen durch ihre neueren, sicheren Entsprechungen ersetzen. Weitere Informationen finden Sie unter [Sichere Vorlagenüberladungen](../../c-runtime-library/secure-template-overloads.md).

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

## <a name="exceptions"></a>Ausnahmen

Die **wcsrtombs_s-Funktion** ist multithreadsicher, solange keine Funktion im aktuellen Thread **setlocale** aufruft, während diese Funktion ausgeführt wird und der *mbstate* null ist.

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

## <a name="see-also"></a>Siehe auch

[Datenkonvertierung](../../c-runtime-library/data-conversion.md)<br/>
[Locale](../../c-runtime-library/locale.md)<br/>
[Interpretation von Multibyte-Zeichensequenzen](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[wcrtomb](wcrtomb.md)<br/>
[wcrtomb_s](wcrtomb-s.md)<br/>
[wctomb, _wctomb_l](wctomb-wctomb-l.md)<br/>
[wcstombs, _wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[mbsinit](mbsinit.md)<br/>
