---
title: Compilerfehler C2703
description: Beschreibt den Microsoft C/C++-Compilerfehler C2703.
ms.date: 08/24/2020
f1_keywords:
- C2703
helpviewer_keywords:
- C2703
ms.assetid: 384295c3-643d-47ae-a9a6-865b3036aa84
ms.openlocfilehash: 4d5b5ccad1cd15c1a107c81423e2372e14165776
ms.sourcegitcommit: efc8c32205c9d610f40597556273a64306dec15d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/26/2020
ms.locfileid: "88898602"
---
# <a name="compiler-error-c2703"></a>Compilerfehler C2703

> Ungültige `__leave` Anweisung

## <a name="remarks"></a>Hinweise

Eine- **`__leave`** Anweisung muss sich innerhalb eines- **`__try`** Blocks befinden.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C2703 generiert:

```cpp
// C2703.cpp
int main() {
   __leave;   // C2703
   __try {
      // try the following line instead
      __leave;
   }
   __finally {}
}
```

## <a name="see-also"></a>Weitere Informationen

[Das `__leave` Schlüsselwort](../../cpp/try-except-statement.md#__leave)\
[`try-except` an](../../cpp/try-except-statement.md)\
[`try-finally`-Anweisung](../../cpp/try-finally-statement.md)
