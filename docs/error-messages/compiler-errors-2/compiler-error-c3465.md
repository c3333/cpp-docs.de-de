---
title: Compilerfehler C3465
ms.date: 11/04/2016
f1_keywords:
- C3465
helpviewer_keywords:
- C3465
ms.assetid: aeb815e5-b3fc-4525-afe2-d738e9321df1
ms.openlocfilehash: 56eeac18d5b8efc32501bf54e2de3aa216e05a13
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/17/2020
ms.locfileid: "90742020"
---
# <a name="compiler-error-c3465"></a>Compilerfehler C3465

Um den Typ 'typ' zu verwenden, müssen Sie auf die Assembly 'assembly' verweisen.

Typweiterleitung funktioniert im Fall einer Clientanwendung bis zur erneuten Kompilierung des Clients. Bei der erneuten Kompilierung benötigen Sie einen Verweis auf jede Assembly, die die Definition eines in Ihrer Clientanwendung verwendeten Typs enthält.

Weitere Informationen finden Sie unter [Typweiterleitung (C++/CLI)](../../extensions/type-forwarding-cpp-cli.md).

## <a name="examples"></a>Beispiele

Das folgende Beispiel erstellt eine Assembly, die den neuen Speicherort eines Typs enthält.

```cpp
// C3465.cpp
// compile with: /clr /LD
public ref class R {
public:
   ref class N {};
};
```

Im folgenden Beispiel wird eine Assembly erstellt, die ursprünglich die Definition des Typs enthielt, jetzt jedoch Weiterleitungssyntax für den Typ enthält.

```cpp
// C3465_b.cpp
// compile with: /clr /LD
#using "C3465.dll"
[ assembly:TypeForwardedTo(R::typeid) ];
```

Im folgenden Beispiel wird C3465 generiert:

```cpp
// C3465_c.cpp
// compile with: /clr
// C3465 expected
#using "C3465_b.dll"
// Uncomment the following line to resolve.
// #using "C3465.dll"

int main() {
   R^ r = gcnew R();
}
```
