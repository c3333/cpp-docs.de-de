---
title: Compilerwarnung (Stufe 1) C4530
ms.date: 11/04/2016
f1_keywords:
- C4530
helpviewer_keywords:
- C4530
ms.assetid: a04dcdb2-84db-459d-9e5e-4e743887465f
ms.openlocfilehash: 69ca60e2cba338bf1bd1ac3470e583739e72a68e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80186451"
---
# <a name="compiler-warning-level-1-c4530"></a>Compilerwarnung (Stufe 1) C4530

C++der Ausnahmehandler wird verwendet, aber die Entlade Semantik ist nicht aktiviert. /EHsc angeben

C++Ausnahmebehandlung wurde verwendet, aber [/EHsc](../../build/reference/eh-exception-handling-model.md) wurde nicht ausgewählt.

Wenn die/EHsc-Option nicht aktiviert wurde, wird ein Objekt mit automatischem Speicher im Frame zwischen der Funktion, die den Throw auslöst, und der Funktion, die den Throw abfängt, nicht zerstört. Ein Objekt mit automatischem Speicher, das in einem **try** -oder **catch** -Block erstellt wurde, wird jedoch zerstört.

Im folgenden Beispiel wird C4530 generiert:

```cpp
// C4530.cpp
// compile with: /W1
int main() {
   try{} catch(int*) {}   // C4530
}
```

Kompilieren Sie das Beispiel mit/EHsc, um die Warnung zu beheben.
