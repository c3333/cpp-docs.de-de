---
title: abstract  (C++/CLI und C++/CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- abstract
- abstract_cpp
helpviewer_keywords:
- abstract keyword [C++]
ms.assetid: cbae3408-0378-4ac8-b70d-c016b381a6d5
ms.openlocfilehash: 1e729589f78c56111717a87a27f9c7370dca7b90
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214294"
---
# <a name="abstract--ccli-and-ccx"></a>abstract  (C++/CLI und C++/CX)

Das **abstract**-Schlüsselwort nimmt eine der folgenden Deklarationen vor:

- Ein Typ kann als Basistyp verwendet werden, aber der Typ selbst kann nicht instanziiert werden.

- Eine Typmemberfunktion kann nur in einem abgeleiteten Typ definiert werden.

## <a name="all-platforms"></a>Alle Plattformen

### <a name="syntax"></a>Syntax

*Klassendeklaration* *Klassenbezeichner* **abstract {}**

**`virtual`** der *Rückgabetyp* *Member-function-identifier* **() abstract;**

### <a name="remarks"></a>Bemerkungen

Die erste Beispielsyntax deklariert eine Klasse als abstrakt. Die *class-declaration-* Komponente kann entweder eine systemeigene C++-Deklaration (** `class` * * * * oder **`struct`** ) oder eine C++-Erweiterungs Deklaration (** ref class * * oder **ref struct**) sein, wenn die- `/ZW` oder- `/clr` Compileroption angegeben wird.

Die zweite Beispielsyntax deklariert eine virtuelle Memberfunktion als abstrakt. Das Deklarieren einer Funktion als abstrakt ist mit dem Deklarieren als rein virtuelle Funktion identisch. Das Deklarieren einer Memberfunktion als abstrakt bewirkt, dass auch die einschließende Klasse als abstrakt deklariert wird.

Das **abstract**-Schlüsselwort wird in nativem und plattformspezifischem Code unterstützt, d.h. es kann mit oder ohne Compileroption `/ZW` oder `/clr` kompiliert werden.

Sie können mit der `__is_abstract(type)`-Typeigenschaft zum Zeitpunkt der Kompilierung ermitteln, ob ein Typ abstrakt ist. Weitere Informationen finden Sie unter [Compilerunterstützung für Typmerkmale](compiler-support-for-type-traits-cpp-component-extensions.md).

Das **abstract**-Schlüsselwort ist ein kontextbezogener Überschreibungsspezifizierer. Weitere Informationen zu kontextbezogenen Schlüsselwörtern finden Sie unter [Kontextbezogene Schlüsselwörter](context-sensitive-keywords-cpp-component-extensions.md). Weitere Informationen zu Überschreibungsspezifizierer finden Sie unter Gewusst [wie: Deklarieren von Überschreibungs Bezeichnungen in systemeigenen Kompilierungen](../dotnet/how-to-declare-override-specifiers-in-native-compilations-cpp-cli.md).

## <a name="windows-runtime"></a>Windows-Runtime

Weitere Informationen finden Sie unter Verweis [Klassen und Strukturen](../cppcx/ref-classes-and-structs-c-cx.md).

### <a name="requirements"></a>Requirements (Anforderungen)

Compileroption: `/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

### <a name="requirements"></a>Requirements (Anforderungen)

Compileroption: `/clr`

### <a name="examples"></a>Beispiele

Das folgende Codebeispiel generiert einen Fehler, da Klasse `X` als **abstract** gekennzeichnet ist.

```cpp
// abstract_keyword.cpp
// compile with: /clr
ref class X abstract {
public:
   virtual void f() {}
};

int main() {
   X ^ MyX = gcnew X;   // C3622
}
```

Das folgende Codebeispiel generiert einen Fehler, da es eine native Klasse instanziiert, die als **abstract** gekennzeichnet ist. Dieser Fehler tritt mit und ohne Compileroption `/clr` auf.

```cpp
// abstract_keyword_2.cpp
class X abstract {
public:
   virtual void f() {}
};

int main() {
   X * MyX = new X; // C3622: 'X': a class declared as 'abstract'
                    // cannot be instantiated. See declaration of 'X'}
```

Das folgende Codebeispiel generiert einen Fehler, da Funktion `f` eine Definition enthält, aber als **abstract** gekennzeichnet ist. Die letzte Anweisung im Beispiel zeigt, dass das Deklarieren einer abstrakten virtuellen Funktion dem Deklarieren einer rein virtuellen Funktion entspricht.

```cpp
// abstract_keyword_3.cpp
// compile with: /clr
ref class X {
public:
   virtual void f() abstract {}   // C3634
   virtual void g() = 0 {}   // C3634
};
```

## <a name="see-also"></a>Weitere Informationen

[Komponenten Erweiterungen für .net und UWP](component-extensions-for-runtime-platforms.md)
