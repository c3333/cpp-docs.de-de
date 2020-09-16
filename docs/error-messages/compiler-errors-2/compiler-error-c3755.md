---
title: Compilerfehler C3755
ms.date: 11/04/2016
f1_keywords:
- C3755
helpviewer_keywords:
- C3755
ms.assetid: 9317b55e-a52e-4b87-b915-5a208d6eda38
ms.openlocfilehash: cc4e5423dc8fc53a8f749e2392ff23658a0cb0f1
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/16/2020
ms.locfileid: "90685114"
---
# <a name="compiler-error-c3755"></a>Compilerfehler C3755

"Delegat": ein Delegat kann nicht definiert werden.

Ein Delegat [(Komponenten Erweiterungen für C++)](../../extensions/delegate-cpp-component-extensions.md) kann deklariert, aber nicht definiert werden.

## <a name="examples"></a>Beispiele

Im folgenden Beispiel wird C3755 generiert.

```cpp
// C3755.cpp
// compile with: /clr /c
delegate void MyDel() {};   // C3755
```

C3755 kann auch auftreten, wenn Sie versuchen, eine Delegatvorlage zu erstellen. Im folgenden Beispiel wird C3755 generiert.

```cpp
// C3755_b.cpp
// compile with: /clr /c
ref struct R {
   template<class T>
   delegate void D(int) {}   // C3755
};
```
