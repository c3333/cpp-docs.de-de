---
title: Compilerwarnung (Stufe 1) C4076
ms.date: 11/04/2016
f1_keywords:
- C4076
helpviewer_keywords:
- C4076
ms.assetid: 04581066-313a-4a11-bb60-721e6d038d75
ms.openlocfilehash: 77efeae27a67ea844759fd9980801d3daf788e89
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80200256"
---
# <a name="compiler-warning-level-1-c4076"></a>Compilerwarnung (Stufe 1) C4076

> "*Typmodifizierer*": kann nicht mit Typ "*Typname*" verwendet werden.

## <a name="remarks"></a>Bemerkungen

Ein Typmodifizierer, ob er **signiert** oder **nicht signiert**ist, kann nicht mit einem nicht ganzzahligen Typ verwendet werden. der *Typmodifizierer* wird ignoriert.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C4076 generiert. Entfernen Sie den Typmodifizierer **ohne** Vorzeichen, um ihn zu beheben:

```cpp
// C4076.cpp
// compile with: /W1 /LD
unsigned double x;   // C4076
```
