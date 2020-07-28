---
title: Compilerfehler C2143
ms.date: 11/04/2016
f1_keywords:
- C2143
helpviewer_keywords:
- C2143
ms.assetid: 1d8d1456-e031-4965-9240-09a6e33ba81c
ms.openlocfilehash: 310083a650f842c6c0f0912efe1ceddb66c4fd6f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214749"
---
# <a name="compiler-error-c2143"></a>Compilerfehler C2143

Syntax Fehler: Fehlendes ' ttoken1 ' vor ' Token2 '

Der Compiler hat ein bestimmtes Token (d. h. ein anderes sprach Element als Leerraum) erwartet und stattdessen ein anderes Token gefunden.

Überprüfen Sie die [C++-Sprachreferenz](../../cpp/cpp-language-reference.md) , um zu bestimmen, wo Code syntaktisch falsch ist. Da der Compiler diesen Fehler möglicherweise meldet, nachdem er auf die Zeile stößt, die das Problem verursacht hat, überprüfen Sie mehrere Codezeilen, die dem Fehler vorangestellt sind.

C2143 kann in verschiedenen Situationen auftreten.

Dies kann vorkommen, wenn einem Operator, der einen Namen ( `::` , `->` und) qualifizieren kann `.` , das-Schlüsselwort folgen muss **`template`** , wie in diesem Beispiel:

```cpp
class MyClass
{
    template<class Ty, typename PropTy>
    struct PutFuncType : public Ty::PutFuncType<Ty, PropTy> // error C2143
    {
    };
};
```

Standardmäßig geht C++ davon aus, dass `Ty::PutFuncType` keine Vorlage `<` ist. Daher wird Folgendes als Vorzeichen interpretiert.  Sie müssen dem Compiler explizit mitteilen, dass `PutFuncType` es sich um eine Vorlage handelt, sodass die Spitze Klammer ordnungsgemäß analysiert werden kann. Um diesen Fehler zu beheben, verwenden Sie das **`template`** Schlüsselwort für den Namen des abhängigen Typs, wie hier gezeigt:

```cpp
class MyClass
{
    template<class Ty, typename PropTy>
    struct PutFuncType : public Ty::template PutFuncType<Ty, PropTy> // correct
    {
    };
};
```

C2143 kann auftreten, wenn **/CLR** verwendet wird und eine- **`using`** Direktive einen Syntax Fehler aufweist:

```cpp
// C2143a.cpp
// compile with: /clr /c
using namespace System.Reflection;   // C2143
using namespace System::Reflection;
```

Dies kann auch auftreten, wenn Sie versuchen, eine Quell Code Datei mithilfe der CLR-Syntax zu kompilieren, ohne auch **/CLR**zu verwenden:

```cpp
// C2143b.cpp
ref struct A {   // C2143 error compile with /clr
   void Test() {}
};

int main() {
   A a;
   a.Test();
}
```

Das erste Zeichen, das kein Leerzeichen ist, das auf eine-Anweisung folgt, **`if`** muss eine linke Klammer sein. Der Compiler kann nichts anderes übersetzen:

```cpp
// C2143c.cpp
int main() {
   int j = 0;

   // OK
   if (j < 25)
      ;

   if (j < 25)   // C2143
}
```

C2143 kann auftreten, wenn eine schließende geschweifte Klammer, Klammer oder Semikolon in der Zeile fehlt, in der der Fehler erkannt wird, oder in einer der oben genannten Zeilen:

```cpp
// C2143d.cpp
// compile with: /c
class X {
   int member1;
   int member2   // C2143
} x;
```

Oder wenn ein ungültiges Tag in einer Klassen Deklaration vorliegt:

```cpp
// C2143e.cpp
class X {
   int member;
} x;

class + {};   // C2143 + is an invalid tag name
class ValidName {};   // OK
```

Oder wenn eine Bezeichnung nicht an eine-Anweisung angefügt ist. Wenn Sie eine Bezeichnung selbst platzieren müssen, z. b. am Ende einer Verbund Anweisung, fügen Sie Sie an eine NULL-Anweisung an:

```cpp
// C2143f.cpp
// compile with: /c
void func1() {
   // OK
   end1:
      ;

   end2:   // C2143
}
```

Der Fehler kann auftreten, wenn ein nicht qualifizierter-Rückruf an einen Typ in der C++-Standard Bibliothek erfolgt:

```cpp
// C2143g.cpp
// compile with: /EHsc /c
#include <vector>
static vector<char> bad;   // C2143
static std::vector<char> good;   // OK
```

Oder es fehlt ein **`typename`** Schlüsselwort:

```cpp
// C2143h.cpp
template <typename T>
struct X {
   struct Y {
      int i;
   };
   Y memFunc();
};
template <typename T>
X<T>::Y X<T>::memFunc() {   // C2143
// try the following line instead
// typename X<T>::Y X<T>::memFunc() {
   return Y();
}
```

Oder wenn Sie versuchen, eine explizite Instanziierung zu definieren:

```cpp
// C2143i.cpp
// compile with: /EHsc /c
// template definition
template <class T>
void PrintType(T i, T j) {}

template void PrintType(float i, float j){}   // C2143
template void PrintType(float i, float j);   // OK
```

In einem C-Programm müssen Variablen am Anfang der Funktion deklariert werden, und Sie können nicht deklariert werden, nachdem die Funktion nicht Deklarations Anweisungen ausgeführt hat.

```C
// C2143j.c
int main()
{
    int i = 0;
    i++;
    int j = 0; // C2143
}
```
