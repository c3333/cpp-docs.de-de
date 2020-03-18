---
title: _mbsnbcpy, _mbsnbcpy_l
ms.date: 11/04/2016
api_name:
- _mbsnbcpy
- _mbsnbcpy_l
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- mbsnbcpy
- _mbsnbcpy
- mbsnbcpy_l
- _mbsnbcpy_l
helpviewer_keywords:
- mbsnbcpy function
- _mbsnbcpy_l function
- _mbsnbcpy function
- _tcsncpy function
- tcsncpy_l function
- _tcsncpy_l function
- mbsnbcpy_l function
- tcsncpy function
ms.assetid: 83d17b50-3cbf-4df9-bce8-3b6d52f85d04
ms.openlocfilehash: 9a52f8abb220c840f1b7f71d029efacd4c5206fb
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79442859"
---
# <a name="_mbsnbcpy-_mbsnbcpy_l"></a>_mbsnbcpy, _mbsnbcpy_l

Kopiert **n** Bytes einer Zeichenfolge in eine Ziel Zeichenfolge. Sicherere Versionen dieser Funktionen sind verfügbar. Informationen dazu finden Sie unter [_mbsnbcpy_s, _mbsnbcpy_s_l](mbsnbcpy-s-mbsnbcpy-s-l.md).

> [!IMPORTANT]
> Diese API kann nicht in Anwendungen verwendet werden, die in Windows-Runtime ausgeführt werden. Weitere Informationen finden Sie im Artikel [CRT functions not supported in Universal Windows Platform apps (In Apps für die universelle Windows-Plattform nicht unterstützte CRT-Funktionen)](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntax

```C
unsigned char * _mbsnbcpy(
   unsigned char * strDest,
   const unsigned char * strSource,
   size_t count
);
unsigned char * _mbsnbcpy_l(
   unsigned char * strDest,
   const unsigned char * strSource,
   size_t count,
   _locale_t locale
);
template <size_t size>
unsigned char * _mbsnbcpy(
   unsigned char (&strDest)[size],
   const unsigned char * strSource,
   size_t count
); // C++ only
template <size_t size>
unsigned char * _mbsnbcpy_l(
   unsigned char (&strDest)[size],
   const unsigned char * strSource,
   size_t count,
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>Parameter

*der schnellste*<br/>
Ziel für die zu kopierende Zeichenfolge.

*-Quelle*<br/>
Zu kopierende Zeichenfolge.

*count*<br/>
Anzahl der zu kopierenden Bytes.

*locale*<br/>
Zu verwendendes Gebietsschema.

## <a name="return-value"></a>Rückgabewert

**_mbsnbcpy** gibt einen Zeiger auf die Ziel Zeichenfolge zurück. Kein Rückgabewert ist zur Fehleranzeige reserviert.

## <a name="remarks"></a>Bemerkungen

Die **_mbsnbcpy** -Funktion kopiert die *Anzahl* von Bytes aus " *strausource* " in " *strandest*" Wenn die *Anzahl* die Größe der *strDest* überschreitet oder sich die Quell-und Ziel Zeichenfolgen überlappen, ist das Verhalten von **_mbsnbcpy** nicht definiert.

Wenn *strSource* oder *strDest* ein NULL-Zeiger ist, ruft diese Funktion den Handler für ungültige Parameter auf, wie in [Parameter Validation (Parameter](../../c-runtime-library/parameter-validation.md)Überprüfung) beschrieben. Wenn die weitere Ausführung zugelassen wird, gibt die Funktion **null** zurück und legt **errno** auf **EINVAL**fest.

Der Ausgabewert wird von der Einstellung der **LC_CTYPE** Kategorieeinstellung des Gebiets Schemas beeinflusst. Weitere Informationen finden Sie [unter setlocale, _wsetlocale](setlocale-wsetlocale.md) . Die Versionen dieser Funktionen sind identisch, außer dass diejenigen, die nicht über das **_l** -Suffix verfügen, das aktuelle Gebiets Schema verwenden, und die Versionen mit dem **_l** Suffix verwenden stattdessen den übergebenen Gebiets Schema Parameter. Weitere Informationen finden Sie unter [Gebietsschema](../../c-runtime-library/locale.md).

> [!IMPORTANT]
> Diese Funktionen sind möglicherweise für Pufferüberlaufrisiken anfällig. Pufferüberläufe können zum Ausführen von beliebigem Angreifercode verwendet werden, der zu einer unbefugten Ausweitung der Berechtigungen führen und das System gefährden kann. Weitere Informationen finden Sie unter [Vermeiden von Pufferüberläufen](/windows/win32/SecBP/avoiding-buffer-overruns).

In C++ haben diese Funktionen Vorlagenüberladungen, mit denen die neueren, sicheren Entsprechungen dieser Funktionen aufgerufen werden. Weitere Informationen finden Sie unter [Sichere Vorlagenüberladung](../../c-runtime-library/secure-template-overloads.md).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|Tchar.h-Routine|_UNICODE und _MBCS nicht definiert|_MBCS definiert|_UNICODE definiert|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcsncpy**|[strncpy](strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)|**_mbsnbcpy**|[wcsncpy](strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)|
|**_tcsncpy_l**|**_strncpy_l**|**_mbsnbcp_l**|**_wcsncpy_l**|

## <a name="requirements"></a>Requirements (Anforderungen)

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**_mbsnbcpy**|\<mbstring.h>|
|**_mbsnbcpy_l**|\<mbstring.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Kompatibilität](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Weitere Informationen

[Zeichenfolgenbearbeitung](../../c-runtime-library/string-manipulation-crt.md)<br/>
[_mbsnbcat, _mbsnbcat_l](mbsnbcat-mbsnbcat-l.md)<br/>
[_mbsnbcmp, _mbsnbcmp_l](mbsnbcmp-mbsnbcmp-l.md)<br/>
[_strncnt, _wcsncnt, _mbsnbcnt, _mbsnbcnt_l, _mbsnccnt, _mbsnccnt_l](strncnt-wcsncnt-mbsnbcnt-mbsnbcnt-l-mbsnccnt-mbsnccnt-l.md)<br/>
[_mbsnbset, _mbsnbset_l](mbsnbset-mbsnbset-l.md)<br/>
[strncpy, _strncpy_l, wcsncpy, _wcsncpy_l, _mbsncpy, _mbsncpy_l](strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)<br/>
