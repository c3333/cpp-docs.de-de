---
title: Compilerfehler C2753
ms.date: 11/04/2016
f1_keywords:
- C2753
helpviewer_keywords:
- C2753
ms.assetid: 92bfeeac-524a-4a8e-9a4f-fb8269055826
ms.openlocfilehash: ea2901c998ac1a44ad142779e7ce48bfffff66c2
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80202150"
---
# <a name="compiler-error-c2753"></a>Compilerfehler C2753

"*Template*": partielle Spezialisierung kann nicht mit der Argumentliste für die primäre Vorlage verglichen werden

Wenn die Vorlagen Argumentliste mit der Parameterliste übereinstimmt, wird Sie vom Compiler als dieselbe Vorlage behandelt. Das doppelte definieren derselben Vorlage ist nicht zulässig.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C2753 generiert und eine Möglichkeit gezeigt, Sie zu beheben:

```cpp
// C2753.cpp
// compile with: cl /c C2753.cpp
template<class T>
struct A {};

template<class T>
struct A<T> {};   // C2753
// try the following line instead
// struct A<int> {};

template<class T, class U, class V, class W, class X>
struct B {};
```
