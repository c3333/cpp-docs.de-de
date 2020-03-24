---
title: Compilerwarnung (Stufe 1) C4353
ms.date: 11/04/2016
f1_keywords:
- C4353
helpviewer_keywords:
- C4353
ms.assetid: 6e79f186-ed82-4c95-9923-0ad5bb9c4db1
ms.openlocfilehash: 9c91a3d21a16cc8891d6f04db49c3a0f0ec26e2c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187192"
---
# <a name="compiler-warning-level-1-c4353"></a>Compilerwarnung (Stufe 1) C4353

nicht dem Standard entsprechende Erweiterung: Konstante 0 als Funktions Ausdruck. Verwenden Sie stattdessen die systeminterne Funktion "__noop".

Die Konstante 0 (null) kann nicht als Funktions Ausdruck verwendet werden. Weitere Informationen finden Sie unter [__noop](../../intrinsics/noop.md).

Im folgenden Beispiel wird C4353 generiert:

```cpp
// C4353.cpp
// compile with: /W1
void MyPrintf(void){};
#define X 0
#if X
   #define DBPRINT MyPrint
#else
   #define DBPRINT 0   // C4353 expected
#endif
int main(){
DBPRINT();
}
```
