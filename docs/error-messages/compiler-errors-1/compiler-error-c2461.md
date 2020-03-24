---
title: Compilerfehler C2461
ms.date: 11/04/2016
f1_keywords:
- C2461
helpviewer_keywords:
- C2461
ms.assetid: e64ba651-f441-4fdb-b5cb-4209bbbe4db4
ms.openlocfilehash: 3d290bd2288f76d0ddefa2057e3e01c9edc3cbc7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80205321"
---
# <a name="compiler-error-c2461"></a>Compilerfehler C2461

> "*Class*": in der Konstruktorsyntax fehlen formale Parameter.

Der Konstruktor für die-Klasse gibt keine formalen Parameter an. Die Deklaration eines Konstruktors muss eine Liste formaler Parameter angeben. Die Liste kann leer sein.

Um dieses Problem zu beheben, fügen Sie nach der Deklaration der *Klasse*::**Klasse*ein paar Klammern hinzu.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird gezeigt, wie C2461 behoben wird:

```cpp
// C2461.cpp
// compile with: /c
class C {
   C::C;     // C2461
   C::C();   // OK
};
```
