---
title: if-else-Anweisung (C++)
ms.date: 07/20/2019
description: Verwenden Sie if-else-Anweisungen in C++, um bedingte Verzweigungen zu steuern.
f1_keywords:
- else_cpp
- if_cpp
helpviewer_keywords:
- if keyword [C++]
- else keyword [C++]
ms.assetid: f8c45cde-6bce-42ae-81db-426b3dbd4caa
ms.openlocfilehash: a9256e32c89890635c5473a85b4bb3b56bec26d4
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87187568"
---
# <a name="if-else-statement-c"></a>if-else-Anweisung (C++)

Steuert den bedingten Branch. Anweisungen im *If-Block* werden nur ausgeführt, wenn der *if-Expression* einen Wert ungleich 0 (null) ergibt (oder **`true`** ). Wenn der Wert des *Ausdrucks* ungleich 0 (null) ist, werden *Anweisung1* und alle anderen Anweisungen im Block ausgeführt, und der Else-Block wird übersprungen. Wenn der Wert von *Expression* NULL ist, wird der If-Block ausgelassen, und der Else-Block wird ausgeführt, falls vorhanden. Ausdrücke, die als ungleich NULL ausgewertet werden, sind

- **`true`**
- ein nicht-NULL-Zeiger,
- ein arithmetischer Wert ungleich 0 (null) oder
- ein Klassentyp, der eine eindeutige Konvertierung in einen arithmetischen, booleschen oder Zeigertyp definiert. (Informationen zu Konvertierungen finden Sie unter [Standard Konvertierungen](../cpp/standard-conversions.md).)

## <a name="syntax"></a>Syntax

```cpp
if ( expression )
{
   statement1;
   ...
}
else  // optional
{
   statement2;
   ...
}

// C++17 - Visual Studio 2017 version 15.3 and later:
if ( initialization; expression )
{
   statement1;
   ...
}
else  // optional
{
   statement2;
   ...
}

// C++17 - Visual Studio 2017 version 15.3 and later:
if constexpr (expression)
{
    statement1;
    ...
}
else  // optional
{
   statement2;
   ...
}
```

## <a name="example"></a>Beispiel

```cpp
// if_else_statement.cpp
#include <iostream>

using namespace std;

class C
{
    public:
    void do_something(){}
};
void init(C){}
bool is_true() { return true; }
int x = 10;

int main()
{
    if (is_true())
    {
        cout << "b is true!\n";  // executed
    }
    else
    {
        cout << "b is false!\n";
    }

    // no else statement
    if (x == 10)
    {
        x = 0;
    }

    C* c;
    init(c);
    if (c)
    {
        c->do_something();
    }
    else
    {
        cout << "c is null!\n";
    }
}
```

## <a name="if-statement-with-an-initializer"></a><a name="if_with_init"></a>if-Anweisung mit einem Initialisierer

**Visual Studio 2017 Version 15,3 und** höher (verfügbar mit [/Std: c++ 17](../build/reference/std-specify-language-standard-version.md)): eine- **`if`** Anweisung kann auch einen Ausdruck enthalten, der eine benannte Variable deklariert und initialisiert. Verwenden Sie diese Form der if-Anweisung, wenn die Variable nur im Bereich des If-Blocks benötigt wird.

## <a name="example"></a>Beispiel

```cpp
#include <iostream>
#include <mutex>
#include <map>
#include <string>
#include <algorithm>

using namespace std;

map<int, string> m;
mutex mx;
bool shared_flag; // guarded by mx
void unsafe_operation() {}

int main()
{

    if (auto it = m.find(10); it != m.end())
    {
        cout << it->second;
        return 0;
    }

    if (char buf[10]; fgets(buf, 10, stdin))
    {
        m[0] += buf;
    }

    if (lock_guard<mutex> lock(mx); shared_flag)
    {
        unsafe_operation();
        shared_flag = false;
    }

    string s{ "if" };
    if (auto keywords = { "if", "for", "while" }; any_of(keywords.begin(), keywords.end(), [&s](const char* kw) { return s == kw; }))
    {
        cout << "Error! Token must not be a keyword\n";
    }
}
```

In allen Formen der- **`if`** Anweisung wird *Expression*, der einen beliebigen Wert außer einer Struktur aufweisen kann, ausgewertet, einschließlich aller Nebeneffekte. Die Steuerung wird von der- **`if`** Anweisung an die nächste Anweisung im Programm weitergeleitet, es sei denn, eine der Anweisungen s enthält eine [break](../cpp/break-statement-cpp.md)-, [Continue](../cpp/continue-statement-cpp.md)-oder [goto](../cpp/goto-statement-cpp.md) *-Anweisung*.

Die-Klausel einer- **`else`** `if...else` Anweisung ist der nächstgelegenen vorangehenden **`if`** Anweisung in demselben Bereich zugeordnet, der keine entsprechende- **`else`** Anweisung hat.

## <a name="a-nameif_constexpr-if-constexpr-statements"></a><a name="if_constexpr">if-Anweisungen (constexpr)

**Visual Studio 2017 Version 15,3 und** höher (verfügbar mit [/Std: c++ 17](../build/reference/std-specify-language-standard-version.md)): in Funktions Vorlagen können Sie mit einer **if constexpr** -Anweisung Kompilierzeit-Verzweigungs Entscheidungen treffen, ohne auf mehrere Funktions Überladungen zurückgreifen zu müssen. Sie können z. b. eine einzelne Funktion schreiben, die das Entpacken von Parametern behandelt (keine NULL-Parameter Überladung erforderlich):

```cpp
template <class T, class... Rest>
void f(T&& t, Rest&&... r)
{
    // handle t
    do_something(t);

    // handle r conditionally
    if constexpr (sizeof...(r))
    {
        f(r...);
    }
    else
    {
        g(r...);
    }
}
```

## <a name="see-also"></a>Weitere Informationen

[Auswahlanweisungen](../cpp/selection-statements-cpp.md)<br/>
[Schlüsselwörter](../cpp/keywords-cpp.md)<br/>
[Switch-Anweisung (C++)](../cpp/switch-statement-cpp.md)
