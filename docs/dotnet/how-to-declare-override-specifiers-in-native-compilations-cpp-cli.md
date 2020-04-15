---
title: 'Gewusst wie: Überschreiben von Bezeichnern deklarieren (C++/CLI)'
ms.date: 11/04/2016
helpviewer_keywords:
- override specifiers in native compilation, overriding
ms.assetid: d0551836-9ac7-41eb-a6e9-a4b3ef60767d
ms.openlocfilehash: 9f3f6855f257d0af250b9bbdd2c0360b308ce775
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374450"
---
# <a name="how-to-declare-override-specifiers-in-native-compilations-ccli"></a>Gewusst wie: Deklarieren von Überschreibungsbezeichnern in nativen Kompilierungen (C++/CLI)

[Sealed](../extensions/sealed-cpp-component-extensions.md), [abstract](../extensions/abstract-cpp-component-extensions.md)und [override](../extensions/override-cpp-component-extensions.md) sind in Kompilierungen verfügbar, die **/ZW** oder [/clr](../build/reference/clr-common-language-runtime-compilation.md)nicht verwenden.

> [!NOTE]
> Die ISO C++11-Standardsprache verfügt über den [Außerkraftsetzungsbezeichner](../cpp/override-specifier.md) `final` und `sealed` den [endgültigen](../cpp/final-specifier.md) Bezeichner, und beide werden in Visual Studio Use anstelle von Code unterstützt, der als nur systemeigener Code kompiliert werden soll.

## <a name="example"></a>Beispiel

### <a name="description"></a>BESCHREIBUNG

Das folgende Beispiel `sealed` zeigt, dass dies in systemeigenen Kompilierungen gültig ist.

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

Das nächste Beispiel `override` zeigt, dass dies in systemeigenen Kompilierungen gültig ist.

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

Dieses Beispiel `abstract` zeigt, dass dies in systemeigenen Kompilierungen gültig ist.

### <a name="code"></a>Code

```cpp
// abstract_native_keyword.cpp
class X abstract {};

int main() {
   X * MyX = new X;   // C3622 cannot instantiate abstract class
}
```

## <a name="see-also"></a>Siehe auch

[Überschreibungsspezifizierer](../extensions/override-specifiers-cpp-component-extensions.md)
