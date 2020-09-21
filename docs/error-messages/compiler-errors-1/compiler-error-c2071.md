---
title: Compilerfehler C2071
ms.date: 11/04/2016
f1_keywords:
- C2071
helpviewer_keywords:
- C2071
ms.assetid: f8c09255-a5c4-47e3-8089-3d875ae43cc5
ms.openlocfilehash: 7619d968379bfc35e98bd87071b75296d10c382c
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/17/2020
ms.locfileid: "90743281"
---
# <a name="compiler-error-c2071"></a>Compilerfehler C2071

'Bezeichner': Ungültige Speicherklasse

`identifier` wurde mit einer ungültigen [Speicher Klasse](../../c-language/c-storage-classes.md)deklariert. Dieser Fehler kann verursacht werden, wenn mehr als eine Speicherklasse für einen Bezeichner angegeben ist oder wenn die Definition mit der Speicherklassen-Deklaration nicht kompatibel ist.

Um dieses Problem zu beheben, verstehen Sie die beabsichtigte Speicher Klasse des Bezeichners – z. b. **`static`** oder **`extern`** –, und korrigieren Sie die Deklaration entsprechend.

## <a name="examples"></a>Beispiele

Im folgenden Beispiel wird C2071 generiert.

```cpp
// C2071.cpp
// compile with: /c
struct C {
   extern int i;   // C2071
};
struct D {
   int i;   // OK, no extern on an automatic
};
```

Im folgenden Beispiel wird C2071 generiert.

```cpp
// C2071_b.cpp
// compile with: /c
typedef int x(int i) { return i; }   // C2071
typedef int (x)(int);   // OK, no local definition in typedef
```
