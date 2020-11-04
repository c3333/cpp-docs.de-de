---
title: MatchEventInMemberFunction
description: Referenz zur Funktion „MatchEventInMemberFunction“ des C++ Build Insights SDK
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MatchEventInMemberFunction
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 62a7bf6bde62dee7fdf5b1d2ce9044491a123f94
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "92920189"
---
# <a name="matcheventinmemberfunction"></a>MatchEventInMemberFunction

::: moniker range="<=msvc-140"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Wenn die Dokumentation für diese Versionen angezeigt werden soll, legen Sie das Steuerelement für die Auswahl der **Version** von Visual Studio für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich am Anfang des Inhaltsverzeichnisses auf dieser Seite.

::: moniker-end
::: moniker range=">=msvc-150"

Die Funktion `MatchEventInMemberFunction` wird verwendet, um ein Ereignis mit dem Typ abzugleichen, der vom ersten Parameter einer Memberfunktion beschrieben wird. Das zugeordnete Ereignis wird zur weiteren Verarbeitung an die Memberfunktion weitergeleitet.

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
Der Typ des abzugleichenden Ereignisses.

*TExtraParams*\
Die Typen der zusätzlichen Parameter, die von der Memberfunktion akzeptiert werden, und der Ereignistyp, der abgeglichen werden soll.

*TExtraArgs*\
Die Typen der zusätzlichen Argumente, die an `MatchEventInMemberFunction` übergeben wurden.

*Ereignis*\
Das Ereignis, das mit den Ereignistypen abgeglichen werden soll, die von *TEvent* beschrieben werden.

*objectPtr*\
Ein Zeiger auf ein Objekt, für das *memberFunc* aufgerufen wird.

*memberFunc*\
Die Memberfunktion, die den abzugleichenden Ereignistyp beschreibt.

*extraArgs*\
Die Argumente, die zusammen mit dem Ereignistypparameter perfekt an *memberFunc* weitergeleitet werden.

### <a name="return-value"></a>Rückgabewert

Ein **`bool`** -Wert, der **`true`** ausgibt, wenn der Zuordnungsvorgang erfolgreich war. Andernfalls wird **`false`** zurückgegeben.

## <a name="remarks"></a>Hinweise

Der Ereignistyp, der für den *TEvent-* Parameter verwendet werden soll, kann aus einer Liste mit *Erfassungsklassen* ausgewählt werden. Eine Liste der Ereignisse und der Erfassungsklassen, die Sie zum Abgleichen verwenden können, finden Sie unter [Ereignistabelle](../event-table.md).

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
