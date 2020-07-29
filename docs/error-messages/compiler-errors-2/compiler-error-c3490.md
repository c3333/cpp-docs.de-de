---
title: Compilerfehler C3490
ms.date: 11/04/2016
f1_keywords:
- C3490
helpviewer_keywords:
- C3490
ms.assetid: 7638559a-fd06-4527-a9c1-0c8ae68b3123
ms.openlocfilehash: ea7341b9c587a764c7366fa7b7c89e4fc67bc7d8
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230856"
---
# <a name="compiler-error-c3490"></a>Compilerfehler C3490

"var" kann nicht geändert werden, da über ein Konstantenobjekt darauf zugegriffen wird

Ein Lambda-Ausdruck, der in einer Methode deklariert ist, **`const`** kann keine änderbaren Elementdaten ändern.

### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler

- Entfernen Sie den- **`const`** Modifizierer aus der Methoden Deklaration.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C3490 generiert, da die Element Variable `_i` in einer Methode geändert wird **`const`** :

```cpp
// C3490a.cpp
// compile with: /c

class C
{
   void f() const
   {
      auto x = [=]() { _i = 20; }; // C3490
   }

   int _i;
};
```

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C3490 durch Entfernen des- **`const`** Modifizierers aus der Methoden Deklaration aufgelöst:

```cpp
// C3490b.cpp
// compile with: /c

class C
{
   void f()
   {
      auto x = [=]() { _i = 20; };
   }

   int _i;
};
```

## <a name="see-also"></a>Siehe auch

[Lambda-Ausdrücke](../../cpp/lambda-expressions-in-cpp.md)
