---
title: Literale (C++/CLI)
description: Das Literalschlüsselwort ist ein Kontext sensibles Schlüsselwort von Microsoft C++/CLI für eine Kompilierzeit Konstante.
ms.date: 10/20/2020
ms.topic: reference
f1_keywords:
- literal
- literal_cpp
helpviewer_keywords:
- literal keyword [C++]
ms.openlocfilehash: 2d71a535252ba51f89407670b474a34b407eaffc
ms.sourcegitcommit: 59b7c18703d1ffd66827db0e2eeece490d3d8789
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/21/2020
ms.locfileid: "92337212"
---
# <a name="literal-ccli"></a>`literal` (C++/CLI)

Eine Variable (Datenmember), die als **`literal`** in einer **`/clr`** Kompilierung gekennzeichnet ist, ist eine Kompilierzeit Konstante. Dabei handelt es sich um das systemeigene Äquivalent einer c#- [`const`](/dotnet/csharp/language-reference/keywords/const) Variablen.

## <a name="all-platforms"></a>Alle Plattformen

### <a name="remarks"></a>Bemerkungen

(Es gibt keine Hinweise für diese Sprachfunktion, die für alle Laufzeiten gültig sind.)

## <a name="windows-runtime"></a>Windows-Runtime

### <a name="remarks"></a>Bemerkungen

(Es gibt keine Hinweise für diese Sprachfunktion, die nur für Windows-Runtime gelten.)

## <a name="common-language-runtime"></a>Common Language Runtime

## <a name="remarks"></a>Bemerkungen

Ein als markierter Datenmember **`literal`** muss initialisiert werden, wenn er deklariert wird. Und der Wert muss ein konstanter ganzzahliger Typ, Enumerationstyp oder Zeichen Folgentyp sein. Die Konvertierung vom Typ des Initialisierungs Ausdrucks in den Typ des **`literal`** Datenmembers kann keine benutzerdefinierte Konvertierung erfordern.

Für das Feld wird zur Laufzeit kein Arbeitsspeicher zugeordnet **`literal`** . der Compiler fügt seinen Wert nur in die Metadaten für die Klasse ein. Der **`literal`** Wert wird als Kompilierzeit Konstante behandelt. Das nächstgelegene Äquivalent in Standard C++ ist **`constexpr`** , ein Datenmember kann jedoch nicht **`constexpr`** in C++/CLI.

Eine Variable, die als gekennzeichnet **`literal`** ist, weicht von einem markierten ab **`static const`** . Ein **`static const`** Datenmember wird nicht in den Metadaten für andere Compiler zur Verfügung gestellt. Weitere Informationen finden Sie unter [`static`](../cpp/storage-classes-cpp.md) und [`const`](../cpp/const-cpp.md).

**`literal`** ist ein kontextsensitiv Schlüsselwort. Weitere Informationen finden Sie unter [Kontextbezogene Schlüsselwörter](context-sensitive-keywords-cpp-component-extensions.md).

## <a name="examples"></a>Beispiele

Dieses Beispiel zeigt, dass eine **`literal`** Variable impliziert **`static`** .

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

Das folgende Beispiel zeigt die Auswirkung von **`literal`** in Metadaten:

```cpp
// mcppv2_literal2.cpp
// compile with: /clr /LD
public ref struct A {
   literal int lit = 0;
   static const int sc = 1;
};
```

Beachten Sie den Unterschied in den Metadaten für `sc` und `lit`: die `modopt`-Anweisung gilt für `sc`, d.h. sie kann von anderen Compilern ignoriert werden.

```MSIL
.field public static int32 modopt([mscorlib]System.Runtime.CompilerServices.IsConst) sc = int32(0x00000001)
```

```MSIL
.field public static literal int32 lit = int32(0x00000000)
```

Das folgende Beispiel, das in c# erstellt wurde, verweist auf die Metadaten, die im vorherigen Beispiel erstellt wurden, und zeigt die Auswirkung der **`literal`** **`static const`** Variablen und:

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
