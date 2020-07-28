---
title: Compilerfehler C3491
ms.date: 11/04/2016
f1_keywords:
- C3491
helpviewer_keywords:
- C3491
ms.assetid: 7f0e71b2-46a0-4d25-bd09-6158a280f509
ms.openlocfilehash: f6f20d9af424fdd4254fc15e0580d62b9dfba144
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87184474"
---
# <a name="compiler-error-c3491"></a>Compilerfehler C3491

"Var": Eine Erfassung nach Wert kann in einem nicht änderbaren Lambda nicht geändert werden.

Ein nicht änderbarer Lambda-Ausdruck kann den Wert einer Variablen nicht ändern, die nach Wert erfasst wird.

### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler

- Deklarieren Sie den Lambda Ausdruck mit dem- **`mutable`** Schlüsselwort, oder

- übergeben Sie die Variable per Verweis an die Erfassungsliste des Lambda-Ausdrucks.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C3491 generiert, da der Text eines nicht änderbaren Lambda-Ausdrucks die Erfassungsvariable `m`ändert:

```cpp
// C3491a.cpp

int main()
{
   int m = 55;
   [m](int n) { m = n; }(99); // C3491
}
```

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C3491 aufgelöst, indem der Lambda-Ausdruck mit dem- **`mutable`** Schlüsselwort deklariert wird:

```cpp
// C3491b.cpp

int main()
{
   int m = 55;
   [m](int n) mutable { m = n; }(99);
}
```

## <a name="see-also"></a>Weitere Informationen

[Lambda-Ausdrücke](../../cpp/lambda-expressions-in-cpp.md)
