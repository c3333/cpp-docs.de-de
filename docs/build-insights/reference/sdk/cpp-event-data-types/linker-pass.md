---
title: LinkerPass-Klasse
description: Die C++ Build Insights SDK LinkerPass-Klassenreferenz.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- LinkerPass
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 2b0c5a02958560faeff30500543b6e6d4921ac52
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324615"
---
# <a name="linkerpass-class"></a>LinkerPass-Klasse

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Um die Dokumentation zu diesen Versionen anzuzeigen, legen Sie das Visual **Studio-Versionsauswahlsteuerelement** für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich oben im Inhaltsverzeichnis auf dieser Seite.

::: moniker-end
::: moniker range=">=vs-2017"

Die `LinkerPass` Klasse wird mit den Funktionen [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)und [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) verwendet. Verwenden Sie es, um ein [PASS1-](../event-table.md#pass1) oder [PASS2-Ereignis](../event-table.md#pass2) abzugleichen.

## <a name="syntax"></a>Syntax

```cpp
class LinkerPass : public Activity
{
public:
    LinkerPass(const RawEvent& event);
};
```

## <a name="members"></a>Member

Zusammen mit den geerbten Membern aus `LinkerPass` der Aktivitätsbasisklasse enthält die Klasse die folgenden Member: [Activity](activity.md)

### <a name="constructors"></a>Konstruktoren

[LinkerPass](#linker-pass)

## <a name="linkerpass"></a><a name="linker-pass"></a>LinkerPass

```cpp
LinkerPass(const RawEvent& event);
```

### <a name="parameters"></a>Parameter

*Ereignis*\
Ein [PASS1-](../event-table.md#pass1) oder [PASS2-Ereignis.](../event-table.md#pass2)

::: moniker-end
