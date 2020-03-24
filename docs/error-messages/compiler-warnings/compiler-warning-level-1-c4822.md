---
title: Compilerwarnung (Stufe 1) C4822
ms.date: 11/04/2016
f1_keywords:
- C4822
helpviewer_keywords:
- C4822
ms.assetid: 0f231a30-2eb0-4722-aaa0-e2d19d3e7eea
ms.openlocfilehash: 59c42227c7e8be9bd31c37776d9724d23db61837
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80174868"
---
# <a name="compiler-warning-level-1-c4822"></a>Compilerwarnung (Stufe 1) C4822

"Member": Lokale Klassenmemberfunktion enthält keinen Text.

Eine lokale Klassenmemberfunktion wurde deklariert, aber nicht in der Klasse definiert. Um eine lokale Klassenmemberfunktion verwenden zu können, müssen Sie sie in der Klasse definieren. Sie können Sie nicht in der Klasse deklarieren und außerhalb der Klasse definieren.

Jede Definition außerhalb der Klasse für eine lokale Klassenmemberfunktion erzeugt einen Fehler.

Im folgenden Beispiel wird C4822 generiert.

```cpp
// C4822.cpp
// compile with: /W1
int main() {
   struct C {
      void func1(int);   // C4822
      // try the following line instead
      // void func1(int){}
  };
}
```
