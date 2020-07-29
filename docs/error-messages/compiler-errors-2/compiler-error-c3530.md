---
title: Compilerfehler C3530
ms.date: 11/04/2016
f1_keywords:
- C3530
helpviewer_keywords:
- C3530
ms.assetid: 21be81ce-b699-4c74-81bc-80a0c34d2d5a
ms.openlocfilehash: 023d7f0a5d509c4b301a9985da8ea7feb1f3d203
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228829"
---
# <a name="compiler-error-c3530"></a>Compilerfehler C3530

"Auto" kann nicht mit einem anderen Typspezifizierer kombiniert werden.

Ein Typspezifizierer wird mit dem- **`auto`** Schlüsselwort verwendet.

### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler

1. Verwenden Sie keinen Typspezifizierer in einer Variablen Deklaration, die das **`auto`** Schlüsselwort verwendet.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C3530 `x` erstellt, da Variable mit dem **`auto`** -Schlüsselwort und dem-Typ deklariert wird **`int`** und da das Beispiel mit **/Zc: Auto**kompiliert wird.

```cpp
// C3530.cpp
// Compile with /Zc:auto
int main()
{
   auto int x;   // C3530
   return 0;
}
```

## <a name="see-also"></a>Siehe auch

[Auto-Schlüsselwort](../../cpp/auto-keyword.md)
