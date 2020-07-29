---
title: novtable
ms.date: 11/04/2016
f1_keywords:
- novtable_cpp
helpviewer_keywords:
- novtable __declspec keyword
- __declspec keyword [C++], novtable
ms.assetid: cfef09c5-8c1e-4b14-8a72-7d726ded4484
ms.openlocfilehash: ccf544608bcba83af17702767562ef93d775b5a9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227256"
---
# <a name="novtable"></a>novtable

**Microsoft-spezifisch**

Dies ist ein **`__declspec`** Erweitertes Attribut.

Diese Form von **`__declspec`** kann auf jede Klassen Deklaration angewendet werden, sollte jedoch nur auf reine Schnittstellen Klassen angewendet werden, d. h. auf Klassen, die nie selbst instanziiert werden. Der **`__declspec`** verhindert, dass der Compiler Code zum Initialisieren des vfptr in den Konstruktoren und debuggingklassen der Klasse erzeugt. In vielen Fällen werden hierdurch die einzigen Verweise auf "vtable" entfernt, die der Klasse zugeordnet sind, sodass der Linker diese entfernt. Die Verwendung dieser Form von **`__declspec`** kann zu einer erheblichen Verringerung der Codegröße führen.

Wenn Sie versuchen, eine mit markierte Klasse zu instanziieren **`novtable`** und dann auf einen Klassenmember zuzugreifen, erhalten Sie eine Zugriffsverletzung (Access Verletzung, AV).

## <a name="example"></a>Beispiel

```cpp
// novtable.cpp
#include <stdio.h>

struct __declspec(novtable) X {
   virtual void mf();
};

struct Y : public X {
   void mf() {
      printf_s("In Y\n");
   }
};

int main() {
   // X *pX = new X();
   // pX->mf();   // Causes a runtime access violation.

   Y *pY = new Y();
   pY->mf();
}
```

```Output
In Y
```

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Siehe auch

[`__declspec`](../cpp/declspec.md)<br/>
[Schlüsselwörter](../cpp/keywords-cpp.md)
