---
title: Compilerwarnung (Stufe 1) C4176
ms.date: 11/04/2016
f1_keywords:
- C4176
helpviewer_keywords:
- C4176
ms.assetid: cfffb934-219a-4a63-9df6-ba54405bf766
ms.openlocfilehash: e7efe17b9840179bd21a432c2654fadd7e9230c6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80199991"
---
# <a name="compiler-warning-level-1-c4176"></a>Compilerwarnung (Stufe 1) C4176

"Subcomponent": Unbekannte Unterkomponente bei #pragma component browser.

#pragma **component** enthält eine ungültige Unterkomponente. Um Verweise auf einen bestimmten Namen auszuschließen, müssen Sie die Option **references** vor dem Namen verwenden.

## <a name="example"></a>Beispiel

```cpp
// C4176.cpp
// compile with: /W1 /LD
#pragma component(browser, off, i)  // C4176
#pragma component(browser, off, references, i) // ok
```
