---
title: OptLBR-Klasse
description: Die Referenz zur OptLBR-Klasse im C++ Build Insights SDK.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- OptLBR
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 5505e50b0acd961a1ff745eee36419bbaa4bd601
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "92923055"
---
# <a name="optlbr-class"></a>OptLBR-Klasse

::: moniker range="<=msvc-140"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Wenn die Dokumentation für diese Versionen angezeigt werden soll, legen Sie das Steuerelement für die Auswahl der **Version** von Visual Studio für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich am Anfang des Inhaltsverzeichnisses auf dieser Seite.

::: moniker-end
::: moniker range=">=msvc-150"

Die `OptLBR`-Klasse wird mit den Funktionen [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md) und [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) verwendet. Dient zum Abgleichen eines [OPT_LBR](../event-table.md#opt-lbr)-Ereignisses.

## <a name="syntax"></a>Syntax

```cpp
class OptLBR : public Activity
{
public:
    OptLBR(const RawEvent& event);
};
```

## <a name="members"></a>Member

Zusammen mit den geerbten Membern aus der [Activity](activity.md)-Basisklasse enthält die `OptLBR`-Klasse die folgenden Member:

### <a name="constructors"></a>Konstruktoren

[OptLBR](#opt-lbr)

## <a name="optlbr"></a><a name="opt-lbr"></a> OptLBR

```cpp
OptLBR(const RawEvent& event);
```

### <a name="parameters"></a>Parameter

*Ereignis*\
Ein [OPT_LBR](../event-table.md#opt-lbr)-Ereignis.

::: moniker-end
