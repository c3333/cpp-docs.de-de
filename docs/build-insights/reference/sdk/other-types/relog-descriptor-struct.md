---
title: RELOG_DESCRIPTOR-Struktur
description: Der Verweis auf die RELOG_DESCRIPTOR-Struktur im C++ Build Insights SDK.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- RELOG_DESCRIPTOR
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 9b3c870998ce4f9ca55fb5bcc23ba66a1af46558
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "92922434"
---
# <a name="relog_descriptor-structure"></a>RELOG_DESCRIPTOR-Struktur

::: moniker range="<=msvc-140"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Wenn die Dokumentation für diese Versionen angezeigt werden soll, legen Sie das Steuerelement für die Auswahl der **Version** von Visual Studio für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich am Anfang des Inhaltsverzeichnisses auf dieser Seite.

::: moniker-end
::: moniker range=">=msvc-150"

Die `RELOG_DESCRIPTOR`-Struktur wird mit den Funktionen [RelogA](../functions/relog-a.md) und [RelogW](../functions/relog-w.md) verwendet. Es wird beschrieben, wie eine Ereignisablaufverfolgung für Windows (Event Tracing for Windows, ETW) erneut protokolliert werden sollte.

## <a name="syntax"></a>Syntax

```cpp
typedef struct RELOG_DESCRIPTOR_TAG
{
    unsigned                NumberOfAnalysisPasses;
    ANALYSIS_CALLBACKS      AnalysisCallbacks;
    RELOG_CALLBACKS         RelogCallbacks;
    unsigned long long      SystemEventsRetentionFlags;
    void*                   AnalysisContext;
    void*                   RelogContext;
} RELOG_DESCRIPTOR;
```

## <a name="members"></a>Member

| name | BESCHREIBUNG |
|--|--|
| `NumberOfAnalysisPasses` | Die Anzahl von Analysedurchläufen, die während der Analysephase der Neuprotokollierungssitzung über die ETW-Ablaufverfolgung durchgeführt werden sollten. |
| `AnalysisCallbacks` | Ein [ANALYSIS_CALLBACKS](analysis-callbacks-struct.md)-Objekt, das angibt, welche Funktionen während der Analysephase der Neuprotokollierungssitzung aufgerufen werden sollen. |
| `RelogCallbacks` | Ein [RELOG_CALLBACKS](relog-callbacks-struct.md)-Objekt, das angibt, welche Funktionen während der Neuprotokollierungsphase der Neuprotokollierungssitzung aufgerufen werden sollen. |
| `SystemEventsRetentionFlags` | Eine [RELOG_RETENTION_SYSTEM_EVENT_FLAGS](relog-retention-system-event-flags-constants.md)-Bitmaske, die angibt, welche ETW-Systemereignisse in der erneut protokollierten Ablaufverfolgung aufbewahrt werden sollen. |
| `AnalysisContext` | Ein vom Benutzer bereitgestellter Kontext, der als Argument an alle in `AnalysisCallbacks` angegebenen Rückruffunktionen übermittelt wird. |
| `RelogContext` | Ein vom Benutzer bereitgestellter Kontext, der als Argument an alle in `RelogCallbacks` angegebenen Rückruffunktionen übermittelt wird. |

## <a name="remarks"></a>Bemerkungen

Die Neuprotokollierung von ETW-Ereignissen während einer Neuprotokollierungssitzung wird vom Benutzer über die in `RelogCallbacks` angegebenen Rückruffunktionen gesteuert. ETW-Systemereignisse wie z. B. CPU-Stichproben werden jedoch nicht an diese Rückruffunktionen weitergeleitet. Steuern Sie über das `SystemEventsRetentionFlags`-Feld die Neuprotokollierung von ETW-Systemereignissen.

Die `AnalysisCallbacks`- und `RelogCallbacks`-Struktur akzeptieren nur Zeiger auf Funktionen, die nicht Member sind. Sie können diese Einschränkung umgehen, indem Sie sie auf einen Objektzeiger festlegen. Dieser Objektzeiger wird als Argument an alle Rückruffunktionen übermittelt, die nicht Member sind. Rufen Sie mit diesem Zeiger Memberfunktionen von den Rückruffunktionen aus auf, die nicht Member sind.

Die Analysephase einer Neuprotokollierungssitzung wird immer vor der Neuprotokollierungsphase ausgeführt.

::: moniker-end
