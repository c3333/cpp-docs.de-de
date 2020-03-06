---
title: Optlbr-Klasse
description: Der C++ Build Insights SDK-optlbr-Klassen Verweis.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- OptLBR
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: fb2482ce943dbf393e74d6398498cc185410140a
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334631"
---
# <a name="optlbr-class"></a>Optlbr-Klasse

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist kompatibel mit Visual Studio 2017 und höher. Um die Dokumentation für diese Versionen anzuzeigen, legen Sie das Steuerelement für die Visual Studio-Versions Auswahl für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest.

::: moniker-end
::: moniker range=">=vs-2017"

Die `OptLBR`-Klasse wird mit den Funktionen [matchevent](../functions/match-event.md), [matcheventinmitgliedfunction](../functions/match-event-in-member-function.md), [matcheventstack](../functions/match-event-stack.md)und [matcheventstackinmembership Function](../functions/match-event-stack-in-member-function.md) verwendet. Verwenden Sie es, um ein [OPT_LBR](../event-table.md#opt-lbr) Ereignis abzugleichen.

## <a name="syntax"></a>Syntax

```cpp
class OptLBR : public Activity
{
public:
    OptLBR(const RawEvent& event);
};
```

## <a name="members"></a>Members

Zusammen mit den geerbten Membern der [Aktivitäts](activity.md) Basisklasse enthält die `OptLBR`-Klasse die folgenden Member:

### <a name="constructors"></a>Konstruktoren

[Optlbr](#opt-lbr)

## <a name="opt-lbr"></a>Optlbr

```cpp
OptLBR(const RawEvent& event);
```

### <a name="parameters"></a>Parameter

*Ereignis*\
Ein [OPT_LBR](../event-table.md#opt-lbr) Ereignis.

::: moniker-end
