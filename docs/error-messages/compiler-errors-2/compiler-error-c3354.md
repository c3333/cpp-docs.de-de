---
title: Compilerfehler C3354
ms.date: 11/04/2016
f1_keywords:
- C3354
helpviewer_keywords:
- C3354
ms.assetid: 185de401-231e-4999-a149-172ee4c69d84
ms.openlocfilehash: fdc5de7493decf1f44617ab22a00fb5e8852116f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231974"
---
# <a name="compiler-error-c3354"></a>Compilerfehler C3354

"Funktion": Die zum Erstellen eines Delegaten verwendete Funktion kann nicht den Rückgabetyp "Typ" haben.

Die folgenden Typen sind als Rückgabe Typen für einen ungültig **`delegate`** :

- Zeiger auf Funktion

- Zeiger auf Member

- Zeiger auf Memberfunktion

- Verweis auf Funktion

- Verweis auf Memberfunktion

Im folgenden Beispiel wird C3354 generiert:

```cpp
// C3354_2.cpp
// compile with: /clr /c
using namespace System;
typedef void ( *VoidPfn )();

delegate VoidPfn func(); // C3354
// try the following line instead
// delegate  void func();
```
