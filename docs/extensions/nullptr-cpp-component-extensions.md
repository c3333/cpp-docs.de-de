---
title: nullptr (C++/CLI und C++/CX)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- __nullptr keyword (C++)
- nullptr keyword [C++]
ms.assetid: 594cfbf7-06cb-4366-9ede-c0b703e1d095
ms.openlocfilehash: 5e7a5d3f9a42968dee35f82d3f19d0fdb6da5d0c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214229"
---
# <a name="nullptr--ccli-and-ccx"></a>nullptr (C++/CLI und C++/CX)

Das **`nullptr`** Schlüsselwort stellt einen *null-Zeiger Wert*dar. Verwenden Sie einen NULL-Zeigerwert, um anzugeben, dass ein Zeiger des Typs „Objekthandle“, „Innerer Zeiger“ oder „Nativer Zeiger“ nicht auf ein Objekt zeigt.

Verwenden Sie **`nullptr`** entweder mit verwaltetem oder nativem Code. Der Compiler gibt geeignete, aber unterschiedliche Anweisungen für verwaltete und native NULL-Zeigerwerte aus. Informationen zur Verwendung der C++-Version nach ISO-Standard dieses Schlüsselworts finden Sie unter [nullptr](../cpp/nullptr.md).

Das **__nullptr** -Schlüsselwort ist ein Microsoft-spezifisches Schlüsselwort, das die gleiche Bedeutung wie hat **`nullptr`** , aber nur für nativen Code gilt. Wenn Sie **`nullptr`** mit nativem C/C++-Code verwenden und dann mit der [/CLR](../build/reference/clr-common-language-runtime-compilation.md) -Compileroption kompilieren, kann der Compiler nicht bestimmen, ob **`nullptr`** einen systemeigenen oder verwalteten NULL-Zeiger Wert angibt. Um die Absicht für den Compiler klar zu machen, verwenden **`nullptr`** Sie, um einen verwalteten Wert anzugeben, oder **__nullptr** , um einen systemeigenen Wert anzugeben.

Das **`nullptr`** -Schlüsselwort entspricht **Nothing** in Visual Basic und **null** in c#.

## <a name="usage"></a>Verbrauch

Das- **`nullptr`** Schlüsselwort kann überall dort verwendet werden, wo ein Handle, ein System eigener Zeiger oder ein Funktions Argument verwendet werden kann.

Das **`nullptr`** Schlüsselwort ist kein Typ und wird nicht für die Verwendung mit unterstützt:

- [sizeof](../cpp/sizeof-operator.md)

- [TypeId](../cpp/typeid-operator.md)

- `throw nullptr` (obwohl `throw (Object^)nullptr;` funktioniert)

Das- **`nullptr`** Schlüsselwort kann bei der Initialisierung der folgenden Zeiger Typen verwendet werden:

- Nativer Zeiger

- Windows-Runtime-Handle

- Verwaltetes Handle

- Verwalteter innerer Zeiger

Das- **`nullptr`** Schlüsselwort kann verwendet werden, um zu testen, ob ein Zeiger-oder Handle-Verweis null ist, bevor der Verweis verwendet wird.

Funktionsaufrufe zwischen Sprachen, die NULL-Zeigerwerte für die Fehlerüberprüfung verwenden, sollten richtig interpretiert werden.

Ein Handle kann nicht mit 0 (null) initialisiert werden. es **`nullptr`** kann nur verwendet werden. Die Zuweisung der Konstante 0 zu einem Objekthandle hat ein geschachteltes `Int32` und eine Umwandlung in `Object^` zur Folge.

## <a name="example"></a>Beispiel

Im folgenden Codebeispiel wird veranschaulicht, dass das- **`nullptr`** Schlüsselwort überall dort verwendet werden kann, wo ein Handle, ein System eigener Zeiger oder ein Funktions Argument verwendet werden kann. Das Beispiel zeigt, dass das- **`nullptr`** Schlüsselwort verwendet werden kann, um einen Verweis zu überprüfen, bevor es verwendet wird.

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

Das folgende Codebeispiel zeigt, dass **`nullptr`** und 0 (null) für Native Zeiger austauschbar verwendet werden können.

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

Das folgende Codebeispiel zeigt, dass **`nullptr`** als Handle für einen beliebigen Typ oder einen systemeigenen Zeiger auf einen beliebigen Typ interpretiert wird. Bei einer Funktionsüberladung mit Handles zu verschiedenen Typen wird ein Mehrdeutigkeitsfehler generiert. **`nullptr`** Muss explizit in einen-Typ umgewandelt werden.

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

Das folgende Codebeispiel zeigt, dass die Umwandlung **`nullptr`** zulässig ist, und gibt einen Zeiger oder ein Handle für den Umwandlungs Typen zurück, der den **`nullptr`** Wert enthält.

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

Im folgenden Codebeispiel wird gezeigt, dass **`nullptr`** als Funktionsparameter verwendet werden kann.

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

Im folgenden Codebeispiel wird veranschaulicht, dass beim Deklarieren und nicht expliziten Initialisieren von Handles der Standardwert für initialisiert wird **`nullptr`** .

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

Das folgende Codebeispiel zeigt, dass einem systemeigenen **`nullptr`** Zeiger zugewiesen werden kann, wenn Sie mit kompilieren `/clr` .

```cpp
// mcpp_nullptr_6.cpp
// compile with: /clr
int main() {
   int * i = 0;
   int * j = nullptr;
}
```

## <a name="requirements"></a>Requirements (Anforderungen)

Compileroption: (nicht erforderlich; wird von allen Code Generierungs Optionen unterstützt, einschließlich `/ZW` und `/clr` )

## <a name="see-also"></a>Weitere Informationen

[Komponenten Erweiterungen für .net und UWP](component-extensions-for-runtime-platforms.md)<br/>
[nullptr](../cpp/nullptr.md)
