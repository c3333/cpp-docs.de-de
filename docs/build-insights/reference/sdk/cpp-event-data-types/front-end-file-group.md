---
title: Frontendfilegroup-Klasse
description: Die C++ Klassenreferenz für den Build Insights SDK-frontendfilegroup.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FrontEndFileGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 343a5a0d798d6c719088bd49668e70b10fba6d1a
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334829"
---
# <a name="frontendfilegroup-class"></a>Frontendfilegroup-Klasse

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist kompatibel mit Visual Studio 2017 und höher. Um die Dokumentation für diese Versionen anzuzeigen, legen Sie das Steuerelement für die Visual Studio-Versions Auswahl für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest.

::: moniker-end
::: moniker range=">=vs-2017"

Die `FrontEndFileGroup`-Klasse wird mit den Funktionen [matcheventstack](../functions/match-event-stack.md) und [matcheventstackinmembership Function](../functions/match-event-stack-in-member-function.md) verwendet. Verwenden Sie ihn, um Gruppen von [FRONT_END_FILE](../event-table.md#front-end-file) Ereignissen abzugleichen.

## <a name="syntax"></a>Syntax

```cpp
class FrontEndFileGroup : public EventGroup<FrontEndFile>
{
public:
    FrontEndFileGroup(std::deque<FrontEndFile>&& group);
};
```

## <a name="members"></a>Members

Zusammen mit den geerbten Membern aus der [Ereignis Gruppe\<frontendfile-\>](event-group.md) Basisklasse enthält die `FrontEndFileGroup`-Klasse die folgenden Member:

### <a name="constructors"></a>Konstruktoren

[Frontendfilegroup](#front-end-file-group)

## <a name="front-end-file-group"></a>Frontendfilegroup

```cpp
FrontEndFileGroup(std::deque<FrontEndFile>&& group);
```

### <a name="parameters"></a>Parameter

*Gruppen*\
Eine Gruppe von [FRONT_END_FILE](../event-table.md#front-end-file) Ereignissen.

::: moniker-end
