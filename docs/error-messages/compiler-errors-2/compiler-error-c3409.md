---
title: Compilerfehler C3409
ms.date: 11/06/2018
f1_keywords:
- C3409
helpviewer_keywords:
- C3409
ms.assetid: e372d9fa-230c-4b28-b6d3-6ad81ccf9dbb
ms.openlocfilehash: 0bf8b918f254c05bfe57034e25611c8dc17a783a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231961"
---
# <a name="compiler-error-c3409"></a>Compilerfehler C3409

> ein leerer Attribut Block ist nicht zulässig.

## <a name="remarks"></a>Bemerkungen

Die eckigen Klammern wurden vom Compiler als [Attribut](../../windows/attributes-alphabetical-reference.md) Block interpretiert, aber es wurden keine Attribute gefunden.

Der Compiler generiert diesen Fehler möglicherweise, wenn Sie eckige Klammern als Teil der Definition eines Lambda-Ausdrucks verwenden. Dieser Fehler tritt auf, wenn der Compiler nicht bestimmen kann, ob die eckigen Klammern Teil der Definition eines Lambda-Ausdrucks oder eines Attribut Blocks sind. Weitere Informationen zu Lambda-Ausdrücken finden Sie unter [Lambda-Ausdrücke](../../cpp/lambda-expressions-in-cpp.md).

### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler

1. Wenn die eckigen Klammern Teil eines Attribut Blocks sind:

   1. Geben Sie ein oder mehrere Attribute im Attribut Block an.

   1. Entfernen Sie den-Attribut Block.

1. Wenn die eckigen Klammern Teil eines Lambda-Ausdrucks sind, stellen Sie sicher, dass der Lambda-Ausdruck gültige Syntax Regeln befolgt.

   Weitere Informationen zur Syntax von Lambda Ausdrücken finden Sie unter [Lambda](../../cpp/lambda-expression-syntax.md)-Ausdruckssyntax.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C3409 generiert.

```cpp
// C3409.cpp
// compile with: /c
#include <windows.h>
[]   // C3409
class a {};

// OK
[object, uuid("00000000-0000-0000-0000-000000000000")]
__interface x {};

[coclass, uuid("00000000-0000-0000-0000-000000000001")]
class b : public x {};
```

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C3409 generiert, da ein Lambda-Ausdruck die **`mutable`** Spezifikation verwendet, aber keine Parameterliste bereitstellt. Der Compiler kann nicht feststellen, ob die eckigen Klammern Teil der Definition eines Lambda-Ausdrucks oder eines Attribut Blocks sind.

```cpp
// C3409b.cpp

int main()
{
   [] mutable {}();
}
```

## <a name="see-also"></a>Weitere Informationen

[attribute](../../windows/attributes-alphabetical-reference.md)<br/>
[Lambda-Ausdrücke](../../cpp/lambda-expressions-in-cpp.md)<br/>
[Syntax von Lambda Ausdrücken](../../cpp/lambda-expression-syntax.md)
