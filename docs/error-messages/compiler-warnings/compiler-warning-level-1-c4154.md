---
title: Compilerwarnung (Stufe 1) C4154
ms.date: 11/04/2016
f1_keywords:
- C4154
helpviewer_keywords:
- C4154
ms.assetid: 4511afeb-e893-4cc6-83b6-4c7a0477f76b
ms.openlocfilehash: 07b4c6e0821c925e70ce1bce1d910f184d658982
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80163611"
---
# <a name="compiler-warning-level-1-c4154"></a>Compilerwarnung (Stufe 1) C4154

Löschen eines Array Ausdrucks Konvertierung in Zeiger angegeben

Sie können `delete` nicht in einem Array verwenden, sodass der Compiler das Array in einen Zeiger konvertiert.

## <a name="example"></a>Beispiel

```cpp
// C4154.cpp
// compile with: /c /W1
int main() {
   int array[ 10 ];
   delete array;   // C4154 can't delete stack object

   int *parray2 = new int [10];
   int (&array2)[10] = (int(&)[10]) parray2;
   delete [] array2;   // C4154

   // try the following line instead
   delete [] &array2;
}
```
