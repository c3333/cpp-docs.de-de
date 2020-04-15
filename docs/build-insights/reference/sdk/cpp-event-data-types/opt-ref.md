---
title: OptRef-Klasse
description: Der C++ Build Insights SDK OptRef-Klassenverweis.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- OptRef
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: dca8cc62eed4b7136f88ed5ba6a1a168b2de56c3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324451"
---
# <a name="optref-class"></a>OptRef-Klasse

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Um die Dokumentation zu diesen Versionen anzuzeigen, legen Sie das Visual **Studio-Versionsauswahlsteuerelement** für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich oben im Inhaltsverzeichnis auf dieser Seite.

::: moniker-end
::: moniker range=">=vs-2017"

Die `OptRef` Klasse wird mit den Funktionen [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)und [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) verwendet. Verwenden Sie es, um ein [OPT_REF](../event-table.md#opt-ref) Ereignis abzugleichen.

## <a name="syntax"></a>Syntax

```cpp
class OptRef : public Activity
{
public:
    OptRef(const RawEvent& event);
};
```

## <a name="members"></a>Member

Zusammen mit den geerbten Membern aus `OptRef` der Aktivitätsbasisklasse enthält die Klasse die folgenden Member: [Activity](activity.md)

### <a name="constructors"></a>Konstruktoren

[OptRef](#opt-ref)

## <a name="optref"></a><a name="opt-ref"></a>OptRef

```cpp
OptRef(const RawEvent& event);
```

### <a name="parameters"></a>Parameter

*Ereignis*\
Ein [OPT_REF](../event-table.md#opt-ref) Ereignis.

::: moniker-end
