---
title: Matchevent
description: Die C++ matchevent-Funktionsreferenz für das Build Insights SDK.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MatchEvent
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: f8022953e2f56f7c8917f161b094c50e0c5ecbdf
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334355"
---
# <a name="matchevent"></a>Matchevent

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist kompatibel mit Visual Studio 2017 und höher. Um die Dokumentation für diese Versionen anzuzeigen, legen Sie das Steuerelement für die Visual Studio-Versions Auswahl für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest.

::: moniker-end
::: moniker range=">=vs-2017"

Die `MatchEvent`-Funktion wird verwendet, um ein Ereignis mit einer Liste von Ereignis Typen abzugleichen. Wenn das Ereignis mit einem Typ in der Liste übereinstimmt, wird es zur weiteren Verarbeitung an einen Handler weitergeleitet.

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

*Tevent* -\
Der erste Ereignistyp, den Sie zuordnen möchten.

\ " *tevents* "
Die restlichen Ereignis Typen, die Sie zuordnen möchten.

*Tcallable* -\
Ein Typ, der `operator()`unterstützt. Weitere Informationen zu den Argumenten, die an diesen Operator übergeben werden, finden Sie in der Beschreibung des *Aufruf baren* Parameters.

*Textraargs*\
Die Typen der zusätzlichen Argumente, die an `MatchEvent`übermittelt wurden.

*Ereignis*\
Das Ereignis, das mit den von " *tevent* " und " *tevents*" beschriebenen Ereignis Typen verglichen werden soll.

*Aufruf Bare*\
`MatchEvent` Ruft die *Aufruf Bare* Methode auf, nachdem das Ereignis erfolgreich mit einem der Ereignis Typen übereinstimmt, die von *tevent* und *tevents*beschrieben werden. Das erste Argument, das an *Callable* übermittelt wird, ist ein r-Wert des übereinstimmenden Ereignis Typs. Das *extraargs* -Parameter Paket wird perfekt in den verbleibenden Parametern von *Callable*weitergeleitet.  

*extraargs*\
Die Argumente, die perfekt an die *Aufruf Bare* weitergeleitet werden, zusammen mit dem passenden Ereignistyp.

### <a name="return-value"></a>Rückgabewert

Ein **boolescher** Wert, der **true** ist, wenn die Übereinstimmung erfolgreich war, andernfalls **false** .

## <a name="remarks"></a>Bemerkungen

Ereignis Typen, die für die Parameter *tevent* und *tevents* verwendet werden sollen, werden aus einer Liste von *Erfassungs Klassen*ausgewählt. Eine Liste der Ereignisse und der Erfassungs Klassen, die Sie verwenden können, finden Sie unter [Ereignis Tabelle](../event-table.md).

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
