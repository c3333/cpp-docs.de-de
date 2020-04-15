---
title: strtoul, _strtoul_l, wcstoul, _wcstoul_l
ms.date: 4/2/2020
api_name:
- _wcstoul_l
- _strtoul_l
- strtoul
- wcstoul
- _o__strtoul_l
- _o__wcstoul_l
- _o_strtoul
- _o_wcstoul
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
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- strtoul
- _tcstoul
- wcstoul
helpviewer_keywords:
- _wcstoul_l function
- _tcstoul function
- _strtoul_l function
- string conversion, to integers
- wcstoul function
- strtoul function
- wcstoul_l function
- strtoul_l function
- tcstoul function
ms.assetid: 38f2afe8-8178-4e0b-8bbe-d5c6ad66e3ab
ms.openlocfilehash: 60ae432fb11c5a29da2c4830c2a85305c6eaa46c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365627"
---
# <a name="strtoul-_strtoul_l-wcstoul-_wcstoul_l"></a>strtoul, _strtoul_l, wcstoul, _wcstoul_l

Konvertiert eine Zeichenfolge in einen langen ganzzahligen Wert ohne Vorzeichen.

## <a name="syntax"></a>Syntax

```C
unsigned long strtoul(
   const char *strSource,
   char **endptr,
   int base
);
unsigned long _strtoul_l(
   const char *strSource,
   char **endptr,
   int base,
   _locale_t locale
);
unsigned long wcstoul(
   const wchar_t *strSource,
   wchar_t **endptr,
   int base
);
unsigned long _wcstoul_l(
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
Zeiger auf ein Zeichen, mit dem die Überprüfung beendet wird.

*base*<br/>
Zu verwendende Zahlenbasis.

*locale*<br/>
Zu verwendendes Gebietsschema.

## <a name="return-value"></a>Rückgabewert

**strtoul** gibt den konvertierten Wert zurück, falls vorhanden, oder **ULONG_MAX** bei Überlauf. **strtoul** gibt 0 zurück, wenn keine Konvertierung durchgeführt werden kann. **wcstoul** gibt Werte analog an **strtoul**zurück. Für beide Funktionen wird **errno** auf **ERANGE** gesetzt, wenn ein Über- oder Unterlauf auftritt.

Weitere Informationen zu diesem und anderen Rückgabecodes finden Sie unter [_doserrno, errno, _sys_errlist und _sys_nerr.](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)

## <a name="remarks"></a>Bemerkungen

Jede dieser Funktionen konvertiert die Eingabezeichenfolge *strSource* in eine **nicht signierte** **long**.

**strtoul** stoppt das Lesen der Zeichenfolge *strSource* beim ersten Zeichen, das es als Teil einer Zahl nicht erkennen kann. Dies kann das beendende Nullzeichen sein, oder es kann das erste numerische Zeichen größer oder gleich *Basis*sein. Die **LC_NUMERIC** Kategorieeinstellung des Gebietsschemas bestimmt die Erkennung des Radixzeichens in *strSource*; Weitere Informationen finden Sie unter [setlocale](setlocale-wsetlocale.md). **strtoul** und **wcstoul** verwenden das aktuelle Gebietsschema; **_strtoul_l** und **_wcstoul_l** identisch sind, außer dass sie stattdessen das übergebene Gebietsschema verwenden. Weitere Informationen finden Sie unter [Locale](../../c-runtime-library/locale.md).

Wenn *endptr* nicht **NULL**ist, wird ein Zeiger auf das Zeichen, das den Scan beendet hat, an der Position gespeichert, auf die *endptr*zeigt. Wenn keine Konvertierung durchgeführt werden kann (es wurden keine gültigen Ziffern gefunden oder eine ungültige Basis angegeben), wird der Wert von *strSource* an der Position gespeichert, auf die *endptr*zeigt.

**wcstoul** ist eine breitstellige Version von **strtoul**; das Argument *strSource* ist eine Zeichenfolge mit großen Zeichen. Anderenfalls verhalten sich diese Funktionen identisch.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|TCHAR.H-Routine|_UNICODE und _MBCS nicht definiert.|_MBCS definiert|_UNICODE definiert|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstoul**|**strtoul**|**strtoul**|**wcstoul**|
|**_tcstoul_l**|**strtoul_l**|**_strtoul_l**|**_wcstoul_l**|

**strtoul** erwartet, dass *strSource* auf eine Zeichenfolge der folgenden Form hinweist:

> [*Leerzeichen*] [a**+** **-**&#124; ' [**0** [- **x** &#124; **X** ' ]] [*Ziffern* &#124; *Buchstaben*]

Ein *Leerzeichen* kann aus Leerzeichen und Registerkartenzeichen bestehen, die ignoriert werden. *Ziffern* sind eine oder mehrere Dezimalstellen. *Buchstaben* sind einer oder mehrere der Buchstaben "a" bis "z" (oder "A" bis "Z"). Das erste Zeichen, das dieser Form nicht entspricht, beendet die Überprüfung. Wenn *die Basis* zwischen 2 und 36 liegt, wird sie als Basis der Zahl verwendet. Wenn *Base* 0 ist, werden die Anfangszeichen der Zeichenfolge, auf die von *strSource* verwiesen wird, verwendet, um die Basis zu bestimmen. Wenn das erste Zeichen "0" und das zweite Zeichen nicht "x" oder "X" ist, wird die Zeichenfolge als ganze Oktalzahl interpretiert. Wenn das erste Zeichen "0" und das zweite Zeichen nicht "x" oder "X" ist, wird die Zeichenfolge als hexadezimale ganze Zahl interpretiert. Wenn das erste Zeichen "1" bis "9 " ist, wird die Zeichenfolge als ganze Dezimalzahl interpretiert. Den Buchstaben „a“ bis „z“ (bzw. „A“ bis „Z“) werden die Werten 10 bis 35 zugewiesen. Es sind nur Buchstaben zulässig, deren zugewiesene Werte kleiner als *base* sind. Das erste Zeichen außerhalb des Bereichs der Basis beendet die Überprüfung. Wenn *basisrist* z. B. 0 ist und das erste gescannte Zeichen '0' ist, wird eine oktale Ganzzahl angenommen, und ein Zeichen '8' oder '9' stoppt den Scan. **strtoul** erlaubt ein**+** Plus -**-**) oder Minus ( ) Vorzeichenpräfix; Ein führendes Minuszeichen gibt an, dass der Rückgabewert negiert wird.

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**strtoul**|\<stdlib.h>|
|**wcstoul**|\<stdlib.h> oder \<wchar.h>|
|**_strtoul_l**|\<stdlib.h>|
|**_wcstoul_l**|\<stdlib.h> oder \<wchar.h>|

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
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
