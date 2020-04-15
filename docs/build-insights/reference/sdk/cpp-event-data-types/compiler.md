---
title: Compilerklasse
description: Der C++ Build Insights SDK Compiler-Klassenverweis.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Compiler
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 9b0a2622c4bc0bc19d7222977fe24c060ee8709e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325033"
---
# <a name="compiler-class"></a>Compilerklasse

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Um die Dokumentation zu diesen Versionen anzuzeigen, legen Sie das Visual **Studio-Versionsauswahlsteuerelement** für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich oben im Inhaltsverzeichnis auf dieser Seite.

::: moniker-end
::: moniker range=">=vs-2017"

Die `Compiler` Klasse wird mit den Funktionen [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)und [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) verwendet. Verwenden Sie es, um ein [COMPILER-Ereignis](../event-table.md#compiler) abzugleichen.

## <a name="syntax"></a>Syntax

```cpp
class Compiler : public Invocation
{
public:
    Compiler(const RawEvent& event);
};
```

## <a name="members"></a>Member

Zusammen mit den geerbten Membern aus `Compiler` der [Aufrufbasisklasse](invocation.md) enthält die Klasse die folgenden Member:

### <a name="constructors"></a>Konstruktoren

[Compiler](#compiler)

## <a name="compiler"></a><a name="compiler"></a>Compiler

```cpp
Compiler(const RawEvent& event);
```

### <a name="parameters"></a>Parameter

*Ereignis*\
Ein [COMPILER](../event-table.md#compiler) COMPILER-Ereignis.

::: moniker-end
