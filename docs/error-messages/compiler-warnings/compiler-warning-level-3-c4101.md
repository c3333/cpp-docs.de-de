---
title: Compilerwarnung (Stufe 3) C4101
ms.date: 11/04/2016
f1_keywords:
- C4101
helpviewer_keywords:
- C4101
ms.assetid: d98563cd-9dce-4aae-8f12-bd552a4ea677
ms.openlocfilehash: f9d3875fdc17def1e7d3bcb72149c5faf90f656a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220053"
---
# <a name="compiler-warning-level-3-c4101"></a>Compilerwarnung (Stufe 3) C4101

"Bezeichner": nicht referenzierte lokale Variable

Die lokale Variable wird nie verwendet. Diese Warnung wird in der offensichtlichen Situation angezeigt:

```cpp
// C4101a.cpp
// compile with: /W3
int main() {
int i;   // C4101
}
```

Diese Warnung tritt jedoch auch auf, wenn eine **`static`** Member-Funktion über eine Instanz der-Klasse aufgerufen wird:

```cpp
// C4101b.cpp
// compile with:  /W3
struct S {
   static int func()
   {
      return 1;
   }
};

int main() {
   S si;   // C4101, si is never used
   int y = si.func();
   return y;
}
```

In diesem Fall verwendet der Compiler Informationen zum `si` Zugriff auf die **`static`** Funktion, aber die Instanz der Klasse ist nicht erforderlich, um die Funktion aufzurufen **`static`** . Daher ist die Warnung. Um diese Warnung zu beheben, können Sie folgende Aktionen ausführen:

- Fügen Sie einen Konstruktor hinzu, in dem der Compiler die Instanz von im-Befehl verwenden würde `si` `func` .

- Entfernen Sie das- **`static`** Schlüsselwort aus der Definition von `func` .

- Explizites aufzurufen der **`static`** Funktion: `int y = S::func();` .
