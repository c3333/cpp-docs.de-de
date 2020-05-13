---
title: mbstowcs_s, _mbstowcs_s_l
ms.date: 4/2/2020
api_name:
- _mbstowcs_s_l
- mbstowcs_s
- _o__mbstowcs_s_l
- _o_mbstowcs_s
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
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-convert-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _mbstowcs_s_l
- mbstowcs_s
helpviewer_keywords:
- _mbstowcs_s_l function
- mbstowcs_s function
- mbstowcs_s_l function
ms.assetid: 2fbda953-6918-498f-b440-3e7b21ed65a4
ms.openlocfilehash: 4a6e86e1122a7392862fa34a59042c32560fd69d
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82915455"
---
# <a name="mbstowcs_s-_mbstowcs_s_l"></a>mbstowcs_s, _mbstowcs_s_l

Konvertiert eine Multibyte-Zeichensequenz in eine entsprechende Breitzeichensequenz. Versionen von [mbstowcs, _mbstowcs_l](mbstowcs-mbstowcs-l.md) mit Sicherheitsverbesserungen wie in [Sicherheitsfunktionen in der CRT](../../c-runtime-library/security-features-in-the-crt.md) beschrieben.

## <a name="syntax"></a>Syntax

```C
errno_t mbstowcs_s(
   size_t *pReturnValue,
   wchar_t *wcstr,
   size_t sizeInWords,
   const char *mbstr,
   size_t count
);
errno_t _mbstowcs_s_l(
   size_t *pReturnValue,
   wchar_t *wcstr,
   size_t sizeInWords,
   const char *mbstr,
   size_t count,
   _locale_t locale
);
template <size_t size>
errno_t mbstowcs_s(
   size_t *pReturnValue,
   wchar_t (&wcstr)[size],
   const char *mbstr,
   size_t count
); // C++ only
template <size_t size>
errno_t _mbstowcs_s_l(
   size_t *pReturnValue,
   wchar_t (&wcstr)[size],
   const char *mbstr,
   size_t count,
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>Parameter

*pReturnValue*<br/>
Die Anzahl von konvertierten Zeichen.

*wcstr*<br/>
Pufferadresse zum Speichern der resultierenden konvertierten Breitzeichenfolge.

*sizin words*<br/>
Die Größe des *wcstr* -Puffers in Wörtern.

*mbstr*<br/>
Adresse einer Multibyte-Zeichensequenz.

*count*<br/>
Die maximale Anzahl von breit Zeichen, die im *wcstr* -Puffer gespeichert werden sollen, ohne das abschließende Null-Zeichen oder [_TRUNCATE](../../c-runtime-library/truncate.md).

*locale*<br/>
Das zu verwendende Gebietsschema.

## <a name="return-value"></a>Rückgabewert

Null, wenn erfolgreich, Fehlercode bei Fehler.

|Fehlerzustand|Rückgabewert und **errno**|
|---------------------|------------------------------|
|*wcstr* ist **null** , und *sizeIn Words* > 0|**Eingabe**|
|*mbstr* ist **null** .|**Eingabe**|
|Der Ziel Puffer ist zu klein, um die konvertierte Zeichenfolge zu enthalten (es sei denn, die *Anzahl* **_TRUNCATE**ist; siehe Hinweise unten)|**ERANGE**|
|*wcstr* ist nicht **null** , und *sizeIn Words* = = 0|**Eingabe**|

Wenn eine dieser Bedingungen auftritt, wird die Ausnahme für ungültige Parameter aufgerufen, wie in [Parametervalidierung](../../c-runtime-library/parameter-validation.md) beschrieben. Wenn die weitere Ausführung zugelassen wird, gibt die Funktion einen Fehlercode zurück und legt **errno** wie in der Tabelle angegeben fest.

## <a name="remarks"></a>Hinweise

Die **mbstowcs_s** -Funktion konvertiert eine Zeichenfolge von Multibytezeichen, auf die von *mbstr* gezeigt wird, in breit Zeichen, die im Puffer gespeichert sind, auf den *wcstr*zeigt. Die Konvertierung wird für jedes Zeichen fortgesetzt, bis eine der folgenden Bedingungen eintritt:

- Ein Multibyte-Nullzeichen wird erkannt.

- Ein ungültiges Multibytezeichen wird erkannt.

- Die Anzahl der breit Zeichen, die im *wcstr* -Puffer gespeichert sind, ist " *count*".

Die Zielzeichenfolge endet immer mit NULL, selbst bei einem Fehler.

Wenn *count* der besondere Wert [_TRUNCATE](../../c-runtime-library/truncate.md)ist, konvertiert **mbstowcs_s** so viele der Zeichen folgen, wie in den Ziel Puffer passen, während ein NULL-Terminator weiterhin Platz bleibt.

Wenn **mbstowcs_s** die Quell Zeichenfolge erfolgreich konvertiert, wird die Größe der konvertierten Zeichenfolge (einschließlich des NULL-Terminator) in breit Zeichen in *&#42;pReturnValue* eingefügt (vorausgesetzt, dass *pReturnValue* nicht **null**ist). Dies tritt auch dann auf, wenn das *wcstr* -Argument **null** ist und eine Möglichkeit bietet, die erforderliche Puffergröße zu bestimmen. Beachten Sie Folgendes: Wenn *wcstr* den Wert **null**hat, wird *count* ignoriert, und *sizanwords* muss 0 sein.

Wenn **mbstowcs_s** auf ein ungültiges Multibytezeichen stößt, wird 0 in *&#42;pReturnValue*eingefügt, der Ziel Puffer auf eine leere Zeichenfolge festgelegt, **errno** auf **EILSEQ**festgelegt und " **EILSEQ**" zurückgegeben.

Wenn die Sequenzen, auf die von *mbstr* und *wcstr* verwiesen wird, überlappen, ist das Verhalten von **mbstowcs_s** nicht definiert.

> [!IMPORTANT]
> Stellen Sie sicher, dass sich *wcstr* und *mbstr* nicht überlappen *und dass die* Anzahl der zu konvertierenden Multibytezeichen korrekt widerspiegelt.

**mbstowcs_s** verwendet das aktuelle Gebiets Schema für jedes vom Gebiets Schema abhängige Verhalten. **_mbstowcs_s_l** ist beinahe identisch, verwendet jedoch stattdessen das übergebene Gebiets Schema. Weitere Informationen finden Sie unter [Locale](../../c-runtime-library/locale.md).

In C++ wird die Verwendung dieser Funktionen durch Vorlagenüberladungen vereinfacht; die Überladungen können automatisch Rückschlüsse auf die Pufferlänge ziehen (wodurch kein Größenargument mehr angegeben werden muss), und sie können automatisch die älteren, nicht sicheren Funktionen durch ihre neueren, sicheren Entsprechungen ersetzen. Weitere Informationen finden Sie unter [Sichere Vorlagenüberladungen](../../c-runtime-library/secure-template-overloads.md).

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**mbstowcs_s**|\<stdlib.h>|
|**_mbstowcs_s_l**|\<stdlib.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Weitere Informationen

[Datenkonvertierung](../../c-runtime-library/data-conversion.md)<br/>
[Locale](../../c-runtime-library/locale.md)<br/>
[MultiByteToWideChar](/windows/win32/api/stringapiset/nf-stringapiset-multibytetowidechar)<br/>
[Interpretation von Multibyte-Zeichensequenzen](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)<br/>
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[wcstombs, _wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[wctomb, _wctomb_l](wctomb-wctomb-l.md)<br/>
