---
title: MakeStaticAnalyzerGroup
description: Der C++ Build Insights SDK MakeStaticAnalyzerGroup-Funktionsverweis.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MakeStaticAnalyzerGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 72f7f5d7a408436902394451a52dd66efe1d93f5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323940"
---
# <a name="makestaticanalyzergroup"></a>MakeStaticAnalyzerGroup

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Um die Dokumentation zu diesen Versionen anzuzeigen, legen Sie das Visual **Studio-Versionsauswahlsteuerelement** für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich oben im Inhaltsverzeichnis auf dieser Seite.

::: moniker-end
::: moniker range=">=vs-2017"

Die `MakeStaticAnalyzerGroup` Funktion wird verwendet, um eine statische Analysatorgruppe zu erstellen, die an Funktionen wie [Analysieren](analyze.md) oder [Relog](relog.md)übergeben werden kann. Mitglieder einer Analysegruppe empfangen Ereignisse nacheinander von links nach rechts, bis alle Ereignisse in einer Ablaufverfolgung analysiert werden.

## <a name="syntax"></a>Syntax

```cpp
template <typename... TAnalyzerPtrs>
auto MakeStaticAnalyzerGroup(TAnalyzerPtrs... analyzers);
```

### <a name="parameters"></a>Parameter

*TAnalyzerPtrs*\
Dieser Parameter wird immer abgeleitet.

*Analysatoren*\
Ein Parameterpaket von [IAnalyzer-Zeigern,](../other-types/ianalyzer-class.md) die in der statischen Analysegruppe enthalten sind. Diese Zeiger können roh, `std::unique_ptr`oder `std::shared_ptr`sein.

### <a name="return-value"></a>Rückgabewert

Eine statische Analysatorgruppe. Verwenden Sie das **Schlüsselwort auto,** um den Rückgabewert zu erfassen.

## <a name="remarks"></a>Bemerkungen

Im Gegensatz zu dynamischen Analysegruppen müssen die Mitglieder einer statischen Analysegruppe zum Zeitpunkt der Kompilierung bekannt sein. Darüber hinaus enthält eine statische Analysegruppe [IAnalyzer-Zeiger,](../other-types/ianalyzer-class.md) die kein polymorphes Verhalten aufweisen. Wenn Sie eine statische Analysegruppe zum Analysieren einer Ereignisablaufverfolgung für Windows `IAnalyzer` (ETW) verwenden, werden Aufrufe der Schnittstelle immer auf das Objekt aufgelöst, auf das direkt vom Mitglied der Analyzer-Gruppe verwiesen wird. Dieser Verlust an Flexibilität bringt die Möglichkeit schnellerer Ereignisverarbeitungszeiten mit sich. Wenn die Mitglieder einer Analyzer-Gruppe zum Zeitpunkt der Kompilierung nicht bekannt `IAnalyzer` sind oder wenn Sie polymorphes Verhalten für Ihre Zeiger benötigen, sollten Sie eine dynamische Analysegruppe verwenden. Um eine dynamische Analysatorgruppe zu verwenden, rufen Sie stattdessen [MakeDynamicAnalyzerGroup](make-static-analyzer-group.md) auf.

::: moniker-end
