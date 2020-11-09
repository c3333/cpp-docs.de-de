---
title: FrontEndFileGroup-Klasse
description: Die Referenz zur FrontEndFileGroup-Klasse im C++ Build Insights SDK.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FrontEndFileGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 902b394f645030fed4eeb79bae79535e6d246a1f
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "92923236"
---
# <a name="frontendfilegroup-class"></a>FrontEndFileGroup-Klasse

::: moniker range="<=msvc-140"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Wenn die Dokumentation für diese Versionen angezeigt werden soll, legen Sie das Steuerelement für die Auswahl der **Version** von Visual Studio für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich am Anfang des Inhaltsverzeichnisses auf dieser Seite.

::: moniker-end
::: moniker range=">=msvc-150"

Die `FrontEndFileGroup`-Klasse wird mit den Funktionen [MatchEventStack](../functions/match-event-stack.md) und [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) verwendet. Dient zum Abgleichen von Gruppen von [FRONT_END_FILE](../event-table.md#front-end-file)-Ereignissen.

## <a name="syntax"></a>Syntax

```cpp
class FrontEndFileGroup : public EventGroup<FrontEndFile>
{
public:
    FrontEndFileGroup(std::deque<FrontEndFile>&& group);
};
```

## <a name="members"></a>Member

Zusammen mit den geerbten Membern aus der Basisklasse [EventGroup\<FrontEndFile\>](event-group.md) enthält die `FrontEndFileGroup`-Klasse die folgenden Member:

### <a name="constructors"></a>Konstruktoren

[FrontEndFileGroup](#front-end-file-group)

## <a name="frontendfilegroup"></a><a name="front-end-file-group"></a> FrontEndFileGroup

```cpp
FrontEndFileGroup(std::deque<FrontEndFile>&& group);
```

### <a name="parameters"></a>Parameter

*group*\
Eine Gruppe von [FRONT_END_FILE](../event-table.md#front-end-file)-Ereignissen.

::: moniker-end
