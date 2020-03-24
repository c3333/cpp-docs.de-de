---
title: Attributziele (C++/CLI und C++/CX)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- custom attributes, targets
ms.assetid: b4e6e224-da77-4520-b6e6-b96846e0ebc1
ms.openlocfilehash: fe2c1d27042b51300d01ba70b951b7601d87701e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80172619"
---
# <a name="attribute-targets-ccli-and-ccx"></a>Attributziele (C++/CLI und C++/CX)

Mit dem Attributnutzungsspezifizierer können Sie Attributziele angeben.  Jedes Attribut wird definiert, um auf bestimmte Sprachelemente angewendet zu werden. Beispielsweise könnte ein Attribut definiert werden, um nur auf Klassen und Strukturen angewendet zu werden.  Die folgende Liste enthält die möglichen syntaktischen Elemente, auf die ein benutzerdefiniertes Attribut angewendet werden kann. Kombinationen dieser Werte (mit logischem OR) sind möglich.

Um ein Attributziel anzugeben, übergeben Sie einen oder mehrere <xref:System.AttributeTargets> Enumeratoren beim Definieren des Attributs an <xref:System.AttributeUsageAttribute>.

Hier sind die gültigen Attributziele aufgelistet:

- `All` (gilt für alle Konstrukte)

    ```cpp
    using namespace System;
    [AttributeUsage(AttributeTargets::All)]
    ref class Attr : public Attribute {};

    [assembly:Attr];
    ```

- `Assembly` (gilt für eine Assembly als Ganzes)

    ```cpp
    using namespace System;
    [AttributeUsage(AttributeTargets::Assembly)]
    ref class Attr : public Attribute {};

    [assembly:Attr];
    ```

- `Module` (gilt für ein Modul als Ganzes)

    ```cpp
    using namespace System;
    [AttributeUsage(AttributeTargets::Module)]
    ref class Attr : public Attribute {};

    [module:Attr];
    ```

- `Class`

    ```cpp
    using namespace System;
    [AttributeUsage(AttributeTargets::Class)]
    ref class Attr : public System::Attribute {};

    [Attr]   // same as [class:Attr]
    ref class MyClass {};
    ```

- `Struct`

    ```cpp
    using namespace System;
    [AttributeUsage(AttributeTargets::Struct)]
    ref class Attr : public Attribute {};

    [Attr]   // same as [struct:Attr]
    value struct MyStruct{};
    ```

- `enum`

    ```cpp
    using namespace System;
    [AttributeUsage(AttributeTargets::Enum)]
    ref class Attr : public Attribute {};

    [Attr]   // same as [enum:Attr]
    enum struct MyEnum{e, d};
    ```

- `Constructor`

    ```cpp
    using namespace System;
    [AttributeUsage(AttributeTargets::Constructor)]
    ref class Attr : public Attribute {};

    ref struct MyStruct{
    [Attr] MyStruct(){}   // same as [constructor:Attr]
    };
    ```

- `Method`

    ```cpp
    using namespace System;
    [AttributeUsage(AttributeTargets::Method)]
    ref class Attr : public Attribute {};

    ref struct MyStruct{
    [Attr] void Test(){}   // same as [method:Attr]
    };
    ```

- `Property`

    ```cpp
    using namespace System;
    [AttributeUsage(AttributeTargets::Property)]
    ref class Attr : public Attribute {};

    ref struct MyStruct{
    [Attr] property int Test;   // same as [property:Attr]
    };
    ```

- `Field`

    ```cpp
    using namespace System;
    [AttributeUsage(AttributeTargets::Field)]
    ref class Attr : public Attribute {};

    ref struct MyStruct{
    [Attr] int Test;   // same as [field:Attr]
    };
    ```

- `Event`

    ```cpp
    using namespace System;
    [AttributeUsage(AttributeTargets::Event)]
    ref class Attr : public Attribute {};

    delegate void ClickEventHandler(int, double);

    ref struct MyStruct{
    [Attr] event ClickEventHandler^ OnClick;   // same as [event:Attr]
    };
    ```

- `Interface`

    ```cpp
    using namespace System;
    [AttributeUsage(AttributeTargets::Interface)]
    ref class Attr : public Attribute {};

    [Attr]   // same as [event:Attr]
    interface struct MyStruct{};
    ```

- `Parameter`

    ```cpp
    using namespace System;
    [AttributeUsage(AttributeTargets::Parameter)]
    ref class Attr : public Attribute {};

    ref struct MyStruct{
    void Test([Attr] int i);
    void Test2([parameter:Attr] int i);
    };
    ```

- `Delegate`

    ```cpp
    using namespace System;
    [AttributeUsage(AttributeTargets::Delegate)]
    ref class Attr : public Attribute {};

    [Attr] delegate void Test();
    [delegate:Attr] delegate void Test2();
    ```

- `ReturnValue`

    ```cpp
    using namespace System;
    [AttributeUsage(AttributeTargets::ReturnValue)]
    ref class Attr : public Attribute {};

    ref struct MyStruct {
    // Note required specifier
    [returnvalue:Attr] int Test() { return 0; }
    };
    ```

Ein Attribut wird in der Regel dem Sprachelement vorangestellt, auf das es angewendet wird. In einigen Fällen reicht jedoch die Position eines Attributs nicht aus, um das beabsichtigte Ziel des Attributs zu bestimmen. Betrachten Sie dieses Beispiel:

```cpp
[Attr] int MyFn(double x)...
```

Syntaktisch gesehen besteht keine Möglichkeit, festzustellen, ob das Attribut zur Anwendung auf die Methode oder den Rückgabewert der Methode bestimmt ist (in diesem Fall gilt standardmäßig die Anwendung auf die Methode). In solchen Fällen kann ein Attributnutzungsspezifizierer verwendet werden. Um das Attribut z.B. auf den Rückgabewert anzuwenden, verwenden Sie den `returnvalue`-Spezifizierer wie folgt:

```cpp
[returnvalue:Attr] int MyFn(double x)... // applies to return value
```

Attributnutzungsspezifizierer sind in den folgenden Situationen erforderlich:

- Um ein Attribut auf Assembly- oder Modulebene anzugeben.

- Um anzugeben, dass ein Attribut auf den Rückgabewert einer Methode, nicht die Methode angewendet wird:

    ```cpp
    [method:Attr] int MyFn(double x)...     // Attr applies to method
    [returnvalue:Attr] int MyFn(double x)...// Attr applies to return value
    [Attr] int MyFn(double x)...            // default: method
    ```

- Um anzugeben, dass ein Attribut auf den Accessor einer Eigenschaft, nicht die Eigenschaft angewendet wird:

    ```cpp
    [method:MyAttr(123)] property int Property()
    [property:MyAttr(123)] property int Property()
    [MyAttr(123)] property int get_MyPropy() // default: property
    ```

- Um anzugeben, dass ein Attribut auf den Accessor eines Ereignisses, nicht das Ereignis angewendet wird:

    ```cpp
    delegate void MyDel();
    ref struct X {
       [field:MyAttr(123)] event MyDel* MyEvent;   //field
       [event:MyAttr(123)] event MyDel* MyEvent;   //event
       [MyAttr(123)] event MyDel* MyEvent;   // default: event
    }
    ```

Ein Attributnutzungsspezifizierer wird nur auf das unmittelbar folgende Attribut angewendet, d.h.

```cpp
[returnvalue:Attr1, Attr2]
```

unterscheidet sich von

```cpp
[returnvalue:Attr1, returnvalue:Attr2]
```

## <a name="example"></a>Beispiel

### <a name="description"></a>BESCHREIBUNG

Dieses Beispiel zeigt, wie Sie mehrere Ziele angeben.

### <a name="code"></a>Code

```cpp
using namespace System;
[AttributeUsage(AttributeTargets::Class | AttributeTargets::Struct, AllowMultiple = true )]
ref struct Attr : public Attribute {
   Attr(bool i){}
   Attr(){}
};

[Attr]
ref class MyClass {};

[Attr]
[Attr(true)]
value struct MyStruct {};
```

## <a name="see-also"></a>Weitere Informationen

[Benutzerdefinierte Attribute](user-defined-attributes-cpp-component-extensions.md)
