---
title: Umgebungsvariable-Klasse
description: Der C++ Build Insights SDK-Umgebungsvariablen-Klassen Verweis.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- EnvironmentVariable
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 19e9278e76fb2116dac30a0e790fba86c6c56484
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334925"
---
# <a name="environmentvariable-class"></a>Umgebungsvariable-Klasse

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist kompatibel mit Visual Studio 2017 und höher. Um die Dokumentation für diese Versionen anzuzeigen, legen Sie das Steuerelement für die Visual Studio-Versions Auswahl für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest.

::: moniker-end
::: moniker range=">=vs-2017"

Die `EnvironmentVariable`-Klasse wird mit den Funktionen [matchevent](../functions/match-event.md), [matcheventinmitgliedfunction](../functions/match-event-in-member-function.md), [matcheventstack](../functions/match-event-stack.md)und [matcheventstackinmembership Function](../functions/match-event-stack-in-member-function.md) verwendet. Verwenden Sie es, um ein [ENVIRONMENT_VARIABLE](../event-table.md#environment-variable) Ereignis abzugleichen.

## <a name="syntax"></a>Syntax

```cpp
class EnvironmentVariable : public SimpleEvent
{
public:
    EnvironmentVariable(const RawEvent& event);

    const wchar_t* Name() const;
    const wchar_t* Value() const;
};
```

## <a name="members"></a>Members

Zusammen mit den geerbten Membern aus der [SimpleEvent](simple-event.md) -Basisklasse enthält die `EnvironmentVariable`-Klasse die folgenden Member:

### <a name="constructors"></a>Konstruktoren

[EnvironmentVariable](#environment-variable)

### <a name="functions"></a>Functions

[Name](#name)
[Wert](#value)

## <a name="environment-variable"></a>EnvironmentVariable

```cpp
EnvironmentVariable(const RawEvent& event);
```

### <a name="parameters"></a>Parameter

*Ereignis*\
Ein [ENVIRONMENT_VARIABLE](../event-table.md#environment-variable) Ereignis.

## <a name="name"></a> Name

```cpp
const wchar_t Name() const;
```

### <a name="return-value"></a>Rückgabewert

Der Name der Umgebungsvariablen.

## <a name="value"></a>Wert

```cpp
const wchar_t Value() const;
```

### <a name="return-value"></a>Rückgabewert

Der Wert der Umgebungsvariablen.

::: moniker-end
