---
title: EVENT_DATA Struktur
description: Das C++ Build Insights SDK EVENT_DATA Strukturreferenz.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- EVENT_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 8ce396febe278c5e7c34fe170939c9522913f92a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325600"
---
# <a name="event_data-structure"></a>EVENT_DATA Struktur

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Um die Dokumentation zu diesen Versionen anzuzeigen, legen Sie das Visual **Studio-Versionsauswahlsteuerelement** für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich oben im Inhaltsverzeichnis auf dieser Seite.

::: moniker-end
::: moniker range=">=vs-2017"

Die `EVENT_DATA` Struktur beschreibt ein Ereignis, das von einer Analyse- oder Reloggingsitzung empfangen wurde. Diese Sitzungen werden durch Aufrufen der Funktionen [Analyze](../functions/analyze.md), [AnalyzeA](../functions/analyze-a.md), [AnalyzeW](../functions/analyze-w.md), [Relog](../functions/relog.md), [RelogA](../functions/relog-a.md)oder [RelogW](../functions/relog-w.md) gestartet.

## <a name="syntax"></a>Syntax

```cpp
typedef struct EVENT_DATA_TAG
{
    unsigned short          EventId;
    unsigned long long      EventInstanceId;

    long long               TickFrequency;
    long long               StartTimestamp;
    long long               StopTimestamp;
    long long               ExclusiveDurationTicks;
    long long               CPUTicks;
    long long               ExclusiveCPUTicks;
    long long               WallClockTimeResponsibilityTicks;
    long long               ExclusiveWallClockTimeResponsibilityTicks;

    const void*             Data;

    unsigned long           ProcessId;
    unsigned long           ThreadId;
    unsigned short          ProcessorIndex;

    const char*             EventName;
    const wchar_t*          EventWideName;

} EVENT_DATA;
```

## <a name="members"></a>Member

|  |  |
|--|--|
| `EventId` | Eine Zahl, die das Ereignis identifiziert. Eine Liste der Ereignisbezeichner finden Sie unter [EVENT_ID](event-id-enum.md). |
| `EventInstanceId` | Eine Zahl, die das aktuelle Ereignis innerhalb einer Ablaufverfolgung eindeutig identifiziert. Dieser Wert ändert sich nicht, wenn dieselbe Ablaufverfolgung mehrmals analysiert oder neu protokolliert wird. Verwenden Sie dieses Feld, um dasselbe Ereignis in mehreren Analyse- oder Relogging-Durchgängen über dieselbe Ablaufverfolgung zu identifizieren. |
| `TickFrequency` | Die Anzahl der Ticks pro Sekunde, die bei der Auswertung einer in Ticks gemessenen Dauer verwendet werden sollen. |
| `StartTimestamp` | Wenn es sich bei dem Ereignis um eine *Aktivität*handelt, wird dieses Feld auf einen Tick-Wert festgelegt, der zum Zeitpunkt des Beginns der Aktivität erfasst wurde. Wenn es sich bei diesem Ereignis um ein *einfaches Ereignis*handelt, wird dieses Feld auf einen Tick-Wert festgelegt, der zum Zeitpunkt des Auftretens des Ereignisses erfasst wurde. |
| `StopTimestamp` | Wenn es sich bei dem Ereignis um eine *Aktivität*handelt, wird dieses Feld auf einen Tick-Wert festgelegt, der zum Zeitpunkt des Beendetwerdens der Aktivität erfasst wurde. Wenn das Stoppereignis für diese Aktivität noch nicht empfangen wurde, wird dieses Feld auf Null gesetzt. Wenn es sich bei diesem Ereignis um ein *einfaches Ereignis*handelt, wird dieses Feld auf Null gesetzt. |
| `ExclusiveDurationTicks` | Wenn es sich bei diesem Ereignis um eine *Aktivität*handelt, wird dieses Feld auf die Anzahl der Ticks festgelegt, die direkt in dieser Aktivität aufgetreten sind. Die Anzahl der Ticks, die in einer untergeordneten Aktivität aufgetreten sind, wird ausgeschlossen. Dieses Feld ist für *einfache Ereignisse*auf Null gesetzt. |
| `CPUTicks` | Wenn es sich bei diesem Ereignis um eine *Aktivität*handelt, wird dieses Feld auf die Anzahl der CPU-Ticks festgelegt, die während dieser Aktivität aufgetreten sind. Ein CPU-Tick unterscheidet sich von einem normalen Tick. CPU-Ticks werden nur gezählt, wenn die CPU Code in einer Aktivität ausführt. CPU-Ticks werden nicht gezählt, wenn der der Aktivität zugeordnete Thread schläft. Dieses Feld ist für *einfache Ereignisse*auf Null gesetzt. |
| `ExclusiveCPUTicks` | Dieses Feld hat die `CPUTicks`gleiche Bedeutung wie , außer dass es keine CPU-Ticks enthält, die in untergeordneten Aktivitäten aufgetreten sind. Dieses Feld ist für *einfache Ereignisse*auf Null gesetzt. |
| `WallClockTimeResponsibilityTicks` | Wenn es sich bei diesem Ereignis um eine *Aktivität*handelt, wird dieses Feld auf eine Tickanzahl festgelegt, die den Beitrag dieser Aktivität zur Gesamtzeit von Wand-Uhr darstellt. Ein Wand-Uhr-Zeitverantwortungs-Tick unterscheidet sich von einem normalen Tick. Wand-Uhr-Zeitverantwortung tickt berücksichtigung Parallelität zwischen Aktivitäten. Beispielsweise können zwei parallele Aktivitäten eine Dauer von 50 Ticks und die gleiche Start- und Stoppzeit haben. In diesem Fall wird beiden eine Wand-Uhr-Zeitverantwortung von 25 Ticks zugewiesen. Dieses Feld ist für *einfache Ereignisse*auf Null gesetzt. |
| `ExclusiveWallClockTimeResponsibilityTicks` | Dieses Feld hat die `WallClockTimeResponsibilityTicks`gleiche Bedeutung wie , außer dass es nicht die Wand-Uhr-Zeitverantwortung tickt von Kinderaktivitäten enthält. Dieses Feld ist für *einfache Ereignisse*auf Null gesetzt. |
| `Data` | Verweist auf zusätzliche Daten, die im Ereignis gespeichert sind. Der Typ der Daten, auf die `EventId` verwiesen wird, ist je nach Feld unterschiedlich. |
| `ProcessId` | Der Bezeichner für den Prozess, in dem das Ereignis aufgetreten ist. |
| `ThreadId` | Der Bezeichner für den Thread, in dem das Ereignis aufgetreten ist. |
| `ProcessorIndex` | Die nullindizierte CPU-Nummer, auf der das Ereignis aufgetreten ist. |
| `EventName` | Eine ANSI-Zeichenfolge, die den `EventId`Namen der Entität enthält, die durch identifiziert wurde. |
| `EventWideName` | Eine breite Zeichenfolge, die den `EventId`Namen der Entität enthält, die durch identifiziert wurde. |

## <a name="remarks"></a>Bemerkungen

Viele Felder `EVENT_DATA` in enthalten Tick-Zahlen. C++ Build Insights verwendet den Leistungsindikator von Window als Quelle von Ticks. Eine Tickanzahl muss mit `TickFrequency` dem Feld verwendet werden, um es in eine geeignete Zeiteinheit wie Sekunden umzuwandeln. Im folgenden Beispiel finden Sie eine Durchführung dieser Konvertierung. `EVENT_DATA`enthält kein Feld für die regelmäßige Tickanzahl einer Aktivität. Um diesen Wert zu `StartTimestamp` `StopTimestamp`erhalten, subtrahieren Sie von . `EVENT_DATA`ist eine Struktur, die von C-API-Benutzern verwendet werden soll. Für C++-API-Benutzer führen Klassen wie [Event](../cpp-event-data-types/event.md) automatisch Zeitkonvertierungen durch.

Der Wert `EVENT_DATA` `Data` des Felds hängt `EventId` vom Wert seines Felds ab. Der Wert `Data` von wird in der folgenden Tabelle beschrieben. Einige Entitätsbezeichner fehlen möglicherweise in der folgenden Tabelle. In diesem Fall `Data` wird das `nullptr` Feld auf null oder Null gesetzt.

| Wert vom Typ `EventId` | Typ, auf den durch`Data` |
|--|--|
| `EVENT_ID_BACK_END_PASS` | [CL_PASS_DATA](cl-pass-data-struct.md) |
| `EVENT_ID_COMMAND_LINE` | `const wchar_t` |
| `EVENT_ID_COMPILER` | [INVOCATION_DATA](invocation-data-struct.md) |
| `EVENT_ID_ENVIRONMENT_VARIABLE` | [NAME_VALUE_PAIR_DATA](name-value-pair-data-struct.md) |
| `EVENT_ID_EXECUTABLE_IMAGE_OUTPUT` | [FILE_DATA](file-data-struct.md) |
| `EVENT_ID_EXP_OUTPUT` | [FILE_DATA](file-data-struct.md) |
| `EVENT_ID_FILE_INPUT` | [FILE_DATA](file-data-struct.md) |
| `EVENT_ID_FORCE_INLINE` | [FUNCTION_FORCE_INLINEE_DATA](function-force-inlinee-data-struct.md) |
| `EVENT_ID_FRONT_END_FILE` | [FRONT_END_FILE_DATA](front-end-file-data-struct.md) |
| `EVENT_ID_FRONT_END_PASS` | [CL_PASS_DATA](cl-pass-data-struct.md) |
| `EVENT_ID_FUNCTION` | [FUNCTION_DATA](function-data-struct.md) |
| `EVENT_ID_IMP_LIB_OUTPUT` | [FILE_DATA](file-data-struct.md) |
| `EVENT_ID_LIB_OUTPUT` | [FILE_DATA](file-data-struct.md) |
| `EVENT_ID_LINKER` | [INVOCATION_DATA](invocation-data-struct.md) |
| `EVENT_ID_OBJ_OUTPUT` | [FILE_DATA](file-data-struct.md) |
| `EVENT_ID_SYMBOL_NAME` | [SYMBOL_NAME_DATA](symbol-name-data-struct.md) |
| `EVENT_ID_TEMPLATE_INSTANTIATION` | [TEMPLATE_INSTANTIATION_DATA](template-instantiation-data-struct.md) |

## <a name="tick-conversion-example"></a>Beispiel für die Tick-Konvertierung

```cpp
//
// We have the elapsed number of ticks, along with the
// number of ticks per second. We use these values
// to convert to the number of elapsed microseconds.
// To guard against loss-of-precision, we convert
// to microseconds *before* dividing by ticks-per-second.
//

long long ConvertDurationToMicroseconds(const sruct EVENT_DATA& eventData)
{
    long long duration = eventData.StopTimestamp - eventData.StartTimestamp;
    long long duration *= 1000000;
    return duration / eventData.TickFrequency;
}
```

::: moniker-end
