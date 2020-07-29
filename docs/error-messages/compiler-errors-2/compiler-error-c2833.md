---
title: Compilerfehler C2833
ms.date: 11/04/2016
f1_keywords:
- C2833
helpviewer_keywords:
- C2833
ms.assetid: b9418ce1-e2ee-4599-8959-6fde89c27569
ms.openlocfilehash: a6ffcb13d04f3c7c5ac62e147a2b6b2b305e11e1
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218168"
---
# <a name="compiler-error-c2833"></a>Compilerfehler C2833

> "Operator *Operator-Name*" ist kein bekannter Operator oder Typ.

Auf das Wort **`operator`** muss ein *Operator Name* folgen, den Sie überschreiben möchten, oder auf einen Typ, den Sie konvertieren möchten.

Eine Liste der Operatoren, die Sie in einem verwalteten Typ definieren können, finden Sie unter [benutzerdefinierte Operatoren](../../dotnet/user-defined-operators-cpp-cli.md).

Im folgenden Beispiel wird C2833 generiert:

```cpp
// C2833.cpp
// compile with: /c
class A {};

void operator ::* ();   // C2833
void operator :: ();   // OK
```
