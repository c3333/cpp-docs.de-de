---
title: Compilerfehler C2362
ms.date: 06/03/2019
f1_keywords:
- C2362
helpviewer_keywords:
- C2362
ms.assetid: 7aafecbc-b3cf-45a6-9ec3-a17e3f222511
ms.openlocfilehash: 330932f53627f8ba09e9e089cec7809eeeb6ab1c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80206075"
---
# <a name="compiler-error-c2362"></a>Compilerfehler C2362

> die Initialisierung von "*Identifier*" wird von "GoTo *Label*" übersprungen.

Beim Kompilieren mit [/Za](../../build/reference/za-ze-disable-language-extensions.md)wird durch einen Sprung zur Bezeichnung verhindert, dass der Bezeichner initialisiert wird.

Sie können nur nach einer Deklaration mit einem Initialisierer springen, wenn die Deklaration in einen nicht eingegebenen Block eingeschlossen ist, oder wenn die Variable bereits initialisiert wurde.

Im folgenden Beispiel wird C2362 generiert:

```cpp
// C2362.cpp
// compile with: /Za
int main() {
   goto label1;
   int i = 1;      // C2362, initialization skipped
label1:;
}
```

Mögliche Lösung:

```cpp
// C2362b.cpp
// compile with: /Za
int main() {
   goto label1;
   {
      int j = 1;   // OK, this block is never entered
   }
label1:;
}
```
