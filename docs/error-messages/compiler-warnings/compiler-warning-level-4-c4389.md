---
title: Compilerwarnung (Stufe 4) C4389
description: Microsoft C/C++-Compilerwarnung C4389, die Ursache und die Lösung.
ms.date: 10/16/2020
f1_keywords:
- c4389
helpviewer_keywords:
- C4389
ms.openlocfilehash: b06b013151ed12b4f66bb23a7e862992d05e6b30
ms.sourcegitcommit: f19f02f217b80804ab321d463c76ce6f681abcc6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2020
ms.locfileid: "92176268"
---
# <a name="compiler-warning-level-4-c4389"></a>Compilerwarnung (Stufe 4) C4389

> "*Equality-Operator*": Konflikt zwischen Vorzeichen und Vorzeichen

Eine **`==`** **`!=`** -oder-Operation mit den **`signed`** -und- **`unsigned`** Variablen. Dies kann zu einem Datenverlust führen.

## <a name="remarks"></a>Bemerkungen

Eine Möglichkeit, diese Warnung zu beheben, ist, wenn Sie einen der beiden Typen umwandeln, wenn Sie **`signed`** -und- **`unsigned`** Typen vergleichen.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C4389 generiert:

```cpp
// C4389.cpp
// compile with: cl /EHsc /W4 C4389.cpp

int main()
{
   int a = 9;
   unsigned int b = 10;
   int result = 0;

   if (a == b)   // C4389
      result = 1;
   else
      result = 2;

   if (unsigned(a) == b) // OK
      result = 3;
   else
      result = 4;

   return result;
}
```

## <a name="see-also"></a>Weitere Informationen

[Compilerwarnung C4018](compiler-warning-level-3-c4018.md)\
[Compilerwarnung (Stufe 4) C4388](c4388.md)
