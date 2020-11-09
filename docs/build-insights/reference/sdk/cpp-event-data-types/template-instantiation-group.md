---
title: TemplateInstantiationGroup-Klasse
description: Die Referenz zur TemplateInstantiationGroup-Klasse im C++ Build Insights SDK.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TemplateInstantiationGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: bacd48fbf15bfbbd768b527f42587425fb0932e6
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "92922971"
---
# <a name="templateinstantiationgroup-class"></a>TemplateInstantiationGroup-Klasse

::: moniker range="<=msvc-140"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Wenn die Dokumentation für diese Versionen angezeigt werden soll, legen Sie das Steuerelement für die Auswahl der **Version** von Visual Studio für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich am Anfang des Inhaltsverzeichnisses auf dieser Seite.

::: moniker-end
::: moniker range=">=msvc-150"

Die `TemplateInstantiationGroup`-Klasse wird mit den Funktionen [MatchEventStack](../functions/match-event-stack.md) und [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) verwendet. Dient zum Abgleichen von Gruppen von [TEMPLATE_INSTANTIATION](../event-table.md#template-instantiation)-Ereignissen.

## <a name="syntax"></a>Syntax

```cpp
class TemplateInstantiationGroup : public EventGroup<TemplateInstantiation>
{
public:
    TemplateInstantiationGroup(std::deque<TemplateInstantiation>&& group);
};
```

## <a name="members"></a>Member

Zusammen mit den geerbten Membern aus der Basisklasse [EventGroup\<TemplateInstantiation\>](event-group.md)enthält die `TemplateInstantiationGroup`-Klasse die folgenden Member:

### <a name="constructors"></a>Konstruktoren

[TemplateInstantiationGroup](#template-instantiation-group)

## <a name="templateinstantiationgroup"></a><a name="template-instantiation-group"></a> TemplateInstantiationGroup

```cpp
TemplateInstantiationGroup(std::deque<TemplateInstantiation>&& group);
```

### <a name="parameters"></a>Parameter

*group*\
Eine Gruppe von [TEMPLATE_INSTANTIATION](../event-table.md#template-instantiation)-Ereignissen.

::: moniker-end
