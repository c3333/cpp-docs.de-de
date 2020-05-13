---
title: MatchEventStack
description: Die C++ Build Insights SDK MatchEventStack-Funktionsreferenz.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MatchEventStack
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: a223d420e8c48667fbd1c6569f02d0486f597b5e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323877"
---
# <a name="matcheventstack"></a>MatchEventStack

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Um die Dokumentation zu diesen Versionen anzuzeigen, legen Sie das Visual **Studio-Versionsauswahlsteuerelement** für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich oben im Inhaltsverzeichnis auf dieser Seite.

::: moniker-end
::: moniker range=">=vs-2017"

Die `MatchEventStack` Funktion wird verwendet, um einen Ereignisstapel mit einer bestimmten Ereignishierarchie abzugleichen. Abgestimmte Hierarchien werden zur weiteren Verarbeitung an einen Handler weitergeleitet. Weitere Informationen zu Ereignissen, Ereignisstapeln und Hierarchien finden Sie in der [Ereignistabelle](../event-table.md).

## <a name="syntax"></a>Syntax

```cpp
template <
    typename          TEvent,
    typename...       TEvents,
    typename          TCallable,
    typename...       TExtraArgs>
bool MatchEventStack(
    const EventStack& eventStack,
    TCallable&&       callable,
    TExtraArgs&&...   extraArgs);
```

### <a name="parameters"></a>Parameter

*TEvent*\
Der Typ des ältesten übergeordneten Elements, das im Ereignisstapel übereinstimmen soll.

*TEvents*\
Die verbleibenden Typen, die Im Ereignisstapel übereinstimmen sollen.

*TCallable*\
Ein Typ, `operator()`der unterstützt. Weitere Informationen darüber, welche Argumente an diesen Operator übergeben werden, finden Sie in der beschreibung des *aufrufbaren* Parameters.

*TExtraArgs*\
Die Typen der zusätzlichen `MatchEventStack`Argumente, die an übergeben werden.

*eventStack*\
Der Ereignisstapel, der mit der von *TEvent* und *TEvents*beschriebenen Ereignistyphierarchie übereinstimmen soll.

*Aufrufbaren*\
Beim erfolgreichen Abgleichen des Ereignisstapels mit der von `MatchEventStack` *TEvent* und *TEvents*beschriebenen Ereignistyphierarchie ruft *aufrufbar*auf. Es wird an *ein* r-Wert-Argument für jeden Typ in der Ereignishierarchie überführt. Das *extraArgs-Parameterpaket* wird in den verbleibenden Parametern von *callable*perfekt weitergeleitet.

*extraArgs*\
Die Argumente, die zusammen mit dem übereinstimmenden Ereignistyp perfekt weitergeleitet werden, um *aufrufbar* zu sein.

### <a name="return-value"></a>Rückgabewert

Ein **bool-Wert,** der **wahr** ist, wenn der Abgleich erfolgreich war, oder andernfalls **false.**

## <a name="remarks"></a>Bemerkungen

Das letzte Ereignis in *eventStack* wird immer mit dem letzten \[Eintrag im verketteten *TEvent*, *TEvents...* \] Typliste. Alle anderen *TEvent-* und *TEvents-Einträge* können mit jeder Position in *eventStack* mit Ausnahme der letzten übereinstimmen, sofern sie in der gleichen Reihenfolge sind.

Ereignistypen, die für die Parameter *TEvent* und *TEvents* verwendet werden sollen, werden aus einer Liste von *Erfassungsklassen*ausgewählt. Eine Liste der Ereignisse und der Erfassungsklassen, die Sie zum Abgleichen verwenden können, finden Sie in der [Ereignistabelle](../event-table.md).

## <a name="example"></a>Beispiel

```cpp
void MyClass::OnStartActivity(const EventStack& eventStack)
{
    // Let's assume eventStack contains:
    // [Compiler, BackEndPass, C2DLL, CodeGeneration, Thread, Function]

    bool b1 = MatchEventStack<Compiler, BackEndPass, C2DLL,
                CodeGeneration, Thread, Function>(
        eventStack, [](Compiler cl, BackEndPass bep, C2DLL c2,
            CodeGeneration cg, Thread t, Function f){ /* Do something ... */ });

    bool b2 = MatchEventStack<Compiler, Function>(
        eventStack, [](Compiler cl, Function f){ /* Do something... */ });

    bool b3 = MatchEventStack<Thread, Compiler, Function>(
        eventStack, [](Thread t, Compiler cl Function f){ /* Do something... */ });

    bool b4 = MatchEventStack<Compiler>(
        eventStack, [](Compiler cl){ /* Do something... */ });


    // b1: true because the list of types matches the eventStack exactly.
    // b2: true because Function is the last entry in both the type list
    //     and 'eventStack', and also because Compiler comes before
    //     Function in 'eventStack' and in the type list.
    // b3: false because, even though both Thread and Compiler come
    //     before Function in 'eventStack', they aren't listed in the
    //     right order in the type list.
    // b4: false because the last entry in the type list is Compiler,
    //     which doesn't match the last entry in 'eventStack' (Function).
}
```

::: moniker-end
