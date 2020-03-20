---
title: new (neuer Slot in vtable) (C++/CLI und C++/CX)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- new keyword [C++]
ms.assetid: 1a9a5704-f02f-46ae-ad65-f0f2b6dbabc3
ms.openlocfilehash: 684c6149457f7b0306f3d444a3652ecda1636839
ms.sourcegitcommit: 8bb2bea1384b290b7570b01608a86c7488ae7a02
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/26/2019
ms.locfileid: "79544411"
---
# <a name="new-new-slot-in-vtable--ccli-and-ccx"></a>new (neuer Slot in vtable) (C++/CLI und C++/CX)

Das Schlüsselwort **new** gibt an, dass ein virtueller Member einen neuen Slot in vtable erhält.

## <a name="all-runtimes"></a>Alle Laufzeiten

(Es gibt keine Hinweise für diese Sprachfunktion, die für alle Laufzeiten gültig sind.)

## <a name="windows-runtime"></a>Windows-Runtime

Wird nicht in Windows-Runtime unterstützt.

## <a name="common-language-runtime"></a>Common Language Runtime

### <a name="remarks"></a>Hinweise

In einer `/clr`-Kompilierung gibt **new** an, dass ein virtueller Member einen neuen Slot in vtable erhält und die Funktion keine Basisklassenmethode überschreibt.

**new** veranlasst, dass der newslot-Modifizierer dem IL für die Funktion hinzugefügt wird.  Weitere Informationen zu "newslot" finden Sie unter:

- <xref:System.Reflection.MethodInfo.GetBaseDefinition?displayProperty=nameWithType>

- <xref:System.Reflection.MethodAttributes?displayProperty=nameWithType>

### <a name="requirements"></a>Voraussetzungen

Compileroption: `/clr`

### <a name="examples"></a>Beispiele

Im folgenden Beispiel werden die Auswirkungen von **new** gezeigt.

```cpp
// newslot.cpp
// compile with: /clr
ref class C {
public:
   virtual void f() {
      System::Console::WriteLine("C::f() called");
   }

   virtual void g() {
      System::Console::WriteLine("C::g() called");
   }
};

ref class D : public C {
public:
   virtual void f() new {
      System::Console::WriteLine("D::f() called");
   }

   virtual void g() override {
      System::Console::WriteLine("D::g() called");
   }
};

ref class E : public D {
public:
   virtual void f() override {
      System::Console::WriteLine("E::f() called");
   }
};

int main() {
   D^ d = gcnew D;
   C^ c = gcnew D;

   c->f();   // calls C::f
   d->f();   // calls D::f

   c->g();   // calls D::g
   d->g();   // calls D::g

   D ^ e = gcnew E;
   e->f();   // calls E::f
}
```

```Output
C::f() called

D::f() called

D::g() called

D::g() called

E::f() called
```

## <a name="see-also"></a>Siehe auch

[Komponentenerweiterungen für .NET und UWP](component-extensions-for-runtime-platforms.md)<br/>
[Überschreibungsspezifizierer](override-specifiers-cpp-component-extensions.md)
