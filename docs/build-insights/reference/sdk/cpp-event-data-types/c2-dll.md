---
title: C2DLL-Klasse
description: Die Referenz zur C2DLL-Klasse im C++ Build Insights SDK.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- C2DLL
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 81aa4722d918646a0275099879bfee567ebc8f22
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "92923372"
---
# <a name="c2dll-class"></a>C2DLL-Klasse

::: moniker range="<=msvc-140"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Wenn die Dokumentation für diese Versionen angezeigt werden soll, legen Sie das Steuerelement für die Auswahl der **Version** von Visual Studio für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich am Anfang des Inhaltsverzeichnisses auf dieser Seite.

::: moniker-end
::: moniker range=">=msvc-150"

Die `C2DLL`-Klasse wird mit den Funktionen [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md) und [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) verwendet. Dient zum Abgleichen eines [C2_DLL](../event-table.md#c2-dll)-Ereignisses.

## <a name="syntax"></a>Syntax

```cpp
class C2DLL : public Activity
{
public:
    C2DLL(const RawEvent& event);
};
```

## <a name="members"></a>Member

Zusammen mit den geerbten Membern aus der [Activity](activity.md)-Basisklasse enthält die `C2DLL`-Klasse die folgenden Member:

### <a name="constructors"></a>Konstruktoren

[C2DLL](#c2-dll)

## <a name="c2dll"></a><a name="c2-dll"></a> C2DLL

```cpp
C2DLL(const RawEvent& event);
```

### <a name="parameters"></a>Parameter

*Ereignis*\
Ein [C2_DLL](../event-table.md#c2-dll)-Ereignis.

::: moniker-end
