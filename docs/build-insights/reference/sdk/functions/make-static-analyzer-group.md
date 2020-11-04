---
title: MakeStaticAnalyzerGroup
description: Referenz zur Funktion „MakeStaticAnalyzerGroup“ des C++ Build Insights SDK
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MakeStaticAnalyzerGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: d7ddb8652400438c38882b1d27e635e8f1e8db51
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "92920241"
---
# <a name="makestaticanalyzergroup"></a>MakeStaticAnalyzerGroup

::: moniker range="<=msvc-140"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Wenn die Dokumentation für diese Versionen angezeigt werden soll, legen Sie das Steuerelement für die Auswahl der **Version** von Visual Studio für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich am Anfang des Inhaltsverzeichnisses auf dieser Seite.

::: moniker-end
::: moniker range=">=msvc-150"

Die Funktion `MakeStaticAnalyzerGroup` wird zum Erstellen einer statischen Analysegruppe verwendet, die an Funktionen wie [`Analyze`](analyze.md) oder [`Relog`](relog.md) übergeben werden können. Die Member einer Analysegruppe empfangen ein Ereignis nach dem anderen (von links nach rechts), bis alle Ereignisse einer Ablaufverfolgung analysiert worden sind.

## <a name="syntax"></a>Syntax

```cpp
template <typename... TAnalyzerPtrs>
auto MakeStaticAnalyzerGroup(TAnalyzerPtrs... analyzers);
```

### <a name="parameters"></a>Parameter

*TAnalyzerPtrs*\
Dieser Parameter wird immer hergeleitet.

*analyzers*\
Ein Parameterpaket aus [`IAnalyzer`](../other-types/ianalyzer-class.md)-Zeigern, die in der statischen Analysegruppe enthalten sind. Diese Zeiger können unformatiert, `std::unique_ptr` oder `std::shared_ptr` sein.

### <a name="return-value"></a>Rückgabewert

Eine statische Analysegruppe. Verwenden Sie das Schlüsselwort **`auto`** , um den Rückgabewert zu erfassen.

## <a name="remarks"></a>Hinweise

Im Gegensatz zu dynamischen Analysegruppen müssen die Member einer statischen Analysegruppe zur Kompilierzeit bekannt sein. Darüber hinaus enthält eine statische Analysegruppe [`IAnalyzer`](../other-types/ianalyzer-class.md)-Zeiger, die kein polymorphes Verhalten aufweisen. Wenn Sie eine statische Analysegruppe verwenden, um eine Ereignisablaufverfolgung für Windows (Event Tracing for Windows, ETW) zu analysieren, haben Aufrufe der Schnittstelle `IAnalyzer` immer zur Folge, dass direkt vom Member der Analysegruppe auf das Objekt gezeigt wird. Dadurch verlieren Sie zwar an Flexibilität, aber Ereignisse können möglicherweise schneller verarbeitet werden. Wenn die Member einer Analysegruppe zur Kompilierzeit nicht bekannt sind oder Ihre `IAnalyzer`-Zeiger polymorphes Verhalten aufweisen müssen, sollten Sie in Erwägung ziehen, eine dynamische Analysegruppe zu verwenden. Wenn Sie eine dynamische Analysegruppe verwenden möchten, rufen Sie stattdessen [`MakeDynamicAnalyzerGroup`](make-static-analyzer-group.md) auf.

::: moniker-end
