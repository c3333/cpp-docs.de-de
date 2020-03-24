---
title: Compilerfehler C3615
ms.date: 10/24/2017
f1_keywords:
- C3615
helpviewer_keywords:
- C3615
ms.assetid: 5ce96ba9-3d31-49f3-9aa8-24e5cdf6dcfc
ms.openlocfilehash: c1a5b6edbc87e14de267cf962dc2b1a71dd6be12
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80200537"
---
# <a name="compiler-error-c3615"></a>Compilerfehler C3615

> die constexpr-Funktion "*Function*" kann keinen konstanten Ausdruck ergeben.

Die Funktions *Funktion* konnte zum Zeitpunkt der Kompilierung nicht als `constexpr` ausgewertet werden. Um `constexpr`zu werden, kann eine Funktion nur andere `constexpr` Funktionen aufzurufen.

## <a name="example"></a>Beispiel

Visual Studio 2017 löst ordnungsgemäß einen Fehler aus, wenn der linke Operand eines bedingt auszuwertenden Vorgangs in einem `constexpr` Kontext nicht gültig ist. Der folgende Code wird in Visual Studio 2015 kompiliert, jedoch nicht in Visual Studio 2017.

```cpp
// C3615.cpp
// Compile with: /c

template<int N>
struct myarray
{
    int size() const { return N; }
};

constexpr bool f(const myarray<1> &arr)
{
    return arr.size() == 10 || arr.size() == 11; // C3615 starting in Visual Studio 2017
}
```

Um dieses Problem zu beheben, deklarieren Sie entweder die `array::size()` Funktion als `constexpr`, oder entfernen Sie den `constexpr` Qualifizierer aus `f`.
