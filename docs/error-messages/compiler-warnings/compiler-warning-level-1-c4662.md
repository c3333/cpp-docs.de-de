---
title: Compilerwarnung (Stufe 1) C4662
ms.date: 11/04/2016
f1_keywords:
- C4662
helpviewer_keywords:
- C4662
ms.assetid: 7efda273-d04a-47b7-ad65-ff1ff94b5ffc
ms.openlocfilehash: 4fdb57eecb17f4385c0c297c1a13902890e16fea
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175598"
---
# <a name="compiler-warning-level-1-c4662"></a>Compilerwarnung (Stufe 1) C4662

Explizite Instanziierung; Vorlagenklasse "Bezeichner1" besitzt keine Definition, von der "Bezeichner2" spezialisiert werden kann.

Die angegebene Vorlagenklasse wurde deklariert, aber nicht definiert.

## <a name="example"></a>Beispiel

```cpp
// C4662.cpp
// compile with: /W1 /LD
template<class T, int i> class MyClass; // no definition
template MyClass< int, 1>;              // C4662
```
