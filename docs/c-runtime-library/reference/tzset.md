---
title: _tzset
ms.date: 4/2/2020
api_name:
- _tzset
- _o__tzset
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _tzset
helpviewer_keywords:
- _tzset function
- time environment variables
- environment variables, setting time
ms.assetid: 3f6ed537-b414-444d-b272-5dd377481930
ms.openlocfilehash: b2537a3bbfd2b5cec6bdf149c520aac7e3344b1e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81362188"
---
# <a name="_tzset"></a>_tzset

Legt die Umgebungsvariablen für die Zeit fest.

> [!IMPORTANT]
> Diese API kann nicht in Anwendungen verwendet werden, die in Windows-Runtime ausgeführt werden. Weitere Informationen finden Sie im Artikel [CRT functions not supported in Universal Windows Platform apps (In Apps für die universelle Windows-Plattform nicht unterstützte CRT-Funktionen)](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntax

```C
void _tzset( void );
```

## <a name="remarks"></a>Bemerkungen

Die **_tzset-Funktion** verwendet die aktuelle Einstellung der Umgebungsvariablen **TZ,** um drei globalen Variablen Werte zuzuweisen: **_daylight**, **_timezone**und **_tzname**. Diese Variablen werden von den [_ftime-](ftime-ftime32-ftime64.md) und [Lokalzeitfunktionen](localtime-localtime32-localtime64.md) verwendet, um Korrekturen von der koordinierten Weltzeit (UTC) bis zur ortszeiten Zeit vorzunehmen, und durch die [Zeitfunktion,](time-time32-time64.md) um UTC aus der Systemzeit zu berechnen. Verwenden Sie die folgende **TZ** Syntax, um die TZ-Umgebungsvariable festzulegen:

> **satz TZ=**_tzn_ \[ **+**&#124;**-**]*hh*\[**:**_mm_\[**:**_ss_] ][*dzn*]

|Parameter|BESCHREIBUNG|
|-|-|
| *tzn* | Dreibuchstabiger Zeitzonenname, z. B. PST. Sie müssen die richtige Verschiebung (Offset) von der Ortszeit zur UTC angeben. |
| *hh* | Unterschied in Stunden zwischen UTC und Ortszeit. Das Pluszeichen (+) ist für positive Werte optional. |
| *Mm* | Minuten. Getrennt von *hh* durch einen Doppelpunkt (**:**). |
| *Ss* | Sekunden. Getrennt von *mm* durch einen Doppelpunkt (**:**). |
| *dzn* | Dreibuchstabige Sommerzeitzone, z. B. PDT. Wenn die Sommerzeit in der Ortschaft nie in Kraft ist, legen Sie **TZ** ohne Wert für *dzn*fest. Die C-Laufzeitbibliothek wendet die Regeln der Vereinigten Staaten an, um die Berechnung der Sommerzeit (DST, Daylight Saving Time) zu implementieren. |

> [!NOTE]
> Seien Sie vorsichtig, wenn Sie das Zeichen des Zeitunterschieds berechnen. Da der Zeitunterschied die Verschiebung von der Ortszeit zu UTC (anstatt umgekehrt) ist, ist das dazugehörige Zeichen gegenüber dem erwarteten möglicherweise das entgegengesetzte. Für Zeitzonen vor UTC ist der Zeitunterschied negativ; für Zeitzonen hinter UTC ist der Unterschied positiv.

Um beispielsweise die **Umgebungsvariable TZ** so einzustellen, dass sie der aktuellen Zeitzone in Deutschland entspricht, geben Sie in der Befehlszeile Folgendes ein:

> **Satz TZ=GST-1GDT**

Dieser Befehl verwendet GST zur Angabe der deutschen Normalzeit und setzt voraus, dass UTC eine Stunde hinter Deutschland (oder Deutschland eine Stunde vor UTC) ist, und dass Deutschland die Sommerzeit berücksichtigt.

Wenn der **TZ-Wert** nicht festgelegt ist, **versucht _tzset,** die vom Betriebssystem angegebenen Zeitzoneninformationen zu verwenden. Im Windows-Betriebssystem werden diese Informationen in der Datum/Uhrzeit-Anwendung in der Systemsteuerung angegeben. Wenn **_tzset** diese Informationen nicht abrufen können, verwendet es standardmäßig PST8PDT, was die Pazifische Zeitzone bedeutet.

Basierend auf dem Wert der TZ-Umgebungsvariablen werden den globalen Variablen **_daylight ,** **_timezone**und **_tzname,** wenn **_tzset** aufgerufen wird, die folgenden Werte zugewiesen: **TZ**

|Globale Variable|BESCHREIBUNG|Standardwert|
|---------------------|-----------------|-------------------|
|**_daylight**|Wert ungleich Null, wenn in der **TZ-Einstellung** eine Sommerzeitzone angegeben ist; andernfalls 0.|1|
|**_timezone**|Unterschied in Sekunden zwischen Ortszeit und UTC.|28800 (28800 Sekunden sind gleich 8 Stunden)|
|**_tzname**[0]|Zeichenfolgenwert des Zeitzonennamens aus der **Umgebungsvariablen TZ;** leer, wenn **TZ** nicht gesetzt wurde.|PST|
|**_tzname**[1]|Zeichenfolgenwert der Sommerzeitzone; leer, wenn die Sommerzeitzone in der **Umweltvariablen TZ** weggelassen wird.|PDT|

Die in der obigen Tabelle angezeigten Standardwerte für **_daylight** und das **array _tzname** entsprechen "PST8PDT". Wenn die DST-Zone in der TZ-Umgebungsvariablen weggelassen wird, ist der Wert von **_daylight** 0, und die [_ftime](ftime-ftime32-ftime64.md)-, [gmtime-](gmtime-gmtime32-gmtime64.md)und **TZ** [Lokalzeitfunktionen](localtime-localtime32-localtime64.md) geben 0 für ihre DST-Flags zurück.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**_tzset**|\<time.h>|

Die **_tzset** Funktion ist Microsoft-spezifisch. Weitere Informationen finden Sie unter [Kompatibilität](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt_tzset.cpp
// This program uses _tzset to set the global variables
// named _daylight, _timezone, and _tzname. Since TZ is
// not being explicitly set, it uses the system time.

#include <time.h>
#include <stdlib.h>
#include <stdio.h>

int main( void )
{
    _tzset();
    int daylight;
    _get_daylight( &daylight );
    printf( "_daylight = %d\n", daylight );
    long timezone;
    _get_timezone( &timezone );
    printf( "_timezone = %ld\n", timezone );
    size_t s;
    char tzname[100];
    _get_tzname( &s, tzname, sizeof(tzname), 0 );
    printf( "_tzname[0] = %s\n", tzname );
    exit( 0 );
}
```

```Output
_daylight = 1
_timezone = 28800
_tzname[0] = Pacific Standard Time
```

## <a name="see-also"></a>Siehe auch

[Zeitmanagement](../../c-runtime-library/time-management.md)<br/>
[asctime, _wasctime](asctime-wasctime.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime, _gmtime32, _gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime, _localtime32, _localtime64](localtime-localtime32-localtime64.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
[_utime, _utime32, _utime64, _wutime, _wutime32, _wutime64](utime-utime32-utime64-wutime-wutime32-wutime64.md)<br/>
