---
title: Compilerwarnung (Stufe 1) C4183
ms.date: 11/04/2016
f1_keywords:
- C4183
helpviewer_keywords:
- C4183
ms.assetid: dc48312c-4b34-44dd-80ff-eb5f11d5ca47
ms.openlocfilehash: cff62c18442cd6d55a9444bb86944b691145b9fe
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231922"
---
# <a name="compiler-warning-level-1-c4183"></a>Compilerwarnung (Stufe 1) C4183

' Identifier ': fehlender Rückgabetyp. angenommen, eine Member-Funktion gibt "int" zurück.

Die Inline Definition einer Member-Funktion in einer Klasse oder einer Struktur weist keinen Rückgabetyp auf. Bei dieser Member-Funktion wird davon ausgegangen, dass Sie den Standard Rückgabetyp hat **`int`** .

Im folgenden Beispiel wird C4183 generiert:

```cpp
// C4183.cpp
// compile with: /W1 /c
#pragma warning(disable : 4430)
class MyClass1;
class MyClass2 {
   MyClass1() {};   // C4183
};
```
