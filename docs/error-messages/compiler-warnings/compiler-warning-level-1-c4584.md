---
title: Compilerwarnung (Stufe 1) C4584
ms.date: 11/04/2016
f1_keywords:
- C4584
helpviewer_keywords:
- C4584
ms.assetid: ad86582f-cb8c-4d21-8c4c-a6c800059e25
ms.openlocfilehash: fa736e8dbab775fcd6cdffc467aee1312004fa60
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80162152"
---
# <a name="compiler-warning-level-1-c4584"></a>Compilerwarnung (Stufe 1) C4584

"Class1": die Basisklasse "Klasse2" ist bereits eine Basisklasse von "class3".

Die Klasse, die Sie definiert haben, erbt von zwei Klassen, von denen eine von der anderen erbt. Beispiel:

```cpp
// C4584.cpp
// compile with: /W1 /LD
class A {
};

class B : public A {
};

class C : public A, public B { // C4584
};
```

In diesem Fall würde eine Warnung für die Klasse C ausgegeben, weil Sie sowohl von Klasse a als auch von Klasse B erbt, die auch von Klasse a erbt. Diese Warnung dient als Erinnerung daran, dass Sie die Verwendung von Membern aus diesen Basisklassen vollständig qualifizieren müssen. oder es wird ein Compilerfehler generiert, weil die Mehrdeutigkeit, auf die Sie verweisen, liegt.
