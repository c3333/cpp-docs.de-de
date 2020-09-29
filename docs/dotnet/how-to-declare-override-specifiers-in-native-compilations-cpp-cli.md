---
title: 'Vorgehensweise: Deklarieren von Überschreibungsspezifizierer (C++/CLI)'
ms.date: 11/04/2016
helpviewer_keywords:
- override specifiers in native compilation, overriding
ms.assetid: d0551836-9ac7-41eb-a6e9-a4b3ef60767d
ms.openlocfilehash: 92bdc41cf9ebe2389f2d22dab211029899283266
ms.sourcegitcommit: 94893973211d0b254c8bcdcf0779997dcc136b0c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/28/2020
ms.locfileid: "91414593"
---
# <a name="how-to-declare-override-specifiers-in-native-compilations-ccli"></a>Gewusst wie: Deklarieren von Überschreibungsbezeichnern in nativen Kompilierungen (C++/CLI)

[sealed](../extensions/sealed-cpp-component-extensions.md), [abstract](../extensions/abstract-cpp-component-extensions.md)und [override](../extensions/override-cpp-component-extensions.md) sind in Kompilierungen verfügbar, die nicht **/ZW** oder [/CLR](../build/reference/clr-common-language-runtime-compilation.md)verwenden.

> [!NOTE]
> Die ISO c++ 11-Standard Sprache verfügt über den [Überschreibungs](../cpp/override-specifier.md) Bezeichner und den [endgültigen](../cpp/final-specifier.md) Bezeichner. beide werden in Visual Studio `final` anstelle von in Code unterstützt, der **`sealed`** als System eigen reine Kompilierung verwendet werden soll.

## <a name="example-sealed-is-valid"></a>Beispiel: versiegelt ist gültig.

### <a name="description"></a>BESCHREIBUNG

Das folgende Beispiel zeigt, dass in systemeigenen **`sealed`** Kompilierungen gültig ist.

### <a name="code"></a>Code

```cpp
// sealed_native_keyword.cpp
#include <stdio.h>
__interface I1 {
   virtual void f();
   virtual void g();
};

class X : public I1 {
public:
   virtual void g() sealed {}
};

class Y : public X {
public:

   // the following override generates a compiler error
   virtual void g() {}   // C3248 X::g is sealed!
};
```

## <a name="example-override-is-valid"></a>Beispiel: außer Kraft Setzung ist gültig

### <a name="description"></a>BESCHREIBUNG

Das nächste Beispiel zeigt, dass in systemeigenen `override` Kompilierungen gültig ist.

### <a name="code"></a>Code

```cpp
// override_native_keyword.cpp
#include <stdio.h>
__interface I1 {
   virtual void f();
};

class X : public I1 {
public:
   virtual void f() override {}   // OK
   virtual void g() override {}   // C3668 I1::g does not exist
};
```

## <a name="example-abstract-is-valid"></a>Beispiel: abstract ist gültig.

### <a name="description"></a>BESCHREIBUNG

Dieses Beispiel zeigt, dass in systemeigenen **`abstract`** Kompilierungen gültig ist.

### <a name="code"></a>Code

```cpp
// abstract_native_keyword.cpp
class X abstract {};

int main() {
   X * MyX = new X;   // C3622 cannot instantiate abstract class
}
```

## <a name="see-also"></a>Siehe auch

[Überschreibungs Spezifizierer](../extensions/override-specifiers-cpp-component-extensions.md)
