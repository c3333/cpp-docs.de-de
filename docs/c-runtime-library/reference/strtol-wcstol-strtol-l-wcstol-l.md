---
title: strtol, wcstol, _strtol_l, _wcstol_l
ms.date: 4/2/2020
api_name:
- strtol
- wcstol
- _strtol_l
- _wcstol_l
- _o__strtol_l
- _o__wcstol_l
- _o_strtol
- _o_wcstol
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
- _wcstol_l
- strtol
- _tcstol
- wcstol
- _strtol_l
- _tcstol_l
helpviewer_keywords:
- wcstol function
- wcstol_l function
- _tcstol function
- string conversion, to integers
- tcstol function
- strtol_l function
- _wcstol_l function
- _strtol_l function
- strtol function
ms.assetid: 1787c96a-f283-4a83-9325-33cfc1c7e240
no-loc:
- strtol
- wcstol
- _strtol_l
- _wcstol_l
- LONG_MAX
- LONG_MIN
- errno
- ERANGE
- EINVAL
- LC_NUMERIC
- _tcstol
- _tcstol_l
- localeconv
- setlocale
- _wsetlocale
- strtod
- _strtod_l
- wcstod
- _wcstod_l
- strtoll
- _strtoll_l
- wcstoll
- _wcstoll_l
- strtoul
- _strtoul_l
- wcstoul
- _wcstoul_l
- atof
- _atof_l
- _wtof
- _wtof_l
ms.openlocfilehash: dbeaf04d34aa20e15de48e99082ed07edb6129ab
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320477"
---
# <a name="strtol-wcstol-_strtol_l-_wcstol_l"></a>strtol, wcstol, _strtol_l, _wcstol_l

Konvertieren Sie Zeichenfolgen in einen **Long** Integer-Wert.

## <a name="syntax"></a>Syntax

```C
long strtol(
   const char *string,
   char **end_ptr,
   int base
);
long wcstol(
   const wchar_t *string,
   wchar_t **end_ptr,
   int base
);
long _strtol_l(
   const char *string,
   char **end_ptr,
   int base,
   _locale_t locale
);
long _wcstol_l(
   const wchar_t *string,
   wchar_t **end_ptr,
   int base,
   _locale_t locale
);
```

### <a name="parameters"></a>Parameter

*Schnur*\
Zu konvertierende mit NULL endende Zeichenfolge.

*end_ptr*\
Ein Ausgabeparameter, der so eingestellt ist, dass er auf das Zeichen nach dem zuletzt interpretierten Zeichen zeigen soll. Ignoriert, wenn **NULL**.

*Basis*\
Zu verwendende Zahlenbasis.

*locale*\
Zu verwendendes Gebietsschema.

## <a name="return-value"></a>Rückgabewert

**strtol**, **wcstol**, **_strtol_l**und **_wcstol_l** geben den in *string*dargestellten Wert zurück. Sie geben 0 zurück, wenn keine Konvertierung möglich ist. Wenn die Darstellung einen Überlauf verursachen würde, geben sie **LONG_MAX** oder **LONG_MIN**zurück.

**errno** wird auf **ERANGE** gesetzt, wenn über- oder unterlaufen wird. Es wird auf **EINVAL** gesetzt, wenn *die Zeichenfolge* **NULL**ist. Oder, wenn *basisungleich* null und kleiner als 2 oder größer als 36 ist. Weitere Informationen zu **ERANGE**, **EINVAL**und anderen Rückgabecodes finden Sie unter [_doserrno, errno, _sys_errlist und _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Bemerkungen

Die Funktionen **strtol**, **wcstol**, **_strtol_l**und **_wcstol_l** konvertieren *Zeichenfolge* in eine **lange**. Sie hören auf, *die Zeichenfolge* beim ersten Zeichen zu lesen, das nicht als Teil einer Zahl erkannt wird. Es kann das Beenden-Null-Zeichen oder das erste alphanumerische Zeichen größer oder gleich *basis*sein.

**wcstol** und **_wcstol_l** sind breitstellige Versionen von **strtol** und **_strtol_l**. Ihr *Zeichenfolgenargument* ist eine Zeichenfolge mit einem großen Zeichen. Diese Funktionen verhalten sich identisch mit **Strtol** und **_strtol_l** sonst. Die **Einstellung LC_NUMERIC** Kategorie des Gebietsschemas bestimmt die Erkennung des Radixzeichens (der Bruchmarkierung oder des Dezimaltrennzeichens) in *string*. Die Funktionen **strtol** und **wcstol** verwenden das aktuelle Gebietsschema. **_strtol_l** und **_wcstol_l** stattdessen das übergebene Gebietsschema verwenden. Weitere Informationen finden Sie unter [setlocale] und [Locale](../../c-runtime-library/locale.md).

Wenn *end_ptr* **NULL**ist, wird er ignoriert. Andernfalls wird ein Zeiger auf das Zeichen, das den Scan beendet hat, an der Position gespeichert, auf die *end_ptr*. Eine Konvertierung ist nicht möglich, wenn keine gültigen Ziffern gefunden oder eine ungültige Basis angegeben wurde. Der Wert der *Zeichenfolge* wird dann an der Position gespeichert, auf die *end_ptr*.

**strtol** erwartet, dass *die Zeichenfolge* auf eine Zeichenfolge der folgenden Form hinweist:

> [*Leerzeichen*] [a**+** **-**&#124; ' [**0** [- **x** &#124; **X** ]] [*alphanumerisch*]

Quadratische Klammern`[ ]`( ) umgeben optionale Elemente. Geschweifte Klammern und`{ | }`ein vertikaler Balken ( ) umgeben Alternativen für ein einzelnes Element. *Leerzeichen* können aus Leerzeichen und Registerkartenzeichen bestehen, die ignoriert werden. *alphanumerische* Werte sind Dezimalstellen oder die Buchstaben 'a' bis 'z' (oder 'A' bis 'Z'). Das erste Zeichen, das nicht zu diesem Formular passt, stoppt den Scan. Wenn *die Basis* zwischen 2 und 36 liegt, wird sie als Basis der Zahl verwendet. Wenn *Basis* 0 ist, werden die Anfangszeichen der Zeichenfolge, auf die durch *Zeichenfolge* verwiesen wird, verwendet, um die Basis zu bestimmen. Wenn das erste Zeichen 0 ist und das zweite Zeichen nicht 'x' oder 'X' ist, wird die Zeichenfolge als oktale Ganzzahl interpretiert. Wenn das erste Zeichen "0" und das zweite Zeichen nicht "x" oder "X" ist, wird die Zeichenfolge als hexadezimale ganze Zahl interpretiert. Wenn das erste Zeichen "1" bis "9 " ist, wird die Zeichenfolge als ganze Dezimalzahl interpretiert. Den Buchstaben "a" bis "z" (oder "A" bis "Z") werden die Werte 10 bis 35 zugewiesen. Der Scan erlaubt nur Buchstaben, deren Werte kleiner als *Basis*sind. Das erste Zeichen außerhalb des Bereichs der Basis beendet die Überprüfung. Angenommen, *die Zeichenfolge* beginnt mit "01". Wenn *Basis* 0 ist, geht der Scanner davon aus, dass es sich um eine oktale Ganzzahl handelt. Ein Zeichen '8' oder '9' stoppt den Scan.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|TCHAR.H-Routine|_UNICODE und _MBCS nicht definiert.|_MBCS definiert|_UNICODE definiert|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstol**|**strtol**|**strtol**|**wcstol**|
|**_tcstol_l**|**_strtol_l**|**_strtol_l**|**_wcstol_l**|

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**strtol**|\<stdlib.h>|
|**wcstol**|\<stdlib.h> oder \<wchar.h>|
|**_strtol_l**|\<stdlib.h>|
|**_wcstol_l**|\<stdlib.h> oder \<wchar.h>|

Die **_strtol_l** **_wcstol_l** und Funktionen sind Microsoft-spezifisch und nicht Teil der Standard-C-Bibliothek. Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../compatibility.md).

## <a name="example"></a>Beispiel

Siehe Beispiel [strtod](strtod-strtod-l-wcstod-wcstod-l.md)für .

## <a name="see-also"></a>Siehe auch

[Datenkonvertierung](../data-conversion.md)\
[Locale](../locale.md)\
[localeconv](localeconv.md)\
[setlocale, _wsetlocale](setlocale-wsetlocale.md)\
[Zeichenfolge zu numerischen Wertfunktionen](../string-to-numeric-value-functions.md)\
[strtod, _strtod_l, wcstod, _wcstod_l](strtod-strtod-l-wcstod-wcstod-l.md)\
[strtoll, _strtoll_l, wcstoll, _wcstoll_l](strtoll-strtoll-l-wcstoll-wcstoll-l.md)\
[strtoul, _strtoul_l, wcstoul, _wcstoul_l](strtoul-strtoul-l-wcstoul-wcstoul-l.md)\
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)
