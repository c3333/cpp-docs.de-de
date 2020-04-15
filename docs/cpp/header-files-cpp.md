---
title: Headerdateien (C++)
ms.date: 12/11/2019
helpviewer_keywords:
- header files [C++]
ms.openlocfilehash: 4ab6a2b2626cde94f35678bc9ec789b80d493b8f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367229"
---
# <a name="header-files-c"></a>Headerdateien (C++)

Die Namen von Programmelementen wie Variablen, Funktionen, Klassen usw. müssen deklariert werden, bevor sie verwendet werden können. Sie können z. B. `x = 42` nicht einfach schreiben, ohne vorher "x" zu deklarieren.

```cpp
int x; // declaration
x = 42; // use x
```

Die Deklaration teilt dem Compiler mit, ob es sich bei dem Element um ein **int**, ein **double**, eine **Funktion**, eine **Klasse** oder etwas anderes handelt.  Darüber hinaus muss jeder Name (direkt oder indirekt) in jeder CPP-Datei deklariert werden, in der er verwendet wird. Wenn Sie ein Programm kompilieren, wird jede .cpp-Datei unabhängig in eine Kompilierungseinheit kompiliert. Der Compiler weiß nicht, welche Namen in anderen Kompilierungseinheiten deklariert werden. Das bedeutet, dass Sie, wenn Sie eine Klasse oder Funktion oder eine globale Variable definieren, eine Deklaration dieses Dings in jeder zusätzlichen CPP-Datei bereitstellen müssen, die sie verwendet. Jede Deklaration dieses Dings muss in allen Dateien genau identisch sein. Eine leichte Inkonsistenz führt zu Fehlern oder unbeabsichtigtem Verhalten, wenn der Linker versucht, alle Kompilierungseinheiten in einem einzigen Programm zusammenzuführen.

Um das Fehlerpotenzial zu minimieren, hat C++ die Konvention angenommen, *Headerdateien* zum Speichern von Deklarationen zu verwenden. Sie erstellen die Deklarationen in einer Headerdatei und verwenden dann die #include-Direktive in jeder CPP-Datei oder einer anderen Headerdatei, die diese Deklaration erfordert. Die #include-Direktive fügt vor der Kompilierung eine Kopie der Headerdatei direkt in die CPP-Datei ein.

> [!NOTE]
> In Visual Studio 2019 wird die *modules* C++20-Modulfunktion als Verbesserung und eventueller Ersatz für Headerdateien eingeführt. Weitere Informationen finden Sie unter [Übersicht über Module in C++](modules-cpp.md).

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt eine allgemeine Möglichkeit, eine Klasse zu deklarieren und dann in einer anderen Quelldatei zu verwenden. Wir beginnen mit der Headerdatei `my_class.h`. Sie enthält eine Klassendefinition, weist jedoch darauf hin, dass die Definition unvollständig ist. die Memberfunktion `do_something` ist nicht definiert:

```cpp
// my_class.h
namespace N
{
    class my_class
    {
    public:
        void do_something();
    };

}
```

Erstellen Sie als Nächstes eine Implementierungsdatei (in der Regel mit einer CPP-Erweiterung oder einer ähnlichen Erweiterung). Wir rufen die Datei my_class.cpp auf und stellen eine Definition für die Memberdeklaration bereit. Wir fügen `#include` eine Direktive für die Datei "my_class.h" hinzu, um die my_class-Erklärung an `<iostream>` dieser Stelle in `std::cout`die .cpp-Datei einfügen zu lassen, und wir schließen ein, um die Deklaration für einzuschließen. Beachten Sie, dass Anführungszeichen für Headerdateien im gleichen Verzeichnis wie die Quelldatei und für Standardbibliotheksheader verwendet werden. Außerdem haben viele Standardbibliotheksheader keine .h oder eine andere Dateierweiterung.

In der Implementierungsdatei können wir optional eine **using-Anweisung** verwenden, um zu vermeiden, dass jede Erwähnung von "my_class" oder "cout" mit "N::" oder "std::" qualifiziert werden muss.  Setzen Sie keine **Anweisungen** in Ihre Headerdateien!

```cpp
// my_class.cpp
#include "my_class.h" // header in local directory
#include <iostream> // header in standard library

using namespace N;
using namespace std;

void my_class::do_something()
{
    cout << "Doing something!" << endl;
}
```

Jetzt können `my_class` wir in einer anderen .cpp-Datei verwenden. Wir #include die Headerdatei, sodass der Compiler die Deklaration abruft. Der Compiler muss nur wissen, dass my_class eine Klasse `do_something()`ist, die über eine öffentliche Memberfunktion namens verfügt.

```cpp
// my_program.cpp
#include "my_class.h"

using namespace N;

int main()
{
    my_class mc;
    mc.do_something();
    return 0;
}
```

Nachdem der Compiler die Kompilierung jeder .cpp-Datei in .obj-Dateien abgeschlossen hat, übergibt er die .obj-Dateien an den Linker. Wenn der Linker die Objektdateien zusammenführt, findet er genau eine Definition für my_class; es befindet sich in der .obj-Datei, die für my_class.cpp erstellt wurde, und der Build ist erfolgreich.

## <a name="include-guards"></a>Einschließen von Wächtern

In der Regel verfügen Headerdateien `#pragma once` über einen Include *Guard* oder eine Direktive, um sicherzustellen, dass sie nicht mehrmals in eine einzelne CPP-Datei eingefügt werden.

```cpp
// my_class.h
#ifndef MY_CLASS_H // include guard
#define MY_CLASS_H

namespace N
{
    class my_class
    {
    public:
        void do_something();
    };
}

#endif /* MY_CLASS_H */
```

## <a name="what-to-put-in-a-header-file"></a>Was in eine Headerdatei zu setzen

Da eine Headerdatei möglicherweise von mehreren Dateien enthalten ist, kann sie keine Definitionen enthalten, die mehrere Definitionen mit demselben Namen erzeugen können. Die folgenden Sind nicht zulässig oder gelten als sehr schlechte Praxis:

- integrierte Typdefinitionen im Namespace oder globalen Bereich
- Nicht-Inline-Funktionsdefinitionen
- Nicht-Const-Variablendefinitionen
- Aggregierte Definitionen
- Unbenannte Namespaces
- using-Direktiven

Die Verwendung **using** der using-Direktive verursacht nicht notwendigerweise einen Fehler, kann aber möglicherweise ein Problem verursachen, da sie den Namespace in jede CPP-Datei, die diesen Header direkt oder indirekt enthält, in den Gültigkeitsbereich bringt.

## <a name="sample-header-file"></a>Beispielheaderdatei

Das folgende Beispiel zeigt die verschiedenen Arten von Deklarationen und Definitionen, die in einer Headerdatei zulässig sind:

```cpp
// sample.h
#pragma once
#include <vector> // #include directive
#include <string>

namespace N  // namespace declaration
{
    inline namespace P
    {
        //...
    }

    enum class colors : short { red, blue, purple, azure };

    const double PI = 3.14;  // const and constexpr definitions
    constexpr int MeaningOfLife{ 42 };
    constexpr int get_meaning()
    {
        static_assert(MeaningOfLife == 42, "unexpected!"); // static_assert
        return MeaningOfLife;
    }
    using vstr = std::vector<int>;  // type alias
    extern double d; // extern variable

#define LOG   // macro definition

#ifdef LOG   // conditional compilation directive
    void print_to_log();
#endif

    class my_class   // regular class definition,
    {                // but no non-inline function definitions

        friend class other_class;
    public:
        void do_something();   // definition in my_class.cpp
        inline void put_value(int i) { vals.push_back(i); } // inline OK

    private:
        vstr vals;
        int i;
    };

    struct RGB
    {
        short r{ 0 };  // member initialization
        short g{ 0 };
        short b{ 0 };
    };

    template <typename T>  // template definition
    class value_store
    {
    public:
        value_store<T>() = default;
        void write_value(T val)
        {
            //... function definition OK in template
        }
    private:
        std::vector<T> vals;
    };

    template <typename T>  // template declaration
    class value_widget;
}
```
