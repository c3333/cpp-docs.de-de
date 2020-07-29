---
title: Compilerfehler C3541
ms.date: 11/04/2016
f1_keywords:
- C3541
helpviewer_keywords:
- C3541
ms.assetid: 252cfd4c-5fd2-415e-a17d-6b0c254350db
ms.openlocfilehash: 32926d0ef9343bad9ed73458e4d52d317b628109
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221041"
---
# <a name="compiler-error-c3541"></a>Compilerfehler C3541

"Typ": typeid kann nicht auf einen Typ angewendet werden, der "Auto" enthält.

Der [typeid](../../extensions/typeid-cpp-component-extensions.md) -Operator kann nicht auf den angezeigtem Typ angewendet werden, weil er den **`auto`** Spezifizierer enthält.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C3541 erzeugt.

```cpp
// C3541.cpp
// Compile with /Zc:auto
#include <typeinfo>
int main() {
    auto x = 123;
    typeid(x);    // OK
    typeid(auto); // C3541
    return 0;
}
```

## <a name="see-also"></a>Siehe auch

[Auto-Schlüsselwort](../../cpp/auto-keyword.md)<br/>
[/Zc: Auto (Variablentyp ableiten)](../../build/reference/zc-auto-deduce-variable-type.md)<br/>
[TypeId](../../extensions/typeid-cpp-component-extensions.md)
