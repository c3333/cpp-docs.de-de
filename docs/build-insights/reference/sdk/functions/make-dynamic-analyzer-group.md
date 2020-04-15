---
title: MakeDynamicAnalyzerGroup
description: Die C++ Build Insights SDK MakeDynamicAnalyzerGroup-Funktionsreferenz.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MakeDynamicAnalyzerGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 148eeea41f29ac6dd75653feed7f3f3f8c301911
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323961"
---
# <a name="makedynamicanalyzergroup"></a>MakeDynamicAnalyzerGroup

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Um die Dokumentation zu diesen Versionen anzuzeigen, legen Sie das Visual **Studio-Versionsauswahlsteuerelement** für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich oben im Inhaltsverzeichnis auf dieser Seite.

::: moniker-end
::: moniker range=">=vs-2017"

Die `MakeDynamicAnalyzerGroup` Funktion wird verwendet, um eine dynamische Analysatorgruppe zu erstellen. Mitglieder einer Analysegruppe empfangen Ereignisse nacheinander von links nach rechts, bis alle Ereignisse in einer Ablaufverfolgung analysiert werden.

## <a name="syntax"></a>Syntax

```cpp
auto MakeDynamicAnalyzerGroup(std::vector<IAnalyzer*> analyzers);

auto MakeDynamicAnalyzerGroup(std::vector<std::shared_ptr<IAnalyzer>> analyzers);

auto MakeDynamicAnalyzerGroup(std::vector<std::unique_ptr<IAnalyzer>> analyzers);
```

### <a name="parameters"></a>Parameter

*Analysatoren*\
Ein Vektor von [IAnalyzer-Zeigern,](../other-types/ianalyzer-class.md) die in der dynamischen Analysegruppe enthalten sind. Diese Zeiger können roh, `std::unique_ptr`oder `std::shared_ptr`sein.

### <a name="return-value"></a>Rückgabewert

Eine dynamische Analysatorgruppe. Verwenden Sie das **Schlüsselwort auto,** um den Rückgabewert zu erfassen.

## <a name="remarks"></a>Bemerkungen

Im Gegensatz zu statischen Analysegruppen müssen die Mitglieder einer dynamischen Analysegruppe zur Kompilierungszeit nicht bekannt sein. Sie können Analyzer-Gruppenmitglieder zur Laufzeit basierend auf Programmeingaben oder basierend auf anderen Werten auswählen, die zur Kompilierungszeit unbekannt sind. Im Gegensatz zu statischen Analysegruppen weisen [IAnalyzer-Zeiger](../other-types/ianalyzer-class.md) innerhalb einer dynamischen Analyzergruppe ein polymorphes Verhalten auf, und virtuelle Funktionsaufrufe werden korrekt ausgelöst. Diese Flexibilität geht zu Kosten einer möglicherweise langsameren Ereignisverarbeitungszeit. Wenn alle Mitglieder der Analyzer-Gruppe zur Kompilierungszeit bekannt sind und Sie kein polymorphes Verhalten benötigen, sollten Sie eine statische Analysatorgruppe verwenden. Um eine statische Analysatorgruppe zu verwenden, rufen Sie stattdessen [MakeStaticAnalyzerGroup](make-static-analyzer-group.md) auf.

Eine dynamische Analysatorgruppe kann innerhalb einer statischen Analysatorgruppe gekapselt werden. Dies geschieht durch Übergeben der Adresse an [MakeStaticAnalyzerGroup](make-static-analyzer-group.md). Verwenden Sie diese Technik zum Übergeben dynamischer Analysegruppen an Funktionen wie [Analysieren](analyze.md), die nur statische Analysatorgruppen akzeptieren.

::: moniker-end
