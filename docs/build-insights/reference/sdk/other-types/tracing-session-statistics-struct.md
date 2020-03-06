---
title: TRACING_SESSION_STATISTICS Struktur
description: Das C++ Build Insights SDK TRACING_SESSION_OPTIONS Struktur Referenz.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TRACING_SESSION_STATISTICS
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 9aa7c0a861d80fd3ebff85eb7ecb17dd05ae869e
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333863"
---
# <a name="tracing_session_statistics-structure"></a>TRACING_SESSION_STATISTICS Struktur

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist kompatibel mit Visual Studio 2017 und höher. Um die Dokumentation für diese Versionen anzuzeigen, legen Sie das Steuerelement für die Visual Studio-Versions Auswahl für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest.

::: moniker-end
::: moniker range=">=vs-2017"

Die `TRACING_SESSION_STATISTICS` Struktur beschreibt Statistiken für eine Ablauf Verfolgung, die erfasst wurde. Die Felder werden beim Beenden einer Ablauf Verfolgungs Sitzung festgelegt.

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

## <a name="members"></a>Members

|  |  |
|--|--|
| `MSVCEventsLost` | Die Anzahl der gelöschten MSVC-Ereignisse. |
| `MSVCBuffersLost` | Die Anzahl der gelöschten MSVC-Ereignis Puffer. |
| `SystemEventsLost` | Die Anzahl der gelöschten Systemereignisse. |
| `SystemBuffersLost` | Die Anzahl der gelöschten System Ereignis Puffer. |

## <a name="remarks"></a>Bemerkungen

Diese Struktur wird aufgefüllt, wenn die folgenden Funktionen aufgerufen werden:

- [Stoptracingsession](../functions/stop-tracing-session.md)
- [Stoptracingsessiona](../functions/stop-tracing-session-a.md)
- [Stoptracingsessionw](../functions/stop-tracing-session-w.md)
- [Stopandanalyzetracingsession](../functions/stop-and-analyze-tracing-session.md)
- [Stopandanalyzetracingsessiona](../functions/stop-and-analyze-tracing-session-a.md)
- [Stopandanalyzetracingsessionw](../functions/stop-and-analyze-tracing-session-w.md)
- [Stopandrelogtracingsession](../functions/stop-and-relog-tracing-session.md)
- [Stopandrelogtracingsessiona](../functions/stop-and-relog-tracing-session-a.md)
- [Stopandrelogtracingsessionw](../functions/stop-and-relog-tracing-session-w.md)

::: moniker-end
