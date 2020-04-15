---
title: MakeStaticReloggerGroup
description: Die C++ Build Insights SDK MakeStaticReloggerGroup-Funktionsreferenz.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MakeStaticReloggerGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 75b638537cb8e0cdeeb5476a3f5277e8e90d9baf
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323914"
---
# <a name="makestaticreloggergroup"></a>MakeStaticReloggerGroup

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Um die Dokumentation zu diesen Versionen anzuzeigen, legen Sie das Visual **Studio-Versionsauswahlsteuerelement** für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich oben im Inhaltsverzeichnis auf dieser Seite.

::: moniker-end
::: moniker range=">=vs-2017"

Die `MakeStaticReloggerGroup` Funktion wird verwendet, um eine statische Reloggergruppe zu erstellen, die an Funktionen wie [Relog](relog.md)übergeben werden kann. Mitglieder einer Reloggergruppe empfangen Ereignisse nacheinander von links nach rechts, bis alle Ereignisse in einer Ablaufverfolgung verarbeitet wurden.

## <a name="syntax"></a>Syntax

```cpp
template <typename... TReloggerPtrs>
auto MakeStaticReloggerGroup(TReloggerPtrs... reloggers);
```

### <a name="parameters"></a>Parameter

*TReloggerPtrs*\
Dieser Parameter wird immer abgeleitet.

*reloggers*\
Ein Parameterpaket mit [IRelogger-Zeigern,](../other-types/irelogger-class.md) das in der statischen Reloggergruppe enthalten ist. Diese Zeiger können roh, `std::unique_ptr`oder `std::shared_ptr`sein. [IAnalyzer-Zeiger](../other-types/ianalyzer-class.md) werden aufgrund `IRelogger` einer Vererbungsbeziehung auch als Zeiger betrachtet.

### <a name="return-value"></a>Rückgabewert

Eine statische Reloggergruppe. Verwenden Sie das **Schlüsselwort auto,** um den Rückgabewert zu erfassen.

## <a name="remarks"></a>Bemerkungen

Im Gegensatz zu dynamischen Reloggergruppen müssen die Mitglieder einer statischen Reloggergruppe zur Kompilierungszeit bekannt sein. Darüber hinaus enthält eine statische Reloggergruppe [IRelogger-Zeiger,](../other-types/irelogger-class.md) die kein polymorphes Verhalten aufweisen. Wenn Sie eine statische Reloggergruppe zum Analysieren einer Ereignisablaufverfolgung für `IRelogger` Windows (ETW) verwenden, werden Aufrufe der Schnittstelle immer auf das Objekt aufgelöst, auf das direkt vom Reloggergruppenmitglied verwiesen wird. Dieser Verlust an Flexibilität bringt die Möglichkeit schnellerer Ereignisverarbeitungszeiten mit sich. Wenn die Mitglieder einer Reloggergruppe zum Zeitpunkt der Kompilierung nicht bekannt sind `IRelogger` oder wenn Sie polymorphes Verhalten für Ihre Zeiger benötigen, sollten Sie eine dynamische Reloggergruppe verwenden. Sie können eine dynamische Reloggergruppe verwenden, indem Sie stattdessen [MakeDynamicReloggerGroup](make-dynamic-relogger-group.md) aufrufen.

::: moniker-end
