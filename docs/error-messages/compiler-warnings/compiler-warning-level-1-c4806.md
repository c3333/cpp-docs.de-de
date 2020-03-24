---
title: Compilerwarnung (Stufe 1) C4806
ms.date: 11/04/2016
f1_keywords:
- C4806
helpviewer_keywords:
- C4806
ms.assetid: 79eb74cd-b925-4b5b-84e1-8ae6f33e38b3
ms.openlocfilehash: 5895e9bf489e240b1eff6f1499b711047ea74b9b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175050"
---
# <a name="compiler-warning-level-1-c4806"></a>Compilerwarnung (Stufe 1) C4806

"operation": unsichere Operation: kein Wert vom Typ "type" erweitert auf Typ "type" kann mit der angegebenen Konstante übereinstimmen

Diese Meldung warnt Sie vor Code wie `b == 3`, wobei `b` Typ `bool`aufweist. Aufgrund der Erweiterungsregeln wird `bool` auf `int`erweitert. Dies ist zulässig, es kann aber nie **true**sein. Im folgenden Beispiel wird C4806 generiert:

```cpp
// C4806.cpp
// compile with: /W1
int main()
{
   bool b = true;
   // try..
   // int b = true;

   if (b == 3)   // C4806
   {
      b = false;
   }
}
```
