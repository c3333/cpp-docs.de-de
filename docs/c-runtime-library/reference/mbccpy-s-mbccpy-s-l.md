---
title: _mbccpy_s, _mbccpy_s_l
ms.date: 4/2/2020
api_name:
- _mbccpy_s
- _mbccpy_s_l
- _o__mbccpy_s
- _o__mbccpy_s_l
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _mbccpy_s_l
- mbccpy_s_l
- mbccpy_s
- _mbccpy_s
helpviewer_keywords:
- tccpy_s_l function
- _tccpy_s function
- _mbccpy_s function
- mbccpy_s function
- tccpy_s function
- mbccpy_s_l function
- _tccpy_s_l function
- _mbccpy_s_l function
ms.assetid: b6e965fa-53c1-4ec3-85ef-a1c4b4f2b2da
ms.openlocfilehash: 08df395c6978c84b3f53ed0b07ce988afd0249f6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81341232"
---
# <a name="_mbccpy_s-_mbccpy_s_l"></a>_mbccpy_s, _mbccpy_s_l

Kopiert ein Multibytezeichen von einer Zeichenfolge in eine andere Zeichenfolge. Diese Versionen von [_mbccpy, _mbccpy_l](mbccpy-mbccpy-l.md) enthalten Sicherheitserweiterungen, wie unter [Sicherheitserweiterungen in der CRT](../../c-runtime-library/security-features-in-the-crt.md) beschrieben.

> [!IMPORTANT]
> Diese API kann nicht in Anwendungen verwendet werden, die in Windows-Runtime ausgeführt werden. Weitere Informationen finden Sie im Artikel [CRT functions not supported in Universal Windows Platform apps (In Apps für die universelle Windows-Plattform nicht unterstützte CRT-Funktionen)](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntax

```C
errno_t _mbccpy_s(
   unsigned char *dest,
   size_t buffSizeInBytes,
   int * pCopied,
   const unsigned char *src
);
errno_t _mbccpy_s_l(
   unsigned char *dest,
   size_t buffSizeInBytes,
   int * pCopied,
   const unsigned char *src,
   locale_t locale
);
template <size_t size>
errno_t _mbccpy_s(
   unsigned char (&dest)[size],
   int * pCopied,
   const unsigned char *src
); // C++ only
template <size_t size>
errno_t _mbccpy_s_l(
   unsigned char (&dest)[size],
   int * pCopied,
   const unsigned char *src,
   locale_t locale
); // C++ only
```

### <a name="parameters"></a>Parameter

*dest*<br/>
Kopierziel.

*buffSizeInBytes*<br/>
Größe des Zielpuffers.

*pCopied*<br/>
Wird mit der Anzahl kopierter Bytes gefüllt (bei Erfolg 1 oder 2). Übergeben Sie **NULL,** wenn Sie sich nicht um die Zahl kümmern.

*src*<br/>
Zu kopierendes Multibytezeichen.

*locale*<br/>
Zu verwendendes Gebietsschema.

## <a name="return-value"></a>Rückgabewert

Null, wenn erfolgreich, ein Fehlercode, wenn ein Fehler auftritt. Wenn *src* oder *dest* **NULL**ist oder wenn mehr als **buffSizeinBytes** Bytes in *dest*kopiert werden, wird der ungültige Parameterhandler aufgerufen, wie unter [Parametervalidierung](../../c-runtime-library/parameter-validation.md)beschrieben. Wenn die Ausführung fortgesetzt werden darf, geben die Funktionen **EINVAL** zurück und **errno** wird auf **EINVAL**gesetzt.

## <a name="remarks"></a>Bemerkungen

Die **_mbccpy_s-Funktion** kopiert ein Multibyte-Zeichen von *src* nach *dest*. Wenn *src* nicht auf das Leadbyte eines Multibyte-Zeichens zeigt, wie durch einen impliziten Aufruf von [_ismbblead](ismbblead-ismbblead-l.md)bestimmt, wird das einzelne Byte kopiert, auf das *src* verweist. Wenn *src* auf ein Leadbyte verweist, aber das folgende Byte 0 und damit ungültig ist, wird 0 in *dest*kopiert, **errno** wird auf **EILSEQ**gesetzt, und die Funktion gibt **EILSEQ**zurück.

**_mbccpy_s** fügt keinen Null-Terminator an. Wenn *src* jedoch auf ein Nullzeichen verweist, wird dieser NULL-Wert in *dest* kopiert (dies ist nur eine normale Single-Byte-Kopie).

Der Wert in *pCopied* wird mit der Anzahl der kopierten Bytes gefüllt. Mögliche Werte sind 1 und 2, wenn der Vorgang erfolgreich ist. Wenn **NULL** übergeben wird, wird dieser Parameter ignoriert.

|*src*|kopiert in *dest*|*pCopied*|Rückgabewert|
|-----------|----------------------|---------------|------------------|
|kein führendes Byte|kein führendes Byte|1|0|
|0|0|1|0|
|führendes Byte gefolgt von Nicht-0|führendes Byte gefolgt von Nicht-0|2|0|
|führendes Byte gefolgt von 0|0|1|**EILSEQ**|

Beachten Sie, dass die zweite Zeile nur ein Sonderfall der ersten ist. Beachten Sie auch, dass die Tabelle von *buffSizeInBytes* >= *pCopied*ausgeht.

**_mbccpy_s** verwendet das aktuelle Gebietsschema für jedes gebietsschemaabhängige Verhalten. **_mbccpy_s_l** ist identisch mit **_mbccpy_s** mit der Ausnahme, dass **_mbccpy_s_l** das Gebietsschema verwendet, das für ein gebietsschemaabhängiges Verhalten übergeben wird.

Die Verwendung dieser Funktionen in C++ wird durch Überladungen (als Vorlagen vorhanden) vereinfacht. Überladungen können automatisch die Pufferlänge ableiten, sodass kein Größenargument angegeben werden muss. Weitere Informationen finden Sie unter [Sichere Vorlagenüberladungen](../../c-runtime-library/secure-template-overloads.md).

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|Tchar.h-Routine|_UNICODE und _MBCS nicht definiert|_MBCS definiert|_UNICODE definiert|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tccpy_s**|Führt eine Zuordnung zum Makro oder zur Inlinefunktion aus.|**_mbccpy_s**|Führt eine Zuordnung zum Makro oder zur Inlinefunktion aus.|

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**_mbccpy_s**|\<mbstring.h>|
|**_mbccpy_s_l**|\<mbstring.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Siehe auch

[Locale](../../c-runtime-library/locale.md)<br/>
[Interpretation von Multibyte-Zeichensequenzen](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)<br/>
