---
title: Compilerfehler C2036
ms.date: 11/04/2016
f1_keywords:
- C2036
helpviewer_keywords:
- C2036
ms.assetid: 895821a9-65d1-44b5-bde1-dae827f3e486
ms.openlocfilehash: 06d292224108434065dfdca2a75d38fd3bb0243c
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/17/2020
ms.locfileid: "90742696"
---
# <a name="compiler-error-c2036"></a>Compilerfehler C2036

' Identifier ': unbekannte Größe

Ein Vorgang für `identifier` erfordert die Größe des Datenobjekts, das nicht ermittelt werden kann.

## <a name="examples"></a>Beispiele

Im folgenden Beispiel wird C2036 generiert.

```c
// C2036.c
// a C program
struct A* pA;
struct B { int i; } *pB;
int main() {
   pA++;   // C2036, size of A not known
   ((char*)pA)++;   // OK

   pB++;   // OK
}
```

Im folgenden Beispiel wird C2036 generiert.

```cpp
// C2036_2.cpp
// a C++ program
struct A* pA;
int main() {
   pA++;   // C2036, size of A not known
   ((char*&)pA)++;   // OK, if sizeof(A) == sizeof(char)
}
```
