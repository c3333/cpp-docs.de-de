---
title: MatcheventInMemberFunktion
description: Der C++ Build Insights SDK MatchEventInMemberFunction-Funktionsverweis.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MatchEventInMemberFunction
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 522630da16e3f4a1294316d88140f4bc25dca2c8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323900"
---
# <a name="matcheventinmemberfunction"></a>MatcheventInMemberFunktion

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Um die Dokumentation zu diesen Versionen anzuzeigen, legen Sie das Visual **Studio-Versionsauswahlsteuerelement** für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich oben im Inhaltsverzeichnis auf dieser Seite.

::: moniker-end
::: moniker range=">=vs-2017"

Die `MatchEventInMemberFunction` Funktion wird verwendet, um ein Ereignis mit dem Typ abzugleichen, der durch den ersten Parameter einer Memberfunktion beschrieben wird. Das übereinstimmende Ereignis wird zur weiteren Verarbeitung an die Memberfunktion weitergeleitet.

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

*TInterface*\
Der Typ, der die Memberfunktion enthält.

*TReturn*\
Der Rückgabetyp der Memberfunktion.

*TEvent*\
Der Typ des übereinstimmenden Ereignisses.

*TExtraParams*\
Die Typen der zusätzlichen Parameter, die von der Memberfunktion akzeptiert werden, zusammen mit dem übereinstimmenden Ereignistyp.

*TExtraArgs*\
Die Typen der zusätzlichen Argumente, `MatchEventInMemberFunction`die an übergeben wurden.

*Ereignis*\
Das Ereignis, das mit dem von *TEvent*beschriebenen Ereignistyp übereinstimmt.

*objectPtr*\
Ein Zeiger auf ein Objekt, für das *memberFunc* aufgerufen wird.

*MitgliedFunc*\
Die Memberfunktion, die den übereinstimmenden Ereignistyp beschreibt.

*extraArgs*\
Die Argumente, die zusammen mit dem Ereignistypparameter perfekt an *memberFunc* weitergeleitet werden.

### <a name="return-value"></a>Rückgabewert

Ein **bool-Wert,** der **wahr** ist, wenn der Abgleich erfolgreich war, oder andernfalls **false.**

## <a name="remarks"></a>Bemerkungen

Der für den *TEvent-Parameter* zu verwendende Ereignistyp kann aus einer Liste von *Erfassungsklassen*ausgewählt werden. Eine Liste der Ereignisse und der Erfassungsklassen, die Sie zum Abgleichen verwenden können, finden Sie in der [Ereignistabelle](../event-table.md).

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
