---
title: Compilerfehler C2868
ms.date: 11/04/2016
f1_keywords:
- C2868
helpviewer_keywords:
- C2868
ms.assetid: 6ff5837b-e66d-44d1-9d17-80af35e08d08
ms.openlocfilehash: 0cbcf7dc80aedc554594f88992059f98b7091c21
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80201634"
---
# <a name="compiler-error-c2868"></a>Compilerfehler C2868

> '*Identifier*': unzulässige Syntax für using-Deklaration; qualifizierter Name erwartet

Für eine [using-Deklaration](../../cpp/using-declaration.md) ist ein *qualifizierter Name*, eine Bereichs Operator (`::`) getrennte Sequenz von Namespace-, Klassen-oder Enumerationsnamen erforderlich, die mit dem Bezeichnernamen endet. Ein einzelner Bereichs Auflösungs Operator kann verwendet werden, um einen Namen aus dem globalen Namespace einzuführen.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C2868 generiert und außerdem die korrekte Verwendung veranschaulicht:

```cpp
// C2868.cpp
class X {
public:
   int i;
};

class Y : X {
public:
   using X::i;   // OK
};

int main() {
   using X;   // C2868
}
```
