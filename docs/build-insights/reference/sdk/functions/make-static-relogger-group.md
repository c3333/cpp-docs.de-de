---
title: MakeStaticReloggerGroup
description: Referenz zur Funktion „MakeStaticReloggerGroup“ des C++ Build Insights SDK
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MakeStaticReloggerGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 1d49f15a14675f265e1f63ef8795f442f49ad5d4
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "92920202"
---
# <a name="makestaticreloggergroup"></a>MakeStaticReloggerGroup

::: moniker range="<=msvc-140"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Wenn die Dokumentation für diese Versionen angezeigt werden soll, legen Sie das Steuerelement für die Auswahl der **Version** von Visual Studio für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich am Anfang des Inhaltsverzeichnisses auf dieser Seite.

::: moniker-end
::: moniker range=">=msvc-150"

Die Funktion `MakeStaticReloggerGroup` wird zum Erstellen einer statischen Reloggergruppe verwendet, die an Funktionen wie [Relog](relog.md) übergeben werden können. Die Member einer Reloggergruppe empfangen ein Ereignis nach dem anderen (von links nach rechts), bis alle Ereignisse einer Ablaufverfolgung verarbeitet wurden.

## <a name="syntax"></a>Syntax

```cpp
template <typename... TReloggerPtrs>
auto MakeStaticReloggerGroup(TReloggerPtrs... reloggers);
```

### <a name="parameters"></a>Parameter

*TReloggerPtrs*\
Dieser Parameter wird immer hergeleitet.

*reloggers*\
Ein Parameterpaket aus [`IRelogger`](../other-types/irelogger-class.md)-Zeigern, die in der statischen Reloggergruppe enthalten sind. Diese Zeiger können unformatiert, `std::unique_ptr` oder `std::shared_ptr` sein. [`IAnalyzer`](../other-types/ianalyzer-class.md)-Zeiger werden aufgrund einer Vererbungsbeziehung auch als `IRelogger`-Zeiger betrachtet.

### <a name="return-value"></a>Rückgabewert

Beim Rückgabewert handelt es sich um eine statische Reloggergruppe. Verwenden Sie das Schlüsselwort **`auto`** , um den Rückgabewert zu erfassen.

## <a name="remarks"></a>Hinweise

Im Gegensatz zu dynamischen Reloggergruppen müssen die Member einer statischen Reloggergruppe zur Kompilierzeit bekannt sein. Darüber hinaus enthält eine statische Reloggergruppe [`IRelogger`](../other-types/irelogger-class.md)-Zeiger, die kein polymorphes Verhalten aufweisen. Wenn Sie eine statische Reloggergruppe verwenden, um eine Ereignisablaufverfolgung für Windows (Event Tracing for Windows, ETW) zu analysieren, haben Aufrufe der Schnittstelle `IRelogger` immer zur Folge, dass direkt vom Member der Reloggergruppe auf das Objekt gezeigt wird. Dadurch verlieren Sie zwar an Flexibilität, aber Ereignisse können möglicherweise schneller verarbeitet werden. Wenn die Member einer Reloggergruppe zur Kompilierzeit nicht bekannt sind oder Ihre `IRelogger`-Zeiger polymorphes Verhalten aufweisen müssen, sollten Sie in Erwägung ziehen, eine dynamische Reloggergruppe zu verwenden. Sie können eine dynamische Reloggergruppe verwenden, indem Sie stattdessen [`MakeDynamicReloggerGroup`](make-dynamic-relogger-group.md) aufrufen.

::: moniker-end
