---
title: Compilerfehler C2144
ms.date: 11/04/2016
f1_keywords:
- C2144
helpviewer_keywords:
- C2144
ms.assetid: 49f3959b-324f-4c06-9588-c0ecef5dc5b3
ms.openlocfilehash: b917c0a2c15aeb70222c948bce9a6fb275c91068
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80207245"
---
# <a name="compiler-error-c2144"></a>Compilerfehler C2144

> Syntax Fehler: '*Type*' sollte '*Token*' vorangestellt sein.

Der Compiler hat stattdessen das *Token* und den gefundenen *Typ* erwartet.

Dieser Fehler kann durch eine fehlende schließende geschweifte Klammer, eine Rechte Klammer oder ein Semikolon verursacht werden.

C2144 kann auch auftreten, wenn Sie versuchen, ein Makro von einem CLR-Schlüsselwort zu erstellen, das ein Leerzeichen enthält.

Möglicherweise wird auch C2144 angezeigt, wenn Sie versuchen, eine Typweiterleitung durchzuführen. Weitere Informationen finden Sie unter [Typweiterleitung (C++/CLI)](../../extensions/type-forwarding-cpp-cli.md) .

## <a name="examples"></a>Beispiele

Im folgenden Beispiel wird C2144 generiert, und es wird eine Möglichkeit gezeigt, Sie zu beheben:

```cpp
// C2144.cpp
// compile with: /clr /c
#define REF ref
REF struct MyStruct0;   // C2144

// OK
#define REF1 ref struct
REF1 MyStruct1;
```

Im folgenden Beispiel wird C2144 generiert, und es wird eine Möglichkeit gezeigt, Sie zu beheben:

```cpp
// C2144_2.cpp
// compile with: /clr /c
ref struct X {

   property double MultiDimProp[,,] {   // C2144
   // try the following line instead
   // property double MultiDimProp[int , int, int] {
      double get(int, int, int) { return 1; }
      void set(int i, int j, int k, double l) {}
   }

   property double MultiDimProp2[] {   // C2144
   // try the following line instead
   // property double MultiDimProp2[int] {
      double get(int) { return 1; }
      void set(int i, double l) {}
   }
};
```
