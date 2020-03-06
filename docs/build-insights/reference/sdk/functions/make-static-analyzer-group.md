---
title: Makestaticanalyzergroup
description: Die C++ Funktionsreferenz für das Build Insights SDK makestaticanalyzergroup.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MakeStaticAnalyzerGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 5eabb0fcbb0a0bb0eea0f4e6bbf27b8e4c53c3ab
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334391"
---
# <a name="makestaticanalyzergroup"></a>Makestaticanalyzergroup

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist kompatibel mit Visual Studio 2017 und höher. Um die Dokumentation für diese Versionen anzuzeigen, legen Sie das Steuerelement für die Visual Studio-Versions Auswahl für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest.

::: moniker-end
::: moniker range=">=vs-2017"

Die `MakeStaticAnalyzerGroup`-Funktion wird zum Erstellen einer statischen Analysegruppe verwendet, die an Funktionen wie z. b. [Analyse](analyze.md) oder [Neuprotokollierung](relog.md)weitergeleitet werden kann. Mitglieder einer Analysegruppe empfangen Ereignisse nacheinander von links nach rechts, bis alle Ereignisse in einer Ablauf Verfolgung analysiert werden.

## <a name="syntax"></a>Syntax

```cpp
template <typename... TAnalyzerPtrs>
auto MakeStaticAnalyzerGroup(TAnalyzerPtrs... analyzers);
```

### <a name="parameters"></a>Parameter

*Tanalyzerptrs* -\
Dieser Parameter wird immer abgeleitet.

\ *Analysen*
Ein Parameter Paket von [ianalyzer](../other-types/ianalyzer-class.md) -Zeigern, das in der statischen Analysegruppe enthalten ist. Diese Zeiger können RAW, `std::unique_ptr`oder `std::shared_ptr`sein.

### <a name="return-value"></a>Rückgabewert

Eine statische Analysegruppe. Verwenden Sie das Schlüsselwort " **Auto** ", um den Rückgabewert aufzuzeichnen.

## <a name="remarks"></a>Bemerkungen

Im Unterschied zu dynamischen Analyzer-Gruppen müssen die Member einer statischen Analysegruppe zum Zeitpunkt der Kompilierung bekannt sein. Darüber hinaus enthält eine statische Analysegruppe [ianalyzer](../other-types/ianalyzer-class.md) -Zeiger, die kein polymorphes Verhalten aufweisen. Wenn Sie eine statische Analysegruppe verwenden, um eine ETW-Ablauf Verfolgung (Event Tracing for Windows, Ereignis Ablauf Verfolgung für Windows) zu analysieren, werden Aufrufe der `IAnalyzer`-Schnittstelle immer in das Objekt aufgelöst, auf das das analyzergruppenmember Dieser Verlust von Flexibilität bietet die Möglichkeit, schnellere Ereignis Verarbeitungszeiten zu verursachen. Wenn die Mitglieder einer Analysegruppe zum Zeitpunkt der Kompilierung nicht bekannt sein können oder wenn Sie polymorphe Verhalten auf den `IAnalyzer` Zeigern benötigen, sollten Sie die Verwendung einer dynamischen Analysegruppe in Erwägung gezogen. Wenn Sie eine dynamische Analysegruppe verwenden möchten, führen Sie stattdessen [makedynamicanalyzergroup](make-static-analyzer-group.md) aus.

::: moniker-end
