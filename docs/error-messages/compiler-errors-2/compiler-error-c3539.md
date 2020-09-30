---
title: Compilerfehler C3539
ms.date: 11/04/2016
f1_keywords:
- C3539
helpviewer_keywords:
- C3539
ms.assetid: 34a33a0f-d1b6-498f-b312-ffad2d4799b3
ms.openlocfilehash: e30ea0713229bfd8da395baef710571f8dfd49e9
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91508146"
---
# <a name="compiler-error-c3539"></a>Compilerfehler C3539

"Typ": ein Vorlagen Argument kann kein Typ sein, der "Auto" enthält.

Der dargestellte Vorlagen Argumenttyp darf keine Verwendung des- **`auto`** Schlüssel Worts enthalten.

### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler

1. Geben Sie das Vorlagen Argument nicht mit dem **`auto`** Schlüsselwort an.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C3539 erzeugt.

```cpp
// C3539.cpp
// Compile with /Zc:auto
template<class T> class C{};
int main()
{
   C<auto> c;   // C3539
   return 0;
}
```

## <a name="see-also"></a>Siehe auch

[Auto-Schlüsselwort](../../cpp/auto-cpp.md)
