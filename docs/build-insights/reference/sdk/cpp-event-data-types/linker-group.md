---
title: Linkergroup-Klasse
description: Die C++ linkergroup-Klassenreferenz für das Build Insights SDK.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- LinkerGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 95b0dcc3a771ec07ee60185a79a5ddbc29434b5d
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334727"
---
# <a name="linkergroup-class"></a>Linkergroup-Klasse

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist kompatibel mit Visual Studio 2017 und höher. Um die Dokumentation für diese Versionen anzuzeigen, legen Sie das Steuerelement für die Visual Studio-Versions Auswahl für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest.

::: moniker-end
::: moniker range=">=vs-2017"

Die `LinkerGroup`-Klasse wird mit den Funktionen [matcheventstack](../functions/match-event-stack.md) und [matcheventstackinmembership Function](../functions/match-event-stack-in-member-function.md) verwendet. Verwenden Sie diese Option, um Gruppen von [Linker](../event-table.md#linker) -Ereignissen abzugleichen.

## <a name="syntax"></a>Syntax

```cpp
class LinkerGroup : public EventGroup<Linker>
{
public:
    LinkerGroup(std::deque<Linker>&& group);
};
```

## <a name="members"></a>Members

Zusammen mit den geerbten Membern aus der [Ereignis Gruppe\<Linker\>](event-group.md) Basisklasse enthält die `LinkerGroup`-Klasse die folgenden Member:

### <a name="constructors"></a>Konstruktoren

[Linkergroup](#linker-group)

## <a name="linker-group"></a>Linkergroup

```cpp
LinkerGroup(std::deque<Linker>&& group);
```

### <a name="parameters"></a>Parameter

*Gruppen*\
Eine Gruppe von [Linker](../event-table.md#linker) -Ereignissen.

::: moniker-end
