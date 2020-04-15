---
title: Übersicht über Klassenmember
ms.date: 11/04/2016
helpviewer_keywords:
- members [C++], types of class members
- members [C++]
- class members [C++], types of
- class members
ms.assetid: 8802cfa9-705d-4f37-acde-245d6838010c
ms.openlocfilehash: cb978434707a9a7808b3388fc541ce4e0d996b0f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366676"
---
# <a name="class-member-overview"></a>Übersicht über Klassenmember

Eine Klasse oder Struktur besteht aus Membern. Die von einer Klasse ausgeführte Arbeit erfolgt über die Memberfunktionen. Den Zustand, den sie verwaltet, wird in Datenmembern gespeichert. Die Initialisierung von Elementen erfolgt durch Konstruktoren, und Bereinigungsarbeiten wie das Freigeben von Speicher und das Freigeben von Ressourcen werden von Destruktoren durchgeführt. In C++11 und höher können Datenmember (und sollten in der Regel) beim Deklarieren initialisiert werden.

## <a name="kinds-of-class-members"></a>Typen von Klassenmembern

Eine vollständige Liste der Memberkategorien finden Sie im Folgenden:

- [Spezielle Mitgliedsfunktionen](special-member-functions.md).

- [Überblick über die Mitgliedsfunktionen](overview-of-member-functions.md).

- [Datenmember,](static-members-cpp.md) einschließlich integrierter Typen und anderer benutzerdefinierter Typen.

- Operatoren

- [Verschachtelte Klassendeklarationen](nested-class-declarations.md) und.)

- [Unions](unions.md)

- [Enumerationen](../cpp/enumerations-cpp.md).

- [Bitfelder](../cpp/cpp-bit-fields.md).

- [Freunde](../cpp/friend-cpp.md).

- [Aliase und typedefs](../cpp/aliases-and-typedefs-cpp.md).

    > [!NOTE]
    >  Friends sind in der vorangehenden Liste inbegriffen, da sie in der Klassendeklaration enthalten sind. Es sind jedoch keine echten Klassenmember, da sie nicht im Gültigkeitsbereich der Klasse liegen.

## <a name="example-class-declaration"></a>Beispiel für eine Klassendeklaration

Im folgenden Beispiel wird eine einfache Klassendeklaration dargestellt:

```cpp
// TestRun.h

class TestRun
{
    // Start member list.

    //The class interface accessible to all callers.
public:
    // Use compiler-generated default constructor:
    TestRun() = default;
    // Don't generate a copy constructor:
    TestRun(const TestRun&) = delete;
    TestRun(std::string name);
    void DoSomething();
    int Calculate(int a, double d);
    virtual ~TestRun();
    enum class State { Active, Suspended };

    // Accessible to this class and derived classes only.
protected:
    virtual void Initialize();
    virtual void Suspend();
    State GetState();

    // Accessible to this class only.
private:
    // Default brace-initialization of instance members:
    State _state{ State::Suspended };
    std::string _testName{ "" };
    int _index{ 0 };

    // Non-const static member:
    static int _instances;
    // End member list.
};

// Define and initialize static member.
int TestRun::_instances{ 0 };
```

## <a name="member-accessibility"></a>Memberzugriff

Die Member einer Klasse werden in der Memberliste deklariert. Die Memberliste einer Klasse kann in eine beliebige Anzahl **privater,** **geschützter** und **öffentlicher** Abschnitte unterteilt werden, die Schlüsselwörter verwenden, die als Zugriffsbezeichner bezeichnet werden.  Ein Doppelpunkt **:** muss dem Zugriffsbezeichner folgen.  Diese Abschnitte müssen nicht fortlaufend sein, d. h. sämtliche dieser Schlüsselwörter können möglicherweise mehrmals in der Memberliste vorkommen.  Das Schlüsselwort legt den Zugriff aller Member bis zum nächsten Zugriffsspezifizierer oder zur schließenden Klammer fest. Weitere Informationen finden Sie unter [Member Access Control (C++)](../cpp/member-access-control-cpp.md).

## <a name="static-members"></a>Statische Member

Ein Datenmember kann als statisch deklariert werden, was bedeutet, dass alle Objekte der Klasse auf die gleiche Kopie zugreifen. Eine Memberfunktion kann als statisch deklariert werden, in diesem Fall kann sie nur auf statische Datenmember der Klasse zugreifen (und hat keinen *Zeiger).* Weitere Informationen finden Sie unter [Statische Datenmember](../cpp/static-members-cpp.md).

## <a name="special-member-functions"></a>Spezielle Memberfunktionen

Spezielle Memberfunktionen stellen Funktionen dar, die vom Compiler automatisch bereitgestellt werden, wenn Sie sie nicht im Quellcode angeben.

1. Standardkonstruktor

1. Kopierkonstruktor

1. **(C++11)** Move-Konstruktor

1. Kopierzuweisungsoperator

1. **(C++11)** Zuweisungsoperator verschieben

1. Destruktor

Weitere Informationen finden Sie unter [Spezielle Mitgliedsfunktionen](../cpp/special-member-functions.md).

## <a name="memberwise-initialization"></a>Memberspezifische Initialisierung

Nicht statische Memberdeklaratoren können in C++11 und höher Initialisierer enthalten.

```cpp
class CanInit
{
public:
    long num {7};       // OK in C++11
    int k = 9;          // OK in C++11
    static int i = 9; // Error: must be defined and initialized
                      // outside of class declaration.

    // initializes num to 7 and k to 9
    CanInit(){}

    // overwrites original initialized value of num:
    CanInit(int val) : num(val) {}
};
int main()
{
}
```

Wenn einem Member ein Wert in einem Konstruktor zugewiesen ist, überschreibt dieser Wert den Wert, mit dem der Member zum Zeitpunkt der Deklaration initialisiert wurde.

Es ist nur eine gemeinsame Kopie der statischen Datenmember für alle Objekte eines gegebenen Klassentyps vorhanden. Statische Datenmember müssen definiert werden und können im Dateigültigkeitsbereich initialisiert werden. (Weitere Informationen zu statischen Datenmembern finden Sie unter [Statische Datenmember](../cpp/static-members-cpp.md).) Das folgende Beispiel zeigt, wie diese Initialisierungen durchgeführt werden:

```cpp
// class_members2.cpp
class CanInit2
{
public:
    CanInit2() {} // Initializes num to 7 when new objects of type
                 //  CanInit are created.
    long     num {7};
    static int i;
    static int j;
};

// At file scope:

// i is defined at file scope and initialized to 15.
// The initializer is evaluated in the scope of CanInit.
int CanInit2::i = 15;

// The right side of the initializer is in the scope
// of the object being initialized
int CanInit2::j = i;
```

> [!NOTE]
> Dem Klassennamen `CanInit2` muss `i` vorausgehen, um anzugeben, dass das definierte `i` ein Member der Klasse `CanInit2` ist.

## <a name="see-also"></a>Siehe auch

[Klassen und Strukturen](../cpp/classes-and-structs-cpp.md)
