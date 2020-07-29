---
title: Compilerfehler C2786
ms.date: 11/04/2016
f1_keywords:
- C2786
helpviewer_keywords:
- C2786
ms.assetid: 6676d8c0-86dd-4a39-bdda-b75a35f4d137
ms.openlocfilehash: 60e921c17cd2b3f9462df77094162bb3f1eff379
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87206678"
---
# <a name="compiler-error-c2786"></a>Compilerfehler C2786

"Type": Ungültiger Operand für __uuidof

Der [__uuidof](../../cpp/uuidof-operator.md) -Operator nimmt einen benutzerdefinierten Typ mit einer angefügten GUID oder einem Objekt eines solchen benutzerdefinierten Typs an.  Mögliche Ursachen:

1. Das-Argument ist kein benutzerdefinierter Typ.

1. **`__uuidof`** die GUID kann nicht aus dem Argument extrahiert werden.

Im folgenden Beispiel wird C2786 generiert:

```cpp
// C2786.cpp
struct __declspec(uuid("00000000-0000-0000-0000-000000000000")) A {};

int main() {
   __uuidof(int);   // C2786
   __uuidof(int *);   // C2786
   __uuidof(A **);   // C2786

   // no error
   __uuidof(A);
   __uuidof(A *);
   __uuidof(A &);
   __uuidof(A[]);

   int i;
   int *pi;
   A **ppa;

   __uuidof(i);      // C2786
   __uuidof(pi);     // C2786
   __uuidof(ppa);    // C2786
}
```
