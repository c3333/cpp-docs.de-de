---
title: Compilerwarnung (Stufe 1) C4269
ms.date: 11/04/2016
f1_keywords:
- C4269
helpviewer_keywords:
- C4269
ms.assetid: 96c97bbc-068a-4b65-8cd8-4ed5dca04c15
ms.openlocfilehash: e2e1781bf4c1b9ac0ee29d0b5900daa6cfe94b45
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80199770"
---
# <a name="compiler-warning-level-1-c4269"></a>Compilerwarnung (Stufe 1) C4269

"Bezeichner": "Konstante" automatische Daten, die mit dem vom Compiler generierten Standardkonstruktor initialisiert werden, erzeugen unzuverlässige Ergebnisse

Eine **Konstante automatische Instanz einer nicht** trivialen Klasse wird mit einem vom Compiler generierten Standardkonstruktor initialisiert.

## <a name="example"></a>Beispiel

```cpp
// C4269.cpp
// compile with: /c /LD /W1
class X {
public:
   int m_data;
};

void g() {
   const X x1;   // C4269
};
```

Da diese Instanz der-Klasse auf dem Stapel generiert wird, kann der Anfangswert von `m_data` beliebiger Wert sein. Da es sich **um eine Konstante** Instanz handelt, kann der Wert von `m_data` nie geändert werden.
