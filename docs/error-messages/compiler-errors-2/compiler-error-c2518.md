---
title: Compilerfehler C2518
ms.date: 11/04/2016
f1_keywords:
- C2518
helpviewer_keywords:
- C2518
ms.assetid: a7895b47-da90-4851-ac97-18e81479595a
ms.openlocfilehash: 315edc3124b4cdd425ce9d7581167366d3831512
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214645"
---
# <a name="compiler-error-c2518"></a>Compilerfehler C2518

Das Schlüsselwort ' Schlüsselwort ' ist in der Basisklassen Liste ungültig. erten

Die Schlüsselwörter **`class`** und **`struct`** sollten nicht in einer Basisklassen Liste angezeigt werden.

Im folgenden Beispiel wird C2518 generiert:

```cpp
// C2518.cpp
// compile with: /c
class B {};
class C : public class B {};   // C2518
class D: public B {};   // OK
```
