---
title: TRACE_INFO_DATA Struktur
description: Das C++ Build Insights SDK TRACE_INFO_DATA Struktur Referenz.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TRACE_INFO_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 04cb5c013bca8879507983d169b38e5af0f1322b
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2020
ms.locfileid: "78335051"
---
# <a name="trace_info_data-structure"></a>TRACE_INFO_DATA Struktur

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist kompatibel mit Visual Studio 2017 und höher. Um die Dokumentation für diese Versionen anzuzeigen, legen Sie das Steuerelement für die Visual Studio-Versions Auswahl für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest.

::: moniker-end
::: moniker range=">=vs-2017"

Die `TRACE_INFO_DATA` Struktur beschreibt, wie eine Ablauf Verfolgung analysiert oder erneut protokolliert wird.

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

## <a name="members"></a>Members

|  |  |
|--|--|
| `LogicalProcessorCount` | Die Anzahl der logischen Prozessoren auf dem Computer, auf dem die Ablauf Verfolgung erfasst wurde. |
| `TickFrequency` | Die Anzahl der Ticks pro Sekunde, die verwendet werden sollen, wenn eine in Ticks gemessene Dauer ausgewertet wird. |
| `StartTimestamp` | Dieses Feld ist auf einen Teil Strich Wert festgelegt, der zum Zeitpunkt der Ablauf Verfolgung aufgezeichnet wurde. |
| `StopTimestamp` | Dieses Feld ist auf einen Teil Strich Wert festgelegt, der zum Zeitpunkt der Beendigung der Ablauf Verfolgung aufgezeichnet wurde. |

## <a name="remarks"></a>Bemerkungen

Subtrahieren Sie `StartTimestamp` von `StopTimestamp`, um die Anzahl der Ticks zu erhalten, die während der gesamten Ablauf Verfolgung verstri Verwenden Sie `TickFrequency`, um den resultierenden Wert in eine Zeiteinheit zu konvertieren. Ein Beispiel für das Konvertieren von Ticks in Zeiteinheiten finden Sie unter [EVENT_DATA](event-data-struct.md).

::: moniker-end
