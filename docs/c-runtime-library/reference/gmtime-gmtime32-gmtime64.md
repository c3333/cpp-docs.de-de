---
title: gmtime, _gmtime32, _gmtime64
description: API-Referenz für `gmtime` , `_gmtime32` und `_gmtime64` , die einen- `time_t` Wert in eine- `tm` Struktur konvertieren.
ms.date: 10/27/2020
api_name:
- _gmtime32
- gmtime
- _gmtime64
- _o__gmtime32
- _o__gmtime64
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
- api-ms-win-crt-time-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- gmtime
- _gmtime32
- _gmtime64
helpviewer_keywords:
- gmtime32 function
- _gmtime64 function
- gmtime function
- time functions
- _gmtime32 function
- gmtime64 function
- time structure conversion
ms.assetid: 315501f3-477e-475d-a414-ef100ee0db27
ms.openlocfilehash: bb8bee6b752f64d85dfb0f8c9e5ba7acf204a76f
ms.sourcegitcommit: 9c801a43ee0d4d84956b03fd387716c818705e0d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/28/2020
ms.locfileid: "92907544"
---
# <a name="gmtime-_gmtime32-_gmtime64"></a>`gmtime`, `_gmtime32`, `_gmtime64`

Konvertiert einen `time_t` Zeitwert in eine- `tm` Struktur. Sicherere Versionen dieser Funktionen sind verfügbar. siehe [ `gmtime_s` , `_gmtime32_s` , `_gmtime64_s` ](gmtime-s-gmtime32-s-gmtime64-s.md).

## <a name="syntax"></a>Syntax

```C
struct tm *gmtime( const time_t *sourceTime );
struct tm *_gmtime32( const __time32_t *sourceTime );
struct tm *_gmtime64( const __time64_t *sourceTime );
```

### <a name="parameters"></a>Parameter

*`sourceTime`*\
Zeiger auf die gespeicherte Zeit. Die Zeit wird in Sekunden dargestellt, die seit dem 1. Januar 1970, Mitternacht (00:00: 00), verstrichen sind. Die Anzeige erfolgt im UTC-Format.

## <a name="return-value"></a>Rückgabewert

Ein Zeiger auf eine Struktur vom Typ [`tm`](../../c-runtime-library/standard-types.md) . Die Felder der zurückgegebenen Struktur enthalten den ausgewerteten Wert des *`sourceTime`* Arguments in UTC und nicht in Ortszeit. Jedes dieser Strukturfelder ist wie folgt vom Typ `int`:

|Feld|Beschreibung|
|-|-|
|`tm_sec`|Sekunden nach Minute (0-59).|
|`tm_min`|Minuten nach Stunde (0-59).|
|`tm_hour`|Stunden seit Mitternacht (0-23).|
|`tm_mday`|Tag des Monats (1-31).|
|`tm_mon`|Monat (0-11; Januar = 0).|
|`tm_year`|Jahr (aktuelles Jahr minus 1900).|
|`tm_wday`|Wochentag (0-6; Sonntag = 0).|
|`tm_yday`|Tag des Jahres (0-365; 1. Januar = 0).|
|`tm_isdst`|Immer 0 für **gmtime** .|

Sowohl die 32-Bit-als auch die 64-Bit-Version von **`gmtime`** , [`mktime`](mktime-mktime32-mktime64.md) , [`mkgmtime`](mkgmtime-mkgmtime32-mkgmtime64.md) und [`localtime`](localtime-localtime32-localtime64.md) verwenden alle eine gemeinsame `tm` Struktur pro Thread für die Konvertierung. Jeder Aufruf dieser Funktionen zerstört das Ergebnis des vorherigen Aufrufs. Wenn *`sourceTime`* ein Datum vor Mitternacht (1. Januar 1970) darstellt, **`gmtime`** gibt zurück `NULL` . Es gibt keine Fehlerrückgabe.

**_gmtime64** , das die- `__time64_t` Struktur verwendet, ermöglicht das Ausdrücken von Datumsangaben bis 23:59:59, 31. Dezember 3000, UTC. **`_gmtime32`** stellt nur Datumsangaben 23:59:59 bis zum 18. Januar 2038 UTC dar. Der 1. Januar 1970 (Mitternacht) ist der untere Datumsbereich für beide Funktionen.

**`gmtime`** ist eine Inline Funktion, die ergibt **`_gmtime64`** , und `time_t` entspricht, `__time64_t` es sei denn, `_USE_32BIT_TIME_T` ist definiert. Wenn Sie den Compiler zwingen müssen, `time_t` als das alte 32-Bit-zu interpretieren `time_t` , können Sie definieren. `_USE_32BIT_TIME_T` Dies bewirkt jedoch, dass **`gmtime`** in **`_gmtime32`** und `time_t` als definiert ist `__time32_t` . Dies wird nicht empfohlen, da dies auf 64-Bit-Plattformen nicht zulässig ist. In jedem Fall kann die Anwendung nach dem 18. Januar 2038 fehlschlagen.

Diese Funktionen überprüfen ihre Parameter. Wenn *`sourceTime`* ein NULL-Zeiger ist oder wenn der *`sourceTime`* Wert negativ ist, rufen diese Funktionen einen Handler für ungültige Parameter auf, wie in [Parameter Validation (Parameter](../../c-runtime-library/parameter-validation.md)Überprüfung) beschrieben. Wenn die weitere Ausführung zugelassen wird, gibt diese Funktion `NULL` zurück und setzt `errno` auf `EINVAL`.

## <a name="remarks"></a>Hinweise

Die **`_gmtime32`** -Funktion gliedert den *`sourceTime`* -Wert und speichert ihn in einer statisch zugeordneten Struktur vom Typ `tm` , die in definiert ist `TIME.H` . Der Wert von *`sourceTime`* wird in der Regel von einem Rückruf der- [`time`](time-time32-time64.md) Funktion abgerufen.

> [!NOTE]
> In den meisten Fällen versucht die Zielumgebung zu bestimmen, ob die Sommerzeit wirksam ist. Die C-Laufzeitbibliothek geht davon aus, dass die Regeln der Vereinigten Staaten für die Implementierung der Berechnung der Sommerzeit (DST, Daylight Saving Time) angewendet werden.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|-Routine zurückgegebener Wert|Erforderlicher C-Header|Erforderlicher C++-Header|
|-------------|---------------------|-|
|**`gmtime`** , **`_gmtime32`** , **`_gmtime64`**|`<time.h>`| `<ctime>` oder `<time.h>`|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt_gmtime.c
// compile with: /W3
// This program uses _gmtime64 to convert a long-
// integer representation of coordinated universal time
// to a structure named newtime, then uses asctime to
// convert this structure to an output string.

#include <time.h>
#include <stdio.h>

int main(void)
{
   struct tm *newtime;
   __int64 ltime;
   char buff[80];

   _time64( &ltime );

   // Obtain coordinated universal time:
   newtime = _gmtime64( &ltime ); // C4996
   // Note: _gmtime64 is deprecated; consider using _gmtime64_s
   asctime_s( buff, sizeof(buff), newtime );
   printf( "Coordinated universal time is %s\n", buff );
}
```

```Output
Coordinated universal time is Tue Feb 12 23:11:31 2002
```

## <a name="see-also"></a>Weitere Informationen

[Zeitverwaltung](../../c-runtime-library/time-management.md)\
[`asctime`, `_wasctime`](asctime-wasctime.md)\
[`ctime`, `_ctime32`, `_ctime64`, `_wctime`, `_wctime32`, `_wctime64`](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)\
[`_ftime`, `_ftime32`, `_ftime64`](ftime-ftime32-ftime64.md)\
[`gmtime_s`, `_gmtime32_s`, `_gmtime64_s`](gmtime-s-gmtime32-s-gmtime64-s.md)\
[`localtime`, `_localtime32`, `_localtime64`](localtime-localtime32-localtime64.md)\
[`_mkgmtime`, `_mkgmtime32`, `_mkgmtime64`](mkgmtime-mkgmtime32-mkgmtime64.md)\
[`mktime`, `_mktime32`, `_mktime64`](mktime-mktime32-mktime64.md)\
[`time`, `_time32`, `_time64`](time-time32-time64.md)
