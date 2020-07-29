---
title: Compilerwarnung (Stufe 4) C4232
ms.date: 11/04/2016
f1_keywords:
- C4232
helpviewer_keywords:
- C4232
ms.assetid: f92028a5-4ddd-43c1-97f5-4f724e5e14af
ms.openlocfilehash: 6081acc4a64394c9122650da8b7f4147f724e5de
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219923"
---
# <a name="compiler-warning-level-4-c4232"></a>Compilerwarnung (Stufe 4) C4232

nicht dem Standard entsprechende Erweiterung: "Bezeichner": die Adresse von DllImport "DllImport" ist nicht statisch, Identität nicht garantiert.

Unter Microsoft Extensions (/Ze) können Sie einen nicht statischen Wert als Adresse einer Funktion angeben, die mit dem- **`dllimport`** Modifizierer deklariert wird. Unter ANSI Compatibility ([/Za](../../build/reference/za-ze-disable-language-extensions.md)) verursacht dies einen Fehler.

Im folgenden Beispiel wird C4232 generiert:

```c
// C4232.c
// compile with: /W4 /Ze /c
int __declspec(dllimport) f();
int (*pfunc)() = &f;   // C4232
```
