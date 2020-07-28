---
title: literal (C++/CLI und C++/CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- literal
- literal_cpp
helpviewer_keywords:
- literal keyword [C++]
ms.assetid: 6b1a1f36-2e1d-4a23-8eb6-172f4f3c477f
ms.openlocfilehash: 2470d5680f7538af2db7bda3611abad11b827970
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214255"
---
# <a name="literal-ccli-and-ccx"></a>literal (C++/CLI und C++/CX)

Eine als **literal** markierte Variable (Datenmember) in einer **/clr**-Kompilierung ist das native Äquivalent einer **static const**-Variablen.

## <a name="all-platforms"></a>Alle Plattformen

### <a name="remarks"></a>Bemerkungen

(Es gibt keine Hinweise für diese Sprachfunktion, die für alle Laufzeiten gültig sind.)

## <a name="windows-runtime"></a>Windows-Runtime

### <a name="remarks"></a>Bemerkungen

(Es gibt keine Hinweise für diese Sprachfunktion, die nur für Windows-Runtime gelten.)

### <a name="requirements"></a>Requirements (Anforderungen)

Compileroption: `/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

## <a name="remarks"></a>Bemerkungen

Ein als **literal** markierter Datenmember muss beim Deklarieren initialisiert werden, und der Wert muss ein konstanter Ganzzahl-, Enumerations- oder Zeichenfolgentyp sein. Die Konvertierung vom Typ des Initialisierungsausdrucks in den Typ des static const-Datenmembers muss keine benutzerdefinierte Konvertierung erfordern.

Für das literal-Feld wird zur Laufzeit kein Arbeitsspeicher belegt; der Compiler fügt nur seinen Wert in die Metadaten für die Klasse ein.

Eine als **static const** markierte Variable wird in den Metadaten nicht für andere Compiler verfügbar sein.

Weitere Informationen finden Sie unter [Static](../cpp/storage-classes-cpp.md) und [const](../cpp/const-cpp.md).

**literal** ist ein kontextbezogenes Schlüsselwort. Weitere Informationen finden Sie unter [Kontextbezogene Schlüsselwörter](context-sensitive-keywords-cpp-component-extensions.md).

## <a name="example"></a>Beispiel

Dieses Beispiel zeigt, dass eine **literalvariable** impliziert **`static`** .

```cpp
// mcppv2_literal.cpp
// compile with: /clr
ref struct X {
   literal int i = 4;
};

int main() {
   int value = X::i;
}
```

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt die Auswirkungen von „literal“ in den Metadaten:

```cpp
// mcppv2_literal2.cpp
// compile with: /clr /LD
public ref struct A {
   literal int lit = 0;
   static const int sc = 1;
};
```

Beachten Sie den Unterschied in den Metadaten für `sc` und `lit`: die `modopt`-Anweisung gilt für `sc`, d.h. sie kann von anderen Compilern ignoriert werden.

```
.field public static int32 modopt([mscorlib]System.Runtime.CompilerServices.IsConst) sc = int32(0x0000000A)
```

```
.field public static literal int32 lit = int32(0x0000000A)
```

## <a name="example"></a>Beispiel

Im folgenden in C# erstellten Beispiel wird auf die im vorherigen Beispiel erstellten Metadaten verwiesen, und es zeigt die Auswirkungen der **literal**- und **static const**-Variablen:

```csharp
// mcppv2_literal3.cs
// compile with: /reference:mcppv2_literal2.dll
// A C# program
class B {
   public static void Main() {
      // OK
      System.Console.WriteLine(A.lit);
      System.Console.WriteLine(A.sc);

      // C# does not enforce C++ const
      A.sc = 9;
      System.Console.WriteLine(A.sc);

      // C# enforces const for a literal
      A.lit = 9;   // CS0131

      // you can assign a C++ literal variable to a C# const variable
      const int i = A.lit;
      System.Console.WriteLine(i);

      // but you cannot assign a C++ static const variable
      // to a C# const variable
      const int j = A.sc;   // CS0133
      System.Console.WriteLine(j);
   }
}
```

## <a name="requirements"></a>Requirements (Anforderungen)

Compileroption: `/clr`

## <a name="see-also"></a>Weitere Informationen

[Komponenten Erweiterungen für .net und UWP](component-extensions-for-runtime-platforms.md)
