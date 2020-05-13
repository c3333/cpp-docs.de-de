---
title: RELOG_RETENTION_SYSTEM_EVENT_FLAGS Konstanten
description: Das C++ Build Insights SDK RELOG_RETENTION_SYSTEM_EVENT_FLAGS Konstantenreferenz.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- RELOG_RETENTION_SYSTEM_EVENT_FLAGS
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 7110f809a819357b31951c203c1fa6ac9fb9f42e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323475"
---
# <a name="relog_retention_system_event_flags-constants"></a>RELOG_RETENTION_SYSTEM_EVENT_FLAGS Konstanten

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Um die Dokumentation zu diesen Versionen anzuzeigen, legen Sie das Visual **Studio-Versionsauswahlsteuerelement** für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich oben im Inhaltsverzeichnis auf dieser Seite.

::: moniker-end
::: moniker range=">=vs-2017"

Die `RELOG_RETENTION_SYSTEM_EVENT_FLAGS` Konstanten werden verwendet, um zu beschreiben, welche Systemereignisse in einer erneut entopierten Ablaufverfolgung beibehalten werden sollen. Verwenden Sie sie, [RELOG_DESCRIPTOR](relog-descriptor-struct.md) um das `SystemEventsRetentionFlags` Feld der RELOG_DESCRIPTOR Struktur zu initialisieren.

## <a name="syntax"></a>Syntax

```cpp
static const unsigned long long
    RELOG_RETENTION_SYSTEM_EVENT_FLAGS_CPU_SAMPLES = 0x1ULL;

static const unsigned long long
    RELOG_RETENTION_SYSTEM_EVENT_FLAGS_ALL         = 0xFFFFFFFFFFFFFFFFULL;
```

## <a name="members"></a>Member

|  |  |
|--|--|
| `RELOG_RETENTION_SYSTEM_EVENT_FLAGS_CPU_SAMPLES` | Bewahren Sie CPU-Beispielsystemereignisse in einer erneut entosierten Ablaufverfolgung auf. |
| `RELOG_RETENTION_SYSTEM_EVENT_FLAGS_ALL` | Bewahren Sie alle Systemereignisse in einer erneuten Ablaufverfolgung auf. |

## <a name="remarks"></a>Bemerkungen

::: moniker-end
