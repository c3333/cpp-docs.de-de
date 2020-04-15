---
title: MatcheventStackInMemberFunktion
description: Der C++ Build Insights SDK MatchEventStackInMemberFunction-Funktionsverweis.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MatchEventStackInMemberFunction
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 28842a02e7edc2e00266d8c7941798f4ce714ded
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323883"
---
# <a name="matcheventstackinmemberfunction"></a>MatcheventStackInMemberFunktion

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist mit Visual Studio 2017 und höher kompatibel. Um die Dokumentation zu diesen Versionen anzuzeigen, legen Sie das Visual **Studio-Versionsauswahlsteuerelement** für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest. Es befindet sich oben im Inhaltsverzeichnis auf dieser Seite.

::: moniker-end
::: moniker range=">=vs-2017"

Die `MatchEventStackInMemberFunction` Funktion wird verwendet, um einen Ereignisstapel mit einer bestimmten Ereignishierarchie abzugleichen, die durch die Parameterliste einer Memberfunktion beschrieben wird. Abgestimmte Hierarchien werden zur weiteren Verarbeitung an die Memberfunktion weitergeleitet. Weitere Informationen zu Ereignissen, Ereignisstapeln und Hierarchien finden Sie in der [Ereignistabelle](../event-table.md).

## <a name="syntax"></a>Syntax

```cpp
template <
    typename     TInterface,
    typename     TReturn,
    typename     T1,
    typename...  TExtraParams,
    typename...  TExtraArgs>
bool MatchEventStackInMemberFunction(
    const EventStack&         eventStack,
    TInterface*               objectPtr,
    TReturn (TInterface::*    memberFunc)(T1, TExtraParams...),
    TExtraArgs&&...           extraArgs);

template <
    typename     TInterface,
    typename     TReturn,
    typename     T1,
    typename     T2,
    typename...  TExtraParams,
    typename...  TExtraArgs>
bool MatchEventStackInMemberFunction(
    const EventStack&         eventStack,
    TInterface*               objectPtr,
    TReturn (TInterface::*    memberFunc)(T1, T2, TExtraParams...),
    TExtraArgs&&...           extraArgs);

// Etc...

template <
    typename     TInterface,
    typename     TReturn,
    typename     T1,
    typename     T2,
    typename     T3,
    typename     T4,
    typename     T5,
    typename     T6,
    typename     T7,
    typename     T8,
    typename     T9,
    typename     T10,
    typename...  TExtraParams,
    typename...  TExtraArgs>
bool MatchEventStackInMemberFunction(
    const EventStack&         eventStack,
    TInterface*               objectPtr,
    TReturn (TInterface::*    memberFunc)(T1, T2, T3, T4, T5, T6, T7, T8, T9, T10, TExtraParams...),
    TExtraArgs&&...           extraArgs);
```

### <a name="parameters"></a>Parameter

*TInterface*\
Der Typ, der die Memberfunktion enthält.

*TReturn*\
Der Rückgabetyp der Memberfunktion.

*T1*, ..., *T10*\
Die Typen, die die übereinstimmende Ereignishierarchie beschreiben.

*TExtraParams*\
Die Typen der zusätzlichen Parameter, die von der Memberfunktion akzeptiert werden, und die Ereignishierarchietypen.

*TExtraArgs*\
Die Typen der zusätzlichen Argumente, `MatchEventStackInMemberFunction`die an übergeben wurden.

*eventStack*\
Der Ereignisstapel, der mit der von *T1* bis *T10*beschriebenen Ereignistyphierarchie übereinstimmen soll.

*objectPtr*\
Ein Zeiger auf ein Objekt, auf dem *memberFunc* aufgerufen wird.

*MitgliedFunc*\
Die Memberfunktion, die die übereinstimmende Ereignistyphierarchie beschreibt.

*extraArgs*\
Die Argumente, die zusammen mit den Parametern der Ereignistyphierarchie perfekt an *memberFunc* weitergeleitet werden.

### <a name="return-value"></a>Rückgabewert

Ein **bool-Wert,** der **wahr** ist, wenn der Abgleich erfolgreich war, oder andernfalls **false.**

## <a name="remarks"></a>Bemerkungen

Das letzte Ereignis in *eventStack* wird immer mit dem letzten Eintrag in der übereinstimmenden Ereignistyphierarchie abgeglichen. Alle anderen Typen in der Ereignistyphierarchie können mit jeder Position in *eventStack* mit Ausnahme der letzten übereinstimmen, sofern sie in der gleichen Reihenfolge sind.

Ereignistypen, die für die Parameter *T1* bis *T10* verwendet werden sollen, werden aus einer Liste von *Erfassungsklassen*ausgewählt. Eine Liste der Ereignisse und der Erfassungsklassen, die Sie zum Abgleichen verwenden können, finden Sie in der [Ereignistabelle](../event-table.md).

## <a name="example"></a>Beispiel

```cpp
void MyClass::Foo1(Compiler cl, BackEndPass bep, C2DLL c2,
    CodeGeneration cg, Thread t, Function f) { }

void MyClass::Foo2(Compiler cl, Function f) { }

void MyClass::Foo3(Thread t, Compiler cl, Function f) { }

void MyClass::Foo4(Compiler cl) { }

void MyClass::OnStartActivity(const EventStack& eventStack)
{
    // Let's assume eventStack contains:
    // [Compiler, BackEndPass, C2DLL, CodeGeneration, Thread, Function]

    bool b1 = MatchEventStackInMemberFunction(
        eventStack, this, &MyClass::Foo1);

    bool b2 = MatchEventStackInMemberFunction(
        eventStack, this, &MyClass::Foo2);

    bool b3 = MatchEventStackInMemberFunction(
        eventStack, this, &MyClass::Foo3);

    bool b4 = MatchEventStackInMemberFunction(
        eventStack, this, &MyClass::Foo4);

    // b1: true because the parameter types of Foo1 match the eventStack
    //     exactly.
    // b2: true because Function is the last entry in both the member
    //     function parameter list and 'eventStack', and also because
    //     Compiler comes before Function in 'eventStack' and in the
    //     parameter type list.
    // b3: false because, even though both Thread and Compiler come
    //     before Function in 'eventStack', the member function parameter
    //     list doesn't list them in the right order.
    // b4: false because the last entry in the member function parameter
    //     list is Compiler, which doesn't match the last entry in 'eventStack'
    //     (Function).
}
```

::: moniker-end
