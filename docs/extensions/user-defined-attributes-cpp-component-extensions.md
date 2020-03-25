---
title: Benutzerdefinierte Attribute (C++/CLI und C++/CX)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- metadata, extending
- custom attributes, extending metadata
ms.assetid: 98b29048-a3ea-4698-8441-f149cdaec9fb
ms.openlocfilehash: aed36ac7fed7eb1f16f8648f7bcd7efb37f43a75
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80171891"
---
# <a name="user-defined-attributes--ccli-and-ccx"></a>Benutzerdefinierte Attribute (C++/CLI und C++/CX)

Mit C++/CLI und C++/CX können Sie plattformspezifische Attribute erstellen, die die Metadaten einer Schnittstelle, Klasse oder Struktur, Methode, eines Parameters oder einer Enumeration erweitern. Diese Attribute unterscheiden sich von den [standardmäßigen C++-Attributen](../cpp/attributes.md).

## <a name="windows-runtime"></a>Windows-Runtime

Sie können C++/CX-Attribute auf Eigenschaften anwenden, aber nicht auf Konstruktoren oder Methoden.

### <a name="requirements"></a>Requirements (Anforderungen)

Compileroption: `/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

Die in diesem Thema vorgestellten Informationen und die vorgestellte Syntax sollen die Informationen unter [Attribut](../windows/attributes/attribute.md) ablösen.

Sie können ein benutzerdefiniertes Attribut definieren, indem Sie einen Typ definieren, <xref:System.Attribute> zur Basisklasse für den Typ machen und optional das <xref:System.AttributeUsageAttribute>-Attribut anwenden.

Weitere Informationen finden Sie unter

- [Attributziele](attribute-targets-cpp-component-extensions.md)

- [Attributparametertypen](attribute-parameter-types-cpp-component-extensions.md)

Informationen zum Signieren von Assemblys in Visual C++ finden Sie unter [Assemblys mit starken Namen (Assemblysignierung) (C++/CLI)](../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md).

### <a name="requirements"></a>Requirements (Anforderungen)

Compileroption: `/clr`

### <a name="examples"></a>Beispiele

Im folgenden Beispiel wird gezeigt, wie Sie ein benutzerdefiniertes Attribut definieren.

```cpp
// user_defined_attributes.cpp
// compile with: /clr /c
using namespace System;

[AttributeUsage(AttributeTargets::All)]
ref struct Attr : public Attribute {
   Attr(bool i){}
   Attr(){}
};

[Attr]
ref class MyClass {};
```

Das folgende Beispiel veranschaulicht einige wichtige Features benutzerdefinierter Attribute. Dieses Beispiel zeigt eine häufige Verwendung der benutzerdefinierten Attribute: Instanziieren eines Servers, der sich gegenüber Clients vollständig selbst beschreiben kann.

```cpp
// extending_metadata_b.cpp
// compile with: /clr
using namespace System;
using namespace System::Reflection;

public enum class Access { Read, Write, Execute };

// Defining the Job attribute:
[AttributeUsage(AttributeTargets::Class, AllowMultiple=true )]
public ref class Job : Attribute {
public:
   property int Priority {
      void set( int value ) { m_Priority = value; }
      int get() { return m_Priority; }
   }

   // You can overload constructors to specify Job attribute in different ways
   Job() { m_Access = Access::Read; }
   Job( Access a ) { m_Access = a; }
   Access m_Access;

protected:
   int m_Priority;
};

interface struct IService {
   void Run();
};

   // Using the Job attribute:
   // Here we specify that QueryService is to be read only with a priority of 2.
   // To prevent namespace collisions, all custom attributes implicitly
   // end with "Attribute".

[Job( Access::Read, Priority=2 )]
ref struct QueryService : public IService {
   virtual void Run() {}
};

// Because we said AllowMultiple=true, we can add multiple attributes
[Job(Access::Read, Priority=1)]
[Job(Access::Write, Priority=3)]
ref struct StatsGenerator : public IService {
   virtual void Run( ) {}
};

int main() {
   IService ^ pIS;
   QueryService ^ pQS = gcnew QueryService;
   StatsGenerator ^ pSG = gcnew StatsGenerator;

   //  use QueryService
   pIS = safe_cast<IService ^>( pQS );

   // use StatsGenerator
   pIS = safe_cast<IService ^>( pSG );

   // Reflection
   MemberInfo ^ pMI = pIS->GetType();
   array <Object ^ > ^ pObjs = pMI->GetCustomAttributes(false);

   // We can now quickly and easily view custom attributes for an
   // Object through Reflection */
   for( int i = 0; i < pObjs->Length; i++ ) {
      Console::Write("Service Priority = ");
      Console::WriteLine(static_cast<Job^>(pObjs[i])->Priority);
      Console::Write("Service Access = ");
      Console::WriteLine(static_cast<Job^>(pObjs[i])->m_Access);
   }
}
```

```Output
Service Priority = 0

Service Access = Write

Service Priority = 3

Service Access = Write

Service Priority = 1

Service Access = Read
```

Der `Object^`-Typ ersetzt den Variant-Datentyp. Das folgende Beispiel definiert ein benutzerdefiniertes Attribut, das von `Object^` ein Array als Parameter übernimmt.

Attributargumente müssen zur Kompilierzeit Konstanten sein; in den meisten Fällen sollten sie konstante Literale.

Unter [typeid](typeid-cpp-component-extensions.md) finden Sie Informationen zur Rückgabe eines Werts von System::Type aus einem benutzerdefinierten Attributblock.

```cpp
// extending_metadata_e.cpp
// compile with: /clr /c
using namespace System;
[AttributeUsage(AttributeTargets::Class | AttributeTargets::Method)]
public ref class AnotherAttr : public Attribute {
public:
   AnotherAttr(array<Object^>^) {}
   array<Object^>^ var1;
};

// applying the attribute
[ AnotherAttr( gcnew array<Object ^> { 3.14159, "pi" }, var1 = gcnew array<Object ^> { "a", "b" } ) ]
public ref class SomeClass {};
```

Die Runtime erfordert, dass der öffentliche Teil des benutzerdefinierten Attributklasse serialisierbar sein muss.  Beim Erstellen benutzerdefinierter Attribute sind benannte Argumente Ihres benutzerdefinierten Attributs auf Konstanten zur Kompilierzeit beschränkt.  (Es handelt sich dabei um eine Sequenz von Bits, die Ihrem Klassenlayout in den Metadaten angefügt wird.)

```cpp
// extending_metadata_f.cpp
// compile with: /clr /c
using namespace System;
ref struct abc {};

[AttributeUsage( AttributeTargets::All )]
ref struct A : Attribute {
   A( Type^ ) {}
   A( String ^ ) {}
   A( int ) {}
};

[A( abc::typeid )]
ref struct B {};
```

## <a name="see-also"></a>Weitere Informationen

[Komponentenerweiterungen für .NET und UWP](component-extensions-for-runtime-platforms.md)
