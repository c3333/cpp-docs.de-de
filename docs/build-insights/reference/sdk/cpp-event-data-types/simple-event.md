---
title: SimpleEvent-Klasse
description: Die C++ Referenz für den Build Insights SDK SimpleEvent-Klasse.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- SimpleEvent
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 4c30f81236138328322d8c870d4ad69d9988b49a
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334589"
---
# <a name="simpleevent-class"></a>SimpleEvent-Klasse

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist kompatibel mit Visual Studio 2017 und höher. Um die Dokumentation für diese Versionen anzuzeigen, legen Sie das Steuerelement für die Visual Studio-Versions Auswahl für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest.

::: moniker-end
::: moniker range=">=vs-2017"

Die `SimpleEvent`-Klasse wird mit den Funktionen [matchevent](../functions/match-event.md), [matcheventinmitgliedfunction](../functions/match-event-in-member-function.md), [matcheventstack](../functions/match-event-stack.md)und [matcheventstackinmembership Function](../functions/match-event-stack-in-member-function.md) verwendet. Verwenden Sie es, um eine Entsprechung für jedes einfache Ereignis In der [Ereignis Tabelle](../event-table.md) finden Sie alle Ereignisse, die mit der `SimpleEvent`-Klasse abgeglichen werden können.

## <a name="syntax"></a>Syntax

```cpp
class SimpleEvent : public Event
{
public:
    SimpleEvent(const RawEvent& event);
};
```

## <a name="members"></a>Members

Zusammen mit den geerbten Membern aus der [Ereignis](event.md) Basisklasse enthält die `SimpleEvent`-Klasse die folgenden Member:

### <a name="constructors"></a>Konstruktoren

[SimpleEvent](#simple-event)

## <a name="simple-event"></a>SimpleEvent

```cpp
SimpleEvent(const RawEvent& event);
```

### <a name="parameters"></a>Parameter

*Ereignis*\
Jedes einfache Ereignis.

::: moniker-end
