---
title: Compilerfehler C3118
ms.date: 11/04/2016
f1_keywords:
- C3118
helpviewer_keywords:
- C3118
ms.assetid: 40fbe681-8868-4cb2-a2b2-4db4449319a7
ms.openlocfilehash: 876b007ce7e537a8871147637188b10a100e997b
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2019
ms.locfileid: "74741117"
---
# <a name="compiler-error-c3118"></a>Compilerfehler C3118

"Interface": Schnittstellen unterstützen keine virtuelle Vererbung.

Sie haben versucht, praktisch von einer Schnittstelle zu erben. Ein auf ein Objekt angewendeter

```cpp
// C3118.cpp
__interface I1 {
};

__interface I2 : virtual I1 {   // C3118
};
```

generiert diesen Fehler.
