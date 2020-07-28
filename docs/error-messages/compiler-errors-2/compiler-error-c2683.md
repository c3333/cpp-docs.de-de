---
title: Compilerfehler C2683
ms.date: 11/04/2016
f1_keywords:
- C2683
helpviewer_keywords:
- C2683
ms.assetid: db605e4f-601b-4d05-92a1-c43ca24de08d
ms.openlocfilehash: cd629b093bdc3992a8ea69f498b1e1cdab1b8826
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214632"
---
# <a name="compiler-error-c2683"></a>Compilerfehler C2683

' Cast ': ' type ' ist kein polymorpher Typ.

Sie können [dynamic_cast](../../cpp/dynamic-cast-operator.md) nicht verwenden, um eine nicht-polymorphe Klasse (eine Klasse ohne virtuelle Funktionen) zu konvertieren.

Sie können [static_cast](../../cpp/static-cast-operator.md) verwenden, um Konvertierungen von nicht polymorphen Typen auszuführen. Führt jedoch **`static_cast`** keine Lauf Zeit Überprüfung aus.

Im folgenden Beispiel wird C2683 generiert:

```cpp
// C2683.cpp
// compile with: /c
class B { };
class D : public B { };

void f(B* pb) {
   D* pd1 = dynamic_cast<D*>(pb);  // C2683
   D* pd1 = static_cast<D*>(pb);   // OK
}
```
