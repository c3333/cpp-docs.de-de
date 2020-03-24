---
title: Compilerwarnung (Stufe 4) C4232
ms.date: 11/04/2016
f1_keywords:
- C4232
helpviewer_keywords:
- C4232
ms.assetid: f92028a5-4ddd-43c1-97f5-4f724e5e14af
ms.openlocfilehash: c0e79dfa4564960a5660f0932b142b436370ac05
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80173919"
---
# <a name="compiler-warning-level-4-c4232"></a>Compilerwarnung (Stufe 4) C4232

nicht dem Standard entsprechende Erweiterung: "Bezeichner": die Adresse von DllImport "DllImport" ist nicht statisch, Identität nicht garantiert.

Unter Microsoft Extensions (/Ze) können Sie einen nicht statischen Wert als Adresse einer Funktion angeben, die mit dem **DllImport** -Modifizierer deklariert wird. Unter ANSI Compatibility ([/Za](../../build/reference/za-ze-disable-language-extensions.md)) verursacht dies einen Fehler.

Im folgenden Beispiel wird C4232 generiert:

```c
// C4232.c
// compile with: /W4 /Ze /c
int __declspec(dllimport) f();
int (*pfunc)() = &f;   // C4232
```
