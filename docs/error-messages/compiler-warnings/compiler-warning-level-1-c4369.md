---
title: Compilerwarnung (Stufe 1) C4369
ms.date: 11/04/2016
f1_keywords:
- C4369
helpviewer_keywords:
- C4369
ms.assetid: ade87e84-36be-4e00-be99-2930af848feb
ms.openlocfilehash: b0d99792e3e0ea372c8629319553dd9a59ad4b47
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187062"
---
# <a name="compiler-warning-level-1-c4369"></a>Compilerwarnung (Stufe 1) C4369

' Enumerator ': der Enumeratorwert ' value ' kann nicht als ' type ' dargestellt werden, der Wert ist ' new_value '.

Ein Enumerator wurde so berechnet, dass er größer als der größte Wert für den angegebenen zugrunde liegenden Typ ist.  Dies verursachte einen Überlauf, und der Compiler hat den Enumeratorwert auf den niedrigsten möglichen Wert für den Typ umschließen.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C4369 generiert.

```cpp
// C4369.cpp
// compile with: /W1
int main() {
   enum Color: char { red = 0x7e, green, blue };   // C4369
   enum Color2: char { red2 = 0x7d, green2, blue2};   // OK
}
```
