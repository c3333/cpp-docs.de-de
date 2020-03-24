---
title: nullptr (C++/CLI und C++/CX)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- __nullptr keyword (C++)
- nullptr keyword [C++]
ms.assetid: 594cfbf7-06cb-4366-9ede-c0b703e1d095
ms.openlocfilehash: 02da716959deb7fcffa7a63a8308279a765c4569
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80172113"
---
# <a name="nullptr--ccli-and-ccx"></a>nullptr (C++/CLI und C++/CX)

Das **nullptr**-Schlüsselwort stellt einen *NULL-Zeigerwert* dar. Verwenden Sie einen NULL-Zeigerwert, um anzugeben, dass ein Zeiger des Typs „Objekthandle“, „Innerer Zeiger“ oder „Nativer Zeiger“ nicht auf ein Objekt zeigt.

Verwenden Sie **nullptr** entweder mit verwaltetem oder nativem Code. Der Compiler gibt geeignete, aber unterschiedliche Anweisungen für verwaltete und native NULL-Zeigerwerte aus. Informationen zur Verwendung der C++-Version nach ISO-Standard dieses Schlüsselworts finden Sie unter [nullptr](../cpp/nullptr.md).

Das Microsoft-spezifische Schlüsselwort **__nullptr** entspricht zwar der Bedeutung von **nullptr**, ist aber nur auf nativen Code anwendbar. Wenn Sie **nullptr** mit nativem C/C++-Code verwenden und dann mit der [/clr](../build/reference/clr-common-language-runtime-compilation.md)-Compileroption kompilieren, kann der Compiler nicht ermitteln, ob **nullptr** einen nativen oder verwalteten NULL-Zeigerwert angibt. Um dem Compiler eindeutige Anweisungen zu geben, verwenden Sie **nullptr**, um einen verwalteten Wert anzugeben, oder **__nullptr**, um einen nativen Wert anzugeben.

Das **nullptr**-Schlüsselwort ist äquivalent zu **Nothing** in Visual Basic und **null** in C#.

## <a name="usage"></a>Verwendung

Das **nullptr**-Schlüsselwort kann überall dort verwendet werden, wo ein Handle, nativer Zeiger oder Funktionsargument verwendet werden kann.

Das **nullptr**-Schlüsselwort ist kein Typ und wird nicht unterstützt zur Verwendung mit:

- [sizeof](../cpp/sizeof-operator.md)

- [typeid](../cpp/typeid-operator.md)

- `throw nullptr` (obwohl `throw (Object^)nullptr;` funktioniert)

Das **nullptr**-Schlüsselwort kann bei der Initialisierung der folgenden Zeigertypen verwendet werden:

- Nativer Zeiger

- Windows-Runtime-Handle

- Verwaltetes Handle

- Verwalteter innerer Zeiger

Das **nullptr**-Schlüsselwort kann verwendet werden, um zu testen, ob ein Zeiger- oder Handleverweis gleich NULL ist, bevor der Verweis verwendet wird.

Funktionsaufrufe zwischen Sprachen, die NULL-Zeigerwerte für die Fehlerüberprüfung verwenden, sollten richtig interpretiert werden.

Sie können ein Handle nicht mit 0 (null) initialisieren; nur **nullptr** kann verwendet werden. Die Zuweisung der Konstante 0 zu einem Objekthandle hat ein geschachteltes `Int32` und eine Umwandlung in `Object^` zur Folge.

## <a name="example"></a>Beispiel

Im folgenden Codebeispiel wird veranschaulicht, dass das **nullptr**-Schlüsselwort überall dort verwendet werden kann, wo ein Handle, nativer Zeiger oder Funktionsargument verwendet werden kann. Außerdem zeigt das Beispiel, dass das **nullptr**-Schlüsselwort verwendet werden kann, um einen Verweis zu überprüfen, bevor er verwendet wird.

```cpp
// mcpp_nullptr.cpp
// compile with: /clr
value class V {};
ref class G {};
void f(System::Object ^) {}

int main() {
// Native pointer.
   int *pN = nullptr;
// Managed handle.
   G ^pG = nullptr;
   V ^pV1 = nullptr;
// Managed interior pointer.
   interior_ptr<V> pV2 = nullptr;
// Reference checking before using a pointer.
   if (pN == nullptr) {}
   if (pG == nullptr) {}
   if (pV1 == nullptr) {}
   if (pV2 == nullptr) {}
// nullptr can be used as a function argument.
   f(nullptr);   // calls f(System::Object ^)
}
```

## <a name="example"></a>Beispiel

Das folgende Codebeispiel zeigt, dass **nullptr** und 0 (null) bei nativen Zeigern austauschbar verwendet werden können.

```cpp
// mcpp_nullptr_1.cpp
// compile with: /clr
class MyClass {
public:
   int i;
};

int main() {
   MyClass * pMyClass = nullptr;
   if ( pMyClass == nullptr)
      System::Console::WriteLine("pMyClass == nullptr");

   if ( pMyClass == 0)
      System::Console::WriteLine("pMyClass == 0");

   pMyClass = 0;
   if ( pMyClass == nullptr)
      System::Console::WriteLine("pMyClass == nullptr");

   if ( pMyClass == 0)
      System::Console::WriteLine("pMyClass == 0");
}
```

```Output
pMyClass == nullptr

pMyClass == 0

pMyClass == nullptr

pMyClass == 0
```

## <a name="example"></a>Beispiel

Das folgende Codebeispiel zeigt, dass **nullptr** als Handle zu einem beliebigen Typ oder nativer Zeiger zu einem beliebigen Typ interpretiert wird. Bei einer Funktionsüberladung mit Handles zu verschiedenen Typen wird ein Mehrdeutigkeitsfehler generiert. **nullptr** müsste explizit in einen Typ umgewandelt werden.

```cpp
// mcpp_nullptr_2.cpp
// compile with: /clr /LD
void f(int *){}
void f(int ^){}

void f_null() {
   f(nullptr);   // C2668
   // try one of the following lines instead
   f((int *) nullptr);
   f((int ^) nullptr);
}
```

## <a name="example"></a>Beispiel

Im folgenden Codebeispiel wird veranschaulicht, dass die Umwandlung von **nullptr** zulässig ist und einen Zeiger bzw. ein Handle in den Umwandlungstyp zurückversetzt, der den **nullptr**-Wert enthält.

```cpp
// mcpp_nullptr_3.cpp
// compile with: /clr /LD
using namespace System;
template <typename T>
void f(T) {}   // C2036 cannot deduce template type because nullptr can be any type

int main() {
   f((Object ^) nullptr);   // T = Object^, call f(Object ^)

   // Delete the following line to resolve.
   f(nullptr);

   f(0);   // T = int, call f(int)
}
```

## <a name="example"></a>Beispiel

Das folgende Codebeispiel zeigt, dass **nullptr** als Funktionsparameter verwendet werden kann.

```cpp
// mcpp_nullptr_4.cpp
// compile with: /clr
using namespace System;
void f(Object ^ x) {
   Console::WriteLine("test");
}

int main() {
   f(nullptr);
}
```

```Output
test
```

## <a name="example"></a>Beispiel

Das folgende Codebeispiel zeigt, dass Handles, die deklariert und nicht explizit initialisiert sind, standardmäßig als **nullptr** initialisiert werden.

```cpp
// mcpp_nullptr_5.cpp
// compile with: /clr
using namespace System;
ref class MyClass {
public:
   void Test() {
      MyClass ^pMyClass;   // gc type
      if (pMyClass == nullptr)
         Console::WriteLine("NULL");
   }
};

int main() {
   MyClass ^ x = gcnew MyClass();
   x -> Test();
}
```

```Output
NULL
```

## <a name="example"></a>Beispiel

Das folgende Codebeispiel zeigt, dass **nullptr** einem nativen Zeiger zugewiesen werden kann, wenn Sie mit `/clr` kompilieren.

```cpp
// mcpp_nullptr_6.cpp
// compile with: /clr
int main() {
   int * i = 0;
   int * j = nullptr;
}
```

## <a name="requirements"></a>Requirements (Anforderungen)

Compileroption: (nicht erforderlich; wird von allen Code Generierungs Optionen unterstützt, einschließlich `/ZW` und `/clr`)

## <a name="see-also"></a>Weitere Informationen

[Komponentenerweiterungen für .NET und UWP](component-extensions-for-runtime-platforms.md)<br/>
[nullptr](../cpp/nullptr.md)
