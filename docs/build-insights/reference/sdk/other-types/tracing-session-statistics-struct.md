---
title: TRACING_SESSION_STATISTICS-Struktur
description: Hier finden Sie die Referenz zur TRACING_SESSION_OPTIONS-Struktur im C++ Build Insights SDK.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TRACING_SESSION_STATISTICS
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 7135c49bdf95ef5ba39db090c95ad46d266d8f65
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "92919656"
---
# <a name="tracing_session_statistics-structure"></a>TRACING_SESSION_STATISTICS-Struktur

::: moniker range="<=msvc-140"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Wenn die Dokumentation für diese Versionen angezeigt werden soll, legen Sie das Steuerelement für die Auswahl der **Version** von Visual Studio für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich am Anfang des Inhaltsverzeichnisses auf dieser Seite.

::: moniker-end
::: moniker range=">=msvc-150"

Die `TRACING_SESSION_STATISTICS`-Struktur beschreibt Statistiken für eine Ablaufverfolgung, die erfasst wurde. Die Felder werden beim Beenden einer Ablaufverfolgungssitzung festgelegt.

## <a name="syntax"></a>Syntax

```cpp
typedef struct TRACING_SESSION_STATISTICS_TAG
{
    unsigned long MSVCEventsLost;
    unsigned long MSVCBuffersLost;
    unsigned long SystemEventsLost;
    unsigned long SystemBuffersLost;

} TRACING_SESSION_STATISTICS;
```

## <a name="members"></a>Member

| name | BESCHREIBUNG |
|--|--|
| `MSVCEventsLost` | Die Anzahl der gelöschten MSVC-Ereignisse. |
| `MSVCBuffersLost` | Die Anzahl der gelöschten MSVC-Ereignispuffer. |
| `SystemEventsLost` | Die Anzahl der gelöschten Systemereignisse. |
| `SystemBuffersLost` | Die Anzahl der gelöschten Systemereignispuffer. |

## <a name="remarks"></a>Bemerkungen

Diese Struktur wird aufgefüllt, wenn die folgenden Funktionen aufgerufen werden:

- [StopTracingSession](../functions/stop-tracing-session.md)
- [StopTracingSessionA](../functions/stop-tracing-session-a.md)
- [StopTracingSessionW](../functions/stop-tracing-session-w.md)
- [StopAndAnalyzeTracingSession](../functions/stop-and-analyze-tracing-session.md)
- [StopAndAnalyzeTracingSessionA](../functions/stop-and-analyze-tracing-session-a.md)
- [StopAndAnalyzeTracingSessionW](../functions/stop-and-analyze-tracing-session-w.md)
- [StopAndRelogTracingSession](../functions/stop-and-relog-tracing-session.md)
- [StopAndRelogTracingSessionA](../functions/stop-and-relog-tracing-session-a.md)
- [StopAndRelogTracingSessionW](../functions/stop-and-relog-tracing-session-w.md)

::: moniker-end
