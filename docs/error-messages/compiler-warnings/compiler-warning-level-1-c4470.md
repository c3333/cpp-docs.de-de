---
title: Compilerwarnung (Stufe 1) C4470
ms.date: 11/04/2016
f1_keywords:
- C4470
helpviewer_keywords:
- C4470
ms.assetid: f52a3eaa-a235-4747-a47d-9ec4ad4cb0ea
ms.openlocfilehash: 164bc1fa85466b80ee66a22a1a1679a40b89ce2e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80186724"
---
# <a name="compiler-warning-level-1-c4470"></a>Compilerwarnung (Stufe 1) C4470

in/CLR werden die Pragmas für Gleit Komma Steuerelemente ignoriert.

Die float-Control-Pragmas:

- [fenv_access](../../preprocessor/fenv-access.md)

- [float_control](../../preprocessor/float-control.md)

- [fp_contract](../../preprocessor/fp-contract.md)

keine Auswirkung unter [/CLR](../../build/reference/clr-common-language-runtime-compilation.md).

Im folgenden Beispiel wird C4470 generiert:

```cpp
// C4470.cpp
// compile with: /clr /W1 /LD
#pragma float_control(except, on)   // C4470
```
