---
title: Stopandanalyzetracingsession
description: Die C++ Funktionsreferenz für das Build Insights SDK stopandanalyzetracingsession.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- StopAndAnalyzeTracingSession
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: b1c605bb63ac093f90128a03c37b186226130912
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334217"
---
# <a name="stopandanalyzetracingsession"></a>Stopandanalyzetracingsession

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist kompatibel mit Visual Studio 2017 und höher. Um die Dokumentation für diese Versionen anzuzeigen, legen Sie das Steuerelement für die Visual Studio-Versions Auswahl für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest.

::: moniker-end
::: moniker range=">=vs-2017"

Die `StopAndAnalyzeTracingSession`-Funktion beendet eine laufende Ablauf Verfolgungs Sitzung und speichert die resultierende Ablauf Verfolgung in einer temporären Datei. Eine Analyse Sitzung wird dann sofort mit der temporären Datei als Eingabe gestartet. Ausführbare Dateien, die diese Funktion aufrufen, müssen über Administratorrechte verfügen.

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

*Sessionname* -\
Der Name der Ablauf Verfolgungs Sitzung, die angehalten werden soll. Verwenden Sie den gleichen Sitzungs Namen wie der, der an [starttracingsession](start-tracing-session.md), [starttracingsessiona](start-tracing-session-a.md)oder [starttracingsessionw](start-tracing-session-w.md)übergeben wird.

" *numofanalysispasses* "\
Die Anzahl der für die Ablauf Verfolgung zu testenden Analyse Durchläufen. Die Ablauf Verfolgung wird einmal pro Analyse Durchlauf durch die angegebene Analysegruppe weitergeleitet.

*Statistik*\
Zeiger auf ein [TRACING_SESSION_STATISTICS](../other-types/tracing-session-statistics-struct.md) Objekt. `StopAndAnalyzeTracingSession` schreibt Statistiken der Ablauf Verfolgungs Sammlung in dieses Objekt, bevor Sie zurückgegeben wird

*analyzergroup* -\
Die Analyzer-Gruppe, die für die Analyse verwendet wird. Rufen Sie [makestaticanalyzergroup](make-static-analyzer-group.md) auf, um eine Analysegruppe zu erstellen. Wenn Sie eine dynamische Analysegruppe verwenden möchten, die von [makedynamicanalyzergroup](make-dynamic-analyzer-group.md)abgerufen wurde, Kapseln Sie Sie zuerst in einer statischen Analysegruppe, indem Sie die Adresse an `MakeStaticAnalyzerGroup`übergeben.

### <a name="return-value"></a>Rückgabewert

Ein Ergebniscode aus der [RESULT_CODE](../other-types/result-code-enum.md) -Aufzählung.

::: moniker-end
