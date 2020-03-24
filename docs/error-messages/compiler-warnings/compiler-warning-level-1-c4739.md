---
title: Compilerwarnung (Stufe 1) C4739
ms.date: 11/04/2016
f1_keywords:
- C4739
helpviewer_keywords:
- C4739
ms.assetid: 600873b3-7c85-4cd4-944e-cd8e01bfcbb0
ms.openlocfilehash: 9c68a9e0a2873de7e919fafbef68835f0970c03b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80185697"
---
# <a name="compiler-warning-level-1-c4739"></a>Compilerwarnung (Stufe 1) C4739

Für den Verweis auf die Variable 'var' ist nicht genügend Speicherplatz vorhanden.

Ein Wert wurde einer Variablen zugewiesen, aber der Wert ist größer als die Größe der Variablen. Der Arbeitsspeicher wird über den Speicherbereich der Variablen hinaus beschrieben, wodurch ein Datenverlust möglich ist.

Weisen Sie einen Wert nur einer Variablen zu, deren Größe den Wert aufnehmen kann, um diese Warnung zu vermeiden.

Im folgenden Beispiel wird C4739 generiert.

```cpp
// C4739.cpp
// compile with: /RTCs /Zi /W1 /c
char *pc;
int main() {
   char c;
   *(int *)&c = 1;   // C4739

   // OK
   *(char *)&c = 1;
}
```
