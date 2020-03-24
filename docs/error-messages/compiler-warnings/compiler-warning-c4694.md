---
title: Compilerwarnung C4694
ms.date: 10/25/2017
f1_keywords:
- C4694
helpviewer_keywords:
- C4694
ms.assetid: 5ca122bb-34f3-43ee-a21f-95802cd515f7
ms.openlocfilehash: daf5423588d08260239c3cff5a68532a358d07b2
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80165118"
---
# <a name="compiler-warning-c4694"></a>Compilerwarnung C4694

> '*Class*': eine versiegelte abstrakte Klasse kann keine Basisklasse '*BASE_CLASS*' aufweisen.

Eine abstrakte und versiegelte Klasse kann nicht von einem Referenztyp erben; eine versiegelte und abstrakte Klasse kann weder die Basisklassenfunktionen implementieren noch ihre eigene Verwendung als Basisklasse zulassen.

Weitere Informationen finden Sie unter [abstrakte](../../extensions/abstract-cpp-component-extensions.md), [versiegelte](../../extensions/sealed-cpp-component-extensions.md)und [Klassen und Strukturen](../../extensions/classes-and-structs-cpp-component-extensions.md).

Diese Warnung wird automatisch zu einem Fehler heraufgestuft. Wenn Sie dieses Verhalten ändern möchten, verwenden Sie [#pragma Warnung](../../preprocessor/warning.md).

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C4694 generiert:

```cpp
// C4694.cpp
// compile with: /c /clr
ref struct A {};
ref struct B sealed abstract : A {};   // C4694
```
