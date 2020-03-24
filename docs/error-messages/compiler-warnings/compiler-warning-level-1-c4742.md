---
title: Compilerwarnung (Stufe 1) C4742
ms.date: 11/04/2016
f1_keywords:
- C4742
helpviewer_keywords:
- C4742
ms.assetid: e520881d-1eeb-48b1-9df0-8017ee8ba076
ms.openlocfilehash: af97c72f496177d2e94cf18f9685ac33c5e62404
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80185658"
---
# <a name="compiler-warning-level-1-c4742"></a>Compilerwarnung (Stufe 1) C4742

"var" hat eine unterschiedliche Ausrichtung in "file1" und "file2": Anzahl und Zahl

Eine externe Variable, auf die in zwei Dateien verwiesen oder diese definiert wurde, weist in diesen Dateien unterschiedliche Ausrichtung auf. Diese Warnung wird ausgegeben, wenn der Compiler feststellt, dass sich `__alignof` für die Variable in *file1* `__alignof` von der Variablen in *file2*unterscheidet. Dies kann durch die Verwendung nicht kompatibler Typen beim Deklarieren von Variablen in unterschiedlichen Dateien oder durch die Verwendung von nicht übereinstimmenden `#pragma pack` in verschiedenen Dateien verursacht werden.

Um diese Warnung zu beheben, verwenden Sie entweder die gleiche Typdefinition, oder verwenden Sie andere Namen für die Variablen.

Weitere Informationen finden Sie unter [Pack](../../preprocessor/pack.md) -und [__alignof Operator](../../cpp/alignof-operator.md).

## <a name="example"></a>Beispiel

Dies ist die erste Datei, die den Typ definiert.

```c
// C4742a.c
// compile with: /c
struct X {
   char x, y, z, w;
} global;
```

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C4742 generiert.

```c
// C4742b.c
// compile with: C4742a.c /W1 /GL
// C4742 expected
extern struct X {
   int a;
} global;

int main() {
   global.a = 0;
}
```
