---
title: TopDown-Klasse
description: Die Referenz zur Thread-Klasse im C++ Build Insights SDK.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TopDown
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 88622461b27a6037d8d7fbb73cd324978302c941
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "92920423"
---
# <a name="topdown-class"></a>TopDown-Klasse

::: moniker range="<=msvc-140"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Wenn die Dokumentation für diese Versionen angezeigt werden soll, legen Sie das Steuerelement für die Auswahl der **Version** von Visual Studio für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich am Anfang des Inhaltsverzeichnisses auf dieser Seite.

::: moniker-end
::: moniker range=">=msvc-150"

Die `TopDown`-Klasse wird mit den Funktionen [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md) und [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) verwendet. Dient zum Abgleichen eines [TOP_DOWN](../event-table.md#top-down)-Ereignisses.

## <a name="syntax"></a>Syntax

```cpp
class TopDown : public Activity
{
public:
    TopDown(const RawEvent& event);
};
```

## <a name="members"></a>Member

Zusammen mit den geerbten Membern aus der [Activity](activity.md)-Basisklasse enthält die `TopDown`-Klasse die folgenden Member:

### <a name="constructors"></a>Konstruktoren

[TopDown](#top-down)

## <a name="topdown"></a><a name="top-down"></a> TopDown

```cpp
TopDown(const RawEvent& event);
```

### <a name="parameters"></a>Parameter

*Ereignis*\
Ein [TOP_DOWN](../event-table.md#top-down)-Ereignis.

::: moniker-end
