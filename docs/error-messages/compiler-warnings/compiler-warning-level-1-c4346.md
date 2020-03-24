---
title: Compilerwarnung (Stufe 1) C4346
ms.date: 11/04/2016
f1_keywords:
- C4346
helpviewer_keywords:
- C4346
ms.assetid: 68ee562d-cca9-4a2a-9a1b-14ad1a1e7396
ms.openlocfilehash: 3ab519f612d5272b0562728917cc777f1de86b79
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187244"
---
# <a name="compiler-warning-level-1-c4346"></a>Compilerwarnung (Stufe 1) C4346

"Name": der abhängige Name ist kein Typ.

Das Schlüsselwort [tykame](../../cpp/typename.md) ist erforderlich, wenn ein abhängiger Name als Typ behandelt werden soll. Fügen Sie für Code, der in allen Versionen von Visual C++identisch funktioniert, `typename` der Deklaration hinzu.

Im folgenden Beispiel wird C4346 generiert:

```cpp
// C4346.cpp
// compile with: /WX /LD
template<class T>
struct C {
   T::X* x;   // C4346
   // try the following line instead
   // typename T::X* x;
};
```

Die folgenden Beispiele zeigen weitere Beispiele, in denen das Schlüsselwort **tyschlame** erforderlich ist:

```cpp
// C4346b.cpp
// compile with: /LD /W1
template<class T>
const typename T::X& f(typename T::Z* p);   // Required in both places

template<class T, int N>
struct L{};

template<class T>
struct M : public L<typename T::Type, T::Value>
{   // required on type argument, not on non-type argument
   typedef typename T::X   Type;
   Type f();   // OK: "Type" is a type-specifer
   typename T::X g();   // typename required
   operator typename T::Z();   // typename required
};
```

und dies,

```cpp
// C4346c.cpp
// compile with: /LD /WX
struct Y {
   typedef int Y_t;
};

template<class T>
struct A {
   typedef Y A_t;
};

template<class T>
struct B {
   typedef /*typename*/ A<T>::A_t B_t;   // C4346 typename needed here
   typedef /*typename*/ B_t::Y_t  B_t2;   // typename also needed here
};
```
