---
title: Compilerfehler C2296
ms.date: 11/04/2016
f1_keywords:
- C2296
helpviewer_keywords:
- C2296
ms.assetid: 47d270f4-13ce-4c16-81e2-7d67c6c4a540
ms.openlocfilehash: 020f046648488ca67923b7035acaa6c79ce495e4
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759073"
---
# <a name="compiler-error-c2296"></a>Compilerfehler C2296

"Operator": Ungültiger Linker Operand

Der linke Operand, der mit `operator` verwendet wird, ist ungültig.

Der Compiler kann z. b. eine Deklaration sehen, in der Sie einen Funktions Aufrufvorgang beabsichtigt haben.

Im folgenden Beispiel wird C2296 generiert:

```cpp
// C2296.cpp
struct MyStruct {
   struct Help {
      Help(float f) : m_f(f) {}
      float m_f;
   };

   MyStruct(const Help &h) : m_f(h.m_f) {}
   MyStruct(float f) : m_f(f) {}
   MyStruct operator*(const MyStruct &f1) const {
      return MyStruct(m_f * f1.m_f);
   }

private:
   float m_f;
};

int main() {
   float f1 = 1.0f;

   MyStruct m_MyStruct1 ( MyStruct::Help( f1 ) );
   // try the following line instead
   // MyStruct m_MyStruct1 = MyStruct::Help( f1 );

   MyStruct m_MyStruct2 ( MyStruct::Help( f1 ) );
   // try the following line instead
   // MyStruct m_MyStruct2 = MyStruct::Help( f1 );

   MyStruct m_MyStruct3 = m_MyStruct1 * m_MyStruct2;   // C2296
}
```
