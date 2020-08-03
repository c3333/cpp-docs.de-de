---
title: MakeDynamicAnalyzerGroup
description: Referenz zur Funktion „MakeDynamicAnalyzerGroup“ des C++ Build Insights SDK
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MakeDynamicAnalyzerGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: c4c244066b41837a8dd95b44bab2b096134ed5d4
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224200"
---
# <a name="makedynamicanalyzergroup"></a>MakeDynamicAnalyzerGroup

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Wenn die Dokumentation für diese Versionen angezeigt werden soll, legen Sie das Steuerelement für die Auswahl der **Version** von Visual Studio für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich am Anfang des Inhaltsverzeichnisses auf dieser Seite.

::: moniker-end
::: moniker range=">=vs-2017"

Die Funktion `MakeDynamicAnalyzerGroup` wird zum Erstellen von dynamischen Analysegruppen verwendet. Die Member einer Analysegruppe empfangen ein Ereignis nach dem anderen (von links nach rechts), bis alle Ereignisse einer Ablaufverfolgung analysiert worden sind.

## <a name="syntax"></a>Syntax

```cpp
auto MakeDynamicAnalyzerGroup(std::vector<IAnalyzer*> analyzers);

auto MakeDynamicAnalyzerGroup(std::vector<std::shared_ptr<IAnalyzer>> analyzers);

auto MakeDynamicAnalyzerGroup(std::vector<std::unique_ptr<IAnalyzer>> analyzers);
```

### <a name="parameters"></a>Parameter

*analyzers*\
Ein Vektor von [IAnalyzer](../other-types/ianalyzer-class.md)-Zeigern, die in der dynamischen Analysegruppe enthalten sind. Diese Zeiger können unformatiert, `std::unique_ptr` oder `std::shared_ptr` sein.

### <a name="return-value"></a>Rückgabewert

Eine dynamische Analysegruppe. Verwenden Sie das Schlüsselwort **`auto`** , um den Rückgabewert zu erfassen.

## <a name="remarks"></a>Hinweise

Im Gegensatz zu statischen Analysegruppen müssen die Member einer dynamischen Analysegruppe zur Kompilierzeit nicht bekannt sein. Sie können Member der Analysegruppe zur Laufzeit basierend auf der Programmeingabe oder basierend auf anderen Werten auswählen, die zur Kompilierzeit unbekannt sind. Im Gegensatz zu statischen Analysegruppen weisen [`IAnalyzer`](../other-types/ianalyzer-class.md)-Zeiger innerhalb einer dynamischen Analysegruppe polymorphes Verhalten auf, und virtuelle Funktionsaufrufe werden richtig weitergeleitet. Diese Flexibilität hat allerdings zur Folge, dass die Ereignisverarbeitung länger dauern kann. Wenn alle Member der Analysegruppe zur Kompilierzeit bekannt sind und Sie nicht auf polymorphes Verhalten angewiesen sind, sollten Sie in Erwägung ziehen, eine statische Analysegruppe zu verwenden. Wenn Sie eine statische Analysegruppe verwenden möchten, rufen Sie stattdessen [`MakeStaticAnalyzerGroup`](make-static-analyzer-group.md) auf.

Eine dynamische Analysegruppe kann in eine statischen Analysegruppe gekapselt werden. Dafür wird ihre Adresse an [`MakeStaticAnalyzerGroup`](make-static-analyzer-group.md) übergeben. Gehen Sie so vor, um dynamische Analysegruppen an Funktionen wie [`Analyze`](analyze.md) zu übergeben, die nur statische Analysegruppen akzeptieren.

::: moniker-end
