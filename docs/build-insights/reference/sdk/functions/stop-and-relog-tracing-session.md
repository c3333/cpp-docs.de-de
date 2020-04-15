---
title: StopAndRelogTracingSession
description: Der C++ Build Insights SDK StopAndRelogTracingSession-Funktionsverweis.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- StopAndRelogTracingSession
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 1f6f5af63d25504226707d977791430463374328
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323670"
---
# <a name="stopandrelogtracingsession"></a>StopAndRelogTracingSession

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Um die Dokumentation zu diesen Versionen anzuzeigen, legen Sie das Visual **Studio-Versionsauswahlsteuerelement** für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich oben im Inhaltsverzeichnis auf dieser Seite.

::: moniker-end
::: moniker range=">=vs-2017"

Die `StopAndRelogTracingSession` Funktion beendet eine fortlaufende Ablaufverfolgungssitzung und speichert die resultierende Ablaufverfolgung in einer temporären Datei. Eine Relogging-Sitzung wird dann sofort mit der temporären Datei als Eingabe gestartet. Die letzte erneut protokollierte Ablaufverfolgung, die von der Relogging-Sitzung erzeugt wird, wird in einer vom Aufrufer angegebenen Datei gespeichert. Ausführbare Dateien, die diese Funktion aufrufen, müssen über Administratorrechte verfügen.

## <a name="syntax"></a>Syntax

```cpp
template <
    typename... TAnalyzerGroupMembers,
    typename... TReloggerGroupMembers>
RESULT_CODE StopAndRelogTracingSession(
    const char*                                   sessionName,
    const char*                                   outputLogFile,
    TRACING_SESSION_STATISTICS*                   statistics,
    unsigned                                      numberOfAnalysisPasses,
    unsigned long long                            systemEventsRetentionFlags,
    StaticAnalyzerGroup<TAnalyzerGroupMembers...> analyzerGroup,
    StaticReloggerGroup<TReloggerGroupMembers...> reloggerGroup);

template <
    typename... TAnalyzerGroupMembers,
    typename... TReloggerGroupMembers>
RESULT_CODE StopAndRelogTracingSession(
    const wchar_t*                                sessionName,
    const wchar_t*                                outputLogFile,
    TRACING_SESSION_STATISTICS*                   statistics,
    unsigned                                      numberOfAnalysisPasses,
    unsigned long long                            systemEventsRetentionFlags,
    StaticAnalyzerGroup<TAnalyzerGroupMembers...> analyzerGroup,
    StaticReloggerGroup<TReloggerGroupMembers...> reloggerGroup);
```

### <a name="parameters"></a>Parameter

*sessionName*\
Der Name der zu beendenden Ablaufverfolgungssitzung. Verwenden Sie denselben Sitzungsnamen wie an [StartTracingSession](start-tracing-session.md), [StartTracingSessionA](start-tracing-session-a.md)oder [StartTracingSessionW](start-tracing-session-w.md)übergeben.

*outputLogFile*\
Die Datei, in die die erneut etologierte Ablaufverfolgung geschrieben werden soll, die von der Relogging-Sitzung erzeugt wurde.

*Statistiken*\
Zeiger auf ein [TRACING_SESSION_STATISTICS](../other-types/tracing-session-statistics-struct.md) Objekt. `StopAndRelogTracingSession`schreibt Ablaufverfolgungssammlungsstatistiken in diesem Objekt, bevor es zurückgegeben wird.

*numberOfAnalysisPasses*\
Die Anzahl der Analysedurchläufe, die für die Ablaufverfolgung ausgeführt werden sollen. Die Ablaufverfolgung wird einmal pro Analysedurchlauf durch die bereitgestellte Analysegruppe geleitet.

*systemEventsRetentionFlags*\
Eine [RELOG_RETENTION_SYSTEM_EVENT_FLAGS](../other-types/relog-retention-system-event-flags-constants.md) Bitmaske an, die angibt, welche System-ETW-Ereignisse in der erneut protokollierten Ablaufverfolgung beibehalten werden sollen.

*analyzerGroup*\
Die Analysegruppe, die für die Analysephase der Relogging-Sitzung verwendet wird. Rufen Sie [MakeStaticAnalyzerGroup](make-static-analyzer-group.md) auf, um eine Analyzer-Gruppe zu erstellen. Wenn Sie eine dynamische Analysatorgruppe verwenden möchten, die von [MakeDynamicAnalyzerGroup](make-dynamic-analyzer-group.md)abgerufen wurde, kapseln `MakeStaticAnalyzerGroup`Sie sie zunächst in einer statischen Analyzergruppe ein, indem Sie ihre Adresse an übergeben.

*reloggerGroup*\
Die Reloggergruppe, die Ereignisse in die in *outputLogFile*angegebene Ablaufverfolgungsdatei neu protokolliert. Rufen Sie [MakeStaticReloggerGroup](make-static-relogger-group.md) auf, um eine Reloggergruppe zu erstellen. Wenn Sie eine dynamische Reloggergruppe verwenden möchten, die von [MakeDynamicReloggerGroup](make-dynamic-relogger-group.md)abgerufen wurde, kapseln `MakeStaticReloggerGroup`Sie sie zuerst in einer statischen Reloggergruppe ein, indem Sie ihre Adresse an übergeben.

### <a name="return-value"></a>Rückgabewert

Ein Ergebniscode aus der [RESULT_CODE](../other-types/result-code-enum.md) Enumerum.

### <a name="remarks"></a>Bemerkungen

Die Eingabeablaufverfolgung wird durch die *Analyzer-GruppenanzahlOfAnalysisPasses-Zeiten* übergeben. Es gibt keine ähnliche Option für das Erneuteinloggen von Durchläufen. Die Spur wird durch die Reloggergruppe nur einmal übergeben, nachdem alle Analysedurchläufe abgeschlossen sind.

Das Relogging von Systemereignissen wie CPU-Samples innerhalb einer Reloggerklasse wird nicht unterstützt. Verwenden Sie den Parameter *systemEventsRetentionFlags,* um zu entscheiden, welche Systemereignisse in der Ausgabeablaufverfolgung beibehalten werden sollen.

::: moniker-end
