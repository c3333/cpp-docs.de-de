---
title: TRACE_INFO_DATA-Struktur
description: Der Verweis auf die TRACE_INFO_DATA-Struktur im C++ Build Insights SDK.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TRACE_INFO_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: ce6301b168aed9f279fc7aaee9aa3a97221fd23a
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "92923425"
---
# <a name="trace_info_data-structure"></a>TRACE_INFO_DATA-Struktur

::: moniker range="<=msvc-140"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Wenn die Dokumentation für diese Versionen angezeigt werden soll, legen Sie das Steuerelement für die Auswahl der **Version** von Visual Studio für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich am Anfang des Inhaltsverzeichnisses auf dieser Seite.

::: moniker-end
::: moniker range=">=msvc-150"

Die `TRACE_INFO_DATA`-Struktur beschreibt, wie eine Ablaufverfolgung analysiert oder erneut protokolliert wird.

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

| name | BESCHREIBUNG |
|--|--|
| `LogicalProcessorCount` | Die Anzahl der logischen Prozessoren auf dem Computer, auf dem die Ablaufverfolgung erfasst wurde. |
| `TickFrequency` | Die Anzahl von Ticks pro Sekunde, die beim Auswerten einer in Ticks gemessenen Dauer verwendet werden soll. |
| `StartTimestamp` | Dieses Feld ist auf einen Taktwert festgelegt, der zum Startzeitpunkt der Ablaufverfolgung aufgezeichnet wurde. |
| `StopTimestamp` | Dieses Feld ist auf einen Taktwert festgelegt, der zum Stoppzeitpunkt der Ablaufverfolgung aufgezeichnet wurde. |

## <a name="remarks"></a>Bemerkungen

Subtrahieren Sie `StartTimestamp` von `StopTimestamp`, um die Anzahl der Takte zu erhalten, die während der gesamten Ablaufverfolgung verstrichen sind. Nutzen Sie `TickFrequency` zur Konvertierung des resultierenden Werts in eine Zeiteinheit. Ein Beispiel für das Konvertieren von Takten in Zeiteinheiten finden Sie unter [EVENT_DATA](event-data-struct.md).

::: moniker-end
