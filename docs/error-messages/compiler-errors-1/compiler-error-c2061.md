---
title: Compilerfehler C2061
ms.date: 11/04/2016
f1_keywords:
- C2061
helpviewer_keywords:
- C2061
ms.assetid: b0e61c0c-a205-4820-b9aa-301d6c6fe6eb
ms.openlocfilehash: 1e1b13960c84d4e03c6316c451c690f8b5a6236e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212864"
---
# <a name="compiler-error-c2061"></a>Compilerfehler C2061

Syntax Fehler: Bezeichner "Bezeichner"

Der Compiler hat einen Bezeichner gefunden, der nicht erwartet wurde. Stellen Sie sicher, dass `identifier` deklariert ist, bevor Sie Sie verwenden.

Ein Initialisierer kann in Klammern eingeschlossen werden. Um dieses Problem zu vermeiden, schließen Sie den Deklarator in Klammern ein, oder erstellen Sie ihn als **`typedef`** .

Dieser Fehler kann auch verursacht werden, wenn der Compiler einen Ausdruck als Klassen Vorlagen Argument erkennt. Verwenden Sie [Typname](../../cpp/typename.md) , um dem Compiler mitzuteilen, dass es sich um einen-Typ handelt.

Im folgenden Beispiel wird C2061 generiert:

```cpp
// C2061.cpp
// compile with: /c
template < A a >   // C2061
// try the following line instead
// template < typename b >
class c{};
```

C2061 kann auftreten, wenn Sie einen Instanznamen an [typeid](../../extensions/typeid-cpp-component-extensions.md)übergeben:

```cpp
// C2061b.cpp
// compile with: /clr
ref struct G {
   int i;
};

int main() {
   G ^ pG = gcnew G;
   System::Type ^ pType = typeid<pG>;   // C2061
   System::Type ^ pType2 = typeid<G>;   // OK
}
```
