---
title: MakeDynamicReloggerGroup
description: Die C++ Build Insights SDK MakeDynamicReloggerGroup Funktionsreferenz.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MakeDynamicReloggerGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: f49e37f8e1a8b9ca9a800d20b2891a54453095ef
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323950"
---
# <a name="makedynamicreloggergroup"></a>MakeDynamicReloggerGroup

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Um die Dokumentation zu diesen Versionen anzuzeigen, legen Sie das Visual **Studio-Versionsauswahlsteuerelement** für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich oben im Inhaltsverzeichnis auf dieser Seite.

::: moniker-end
::: moniker range=">=vs-2017"

Die `MakeDynamicReloggerGroup` Funktion wird verwendet, um eine dynamische Reloggergruppe zu erstellen. Mitglieder einer Reloggergruppe empfangen Ereignisse nacheinander von links nach rechts, bis alle Ereignisse in einer Ablaufverfolgung verarbeitet wurden.

## <a name="syntax"></a>Syntax

```cpp
auto MakeDynamicReloggerGroup(std::vector<IRelogger*> reloggers);

auto MakeDynamicReloggerGroup(std::vector<std::shared_ptr<IRelogger>> reloggers);

auto MakeDynamicReloggerGroup(std::vector<std::unique_ptr<IRelogger>> reloggers);
```

### <a name="parameters"></a>Parameter

*reloggers*\
Ein Vektor von [IRelogger-Zeigern,](../other-types/irelogger-class.md) die in der dynamischen Reloggergruppe enthalten sind. Diese Zeiger können roh, `std::unique_ptr`oder `std::shared_ptr`sein. [IAnalyzer-Zeiger](../other-types/ianalyzer-class.md) werden aufgrund `IRelogger` einer Vererbungsbeziehung auch als Zeiger betrachtet.

### <a name="return-value"></a>Rückgabewert

Eine dynamische Reloggergruppe. Verwenden Sie das **Schlüsselwort auto,** um den Rückgabewert zu erfassen.

## <a name="remarks"></a>Bemerkungen

Im Gegensatz zu statischen Reloggergruppen müssen die Mitglieder einer dynamischen Reloggergruppe zur Kompilierungszeit nicht bekannt sein. Sie können Reloggergruppenmitglieder zur Laufzeit basierend auf Programmeingaben oder basierend auf anderen Werten auswählen, die zur Kompilierungszeit unbekannt sind. Im Gegensatz zu statischen Reloggergruppen weisen [IRelogger-Zeiger](../other-types/irelogger-class.md) innerhalb einer dynamischen Reloggergruppe ein polymorphes Verhalten auf, und virtuelle Funktionsaufrufe werden korrekt ausgelöst. Diese Flexibilität geht zu Kosten einer möglicherweise langsameren Ereignisverarbeitungszeit. Wenn alle Reloggergruppenmitglieder zur Kompilierungszeit bekannt sind und Sie kein polymorphes Verhalten benötigen, sollten Sie eine statische Reloggergruppe verwenden. Um eine statische Reloggergruppe zu verwenden, rufen Sie stattdessen [MakeStaticReloggerGroup](make-static-relogger-group.md) auf.

Eine dynamische Reloggergruppe kann innerhalb einer statischen Reloggergruppe gekapselt werden. Sie übergeben die Adresse an [MakeStaticReloggerGroup](make-static-relogger-group.md). Verwenden Sie diese Technik zum Übergeben dynamischer Reloggergruppen an Funktionen wie [Relog](relog.md), die nur statische Reloggergruppen akzeptieren.

::: moniker-end
