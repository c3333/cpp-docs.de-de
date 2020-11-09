---
title: LTCG-Klasse
description: Die Referenz zur LTCG-Klasse im C++ Build Insights SDK.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- LTCG
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 3b6bab629307c9fc4fb021df2e75772d5247566d
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "92920553"
---
# <a name="ltcg-class"></a>LTCG-Klasse

::: moniker range="<=msvc-140"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Wenn die Dokumentation für diese Versionen angezeigt werden soll, legen Sie das Steuerelement für die Auswahl der **Version** von Visual Studio für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich am Anfang des Inhaltsverzeichnisses auf dieser Seite.

::: moniker-end
::: moniker range=">=msvc-150"

Die `LTCG`-Klasse wird mit den Funktionen [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md) und [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) verwendet. Dient zum Abgleichen eines [LTCG](../event-table.md#ltcg)-Ereignisses.

## <a name="syntax"></a>Syntax

```cpp
class LTCG : public Activity
{
public:
    LTCG(const RawEvent& event);
};
```

## <a name="members"></a>Member

Zusammen mit den geerbten Membern aus der [Activity](activity.md)-Basisklasse enthält die `LTCG`-Klasse die folgenden Member:

### <a name="constructors"></a>Konstruktoren

[LTCG](#ltcg)

## <a name="ltcg"></a><a name="ltcg"></a> LTCG

```cpp
LTCG(const RawEvent& event);
```

### <a name="parameters"></a>Parameter

*Ereignis*\
Ein [LTCG](../event-table.md#ltcg)-Ereignis.

::: moniker-end
