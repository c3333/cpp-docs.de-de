---
title: Compilerfehler C2248
ms.date: 11/04/2016
f1_keywords:
- C2248
helpviewer_keywords:
- C2248
ms.assetid: 7a3ba0e8-d3b9-4bb9-95db-81ef17e31d23
ms.openlocfilehash: d35ded4b06423be53911f3efd0b55d75cb979773
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212812"
---
# <a name="compiler-error-c2248"></a>Compilerfehler C2248

"*Member*": auf das in der*Klasse "Class"* deklarierte Element "*access_level*" kann nicht zugegriffen werden.

Member einer abgeleiteten Klasse können nicht **`private`** auf Member einer Basisklasse zugreifen. Sie können nicht **`private`** auf-oder-Member **`protected`** von Klassen Instanzen zugreifen.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C2248 generiert, wenn von außerhalb der-Klasse auf private oder geschützte Member einer-Klasse zugegriffen wird. Um dieses Problem zu beheben, können Sie nicht direkt außerhalb der Klasse auf diese Member zugreifen. Verwenden Sie öffentliche Elementdaten und Element Funktionen für die Interaktion mit der-Klasse.

```cpp
// C2248_access.cpp
// compile with: cl /EHsc /W4 C2248_access.cpp
#include <stdio.h>

class X {
public:
    int  m_publicMember;
    void setPrivateMember( int i ) {
        m_privateMember = i;
        printf_s("\n%d", m_privateMember);
    }
protected:
    int  m_protectedMember;

private:
    int  m_privateMember;
} x;

int main() {
    x.m_publicMember = 4;
    printf_s("\n%d", x.m_publicMember);
    x.m_protectedMember = 2; // C2248 m_protectedMember is protected
    x.m_privateMember = 3;   // C2248  m_privMemb is private
    x.setPrivateMember(0);   // OK uses public access function
}
```

Ein weiteres Konformitäts Problem, das C2248 verfügbar macht, ist die Verwendung von Vorlagen-Freunden und Spezialisierung. Um dieses Problem zu beheben, deklarieren Sie Friend-Vorlagen Funktionen, indem Sie entweder eine leere Vorlagen Parameterliste <> oder bestimmte Vorlagen Parameter verwenden.

```cpp
// C2248_template.cpp
// compile with: cl /EHsc /W4 C2248_template.cpp
template<class T>
void f(T t) {
    t.i;   // C2248
}

struct S {
private:
    int i;

public:
    S() {}
    friend void f(S);   // refer to the non-template function void f(S)
    // To fix, comment out the previous line and
    // uncomment the following line.
    // friend void f<S>(S);
};

int main() {
    S s;
    f<S>(s);
}
```

Ein anderes Konformitäts Problem, das C2248 verfügbar macht, ist, wenn Sie versuchen, einen Freund einer Klasse zu deklarieren, und wenn die Klasse für die Friend-Deklaration im Gültigkeitsbereich der Klasse nicht sichtbar ist. Um dieses Problem zu beheben, gewähren Sie der einschließenden Klasse eine Freundschaft.

```cpp
// C2248_enclose.cpp
// compile with: cl /W4 /c C2248_enclose.cpp
class T {
    class S {
        class E {};
    };
    friend class S::E;   // C2248
};

class A {
    class S {
        class E {};
        friend class A;  // grant friendship to enclosing class
    };
    friend class S::E;   // OK
};
```
