---
title: Compilerfehler C3490
ms.date: 11/04/2016
f1_keywords:
- C3490
helpviewer_keywords:
- C3490
ms.assetid: 7638559a-fd06-4527-a9c1-0c8ae68b3123
ms.openlocfilehash: 76729f49358e2a05b425730517e88ba14f2909c6
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/16/2020
ms.locfileid: "90685723"
---
# <a name="compiler-error-c3490"></a>Compilerfehler C3490

"var" kann nicht geändert werden, da über ein Konstantenobjekt darauf zugegriffen wird

Ein Lambda-Ausdruck, der in einer Methode deklariert ist, **`const`** kann keine änderbaren Elementdaten ändern.

### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler

- Entfernen Sie den- **`const`** Modifizierer aus der Methoden Deklaration.

## <a name="examples"></a>Beispiele

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
