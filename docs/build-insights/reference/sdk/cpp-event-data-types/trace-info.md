---
title: TraceInfo-Klasse
description: Der C++ Build Insights SDK TraceInfo-Klassenverweis.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TraceInfo
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 75d53937e3999f5692dee0ecf419e0ce5f49a274
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324170"
---
# <a name="traceinfo-class"></a>TraceInfo-Klasse

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Um die Dokumentation zu diesen Versionen anzuzeigen, legen Sie das Visual **Studio-Versionsauswahlsteuerelement** für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich oben im Inhaltsverzeichnis auf dieser Seite.

::: moniker-end
::: moniker range=">=vs-2017"

Die `TraceInfo` Klasse wird verwendet, um auf nützliche Eigenschaften für eine Zuverfolgung zuzugreifen, die analysiert oder erneut protokolliert wird.

## <a name="syntax"></a>Syntax

```cpp
class TraceInfo
{
public:
    TraceInfo(const TRACE_INFO_DATA& data);

    const unsigned long& LogicalProcessorCount() const;

    const long long& TickFrequency() const;
    const long long& StartTimestamp() const;
    const long long& StopTimestamp() const;

    std::chrono::nanoseconds Duration() const;
};
```

## <a name="remarks"></a>Bemerkungen

Subtrahieren `StopTimestamp` Sie die, `StartTimestamp` um die Anzahl der Ticks zu erhalten, die während der gesamten Spur verstrichen sind. Verwenden `TickFrequency` Sie diese Datei, um den resultierenden Wert in eine Zeiteinheit zu konvertieren. Ein Beispiel für das Konvertieren von Ticks in die Zeit finden Sie unter [EVENT_DATA](../c-event-data-types/event-data-struct.md).

Wenn Sie Ticks nicht selbst konvertieren `TraceInfo` möchten, stellt die Klasse eine Memberfunktion bereit, die die Ablaufverfolgungsdauer in Nanosekunden zurückgibt. Verwenden Sie die `chrono` Standard-C++-Bibliothek, um diesen Wert in andere Zeiteinheiten zu konvertieren.

## <a name="members"></a>Member

### <a name="constructors"></a>Konstruktoren

[TraceInfo](#trace-info)

### <a name="functions"></a>Functions

[Dauer](#duration)
[LogicalProcessorCount](#logical-processor-count)
[StartTimestamp](#start-timestamp)
[StopTimestamp](#stop-timestamp)
[TickFrequency](#tick-frequency)

## <a name="duration"></a><a name="duration"></a>Dauer

```cpp
std::chrono::nanoseconds Duration() const;
```

### <a name="return-value"></a>Rückgabewert

Die Dauer der Aktivität in Nanosekunden.

## <a name="logicalprocessorcount"></a><a name="logical-processor-count"></a>LogicalProcessorCount

```cpp
const unsigned long& LogicalProcessorCount() const;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der logischen Prozessoren auf dem Computer, auf dem die Ablaufverfolgung erfasst wurde.

## <a name="starttimestamp"></a><a name="start-timestamp"></a>StartTimestamp

```cpp
const long long& StartTimestamp() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Tick-Wert, der zum Zeitpunkt des Startens der Ablaufverfolgung erfasst wurde.

## <a name="stoptimestamp"></a><a name="stop-timestamp"></a>StopTimestamp

```cpp
const long long& StopTimestamp() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Tick-Wert, der zum Zeitpunkt des Anhaltens der Ablaufverfolgung erfasst wurde.

## <a name="tickfrequency"></a><a name="tick-frequency"></a>Tickfrequency

```cpp
const long long& TickFrequency() const;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Ticks pro Sekunde, die bei der Auswertung einer in Ticks gemessenen Dauer verwendet werden sollen.

## <a name="traceinfo"></a><a name="trace-info"></a>TraceInfo

```cpp
TraceInfo(const TRACE_INFO_DATA& data);
```

### <a name="parameters"></a>Parameter

*Daten*\
Die Daten, die die Informationen über die Ablaufverfolgung enthalten.

::: moniker-end
