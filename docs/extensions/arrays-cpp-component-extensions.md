---
title: Arrays (C++/CLI und C++/CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- cli::array
- details::array
- lang::array
helpviewer_keywords:
- array keyword [C++]
- arrays [C++], multidimensional
- multidimensional arrays
- arrays [C++]
ms.assetid: 49445812-d775-4db1-a231-869598dbb955
ms.openlocfilehash: 814be57caafed117a1403105d46326ac53682578
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91500894"
---
# <a name="arrays-ccli-and-ccx"></a>Arrays (C++/CLI und C++/CX)

Der `Platform::Array<T>`-Typ in C++/CX oder das **array**-Schlüsselwort in C++/CLI deklarieren ein Array des angegebenen Typs und den Anfangswert.

## <a name="all-platforms"></a>Alle Plattformen

Das Array muss mit dem Handle-to-Object-Modifizierer (^) nach der schließenden spitzen Klammer (>) in der Deklaration deklariert werden.
Die Anzahl der Elemente des Arrays ist nicht Teil des Typs. Eine Arrayvariable kann auf Arrays von unterschiedlicher Größe verweisen.

Im Gegensatz zu standardmäßigem C++ ist die Indizierung kein Synonym für Zeigerarithmetik und nicht kommutativ.

Weitere Informationen zu Arrays finden Sie hier:

- [Gewusst wie: Verwenden von Arrays in C++/CLI](../dotnet/how-to-use-arrays-in-cpp-cli.md)

- [Variable Argumentlisten (...) (C++/CLI)](variable-argument-lists-dot-dot-dot-cpp-cli.md)

## <a name="windows-runtime"></a>Windows-Runtime

Arrays sind Member des `Platform`-Namespace. Arrays können nur eindimensional sein.

### <a name="syntax"></a>Syntax

Im ersten Beispiel der Syntax wird mit dem **ref new**-Aggregatschlüsselwort ein Array zugeordnet. Im zweiten Beispiel wird ein lokales Array deklariert.

```cpp
[qualifiers] [Platform::]Array<[qualifiers] array-type [,rank]>^ identifier =
    ref new[Platform::]Array<initialization-type> [{initialization-list [,...]}]

[qualifiers] [Platform::]Array<[qualifiers] array-type [,rank]>^ identifier =
    {initialization-list [,...]}
```

*und „Me.“*<br/>
(Optional) Einer oder mehrere der folgenden Speicherklassenspezifizierer: [mutable](../cpp/mutable-data-members-cpp.md), [volatile](../cpp/volatile-cpp.md), [const](../cpp/const-cpp.md), [extern](../cpp/extern-cpp.md), [static](../cpp/static-members-cpp.md).

*Arraytyp*<br/>
Der Typ der Arrayvariablen. Gültige Typen sind Windows-Runtime-Klassen und grundlegende Typen, Verweisklassen und -strukturen, Wertklassen und -strukturen und native Zeiger (`type*`).

*gehören*<br/>
(Optional) Die Anzahl der Dimensionen des Arrays. Muss 1 sein.

*identifier*<br/>
Der Name der Arrayvariablen.

*initialization-type*<br/>
Der Typ der Werte, die das Array initialisieren. In der Regel haben *array-type* und *initialization-type* denselben Typ. Die Typen können jedoch unterschiedlich sein, wenn eine Konvertierung von *initialization-type* zu *array-type* erfolgt – z.B., wenn *initialization-type* von *array-type* abgeleitet ist.

*initialization-list*<br/>
(Optional) Eine durch Trennzeichen getrennte Liste von Werten in geschweiften Klammern, die die Elemente des Arrays initialisieren. Wenn z.B. *rank-size-list*`(3)` wäre, was ein eindimensionales Array von 3 Elementen deklariert, könnte *initialization-list*`{1,2,3}` sein.

### <a name="remarks"></a>Bemerkungen

Sie können zur Kompilierzeit mit `__is_ref_array(type)` erkennen, ob ein Typ ein Array mit Verweiszählung ist. Weitere Informationen finden Sie unter [Compilerunterstützung für Typmerkmale](compiler-support-for-type-traits-cpp-component-extensions.md).

### <a name="requirements"></a>Requirements (Anforderungen)

Compileroption: `/ZW`

### <a name="examples"></a>Beispiele

Im folgenden Beispiel wird ein eindimensionales Array erstellt, das über 100 Elemente verfügt.

```cpp
// cwr_array.cpp
// compile with: /ZW
using namespace Platform;
ref class MyClass {};
int main() {
   // one-dimensional array
   Array<MyClass^>^ My1DArray = ref new Array<MyClass^>(100);
   My1DArray[99] = ref new MyClass();
}
```

## <a name="common-language-runtime"></a>Common Language Runtime

### <a name="syntax"></a>Syntax

Im ersten Beispiel der Syntax wird mit dem **gcnew**-Schlüsselwort ein Array zugeordnet. Im zweiten Beispiel wird ein lokales Array deklariert.

```cpp
[qualifiers] [cli::]array<[qualifiers] array-type [,rank]>^ identifier =
    gcnew [cli::]array<initialization-type[,rank]>(rank-size-list[,...]) [{initialization-list [,...]}]

[qualifiers] [cli::]array<[qualifiers] array-type [,rank]>^ identifier =
    {initialization-list [,...]}
```

*und „Me.“*<br/>
(Optional) Einer oder mehrere der folgenden Speicherklassenspezifizierer: [mutable](../cpp/mutable-data-members-cpp.md), [volatile](../cpp/volatile-cpp.md), [const](../cpp/const-cpp.md), [extern](../cpp/extern-cpp.md), [static](../cpp/static-members-cpp.md).

*Arraytyp*<br/>
Der Typ der Arrayvariablen. Gültige Typen sind Windows-Runtime-Klassen und grundlegende Typen, Verweisklassen und -strukturen, Wertklassen und -strukturen, native Zeiger (`type*`) und native POD-Typen (Plain Old Data).

*gehören*<br/>
(Optional) Die Anzahl der Dimensionen des Arrays. Der Standardwert ist 1, der Höchstwert 32. Jede Dimension des Arrays ist selbst ein Array.

*identifier*<br/>
Der Name der Arrayvariablen.

*initialization-type*<br/>
Der Typ der Werte, die das Array initialisieren. In der Regel haben *array-type* und *initialization-type* denselben Typ. Die Typen können jedoch unterschiedlich sein, wenn eine Konvertierung von *initialization-type* zu *array-type* erfolgt – z.B., wenn *initialization-type* von *array-type* abgeleitet ist.

*rank-size-list*<br/>
Eine durch Trennzeichen getrennte Liste der Größe der einzelnen Dimensionen im Array. Alternativ kann der Compiler bei Angabe des *initialization-list*-Parameters die Größe der jeweiligen Dimension ableiten, sodass *rank-size-list* ausgelassen werden kann.

*initialization-list*<br/>
(Optional) Eine durch Trennzeichen getrennte Liste von Werten in geschweiften Klammern, die die Elemente des Arrays initialisieren. Es kann auch eine durch Trennzeichen getrennte Liste von geschachtelten oder *initialization-list*-Elementen sein, die die Elemente in einem mehrdimensionalen Array initialisieren.

Wenn z.B. *rank-size-list*`(3)` wäre, was ein eindimensionales Array von 3 Elementen deklariert, könnte *initialization-list*`{1,2,3}` sein. Wenn *rank-size-list*`(3,2,4)` wäre, was ein dreidimensionales Arrays von 3 Elementen in der ersten, 2 Elementen in der zweiten und 4 Elementen in der dritten Dimension deklariert, könnte *initialization-list*`{{1,2,3},{0,0},{-5,10,-21,99}}` sein.

### <a name="remarks"></a>Bemerkungen

**array** befindet sich in [Plattform-, Standard- und CLI-Namespaces (C++/CLI und C++/CX)](platform-default-and-cli-namespaces-cpp-component-extensions.md).

Wie bei standardmäßigem C++ sind die Indizes eines Arrays nullbasiert, und ein Array wird mit eckigen Klammern ([]) indiziert. Im Gegensatz zu standardmäßigem C++ sind die Indizes eines mehrdimensionalen Arrays in einer Liste von Indizes für jede Dimension anstatt eines Satzes von Operatoren mit eckigen Klammern ([]) für jede Dimension angegeben. Beispiel: *Bezeichner*[*index1*, *index2*] anstelle von *Bezeichner*[*index1*][*index2*].

Alle verwalteten Arrays erben von `System::Array`. Eine beliebige Methode oder Eigenschaft von `System::Array` kann direkt auf die Arrayvariable angewendet werden.

Wenn Sie ein Array zuordnen, dessen Elementtyp Zeiger auf eine verwaltete Klasse ist, sind die Elemente 0-initialisiert.

Wenn Sie ein Array zuordnen, dessen Elementtyp ein Werttyp `V` ist, wird der Standardkonstruktor für `V` auf jedes Arrayelement angewendet. Weitere Informationen finden Sie unter [.NET Framework-Entsprechungen der nativen Typen in C++ (C++/CLI)](../dotnet/managed-types-cpp-cli.md#dotnet).

Zur Kompilierzeit können Sie mit `__is_ref_array(type)` erkennen, ob ein Typ ein Common Language Runtime-Array (CLR) ist. Weitere Informationen finden Sie unter [Compilerunterstützung für Typmerkmale](compiler-support-for-type-traits-cpp-component-extensions.md).

### <a name="requirements"></a>Requirements (Anforderungen)

Compileroption: `/clr`

### <a name="examples"></a>Beispiele

Im folgenden Beispiel werden ein eindimensionales Array mit 100 Elementen erstellt sowie ein dreidimensionales Array mit 3 Elementen in der ersten, 5 Elementen in der zweiten und 6 Elementen in der dritten Dimension.

```cpp
// clr_array.cpp
// compile with: /clr
ref class MyClass {};
int main() {
   // one-dimensional array
   array<MyClass ^> ^ My1DArray = gcnew array<MyClass ^>(100);
   My1DArray[99] = gcnew MyClass();

   // three-dimensional array
   array<MyClass ^, 3> ^ My3DArray = gcnew array<MyClass ^, 3>(3, 5, 6);
   My3DArray[0,0,0] = gcnew MyClass();
}
```

## <a name="see-also"></a>Weitere Informationen

[Komponenten Erweiterungen für .net und UWP](component-extensions-for-runtime-platforms.md)
