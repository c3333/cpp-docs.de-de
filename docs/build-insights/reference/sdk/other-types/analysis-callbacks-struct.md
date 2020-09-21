---
title: ANALYSIS_CALLBACKS-Struktur
description: Der Verweis auf die ANALYSIS_CALLBACKS-Struktur im C++ Build Insights SDK.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- ANALYSIS_CALLBACKS
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: a24755befdd446051ae376b49d3dca06c7bc3320
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/12/2020
ms.locfileid: "90041041"
---
# <a name="analysis_callbacks-structure"></a>ANALYSIS_CALLBACKS-Struktur

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Wenn die Dokumentation für diese Versionen angezeigt werden soll, legen Sie das Steuerelement für die Auswahl der **Version** von Visual Studio für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich am Anfang des Inhaltsverzeichnisses auf dieser Seite.

::: moniker-end
::: moniker range=">=vs-2017"

Die `ANALYSIS_CALLBACKS`-Struktur wird beim Initialisieren eines [ANALYSIS_DESCRIPTOR](analysis-descriptor-struct.md)- oder [RELOG_DESCRIPTOR](relog-descriptor-struct.md)-Objekts verwendet. Sie gibt an, welche Funktionen während der Analyse oder Neuprotokollierung einer Ereignisablaufverfolgung für Windows (Event Tracing for Windows, ETW) aufgerufen werden.

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

| name | BESCHREIBUNG |
|--|--|
| `OnStartActivity` | Wird aufgerufen, um ein Aktivitätsstartereignis zu verarbeiten. |
| `OnStopActivity` | Wird aufgerufen, um ein Aktivitätsstoppereignis zu verarbeiten. |
| `OnSimpleEvent` | Wird aufgerufen, um ein einfaches Ereignis zu verarbeiten. |
| `OnTraceInfo` | Wird für Analysesitzungen zu Beginn jedes Analysedurchlaufs aufgerufen. Wird für Neuprotokollierungssitzungen zu Beginn der einzelnen Analysedurchläufe und wieder am Anfang des Neuprotokollierungsdurchlaufs aufgerufen. Diese Funktion wird nur nach dem Aufruf von OnBeginAnalysisPass aufgerufen. |
| `OnBeginAnalysis` | Wird für Analysesitzungen aufgerufen, bevor ein Analysedurchlauf begonnen hat. Wird für Neuprotokollierungssitzungen zweimal vor Beginn der Analysephase aufgerufen: einmal, um den Beginn der Neuprotokollierungssitzung anzukündigen, und noch einmal, um den Beginn der Analysephase anzukündigen. |
| `OnEndAnalysis` | Für Analysesitzungen wird diese Funktion aufgerufen, nachdem alle Analysedurchläufe beendet wurden. Für Neuprotokollierungssitzungen wird diese Funktion aufgerufen, wenn alle Analysedurchläufe der Analysephase beendet wurden. Anschließend wird sie erneut aufgerufen, nachdem der Neuprotokollierungsdurchlauf beendet wurde. |
| `OnBeginAnalysisPass` | Wird beim Start eines Analyse- oder Neuprotokollierungsdurchlaufs aufgerufen, bevor ein Ereignis verarbeitet wird. |
| `OnEndAnalysisPass` | Wird beim Ende eines Analyse- oder Neuprotokollierungsdurchlaufs aufgerufen, nachdem alle Ereignisse verarbeitet wurden. |

## <a name="remarks"></a>Bemerkungen

Die Analysephase einer Neuprotokollierungssitzung wird als Teil der Neuprotokollierungssitzung angesehen und kann mehrere Analysedurchläufe enthalten. Aus diesem Grund wird `OnBeginAnalysis` zu Beginn einer Neuprotokollierungssitzung zweimal in einer Zeile aufgerufen. `OnEndAnalysis` wird am Ende der Analysephase aufgerufen, bevor die Neuprotokollierungsphase gestartet wird, und wieder am Ende der Neuprotokollierungsphase. Die Neuprotokollierungsphase enthält immer einen einzelnen Neuprotokollierungsdurchlauf.

Analysetools können sowohl Teil der Analyse als auch der Neuprotokollierungsphase einer Neuprotokollierungssitzung sein. Diese Analysetoolmodule können bestimmen, welche Phase zurzeit durchgeführt wird, indem sie die OnBeginAnalysis- und `OnEndAnalysis`-Aufrufpaare nachverfolgen. Zwei `OnBeginAnalysis`-Aufrufe ohne `OnEndAnalysis`-Aufruf bedeutet, dass die Analysephase durchgeführt wird. Zwei `OnBeginAnalysis`-Aufrufe und ein `OnEndAnalysis`-Aufruf bedeutet, dass die Phase der Neuprotokollierung durchgeführt wird. Zwei OnBeginAnalysis- und zwei `OnEndAnalysis`-Aufrufe bedeutet, dass beide Phasen beendet wurden.

Alle Member der `ANALYSIS_CALLBACKS`-Struktur müssen auf eine gültige Funktion verweisen. Weitere Informationen zu den akzeptierten Funktionssignaturen finden Sie unter [OnAnalysisEventFunc](on-analysis-event-func-typedef.md), [OnTraceInfoFunc](on-trace-info-func-typedef.md) und [OnBeginEndPassFunc](on-begin-end-pass-func-typedef.md).

::: moniker-end
