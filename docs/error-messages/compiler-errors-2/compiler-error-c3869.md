---
title: Compilerfehler C3869
ms.date: 11/04/2016
f1_keywords:
- C3869
helpviewer_keywords:
- C3869
ms.assetid: 85b2ad72-95c1-4ed6-9761-6ef66c3802b7
ms.openlocfilehash: 3ca56ce3c02915c88f70907d024aea3930a1aa1e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87197539"
---
# <a name="compiler-error-c3869"></a>Compilerfehler C3869

in der gcnew-Einschränkung fehlt die leere Parameterliste "()".

Die **`gcnew`** besondere Einschränkung wurde ohne die leere Parameterliste angegeben. Weitere Informationen finden Sie [unter Einschränkungen für generische Typparameter (C++/CLI)](../../extensions/constraints-on-generic-type-parameters-cpp-cli.md) .

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C3869 generiert.

```cpp
// C3869.cpp
// compile with: /c /clr
using namespace System;
generic <typename T>
where T : gcnew   // C3869
// try the following line instead
// where T : gcnew()
ref class List {};
```
