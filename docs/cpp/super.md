---
title: __super
ms.date: 11/04/2016
f1_keywords:
- __super_cpp
helpviewer_keywords:
- __super keyword [C++]
ms.assetid: f0957c31-9256-405b-b402-cad182404b5f
ms.openlocfilehash: 3afc2e8049cfcca40db389bed84baa6f42dae126
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213150"
---
# `__super`

**Microsoft-spezifisch**

Ermöglicht es Ihnen, explizit anzugeben, dass Sie eine Basisklassenimplementierung für eine Funktion aufrufen, die Sie überschreiben.

## <a name="syntax"></a>Syntax

```
__super::member_function();
```

## <a name="remarks"></a>Bemerkungen

Alle verfügbaren Basisklassenmethoden werden während der Überladungsauflösungsphase berücksichtigt, und die Funktion, die die beste Übereinstimmung bereitstellt, ist die, die aufgerufen wird.

**`__super`** kann nur im Text einer Member-Funktion angezeigt werden.

**`__super`** kann nicht mit einer using-Deklaration verwendet werden. Weitere Informationen finden [Sie unter using-Deklaration](../cpp/using-declaration.md) .

Mit der Einführung von [Attributen](../windows/attributes/attributes-alphabetical-reference.md) , die Code einfügen, kann Ihr Code eine oder mehrere Basisklassen enthalten, deren Namen Sie möglicherweise nicht kennen, aber die Methoden enthalten, die Sie aufzurufen möchten.

## <a name="example"></a>Beispiel

```cpp
// deriv_super.cpp
// compile with: /c
struct B1 {
   void mf(int) {}
};

struct B2 {
   void mf(short) {}

   void mf(char) {}
};

struct D : B1, B2 {
   void mf(short) {
      __super::mf(1);   // Calls B1::mf(int)
      __super::mf('s');   // Calls B2::mf(char)
   }
};
```

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Siehe auch

[Schlüsselwörter](../cpp/keywords-cpp.md)
