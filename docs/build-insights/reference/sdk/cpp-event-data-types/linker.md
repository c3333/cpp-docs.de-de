---
title: Linker-Klasse
description: Der C++ Build Insights SDK Linker-Klassenverweis.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Linker
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: e5d4c0c3841377fc2e029c23d5cbbd076c8029cc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324601"
---
# <a name="linker-class"></a>Linker-Klasse

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Um die Dokumentation zu diesen Versionen anzuzeigen, legen Sie das Visual **Studio-Versionsauswahlsteuerelement** für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich oben im Inhaltsverzeichnis auf dieser Seite.

::: moniker-end
::: moniker range=">=vs-2017"

Die `Linker` Klasse wird mit den Funktionen [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)und [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) verwendet. Verwenden Sie es, um ein [LINKER-Ereignis](../event-table.md#linker) abzugleichen.

## <a name="syntax"></a>Syntax

```cpp
class Linker : public Invocation
{
public:
    Linker(const RawEvent& event);
};
```

## <a name="members"></a>Member

Zusammen mit den geerbten Membern aus `Linker` der [Aufrufbasisklasse](invocation.md) enthält die Klasse die folgenden Member:

### <a name="constructors"></a>Konstruktoren

[Linker](#linker)

## <a name="linker"></a><a name="linker"></a>Linker

```cpp
Linker(const RawEvent& event);
```

### <a name="parameters"></a>Parameter

*Ereignis*\
Ein [LINKER-Ereignis.](../event-table.md#linker)

::: moniker-end
