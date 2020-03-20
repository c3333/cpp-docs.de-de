---
title: Explizite Überschreibungen (C++/CLI und C++/CX)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- overriding, override [C++]
ms.assetid: 4ec3eaf5-163b-4df8-8f16-7a2ec04c3d0f
ms.openlocfilehash: b80e49489c0b0d26469ba9f8b77e80a962668e35
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/29/2020
ms.locfileid: "79545432"
---
# <a name="explicit-overrides--ccli-and-ccx"></a>Explizite Überschreibungen (C++/CLI und C++/CX)

In diesem Thema wird erläutert, wie Sie einen Member einer Basisklasse oder -schnittstelle explizit überschreiben. Eine benannte (explizite) Überschreibung sollte nur zum Überschreiben einer Methode mit einer abgeleiteten Methode verwendet werden, die einen anderen Namen aufweist.

## <a name="all-runtimes"></a>Alle Laufzeiten

### <a name="syntax"></a>Syntax

```cpp
overriding-function-declarator = type::function [,type::function] { overriding-function-definition }
overriding-function-declarator = function { overriding-function-definition }
```

### <a name="parameters"></a>Parameter

*overriding-function-declarator*<br/>
Der Rückgabetyp, der Name und die Argumentliste der überschreibenden Funktion.  Beachten Sie, dass die überschreibende Funktion nicht den gleichen Namen aufweisen muss wie die Funktion, die überschrieben wird.

*type*<br/>
Der Basistyp, der eine zu überschreibende Funktion enthält.

*Funktion*<br/>
Eine durch Trennzeichen getrennte Liste mit zu überschreibenden Funktionsnamen.

*overriding-function-definition*<br/>
Die Funktionstextanweisungen, die die überschreibende Funktion definieren.

### <a name="remarks"></a>Hinweise

Verwenden Sie explizite über schreibungen, um einen Alias für eine Methoden Signatur zu erstellen oder um verschiedene Implementierungen für Methoden mit der gleichen Signatur bereitzustellen.

Informationen zum Ändern des Verhaltens von geerbten Typen und geerbten Typmembern finden Sie unter [Überschreibungsspezifizierer](override-specifiers-cpp-component-extensions.md).

## <a name="windows-runtime"></a>Windows-Runtime

### <a name="requirements"></a>Voraussetzungen

Compileroption: `/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

### <a name="remarks"></a>Hinweise

Informationen zu expliziten Überschreibungen in nativem Code oder in mit `/clr:oldSyntax` kompiliertem Code finden Sie unter [Explizite Überschreibungen](../cpp/explicit-overrides-cpp.md).

### <a name="requirements"></a>Voraussetzungen

Compileroption: `/clr`

### <a name="examples"></a>Beispiele

Das folgende Codebeispiel zeigt eine einfache, implizite Überschreibung und die Implementierung eines Members in einer Basisschnittstelle ohne Verwendung von expliziten Überschreibungen.

```cpp
// explicit_override_1.cpp
// compile with: /clr
interface struct I1 {
   virtual void f();
};

ref class X : public I1 {
public:
   virtual void f() {
      System::Console::WriteLine("X::f override of I1::f");
   }
};

int main() {
   I1 ^ MyI = gcnew X;
   MyI -> f();
}
```

```Output
X::f override of I1::f
```

Das folgende Codebeispiel zeigt, wie Sie alle Schnittstellenmember mit einer gemeinsamen Signatur und unter Verwendung einer expliziten Überschreibungssyntax implementieren.

```cpp
// explicit_override_2.cpp
// compile with: /clr
interface struct I1 {
   virtual void f();
};

interface struct I2 {
   virtual void f();
};

ref struct X : public I1, I2 {
   virtual void f() = I1::f, I2::f {
      System::Console::WriteLine("X::f override of I1::f and I2::f");
   }
};

int main() {
   I1 ^ MyI = gcnew X;
   I2 ^ MyI2 = gcnew X;
   MyI -> f();
   MyI2 -> f();
}
```

```Output
X::f override of I1::f and I2::f
X::f override of I1::f and I2::f
```

Das folgende Codebeispiel zeigt, wie eine Funktionsüberschreibung einen anderen Namen aufweisen kann als die Funktion, die sie implementiert.

```cpp
// explicit_override_3.cpp
// compile with: /clr
interface struct I1 {
   virtual void f();
};

ref class X : public I1 {
public:
   virtual void g() = I1::f {
      System::Console::WriteLine("X::g");
   }
};

int main() {
   I1 ^ a = gcnew X;
   a->f();
}
```

```Output
X::g
```

Das folgende Codebeispiel zeigt eine explizite Schnittstellenimplementierung, die eine typsichere Auflistung implementiert.

```cpp
// explicit_override_4.cpp
// compile with: /clr /LD
using namespace System;
ref class R : ICloneable {
   int X;

   virtual Object^ C() sealed = ICloneable::Clone {
      return this->Clone();
   }

public:
   R() : X(0) {}
   R(int x) : X(x) {}

   virtual R^ Clone() {
      R^ r = gcnew R;
      r->X = this->X;
      return r;
   }
};
```

## <a name="see-also"></a>Siehe auch

[Komponentenerweiterungen für .NET und UWP](component-extensions-for-runtime-platforms.md)