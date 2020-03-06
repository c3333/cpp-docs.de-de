---
title: CommandLine-Klasse
description: Die C++ Befehlszeilen-Klassenreferenz für das Build Insights SDK.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- CommandLine
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: ff16646920fe77f7f3b4cb8a194a38984c3e6c32
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334985"
---
# <a name="commandline-class"></a>CommandLine-Klasse

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist kompatibel mit Visual Studio 2017 und höher. Um die Dokumentation für diese Versionen anzuzeigen, legen Sie das Steuerelement für die Visual Studio-Versions Auswahl für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest.

::: moniker-end
::: moniker range=">=vs-2017"

Die `CommandLine`-Klasse wird mit den Funktionen [matchevent](../functions/match-event.md), [matcheventinmitgliedfunction](../functions/match-event-in-member-function.md), [matcheventstack](../functions/match-event-stack.md)und [matcheventstackinmembership Function](../functions/match-event-stack-in-member-function.md) verwendet. Verwenden Sie es, um ein [command_line](../event-table.md#command-line) Ereignis abzugleichen.

## <a name="syntax"></a>Syntax

```cpp
class CommandLine : public SimpleEvent
{
public:
    CommandLine(const RawEvent& event);

    const wchar_t* Value() const;
};
```

## <a name="members"></a>Members

Zusammen mit den geerbten Membern aus der [SimpleEvent](simple-event.md) -Basisklasse enthält die `CommandLine`-Klasse die folgenden Member:

### <a name="constructors"></a>Konstruktoren

[CommandLine](#command-line)

### <a name="functions"></a>Functions

[Wert](#value)

## <a name="command-line"></a>CommandLine

```cpp
CommandLine(const RawEvent& event);
```

### <a name="parameters"></a>Parameter

*Ereignis*\
Ein [command_line](../event-table.md#command-line) Ereignis.

## <a name="value"></a>Wert

```cpp
const wchar_t Value() const;
```

### <a name="return-value"></a>Rückgabewert

Eine Zeichenfolge, die eine Befehlszeile enthält. Der Wert enthält die Argumente, die aus einer Antwortdatei abgerufen wurden, und von Umgebungsvariablen wie CL, \_cl\_, Link und \_Link\_.

::: moniker-end
