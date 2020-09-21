---
title: Compilerfehler C2666
ms.date: 11/04/2016
f1_keywords:
- C2666
helpviewer_keywords:
- C2666
ms.assetid: 78364d15-c6eb-439a-9088-e04a0176692b
ms.openlocfilehash: ebe41a4c4aa090e609d3352635d4e1fc06e22454
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/17/2020
ms.locfileid: "90743216"
---
# <a name="compiler-error-c2666"></a>Compilerfehler C2666

"Bezeichner": Zahl Überladungen haben ähnliche Konvertierungen

Eine überladene Funktion oder Operator ist mehrdeutig.   Formale Parameterlisten können für den Compiler zu ähnlich sein, um die Mehrdeutigkeit aufzulösen.  Um diesen Fehler zu beheben, müssen Sie einen oder mehrere der eigentlichen Parameter explizit umwandeln.

## <a name="examples"></a>Beispiele

Im folgenden Beispiel wird C2666 generiert:

```cpp
// C2666.cpp
struct complex {
   complex(double);
};

void h(int,complex);
void h(double, double);

int main() {
   h(3,4);   // C2666
}
```

Dieser Fehler kann auch infolge einer compilerübereinstimmungs-Arbeit generiert werden, die für Visual Studio .NET 2003 ausgeführt wurde:

- binäre Operatoren und benutzerdefinierte Konvertierungen in Zeiger Typen

- die Qualifikations Konvertierung ist nicht mit der Identitäts Konvertierung identisch.

Für die binären Operatoren \<, > \<=, and > = wird ein übergebener Parameter jetzt implizit in den Typ des Operanden konvertiert, wenn der Typ des Parameters einen benutzerdefinierten Konvertierungs Operator für die Konvertierung in den Typ des Operanden definiert. Es gibt jetzt potenzielle Mehrdeutigkeit.

Für Code, der sowohl in der Visual Studio .NET 2003-als auch in der Visual Studio .NET-Version von Visual C++ gültig ist, wird der-Klassen Operator explizit mithilfe der Funktions Syntax aufgerufen.

```cpp
// C2666b.cpp
#include <string.h>
#include <stdio.h>

struct T
{
    T( const T& copy )
    {
        m_str = copy.m_str;
    }

    T( const char* str )
    {
        int iSize = (strlen( str )+ 1);
        m_str = new char[ iSize ];
        if (m_str)
            strcpy_s( m_str, iSize, str );
    }

    bool operator<( const T& RHS )
    {
        return m_str < RHS.m_str;
    }

    operator char*() const
    {
        return m_str;
    }

    char* m_str;
};

int main()
{
    T str1( "ABCD" );
    const char* str2 = "DEFG";

    // Error - Ambiguous call to operator<()
    // Trying to convert str1 to char* and then call
    // operator<( const char*, const char* )?
    //  OR
    // trying to convert str2 to T and then call
    // T::operator<( const T& )?

    if( str1 < str2 )   // C2666

    if ( str1.operator < ( str2 ) )   // Treat str2 as type T
        printf_s("str1.operator < ( str2 )\n");

    if ( str1.operator char*() < str2 )   // Treat str1 as type char*
        printf_s("str1.operator char*() < str2\n");
}
```

Im folgenden Beispiel wird C2666 generiert.

```cpp
// C2666c.cpp
// compile with: /c

enum E
{
    E_A,   E_B
};

class A
{
    int h(const E e) const {return 0; }
    int h(const int i) { return 1; }
    // Uncomment the following line to resolve.
    // int h(const E e) { return 0; }

    void Test()
    {
        h(E_A);   // C2666
        h((const int) E_A);
        h((int) E_A);
    }
};
```
