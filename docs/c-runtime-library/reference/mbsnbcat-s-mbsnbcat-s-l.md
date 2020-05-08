---
title: _mbsnbcat_s, _mbsnbcat_s_l
ms.date: 4/2/2020
api_name:
- _mbsnbcat_s_l
- _mbsnbcat_s
- _o__mbsnbcat_s
- _o__mbsnbcat_s_l
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
- _mbsnbcat_s
- mbsnbcat_s
- _mbsnbcat_s_l
- mbsnbcat_s_l
helpviewer_keywords:
- _tcsncat function
- mbsnbcat_s function
- _mbsnbcat_s function
- _mbsnbcat_s_l function
- _tcsncat_s_l function
- tcsncat_s_l function
- mbsnbcat_s_l function
- tcsncat function
ms.assetid: 2c9e9be7-d979-4a54-8ada-23428b6648a9
ms.openlocfilehash: d731c94c879d0e4334dc3b57a19b94cc0378abaf
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82915633"
---
# <a name="_mbsnbcat_s-_mbsnbcat_s_l"></a>_mbsnbcat_s, _mbsnbcat_s_l

Fügt an eine Multibytezeichenfolge an, höchstens die ersten **n** Bytes einer anderen Multibytezeichen-Zeichenfolge. Dies sind Versionen von [_mbsnbcat, _mbsnbcat_l](mbsnbcat-mbsnbcat-l.md), enthalten aber Sicherheitserweiterungen wie unter [Sicherheitsfunktionen im CRT](../../c-runtime-library/security-features-in-the-crt.md) beschrieben.

> [!IMPORTANT]
> Diese API kann nicht in Anwendungen verwendet werden, die in Windows-Runtime ausgeführt werden. Weitere Informationen finden Sie im Artikel [CRT functions not supported in Universal Windows Platform apps (In Apps für die universelle Windows-Plattform nicht unterstützte CRT-Funktionen)](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntax

```C
errno_t _mbsnbcat_s(
   unsigned char *dest,
   size_t sizeInBytes,
   const unsigned char *src,
   size_t count
);
errno_t _mbsnbcat_s_l(
   unsigned char *dest,
   size_t sizeInBytes,
   const unsigned char *src,
   size_t count,
   _locale_t locale
);
template <size_t size>
errno_t _mbsnbcat_s(
   unsigned char (&dest)[size],
   const unsigned char *src,
   size_t count
); // C++ only
template <size_t size>
errno_t _mbsnbcat_s_l(
   unsigned char (&dest)[size],
   const unsigned char *src,
   size_t count,
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>Parameter

*dest*<br/>
Auf NULL endende Multibytezielzeichenfolge.

*sizeInBytes*<br/>
Größe des *dest* -Puffers in Bytes.

*src*<br/>
Auf NULL endende Multibytequellzeichenfolge.

*count*<br/>
Anzahl von Bytes von *src* zum Anfügen an *dest*.

*locale*<br/>
Zu verwendendes Gebietsschema.

## <a name="return-value"></a>Rückgabewert

Null, wenn erfolgreich, andernfalls ein Fehlercode.

### <a name="error-conditions"></a>Fehlerbedingungen

|**Dest**|*sizeInBytes*|*src*|Rückgabewert|
|------------|-------------------|-----------|------------------|
|**Normal**|any|any|**Eingabe**|
|Any|<= 0|any|**Eingabe**|
|Any|any|**Normal**|**Eingabe**|

Wenn eine dieser Fehlerbedingungen auftritt, generiert die Funktion einen Fehler über ungültige Parameter, wie dies unter [Parametervalidierung](../../c-runtime-library/parameter-validation.md) beschrieben wird. Wenn der Fehler behandelt wird, gibt die Funktion " **EINVAL** " zurück und legt " **errno** " auf " **EINVAL**" fest.

## <a name="remarks"></a>Hinweise

Die **_mbsnbcat_s** -Funktion fügt höchstens *die ersten Bytes* von *src*an *dest*an. Wenn das Byte, das dem NULL-Zeichen in *dest* unmittelbar vorangestellt ist, ein führendes Byte ist, wird es durch das ursprüngliche Byte von *src*überschrieben. Andernfalls überschreibt das ursprüngliche Byte von *src* das abschließende Null-Zeichen von *dest*. Wenn ein NULL-Byte in *src* angezeigt wird, bevor *count* -Bytes angefügt werden, fügt **_mbsnbcat_s** alle Bytes von *src*bis zum NULL-Zeichen an. Wenn *count* größer als die Länge von *src*ist, wird die Länge von *src* anstelle der *Anzahl*verwendet. Die resultierende Zeichenfolge wird durch ein NULL-Zeichen beendet. Wenn der Kopiervorgang zwischen Zeichenfolgen ausgeführt wird, die sich überschneiden, ist das Verhalten nicht definiert.

Der Ausgabewert wird von der Einstellung der **LC_CTYPE** Kategorieeinstellung des Gebiets Schemas beeinflusst. Weitere Informationen finden Sie [unter setlocale, _wsetlocale](setlocale-wsetlocale.md) . Die Versionen dieser Funktionen sind identisch, mit der Ausnahme, dass diejenigen, die nicht über das **_l** -Suffix verfügen, das aktuelle Gebiets Schema verwenden, und diejenigen, die das **_l** Suffix haben, stattdessen den übergebenen Gebiets Schema Parameter verwenden. Weitere Informationen finden Sie unter [Locale](../../c-runtime-library/locale.md).

In C++ wird die Verwendung dieser Funktionen durch Vorlagenüberladungen vereinfacht. Die Überladungen können automatisch Rückschlüsse über die Pufferlänge ziehen, wodurch kein „size“-Argument angegeben werden muss. Zudem können sie automatisch ihre neueren und sichereren Funktionen zum Ersetzen von älteren, unsichereren Funktionen verwenden. Weitere Informationen finden Sie unter [Sichere Vorlagenüberladungen](../../c-runtime-library/secure-template-overloads.md).

Die Debug-Bibliotheksversionen dieser Funktionen füllen zunächst den Puffer mit "0xFE" auf. Um dieses Verhalten zu deaktivieren, verwenden Sie [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|Tchar.h-Routine|_UNICODE und _MBCS nicht definiert|_MBCS definiert|_UNICODE definiert|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcsncat**|[strncat](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)|**_mbsnbcat_s**|[wcsncat](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)|
|**_tcsncat_s_l**|**_strncat_s_l**|**_mbsnbcat_s_l**|**_wcsncat_s_l**|

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**_mbsnbcat_s**|\<mbstring.h>|
|**_mbsnbcat_s_l**|\<mbstring.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Weitere Informationen

[Zeichen folgen Bearbeitung](../../c-runtime-library/string-manipulation-crt.md)<br/>
[_mbsnbcmp, _mbsnbcmp_l](mbsnbcmp-mbsnbcmp-l.md)<br/>
[_strncnt, _wcsncnt, _mbsnbcnt, _mbsnbcnt_l, _mbsnccnt, _mbsnccnt_l](strncnt-wcsncnt-mbsnbcnt-mbsnbcnt-l-mbsnccnt-mbsnccnt-l.md)<br/>
[_mbsnbcpy, _mbsnbcpy_l](mbsnbcpy-mbsnbcpy-l.md)<br/>
[_mbsnbcpy_s, _mbsnbcpy_s_l](mbsnbcpy-s-mbsnbcpy-s-l.md)<br/>
[_mbsnbset, _mbsnbset_l](mbsnbset-mbsnbset-l.md)<br/>
[strncat, _strncat_l, wcsncat, _wcsncat_l, _mbsncat, _mbsncat_l](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)<br/>
[strncat_s, _strncat_s_l, wcsncat_s, _wcsncat_s_l, _mbsncat_s, _mbsncat_s_l](strncat-s-strncat-s-l-wcsncat-s-wcsncat-s-l-mbsncat-s-mbsncat-s-l.md)<br/>
