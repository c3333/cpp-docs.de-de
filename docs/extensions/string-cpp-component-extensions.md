---
title: Zeichenfolge (C++/CLI und C++/CX)
ms.date: 10/08/2018
ms.topic: reference
helpviewer_keywords:
- string support with /clr
- /clr compiler option [C++], string support
ms.assetid: c695f965-9be0-4e20-9661-373bfee6557e
ms.openlocfilehash: b9da900ffbfff34dc596d8981095d8285bf37208
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80171943"
---
# <a name="string--ccli-and-ccx"></a>Zeichenfolge (C++/CLI und C++/CX)

Die Windows-Runtime und die Common Language Runtime stellen Zeichenfolgen als Objekte dar, deren belegter Speicher automatisch verwaltet wird. Das heißt, dass es nicht erforderlich ist, den Arbeitsspeicher für eine Zeichenfolge explizit zu verwerfen, wenn die Zeichenfolgenvariable außerhalb des gültigen Bereichs liegt oder die Anwendung beendet wird. Um anzugeben, dass die Lebensdauer eines Zeichenfolgenobjekts automatisch verwaltet werden soll, deklarieren Sie den Zeichenfolgentyp mit dem [handle-to-object (^)](handle-to-object-operator-hat-cpp-component-extensions.md)-Modifizierer.

## <a name="windows-runtime"></a>Windows-Runtime

Die Windows-Runtime-Architektur erfordert, den `String`-Datentyp im `Platform`-Namespace zu platzieren. Zur Vereinfachung stellt Visual C++ den `string`-Datentyp, der synonym mit `Platform::String` ist, auch im `default`-Namespace bereit.

### <a name="syntax"></a>Syntax

```cpp
// compile with /ZW
using namespace Platform;
using namespace default;
   Platform::String^ MyString1 = "The quick brown fox";
   String^ MyString2 = "jumped over the lazy dog.";
   String^ MyString3 = "Hello, world!";
```

### <a name="requirements"></a>Requirements (Anforderungen)

Compileroption: `/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

Beim Kompilieren mit `/clr` konvertiert der Compiler Zeichenfolgenliterale in Zeichenfolgen des Typs <xref:System.String>. Um die Abwärtskompatibilität mit vorhandenem Code beizubehalten, bestehen dabei die folgenden beiden Ausnahmen:

- Ausnahmebehandlung. Wenn ein Zeichenfolgenliteral ausgelöst wird, fängt der Compiler dieses auch als Zeichenfolgenliteral ab.

- Vorlagenableitung. Wenn ein Zeichenfolgenliteral als Vorlagenargument übergeben wird, wird es durch den Compiler nicht in <xref:System.String> konvertiert. Hinweis: Zeichenfolgenliterale, die als generisches Argument übergeben werden, werden zu <xref:System.String> höhergestuft.

Der Compiler verfügt auch über integrierte Unterstützung für drei Operatoren, die Sie überschreiben können, um ihr Verhalten anzupassen:

- System::String^ operator +( System::String, System::String);

- System::String^ operator +( System::Object, System::String);

- System::String^ operator +( System::String, System::Object);

Wenn ein <xref:System.String> übergeben wird, wird das Objekt (mit ToString) mit der Zeichenfolge vom Compiler geschachtelt und ggf. verkettet.

> [!NOTE]
> Das Caretzeichen ("^") gibt an, dass die deklarierte Variable ein Handle zu einem verwalteten C++/CLI-Objekt ist.

Weitere Informationen finden Sie unter [Zeichenfolgen- und Zeichenliterale (C++)](../cpp/string-and-character-literals-cpp.md).

### <a name="requirements"></a>Requirements (Anforderungen)

Compileroption: **/clr**

### <a name="examples"></a>Beispiele

Im folgenden Codebeispiel wird das Verketten und Vergleichen von Zeichenfolgen veranschaulicht.

```cpp
// string_operators.cpp
// compile with: /clr
// In the following code, the caret ("^") indicates that the
// declared variable is a handle to a C++/CLI managed object.
using namespace System;

int main() {
   String^ a = gcnew String("abc");
   String^ b = "def";   // same as gcnew form
   Object^ c = gcnew String("ghi");

   char d[100] = "abc";

   // variables of System::String returning a System::String
   Console::WriteLine(a + b);
   Console::WriteLine(a + c);
   Console::WriteLine(c + a);

   // accessing a character in the string
   Console::WriteLine(a[2]);

   // concatenation of three System::Strings
   Console::WriteLine(a + b + c);

   // concatenation of a System::String and string literal
   Console::WriteLine(a + "zzz");

   // you can append to a System::String^
   Console::WriteLine(a + 1);
   Console::WriteLine(a + 'a');
   Console::WriteLine(a + 3.1);

   // test System::String^ for equality
   a += b;
   Console::WriteLine(a);
   a = b;
   if (a == b)
      Console::WriteLine("a and b are equal");

   a = "abc";
   if (a != b)
      Console::WriteLine("a and b are not equal");

   // System:String^ and tracking reference
   String^% rstr1 = a;
   Console::WriteLine(rstr1);

   // testing an empty System::String^
   String^ n;
   if (n == nullptr)
      Console::WriteLine("n is empty");
}
```

```Output
abcdef

abcghi

ghiabc

c

abcdefghi

abczzz

abc1

abc97

abc3.1

abcdef

a and b are equal

a and b are not equal

abc

n is empty
```

Im folgenden Beispiel wird gezeigt, dass Sie die vom Compiler bereitgestellten Operatoren überladen können und vom Compiler eine Funktionsüberladung basierend auf dem <xref:System.String>-Typ gefunden wird.

```cpp
// string_operators_2.cpp
// compile with: /clr
using namespace System;

// a string^ overload will be favored when calling with a String
void Test_Overload(const char * a) {
   Console::WriteLine("const char * a");
}
void Test_Overload(String^ a) {
   Console::WriteLine("String^ a");
}

// overload will be called instead of compiler defined operator
String^ operator +(String^ a, String^ b) {
   return ("overloaded +(String^ a, String^ b)");
}

// overload will be called instead of compiler defined operator
String^ operator +(Object^ a, String^ b) {
   return ("overloaded +(Object^ a, String^ b)");
}

// overload will be called instead of compiler defined operator
String^ operator +(String^ a, Object^ b) {
   return ("overloaded +(String^ a, Object^ b)");
}

int main() {
   String^ a = gcnew String("abc");
   String^ b = "def";   // same as gcnew form
   Object^ c = gcnew String("ghi");

   char d[100] = "abc";

   Console::WriteLine(a + b);
   Console::WriteLine(a + c);
   Console::WriteLine(c + a);

   Test_Overload("hello");
   Test_Overload(d);
}
```

```Output
overloaded +(String^ a, String^ b)

overloaded +(String^ a, Object^ b)

overloaded +(Object^ a, String^ b)

String^ a

const char * a
```

Im folgenden Beispiel wird gezeigt, dass der Compiler zwischen systemeigenen Zeichenfolgen und <xref:System.String>-Zeichenfolgen unterscheidet.

```cpp
// string_operators_3.cpp
// compile with: /clr
using namespace System;
int func() {
   throw "simple string";   // const char *
};

int func2() {
   throw "string" + "string";   // returns System::String
};

template<typename T>
void func3(T t) {
   Console::WriteLine(T::typeid);
}

int main() {
   try {
      func();
   }
   catch(char * e) {
      Console::WriteLine("char *");
   }

   try {
      func2();
   }
   catch(String^ str) {
      Console::WriteLine("String^ str");
   }

   func3("string");   // const char *
   func3("string" + "string");   // returns System::String
}
```

```Output
char *

String^ str

System.SByte*

System.String
```

## <a name="see-also"></a>Weitere Informationen

[Komponentenerweiterungen für .NET und UWP](component-extensions-for-runtime-platforms.md)<br/>
[Zeichenfolgen- und Zeichenliterale](../cpp/string-and-character-literals-cpp.md)<br/>
[/clr (Common Language Runtime-Kompilierung)](../build/reference/clr-common-language-runtime-compilation.md)
