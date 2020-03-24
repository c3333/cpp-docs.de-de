---
title: Enumerationsklasse (C++/CLI und C++/CX)
ms.date: 10/12/2018
ms.topic: reference
ms.assetid: 8010fa8c-bad6-45b4-8214-b4db64d7ffe1
ms.openlocfilehash: 6305d41febfe4d55b2b84062e76ff62c3ea2b18a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80182135"
---
# <a name="enum-class--ccli-and-ccx"></a>Enumerationsklasse (C++/CLI und C++/CX)

Deklariert eine Enumeration im Namespacebereich, die ein benutzerdefinierter Typ ist, der aus einem Satz von benannten Konstanten besteht, die als Enumeratoren bezeichnet werden.

## <a name="all-runtimes"></a>Alle Laufzeiten

### <a name="remarks"></a>Bemerkungen

C++/CX und C++/CLI unterstützen **öffentliche Enumerationsklassen** und **private Enumerationsklassen**, die der standardmäßigen **Enumerationsklasse** von C++ ähneln, jedoch zusätzlich einen Zugriffsspezifizierer besitzen. Unter **/clr**ist der C++11-Typ **enum class** zulässig, jedoch wird die Warnung C4472 generiert, die sicherstellen soll, dass Sie tatsächlich den ISO-Enumerationstyp und nicht den C++/CX- und C++/CLI-Typ verwenden möchten. Weitere Informationen zum C++-Schlüsselwort **enum** nach ISO-Standard finden Sie unter [Enumerationen](../cpp/enumerations-cpp.md).

## <a name="windows-runtime"></a>Windows-Runtime

### <a name="syntax"></a>Syntax

```cpp
      access
      enum class
      enumeration-identifier
      [:underlying-type] { enumerator-list } [var];
accessenum structenumeration-identifier[:underlying-type] { enumerator-list } [var];
```

### <a name="parameters"></a>Parameter

*access*<br/>
Der Zugriff auf die Enumeration, der öffentlich (**public**) oder privat (**private**) sein kann.

*enumeration-identifier*<br/>
Der Name der Enumeration.

*underlying-type*<br/>
(Optional) Der zugrunde liegende Typ der Enumeration.

(Optional. Nur Windows-Runtime) Der zugrunde liegende Typ der Enumeration, der **bool**, **char**, `char16`, `int16`, `uint16`, **int**, `uint32`, `int64` oder `uint64` sein kann.

*enumerator-list*<br/>
Eine durch Komma getrennte Liste mit Enumeratornamen.

Der Wert jedes Enumerators ist ein konstanter Ausdruck, der entweder implizit vom Compiler oder explizit durch die Notation *enumerator*`=`*constant-expression*. Standardmäßig ist der Wert des ersten Enumerators Null, wenn er implizit definiert ist. Der Wert jedes folgenden implizit definierten Enumerators ist der Wert des vorherigen Enumerators + 1.

*var*<br/>
(Optional) Der Name einer Variablen des Enumerationstyps.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen und Beispiele finden Sie unter [Enums](../cppcx/enums-c-cx.md).

Beachten Sie, dass der Compiler Fehlermeldungen ausgibt, wenn der konstante Ausdruck, der den Wert eines Enumerators definiert, nicht durch den *underlying-type*dargestellt werden kann.  Der Compiler meldet jedoch keinen Fehler für einen Wert, der für den zugrunde liegenden Typ ungeeignet ist. Beispiel:

- Wenn der *underlying-type* numerisch ist und ein Enumerator den maximalen Wert für diesen Typ angibt, kann der Wert der folgenden implizit definierten Enumeration nicht dargestellt werden.

- Wenn der *underlying-type***bool** ist und mehr als zwei Enumeratoren implizit definiert werden, können die Enumeratoren, die auf die ersten beiden folgen, nicht dargestellt werden.

- Wenn der *underlying-type*`char16`ist und der Enumerationswert von 0xD800 bis 0xDFFF reicht, kann der Wert dargestellt werden. Der Wert ist jedoch logisch falsch, da er die Hälfte ein Unicode-Ersatzzeichenpaars darstellt und nicht isoliert angezeigt werden soll.

### <a name="requirements"></a>Requirements (Anforderungen)

Compileroption: `/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

### <a name="syntax"></a>Syntax

```cpp
      access
      enum class
      name [:type] { enumerator-list } var;
accessenum structname [:type] { enumerator-list } var;
```

### <a name="parameters"></a>Parameter

*access*<br/>
Die Zugriff der Enumeration. Er kann entweder öffentlich (**public**) oder privat (**private**) sein.

*enumerator-list*<br/>
Eine durch Komma getrennte Liste der Bezeichner (Enumeratoren) in der Enumeration.

*name*<br/>
Der Name der Enumeration. Anonyme verwaltete Enumerationen sind nicht zulässig.

*type*<br/>
(Optional) Der zugrunde liegende Typ der *Bezeichner*. Dabei kann es sich um einen beliebigen skalaren Typ handeln, wie Versionen von **int**, **short** oder **long** mit oder ohne Vorzeichen.  **bool** oder **char** sind ebenfalls zulässig.

*var*<br/>
(Optional) Der Name einer Variablen des Enumerationstyps.

### <a name="remarks"></a>Bemerkungen

**enum class** und **enum struct** sind entsprechende Deklarationen.

Es gibt zwei Typen von Enumerationen: C++/CX und Standard.

Eine verwaltete oder C++/CX-Enumeration kann wie folgt definiert sein:

```cpp
public enum class day {sun, mon };
```

und ist semantisch äquivalent zu:

```cpp
ref class day {
public:
   static const int sun = 0;
   static const int mon = 1;
};
```

Eine Standard-Enumeration kann wie folgt definiert sein:

```cpp
enum day2 { sun, mon };
```

und ist semantisch äquivalent zu:

```cpp
static const int sun = 0;
static const int mon = 1;
```

Verwaltete Enumeratornamen (*Bezeichner*) werden nicht in den Bereich injiziert, in dem die Enumeration definiert ist. Alle Verweise auf Enumeratoren müssen vollständig qualifiziert sein (*Name*`::`*Bezeichner*).  Aus diesem Grund können Sie keine anonyme verwaltete Enumeration definieren.

Die Enumeratoren einer Standardenumeration werden stark in den einschließenden Bereich eingefügt.  Das heißt, wenn es ein anderes Symbol mit dem gleichen Namen wie ein Enumerator im einschließenden Bereich gibt, generiert der Compiler einen Fehler.

In Visual Studio 2002 und Visual Studio 2003 wurden Enumeratoren schwach eingefügt (sichtbar im einschließenden Bereich, sofern es keinen anderen Bezeichner mit demselben Namen gibt).

Wenn eine standardmäßige C++-Enumeration (ohne **Klasse** oder **Struktur**) definiert ist, wird die Enumeration beim Kompilieren mit `/clr` als verwaltete Enumeration kompiliert.  Die Enumeration hat weiterhin die Semantik einer nicht verwalteten Enumeration.  Hinweis: Der Compiler fügt das Attribut `Microsoft::VisualC::NativeEnumAttribute` ein, um zu kennzeichnen, dass der Programmierer eine native Enumeration beabsichtigt hat.  Andere Compiler erkennen einfach die Standardenumeration als verwaltete Enumeration.

Eine benannte Standardenumeration, die mit `/clr` kompiliert wurde, ist in der Assembly als verwaltete Enumeration sichtbar und kann von jedem anderen verwalteten Compiler genutzt werden.   Eine unbenannte Standardenumeration ist jedoch nicht öffentlich aus der Assembly sichtbar.

In Visual Studio 2002 und Visual Studio 2003 würde eine Standardenumeration, die als Typ in einem Funktionsparameter verwendet wird:

```cpp
// mcppv2_enum.cpp
// compile with: /clr
enum E { a, b };
void f(E) {System::Console::WriteLine("hi");}

int main() {
   E myi = b;
   f(myi);
}
```

die folgende in MSIL für die Funktionssignatur ausgeben:

```cpp
void f(int32);
```

In den aktuellen Versionen des Compilers, wird die Standardenumeration als verwaltete Enumeration mit einem [NativeEnumAttribute] und dem folgenden in MSIL für die Funktionssignatur ausgegeben:

```cpp
void f(E)
```

Weitere Informationen zu systemeigenen Enumerationen finden Sie unter [Deklarationen von C++-Enumerationen](../cpp/enumerations-cpp.md).

Weitere Informationen zu CLR-Enumerationen finden Sie unter:

- [Zugrunde liegender Typ eines Enumerators](../dotnet/how-to-define-and-consume-enums-in-cpp-cli.md)

### <a name="requirements"></a>Requirements (Anforderungen)

Compileroption: `/clr`

### <a name="examples"></a>Beispiele

```cpp
// mcppv2_enum_2.cpp
// compile with: /clr
// managed enum
public enum class m { a, b };

// standard enum
public enum n { c, d };

// unnamed, standard enum
public enum { e, f } o;

int main()
{
   // consume managed enum
   m mym = m::b;
   System::Console::WriteLine("no automatic conversion to int: {0}", mym);
   System::Console::WriteLine("convert to int: {0}", (int)mym);

   // consume standard enum
   n myn = d;
   System::Console::WriteLine(myn);

   // consume standard, unnamed enum
   o = f;
   System::Console::WriteLine(o);
}
```

```Output
no automatic conversion to int: b

convert to int: 1

1

1
```

## <a name="see-also"></a>Weitere Informationen

[Komponentenerweiterungen für .NET und UWP](component-extensions-for-runtime-platforms.md)
