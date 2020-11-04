---
title: MatchEvent
description: Referenz zur Funktion „MatchEvent“ des C++ Build Insights SDK
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MatchEvent
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 1486a76aab7b9a4f3b4da209f4f163b4c65b0ac4
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "92920098"
---
# <a name="matchevent"></a>MatchEvent

::: moniker range="<=msvc-140"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Wenn die Dokumentation für diese Versionen angezeigt werden soll, legen Sie das Steuerelement für die Auswahl der **Version** von Visual Studio für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich am Anfang des Inhaltsverzeichnisses auf dieser Seite.

::: moniker-end
::: moniker range=">=msvc-150"

Die Funktion `MatchEvent` wird verwendet, um ein Ereignis mit einer Liste von Ereignistypen abzugleichen. Wenn das Ereignis mit einem Typ in der Liste übereinstimmt, wird es zur weiteren Verarbeitung an einen Handler weitergeleitet.

## <a name="syntax"></a>Syntax

```cpp
template <
    typename        TEvent,
    typename...     TEvents,
    typename        TCallable,
    typename...     TExtraArgs>
bool MatchEvent(
    const RawEvent& event,
    TCallable&&     callable,
    TExtraArgs&&... extraArgs);
```

### <a name="parameters"></a>Parameter

*TEvent*\
Der erste Ereignistyp, den Sie zuordnen möchten.

*TEvents*\
Die übrigen Ereignistypen, die Sie zuordnen möchten.

*TCallable*\
Ein Typ, der den Operator `operator()` unterstützt. Weitere Informationen zu den Argumenten, die an diesen Operator übergeben werden, finden Sie in der Beschreibung des Parameters *callable*.

*TExtraArgs*\
Die Typen der zusätzlichen Argumente, die an `MatchEvent` übergeben wurden.

*Ereignis*\
Das Ereignis, das mit den Ereignistypen abgeglichen werden soll, die von *TEvent* und *TEvents* beschrieben werden.

*callable*\
`MatchEvent` ruft den Parameter *callable* auf, nachdem das Ereignis erfolgreich einem der in *TEvent* und *TEvents* beschriebenen Ereignistypen zugeordnet werden konnte. Das erste Argument, das an den Parameter *callable* übergeben wird, ist ein R-Wert des zugeordneten Eventtyps. Das Parameterpaket *extraArgs* wird perfekt an die übrigen *callable* -Parameter weitergeleitet.  

*extraArgs*\
Die Argumente, die zusammen mit dem zugeordneten Ereignistyp perfekt an den Parameter *callable* weitergeleitet werden.

### <a name="return-value"></a>Rückgabewert

Ein **`bool`** -Wert, der **`true`** zurückgibt, wenn der Zuordnungsvorgang erfolgreich ist. Andernfalls wird **`false`** zurückgegeben.

## <a name="remarks"></a>Hinweise

Die Eventtypen, die für die Parameter *TEvent* und *TEvents* verwendet werden sollen, werden aus eine Liste mit *Erfassungsklassen* ausgewählt. Eine Liste der Ereignisse und der Erfassungsklassen, die Sie zum Abgleichen verwenden können, finden Sie unter [Ereignistabelle](../event-table.md).

## <a name="example"></a>Beispiel

```cpp
void MyClass::OnStartActivity(const EventStack& eventStack)
{
    // Let's assume eventStack contains:
    // [Compiler, BackEndPass, C2DLL, CodeGeneration, Thread, Function]

    auto& functionEvent = eventStack.Back(); // The Function event

    bool b1 = MatchEvent<Function, Thread>(
        functionEvent, [](auto matchedEvent){ /* Do something... */});

    bool b2 = MatchEvent<CodeGeneration, Thread>(
        functionEvent, [](auto matchedEvent){ /* Do something... */});


    // b1: true because the list of types contains Function, which is
    //     the type of the event we are trying to match.
    // b2: false because the list of types doesn't contain Function.
}
```

::: moniker-end
