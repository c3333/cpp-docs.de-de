---
title: Relog
description: Der C++ Build Insights SDK Relog-Funktionsverweis.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Relog
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 28b290d2bf2880ce2f534fa1cd91750890e2fead
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323781"
---
# <a name="relog"></a>Relog

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Um die Dokumentation zu diesen Versionen anzuzeigen, legen Sie das Visual **Studio-Versionsauswahlsteuerelement** für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich oben im Inhaltsverzeichnis auf dieser Seite.

::: moniker-end
::: moniker range=">=vs-2017"

Die `Relog` Funktion wird verwendet, um MSVC-Ereignisse aus einer Ereignisablaufverfolgung für Windows (ETW) zu lesen und in eine neue, geänderte ETW-Ablaufverfolgung zu schreiben.

## <a name="syntax"></a>Syntax

```cpp
template <
    typename... TAnalyzerGroupMembers,
    typename... TReloggerGroupMembers>
RESULT_CODE Relog(
    const char*                                   inputLogFile,
    const char*                                   outputLogFile,
    unsigned                                      numberOfAnalysisPasses,
    unsigned long long                            systemEventsRetentionFlags,
    StaticAnalyzerGroup<TAnalyzerGroupMembers...> analyzerGroup,
    StaticReloggerGroup<TReloggerGroupMembers...> reloggerGroup);

template <
    typename... TAnalyzerGroupMembers,
    typename... TReloggerGroupMembers>
RESULT_CODE Relog(
    const wchar_t*                                inputLogFile,
    const wchar_t*                                outputLogFile,
    unsigned                                      numberOfAnalysisPasses,
    unsigned long long                            systemEventsRetentionFlags,
    StaticAnalyzerGroup<TAnalyzerGroupMembers...> analyzerGroup,
    StaticReloggerGroup<TReloggerGroupMembers...> reloggerGroup);
```

### <a name="parameters"></a>Parameter

*TAnalyzerGroupMembers*\
Dieser Parameter wird immer abgeleitet.

*TReloggerGroupMitglieder*\
Dieser Parameter wird immer abgeleitet.

*inputLogFile*\
Die Eingabe-ETW-Ablaufverfolgung, aus der Sie Ereignisse lesen möchten.

*outputLogFile*\
Die Datei, in die die neuen Ereignisse geschrieben werden sollen.

*numberOfAnalysisPasses*\
Die Anzahl der Analysedurchläufe, die für die Eingabeablaufverfolgung ausgeführt werden sollen. Die Ablaufverfolgung wird einmal pro Analysedurchlauf durch die bereitgestellte Analysegruppe geleitet.

*systemEventsRetentionFlags*\
Eine Bitmaske, die angibt, welche System-ETW-Ereignisse in der erneut protokollierten Ablaufverfolgung beibehalten werden sollen. Weitere Informationen finden Sie unter [RELOG_RETENTION_SYSTEM_EVENT_FLAGS](../other-types/relog-retention-system-event-flags-constants.md).

*analyzerGroup*\
Die Analysegruppe, die für die Analysephase der Relogging-Sitzung verwendet wird. Rufen Sie [MakeStaticAnalyzerGroup](make-static-analyzer-group.md) auf, um eine Analyzer-Gruppe zu erstellen. Um eine dynamische Analysatorgruppe zu verwenden, die von [MakeDynamicAnalyzerGroup](make-dynamic-analyzer-group.md)abgerufen wurde, kapseln Sie sie zunächst in einer statischen Analysatorgruppe ein, indem Sie ihre Adresse an `MakeStaticAnalyzerGroup`übergeben.

*reloggerGroup*\
Die Reloggergruppe, die Ereignisse in die in *outputLogFile*angegebene Ablaufverfolgungsdatei neu protokolliert. Rufen Sie [MakeStaticReloggerGroup](make-static-relogger-group.md) auf, um eine Reloggergruppe zu erstellen. Um eine dynamische Reloggergruppe zu verwenden, die von [MakeDynamicReloggerGroup](make-dynamic-relogger-group.md)abgerufen wurde, kapseln `MakeStaticReloggerGroup`Sie sie zunächst in einer statischen Reloggergruppe ein, indem Sie ihre Adresse an übergeben.

### <a name="return-value"></a>Rückgabewert

Ein Ergebniscode aus der [RESULT_CODE](../other-types/result-code-enum.md) Enumerum.

### <a name="remark"></a>Anmerkung

Die Eingabeablaufverfolgung wird durch die *Analyzer-GruppenanzahlOfAnalysisPasses-Zeiten* übergeben. Es gibt keine ähnliche Option für das Erneuteinloggen von Durchläufen. Die Spur wird durch die Reloggergruppe nur einmal übergeben, nachdem alle Analysedurchläufe abgeschlossen sind.

Das Relogging von Systemereignissen wie CPU-Samples innerhalb einer Reloggerklasse wird nicht unterstützt. Verwenden Sie den Parameter *systemEventsRetentionFlags,* um zu entscheiden, welche Systemereignisse in der Ausgabeablaufverfolgung beibehalten werden sollen.

::: moniker-end
