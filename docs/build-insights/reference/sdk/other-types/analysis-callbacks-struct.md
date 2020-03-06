---
title: ANALYSIS_CALLBACKS Struktur
description: Das C++ Build Insights SDK ANALYSIS_CALLBACKS Struktur Referenz.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- ANALYSIS_CALLBACKS
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 8c35e740d97488969a6b69467d54412297e49227
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334145"
---
# <a name="analysis_callbacks-structure"></a>ANALYSIS_CALLBACKS Struktur

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist kompatibel mit Visual Studio 2017 und höher. Um die Dokumentation für diese Versionen anzuzeigen, legen Sie das Steuerelement für die Visual Studio-Versions Auswahl für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest.

::: moniker-end
::: moniker range=">=vs-2017"

Die `ANALYSIS_CALLBACKS`-Struktur wird verwendet, wenn ein [ANALYSIS_DESCRIPTOR](analysis-descriptor-struct.md) -oder [RELOG_DESCRIPTOR](relog-descriptor-struct.md) -Objekt initialisiert wird. Gibt an, welche Funktionen während der Analyse oder Neuprotokollierung einer etw-Ablauf Verfolgung (Ereignis Ablauf Verfolgung für Windows) aufgerufen werden.

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

## <a name="members"></a>Members

|  |  |
|--|--|
| `OnStartActivity` | Wird aufgerufen, um ein Aktivitäts Start Ereignis zu verarbeiten. |
| `OnStopActivity` | Wird aufgerufen, um ein Aktivitäts beenden-Ereignis zu verarbeiten. |
| `OnSimpleEvent` | Wird aufgerufen, um ein einfaches Ereignis zu verarbeiten. |
| `OnTraceInfo` | Für Analyse Sitzungen, die zu Beginn jeder Analysephase aufgerufen werden. Zum erneuten Protokollieren von Sitzungen, die zu Beginn der einzelnen Analyse durchlaufen werden, und wieder am Anfang der erneuten Protokollierungs Phase. Diese Funktion wird nur aufgerufen, nachdem onbeginanalysispass aufgerufen wurde. |
| `OnBeginAnalysis` | Für Analyse Sitzungen, die aufgerufen werden, bevor ein Analyse Durchlauf begonnen hat. Zum erneuten Protokollieren von Sitzungen, die vor Beginn der Analysephase zweimal aufgerufen werden: einmal, um den Beginn der erneuten Protokollierungs Sitzung anzukündigen, und noch einmal, um den Beginn der Analysephase ankündigen zu können. |
| `OnEndAnalysis` | Für Analyse Sitzungen wird diese Funktion aufgerufen, nachdem alle Analyse Durchläufen beendet wurden. Zum erneuten Protokollieren von Sitzungen wird diese Funktion aufgerufen, wenn alle Analyse Durchläufen der Analysephase beendet wurden. Anschließend wird Sie erneut aufgerufen, nachdem die erneute Protokollierung abgeschlossen wurde. |
| `OnBeginAnalysisPass` | Wird aufgerufen, wenn ein Analyse Durchlauf oder der neuprotokollierungs Durchlauf begonnen wird, bevor ein Ereignis verarbeitet wird. |
| `OnEndAnalysisPass` | Wird aufgerufen, wenn ein Analyse Durchlauf oder der neuprotokollierungs Durchlauf beendet wird, nachdem alle Ereignisse verarbeitet wurden. |

## <a name="remarks"></a>Bemerkungen

Die Analysephase einer erneuten Protokollierungs Sitzung wird als Teil der Sitzung für die erneute Protokollierung angesehen und kann mehrere Analyse Durchläufen enthalten. Aus diesem Grund wird `OnBeginAnalysis` zweimal in einer Zeile zu Beginn einer erneuten Protokollierungs Sitzung aufgerufen. `OnEndAnalysis` wird am Ende der Analysephase aufgerufen, bevor die neuprotokollierungs Phase beginnt, und wieder am Ende der Phase der erneuten Protokollierung. Die neuprotokollierungs Phase enthält immer einen einzelnen erneuten Protokollierungs Durchlauf.

Es ist möglich, dass Analysen sowohl in der Analyse als auch in der neuprotokollierungs Phase einer erneuten Protokollierungs Sitzung enthalten sind. Diese Analysemodule können bestimmen, welche Phase zurzeit durchgeführt wird, indem Sie die onbeginanalysis-und `OnEndAnalysis`-rufpaare nachverfolgen. Zwei `OnBeginAnalysis` Aufrufe ohne `OnEndAnalysis` Aufruf bedeutet, dass die Analysephase fortlaufend ist. Zwei `OnBeginAnalysis` Aufrufe und ein `OnEndAnalysis` Aufruf bedeutet, dass die erneute Protokollierungs Phase fortlaufend ist. Zwei Phasen vom onbeginanalysis-und zwei-`OnEndAnalysis` bedeutet, dass beide Phasen beendet wurden.

Alle Elemente der `ANALYSIS_CALLBACKS` Struktur müssen auf eine gültige Funktion verweisen. Weitere Informationen zu den akzeptierten Funktions Signaturen finden Sie unter [onanalysisiebziger Func](on-analysis-event-func-typedef.md), [ontraceinfofunc](on-trace-info-func-typedef.md)und [onbeginendpassfunc](on-begin-end-pass-func-typedef.md).

::: moniker-end
