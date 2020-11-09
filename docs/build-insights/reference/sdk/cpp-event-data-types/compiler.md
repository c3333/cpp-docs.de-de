---
title: Compiler-Klasse
description: Die Referenz zur Compiler-Klasse im C++ Build Insights SDK.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Compiler
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 52f8bb2ffc474cbf8e58552c77a4bb9fabc13c7e
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "92923320"
---
# <a name="compiler-class"></a>Compiler-Klasse

::: moniker range="<=msvc-140"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Wenn die Dokumentation für diese Versionen angezeigt werden soll, legen Sie das Steuerelement für die Auswahl der **Version** von Visual Studio für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich am Anfang des Inhaltsverzeichnisses auf dieser Seite.

::: moniker-end
::: moniker range=">=msvc-150"

Die `Compiler`-Klasse wird mit den Funktionen [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md) und [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) verwendet. Dient zum Abgleichen eines [COMPILER](../event-table.md#compiler)-Ereignisses.

## <a name="syntax"></a>Syntax

```cpp
class Compiler : public Invocation
{
public:
    Compiler(const RawEvent& event);
};
```

## <a name="members"></a>Member

Zusammen mit den geerbten Membern aus der Basisklasse [Invocation](invocation.md) enthält die `Compiler`-Klasse die folgenden Member:

### <a name="constructors"></a>Konstruktoren

[Compiler](#compiler)

## <a name="compiler"></a><a name="compiler"></a> Compiler

```cpp
Compiler(const RawEvent& event);
```

### <a name="parameters"></a>Parameter

*Ereignis*\
Ein [Compiler](../event-table.md#compiler)-Ereignis.

::: moniker-end
