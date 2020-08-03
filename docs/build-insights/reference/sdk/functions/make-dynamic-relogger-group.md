---
title: MakeDynamicReloggerGroup
description: Referenz zur Funktion „MakeDynamicReloggerGroup“ des C++ Build Insights SDK
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MakeDynamicReloggerGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: c0d1348be8878e686aeba4a58c407264264c5bc4
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224187"
---
# <a name="makedynamicreloggergroup"></a>MakeDynamicReloggerGroup

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Wenn die Dokumentation für diese Versionen angezeigt werden soll, legen Sie das Steuerelement für die Auswahl der **Version** von Visual Studio für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich am Anfang des Inhaltsverzeichnisses auf dieser Seite.

::: moniker-end
::: moniker range=">=vs-2017"

Die Funktion `MakeDynamicReloggerGroup` wird zum Erstellen von dynamischen Reloggergruppen verwendet. Die Member einer Reloggergruppe empfangen ein Ereignis nach dem anderen (von links nach rechts), bis alle Ereignisse einer Ablaufverfolgung verarbeitet worden sind.

## <a name="syntax"></a>Syntax

```cpp
auto MakeDynamicReloggerGroup(std::vector<IRelogger*> reloggers);

auto MakeDynamicReloggerGroup(std::vector<std::shared_ptr<IRelogger>> reloggers);

auto MakeDynamicReloggerGroup(std::vector<std::unique_ptr<IRelogger>> reloggers);
```

### <a name="parameters"></a>Parameter

*reloggers*\
Ein Vektor von [IRelogger](../other-types/irelogger-class.md)-Zeigern, die in der dynamischen Reloggergruppe enthalten sind. Diese Zeiger können unformatiert, `std::unique_ptr` oder `std::shared_ptr` sein. [IAnalyzer](../other-types/ianalyzer-class.md)-Zeiger werden aufgrund einer Vererbungsbeziehung auch als `IRelogger`-Zeiger bezeichnet.

### <a name="return-value"></a>Rückgabewert

Eine dynamische Reloggergruppe. Verwenden Sie das Schlüsselwort **`auto`** , um den Rückgabewert zu erfassen.

## <a name="remarks"></a>Hinweise

Im Gegensatz zu statischen Reloggergruppen müssen die Member einer dynamischen Reloggergruppe nicht zur Kompilierzeit bekannt sein. Sie können Member der Reloggergruppe zur Laufzeit basierend auf der Programmeingabe oder basierend auf anderen Werten auswählen, die zur Kompilierzeit unbekannt sind. Im Gegensatz zu statischen Reloggergruppen weisen [`IRelogger`](../other-types/irelogger-class.md)-Zeiger innerhalb einer dynamischen Reloggergruppe polymorphes Verhalten auf, und virtuelle Funktionsaufrufe werden richtig weitergeleitet. Diese Flexibilität hat allerdings zur Folge, dass die Ereignisverarbeitung länger dauern kann. Wenn alle Member der Reloggergruppe zur Kompilierzeit bekannt sind und kein polymorphes Verhalten erforderlich ist, sollten Sie in Erwägung ziehen, eine statische Reloggergruppe zu verwenden. Wenn Sie eine statische Reloggergruppe verwenden möchten, rufen Sie stattdessen [`MakeStaticReloggerGroup`](make-static-relogger-group.md) auf.

Eine dynamische Reloggergruppe kann in einer statischen Reloggergruppe gekapselt werden. Übergeben Sie ihre Adresse an [`MakeStaticReloggerGroup`](make-static-relogger-group.md). Gehen Sie so vor, um dynamische Reloggergruppen an Funktionen wie [`Relog`](relog.md) zu übergeben, die nur statische Reloggergruppen akzeptieren.

::: moniker-end
