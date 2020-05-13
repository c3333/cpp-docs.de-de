---
title: LinkerGroup-Klasse
description: Der C++ Build Insights SDK LinkerGroup-Klassenverweis.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- LinkerGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: c59d62938e5bd7b839ad12a321a03510e708e0fd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324646"
---
# <a name="linkergroup-class"></a>LinkerGroup-Klasse

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Um die Dokumentation zu diesen Versionen anzuzeigen, legen Sie das Visual **Studio-Versionsauswahlsteuerelement** für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich oben im Inhaltsverzeichnis auf dieser Seite.

::: moniker-end
::: moniker range=">=vs-2017"

Die `LinkerGroup` Klasse wird mit den Funktionen [MatchEventStack](../functions/match-event-stack.md) und [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) verwendet. Verwenden Sie es, um Gruppen von [LINKER-Ereignissen](../event-table.md#linker) abzugleichen.

## <a name="syntax"></a>Syntax

```cpp
class LinkerGroup : public EventGroup<Linker>
{
public:
    LinkerGroup(std::deque<Linker>&& group);
};
```

## <a name="members"></a>Member

Zusammen mit den geerbten Membern aus der `LinkerGroup` [EventGroup\<\> Linker-Basisklasse](event-group.md) enthält die Klasse die folgenden Member:

### <a name="constructors"></a>Konstruktoren

[LinkerGroup](#linker-group)

## <a name="linkergroup"></a><a name="linker-group"></a>LinkerGroup

```cpp
LinkerGroup(std::deque<Linker>&& group);
```

### <a name="parameters"></a>Parameter

*Gruppe*\
Eine Gruppe von [LINKER-Ereignissen.](../event-table.md#linker)

::: moniker-end
