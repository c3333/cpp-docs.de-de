---
title: Compilerfehler C3492
ms.date: 11/04/2016
f1_keywords:
- C3492
helpviewer_keywords:
- C3492
ms.assetid: b1dc6342-9133-4b1f-a9c3-e8c65d20d121
ms.openlocfilehash: bdaeb8797eb71b205f737d08e74430f161cb8caa
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/16/2020
ms.locfileid: "90686547"
---
# <a name="compiler-error-c3492"></a>Compilerfehler C3492

'var': Ein Member einer anonymen Union kann nicht erfasst werden.

Sie können ein Member einer unbenannten Union nicht erfassen.

### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler

- Weisen Sie der Union einen Namen zu, und übergeben Sie die vollständige Union-Struktur an die Erfassungsliste des Lambdaausdrucks.

## <a name="examples"></a>Beispiele

Im folgenden Beispiel wird C3492 generiert, da ein Member einer anonymen Union erfasst wird:

```cpp
// C3492a.cpp

int main()
{
   union
   {
      char ch;
      int x;
   };

   ch = 'y';
   [&x](char ch) { x = ch; }(ch); // C3492
}
```

Im folgenden Beispiel wird C3492 behoben, indem der Union ein Name zugewiesen und die vollständige Union-Struktur an die Erfassungsliste des Lambdaausdrucks übergeben wird.

```cpp
// C3492b.cpp

int main()
{
   union
   {
      char ch;
      int x;
   } u;

   u.ch = 'y';
   [&u](char ch) { u.x = ch; }(u.ch);
}
```

## <a name="see-also"></a>Siehe auch

[Lambda-Ausdrücke](../../cpp/lambda-expressions-in-cpp.md)
