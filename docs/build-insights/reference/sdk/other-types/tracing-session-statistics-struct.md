---
title: TRACING_SESSION_STATISTICS Struktur
description: Das C++ Build Insights SDK TRACING_SESSION_OPTIONS Strukturreferenz.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TRACING_SESSION_STATISTICS
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 96cff3a231fd515ec1c52a048b8350a63ba46a39
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323380"
---
# <a name="tracing_session_statistics-structure"></a>TRACING_SESSION_STATISTICS Struktur

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Um die Dokumentation zu diesen Versionen anzuzeigen, legen Sie das Visual **Studio-Versionsauswahlsteuerelement** für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich oben im Inhaltsverzeichnis auf dieser Seite.

::: moniker-end
::: moniker range=">=vs-2017"

Die `TRACING_SESSION_STATISTICS` Struktur beschreibt Statistiken über eine Spur, die gesammelt wurde. Seine Felder werden beim Beenden einer Ablaufverfolgungssitzung festgelegt.

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

|  |  |
|--|--|
| `MSVCEventsLost` | Die Anzahl der MSVC-Ereignisse, die gelöscht wurden. |
| `MSVCBuffersLost` | Die Anzahl der MSVC-Ereignispuffer, die gelöscht wurden. |
| `SystemEventsLost` | Die Anzahl der Systemereignisse, die gelöscht wurden. |
| `SystemBuffersLost` | Die Anzahl der Systemereignispuffer, die gelöscht wurden. |

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
