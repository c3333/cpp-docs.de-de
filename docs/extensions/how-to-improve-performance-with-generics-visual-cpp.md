---
title: 'Vorgehensweise: Verbessern der Leistung mit Generics (C++/CLI)'
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- performance, C++
- C++, performance
- C++, generics
- generics [C++], performance
ms.assetid: f14a175b-301f-46cc-86e4-c82d35f9aa3e
ms.openlocfilehash: 039c5b069351249e51d961d9d1757ed6b09ef99c
ms.sourcegitcommit: 94893973211d0b254c8bcdcf0779997dcc136b0c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/28/2020
ms.locfileid: "91414164"
---
# <a name="how-to-improve-performance-with-generics-ccli"></a>Vorgehensweise: Verbessern der Leistung mit Generics (C++/CLI)

Mit Generics können Sie wiederverwendbaren Code auf Basis eines Typparameters erstellen. Der tatsächliche Typ des Typparameters wird zurückgestellt, bis er vom Clientcode aufgerufen wird. Weitere Informationen zu Generika finden Sie unter [Generics](generics-cpp-component-extensions.md).

In diesem Artikel wird erläutert, wie Generics die Leistung einer Anwendung steigern können, die Sammlungen verwendet.

## <a name="example-two-main-drawbacks-of-net-framework-collections"></a>Beispiel: zwei Haupt Nachteile .NET Framework Auflistungen

Im <xref:System.Collections?displayProperty=fullName>-Namespace von .NET Framework sind viele Sammlungsklassen enthalten. Die meisten dieser Sammlungen werden für Objekte des Typs <xref:System.Object?displayProperty=fullName> eingesetzt. Dadurch können Sammlungen jeden beliebigen Typ speichern, da alle Typen in .NET Framework, auch Werttypen, von <xref:System.Object?displayProperty=fullName> abgeleitet sind. Dieser Ansatz hat jedoch zwei Nachteile.

Erstens: Wenn die Sammlung Werttypen wie z.B. Ganzzahlen speichert, muss der Wert mittels Boxing konvertiert werden, bevor er der Sammlung hinzugefügt wird, und mittels Unboxing zurückkonvertiert werden, wenn der Wert aus der Sammlung abgerufen wird. Hierbei handelt es sich um kostenintensive Vorgänge.

Zweitens: Es besteht keine Möglichkeit, zu steuern, welche Typen einer Sammlung hinzugefügt werden können. Es ist durchaus zulässig, eine Ganzzahl und eine Zeichenfolge der gleichen Sammlung hinzuzufügen, obwohl dies wahrscheinlich nicht beabsichtigt war. Damit Ihr Code typsicher ist, müssen Sie daher überprüfen, ob der aus der Sammlung abgerufene Typ wirklich Ihrer Erwartung entspricht.

Im folgenden Codebeispiel werden die zwei wesentlichen Nachteile der .NET Framework-Sammlungen vor Generics veranschaulicht.

```cpp
// perf_pre_generics.cpp
// compile with: /clr

using namespace System;
using namespace System::Collections;

int main()
{
    // This Stack can contain any type.
    Stack ^s = gcnew Stack();

    // Push an integer to the Stack.
    // A boxing operation is performed here.
    s->Push(7);

    // Push a String to the same Stack.
    // The Stack now contains two different data types.
    s->Push("Seven");

    // Pop the items off the Stack.
    // The item is returned as an Object, so a cast is
    // necessary to convert it to its proper type.
    while (s->Count> 0)
    {
        Object ^o = s->Pop();
        if (o->GetType() == Type::GetType("System.String"))
        {
            Console::WriteLine("Popped a String: {0}", (String ^)o);
        }
        else if (o->GetType() == Type::GetType("System.Int32"))
        {
            Console::WriteLine("Popped an int: {0}", (int)o);
        }
        else
        {
            Console::WriteLine("Popped an unknown type!");
        }
    }
}
```

```Output
Popped a String: Seven
Popped an int: 7
```

## <a name="example-benefit-of-using-generic-collection"></a>Beispiel: Vorteil der Verwendung der generischen Sammlung

Der neue <xref:System.Collections.Generic?displayProperty=fullName>-Namespace enthält viele der gleichen Sammlungen, die im <xref:System.Collections?displayProperty=fullName>-Namespace enthalten sind, aber sie wurden so geändert, dass sie generische Typparameter akzeptieren. Dies beseitigt die zwei Nachteile nicht generischer Sammlungen: das Boxing und Unboxing von Werttypen und die Unfähigkeit, die in den Sammlungen zu speichernden Typen anzugeben. Die Vorgänge an den beiden Sammlungen sind identisch. Sie unterscheiden sich nur in der Weise, wie sie instanziiert werden.

Vergleichen Sie das Beispiel oben mit diesem Beispiel, in dem eine generische <xref:System.Collections.Generic.Stack%601>-Sammlung verwendet wird. Bei großen Sammlungen, auf die häufig zugegriffen wird, ist die Leistung in diesem Beispiel deutlich höher als im vorherigen Beispiel.

```cpp
// perf_post_generics.cpp
// compile with: /clr

#using <System.dll>

using namespace System;
using namespace System::Collections::Generic;

int main()
{
    // This Stack can only contain integers.
    Stack<int> ^s = gcnew Stack<int>();

    // Push an integer to the Stack.
    // A boxing operation is performed here.
    s->Push(7);
    s->Push(14);

    // You can no longer push a String to the same Stack.
    // This will result in compile time error C2664.
    //s->Push("Seven");

    // Pop an item off the Stack.
    // The item is returned as the type of the collection, so no
    // casting is necessary and no unboxing is performed for
    // value types.
    int i = s->Pop();
    Console::WriteLine(i);

    // You can no longer retrieve a String from the Stack.
    // This will result in compile time error C2440.
    //String ^str = s->Pop();
}
```

```Output
14
```

## <a name="see-also"></a>Siehe auch

[Generics](generics-cpp-component-extensions.md)
