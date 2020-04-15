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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: aabe7e7c2e44f558b936e0fd4c6fa4a85dc582f5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81362972"
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

*Strdest*<br/>
Zielzeichenfolge.

*Strsource*<br/>
Quellzeichenfolge.

*count*<br/>
Maximale Anzahl von Zeichen, die in *strDest*platziert werden sollen.

*locale*<br/>
Das zu verwendende Gebietsschema.

## <a name="return-value"></a>Rückgabewert

Gibt die Länge der transformierten Zeichenfolge ohne Berücksichtigung des beendenden Null-Zeichens zurück. Wenn der Rückgabewert größer oder gleich der *Anzahl*ist, ist der Inhalt von *strDest* unvorhersehbar. Bei einem Fehler legt jede Funktion **errno** fest und gibt **INT_MAX**zurück. Für ein ungültiges Zeichen wird **errno** auf **EILSEQ**festgelegt.

## <a name="remarks"></a>Bemerkungen

Die **strxfrm-Funktion** transformiert die Zeichenfolge, auf die *strSource* zeigt, in eine neue gesammelte Form, die in *strDest*gespeichert wird. Es werden nicht mehr als *Zählzeichen,* einschließlich des Nullzeichens, transformiert und in die resultierende Zeichenfolge eingefügt. Die Transformation erfolgt mithilfe der **LC_COLLATE** Kategorieeinstellung des Gebietsschemas. Weitere Informationen **zu LC_COLLATE**finden Sie unter [setlocale](setlocale-wsetlocale.md). **strxfrm** verwendet das aktuelle Gebietsschema für sein gebietsschemaabhängiges Verhalten. **_strxfrm_l** identisch ist, außer dass es das übergebene Gebietsschema anstelle des aktuellen Gebietsschemas verwendet. Weitere Informationen finden Sie unter [Locale](../../c-runtime-library/locale.md).

Nach der Transformation ergibt ein Aufruf von **strcmp** mit den beiden transformierten Zeichenfolgen Ergebnisse, die mit denen eines Aufrufs von **strcoll** identisch sind, der auf die ursprünglichen beiden Zeichenfolgen angewendet wird. Wie bei **strcoll** und **stricoll**verarbeitet **strxfrm** automatisch Multibyte-Zeichen-Zeichenfolgen.

**wcsxfrm** ist eine Breitzeichenversion von **strxfrm**; Die Zeichenfolgenargumente von **wcsxfrm** sind Breitzeichenzeiger. Bei **wcsxfrm**ergibt ein Aufruf von **wcscmp** mit den beiden transformierten Zeichenfolgen nach der Zeichenfolgentransformation Ergebnisse, die mit denen eines Aufrufs von **wcscoll** identisch sind, der auf die ursprünglichen beiden Zeichenfolgen angewendet wird. **wcsxfrm** und **strxfrm** verhalten sich ansonsten identisch. **wcsxfrm** verwendet das aktuelle Gebietsschema für sein gebietsschemaabhängiges Verhalten. **_wcsxfrm_l** verwendet das übergebene Gebietsschema anstelle des aktuellen Gebietsschemas.

Diese Funktionen überprüfen ihre Parameter. Wenn *strSource* ein Nullzeiger oder *strDest* ein **NULL-Zeiger** ist (es sei denn, Die *Anzahl* ist Null), oder wenn die Anzahl größer als **INT_MAX**ist, wird der ungültige Parameterhandler aufgerufen, wie in [Parametervalidierung](../../c-runtime-library/parameter-validation.md) beschrieben. Wenn die Ausführung fortgesetzt werden darf, legen diese Funktionen **errno** auf **EINVAL** fest und geben **INT_MAX**zurück.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|TCHAR.H-Routine|_UNICODE und _MBCS nicht definiert.|_MBCS definiert|_UNICODE definiert|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsxfrm**|**strxfrm**|**strxfrm**|**wcsxfrm**|
|**_tcsxfrm_l**|**_strxfrm_l**|**_strxfrm_l**|**_wcsxfrm_l**|

Im Gebietsschema „C“ ist die Reihenfolge der Zeichen im Zeichensatz (ASCII-Zeichensatz) die gleiche wie die lexikografische Reihenfolge von Zeichen. In anderen Gebietsschemata kann die Reihenfolge der Zeichen im Zeichensatz jedoch von der lexikografischen Reihenfolge der Zeichen abweichen. In bestimmten europäischen Gebietsschemata beispielsweise steht im Zeichensatz das Zeichen „a“ (Wert 0x61) vor dem Zeichen „&\#x00E4;“ (Wert 0xE4), das Zeichen „ä“ steht lexikografisch gesehen jedoch vor dem Zeichen „a“.

Verwenden Sie in Gebietsschemas, für die sich der Zeichensatz und die lexikographische Zeichenreihenfolge unterscheiden, **strxfrm** für die ursprünglichen Zeichenfolgen und dann **strcmp** für die resultierenden Zeichenfolgen, um einen lexikographischen Zeichenfolgenvergleich gemäß der **LC_COLLATE-Kategorieeinstellung** des aktuellen Gebietsschemas zu erstellen. Um also zwei Saiten lexikographisch im obigen Gebietsschema zu vergleichen, verwenden Sie **strxfrm** auf den ursprünglichen Zeichenfolgen und dann **strcmp** auf den resultierenden Zeichenfolgen. Alternativ können Sie **Strcoll** anstelle **von strcmp** für die ursprünglichen Zeichenfolgen verwenden.

**strxfrm** ist im Grunde ein Wrapper um [LCMapString](/windows/win32/api/winnls/nf-winnls-lcmapstringw) mit **LCMAP_SORTKEY**.

Der Wert des folgenden Ausdrucks ist die Größe des Arrays, das für die **strxfrm-Transformation** der Quellzeichenfolge erforderlich ist:

`1 + strxfrm( NULL, string, 0 )`

Nur im Gebietsschema "C" entspricht **strxfrm** den folgenden:

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

## <a name="see-also"></a>Siehe auch

[Datenkonvertierung](../../c-runtime-library/data-conversion.md)<br/>
[localeconv](localeconv.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
[Locale](../../c-runtime-library/locale.md)<br/>
[String-Manipulation](../../c-runtime-library/string-manipulation-crt.md)<br/>
[strcoll-Funktionen](../../c-runtime-library/strcoll-functions.md)<br/>
[strcmp, wcscmp, _mbscmp](strcmp-wcscmp-mbscmp.md)<br/>
[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
