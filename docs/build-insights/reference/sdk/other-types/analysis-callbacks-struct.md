---
title: ANALYSIS_CALLBACKS Struktur
description: Das C++ Build Insights SDK ANALYSIS_CALLBACKS Strukturreferenz.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- ANALYSIS_CALLBACKS
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 3c6de999b19657f999f884075ee53e21a4d2f2b5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323513"
---
# <a name="analysis_callbacks-structure"></a>ANALYSIS_CALLBACKS Struktur

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Um die Dokumentation zu diesen Versionen anzuzeigen, legen Sie das Visual **Studio-Versionsauswahlsteuerelement** für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich oben im Inhaltsverzeichnis auf dieser Seite.

::: moniker-end
::: moniker range=">=vs-2017"

Die `ANALYSIS_CALLBACKS` Struktur wird beim Initialisieren eines [ANALYSIS_DESCRIPTOR](analysis-descriptor-struct.md) oder [RELOG_DESCRIPTOR](relog-descriptor-struct.md) Objekts verwendet. Es gibt an, welche Funktionen während der Analyse oder Neuprotokollierung einer ETW-Ablaufverfolgung (Event Tracing for Windows) aufzurufen sind.

## <a name="syntax"></a>Syntax

```cpp
typedef struct ANALYSIS_CALLBACKS_TAG
{
    OnAnalysisEventFunc     OnStartActivity;
    OnAnalysisEventFunc     OnStopActivity;
    OnAnalysisEventFunc     OnSimpleEvent;
    OnTraceInfoFunc         OnTraceInfo;
    OnBeginEndPassFunc      OnBeginAnalysis;
    OnBeginEndPassFunc      OnEndAnalysis;
    OnBeginEndPassFunc      OnBeginAnalysisPass;
    OnBeginEndPassFunc      OnEndAnalysisPass;
} ANALYSIS_CALLBACKS;
```

## <a name="members"></a>Member

|  |  |
|--|--|
| `OnStartActivity` | Wird aufgerufen, um ein Aktivitätsstartereignis zu verarbeiten. |
| `OnStopActivity` | Wird aufgerufen, um ein Aktivitätsstoppereignis zu verarbeiten. |
| `OnSimpleEvent` | Wird aufgerufen, um ein einfaches Ereignis zu verarbeiten. |
| `OnTraceInfo` | Für Analysesitzungen, die am Anfang jedes Analysedurchlaufs aufgerufen werden. Für Relogging-Sitzungen, die zu Beginn jedes Analysedurchlaufs und erneut zu Beginn des Relogging-Durchlaufs aufgerufen werden. Diese Funktion wird erst aufgerufen, nachdem OnBeginAnalysisPass aufgerufen wurde. |
| `OnBeginAnalysis` | Für Analysesitzungen, die aufgerufen werden, bevor ein Analysedurchlauf begonnen hat. Für Relogging-Sitzungen, die zweimal aufgerufen werden, bevor die Analysephase begonnen hat: einmal, um den Beginn der Relogging-Sitzung anzukündigen, und noch einmal, um den Beginn der Analysephase anzukündigen. |
| `OnEndAnalysis` | Bei Analysesitzungen wird diese Funktion aufgerufen, nachdem alle Analysedurchläufe beendet wurden. Bei Relogging-Sitzungen wird diese Funktion aufgerufen, wenn alle Analysedurchläufe der Analysephase beendet sind. Dann wird es wieder aufgerufen, nachdem der Relogging-Pass beendet wurde. |
| `OnBeginAnalysisPass` | Wird aufgerufen, wenn ein Analysedurchlauf oder der Relogging-Durchlauf vor der Verarbeitung eines Ereignisses aufgerufen wird. |
| `OnEndAnalysisPass` | Wird aufgerufen, wenn ein Analysedurchlauf oder der Relogging-Durchlauf nach der Verarbeitung aller Ereignisse beendet wird. |

## <a name="remarks"></a>Bemerkungen

Die Analysephase einer Relogging-Sitzung wird als Teil der Relogging-Sitzung betrachtet und kann mehrere Analysedurchläufe enthalten. Aus diesem `OnBeginAnalysis` Grund wird zu Beginn einer Relogging-Sitzung zweimal hintereinander aufgerufen. `OnEndAnalysis`wird am Ende der Analysephase aufgerufen, bevor die Relogging-Phase und erneut am Ende der Relogging-Phase gestartet wird. Die Relogging-Phase enthält immer einen einzelnen Relogging-Durchlauf.

Es ist möglich, dass Analysatoren sowohl Teil der Analyse- als auch der Relogging-Phase einer Relogging-Sitzung sind. Diese Analysatoren können bestimmen, welche Phase derzeit läuft, `OnEndAnalysis` indem sie die OnBeginAnalysis- und Anrufpaare nachverfolgen. Zwei `OnBeginAnalysis` Anrufe `OnEndAnalysis` ohne Aufruf bedeutet, dass die Analysephase im Gange ist. Zwei `OnBeginAnalysis` Anrufe `OnEndAnalysis` und ein Anruf bedeuten, dass die Relogging-Phase im Gange ist. Zwei OnBeginAnalysis `OnEndAnalysis` und zwei Aufrufe bedeuten, dass beide Phasen beendet wurden.

Alle Elemente `ANALYSIS_CALLBACKS` der Struktur müssen auf eine gültige Funktion verweisen. Weitere Informationen zu den akzeptierten Funktionssignaturen finden Sie unter [OnAnalysisEventFunc](on-analysis-event-func-typedef.md), [OnTraceInfoFunc](on-trace-info-func-typedef.md)und [OnBeginEndPassFunc](on-begin-end-pass-func-typedef.md).

::: moniker-end
