---
title: Function-Klasse
description: Die Referenz zur Function-Klasse im C++ Build Insights SDK.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Function
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 874477b9ca31095bfcf4ba3c7a6fd220dc073415
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "92920644"
---
# <a name="function-class"></a>Function-Klasse

::: moniker range="<=msvc-140"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Wenn die Dokumentation für diese Versionen angezeigt werden soll, legen Sie das Steuerelement für die Auswahl der **Version** von Visual Studio für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich am Anfang des Inhaltsverzeichnisses auf dieser Seite.

::: moniker-end
::: moniker range=">=msvc-150"

Die `Function`-Klasse wird mit den Funktionen [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md) und [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) verwendet. Dient zum Abgleichen eines [FUNCTION](../event-table.md#function)-Ereignisses.

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

Zusammen mit den geerbten Membern aus der [Activity](activity.md)-Basisklasse enthält die `Function`-Klasse die folgenden Member:

### <a name="constructors"></a>Konstruktoren

[Function](#function)

### <a name="functions"></a>Functions

[Name](#name)

## <a name="function"></a><a name="function"></a> Function

```cpp
Function(const RawEvent& event);
```

### <a name="parameters"></a>Parameter

*Ereignis*\
Ein [FUNCTION](../event-table.md#function)-Ereignis.

## <a name="name"></a><a name="name"></a> Name

```cpp
const char* Name() const;
```

### <a name="return-value"></a>Rückgabewert

Der in UTF-8 codierte Name der Funktion.

::: moniker-end
