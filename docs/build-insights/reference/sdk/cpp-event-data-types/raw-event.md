---
title: Rawevent-Klasse
description: Die C++ rawevent-Klassenreferenz für das Build Insights SDK.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- RawEvent
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 4088920d6070e14d64ccd046238c1c49b2556ea1
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334601"
---
# <a name="rawevent-class"></a>Rawevent-Klasse

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist kompatibel mit Visual Studio 2017 und höher. Um die Dokumentation für diese Versionen anzuzeigen, legen Sie das Steuerelement für die Visual Studio-Versions Auswahl für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest.

::: moniker-end
::: moniker range=">=vs-2017"

Die `RawEvent`-Klasse wird verwendet, um ein allgemeines Ereignis in einem [Ereignis Stapel](event-stack.md)darzustellen.

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

Mehrere Element Funktionen in der `RawEvent`-Klasse geben eine Takt Anzahl zurück. C++Buildinsights verwendet den Windows-Leistungs Leistungswert als eine Quelle von Ticks. Eine Takt Anzahl muss mit einer Taktfrequenz verwendet werden, um Sie in eine Zeiteinheit wie Sekunden umzuwandeln. Die `TickFrequency` Member-Funktion kann aufgerufen werden, um die Taktfrequenz zu erhalten. Ein Beispiel zum Konvertieren von Ticks in eine Zeiteinheit finden Sie auf der Seite [EVENT_DATA](../c-event-data-types/event-data-struct.md#tick-conversion-example) .

Wenn Sie Ticks nicht selbst konvertieren möchten, stellt die `RawEvent`-Klasse Member-Funktionen bereit, die Zeit Werte in Nanosekunden zurückgeben. Konvertieren Sie Nanosekunden mithilfe der Standard C++ -`chrono` Bibliothek in andere Zeiteinheiten.

## <a name="members"></a>Members

### <a name="constructor"></a>Konstruktor

[Rawevent](#raw-event)

### <a name="functions"></a>Functions

[CPUTICKS](#cpu-ticks) -\
[Cputime](#cpu-time) -\
[Daten](#data)\
[Dauer](#duration)\
[EventID](#event-id)
[eventinstanceid](#event-instance-id)
[EventName](#event-name)\
[Eventwidename](#event-wide-name) -\
[Exclusivecputicks](#exclusive-cpu-ticks) -\
[Exclusivecputime](#exclusive-cpu-time) -\
[Exclusiveduration](#exclusive-duration) -\
[Exclusivedurationticks](#exclusive-duration-ticks) -\
[Exclusivewallclocktimeresponsibility](#exclusive-wall-clock-time-responsibility)\
[Exclusivewallclocktimeresponsibilityticks](#exclusive-wall-clock-time-responsibility-ticks)\
\ [ProcessID](#process-id)
[Processorindex](#processor-index) -\
[Starttimestamp](#start-timestamp) -\
[Stoptimestamp](#stop-timestamp) -\
[ThreadId](#thread-id)\
[TickFrequency](#tick-frequency) -\
[Wallclocktimeresponsibility](#wall-clock-time-responsibility)\
[Wallclocktimeresponsibilityticks](#wall-clock-time-responsibility-ticks)

## <a name="raw-event"></a>Rawevent

```cpp
RawEvent(const EVENT_DATA& data);
```

### <a name="parameters"></a>Parameter

*Ereignis*\
Die Ereignisdaten.

## <a name="cpu-ticks"></a>CPUTICKS

```cpp
const long long& CPUTicks() const;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der CPU-Ticks, die während dieser Aktivität aufgetreten sind. Ein CPU-Tick unterscheidet sich von einem regulären Tick. CPU-Ticks werden nur gezählt, wenn die CPU Code in einer Aktivität ausführt. CPU-Ticks werden nicht gezählt, wenn der der Aktivität zugeordnete Thread im Ruhezustand ist.

## <a name="cpu-time"></a>CPUTime

```cpp
std::chrono::nanoseconds CPUTime()() const;
```

### <a name="return-value"></a>Rückgabewert

Die Zeitspanne, in der die CPU Code in dieser Aktivität ausgeführt hat. Dieser Wert ist möglicherweise höher als die Dauer der Aktivität, wenn untergeordnete Aktivitäten in separaten Threads ausgeführt werden. Der Wert wird in Nanosekunden zurückgegeben.

## <a name="data"></a>Vorrats

```cpp
const void* Data() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf zusätzliche Daten, die in diesem Ereignis enthalten sind. Weitere Informationen zum Interpretieren dieses Felds finden Sie unter [EVENT_DATA](../c-event-data-types/event-data-struct.md).

## <a name="duration"></a>Auf

```cpp
std::chrono::nanoseconds Duration() const;
```

### <a name="return-value"></a>Rückgabewert

Die Dauer der Aktivität in Nanosekunden.

## <a name="event-id"></a>EventID

```cpp
const unsigned short& EventId() const;
```

### <a name="return-value"></a>Rückgabewert

Eine Zahl, die den Ereignistyp identifiziert. Eine Liste der Ereignis Bezeichner finden Sie unter [event_id](../c-event-data-types/event-id-enum.md).

## <a name="event-instance-id"></a>Eventinstanceid

```cpp
const unsigned long long& EventInstanceId() const;
```

### <a name="return-value"></a>Rückgabewert

Eine Zahl, die das Ereignis innerhalb einer Ablauf Verfolgung eindeutig identifiziert. Dieser Wert ändert sich nicht, wenn dieselbe Ablauf Verfolgung mehrmals analysiert oder neu protokolliert wird. Verwenden Sie diesen Wert, um das gleiche Ereignis in mehreren Analysen zu identifizieren oder die erneute Protokollierung über dieselbe Ablauf Verfolgung durchzuführen.

## <a name="event-name"></a>EventName

```cpp
const char* EventName() const;
```

### <a name="return-value"></a>Rückgabewert

Eine ANSI-Zeichenfolge, die den Namen des von [EventID](#event-id)identifizierten Ereignis Typs enthält.

## <a name="event-wide-name"></a>Eventwidename

```cpp
const wchar_t* EventWideName() const;
```

### <a name="return-value"></a>Rückgabewert

Eine Breite Zeichenfolge, die den Namen des von [EventID](#event-id)identifizierten Ereignis Typs enthält.

## <a name="exclusive-cpu-ticks"></a>Exclusivecputicks

```cpp
const long long& ExclusiveCPUTicks() const;
```

### <a name="return-value"></a>Rückgabewert

Identisch mit [CPUTICKS](#cpu-ticks), aber nicht mit den CPU-Ticks, die in untergeordneten Aktivitäten aufgetreten sind.

## <a name="exclusive-cpu-time"></a>Exclusivecputime

```cpp
std::chrono::nanoseconds ExclusiveCPUTime() const;
```

### <a name="return-value"></a>Rückgabewert

Identisch mit [cputime](#cpu-time), mit dem Unterschied, dass die CPU-Zeit von untergeordneten Aktivitäten nicht berücksichtigt wird.

## <a name="exclusive-duration"></a>Exclusiveduration

```cpp
std::chrono::nanoseconds ExclusiveDuration() const;
```

### <a name="return-value"></a>Rückgabewert

Die Dauer der Aktivität in Nanosekunden, ohne die Zeitspanne, die für untergeordnete Aktivitäten aufgewendet wurde.

## <a name="exclusive-duration-ticks"></a>Exclusivedurationticks

```cpp
const long long& ExclusiveDurationTicks() const;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Ticks, die in dieser Aktivität aufgetreten sind, ohne die Anzahl der Ticks, die in untergeordneten Aktivitäten aufgetreten sind.

## <a name="exclusive-wall-clock-time-responsibility"></a>Exclusivewallclocktimeresponsibility

```cpp
std::chrono::nanoseconds ExclusiveWallClockTimeResponsibility() const;
```

### <a name="return-value"></a>Rückgabewert

Identisch mit der " [wallclocktimeresponsibility](#wall-clock-time-responsibility)", aber nicht mit der Zeit für untergeordnete Aktivitäten.

## <a name="exclusive-wall-clock-time-responsibility-ticks"></a>Exclusivewallclocktimeresponsibilityticks

```cpp
const long long& ExclusiveWallClockTimeResponsibilityTicks() const;
```

### <a name="return-value"></a>Rückgabewert

Identisch mit " [wallclocktimeresponsibilityticks](#wall-clock-time-responsibility-ticks)", aber nicht mit den Zeiteinheiten für die Zeit, die für untergeordnete Aktivitäten zuständig sind.

## <a name="process-id"></a>ProcessID

```cpp
const unsigned long& ProcessId() const;
```

### <a name="return-value"></a>Rückgabewert

Der Bezeichner für den Prozess, in dem das Ereignis aufgetreten ist.

## <a name="processor-index"></a>Processorindex

```cpp
const unsigned short& ProcessorIndex() const;
```

### <a name="return-value"></a>Rückgabewert

Der null basierte Index für den logischen Prozessor, auf dem das Ereignis aufgetreten ist.

## <a name="start-timestamp"></a>Starttimestamp

```cpp
const long long& StartTimestamp() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Teil Strich Wert, der zum Zeitpunkt der Aktivitäts Beginn aufgezeichnet wurde.

## <a name="stop-timestamp"></a>Stoptimestamp

```cpp
const long long& StopTimestamp() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Tick-Wert, der zum Zeitpunkt der Beendigung der Aktivität aufgezeichnet wurde.

## <a name="thread-id"></a>ThreadID

```cpp
const unsigned long& ThreadId() const;
```

### <a name="return-value"></a>Rückgabewert

Der Bezeichner für den Thread, in dem das Ereignis aufgetreten ist.

## <a name="tick-frequency"></a>TickFrequency

```cpp
const long long& TickFrequency() const;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Ticks pro Sekunde, die verwendet werden sollen, wenn eine in Ticks für dieses Ereignis gemessene Dauer ausgewertet wird.

## <a name="wall-clock-time-responsibility"></a>Wallclocktimeresponsibility

```cpp
std::chrono::nanoseconds WallClockTimeResponsibility() const;
```

### <a name="return-value"></a>Rückgabewert

Die Zeit in Nanosekunden, die für diese Aktivität verantwortlich ist. Weitere Informationen zur Bedeutung von "Wall-Clock Time Responsibility" finden Sie unter " [wallclocktimeresponsibilityticks](#wall-clock-time-responsibility-ticks)".

## <a name="wall-clock-time-responsibility-ticks"></a>Wallclocktimeresponsibilityticks

```cpp
const long long& WallClockTimeResponsibilityTicks() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Tick-Zähler, der den Beitrag dieser Aktivität zur Gesamtzeit der Gesamtzeit darstellt. Der Takt der Aufgaben für die Wand Zeit unterscheidet sich von einem regulären Tick. Bei der Zeit, in der die Zeit für die Zeit in der Arbeit berücksichtigt wird Zwei parallele Aktivitäten können über eine Dauer von 50 Ticks und dieselbe Start-und Endzeit verfügen. In diesem Fall wird für beide die Aufgabe "Wall-Clock-Zeit" von 25 Ticks zugewiesen.

::: moniker-end
