---
title: Compilerwarnung (Stufe 1) C4742
ms.date: 07/22/2020
f1_keywords:
- C4742
helpviewer_keywords:
- C4742
ms.assetid: e520881d-1eeb-48b1-9df0-8017ee8ba076
ms.openlocfilehash: e6ecd082a9f6d690414761d11d3a0adf101f87c2
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233235"
---
# <a name="compiler-warning-level-1-c4742"></a>Compilerwarnung (Stufe 1) C4742

> "*Variable*" hat eine unterschiedliche Ausrichtung in "*file1*" und "*file2*": *Zahl1* und *Zahl2*

Eine externe Variable, auf die in zwei Dateien verwiesen oder diese definiert wurde, weist in diesen Dateien unterschiedliche Ausrichtung auf.

## <a name="remarks"></a>Bemerkungen

Diese Warnung wird ausgegeben, wenn der Compiler feststellt, dass **`alignof`** für die Variable in *file1* von **`alignof`** der Variablen in *file2*abweicht. Dies kann durch die Verwendung nicht kompatibler Typen beim Deklarieren von Variablen in unterschiedlichen Dateien oder durch Verwendung von nicht übereinstimmenden `#pragma pack` in verschiedenen Dateien verursacht werden.

Um diese Warnung zu beheben, verwenden Sie entweder die gleiche Typdefinition, oder verwenden Sie andere Namen für die Variablen.

Weitere Informationen finden Sie unter [`pack`](../../preprocessor/pack.md) und [ `alignof` Operator](../../cpp/alignof-operator.md).

## <a name="example"></a>Beispiel

Dies ist die erste Datei, die den Typ definiert.

```c
// C4742a.c
// compile with: /c
struct X {
   char x, y, z, w;
} global;
```

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
