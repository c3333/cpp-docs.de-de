---
title: Pointer-to-Member-Operatoren:. * und-&gt;*
ms.date: 11/04/2016
f1_keywords:
- .*
- ->*
helpviewer_keywords:
- expressions [C++], pointer
- pointer-to-member operators [C++]
- .* operator
- expressions [C++], operators
- ->* operator
ms.assetid: 2632be3f-1c81-4523-b56c-982a92a68688
ms.openlocfilehash: 1ff7dd26f36f10948dac42783ad61d16f5feda09
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80188336"
---
# <a name="pointer-to-member-operators--and--gt"></a>Pointer-to-Member-Operatoren:. * und-&gt;*

## <a name="syntax"></a>Syntax

```
expression .* expression
expression ->* expression
```

## <a name="remarks"></a>Bemerkungen

Die Pointer-to-Member-Operatoren. * und->\*geben den Wert eines bestimmten Klassenmembers für das auf der linken Seite des Ausdrucks angegebene Objekt zurück.  Die rechte Seite muss einen Klassenmember angeben.  Im folgenden Beispiel wird die Verwendung dieser Operatoren dargestellt:

```cpp
// expre_Expressions_with_Pointer_Member_Operators.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;

class Testpm {
public:
   void m_func1() { cout << "m_func1\n"; }
   int m_num;
};

// Define derived types pmfn and pmd.
// These types are pointers to members m_func1() and
// m_num, respectively.
void (Testpm::*pmfn)() = &Testpm::m_func1;
int Testpm::*pmd = &Testpm::m_num;

int main() {
   Testpm ATestpm;
   Testpm *pTestpm = new Testpm;

// Access the member function
   (ATestpm.*pmfn)();
   (pTestpm->*pmfn)();   // Parentheses required since * binds
                        // less tightly than the function call.

// Access the member data
   ATestpm.*pmd = 1;
   pTestpm->*pmd = 2;

   cout  << ATestpm.*pmd << endl
         << pTestpm->*pmd << endl;
   delete pTestpm;
}
```

## <a name="output"></a>Output

```Output
m_func1
m_func1
1
2
```

Im vorherigen Beispiel wird ein Zeiger auf einen Member, `pmfn` verwendet, um die Memberfunktion `m_func1` aufzurufen. Mit einem weiteren Zeiger auf einen Member, `pmd`, erfolgt der Zugriff auf den `m_num`-Member.

Der binäre Operator. * kombiniert den ersten Operanden, der ein Objekt des Klassentyps sein muss, mit dem zweiten Operanden, der ein "Pointer-to-Member"-Typ sein muss.

Der binäre Operator-> * kombiniert den ersten Operanden, der ein Zeiger auf ein Objekt des Klassen Typs sein muss, mit dem zweiten Operanden, der ein Zeiger-auf-Member-Typ sein muss.

In einem Ausdruck, der den .*-Operator enthält, muss der erste Operand vom Klassentyp des Zeigers auf den Member sein (oder er muss auf ihn zugreifen können), der im zweiten Operanden angegeben wurde, oder er muss ein zugreifbarer Typ sein, der eindeutig von dieser Klasse abgeleitet wurde und für diese Klasse zugreifbar ist.

In einem Ausdruck, der den-> *-Operator enthält, muss der erste Operand vom Typ "Zeiger auf den Klassentyp" des Typs sein, der im zweiten Operanden angegeben ist, oder er muss von einem Typ sein, der eindeutig von dieser Klasse abgeleitet ist.

## <a name="example"></a>Beispiel

Berücksichtigen Sie die folgenden Klassen und das Programmfragment:

```cpp
// expre_Expressions_with_Pointer_Member_Operators2.cpp
// C2440 expected
class BaseClass {
public:
   BaseClass(); // Base class constructor.
   void Func1();
};

// Declare a pointer to member function Func1.
void (BaseClass::*pmfnFunc1)() = &BaseClass::Func1;

class Derived : public BaseClass {
public:
   Derived();  // Derived class constructor.
   void Func2();
};

// Declare a pointer to member function Func2.
void (Derived::*pmfnFunc2)() = &Derived::Func2;

int main() {
   BaseClass ABase;
   Derived ADerived;

   (ABase.*pmfnFunc1)();   // OK: defined for BaseClass.
   (ABase.*pmfnFunc2)();   // Error: cannot use base class to
                           // access pointers to members of
                           // derived classes.

   (ADerived.*pmfnFunc1)();   // OK: Derived is unambiguously
                              // derived from BaseClass.
   (ADerived.*pmfnFunc2)();   // OK: defined for Derived.
}
```

Das Ergebnis der\* Zeiger-auf-Member-Operatoren. * oder-> ist ein Objekt oder eine Funktion des Typs, der in der Deklaration des Zeigers auf Member angegeben wird. Im vorherigen Beispiel ist das Ergebnis des Ausdrucks `ADerived.*pmfnFunc1()` ein Zeiger auf eine Funktion, die "void" zurückgibt. Dieses Ergebnis ist ein L-Wert, wenn der zweite Operand ein L-Wert ist.

> [!NOTE]
>  Wenn das Ergebnis eines der Zeiger-auf-Member-Operatoren eine Funktion ist, kann das Ergebnis nur als Operand für den Funktionsaufrufoperator verwendet werden.

## <a name="see-also"></a>Weitere Informationen

[C++-Built-in-Operatoren, Rangfolge und Assoziativität](../cpp/cpp-built-in-operators-precedence-and-associativity.md)
