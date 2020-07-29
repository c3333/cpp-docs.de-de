---
title: typeid (C++/CLI und C++/CX)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- typeid keyword [C++]
ms.assetid: e9706cae-e7c4-4d6d-b474-646d73df3e70
ms.openlocfilehash: 56319fb773b8398f85f5fd82c812f0efdb7dde15
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225110"
---
# <a name="typeid--ccli-and-ccx"></a>typeid (C++/CLI und C++/CX)

Ruft einen Wert ab, der den Typ eines Objekts angibt.

> [!NOTE]
> Dieses Thema behandelt die C++-Komponentenerweiterungsversion von "typeid". Die ISO C++-Version dieses Schlüsselworts finden Sie unter [typeid-Operator](../cpp/typeid-operator.md).

## <a name="all-runtimes"></a>Alle Laufzeiten

### <a name="syntax"></a>Syntax

```cpp
T::typeid
```

### <a name="parameters"></a>Parameter

*T*<br/>
Ein Typname.

## <a name="windows-runtime"></a>Windows-Runtime

### <a name="syntax"></a>Syntax

```cpp
Platform::Type^ type = T::typeid;
```

### <a name="parameters"></a>Parameter

*T*<br/>
Ein Typname.

### <a name="remarks"></a>Bemerkungen

In C++/CX gibt „typeid“ einen [Platform::Type](../cppcx/platform-type-class.md) zurück, der aus Runtimetypinformationen erstellt wird.

### <a name="requirements"></a>Requirements (Anforderungen)

Compileroption: `/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

### <a name="syntax"></a>Syntax

```
type::typeid
```

### <a name="parameters"></a>Parameter

*type*<br/>
Der Name eines Typs (abstrakter Deklarator), für den das `System::Type`-Objekt gelten soll.

### <a name="remarks"></a>Bemerkungen

**`typeid`** wird verwendet, um den <xref:System.Type> für einen Typ zur Kompilierzeit zu erhalten.

**`typeid`** ähnelt dem erhalten der `System::Type` für einen Typ zur Laufzeit mit <xref:System.Type.GetType%2A> oder <xref:System.Object.GetType%2A> . Akzeptiert jedoch **`typeid`** nur einen Typnamen als Parameter.  Wenn Sie eine Instanz eines Typs verwenden möchten, um den Namen zu erhalten `System::Type` , verwenden Sie `GetType` .

**`typeid`** muss in der Lage sein, einen Typnamen (Typ) zur Kompilierzeit auszuwerten, wohingegen GetType den Typ auswertet, der zur Laufzeit zurückgegeben werden soll.

**`typeid`** kann einen systemeigenen Typnamen oder Common Language Runtime Alias für den nativen Typnamen verwenden. Weitere Informationen finden [Sie unter .NET Framework Entsprechungen zu C++ Native Types (C++/CLI)](../dotnet/dotnet-framework-equivalents-to-cpp-native-types-cpp-cli.md) .

**`typeid`** kann auch mit systemeigenen Typen verwendet werden, obwohl trotzdem ein zurückgegeben wird `System::Type` .  Um eine Type_info Struktur zu erhalten, verwenden Sie den- [ `typeid` Operator](../cpp/typeid-operator.md).

### <a name="requirements"></a>Requirements (Anforderungen)

Compileroption: `/clr`

### <a name="examples"></a>Beispiele

Im folgenden Beispiel wird das typeid-Schlüsselwort mit dem `GetType()`-Member verglichen.

```cpp
// keyword__typeid.cpp
// compile with: /clr
using namespace System;

ref struct G {
   int i;
};

int main() {
   G ^ pG = gcnew G;
   Type ^ pType = pG->GetType();
   Type ^ pType2 = G::typeid;

   if (pType == pType2)
      Console::WriteLine("typeid and GetType returned the same System::Type");
   Console::WriteLine(G::typeid);

   typedef float* FloatPtr;
   Console::WriteLine(FloatPtr::typeid);
}
```

```Output
typeid and GetType returned the same System::Type
G

System.Single*
```

Das folgende Beispiel zeigt, dass eine Variable des Typs System::Type verwendet werden kann, um die Attribute für einen Typ abzurufen.  Außerdem wird gezeigt, dass Sie für einige Typen eine typedef erstellen müssen, um zu verwenden **`typeid`** .

```cpp
// keyword__typeid_2.cpp
// compile with: /clr
using namespace System;
using namespace System::Security;
using namespace System::Security::Permissions;

typedef int ^ handle_to_int;
typedef int * pointer_to_int;

public ref class MyClass {};

class MyClass2 {};

[attribute(AttributeTargets::All)]
ref class AtClass {
public:
   AtClass(Type ^) {
      Console::WriteLine("in AtClass Type ^ constructor");
   }
};

[attribute(AttributeTargets::All)]
ref class AtClass2 {
public:
   AtClass2() {
      Console::WriteLine("in AtClass2 constructor");
   }
};

// Apply the AtClass and AtClass2 attributes to class B
[AtClass(MyClass::typeid), AtClass2]
[AttributeUsage(AttributeTargets::All)]
ref class B : Attribute {};

int main() {
   Type ^ MyType = B::typeid;

   Console::WriteLine(MyType->IsClass);

   array<Object^>^ MyArray = MyType -> GetCustomAttributes(true);
   for (int i = 0 ; i < MyArray->Length ; i++ )
      Console::WriteLine(MyArray[i]);

   if (int::typeid != pointer_to_int::typeid)
      Console::WriteLine("int::typeid != pointer_to_int::typeid, as expected");

   if (int::typeid == handle_to_int::typeid)
      Console::WriteLine("int::typeid == handle_to_int::typeid, as expected");
}
```

```Output
True

in AtClass2 constructor

in AtClass Type ^ constructor

AtClass2

System.AttributeUsageAttribute

AtClass

int::typeid != pointer_to_int::typeid, as expected

int::typeid == handle_to_int::typeid, as expected
```

## <a name="see-also"></a>Siehe auch

[Komponenten Erweiterungen für .net und UWP](component-extensions-for-runtime-platforms.md)
