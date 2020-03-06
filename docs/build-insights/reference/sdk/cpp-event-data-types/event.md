---
title: Ereignisklasse
description: Die C++ Build Insights SDK-Ereignis Klassenreferenz.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Event
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 205a4e0ca9dd9449933f38f02d4ceafd5df8ead2
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334889"
---
# <a name="event-class"></a>Ereignisklasse

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist kompatibel mit Visual Studio 2017 und höher. Um die Dokumentation für diese Versionen anzuzeigen, legen Sie das Steuerelement für die Visual Studio-Versions Auswahl für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest.

::: moniker-end
::: moniker range=">=vs-2017"

Die `Event`-Klasse wird mit den Funktionen [matchevent](../functions/match-event.md), [matcheventinmitgliedfunction](../functions/match-event-in-member-function.md), [matcheventstack](../functions/match-event-stack.md)und [matcheventstackinmembership Function](../functions/match-event-stack-in-member-function.md) verwendet. Verwenden Sie es, um eine Entsprechung für jedes beliebige Ereignis

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

## <a name="members"></a>Members

### <a name="constructors"></a>Konstruktoren

[Event](#entity)

### <a name="functions"></a>Functions

[Daten](#data)
[EventID-](#event-id)\
[Eventinstanceid](#event-instance-id)\
[Ereignis Name](#event-name)\
[Eventwidename](#event-wide-name) -\
\ [ProcessID](#process-id)
[Processorindex](#processor-index) -\
[ThreadId](#thread-id)\
[TickFrequency](#tick-frequency) -\
[Timestamp](#timestamp)

## <a name="entity"></a>Veranstalter

```cpp
Event(const RawEvent& event);
```

### <a name="parameters"></a>Parameter

*Ereignis*\
Beliebiges Ereignis.

## <a name="data"></a>Vorrats

```cpp
const void* Data() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf zusätzliche Daten, die in diesem Ereignis enthalten sind. Weitere Informationen zum Interpretieren dieses Felds finden Sie unter [EVENT_DATA](../c-event-data-types/event-data-struct.md).

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

Eine Breite Zeichenfolge, die den Namen des von [EventID](#event-id)identifizierten Ereignisses enthält.

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

## <a name="timestamp"></a>Zeitstempel

```cpp
const long long& Timestamp() const;
```

### <a name="return-value"></a>Rückgabewert

Wenn es sich bei dem Ereignis um eine Aktivität handelt, gibt diese Funktion einen Tick-Wert zurück, der zum Zeitpunkt der Aktivitäts Starts aufgezeichnet wurde. Bei einem einfachen Ereignis gibt diese Funktion einen Tick-Wert zurück, der zum Zeitpunkt des Auftretens des Ereignisses erfasst wurde.

::: moniker-end
