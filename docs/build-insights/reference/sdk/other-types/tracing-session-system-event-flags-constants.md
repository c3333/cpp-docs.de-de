---
title: TRACING_SESSION_SYSTEM_EVENT_FLAGS-Konstanten
description: Die Referenz zu den TRACING_SESSION_SYSTEM_EVENT_FLAGS-Konstanten im C++ Build Insights SDK.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TRACING_SESSION_SYSTEM_EVENT_FLAGS
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 346c955355ffbc6c062a34bf928f16ccd3940154
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "92922371"
---
# <a name="tracing_session_system_event_flags-constants"></a>TRACING_SESSION_SYSTEM_EVENT_FLAGS-Konstanten

::: moniker range="<=msvc-140"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Wenn die Dokumentation für diese Versionen angezeigt werden soll, legen Sie das Steuerelement für die Auswahl der **Version** von Visual Studio für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich am Anfang des Inhaltsverzeichnisses auf dieser Seite.

::: moniker-end
::: moniker range=">=msvc-150"

Mit den `TRACING_SESSION_SYSTEM_EVENT_FLAGS`-Konstanten wird beschrieben, welche Systemereignisse bei einer Ablaufverfolgung gesammelt werden sollen. Initialisieren Sie mit ihnen das Feld `SystemEventFlags` der [RELOG_DESCRIPTOR](tracing-session-options-struct.md)-Struktur.

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

| name | Von diesem Flag aktivierte Ereignisse |
|--|--|
| `TRACING_SESSION_SYSTEM_EVENT_FLAGS_CONTEXT` | Dieses Flag wird vom C++ Build Insights SDK. standardmäßig aktiviert, auch wenn es nicht explizit angegeben wird. Es ermöglicht, dass grundlegende Systemereignisse, die von C++ Build Insights benötigt werden, ordnungsgemäß funktionieren. Die durch dieses Flag aktivierten Ereignisse liefern Informationen über Prozesse, Threads und das Laden von Images. Diese Ereignisse können nicht deaktiviert werden. |
| `TRACING_SESSION_SYSTEM_EVENT_FLAGS_CPU_SAMPLES` | CPU-Stichproben |
| `TRACING_SESSION_SYSTEM_EVENT_FLAGS_ALL` | Dieses Flag aktiviert alle Systemereignisse. |

::: moniker-end
