---
title: Compilerwarnung (Stufe 2) C4396
ms.date: 11/04/2016
f1_keywords:
- C4396
helpviewer_keywords:
- C4396
ms.assetid: 7cd6b283-db17-4574-b299-03e0b913ad70
ms.openlocfilehash: fec6875fdb2e8a60e71fe08da1ed4e8fa82e4641
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87206041"
---
# <a name="compiler-warning-level-2-c4396"></a>Compilerwarnung (Stufe 2) C4396

"Name": Der Inlinespezifizierer kann nicht verwendet werden, wenn eine Friend-Deklaration auf die Spezialisierung einer Funktionsvorlage verweist.

Für die Spezialisierung einer Funktionsvorlage kann kein [Inline](../../cpp/inline-functions-cpp.md) -Spezifizierer angegeben werden. Der Compiler gibt die Warnung C4396 aus und ignoriert den Inlinespezifizierer.

### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler

- Entfernen Sie den-,-oder-Bezeichner **`inline`** **`__inline`** **`__forceinline`** aus der Deklaration der Friend-Funktion.

## <a name="example"></a>Beispiel

Das folgende Codebeispiel zeigt eine ungültige Friend-Funktionsdeklaration mit einem- **`inline`** Spezifizierer.

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
