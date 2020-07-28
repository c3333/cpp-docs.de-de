---
title: Compilerfehler C2065
ms.date: 08/19/2019
f1_keywords:
- C2065
helpviewer_keywords:
- C2065
ms.assetid: 78093376-acb7-45f5-9323-5ed7e0aab1dc
ms.openlocfilehash: 68817498d6f29ef5982b72a2fee4e64a4423ccde
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214814"
---
# <a name="compiler-error-c2065"></a>Compilerfehler C2065

> "*Bezeichner*": nicht deklarierter Bezeichner

Der Compiler kann die Deklaration für einen Bezeichner nicht finden. Es gibt zahlreiche mögliche Ursachen für diesen Fehler. Die häufigsten Gründe für C2065 sind, dass der Bezeichner nicht deklariert wurde, der Bezeichner falsch geschrieben wurde, der Header, in dem der Bezeichner deklariert ist, nicht in der Datei enthalten ist, oder dem Bezeichner fehlt ein Bereichs Qualifizierer, z `cout` . b. anstelle von `std::cout` . Weitere Informationen zu Deklarationen in C++ finden Sie unter [Deklarationen und Definitionen (C++)](../../cpp/declarations-and-definitions-cpp.md).

Im folgenden finden Sie einige häufige Probleme und Lösungen ausführlicher.

## <a name="the-identifier-is-undeclared"></a>Der Bezeichner ist nicht deklariert.

Wenn der Bezeichner eine Variable oder ein Funktionsname ist, müssen Sie ihn vor der Verwendung deklarieren. Eine Funktionsdeklaration muss auch die Typen ihrer Parameter enthalten, bevor die Funktion verwendet werden kann. Wenn die Variable mit deklariert wird **`auto`** , muss der Compiler in der Lage sein, den Typ aus dem Initialisierer abzuleiten.

Wenn der Bezeichner ein Member einer Klasse oder Struktur ist oder in einem Namespace deklariert ist, muss er durch den Klassen-oder Struktur Namen oder den Namespace Namen qualifiziert werden, wenn er außerhalb der Struktur-, Klassen-oder Namespace-Gültigkeitsbereich verwendet wird. Alternativ muss der Namespace durch eine- **`using`** Direktive `using namespace std;` , z. b., eingefügt werden, oder der Elementname muss durch eine- **`using`** Deklaration, z. b., in den Gültigkeitsbereich eingefügt werden `using std::string;` . Andernfalls wird der nicht qualifizierte Name als nicht deklarierter Bezeichner im aktuellen Bereich betrachtet.

Wenn der Bezeichner das Tag für einen benutzerdefinierten Typ ist (z. b. **`class`** oder) **`struct`** , muss der Typ des Tags deklariert werden, bevor er verwendet werden kann. Beispielsweise muss die Deklaration `struct SomeStruct { /*...*/ };` vorhanden sein, bevor Sie eine Variable `SomeStruct myStruct;` im Code deklarieren können.

Wenn der Bezeichner ein Typalias ist, muss der Typ mit einer- **`using`** Deklaration oder vor der Verwendung deklariert werden **`typedef`** . Beispielsweise müssen Sie deklarieren, `using my_flags = std::ios_base::fmtflags;` bevor Sie `my_flags` als Typalias für verwenden können `std::ios_base::fmtflags` .

## <a name="example-misspelled-identifier"></a>Beispiel: falsch geschriebener Bezeichner

Dieser Fehler tritt häufig auf, wenn der Bezeichnername falsch geschrieben wurde, oder der Bezeichner falsche Groß-und Kleinbuchstaben verwendet. Der Name in der Deklaration muss exakt mit dem von Ihnen verwendeten Namen übereinstimmen.

```cpp
// C2065_spell.cpp
// compile with: cl /EHsc C2065_spell.cpp
#include <iostream>
using namespace std;
int main() {
    int someIdentifier = 42;
    cout << "Some Identifier: " << SomeIdentifier << endl;
    // C2065: 'SomeIdentifier': undeclared identifier
    // To fix, correct the spelling:
    // cout << "Some Identifier: " << someIdentifier << endl;
}
```

## <a name="example-use-an-unscoped-identifier"></a>Beispiel: Verwenden eines nicht Bereichs bezogenen Bezeichners

Dieser Fehler kann auftreten, wenn der Bezeichner nicht ordnungsgemäß Bereichs bezogen ist. Wenn C2065 bei Verwendung von angezeigt wird `cout` , ist dies die Ursache. Wenn die Funktionen und Operatoren der C++-Standard Bibliothek nicht vollständig durch den Namespace qualifiziert sind oder Sie den `std` Namespace nicht mit einer-Direktive in den aktuellen Gültigkeitsbereich gebracht haben **`using`** , kann der Compiler diese nicht finden. Um dieses Problem zu beheben, müssen Sie entweder die Bezeichnernamen vollständig qualifizieren oder den Namespace mit der- **`using`** Direktive angeben.

Dieses Beispiel kann nicht kompiliert werden, da `cout` und `endl` im- `std` Namespace definiert sind:

```cpp
// C2065_scope.cpp
// compile with: cl /EHsc C2065_scope.cpp
#include <iostream>
// using namespace std;   // Uncomment this line to fix

int main() {
    cout << "Hello" << endl;   // C2065 'cout': undeclared identifier
                               // C2065 'endl': undeclared identifier
    // Or try the following line instead
    std::cout << "Hello" << std::endl;
}
```

Bezeichner, die in-,-oder-Typen deklariert sind, **`class`** **`struct`** **`enum class`** müssen auch durch den Namen Ihres einschließenden Bereichs qualifiziert werden, wenn Sie Sie außerhalb dieses Bereichs verwenden.

## <a name="example-precompiled-header-isnt-first"></a>Beispiel: der vorkompilierte Header ist nicht der erste.

Dieser Fehler kann auftreten, wenn Sie vor dem #Include einer vorkompilierten Header Datei eine Präprozessordirektive, z. b. #include, #define oder #pragma, einfügen. Wenn die Quelldatei eine vorkompilierte Header Datei verwendet (d. h., wenn Sie mit der **/Yu** -Compileroption kompiliert wird), werden alle Präprozessordirektiven vor der vorkompilierten Header Datei ignoriert.

Dieses Beispiel kann nicht kompiliert `cout` `endl` werden, da und im- \<iostream> Header definiert sind, das ignoriert wird, da es vor der vorkompilierten Header Datei enthalten ist. Um dieses Beispiel zu erstellen, erstellen Sie alle drei Dateien, kompilieren Sie "stdafx. cpp", und kompilieren Sie dann C2065_pch. cpp.

```cpp
// pch.h (stdafx.h in Visual Studio 2017 and earlier)
#include <stdio.h>
```

```cpp
// pch.cpp (stdafx.cpp in Visual Studio 2017 and earlier)
// Compile by using: cl /EHsc /W4 /c /Ycstdafx.h stdafx.cpp
#include "pch.h"
```

```cpp
// C2065_pch.cpp
// compile with: cl /EHsc /W4 /Yustdafx.h C2065_pch.cpp
#include <iostream>
#include "stdafx.h"
using namespace std;

int main() {
    cout << "Hello" << endl;   // C2065 'cout': undeclared identifier
                               // C2065 'endl': undeclared identifier
}
```

Um dieses Problem zu beheben, fügen Sie die #include von der \<iostream> vorkompilierten Header Datei hinzu, oder verschieben Sie Sie, nachdem die vorkompilierte Header Datei in die Quelldatei eingefügt wurde.

## <a name="example-missing-header-file"></a>Beispiel: fehlende Header Datei

Sie haben die Header Datei, die den Bezeichner deklariert, nicht eingeschlossen. Stellen Sie sicher, dass die Datei, die die Deklaration für den Bezeichner enthält, in jeder Quelldatei enthalten ist, die Sie verwendet.

```cpp
// C2065_header.cpp
// compile with: cl /EHsc C2065_header.cpp

//#include <stdio.h>
int main() {
    fpos_t file_position = 42; // C2065: 'fpos_t': undeclared identifier
    // To fix, uncomment the #include <stdio.h> line
    // to include the header where fpos_t is defined
}
```

Eine weitere mögliche Ursache ist, wenn Sie eine Initialisiererliste ohne den- \<initializer_list> Header verwenden.

```cpp
// C2065_initializer.cpp
// compile with: cl /EHsc C2065_initializer.cpp

// #include <initializer_list>
int main() {
    for (auto strList : {"hello", "world"})
        if (strList == "hello") // C2065: 'strList': undeclared identifier
            return 1;
    // To fix, uncomment the #include <initializer_list> line
}
```

Dieser Fehler kann in Windows-Desktop-App-Quelldateien angezeigt werden `VC_EXTRALEAN` , wenn Sie, `WIN32_LEAN_AND_MEAN` oder definieren `WIN32_EXTRA_LEAN` . Diese Präprozessormakros schließen einige Header Dateien aus Windows. h und afxv \_ W32. h aus, um die Kompilierungen zu beschleunigen. Unter "Windows. h" und "afxv_w32. h" finden Sie eine aktuelle Beschreibung der ausgeschlossenen Elemente.

## <a name="example-missing-closing-quote"></a>Beispiel: Fehlendes Schließ Endes Anführungszeichen

Dieser Fehler kann auftreten, wenn ein Schließ Endes Anführungszeichen nach einer Zeichen folgen Konstante fehlt. Dies ist eine einfache Möglichkeit, um den Compiler zu verwechseln. Beachten Sie, dass das fehlende schließende Anführungszeichen möglicherweise mehrere Zeilen vor dem gemeldeten Fehler Speicherort ist.

```cpp
// C2065_quote.cpp
// compile with: cl /EHsc C2065_quote.cpp
#include <iostream>

int main() {
    // Fix this issue by adding the closing quote to "Aaaa"
    char * first = "Aaaa, * last = "Zeee";
    std::cout << "Name: " << first
        << " " << last << std::endl; // C2065: 'last': undeclared identifier
}
```

## <a name="example-use-iterator-outside-for-loop-scope"></a>Beispiel: Iterator außerhalb eines Schleifen Bereichs verwenden

Dieser Fehler kann auftreten, wenn Sie eine Iteratorvariable in einer **`for`** Schleife deklarieren und dann versuchen, diese Iteratorvariable außerhalb des Gültigkeits Bereichs der **`for`** Schleife zu verwenden. Der Compiler aktiviert standardmäßig die [/Zc: forScope](../../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md) -Compileroption. Weitere Informationen finden Sie [unter Debug Iterator Support](../../standard-library/debug-iterator-support.md) .

```cpp
// C2065_iter.cpp
// compile with: cl /EHsc C2065_iter.cpp
#include <iostream>
#include <string>

int main() {
    // char last = '!';
    std::string letters{ "ABCDEFGHIJKLMNOPQRSTUVWXYZ" };
    for (const char& c : letters) {
        if ('Q' == c) {
            std::cout << "Found Q!" << std::endl;
        }
        // last = c;
    }
    std::cout << "Last letter was " << c << std::endl; // C2065
    // Fix by using a variable declared in an outer scope.
    // Uncomment the lines that declare and use 'last' for an example.
    // std::cout << "Last letter was " << last << std::endl; // C2065
}
```

## <a name="example-preprocessor-removed-declaration"></a>Beispiel: Deklaration mit präprozessorentfernung

Dieser Fehler kann auftreten, wenn Sie auf eine Funktion oder Variable verweisen, die sich in bedingt kompiliertem Code befindet und nicht für die aktuelle Konfiguration kompiliert ist. Dies kann auch vorkommen, wenn Sie eine Funktion in einer Header Datei aufzurufen, die in der Buildumgebung derzeit nicht unterstützt wird. Wenn bestimmte Variablen oder Funktionen nur verfügbar sind, wenn ein bestimmtes Präprozessormakro definiert ist, stellen Sie sicher, dass der Code, der diese Funktionen aufruft, nur kompiliert werden kann, wenn das gleiche Präprozessormakro definiert ist. Dieses Problem lässt sich in der IDE leicht erkennen, da die Deklaration der-Funktion abgeblendet ist, wenn die erforderlichen Präprozessormakros nicht für die aktuelle Buildkonfiguration definiert sind.

Dies ist ein Beispiel für Code, der funktioniert, wenn Sie in Debug, aber nicht im Einzelhandel erstellen:

```cpp
// C2065_defined.cpp
// Compile with: cl /EHsc /W4 /MT C2065_defined.cpp
#include <iostream>
#include <crtdbg.h>
#ifdef _DEBUG
    _CrtMemState oldstate;
#endif
int main() {
    _CrtMemDumpStatistics(&oldstate);
    std::cout << "Total count " << oldstate.lTotalCount; // C2065
    // Fix by guarding references the same way as the declaration:
    // #ifdef _DEBUG
    //    std::cout << "Total count " << oldstate.lTotalCount;
    // #endif
}
```

## <a name="example-ccli-type-deduction-failure"></a>Beispiel: C++/CLI typableitungs Fehler

Dieser Fehler kann auftreten, wenn eine generische Funktion aufgerufen wird, wenn das beabsichtigte Typargument nicht aus den verwendeten Parametern abgeleitet werden kann. Weitere Informationen finden Sie unter [generische Funktionen (C++/CLI)](../../extensions/generic-functions-cpp-cli.md).

```cpp
// C2065_b.cpp
// compile with: cl /clr C2065_b.cpp
generic <typename ItemType>
void G(int i) {}

int main() {
   // global generic function call
   G<T>(10);     // C2065
   G<int>(10);   // OK - fix with a specific type argument
}
```

## <a name="example-ccli-attribute-parameters"></a>Beispiel: C++/CLI Attribute Parameters

Dieser Fehler kann auch infolge einer compilerübereinstimmungs-Arbeit generiert werden, die für Visual Studio 2005 ausgeführt wurde: Parameter Überprüfung für Visual C++ Attribute.

```cpp
// C2065_attributes.cpp
// compile with: cl /c /clr C2065_attributes.cpp
[module(DLL, name=MyLibrary)];   // C2065
// try the following line instead
// [module(dll, name="MyLibrary")];

[export]
struct MyStruct {
   int i;
};
```
