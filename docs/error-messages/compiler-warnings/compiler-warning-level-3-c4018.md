---
title: Compilerwarnung (Stufe 3) C4018
description: Microsoft C/C++-Compilerwarnung C4018, die Ursache und die Lösung.
ms.date: 10/16/2020
f1_keywords:
- C4018
helpviewer_keywords:
- C4018
ms.openlocfilehash: b9d01f6b733c2ca18880aa6f4b6fca9771f8123f
ms.sourcegitcommit: f19f02f217b80804ab321d463c76ce6f681abcc6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2020
ms.locfileid: "92176174"
---
# <a name="compiler-warning-level-3-c4018"></a>Compilerwarnung (Stufe 3) C4018

> "*Token*": Konflikt zwischen "signed" und "unsigned"

Die Verwendung des *tokenoperators* zum Vergleichen von **`signed`** und Zahlen erforderte, dass **`unsigned`** der Compiler den **`signed`** Wert in konvertiert **`unsigned`** .

## <a name="remarks"></a>Bemerkungen

Eine Möglichkeit, diese Warnung zu beheben, ist, wenn Sie einen der beiden Typen umwandeln, wenn Sie **`signed`** -und- **`unsigned`** Typen vergleichen.

## <a name="example"></a>Beispiel

Dieses Beispiel generiert C4018 und zeigt, wie Sie dieses Problem beheben:

```cpp
// C4018.cpp
// compile with: cl /EHsc /W4 C4018.cpp
int main() {
    unsigned int uc = 0;
    int c = 0;
    unsigned int c2 = c; // implicit conversion

    if (uc < c)           // C4018
        uc = 0;

    if (uc < unsigned(c)) // OK
        uc = 0;

    if (uc < c2)          // Also OK
       uc = 0;
}
```

## <a name="see-also"></a>Weitere Informationen

[Compilerwarnung (Stufe 4) C4388](c4388.md)\
[Compilerwarnung (Stufe 4) C4389](compiler-warning-level-4-c4389.md)
