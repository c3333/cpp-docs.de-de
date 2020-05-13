---
title: TRACE_INFO_DATA Struktur
description: Das C++ Build Insights SDK TRACE_INFO_DATA Strukturreferenz.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TRACE_INFO_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 70ae17a376f79cad7a669d81e482f551afd0ec62
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325278"
---
# <a name="trace_info_data-structure"></a>TRACE_INFO_DATA Struktur

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Um die Dokumentation zu diesen Versionen anzuzeigen, legen Sie das Visual **Studio-Versionsauswahlsteuerelement** für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich oben im Inhaltsverzeichnis auf dieser Seite.

::: moniker-end
::: moniker range=">=vs-2017"

Die `TRACE_INFO_DATA` Struktur beschreibt eine Spur, die analysiert oder neu protokolliert wird.

## <a name="syntax"></a>Syntax

```cpp
typedef struct TRACE_INFO_DATA_TAG
{
    unsigned long           LogicalProcessorCount;
    long long               TickFrequency;
    long long               StartTimestamp;
    long long               StopTimestamp;

} TRACE_INFO_DATA;
```

## <a name="members"></a>Member

|  |  |
|--|--|
| `LogicalProcessorCount` | Die Anzahl der logischen Prozessoren auf dem Computer, auf dem die Ablaufverfolgung erfasst wurde. |
| `TickFrequency` | Die Anzahl der Ticks pro Sekunde, die bei der Auswertung einer in Ticks gemessenen Dauer verwendet werden sollen. |
| `StartTimestamp` | Dieses Feld wird auf einen Tick-Wert festgelegt, der zum Zeitpunkt des Startens der Ablaufverfolgung erfasst wurde. |
| `StopTimestamp` | Dieses Feld wird auf einen Tick-Wert festgelegt, der zum Zeitpunkt des Anhaltens der Ablaufverfolgung erfasst wurde. |

## <a name="remarks"></a>Bemerkungen

Subtrahieren Sie `StartTimestamp` von, `StopTimestamp` um die Anzahl der Ticks zu erhalten, die während der gesamten Spur verstrichen sind. Verwenden `TickFrequency` Sie diese Datei, um den resultierenden Wert in eine Zeiteinheit zu konvertieren. Ein Beispiel, das Ticks in Zeiteinheiten konvertiert, finden Sie [unter EVENT_DATA](event-data-struct.md).

::: moniker-end
