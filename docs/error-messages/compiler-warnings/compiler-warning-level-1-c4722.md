---
title: Compilerwarnung (Stufe 1) C4722
ms.date: 11/04/2016
f1_keywords:
- C4722
helpviewer_keywords:
- C4722
ms.assetid: d8660710-f67b-4f59-a5fd-59259475529e
ms.openlocfilehash: 3fee3296eba4476680f4948b4a1f7fdee03e8840
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175206"
---
# <a name="compiler-warning-level-1-c4722"></a>Compilerwarnung (Stufe 1) C4722

„function“: Der Destruktor gibt nie Werte zurück, möglicherweise ist ein Speicherverlust aufgetreten.

Die Ablaufsteuerung wird mit einem Destruktor beendet. Der Thread oder das gesamte Programm wird beendet, und zugeordnete Ressourcen können möglicherweise nicht freigegeben werden.  Zudem ist das Verhalten der ausführbaren Datei nicht definiert, wenn ein Destruktor für die Stapelentladung während der Ausnahmeverarbeitung aufgerufen wird.

Zum Beheben dieses Fehlers entfernen Sie den Funktionsaufruf, der bewirkt, dass der Destruktor nicht zurückgegeben wird.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C4722 generiert.

```cpp
// C4722.cpp
// compile with: /O1 /W1 /c
#include <stdlib.h>
class C {
public:
   C();
   ~C() { exit(1); };   // C4722
};

extern void func (C*);

void Test(){
   C x;
   func(&x);
   // control will not leave Test because destructor will exit
}
```
