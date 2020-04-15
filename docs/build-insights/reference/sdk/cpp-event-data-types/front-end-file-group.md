---
title: FrontEndFileGroup-Klasse
description: Der C++ Build Insights SDK FrontEndFileGroup-Klassenverweis.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FrontEndFileGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: d2eebb650e59e750e5ebde74914dca5f0ef4779d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324773"
---
# <a name="frontendfilegroup-class"></a>FrontEndFileGroup-Klasse

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Um die Dokumentation zu diesen Versionen anzuzeigen, legen Sie das Visual **Studio-Versionsauswahlsteuerelement** für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich oben im Inhaltsverzeichnis auf dieser Seite.

::: moniker-end
::: moniker range=">=vs-2017"

Die `FrontEndFileGroup` Klasse wird mit den Funktionen [MatchEventStack](../functions/match-event-stack.md) und [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) verwendet. Verwenden Sie es, um Gruppen von [FRONT_END_FILE](../event-table.md#front-end-file) Ereignissen abzugleichen.

## <a name="syntax"></a>Syntax

```cpp
class FrontEndFileGroup : public EventGroup<FrontEndFile>
{
public:
    FrontEndFileGroup(std::deque<FrontEndFile>&& group);
};
```

## <a name="members"></a>Member

Zusammen mit den geerbten Membern aus der [EventGroup\<\> FrontEndFile-Basisklasse](event-group.md) enthält die `FrontEndFileGroup` Klasse die folgenden Member:

### <a name="constructors"></a>Konstruktoren

[FrontEndFileGroup](#front-end-file-group)

## <a name="frontendfilegroup"></a><a name="front-end-file-group"></a>FrontEndFileGroup

```cpp
FrontEndFileGroup(std::deque<FrontEndFile>&& group);
```

### <a name="parameters"></a>Parameter

*Gruppe*\
Eine Gruppe von [FRONT_END_FILE](../event-table.md#front-end-file) Ereignissen.

::: moniker-end
