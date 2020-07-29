---
title: Compilerfehler C3532
ms.date: 11/04/2016
f1_keywords:
- C3532
helpviewer_keywords:
- C3532
ms.assetid: 51067853-eda8-4f59-86e8-8924e16d3a95
ms.openlocfilehash: e2329111e916df9eac99d156bcf58a58e148cb08
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228816"
---
# <a name="compiler-error-c3532"></a>Compilerfehler C3532

"Typ": falsche Verwendung von "Auto"

Der angegebenen Typ kann nicht mit dem- **`auto`** Schlüsselwort deklariert werden. Beispielsweise können Sie das- **`auto`** Schlüsselwort nicht verwenden, um ein Array oder einen Methoden Rückgabetyp zu deklarieren.

### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler

1. Stellen Sie sicher, dass der Initialisierungs Ausdruck einen gültigen Typ ergibt.

1. Stellen Sie sicher, dass Sie kein Array oder Methoden Rückgabetyp deklarieren.

## <a name="example"></a>Beispiel

Das folgende Beispiel ergibt C3532, da das- **`auto`** Schlüsselwort keinen Methoden Rückgabetyp deklarieren kann.

```cpp
// C3532a.cpp
// Compile with /Zc:auto
auto f(){}   // C3532
```

## <a name="example"></a>Beispiel

Das folgende Beispiel ergibt C3532, da das- **`auto`** Schlüsselwort kein Array deklarieren kann.

```cpp
// C3532b.cpp
// Compile with /Zc:auto
int main()
{
   int x[5];
   auto a[5];            // C3532
   auto b[1][2];         // C3532
   auto y[5] = x;        // C3532
   auto z[] = {1, 2, 3}; // C3532
   auto w[] = x;         // C3532
   return 0;
}
```

## <a name="see-also"></a>Siehe auch

[Auto-Schlüsselwort](../../cpp/auto-keyword.md)
