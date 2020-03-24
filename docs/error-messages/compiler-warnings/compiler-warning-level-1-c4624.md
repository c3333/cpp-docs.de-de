---
title: Compilerwarnung (Stufe 1) C4624
ms.date: 11/04/2016
f1_keywords:
- C4624
helpviewer_keywords:
- C4624
ms.assetid: 14f61769-d92e-482b-9515-debd87b30a66
ms.openlocfilehash: 5d6e89efb042b8f757feec3911b160961e51f72a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80199692"
---
# <a name="compiler-warning-level-1-c4624"></a>Compilerwarnung (Stufe 1) C4624

'derived class': Der Destruktor wurde impliziert als gelöscht definiert, da ein Basisklassen-Destruktor nicht zugreifbar ist oder gelöscht wurde.

Ein Destruktor stand nicht für den Zugriff zur Verfügung oder wurde in einer Basisklasse gelöscht. Daher wurde er nicht für eine abgeleitete Klasse generiert. Jeder Versuch, ein Objekt dieses Typs auf dem Stapel zu erstellen, verursacht einen Compilerfehler.

Im folgenden Beispiel wird C4624 generiert und gezeigt, wie Sie diesen Fehler beheben:

```cpp
// C4624.cpp
// compile with: /W1 /c
class B {
// Uncomment the following line to fix.
// public:
   ~B();
};

class D : public B {};   // C4624 B's destructor not public
```
