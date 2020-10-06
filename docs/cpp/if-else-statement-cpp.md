---
title: If-Else-Anweisung (C++)
description: Verwenden Sie "If-Else", "If-Else" mit dem Initialisierer und "if-constexpr"-Anweisungen zum Steuern der bedingten Verzweigung.
ms.date: 10/02/2020
f1_keywords:
- else_cpp
- if_cpp
helpviewer_keywords:
- if keyword [C++]
- else keyword [C++]
ms.assetid: f8c45cde-6bce-42ae-81db-426b3dbd4caa
ms.openlocfilehash: 20d828bf00a79687fe0a9fffbeb1a9cc56fae08c
ms.sourcegitcommit: 30792632548d1c71894f9fecbe2f554294b86020
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/06/2020
ms.locfileid: "91765301"
---
# <a name="if-else-statement-c"></a>If-Else-Anweisung (C++)

Eine if-else-Anweisung steuert die bedingte Verzweigung. -Anweisungen in *`if-branch`* werden nur ausgeführt, wenn der *`condition`* -Wert einen Wert ungleich 0 (null) ergibt (oder **`true`** ). Wenn der Wert von ungleich *`condition`* NULL ist, wird die folgende-Anweisung ausgeführt, und die-Anweisung, die auf den optionalen folgt, **`else`** wird übersprungen. Andernfalls wird die folgende-Anweisung ausgelassen, und wenn ein vorhanden ist, **`else`** wird die-Anweisung ausgeführt, die nach dem **`else`** ausgeführt wird.

*`condition`* Ausdrücke, die als ungleich NULL ausgewertet werden, sind:

- **`true`**
- ein nicht-NULL-Zeiger,
- ein arithmetischer Wert ungleich 0 (null) oder
- ein Klassentyp, der eine eindeutige Konvertierung in einen arithmetischen, booleschen oder Zeigertyp definiert. (Informationen zu Konvertierungen finden Sie unter [Standard Konvertierungen](../cpp/standard-conversions.md).)

## <a name="syntax"></a>Syntax

*`init-statement`*:\
&emsp; *`expression-statement`*\
&emsp; *`simple-declaration`*

*`condition`*:\
&emsp; *`expression`*\
&emsp;*`attribute-specifier-seq`* <sub>*opt*</sub> *`decl-specifier-seq`* opt *`declarator`**`brace-or-equal-initializer`*

*`statement`*:\
&emsp; *`expression-statement`*\
&emsp; *`compound-statement`*

*`expression-statement`*:\
&emsp;*`expression`* <sub>*opt*</sub>**`;`**

*`compound-statement`*:\
&emsp;**`{`** *`statement-seq`* <sub>*opt*</sub>**`}`**

*`statement-seq`*:\
&emsp; *`statement`*\
&emsp; *`statement-seq`* *`statement`*

*`if-branch`*:\
&emsp; *`statement`*

*`else-branch`*:\
&emsp; *`statement`*

*`selection-statement`*:\
&emsp;**`if`** **`constexpr`** <sub>*opt*</sub><sup>17</sup> **`(`** *`init-statement`* <sub>*opt*</sub><sup>17</sup> 17 *`condition`* **`)`***`if-branch`*\
&emsp;**`if`** **`constexpr`** <sub>*opt*</sub><sup>17</sup> **`(`** *`init-statement`* <sub>*opt*</sub><sup>17</sup> 17 *`condition`* **`)`** *`if-branch`* **`else`***`else-branch`*

<sup>17</sup> dieses optionale Element ist ab c++ 17 verfügbar.

## <a name="if-else-statements"></a>if-else-Anweisungen

In allen Formen der- **`if`** Anweisung, *`condition`* die einen beliebigen Wert außer einer Struktur aufweisen kann, wird ausgewertet, einschließlich aller Nebeneffekte. Die Steuerung wird von der- **`if`** Anweisung an die nächste Anweisung im Programm weitergeleitet, es sei denn, die ausgeführte *`if-branch`* oder *`else-branch`* enthält [`break`](../cpp/break-statement-cpp.md) , [`continue`](../cpp/continue-statement-cpp.md) oder [`goto`](../cpp/goto-statement-cpp.md) .

Die-Klausel einer- **`else`** `if...else` Anweisung ist mit der nächstgelegenen vorangehenden- **`if`** Anweisung in demselben Bereich verknüpft, der keine entsprechende- **`else`** Anweisung hat.

### <a name="example"></a>Beispiel

Dieser Beispielcode zeigt mehrere **`if`** verwendete-Anweisungen, sowohl mit als auch ohne **`else`** :

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

## <a name="if-statement-with-an-initializer"></a><a name="if_with_init"></a> if-Anweisung mit einem Initialisierer

Ab c++ 17 kann eine- **`if`** Anweisung auch einen Ausdruck enthalten *`init-statement`* , der eine benannte Variable deklariert und initialisiert. Verwenden Sie diese Form der if-Anweisung, wenn die Variable nur im Gültigkeitsbereich der if-Anweisung benötigt wird. **Microsoft-spezifisch**: dieses Formular ist ab Visual Studio 2017 Version 15,3 verfügbar und erfordert mindestens die- [`/std:c++17`](../build/reference/std-specify-language-standard-version.md) Compileroption.

### <a name="example"></a>Beispiel

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

## <a name="a-nameif_constexpr-if-constexpr-statements"></a><a name="if_constexpr"> if-Anweisungen (constexpr)

Ab c++ 17 können Sie eine- **`if constexpr`** Anweisung in Funktions Vorlagen verwenden, um Entscheidungen zur Kompilierzeit Verzweigung zu treffen, ohne auf mehrere Funktions Überladungen zurückgreifen zu müssen. **Microsoft-spezifisch**: dieses Formular ist ab Visual Studio 2017 Version 15,3 verfügbar und erfordert mindestens die- [`/std:c++17`](../build/reference/std-specify-language-standard-version.md) Compileroption.

### <a name="example"></a>Beispiel

Dieses Beispiel zeigt, wie Sie eine einzelne Funktion schreiben können, die das Entpacken von Parametern behandelt. Keine NULL-Parameter Überladung erforderlich:

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

## <a name="see-also"></a>Siehe auch

[Auswahl Anweisungen](../cpp/selection-statements-cpp.md)\
[Keywords](../cpp/keywords-cpp.md)\
[`switch`-Anweisung (C++)](../cpp/switch-statement-cpp.md)
