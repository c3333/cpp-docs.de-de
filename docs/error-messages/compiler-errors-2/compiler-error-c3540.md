---
title: Compilerfehler C3540
ms.date: 11/04/2016
f1_keywords:
- C3540
helpviewer_keywords:
- C3540
ms.assetid: 3c0c959c-e3b7-40eb-b922-ccac44bd9d85
ms.openlocfilehash: 897defd5643a90234c2ae3b7bb4f58904864e858
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91508081"
---
# <a name="compiler-error-c3540"></a>Compilerfehler C3540

"Type": "sizeof" kann nicht auf einen Typ angewendet werden, der "Auto" enthält.

Der [sizeof](../../cpp/sizeof-operator.md) -Operator kann nicht auf den angezeigtem Typ angewendet werden, weil er den **`auto`** Spezifizierer enthält.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C3540 erzeugt.

```cpp
// C3540.cpp
// Compile with /Zc:auto
int main() {
    auto x = 123;
    sizeof(x);    // OK
    sizeof(auto); // C3540
    return 0;
}
```

## <a name="see-also"></a>Siehe auch

[Auto-Schlüsselwort](../../cpp/auto-cpp.md)<br/>
[/Zc: Auto (Variablentyp ableiten)](../../build/reference/zc-auto-deduce-variable-type.md)<br/>
[sizeof-Operator](../../cpp/sizeof-operator.md)
