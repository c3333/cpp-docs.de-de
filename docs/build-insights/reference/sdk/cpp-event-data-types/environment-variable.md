---
title: EnvironmentVariable-Klasse
description: Die Referenz zur EnvironmentVariable-Klasse im C++ Build Insights SDK.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- EnvironmentVariable
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: f707ab744aaf6097975ba9e189815df3c9f32266
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "92920762"
---
# <a name="environmentvariable-class"></a>EnvironmentVariable-Klasse

::: moniker range="<=msvc-140"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Wenn die Dokumentation für diese Versionen angezeigt werden soll, legen Sie das Steuerelement für die Auswahl der **Version** von Visual Studio für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich am Anfang des Inhaltsverzeichnisses auf dieser Seite.

::: moniker-end
::: moniker range=">=msvc-150"

Die `EnvironmentVariable`-Klasse wird mit den Funktionen [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md) und [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) verwendet. Dient zum Abgleichen eines [ENVIRONMENT_VARIABLE](../event-table.md#environment-variable)-Ereignisses.

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

## <a name="members"></a>Member

Zusammen mit den geerbten Membern aus der Basisklasse [SimpleEvent](simple-event.md) enthält die `EnvironmentVariable`-Klasse die folgenden Member:

### <a name="constructors"></a>Konstruktoren

[EnvironmentVariable](#environment-variable)

### <a name="functions"></a>Functions

[Name](#name)
[Wert](#value)

## <a name="environmentvariable"></a><a name="environment-variable"></a> EnvironmentVariable

```cpp
EnvironmentVariable(const RawEvent& event);
```

### <a name="parameters"></a>Parameter

*Ereignis*\
Ein [ENVIRONMENT_VARIABLE](../event-table.md#environment-variable)-Ereignis.

## <a name="name"></a><a name="name"></a> Name

```cpp
const wchar_t Name() const;
```

### <a name="return-value"></a>Rückgabewert

Der Name der Umgebungsvariablen.

## <a name="value"></a><a name="value"></a>-Wert

```cpp
const wchar_t Value() const;
```

### <a name="return-value"></a>Rückgabewert

Der Wert der Umgebungsvariablen.

::: moniker-end
