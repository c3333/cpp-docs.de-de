---
title: Ereignisklasse
description: Die Referenz zur Event-Klasse im C++ Build Insights SDK.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Event
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 7dd96ffa3518c58e1b18312bb4fe2c36df26bd67
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "92923297"
---
# <a name="event-class"></a>Ereignisklasse

::: moniker range="<=msvc-140"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Wenn die Dokumentation für diese Versionen angezeigt werden soll, legen Sie das Steuerelement für die Auswahl der **Version** von Visual Studio für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich am Anfang des Inhaltsverzeichnisses auf dieser Seite.

::: moniker-end
::: moniker range=">=msvc-150"

Die `Event`-Klasse wird mit den Funktionen [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md) und [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) verwendet. Dient zum Abgleichen eines beliebigen Ereignisses.

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
[EventId](#event-id)\
[EventInstanceId](#event-instance-id)\
[EventName](#event-name)\
[EventWideName](#event-wide-name)\
[ProcessId](#process-id)\
[ProcessorIndex](#processor-index)\
[ThreadId](#thread-id)\
[TickFrequency](#tick-frequency)\
[Timestamp](#timestamp)

## <a name="event"></a><a name="entity"></a> -Ereignis

```cpp
Event(const RawEvent& event);
```

### <a name="parameters"></a>Parameter

*Ereignis*\
Beliebiges Ereignis.

## <a name="data"></a><a name="data"></a> Data

```cpp
const void* Data() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf zusätzliche Daten, die in diesem Ereignis enthalten sind. Weitere Informationen zum Interpretieren dieses Felds finden Sie unter [EVENT_DATA](../c-event-data-types/event-data-struct.md).

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

Eine Zahl, die das Ereignis innerhalb einer Ablaufverfolgung eindeutig identifiziert. Dieser Wert ändert sich nicht, wenn dieselbe Ablaufverfolgung mehrmals analysiert oder erneut protokolliert wird. Verwenden Sie dieses Feld, um ein und dasselbe Ereignis in mehreren Durchgängen derselben Ablaufverfolgung zur Analyse oder Neuprotokollierung zu identifizieren.

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

Eine Zeichenfolge mit breiten Zeichen mit dem Namen des durch [EventId](#event-id) identifizierten Ereignisses.

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

## <a name="timestamp"></a><a name="timestamp"></a> Timestamp

```cpp
const long long& Timestamp() const;
```

### <a name="return-value"></a>Rückgabewert

Wenn es sich bei dem Ereignis um eine Aktivität handelt, gibt diese Funktion einen Taktwert zurück, der zu Beginn der Aktivität erfasst wurde. Bei einem einfachen Ereignis gibt diese Funktion einen Taktwert zurück, der zum Zeitpunkt des Auftretens des Ereignisses erfasst wurde.

::: moniker-end
