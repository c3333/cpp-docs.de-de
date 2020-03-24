---
title: Compilerfehler C3286
ms.date: 11/04/2016
f1_keywords:
- C3286
helpviewer_keywords:
- C3286
ms.assetid: 554328c8-cf44-4f7d-a8d2-def74d28ecdd
ms.openlocfilehash: 4c87e98f11a560d0d92be8ea7bc624edd4e09ad2
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80201395"
---
# <a name="compiler-error-c3286"></a>Compilerfehler C3286

> "*Spezifizierer*": eine Iterations Variable darf keine Speicherklassenspezifizierer aufweisen.

Eine Speicher Klasse kann nicht für eine Iterations Variable angegeben werden. Weitere Informationen finden Sie unter [Speicher Klassen (C++)](../../cpp/storage-classes-cpp.md) und [für jede in](../../dotnet/for-each-in.md).

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C3286 generiert. Außerdem wird die korrekte Verwendung veranschaulicht.

```cpp
// C3286.cpp
// compile with: /clr
int main() {
   array<int> ^p = { 1, 2, 3 };
   for each (static int i in p) {}   // C3286
   for each (int j in p) {}   // OK
}
```
