---
title: ':::no-loc(extern)::: (C++)'
description: 'Leitfaden zum C++-Programmiersprachen :::no-loc(extern)::: Schlüsselwort.'
ms.date: 01/28/2020
f1_keywords:
- ':::no-loc(extern):::'
- :::no-loc(extern):::_CPP
helpviewer_keywords:
- ':::no-loc(extern)::: keyword [C++], linkage to non-C++ functions'
- declarations, :::no-loc(extern):::al
- ':::no-loc(extern):::al linkage, :::no-loc(extern)::: modifier'
ms.assetid: 1e2f0ae3-ae98-4410-85b5-222d6abc865a
no-loc:
- ':::no-loc(extern):::'
- ':::no-loc(const):::'
- ':::no-loc(constexpr):::'
- ':::no-loc(permissive):::'
ms.openlocfilehash: 510352f9e99e513f4a426f6ef89be4474085d97c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227503"
---
# <a name="no-locextern-c"></a>:::no-loc(extern)::: (C++)

Das **`:::no-loc(extern):::`** Schlüsselwort kann auf eine globale Variable, eine Funktion oder eine Vorlagen Deklaration angewendet werden. Gibt an, dass das Symbol über eine * :::no-loc(extern)::: Al-Verknüpfung*verfügt. Hintergrundinformationen über Verknüpfungen und Gründe für die Verwendung von globalen Variablen finden Sie unter [Übersetzungseinheiten und Verknüpfungen](program-and-linkage-cpp.md).

Das **`:::no-loc(extern):::`** Schlüsselwort hat abhängig vom Kontext vier Bedeutungen:

- Gibt in einer nicht **`:::no-loc(const):::`** globalen Variablen Deklaration **`:::no-loc(extern):::`** an, dass die Variable oder Funktion in einer anderen Übersetzungseinheit definiert ist. Der **`:::no-loc(extern):::`** muss in allen Dateien angewendet werden, mit Ausnahme derjenigen, in der die Variable definiert ist.

- In einer **`:::no-loc(const):::`** Variablen Deklaration gibt Sie an, dass die Variable über eine :::no-loc(extern)::: Al-Verknüpfung verfügt. **`:::no-loc(extern):::`** Muss auf alle Deklarationen in allen Dateien angewendet werden. (Globale **`:::no-loc(const):::`** Variablen haben standardmäßig interne Verknüpfungen.)

- ** :::no-loc(extern)::: "C"** gibt an, dass die Funktion an anderer Stelle definiert ist, und verwendet die Aufruf Konvention der C-Sprache. Der :::no-loc(extern)::: C-Modifizierer kann auch auf mehrere Funktions Deklarationen in einem-Block angewendet werden.

- Gibt in einer Vorlagen Deklaration an, **`:::no-loc(extern):::`** dass die Vorlage bereits an anderer Stelle instanziiert wurde. **`:::no-loc(extern):::`** weist den Compiler an, dass die andere Instanziierung wieder verwendet werden kann, anstatt eine neue Instanz am aktuellen Speicherort zu erstellen. Weitere Informationen zu dieser Verwendung von **`:::no-loc(extern):::`** finden Sie unter [explizite Instanziierung](explicit-instantiation.md).

## <a name="no-locextern-linkage-for-non-no-locconst-globals"></a>:::no-loc(extern):::Verknüpfung für nicht- :::no-loc(const)::: Globals

Wenn der Linker **`:::no-loc(extern):::`** vor einer globalen Variablen Deklaration sieht, sucht er nach der Definition in einer anderen Übersetzungseinheit. Deklarationen von nicht **`:::no-loc(const):::`** Variablen im globalen Gültigkeitsbereich sind :::no-loc(extern)::: standardmäßig al. Gilt nur **`:::no-loc(extern):::`** für die Deklarationen, die die Definition nicht bereitstellen.

```cpp
//fileA.cpp
int i = 42; // declaration and definition

//fileB.cpp
:::no-loc(extern)::: int i;  // declaration only. same as i in FileA

//fileC.cpp
:::no-loc(extern)::: int i;  // declaration only. same as i in FileA

//fileD.cpp
int i = 43; // LNK2005! 'i' already has a definition.
:::no-loc(extern)::: int i = 43; // same error (:::no-loc(extern)::: is ignored on definitions)
```

## <a name="no-locextern-linkage-for-no-locconst-globals"></a>:::no-loc(extern):::Verknüpfung für :::no-loc(const)::: Globals

Eine **`:::no-loc(const):::`** globale Variable verfügt standardmäßig über interne Verknüpfungen. Wenn die Variable eine :::no-loc(extern)::: Al-Verknüpfung enthalten soll, wenden Sie das **`:::no-loc(extern):::`** -Schlüsselwort auf die Definition und alle anderen Deklarationen in anderen Dateien an:

```cpp
//fileA.cpp
:::no-loc(extern)::: :::no-loc(const)::: int i = 42; // :::no-loc(extern)::: :::no-loc(const)::: definition

//fileB.cpp
:::no-loc(extern)::: :::no-loc(const)::: int i;  // declaration only. same as i in FileA
```

## <a name="no-locextern-no-locconstexpr-linkage"></a>:::no-loc(extern)::::::no-loc(constexpr):::Verknüpfung

In Visual Studio 2017 Version 15,3 und früher gab der Compiler immer eine **`:::no-loc(constexpr):::`** interne Variablen Verknüpfung, auch wenn die Variable als markiert wurde **`:::no-loc(extern):::`** . In Visual Studio 2017 Version 15,5 und höher ermöglicht der [/Zc: :::no-loc(extern)::: constexpr](../build/reference/zc-:::no-loc(extern)::::::no-loc(constexpr):::.md) -Compilerschalter ein korrektes Standardverhalten. Schließlich wird die Option zum Standardwert. Die [/:::no-loc(permissive):::-](../build/reference/:::no-loc(permissive):::-standards-conformance.md) Option aktiviert **/Zc: :::no-loc(extern)::: constexpr**nicht.

```cpp
:::no-loc(extern)::: :::no-loc(constexpr)::: int x = 10; //error LNK2005: "int :::no-loc(const)::: x" already defined
```

Wenn eine Header Datei eine deklarierte Variable enthält **`:::no-loc(extern):::`** **`:::no-loc(constexpr):::`** , muss Sie so gekennzeichnet sein, dass `__declspec(selectany)` Ihre doppelten Deklarationen ordnungsgemäß kombiniert werden:

```cpp
:::no-loc(extern)::: :::no-loc(constexpr)::: __declspec(selectany) int x = 10;
```

## <a name="no-locextern-c-and-no-locextern-c-function-declarations"></a>:::no-loc(extern):::"C"-und :::no-loc(extern)::: "C++"-Funktions Deklarationen

Gibt in C++ bei Verwendung mit einer Zeichenfolge an, **`:::no-loc(extern):::`** dass die Verknüpfungs Konventionen einer anderen Sprache für die Deklaratoren verwendet werden. Auf c-Funktionen und-Daten kann nur zugegriffen werden, wenn Sie zuvor als c-Verknüpfung deklariert wurden. Allerdings müssen sie in einer separat kompilierten Übersetzungseinheit definiert sein.

Microsoft C++ unterstützt die Zeichen folgen **"C"** und **"C++"** im Feld *Zeichenfolgenliteral.* Alle standardmäßigen Includedateien verwenden die ** :::no-loc(extern)::: C** -Syntax, damit die Lauf Zeit Bibliotheksfunktionen in C++-Programmen verwendet werden können.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird gezeigt, wie Namen mit C-Verknüpfung deklariert werden:

```cpp
// Declare printf with C linkage.
:::no-loc(extern)::: "C" int printf(:::no-loc(const)::: char *fmt, ...);

//  Cause everything in the specified
//  header files to have C linkage.
:::no-loc(extern)::: "C" {
    // add your #include statements here
#include <stdio.h>
}

//  Declare the two functions ShowChar
//  and GetChar with C linkage.
:::no-loc(extern)::: "C" {
    char ShowChar(char ch);
    char GetChar(void);
}

//  Define the two functions
//  ShowChar and GetChar with C linkage.
:::no-loc(extern)::: "C" char ShowChar(char ch) {
    putchar(ch);
    return ch;
}

:::no-loc(extern)::: "C" char GetChar(void) {
    char ch;
    ch = getchar();
    return ch;
}

// Declare a global variable, errno, with C linkage.
:::no-loc(extern)::: "C" int errno;
```

Wenn eine Funktion über mehr als eine Verknüpfungs Spezifikation verfügt, müssen Sie zustimmen. Es ist ein Fehler, Funktionen als C-und C++-Verknüpfung zu deklarieren. Wenn darüber hinaus zwei Deklarationen für eine Funktion in einem Programm auftreten – eine mit einer Verknüpfungsspezifikation und eine ohne – muss die Deklaration mit der Verknüpfungsspezifikation die erste sein. Alle redundanten Deklarationen von Funktionen, die bereits eine Verknüpfungsspezifikation haben, erhalten die in der ersten Deklaration angegebene Bindung. Beispiel:

```cpp
:::no-loc(extern)::: "C" int CFunc1();
...
int CFunc1();            // Redeclaration is benign; C linkage is
                         //  retained.

int CFunc2();
...
:::no-loc(extern)::: "C" int CFunc2(); // Error: not the first declaration of
                         //  CFunc2;  cannot contain linkage
                         //  specifier.
```

## <a name="see-also"></a>Siehe auch

[Keywords](../cpp/keywords-cpp.md)\
[Übersetzungseinheiten und Verknüpfungen](program-and-linkage-cpp.md)\
[:::no-loc(extern):::Speicherklassenspezifizierer in C](../c-language/:::no-loc(extern):::-storage-class-specifier.md)\
[Verhalten von bezeichlern in C](../c-language/behavior-of-identifiers.md)\
[Verknüpfung in C](../c-language/linkage.md)
