---
title: Übersicht über den neuen MSVC-Präprozessor
description: Der MSVC-Präprozessor wird in Übereinstimmung mit den C/C++-Standards aktualisiert.
ms.date: 09/10/2020
helpviewer_keywords:
- preprocessor, experimental
- preprocessor, new
ms.openlocfilehash: c95f923d8c38250958e26431b61a71a1e6a7fdda
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/12/2020
ms.locfileid: "90041366"
---
# <a name="msvc-new-preprocessor-overview"></a>Übersicht über den neuen MSVC-Präprozessor

::: moniker range="vs-2015"

Visual Studio 2015 verwendet den herkömmlichen Präprozessor, der nicht mit den Standard mäßigen C++ oder C99 übereinstimmt. Ab Visual Studio 2019, Version 16,5, ist die neue präprozessorunterstützung für den c++ 20-Standard Feature-Complete. Diese Änderungen sind über den [/Zc: präprocessor](../build/reference/zc-preprocessor.md) -Compilerschalter verfügbar. Eine experimentelle Version des neuen Präprozessors ist ab Visual Studio 2017, Version 15,8 und höher, mit dem [/experimental: Präprozessor](../build/reference/experimental-preprocessor.md) Compiler-Schalter verfügbar. Weitere Informationen zur Verwendung des neuen Präprozessors in Visual Studio 2017 und Visual Studio 2019 sind verfügbar. Um die Dokumentation für Ihre bevorzugte Version von Visual Studio anzuzeigen, verwenden Sie das Auswahlsteuerelement **Version**. Es befindet sich am Anfang des Inhaltsverzeichnisses auf dieser Seite.

::: moniker-end

::: moniker range=">=vs-2017"

Wir aktualisieren den Microsoft C++-Präprozessor, um die Einhaltung von Standards zu verbessern, langjährige Fehler zu beheben und einige Verhaltensweisen zu ändern, die offiziell nicht definiert sind. Wir haben auch neue Diagnose hinzugefügt, um bei Fehlern in Makro Definitionen zu warnen.

Ab Visual Studio 2019 Version 16,5 ist die präprozessorunterstützung für den c++ 20-Standard Features-Complete. Diese Änderungen sind über den [/Zc: präprocessor](../build/reference/zc-preprocessor.md) -Compilerschalter verfügbar. Eine experimentelle Version des neuen Präprozessors steht in früheren Versionen ab Visual Studio 2017, Version 15,8, zur Verfügung. Sie können ihn mithilfe des [/experimental: präprocessor](../build/reference/experimental-preprocessor.md) -Compilerschalters aktivieren. Das standardmäßige präprozessorverhalten bleibt mit dem in früheren Versionen identisch.

## <a name="new-predefined-macro"></a>Neues vordefiniertes Makro

Sie können erkennen, welcher Präprozessor zum Zeitpunkt der Kompilierung verwendet wird. Überprüfen Sie den Wert des vordefinierten Makros [`_MSVC_TRADITIONAL`](predefined-macros.md) , um zu ermitteln, ob der herkömmliche Präprozessor bereits verwendet wird. Dieses Makro wird von Versionen des Compilers, die es unterstützen, bedingungslos festgelegt, unabhängig davon, welcher Präprozessor aufgerufen wird. Der Wert für den herkömmlichen Präprozessor ist 1. Der Wert ist 0 (null) für den konformen Präprozessor.

```cpp
#if defined(_MSVC_TRADITIONAL) && _MSVC_TRADITIONAL
// Logic using the traditional preprocessor
#else
// Logic using cross-platform compatible preprocessor
#endif
```

## <a name="behavior-changes-in-the-new-preprocessor"></a>Verhaltensänderungen im neuen Präprozessor

Der erste Aufwand für den neuen Präprozessor liegt darin, alle Makro Erweiterungen dem Standard zu entsprechen. Sie können den MSVC-Compiler mit Bibliotheken verwenden, die zurzeit durch das herkömmliche Verhalten blockiert werden. Wir haben den aktualisierten Präprozessor in realen Projekten getestet. Im folgenden finden Sie einige der gängigeren wichtigen Änderungen, die wir gefunden haben:

### <a name="macro-comments"></a>Makro Kommentare

Der herkömmliche Präprozessor basiert auf Zeichen Puffern anstelle von Präprozessortoken. Dies ermöglicht ungewöhnliche Verhaltensweisen, wie z. b. den folgenden präprozessorkommentartrick, der unter dem entsprechenden Präprozessor nicht funktioniert:

```cpp
#if DISAPPEAR
#define DISAPPEARING_TYPE /##/
#else
#define DISAPPEARING_TYPE int
#endif

// myVal disappears when DISAPPEARING_TYPE is turned into a comment
DISAPPEARING_TYPE myVal;
```

Die standardkonforme Lösung besteht darin, `int myVal` innerhalb der entsprechenden Direktiven zu deklarieren `#ifdef/#endif` :

```cpp
#define MYVAL 1

#ifdef MYVAL
int myVal;
#endif
```

### <a name="lval"></a>L # Val

Der herkömmliche Präprozessor kombiniert fälschlicherweise ein Zeichen folgen Präfix mit dem Ergebnis des Zeichen folgen Operator [(#)](stringizing-operator-hash.md) :

```cpp
 #define DEBUG_INFO(val) L"debug prefix:" L#val
//                                       ^
//                                       this prefix

const wchar_t *info = DEBUG_INFO(hello world);
```

In diesem Fall ist das `L` Präfix nicht erforderlich, da die angrenzenden Zeichenfolgenliterale nach der Makro Erweiterung immer kombiniert werden. Die abwärts kompatible Lösung besteht darin, die Definition zu ändern:

```cpp
#define DEBUG_INFO(val) L"debug prefix:" #val
//                                       ^
//                                       no prefix
```

Das gleiche Problem ist auch bei der Handhabung von Makros zu finden, die das Argument für ein breites Zeichenfolgenliteralzeichen "stringisieren":

```cpp
 // The traditional preprocessor creates a single wide string literal token
#define STRING(str) L#str
```

Sie können das Problem auf verschiedene Arten beheben:

- Verwenden Sie die Zeichen folgen Verkettung von `L""` und `#str` , um Präfix hinzuzufügen. Angrenzende Zeichen folgen Literale werden nach der Makro Erweiterung kombiniert:

   ```cpp
   #define STRING1(str) L""#str
   ```

- Präfix hinzufügen, nachdem der eine `#str` zusätzliche Makro Erweiterung zugeordnet wurde

   ```cpp
   #define WIDE(str) L##str
   #define STRING2(str) WIDE(#str)
   ```

- Verwenden Sie den Verkettungs Operator `##` , um die Token zu kombinieren. Die Reihenfolge der Vorgänge für `##` und `#` ist nicht angegeben, obwohl alle Compiler den `#` Operator vor `##` in diesem Fall auswerten.

   ```cpp
   #define STRING3(str) L## #str
   ```

### <a name="warning-on-invalid-"></a>Warnung bei ungültigem \#\#

Wenn der [tokeneinfügenden Operator (# #)](token-pasting-operator-hash-hash.md) nicht zu einem einzelnen gültigen Vorverarbeitungs Token führt, ist das Verhalten nicht definiert. Der herkömmliche präprozessorvorgang kann die Token nicht kombinieren. Der neue Präprozessor entspricht dem Verhalten der meisten anderen Compiler und gibt eine Diagnose aus.

```cpp
// The ## is unnecessary and does not result in a single preprocessing token.
#define ADD_STD(x) std::##x
// Declare a std::string
ADD_STD(string) s;
```

### <a name="comma-elision-in-variadic-macros"></a>Komma-elisions in Variadic-Makros

Der herkömmliche MSVC-Präprozessor entfernt vor leeren Ersetzungen immer Kommas `__VA_ARGS__` . Der neue Präprozessor folgt genauer an das Verhalten anderer beliebter plattformübergreifender Compiler. Damit das Komma entfernt wird, muss das Variadic-Argument fehlen (nicht nur leer), und es muss mit einem-Operator gekennzeichnet werden `##` . Betrachten Sie das folgende Beispiel:

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

Im folgenden Beispiel fehlt im Aufruf von `FUNC2(1)` das Variadic-Argument in dem aufgerufenen Makro. Im-Rückruf `FUNC2(1, )` ist das Variadic-Argument leer, aber nicht vorhanden (Beachten Sie das Komma in der Argumentliste).

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

Im bevorstehenden c++ 20-Standard wurde dieses Problem durch Hinzufügen von gelöst `__VA_OPT__` . Die neue präprozessorunterstützung für  `__VA_OPT__` ist ab Visual Studio 2019, Version 16,5, verfügbar.

### <a name="c20-variadic-macro-extension"></a>C++ 20 Variadic-Makro Erweiterung

Der neue Präprozessor unterstützt c++ 20 Variadic-Makro Argument Elision:

```cpp
#define FUNC(a, ...) __VA_ARGS__ + a
int main()
  {
  int ret = FUNC(0);
  return ret;
  }
```

Dieser Code entspricht nicht vor dem c++ 20-Standard. In MSVC erweitert der neue Präprozessor dieses c++ 20-Verhalten in niedrigere sprach Standardmodi ( **`/std:c++14`** , **`/std:c++17`** ). Diese Erweiterung entspricht dem Verhalten anderer wichtiger plattformübergreifender C++-Compiler.

### <a name="macro-arguments-are-unpacked"></a>Makro Argumente werden "entpackt"

Wenn ein Makro im herkömmlichen Präprozessor eines seiner Argumente an ein anderes abhängiges Makro weiterleitet, wird das Argument beim Einfügen nicht "entpackt". Diese Optimierung wird normalerweise nicht bemerkt, kann jedoch zu ungewöhnlichen Verhalten führen:

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

Beim Erweitern `A()` leitet der herkömmliche Präprozessor alle in paketierten Argumente `__VA_ARGS__` an das erste Argument von TWO_STRINGS weiter, wodurch das Variadic-Argument leer bleibt `TWO_STRINGS` . Dies bewirkt, dass das Ergebnis von `#first` "1, 2" und nicht nur "1" ist. Wenn Sie genau daran arbeiten, Fragen Sie sich vielleicht, was mit dem Ergebnis von `#__VA_ARGS__` in der herkömmlichen PräprozessorErweiterung passiert ist: Wenn der Variadic-Parameter leer ist, sollte er zu einem leeren Zeichenfolgenliterals führen `""` . Ein separates Problem hat das Generieren des leeren zeichenfolgenliteraltokens verhindert.

### <a name="rescanning-replacement-list-for-macros"></a>Die Ersetzungs Liste für Makros wird neu berechnet.

Nachdem ein Makro ersetzt wurde, werden die sich ergebenden Token neu berechnet, um weitere Makro Bezeichner zu ersetzen. Der Algorithmus, der vom herkömmlichen Präprozessor für die erneute Überprüfung verwendet wird, ist nicht konform, wie in diesem Beispiel basierend auf tatsächlichem Code gezeigt:

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

Obwohl dieses Beispiel vielleicht etwas erfunden ist, haben wir es in "Real-World Code" gesehen.

Um zu sehen, was passiert, können wir die Erweiterung starten mit `DO_THING` :

1. `DO_THING(1, "World")` erweitert zu `CAT(IMPL, 1) ECHO(("Hello", "World"))`
1. `CAT(IMPL, 1)` erweitert zu `IMPL ## 1` , was zu erweitert wird `IMPL1`
1. Die Token befinden sich nun in diesem Status: `IMPL1 ECHO(("Hello", "World"))`
1. Der Präprozessor findet den Funktions ähnlichen Makro Bezeichner `IMPL1` . Da nicht auf folgt `(` , wird es nicht als Funktions ähnlicher Makro Aufruf angesehen.
1. Der Präprozessor wechselt zu den folgenden Token. Er findet fest, dass das Funktions ähnliche Makro `ECHO` aufgerufen wird: `ECHO(("Hello", "World"))` , das zu erweitert wird. `("Hello", "World")`
1. `IMPL1` wird nie für die Erweiterung wieder in Erwägung gezogen, daher lautet das vollständige Ergebnis der Erweiterungen wie folgt: `IMPL1("Hello", "World");`

Fügen Sie eine andere Dereferenzierungsschicht hinzu, um das Makro so zu ändern, dass es unter dem neuen Präprozessor und dem herkömmlichen Präprozessor identisch ist:

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

## <a name="incomplete-features-before-165"></a>Unvollständige Features vor 16,5

Ab Visual Studio 2019 Version 16,5 ist die neue präprozessorfunktion "Feature-Complete" für c++ 20. In früheren Versionen von Visual Studio ist der neue Präprozessor größtenteils fertiggestellt, obwohl einige präprozessordirektivenlogik weiterhin auf das herkömmliche Verhalten zurückgreift. Im folgenden finden Sie eine partielle Liste unvollständiger Features in Visual Studio-Versionen vor 16,5:

- Unterstützung für `_Pragma`
- C++ 20 Features
- Blockierungs Fehler verstärken: logische Operatoren in präprozessorkonstantenausdrücken sind im neuen Präprozessor vor Version 16,5 nicht vollständig implementiert. Bei einigen `#if` Direktiven kann der neue Präprozessor auf den herkömmlichen Präprozessor zurückgreifen. Der Effekt ist nur sichtbar, wenn Makros, die mit dem herkömmlichen Präprozessor nicht kompatibel sind, erweitert werden. Dies kann beim Aufbau von Boost-präprozessorslots vorkommen.

::: moniker-end
