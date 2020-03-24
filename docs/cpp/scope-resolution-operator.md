---
title: 'Bereichsauflösungsoperator: ::'
ms.date: 11/04/2016
f1_keywords:
- '::'
helpviewer_keywords:
- scope, scope resolution operator
- operators [C++], scope resolution
- scope resolution operator
- ':: operator'
ms.assetid: fd5de9d3-c716-4e12-bae9-03a16fd79a50
ms.openlocfilehash: 07c2884ed0ba114c22a0c71bbaf7268d6f6931a4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80178885"
---
# <a name="scope-resolution-operator-"></a>Bereichsauflösungsoperator: ::

Der Bereichs Auflösungs Operator **::** wird verwendet, um Bezeichner zu identifizieren und zu unterscheiden, die in unterschiedlichen Bereichen verwendet werden. Weitere Informationen zum Gültigkeitsbereich finden Sie unter [Scope](../cpp/scope-visual-cpp.md).

## <a name="syntax"></a>Syntax

```
:: identifier
class-name :: identifier
namespace :: identifier
enum class :: identifier
enum struct :: identifier
```

## <a name="remarks"></a>Bemerkungen

`identifier` kann eine Variable, eine Funktion oder ein Enumerationswert sein.

## <a name="with-classes-and-namespaces"></a>Mit Klassen und Namespaces

Das folgende Beispiel zeigt die Verwendung des Bereichsauflösungsoperators mit Namespaces und Klassen:

```cpp
namespace NamespaceA{
    int x;
    class ClassA {
    public:
        int x;
    };
}

int main() {

    // A namespace name used to disambiguate
    NamespaceA::x = 1;

    // A class name used to disambiguate
    NamespaceA::ClassA a1;
    a1.x = 2;
}
```

Ein Bereichsauflösungsoperator ohne Bereichsqualifizierer verweist auf den globalen Namespace.

```cpp
namespace NamespaceA{
    int x;
}

int x;

int main() {
    int x;

    // the x in main()
    x = 0;
    // The x in the global namespace
    ::x = 1;

    // The x in the A namespace
    NamespaceA::x = 2;
}
```

Mit dem Bereichsauflösungsoperator können Sie ein Mitglied eines Namespaces oder einen Namespace, der den Namespace des Mitglieds benennt, in einer Using-Direktive identifizieren. Im folgenden Beispiel können Sie `NamespaceC` zum Qualifizieren von `ClassB` verwenden, obwohl `ClassB` im Namespace `NamespaceB` deklariert wurde, da `NamespaceB` in `NamespaceC` durch eine using-Anweisung benannt wurde.

```cpp
namespace NamespaceB {
    class ClassB {
    public:
        int x;
    };
}

namespace NamespaceC{
    using namespace B;
}
int main() {
    NamespaceB::ClassB c_b;
    NamespaceC::ClassB c_c;

    c_b.x = 3;
    c_c.x = 4;
}
```

Bereichsauflösungsoperatoren können verkettet werden. Im folgenden Beispiel identifiziert `NamespaceD::NamespaceD1` den geschachtelten Namespace `NamespaceD1`, und `NamespaceE::ClassE::ClassE1` identifiziert die geschachtelte Klasse `ClassE1`.

```cpp
namespace NamespaceD{
    namespace NamespaceD1{
        int x;
    }
}

namespace NamespaceE{
    class ClassE{
    public:
        class ClassE1{
        public:
            int x;
        };
    };
}

int main() {
    NamespaceD:: NamespaceD1::x = 6;
    NamespaceE::ClassE::ClassE1 e1;
    e1.x = 7  ;
}
```

## <a name="with-static-members"></a>Mit statischen Members

Sie müssen den Bereichsauflösungsoperator verwenden, um statische Member von Klassen aufzurufen.

```cpp
class ClassG {
public:
    static int get_x() { return x;}
    static int x;
};

int ClassG::x = 6;

int main() {

    int gx1 = ClassG::x;
    int gx2 = ClassG::get_x();
}
```

## <a name="with-scoped-enumerations"></a>Mit bereichsbezogenen Enumerationen

Der Bereichs bezogene Auflösungs Operator wird auch mit den Werten einer Bereichs bezogenen [enumerationsenumerationsdeklaration](../cpp/enumerations-cpp.md)verwendet, wie im folgenden Beispiel dargestellt:

```cpp
enum class EnumA{
    First,
    Second,
    Third
};

int main() {
    EnumA enum_value = EnumA::First;
}
```

## <a name="see-also"></a>Weitere Informationen

[C++-Built-in-Operatoren, Rangfolge und Assoziativität](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Namespaces](../cpp/namespaces-cpp.md)
