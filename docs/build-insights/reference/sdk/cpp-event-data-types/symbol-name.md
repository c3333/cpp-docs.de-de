---
title: SymbolName-Klasse
description: Die Referenz zur SymbolName-Klasse im C++ Build Insights SDK.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- SymbolName
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: a749d95b3812df8b1cc0cd7d2da037e98467cefc
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "92920475"
---
# <a name="symbolname-class"></a>SymbolName-Klasse

::: moniker range="<=msvc-140"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Wenn die Dokumentation für diese Versionen angezeigt werden soll, legen Sie das Steuerelement für die Auswahl der **Version** von Visual Studio für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich am Anfang des Inhaltsverzeichnisses auf dieser Seite.

::: moniker-end
::: moniker range=">=msvc-150"

Die `SymbolName`-Klasse wird mit den Funktionen [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md) und [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) verwendet. Dient zum Abgleichen eines [SYMBOL_NAME](../event-table.md#symbol-name)-Ereignisses.

## <a name="syntax"></a>Syntax

```cpp
class SymbolName : public SimpleEvent
{
public:
    SymbolName(const RawEvent& event);

    const unsigned long long&  Key() const;
    const char*                Name() const;
};
```

## <a name="members"></a>Member

Zusammen mit den geerbten Membern aus der Basisklasse [SimpleEvent](simple-event.md) enthält die `SymbolName`-Klasse die folgenden Member:

### <a name="constructors"></a>Konstruktoren

[SymbolName](#symbol-name)

### <a name="functions"></a>Functions

[Key](#key)
[Name](#name)

## <a name="key"></a><a name="key"></a> Key

```cpp
const unsigned long long& Key() const;
```

### <a name="return-value"></a>Rückgabewert

Numerischer Bezeichner für den von diesem Symbol dargestellten Typ. Dieser Bezeichner ist innerhalb eines Compiler-Front-End-Durchlaufs eindeutig.

## <a name="name"></a><a name="name"></a> Name

```cpp
const char* Name() const;
```

### <a name="return-value"></a>Rückgabewert

Der Name des Typs, der durch das UTF-8-codierte Symbol dargestellt wird.

## <a name="symbolname"></a><a name="symbol-name"></a> SymbolName

```cpp
SymbolName(const RawEvent& event);
```

### <a name="parameters"></a>Parameter

*Ereignis*\
Ein [SYMBOL_NAME](../event-table.md#symbol-name)-Ereignis.

::: moniker-end
