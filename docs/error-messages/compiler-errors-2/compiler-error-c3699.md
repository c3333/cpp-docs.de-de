---
title: Compilerfehler C3699
ms.date: 11/04/2016
f1_keywords:
- C3699
helpviewer_keywords:
- C3699
ms.assetid: 47c29afc-ab8b-4238-adfe-788dd6e00b3b
ms.openlocfilehash: d313168e8033395da1749e000e52421939f77af4
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/16/2020
ms.locfileid: "90686651"
---
# <a name="compiler-error-c3699"></a>Compilerfehler C3699

"Operator": Diese Dereferenzierung kann nicht für den Typ "Typ" verwendet werden.

Es wurde versucht, Dereferenzierung zu verwenden, die für nicht zulässig ist `type` .

## <a name="examples"></a>Beispiele

Im folgenden Beispiel wird C3699 generiert.

```cpp
// C3699.cpp
// compile with: /clr /c
using namespace System;
int main() {
   String * s;   // C3699
   // try the following line instead
   // String ^ s2;
}
```

Eine triviale Eigenschaft kann keinen Verweistyp aufweisen. Weitere Informationen finden Sie unter [property](../../extensions/property-cpp-component-extensions.md) . Im folgenden Beispiel wird C3699 generiert.

```cpp
// C3699_b.cpp
// compile with: /clr /c
ref struct C {
   property System::String % x;   // C3699
   property System::String ^ y;   // OK
};
```

Das Äquivalent eines "Zeiger auf eine Zeiger"-Syntax ist ein Handle für einen nach Verfolgungs Verweis. Im folgenden Beispiel wird C3699 generiert.

```cpp
// C3699_c.cpp
// compile with: /clr /c
using namespace System;
void Test(String ^^ i);   // C3699
void Test2(String ^% i);
```
