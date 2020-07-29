---
title: Compilerfehler C2723
ms.date: 11/04/2016
f1_keywords:
- C2723
helpviewer_keywords:
- C2723
ms.assetid: 86925601-2297-4cfd-94e2-2caf27c474c4
ms.openlocfilehash: f723fcc0a3d9626f01f2059a3d9363801221bca0
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216049"
---
# <a name="compiler-error-c2723"></a>Compilerfehler C2723

„Funktion“: Spezifizierer „Spezifizierer“ ist in Funktionsdefinition unzulässig.

Der Spezifizierer darf nicht mit einer Funktionsdefinition außerhalb einer Klassendeklaration vorkommen. Der **`virtual`** Spezifizierer kann nur für eine Element Funktionsdeklaration innerhalb einer Klassen Deklaration angegeben werden.

Im folgenden Beispiel wird C2723 generiert und gezeigt, wie Sie diesen Fehler beheben:

```cpp
// C2723.cpp
struct X {
   virtual void f();
   virtual void g();
};

virtual void X::f() {}   // C2723

// try the following line instead
void X::g() {}
```
