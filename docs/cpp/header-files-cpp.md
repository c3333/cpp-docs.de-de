---
title: Header Dateien (C++)
ms.date: 12/11/2019
helpviewer_keywords:
- header files [C++]
ms.openlocfilehash: 0b76773b8b7d55645c807588fe41b242df9eea2f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227451"
---
# <a name="header-files-c"></a>Header Dateien (C++)

Die Namen der Programmelemente (z. b. Variablen, Funktionen, Klassen usw.) müssen deklariert werden, bevor Sie verwendet werden können. Beispielsweise können Sie nicht einfach schreiben, `x = 42` ohne zuerst "x" zu deklarieren.

```cpp
int x; // declaration
x = 42; // use x
```

Die-Deklaration teilt dem Compiler mit, ob das Element ein **`int`** , ein **`double`** , eine **Funktion**, ein oder ein anderes Element ist **`class`** .  Außerdem muss jeder Name (direkt oder indirekt) in jeder cpp-Datei deklariert werden, in der er verwendet wird. Wenn Sie ein Programm kompilieren, wird jede cpp-Datei unabhängig in eine Kompilierungseinheit kompiliert. Der Compiler weiß nicht, welche Namen in anderen Kompilierungs Einheiten deklariert werden. Das heißt, wenn Sie eine Klasse oder eine Funktion oder eine globale Variable definieren, müssen Sie in jeder zusätzlichen cpp-Datei, die Sie verwendet, eine Deklaration dieser Funktion bereitstellen. Jede Deklaration dieses Objekts muss in allen Dateien genau identisch sein. Eine geringfügige Inkonsistenz führt zu Fehlern oder unbeabsichtigtem Verhalten, wenn der Linker versucht, alle Kompilierungs Einheiten in einem einzigen Programm zusammenzuführen.

Um das Fehlerpotenzial zu minimieren, hat C++ die Konvention zur Verwendung von *Header Dateien* zum enthalten von Deklarationen übernommen. Sie nehmen die Deklarationen in einer Header Datei vor und verwenden dann die #include-Direktive in jeder cpp-Datei oder einer anderen Header Datei, die diese Deklaration erfordert. Die #include-Direktive fügt vor der Kompilierung eine Kopie der Header Datei direkt in die CPP-Datei ein.

> [!NOTE]
> In Visual Studio 2019 wird das Feature "c++ 20 *modules* " als Verbesserung und schließlich Ersetzung für Header Dateien eingeführt. Weitere Informationen finden Sie unter [Übersicht über Module in C++](modules-cpp.md).

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt eine gängige Methode zum Deklarieren einer Klasse und deren Verwendung in einer anderen Quelldatei. Wir beginnen mit der Header Datei, `my_class.h` . Sie enthält eine Klassendefinition, aber beachten Sie, dass die Definition unvollständig ist. die Member-Funktion `do_something` ist nicht definiert:

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

Erstellen Sie als nächstes eine Implementierungs Datei (in der Regel mit einer cpp-Erweiterung oder einer ähnlichen Erweiterung). Wir nennen die Datei my_class. cpp und geben eine Definition für die Element Deklaration an. Wir fügen eine- `#include` Direktive für die Datei "my_class. h" hinzu, damit die my_class Deklaration an dieser Stelle in die CPP-Datei eingefügt wird, und wir schließen ein, um `<iostream>` die Deklaration für abzurufen `std::cout` . Beachten Sie, dass Anführungszeichen für Header Dateien im gleichen Verzeichnis wie die Quelldatei verwendet werden und spitzen Klammern für die Header der Standardbibliothek verwendet werden. Außerdem verfügen viele Standard Bibliotheks Header nicht über die Dateierweiterung ". h" oder eine andere Dateierweiterung.

In der Implementierungs Datei können wir optional eine-Anweisung verwenden, **`using`** um zu vermeiden, dass Sie jede Erwähnung von "my_class" oder "cout" mit "N::" oder "Std::" qualifizieren müssen.  Fügen Sie keine- **`using`** Anweisungen in Ihre Header Dateien ein.

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

Nun können wir `my_class` in einer anderen cpp-Datei verwenden. Wir #include die Header Datei, sodass der Compiler die Deklaration abruft. Der Compiler muss wissen, dass my_class eine Klasse ist, die über eine öffentliche Member-Funktion mit dem Namen verfügt `do_something()` .

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

Nachdem der Compiler das Kompilieren der CPP-Datei in OBJ-Dateien abgeschlossen hat, übergibt er die OBJ-Dateien an den Linker. Wenn der Linker die Objektdateien zusammenfasst, findet er genau eine Definition für my_class; Sie befindet sich in der obj-Datei, die für my_class. cpp erstellt wurde, und der Build ist erfolgreich.

## <a name="include-guards"></a>Schutz einschließen

Header Dateien verfügen in der Regel über einen *include-Wächter* oder eine- `#pragma once` Direktive, um sicherzustellen, dass Sie nicht mehrmals in eine einzelne cpp-Datei eingefügt werden.

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

## <a name="what-to-put-in-a-header-file"></a>Was Sie in eine Header Datei einfügen müssen

Da eine Header Datei möglicherweise von mehreren Dateien eingeschlossen werden kann, kann Sie keine Definitionen enthalten, die möglicherweise mehrere Definitionen desselben Namens enthalten. Folgendes ist nicht zulässig oder wird als äußerst schlechte Vorgehensweise angesehen:

- integrierte Typdefinitionen im Namespace oder globalen Gültigkeitsbereich
- nicht Inline Funktionsdefinitionen
- nicht konstanten Variablen Definitionen
- Aggregat Definitionen
- Unbenannte Namespaces
- using-Direktiven

Die Verwendung der- **`using`** Direktive löst nicht notwendigerweise einen Fehler aus, kann jedoch zu einem Problem führen, da der Namespace in jeder cpp-Datei, die diesen Header direkt oder indirekt enthält, in den Gültigkeitsbereich eingefügt wird.

## <a name="sample-header-file"></a>Beispiel Header Datei

Das folgende Beispiel zeigt die verschiedenen Arten von Deklarationen und Definitionen, die in einer Header Datei zulässig sind:

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
