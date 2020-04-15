---
title: CommandLine-Klasse
description: Der C++ Build Insights SDK CommandLine-Klassenverweis.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- CommandLine
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: b35d688acf06579cc27f2fee053ef58032e204e0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325057"
---
# <a name="commandline-class"></a>CommandLine-Klasse

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Um die Dokumentation zu diesen Versionen anzuzeigen, legen Sie das Visual **Studio-Versionsauswahlsteuerelement** für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich oben im Inhaltsverzeichnis auf dieser Seite.

::: moniker-end
::: moniker range=">=vs-2017"

Die `CommandLine` Klasse wird mit den Funktionen [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)und [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) verwendet. Verwenden Sie es, um ein [COMMAND_LINE](../event-table.md#command-line) Ereignis abzugleichen.

## <a name="syntax"></a>Syntax

```cpp
class CommandLine : public SimpleEvent
{
public:
    CommandLine(const RawEvent& event);

    const wchar_t* Value() const;
};
```

## <a name="members"></a>Member

Zusammen mit den geerbten Membern aus `CommandLine` der [SimpleEvent-Basisklasse](simple-event.md) enthält die Klasse die folgenden Member:

### <a name="constructors"></a>Konstruktoren

[Commandline](#command-line)

### <a name="functions"></a>Functions

[Wert](#value)

## <a name="commandline"></a><a name="command-line"></a>Commandline

```cpp
CommandLine(const RawEvent& event);
```

### <a name="parameters"></a>Parameter

*Ereignis*\
Ein [COMMAND_LINE](../event-table.md#command-line) Ereignis.

## <a name="value"></a><a name="value"></a> Wert

```cpp
const wchar_t Value() const;
```

### <a name="return-value"></a>Rückgabewert

Eine Zeichenfolge, die eine Befehlszeile enthält. Der Wert enthält Argumente, die aus einer Antwortdatei und \_\_aus Umgebungsvariablen wie CL, CL , Link und \_LINK\_abgerufen wurden.

::: moniker-end
