---
title: Compilerwarnung (Stufe 4) C4062
ms.date: 04/05/2019
f1_keywords:
- C4062
helpviewer_keywords:
- C4062
ms.assetid: 36d1c6ae-c917-4b08-bf30-2eb49ee94169
ms.openlocfilehash: efe021c9994e20f2630e31537bcc6099783b4308
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220001"
---
# <a name="compiler-warning-level-4-c4062"></a>Compilerwarnung (Stufe 4) C4062

> Enumerator '*Identifier*' in Switch of Enumeration '*Enumeration*' wird nicht verarbeitet

Der enumeratorbezeichner weist keinen zugeordneten *identifier* `case` Handler in einer **`switch`** -Anweisung auf, und es gibt keine Bezeichnung, **`default`** die ihn abfangen kann. Der fehlende Fall ist möglicherweise eine Überwachung und ein potenzieller Fehler in Ihrem Code. Eine verwandte Warnung zu nicht verwendeten Enumeratoren in- **`switch`** Anweisungen, die einen **`default`** Fall aufweisen, finden Sie unter [C4061](compiler-warning-level-4-c4061.md).

Diese Warnung ist standardmäßig deaktiviert. Weitere Informationen zum Aktivieren von Warnungen, die standardmäßig deaktiviert sind, finden Sie unter [standardmäßig](../../preprocessor/compiler-warnings-that-are-off-by-default.md)deaktivierte Compilerwarnungen.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C4062 generiert und gezeigt, wie Sie diesen Fehler beheben:

```cpp
// C4062.cpp
// compile with: /EHsc /W4
#pragma warning(default : 4062)
enum E { a, b, c };
void func ( E e ) {
   switch(e) {
      case a:
      case b:
   // case c:  // to fix, uncomment this line
      break;   // no default label
   }   // C4062, enumerator 'c' not handled
}

int main() {
}
```

## <a name="see-also"></a>Weitere Informationen

[Compilerwarnung (Stufe 4) C4061](compiler-warning-level-4-c4061.md)
