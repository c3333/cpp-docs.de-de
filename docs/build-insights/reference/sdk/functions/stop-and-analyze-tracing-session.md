---
title: StopAndAnalyzeTracingSession
description: Die Referenz zur StopAndAnalyzeTracingSession-Funktion im C++ Build Insights SDK.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- StopAndAnalyzeTracingSession
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 81a8ce43ecedfa51874508193637969411ae52d6
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "92922716"
---
# <a name="stopandanalyzetracingsession"></a>StopAndAnalyzeTracingSession

::: moniker range="<=msvc-140"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Wenn die Dokumentation für diese Versionen angezeigt werden soll, legen Sie das Steuerelement für die Auswahl der **Version** von Visual Studio für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich am Anfang des Inhaltsverzeichnisses auf dieser Seite.

::: moniker-end
::: moniker range=">=msvc-150"

Die `StopAndAnalyzeTracingSession`-Funktion beendet eine laufende Ablaufverfolgungssitzung und speichert die resultierende Ablaufverfolgung in einer temporären Datei. Eine Analysesitzung wird dann sofort mit der temporären Datei als Eingabe gestartet. Ausführbare Dateien, die diese Funktion aufrufen, benötigen Administratorberechtigungen.

## <a name="syntax"></a>Syntax

```cpp
template <typename... TAnalyzerGroupMembers>
RESULT_CODE StopAndAnalyzeTracingSession(
    const char*                                   sessionName,
    unsigned                                      numberOfAnalysisPasses,
    TRACING_SESSION_STATISTICS*                   statistics,
    StaticAnalyzerGroup<TAnalyzerGroupMembers...> analyzerGroup);

template <typename... TAnalyzerGroupMembers>
RESULT_CODE StopAndAnalyzeTracingSession(
    const wchar_t*                                sessionName,
    unsigned                                      numberOfAnalysisPasses,
    TRACING_SESSION_STATISTICS*                   statistics,
    StaticAnalyzerGroup<TAnalyzerGroupMembers...> analyzerGroup);
```

### <a name="parameters"></a>Parameter

*sessionName*\
Der Name der anzuhaltenden Ablaufverfolgungssitzung. Verwenden Sie den gleichen Sitzungsnamen wie den, der an [StartTracingSession](start-tracing-session.md), [StartTracingSessionA](start-tracing-session-a.md) oder [StartTracingSessionW](start-tracing-session-w.md) übergeben wurde.

*numberOfAnalysisPasses*\
Anzahl der Analysedurchläufe, die für die Ablaufverfolgung ausgeführt werden sollen. Die Ablaufverfolgung durchläuft die angegebene Analysegruppe einmal pro Analysedurchlauf.

*statistics*\
Zeiger auf ein [TRACING_SESSION_STATISTICS](../other-types/tracing-session-statistics-struct.md)-Objekt. `StopAndAnalyzeTracingSession` schreibt Sammlungsstatistiken zur Ablaufverfolgung in dieses Objekt, bevor es zurückgegeben wird.

*analyzerGroup*\
Die Analysetoolgruppe, die für die Analyse verwendet wird. Rufen Sie [MakeStaticAnalyzerGroup](make-static-analyzer-group.md) auf, um eine Analysetoolgruppe zu erstellen. Wenn Sie eine dynamische Analysetoolgruppe verwenden möchten, die aus [MakeDynamicAnalyzerGroup](make-dynamic-analyzer-group.md) abgerufen wurde, kapseln Sie sie zuerst in einer statischen Analysetoolgruppe, indem Sie deren Adresse an `MakeStaticAnalyzerGroup` übergeben.

### <a name="return-value"></a>Rückgabewert

Ein Ergebniscode aus der Enumeration [RESULT_CODE](../other-types/result-code-enum.md).

::: moniker-end
