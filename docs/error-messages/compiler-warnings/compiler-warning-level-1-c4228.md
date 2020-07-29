---
title: Compilerwarnung (Stufe 1) C4228
ms.date: 11/04/2016
f1_keywords:
- C4228
helpviewer_keywords:
- C4228
ms.assetid: 9301d660-d601-464e-83f5-7ed844a3c6dc
ms.openlocfilehash: 3a89d5c0924e6fd12a4ccf8afa957f8908670d49
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223238"
---
# <a name="compiler-warning-level-1-c4228"></a>Compilerwarnung (Stufe 1) C4228

nicht dem Standard entsprechende Erweiterung: Qualifizierer nach einem Komma in der Deklaratorliste werden ignoriert.

Die Verwendung von Qualifizierern wie **`const`** oder **`volatile`** nach einem Komma beim Deklarieren von Variablen ist eine Microsoft-Erweiterung ([/Ze](../../build/reference/za-ze-disable-language-extensions.md)).

## <a name="example"></a>Beispiel

```cpp
// C4228.cpp
// compile with: /W1
int j, const i = 0;  // C4228
int k;
int const m = 0;  // ok
int main()
{
}
```
