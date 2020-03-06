---
title: Templateingestantiationgroup-Klasse
description: Der C++ buildinsights-SDK-templateinstantiationgroup-Klassen Verweis.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TemplateInstantiationGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 281088b4c6cbd39b2fb7677180a7966b490ec3ac
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334541"
---
# <a name="templateinstantiationgroup-class"></a>Templateingestantiationgroup-Klasse

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist kompatibel mit Visual Studio 2017 und höher. Um die Dokumentation für diese Versionen anzuzeigen, legen Sie das Steuerelement für die Visual Studio-Versions Auswahl für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest.

::: moniker-end
::: moniker range=">=vs-2017"

Die `TemplateInstantiationGroup`-Klasse wird mit den Funktionen [matcheventstack](../functions/match-event-stack.md) und [matcheventstackinmembership Function](../functions/match-event-stack-in-member-function.md) verwendet. Verwenden Sie ihn, um Gruppen von [TEMPLATE_INSTANTIATION](../event-table.md#template-instantiation) Ereignissen abzugleichen.

## <a name="syntax"></a>Syntax

```cpp
class TemplateInstantiationGroup : public EventGroup<TemplateInstantiation>
{
public:
    TemplateInstantiationGroup(std::deque<TemplateInstantiation>&& group);
};
```

## <a name="members"></a>Members

Zusammen mit den geerbten Membern aus der [Ereignis Gruppe\<templateinstantiations\>](event-group.md) Basisklasse enthält die `TemplateInstantiationGroup`-Klasse die folgenden Member:

### <a name="constructors"></a>Konstruktoren

[Templateingestantiationgroup](#template-instantiation-group)

## <a name="template-instantiation-group"></a>Templateingestantiationgroup

```cpp
TemplateInstantiationGroup(std::deque<TemplateInstantiation>&& group);
```

### <a name="parameters"></a>Parameter

*Gruppen*\
Eine Gruppe von [TEMPLATE_INSTANTIATION](../event-table.md#template-instantiation) Ereignissen.

::: moniker-end
