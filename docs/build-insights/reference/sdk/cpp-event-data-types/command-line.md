---
title: CommandLine-Klasse
description: Die Referenz zur CommandLine-Klasse im C++ Build Insights SDK.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- CommandLine
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 5214f2970329510088184dc3092db66607f4d67e
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "92923340"
---
# <a name="commandline-class"></a>CommandLine-Klasse

::: moniker range="<=msvc-140"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Wenn die Dokumentation für diese Versionen angezeigt werden soll, legen Sie das Steuerelement für die Auswahl der **Version** von Visual Studio für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich am Anfang des Inhaltsverzeichnisses auf dieser Seite.

::: moniker-end
::: moniker range=">=msvc-150"

Die `CommandLine`-Klasse wird mit den Funktionen [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md) und [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) verwendet. Dient zum Abgleichen eines [COMMAND_LINE](../event-table.md#command-line)-Ereignisses.

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

Zusammen mit den geerbten Membern aus der Basisklasse [SimpleEvent](simple-event.md) enthält die `CommandLine`-Klasse die folgenden Member:

### <a name="constructors"></a>Konstruktoren

[CommandLine](#command-line)

### <a name="functions"></a>Functions

[Wert](#value)

## <a name="commandline"></a><a name="command-line"></a> CommandLine

```cpp
CommandLine(const RawEvent& event);
```

### <a name="parameters"></a>Parameter

*Ereignis*\
Ein [COMMAND_LINE](../event-table.md#command-line)-Ereignis.

## <a name="value"></a><a name="value"></a>-Wert

```cpp
const wchar_t Value() const;
```

### <a name="return-value"></a>Rückgabewert

Eine Zeichenfolge mit einer Befehlszeile. Der Wert enthält Argumente, die aus einer Antwortdatei und Umgebungsvariablen wie CL, \_CL\_, Link und \_LINK\_ abgerufen wurden.

::: moniker-end
