---
title: true (C++)
ms.date: 11/04/2016
f1_keywords:
- true_cpp
helpviewer_keywords:
- true keyword [C++]
ms.assetid: 96be2a70-51c3-4250-9752-874d25a5a11e
ms.openlocfilehash: f6420d0abea8bac1d385c1cfdfd58a5500cf5bd3
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87185839"
---
# <a name="true-c"></a>true (C++)

## <a name="syntax"></a>Syntax

```
bool-identifier = true ;
bool-expression logical-operator true ;
```

## <a name="remarks"></a>Bemerkungen

Dieses Schlüsselwort ist einer der beiden Werte für eine Variable vom Typ [bool](../cpp/bool-cpp.md) oder ein bedingter Ausdruck (ein bedingter Ausdruck ist jetzt ein echter boolescher Ausdruck). Wenn `i` vom Typ ist **`bool`** , wird die- `i = true;` Anweisung **`true`** zugewiesen `i` .

## <a name="example"></a>Beispiel

```cpp
// bool_true.cpp
#include <stdio.h>
int main()
{
    bool bb = true;
    printf_s("%d\n", bb);
    bb = false;
    printf_s("%d\n", bb);
}
```

```Output
1
0
```

## <a name="see-also"></a>Weitere Informationen

[Schlüsselwörter](../cpp/keywords-cpp.md)
