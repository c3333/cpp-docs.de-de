---
title: Thread-Klasse
description: Der C++ Build Insights SDK-Thread Klassen Verweis.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Thread
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: a74eb130bd3f8be949fef0c19d545f61a72f3934
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334517"
---
# <a name="thread-class"></a>Thread-Klasse

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist kompatibel mit Visual Studio 2017 und höher. Um die Dokumentation für diese Versionen anzuzeigen, legen Sie das Steuerelement für die Visual Studio-Versions Auswahl für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest.

::: moniker-end
::: moniker range=">=vs-2017"

Die `Thread`-Klasse wird mit den Funktionen [matchevent](../functions/match-event.md), [matcheventinmitgliedfunction](../functions/match-event-in-member-function.md), [matcheventstack](../functions/match-event-stack.md)und [matcheventstackinmembership Function](../functions/match-event-stack-in-member-function.md) verwendet. Verwenden Sie es, um ein [Thread](../event-table.md#thread) Ereignis abzugleichen.

## <a name="syntax"></a>Syntax

```cpp
class Thread : public Activity
{
public:
    Thread(const RawEvent& event);
};
```

## <a name="members"></a>Members

Zusammen mit den geerbten Membern der [Aktivitäts](activity.md) Basisklasse enthält die `Thread`-Klasse die folgenden Member:

### <a name="constructors"></a>Konstruktoren

[Thread](#thread)

## <a name="thread"></a>Aden

```cpp
Thread(const RawEvent& event);
```

### <a name="parameters"></a>Parameter

*Ereignis*\
Ein [Thread](../event-table.md#thread) Ereignis.

::: moniker-end
