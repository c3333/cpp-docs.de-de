---
title: Analysieren
description: Die C++ Build Insights SDK-Analyse Funktionsreferenz.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Analyze
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 49161641d1cff1c64261d95bb2caace2f802543a
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334433"
---
# <a name="analyze"></a>Analysieren

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist kompatibel mit Visual Studio 2017 und höher. Um die Dokumentation für diese Versionen anzuzeigen, legen Sie das Steuerelement für die Visual Studio-Versions Auswahl für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest.

::: moniker-end
::: moniker range=">=vs-2017"

Die `Analyze`-Funktion wird verwendet, um eine ETW-Ablauf Verfolgung (Event Tracing for Windows, Ereignis Ablauf Verfolgung für Windows C++ ) zu analysieren, die von MSVC abgerufen wurde Die Ereignisse in der etw-Ablauf Verfolgung werden sequenziell an eine vom Aufrufer bereitgestellte Analysegruppe weitergeleitet. Diese Funktion unterstützt Multipass-Analysen, mit denen der Ereignisdaten Strom mehrmals in einer Zeile an die Analysegruppe weitergeleitet werden kann.

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

*Tanalyzergroupmembers* -\
Dieser Parameter wird immer abgeleitet.

*inputlogfile* -\
Die Eingabe-etw-Ablauf Verfolgung, von der Ereignisse gelesen werden sollen.

*Anzahl* der\
Die Anzahl der an der Eingabe Ablauf Verfolgung zu testenden Analysen. Die Ablauf Verfolgung wird einmal pro Analyse Durchlauf durch die angegebene Analysegruppe weitergeleitet.

*analyzergroup* -\
Die Analyzer-Gruppe, die für die Analyse verwendet wird. Rufen Sie [makestaticanalyzergroup](make-static-analyzer-group.md) auf, um eine Analysegruppe zu erstellen. Wenn Sie eine dynamische Analysegruppe verwenden möchten, die von [makedynamicanalyzergroup](make-dynamic-analyzer-group.md)abgerufen wurde, Kapseln Sie Sie zuerst in einer statischen Analysegruppe, indem Sie die Adresse an `MakeStaticAnalyzerGroup`übergeben.

### <a name="return-value"></a>Rückgabewert

Ein Ergebniscode aus der [RESULT_CODE](../other-types/result-code-enum.md) -Aufzählung.

::: moniker-end
