---
title: Verwaltete Typen (C++/CLI)
ms.date: 11/04/2016
helpviewer_keywords:
- data types [C++], managed
- managed data types [C++]
- .NET Framework [C++], managed types
- data types [C++], .NET feature access
- main function, in managed applications
- managed code, main() function
- .NET Framework [C++], C++ equivalents
- __nogc type declarations
- __value keyword, issues when nesting
- equality, testing for
- versioning, diagnosing conflicts
- versioning
- exceptions, diagnosing odd behavior
- compatibility, between assemblies
ms.assetid: 679b8ed3-d966-4a0c-b627-2a3f3ec96b74
ms.openlocfilehash: c542151bda780e5306db35049d988e6514fffd62
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225604"
---
# <a name="managed-types-ccli"></a>Verwaltete Typen (C++/CLI)

Visual C++ ermöglicht den Zugriff auf .NET-Funktionen über verwaltete Typen, die Unterstützung für Funktionen des Common Language Runtime bieten und den Vorteilen und Einschränkungen der Laufzeit unterliegen.

## <a name="managed-types-and-the-main-function"></a><a name="main_functions"></a>Verwaltete Typen und die Main-Funktion

Beim Schreiben einer Anwendung mit **`/clr`** können die Argumente der **Main ()** -Funktion keinen verwalteten Typ aufweisen.

Ein Beispiel für eine ordnungsgemäße Signatur ist:

```cpp
// managed_types_and_main.cpp
// compile with: /clr
int main(int, char*[], char*[]) {}
```

## <a name="net-framework-equivalents-to-c-native-types"></a><a name="dotnet"></a>.NET Framework Entsprechungen für Native C++-Typen

In der folgenden Tabelle sind die Schlüsselwörter für integrierte Visual C++ Typen aufgeführt, die Aliase vordefinierter Typen im **System** -Namespace sind.

|Visual C++-Typ|.NET Framework-Typ|
|-----------------------|-------------------------|
|**`void`**|<xref:System.Void?displayProperty=nameWithType>|
|**`bool`**|<xref:System.Boolean?displayProperty=nameWithType>|
|**`signed char`** |<xref:System.SByte?displayProperty=nameWithType>|
|**`unsigned char`**|<xref:System.Byte?displayProperty=nameWithType>|
|**`wchar_t`**|<xref:System.Char?displayProperty=nameWithType>|
|**`short`** und **`signed short`**|<xref:System.Int16?displayProperty=nameWithType>|
|**`unsigned short`**|<xref:System.UInt16?displayProperty=nameWithType>|
|**`int`**, **`signed int`** , **`long`** und**`signed long`**|<xref:System.Int32?displayProperty=nameWithType>|
|**`unsigned int`** und **`unsigned long`**|<xref:System.UInt32?displayProperty=nameWithType>|
|**`__int64`** und **`signed __int64`**|<xref:System.Int64?displayProperty=nameWithType>|
|**`unsigned __int64`**|<xref:System.UInt64?displayProperty=nameWithType>|
|**`float`**|<xref:System.Single?displayProperty=nameWithType>|
|**`double`** und **`long double`**|<xref:System.Double?displayProperty=nameWithType>|

Weitere Informationen zur-Compileroption, die standardmäßig **`signed char`** oder ist, finden Sie unter (der **`unsigned char`** [ `/J` Standardtyp **`char`** ist **`unsigned`** )](../build/reference/j-default-char-type-is-unsigned.md).

## <a name="version-issues-for-value-types-nested-in-native-types"></a><a name="version_issues"></a>Versions Probleme bei in systemeigenen Typen eingefügten Werttypen

Nehmen Sie eine signierte Assemblykomponente (Strong Name), die zum Erstellen einer Clientassembly verwendet wird. Die Komponente enthält einen Werttyp, der im Client als Typ für einen Member einer nativen Union, einer Klasse oder eines Arrays verwendet wird. Wenn eine zukünftige Version der Komponente die Größe oder das Layout des Werttyps ändert, muss der Client erneut kompiliert werden.

Erstellen Sie eine Schlüsseldatei mit [sn.exe](/dotnet/framework/tools/sn-exe-strong-name-tool) ( `sn -k mykey.snk` ).

### <a name="example"></a>Beispiel

Das folgende Beispiel ist die-Komponente.

```cpp
// nested_value_types.cpp
// compile with: /clr /LD
using namespace System::Reflection;
[assembly:AssemblyVersion("1.0.0.*"),
assembly:AssemblyKeyFile("mykey.snk")];

public value struct S {
   int i;
   void Test() {
      System::Console::WriteLine("S.i = {0}", i);
   }
};
```

### <a name="example"></a>Beispiel

Dieses Beispiel ist der Client:

```cpp
// nested_value_types_2.cpp
// compile with: /clr
#using <nested_value_types.dll>

struct S2 {
   S MyS1, MyS2;
};

int main() {
   S2 MyS2a, MyS2b;
   MyS2a.MyS1.i = 5;
   MyS2a.MyS2.i = 6;
   MyS2b.MyS1.i = 10;
   MyS2b.MyS2.i = 11;

   MyS2a.MyS1.Test();
   MyS2a.MyS2.Test();
   MyS2b.MyS1.Test();
   MyS2b.MyS2.Test();
}
```

### <a name="output"></a>Output

```Output
S.i = 5
S.i = 6
S.i = 10
S.i = 11
```

### <a name="comments"></a>Kommentare

Wenn Sie jedoch `struct S` in nested_value_types. cpp ein weiteres Element hinzufügen (z. b. `double d;` ) und die Komponente neu kompilieren, ohne den Client neu zu kompilieren, ist das Ergebnis eine unbehandelte Ausnahme (vom Typ <xref:System.IO.FileLoadException?displayProperty=fullName> ).

## <a name="how-to-test-for-equality"></a><a name="test_equality"></a>Gewusst wie: Überprüfen auf Gleichheit

Im folgenden Beispiel basiert ein Test auf Gleichheit, der Managed Extensions for C++ verwendet, auf dem, auf den die Handles verweisen.

### <a name="example"></a>Beispiel

```cpp
// mcppv2_equality_test.cpp
// compile with: /clr /LD
using namespace System;

bool Test1() {
   String ^ str1 = "test";
   String ^ str2 = "test";
   return (str1 == str2);
}
```

Die Il für dieses Programm zeigt, dass der Rückgabewert mithilfe eines Aufrufes op_Equality implementiert wird.

```MSIL
IL_0012:  call       bool [mscorlib]System.String::op_Equality(string,
                                                               string)
```

## <a name="how-to-diagnose-and-fix-assembly-compatibility-problems"></a><a name="diagnose_fix"></a>Vorgehensweise: diagnostizieren und Beheben von assemblykompatibilitäts Problemen

In diesem Thema wird erläutert, was passieren kann, wenn die Version einer Assembly, auf die zum Zeitpunkt der Kompilierung verwiesen wird, nicht mit der Version der Assembly identisch ist, auf die zur Laufzeit verwiesen wird.

Wenn eine Assembly kompiliert wird, kann auf andere Assemblys mit der-Syntax verwiesen werden `#using` . Während der Kompilierung wird der Compiler auf diese Assemblys zugreifen. Informationen aus diesen Assemblys werden verwendet, um Optimierungs Entscheidungen zu treffen.

Wenn jedoch die referenzierte Assembly geändert und neu kompiliert wird und Sie die referenzierende Assembly, die von ihr abhängt, nicht neu kompilieren, sind die Assemblys möglicherweise noch nicht kompatibel. Optimierungs Entscheidungen, die zuerst gültig waren, sind in Bezug auf die neue Assemblyversion möglicherweise nicht korrekt. Aufgrund dieser Inkompatibilitäten können verschiedene Laufzeitfehler auftreten. Es gibt keine bestimmte Ausnahme, die in solchen Fällen erzeugt wird. Die Art und Weise, wie der Fehler zur Laufzeit gemeldet wird, hängt von der Art der Codeänderung ab, die das Problem verursacht hat.

Diese Fehler sollten im endgültigen Produktionscode kein Problem darstellen, solange die gesamte Anwendung für die veröffentlichte Version Ihres Produkts neu erstellt wird. Assemblys, die für öffentlich freigegeben werden, müssen mit einer offiziellen Versionsnummer gekennzeichnet werden, um sicherzustellen, dass diese Probleme vermieden werden. Weitere Informationen dazu finden Sie unter [Assemblyversionen](/dotnet/framework/app-domains/assembly-versioning).

### <a name="diagnosing-and-fixing-an-incompatibility-error"></a>Diagnostizieren und Beheben eines Inkompatibilitäts Fehlers

1. Wenn Sie Lauf Zeit Ausnahmen oder andere Fehlerbedingungen auftreten, die in Code auftreten, der auf eine andere Assembly verweist, und keine andere identifizierte Ursache haben, können Sie mit einer veralteten Assembly arbeiten.

1. Isolieren und reproduzieren Sie zunächst die Ausnahme oder eine andere Fehlerbedingung. Ein Problem, das aufgrund einer veralteten Ausnahme auftritt, sollte reproduzierbar sein.

1. Überprüfen Sie den Zeitstempel aller Assemblys, auf die in der Anwendung verwiesen wird

1. Wenn die Zeitstempel aller Assemblys, auf die verwiesen wird, höher als der Zeitstempel der letzten Kompilierung der Anwendung ist, ist die Anwendung nicht mehr aktuell. Kompilieren Sie in diesem Fall die Anwendung mit der aktuellen Assembly neu, und nehmen Sie die erforderlichen Codeänderungen vor.

1. Führen Sie die Anwendung erneut aus, führen Sie die Schritte zum Reproduzieren des Problems aus, und vergewissern Sie sich, dass die Ausnahme nicht auftritt.

### <a name="example"></a>Beispiel

Das folgende Programm veranschaulicht das Problem, indem der Zugriff auf eine Methode reduziert und versucht wird, auf diese Methode in einer anderen Assembly zuzugreifen, ohne dass eine erneute Kompilierung durchführt. Kompilieren Sie `changeaccess.cpp` zuerst. Dabei handelt es sich um die Assembly, auf die verwiesen wird. Kompilieren Sie anschließend `referencing.cpp` . Die Kompilierung ist erfolgreich. Reduzieren Sie nun den Zugriff auf die aufgerufene Methode. Kompilieren Sie `changeaccess.cpp` mit dem-Flag erneut `/DCHANGE_ACCESS` . Dadurch wird die Methode anstelle von Privat geschützt, sodass Sie länger legal aufgerufen werden kann. Führen Sie die Anwendung erneut aus, ohne Sie neu kompilieren zu `referencing.exe` müssen. Eine Ausnahme <xref:System.MethodAccessException> wird ausgelöst.

```cpp
// changeaccess.cpp
// compile with: /clr:safe /LD
// After the initial compilation, add /DCHANGE_ACCESS and rerun
// referencing.exe to introduce an error at runtime. To correct
// the problem, recompile referencing.exe

public ref class Test {
#if defined(CHANGE_ACCESS)
protected:
#else
public:
#endif

  int access_me() {
    return 0;
  }

};
```

```cpp
// referencing.cpp
// compile with: /clr:safe
#using <changeaccess.dll>

// Force the function to be inline, to override the compiler's own
// algorithm.
__forceinline
int CallMethod(Test^ t) {
  // The call is allowed only if access_me is declared public
  return t->access_me();
}

int main() {
  Test^ t = gcnew Test();
  try
  {
    CallMethod(t);
    System::Console::WriteLine("No exception.");
  }
  catch (System::Exception ^ e)
  {
    System::Console::WriteLine("Exception!");
  }
  return 0;
}
```

## <a name="see-also"></a>Siehe auch

[.NET-Programmierung mit C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)<br/>
[Interoperabilität mit anderen .NET-Sprachen (C++/CLI)](../dotnet/interoperability-with-other-dotnet-languages-cpp-cli.md)<br/>
[Verwaltete Typen (C++/CLI)](../dotnet/managed-types-cpp-cli.md)<br/>
[#using-Direktive](../preprocessor/hash-using-directive-cpp.md)
