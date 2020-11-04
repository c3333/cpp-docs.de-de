---
title: RELOG_RETENTION_SYSTEM_EVENT_FLAGS-Konstanten
description: Der C++ Build Insights SDK-Verweis auf RELOG_RETENTION_SYSTEM_EVENT_FLAGS-Konstanten.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- RELOG_RETENTION_SYSTEM_EVENT_FLAGS
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: e0144835568dab12c8593fe8fbfa820f6cde7647
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "92919730"
---
# <a name="relog_retention_system_event_flags-constants"></a>RELOG_RETENTION_SYSTEM_EVENT_FLAGS-Konstanten

::: moniker range="<=msvc-140"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Wenn die Dokumentation für diese Versionen angezeigt werden soll, legen Sie das Steuerelement für die Auswahl der **Version** von Visual Studio für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich am Anfang des Inhaltsverzeichnisses auf dieser Seite.

::: moniker-end
::: moniker range=">=msvc-150"

Mit den `RELOG_RETENTION_SYSTEM_EVENT_FLAGS`-Konstanten wird beschrieben, welche Systemereignisse in einer erneut protokollierten Ablaufverfolgung beibehalten werden sollen. Initialisieren Sie mit ihnen das `SystemEventsRetentionFlags`-Feld der [RELOG_DESCRIPTOR](relog-descriptor-struct.md)-Struktur.

## <a name="syntax"></a>Syntax

```cpp
static const unsigned long long
    RELOG_RETENTION_SYSTEM_EVENT_FLAGS_CPU_SAMPLES = 0x1ULL;

static const unsigned long long
    RELOG_RETENTION_SYSTEM_EVENT_FLAGS_ALL         = 0xFFFFFFFFFFFFFFFFULL;
```

## <a name="members"></a>Member

| name | BESCHREIBUNG |
|--|--|
| `RELOG_RETENTION_SYSTEM_EVENT_FLAGS_CPU_SAMPLES` | Beibehalten von CPU-Beispielsystemereignissen in einer erneut protokollierten Ablaufverfolgung. |
| `RELOG_RETENTION_SYSTEM_EVENT_FLAGS_ALL` | Beibehalten aller Systemereignisse in einer erneut protokollierten Ablaufverfolgung. |

## <a name="remarks"></a>Bemerkungen

::: moniker-end
