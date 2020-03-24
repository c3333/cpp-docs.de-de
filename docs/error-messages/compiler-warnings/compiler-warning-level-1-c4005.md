---
title: Compilerwarnung (Stufe 1) C4005
ms.date: 11/04/2016
f1_keywords:
- C4005
helpviewer_keywords:
- C4005
ms.assetid: 7f2dc79a-9fcb-4d5b-be61-120d9cb487ad
ms.openlocfilehash: 4e95f8deeb61c5a4d56e0643beb6a746f848e33e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80164728"
---
# <a name="compiler-warning-level-1-c4005"></a>Compilerwarnung (Stufe 1) C4005

"Bezeichner": Makro Neudefinition

Der Makro Bezeichner wird zweimal definiert. Der Compiler verwendet die zweite Makro Definition.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Dieser Fehler kann eine der folgenden Ursachen haben:

1. Definieren eines Makros in der Befehlszeile und im Code mit einer `#define`-Direktive.

1. Makros, die aus Includedateien importiert wurden.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>So beheben Sie den Fehler (unterschiedliche Lösungsmöglichkeiten)

1. Entfernen Sie eine der Definitionen.

1. Verwenden Sie eine [#undef](../../preprocessor/hash-undef-directive-c-cpp.md) -Direktive vor der zweiten Definition.

Im folgenden Beispiel wird C4005 generiert:

```cpp
// C4005.cpp
// compile with: /W1 /EHsc
#include <iostream>
using namespace std;

#define TEST "test1"
#define TEST "test2"   // C4005 delete or rename to resolve the warning

int main() {
   cout << TEST << endl;
}
```
