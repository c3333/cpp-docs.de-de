---
title: Compilerfehler C3540
ms.date: 11/04/2016
f1_keywords:
- C3540
helpviewer_keywords:
- C3540
ms.assetid: 3c0c959c-e3b7-40eb-b922-ccac44bd9d85
ms.openlocfilehash: a041961e8a91832be67d8def8f2a6a3ef70906d9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223394"
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

[Auto-Schlüsselwort](../../cpp/auto-keyword.md)<br/>
[/Zc: Auto (Variablentyp ableiten)](../../build/reference/zc-auto-deduce-variable-type.md)<br/>
[sizeof-Operator](../../cpp/sizeof-operator.md)
