---
title: /Zc:ternary (Regeln für bedingte Operatoren erzwingen)
ms.date: 09/12/2019
f1_keywords:
- /Zc:ternary
helpviewer_keywords:
- /Zc:ternary
- Zc:ternary
- -Zc:ternary
ms.openlocfilehash: 04bd0c49528d86ddd4d1e6c77804cf64278db188
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87211878"
---
# <a name="zcternary-enforce-conditional-operator-rules"></a>`/Zc:ternary`(Regeln für bedingten Operator erzwingen)

Aktivieren Sie die Erzwingung der C++-Standard Regeln für die Typen und die Konstante oder volatile-Qualifikation (CV) des zweiten und dritten Operanden in einem Bedingungs Operator Ausdruck.

## <a name="syntax"></a>Syntax

> **`/Zc:ternary`**[**`-`**]

## <a name="remarks"></a>Bemerkungen

Ab Visual Studio 2017 unterstützt der Compiler C++ Standardverhalten des *bedingten Operators* ( **`?:`** ). Sie wird auch als *ternärer Operator*bezeichnet. Der C++-Standard erfordert, dass ternäre Operanden eine von drei Bedingungen erfüllen: die Operanden müssen denselben Typ und **`const`** dieselbe **`volatile`** Qualifikation aufweisen (CV-Qualifizierung), oder nur ein Operand muss eindeutig in denselben Typ und die CV-Qualifikation konvertiert werden. Ein oder beide Operanden müssen ein Throw-Ausdruck sein. In Versionen vor Visual Studio 2017, Version 15,5, erlaubte der Compiler Konvertierungen, die vom Standard als mehrdeutig angesehen werden.

Wenn die **`/Zc:ternary`** Option angegeben wird, entspricht der Compiler dem Standard. Er lehnt Code ab, der die Regeln für übereinstimmende Typen und CV-Qualifizierung des zweiten und dritten Operanden nicht erfüllt.

Die **`/Zc:ternary`** Option ist in Visual Studio 2017 standardmäßig deaktiviert. Verwenden **`/Zc:ternary`** Sie, um ein konformes Verhalten zu aktivieren, oder, **`/Zc:ternary-`** um das vorherige nicht konforme Compilerverhalten explizit anzugeben. Die [`/permissive-`](permissive-standards-conformance.md) Option aktiviert diese Option implizit, kann jedoch mit überschrieben werden **`/Zc:ternary-`** .

### <a name="examples"></a>Beispiele

Dieses Beispiel zeigt, wie eine Klasse, die sowohl eine nicht explizite Initialisierung von einem-Typ als auch eine Konvertierung in einen-Typ bereitstellt, zu mehrdeutigen Konvertierungen führen kann. Dieser Code wird standardmäßig vom Compiler akzeptiert, wird jedoch zurückgewiesen, wenn **/`Zc:ternary`** oder **`/permissive-`** angegeben wird.

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

Um diesen Code zu korrigieren, nehmen Sie eine explizite Umwandlung in den bevorzugten allgemeinen Typ vor, oder verhindern Sie eine Richtung der Typkonvertierung. Sie können verhindern, dass der Compiler mit einer Typkonvertierung übereinstimmt, indem Sie die Konvertierung explizit vornehmen.

Eine wichtige Ausnahme für dieses gängige Muster ist, wenn der Typ der Operanden einem der null-terminierten Zeichen folgen Typen entspricht, `const char*` z `const char16_t*` . b., usw. Sie können den Effekt auch mit Array Typen und den Zeiger Typen reproduzieren, in die Sie verfallen. Das Verhalten, wenn der tatsächliche zweite oder dritte Operand in `?:` ein Zeichenfolgenliteralwert des entsprechenden Typs ist, hängt vom verwendeten Sprachstandard ab. C++ 17 hat die Semantik für diesen Fall von c++ 14 geändert. Folglich akzeptiert der Compiler den Code im folgenden Beispiel unter dem Standardwert **`/std:c++14`** , lehnt ihn jedoch ab, wenn Sie angeben **`/std:c++17`** .

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

Um diesen Code zu korrigieren, wandeln Sie einen der Operanden explizit um.

Unter **`/Zc:ternary`** lehnt der Compiler bedingte Operatoren ab, bei denen eines der Argumente vom Typ ist **`void`** und der andere kein- **`throw`** Ausdruck ist. Dieses Muster wird häufig in Assert-ähnlichen Makros verwendet:

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

Die typische Lösung besteht darin, das nicht-void-Argument durch zu ersetzen `void()` .

Dieses Beispiel zeigt Code, der einen Fehler sowohl unter **`/Zc:ternary`** als auch in generiert **`/Zc:ternary-`** :

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

Dieser Fehler wurde zuvor in diesem Code angezeigt:

```Output
error C2446: ':': no conversion from 'foo::<lambda_f6cd18702c42f6cd636bfee362b37033>' to 'foo::<lambda_717fca3fc65510deea10bc47e2b06be4>'
note: No user-defined-conversion operator available that can perform this conversion, or the operator cannot be called
```

Mit **`/Zc:ternary`** wird der Grund für den Fehler klarer. Jede der von der Implementierung definierten Aufruf Konventionen könnte verwendet werden, um die einzelnen Lambda-Ausdrücke zu generieren. Der Compiler hat jedoch keine bevorzugte Regel, um die möglichen Lambda-Signaturen eindeutig zu machen. Die neue Ausgabe sieht wie folgt aus:

```Output
error C2593: 'operator ?' is ambiguous
note: could be 'built-in C++ operator?(bool (__cdecl *)(int,int), bool (__cdecl *)(int,int))'
note: or       'built-in C++ operator?(bool (__stdcall *)(int,int), bool (__stdcall *)(int,int))'
note: or       'built-in C++ operator?(bool (__fastcall *)(int,int), bool (__fastcall *)(int,int))'
note: or       'built-in C++ operator?(bool (__vectorcall *)(int,int), bool (__vectorcall *)(int,int))'
note: while trying to match the argument list '(foo::<lambda_717fca3fc65510deea10bc47e2b06be4>, foo::<lambda_f6cd18702c42f6cd636bfee362b37033>)'
```

Eine häufige Ursache für Probleme, die von gefunden **`/Zc:ternary`** werden, stammt aus bedingten Operatoren, die in der Metaprogrammierung von Vorlagen verwendet Einige der Ergebnistypen ändern sich unter diesem Switch. Im folgenden Beispiel werden zwei Fälle veranschaulicht, in denen der **`/Zc:ternary`** Ergebnistyp eines bedingten Ausdrucks in einem nicht-metaprogrammierungs Kontext geändert wird:

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

Die typische Lösung ist das Anwenden eines `std::remove_reference` Merkmals auf den Ergebnistyp, sofern dies erforderlich ist, um das alte Verhalten beizubehalten.

Weitere Informationen über Konformitätsprobleme in Visual C++ finden Sie unter [Nonstandard Behavior](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>So legen Sie diese Compileroption in der Visual Studio-Entwicklungsumgebung fest

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** des Projekts. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Wählen Sie die **Eigenschaften Seite Konfigurations Eigenschaften**  >  **C/C++-**  >  **Befehlszeile** aus.

1. Ändern Sie die Eigenschaft **zusätzliche Optionen** so, dass oder einschließt, **`/Zc:ternary`** **`/Zc:ternary-`** und wählen Sie dann **OK**aus.

## <a name="see-also"></a>Weitere Informationen

[`/Zc`Konformitäts](zc-conformance.md)
