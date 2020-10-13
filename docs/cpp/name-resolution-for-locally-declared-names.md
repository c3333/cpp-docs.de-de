---
title: Namensauflösung für lokal deklarierte Namen
ms.date: 11/04/2016
ms.assetid: 743b88f3-de11-48f4-ae83-931449ea3886
ms.openlocfilehash: 0216154b55e9742c2c4f3f5df7e6d612e16ec9b1
ms.sourcegitcommit: 43cee7a0d41a062661229043c2f7cbc6ace17fa3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/13/2020
ms.locfileid: "92008921"
---
# <a name="name-resolution-for-locally-declared-names"></a>Namensauflösung für lokal deklarierte Namen

Der Name der Vorlage selbst kann mit oder ohne Vorlagenargumente angegeben werden. Im Bereich einer Klassenvorlage bezieht sich der Name selbst auf die Vorlage. Im Bereich einer Vorlagenspezialisierung oder Teilspezialisierung bezieht sich der Name allein auf die Spezialisierung oder Teilspezialisierung. Andere Spezialisierungen oder Teilspezialisierungen der Vorlage können mit den entsprechenden Vorlagenargumenten ebenfalls referenziert werden.

## <a name="example-specialization-versus-partial-specialization"></a>Beispiel: Spezialisierung und partielle Spezialisierung

Der folgende Code zeigt, dass der Name der Klassenvorlage A im Bereich einer Spezialisierung oder einer teilweisen Spezialisierung unterschiedlich interpretiert wird.

```cpp
// template_name_resolution3.cpp
// compile with: /c
template <class T> class A {
   A* a1;   // A refers to A<T>
   A<int>* a2;  // A<int> refers to a specialization of A.
   A<T*>* a3;   // A<T*> refers to the partial specialization A<T*>.
};

template <class T> class A<T*> {
   A* a4; // A refers to A<T*>.
};

template<> class A<int> {
   A* a5; // A refers to A<int>.
};
```

## <a name="example-name-conflict-between-template-parameter-and-object"></a>Beispiel: namens Konflikt zwischen Vorlagen Parameter und Objekt

Im Falle eines Namenskonflikts zwischen einem Vorlagenparameter und einem anderen Objekt kann der Vorlagenparameter ausgeblendet oder nicht ausgeblendet werden. Die folgenden Regeln bestimmen die Vorrangigkeit.

Der Vorlagenparameter befindet sich ab seinem ersten Auftreten bis zum Ende der Klasse oder Funktionsvorlage im Gültigkeitsbereich. Wenn der Name erneut in der Vorlagenargumentliste oder in der Liste der Basisklassen vorkommt, bezieht er sich auf denselben Typ. In Standard-C++ kann kein anderer Name, der mit dem Vorlagenparameter identisch ist, im selben Gültigkeitsbereich deklariert werden. Mit einer Microsoft-Erweiterung kann der Vorlagenparameter im Gültigkeitsbereich der Vorlage neu definiert werden. Das folgende Beispiel zeigt die Verwendung des Vorlagenparameters in der Basisspezifizierung einer Klassenvorlage.

```cpp
// template_name_resolution4.cpp
// compile with: /EHsc
template <class T>
class Base1 {};

template <class T>
class Derived1 : Base1<T> {};

int main() {
   // Derived1<int> d;
}
```

## <a name="example-define-member-function-outside-class-template"></a>Beispiel: Definieren der Element Funktion außerhalb der Klassen Vorlage

Wenn Sie die Memberfunktionen einer Vorlage außerhalb der Klassenvorlage definieren, kann ein anderer Vorlagenparametername verwendet werden. Wenn die Definition für die Vorlagenmemberfunktion einen anderen Namen für den Vorlagenparameter verwendet als die Deklaration, und der Name in der Definition mit einem anderen Member der Deklaration in Konflikt steht, hat der Member in der Vorlagendeklaration Vorrang.

```cpp
// template_name_resolution5.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

template <class T> class C {
public:
   struct Z {
      Z() { cout << "Z::Z()" << endl; }
   };
   void f();
};

template <class Z>
void C<Z>::f() {
   // Z refers to the struct Z, not to the template arg;
   // Therefore, the constructor for struct Z will be called.
   Z z;
}

int main() {
   C<int> c;
   c.f();
}
```

```Output
Z::Z()
```

## <a name="example-define-template-or-member-function-outside-namespace"></a>Beispiel: Definieren einer Vorlage oder einer Element Funktion außerhalb des Namespace

Wenn eine Vorlagenfunktion oder Memberfunktion außerhalb des Namespaces definiert wird, in dem die Vorlage deklariert wurde, hat das Vorlagenargument Vorrang vor den Namen anderer Member des Namespaces.

```cpp
// template_name_resolution6.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

namespace NS {
   void g() { cout << "NS::g" << endl; }

   template <class T> struct C {
      void f();
      void g() { cout << "C<T>::g" << endl; }
   };
};

template <class T>
void NS::C<T>::f() {
   g(); // C<T>::g, not NS::g
};

int main() {
   NS::C<int> c;
   c.f();
}
```

```Output
C<T>::g
```

## <a name="example-base-class-or-member-name-hides-template-argument"></a>Beispiel: Basisklassen-oder Elementname blendet das Vorlagen Argument aus.

In Definitionen, die sich außerhalb der Deklaration der Vorlagenklassen befinden, gilt: Wenn eine Vorlagenklasse über eine Basisklasse verfügt, die nicht von einem Vorlagenargument abhängig ist, und wenn die Basisklasse oder einer ihrer Member über denselben Namen wie ein Vorlagenargument verfügt, blendet die Basisklasse oder der Membername das Vorlagenargument aus.

```cpp
// template_name_resolution7.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

struct B {
   int i;
   void print() { cout << "Base" << endl; }
};

template <class T, int i> struct C : public B {
   void f();
};

template <class B, int i>
void C<B, i>::f() {
   B b;   // Base class b, not template argument.
   b.print();
   i = 1; // Set base class's i to 1.
}

int main() {
   C<int, 1> c;
   c.f();
   cout << c.i << endl;
}
```

```Output
Base
1
```

## <a name="see-also"></a>Siehe auch

[Namensauflösung](../cpp/templates-and-name-resolution.md)
