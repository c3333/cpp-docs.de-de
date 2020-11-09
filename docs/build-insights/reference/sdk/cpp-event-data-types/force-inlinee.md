---
title: ForceInlinee-Klasse
description: Die Referenz zur ForceInlinee-Klasse im C++ Build Insights SDK.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- ForceInlinee
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 53fff7b6cfd37ba3e3211dd072c1ce3386d00fda
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "92920670"
---
# <a name="forceinlinee-class"></a>ForceInlinee-Klasse

::: moniker range="<=msvc-140"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Wenn die Dokumentation für diese Versionen angezeigt werden soll, legen Sie das Steuerelement für die Auswahl der **Version** von Visual Studio für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich am Anfang des Inhaltsverzeichnisses auf dieser Seite.

::: moniker-end
::: moniker range=">=msvc-150"

Die `ForceInlinee`-Klasse wird mit den Funktionen [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md) und [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) verwendet. Dient zum Abgleichen eines [FORCE_INLINEE](../event-table.md#force-inlinee)-Ereignisses.

## <a name="syntax"></a>Syntax

```cpp
class ForceInlinee : public SimpleEvent
{
public:
    ForceInlinee(const RawEvent& event);

    const char*             Name() const;
    const unsigned short&   Size() const;
};
```

## <a name="members"></a>Member

Zusammen mit den geerbten Membern aus der Basisklasse [SimpleEvent](simple-event.md) enthält die `ForceInlinee`-Klasse die folgenden Member:

### <a name="constructors"></a>Konstruktoren

[ForceInlinee](#force-inlinee)

### <a name="functions"></a>Functions

[Name](#name)
[Size](#size)

## <a name="forceinlinee"></a><a name="force-inlinee"></a> ForceInlinee

```cpp
ForceInlinee(const RawEvent& event);
```

### <a name="parameters"></a>Parameter

*Ereignis*\
Ein [FORCE_INLINEE](../event-table.md#force-inlinee)-Ereignis.

## <a name="name"></a><a name="name"></a> Name

```cpp
const char* Name() const;
```

### <a name="return-value"></a>Rückgabewert

Der Name der erzwungenen UTF-8-codierten Inlinefunktion.

## <a name="size"></a><a name="size"></a>-Größe

```cpp
const unsigned short& Size() const;
```

### <a name="return-value"></a>Rückgabewert

Die Größe der erzwungenen Inlinefunktion als Anzahl von Zwischenanweisungen.

::: moniker-end
