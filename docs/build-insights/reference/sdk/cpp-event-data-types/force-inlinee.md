---
title: Forceingelinee-Klasse
description: Der C++ Build Insights SDK-forceinlinee-Klassen Verweis.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- ForceInlinee
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 7d3cce13601a0b3edbcd2b57664b2d0d94a7d3df
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334835"
---
# <a name="forceinlinee-class"></a>Forceingelinee-Klasse

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist kompatibel mit Visual Studio 2017 und höher. Um die Dokumentation für diese Versionen anzuzeigen, legen Sie das Steuerelement für die Visual Studio-Versions Auswahl für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest.

::: moniker-end
::: moniker range=">=vs-2017"

Die `ForceInlinee`-Klasse wird mit den Funktionen [matchevent](../functions/match-event.md), [matcheventinmitgliedfunction](../functions/match-event-in-member-function.md), [matcheventstack](../functions/match-event-stack.md)und [matcheventstackinmembership Function](../functions/match-event-stack-in-member-function.md) verwendet. Verwenden Sie es, um ein [FORCE_INLINEE](../event-table.md#force-inlinee) Ereignis abzugleichen.

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

## <a name="members"></a>Members

Zusammen mit den geerbten Membern aus der [SimpleEvent](simple-event.md) -Basisklasse enthält die `ForceInlinee`-Klasse die folgenden Member:

### <a name="constructors"></a>Konstruktoren

[Forceingelinee](#force-inlinee)

### <a name="functions"></a>Functions

[Name](#name)
[Größe](#size)

## <a name="force-inlinee"></a>Forceingelinee

```cpp
ForceInlinee(const RawEvent& event);
```

### <a name="parameters"></a>Parameter

*Ereignis*\
Ein [FORCE_INLINEE](../event-table.md#force-inlinee) Ereignis.

## <a name="name"></a> Name

```cpp
const char* Name() const;
```

### <a name="return-value"></a>Rückgabewert

Der Name der in UTF-8 codierten Force-Inline-Funktion.

## <a name="size"></a>Größe

```cpp
const unsigned short& Size() const;
```

### <a name="return-value"></a>Rückgabewert

Die Größe der Force-Inline-Funktion als zwischen Anweisungs Anzahl.

::: moniker-end
