---
title: MatchEventStack
description: Die Funktionsreferenz zu MatchEventStack im C++ Build Insights SDK.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MatchEventStack
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: ae476c402c3ea0cad558ce41a979b4233e0f1dd3
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224122"
---
# <a name="matcheventstack"></a>MatchEventStack

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Wenn die Dokumentation für diese Versionen angezeigt werden soll, legen Sie das Steuerelement für die Auswahl der **Version** von Visual Studio für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich am Anfang des Inhaltsverzeichnisses auf dieser Seite.

::: moniker-end
::: moniker range=">=vs-2017"

Die `MatchEventStack`-Funktion wird zum Abgleichen eines Ereignisstapels mit einer bestimmten Ereignishierarchie verwendet. Übereinstimmende Hierarchien werden zur weiteren Verarbeitung an einen Handler weitergeleitet. Weitere Informationen zu Ereignissen, Ereignisstapeln und Hierarchien finden Sie in der [Ereignistabelle](../event-table.md).

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
Der Typ des ältesten übergeordneten Elements, das im Ereignisstapel abgeglichen werden soll.

*TEvents*\
Die verbleibenden Typen, die im Ereignisstapel abgeglichen werden sollen.

*TCallable*\
Ein Typ, der `operator()` unterstützt. Weitere Informationen zu den Argumenten, die an diesen Operator übergeben werden, finden Sie in der Beschreibung des Parameters *callable*.

*TExtraArgs*\
Die Typen der zusätzlichen Argumente, die an `MatchEventStack` übergeben werden.

*eventStack*\
Der Ereignisstapel, der mit der von *TEvent* und *TEvents* beschriebenen Ereignistyphierarchie abgeglichen werden soll.

*callable*\
Nach erfolgreichem Abgleich des Ereignisstapels mit der von *TEvent* und *TEvents* beschriebenen Ereignistyphierarchie ruft `MatchEventStack` den Parameter *callable* auf. Für jeden Typ in der Ereignishierarchie wird ein Rückgabewertargument an *callable* übergeben. Das Parameterpaket *extraArgs* wird perfekt an die übrigen *callable*-Parameter weitergeleitet.

*extraArgs*\
Die Argumente, die zusammen mit dem übereinstimmenden Ereignistyp perfekt an den Parameter *callable* weitergeleitet werden.

### <a name="return-value"></a>Rückgabewert

Ein **`bool`** -Wert, der **`true`** ist, wenn der Abgleich erfolgreich war. Andernfalls wird **`false`** zurückgegeben.

## <a name="remarks"></a>Hinweise

Das letzte Ereignis in *eventStack* wird immer mit dem letzten Eintrag in der verketteten Typliste \[*TEvent*, *TEvents...* \] abgeglichen. Alle anderen *TEvent*- und *TEvents*-Einträge können mit jeder Position in *eventStack* außer der letzten übereinstimmen, vorausgesetzt, sie liegen in der gleichen Reihenfolge vor.

Die Ereignistypen, die für die Parameter *TEvent* und *TEvents* verwendet werden sollen, werden aus eine Liste mit *Erfassungsklassen* ausgewählt. Eine Liste der Ereignisse und der Erfassungsklassen, die Sie zum Abgleichen verwenden können, finden Sie in der [Ereignistabelle](../event-table.md).

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
