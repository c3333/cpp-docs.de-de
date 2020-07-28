---
title: Compilerwarnung (Stufe 1) C4224
ms.date: 11/04/2016
f1_keywords:
- C4224
helpviewer_keywords:
- C4224
ms.assetid: 1531cae0-5040-49fd-b149-005bb5085391
ms.openlocfilehash: c58b003e43e74886c65d41e9abd6e49d15825653
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220092"
---
# <a name="compiler-warning-level-1-c4224"></a>Compilerwarnung (Stufe 1) C4224

nicht dem Standard entsprechende Erweiterung: der formale Parameter "Identifier" wurde zuvor als Typ definiert.

Der Bezeichner wurde zuvor als verwendet **`typedef`** . Dies verursacht eine Warnung unter ANSI-Kompatibilität ([/Za](../../build/reference/za-ze-disable-language-extensions.md)).

## <a name="example"></a>Beispiel

```cpp
// C4224.cpp
// compile with: /Za /W1 /LD
typedef int I;
void func ( int I );  // C4224
```
