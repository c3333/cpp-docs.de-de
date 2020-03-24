---
title: Compilerwarnung (Stufe 3) C4101
ms.date: 11/04/2016
f1_keywords:
- C4101
helpviewer_keywords:
- C4101
ms.assetid: d98563cd-9dce-4aae-8f12-bd552a4ea677
ms.openlocfilehash: 0ac34fbaf4cbb54583394dff5b8645fe56b8b9cd
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80199044"
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

Diese Warnung tritt jedoch auch beim Aufrufen einer **statischen** Element Funktion durch eine Instanz der-Klasse auf:

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

In diesem Fall verwendet der Compiler Informationen zu `si`, um auf die **statische** Funktion zuzugreifen, aber die Instanz der Klasse ist nicht erforderlich, um die **statische** Funktion aufzurufen. Daher wird die Warnung angezeigt. Um diese Warnung zu beheben, können Sie folgende Aktionen ausführen:

- Fügen Sie einen Konstruktor hinzu, in dem der Compiler die Instanz von `si` im Aufruf`func`verwendet.

- Entfernen Sie das **static** -Schlüsselwort aus der Definition von `func`.

- Explizites Abrufen der **statischen** Funktion: `int y = S::func();`.
