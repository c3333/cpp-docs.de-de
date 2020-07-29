---
title: Compilerwarnung (Stufe 1) C4269
ms.date: 11/04/2016
f1_keywords:
- C4269
helpviewer_keywords:
- C4269
ms.assetid: 96c97bbc-068a-4b65-8cd8-4ed5dca04c15
ms.openlocfilehash: 1b63d1af49a53b7b15cdbae912d79a1b4f0cf787
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230713"
---
# <a name="compiler-warning-level-1-c4269"></a>Compilerwarnung (Stufe 1) C4269

"Bezeichner": "Konstante" automatische Daten, die mit dem vom Compiler generierten Standardkonstruktor initialisiert werden, erzeugen unzuverlässige Ergebnisse

Eine **`const`** Automatische Instanz einer nicht trivialen Klasse wird mit einem vom Compiler generierten Standardkonstruktor initialisiert.

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

Da diese Instanz der-Klasse auf dem Stapel generiert wird, kann der Anfangswert von `m_data` etwas sein. Da es sich um eine- **`const`** Instanz handelt, kann der Wert von `m_data` niemals geändert werden.
