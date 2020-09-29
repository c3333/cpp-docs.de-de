---
title: Compilerfehler C2530
ms.date: 11/04/2016
f1_keywords:
- C2530
helpviewer_keywords:
- C2530
ms.assetid: b790a312-48df-4a6a-9e27-be2c5f32f16c
ms.openlocfilehash: 4eca5579f6bf132452a813d8dd99193df5f76b92
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91500540"
---
# <a name="compiler-error-c2530"></a>Compilerfehler C2530

"Bezeichner": Verweise müssen initialisiert werden.

Sie müssen einen Verweis initialisieren, wenn er deklariert wurde, es sei denn, er ist bereits deklariert:

- Mit dem Schlüsselwort [extern](../../cpp/extern-cpp.md).

- Als Member einer Klasse, Struktur oder Union (und im Konstruktor initialisiert).

- Als Parameter in einer Funktionsdeklaration oder-Definition.

- Als Rückgabetyp einer Funktion.

Im folgenden Beispiel wird C2530 generiert:

```cpp
// C2530.cpp
int main() {
   int i = 0;
   int &j;   // C2530
   int &k = i;   // OK
}
```
