---
title: Compilerfehler C3622
ms.date: 11/04/2016
f1_keywords:
- C3622
helpviewer_keywords:
- C3622
ms.assetid: 02836f78-0cf2-4947-b87e-710187d81014
ms.openlocfilehash: 8775ff6fd78f1092ae931921a2b15ed2f8b166e9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214541"
---
# <a name="compiler-error-c3622"></a>Compilerfehler C3622

"Class": eine Klasse, die als "Schlüsselwort" deklariert wurde, kann nicht instanziiert werden.

Es wurde versucht, eine Klasse zu instanziieren, die als [abstrakt](../../extensions/abstract-cpp-component-extensions.md)markiert ist. Eine als gekennzeichnete Klasse **`abstract`** kann eine Basisklasse sein, aber Sie kann nicht instanziiert werden.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C3622 generiert.

```cpp
// C3622.cpp
// compile with: /clr
ref class a abstract {};

int main() {
   a aa;   // C3622
}
```
