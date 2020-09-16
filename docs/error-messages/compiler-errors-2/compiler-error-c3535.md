---
title: Compilerfehler C3535
ms.date: 11/04/2016
f1_keywords:
- C3535
helpviewer_keywords:
- C3535
ms.assetid: 24449c98-f681-484d-a00b-32533dca3a88
ms.openlocfilehash: 673fe6a8b5eb6dfcd9caa841b18d5b47fb7858bf
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/16/2020
ms.locfileid: "90686089"
---
# <a name="compiler-error-c3535"></a>Compilerfehler C3535

der Typ für "Typ1" kann nicht von "Typ2" abgeleitet werden.

Der Typ der Variablen, die vom- **`auto`** Schlüsselwort deklariert wurde, kann nicht vom Typ des Initialisierungs Ausdrucks abgeleitet werden. Dieser Fehler tritt z. b. auf, wenn der Initialisierungs Ausdruck zu ausgewertet **`void`** wird, der kein-Typ ist.

### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler

1. Stellen Sie sicher, dass der Typ des Initialisierungs Ausdrucks nicht ist **`void`** .

1. Stellen Sie sicher, dass die Deklaration kein Zeiger auf einen grundlegenden Typ ist. Weitere Informationen finden Sie unter [grundlegende Typen](../../cpp/fundamental-types-cpp.md).

1. Stellen Sie sicher, dass der Initialisierungs Ausdruck ein Zeigertyp ist, wenn die Deklaration ein Zeiger auf einen Typ ist.

## <a name="examples"></a>Beispiele

Im folgenden Beispiel wird C3535 erzeugt, da der Initialisierungs Ausdruck als ausgewertet wird **`void`** .

```cpp
// C3535a.cpp
// Compile with /Zc:auto
void f(){}
int main()
{
   auto x = f();   //C3535
   return 0;
}
```

Im folgenden Beispiel wird C3535 erzeugt, da die-Anweisung Variable `x` als Zeiger auf einen abgeleiteten Typ deklariert, aber der Typ des initialisiererausdrucks ist Double. Folglich kann der Compiler den Typ der Variablen nicht ableiten.

```cpp
// C3535b.cpp
// Compile with /Zc:auto
int main()
{
   auto* x = 123.0;   // C3535
   return 0;
}
```

Im folgenden Beispiel wird C3535 erzeugt, da die Variable `p` einen Zeiger auf einen abgeleiteten Typ deklariert, der Initialisierungs Ausdruck jedoch kein Zeigertyp ist.

```cpp
// C3535c.cpp
// Compile with /Zc:auto
class A { };
A x;
auto *p = x;  // C3535
```

## <a name="see-also"></a>Siehe auch

[Auto-Schlüsselwort](../../cpp/auto-keyword.md)<br/>
[Grundlegende Typen](../../cpp/fundamental-types-cpp.md)
