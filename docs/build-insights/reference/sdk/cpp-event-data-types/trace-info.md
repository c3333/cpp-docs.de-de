---
title: Traceingefo-Klasse
description: Die C++ Referenz zum Build Insights SDK TraceInfo-Klasse.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TraceInfo
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 5cf32c8dc954a803a11888231d35b1050ac81cc3
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334499"
---
# <a name="traceinfo-class"></a>Traceingefo-Klasse

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist kompatibel mit Visual Studio 2017 und höher. Um die Dokumentation für diese Versionen anzuzeigen, legen Sie das Steuerelement für die Visual Studio-Versions Auswahl für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest.

::: moniker-end
::: moniker range=">=vs-2017"

Die `TraceInfo`-Klasse wird verwendet, um auf nützliche Eigenschaften über eine zu analysierende oder erneut protokollierte Ablauf Verfolgung zuzugreifen.

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

Ziehen Sie die `StartTimestamp` von `StopTimestamp` ab, um die Anzahl der Ticks zu erhalten, die während der gesamten Ablauf Verfolgung verstrichen sind Verwenden Sie `TickFrequency`, um den resultierenden Wert in eine Zeiteinheit zu konvertieren. Ein Beispiel für die Umstellung von Ticks in Time finden Sie unter [EVENT_DATA](../c-event-data-types/event-data-struct.md).

Wenn Sie Ticks nicht selbst konvertieren möchten, stellt die `TraceInfo`-Klasse eine Member-Funktion bereit, die die Ablauf Verfolgungs Dauer in Nanosekunden zurückgibt. Konvertieren Sie diesen C++ Wert mit der Standard-`chrono` Bibliothek in andere Zeiteinheiten.

## <a name="members"></a>Members

### <a name="constructors"></a>Konstruktoren

[Traceingefo](#trace-info)

### <a name="functions"></a>Functions

[Dauer](#duration)
[logicalprocessorcount](#logical-processor-count)
[starttimestamp](#start-timestamp)
[stoptimestamp](#stop-timestamp)
[TickFrequency](#tick-frequency)

## <a name="duration"></a>Auf

```cpp
std::chrono::nanoseconds Duration() const;
```

### <a name="return-value"></a>Rückgabewert

Die Dauer der Aktivität in Nanosekunden.

## <a name="logical-processor-count"></a>Logicalprocessorcount

```cpp
const unsigned long& LogicalProcessorCount() const;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der logischen Prozessoren auf dem Computer, auf dem die Ablauf Verfolgung erfasst wurde.

## <a name="start-timestamp"></a>Starttimestamp

```cpp
const long long& StartTimestamp() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Tick-Wert, der zum Zeitpunkt der Ablauf Verfolgung aufgezeichnet wurde.

## <a name="stop-timestamp"></a>Stoptimestamp

```cpp
const long long& StopTimestamp() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Tick-Wert, der zum Zeitpunkt der Beendigung der Ablauf Verfolgung aufgezeichnet wurde.

## <a name="tick-frequency"></a>TickFrequency

```cpp
const long long& TickFrequency() const;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Ticks pro Sekunde, die verwendet werden sollen, wenn eine in Ticks gemessene Dauer ausgewertet wird.

## <a name="trace-info"></a>Traceingefo

```cpp
TraceInfo(const TRACE_INFO_DATA& data);
```

### <a name="parameters"></a>Parameter

*Daten*\
Die Daten, die die Informationen zur Ablauf Verfolgung enthalten.

::: moniker-end
