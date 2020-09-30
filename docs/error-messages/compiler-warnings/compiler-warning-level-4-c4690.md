---
title: Compilerwarnung (Stufe 4) C4690
ms.date: 07/03/2018
f1_keywords:
- C4690
helpviewer_keywords:
- C4690
ms.assetid: 080a0ea1-458b-477b-a37a-4a34c94709ff
ms.openlocfilehash: de996128c68ebf96b4a00f6206cbaf54d97ca275
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91509969"
---
# <a name="compiler-warning-level-4-c4690"></a>Compilerwarnung (Stufe 4) C4690

> \[ Emitidl (Pop)]: mehr POPs als Pushvorgänge

## <a name="remarks"></a>Bemerkungen

Das [emitidl](../../windows/attributes/emitidl.md) -Attribut wurde einmal mehr vom Stapel abgerufen als in den Stapel verschoben.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C4690 generiert. Um dieses Problem zu beheben, stellen Sie sicher, dass das Attribut genau so oft wie möglich per Pushvorgang übermittelt wird.

```cpp
// C4690.cpp
// compile with: /c /W4
[emitidl(pop)];   // C4690
class x {};
```
