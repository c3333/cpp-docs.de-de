---
title: MSVC experimentellepräprozessorische Übersicht
description: Der MSVC-Präprozessor wird entsprechend den C/C++-Standards aktualisiert.
ms.date: 02/09/2020
helpviewer_keywords:
- preprocessor, experimental
ms.openlocfilehash: 00c34ef75270e505d3781cf7eedf4d8aba95ee6e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81337484"
---
# <a name="msvc-experimental-preprocessor-overview"></a>MSVC experimentellepräprozessorische Übersicht

::: moniker range="vs-2015"

Visual Studio 2015 verwendet den herkömmlichen Präprozessor, der nicht mit Standard C++ übereinstimmt. Ein experimenteller Präprozessor ist in Visual Studio 2017 und Visual Studio 2019 mit dem Compiler-Switch [/experimental:preprocessor](../build/reference/experimental-preprocessor.md) verfügbar. Weitere Informationen zur Verwendung des neuen Präprozessors in Visual Studio 2017 und Visual Studio 2019 sind verfügbar. Verwenden Sie das Versionsauswahlsteuerelement, um die **Version** Dokumentation für Ihre bevorzugte Version von Visual Studio anzuzeigen. Es befindet sich oben im Inhaltsverzeichnis auf dieser Seite.

::: moniker-end

::: moniker range=">=vs-2017"

Wir aktualisieren den Microsoft C++-Präprozessor, um die Standardkonformität zu verbessern, langjährige Fehler zu beheben und einige Verhaltensweisen zu ändern, die offiziell nicht definiert sind. Wir haben auch neue Diagnosen hinzugefügt, um vor Fehlern in Makrodefinitionen zu warnen.

Diese Änderungen sind über den Compilerschalter [/experimental:preprocessor](../build/reference/experimental-preprocessor.md) in Visual Studio 2017 oder Visual Studio 2019 verfügbar. Das Standardverhalten des Präprozessors bleibt das gleiche wie in früheren Versionen.

Ab Visual Studio 2019 Version 16.5 ist die experimentelle Preprozessorunterstützung für den C++20-Standard funktionsdurchtiert.

## <a name="new-predefined-macro"></a>Neues vordefiniertes Makro

Sie können erkennen, welcher Präprozessor zur Kompilierungszeit verwendet wird. Überprüfen Sie den Wert des vordefinierten Makros [ \_\_MSVC TRADITIONAL,](predefined-macros.md) um zu erkennen, ob der herkömmliche Präprozessor verwendet wird. Dieses Makro wird bedingungslos von Versionen des Compilers festgelegt, die es unterstützen, unabhängig davon, welcher Präprozessor aufgerufen wird. Sein Wert ist 1 für den traditionellen Präprozessor. Es ist 0 für den konformen Präprozessor.

```cpp
#if defined(_MSVC_TRADITIONAL) && _MSVC_TRADITIONAL
// Logic using the traditional preprocessor
#else
// Logic using cross-platform compatible preprocessor
#endif
```

## <a name="behavior-changes-in-the-experimental-preprocessor"></a>Verhaltensänderungen im experimentellen Präprozessor

Die ersten Arbeiten am experimentellen Präprozessor konzentrierten sich darauf, alle Makroerweiterungen an den Standard anzupassen. Sie können den MSVC-Compiler mit Bibliotheken verwenden, die derzeit durch die herkömmlichen Verhaltensweisen blockiert sind. Wir haben den aktualisierten Präprozessor bei realen Projekten getestet. Hier sind einige der häufigsten Änderungen, die wir gefunden haben:

### <a name="macro-comments"></a>Makrokommentare

Der herkömmliche Präprozessor basiert auf Zeichenpuffern und nicht auf Präprozessortoken. Es erlaubt ungewöhnliches Verhalten wie den folgenden Präprozessorkommentar-Trick, der unter dem konformen Präprozessor nicht funktioniert:

```cpp
#if DISAPPEAR
#define DISAPPEARING_TYPE /##/
#else
#define DISAPPEARING_TYPE int
#endif

// myVal disappears when DISAPPEARING_TYPE is turned into a comment
DISAPPEARING_TYPE myVal;
```

Die normkonforme Fixistierung `int myVal` besteht `#ifdef/#endif` darin, innerhalb der entsprechenden Richtlinien zu deklarieren:

```cpp
#define MYVAL 1

#ifdef MYVAL
int myVal;
#endif
```

### <a name="lval"></a>L-val

Der herkömmliche Präprozessor kombiniert fälschlicherweise ein Zeichenfolgenpräfix mit dem Ergebnis des [Stringizing-Operators(](stringizing-operator-hash.md)

```cpp
 #define DEBUG_INFO(val) L"debug prefix:" L#val
//                                       ^
//                                       this prefix

const wchar_t *info = DEBUG_INFO(hello world);
```

In diesem Fall `L` ist das Präfix nicht erforderlich, da die angrenzenden Zeichenfolgenliterale ohnehin nach der Makroerweiterung kombiniert werden. Die abwärtskompatible Lösung besteht darin, die Definition zu ändern:

```cpp
#define DEBUG_INFO(val) L"debug prefix:" #val
//                                       ^
//                                       no prefix
```

Das gleiche Problem findet sich auch in Convenience-Makros, die das Argument in ein breites Zeichenfolgenliteral "saitieren":

```cpp
 // The traditional preprocessor creates a single wide string literal token
#define STRING(str) L#str
```

Sie können das Problem auf verschiedene Weise beheben:

- Verwenden Sie die `L""` Zeichenfolgenverkettung von und `#str` zum Hinzufügen eines Präfixes. Benachbarte Zeichenfolgenliterale werden nach der Makroerweiterung kombiniert:

   ```cpp
   #define STRING1(str) L""#str
   ```

- Hinzufügen des Präfixes, nachdem `#str` es mit zusätzlicher Makroerweiterung zeichenfolgeisiert wurde

   ```cpp
   #define WIDE(str) L##str
   #define STRING2(str) WIDE(#str)
   ```

- Verwenden Sie den `##` Verkettungsoperator, um die Token zu kombinieren. Die Reihenfolge der `##` `#` Vorgänge für und ist nicht angegeben, `#` obwohl `##` alle Compiler den Operator vor in diesem Fall auszuwerten scheinen.

   ```cpp
   #define STRING3(str) L## #str
   ```

### <a name="warning-on-invalid-"></a>Warnung bei ungültigen\#\#

Wenn der [Token-Pasting-Operator (-)](token-pasting-operator-hash-hash.md) nicht zu einem einzigen gültigen Vorverarbeitungstoken führt, ist das Verhalten nicht definiert. Der herkömmliche Präprozessor kann die Token nicht im Hintergrund kombinieren. Der neue Präprozessor entspricht dem Verhalten der meisten anderen Compiler und gibt eine Diagnose aus.

```cpp
// The ## is unnecessary and does not result in a single preprocessing token.
#define ADD_STD(x) std::##x
// Declare a std::string
ADD_STD(string) s;
```

### <a name="comma-elision-in-variadic-macros"></a>Komma-Elision in variadischen Makros

Der herkömmliche MSVC-Präprozessor entfernt immer `__VA_ARGS__` Kommas vor leeren Ersetzungen. Der experimentelle Präprozessor folgt dem Verhalten anderer beliebter plattformübergreifender Compiler genauer. Damit das Komma entfernt werden kann, muss das variadische Argument fehlen (nicht nur leer) und mit einem `##` Operator gekennzeichnet sein. Betrachten Sie das folgenden Beispiel:

```cpp
void func(int, int = 2, int = 3);
// This macro replacement list has a comma followed by __VA_ARGS__
#define FUNC(a, ...) func(a, __VA_ARGS__)
int main()
{
    // In the traditional preprocessor, the
    // following macro is replaced with:
    // func(10,20,30)
    FUNC(10, 20, 30);

    // A conforming preprocessor replaces the
    // following macro with: func(1, ), which
    // results in a syntax error.
    FUNC(1, );
}
```

Im folgenden Beispiel fehlt im `FUNC2(1)` Aufruf des variadic-Arguments das aufgerufene Makro. Im Aufruf `FUNC2(1, )` des variadic-Arguments ist leer, aber nicht fehlen (beachten Sie das Komma in der Argumentliste).

```cpp
#define FUNC2(a, ...) func(a , ## __VA_ARGS__)
int main()
{
   // Expands to func(1)
   FUNC2(1);

   // Expands to func(1, )
   FUNC2(1, );
}
```

Im kommenden C++20-Standard wurde dieses Problem `__VA_OPT__`durch Hinzufügen von behoben. Experimentelle Präprozessorunterstützung `__VA_OPT__` für ist ab Visual Studio 2019 Version 16.5 verfügbar.

### <a name="c20-variadic-macro-extension"></a>C++20 variadic Makroerweiterung

Der experimentelle Präprozessor unterstützt c++20 variadic Macro Argument elision:

```cpp
#define FUNC(a, ...) __VA_ARGS__ + a
int main()
  {
  int ret = FUNC(0);
  return ret;
  }
```

Dieser Code entspricht nicht dem C++20-Standard. In MSVC erweitert der experimentelle Präprozessor dieses C++20-Verhalten**`/std:c++14`** auf **`/std:c++17`** niedrigere Sprachstandardmodi ( , ). Diese Erweiterung entspricht dem Verhalten anderer wichtiger plattformübergreifender C++-Compiler.

### <a name="macro-arguments-are-unpacked"></a>Makroargumente werden "entpackt"

Wenn ein Makro im herkömmlichen Präprozessor eines seiner Argumente an ein anderes abhängiges Makro weiterleitet, wird das Argument beim Einfügen nicht "entpackt". Normalerweise bleibt diese Optimierung unbemerkt, kann aber zu ungewöhnlichem Verhalten führen:

```cpp
// Create a string out of the first argument, and the rest of the arguments.
#define TWO_STRINGS( first, ... ) #first, #__VA_ARGS__
#define A( ... ) TWO_STRINGS(__VA_ARGS__)
const char* c[2] = { A(1, 2) };

// Conforming preprocessor results:
// const char c[2] = { "1", "2" };

// Traditional preprocessor results, all arguments are in the first string:
// const char c[2] = { "1, 2", };
```

Beim `A()`Erweitern leitet der traditionelle Präprozessor alle Argumente `__VA_ARGS__` weiter, die in das erste Argument von `TWO_STRINGS` TWO_STRINGS eingepackt sind, wodurch das variadische Argument leer bleibt. Das führt `#first` dazu, dass das Ergebnis "1, 2" und nicht nur "1" ist. Wenn Sie genau verfolgen, dann fragen Sie sich vielleicht, `#__VA_ARGS__` was mit dem Ergebnis der traditionellen Präprozessorerweiterung passiert ist: Wenn `""`der variadic Parameter leer ist, sollte er zu einem leeren Zeichenfolgenliteral führen. Ein separates Problem verhinderte, dass das leere Zeichenfolgenliteraltoken generiert wurde.

### <a name="rescanning-replacement-list-for-macros"></a>Erneutes Scannen der Ersatzliste für Makros

Nachdem ein Makro ersetzt wurde, werden die resultierenden Token erneut gescannt, um weitere Makrobezeichner zu ersetzen. Der Algorithmus, der vom herkömmlichen Präprozessor für den Rescan verwendet wird, entspricht nicht, wie in diesem Beispiel basierend auf dem tatsächlichen Code gezeigt:

```cpp
#define CAT(a,b) a ## b
#define ECHO(...) __VA_ARGS__
// IMPL1 and IMPL2 are implementation details
#define IMPL1(prefix,value) do_thing_one( prefix, value)
#define IMPL2(prefix,value) do_thing_two( prefix, value)

// MACRO chooses the expansion behavior based on the value passed to macro_switch
#define DO_THING(macro_switch, b) CAT(IMPL, macro_switch) ECHO(( "Hello", b))
DO_THING(1, "World");

// Traditional preprocessor:
// do_thing_one( "Hello", "World");
// Conforming preprocessor:
// IMPL1 ( "Hello","World");
```

Obwohl dieses Beispiel ein wenig ausgeklügelt erscheinen mag, haben wir es im realen Weltcode gesehen. Um zu sehen, was vor sich geht, `DO_THING`können wir die Erweiterung abbrechen:

1. `DO_THING(1, "World")`erweitert sich auf`CAT(IMPL, 1) ECHO(("Hello", "World"))`
1. `CAT(IMPL, 1)`erweitert sich `IMPL ## 1`auf , die sich auf`IMPL1`
1. Jetzt befinden sich die Token in diesem Zustand:`IMPL1 ECHO(("Hello", "World"))`
1. Der Präprozessor findet den funktionsähnlichen Makrobezeichner `IMPL1`. Da darauf keine `(`gefolgt wird, wird sie nicht als funktionsähnliche Makroaufrufe betrachtet.
1. Der Präprozessor wechselt zu den folgenden Token. Es findet das funktionsähnliche Makro `ECHO` `ECHO(("Hello", "World"))`wird aufgerufen: , das sich auf`("Hello", "World")`
1. `IMPL1`wird nie wieder für die Erweiterung in Betracht gezogen, so dass das vollständige Ergebnis der Erweiterungen ist:`IMPL1("Hello", "World");`

Um das Makro so zu ändern, dass es sich sowohl unter dem experimentellen als auch beim herkömmlichen Präprozessor gleich verhält, fügen Sie eine weitere Ebene der Indirektion hinzu:

```cpp
#define CAT(a,b) a##b
#define ECHO(...) __VA_ARGS__
// IMPL1 and IMPL2 are macros implementation details
#define IMPL1(prefix,value) do_thing_one( prefix, value)
#define IMPL2(prefix,value) do_thing_two( prefix, value)
#define CALL(macroName, args) macroName args
#define DO_THING_FIXED(a,b) CALL( CAT(IMPL, a), ECHO(( "Hello",b)))
DO_THING_FIXED(1, "World");

// macro expands to:
// do_thing_one( "Hello", "World");
```

## <a name="incomplete-features"></a>Unvollständige Funktionen

Ab Visual Studio 2019 Version 16.5 ist der experimentelle Präprozessor für C++20 funktionsdurcht. In früheren Versionen von Visual Studio ist der experimentelle Präprozessor größtenteils vollständig, obwohl einige Präprozessordirektivenlogik immer noch auf das traditionelle Verhalten zurückgreift. Hier ist eine unvollständige Liste unvollständiger Features in Visual Studio-Versionen vor 16.5:

- Unterstützung für `_Pragma`
- C++20-Funktionen
- Boost-Blockierungsfehler: Logische Operatoren in Präprozessorkonstantenausdrücken werden im neuen Präprozessor vor Version 16.5 nicht vollständig implementiert. Bei `#if` einigen Direktiven kann der neue Präprozessor auf den herkömmlichen Präprozessor zurückgreifen. Der Effekt ist nur spürbar, wenn Makros, die nicht mit dem herkömmlichen Präprozessor kompatibel sind, erweitert werden. Es kann passieren, wenn Boost-Preprozessor-Slots erstellen.

::: moniker-end
