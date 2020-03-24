---
title: Compilerwarnung (Stufe 1) C4002
ms.date: 11/04/2016
f1_keywords:
- C4002
helpviewer_keywords:
- C4002
ms.assetid: 6bda1dfe-e2e4-4771-9794-5a404c466dd5
ms.openlocfilehash: cb1e36a606f5c8bb0a1622260d64124264f0db32
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80164767"
---
# <a name="compiler-warning-level-1-c4002"></a>Compilerwarnung (Stufe 1) C4002

Zu viele übergebene Parameter für das Makro "Bezeichner"

Die Anzahl der tatsächlich im Makro enthaltenen Parameter überschreitet die Anzahl der formalen Parameter in der Makrodefinition. Der Präprozessor erfasst die zusätzlichen Parameter, aber ignoriert diese bei der Makroerweiterung.

C4002 kann bei falscher Verwendung von [Variadic Macros](../../preprocessor/variadic-macros.md)auftreten.

Im folgenden Beispiel wird C4002 generiert:

```cpp
// C4002.cpp
// compile with: /W1
#define test(a) (a)

int main() {
   int a = 1;
   int b = 2;
   a = test(a,b);   // C4002
   // try..
   a = test(a);
}
```

Dieser Fehler kann auch infolge einer Konformitätsverbesserung für Compiler für Visual Studio .NET 2003 auftreten: Zusätzliche Kommas in Makros werden nicht mehr akzeptiert.

Zusätzliche Kommas in Makros werden vom Compiler nicht mehr akzeptiert. Entfernen Sie zusätzliche Kommas, damit der Code in den Visual Studio .NET 2003- und Visual Studio .NET-Versionen von Visual C++ gültig ist.

```cpp
// C4002b.cpp
// compile with: /W1
#define F(x,y)
int main()
{
   F(2,,,,,,3,,,,,,)   // C4002
   // Try the following line instead:
   // F(2,3)
}
```
