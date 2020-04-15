---
title: Funktionsklasse
description: Der C++ Build Insights SDK-Funktionsklassenverweis.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Function
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 69acbe4d6630de37120aec89a24a9f33d447009e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324712"
---
# <a name="function-class"></a>Funktionsklasse

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Um die Dokumentation zu diesen Versionen anzuzeigen, legen Sie das Visual **Studio-Versionsauswahlsteuerelement** für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich oben im Inhaltsverzeichnis auf dieser Seite.

::: moniker-end
::: moniker range=">=vs-2017"

Die `Function` Klasse wird mit den Funktionen [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)und [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) verwendet. Verwenden Sie es, um ein [FUNCTION-Ereignis](../event-table.md#function) abzugleichen.

## <a name="syntax"></a>Syntax

```cpp
class Function : public Activity
{
public:
    Function(const RawEvent& event);

    const char* Name() const;
};
```

## <a name="members"></a>Member

Zusammen mit den geerbten Membern aus `Function` der Aktivitätsbasisklasse enthält die Klasse die folgenden Member: [Activity](activity.md)

### <a name="constructors"></a>Konstruktoren

[Funktion](#function)

### <a name="functions"></a>Functions

[Name](#name)

## <a name="function"></a><a name="function"></a>Funktion

```cpp
Function(const RawEvent& event);
```

### <a name="parameters"></a>Parameter

*Ereignis*\
Ein [FUNCTION](../event-table.md#function) FUNCTION-Ereignis.

## <a name="name"></a><a name="name"></a>Namen

```cpp
const char* Name() const;
```

### <a name="return-value"></a>Rückgabewert

Der Name der Funktion, kodiert in UTF-8.

::: moniker-end
