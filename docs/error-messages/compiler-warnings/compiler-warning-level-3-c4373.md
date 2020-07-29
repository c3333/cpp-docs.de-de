---
title: Compilerwarnung (Stufe 3) C4373
ms.date: 11/04/2016
f1_keywords:
- C4373
helpviewer_keywords:
- C4373
ms.assetid: 670c0ba3-b7d6-4aed-b207-1cb84da3bcde
ms.openlocfilehash: b3ab8a0c5d826aa44eee3fea53908091ef0c6803
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225318"
---
# <a name="compiler-warning-level-3-c4373"></a>Compilerwarnung (Stufe 3) C4373

> "*Funktion*": die virtuelle Funktion überschreibt "*Base_function*", frühere Versionen des Compilers wurden nicht überschrieben, wenn sich die Parameter nur durch Konstanten/volatile-Qualifizierer unterscheiden.

## <a name="remarks"></a>Bemerkungen

Die Anwendung enthält eine Methode in einer abgeleiteten Klasse, die eine virtuelle Methode in einer Basisklasse überschreibt, und die Parameter in der überschreibenden Methode unterscheiden sich nur durch einen [const](../../cpp/const-cpp.md) - oder [volatile](../../cpp/volatile-cpp.md) -Qualifizierer von den Parametern der virtuellen Methode. Dies bedeutet, dass der Compiler einen Funktionsverweis an die Methode in der Basisklasse oder abgeleiteten Klasse binden muss.

Compilerversionen vor Visual Studio 2008 binden die Funktion an die Methode in der Basisklasse und geben dann eine Warnmeldung aus. Nachfolgende Compilerversionen ignorieren den- **`const`** oder- **`volatile`** Qualifizierer, binden die Funktion an die Methode in der abgeleiteten Klasse und geben dann Warning **C4373**aus. Das zuletzt genannte Verhalten entspricht dem C++-Standard.

## <a name="example"></a>Beispiel

Im folgenden Codebeispiel wird die Warnung C4373 generiert: Um dieses Problem zu beheben, können Sie festlegen, dass die Überschreibung dieselben CV-Qualifizierer wie die Basismember-Funktion verwenden soll. Wenn Sie keine außer Kraft Setzung erstellen möchten, können Sie der Funktion in der abgeleiteten Klasse einen anderen Namen geben.

```cpp
// c4373.cpp
// compile with: /c /W3
#include <stdio.h>
struct Base
{
    virtual void f(int i) {
        printf("base\n");
    }
};

struct Derived : Base
{
    void f(const int i) {  // C4373
        printf("derived\n");
    }
};

int main()
{
    Derived d;
    Base* p = &d;
    p->f(1);
}
```

```Output
derived
```
