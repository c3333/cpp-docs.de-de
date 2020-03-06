---
title: Makedynamicanalyzergroup
description: Die C++ Funktionsreferenz für das Build Insights SDK makedynamicanalyzergroup.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MakeDynamicAnalyzerGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: f409d685c6af6514b73cd837d668a962c1a0d01a
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334403"
---
# <a name="makedynamicanalyzergroup"></a>Makedynamicanalyzergroup

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist kompatibel mit Visual Studio 2017 und höher. Um die Dokumentation für diese Versionen anzuzeigen, legen Sie das Steuerelement für die Visual Studio-Versions Auswahl für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest.

::: moniker-end
::: moniker range=">=vs-2017"

Die `MakeDynamicAnalyzerGroup`-Funktion wird zum Erstellen einer dynamischen Analysegruppe verwendet. Mitglieder einer Analysegruppe empfangen Ereignisse nacheinander von links nach rechts, bis alle Ereignisse in einer Ablauf Verfolgung analysiert werden.

## <a name="syntax"></a>Syntax

```cpp
auto MakeDynamicAnalyzerGroup(std::vector<IAnalyzer*> analyzers);

auto MakeDynamicAnalyzerGroup(std::vector<std::shared_ptr<IAnalyzer>> analyzers);

auto MakeDynamicAnalyzerGroup(std::vector<std::unique_ptr<IAnalyzer>> analyzers);
```

### <a name="parameters"></a>Parameter

\ *Analysen*
Ein Vektor von [ianalyzer](../other-types/ianalyzer-class.md) -Zeigern, der in der dynamischen Analysegruppe enthalten ist. Diese Zeiger können RAW, `std::unique_ptr`oder `std::shared_ptr`sein.

### <a name="return-value"></a>Rückgabewert

Eine dynamische Analysegruppe. Verwenden Sie das Schlüsselwort " **Auto** ", um den Rückgabewert aufzuzeichnen.

## <a name="remarks"></a>Bemerkungen

Im Unterschied zu statischen Analyzer-Gruppen müssen die Mitglieder einer dynamischen Analysegruppe zum Zeitpunkt der Kompilierung nicht bekannt sein. Sie können Analyzer-Gruppenmitglieder zur Laufzeit basierend auf der Programm Eingabe oder basierend auf anderen Werten auswählen, die zum Zeitpunkt der Kompilierung unbekannt sind. Im Unterschied zu statischen Analyzer-Gruppen weisen [ianalyzer](../other-types/ianalyzer-class.md) -Zeiger innerhalb einer dynamischen Analysegruppe polymorphe Verhalten auf, und virtuelle Funktionsaufrufe werden ordnungsgemäß weitergeleitet. Diese Flexibilität ergibt sich aus einer möglicherweise langsameren Ereignis Verarbeitungszeit. Wenn alle analyzergruppenmember zum Zeitpunkt der Kompilierung bekannt sind und Sie kein polymorphes Verhalten benötigen, sollten Sie die Verwendung einer statischen Analysegruppe in Erwägung gezogen. Wenn Sie eine statische Analysegruppe verwenden möchten, führen Sie stattdessen [makestaticanalyzergroup](make-static-analyzer-group.md) aus.

Eine dynamische Analysegruppe kann in einer statischen Analysegruppe gekapselt werden. Dies erfolgt durch Übergabe der Adresse an [makestaticanalyzergroup](make-static-analyzer-group.md). Verwenden Sie dieses Verfahren, um dynamische Analyse Gruppen an Funktionen wie " [analysieren](analyze.md)" zu übergeben, die nur statische Analyse Gruppen akzeptieren.

::: moniker-end
