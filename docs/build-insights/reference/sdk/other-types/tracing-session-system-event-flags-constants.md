---
title: TRACING_SESSION_SYSTEM_EVENT_FLAGS Konstanten
description: Der C++ Verweis auf das Build Insights SDK TRACING_SESSION_SYSTEM_EVENT_FLAGS Konstanten.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TRACING_SESSION_SYSTEM_EVENT_FLAGS
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: ce0b0ea373ec53f0d5bcf228269299d69b49bb95
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333995"
---
# <a name="tracing_session_system_event_flags-constants"></a>TRACING_SESSION_SYSTEM_EVENT_FLAGS Konstanten

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist kompatibel mit Visual Studio 2017 und höher. Um die Dokumentation für diese Versionen anzuzeigen, legen Sie das Steuerelement für die Visual Studio-Versions Auswahl für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest.

::: moniker-end
::: moniker range=">=vs-2017"

Die `TRACING_SESSION_SYSTEM_EVENT_FLAGS` Konstanten werden verwendet, um zu beschreiben, welche Systemereignisse während einer Ablauf Verfolgung erfasst werden sollen. Verwenden Sie diese, um das `SystemEventFlags` Feld der [TRACING_SESSION_OPTIONS](tracing-session-options-struct.md) Struktur zu initialisieren.

## <a name="syntax"></a>Syntax

```cpp
static const unsigned long long
    TRACING_SESSION_SYSTEM_EVENT_FLAGS_CONTEXT      = 0x1ULL;

static const unsigned long long
    TRACING_SESSION_SYSTEM_EVENT_FLAGS_CPU_SAMPLES  = 0x2ULL;

static const unsigned long long
    TRACING_SESSION_SYSTEM_EVENT_FLAGS_ALL          = 0xFFFFFFFFFFFFFFFFULL;
```

## <a name="members"></a>Members

| Name | Von diesem Flag aktivierten Ereignisse |
|--|--|
| `TRACING_SESSION_SYSTEM_EVENT_FLAGS_CONTEXT` | Dieses Flag wird standardmäßig vom C++ Build Insights SDK aktiviert, auch wenn es nicht explizit angegeben wurde. Es ermöglicht grundlegende Systemereignisse, die für C++ die ordnungsgemäße Funktion von Build Insights erforderlich sind. Die von diesem Flag aktivierten Ereignisse stellen Informationen zu Prozessen, Threads und zum Laden von Bildern bereit. Diese Ereignisse können nicht deaktiviert werden. |
| `TRACING_SESSION_SYSTEM_EVENT_FLAGS_CPU_SAMPLES` | CPU-Beispiele |
| `TRACING_SESSION_SYSTEM_EVENT_FLAGS_ALL` | Dieses Flag schaltet alle Systemereignisse ein. |

::: moniker-end
