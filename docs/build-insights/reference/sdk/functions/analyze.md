---
title: Analysieren
description: Die C++ Build Insights SDK Analyze-Funktionsreferenz.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Analyze
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 08b3643270cc785b3fbea36720d192b4a1473104
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324112"
---
# <a name="analyze"></a>Analysieren

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Um die Dokumentation zu diesen Versionen anzuzeigen, legen Sie das Visual **Studio-Versionsauswahlsteuerelement** für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich oben im Inhaltsverzeichnis auf dieser Seite.

::: moniker-end
::: moniker range=">=vs-2017"

Die `Analyze` Funktion wird verwendet, um eine ETW-Ablaufverfolgung (Event Tracing for Windows) zu analysieren, die von MSVC abgerufen wurde, während ein C++-Build nachverfolgt wird. Die Ereignisse in der ETW-Ablaufverfolgung werden sequenziell an eine vom Aufrufer bereitgestellte Analysegruppe weitergeleitet. Diese Funktion unterstützt Multipassanalysen, die die Weiterleitung des Ereignisstreams an die Analysegruppe mehrmals hintereinander ermöglichen.

## <a name="syntax"></a>Syntax

```cpp
template <typename... TAnalyzerGroupMembers>
RESULT_CODE Analyze(
    const char*                                   inputLogFile,
    unsigned                                      numberOfPasses,
    StaticAnalyzerGroup<TAnalyzerGroupMembers...> analyzerGroup);

template <typename... TAnalyzerGroupMembers>
RESULT_CODE Analyze(
    const wchar_t*                                inputLogFile,
    unsigned                                      numberOfPasses,
    StaticAnalyzerGroup<TAnalyzerGroupMembers...> analyzerGroup);
```

### <a name="parameters"></a>Parameter

*TAnalyzerGroupMembers*\
Dieser Parameter wird immer abgeleitet.

*inputLogFile*\
Die Eingabe-ETW-Ablaufverfolgung, aus der Sie Ereignisse lesen möchten.

*numberOfPasses*\
Die Anzahl der Analysedurchläufe, die für die Eingabeablaufverfolgung ausgeführt werden sollen. Die Ablaufverfolgung wird einmal pro Analysedurchlauf durch die bereitgestellte Analysegruppe geleitet.

*analyzerGroup*\
Die für die Analyse verwendete Analysegruppe. Rufen Sie [MakeStaticAnalyzerGroup](make-static-analyzer-group.md) auf, um eine Analyzer-Gruppe zu erstellen. Um eine dynamische Analysatorgruppe zu verwenden, die von [MakeDynamicAnalyzerGroup](make-dynamic-analyzer-group.md)abgerufen wurde, kapseln Sie sie zunächst in einer statischen Analysatorgruppe ein, indem Sie ihre Adresse an `MakeStaticAnalyzerGroup`übergeben.

### <a name="return-value"></a>Rückgabewert

Ein Ergebniscode aus der [RESULT_CODE](../other-types/result-code-enum.md) Enumerum.

::: moniker-end
