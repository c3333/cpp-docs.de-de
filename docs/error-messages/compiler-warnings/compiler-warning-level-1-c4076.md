---
title: Compilerwarnung (Stufe 1) C4076
ms.date: 11/04/2016
f1_keywords:
- C4076
helpviewer_keywords:
- C4076
ms.assetid: 04581066-313a-4a11-bb60-721e6d038d75
ms.openlocfilehash: 1958aec4d6642188af1467ab4cab1ecf55c29165
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223316"
---
# <a name="compiler-warning-level-1-c4076"></a>Compilerwarnung (Stufe 1) C4076

> "*Typmodifizierer*": kann nicht mit Typ "*Typname*" verwendet werden.

## <a name="remarks"></a>Bemerkungen

Ein Typmodifizierer, ob er **`signed`** oder ist **`unsigned`** , kann nicht mit einem nicht ganzzahligen Typ verwendet werden. der *Typmodifizierer* wird ignoriert.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C4076 generiert. Entfernen Sie den Typmodifizierer, um ihn zu beheben **`unsigned`** :

```cpp
// C4076.cpp
// compile with: /W1 /LD
unsigned double x;   // C4076
```
