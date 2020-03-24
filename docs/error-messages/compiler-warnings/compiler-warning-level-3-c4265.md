---
title: Compilerwarnung (Stufe 3) C4265
ms.date: 11/04/2016
f1_keywords:
- C4265
helpviewer_keywords:
- C4265
ms.assetid: 20547159-6f30-4cc4-83aa-927884c8bb4c
ms.openlocfilehash: cfcbd9d9268785b87e45a833b332c276eec01522
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80161541"
---
# <a name="compiler-warning-level-3-c4265"></a>Compilerwarnung (Stufe 3) C4265

"Class": die Klasse besitzt virtuelle Funktionen, aber der debugtor ist nicht virtuell.

Wenn eine Klasse über virtuelle Funktionen, aber einen nicht virtuellen debugtor verfügt, werden Objekte des Typs möglicherweise nicht ordnungsgemäß zerstört, wenn die Klasse über einen Basisklassen Zeiger zerstört wird.

Diese Warnung ist standardmäßig deaktiviert. Weitere Informationen finden Sie unter [Standardmäßig deaktivierte Compilerwarnungen](../../preprocessor/compiler-warnings-that-are-off-by-default.md) .

Im folgenden Beispiel wird C4265 generiert:

```cpp
// C4265.cpp
// compile with: /W3 /c
#pragma warning(default : 4265)
class B
{
public:
   virtual void vmf();

   ~B();
   // try the following line instead
   // virtual ~B();
};   // C4265

int main()
{
   B b;
}
```
