---
title: Ereignisklasse
description: Der C++ Build Insights SDK-Ereignisverweis.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Event
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 25d58f642a1c314e48ddff62553394bcc65e4717
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324963"
---
# <a name="event-class"></a>Ereignisklasse

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Um die Dokumentation zu diesen Versionen anzuzeigen, legen Sie das Visual **Studio-Versionsauswahlsteuerelement** für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich oben im Inhaltsverzeichnis auf dieser Seite.

::: moniker-end
::: moniker range=">=vs-2017"

Die `Event` Klasse wird mit den Funktionen [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)und [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) verwendet. Verwenden Sie es, um jedem Ereignis zu entsprechen.

## <a name="syntax"></a>Syntax

```cpp
class Event
{
public:
    Event(const RawEvent& event);

    const unsigned short&        EventId() const;
    const unsigned long long&    EventInstanceId() const;
    const long long&             TickFrequency() const;
    const long long&             Timestamp() const;
    const unsigned long&         ProcessId() const;
    const unsigned long&         ThreadId() const;
    const unsigned short&        ProcessorIndex() const;
    const char*                  EventName() const;
    const wchar_t*               EventWideName() const;
};
```

## <a name="members"></a>Member

### <a name="constructors"></a>Konstruktoren

[Event](#entity)

### <a name="functions"></a>Functions

[Data](#data)
[Datenereignis-Id](#event-id)\
[EventInstanceId](#event-instance-id)\
[Eventname](#event-name)\
[EventWideName](#event-wide-name)\
[Processid](#process-id)\
[ProcessorIndex](#processor-index)\
[Threadid](#thread-id)\
[Tickfrequency](#tick-frequency)\
[Timestamp](#timestamp)

## <a name="event"></a><a name="entity"></a> -Ereignis

```cpp
Event(const RawEvent& event);
```

### <a name="parameters"></a>Parameter

*Ereignis*\
Jedes Ereignis.

## <a name="data"></a><a name="data"></a>Daten

```cpp
const void* Data() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf zusätzliche Daten, die in diesem Ereignis enthalten sind. Weitere Informationen zum Interpretieren dieses Felds finden Sie [unter EVENT_DATA](../c-event-data-types/event-data-struct.md).

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

Eine breite Zeichenfolge, die den Namen des von [EventId](#event-id)identifizierten Ereignisses enthält.

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

## <a name="timestamp"></a><a name="timestamp"></a>Timestamp

```cpp
const long long& Timestamp() const;
```

### <a name="return-value"></a>Rückgabewert

Wenn es sich bei dem Ereignis um eine Aktivität handelt, gibt diese Funktion einen Tickwert zurück, der zum Zeitpunkt des Startens der Aktivität erfasst wurde. Für ein einfaches Ereignis gibt diese Funktion einen Tick-Wert zurück, der zum Zeitpunkt des Auftretens des Ereignisses erfasst wurde.

::: moniker-end
