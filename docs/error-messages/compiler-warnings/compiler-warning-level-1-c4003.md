---
title: Compilerwarnung (Stufe 1) C4003
ms.date: 11/04/2016
f1_keywords:
- C4003
helpviewer_keywords:
- C4003
ms.assetid: 0ed1c285-4428-4c90-8131-86897e31f115
ms.openlocfilehash: 3bf1eea1b8ad0529d6603a2388e61b9107304f43
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80164741"
---
# <a name="compiler-warning-level-1-c4003"></a>Compilerwarnung (Stufe 1) C4003

Nicht genügend tatsächliche Parameter für das Makro 'identifier'

Die Anzahl der formalen Parameter in der Makro Definition überschreitet die Anzahl der tatsächlichen Parameter im Makro. Die Makro Erweiterung ersetzt leeren Text für die fehlenden Parameter.

Im folgenden Beispiel wird C4003 generiert:

```cpp
// C4003.cpp
// compile with: /WX
#define test(a,b) (a+b)

int main()
{
   int a = 1;
   int b = 2;
   a = test(b);   // C4003
   // try..
   a = test(a,b);
}
```
