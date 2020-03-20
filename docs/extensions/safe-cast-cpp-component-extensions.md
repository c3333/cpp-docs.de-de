---
title: safe_cast (C++/CLI und C++/CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- safe_cast
- safe_cast_cpp
- stdcli::language::safe_cast
helpviewer_keywords:
- safe_cast keyword [C++]
ms.assetid: 4fa688bf-a8ec-49bc-a4c5-f48134efa4f7
ms.openlocfilehash: 42e141caed720aa29cf918a2bdf69d9a2c4203dc
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/15/2019
ms.locfileid: "79544639"
---
# <a name="safe_cast-ccli-and-ccx"></a>safe_cast (C++/CLI und C++/CX)

Der **safe_cast**-Vorgang gibt im Erfolgsfall den angegebenen Ausdruck als den angegebenen Typ zurück, andernfalls wird eine `InvalidCastException` ausgelöst.

## <a name="all-runtimes"></a>Alle Laufzeiten

(Es gibt keine Hinweise für diese Sprachfunktion, die für alle Laufzeiten gültig sind.)

### <a name="syntax"></a>Syntax

```cpp
[default]:: safe_cast< type-id >( expression )
```

## <a name="windows-runtime"></a>Windows-Runtime

Mit **safe_cast** können Sie den Typ eines angegebenen Ausdrucks ändern. In Situationen, in denen Sie mit Sicherheit erwarten, dass eine Variable oder ein Parameter zu einem bestimmten Typ konvertiert werden kann, können Sie **safe_cast** ohne einen **try-catch**-Block verwenden, um während der Entwicklung Programmierfehler zu ermitteln. Weitere Informationen finden Sie unter [Umwandlung (C++/CX)](../cppcx/casting-c-cx.md).

### <a name="syntax"></a>Syntax

```cpp
[default]:: safe_cast< type-id >( expression )
```

### <a name="parameters"></a>Parameter

*type-id*<br/>
Der Typ, zu dem *expression* konvertiert werden soll. Ein Handle zu einem Verweis- oder Werttyp, ein Werttyp oder ein Nachverfolgungsverweis auf einen Verweis- oder Werttyp.

*expression*<br/>
Ein Ausdruck, der als ein Handle zu einem Verweis oder Werttyp ausgewertet wird, ein Werttyp oder ein Nachverfolgungsverweis auf einen Verweis- oder Werttyp.

### <a name="remarks"></a>Hinweise

**safe_cast** löst `InvalidCastException` aus, wenn der *Ausdruck* nicht in den durch *Type-ID*angegebenen Typ konvertiert werden kann. Um `InvalidCastException`zu erfassen, geben Sie die Compileroption [/eh (Ausnahme Behandlungsmodell)](../build/reference/eh-exception-handling-model.md) an, und verwenden **Sie eine try/catch-** Anweisung.

### <a name="requirements"></a>Voraussetzungen

Compileroption: `/ZW`

### <a name="examples"></a>Beispiele

Der folgende Code veranschaulicht die Verwendung von **safe_cast** mit der Windows-Runtime.

```cpp
// safe_cast_ZW.cpp
// compile with: /ZW /EHsc

using namespace default;
using namespace Platform;

interface class I1 {};
interface class I2 {};
interface class I3 {};

ref class X : public I1, public I2 {};

int main(Array<String^>^ args) {
   I1^ i1 = ref new X;
   I2^ i2 = safe_cast<I2^>(i1);   // OK, I1 and I2 have common type: X
   // I2^ i3 = static_cast<I2^>(i1);   C2440 use safe_cast instead
   try {
      I3^ i4 = safe_cast<I3^>(i1);   // Fails because i1 is not derived from I3.
   }
   catch(InvalidCastException^ ic) {
   wprintf(L"Caught expected exception: %s\n", ic->Message);
   }
}
```

```Output
Caught expected exception: InvalidCastException
```

## <a name="common-language-runtime"></a>Common Language Runtime

Mit **safe_cast** können Sie den Typ eines Ausdrucks ändern und überprüfbaren MSIL-Code generieren.

### <a name="syntax"></a>Syntax

```cpp
[cli]:: safe_cast< type-id >( expression )
```

### <a name="parameters"></a>Parameter

*type-id*<br/>
Ein Handle zu einem Verweis- oder Werttyp, ein Werttyp oder ein Nachverfolgungsverweis auf einen Verweis- oder Werttyp.

*expression*<br/>
Ein Ausdruck, der als ein Handle zu einem Verweis oder Werttyp ausgewertet wird, ein Werttyp oder ein Nachverfolgungsverweis auf einen Verweis- oder Werttyp.

### <a name="remarks"></a>Hinweise

Der Ausdruck `safe_cast<`*type-id*`>(`*expression*`)` konvertiert den Operanden *expression* in ein Objekt vom Typ *type-id*.

Der Compiler akzeptiert [static_cast](../cpp/static-cast-operator.md) an den meisten Stellen, an denen auch **safe_cast** akzeptiert wird.  Allerdings erzeugt **safe_cast** garantiert eine überprüfbare MSIL, wohingegen **static_cast** eine nicht überprüfbare MSIL generieren könnte.  Weitere Informationen zu überprüfbarem Code finden Sie unter [Reiner und überprüfbarer Code (C++/CLI)](../dotnet/pure-and-verifiable-code-cpp-cli.md) und [Peverify.exe (PEVerify-Tool)](/dotnet/framework/tools/peverify-exe-peverify-tool).

Ähnlich wie **static_cast** ruft auch **safe_cast** benutzerdefinierte Konvertierungen auf.

Weitere Informationen zu Umwandlungen finden Sie unter [Umwandlungsoperatoren](../cpp/casting-operators.md).

**safe_cast** wendet kein **const_cast** an (kann **const** nicht umwandeln).

**safe_cast** befindet sich im cli-Namespace.  Weitere Informationen finden Sie unter [Namespaces „Platform“, „default“ und „cli“](platform-default-and-cli-namespaces-cpp-component-extensions.md).

Weitere Informationen über **safe_cast** finden Sie hier:

- [Umwandlungen im C-Stil mit /clr (C++/CLI)](c-style-casts-with-clr-cpp-cli.md)

- [Vorgehensweise: Verwenden von safe_cast in C++/CLI](../dotnet/how-to-use-safe-cast-in-cpp-cli.md)

### <a name="requirements"></a>Voraussetzungen

Compileroption: `/clr`

### <a name="examples"></a>Beispiele

Ein Beispiel, in dem der Compiler **static_cast** nicht akzeptiert, **safe_cast** jedoch akzeptiert, sind Umwandlungen zwischen nicht verknüpften Schnittstellentypen.  Mit **safe_cast** gibt der Compiler keinen Konvertierungsfehler aus und führt zur Laufzeit eine Überprüfung aus, um zu ermitteln, ob die Umwandlung möglich ist.

```cpp
// safe_cast.cpp
// compile with: /clr
using namespace System;

interface class I1 {};
interface class I2 {};
interface class I3 {};

ref class X : public I1, public I2 {};

int main() {
   I1^ i1 = gcnew X;
   I2^ i2 = safe_cast<I2^>(i1);   // OK, I1 and I2 have common type: X
   // I2^ i3 = static_cast<I2^>(i1);   C2440 use safe_cast instead
   try {
      I3^ i4 = safe_cast<I3^>(i1);   // fail at runtime, no common type
   }
   catch(InvalidCastException^) {
      Console::WriteLine("Caught expected exception");
   }
}
```

```Output
Caught expected exception
```

## <a name="see-also"></a>Siehe auch

[Komponentenerweiterungen für .NET und UWP](component-extensions-for-runtime-platforms.md)
