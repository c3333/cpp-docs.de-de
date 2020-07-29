---
title: Compilerfehler C3615
ms.date: 10/24/2017
f1_keywords:
- C3615
helpviewer_keywords:
- C3615
ms.assetid: 5ce96ba9-3d31-49f3-9aa8-24e5cdf6dcfc
ms.openlocfilehash: 17a210e2a514af1ffd62bf38651c4d17bd1fe32b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230791"
---
# <a name="compiler-error-c3615"></a>Compilerfehler C3615

> die constexpr-Funktion "*Function*" kann keinen konstanten Ausdruck ergeben.

Die Funktions *Funktion* konnte nicht als zum Zeitpunkt der **`constexpr`** Kompilierung ausgewertet werden. Dazu **`constexpr`** kann eine Funktion nur andere Funktionen aufzurufen **`constexpr`** .

## <a name="example"></a>Beispiel

Visual Studio 2017 löst ordnungsgemäß einen Fehler aus, wenn der linke Operand eines bedingt auszuwertenden Vorgangs in einem Kontext nicht gültig ist **`constexpr`** . Der folgende Code wird in Visual Studio 2015 kompiliert, jedoch nicht in Visual Studio 2017.

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

Um dieses Problem zu beheben, deklarieren Sie entweder die `array::size()` Funktion als, **`constexpr`** oder entfernen Sie den **`constexpr`** Qualifizierer aus `f` .
