---
title: Compilerfehler C3072
ms.date: 11/04/2016
f1_keywords:
- C3072
helpviewer_keywords:
- C3072
ms.assetid: cdd5cb6b-c478-4698-adfa-c40188d34a18
ms.openlocfilehash: bcf2548fbe1182f7f6c4bd966ca6aa9ef9f10089
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212604"
---
# <a name="compiler-error-c3072"></a>Compilerfehler C3072

> der Operator "*Operator-Name*" kann nicht auf eine Instanz einer Verweis Klasse angewendet werden.

Verwenden Sie den unären *Operator-Name-* Operator, um eine Instanz einer Verweis Klasse in einen Handles-Typ zu konvertieren.

Ein CLR-Typ erfordert CLR-Operatoren, nicht native (oder Standard-) Operatoren.  Weitere Informationen finden Sie unter [Tracking Reference Operator](../../extensions/tracking-reference-operator-cpp-component-extensions.md).

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C3072 generiert.

```cpp
// C3072.cpp
// compile with: /clr
ref class R {};

int main() {
   R r1;
   R^ r2 = &r1;   // C3072
   R^ r3 = %r1;   // OK
}
```
