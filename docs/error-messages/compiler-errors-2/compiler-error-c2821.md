---
title: Compilerfehler C2821
ms.date: 11/04/2016
f1_keywords:
- C2821
helpviewer_keywords:
- C2821
ms.assetid: e8d71988-a968-4484-94db-e8c3bad74a4a
ms.openlocfilehash: d099c4a0f6e1ea77a25213e3873b8a0814e28dcd
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80201994"
---
# <a name="compiler-error-c2821"></a>Compilerfehler C2821

der erste formale Parameter für "Operator new" muss "unsigned int" sein.

Der erste formale Parameter des [new-Operators](../../standard-library/new-operators.md#op_new) muss ein nicht signiertes `int`sein.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C2821 generiert:

```cpp
// C2821.cpp
// compile with: /c
void * operator new( /* unsigned int,*/ void * );   // C2821
void * operator new( unsigned int, void * );
```
