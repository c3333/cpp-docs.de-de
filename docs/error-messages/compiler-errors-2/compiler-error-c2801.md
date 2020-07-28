---
title: Compilerfehler C2801
ms.date: 11/04/2016
f1_keywords:
- C2801
helpviewer_keywords:
- C2801
ms.assetid: 35dfc7ea-9e37-4e30-baa1-944dc61302f5
ms.openlocfilehash: cfb89c79534318ab1fbcaa06667d594bfe2f1157
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214593"
---
# <a name="compiler-error-c2801"></a>Compilerfehler C2801

"Operator Operator" muss ein nicht statischer Member sein.

Die folgenden Operatoren können nur als nicht statische Member überladen werden:

- Tätigkeit`=`

- Zugriff auf Klassenmember`->`

- Feld Indizierung`[]`

- Funktionsaufrufe`()`

Mögliche C2801 Ursachen:

- Der überladene Operator ist kein Klassen-, Struktur-oder Union-Member.

- Der überladene Operator ist deklariert **`static`** .

- Im folgenden Beispiel wird C2801 generiert:

```cpp
// C2801.cpp
// compile with: /c
operator[]();   // C2801 not a member
class A {
   static operator->();   // C2801 static
   operator()();   // OK
};
```
