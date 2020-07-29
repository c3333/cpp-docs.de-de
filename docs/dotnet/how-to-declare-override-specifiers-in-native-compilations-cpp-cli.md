---
title: 'Vorgehensweise: Deklarieren von Überschreibungsspezifizierer (C++/CLI)'
ms.date: 11/04/2016
helpviewer_keywords:
- override specifiers in native compilation, overriding
ms.assetid: d0551836-9ac7-41eb-a6e9-a4b3ef60767d
ms.openlocfilehash: c5ed413f403fb12f116633c0e39f9e7b32b2e9f8
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221327"
---
# <a name="how-to-declare-override-specifiers-in-native-compilations-ccli"></a>Gewusst wie: Deklarieren von Überschreibungsbezeichnern in nativen Kompilierungen (C++/CLI)

[sealed](../extensions/sealed-cpp-component-extensions.md), [abstract](../extensions/abstract-cpp-component-extensions.md)und [override](../extensions/override-cpp-component-extensions.md) sind in Kompilierungen verfügbar, die nicht **/ZW** oder [/CLR](../build/reference/clr-common-language-runtime-compilation.md)verwenden.

> [!NOTE]
> Die ISO c++ 11-Standard Sprache verfügt über den [Überschreibungs](../cpp/override-specifier.md) Bezeichner und den [endgültigen](../cpp/final-specifier.md) Bezeichner. beide werden in Visual Studio `final` anstelle von in Code unterstützt, der **`sealed`** als System eigen reine Kompilierung verwendet werden soll.

## <a name="example"></a>Beispiel

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

## <a name="example"></a>Beispiel

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

## <a name="example"></a>Beispiel

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

## <a name="see-also"></a>Weitere Informationen

[Überschreibungs Spezifizierer](../extensions/override-specifiers-cpp-component-extensions.md)
