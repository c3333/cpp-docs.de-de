---
title: ForceInlinee-Klasse
description: Der C++ Build Insights SDK ForceInlinee-Klassenverweis.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- ForceInlinee
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: c6a1af0384197a0a3b6062ad9ef30537c348190d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324785"
---
# <a name="forceinlinee-class"></a>ForceInlinee-Klasse

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Um die Dokumentation zu diesen Versionen anzuzeigen, legen Sie das Visual **Studio-Versionsauswahlsteuerelement** für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich oben im Inhaltsverzeichnis auf dieser Seite.

::: moniker-end
::: moniker range=">=vs-2017"

Die `ForceInlinee` Klasse wird mit den Funktionen [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)und [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) verwendet. Verwenden Sie es, um ein [FORCE_INLINEE](../event-table.md#force-inlinee) Ereignis abzugleichen.

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

Zusammen mit den geerbten Membern aus `ForceInlinee` der [SimpleEvent-Basisklasse](simple-event.md) enthält die Klasse die folgenden Member:

### <a name="constructors"></a>Konstruktoren

[ForceInlinee](#force-inlinee)

### <a name="functions"></a>Functions

[Namensgröße](#name)
[Size](#size)

## <a name="forceinlinee"></a><a name="force-inlinee"></a>ForceInlinee

```cpp
ForceInlinee(const RawEvent& event);
```

### <a name="parameters"></a>Parameter

*Ereignis*\
Ein [FORCE_INLINEE](../event-table.md#force-inlinee) Ereignis.

## <a name="name"></a><a name="name"></a>Namen

```cpp
const char* Name() const;
```

### <a name="return-value"></a>Rückgabewert

Der Name der force-inlined-Funktion, kodiert in UTF-8.

## <a name="size"></a><a name="size"></a>-Größe

```cpp
const unsigned short& Size() const;
```

### <a name="return-value"></a>Rückgabewert

Die Größe der force-inlined-Funktion als Zwischenanweisungszahl.

::: moniker-end
