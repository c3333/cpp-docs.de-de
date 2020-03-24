---
title: Compilerwarnung (Stufe 2) C4396
ms.date: 11/04/2016
f1_keywords:
- C4396
helpviewer_keywords:
- C4396
ms.assetid: 7cd6b283-db17-4574-b299-03e0b913ad70
ms.openlocfilehash: f37fcc7ece09bb9028a522ec6baf85d0e0e585c2
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80161814"
---
# <a name="compiler-warning-level-2-c4396"></a>Compilerwarnung (Stufe 2) C4396

"Name": Der Inlinespezifizierer kann nicht verwendet werden, wenn eine Friend-Deklaration auf die Spezialisierung einer Funktionsvorlage verweist.

Für die Spezialisierung einer Funktionsvorlage kann kein [Inline](../../cpp/inline-functions-cpp.md) -Spezifizierer angegeben werden. Der Compiler gibt die Warnung C4396 aus und ignoriert den Inlinespezifizierer.

### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler

- Entfernen Sie den `inline`-, `__inline`- oder `__forceinline` -Spezifizierer aus der Deklaration der Friend-Funktion.

## <a name="example"></a>Beispiel

Das folgende Codebeispiel enthält eine ungültige Friend-Funktionsdeklaration mit einem `inline` -Spezifizierer.

```cpp
// C4396.cpp
// compile with: /W2 /c

class X;
template<class T> void Func(T t, int i);

class X {
    friend inline void Func<char>(char t, int i);  //C4396
// try the following line instead
//    friend void Func<char>(char t, int i);
    int i;
};
```
