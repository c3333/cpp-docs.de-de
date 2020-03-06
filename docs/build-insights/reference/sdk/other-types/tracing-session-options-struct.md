---
title: TRACING_SESSION_OPTIONS Struktur
description: Das C++ Build Insights SDK TRACING_SESSION_OPTIONS Struktur Referenz.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TRACING_SESSION_OPTIONS
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 3f02552d5df4ffe71bc4be5c46e4b5239f25d73c
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333869"
---
# <a name="tracing_session_options-structure"></a>TRACING_SESSION_OPTIONS Struktur

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist kompatibel mit Visual Studio 2017 und höher. Um die Dokumentation für diese Versionen anzuzeigen, legen Sie das Steuerelement für die Visual Studio-Versions Auswahl für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest.

::: moniker-end
::: moniker range=">=vs-2017"

Die `TRACING_SESSION_OPTIONS`-Struktur wird beim Initialisieren einer [ANALYSIS_DESCRIPTOR](analysis-descriptor-struct.md) -oder [RELOG_DESCRIPTOR](relog-descriptor-struct.md) -Struktur verwendet. Es wird beschrieben, welche Ereignisse während der Sammlung einer Ablauf Verfolgung erfasst werden müssen.

## <a name="syntax"></a>Syntax

```cpp
typedef struct TRACING_SESSION_OPTIONS_TAG
{
    unsigned long long SystemEventFlags;
    unsigned long long MsvcEventFlags;

} TRACING_SESSION_OPTIONS;
```

## <a name="members"></a>Members

|  |  |
|--|--|
| `SystemEventFlags` | Eine Bitmaske, die die zu erfassenden Systemereignisse beschreibt. Weitere Informationen finden Sie unter [TRACING_SESSION_SYSTEM_EVENT_FLAGS](tracing-session-system-event-flags-constants.md). |
| `MsvcEventFlags` | Eine Bitmaske, die die zu erfassenden MSVC-Ereignisse beschreibt. Weitere Informationen finden Sie unter [TRACING_SESSION_MSVC_EVENT_FLAGS](tracing-session-msvc-event-flags-constants.md). |

::: moniker-end
