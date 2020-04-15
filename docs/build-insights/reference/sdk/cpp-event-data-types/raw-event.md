---
title: RawEvent-Klasse
description: Der C++ Build Insights SDK RawEvent-Klassenverweis.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- RawEvent
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 83629457ac3a0d1f991f6b084af2f3400612b2ac
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324385"
---
# <a name="rawevent-class"></a>RawEvent-Klasse

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Um die Dokumentation zu diesen Versionen anzuzeigen, legen Sie das Visual **Studio-Versionsauswahlsteuerelement** für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich oben im Inhaltsverzeichnis auf dieser Seite.

::: moniker-end
::: moniker range=">=vs-2017"

Die `RawEvent` Klasse wird verwendet, um ein allgemeines Ereignis in einem [EventStack](event-stack.md)darzustellen.

## <a name="syntax"></a>Syntax

```cpp
class RawEvent
{
public:
    RawEvent(const EVENT_DATA& event);

    const unsigned short&        EventId() const;
    const unsigned long long&    EventInstanceId() const;
    const long long&             TickFrequency() const;
    const long long&             StartTimestamp() const;
    const long long&             StopTimestamp() const;
    const long long&             ExclusiveDurationTicks() const;
    const long long&             CPUTicks() const;
    const long long&             ExclusiveCPUTicks() const;
    const long long&             WallClockTimeResponsibilityTicks() const;
    const long long&             ExclusiveWallClockTimeResponsibilityTicks() const;
    const void*                  Data() const;
    const unsigned long&         ProcessId() const;
    const unsigned long&         ThreadId() const;
    const unsigned short&        ProcessorIndex() const;
    const char*                  EventName() const;
    const wchar_t*               EventWideName() const;

    std::chrono::nanoseconds Duration() const;
    std::chrono::nanoseconds ExclusiveDuration() const;
    std::chrono::nanoseconds CPUTime() const ;
    std::chrono::nanoseconds ExclusiveCPUTime() const;
    std::chrono::nanoseconds WallClockTimeResponsibility() const;
    std::chrono::nanoseconds ExclusiveWallClockTimeResponsibility() const;
};
```

## <a name="remarks"></a>Bemerkungen

Mehrere Memberfunktionen `RawEvent` in der Klasse geben eine Tickanzahl zurück. C++ Build Insights verwendet den Leistungsindikator von Windows als Quelle von Ticks. Eine Tick-Zahl muss mit einer Tick-Frequenz verwendet werden, um sie in eine Zeiteinheit wie Sekunden umzuwandeln. Die `TickFrequency` Memberfunktion kann aufgerufen werden, um die Tick-Frequenz zu erhalten. Auf der [Seite EVENT_DATA](../c-event-data-types/event-data-struct.md#tick-conversion-example) finden Sie ein Beispiel zum Konvertieren von Ticks in eine Zeiteinheit.

Wenn Sie Ticks nicht selbst konvertieren `RawEvent` möchten, stellt die Klasse Memberfunktionen bereit, die Zeitwerte in Nanosekunden zurückgeben. Verwenden Sie die `chrono` Standard-C++-Bibliothek, um Nanosekunden in andere Zeiteinheiten zu konvertieren.

## <a name="members"></a>Member

### <a name="constructor"></a>Konstruktor

[RawEvent](#raw-event)

### <a name="functions"></a>Functions

[CPUTicks](#cpu-ticks)\
[CPUTime](#cpu-time)\
[Daten](#data)\
[Dauer](#duration)\
[EventId](#event-id)
[EventId-EreignisInstanzid-Ereignisname](#event-instance-id)
[EventName](#event-name)\
[EventWideName](#event-wide-name)\
[ExclusiveCPUTicks](#exclusive-cpu-ticks)\
[ExclusiveCPUTime](#exclusive-cpu-time)\
[ExclusiveDuration](#exclusive-duration)\
[ExclusiveDurationTicks](#exclusive-duration-ticks)\
[ExclusiveWallClockTimeResponsibility](#exclusive-wall-clock-time-responsibility)\
[ExclusiveWallClockTimeResponsibilityTicks](#exclusive-wall-clock-time-responsibility-ticks)\
[Processid](#process-id)\
[ProcessorIndex](#processor-index)\
[StartTimestamp](#start-timestamp)\
[StopTimestamp](#stop-timestamp)\
[Threadid](#thread-id)\
[Tickfrequency](#tick-frequency)\
[WallClockTimeResponsibility](#wall-clock-time-responsibility)\
[WallClockTimeResponsibilityTicks](#wall-clock-time-responsibility-ticks)

## <a name="rawevent"></a><a name="raw-event"></a>RawEvent

```cpp
RawEvent(const EVENT_DATA& data);
```

### <a name="parameters"></a>Parameter

*Ereignis*\
Die Ereignisdaten.

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

## <a name="data"></a><a name="data"></a>Daten

```cpp
const void* Data() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf zusätzliche Daten, die in diesem Ereignis enthalten sind. Weitere Informationen zum Interpretieren dieses Felds finden Sie [unter EVENT_DATA](../c-event-data-types/event-data-struct.md).

## <a name="duration"></a><a name="duration"></a>Dauer

```cpp
std::chrono::nanoseconds Duration() const;
```

### <a name="return-value"></a>Rückgabewert

Die Dauer der Aktivität in Nanosekunden.

## <a name="eventid"></a><a name="event-id"></a>Eventid

```cpp
const unsigned short& EventId() const;
```

### <a name="return-value"></a>Rückgabewert

Eine Zahl, die den Ereignistyp identifiziert. Eine Liste der Ereignisbezeichner finden Sie unter [EVENT_ID](../c-event-data-types/event-id-enum.md).

## <a name="eventinstanceid"></a><a name="event-instance-id"></a>EventInstanceId

```cpp
const unsigned long long& EventInstanceId() const;
```

### <a name="return-value"></a>Rückgabewert

Eine Zahl, die das Ereignis innerhalb einer Ablaufverfolgung eindeutig identifiziert. Dieser Wert ändert sich nicht, wenn dieselbe Ablaufverfolgung mehrmals analysiert oder neu protokolliert wird. Verwenden Sie diesen Wert, um dasselbe Ereignis in mehreren Analyse- oder Relogging-Durchläufen über dieselbe Ablaufverfolgung zu identifizieren.

## <a name="eventname"></a><a name="event-name"></a>Eventname

```cpp
const char* EventName() const;
```

### <a name="return-value"></a>Rückgabewert

Eine ANSI-Zeichenfolge, die den Namen des ereignistyps enthält, der durch [EventId](#event-id)identifiziert wird.

## <a name="eventwidename"></a><a name="event-wide-name"></a>EventWideName

```cpp
const wchar_t* EventWideName() const;
```

### <a name="return-value"></a>Rückgabewert

Eine breite Zeichenfolge, die den Namen des ereignistyps enthält, der durch [EventId](#event-id)identifiziert wird.

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

## <a name="processid"></a><a name="process-id"></a>Processid

```cpp
const unsigned long& ProcessId() const;
```

### <a name="return-value"></a>Rückgabewert

Der Bezeichner für den Prozess, in dem das Ereignis aufgetreten ist.

## <a name="processorindex"></a><a name="processor-index"></a>ProcessorIndex

```cpp
const unsigned short& ProcessorIndex() const;
```

### <a name="return-value"></a>Rückgabewert

Der nullbasierte Index für den logischen Prozessor, auf dem das Ereignis aufgetreten ist.

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

## <a name="threadid"></a><a name="thread-id"></a>Threadid

```cpp
const unsigned long& ThreadId() const;
```

### <a name="return-value"></a>Rückgabewert

Der Bezeichner für den Thread, in dem das Ereignis aufgetreten ist.

## <a name="tickfrequency"></a><a name="tick-frequency"></a>Tickfrequency

```cpp
const long long& TickFrequency() const;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Ticks pro Sekunde, die bei der Auswertung einer in Ticks für dieses Ereignis gemessenen Dauer verwendet werden sollen.

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

Eine Tick-Zahl, die den Beitrag dieser Aktivität zur Gesamtzeit der Wanduhr darstellt. Ein Wand-Uhr-Zeitverantwortungs-Tick unterscheidet sich von einem normalen Tick. Wand-Uhr-Zeitverantwortung tickt berücksichtigung Parallelität zwischen Aktivitäten. Zwei parallele Aktivitäten können eine Dauer von 50 Ticks und die gleiche Start- und Stoppzeit haben. In diesem Fall erhalten beide eine Wand-Uhr-Zeitverantwortung von 25 Ticks.

::: moniker-end
