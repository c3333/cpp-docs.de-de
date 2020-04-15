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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 07d694a7430f23e2f9600a5d2b147bcee2ef0e09
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338811"
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

*Preturnvalue*<br/>
Die Anzahl von konvertierten Zeichen.

*Wcstr*<br/>
Pufferadresse zum Speichern der resultierenden konvertierten Breitzeichenfolge.

*sizeInWords*<br/>
Die Größe des *wcstr-Puffers* in Wörtern.

*mbstr*<br/>
Adresse einer Multibyte-Zeichensequenz.

*count*<br/>
Die maximale Anzahl von breiten Zeichen, die im *wcstr-Puffer* gespeichert werden sollen, ohne die beendende NULL oder [_TRUNCATE](../../c-runtime-library/truncate.md).

*locale*<br/>
Das zu verwendende Gebietsschema.

## <a name="return-value"></a>Rückgabewert

Null, wenn erfolgreich, Fehlercode bei Fehler.

|Fehlerzustand|Rückgabewert und **errno**|
|---------------------|------------------------------|
|*wcstr* ist **NULL** und *sizeInWords* > 0|**Einval**|
|*mbstr* ist **NULL**|**Einval**|
|Der Zielpuffer ist zu klein, um die konvertierte Zeichenfolge zu enthalten (es sei denn, *die Anzahl* ist **_TRUNCATE**; siehe Hinweise unten)|**ERANGE**|
|*wcstr* ist nicht **NULL** und *sizeInWords* == 0|**Einval**|

Wenn eine dieser Bedingungen auftritt, wird die Ausnahme für ungültige Parameter aufgerufen, wie in [Parametervalidierung](../../c-runtime-library/parameter-validation.md) beschrieben. Wenn die Ausführung fortgesetzt werden darf, gibt die Funktion einen Fehlercode zurück und setzt **errno,** wie in der Tabelle angegeben.

## <a name="remarks"></a>Bemerkungen

Die **mbstowcs_s-Funktion** konvertiert eine Zeichenfolge mit mehreren Byte-Zeichen, auf die *mbstr* zeigt, in breite Zeichen, die im Puffer gespeichert sind, auf den *wcstr*zeigt. Die Konvertierung wird für jedes Zeichen fortgesetzt, bis eine der folgenden Bedingungen eintritt:

- Ein Multibyte-Nullzeichen wird erkannt.

- Ein ungültiges Multibytezeichen wird erkannt.

- Die Anzahl der im *wcstr-Puffer* gespeicherten breiten Zeichen entspricht *der Anzahl*.

Die Zielzeichenfolge endet immer mit NULL, selbst bei einem Fehler.

Wenn *count* der sonderwert [_TRUNCATE](../../c-runtime-library/truncate.md)ist, konvertiert **mbstowcs_s** so viel von der Zeichenfolge, wie in den Zielpuffer passt, während dennoch Platz für einen Nullabschluss bleibt.

Wenn **mbstowcs_s** die Quellzeichenfolge erfolgreich konvertiert, wird die Größe in breit gefächerten Zeichen der konvertierten Zeichenfolge, einschließlich des NULL-Terminators, in *&#42;pReturnValue (vorausgesetzt,* *pReturnValue* ist nicht **NULL**). Dies tritt auch dann auf, wenn das *wcstr-Argument* **NULL** ist und eine Möglichkeit bietet, die erforderliche Puffergröße zu bestimmen. Beachten Sie, dass, wenn *wcstr* **NULL**ist, *die Anzahl* ignoriert wird und *sizeInWords* 0 sein muss.

Wenn **mbstowcs_s** auf ein ungültiges Multibyte-Zeichen trifft, setzt es 0 in *&#42;pReturnValue*, legt den Zielpuffer auf eine leere Zeichenfolge fest, setzt **errno** auf **EILSEQ**und gibt **EILSEQ**zurück.

Wenn sich die Sequenzen, auf die *mbstr* und *wcstr* zeigten, überlappen, ist das Verhalten von **mbstowcs_s** nicht definiert.

> [!IMPORTANT]
> Stellen Sie sicher, dass *sich wcstr* und *mbstr* nicht überlappen und diese *Anzahl* die Anzahl der zu konvertierenden Multibyte-Zeichen korrekt wiedergibt.

**mbstowcs_s** verwendet das aktuelle Gebietsschema für jedes gebietsschemaabhängige Verhalten. **_mbstowcs_s_l** ist identisch, außer dass es stattdessen das übergebene Gebietsschema verwendet. Weitere Informationen finden Sie unter [Locale](../../c-runtime-library/locale.md).

In C++ wird die Verwendung dieser Funktionen durch Vorlagenüberladungen vereinfacht; die Überladungen können automatisch Rückschlüsse auf die Pufferlänge ziehen (wodurch kein Größenargument mehr angegeben werden muss), und sie können automatisch die älteren, nicht sicheren Funktionen durch ihre neueren, sicheren Entsprechungen ersetzen. Weitere Informationen finden Sie unter [Sichere Vorlagenüberladungen](../../c-runtime-library/secure-template-overloads.md).

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**mbstowcs_s**|\<stdlib.h>|
|**_mbstowcs_s_l**|\<stdlib.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Siehe auch

[Datenkonvertierung](../../c-runtime-library/data-conversion.md)<br/>
[Locale](../../c-runtime-library/locale.md)<br/>
[MultiByteToWideChar](/windows/win32/api/stringapiset/nf-stringapiset-multibytetowidechar)<br/>
[Interpretation von Multibyte-Zeichensequenzen](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)<br/>
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[wcstombs, _wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[wctomb, _wctomb_l](wctomb-wctomb-l.md)<br/>
