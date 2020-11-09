---
title: RawEvent-Klasse
description: Die Referenz zur RawEvent-Klasse im C++ Build Insights SDK.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- RawEvent
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 1cf96e1b8eadaf1de9fe2cf565a993f3bcafe358
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "92920462"
---
# <a name="rawevent-class"></a>RawEvent-Klasse

::: moniker range="<=msvc-140"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Wenn die Dokumentation für diese Versionen angezeigt werden soll, legen Sie das Steuerelement für die Auswahl der **Version** von Visual Studio für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich am Anfang des Inhaltsverzeichnisses auf dieser Seite.

::: moniker-end
::: moniker range=">=msvc-150"

Die `RawEvent`-Klasse dient zur Darstellung eines allgemeinen Ereignisses in einem [EventStack](event-stack.md).

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

## <a name="remarks"></a>Hinweise

Mehrere Memberfunktionen in der `RawEvent`-Klasse geben eine Taktanzahl zurück. C++ Build Insights verwendet den Leistungsindikator von Windows als Taktquelle. Eine Taktanzahl muss mit einer Taktfrequenz verwendet werden, um sie in eine Zeiteinheit wie Sekunden umzurechnen. Die Memberfunktion `TickFrequency` kann zum Abrufen der Taktfrequenz aufgerufen werden. Auf der Seite [EVENT_DATA](../c-event-data-types/event-data-struct.md#tick-conversion-example) finden Sie ein Beispiel für die Umrechnung von Takten in eine Zeiteinheit.

Wenn Sie Takte nicht selbst umrechnen möchten, stellt die `RawEvent`-Klasse Memberfunktionen bereit, die die Zeitwerte in Nanosekunden zurückgeben. Zur Umrechnung von Nanosekunden in andere Zeiteinheiten verwenden Sie die C++-Standardbibliothek `chrono`.

## <a name="members"></a>Member

### <a name="constructor"></a>Konstruktor

[RawEvent](#raw-event)

### <a name="functions"></a>Functions

[CPUTicks](#cpu-ticks)\
[CPUTime](#cpu-time)\
[Daten](#data)\
[Duration](#duration)\
[EventId](#event-id)
[EventInstanceId](#event-instance-id)
[EventName](#event-name)\
[EventWideName](#event-wide-name)\
[ExclusiveCPUTicks](#exclusive-cpu-ticks)\
[ExclusiveCPUTime](#exclusive-cpu-time)\
[ExclusiveDuration](#exclusive-duration)\
[ExclusiveDurationTicks](#exclusive-duration-ticks)\
[ExclusiveWallClockTimeResponsibility](#exclusive-wall-clock-time-responsibility)\
[ExclusiveWallClockTimeResponsibilityTicks](#exclusive-wall-clock-time-responsibility-ticks)\
[ProcessId](#process-id)\
[ProcessorIndex](#processor-index)\
[StartTimestamp](#start-timestamp)\
[StopTimestamp](#stop-timestamp)\
[ThreadId](#thread-id)\
[TickFrequency](#tick-frequency)\
[WallClockTimeResponsibility](#wall-clock-time-responsibility)\
[WallClockTimeResponsibilityTicks](#wall-clock-time-responsibility-ticks)

## <a name="rawevent"></a><a name="raw-event"></a> RawEvent

```cpp
RawEvent(const EVENT_DATA& data);
```

### <a name="parameters"></a>Parameter

*Ereignis*\
Die Ereignisdaten.

## <a name="cputicks"></a><a name="cpu-ticks"></a> CPUTicks

```cpp
const long long& CPUTicks() const;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der CPU-Takte während dieser Aktivität. Ein CPU-Tick unterscheidet sich von einem normalen Tick. CPU-Ticks werden nur gezählt, wenn die CPU Code in einer Aktivität ausführt. CPU-Ticks werden nicht gezählt, wenn sich der mit der Aktivität verknüpfte Thread im Ruhezustand befindet.

## <a name="cputime"></a><a name="cpu-time"></a> CPUTime

```cpp
std::chrono::nanoseconds CPUTime()() const;
```

### <a name="return-value"></a>Rückgabewert

Die Zeitspanne, in der die CPU Code in dieser Aktivität ausgeführt hat. Dieser Wert kann höher sein als die Dauer der Aktivität, wenn untergeordnete Aktivitäten in separaten Threads ausgeführt werden. Der Wert wird in Nanosekunden zurückgegeben.

## <a name="data"></a><a name="data"></a> Data

```cpp
const void* Data() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf zusätzliche Daten, die in diesem Ereignis enthalten sind. Weitere Informationen zum Interpretieren dieses Felds finden Sie unter [EVENT_DATA](../c-event-data-types/event-data-struct.md).

## <a name="duration"></a><a name="duration"></a> Duration

```cpp
std::chrono::nanoseconds Duration() const;
```

### <a name="return-value"></a>Rückgabewert

Die Dauer dieser Aktivität in Nanosekunden.

## <a name="eventid"></a><a name="event-id"></a> EventId

```cpp
const unsigned short& EventId() const;
```

### <a name="return-value"></a>Rückgabewert

Eine Zahl, die den Ereignistyp identifiziert. Eine Liste der Ereignisbezeichner finden Sie unter [EVENT_ID](../c-event-data-types/event-id-enum.md).

## <a name="eventinstanceid"></a><a name="event-instance-id"></a> EventInstanceId

```cpp
const unsigned long long& EventInstanceId() const;
```

### <a name="return-value"></a>Rückgabewert

Eine Zahl, die das Ereignis innerhalb einer Ablaufverfolgung eindeutig identifiziert. Dieser Wert ändert sich nicht, wenn dieselbe Stapelüberwachung mehrmals analysiert oder erneut protokolliert wird. Verwenden Sie dieses Feld, um ein und dasselbe Ereignis in mehreren Durchgängen derselben Ablaufverfolgung zur Analyse oder Neuprotokollierung zu identifizieren.

## <a name="eventname"></a><a name="event-name"></a> EventName

```cpp
const char* EventName() const;
```

### <a name="return-value"></a>Rückgabewert

Eine ANSI-Zeichenfolge mit dem Namen des durch [EventId](#event-id) identifizierten Entitätstyps.

## <a name="eventwidename"></a><a name="event-wide-name"></a> EventWideName

```cpp
const wchar_t* EventWideName() const;
```

### <a name="return-value"></a>Rückgabewert

Eine Zeichenfolge mit breiten Zeichen mit dem Namen des durch [EventId](#event-id) identifizierten Ereignistyps.

## <a name="exclusivecputicks"></a><a name="exclusive-cpu-ticks"></a> ExclusiveCPUTicks

```cpp
const long long& ExclusiveCPUTicks() const;
```

### <a name="return-value"></a>Rückgabewert

Identisch mit [CPUTicks](#cpu-ticks), aber ohne die CPU-Takte in untergeordneten Aktivitäten.

## <a name="exclusivecputime"></a><a name="exclusive-cpu-time"></a> ExclusiveCPUTime

```cpp
std::chrono::nanoseconds ExclusiveCPUTime() const;
```

### <a name="return-value"></a>Rückgabewert

Identisch mit [CPUTime](#cpu-time), mit dem Unterschied, dass die CPU-Zeit untergeordneter Aktivitäten nicht inbegriffen ist.

## <a name="exclusiveduration"></a><a name="exclusive-duration"></a> ExclusiveDuration

```cpp
std::chrono::nanoseconds ExclusiveDuration() const;
```

### <a name="return-value"></a>Rückgabewert

Die Dauer der Aktivität in Nanosekunden ohne die in untergeordneten Aktivitäten verbrachte Zeit.

## <a name="exclusivedurationticks"></a><a name="exclusive-duration-ticks"></a> ExclusiveDurationTicks

```cpp
const long long& ExclusiveDurationTicks() const;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Takte in dieser Aktivität ohne die Anzahl der Takte in untergeordneten Aktivitäten.

## <a name="exclusivewallclocktimeresponsibility"></a><a name="exclusive-wall-clock-time-responsibility"></a> ExclusiveWallClockTimeResponsibility

```cpp
std::chrono::nanoseconds ExclusiveWallClockTimeResponsibility() const;
```

### <a name="return-value"></a>Rückgabewert

Identisch mit [WallClockTimeResponsibility](#wall-clock-time-responsibility) mit Ausnahme der Gesamtbetrachtungszeit-Verantwortung untergeordneter Aktivitäten.

## <a name="exclusivewallclocktimeresponsibilityticks"></a><a name="exclusive-wall-clock-time-responsibility-ticks"></a> ExclusiveWallClockTimeResponsibilityTicks

```cpp
const long long& ExclusiveWallClockTimeResponsibilityTicks() const;
```

### <a name="return-value"></a>Rückgabewert

Identisch mit [WallClockTimeResponsibilityTicks](#wall-clock-time-responsibility-ticks) mit Ausnahme der Gesamtbetrachtungszeit-Verantwortungstakte untergeordneter Aktivitäten.

## <a name="processid"></a><a name="process-id"></a> ProcessId

```cpp
const unsigned long& ProcessId() const;
```

### <a name="return-value"></a>Rückgabewert

Der Bezeichner für den Prozess, in dem das Ereignis aufgetreten ist.

## <a name="processorindex"></a><a name="processor-index"></a> ProcessorIndex

```cpp
const unsigned short& ProcessorIndex() const;
```

### <a name="return-value"></a>Rückgabewert

Ein auf 0 (null) basierender Index für den logischen Prozessor, in dem das Ereignis aufgetreten ist.

## <a name="starttimestamp"></a><a name="start-timestamp"></a> StartTimestamp

```cpp
const long long& StartTimestamp() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Taktwert, der zum Startzeitpunkt der Aktivität aufgezeichnet wurde.

## <a name="stoptimestamp"></a><a name="stop-timestamp"></a> StopTimestamp

```cpp
const long long& StopTimestamp() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Taktwert, der zum Stoppzeitpunkt der Aktivität aufgezeichnet wurde.

## <a name="threadid"></a><a name="thread-id"></a> ThreadId

```cpp
const unsigned long& ThreadId() const;
```

### <a name="return-value"></a>Rückgabewert

Der Bezeichner für den Thread, in dem das Ereignis aufgetreten ist.

## <a name="tickfrequency"></a><a name="tick-frequency"></a> TickFrequency

```cpp
const long long& TickFrequency() const;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl von Takten pro Sekunde, die beim Auswerten einer in Takten gemessenen Dauer für dieses Ereignis verwendet werden soll.

## <a name="wallclocktimeresponsibility"></a><a name="wall-clock-time-responsibility"></a> WallClockTimeResponsibility

```cpp
std::chrono::nanoseconds WallClockTimeResponsibility() const;
```

### <a name="return-value"></a>Rückgabewert

Die Gesamtbetrachtungszeit-Verantwortung dieser Aktivität in Nanosekunden. Weitere Informationen dazu, was Gesamtbetrachtungszeit-Verantwortung bedeutet, finden Sie unter [WallClockTimeResponsibilityTicks](#wall-clock-time-responsibility-ticks).

## <a name="wallclocktimeresponsibilityticks"></a><a name="wall-clock-time-responsibility-ticks"></a> WallClockTimeResponsibilityTicks

```cpp
const long long& WallClockTimeResponsibilityTicks() const;
```

### <a name="return-value"></a>Rückgabewert

Die Taktanzahl, die den Beitrag dieser Aktivität zur Gesamtbetrachtungszeit darstellt. Ein Tick der tatsächlich verstrichenen Zeit unterscheidet sich von einem normalen Tick. Ticks der tatsächlich verstrichenen Zeit berücksichtigen Parallelität zwischen Aktivitäten. Zwei parallele Aktivitäten weisen eine Dauer von 50 Takten sowie dieselbe Start- und Endzeit auf. In diesem Fall wird beiden Aktivitäten eine Gesamtbetrachtungszeit von 25 Takten zugewiesen.

::: moniker-end
