---
title: ':::no-loc(strtol):::, :::no-loc(wcstol):::, :::no-loc(_strtol_l):::, :::no-loc(_wcstol_l):::'
ms.date: 4/2/2020
api_name:
- ':::no-loc(strtol):::'
- ':::no-loc(wcstol):::'
- ':::no-loc(_strtol_l):::'
- ':::no-loc(_wcstol_l):::'
- '_o_:::no-loc(_strtol_l):::'
- '_o_:::no-loc(_wcstol_l):::'
- '_o_:::no-loc(strtol):::'
- '_o_:::no-loc(wcstol):::'
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- ':::no-loc(_wcstol_l):::'
- ':::no-loc(strtol):::'
- ':::no-loc(_tcstol):::'
- ':::no-loc(wcstol):::'
- ':::no-loc(_strtol_l):::'
- ':::no-loc(_tcstol_l):::'
helpviewer_keywords:
- ':::no-loc(wcstol)::: function'
- :::no-loc(wcstol):::_l function
- ':::no-loc(_tcstol)::: function'
- string conversion, to integers
- tcstol function
- :::no-loc(strtol):::_l function
- ':::no-loc(_wcstol_l)::: function'
- ':::no-loc(_strtol_l)::: function'
- ':::no-loc(strtol)::: function'
ms.assetid: 1787c96a-f283-4a83-9325-33cfc1c7e240
no-loc:
- ':::no-loc(strtol):::'
- ':::no-loc(wcstol):::'
- ':::no-loc(_strtol_l):::'
- ':::no-loc(_wcstol_l):::'
- ':::no-loc(LONG_MAX):::'
- ':::no-loc(LONG_MIN):::'
- ':::no-loc(errno):::'
- ':::no-loc(ERANGE):::'
- ':::no-loc(EINVAL):::'
- ':::no-loc(LC_NUMERIC):::'
- ':::no-loc(_tcstol):::'
- ':::no-loc(_tcstol_l):::'
- ':::no-loc(localeconv):::'
- ':::no-loc(setlocale):::'
- ':::no-loc(_wsetlocale):::'
- ':::no-loc(strtod):::'
- ':::no-loc(_strtod_l):::'
- ':::no-loc(wcstod):::'
- ':::no-loc(_wcstod_l):::'
- ':::no-loc(strtoll):::'
- ':::no-loc(_strtoll_l):::'
- ':::no-loc(wcstoll):::'
- ':::no-loc(_wcstoll_l):::'
- ':::no-loc(strtoul):::'
- ':::no-loc(_strtoul_l):::'
- ':::no-loc(wcstoul):::'
- ':::no-loc(_wcstoul_l):::'
- ':::no-loc(atof):::'
- ':::no-loc(_atof_l):::'
- ':::no-loc(_wtof):::'
- ':::no-loc(_wtof_l):::'
ms.openlocfilehash: a5265b434f14f299532d6f5ebb65c83d75ea63ca
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232403"
---
# <a name="no-locstrtol-no-locwcstol-no-loc_strtol_l-no-loc_wcstol_l"></a>:::no-loc(strtol):::, :::no-loc(wcstol):::, :::no-loc(_strtol_l):::, :::no-loc(_wcstol_l):::

Konvertieren von Zeichen folgen in einen **`long`** ganzzahligen Wert.

## <a name="syntax"></a>Syntax

```C
long :::no-loc(strtol):::(
   const char *string,
   char **end_ptr,
   int base
);
long :::no-loc(wcstol):::(
   const wchar_t *string,
   wchar_t **end_ptr,
   int base
);
long :::no-loc(_strtol_l):::(
   const char *string,
   char **end_ptr,
   int base,
   _locale_t locale
);
long :::no-loc(_wcstol_l):::(
   const wchar_t *string,
   wchar_t **end_ptr,
   int base,
   _locale_t locale
);
```

### <a name="parameters"></a>Parameter

*Schnür*\
Zu konvertierende mit NULL endende Zeichenfolge.

*end_ptr*\
Ein Ausgabeparameter, der auf das Zeichen nach dem letzten interpretierten Zeichen zeigen soll. Ignoriert, wenn **null**.

*sock*\
Zu verwendende Zahlenbasis.

*Konfigurations*\
Zu verwendendes Gebietsschema.

## <a name="return-value"></a>Rückgabewert

**:::no-loc(strtol):::**, **:::no-loc(wcstol):::** , **:::no-loc(_strtol_l):::** und **:::no-loc(_wcstol_l):::** geben den in der *Zeichenfolge*dargestellten Wert zurück. Wenn keine Konvertierung möglich ist, wird 0 zurückgegeben. Wenn die Darstellung einen Überlauf verursachen würde, wird oder zurückgegeben **:::no-loc(LONG_MAX):::** **:::no-loc(LONG_MIN):::** .

**:::no-loc(errno):::** wird auf festgelegt, **:::no-loc(ERANGE):::** Wenn ein Überlauf oder ein Unterlauf auftritt. Sie wird auf festgelegt, **:::no-loc(EINVAL):::** Wenn die *Zeichenfolge* **null**ist. Oder, wenn *Base* ungleich 0 (null) und kleiner als 2 oder größer als 36 ist. Weitere Informationen zu **:::no-loc(ERANGE):::** , **:::no-loc(EINVAL):::** und anderen Rückgabecodes finden Sie unter [_dos :::no-loc(errno)::: , :::no-loc(errno)::: , _sys_errlist und _sys_nerr](../../c-runtime-library/:::no-loc(errno):::-dos:::no-loc(errno):::-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Bemerkungen

Die **:::no-loc(strtol):::** **:::no-loc(wcstol):::** Funktionen,, **:::no-loc(_strtol_l):::** und **:::no-loc(_wcstol_l):::** konvertieren *Zeichen* folgen in eine **`long`** . Sie beendet das Lesen der *Zeichenfolge* beim ersten Zeichen, das nicht als Teil einer Zahl erkannt wird. Dies kann das abschließende Null-Zeichen oder das erste alphanumerische Zeichen sein, das größer oder gleich der *Basis*ist.

**:::no-loc(wcstol):::** und **:::no-loc(_wcstol_l):::** sind breit Zeichen Versionen von **:::no-loc(strtol):::** und **:::no-loc(_strtol_l):::** . Das *Zeichen* folgen Argument ist eine Zeichenfolge mit breit Zeichen. Diese Funktionen Verhalten sich identisch mit **:::no-loc(strtol):::** und **:::no-loc(_strtol_l):::** andernfalls. Die **:::no-loc(LC_NUMERIC):::** Kategorieeinstellung des Gebiets Schemas bestimmt die Erkennung des Basis Zeichens (der Bruch Komma-oder Dezimaltrennzeichen) in der *Zeichenfolge*. Die Funktionen **:::no-loc(strtol):::** und **:::no-loc(wcstol):::** verwenden das aktuelle Gebiets Schema. **:::no-loc(_strtol_l):::** und **:::no-loc(_wcstol_l):::** verwenden stattdessen das übergebene Gebiets Schema. Weitere Informationen finden Sie unter [ :::no-loc(setlocale)::: ] und [Locale](../../c-runtime-library/locale.md)Gebiets Schema.

Wenn *end_ptr* **null**ist, wird es ignoriert. Andernfalls wird ein Zeiger auf das Zeichen, das die Überprüfung beendet hat, an dem Speicherort gespeichert, auf den von *end_ptr*verwiesen wird. Es ist keine Konvertierung möglich, wenn keine gültigen Ziffern gefunden werden oder eine ungültige Basis angegeben wird. Der Wert der *Zeichenfolge* wird dann an dem Speicherort gespeichert, auf den von *end_ptr*verwiesen wird.

**:::no-loc(strtol):::** erwartet, dass die *Zeichen* Folge auf eine Zeichenfolge der folgenden Form verweist:

> [*Leerzeichen*] [{ **+** &#124; **-** }] [**0** [{ **x** &#124; **x** }]] [*Alpha*numerische Zeichen]

Eckige Klammern ( `[ ]` ) umschließen optionale Elemente. Geschweifte Klammern und ein vertikales Balken ( `{ | }` ) umschließen Alternativen für ein einzelnes Element. *Leerräume können aus* Leerzeichen und Tabstopp Zeichen bestehen, die ignoriert werden. *alphanumerische* Zeichen sind Dezimalstellen oder die Buchstaben "a" bis "z" (oder "a" bis "z"). Das erste Zeichen, das dieser Form nicht entspricht, beendet die Überprüfung. Wenn die *Basis* zwischen 2 und 36 ist, wird Sie als Basis der Zahl verwendet. Wenn *Base* den Wert 0 hat, werden die ersten Zeichen der Zeichenfolge, auf die von *String* verwiesen wird, verwendet, um die Basis zu bestimmen. Wenn das erste Zeichen "0" und das zweite Zeichen nicht "x" oder "x" ist, wird die Zeichenfolge als oktale ganze Zahl interpretiert. Wenn das erste Zeichen "0" und das zweite Zeichen nicht "x" oder "X" ist, wird die Zeichenfolge als hexadezimale ganze Zahl interpretiert. Wenn das erste Zeichen "1" bis "9 " ist, wird die Zeichenfolge als ganze Dezimalzahl interpretiert. Den Buchstaben "a" bis "z" (oder "a" bis "z") werden die Werte 10 bis 35 zugewiesen. Der Scan lässt nur Buchstaben zu, deren Werte kleiner als *Base*sind. Das erste Zeichen außerhalb des Bereichs der Basis beendet die Überprüfung. Angenommen, die *Zeichenfolge* beginnt mit "01". Wenn *Base* 0 ist, geht der Scanner davon aus, dass es sich um eine oktale ganze Zahl handelt. Das Zeichen "8" oder "9" beendet die Überprüfung.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|TCHAR.H-Routine|_UNICODE und _MBCS nicht definiert.|_MBCS definiert|_UNICODE definiert|
|---------------------|------------------------------------|--------------------|-----------------------|
|**:::no-loc(_tcstol):::**|**:::no-loc(strtol):::**|**:::no-loc(strtol):::**|**:::no-loc(wcstol):::**|
|**:::no-loc(_tcstol_l):::**|**:::no-loc(_strtol_l):::**|**:::no-loc(_strtol_l):::**|**:::no-loc(_wcstol_l):::**|

## <a name="requirements"></a>Anforderungen

|-Routine zurückgegebener Wert|Erforderlicher Header|
|-------------|---------------------|
|**:::no-loc(strtol):::**|\<stdlib.h>|
|**:::no-loc(wcstol):::**|\<stdlib.h> oder \<wchar.h>|
|**:::no-loc(_strtol_l):::**|\<stdlib.h>|
|**:::no-loc(_wcstol_l):::**|\<stdlib.h> oder \<wchar.h>|

Die **:::no-loc(_strtol_l):::** **:::no-loc(_wcstol_l):::** Funktionen und sind Microsoft-spezifisch, nicht Teil der Standard-C-Bibliothek. Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../compatibility.md).

## <a name="example"></a>Beispiel

Weitere Informationen finden Sie im Beispiel für [:::no-loc(strtod):::](:::no-loc(strtod):::-:::no-loc(strtod):::-l-:::no-loc(wcstod):::-:::no-loc(wcstod):::-l.md) .

## <a name="see-also"></a>Weitere Informationen

[Datenkonvertierung](../data-conversion.md)\
[Konfigurations](../locale.md)\
[:::no-loc(localeconv):::](:::no-loc(localeconv):::.md)\
[:::no-loc(setlocale):::, :::no-loc(_wsetlocale):::](:::no-loc(setlocale):::-w:::no-loc(setlocale):::.md)\
[Funktionen für Zeichen folgen in numerische Werte](../string-to-numeric-value-functions.md)\
[:::no-loc(strtod):::, :::no-loc(_strtod_l):::, :::no-loc(wcstod):::, :::no-loc(_wcstod_l):::](:::no-loc(strtod):::-:::no-loc(strtod):::-l-:::no-loc(wcstod):::-:::no-loc(wcstod):::-l.md)\
[:::no-loc(strtoll):::, :::no-loc(_strtoll_l):::, :::no-loc(wcstoll):::, :::no-loc(_wcstoll_l):::](:::no-loc(strtoll):::-:::no-loc(strtoll):::-l-:::no-loc(wcstoll):::-:::no-loc(wcstoll):::-l.md)\
[:::no-loc(strtoul):::, :::no-loc(_strtoul_l):::, :::no-loc(wcstoul):::, :::no-loc(_wcstoul_l):::](:::no-loc(strtoul):::-:::no-loc(strtoul):::-l-:::no-loc(wcstoul):::-:::no-loc(wcstoul):::-l.md)\
[:::no-loc(atof):::, :::no-loc(_atof_l):::, :::no-loc(_wtof):::, :::no-loc(_wtof_l):::](:::no-loc(atof):::-:::no-loc(atof):::-l-wtof-wtof-l.md)
