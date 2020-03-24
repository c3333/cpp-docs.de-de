---
title: Compilerfehler C3553
ms.date: 11/04/2016
f1_keywords:
- C3553
helpviewer_keywords:
- C3553
ms.assetid: 7f84bf37-6419-4ad3-ab30-64266100b930
ms.openlocfilehash: 82540e0f6c4b60aea2e708dcf00796490cd7d3cc
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80200654"
---
# <a name="compiler-error-c3553"></a>Compilerfehler C3553

> "decltype" erwartet einen Ausdruck und keinen Typ.

Das `decltype()` -Schlüsselwort benötigt einen Ausdruck als Argument, nicht den Namen eines Typs. Im folgenden Codefragment wird beispielsweise durch die letzte Anweisung der Fehler C3553 verursacht.

```cpp
int x = 0;
decltype(x+1);
decltype(int); // C3553
```
