---
title: Invocationgroup-Klasse
description: Die C++ Klassenreferenz für den Build Insights SDK invocationgroup.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- InvocationGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: b9a2bbcd2b7649b9b5703adc08ed41b272e10276
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334751"
---
# <a name="invocationgroup-class"></a>Invocationgroup-Klasse

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist kompatibel mit Visual Studio 2017 und höher. Um die Dokumentation für diese Versionen anzuzeigen, legen Sie das Steuerelement für die Visual Studio-Versions Auswahl für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest.

::: moniker-end
::: moniker range=">=vs-2017"

Die `InvocationGroup`-Klasse wird mit den Funktionen [matcheventstack](../functions/match-event-stack.md) und [matcheventstackinmembership Function](../functions/match-event-stack-in-member-function.md) verwendet. Verwenden Sie es, um Gruppen abzugleichen, die eine  Mischung aus [compilerereignissen](../event-table.md#compiler) und [linkerereignissen](../event-table.md#linker)

## <a name="syntax"></a>Syntax

```cpp
class InvocationGroup : public EventGroup<Invocation>
{
public:
    InvocationGroup(std::deque<Invocation>&& group);
};
```

## <a name="members"></a>Member

Zusammen mit den geerbten Membern aus der [Ereignis Gruppe\<Aufruf\>](event-group.md) Basisklasse enthält die `InvocationGroup`-Klasse die folgenden Member:

### <a name="constructors"></a>Konstruktoren

[Invocationgroup](#invocation-group)

## <a name="invocationgroup"></a><a name="invocation-group"></a>Invocationgroup

```cpp
InvocationGroup(std::deque<Invocation>&& group);
```

### <a name="parameters"></a>Parameter

*Gruppen*\
Eine Gruppe, die eine Mischung aus [compilerereignissen](../event-table.md#compiler) und [Linker](../event-table.md#linker) -Ereignissen enthält.

::: moniker-end
