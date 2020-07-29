---
title: Compilerunterstützung für Typmerkmale (C++/CLI und C++/CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- __is_simple_value_class
- __has_trivial_destructor
- __has_assign
- __is_union
- __is_class
- __is_abstract
- __has_trivial_assign
- __has_virtual_destructor
- __is_ref_array
- __is_base_of
- __has_copy
- __is_polymorphic
- __has_nothrow_constructor
- __is_ref_class
- __is_delegate
- __is_convertible_to
- __is_value_class
- __is_interface_class
- __has_nothrow_copy
- __is_sealed
- __has_trivial_constructor
- __has_trivial_copy
- __is_enum
- __has_nothrow_assign
- __has_finalizer
- __is_empty
- __is_pod
- __has_user_destructor
helpviewer_keywords:
- __is_class keyword [C++]
- __is_pod keyword [C++]
- __is_delegate keyword [C++]
- __is_value_class keyword [C++]
- __has_copy keyword [C++]
- __has_nothrow_copy keyword [C++]
- __is_interface_class keyword [C++]
- __is_sealed keyword [C++]
- __is_convertible_to keyword [C++]
- __is_ref_class keyword [C++]
- __has_trivial_copy keyword [C++]
- __has_user_destructor keyword [C++]
- __is_abstract keyword [C++]
- __is_empty keyword [C++]
- __has_trivial_assign keyword [C++]
- __has_nothrow_constructor keyword [C++]
- __is_ref_array keyword [C++]
- __is_base_of keyword [C++]
- __has_nothrow_assign keyword [C++]
- __has_virtual_destructor keyword [C++]
- __has_finalizer keyword [C++]
- __is_union keyword [C++]
- __has_assign keyword [C++]
- __has_trivial_destructor keyword [C++]
- __is_polymorphic keyword [C++]
- __is_enum keyword [C++]
- __is_simple_value_class keyword [C++]
- __has_trivial_constructor keyword [C++]
ms.assetid: cd440630-0394-48c0-a16b-1580b6ef5844
ms.openlocfilehash: 16c79e05c6ba6f50a3e6c0d6dd5f48963be40fa8
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219780"
---
# <a name="compiler-support-for-type-traits-ccli-and-ccx"></a>Compilerunterstützung für Typmerkmale (C++/CLI und C++/CX)

Der Microsoft C++-Compiler unterstützt * Typmerkmale* für C++/CLI- und C++/CX-Erweiterungen, die verschiedene Merkmale eines Typs zur Kompilierzeit angeben.

## <a name="all-runtimes"></a>Alle Laufzeiten

### <a name="remarks"></a>Bemerkungen

Typeigenschaften sind besonders nützlich für Programmierer, die Bibliotheken schreiben.

Die folgende Liste enthält die Typmerkmale, die vom Compiler unterstützt werden. Alle Typmerkmale geben zurück, **`false`** Wenn die durch den Namen des typmerkmals angegebene Bedingung nicht erfüllt wird.

(In der folgenden Liste sind die Codebeispiele nur in C++/CLI geschrieben. Das entsprechende Typmerkmal wird auch in C++/CX unterstützt, sofern nichts anderes angegeben ist. Der Begriff „Plattformtyp“ bezieht sich entweder auf Windows-Runtime oder Common Language Runtime-Typen.)

- `__has_assign(`*Typ*`)`

   Gibt zurück, **`true`** Wenn die Plattform oder der systemeigene Typ einen Kopier Zuweisungs Operator aufweist.

    ```cpp
    ref struct R {
    void operator=(R% r) {}
    };

    int main() {
    System::Console::WriteLine(__has_assign(R));
    }
    ```

- `__has_copy(`*Typ*`)`

   Gibt zurück, **`true`** Wenn die Plattform oder der systemeigene Typ einen Kopierkonstruktor aufweist.

    ```cpp
    ref struct R {
    R(R% r) {}
    };

    int main() {
    System::Console::WriteLine(__has_copy(R));
    }
    ```

- `__has_finalizer(`*Typ*`)`

   (Nicht unterstützt in C++/CX.) Gibt zurück, **`true`** Wenn der CLR-Typ über einen Finalizer verfügt. Weitere Informationen finden [Sie unter debugtoren und Finalizer in Gewusst wie: definieren und Verarbeiten von Klassen und Strukturen (C++/CLI)](../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers) .

    ```cpp
    using namespace System;
    ref struct R {
    ~R() {}
    protected:
    !R() {}
    };

    int main() {
    Console::WriteLine(__has_finalizer(R));
    }
    ```

- `__has_nothrow_assign(`*Typ*`)`

   Gibt zurück, **`true`** Wenn ein Kopier Zuweisungs Operator eine leere Ausnahme Spezifikation aufweist.

    ```cpp
    #include <stdio.h>
    struct S {
    void operator=(S& r) throw() {}
    };

    int main() {
    __has_nothrow_assign(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__has_nothrow_constructor(`*Typ*`)`

   Gibt zurück, **`true`** Wenn der Standardkonstruktor eine leere Ausnahme Spezifikation aufweist.

    ```cpp
    #include <stdio.h>
    struct S {
    S() throw() {}
    };

    int main() {
    __has_nothrow_constructor(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__has_nothrow_copy(`*Typ*`)`

   Gibt zurück, **`true`** Wenn der Kopierkonstruktor eine leere Ausnahme Spezifikation aufweist.

    ```cpp
    #include <stdio.h>
    struct S {
    S(S& r) throw() {}
    };

    int main() {
    __has_nothrow_copy(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__has_trivial_assign(`*Typ*`)`

   Gibt zurück **`true`** , wenn der Typ einen trivialen, vom Compiler generierten Zuweisungs Operator aufweist.

    ```cpp
    #include <stdio.h>
    struct S {};

    int main() {
    __has_trivial_assign(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__has_trivial_constructor(`*Typ*`)`

   Gibt zurück **`true`** , wenn der Typ einen trivialen, vom Compiler generierten Konstruktor aufweist.

    ```cpp
    #include <stdio.h>
    struct S {};

    int main() {
    __has_trivial_constructor(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__has_trivial_copy(`*Typ*`)`

   Gibt zurück **`true`** , wenn der Typ einen trivialen, vom Compiler generierten Kopierkonstruktor aufweist.

    ```cpp
    #include <stdio.h>
    struct S {};

    int main() {
    __has_trivial_copy(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__has_trivial_destructor(`*Typ*`)`

   Gibt zurück **`true`** , wenn der Typ einen trivialen, vom Compiler generierten Dekonstruktor aufweist.

    ``` cpp
    // has_trivial_destructor.cpp
    #include <stdio.h>
    struct S {};

    int main() {
    __has_trivial_destructor(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__has_user_destructor(`*Typ*`)`

   Gibt zurück, **`true`** Wenn die Plattform oder der systemeigene Typ einen vom Benutzer deklarierten Dekonstruktor aufweist.

    ```cpp
    // has_user_destructor.cpp

    using namespace System;
    ref class R {
    ~R() {}
    };

    int main() {
    Console::WriteLine(__has_user_destructor(R));
    }
    ```

- `__has_virtual_destructor(`*Typ*`)`

   Gibt zurück, **`true`** Wenn der Typ einen virtuellen Dekonstruktor aufweist.

   `__has_virtual_destructor` funktioniert auch für Plattformtypen, und jeder benutzerdefinierte Destruktor in einem Plattformtyp ist ein virtueller Destruktor.

    ```cpp
    // has_virtual_destructor.cpp
    #include <stdio.h>
    struct S {
    virtual ~S() {}
    };

    int main() {
    __has_virtual_destructor(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__is_abstract(`*Typ*`)`

   Gibt zurück, **`true`** Wenn der Typ ein abstrakter Typ ist. Weitere Informationen zu nativen abstrakten Typen finden Sie unter [Abstrakte Klassen](../cpp/abstract-classes-cpp.md).

   `__is_abstract` funktioniert auch für die Plattformtypen. Eine Schnittstelle mit mindestens einem Member ist ein abstrakter Typ, genauso wie ein Verweistyp mit mindestens einem abstrakten Member. Weitere Informationen zu abstrakten Plattformtypen finden Sie unter [abstract](abstract-cpp-component-extensions.md).

    ```cpp
    // is_abstract.cpp
    #include <stdio.h>
    struct S {
    virtual void Test() = 0;
    };

    int main() {
    __is_abstract(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__is_base_of(` `base` `,` `derived` `)`

   Gibt zurück **`true`** , wenn der erste Typ eine Basisklasse des zweiten Typs ist, von, wenn beide Typen identisch sind.

   `__is_base_of` funktioniert auch für Plattformtypen. Beispielsweise wird zurückgegeben, **`true`** Wenn der erste Typ eine [Schnittstellen Klasse](interface-class-cpp-component-extensions.md) ist und der zweite Typ die-Schnittstelle implementiert.

    ```cpp
    // is_base_of.cpp
    #include <stdio.h>
    struct S {};
    struct T : public S {};

    int main() {
    __is_base_of(S, T) == true ?
    printf("true\n") : printf("false\n");

    __is_base_of(S, S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__is_class(`*Typ*`)`

   Gibt zurück, **`true`** Wenn der Typ eine systemeigene Klasse oder Struktur ist.

    ```cpp
    #include <stdio.h>
    struct S {};

    int main() {
    __is_class(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__is_convertible_to(` `from` `,`  `to` `)`

   Gibt zurück **`true`** , wenn der erste Typ in den zweiten Typ konvertiert werden kann.

    ```cpp
    #include <stdio.h>
    struct S {};
    struct T : public S {};

    int main() {
    S * s = new S;
    T * t = new T;
    s = t;
    __is_convertible_to(T, S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__is_delegate(`*Typ*`)`

   Gibt zurück, **`true`** Wenn ein Delegat `type` ist. Weitere Informationen finden Sie unter [delegate (C++/CLI und C++/CX)](delegate-cpp-component-extensions.md).

    ```cpp
    delegate void MyDel();
    int main() {
    System::Console::WriteLine(__is_delegate(MyDel));
    }
    ```

- `__is_empty(`*Typ*`)`

   Gibt zurück, **`true`** Wenn der Typ keine instanzdatenmember aufweist.

    ```cpp
    #include <stdio.h>
    struct S {
    int Test() {}
    static int i;
    };
    int main() {
    __is_empty(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__is_enum(`*Typ*`)`

   Gibt zurück, **`true`** Wenn der Typ eine native Enum ist.

    ```cpp
    // is_enum.cpp
    #include <stdio.h>
    enum E { a, b };

    struct S {
    enum E2 { c, d };
    };

    int main() {
    __is_enum(E) == true ?
    printf("true\n") : printf("false\n");

    __is_enum(S::E2) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__is_interface_class(`*Typ*`)`

   Gibt zurück, **`true`** Wenn eine Platt Form Schnittstelle überschritten wurde. Weitere Informationen finden Sie unter [Schnittstellenklasse](interface-class-cpp-component-extensions.md).

    ```cpp
    // is_interface_class.cpp

    using namespace System;
    interface class I {};
    int main() {
    Console::WriteLine(__is_interface_class(I));
    }
    ```

- `__is_pod(`*Typ*`)`

   Gibt zurück **`true`** , wenn der Typ eine Klasse oder Union ohne Konstruktor oder private oder geschützte nicht statische Member, keine Basisklassen und keine virtuellen Funktionen ist. Weitere Informationen zu PODs finden Sie im C++-Standard in den Abschnitten 8.5.1/1, 9/4 und 3.9/10.

   `__is_pod` gibt „false“ für grundlegende Typen zurück.

    ```cpp
    #include <stdio.h>
    struct S {};

    int main() {
    __is_pod(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__is_polymorphic(`*Typ*`)`

   Gibt zurück, **`true`** Wenn ein System eigener Typ über virtuelle Funktionen verfügt.

    ```cpp
    #include <stdio.h>
    struct S {
    virtual void Test(){}
    };

    int main() {
    __is_polymorphic(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__is_ref_array(`*Typ*`)`

   Gibt zurück, **`true`** Wenn ein Platt Form Array überschritten wurde. Weitere Informationen finden Sie unter [Arrays](arrays-cpp-component-extensions.md).

    ```cpp
    using namespace System;
    int main() {
    array<int>^ x = gcnew array<int>(10);
    Console::WriteLine(__is_ref_array(array<int>));
    }
    ```

- `__is_ref_class(`*Typ*`)`

   Gibt zurück, **`true`** Wenn eine Verweis Klasse übermittelt wurde. Weitere Informationen zu benutzerdefinierten Verweistypen finden Sie unter [Klassen und Strukturen](classes-and-structs-cpp-component-extensions.md).

    ```cpp
    using namespace System;
    ref class R {};
    int main() {
    Console::WriteLine(__is_ref_class(Buffer));
    Console::WriteLine(__is_ref_class(R));
    }
    ```

- `__is_sealed(`*Typ*`)`

   Gibt zurück, **`true`** Wenn eine Plattform oder ein System eigener Typ, der als versiegelt gekennzeichnet Weitere Informationen finden Sie unter [sealed](sealed-cpp-component-extensions.md).

    ```cpp
    ref class R sealed{};
    int main() {
    System::Console::WriteLine(__is_sealed(R));
    }
    ```

- `__is_simple_value_class(`*Typ*`)`

   Gibt zurück **`true`** , wenn ein Werttyp übergeben wurde, der keine Verweise auf den Heap mit Garbage Collection enthält. Weitere Informationen zu benutzerdefinierten Werttypen finden Sie unter [Klassen und Strukturen](classes-and-structs-cpp-component-extensions.md).

    ```cpp
    using namespace System;
    ref class R {};
    value struct V {};
    value struct V2 {
    R ^ r;   // not a simnple value type
    };

    int main() {
    Console::WriteLine(__is_simple_value_class(V));
    Console::WriteLine(__is_simple_value_class(V2));
    }
    ```

- `__is_union(`*Typ*`)`

   Gibt zurück, **`true`** Wenn ein Typ eine Union ist.

    ```cpp
    #include <stdio.h>
    union A {
    int i;
    float f;
    };

    int main() {
    __is_union(A) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__is_value_class(`*Typ*`)`

   Gibt zurück, **`true`** Wenn ein Werttyp übermittelt wurde. Weitere Informationen zu benutzerdefinierten Werttypen finden Sie unter [Klassen und Strukturen](classes-and-structs-cpp-component-extensions.md).

    ```cpp
    value struct V {};

    int main() {
    System::Console::WriteLine(__is_value_class(V));
    }
    ```

## <a name="windows-runtime"></a>Windows-Runtime

### <a name="remarks"></a>Bemerkungen

Die `__has_finalizer(` *type* `)` typtypisierungs Eigenschaft wird nicht unterstützt, da diese Plattform keine Finalizer unterstützt.

### <a name="requirements"></a>Requirements (Anforderungen)

Compileroption: `/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

### <a name="remarks"></a>Bemerkungen

(Es gibt keine plattformspezifischen Hinweise für diese Funktion.)

### <a name="requirements"></a>Requirements (Anforderungen)

Compileroption: `/clr`

### <a name="examples"></a>Beispiele

**Beispiel**

Im folgenden Codebeispiel wird veranschaulicht, wie Sie mit einer Klassenvorlage eine Compiler-Typeigenschaft für eine `/clr`-Kompilierung verfügbar machen. Weitere Informationen finden Sie unter [Windows-Runtime und verwaltete Vorlagen](windows-runtime-and-managed-templates-cpp-component-extensions.md).

```cpp
// compiler_type_traits.cpp
// compile with: /clr
using namespace System;

template <class T>
ref struct is_class {
   literal bool value = __is_ref_class(T);
};

ref class R {};

int main () {
   if (is_class<R>::value)
      Console::WriteLine("R is a ref class");
   else
      Console::WriteLine("R is not a ref class");
}
```

```Output
R is a ref class
```

## <a name="see-also"></a>Weitere Informationen

[Komponenten Erweiterungen für .net und UWP](component-extensions-for-runtime-platforms.md)
