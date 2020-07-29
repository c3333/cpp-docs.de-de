---
title: Compilerfehler C2632
ms.date: 11/04/2016
f1_keywords:
- C2632
helpviewer_keywords:
- C2632
ms.assetid: b15a6b1b-42d2-4e1b-8660-e6bfde61052d
ms.openlocfilehash: 8ea3a106e8819bf067203f220ca51e17b87bfe46
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225461"
---
# <a name="compiler-error-c2632"></a>Compilerfehler C2632

"Typ1" gefolgt von "Typ2" ist unzulässig.

Dieser Fehler kann verursacht werden, wenn ein Code zwischen zwei typspezifibezeichmern fehlt.

Im folgenden Beispiel wird C2632 generiert:

```cpp
// C2632.cpp
int float i;   // C2632
```

Dieser Fehler kann auch infolge einer compilerübereinstimmungs-Arbeit generiert werden, die für Visual Studio .NET 2003 durchgeführt wurde. **`bool`** ist nun ein geeigneter Typ. In früheren Versionen **`bool`** war eine typedef, und Sie konnten Bezeichner mit diesem Namen erstellen.

Im folgenden Beispiel wird C2632 generiert:

```cpp
// C2632_2.cpp
// compile with: /LD
void f(int bool);   // C2632
```

Um diesen Fehler zu beheben, sodass der Code sowohl in der Visual Studio .NET 2003-als auch in der Visual Studio .NET-Version von Visual C++ gültig ist, benennen Sie den Bezeichner um.
