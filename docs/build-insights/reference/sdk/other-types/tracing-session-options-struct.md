---
title: TRACING_SESSION_OPTIONS-Struktur
description: Der Verweis auf die TRACING_SESSION_OPTIONS-Struktur im C++ Build Insights SDK.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TRACING_SESSION_OPTIONS
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: c8a248d884b5232fbc5332db1a68533220ef2fab
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/12/2020
ms.locfileid: "90041262"
---
# <a name="tracing_session_options-structure"></a>TRACING_SESSION_OPTIONS-Struktur

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Wenn die Dokumentation für diese Versionen angezeigt werden soll, legen Sie das Steuerelement für die Auswahl der **Version** von Visual Studio für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich am Anfang des Inhaltsverzeichnisses auf dieser Seite.

::: moniker-end
::: moniker range=">=vs-2017"

Die `TRACING_SESSION_OPTIONS`-Struktur wird beim Initialisieren einer [ANALYSIS_DESCRIPTOR](analysis-descriptor-struct.md)- oder [RELOG_DESCRIPTOR](relog-descriptor-struct.md)-Struktur verwendet. Sie beschreibt, welche Ereignisse während der Erfassung einer Ablaufverfolgung erfasst werden müssen.

## <a name="syntax"></a>Syntax

```cpp
typedef struct TRACING_SESSION_OPTIONS_TAG
{
    unsigned long long SystemEventFlags;
    unsigned long long MsvcEventFlags;

} TRACING_SESSION_OPTIONS;
```

## <a name="members"></a>Member

| name | BESCHREIBUNG |
|--|--|
| `SystemEventFlags` | Eine Bitmaske, die die zu erfassenden Systemereignisse beschreibt. Weitere Informationen finden Sie unter [TRACING_SESSION_SYSTEM_EVENT_FLAGS](tracing-session-system-event-flags-constants.md). |
| `MsvcEventFlags` | Eine Bitmaske, die die zu erfassenden MSVC-Ereignisse beschreibt. Weitere Informationen finden Sie unter [TRACING_SESSION_MSVC_EVENT_FLAGS](tracing-session-msvc-event-flags-constants.md). |

::: moniker-end
