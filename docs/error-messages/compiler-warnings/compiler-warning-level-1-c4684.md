---
title: Compilerwarnung (Stufe 1) C4684
ms.date: 11/04/2016
f1_keywords:
- C4684
helpviewer_keywords:
- C4684
ms.assetid: e95f1a83-2784-4b05-ae94-12148e056e26
ms.openlocfilehash: 017d2ad9ac327e99bdd9afb0914d17946103771c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175453"
---
# <a name="compiler-warning-level-1-c4684"></a>Compilerwarnung (Stufe 1) C4684

' Attribut ': Warnung! das Attribut kann eine ungültige Codegenerierung verursachen: Verwendung mit Vorsicht.

Sie haben ein Attribut verwendet, das nicht häufig verwendet werden sollte.

Im folgenden Beispiel wird C4684 generiert:

```cpp
// C4684.cpp
// compile with: /W1 /LD
[module(name="xx")]; // C4684 expected
[no_injected_text];
```
