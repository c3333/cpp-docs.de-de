---
title: Compilerfehler C3850
ms.date: 09/05/2018
f1_keywords:
- C3850
helpviewer_keywords:
- C3850
ms.assetid: 028f3a37-f3ad-4ebc-9168-3cdea47524d4
ms.openlocfilehash: 5de7994e8bf46105e94271ab29bf9e27f1da3e76
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80165562"
---
# <a name="compiler-error-c3850"></a>Compilerfehler C3850

> "*char*": ein universeller Zeichen Name gibt ein ungültiges Zeichen an.

## <a name="remarks"></a>Bemerkungen

Zeichen, die als universelle Zeichennamen dargestellt werden, müssen gültigen Unicode-Codepunkten im Bereich 0-10FFFF entsprechen. Ein universeller Zeichenname darf weder einen Wert im Unicode-Ersatzbereich, D800-DFFF, noch ein codiertes Ersatzzeichenpaar enthalten. Der Compiler generiert das Ersatzpaar automatisch aus einem gültigen Codepunkt.

In Code, der als C kompiliert wird, darf ein universeller Zeichen Name kein Zeichen im Bereich 0000-009F (inklusiv) darstellen, mit Ausnahme von 0024 (' $ '), 0040 ('\@') und 0060 (' ' ').

In Code, der als C++ kompiliert wird, darf für einen universellen Zeichennamen jeder gültige Unicode-Codepunkt in einer Zeichenfolge oder in einem Zeichenliteral verwendet werden. Außerhalb eines Literals darf ein universeller Zeichenname weder Steuerzeichen in den Bereichen 0000-001F und 007F-009F (beide inklusive) oder ein Member des grundlegenden Quellzeichensatzes darstellen.  Weitere Informationen finden Sie unter [Character Sets](../../cpp/character-sets.md).

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C3850 generiert und gezeigt, wie Sie diesen Fehler beheben:

```cpp
// C3850.cpp
int main() {
   int \u0019 = 0;   // C3850, not in allowed range for an identifier
   const wchar_t * wstr_bad  = L"\UD840DC8A"; // C3850, UCN is surrogate pair
   const wchar_t * wstr_good = L"\U0002008A"; // Okay, UCN is valid code point
}
```
