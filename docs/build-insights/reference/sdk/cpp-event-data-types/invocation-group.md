---
title: InvocationGroup-Klasse
description: Der C++ Build Insights SDK InvocationGroup-Klassenverweis.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- InvocationGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: ff5a73d5304a21c314c0fc5ce442e0ffc23b28fd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324689"
---
# <a name="invocationgroup-class"></a>InvocationGroup-Klasse

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Um die Dokumentation zu diesen Versionen anzuzeigen, legen Sie das Visual **Studio-Versionsauswahlsteuerelement** für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich oben im Inhaltsverzeichnis auf dieser Seite.

::: moniker-end
::: moniker range=">=vs-2017"

Die `InvocationGroup` Klasse wird mit den Funktionen [MatchEventStack](../functions/match-event-stack.md) und [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) verwendet. Verwenden Sie es, um Gruppen abzugleichen, die eine Mischung aus [COMPILER-](../event-table.md#compiler) und [LINKER-Ereignissen](../event-table.md#linker) enthalten.

## <a name="syntax"></a>Syntax

```cpp
class InvocationGroup : public EventGroup<Invocation>
{
public:
    InvocationGroup(std::deque<Invocation>&& group);
};
```

## <a name="members"></a>Member

Zusammen mit den geerbten Membern aus der `InvocationGroup` [\<EventGroup-Aufrufbasisklasse\> ](event-group.md) enthält die Klasse die folgenden Member:

### <a name="constructors"></a>Konstruktoren

[InvocationGroup](#invocation-group)

## <a name="invocationgroup"></a><a name="invocation-group"></a>InvocationGroup

```cpp
InvocationGroup(std::deque<Invocation>&& group);
```

### <a name="parameters"></a>Parameter

*Gruppe*\
Eine Gruppe, die eine Mischung aus [COMPILER-](../event-table.md#compiler) und [LINKER-Ereignissen](../event-table.md#linker) enthält.

::: moniker-end
