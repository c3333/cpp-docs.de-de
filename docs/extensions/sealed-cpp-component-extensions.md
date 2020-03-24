---
title: sealed (C++/CLI und C++/CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- sealed_cpp
- sealed
helpviewer_keywords:
- sealed keyword [C++]
ms.assetid: 3d0d688a-41aa-45f5-a25a-65c44206521e
ms.openlocfilehash: ab5d5b32ceb87a3b1ccf08d170889dd4825f6c17
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80181797"
---
# <a name="sealed--ccli-and-ccx"></a>sealed (C++/CLI und C++/CX)

**sealed** ist ein kontextbezogenes Schlüsselwort für Verweisklassen, das anzeigt, dass ein virtuelles Element nicht außer Kraft gesetzt werden kann oder ein bestimmter Typ nicht als Basistyp verwendet werden kann.

> [!NOTE]
> Mit der ISO C++ 11-Standardsprache wurde das [final](../cpp/final-specifier.md)-Schlüsselwort eingeführt. Verwenden Sie **final** für Standardklassen und **sealed** für Verweisklassen.

## <a name="all-runtimes"></a>Alle Laufzeiten

## <a name="syntax"></a>Syntax

```cpp
ref class identifier sealed {...};
virtual return-type identifier() sealed {...};
```

### <a name="parameters"></a>Parameter

*identifier*<br/>
Der Name der Funktion oder Klasse.

*return-type*<br/>
Der Typ, der von einer Funktion zurückgegeben wird.

## <a name="remarks"></a>Bemerkungen

Im ersten Syntaxbeispiel wird eine Klasse versiegelt. Im zweiten Beispiel wird eine virtuelle Funktion versiegelt.

Verwenden Sie das **sealed**-Schlüsselwort für Verweisklassen und ihre virtuellen Memberfunktionen. Weitere Informationen finden Sie unter [Überschreibungsspezifizierer und native Kompilierungen](../dotnet/how-to-declare-override-specifiers-in-native-compilations-cpp-cli.md).

Sie können zur Kompilierzeit erkennen, ob ein Typ „sealed“ ist, indem Sie das Typmerkmal `__is_sealed(type)` verwenden. Weitere Informationen finden Sie unter [Compilerunterstützung für Typmerkmale](compiler-support-for-type-traits-cpp-component-extensions.md).

**sealed** ist ein kontextbezogenes Schlüsselwort.  Weitere Informationen finden Sie unter [Kontextbezogene Schlüsselwörter](context-sensitive-keywords-cpp-component-extensions.md).

## <a name="windows-runtime"></a>Windows-Runtime

Siehe [Verweisklassen und Strukturen](../cppcx/ref-classes-and-structs-c-cx.md).

### <a name="requirements"></a>Requirements (Anforderungen)

Compileroption: `/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

(Es gibt keine Hinweise für diese Sprachfunktion, die nur für Common Language Runtime gelten.)

### <a name="requirements"></a>Requirements (Anforderungen)

Compileroption: `/clr`

### <a name="examples"></a>Beispiele

Das folgende Codebeispiel zeigt die Wirkung von **sealed** auf einen virtuellen Member.

```cpp
// sealed_keyword.cpp
// compile with: /clr
interface struct I1 {
   virtual void f();
   virtual void g();
};

ref class X : I1 {
public:
   virtual void f() {
      System::Console::WriteLine("X::f override of I1::f");
   }

   virtual void g() sealed {
      System::Console::WriteLine("X::f override of I1::g");
   }
};

ref class Y : public X {
public:
   virtual void f() override {
      System::Console::WriteLine("Y::f override of I1::f");
   }

   /*
   // the following override generates a compiler error
   virtual void g() override {
      System::Console::WriteLine("Y::g override of I1::g");
   }
   */
};

int main() {
   I1 ^ MyI = gcnew X;
   MyI -> f();
   MyI -> g();

   I1 ^ MyI2 = gcnew Y;
   MyI2 -> f();
}
```

```Output
X::f override of I1::f
X::f override of I1::g
Y::f override of I1::f
```

Das nächste Codebeispiel zeigt , wie eine Klasse als versiegelt markiert wird.

```cpp
// sealed_keyword_2.cpp
// compile with: /clr
interface struct I1 {
   virtual void f();
};

ref class X sealed : I1 {
public:
   virtual void f() override {}
};

ref class Y : public X {   // C3246 base class X is sealed
public:
   virtual void f() override {}
};
```

## <a name="see-also"></a>Weitere Informationen

[Komponentenerweiterungen für .NET und UWP](component-extensions-for-runtime-platforms.md)
