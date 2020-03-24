---
title: Compilerwarnung (Stufe 2) C4309
ms.date: 11/04/2016
f1_keywords:
- C4309
helpviewer_keywords:
- C4309
ms.assetid: cb3f41ef-fd8a-4def-baa1-924e751fca68
ms.openlocfilehash: a307d941f6225c9e431ad71a6385229bd01957f9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80161866"
---
# <a name="compiler-warning-level-2-c4309"></a>Compilerwarnung (Stufe 2) C4309

' Konvertierung ': Abschneiden eines konstanten Werts

Die Typkonvertierung bewirkt, dass eine Konstante den zugeordneten Speicherplatz überschreitet. Möglicherweise müssen Sie einen größeren Typ für die Konstante verwenden.

Im folgenden Beispiel wird C4309 generiert:

```cpp
// C4309.cpp
// compile with: /W2
int main()
{
   char c = 128;   // C4309
}
```
