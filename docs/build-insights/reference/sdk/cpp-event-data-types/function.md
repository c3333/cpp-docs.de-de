---
title: Function-Klasse
description: Der C++ Build Insights SDK-Funktionsklassen Verweis.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Function
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 3ff66119007ed7172fed7e824287ab8617c70973
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334769"
---
# <a name="function-class"></a>Function-Klasse

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist kompatibel mit Visual Studio 2017 und höher. Um die Dokumentation für diese Versionen anzuzeigen, legen Sie das Steuerelement für die Visual Studio-Versions Auswahl für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest.

::: moniker-end
::: moniker range=">=vs-2017"

Die `Function`-Klasse wird mit den Funktionen [matchevent](../functions/match-event.md), [matcheventinmitgliedfunction](../functions/match-event-in-member-function.md), [matcheventstack](../functions/match-event-stack.md)und [matcheventstackinmembership Function](../functions/match-event-stack-in-member-function.md) verwendet. Verwenden Sie es, um ein [Funktions](../event-table.md#function) Ereignis abzugleichen.

## <a name="syntax"></a>Syntax

```cpp
class Function : public Activity
{
public:
    Function(const RawEvent& event);

    const char* Name() const;
};
```

## <a name="members"></a>Members

Zusammen mit den geerbten Membern der [Aktivitäts](activity.md) Basisklasse enthält die `Function`-Klasse die folgenden Member:

### <a name="constructors"></a>Konstruktoren

[Function](#function)

### <a name="functions"></a>Functions

[Name](#name)

## <a name="function"></a>Funktion

```cpp
Function(const RawEvent& event);
```

### <a name="parameters"></a>Parameter

*Ereignis*\
Ein [Funktions](../event-table.md#function) Ereignis.

## <a name="name"></a> Name

```cpp
const char* Name() const;
```

### <a name="return-value"></a>Rückgabewert

Der Name der Funktion, die in UTF-8 codiert ist.

::: moniker-end
