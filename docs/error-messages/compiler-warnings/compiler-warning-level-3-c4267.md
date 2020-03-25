---
title: Compilerwarnung (Stufe 3) C4267
ms.date: 11/04/2016
f1_keywords:
- C4267
helpviewer_keywords:
- C4267
ms.assetid: 2fa2f13f-fa4f-47bb-ad8f-6cb19cfc91e6
ms.openlocfilehash: 2ae4b53dfa5050e178bf5ddd366e97c4ff773dd0
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80161515"
---
# <a name="compiler-warning-level-3-c4267"></a>Compilerwarnung (Stufe 3) C4267

'var': Konvertierung von 'size_t' nach 'type', Datenverlust möglich

Der Compiler hat eine Konvertierung von `size_t` zu einem kleineren Typ ermittelt.

Verwenden Sie zum Beheben dieser Warnung `size_t` anstelle von `type`. Verwenden Sie alternativ einen integralen Typ, der mindestens so groß wie `size_t` ist.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird der Fehler C4267 generiert:

```cpp
// C4267.cpp
// compile by using: cl /W4 C4267.cpp
void Func1(short) {}
void Func2(int) {}
void Func3(long) {}
void Func4(size_t) {}

int main() {
   size_t bufferSize = 10;
   Func1(bufferSize);   // C4267 for all platforms
   Func2(bufferSize);   // C4267 only for 64-bit platforms
   Func3(bufferSize);   // C4267 only for 64-bit platforms
   Func4(bufferSize);   // OK for all platforms
}
```
