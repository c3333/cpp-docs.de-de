---
title: BottomUp-Klasse
description: Der C++ Build Insights SDK-Klassen Verweis in der Klasse.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- BottomUp
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: fa26acfdf25acc3b78de71fd21b20cbf5a0df66b
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2020
ms.locfileid: "78335009"
---
# <a name="bottomup-class"></a>BottomUp-Klasse

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist kompatibel mit Visual Studio 2017 und höher. Um die Dokumentation für diese Versionen anzuzeigen, legen Sie das Steuerelement für die Visual Studio-Versions Auswahl für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest.

::: moniker-end
::: moniker range=">=vs-2017"

Die `BottomUp`-Klasse wird mit den Funktionen [matchevent](../functions/match-event.md), [matcheventinmitgliedfunction](../functions/match-event-in-member-function.md), [matcheventstack](../functions/match-event-stack.md)und [matcheventstackinmembership Function](../functions/match-event-stack-in-member-function.md) verwendet. Verwenden Sie es, um ein [BOTTOM_UP](../event-table.md#bottom-up) Ereignis abzugleichen.

## <a name="syntax"></a>Syntax

```cpp
class BottomUp : public Activity
{
public:
    BottomUp(const RawEvent& event);
};
```

## <a name="members"></a>Members

Zusammen mit den geerbten Membern der [Aktivitäts](activity.md) Basisklasse enthält die `BottomUp`-Klasse die folgenden Member:

### <a name="constructors"></a>Konstruktoren

[Nach unten](#bottom-up)

## <a name="bottom-up"></a>Nach unten

```cpp
BottomUp(const RawEvent& event);
```

### <a name="parameters"></a>Parameter

*Ereignis*\
Ein [BOTTOM_UP](../event-table.md#bottom-up) Ereignis.

::: moniker-end
