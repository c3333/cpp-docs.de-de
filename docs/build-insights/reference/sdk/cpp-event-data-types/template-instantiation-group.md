---
title: TemplateInstantiationGroup-Klasse
description: Der C++ Build Insights SDK TemplateInstantiationGroup-Klassenverweis.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TemplateInstantiationGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 18dd48219c7c68ce152c381eb505fe37b19ec8dd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324260"
---
# <a name="templateinstantiationgroup-class"></a>TemplateInstantiationGroup-Klasse

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Um die Dokumentation zu diesen Versionen anzuzeigen, legen Sie das Visual **Studio-Versionsauswahlsteuerelement** für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich oben im Inhaltsverzeichnis auf dieser Seite.

::: moniker-end
::: moniker range=">=vs-2017"

Die `TemplateInstantiationGroup` Klasse wird mit den Funktionen [MatchEventStack](../functions/match-event-stack.md) und [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) verwendet. Verwenden Sie es, um Gruppen von [TEMPLATE_INSTANTIATION](../event-table.md#template-instantiation) Ereignissen abzugleichen.

## <a name="syntax"></a>Syntax

```cpp
class TemplateInstantiationGroup : public EventGroup<TemplateInstantiation>
{
public:
    TemplateInstantiationGroup(std::deque<TemplateInstantiation>&& group);
};
```

## <a name="members"></a>Member

Zusammen mit den geerbten Membern aus der [EventGroup\<\> TemplateInstantiation-Basisklasse](event-group.md) enthält die `TemplateInstantiationGroup` Klasse die folgenden Member:

### <a name="constructors"></a>Konstruktoren

[TemplateInstantiationGroup](#template-instantiation-group)

## <a name="templateinstantiationgroup"></a><a name="template-instantiation-group"></a>TemplateInstantiationGroup

```cpp
TemplateInstantiationGroup(std::deque<TemplateInstantiation>&& group);
```

### <a name="parameters"></a>Parameter

*Gruppe*\
Eine Gruppe von [TEMPLATE_INSTANTIATION](../event-table.md#template-instantiation) Ereignissen.

::: moniker-end
