---
title: Thread-Klasse
description: Der C++ Build Insights SDK-Threadklassenverweis.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Thread
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 397083c63f451b2d3fb8dad529adf73855af8644
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324194"
---
# <a name="thread-class"></a>Thread-Klasse

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Um die Dokumentation zu diesen Versionen anzuzeigen, legen Sie das Visual **Studio-Versionsauswahlsteuerelement** für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich oben im Inhaltsverzeichnis auf dieser Seite.

::: moniker-end
::: moniker range=">=vs-2017"

Die `Thread` Klasse wird mit den Funktionen [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)und [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) verwendet. Verwenden Sie es, um einem [THREAD-Ereignis](../event-table.md#thread) zu entsprechen.

## <a name="syntax"></a>Syntax

```cpp
class Thread : public Activity
{
public:
    Thread(const RawEvent& event);
};
```

## <a name="members"></a>Member

Zusammen mit den geerbten Membern aus `Thread` der Aktivitätsbasisklasse enthält die Klasse die folgenden Member: [Activity](activity.md)

### <a name="constructors"></a>Konstruktoren

[Thread](#thread)

## <a name="thread"></a><a name="thread"></a>Thread

```cpp
Thread(const RawEvent& event);
```

### <a name="parameters"></a>Parameter

*Ereignis*\
Ein [THREAD](../event-table.md#thread) THREAD-Ereignis.

::: moniker-end
