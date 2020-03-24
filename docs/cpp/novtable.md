---
title: novtable
ms.date: 11/04/2016
f1_keywords:
- novtable_cpp
helpviewer_keywords:
- novtable __declspec keyword
- __declspec keyword [C++], novtable
ms.assetid: cfef09c5-8c1e-4b14-8a72-7d726ded4484
ms.openlocfilehash: d101e73f2f8d476c50b1b80b8daa7994151d43af
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80177832"
---
# <a name="novtable"></a>novtable

**Microsoft-spezifisch**

Dies ist ein **__declspec** Erweitertes Attribut.

Diese Form von **__declspec** kann auf jede Klassen Deklaration angewendet werden, sollte jedoch nur auf reine Schnittstellen Klassen angewendet werden, d. h. auf Klassen, die nie selbst instanziiert werden. Der **__declspec** hindert den Compiler daran, Code zum Initialisieren des vfptr in den Konstruktoren und dem debugtor der-Klasse zu erstellen. In vielen Fällen werden hierdurch die einzigen Verweise auf "vtable" entfernt, die der Klasse zugeordnet sind, sodass der Linker diese entfernt. Die Verwendung dieser Form von **__declspec** kann zu einer erheblichen Verringerung der Codegröße führen.

Wenn Sie versuchen, eine mit " **novtable** " markierte Klasse zu instanziieren und dann auf einen Klassenmember zuzugreifen, erhalten Sie eine Zugriffsverletzung (Access Verletzung, AV).

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

## <a name="see-also"></a>Weitere Informationen

[__declspec](../cpp/declspec.md)<br/>
[Schlüsselwörter](../cpp/keywords-cpp.md)
