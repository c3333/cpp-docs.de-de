---
title: /Zc:ternary (Regeln für bedingte Operatoren erzwingen)
ms.date: 09/12/2019
f1_keywords:
- /Zc:ternary
helpviewer_keywords:
- /Zc:ternary
- Zc:ternary
- -Zc:ternary
ms.openlocfilehash: 7c95f061e195ccf7fef8a6a21d193b257baa5f39
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81335681"
---
# <a name="zcternary-enforce-conditional-operator-rules"></a>/Zc:ternary (Regeln für bedingte Operatoren erzwingen)

Aktivieren Sie die Erzwingung von C++-Standardregeln für die Typen und die konstante oder flüchtige (cv) Qualifizierung des zweiten und dritten Operanden in einem bedingten Operatorausdruck.

## <a name="syntax"></a>Syntax

> **/Zc:ternary****-**[ ]

## <a name="remarks"></a>Bemerkungen

Ab Visual Studio 2017 unterstützt der Compiler das Verhalten des *C++-Standardbedingungsoperators* (**?:**). Es ist auch bekannt als der *ternäre Operator*. Der C++-Standard verlangt, dass ternäre Operanden eine von drei Bedingungen erfüllen: Die Operanden müssen vom gleichen Typ und **const** oder **volatileQualifikation** (cv-Qualifikation) sein, oder nur ein Operand muss eindeutig auf den gleichen Typ und die cv-Qualifikation wie die andere konvertierbar sein. Oder ein oder beide Operanden müssen ein Wurfausdruck sein. In Versionen vor Visual Studio 2017 Version 15.5 erlaubte der Compiler Konvertierungen, die vom Standard als mehrdeutig betrachtet werden.

Wenn die Option **/Zc:ternary** angegeben ist, entspricht der Compiler dem Standard. Es lehnt Code ab, der nicht den Regeln für übereinstimmende Typen und die cv-Qualifikation des zweiten und dritten Operanden entspricht.

Die Option **/Zc:ternary** ist in Visual Studio 2017 standardmäßig deaktiviert. Verwenden Sie **/Zc:ternary,** um das konforme Verhalten zu aktivieren, oder **/Zc:ternary-,** um explizit das vorherige nicht konforme Compilerverhalten anzugeben. Die Option [/permissive-](permissive-standards-conformance.md) aktiviert diese Option implizit, kann aber mit **/Zc:ternary-** überschrieben werden.

### <a name="examples"></a>Beispiele

Dieses Beispiel zeigt, wie eine Klasse, die sowohl die nicht explizite Initialisierung von einem Typ als auch die Konvertierung in einen Typ bereitstellt, zu mehrdeutigen Konvertierungen führen kann. Dieser Code wird standardmäßig vom Compiler akzeptiert, aber abgelehnt, wenn **/Zc:ternary** oder **/permissive-** angegeben wird.

```cpp
// zcternary1.cpp
// Compile by using: cl /EHsc /W4 /nologo /Zc:ternary zcternary1.cpp

struct A
{
   long l;
   A(int i) : l{i} {}    // explicit prevents conversion of int
   operator int() const { return static_cast<int>(l); }
};

int main()
{
   A a(42);
   // Accepted when /Zc:ternary (or /permissive-) is not used
   auto x = true ? 7 : a;  // old behavior prefers A(7) over (int)a
   auto y = true ? A(7) : a;   // always accepted
   auto z = true ? 7 : (int)a; // always accepted
   return x + y + z;
}
```

Um diesen Code zu beheben, erstellen Sie eine explizite Umwandlung in den bevorzugten allgemeinen Typ, oder verhindern Sie eine Richtung der Typkonvertierung. Sie können verhindern, dass der Compiler einer Typkonvertierung entspricht, indem Sie die Konvertierung explizit machen.

Eine wichtige Ausnahme von diesem allgemeinen Muster ist, wenn der Typ der Operanden `const char*`einer `const char16_t*`der null-terminierten Zeichenfolgentypen ist, z. B. , usw. Sie können den Effekt auch mit Arraytypen und den Zeigertypen reproduzieren, zu denen sie zerfallen. Das Verhalten, wenn der tatsächliche `?:` zweite oder dritte Operand ein Zeichenfolgenliteral des entsprechenden Typs ist, hängt vom verwendeten Sprachstandard ab. C++17 hat die Semantik für diesen Fall von C++14 geändert. Daher akzeptiert der Compiler den Code im folgenden Beispiel unter der Standardeinstellung **/std:c++14**, lehnt ihn jedoch ab, wenn Sie **/std:c++17**angeben.

```cpp
// zcternary2.cpp
// Compile by using: cl /EHsc /W4 /nologo /Zc:ternary /std:c++17 zcternary2.cpp

struct MyString
{
   const char * p;
   MyString(const char* s = "") noexcept : p{s} {} // from char*
   operator const char*() const noexcept { return p; } // to char*
};

int main()
{
   MyString s;
   auto x = true ? "A" : s; // MyString: permissive prefers MyString("A") over (const char*)s
}
```

Um diesen Code zu beheben, geben Sie einen der Operanden explizit ab.

Unter **/Zc:ternary**lehnt der Compiler bedingte Operatoren ab, bei denen eines der Argumente vom Typ **void**und das andere kein throw-Ausdruck ist. Dieses Muster wird häufig in ASSERT-ähnlichen Makros verwendet:

```cpp
// zcternary3.cpp
// Compile by using: cl /EHsc /W4 /nologo /Zc:ternary /c zcternary3.cpp

void myassert(const char* text, const char* file, int line);
#define ASSERT(ex) (void)((ex) ? 0 : myassert(#ex, __FILE__, __LINE__))
// To fix, define it this way instead:
// #define ASSERT(ex) (void)((ex) ? void() : myassert(#ex, __FILE__, __LINE__))

int main()
{
   ASSERT(false);  // C3447
}
```

Die typische Lösung besteht darin, das `void()`Argument "Nicht-void" durch zu ersetzen.

Dieses Beispiel zeigt Code, der einen Fehler unter **/Zc:ternary** und **/Zc:ternary-** generiert:

```cpp
// zcternary4.cpp
// Compile by using:
//   cl /EHsc /W4 /nologo /Zc:ternary zcternary4.cpp
//   cl /EHsc /W4 /nologo /Zc:ternary zcternary4.cpp

int main() {
   auto p1 = [](int a, int b) { return a > b; };
   auto p2 = [](int a, int b) { return a > b; };
   auto p3 = true ? p1 : p2; // C2593 under /Zc:ternary, was C2446
}
```

Dieser Code hat zuvor diesen Fehler gegeben:

```Output
error C2446: ':': no conversion from 'foo::<lambda_f6cd18702c42f6cd636bfee362b37033>' to 'foo::<lambda_717fca3fc65510deea10bc47e2b06be4>'
note: No user-defined-conversion operator available that can perform this conversion, or the operator cannot be called
```

Mit **/Zc:ternary**wird der Grund für das Scheitern klarer. Jede von mehreren implementierungsdefinierten Aufrufkonventionen kann verwendet werden, um jeden Lambda zu generieren. Der Compiler verfügt jedoch über keine Vorzugsregel, um die möglichen Lambdasignaturen zu disambiguieren. Die neue Ausgabe sieht wie folgt aus:

```Output
error C2593: 'operator ?' is ambiguous
note: could be 'built-in C++ operator?(bool (__cdecl *)(int,int), bool (__cdecl *)(int,int))'
note: or       'built-in C++ operator?(bool (__stdcall *)(int,int), bool (__stdcall *)(int,int))'
note: or       'built-in C++ operator?(bool (__fastcall *)(int,int), bool (__fastcall *)(int,int))'
note: or       'built-in C++ operator?(bool (__vectorcall *)(int,int), bool (__vectorcall *)(int,int))'
note: while trying to match the argument list '(foo::<lambda_717fca3fc65510deea10bc47e2b06be4>, foo::<lambda_f6cd18702c42f6cd636bfee362b37033>)'
```

Eine häufige Ursache für Probleme, die von **/Zc:ternary** gefunden werden, stammt von bedingten Operatoren, die in der Vorlagenmetaprogrammierung verwendet werden. Einige der Ergebnistypen ändern sich unter diesem Schalter. Das folgende Beispiel zeigt zwei Fälle, in denen **/Zc:ternary** den Ergebnistyp eines bedingten Ausdrucks in einem Kontext ohne Metaprogrammierung ändert:

```cpp
// zcternary5.cpp
// Compile by using: cl /EHsc /W4 /nologo /Zc:ternary zcternary5.cpp

int main(int argc, char**) {
   char a = 'A';
   const char b = 'B';
   decltype(auto) x = true ? a : b; // char without, const char& with /Zc:ternary
   const char(&z)[2] = argc > 3 ? "A" : "B"; // const char* without /Zc:ternary
   return x > *z;
}
```

Die typische Korrektur besteht `std::remove_reference` darin, eine Eigenschaft auf den Ergebnistyp anzuwenden, wo dies erforderlich ist, um das alte Verhalten beizubehalten.

Weitere Informationen über Konformitätsprobleme in Visual C++ finden Sie unter [Nonstandard Behavior](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>So legen Sie diese Compileroption in der Visual Studio-Entwicklungsumgebung fest

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** des Projekts. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Wählen Sie die Eigenschaftenseite **"Konfigurationseigenschaften** > **C/C++** > **Befehlszeile"** aus.

1. Ändern Sie die Eigenschaft **Zusätzliche Optionen,** um **/Zc:ternary** oder **/Zc:ternary-** einzuschließen, und wählen Sie dann **OK**aus.

## <a name="see-also"></a>Siehe auch

[/Zc (Übereinstimmung)](zc-conformance.md)
