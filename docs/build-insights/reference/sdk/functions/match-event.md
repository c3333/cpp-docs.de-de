---
title: MatchEvent
description: Die C++ Build Insights SDK MatchEvent-Funktionsreferenz.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MatchEvent
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 0c60653641c676716bcdd60865433773da79325f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323857"
---
# <a name="matchevent"></a>MatchEvent

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Um die Dokumentation zu diesen Versionen anzuzeigen, legen Sie das Visual **Studio-Versionsauswahlsteuerelement** für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich oben im Inhaltsverzeichnis auf dieser Seite.

::: moniker-end
::: moniker range=">=vs-2017"

Die `MatchEvent` Funktion wird verwendet, um ein Ereignis mit einer Liste von Ereignistypen abzugleichen. Wenn das Ereignis mit einem Typ in der Liste übereinstimmt, wird es zur weiteren Verarbeitung an einen Handler weitergeleitet.

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
Der erste Ereignistyp, dem Sie entsprechen möchten.

*TEvents*\
Die verbleibenden Ereignistypen, die Sie abgleichen möchten.

*TCallable*\
Ein Typ, `operator()`der unterstützt. Weitere Informationen darüber, welche Argumente an diesen Operator übergeben werden, finden Sie in der beschreibung des *aufrufbaren* Parameters.

*TExtraArgs*\
Die Typen der zusätzlichen Argumente, `MatchEvent`die an übergeben wurden.

*Ereignis*\
Das Ereignis, das mit den von *TEvent* und *TEvents*beschriebenen Ereignistypen übereinstimmt.

*Aufrufbaren*\
`MatchEvent`ruft *aufrufbar auf,* nachdem das Ereignis erfolgreich mit einem der von *TEvent* und *TEvents*beschriebenen Ereignistypen ababgestimmt wurde. Das erste Argument, das an callable übergeben *wird,* ist ein r-Wert des übereinstimmenden Ereignistyps. Das *extraArgs-Parameterpaket* wird in den verbleibenden Parametern von *callable*perfekt weitergeleitet.  

*extraArgs*\
Die Argumente, die zusammen mit dem übereinstimmenden Ereignistyp perfekt weitergeleitet werden, um *aufrufbar* zu sein.

### <a name="return-value"></a>Rückgabewert

Ein **bool-Wert,** der **wahr** ist, wenn der Abgleich erfolgreich war, oder **andernfalls false.**

## <a name="remarks"></a>Bemerkungen

Ereignistypen, die für die Parameter *TEvent* und *TEvents* verwendet werden sollen, werden aus einer Liste von *Erfassungsklassen*ausgewählt. Eine Liste der Ereignisse und der Erfassungsklassen, die Sie zum Abgleichen verwenden können, finden Sie in der [Ereignistabelle](../event-table.md).

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
