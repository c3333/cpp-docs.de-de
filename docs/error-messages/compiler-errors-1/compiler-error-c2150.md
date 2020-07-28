---
title: Compilerfehler C2150
ms.date: 11/04/2016
f1_keywords:
- C2150
helpviewer_keywords:
- C2150
ms.assetid: 21e82a10-c1d4-4c0d-9dc6-c5d92ea42a31
ms.openlocfilehash: 419aa8229e0fe60d391345556c5fbd8be17558d8
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214736"
---
# <a name="compiler-error-c2150"></a>Compilerfehler C2150

> '*Identifier*': Das Bitfeld muss den Typ ' int ', ' signed int ' oder ' unsigned int ' aufweisen.

Der Basistyp für ein Bitfeld muss **`int`** , **`signed int`** oder sein **`unsigned int`** .

## <a name="example"></a>Beispiel

Dieses Beispiel zeigt, wie Sie C2150 und wie Sie das Problem beheben können:

```cpp
// C2150.cpp
// compile with: /c
struct A {
   float a : 8;    // C2150
   int i : 8;      // OK
};
```
