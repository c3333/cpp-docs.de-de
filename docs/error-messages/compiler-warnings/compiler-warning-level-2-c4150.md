---
title: Compilerwarnung (Stufe 2) C4150
ms.date: 11/04/2016
f1_keywords:
- C4150
helpviewer_keywords:
- C4150
ms.assetid: ff1760ec-0d9f-4d45-b797-94261624becf
ms.openlocfilehash: a3993d2b993205c98de968ca893f24f703b3b635
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218142"
---
# <a name="compiler-warning-level-2-c4150"></a>Compilerwarnung (Stufe 2) C4150

Löschen eines Zeigers auf den unvollständigen Typ "Typ"; kein Dekonstruktor aufgerufen

Der- **`delete`** Operator wird aufgerufen, um einen Typ zu löschen, der deklariert, aber nicht definiert wurde, sodass der Compiler einen Dekonstruktor nicht finden kann.

Im folgenden Beispiel wird C4150 generiert:

```cpp
// C4150.cpp
// compile with: /W2
class  IncClass;

void NoDestruct( IncClass* pIncClass )
{
   delete pIncClass;
} // C4150, define class to resolve

int main()
{
}
```
