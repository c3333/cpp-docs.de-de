---
title: strtoull, _strtoull_l, wcstoull, _wcstoull_l
ms.date: 4/2/2020
api_name:
- _strtoull_l
- _wcstoull_l
- strtoull
- wcstoull
- _o__strtoull_l
- _o__wcstoull_l
- _o_strtoull
- _o_wcstoull
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
- _wcstoull_l
- _tcstoull
- _tcstoull_l
- wcstoull
- _strtoull_l
- strtoull
helpviewer_keywords:
- strtoull function
- _tcstoull_l function
- _tcstoull function
- _wcstoull_l function
- _strtoull_l function
- wcstoull function
ms.assetid: 36dac1cc-e901-40a0-8802-63562d6d01df
ms.openlocfilehash: 5a27218b9d83314f995df30fbe21d97031d371af
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81354054"
---
# <a name="strtoull-_strtoull_l-wcstoull-_wcstoull_l"></a>strtoull, _strtoull_l, wcstoull, _wcstoull_l

Konvertiert eine Zeichenfolge in einen langenganzzahligen Wert ohne Vorzeichen.

## <a name="syntax"></a>Syntax

```C
unsigned long long strtoull(
   const char *strSource,
   char **endptr,
   int base
);
unsigned long long _strtoull_l(
   const char *strSource,
   char **endptr,
   int base,
   _locale_t locale
);
unsigned long long wcstoull(
   const wchar_t *strSource,
   wchar_t **endptr,
   int base
);
unsigned long long _wcstoull_l(
   const wchar_t *strSource,
   wchar_t **endptr,
   int base,
   _locale_t locale
);
```

### <a name="parameters"></a>Parameter

*Strsource*<br/>
Zu konvertierende mit NULL endende Zeichenfolge.

*endptr*<br/>
Zeiger auf das Zeichen, das die Überprüfung stoppt.

*base*<br/>
Zu verwendende Zahlenbasis.

*locale*<br/>
Zu verwendendes Gebietsschema.

## <a name="return-value"></a>Rückgabewert

**strtoull** gibt den konvertierten Wert zurück, falls vorhanden, oder **ULLONG_MAX** bei Überlauf. **strtoull** gibt 0 zurück, wenn keine Konvertierung durchgeführt werden kann. **wcstoull** gibt Werte analog an **strtoull**zurück. Für beide Funktionen wird **errno** auf **ERANGE** gesetzt, wenn ein Über- oder Unterlauf auftritt.

Weitere Informationen zu Rückgabecodes finden Sie unter [errno, _doserrno, _sys_errlist und _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Bemerkungen

Jede dieser Funktionen konvertiert die Eingabezeichenfolge *strSource* in einen **nicht signierten** **Long-Long-Ganzzahlwert.** **long**

**strtoull** hört auf, die Zeichenfolge *strSource* beim ersten Zeichen zu lesen, das es nicht als Teil einer Zahl erkennen kann. Dies kann das beendende Nullzeichen sein, oder es kann das erste numerische Zeichen sein, das größer oder gleich *basis*ist. Die Einstellung der **LC_NUMERIC** Kategorie des Gebietsschemas bestimmt die Erkennung des Radixzeichens in *strSource*; Weitere Informationen finden Sie unter [setlocale, _wsetlocale](setlocale-wsetlocale.md). **strtoull** und **wcstoull** verwenden das aktuelle Gebietsschema; **_strtoull_l** und **_wcstoull_l** stattdessen das Gebietsschema verwenden, das übergeben wurde, aber ansonsten identisch sind. Weitere Informationen finden Sie unter [Locale](../../c-runtime-library/locale.md).

Wenn *endptr* nicht **NULL**ist, wird ein Zeiger auf das Zeichen, das den Scan beendet hat, an der Position gespeichert, auf die *endptr*zeigt. Wenn keine Konvertierung durchgeführt werden kann (es wurden keine gültigen Ziffern gefunden oder eine ungültige Basis angegeben), wird der Wert von *strSource* an der Position gespeichert, auf die von *endptr*verwiesen wird.

**wcstoull** ist eine Breitzeichenversion von **strtoull** und das Argument *strSource* ist eine Zeichenfolge mit großen Zeichen. Ansonsten verhalten sich diese Funktionen identisch.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|TCHAR.H-Routine|_UNICODE und _MBCS nicht definiert.|_MBCS definiert|_UNICODE definiert|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstoull**|**strtoull**|**strtoull**|**wcstoull**|
|**_tcstoull_l**|**strtoull_l**|**_strtoull_l**|**_wcstoull_l**|

**strtoull** erwartet, dass *strSource* auf eine Zeichenfolge der folgenden Form hinweist:

> [*Leerzeichen*] [a**+** **-**&#124; ' [**0** [- **x** &#124; **X** ' ]] [*Ziffern* &#124; *Buchstaben*]

Ein *Leerzeichen* kann aus Leerzeichen und Registerkartenzeichen bestehen, die ignoriert werden. *Ziffern* sind eine oder mehrere Dezimalstellen. *Buchstaben* sind einer oder mehrere der Buchstaben "a" bis "z" (oder "A" bis "Z"). Das erste Zeichen, das dieser Form nicht entspricht, beendet die Überprüfung. Wenn *die Basis* zwischen 2 und 36 liegt, wird sie als Basis der Zahl verwendet. Wenn *Base* 0 ist, werden die Anfangszeichen der Zeichenfolge, auf die von *strSource* verwiesen wird, verwendet, um die Basis zu bestimmen. Wenn das erste Zeichen "0 " und das zweite Zeichen nicht "x" oder "X" ist, wird die Zeichenfolge als oktale ganze Zahl interpretiert. Wenn das erste Zeichen "0" und das zweite Zeichen nicht "x" oder "X" ist, wird die Zeichenfolge als hexadezimale ganze Zahl interpretiert. Wenn das erste Zeichen "1" bis "9 " ist, wird die Zeichenfolge als ganze Dezimalzahl interpretiert. Den Buchstaben „a“ bis „z“ (bzw. „A“ bis „Z“) werden die Werten 10 bis 35 zugewiesen. Es sind nur Buchstaben zulässig, deren zugewiesene Werte kleiner als *base* sind. Das erste Zeichen außerhalb des Bereichs der Basis beendet die Überprüfung. Wenn z. *B. Basis* 0 ist und das erste gescannte Zeichen '0' ist, wird eine oktale Ganzzahl angenommen und ein Zeichen '8' oder '9' stoppt den Scan. **strtoull** erlaubt ein**+** Pluszeichen (**-**) oder Minuszeichen ( ) Präfix; Ein führendes Minuszeichen gibt an, dass der Rückgabewert negiert wird.

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**strtoull**|\<stdlib.h>|
|**wcstoull**|\<stdlib.h> oder \<wchar.h>|
|**_strtoull_l**|\<stdlib.h>|
|**_wcstoull_l**|\<stdlib.h> oder \<wchar.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

Ein Beispiel hierfür finden Sie unter [strtod](strtod-strtod-l-wcstod-wcstod-l.md).

## <a name="see-also"></a>Siehe auch

[Datenkonvertierung](../../c-runtime-library/data-conversion.md)<br/>
[Locale](../../c-runtime-library/locale.md)<br/>
[localeconv](localeconv.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
[Funktionen zur Konvertierung von Zeichenfolgen in numerische Werte](../../c-runtime-library/string-to-numeric-value-functions.md)<br/>
[strtod, _strtod_l, wcstod, _wcstod_l](strtod-strtod-l-wcstod-wcstod-l.md)<br/>
[strtol, wcstol, _strtol_l, _wcstol_l](strtol-wcstol-strtol-l-wcstol-l.md)<br/>
[strtoul, _strtoul_l, wcstoul, _wcstoul_l](strtoul-strtoul-l-wcstoul-wcstoul-l.md)<br/>
[strtoll, _strtoll_l, wcstoll, _wcstoll_l](strtoll-strtoll-l-wcstoll-wcstoll-l.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
