---
title: Compilerfehler C2059
ms.date: 03/26/2019
f1_keywords:
- C2059
helpviewer_keywords:
- C2059
ms.assetid: 2be4eb39-3f37-4b32-8e8d-75835e07c78a
ms.openlocfilehash: 52b389806f5bacac78750bc745cd77699eb59735
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212877"
---
# <a name="compiler-error-c2059"></a>Compilerfehler C2059

Syntax Fehler: ' Token '

Das Token verursachte einen Syntax Fehler.

Im folgenden Beispiel wird eine Fehlermeldung für die Zeile generiert, die deklariert `j` .

```cpp
// C2059e.cpp
// compile with: /c
// C2143 expected
// Error caused by the incorrect use of '*'.
   int j*; // C2059
```

Um die Ursache des Fehlers zu ermitteln, untersuchen Sie nicht nur die Zeile, die in der Fehlermeldung aufgeführt ist, sondern auch die oben aufgeführten Zeilen. Wenn die Untersuchung der Zeilen keinen Hinweis auf das Problem liefert, versuchen Sie, die Zeile, die in der Fehlermeldung aufgeführt ist, und möglicherweise mehrere Zeilen darüber auszukommentieren.

Wenn die Fehlermeldung auf einem Symbol auftritt, das direkt auf eine **`typedef`** Variable folgt, stellen Sie sicher, dass die Variable im Quellcode definiert ist.

C2059 wird ausgelöst, wenn ein präprozessorsymbolname als Bezeichner wieder verwendet wird. Im folgenden Beispiel sieht der Compiler `DIGITS.ONE` als die Zahl 1, die als Enumerationselementname ungültig ist:

```cpp
#define ONE 1

enum class DIGITS {
    ZERO,
    ONE // error C2059
};
```

Möglicherweise erhalten Sie C2059, wenn ein Symbol zu "Nothing" ausgewertet wird, wenn das **/D**-_Symbol_ **=** zum Kompilieren verwendet wird.

```cpp
// C2059a.cpp
// compile with: /DTEST=
#include <stdio.h>

int main() {
   #ifdef TEST
      printf_s("\nTEST defined %d", TEST);   // C2059
   #else
      printf_s("\nTEST not defined");
   #endif
}
```

Ein weiterer Fall, in dem C2059 auftreten kann, ist die Kompilierung einer Anwendung, die eine Struktur in den Standardargumenten für eine Funktion angibt. Der Standardwert für ein Argument muss ein Ausdruck sein. Eine Initialisiererliste – z. b. eine, die zum Initialisieren einer Struktur verwendet wurde – ist kein Ausdruck.  Um dieses Problem zu beheben, definieren Sie einen Konstruktor, um die erforderliche Initialisierung auszuführen.

Im folgenden Beispiel wird C2059 generiert:

```cpp
// C2059b.cpp
// compile with: /c
struct ag_type {
   int a;
   float b;
   // Uncomment the following line to resolve.
   // ag_type(int aa, float bb) : a(aa), b(bb) {}
};

void func(ag_type arg = {5, 7.0});   // C2059
void func(ag_type arg = ag_type(5, 7.0));   // OK
```

C2059 kann bei einer falsch formatierten Umwandlung auftreten.

Im folgenden Beispiel wird C2059 generiert:

```cpp
// C2059c.cpp
// compile with: /clr
using namespace System;
ref class From {};
ref class To : public From {};

int main() {
   From^ refbase = gcnew To();
   To^ refTo = safe_cast<To^>(From^);   // C2059
   To^ refTo2 = safe_cast<To^>(refbase);   // OK
}
```

C2059 kann auch auftreten, wenn Sie versuchen, einen Namespace Namen zu erstellen, der einen-Zeitraum enthält.

Im folgenden Beispiel wird C2059 generiert:

```cpp
// C2059d.cpp
// compile with: /c
namespace A.B {}   // C2059

// OK
namespace A  {
   namespace B {}
}
```

C2059 kann auftreten, wenn einem Operator, der einen Namen ( `::` , `->` und) qualifizieren kann `.` , das-Schlüsselwort folgen muss **`template`** , wie im folgenden Beispiel gezeigt:

```cpp
template <typename T> struct Allocator {
    template <typename U> struct Rebind {
        typedef Allocator<U> Other;
    };
};

template <typename X, typename AY> struct Container {
    typedef typename AY::Rebind<X>::Other AX; // error C2059
};
```

Standardmäßig geht C++ davon aus, dass `AY::Rebind` keine Vorlage `<` ist. Daher wird Folgendes als Vorzeichen interpretiert.  Sie müssen dem Compiler explizit mitteilen, dass `Rebind` es sich um eine Vorlage handelt, sodass die Spitze Klammer ordnungsgemäß analysiert werden kann. Um diesen Fehler zu beheben, verwenden Sie das **`template`** Schlüsselwort für den Namen des abhängigen Typs, wie hier gezeigt:

```cpp
template <typename T> struct Allocator {
    template <typename U> struct Rebind {
        typedef Allocator<U> Other;
    };
};

template <typename X, typename AY> struct Container {
    typedef typename AY::template Rebind<X>::Other AX; // correct
};
```
