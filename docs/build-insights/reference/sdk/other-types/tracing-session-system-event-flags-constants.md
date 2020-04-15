---
title: TRACING_SESSION_SYSTEM_EVENT_FLAGS Konstanten
description: Das C++ Build Insights SDK TRACING_SESSION_SYSTEM_EVENT_FLAGS Konstantenreferenz.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TRACING_SESSION_SYSTEM_EVENT_FLAGS
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 264d697cc905eb6b44c8ec7de835a552976f0eb8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323270"
---
# <a name="tracing_session_system_event_flags-constants"></a>TRACING_SESSION_SYSTEM_EVENT_FLAGS Konstanten

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Um die Dokumentation zu diesen Versionen anzuzeigen, legen Sie das Visual **Studio-Versionsauswahlsteuerelement** für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich oben im Inhaltsverzeichnis auf dieser Seite.

::: moniker-end
::: moniker range=">=vs-2017"

Die `TRACING_SESSION_SYSTEM_EVENT_FLAGS` Konstanten werden verwendet, um zu beschreiben, welche Systemereignisse während einer Ablaufverfolgung gesammelt werden sollen. Verwenden Sie sie, [TRACING_SESSION_OPTIONS](tracing-session-options-struct.md) um das `SystemEventFlags` Feld der TRACING_SESSION_OPTIONS Struktur zu initialisieren.

## <a name="syntax"></a>Syntax

```cpp
static const unsigned long long
    TRACING_SESSION_SYSTEM_EVENT_FLAGS_CONTEXT      = 0x1ULL;

static const unsigned long long
    TRACING_SESSION_SYSTEM_EVENT_FLAGS_CPU_SAMPLES  = 0x2ULL;

static const unsigned long long
    TRACING_SESSION_SYSTEM_EVENT_FLAGS_ALL          = 0xFFFFFFFFFFFFFFFFULL;
```

## <a name="members"></a>Member

| Name | Ereignisse, die von dieser Flagge aktiviert wurden |
|--|--|
| `TRACING_SESSION_SYSTEM_EVENT_FLAGS_CONTEXT` | Dieses Flag wird standardmäßig vom C++ Build Insights SDK aktiviert, auch wenn es nicht explizit angegeben ist. Es ermöglicht grundlegende Systemereignisse, die von C++ Build Insights benötigt werden, ordnungsgemäß zu funktionieren. Die durch dieses Flag aktivierten Ereignisse enthalten Informationen zu Prozessen, Threads und dem Laden von Bildern. Sie können diese Ereignisse nicht deaktivieren. |
| `TRACING_SESSION_SYSTEM_EVENT_FLAGS_CPU_SAMPLES` | CPU-Beispiele |
| `TRACING_SESSION_SYSTEM_EVENT_FLAGS_ALL` | Dieses Flag aktiviert alle Systemereignisse. |

::: moniker-end
