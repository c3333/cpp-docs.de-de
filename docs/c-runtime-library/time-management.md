---
title: Zeitmanagement
ms.date: 11/04/2016
helpviewer_keywords:
- dates, run-time library members
- time, time management
- date functions
- time functions
ms.assetid: 93599220-c011-45d5-978f-12182abfdd2f
ms.openlocfilehash: 096207465b1be2eba70e95cff2c226924fc91bd7
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213449"
---
# <a name="time-management"></a>Zeitmanagement

Verwenden Sie diese Funktionen, um die aktuelle Uhrzeit abzurufen und sie nach Bedarf zu konvertieren, anzupassen und zu speichern. Die aktuelle Uhrzeit ist die Systemzeit.

Die Routinen **_ftime** und **localtime** verwenden die Umgebungsvariable **TZ**. Wenn **TZ** nicht festgelegt ist, versucht die Laufzeitbibliothek, die vom Betriebssystem festgelegten Zeitzoneninformationen zu verwenden. Stehen diese Informationen nicht zur Verfügung, verwenden diese Funktionen den Standardwert von PST8PDT. Weitere Informationen zu **TZ** finden Sie unter [_tzset](../c-runtime-library/reference/tzset.md). Siehe auch [_daylight, timezone und _tzname](../c-runtime-library/daylight-dstbias-timezone-and-tzname.md).

### <a name="time-routines"></a>Uhrzeitroutinen

|Funktion|Zweck|
|--------------|---------|
|[asctime, _wasctime](../c-runtime-library/reference/asctime-wasctime.md), [asctime_s, _wasctime_s](../c-runtime-library/reference/asctime-s-wasctime-s.md)|Konvertiert einen Zeitwert vom Typ **struct tm** in eine Zeichenfolge. Die Versionen dieser Funktionen mit dem Suffix **_s** sind sicherer.|
|[clock](../c-runtime-library/reference/clock.md)|Gibt die verstrichene Wanduhrzeit für den Prozess zurück.|
|[ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md), [_ctime_s, _ctime32_s, _ctime64_s, _wctime_s, _wctime32_s, _wctime64_s](../c-runtime-library/reference/ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)|Konvertiert einen Zeitwert vom Typ **time_t**, **__time32_t** oder **__time64_t** in eine Zeichenfolge. Die Versionen dieser Funktionen mit dem Suffix **_s** sind sicherer.|
|[difftime, _difftime32, _difftime64](../c-runtime-library/reference/difftime-difftime32-difftime64.md)|Bestimmt den Unterschied zwischen zwei Uhrzeiten.|
|[_ftime, _ftime32, _ftime64](../c-runtime-library/reference/ftime-ftime32-ftime64.md),[_ftime_s, _ftime32_s, _ftime64_s](../c-runtime-library/reference/ftime-s-ftime32-s-ftime64-s.md)|Speichert die aktuelle Systemzeit in einer Variablen vom Typ **struct _timeb** oder **struct __timeb64**. Die Versionen dieser Funktionen mit dem Suffix **_s** sind sicherer.|
|[_futime, _futime32, _futime64](../c-runtime-library/reference/futime-futime32-futime64.md)|Legt die Änderungszeit einer offenen Datei fest.|
|[gmtime, _gmtime32, _gmtime64](../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md), [gmtime_s, _gmtime32_s, _gmtime64_s](../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)|Konvertiert einen Zeitwert vom Typ **time_t** in **struct tm** oder vom Typ **__time64_t** in **struct tm**. Die Versionen dieser Funktionen mit dem Suffix **_s** sind sicherer.|
|[localtime, _localtime32, _localtime64](../c-runtime-library/reference/localtime-localtime32-localtime64.md), [localtime_s, _localtime32_s, _localtime64_s](../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md)|Konvertiert einen Zeitwert vom Type **time_t** in **struct tm** oder vom Typ **__time64_t** in **struct tm** mit lokaler Korrektur. Die Versionen dieser Funktionen mit dem Suffix **_s** sind sicherer.|
|[_mkgmtime, _mkgmtime32, _mkgmtime64](../c-runtime-library/reference/mkgmtime-mkgmtime32-mkgmtime64.md)|Konvertiert einen Zeitwert in einen Kalenderwert in GMT (Greenwich Mean Time).|
|[mktime, _mktime32, _mktime64](../c-runtime-library/reference/mktime-mktime32-mktime64.md)|Konvertiert einen Zeitwert in einen Kalenderwert.|
|[_strdate, _wstrdate](../c-runtime-library/reference/strdate-wstrdate.md), [_strdate_s, _wstrdate_s](../c-runtime-library/reference/strdate-s-wstrdate-s.md)|Gibt das aktuelle Systemdatum als Zeichenfolge zurück. Die Versionen dieser Funktionen mit dem Suffix **_s** sind sicherer.|
|[strftime, wcsftime, _strftime_l, _wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)|Formatiert die Datums- und Uhrzeitzeichenfolge für die internationale Verwendung.|
|[_strtime, _wstrtime](../c-runtime-library/reference/strtime-wstrtime.md), [_strtime_s, _wstrtime_s](../c-runtime-library/reference/strtime-s-wstrtime-s.md)|Gibt die aktuelle Systemzeit als Zeichenfolge zurück. Die Versionen dieser Funktionen mit dem Suffix **_s** sind sicherer.|
|[time, _time32, _time64](../c-runtime-library/reference/time-time32-time64.md)|Legt die aktuelle Systemzeit auf einen der folgenden Typen fest: **time_t**, **__time32_t** oder **__time64_t**.|
|[_tzset](../c-runtime-library/reference/tzset.md)|Legt externe Zeitvariablen aus der Umgebungsvariable **TZ** fest.|
|[_utime, _utime32, _utime64, _wutime, _wutime32, _wutime64](../c-runtime-library/reference/utime-utime32-utime64-wutime-wutime32-wutime64.md)|Legt die Änderungszeit für eine angegebene Datei fest. Hierzu wird entweder die aktuelle Uhrzeit oder der Uhrzeitwert verwendet, der in der Struktur gespeichert ist.|

> [!NOTE]
> Die Uhrzeitfunktion gibt in allen Versionen von Microsoft C/C++ (mit Ausnahme von Microsoft C/C++ 7.0) und in allen Versionen von Visual C++ die aktuelle Uhrzeit als die Anzahl von Sekunden zurück, die seit dem 1. Januar 1970 verstrichen sind. In Microsoft C/C++ 7.0 gab **time** die aktuelle Uhrzeit als die Anzahl von Sekunden zurück, die seit dem 31. Dezember 1899 verstrichen sind.

> [!NOTE]
> In Versionen von Visual C++ und Microsoft C/C++ vor Visual Studio 2005 war **time_t** ein **`long int`** (32 Bits) und konnte deshalb nicht für Datumsangaben nach dem 19. Januar 3:14:07, 2038 UTC verwendet werden. **time_t** entspricht jetzt standardmäßig **__time64_t**, aber das Definieren von **_USE_32BIT_TIME_T** ändert **time_t** in **__time32_t** und zwingt viele Zeitfunktionen zum Aufruf von Versionen, die die 32-Bit-Version von **time_t** akzeptieren. Weitere Informationen finden Sie unter [Standardtypen](../c-runtime-library/standard-types.md) und in den Kommentaren in der Dokumentation zu den einzelnen Zeitfunktionen.

## <a name="see-also"></a>Weitere Informationen

[Universelle C-Laufzeitroutinen nach Kategorie](../c-runtime-library/run-time-routines-by-category.md)<br/>
