---
title: RELOG_RETENTION_SYSTEM_EVENT_FLAGS Konstanten
description: Der C++ Verweis auf das Build Insights SDK RELOG_RETENTION_SYSTEM_EVENT_FLAGS Konstanten.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- RELOG_RETENTION_SYSTEM_EVENT_FLAGS
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 74afc10faa26ba39a669a05aa3e3cabd1a211293
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333965"
---
# <a name="relog_retention_system_event_flags-constants"></a>RELOG_RETENTION_SYSTEM_EVENT_FLAGS Konstanten

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist kompatibel mit Visual Studio 2017 und höher. Um die Dokumentation für diese Versionen anzuzeigen, legen Sie das Steuerelement für die Visual Studio-Versions Auswahl für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest.

::: moniker-end
::: moniker range=">=vs-2017"

Die `RELOG_RETENTION_SYSTEM_EVENT_FLAGS` Konstanten werden verwendet, um zu beschreiben, welche Systemereignisse in einer erneut protokollierten Ablauf Verfolgung aufbewahrt werden sollen. Verwenden Sie diese, um das `SystemEventsRetentionFlags` Feld der [RELOG_DESCRIPTOR](relog-descriptor-struct.md) Struktur zu initialisieren.

## <a name="syntax"></a>Syntax

```cpp
static const unsigned long long
    RELOG_RETENTION_SYSTEM_EVENT_FLAGS_CPU_SAMPLES = 0x1ULL;

static const unsigned long long
    RELOG_RETENTION_SYSTEM_EVENT_FLAGS_ALL         = 0xFFFFFFFFFFFFFFFFULL;
```

## <a name="members"></a>Members

|  |  |
|--|--|
| `RELOG_RETENTION_SYSTEM_EVENT_FLAGS_CPU_SAMPLES` | Behalten Sie die CPU-Beispiel Systemereignisse in einer erneut protokollierten Ablauf Verfolgung. |
| `RELOG_RETENTION_SYSTEM_EVENT_FLAGS_ALL` | Behalten Sie alle Systemereignisse in einer erneut protokollierten Ablauf Verfolgung bei. |

## <a name="remarks"></a>Bemerkungen

::: moniker-end
