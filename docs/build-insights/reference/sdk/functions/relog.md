---
title: Relog
description: Die Referenz zur Relog-Funktion im C++ Build Insights SDK.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Relog
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 628f60042a10cf80c0b077d28387ed75466e925b
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "92922751"
---
# <a name="relog"></a>Relog

::: moniker range="<=msvc-140"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Wenn die Dokumentation für diese Versionen angezeigt werden soll, legen Sie das Steuerelement für die Auswahl der **Version** von Visual Studio für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich am Anfang des Inhaltsverzeichnisses auf dieser Seite.

::: moniker-end
::: moniker range=">=msvc-150"

Die `Relog`-Funktion dient zum Lesen von MSVC-Ereignissen aus einer Ereignisablaufverfolgung für Windows (Event Trace for Windows, ETW), die in eine neue, geänderte ETW geschrieben werden.

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
Dieser Parameter wird immer hergeleitet.

*TReloggerGroupMembers*\
Dieser Parameter wird immer hergeleitet.

*inputLogFile*\
Die Eingabe-ETW, aus der Ereignisse gelesen werden sollen.

*outputLogFile*\
Die Datei, in die die neuen Ereignisse geschrieben werden sollen.

*numberOfAnalysisPasses*\
Anzahl der Analysedurchläufe, die für die Eingabeablaufverfolgung ausgeführt werden sollen. Die Ablaufverfolgung durchläuft die angegebene Analysegruppe einmal pro Analysedurchlauf.

*systemEventsRetentionFlags*\
Bitmaske, die angibt, welche ETW-Systemereignisse in der neu protokollierten Ablaufverfolgung aufbewahrt werden sollen. Weitere Informationen finden Sie unter [RELOG_RETENTION_SYSTEM_EVENT_FLAGS](../other-types/relog-retention-system-event-flags-constants.md).

*analyzerGroup*\
Die Analysetoolgruppe, die für die Analysephase der Neuprotokollierungssitzung verwendet wird. Rufen Sie [MakeStaticAnalyzerGroup](make-static-analyzer-group.md) auf, um eine Analysetoolgruppe zu erstellen. Wenn Sie eine dynamische Analysetoolgruppe verwenden möchten, die aus [MakeDynamicAnalyzerGroup](make-dynamic-analyzer-group.md) abgerufen wurde, kapseln Sie sie zuerst in einer statischen Analysetoolgruppe, indem Sie deren Adresse an `MakeStaticAnalyzerGroup` übergeben.

*reloggerGroup*\
Die Neuprotokollierungsgruppe, die Ereignisse in der in *outputLogFile* angegebenen Ablaufverfolgungsdatei neu protokolliert. Rufen Sie [MakeStaticReloggerGroup](make-static-relogger-group.md) auf, um eine Neuprotokollierungsgruppe zu erstellen. Wenn Sie eine dynamische Neuprotokollierungsgruppe verwenden möchten, die von [MakeDynamicReloggerGroup](make-dynamic-relogger-group.md) abgerufen wurde, kapseln Sie sie zuerst in einer statischen Neuprotokollierungsgruppe, indem Sie deren Adresse an `MakeStaticReloggerGroup` übergeben.

### <a name="return-value"></a>Rückgabewert

Ein Ergebniscode aus der Enumeration [RESULT_CODE](../other-types/result-code-enum.md).

### <a name="remark"></a>Anmerkung

Die Eingabeablaufverfolgung durchläuft die Analysetoolgruppe mit der von *numberOfAnalysisPasses* angegebenen Häufigkeit. Für Neuprotokollierungsdurchläufe gibt es keine ähnliche Option. Die Ablaufverfolgung durchläuft die Neuprotokollierungsgruppe nur einmal, nachdem alle Analysedurchläufe abgeschlossen wurden.

Die Neuprotokollierung von Systemereignissen wie CPU-Stichproben in einer Relogger-Klasse wird nicht unterstützt. Verwenden Sie den Parameter *systemEventsRetentionFlags* , um zu entscheiden, welche Systemereignisse in der Ausgabeablaufverfolgung aufbewahrt werden sollen.

::: moniker-end
