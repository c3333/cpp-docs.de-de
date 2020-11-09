---
title: WholeProgramAnalysis-Klasse
description: Die Referenz zur WholeProgramAnalysis-Klasse im C++ Build Insights SDK.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- WholeProgramAnalysis
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: aa766bb33c358627d3347e1d64ed7cc3be832116
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "92920345"
---
# <a name="wholeprogramanalysis-class"></a>WholeProgramAnalysis-Klasse

::: moniker range="<=msvc-140"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Wenn die Dokumentation für diese Versionen angezeigt werden soll, legen Sie das Steuerelement für die Auswahl der **Version** von Visual Studio für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich am Anfang des Inhaltsverzeichnisses auf dieser Seite.

::: moniker-end
::: moniker range=">=msvc-150"

Die `WholeProgramAnalysis`-Klasse wird mit den Funktionen [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md) und [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) verwendet. Dient zum Abgleichen eines [WHOLE_PROGRAM_ANALYSIS](../event-table.md#whole-program-analysis)-Ereignisses.

## <a name="syntax"></a>Syntax

```cpp
class WholeProgramAnalysis : public Activity
{
public:
    WholeProgramAnalysis(const RawEvent& event);
};
```

## <a name="members"></a>Member

Zusammen mit den geerbten Membern aus der [Activity](activity.md)-Basisklasse enthält die `WholeProgramAnalysis`-Klasse die folgenden Member:

### <a name="constructors"></a>Konstruktoren

[WholeProgramAnalysis](#whole-program-analysis)

## <a name="wholeprogramanalysis"></a><a name="whole-program-analysis"></a> WholeProgramAnalysis

```cpp
WholeProgramAnalysis(const RawEvent& event);
```

### <a name="parameters"></a>Parameter

*Ereignis*\
Ein [WHOLE_PROGRAM_ANALYSIS](../event-table.md#whole-program-analysis)-Ereignis.

::: moniker-end
