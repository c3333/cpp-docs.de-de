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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 85db4e478b070823bb14028018d918e0f3cabbd7
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82920322"
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

*buffsizin bytes*<br/>
Größe des Zielpuffers.

*pkopiert*<br/>
Wird mit der Anzahl kopierter Bytes gefüllt (bei Erfolg 1 oder 2). Übergeben Sie **null** , wenn die Zahl nicht relevant ist.

*src*<br/>
Zu kopierendes Multibytezeichen.

*locale*<br/>
Zu verwendendes Gebietsschema.

## <a name="return-value"></a>Rückgabewert

Null, wenn erfolgreich, ein Fehlercode, wenn ein Fehler auftritt. Wenn *src* oder *dest* **null**ist oder wenn mehr als **buffsizin Bytes** in das *dest*-Element kopiert werden, wird der Handler für ungültige Parameter aufgerufen, wie in [Parameter Validation (Parameter](../../c-runtime-library/parameter-validation.md)Überprüfung) beschrieben. Wenn die weitere Ausführung zugelassen wird, geben die Funktionen **EINVAL** zurück, und **errno** ist auf **EINVAL**festgelegt.

## <a name="remarks"></a>Hinweise

Die **_mbccpy_s** -Funktion kopiert ein Multibytezeichen von *src* in *dest*. Wenn *src* nicht auf das führende Byte eines multibytezeichens zeigt, wie durch einen impliziten-aufzurufenden [_ismbblead](ismbblead-ismbblead-l.md)aufgerufen wird, wird das einzelne Byte *, auf das* verwiesen wird, kopiert. Wenn *src* auf ein führendes Byte zeigt, aber das folgende Byte 0 und somit ungültig ist, wird 0 nach *dest*kopiert, **errno** ist auf **EILSEQ**festgelegt, und die Funktion gibt " **EILSEQ**" zurück.

**_mbccpy_s** fügt keinen null-Terminator an; Wenn *src* jedoch auf ein NULL-Zeichen zeigt, wird dieser NULL-Wert in das *dest* -Zeichen kopiert (Dies ist nur eine reguläre Einzel Byte Kopie).

Der Wert in " *pkopiert* " wird mit der Anzahl der kopierten Bytes aufgefüllt. Mögliche Werte sind 1 und 2, wenn der Vorgang erfolgreich ist. Wenn **null** übergeben wird, wird dieser Parameter ignoriert.

|*src*|in *dest* kopiert|*pkopiert*|Rückgabewert|
|-----------|----------------------|---------------|------------------|
|kein führendes Byte|kein führendes Byte|1|0|
|0|0|1|0|
|führendes Byte gefolgt von Nicht-0|führendes Byte gefolgt von Nicht-0|2|0|
|führendes Byte gefolgt von 0|0|1|**EILSEQ**|

Beachten Sie, dass die zweite Zeile nur ein Sonderfall der ersten ist. Beachten Sie außerdem, dass in der Tabelle " *buffsizone Bytes* >= " mit "*pkopiert*"

**_mbccpy_s** verwendet das aktuelle Gebiets Schema für jedes vom Gebiets Schema abhängige Verhalten. **_mbccpy_s_l** ist mit **_mbccpy_s** identisch, mit dem Unterschied, dass **_mbccpy_s_l** das übergebene Gebiets Schema für jedes vom Gebiets Schema abhängige Verhalten verwendet.

Die Verwendung dieser Funktionen in C++ wird durch Überladungen (als Vorlagen vorhanden) vereinfacht. Überladungen können automatisch die Pufferlänge ableiten, sodass kein Größenargument angegeben werden muss. Weitere Informationen finden Sie unter [Sichere Vorlagenüberladungen](../../c-runtime-library/secure-template-overloads.md).

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

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

## <a name="see-also"></a>Weitere Informationen

[Locale](../../c-runtime-library/locale.md)<br/>
[Interpretation von Multibyte-Zeichensequenzen](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)<br/>
