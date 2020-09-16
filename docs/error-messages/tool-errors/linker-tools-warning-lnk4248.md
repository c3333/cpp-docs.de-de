---
title: Linkertoolwarnung LNK4248
ms.date: 11/04/2016
f1_keywords:
- LNK4248
helpviewer_keywords:
- LNK4248
ms.assetid: e40523ff-e3cb-4ba6-ab79-23f0f339f6cf
ms.openlocfilehash: 81f3c2abc41673e6e4c9e3f59ff1dd515e1cf365
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/16/2020
ms.locfileid: "90685424"
---
# <a name="linker-tools-warning-lnk4248"></a>Linkertoolwarnung LNK4248

nicht aufgelöstes TypeRef-Token (Token) für ' Typ '; Image kann möglicherweise nicht ausgeführt werden

Ein Typ verfügt nicht über eine Definition in den MSIL-Metadaten.

Linkertoolwarnung LNK4248 kann auftreten, wenn in einem MSIL-Modul (mit **/CLR**kompiliert) nur eine vorwärts Deklaration für einen Typ vorhanden ist, bei der im MSIL-Modul auf den Typ verwiesen wird und das MSIL-Modul mit einem systemeigenen Modul verknüpft ist, das über eine Definition für den Typ verfügt.

In dieser Situation stellt der Linker die Definition des systemeigenen Typs in den MSIL-Metadaten bereit, und dies kann das korrekte Verhalten bereitstellen.

Wenn eine vorwärts-Typdeklaration jedoch ein CLR-Typ ist, ist die native Typdefinition des Linkers möglicherweise nicht korrekt.

Weitere Informationen finden Sie unter [/CLR (Common Language Runtime-Kompilierung)](../../build/reference/clr-common-language-runtime-compilation.md).

### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler

1. Geben Sie die Typdefinition im MSIL-Modul an.

## <a name="examples"></a>Beispiele

Im folgenden Beispiel wird Linkertoolwarnung LNK4248 generiert. Definieren Sie die zu lösende Struktur A.

```cpp
// LNK4248.cpp
// compile with: /clr /W1
// LNK4248 expected
struct A;
void Test(A*){}

int main() {
   Test(0);
}
```

Das folgende Beispiel weist eine vorwärts Definition eines Typs auf.

```cpp
// LNK4248_2.cpp
// compile with: /clr /c
class A;   // provide a definition for A here to resolve
A * newA();
int valueA(A * a);

int main() {
   A * a = newA();
   return valueA(a);
}
```

Im folgenden Beispiel wird Linkertoolwarnung LNK4248 generiert.

```cpp
// LNK4248_3.cpp
// compile with: /c
// post-build command: link LNK4248_2.obj LNK4248_3.obj
class A {
public:
   int b;
};

A* newA() {
   return new A;
}

int valueA(A * a) {
   return (int)a;
}
```
