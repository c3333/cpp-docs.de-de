---
title: InvocationGroup-Klasse
description: Die Referenz zur InvocationGroup-Klasse im C++ Build Insights SDK.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- InvocationGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 1a8d4786a228ab25551ee36ce22637d44dc07307
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "92920631"
---
# <a name="invocationgroup-class"></a>InvocationGroup-Klasse

::: moniker range="<=msvc-140"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Wenn die Dokumentation für diese Versionen angezeigt werden soll, legen Sie das Steuerelement für die Auswahl der **Version** von Visual Studio für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich am Anfang des Inhaltsverzeichnisses auf dieser Seite.

::: moniker-end
::: moniker range=">=msvc-150"

Die `InvocationGroup`-Klasse wird mit den Funktionen [MatchEventStack](../functions/match-event-stack.md) und [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) verwendet. Dient zum Abgleichen von Gruppen mit einer Kombination der Ereignisse [COMPILER](../event-table.md#compiler) und [LINKER](../event-table.md#linker).

## <a name="syntax"></a>Syntax

```cpp
class InvocationGroup : public EventGroup<Invocation>
{
public:
    InvocationGroup(std::deque<Invocation>&& group);
};
```

## <a name="members"></a>Member

Zusammen mit den geerbten Membern aus der Basisklasse [EventGroup\<Invocation\>](event-group.md) enthält die `InvocationGroup`-Klasse die folgenden Member:

### <a name="constructors"></a>Konstruktoren

[InvocationGroup](#invocation-group)

## <a name="invocationgroup"></a><a name="invocation-group"></a> InvocationGroup

```cpp
InvocationGroup(std::deque<Invocation>&& group);
```

### <a name="parameters"></a>Parameter

*group*\
Eine Gruppe mit einer Kombination der Ereignisse [COMPILER](../event-table.md#compiler) und [LINKER](../event-table.md#linker).

::: moniker-end
