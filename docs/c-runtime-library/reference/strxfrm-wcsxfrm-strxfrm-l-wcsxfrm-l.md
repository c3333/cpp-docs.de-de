---
title: strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l
ms.date: 4/2/2020
api_name:
- strxfrm
- _wcsxfrm_l
- _strxfrm_l
- wcsxfrm
- _o__strxfrm_l
- _o__wcsxfrm_l
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
- strxfrm
- _tcsxfrm
- wcsxfrm
helpviewer_keywords:
- strxfrm_l function
- _tcsxfrm function
- _strxfrm_l function
- strxfrm function
- wcsxfrm_l function
- wcsxfrm function
- string comparison [C++], transforming strings
- tcsxfrm function
- strings [C++], comparing locale
- _wcsxfrm_l function
ms.assetid: 6ba8e1f6-4484-49aa-83b8-bc2373187d9e
ms.openlocfilehash: 3ab3f978d4162f968f518272612c18767247f2fb
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82912352"
---
# <a name="strxfrm-wcsxfrm-_strxfrm_l-_wcsxfrm_l"></a>strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l

Transformieren einer Zeichenfolge auf der Grundlage von gebietsschemaspezifischen Informationen

## <a name="syntax"></a>Syntax

```C
size_t strxfrm(
   char *strDest,
   const char *strSource,
   size_t count
);
size_t wcsxfrm(
   wchar_t *strDest,
   const wchar_t *strSource,
   size_t count
);
size_t _strxfrm_l(
   char *strDest,
   const char *strSource,
   size_t count,
   _locale_t locale
);
size_t wcsxfrm_l(
   wchar_t *strDest,
   const wchar_t *strSource,
   size_t count,
   _locale_t locale
);
```

### <a name="parameters"></a>Parameter

*der schnellste*<br/>
Zielzeichenfolge.

*-Quelle*<br/>
Quellzeichenfolge.

*count*<br/>
Maximale Anzahl von Zeichen, die in " *strindest*" platziert werden sollen.

*locale*<br/>
Das zu verwendende Gebietsschema.

## <a name="return-value"></a>Rückgabewert

Gibt die Länge der transformierten Zeichenfolge ohne Berücksichtigung des beendenden Null-Zeichens zurück. Wenn der Rückgabewert größer als oder gleich *count*ist, ist der Inhalt von " *strandest* " unvorhersehbar. Bei einem Fehler legt jede Funktion **errno** fest und gibt **INT_MAX**zurück. Bei einem ungültigen Zeichen wird **errno** auf **EILSEQ**festgelegt.

## <a name="remarks"></a>Hinweise

Die **strxfrm** -Funktion transformiert die Zeichenfolge, auf die von *strSource* verwiesen wird, in ein neues sortierte Formular, das in *strDest*gespeichert wird. Nicht mehr als *Zähl* Zeichen, einschließlich des NULL-Zeichens, werden transformiert und in die resultierende Zeichenfolge eingefügt. Die Transformation erfolgt mithilfe der **LC_COLLATE** Kategorieeinstellung des Gebiets Schemas. Weitere Informationen zu **LC_COLLATE**finden Sie unter [setlocale](setlocale-wsetlocale.md). " **strauxfrm** " verwendet das aktuelle Gebiets Schema für sein vom Gebiets Schema abhängiges Verhalten. **_strxfrm_l** ist beinahe identisch, verwendet jedoch das übergebene Gebiets Schema anstelle des aktuellen Gebiets Schemas. Weitere Informationen finden Sie unter [Locale](../../c-runtime-library/locale.md).

Nach der Transformation ergibt ein Aufrufe von **strcmp** mit den beiden transformierten Zeichen folgen Ergebnisse, die mit denen eines auf die ursprünglichen beiden Zeichen folgen angewendeten **strcoll** -Aufrufs identisch sind. Wie bei **strcoll** und **stricoll**verarbeitet **strxfrm** automatisch Multibyte-Zeichen folgen.

**wcsxfrm** ist eine breit Zeichen Version von " **strauxfrm**;". die Zeichen folgen Argumente von **wcsxfrm** sind breit Zeichen Zeiger. Bei **wcsxfrm**ergibt ein **wcscmp** -Aufrufe mit den beiden transformierten Zeichen folgen Ergebnisse, die mit denen eines **wcscoll** -Aufrufes auf die ursprünglichen beiden Zeichen folgen angewendet werden. **wcsxfrm** und **strauxfrm** Verhalten sich andernfalls identisch. **wcsxfrm** verwendet das aktuelle Gebiets Schema für Ihr vom Gebiets Schema abhängiges Verhalten. **_wcsxfrm_l** verwendet das übergebene Gebiets Schema anstelle des aktuellen Gebiets Schemas.

Diese Funktionen überprüfen ihre Parameter. Wenn " *strinsource* " ein NULL-Zeiger *ist oder ein* **null** -Zeiger ist (es sei denn, count ist gleich null), oder wenn *count* größer als **INT_MAX**ist, wird der Handler für ungültige Parameter aufgerufen, wie in [Parameter Validation (Parameter](../../c-runtime-library/parameter-validation.md) Überprüfung) beschrieben. Wenn die weitere Ausführung zugelassen wird, legen diese Funktionen **errno** auf **EINVAL** fest und geben **INT_MAX**zurück.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|TCHAR.H-Routine|_UNICODE und _MBCS nicht definiert.|_MBCS definiert|_UNICODE definiert|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsxfrm**|**strxfrm**|**strxfrm**|**wcsxfrm**|
|**_tcsxfrm_l**|**_strxfrm_l**|**_strxfrm_l**|**_wcsxfrm_l**|

Im Gebietsschema „C“ ist die Reihenfolge der Zeichen im Zeichensatz (ASCII-Zeichensatz) die gleiche wie die lexikografische Reihenfolge von Zeichen. In anderen Gebietsschemata kann die Reihenfolge der Zeichen im Zeichensatz jedoch von der lexikografischen Reihenfolge der Zeichen abweichen. In bestimmten europäischen Gebietsschemata beispielsweise steht im Zeichensatz das Zeichen „a“ (Wert 0x61) vor dem Zeichen „&\#x00E4;“ (Wert 0xE4), das Zeichen „ä“ steht lexikografisch gesehen jedoch vor dem Zeichen „a“.

Verwenden Sie in Gebiets Schemas, für die sich der Zeichensatz und die lexikografische Zeichen Reihenfolge unterscheiden, **strxfrm** für die ursprünglichen Zeichen folgen und dann für die resultierenden Zeichen folgen **strcmp** , um einen lexikografischen Zeichen folgen Vergleich gemäß der **LC_COLLATE** Kategorieeinstellung des aktuellen Gebiets Schemas herzustellen Verwenden Sie daher zum Vergleichen von zwei Zeichen folgen lexikografisch im obigen Gebiets Schema **strxfrm** für die ursprünglichen Zeichen folgen und dann für die resultierenden Zeichen folgen **strcmp** . Alternativ können Sie **strcoll** anstelle von **strcmp** für die ursprünglichen Zeichen folgen verwenden.

bei " **strauxfrm** " handelt es sich im Grunde um einen Wrapper um [LCMapString](/windows/win32/api/winnls/nf-winnls-lcmapstringw) mit **LCMAP_SORTKEY**.

Der Wert des folgenden Ausdrucks ist die Größe des Arrays, das zum Speichern der **strxfrm** -Transformation der Quell Zeichenfolge erforderlich ist:

`1 + strxfrm( NULL, string, 0 )`

Nur im Gebiets Schema "C" entspricht " **strauxfrm** " folgendem:

```C
strncpy( _string1, _string2, _count );
return( strlen( _string1 ) );
```

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**strxfrm**|\<string.h>|
|**wcsxfrm**|\<string.h> oder \<wchar.h>|
|**_strxfrm_l**|\<string.h>|
|**_wcsxfrm_l**|\<string.h> oder \<wchar.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Weitere Informationen

[Datenkonvertierung](../../c-runtime-library/data-conversion.md)<br/>
[localeconv](localeconv.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
[Locale](../../c-runtime-library/locale.md)<br/>
[Zeichen folgen Bearbeitung](../../c-runtime-library/string-manipulation-crt.md)<br/>
[Funktionen von "strecoll"](../../c-runtime-library/strcoll-functions.md)<br/>
[strcmp, wcscmp, _mbscmp](strcmp-wcscmp-mbscmp.md)<br/>
[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
