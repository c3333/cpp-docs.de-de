---
title: Matcheventinmembership Function
description: Die C++ Funktionsreferenz für den Build Insights SDK matcheventinmembership function.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MatchEventInMemberFunction
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: eabbb8a91609b1447ebcc19af32df2ffed347c24
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334379"
---
# <a name="matcheventinmemberfunction"></a>Matcheventinmembership Function

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist kompatibel mit Visual Studio 2017 und höher. Um die Dokumentation für diese Versionen anzuzeigen, legen Sie das Steuerelement für die Visual Studio-Versions Auswahl für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest.

::: moniker-end
::: moniker range=">=vs-2017"

Die `MatchEventInMemberFunction`-Funktion wird verwendet, um ein Ereignis mit dem Typ abzugleichen, der durch den ersten Parameter einer Member-Funktion beschrieben wird. Das übereinstimmende Ereignis wird zur weiteren Verarbeitung an die Member-Funktion weitergeleitet.

## <a name="syntax"></a>Syntax

```cpp
template <
    typename     TInterface,
    typename     TReturn,
    typename     TEvent,
    typename...  TExtraParams,
    typename...  TExtraArgs>
bool MatchEventInMemberFunction(
    const RawEvent&          event,
    TInterface*              objectPtr,
    TReturn (TInterface::*   memberFunc)(TEvent, TExtraParams...),
    TExtraArgs&&...          extraArgs);
```

### <a name="parameters"></a>Parameter

*TInterface* -\
Der Typ, der die Member-Funktion enthält.

*Treturn* -\
Der Rückgabetyp der Member-Funktion.

*Tevent* -\
Der Typ des Ereignisses, das abgeglichen werden soll.

*Textraparameams* -\
Die Typen der zusätzlichen Parameter, die von der Element Funktion akzeptiert werden, zusammen mit dem Ereignistyp, der abgeglichen werden soll.

*Textraargs*\
Die Typen der zusätzlichen Argumente, die an `MatchEventInMemberFunction`übermittelt wurden.

*Ereignis*\
Das Ereignis, das mit dem von *tevent*beschriebenen Ereignistyp verglichen werden soll.

*objectptr* -\
Ein Zeiger auf ein Objekt, für das die *mitgliedeinfunktion* aufgerufen wird.

*Mitglied\*
Die Member-Funktion, die den abzugleichenden Ereignistyp beschreibt.

*extraargs*\
Die Argumente, die perfekt mit dem Ereignistyp Parameter an die *Mitgliedschaft* weitergeleitet werden.

### <a name="return-value"></a>Rückgabewert

Ein **boolescher** Wert, der **true** ist, wenn die Übereinstimmung erfolgreich war, andernfalls **false** .

## <a name="remarks"></a>Bemerkungen

Der Ereignistyp, der für den *tevent* -Parameter verwendet werden soll, kann aus einer Liste von *Erfassungs Klassen*ausgewählt werden. Eine Liste der Ereignisse und der Erfassungs Klassen, die Sie verwenden können, finden Sie unter [Ereignis Tabelle](../event-table.md).

## <a name="example"></a>Beispiel

```cpp
void MyClass::Foo1(Function f) {}

void MyClass::Foo2(Compiler cl) {}

void MyClass::OnStartActivity(const EventStack& eventStack)
{
    // Let's assume eventStack contains:
    // [Compiler, BackEndPass, C2DLL, CodeGeneration, Thread, Function]

    auto& functionEvent = eventStack.Back(); // The Function event

    bool b1 = MatchEventInMemberFunction(
        functionEvent, this, &MyClass::Foo1);

    bool b2 = MatchEventInMemberFunction(
        functionEvent, this, &MyClass::Foo2);

    // b1: true because the first parameter of Foo1 is Function.
    // b2: false because the first parameter of Foo2 isn't Function.
}
```

::: moniker-end
