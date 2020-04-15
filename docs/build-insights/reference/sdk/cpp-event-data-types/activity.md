---
title: Aktivitätsklasse
description: Der C++Build Insights SDK-Aktivitätsklassenverweis.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Activity
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 2ea04150aec9c0b2366d97e6e4c15de557a4f47c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325246"
---
# <a name="activity-class"></a>Aktivitätsklasse

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Um die Dokumentation zu diesen Versionen anzuzeigen, legen Sie das Visual **Studio-Versionsauswahlsteuerelement** für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich oben im Inhaltsverzeichnis auf dieser Seite.

::: moniker-end
::: moniker range=">=vs-2017"

Die `Activity` Klasse wird mit den Funktionen [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)und [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) verwendet. Verwenden Sie es, um jedem Aktivitätsereignis zu entsprechen. Verweisen Sie auf [die Ereignistabelle,](../event-table.md) um `Activity` alle Ereignisse anzuzeigen, die von der Klasse abgeglichen werden können.

## <a name="syntax"></a>Syntax

```cpp
class Activity : public Event
{
public:
    Activity(const RawEvent& event);

    const long long& StartTimestamp() const;
    const long long& StopTimestamp() const;
    const long long& ExclusiveDurationTicks() const;
    const long long& CPUTicks() const;
    const long long& ExclusiveCPUTicks() const;
    const long long& WallClockTimeResponsibilityTicks() const;
    const long long& ExclusiveWallClockTimeResponsibilityTicks() const;

    std::chrono::nanoseconds Duration() const;
    std::chrono::nanoseconds ExclusiveDuration() const;
    std::chrono::nanoseconds CPUTime() const ;
    std::chrono::nanoseconds ExclusiveCPUTime() const;
    std::chrono::nanoseconds WallClockTimeResponsibility() const;
    std::chrono::nanoseconds ExclusiveWallClockTimeResponsibility() const;
};
```

## <a name="remarks"></a>Bemerkungen

Mehrere Memberfunktionen `Activity` in der Klasse geben eine Tickanzahl zurück. C++ Build Insights verwendet den Leistungsindikator von Windows als Quelle von Ticks. Eine Tick-Zahl muss mit einer Tick-Frequenz verwendet werden, um sie in eine Zeiteinheit wie Sekunden umzuwandeln. Die `TickFrequency` Memberfunktion, die in der [Ereignisbasisklasse](event.md) verfügbar ist, kann aufgerufen werden, um die Tick-Frequenz zu erhalten. Die [seite EVENT_DATA](../c-event-data-types/event-data-struct.md#tick-conversion-example) zeigt ein Beispiel für die Konvertierung von Ticks in eine Zeiteinheit.

Wenn Sie Ticks nicht selbst in Zeiteinheiten `Activity` konvertieren möchten, stellt die Klasse Memberfunktionen bereit, die Zeitwerte in Nanosekunden zurückgeben. Verwenden Sie die `chrono` Standard-C++-Bibliothek, um sie in andere Zeiteinheiten umzuwandeln.

## <a name="members"></a>Member

Zusammen mit ihren Membern, die von `Activity` der [Ereignisbasisklasse](event.md) geerbt wurden, enthält die Klasse die folgenden Member:

### <a name="constructor"></a>Konstruktor

[Aktivität](#activity)

### <a name="functions"></a>Functions

[CPUTicks](#cpu-ticks)\
[CPUTime](#cpu-time)\
[Dauer](#duration)\
[ExclusiveCPUTicks](#exclusive-cpu-ticks)\
[ExclusiveCPUTime](#exclusive-cpu-time)\
[ExclusiveDuration](#exclusive-duration)\
[ExclusiveDurationTicks](#exclusive-duration-ticks)\
[ExclusiveWallClockTimeResponsibility](#exclusive-wall-clock-time-responsibility)\
[ExclusiveWallClockTimeResponsibilityTicks](#exclusive-wall-clock-time-responsibility-ticks)\
[StartTimestamp](#start-timestamp)\
[StopTimestamp](#stop-timestamp)\
[WallClockTimeResponsibility](#wall-clock-time-responsibility)\
[WallClockTimeResponsibilityTicks](#wall-clock-time-responsibility-ticks)

## <a name="activity"></a><a name="activity"></a> -Aktivität

```cpp
Activity(const RawEvent& event);
```

### <a name="parameters"></a>Parameter

*Ereignis*\
Jedes Aktivitätsereignis.

## <a name="cputicks"></a><a name="cpu-ticks"></a>CPUTicks

```cpp
const long long& CPUTicks() const;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der CPU-Ticks, die während dieser Aktivität aufgetreten sind. Ein CPU-Tick unterscheidet sich von einem normalen Tick. CPU-Ticks werden nur gezählt, wenn die CPU Code in einer Aktivität ausführt. CPU-Ticks werden nicht gezählt, wenn der der Aktivität zugeordnete Thread schläft.

## <a name="cputime"></a><a name="cpu-time"></a>CPUTime

```cpp
std::chrono::nanoseconds CPUTime()() const;
```

### <a name="return-value"></a>Rückgabewert

Die Zeit, mit der die CPU Code innerhalb dieser Aktivität ausführte. Dieser Wert kann höher als die Dauer der Aktivität sein, wenn untergeordnete Aktivitäten in separaten Threads ausgeführt werden. Der Wert wird in Nanosekunden zurückgegeben.

## <a name="duration"></a><a name="duration"></a>Dauer

```cpp
std::chrono::nanoseconds Duration() const;
```

### <a name="return-value"></a>Rückgabewert

Die Dauer der Aktivität in Nanosekunden.

## <a name="exclusivecputicks"></a><a name="exclusive-cpu-ticks"></a>ExclusiveCPUTicks

```cpp
const long long& ExclusiveCPUTicks() const;
```

### <a name="return-value"></a>Rückgabewert

Genauso wie [CPUTicks](#cpu-ticks), jedoch ohne die CPU-Ticks, die in untergeordneten Aktivitäten aufgetreten sind.

## <a name="exclusivecputime"></a><a name="exclusive-cpu-time"></a>ExclusiveCPUTime

```cpp
std::chrono::nanoseconds ExclusiveCPUTime() const;
```

### <a name="return-value"></a>Rückgabewert

Genauso wie [CPUTime](#cpu-time), mit der Ausnahme, dass die CPU-Zeit für untergeordnete Aktivitäten nicht enthalten ist.

## <a name="exclusiveduration"></a><a name="exclusive-duration"></a>ExclusiveDuration

```cpp
std::chrono::nanoseconds ExclusiveDuration() const;
```

### <a name="return-value"></a>Rückgabewert

Die Dauer der Aktivität in Nanosekunden, ohne die Zeit, die für untergeordnete Aktivitäten aufgewendet wurde.

## <a name="exclusivedurationticks"></a><a name="exclusive-duration-ticks"></a>ExclusiveDurationTicks

```cpp
const long long& ExclusiveDurationTicks() const;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Ticks, die in dieser Aktivität aufgetreten sind, mit Ausnahme der Anzahl der Ticks, die in untergeordneten Aktivitäten aufgetreten sind.

## <a name="exclusivewallclocktimeresponsibility"></a><a name="exclusive-wall-clock-time-responsibility"></a>ExclusiveWallClockTimeResponsibility

```cpp
std::chrono::nanoseconds ExclusiveWallClockTimeResponsibility() const;
```

### <a name="return-value"></a>Rückgabewert

Genauso wie [WallClockTimeResponsibility](#wall-clock-time-responsibility), ohne die Wand-Uhr-Zeitverantwortung für untergeordnete Aktivitäten.

## <a name="exclusivewallclocktimeresponsibilityticks"></a><a name="exclusive-wall-clock-time-responsibility-ticks"></a>ExclusiveWallClockTimeResponsibilityTicks

```cpp
const long long& ExclusiveWallClockTimeResponsibilityTicks() const;
```

### <a name="return-value"></a>Rückgabewert

Genauso wie [WallClockTimeResponsibilityTicks](#wall-clock-time-responsibility-ticks), jedoch ohne die Wand-Uhr-Zeitverantwortung, die von untergeordneten Aktivitäten angekreuzt wird.

## <a name="starttimestamp"></a><a name="start-timestamp"></a>StartTimestamp

```cpp
const long long& StartTimestamp() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Tick-Wert, der zum Zeitpunkt des Beginns der Aktivität erfasst wurde.

## <a name="stoptimestamp"></a><a name="stop-timestamp"></a>StopTimestamp

```cpp
const long long& StopTimestamp() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Tick-Wert, der zum Zeitpunkt des Beendetwerdens der Aktivität erfasst wurde.

## <a name="wallclocktimeresponsibility"></a><a name="wall-clock-time-responsibility"></a>WallClockTimeResponsibility

```cpp
std::chrono::nanoseconds WallClockTimeResponsibility() const;
```

### <a name="return-value"></a>Rückgabewert

Die Wand-Uhr-Zeitverantwortung dieser Aktivität, in Nanosekunden. Weitere Informationen dazu, was Wand-Uhr-Zeitverantwortung bedeutet, finden Sie unter [WallClockTimeResponsibilityTicks](#wall-clock-time-responsibility-ticks).

## <a name="wallclocktimeresponsibilityticks"></a><a name="wall-clock-time-responsibility-ticks"></a>WallClockTimeResponsibilityTicks

```cpp
const long long& WallClockTimeResponsibilityTicks() const;
```

### <a name="return-value"></a>Rückgabewert

Eine Tick-Zahl, die den Beitrag dieser Aktivität zur Gesamtzeit der Wanduhr darstellt. Ein Wand-Uhr-Zeitverantwortungs-Tick unterscheidet sich von einem normalen Tick. Wand-Uhr-Zeitverantwortung tickt berücksichtigung Parallelität zwischen Aktivitäten. Zwei parallele Aktivitäten können eine Dauer von 50 Ticks haben, und die gleiche Start-stopp-Zeit. In diesem Fall erhalten beide eine Wand-Uhr-Zeitverantwortung von 25 Ticks.

::: moniker-end
