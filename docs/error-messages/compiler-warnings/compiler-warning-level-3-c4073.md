---
title: Compilerwarnung (Stufe 3) C4073
ms.date: 11/04/2016
f1_keywords:
- C4073
helpviewer_keywords:
- C4073
ms.assetid: 50081a6e-6acd-45ff-8484-9b1ea926cc5c
ms.openlocfilehash: 80b43f5fc5af23d84fe43727b75d041e39405ade
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80199109"
---
# <a name="compiler-warning-level-3-c4073"></a>Compilerwarnung (Stufe 3) C4073

Initialisierer werden im Bibliotheks Initialisierungs Bereich abgelegt.

Nur Entwickler von Drittanbieterbibliotheken sollten den Bibliotheks Initialisierungs Bereich verwenden, der durch [#pragma init_seg](../../preprocessor/init-seg.md)angegeben wird. Im folgenden Beispiel wird C4073 generiert:

```cpp
// C4073.cpp
// compile with: /W3
#pragma init_seg(lib)   // C4073

// try this line to resolve the warning
// #pragma init_seg(user)

int main() {
}
```
