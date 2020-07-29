---
title: Compilerfehler C2821
ms.date: 11/04/2016
f1_keywords:
- C2821
helpviewer_keywords:
- C2821
ms.assetid: e8d71988-a968-4484-94db-e8c3bad74a4a
ms.openlocfilehash: 115874724a24530e0d85256e11c3aa355aa4d6af
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225396"
---
# <a name="compiler-error-c2821"></a>Compilerfehler C2821

der erste formale Parameter für "Operator new" muss "unsigned int" sein.

Der erste formale Parameter des [new-Operators](../../standard-library/new-operators.md#op_new) muss ein ohne Vorzeichen sein **`int`** .

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C2821 generiert:

```cpp
// C2821.cpp
// compile with: /c
void * operator new( /* unsigned int,*/ void * );   // C2821
void * operator new( unsigned int, void * );
```
