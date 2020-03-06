---
title: Matcheventstackinmembership-Funktion
description: Die C++ Funktionsreferenz für das Build Insights SDK matcheventstackinmitgliedfunction.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MatchEventStackInMemberFunction
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 2a966ea5209a25a62c08cb0873d0565299a15d27
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334367"
---
# <a name="matcheventstackinmemberfunction"></a>Matcheventstackinmembership-Funktion

::: moniker range="<=vs-2015"

Das C++ Build Insights SDK ist kompatibel mit Visual Studio 2017 und höher. Um die Dokumentation für diese Versionen anzuzeigen, legen Sie das Steuerelement für die Visual Studio-Versions Auswahl für diesen Artikel auf Visual Studio 2017 oder Visual Studio 2019 fest.

::: moniker-end
::: moniker range=">=vs-2017"

Die `MatchEventStackInMemberFunction`-Funktion wird verwendet, um einen Ereignis Stapel mit einer bestimmten Ereignis Hierarchie abzugleichen, die in der Parameterliste einer Member-Funktion beschrieben wird. Übereinstimmende Hierarchien werden zur weiteren Verarbeitung an die Member-Funktion weitergeleitet. Weitere Informationen zu Ereignissen, Ereignis Stapeln und Hierarchien finden Sie unter [Ereignis Tabelle](../event-table.md).

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

*TInterface* -\
Der Typ, der die Member-Funktion enthält.

*Treturn* -\
Der Rückgabetyp der Member-Funktion.

*T1*,..., *T10*\
Die Typen, die die Abzugleichende Ereignis Hierarchie beschreiben.

*Textraparameams* -\
Die Typen der zusätzlichen Parameter, die von der Member-Funktion akzeptiert werden, und die Ereignis Hierarchietypen.

*Textraargs*\
Die Typen der zusätzlichen Argumente, die an `MatchEventStackInMemberFunction`übermittelt wurden.

*Event Stack* -\
Der Ereignis Stapel, der mit der von *T1* bis *T10*beschriebenen Ereignistyp Hierarchie abgeglichen werden soll.

*objectptr* -\
Ein Zeiger auf ein Objekt, für das der *mitgliedsemember* aufgerufen wird.

*Mitglied\*
Die Member-Funktion, die die abzugleichenden Ereignistyp Hierarchie beschreibt.

*extraargs*\
Die Argumente, die perfekt mit den Ereignistyp-Hierarchie Parametern an die *Mitgliedsart* weitergeleitet werden.

### <a name="return-value"></a>Rückgabewert

Ein **boolescher** Wert, der **true** ist, wenn die Übereinstimmung erfolgreich war, andernfalls **false** .

## <a name="remarks"></a>Bemerkungen

Das letzte Ereignis in *eventstack* wird immer mit dem letzten Eintrag in der Ereignistyp Hierarchie abgeglichen, um eine Übereinstimmung zu finden. Alle anderen Typen in der Ereignistyp Hierarchie können mit einer beliebigen Position in *eventstack* außer der letzten übereinstimmen, vorausgesetzt, Sie befinden sich in der gleichen Reihenfolge.

Ereignis Typen, die für die Parameter *T1* bis *T10* verwendet werden sollen, werden aus einer Liste von *Erfassungs Klassen*ausgewählt. Eine Liste der Ereignisse und der Erfassungs Klassen, die Sie verwenden können, finden Sie unter [Ereignis Tabelle](../event-table.md).

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
