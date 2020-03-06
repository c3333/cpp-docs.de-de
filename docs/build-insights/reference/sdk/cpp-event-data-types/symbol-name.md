---
title: Symbolname-Klasse
description: Die C++ Build Insights SDK-Symbolname-Klassenreferenz.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- SymbolName
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: b5e9a9b22db99c099b9f7dc1813fb335358a83e8
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334547"
---
# <a name="symbolname-class"></a>Symbolname-Klasse

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist kompatibel mit Visual Studio 2017 und höher. Um die Dokumentation für diese Versionen anzuzeigen, legen Sie das Steuerelement für die Visual Studio-Versions Auswahl für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest.

::: moniker-end
::: moniker range=">=vs-2017"

Die `SymbolName`-Klasse wird mit den Funktionen [matchevent](../functions/match-event.md), [matcheventinmitgliedfunction](../functions/match-event-in-member-function.md), [matcheventstack](../functions/match-event-stack.md)und [matcheventstackinmembership Function](../functions/match-event-stack-in-member-function.md) verwendet. Verwenden Sie es, um ein [SYMBOL_NAME](../event-table.md#symbol-name) Ereignis abzugleichen.

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

## <a name="members"></a>Members

Zusammen mit den geerbten Membern aus der [SimpleEvent](simple-event.md) -Basisklasse enthält die `SymbolName`-Klasse die folgenden Member:

### <a name="constructors"></a>Konstruktoren

[Symbolname](#symbol-name)

### <a name="functions"></a>Functions

[Schlüssel](#key)
[Name](#name)

## <a name="key"></a>Wichtigen

```cpp
const unsigned long long& Key() const;
```

### <a name="return-value"></a>Rückgabewert

Ein numerischer Bezeichner für den durch dieses Symbol dargestellten Typ. Dieser Bezeichner ist innerhalb eines compilerfront-End-bestanden eindeutig.

## <a name="name"></a> Name

```cpp
const char* Name() const;
```

### <a name="return-value"></a>Rückgabewert

Der Name des durch das Symbol dargestellten Typs, der in UTF-8 codiert ist.

## <a name="symbol-name"></a>Symbolname

```cpp
SymbolName(const RawEvent& event);
```

### <a name="parameters"></a>Parameter

*Ereignis*\
Ein [SYMBOL_NAME](../event-table.md#symbol-name) Ereignis.

::: moniker-end
