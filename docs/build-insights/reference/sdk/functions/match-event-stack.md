---
title: Matcheventstack
description: Die C++ Referenz zu den Build Insights SDK matcheventstack-Funktionen.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MatchEventStack
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 445c2d00c24da10754d32256de0c691e82b557e1
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334361"
---
# <a name="matcheventstack"></a>Matcheventstack

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist kompatibel mit Visual Studio 2017 und höher. Um die Dokumentation für diese Versionen anzuzeigen, legen Sie das Steuerelement für die Visual Studio-Versions Auswahl für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest.

::: moniker-end
::: moniker range=">=vs-2017"

Die `MatchEventStack`-Funktion wird verwendet, um einen Ereignis Stapel mit einer bestimmten Ereignis Hierarchie abzugleichen. Übereinstimmende Hierarchien werden zur weiteren Verarbeitung an einen Handler weitergeleitet. Weitere Informationen zu Ereignissen, Ereignis Stapeln und Hierarchien finden Sie unter [Ereignis Tabelle](../event-table.md).

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

*Tevent* -\
Der Typ des ältesten übergeordneten Elements, das im Ereignis Stapel gefunden werden soll.

\ " *tevents* "
Die verbleibenden Typen, die Sie im Ereignis Stapel vergleichen möchten.

*Tcallable* -\
Ein Typ, der `operator()`unterstützt. Weitere Informationen zu den Argumenten, die an diesen Operator übergeben werden, finden Sie in der Beschreibung des *Aufruf baren* Parameters.

*Textraargs*\
Die Typen der zusätzlichen Argumente, die an `MatchEventStack`übermittelt werden.

*Event Stack* -\
Der Ereignis Stapel, der mit der von *tevent* und *tevent*beschriebenen Ereignistyp Hierarchie abgeglichen werden soll.

*Aufruf Bare*\
Nachdem der Ereignis Stapel erfolgreich mit der von " *tevent* " und " *tevents*" beschriebenen Ereignistyp Hierarchie übereinstimmt, ruft `MatchEventStack` *Aufruf Bare*auf. Sie übergibt für jeden Typ in der Ereignis Hierarchie ein *Aufruf bares* r-Wert-Argument. Das *extraargs* -Parameter Paket wird perfekt in den verbleibenden Parametern von *Callable*weitergeleitet.

*extraargs*\
Die Argumente, die perfekt an die *Aufruf Bare* weitergeleitet werden, zusammen mit dem passenden Ereignistyp.

### <a name="return-value"></a>Rückgabewert

Ein **boolescher** Wert, der **true** ist, wenn die Übereinstimmung erfolgreich war, andernfalls **false** .

## <a name="remarks"></a>Bemerkungen

Das letzte Ereignis in *eventstack* wird immer mit dem letzten Eintrag in der verketteten \[*tevent*-, *tevents...* \] Type-Liste abgeglichen. Alle anderen " *tevent* "-und " *tevent* "-Einträge können mit einer beliebigen Position in *eventstack* übereinstimmen, sofern Sie in der gleichen Reihenfolge vorliegen.

Ereignis Typen, die für die Parameter *tevent* und *tevents* verwendet werden sollen, werden aus einer Liste von *Erfassungs Klassen*ausgewählt. Eine Liste der Ereignisse und der Erfassungs Klassen, die Sie verwenden können, finden Sie unter [Ereignis Tabelle](../event-table.md).

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
