---
title: EnvironmentVariable-Klasse
description: Der C++ Build Insights SDK EnvironmentVariable-Klassenverweis.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- EnvironmentVariable
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 963c52e0ea9e048448c6f2b3ac62d9938817467e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325018"
---
# <a name="environmentvariable-class"></a>EnvironmentVariable-Klasse

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Um die Dokumentation zu diesen Versionen anzuzeigen, legen Sie das Visual **Studio-Versionsauswahlsteuerelement** für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich oben im Inhaltsverzeichnis auf dieser Seite.

::: moniker-end
::: moniker range=">=vs-2017"

Die `EnvironmentVariable` Klasse wird mit den Funktionen [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)und [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) verwendet. Verwenden Sie es, um ein [ENVIRONMENT_VARIABLE](../event-table.md#environment-variable) Ereignis abzugleichen.

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

Zusammen mit den geerbten Membern aus `EnvironmentVariable` der [SimpleEvent-Basisklasse](simple-event.md) enthält die Klasse die folgenden Member:

### <a name="constructors"></a>Konstruktoren

[EnvironmentVariable](#environment-variable)

### <a name="functions"></a>Functions

[Name](#name)
[Name-Wert](#value)

## <a name="environmentvariable"></a><a name="environment-variable"></a>UmweltVariable

```cpp
EnvironmentVariable(const RawEvent& event);
```

### <a name="parameters"></a>Parameter

*Ereignis*\
Ein [ENVIRONMENT_VARIABLE](../event-table.md#environment-variable) Ereignis.

## <a name="name"></a><a name="name"></a>Namen

```cpp
const wchar_t Name() const;
```

### <a name="return-value"></a>Rückgabewert

Der Name der Umgebungsvariablen.

## <a name="value"></a><a name="value"></a> Wert

```cpp
const wchar_t Value() const;
```

### <a name="return-value"></a>Rückgabewert

Der Wert der Umgebungsvariablen.

::: moniker-end
