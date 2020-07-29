---
title: Compilerfehler C2280
ms.date: 04/25/2017
f1_keywords:
- C2280
helpviewer_keywords:
- C2280
ms.assetid: e6c5b1fb-2b9b-4554-8ff9-775eeb37161b
ms.openlocfilehash: 9ee5b8105241ee347812a0dcc083a4f1cc7dca49
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87208407"
---
# <a name="compiler-error-c2280"></a>Compilerfehler C2280

'*Declaration*': Es wurde versucht, auf eine gelöschte Funktion zu verweisen

Der Compiler hat einen Versuch erkannt, auf eine Funktion zu verweisen `deleted` . Dieser Fehler kann durch einen aufzurufenden Member einer Member-Funktion verursacht werden, die explizit als `= deleted` im Quellcode gekennzeichnet wurde. Dieser Fehler kann auch durch einen Rückruf einer impliziten speziellen Member-Funktion einer Struktur oder Klasse verursacht werden, die vom Compiler automatisch deklariert und gekennzeichnet wird `deleted` . Weitere Informationen dazu, wann der Compiler automatisch **`default`** oder `deleted` spezielle Element Funktionen generiert, finden Sie unter [besondere Member-Funktionen](../../cpp/special-member-functions.md).

## <a name="example-explicitly-deleted-functions"></a>Beispiel: explizit gelöschte Funktionen

Dieser Fehler wird durch einen expliziten Funktions aufrufungs Vorgang `deleted` verursacht. Eine explizite `deleted` Member-Funktion impliziert, dass die Klasse oder Struktur absichtlich entworfen wurde, um deren Verwendung zu verhindern. um dieses Problem zu beheben, sollten Sie den Code ändern, um ihn zu vermeiden.

```cpp
// C2280_explicit.cpp
// compile with: cl /c /W4 C2280_explicit.cpp
struct A {
    A();
    A(int) = delete;
};

struct B {
    A a1;
    A a2 = A(3); // C2280, calls deleted A::A(int)
    // To fix, remove the call to A(int)
};

void f() {
    B b;    // calls implicit B::B(void)
}
```

## <a name="example-uninitialized-data-members"></a>Beispiel: nicht initialisierte Datenmember

Ein nicht initialisiertes Datenmember oder **`const`** Datenmember des Verweistyps bewirkt, dass der Compiler implizit einen `deleted` Standardkonstruktor deklariert. Um dieses Problem zu beheben, initialisieren Sie den Datenmember, wenn er deklariert wird.

```cpp
// C2280_uninit.cpp
// compile with: cl /c C2280_uninit.cpp
struct A {
    const int i; // uninitialized const-qualified data
    // members or reference type data members cause
    // the implicit default constructor to be deleted.
    // To fix, initialize the value in the declaration:
    // const int i = 42;
} a;    // C2280
```

## <a name="example-reference-and-const-data-members"></a>Beispiel: Reference-und Konstante-Datenmember

Ein- **`const`** oder Verweistyp Datenmember bewirkt, dass der Compiler einen `deleted` Kopier Zuweisungs Operator deklariert. Nach der Initialisierung können diese Member nicht zugewiesen werden, sodass eine einfache Kopie oder Verschiebung nicht funktioniert. Um dieses Problem zu beheben, empfiehlt es sich, die Logik zum Entfernen der Zuweisungs Vorgänge zu ändern, die den Fehler verursachen.

```cpp
// C2280_ref.cpp
// compile with: cl /c C2280_ref.cpp
extern int k;
struct A {
    A();
    int& ri = k; // a const or reference data member causes
    // implicit copy assignment operator to be deleted.
};

void f() {
    A a1, a2;
    // To fix, consider removing this assignment.
    a2 = a1;    // C2280
}
```

## <a name="example-movable-deletes-implicit-copy"></a>Beispiel: die implizite Kopie der verschiebbaren Kopie

Wenn eine Klasse einen bewegungskonstruktor oder Bewegungs Zuweisungs Operator deklariert, aber nicht explizit einen Kopierkonstruktor deklariert, deklariert der Compiler implizit einen Kopierkonstruktor und definiert ihn als `deleted` . Wenn eine Klasse einen bewegungskonstruktor oder Bewegungs Zuweisungs Operator deklariert, aber nicht explizit einen Kopier Zuweisungs Operator deklariert, deklariert der Compiler implizit einen Kopier Zuweisungs Operator und definiert ihn als `deleted` . Um dieses Problem zu beheben, müssen Sie diese Member explizit deklarieren.

Wenn Error C2280 in Verbindung mit einem angezeigt wird `unique_ptr` , liegt dies fast sicherlich daran, dass Sie versuchen, den Kopierkonstruktor aufzurufen, bei dem es sich um eine `deleted` Funktion handelt. Entwurfs bedingt `unique_ptr` kann nicht kopiert werden. Verwenden Sie stattdessen einen bewegungskonstruktor zum Übertragen des Besitzes.

```cpp
// C2280_move.cpp
// compile with: cl /c C2280_move.cpp
class base
{
public:
    base();
    ~base();
    base(base&&);
    // Move constructor causes copy constructor to be
    // implicitly declared as deleted. To fix this
    // issue, you can explicitly declare a copy constructor:
    // base(base&);
    // If you want the compiler default version, do this:
    // base(base&) = default;
};

void copy(base *p)
{
    base b{*p};  // C2280
}
```

## <a name="example-variant-and-volatile-members"></a>Beispiel: Variant und volatile-Member

Versionen des Compilers vor Visual Studio 2015 Update 2 waren nicht konform und generierte Standardkonstruktoren und Dekonstruktoren für anonyme Unions. Diese werden jetzt implizit als deklariert `deleted` . Diese Versionen erlaubten auch eine nicht konforme implizite Definition von **`default`** Kopier-und verschiebungskonstruktoren und **`default`** Kopier-und Verschiebungs Zuweisungs Operatoren in Klassen und Strukturen, die über Element **`volatile`** Variablen verfügen. Der Compiler betrachtet diese nun als nicht triviale Konstruktoren und Zuweisungs Operatoren und generiert keine **`default`** Implementierungen. Wenn eine solche Klasse ein Member einer Union oder eine anonyme Union innerhalb einer Klasse ist, werden die Kopier-und bewegungskonstruktoren und die Kopier-und Verschiebungs Zuweisungs Operatoren der Union oder Klasse implizit als definiert `deleted` . Um dieses Problem zu beheben, müssen Sie explizit die erforderlichen speziellen Member-Funktionen deklarieren.

```cpp
// C2280_variant.cpp
// compile with: cl /c C2280_variant.cpp
struct A {
    A() = default;
    A(const A&);
};

struct B {
    union {
        A a;
        int i;
    };
    // To fix this issue, declare the required
    // special member functions:
    // B();
    // B(const B& b);
};

int main() {
    B b1;
    B b2(b1);  // C2280
}
```

## <a name="example-indirect-base-members-deleted"></a>Beispiel: indirekte Basismember gelöscht

Versionen des Compilers vor Visual Studio 2015 Update 2 waren nicht konform und ermöglichten, dass eine abgeleitete Klasse besondere Member-Funktionen von indirekt abgeleiteten `private virtual` Basisklassen aufrief. Der Compiler gibt jetzt einen Compilerfehler aus C2280 wenn ein solcher-Rückruf erfolgt.

In diesem Beispiel wird die Klasse `top` indirekt von der privaten virtuellen Klasse abgeleitet `base` . In übereinstimmenden Code werden dadurch die Member von `base` nicht mehr zugänglich `top` . ein Objekt vom Typ `top` kann nicht standardmäßig erstellt oder zerstört werden. Um dieses Problem im Code zu beheben, der auf das alte Compilerverhalten beruht, ändern Sie die-Zwischenklasse so, dass Sie `protected virtual` abgeleitet wird, oder ändern Sie die-Klasse, sodass `top` Sie die direkte Ableitung verwendet:

```cpp
// C2280_indirect.cpp
// compile with: cl /c C2280_indirect.cpp
class base
{
protected:
    base();
    ~base();
};

class middle : private virtual base {};
// Possible fix: Replace line above with:
// class middle : protected virtual base {};
class top : public virtual middle {};    // C4594, C4624
// Another possible fix: use direct derivation:
// class top : public virtual middle, private virtual base {};

void destroy(top *p)
{
    delete p;  // C2280
}
```
