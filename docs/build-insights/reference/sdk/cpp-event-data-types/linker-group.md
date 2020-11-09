---
title: LinkerGroup-Klasse
description: Die Referenz zur LinkerGroup-Klasse im C++ Build Insights SDK.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- LinkerGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 8a818cf7524405d4e2f29a1987e93b77371607cc
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "92923109"
---
# <a name="linkergroup-class"></a>LinkerGroup-Klasse

::: moniker range="<=msvc-140"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Wenn die Dokumentation für diese Versionen angezeigt werden soll, legen Sie das Steuerelement für die Auswahl der **Version** von Visual Studio für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich am Anfang des Inhaltsverzeichnisses auf dieser Seite.

::: moniker-end
::: moniker range=">=msvc-150"

Die `LinkerGroup`-Klasse wird mit den Funktionen [MatchEventStack](../functions/match-event-stack.md) und [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) verwendet. Dient zum Abgleichen von Gruppen von [LINKER](../event-table.md#linker)-Ereignissen.

## <a name="syntax"></a>Syntax

```cpp
class LinkerGroup : public EventGroup<Linker>
{
public:
    LinkerGroup(std::deque<Linker>&& group);
};
```

## <a name="members"></a>Member

Zusammen mit den geerbten Membern aus der Basisklasse [EventGroup\<Linker\>](event-group.md) enthält die `LinkerGroup`-Klasse die folgenden Member:

### <a name="constructors"></a>Konstruktoren

[LinkerGroup](#linker-group)

## <a name="linkergroup"></a><a name="linker-group"></a> LinkerGroup

```cpp
LinkerGroup(std::deque<Linker>&& group);
```

### <a name="parameters"></a>Parameter

*group*\
Eine Gruppe von [LINKER](../event-table.md#linker)-Ereignissen.

::: moniker-end
