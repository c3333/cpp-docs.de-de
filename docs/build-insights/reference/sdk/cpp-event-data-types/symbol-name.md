---
title: SymbolName-Klasse
description: Der C++ Build Insights SDK SymbolName-Klassenverweis.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- SymbolName
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 1306fb43d6c2140a75b36c5f142532916cf26ae4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324358"
---
# <a name="symbolname-class"></a>SymbolName-Klasse

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Um die Dokumentation zu diesen Versionen anzuzeigen, legen Sie das Visual **Studio-Versionsauswahlsteuerelement** für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich oben im Inhaltsverzeichnis auf dieser Seite.

::: moniker-end
::: moniker range=">=vs-2017"

Die `SymbolName` Klasse wird mit den Funktionen [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)und [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) verwendet. Verwenden Sie es, um ein [SYMBOL_NAME](../event-table.md#symbol-name) Ereignis abzugleichen.

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

Zusammen mit den geerbten Membern aus `SymbolName` der [SimpleEvent-Basisklasse](simple-event.md) enthält die Klasse die folgenden Member:

### <a name="constructors"></a>Konstruktoren

[Symbolname](#symbol-name)

### <a name="functions"></a>Functions

[Schlüsselname](#key)
[Name](#name)

## <a name="key"></a><a name="key"></a>Schlüssel

```cpp
const unsigned long long& Key() const;
```

### <a name="return-value"></a>Rückgabewert

Ein numerischer Bezeichner für den Typ, der durch dieses Symbol dargestellt wird. Dieser Bezeichner ist innerhalb eines Compiler-Front-End-Passes eindeutig.

## <a name="name"></a><a name="name"></a>Namen

```cpp
const char* Name() const;
```

### <a name="return-value"></a>Rückgabewert

Der Name des Typs, der durch das Symbol dargestellt wird, kodiert in UTF-8.

## <a name="symbolname"></a><a name="symbol-name"></a>Symbolname

```cpp
SymbolName(const RawEvent& event);
```

### <a name="parameters"></a>Parameter

*Ereignis*\
Ein [SYMBOL_NAME](../event-table.md#symbol-name) SYMBOL_NAME-Ereignis.

::: moniker-end
