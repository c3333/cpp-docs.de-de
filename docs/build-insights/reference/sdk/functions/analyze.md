---
title: Analysieren
description: Die Referenz zur Analyze-Funktion im C++ Build Insights SDK.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Analyze
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 5e593b690231adf6f04161f9c3ff6aef3217f9ef
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "92920319"
---
# <a name="analyze"></a>Analysieren

::: moniker range="<=msvc-140"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Wenn die Dokumentation für diese Versionen angezeigt werden soll, legen Sie das Steuerelement für die Auswahl der **Version** von Visual Studio für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich am Anfang des Inhaltsverzeichnisses auf dieser Seite.

::: moniker-end
::: moniker range=">=msvc-150"

Die Funktion `Analyze` dient zur Analyse einer Ereignisablaufverfolgung für Windows (ETW), die von MSVC während der Ablaufverfolgung eines C++-Builds abgerufen wird. Die Ereignisse in der Ereignisablaufverfolgung für Windows werden sequenziell an eine vom Aufrufer bereitgestellte Analysetoolgruppe weitergeleitet. Diese Funktion unterstützt Analysen mit mehreren Durchläufen, die es ermöglichen, den Ereignisdatenstrom mehrmals hintereinander an die Analysetoolgruppe weiterzuleiten.

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
Dieser Parameter wird immer hergeleitet.

*inputLogFile*\
Die Eingabe-ETW, aus der Ereignisse gelesen werden sollen.

*numberOfPasses*\
Anzahl der Analysedurchläufe, die für die Eingabeablaufverfolgung ausgeführt werden sollen. Die Ablaufverfolgung durchläuft die angegebene Analysegruppe einmal pro Analysedurchlauf.

*analyzerGroup*\
Die Analysetoolgruppe, die für die Analyse verwendet wird. Rufen Sie [MakeStaticAnalyzerGroup](make-static-analyzer-group.md) auf, um eine Analysetoolgruppe zu erstellen. Wenn Sie eine dynamische Analysetoolgruppe verwenden möchten, die aus [MakeDynamicAnalyzerGroup](make-dynamic-analyzer-group.md) abgerufen wurde, kapseln Sie sie zuerst in einer statischen Analysetoolgruppe, indem Sie deren Adresse an `MakeStaticAnalyzerGroup` übergeben.

### <a name="return-value"></a>Rückgabewert

Ein Ergebniscode aus der Enumeration [RESULT_CODE](../other-types/result-code-enum.md).

::: moniker-end
