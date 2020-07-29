---
title: Compilerwarnung (Stufe 4) C4061
ms.date: 04/05/2019
f1_keywords:
- C4061
helpviewer_keywords:
- C4061
ms.assetid: a99cf88e-7941-4519-8b1b-f6889d914b2f
ms.openlocfilehash: 18c5a51e24af36c5a330e10a66ce3dcc38295fb1
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225279"
---
# <a name="compiler-warning-level-4-c4061"></a>Compilerwarnung (Stufe 4) C4061

> Enumerator '*Identifier*' in Switch of Enumeration '*Enumeration*' wird nicht explizit von einer Case-Bezeichnung behandelt.

Der angegebene enumeratorbezeichner weist keinen zugeordneten Handler in einer-Anweisung auf *identifier* **`switch`** , die einen-Wert aufweist **`default`** . Der fehlende Fall ist möglicherweise ein Problem, oder es handelt sich nicht um ein Problem. Dies hängt möglicherweise davon ab, ob der Enumerator vom Standardfall behandelt wird oder nicht. Eine verwandte Warnung zu nicht verwendeten Enumeratoren in- **`switch`** Anweisungen, die keine groß- **`default`** /Kleinschreibung aufweisen, finden Sie unter [C4062](compiler-warning-level-4-c4062.md).

Diese Warnung ist standardmäßig deaktiviert. Weitere Informationen zum Aktivieren von Warnungen, die standardmäßig deaktiviert sind, finden Sie unter [standardmäßig](../../preprocessor/compiler-warnings-that-are-off-by-default.md)deaktivierte Compilerwarnungen.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C4061 generiert. Fügen Sie einen Fall für den fehlenden Enumerator hinzu, um den Fehler zu beheben:

```cpp
// C4061.cpp
// compile with: /W4
#pragma warning(default : 4061)

enum E { a, b, c };
void func ( E e )
{
   switch(e)
   {
      case a:
      case b:
      default:
         break;
   }   // C4061 c' not handled
}

int main()
{
}
```

## <a name="see-also"></a>Siehe auch

[Compilerwarnung (Stufe 4) C4062](compiler-warning-level-4-c4062.md)
