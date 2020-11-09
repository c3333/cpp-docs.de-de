---
title: StopAndRelogTracingSession
description: Die Referenz zur StopAndRelogTracingSession-Funktion im C++ Build Insights SDK.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- StopAndRelogTracingSession
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: d36dee1b16ca467d16b22587abe3ef34ee6ccb29
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "92919955"
---
# <a name="stopandrelogtracingsession"></a>StopAndRelogTracingSession

::: moniker range="<=msvc-140"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Wenn die Dokumentation für diese Versionen angezeigt werden soll, legen Sie das Steuerelement für die Auswahl der **Version** von Visual Studio für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich am Anfang des Inhaltsverzeichnisses auf dieser Seite.

::: moniker-end
::: moniker range=">=msvc-150"

Die `StopAndRelogTracingSession`-Funktion beendet eine laufende Ablaufverfolgungssitzung und speichert die resultierende Ablaufverfolgung in einer temporären Datei. Eine Neuprotokollierungssitzung wird dann sofort mit der temporären Datei als Eingabe gestartet. Die durch die Neuprotokollierung erzeugte endgültige Ablaufverfolgung wird in einer vom Aufrufer angegebenen Datei gespeichert. Ausführbare Dateien, die diese Funktion aufrufen, benötigen Administratorberechtigungen.

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
Der Name der anzuhaltenden Ablaufverfolgungssitzung. Verwenden Sie den gleichen Sitzungsnamen wie den, der an [StartTracingSession](start-tracing-session.md), [StartTracingSessionA](start-tracing-session-a.md) oder [StartTracingSessionW](start-tracing-session-w.md) übergeben wurde.

*outputLogFile*\
Die Datei, in die die neu protokollierte Ablaufverfolgung geschrieben werden soll, die von der Neuprotokollierungssitzung generiert wurde.

*statistics*\
Zeiger auf ein [TRACING_SESSION_STATISTICS](../other-types/tracing-session-statistics-struct.md)-Objekt. `StopAndRelogTracingSession` schreibt Sammlungsstatistiken zur Ablaufverfolgung in dieses Objekt, bevor es zurückgegeben wird.

*numberOfAnalysisPasses*\
Anzahl der Analysedurchläufe, die für die Ablaufverfolgung ausgeführt werden sollen. Die Ablaufverfolgung durchläuft die angegebene Analysegruppe einmal pro Analysedurchlauf.

*systemEventsRetentionFlags*\
Eine [RELOG_RETENTION_SYSTEM_EVENT_FLAGS](../other-types/relog-retention-system-event-flags-constants.md)-Bitmaske, die angibt, welche ETW-Systemereignisse in der erneut protokollierten Ablaufverfolgung aufbewahrt werden sollen.

*analyzerGroup*\
Die Analysetoolgruppe, die für die Analysephase der Neuprotokollierungssitzung verwendet wird. Rufen Sie [MakeStaticAnalyzerGroup](make-static-analyzer-group.md) auf, um eine Analysetoolgruppe zu erstellen. Wenn Sie eine dynamische Analysetoolgruppe verwenden möchten, die aus [MakeDynamicAnalyzerGroup](make-dynamic-analyzer-group.md) abgerufen wurde, kapseln Sie sie zuerst in einer statischen Analysetoolgruppe, indem Sie deren Adresse an `MakeStaticAnalyzerGroup` übergeben.

*reloggerGroup*\
Die Neuprotokollierungsgruppe, die Ereignisse in der in *outputLogFile* angegebenen Ablaufverfolgungsdatei neu protokolliert. Rufen Sie [MakeStaticReloggerGroup](make-static-relogger-group.md) auf, um eine Neuprotokollierungsgruppe zu erstellen. Wenn Sie eine dynamische Neuprotokollierungsgruppe verwenden möchten, die von [MakeDynamicReloggerGroup](make-dynamic-relogger-group.md) abgerufen wurde, kapseln Sie sie zuerst in einer statischen Neuprotokollierungsgruppe, indem Sie deren Adresse an `MakeStaticReloggerGroup` übergeben.

### <a name="return-value"></a>Rückgabewert

Ein Ergebniscode aus der Enumeration [RESULT_CODE](../other-types/result-code-enum.md).

### <a name="remarks"></a>Hinweise

Die Eingabeablaufverfolgung durchläuft die Analysetoolgruppe mit der von *numberOfAnalysisPasses* angegebenen Häufigkeit. Für Neuprotokollierungsdurchläufe gibt es keine ähnliche Option. Die Ablaufverfolgung durchläuft die Neuprotokollierungsgruppe nur einmal, nachdem alle Analysedurchläufe abgeschlossen wurden.

Die Neuprotokollierung von Systemereignissen wie CPU-Stichproben in einer Relogger-Klasse wird nicht unterstützt. Verwenden Sie den Parameter *systemEventsRetentionFlags* , um zu entscheiden, welche Systemereignisse in der Ausgabeablaufverfolgung aufbewahrt werden sollen.

::: moniker-end
