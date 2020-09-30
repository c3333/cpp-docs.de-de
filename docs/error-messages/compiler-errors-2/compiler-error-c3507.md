---
title: Compilerfehler C3507
ms.date: 11/04/2016
f1_keywords:
- C3507
helpviewer_keywords:
- C3507
ms.assetid: 75f89767-f6f9-40f6-9820-81a49e09abdf
ms.openlocfilehash: a38efcc0d74bbea0e0bf767cb9e5a11561ab4fb8
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91507131"
---
# <a name="compiler-error-c3507"></a>Compilerfehler C3507

eine ProgID kann nicht mehr als 39 Zeichen ' ID ' aufweisen. und enthalten keine Interpunktions Zeichen außer "."; und nicht mit einer Ziffer beginnen

Das [ProgID](../../windows/attributes/progid.md) -Attribut weist Einschränkungen hinsichtlich der Werte auf, die es annehmen kann.

Im folgenden Beispiel wird C3507 generiert:

```cpp
// C3507.cpp
[module(name="x")];
[
coclass,
progid("0123456789012345678901234567890123456789"),
uuid("00000000-0000-0000-0000-000000000001") // C3507 expected
]
struct CMyStruct {
};
int main() {
}
```
