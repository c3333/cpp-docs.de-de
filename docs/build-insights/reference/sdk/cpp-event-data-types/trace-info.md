---
title: TraceInfo-Klasse
description: Die Referenz zur TraceInfo-Klasse im C++ Build Insights SDK.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TraceInfo
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: b772cc13981720c73238e56a561ca92144775cb4
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "92922923"
---
# <a name="traceinfo-class"></a>TraceInfo-Klasse

::: moniker range="<=msvc-140"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Wenn die Dokumentation für diese Versionen angezeigt werden soll, legen Sie das Steuerelement für die Auswahl der **Version** von Visual Studio für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich am Anfang des Inhaltsverzeichnisses auf dieser Seite.

::: moniker-end
::: moniker range=">=msvc-150"

Die `TraceInfo`-Klasse dient zum Zugriff auf nützliche Eigenschaften zur analysierten oder neu protokollierten Ablaufverfolgung.

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

## <a name="remarks"></a>Hinweise

Subtrahieren Sie `StartTimestamp` von `StopTimestamp`, um die Anzahl der Takte zu erhalten, die während der gesamten Ablaufverfolgung verstrichen sind. Nutzen Sie `TickFrequency` zur Konvertierung des resultierenden Werts in eine Zeiteinheit. Ein Beispiel für das Konvertieren von Takten in Zeiteinheiten finden Sie unter [EVENT_DATA](../c-event-data-types/event-data-struct.md).

Wenn Sie Takte nicht selbst konvertieren möchten, stellt die `TraceInfo`-Klasse eine Memberfunktion bereit, die die Dauer der Ablaufverfolgung in Nanosekunden zurückgibt. Zur Umrechnung dieses Werts in andere Zeiteinheiten verwenden Sie die C++-Standardbibliothek `chrono`.

## <a name="members"></a>Member

### <a name="constructors"></a>Konstruktoren

[TraceInfo](#trace-info)

### <a name="functions"></a>Functions

[Duration](#duration)
[LogicalProcessorCount](#logical-processor-count)
[StartTimestamp](#start-timestamp)
[StopTimestamp](#stop-timestamp)
[TickFrequency](#tick-frequency)

## <a name="duration"></a><a name="duration"></a> Duration

```cpp
std::chrono::nanoseconds Duration() const;
```

### <a name="return-value"></a>Rückgabewert

Die Dauer dieser Aktivität in Nanosekunden.

## <a name="logicalprocessorcount"></a><a name="logical-processor-count"></a> LogicalProcessorCount

```cpp
const unsigned long& LogicalProcessorCount() const;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der logischen Prozessoren auf dem Computer, auf dem die Ablaufverfolgung erfasst wurde.

## <a name="starttimestamp"></a><a name="start-timestamp"></a> StartTimestamp

```cpp
const long long& StartTimestamp() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Taktwert, der zum Startzeitpunkt der Ablaufverfolgung aufgezeichnet wurde.

## <a name="stoptimestamp"></a><a name="stop-timestamp"></a> StopTimestamp

```cpp
const long long& StopTimestamp() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Taktwert, der zum Stoppzeitpunkt der Ablaufverfolgung aufgezeichnet wurde.

## <a name="tickfrequency"></a><a name="tick-frequency"></a> TickFrequency

```cpp
const long long& TickFrequency() const;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl von Ticks pro Sekunde, die beim Auswerten einer in Ticks gemessenen Dauer verwendet werden soll.

## <a name="traceinfo"></a><a name="trace-info"></a> TraceInfo

```cpp
TraceInfo(const TRACE_INFO_DATA& data);
```

### <a name="parameters"></a>Parameter

*data*\
Die Daten mit den Informationen zur Ablaufverfolgung.

::: moniker-end
