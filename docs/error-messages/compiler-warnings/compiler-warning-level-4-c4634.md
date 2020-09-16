---
title: Compilerwarnung (Stufe 4) C4634
ms.date: 11/04/2016
f1_keywords:
- C4634
helpviewer_keywords:
- C4634
ms.assetid: 3e3496ce-2ac7-43d0-a48a-f514c950e81d
ms.openlocfilehash: 86ac95fbd030ecf35a85eba153a449511ee7a535
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/16/2020
ms.locfileid: "90683883"
---
# <a name="compiler-warning-level-4-c4634"></a>Compilerwarnung (Stufe 4) C4634

XML-Dokumentkommentar: Kann nicht angewendet werden: Grund

XML-Dokumentationstags können nicht auf alle C++-Konstrukte angewendet werden.  So kann z. B. einem Namespace oder einer Vorlage kein Dokumentationskommentar hinzugefügt werden.

Weitere Informationen finden Sie unter [XML Documentation](../../build/reference/xml-documentation-visual-cpp.md).

## <a name="examples"></a>Beispiele

Im folgenden Beispiel wird C4634 generiert.

```cpp
// C4634.cpp
// compile with: /W4 /doc /c
/// This is a namespace.   // C4634
namespace hello {
   class MyClass  {};
};
```

Im folgenden Beispiel wird C4634 generiert.

```cpp
// C4634_b.cpp
// compile with: /W4 /doc /c
/// This is a template.   // C4634
template <class T>
class MyClass  {};
```
