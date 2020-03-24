---
title: Compilerwarnung (Stufe 1) C4229
ms.date: 11/04/2016
f1_keywords:
- C4229
helpviewer_keywords:
- C4229
ms.assetid: aadfc83b-1e5f-4229-bd0a-9c10a5d13182
ms.openlocfilehash: b1cb97c51dca7cf3fdbca024ead969c4d4e1f3eb
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80163283"
---
# <a name="compiler-warning-level-1-c4229"></a>Compilerwarnung (Stufe 1) C4229

Anachronismus verwendet: modifiziererdaten werden ignoriert.

Die Verwendung eines Microsoft-Modifizierers wie `__cdecl` in einer Daten Deklaration ist eine veraltete Vorgehensweise.

## <a name="example"></a>Beispiel

```cpp
// C4229.cpp
// compile with: /W1 /LD
int __cdecl counter;   // C4229 cdecl ignored
```
