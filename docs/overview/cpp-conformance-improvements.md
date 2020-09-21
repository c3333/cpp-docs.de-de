---
title: Verbesserungen an C++ bei der Übereinstimmung mit Standards
ms.date: 08/04/2020
description: Microsoft C++ in Visual Studio  bewegt sich auf die vollständige Konformität mit dem Sprachstandard C++20 zu.
ms.technology: cpp-language
ms.openlocfilehash: 3a0e21bf08fcf7861feedd3fd43666bd3768deee
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/12/2020
ms.locfileid: "90042120"
---
# <a name="c-conformance-improvements-in-visual-studio"></a>Verbesserungen der C++-Konformität in Visual Studio

Microsoft C++ nimmt bei jedem Release Verbesserungen bei der Übereinstimmung mit Standards und Fehlerbehebungen vor. Dieser Artikel listet die Verbesserungen nach Hauptrelease und dann nach Versionen auf. Außerdem werden wichtige Fehlerbehebungen geordnet nach Version aufgeführt. Um direkt zu den Änderungen für eine bestimmte Version zu gelangen, verwenden Sie die Liste **In diesem Artikel**.

::: moniker range="vs-2019"

## <a name="conformance-improvements-in-visual-studio-2019-rtw-version-160"></a><a name="improvements_160"></a> Verbesserungen der Konformität in Visual Studio 2019 RTW (Version 16.0)

Visual Studio 2019 (RTW) enthält die folgenden Verbesserungen der Konformität, Fehlerbehebungen und Verhaltensänderungen des Microsoft C++-Compilers (MSVC).

**Hinweis**: C++20-Features werden im Modus **`/std:c++latest`** zur Verfügung gestellt, bis die C++20-Implementierung für den Compiler und IntelliSense abgeschlossen ist. Zu diesem Zeitpunkt wird der Compilermodus **`/std:c++20`** eingeführt.

### <a name="improved-modules-support-for-templates-and-error-detection"></a>Verbesserte Unterstützung von Modulen für Vorlagen und die Fehlererkennung

Module entsprechen nun offiziell dem C++20-Standard. Die verbesserte Unterstützung wurde in Visual Studio 2017 Version 15.9 hinzugefügt. Weitere Informationen finden Sie unter [Better template support and error detection in C++ Modules with MSVC 2017 version 15.9 (Verbesserte Unterstützung von Vorlagen und Fehlererkennung in C++-Modulen mit MSVC 2017 Version 15.9)](https://devblogs.microsoft.com/cppblog/better-template-support-and-error-detection-in-c-modules-with-msvc-2017-version-15-9/).

### <a name="modified-specification-of-aggregate-type"></a>Geänderte Spezifikation des Aggregattyps

Die Spezifikation von Aggregattypen wurde in C++20 geändert (siehe [Prohibit aggregates with user-declared constructors (Verbieten von Aggregaten mit benutzerdeklarierten Konstruktoren)](https://wg21.link/p1008r1)). In Visual Studio 2019 ist eine Klasse mit einem beliebigen benutzerdeklarierten Konstruktor (z. B. Einschließen von mit `= default` oder `= delete` deklarierten Konstruktoren) bei Verwendung von **`/std:c++latest`** kein Aggregat. Zuvor wurden Klassen nur durch von Benutzern bereitgestellte Konstruktoren als Aggregat disqualifiziert. Diese Änderung führt weitere Einschränkungen für die Initialisierung solcher Typen ein.

Der folgende Code wird in Visual Studio 2017 fehlerfrei kompiliert, löst jedoch bei Verwendung von **`/std:c++latest`** die Fehler C2280 und C2440 in Visual Studio 2019 aus:

```cpp
struct A
{
    A() = delete; // user-declared ctor
};

struct B
{
    B() = default; // user-declared ctor
    int i = 0;
};

A a{}; // ill-formed in C++20, previously well-formed
B b = { 1 }; // ill-formed in C++20, previously well-formed
```

### <a name="partial-support-for-operator-"></a>Teilweise Unterstützung für `operator <=>`

[P0515R3](https://wg21.link/p0515r3) C++20 führt den Operator für Dreiwegevergleiche `<=>` ein, der auch als „Raumschiffoperator“ bekannt ist. Visual Studio 2019 im **`/std:c++latest`** -Modus führt teilweise Unterstützung für den Operator ein, indem Fehler für die Syntax ausgelöst werden, die nun unzulässig ist. Der folgende Code wird beispielsweise in Visual Studio 2017 fehlerfrei kompiliert, löst bei Verwendung von **`/std:c++latest`** in Visual Studio 2019 jedoch mehrere Fehler aus:

```cpp
struct S
{
    bool operator<=(const S&) const { return true; }
};

template <bool (S::*)(const S&) const>
struct U { };

int main(int argc, char** argv)
{
    U<&S::operator<=> u; // In Visual Studio 2019 raises C2039, 2065, 2146.
}
```

Fügen Sie ein Leerzeichen in die betroffene Zeile vor der letzten spitzen Klammer ein, um die Fehler zu vermeiden: `U<&S::operator<= > u;`.

### <a name="references-to-types-with-mismatched-cv-qualifiers"></a>Verweise auf Typen mit nicht übereinstimmenden CV-Qualifizierern

MSVC hat zuvor die direkte Einbindung von Verweisen auf einen Typ mit nicht übereinstimmenden CV-Qualifizierern unter der obersten Ebene zugelassen. Diese Bindung kann die Änderung von vermeintlichen const-Daten ermöglichen, auf die sich der Verweis bezieht. Der Compiler erstellt jetzt gemäß den Anforderung des Standards einen temporären Wert. In Visual Studio 2017 wird der folgende Code ohne Warnungen kompiliert. In Visual Studio 2019 löst der Compiler die Warnung „C4172: `<func:#1 "?PData@X@@QBEABQBXXZ"> returning address of local variable or temporary.`“ aus:

```cpp
struct X
{
    const void* const& PData() const
    {
        return _pv;
    }

    void* _pv;
};

int main()
{
    X x;
    auto p = x.PData(); // C4172
}
```

### <a name="reinterpret_cast-from-an-overloaded-function"></a>Der Operator `reinterpret_cast` einer überladenen Funktion

Das Argument für **`reinterpret_cast`** ist keiner der Kontexte, in denen die Adresse einer überladenen Funktion zulässig ist. Der folgende Code wird in Visual Studio 2017 fehlerfrei kompiliert, in Visual Studio 2019 wird jedoch der Fehler „C2440: `cannot convert from 'overloaded-function' to 'fp'`“ ausgelöst:

```cpp
int f(int) { return 1; }
int f(float) { return .1f; }
using fp = int(*)(int);

int main()
{
    fp r = reinterpret_cast<fp>(&f);
}
```

Verwenden Sie für dieses Szenario eine zulässige Umwandlung, um den Fehler zu vermeiden:

```cpp
int f(int);
int f(float);
using fp = int(*)(int);

int main()
{
    fp r = static_cast<fp>(&f); // or just &f;
}
```

### <a name="lambda-closures"></a>Lambda-Closures

In C++14 sind Lambda-Closure-Typen nicht literal. Die primäre Folge dieser Regel ist, dass ein Lambda keinen **`constexpr`** -Variablen zugewiesen werden kann. Der folgende Code wird in Visual Studio 2017 fehlerfrei kompiliert, in Visual Studio 2019 wird jedoch der Fehler „C2127: `'l': illegal initialization of 'constexpr' entity with a non-constant expression`“ ausgelöst:

```cpp
int main()
{
    constexpr auto l = [] {}; // C2127 in VS2019
}
```

Entfernen Sie entweder den Qualifizierer **`constexpr`** , oder ändern Sie den Konformitätsmodus in **`/std:c++17`** , um diesen Fehler zu vermeiden.

### <a name="stdcreate_directory-failure-codes"></a>`std::create_directory`-Fehlercodes

[P1164](https://wg21.link/p1164r1) des C++20-Standards wurde bedingungslos implementiert. Dadurch wurde `std::create_directory` so geändert, dass überprüft wird, ob das Ziel beim Auftreten des Fehlers bereits ein Verzeichnis war. Zuvor wurden alle Fehler vom Typ ERROR_ALREADY_EXISTS in erfolgreiche Codes umgewandelt, die jedoch kein Verzeichnis erstellt haben.

### `operator<<(std::ostream, nullptr_t)`

Gemäß [LWG 2221](https://cplusplus.github.io/LWG/issue2221) wurde `operator<<(std::ostream, nullptr_t)` zum Schreiben von nullptrs in Streams hinzugefügt.

### <a name="additional-parallel-algorithms"></a>Zusätzliche parallele Algorithmen

Neue parallele Versionen von `is_sorted`, `is_sorted_until`, `is_partitioned`, `set_difference`, `set_intersection`, `is_heap` und `is_heap_until` wurden hinzugefügt.

### <a name="atomic-initialization"></a>Atomische Initialisierung

[P0883 "Fixing atomic initialization"](https://wg21.link/p0883r1) (Beheben der atomischen Initialisierung) ändert `std::atomic` in die Initialisierung des enthaltenen Werts von T, anstatt eine Standardinitialisierung durchzuführen. Die Behebung wird aktiviert, wenn Clang/LLVM mit der Microsoft-Standardbibliothek verwendet wird. Sie ist derzeit für den C++-Compiler von Microsoft als Workaround für einen Fehler in der Verarbeitung von **`constexpr`** deaktiviert.

### <a name="remove_cvref-and-remove_cvref_t"></a>`remove_cvref` und `remove_cvref_t`

Die Typmerkmale `remove_cvref` und `remove_cvref_t` aus [P0550](https://wg21.link/p0550r2) wurden implementiert. Diese entfernen die reference- und CV-Qualifizierer eines Typs ohne verfallende Funktionen und Arrays in Zeigern (im Gegensatz zu `std::decay` und `std::decay_t`).

### <a name="feature-test-macros"></a>Makros für Featuretests

Die Entwicklung der [Featuretestmakros (P0941R2)](https://wg21.link/p0941r2) ist nun abgeschlossen. Dadurch wird `__has_cpp_attribute` unterstützt. Featuretestmakros werden in allen Standardmodi unterstützt.

### <a name="prohibit-aggregates-with-user-declared-constructors"></a>Unterbinden von Aggregaten mit benutzerdeklarierten Konstruktoren

[C++20 P1008R1 - prohibiting aggregates with user-declared constructors (Unterbinden von Aggregaten mit benutzerdeklarierten Konstruktoren)](https://wg21.link/p1008r1) ist abgeschlossen.

## <a name="conformance-improvements-in-161"></a><a name="improvements_161"></a> Verbesserungen der Konformität in 16.1

### <a name="char8_t"></a>char8_t

[P0482r6](https://wg21.link/p0482r6). C++20 führt einen neuen Zeichentyp ein, der für die Darstellung von UTF-8-Codeeinheiten verwendet wird. `u8`-Zeichenfolgenliterale in C++20 verfügen über den Typ `const char8_t[N]` anstelle von `const char[N]` (der vorherige Typ). Ähnliche Änderungen wurden in [N2231](https://wg14.link/n2231) für den C-Standard vorgeschlagen. Vorschläge für die Wiederherstellung der Abwärtskompatibilität von **`char8_t`** finden Sie in [P1423r3](https://wg21.link/p1423r3). In Visual Studio 2019 Version 16.1 fügt der C++-Compiler von Microsoft Unterstützung für **`char8_t`** hinzu, wenn die Compileroption **`/Zc:char8_t`** angegeben wird. Zukünftig erfolgt die Unterstützung mit [`/std:c++latest`](../build/reference/std-specify-language-standard-version.md), was mithilfe von **`/Zc:char8_t-`** in das C++17-Verhalten zurückversetzt werden kann. Der EDG-Compiler, mit dem IntelliSense arbeitet, unterstützt dies noch nicht. Möglicherweise sehen Sie falsche nur auf IntelliSense bezogene Fehler, die keinen Einfluss auf die tatsächliche Kompilierung haben.

#### <a name="example"></a>Beispiel

```cpp
const char* s = u8"Hello"; // C++17
const char8_t* s = u8"Hello"; // C++20
```

### <a name="stdtype_identity-metafunction-and-stdidentity-function-object"></a>Die std::type_identity-Metafunktion und das std::identity-Funktionsobjekt

[P0887R1 type_identity](https://wg21.link/p0887r1). Die veraltete `std::identity`-Klassenvorlagenerweiterung wurde entfernt und durch die `std::type_identity`-Metafunktion und das `std::identity`-Funktionsobjekt von C++20 ersetzt. Beide sind nur in [`/std:c++latest`](../build/reference/std-specify-language-standard-version.md) verfügbar.

Im folgenden Beispiel wird die Veraltungswarnung C4996 für `std::identity` (in \<type_traits> definiert) in Visual Studio 2017 erzeugt:

```cpp
#include <type_traits>

using T = std::identity<int>::type;
T x, y = std::identity<T>{}(x);
int i = 42;
long j = std::identity<long>{}(i);
```

Im folgenden Beispiel wird die Verwendung des neuen `std::identity`-Funktionsobjekts (in \<functional> definiert) gemeinsam mit der neuen `std::type_identity`-Metafunktion veranschaulicht:

```cpp
#include <type_traits>
#include <functional>

using T = std::type_identity<int>::type;
T x, y = std::identity{}(x);
int i = 42;
long j = static_cast<long>(i);
```

### <a name="syntax-checks-for-generic-lambdas"></a>Syntaxprüfung für generische Lambdas

Der neue Lambdafunktionsprozessor ermöglicht im Konformitätsmodus einige syntaktische Überprüfungen in generischen Lambdafunktionen bei Verwendung von [`/std:c++latest`](../build/reference/std-specify-language-standard-version.md) oder anderen Sprachmodi mit **`/experimental:newLambdaProcessor`** .

Dieser Code wird in Visual Studio 2017 fehlerfrei kompiliert, erzeugt in Visual Studio 2019 jedoch den Fehler „C2760 `syntax error: unexpected token '\<id-expr>', expected 'id-expression'`“:

```cpp
void f() {
    auto a = [](auto arg) {
        decltype(arg)::Type t;
    };
}
```

Im folgenden Beispiel wird die richtige Syntax veranschaulicht, die nun vom Compiler erzwungen wird:

```cpp
void f() {
    auto a = [](auto arg) {
        typename decltype(arg)::Type t;
    };
}
```

### <a name="argument-dependent-lookup-for-function-calls"></a>Argumentbezogene Suchen nach Funktionsaufrufen

[P0846R0](https://wg21.link/p0846r0) (C++20) Die Möglichkeit, Funktionsvorlagen über argumentbezogene Suchen nach Funktionsaufrufausdrücken zu suchen, wurde mit expliziten Vorlagenargumenten erweitert. Erfordert **`/std:c++latest`** .

### <a name="designated-initialization"></a>Designierte Initialisierung

[P0329R4](https://wg21.link/p0329r4) (C++20) Die *designierte Initialisierung* ermöglicht, dass bestimmte Member in der Aggregatinitialisierung mithilfe der `Type t { .member = expr }`-Syntax ausgewählt werden können. Erfordert **`/std:c++latest`** .

### <a name="new-and-updated-standard-library-functions-c20"></a>Neue und aktualisierte Standardbibliotheksfunktionen (C++20)

- `starts_with()` und `ends_with()` für `basic_string` und `basic_string_view`.
- `contains()` für assoziative Container.
- `remove()`, `remove_if()` und `unique()` für `list` und `forward_list` geben nun `size_type` zurück.
- `shift_left()` und `shift_right()` wurden \<algorithm> hinzugefügt.

## <a name="conformance-improvements-in-162"></a><a name="improvements_162"></a> Verbesserungen der Konformität in 16.2

### <a name="noexcept-constexpr-functions"></a>`noexcept` `constexpr`-Funktionen

**`constexpr`** -Funktionen werden bei Verwendung in einem konstanten Ausdruck nicht mehr standardmäßig als **`noexcept`** angesehen. Dieser Behavior Change stammt aus der Auflösung von [CWG 1351](https://wg21.link/cwg1351) und ist in [`/permissive-`](../build/reference/permissive-standards-conformance.md) aktiviert. Das folgende Beispiel wird in Visual Studio 2019 Version 16.1 und früher kompiliert, erzeugt jedoch C2338 in Visual Studio 2019 Version 16.2:

```cpp
constexpr int f() { return 0; }

int main() {
    static_assert(noexcept(f()), "f should be noexcept"); // C2338 in 16.2
}
```

Fügen Sie den Ausdruck **`noexcept`** zur Funktionsdeklaration hinzu, um den Fehler zu beheben:

```cpp
constexpr int f() noexcept { return 0; }

int main() {
    static_assert(noexcept(f()), "f should be noexcept");
}
```

### <a name="binary-expressions-with-different-enum-types"></a>Binäre Ausdrücke mit unterschiedlichen Enumerationstypen

C++20 hat die üblichen arithmetischen Konvertierungen für Operanden als veraltet markiert, wobei:

- ein Operand ein Enumerationstyp und

- der andere ein anderer Enumerations- oder Gleitkommatyp ist.

Weitere Informationen finden Sie unter [P1120R0](https://wg21.link/p1120r0).

Ab Visual Studio 2019, Version 16.2 erzeugt der folgende Code eine Warnung der Stufe 4, wenn die Compileroption [`/std:c++latest`](../build/reference/std-specify-language-standard-version.md) aktiviert ist:

```cpp
enum E1 { a };
enum E2 { b };
int main() {
    int i = a | b; // warning C5054: operator '|': deprecated between enumerations of different types
}
```

Konvertieren Sie den zweiten Operanden mit [static_cast](../cpp/static-cast-operator.md), um zu vermeiden, dass eine Warnung ausgelöst wird:

```cpp
enum E1 { a };
enum E2 { b };
int main() {
  int i = a | static_cast<int>(b);
}
```

Das heißt, die Verwendung einer binären Operation zwischen einem Enumerations- und einem Gleitkommatyp löst jetzt eine Warnung aus, wenn die Compileroption [`/std:c++latest`](../build/reference/std-specify-language-standard-version.md) aktiviert ist:

```cpp
enum E1 { a };
int main() {
  double i = a * 1.1;
}
```

Konvertieren Sie den zweiten Operanden mit [static_cast](../cpp/static-cast-operator.md), um zu vermeiden, dass eine Warnung ausgelöst wird:

```cpp
enum E1 { a };
int main() {
   double i = static_cast<int>(a) * 1.1;
}
```

### <a name="equality-and-relational-comparisons-of-arrays"></a>Gleichheitsvergleiche und relationale Vergleiche von Arrays

Gleichheitsvergleiche und relationale Vergleiche zwischen zwei Operanden des Arraytyps werden in C++20 ([P1120R0](https://wg21.link/p1120r0)) als veraltet eingestuft. Das heißt, dass ein Vergleichsvorgang zwischen zwei Arrays (trotz des Rangs und der Ähnlichkeiten der Erweiterung) jetzt eine Warnung auslöst. Ab Visual Studio 2019, Version 16.2 erzeugt der folgende Code die Meldung „C5056: `operator '==': deprecated for array types`“, wenn die Compileroption [`/std:c++latest`](../build/reference/std-specify-language-standard-version.md) aktiviert ist:

```cpp
int main() {
    int a[] = { 1, 2, 3 };
    int b[] = { 1, 2, 3 };
    if (a == b) { return 1; }
}
```

Sie können die Adressen der ersten Elemente vergleichen, um zu vermeiden, dass eine Warnung ausgelöst wird:

```cpp
int main() {
    int a[] = { 1, 2, 3 };
    int b[] = { 1, 2, 3 };
    if (&a[0] == &b[0]) { return 1; }
}
```

Sie können ermitteln, ob der Inhalt von zwei Arrays gleich ist, indem Sie die [std::equal](../standard-library/algorithm-functions.md#equal)-Funktion verwenden:

```cpp
std::equal(std::begin(a), std::end(a), std::begin(b), std::end(b));
```

### <a name="effect-of-defining-spaceship-operator-on--and-"></a>Auswirkung der Definition des Spaceship-Operators auf `==` und `!=`

Eine Definition des Spaceship-Operators ( **`<=>`** ) allein schreibt keine Ausdrücke mit **`==`** oder **`!=`** mehr neu, es sei denn, der Spaceship-Operator ist als **`= default`** ([P1185R2](https://wg21.link/p1185r2)) markiert. Das folgende Beispiel wird in Visual Studio 2019 RTW und Version 16.1 kompiliert, erzeugt jedoch C2678 in Visual Studio 2019 Version 16.2:

```cpp
#include <compare>

struct S {
  int a;
  auto operator<=>(const S& rhs) const {
    return a <=> rhs.a;
  }
};
bool eq(const S& lhs, const S& rhs) {
  return lhs == rhs;
}
bool neq(const S& lhs, const S& rhs) {
    return lhs != rhs;
}
```

Sie können diesen Fehler vermeiden, indem Sie den Operator == definieren oder als Standard deklarieren:

```cpp
#include <compare>

struct S {
  int a;
  auto operator<=>(const S& rhs) const {
    return a <=> rhs.a;
  }
  bool operator==(const S&) const = default;
};
bool eq(const S& lhs, const S& rhs) {
  return lhs == rhs;
}
bool neq(const S& lhs, const S& rhs) {
    return lhs != rhs;
}
```

### <a name="standard-library-improvements"></a>Verbesserungen der Standardbibliothek

- \<charconv> `to_chars()` mit fester/wissenschaftlicher Genauigkeit (Die allgemeine Genauigkeit ist derzeit für Version 16.4 geplant.)
- [P0020R6](https://wg21.link/p0020r6): atomic\<float>, atomic\<double>, atomic\<long double>
- [P0463R1](https://wg21.link/p0463r1): endian
- [P0482R6](https://wg21.link/p0482r6): Bibliotheksunterstützung für char8_t
- [P0600R1](https://wg21.link/p0600r1): [\[nodiscard]]Für STL, Teil 1
- [P0653R2](https://wg21.link/p0653r2): to_address()
- [P0754R2](https://wg21.link/p0754r2): \<version>
- [P0771R1](https://wg21.link/p0771r1): noexcept für Bewegungskonstruktor von std::function

## <a name="conformance-improvements-in-visual-studio-2019-version-163"></a><a name="improvements_163"></a> Verbesserungen der Konformität in Visual Studio 2019, Version 16.3

### <a name="stream-extraction-operators-for-char-removed"></a>Streamextraktionsoperatoren für char* entfernt

Die Streamextraktionsoperatoren für Zeiger auf Zeichen wurden entfernt und durch Extraktionsoperatoren für Arrayzeichen ersetzt (vgl. [P0487R1](https://wg21.link/p0487r1)). WG21 betrachtet die entfernten Überladungen als unsicher. Im Modus [`/std:c++latest`](../build/reference/std-specify-language-standard-version.md) löst das folgende Beispiel jetzt „C2679: `binary '>>': no operator found which takes a right-hand operand of type 'char*' (or there is no acceptable conversion)`“ aus:

```cpp
   char x[42];
   char* p = x;
   std::cin >> std::setw(42);
   std::cin >> p;
```

Sie können den Fehler vermeiden, indem Sie den Extraktionsoperator mit einer char[]-Variablen verwenden:

```cpp
char x[42];
std::cin >> x;
```

### <a name="new-keywords-requires-and-concept"></a>Neue Schlüsselwörter `requires` und `concept`

Die neuen Schlüsselwörter **`requires`** und **`concept`** wurden zum Microsoft C++-Compiler hinzugefügt. Wenn Sie versuchen, eines dieser Schlüsselwörter als Bezeichner im Modus [`/std:c++latest`](../build/reference/std-specify-language-standard-version.md) zu verwenden, löst der Compiler den Fehler „C2059: `syntax error`“ aus.

### <a name="constructors-as-type-names-disallowed"></a>Konstruktoren als Typnamen nicht zulässig

Konstruktornamen werden vom Compiler in diesem Fall nicht mehr als injizierte Klassennamen betrachtet, wenn sie in einem qualifizierten Namen nach einem Alias für eine Spezialisierung einer Klassenvorlage enthalten sind. Zuvor waren Konstruktoren als Typname zur Deklaration anderer Entitäten einsetzbar. Mit dem folgenden Beispiel wird nun der Fehler „C3646: `'TotalDuration': unknown override specifier`“ ausgelöst:

```cpp
#include <chrono>

class Foo {
   std::chrono::milliseconds::duration TotalDuration{};
};

```

Sie können den Fehler vermeiden, indem wie im Folgenden gezeigt `TotalDuration` deklarieren:

```cpp
#include <chrono>

class Foo {
  std::chrono::milliseconds TotalDuration {};
};
```

### <a name="stricter-checking-of-extern-c-functions"></a>Strengere Überprüfung von `extern "C"`-Funktionen

Wenn eine **`extern "C"`** -Funktion in verschiedenen Namespaces deklariert wurde, haben frühere Versionen des Microsoft C++-Compilers nicht überprüft, ob die Deklarationen kompatibel waren. Ab Visual Studio 2019, Version 16.3 führt der Compiler Prüfungen auf Kompatibilität durch. Im Modus [`/permissive-`](../build/reference/permissive-standards-conformance.md) löst der folgende Code die Fehler „C2371 `redefinition; different basic types`“ und „C2733 `you cannot overload a function with C linkage`“ aus:

```cpp
using BOOL = int;

namespace N
{
   extern "C" void f(int, int, int, bool);
}

void g()
{
   N::f(0, 1, 2, false);
}

extern "C" void f(int, int, int, BOOL){}
```

Sie können die Fehler im vorherigen Beispiel vermeiden, indem Sie konsistent **`bool`** anstelle von `BOOL` in beiden Deklarationen von `f` verwenden.

### <a name="standard-library-improvements"></a>Verbesserungen der Standardbibliothek

Die nicht standardmäßigen Header \<stdexcpt.h> und \<typeinfo.h> wurden entfernt. Code, der diese enthält, sollte stattdessen jeweils die standardmäßigen Header \<exception> und \<typeinfo> enthalten.

## <a name="conformance-improvements-in-visual-studio-2019-version-164"></a><a name="improvements_164"></a> Verbesserungen der Konformität in Visual Studio 2019, Version 16.4

### <a name="better-enforcement-of-two-phase-name-lookup-for-qualified-ids-in-permissive-"></a>Bessere Durchsetzung der zweiphasigen Namenssuche für qualified-ids in `/permissive-`

Die Zweiphasennamenssuche erfordert, dass nicht abhängige Namen in Vorlagentexten zum Zeitpunkt der Definition für die Vorlage sichtbar sind. Zuvor wurden solche Namen gefunden, wenn die Vorlage instanziiert wurde. Diese Änderung vereinfacht das Schreiben von portierbarem, konformem Code in MSVC bei Verwendung des Flags [`/permissive-`](../build/reference/permissive-standards-conformance.md).

Wenn in Visual Studio 2019, Version 16.4, das Flag **`/permissive-`** festgelegt ist, erzeugt das folgende Beispiel einen Fehler, weil `N::f` beim Definieren der Vorlage `f<T>` nicht sichtbar ist:

```cpp
template <class T>
int f() {
    return N::f() + T{}; // error C2039: 'f': is not a member of 'N'
}

namespace N {
    int f() { return 42; }
}
```

In der Regel lässt sich dieser Fehler durch Einschließen fehlender Header oder Vorausdeklarieren von Funktionen oder Variablen beheben, wie im folgenden Beispiel gezeigt:

```cpp
namespace N {
    int f();
}

template <class T>
int f() {
    return N::f() + T{};
}

namespace N {
    int f() { return 42; }
}
```

### <a name="implicit-conversion-of-integral-constant-expressions-to-null-pointer"></a>Implizite Konvertierung integraler konstanter Ausdrücke in NULL-Zeiger

Der MSVC-Compiler implementiert jetzt [CWG Issue 903](https://wg21.link/cwg903) im Konformitätsmodus ( **`/permissive-`** ). Diese Regel lässt keine implizite Konvertierung von integralen konstanten Ausdrücken (mit Ausnahme des Integerliterals „0“) in NULL-Zeiger-Konstanten zu. Das folgende Beispiel erzeugt C2440 im Konformitätsmodus:

```cpp
int* f(bool* p) {
    p = false; // error C2440: '=': cannot convert from 'bool' to 'bool *'
    p = 0; // OK
    return false; // error C2440: 'return': cannot convert from 'bool' to 'int *'
}
```

Verwenden Sie zur Behebung des Fehlers **`nullptr`** anstelle von **`false`** . Das Literal „0“ ist weiterhin erlaubt:

```cpp
int* f(bool* p) {
    p = nullptr; // OK
    p = 0; // OK
    return nullptr; // OK
}
```

### <a name="standard-rules-for-types-of-integer-literals"></a>Standardregeln für Typen von Integerliteralen

Im Konformitätsmodus (aktiviert durch [`/permissive-`](../build/reference/permissive-standards-conformance.md)) verwendet MSVC die Standardregeln für Typen von Integerliteralen. Dezimalliteralen, die zu groß für einen **`signed int`** -Typ sind, wurde früher der Typ **`unsigned int`** zugewiesen. Jetzt erhalten solche Literale den nächstgrößeren **`signed`** -Integertyp: **`long long`** . Darüber hinaus wird Literalen mit dem Suffix „ll“, die zu groß für einen **`signed`** -Typ sind, der Typ **`unsigned long long`** zugewiesen.

Dies kann dazu führen, dass verschiedene Warnungsdiagnosen generiert werden und Unterschiede im Verhalten bei arithmetischen Operationen in Literalen auftreten.

Das folgende Beispiel zeigt das neue Verhalten in Visual Studio 2019, Version 16.4. Die Variable `i` weist jetzt den Typ **`unsigned int`** auf. Aus diesem Grund wird die Warnung ausgelöst. Die höchstwertigen Bits der Variable `j` werden auf 0 festgelegt.

```cpp
void f(int r) {
    int i = 2964557531; // warning C4309: truncation of constant value
    long long j = 0x8000000000000000ll >> r; // literal is now unsigned, shift will fill high-order bits with 0
}
```

Das folgende Beispiel zeigt, wie Sie das alte Verhalten beibehalten und Warnungen und die Verhaltensänderung zur Laufzeit vermeiden:

```cpp
void f(int r) {
int i = 2964557531u; // OK
long long j = (long long)0x8000000000000000ll >> r; // shift will keep high-order bits
}
```

### <a name="function-parameters-that-shadow-template-parameters"></a>Funktionsparameter, die ein Shadowing für Vorlagenparameter durchführen

Der MSVC-Compiler löst jetzt einen Fehler aus, wenn ein Funktionsparameter ein Shadowing für einen Vorlagenparameter durchführt:

```cpp
template<typename T>
void f(T* buffer, int size, int& size_read);

template<typename T, int Size>
void f(T(&buffer)[Size], int& Size) // error C7576: declaration of 'Size' shadows a template parameter
{
    return f(buffer, Size, Size);
}
```

Um den Fehler zu beheben, ändern Sie Namen eines der Parameter:

```cpp
template<typename T>
void f(T* buffer, int size, int& size_read);

template<typename T, int Size>
void f(T (&buffer)[Size], int& size_read)
{
    return f(buffer, Size, size_read);
}
```

### <a name="user-provided-specializations-of-type-traits"></a>Vom Benutzer bereitgestellte Spezialisierungen von Typmerkmalen

In Übereinstimmung mit der Unterklausel *meta.rqmts* der Standardversion löst der MSVC-Compiler jetzt einen Fehler aus, wenn eine benutzerdefinierte Spezialisierung einer der angegebenen `type_traits`-Vorlagen im Namespace `std` gefunden wird. Sofern nicht anders angegeben, führen solche Spezialisierungen zu nicht definiertem Verhalten. Das folgende Beispiel zeigt ein nicht definiertes Verhalten, weil es die Regel verletzt, und bei **`static_assert`** tritt der Fehler C2338 auf.

```cpp
#include <type_traits>
struct S;

template<>
struct std::is_fundamental<S> : std::true_type {};

static_assert(std::is_fundamental<S>::value, "fail");
```

Definieren Sie eine Struktur, die vom bevorzugten `type_trait`-Element erbt, und legen Sie Folgendes fest, um den Fehler zu vermeiden:

```cpp
#include <type_traits>

struct S;

template<typename T>
struct my_is_fundamental : std::is_fundamental<T> {};

template<>
struct my_is_fundamental<S> : std::true_type { };

static_assert(my_is_fundamental<S>::value, "fail");
```

### <a name="changes-to-compiler-provided-comparison-operators"></a>Änderungen an vom Compiler bereitgestellten Vergleichsoperatoren

Der MSVC-Compiler implementiert jetzt die folgenden Änderungen an Vergleichsoperatoren gemäß [P1630R1](https://wg21.link/p1630r1), wenn die Option [`/std:c++latest`](../build/reference/std-specify-language-standard-version.md) aktiviert ist:

Der Compiler schreibt Ausdrücke nicht mehr mithilfe von `operator==` neu, wenn diese einen Rückgabetyp beinhalten, der kein **`bool`** -Wert ist. Mit dem folgenden Code wird nun der Fehler „C2088: `'!=': illegal for struct`“ generiert:

```cpp
struct U {
    operator bool() const;
};

struct S {
    U operator==(const S&) const;
};

bool neq(const S& lhs, const S& rhs) {
    return lhs != rhs;
}
```

Um diesen Fehler zu vermeiden, müssen Sie den erforderlichen Operator explizit definieren:

```cpp
struct U {
    operator bool() const;
};

struct S {
    U operator==(const S&) const;
    U operator!=(const S&) const;
};

bool neq(const S& lhs, const S& rhs) {
    return lhs != rhs;
}
```

Der Compiler definiert keinen Standardvergleichsoperator mehr, wenn es sich um einen Member einer union-ähnlichen Klasse handelt. Mit dem folgenden Beispiel wird nun der Fehler „C2120: `'void' illegal with all types`“ generiert:

```cpp
#include <compare>

union S {
    int a;
    char b;
    auto operator<=>(const S&) const = default;
};

bool lt(const S& lhs, const S& rhs) {
    return lhs < rhs;
}
```

Um diesen Fehler zu vermeiden, definieren Sie einen Text für den Operator:

```cpp
#include <compare>

union S {
    int a;
    char b;
    auto operator<=>(const S&) const { ... }
};

bool lt(const S& lhs, const S& rhs) {
    return lhs < rhs;
}
```

Der Compiler definiert keinen standardmäßigen Vergleichsoperator mehr, wenn die Klasse einen Verweismember enthält. Mit dem folgenden Code wird nun der Fehler „C2120: `'void' illegal with all types`“ generiert:

```cpp
#include <compare>

struct U {
    int& a;
    auto operator<=>(const U&) const = default;
};

bool lt(const U& lhs, const U& rhs) {
    return lhs < rhs;
}
```

Um diesen Fehler zu vermeiden, definieren Sie einen Text für den Operator:

```cpp
#include <compare>

struct U {
    int& a;
    auto operator<=>(const U&) const { ... };
};

bool lt(const U& lhs, const U& rhs) {
    return lhs < rhs;
}
```

## <a name="conformance-improvements-in-visual-studio-2019-version-165"></a><a name="improvements_165"></a> Verbesserungen der Konformität in Visual Studio 2019, Version 16.5

### <a name="explicit-specialization-declaration-without-an-initializer-isnt-a-definition"></a>Eine explizite Spezialisierungsdeklaration ohne Initialisierer ist keine Definition

Unter `/permissive-` erzwingt MSVC jetzt eine Standardregel, die besagt, dass explizite Spezialisierungsdeklarationen ohne Initialisierer keine Definitionen sind. Zuvor galt die Deklaration als Definition mit einem Standardinitialisierer. Der Effekt kann zum Zeitpunkt der Verknüpfung beobachtet werden, da ein Programm, das von diesem Verhalten abhängig ist, nun nicht aufgelöste Symbole aufweisen kann. Dieses Beispiel führt jetzt zu einem Fehler:

```cpp
template <typename> struct S {
    static int a;
};

// In permissive-, this declaration isn't a definition, and the program won't link.
template <> int S<char>::a;

int main() {
    return S<char>::a;
}
```

```Output
error LNK2019: unresolved external symbol "public: static int S<char>::a" (?a@?$S@D@@2HA) referenced in function _main
at link time.
```

Fügen Sie einen Initialisierer hinzu, um das Problem zu beheben:

```cpp
template <typename> struct S {
    static int a;
};

// Add an initializer for the declaration to be a definition.
template <> int S<char>::a{};

int main() {
    return S<char>::a;
}
```

### <a name="preprocessor-output-preserves-newlines"></a>Präprozessorausgabe behält Zeilenumbrüche bei

Der experimentelle Präprozessor behält bei der Verwendung von **`/P`** oder **`/E`** mit **`/experimental:preprocessor`** nun Zeilenumbrüche und Leerzeichen bei.

Gehen wir von folgender Beispielquelle aus:

```cpp
#define m()
line m(
) line
```

Die vorherige Ausgabe von **`/E`** war:

```Output
line line
#line 2
```

Die neue Ausgabe von **`/E`** ist nun:

```Output
line
 line
```

### <a name="import-and-module-keywords-are-context-dependent"></a>Die Schlüsselwörter „import“ und „module“ sind kontextabhängig

Pro P1857R1 gelten für die Präprozessoranweisungen „import“ und „module“ zusätzliche Syntaxeinschränkungen. Das folgende Beispiel wird nicht mehr kompiliert:

```cpp
import // Invalid
m;
```

Es gibt die folgende Fehlermeldung zurück:

```Output
error C2146: syntax error: missing ';' before identifier 'm'
```

Behalten Sie den Import auf derselben Zeile:

```cpp
import m; // OK
```

### <a name="removal-of-stdweak_equality-and-stdstrong_equality"></a>Entfernen von „std::weak_equality“ und „std::strong_equality“

Für das Zusammenführen von P1959R0 muss der Compiler Verhalten sowie Verweise auf die Typen `std::weak_equality` und `std::strong_equality` entfernen.

Das folgende Beispiel wird nicht mehr kompiliert:

```cpp
#include <compare>

struct S {
    std::strong_equality operator<=>(const S&) const = default;
};

void f() {
    nullptr<=>nullptr;
    &f <=> &f;
    &S::operator<=> <=> &S::operator<=>;
}
```

Das Beispiel führt nun zu folgenden Fehlern:

```Output
error C2039: 'strong_equality': is not a member of 'std'
error C2143: syntax error: missing ';' before '<=>'
error C4430: missing type specifier - int assumed. Note: C++ does not support default-int
error C4430: missing type specifier - int assumed. Note: C++ does not support default-int
error C7546: binary operator '<=>': unsupported operand types 'nullptr' and 'nullptr'
error C7546: binary operator '<=>': unsupported operand types 'void (__cdecl *)(void)' and 'void (__cdecl *)(void)'
error C7546: binary operator '<=>': unsupported operand types 'int (__thiscall S::* )(const S &) const' and 'int (__thiscall S::* )(const S &) const'
```

Aktualisieren Sie den Code, sodass die integrierten relationalen Operatoren bevorzugt und die entfernten Typen ersetzt werden, um das Problem zu beheben:

```cpp
#include <compare>

struct S {
    std::strong_ordering operator<=>(const S&) const = default; // prefer 'std::strong_ordering'
};

void f() {
    nullptr != nullptr; // use pre-existing builtin operator != or ==.
    &f != &f;
    &S::operator<=> != &S::operator<=>;
}
```

### <a name="tls-guard-changes"></a>Änderung des TLS-Wächters

Zuvor wurden lokale Threadvariablen in DLLs nicht ordnungsgemäß initialisiert. Anders als beim Thread, der die DLL geladen hat, wurden sie bei Threads, die bereits vor dem Laden der DLL vorhanden waren, vor der ersten Verwendung nicht initialisiert. Dieser Fehler wurde nun behoben. Threadlokale Variablen in einer solchen DLL werden sofort initialisiert, bevor sie zum ersten Mal in solchen Threads verwendet werden.

Dieses neue Verhalten des Tests auf Initialisierung bei Verwendung von threadlokalen Variablen kann mithilfe des Compilerschalters **`/Zc:tlsGuards-`** deaktiviert werden. Eine weitere Möglichkeit ist das Hinzufügen des `[[msvc:no_tls_guard]]`-Attributs zu bestimmten threadlokalen Variablen.

### <a name="better-diagnosis-of-call-to-deleted-functions"></a>Bessere Diagnose des Aufrufs gelöschter Funktionen

Unser Compiler war bisher weniger einschränkend in Bezug auf Aufrufe gelöschter Funktionen. Wenn die Aufrufe beispielsweise im Kontext eines Vorlagentexts stattfanden, wurden sie nicht diagnostiziert. Zudem wurde bei mehreren Instanzen von Aufrufen gelöschter Funktionen nur eine Diagnose ausgegeben. Nun geben wir für jede dieser Instanzen eine Diagnose aus.

Eine Konsequenz des neuen Verhaltens kann zu einem kleinen Breaking Change führen: Code, der eine gelöschte Funktion aufgerufen hat, wurde nicht diagnostiziert, wenn er nie für die Codegenerierung benötigt wurde. Nun wird er vorab diagnostiziert.

In diesem Beispiel wird Code angezeigt, der nun zu einem Fehler führt:

```cpp
struct S {
  S() = delete;
  S(int) { }
};

struct U {
  U() = delete;
  U(int i): s{ i } { }

  S s{};
};

U u{ 0 };
```

```Output
error C2280: 'S::S(void)': attempting to reference a deleted function
note: see declaration of 'S::S'
note: 'S::S(void)': function was explicitly deleted
```

Entfernen Sie Aufrufe gelöschter Funktionen, um das Problem zu beheben:

```cpp
struct S {
  S() = delete;
  S(int) { }
};

struct U {
  U() = delete;
  U(int i): s{ i } { }

  S s;  // Do not call the deleted ctor of 'S'.
};

U u{ 0 };
```

## <a name="conformance-improvements-in-visual-studio-2019-version-166"></a><a name="improvements_166"></a> Verbesserungen der Konformität in Visual Studio 2019, Version 16.6

### <a name="standard-library-streams-reject-insertions-of-mis-encoded-character-types"></a>Bei Datenströmen der Standardbibliothek werden Einfügungen von nicht korrekt codierten Zeichentypen abgelehnt

Beim Einfügen von **`wchar_t`** in `std::ostream` sowie von **`char16_t`** oder **`char32_t`** in `std::ostream` oder `std::wostream` wird üblicherweise ein ganzzahliger Wert ausgegeben. Beim Einfügen von Zeigern in diese Zeichentypen wird der Zeigerwert ausgegeben. Für Programmierer sind beide Verhalten nicht intuitiv. Vielmehr erwarten sie, dass die Standardbibliothek die auf Zeichen oder NULL endende Zeichenfolge transcodiert und das Ergebnis ausgibt.

Mit dem C++20-Vorschlag [P1423R3](https://wg21.link/p1423r3) werden gelöschte insertion-Operatorüberladungen im Datenstrom für diese Kombinationen aus Datenstrom und Zeichen- oder Zeichenzeigertypen hinzugefügt. Bei Verwendung von **`/std:c++latest`** haben die Überladungen zur Folge, dass diese Einfügungen nicht korrekt angegeben werden. Das Verhalten entspricht dadurch nicht einem vermutlich unbeabsichtigten Verhalten. Wird ein solches Element ermittelt, löst der Compiler den Fehler C2280 aus. Um das alte Verhalten wiederherzustellen, können Sie das escape hatch-Makro `_HAS_STREAM_INSERTION_OPERATORS_DELETED_IN_CXX20` als `1` definieren. (Der Vorschlag löscht auch insertion-Operatoren in Datenströmen für **`char8_t`** . Unsere Standardbibliothek hat ähnliche Überladungen implementiert, als Unterstützung für **`char8_t`** hinzugefügt wurde. Das „falsche“ Verhalten war für **`char8_t`** also nie verfügbar.)

Dieses Beispiel zeigt das Verhalten bei dieser Änderung:

```cpp
#include <iostream>
int main() {
    const wchar_t cw = L'x', *pw = L"meow";
    const char16_t c16 = u'x', *p16 = u"meow";
    const char32_t c32 = U'x', *p32 = U"meow";
    std::cout << cw << ' ' << pw << '\n';
    std::cout << c16 << ' ' << p16 << '\n';
    std::cout << c32 << ' ' << p32 << '\n';
    std::wcout << c16 << ' ' << p16 << '\n';
    std::wcout << c32 << ' ' << p32 << '\n';
}
```

Der Code erzeugt nun folgende Diagnosemeldungen:

```Output
error C2280: 'std::basic_ostream<char,std::char_traits<char>> &std::<<<std::char_traits<char>>(std::basic_ostream<char,std::char_traits<char>> &,wchar_t)': attempting to reference a deleted function
error C2280: 'std::basic_ostream<char,std::char_traits<char>> &std::<<<std::char_traits<char>>(std::basic_ostream<char,std::char_traits<char>> &,char16_t)': attempting to reference a deleted function
error C2280: 'std::basic_ostream<char,std::char_traits<char>> &std::<<<std::char_traits<char>>(std::basic_ostream<char,std::char_traits<char>> &,char32_t)': attempting to reference a deleted function
error C2280: 'std::basic_ostream<wchar_t,std::char_traits<wchar_t>> &std::<<<std::char_traits<wchar_t>>(std::basic_ostream<wchar_t,std::char_traits<wchar_t>> &,char16_t)': attempting to reference a deleted function
error C2280: 'std::basic_ostream<wchar_t,std::char_traits<wchar_t>> &std::<<<std::char_traits<wchar_t>>(std::basic_ostream<wchar_t,std::char_traits<wchar_t>> &,char32_t)': attempting to reference a deleted function
```

Sie können den Effekt des alten Verhaltens in allen Sprachmodi erzielen, indem Sie Zeichentypen in **`unsigned int`** bzw. Zeiger-zu-Zeichen-Typen in `const void*` konvertieren:

```c++
#include <iostream>
int main() {
    const wchar_t cw = L'x', *pw = L"meow";
    const char16_t c16 = u'x', *p16 = u"meow";
    const char32_t c32 = U'x', *p32 = U"meow";
    std::cout << (unsigned)cw << ' ' << (const void*)pw << '\n'; // Outputs "120 0052B1C0"
    std::cout << (unsigned)c16 << ' ' << (const void*)p16 << '\n'; // Outputs "120 0052B1CC"
    std::cout << (unsigned)c32 << ' ' << (const void*)p32 << '\n'; // Outputs "120 0052B1D8"
    std::wcout << (unsigned)c16 << ' ' << (const void*)p16 << '\n'; // Outputs "120 0052B1CC"
    std::wcout << (unsigned)c32 << ' ' << (const void*)p32 << '\n'; // Outputs "120 0052B1D8"
}
```

### <a name="changed-return-type-of-stdpow-for-stdcomplex"></a>Änderung des Rückgabetyps von `std::pow()` für `std::complex`

In der Vergangenheit war die MSVC-Implementierung der Aktionsregeln für den Rückgabetyp der Funktionsvorlage `std::pow()` nicht korrekt. Beispielsweise wurde von `pow(complex<float>, int)` früher `complex<float>` zurückgegeben. Nun wird der richtige Typ `complex<double>` zurückgegeben. Die Korrektur wurde ohne Bedingungen für alle Standardmodi in Visual Studio 2019 Version 16.6 implementiert.

Diese Änderung kann zu Compilerfehlern führen. So konnte `pow(complex<float>, int)` beispielsweise früher mit **`float`** multipliziert werden. Da `complex<T> operator*` Argumente desselben Typs erwartet, wird mit dem folgenden Beispiel nun der Compilerfehler „C2676: `binary '*': 'std::complex<double>' does not define this operator or a conversion to a type acceptable to the predefined operator`“ verursacht:

```cpp
// pow_error.cpp
// compile by using: cl /EHsc /nologo /W4 pow_error.cpp
#include <complex>

int main() {
    std::complex<float> cf(2.0f, 0.0f);
    (void) (std::pow(cf, -1) * 3.0f);
}
```

Für dieses Problem sind eine Vielzahl von Korrekturen möglich:

- Ändern Sie den Typ des Multiplikands **`float`** in **`double`** . Dieses Argument kann direkt in ein `complex<double>`-Element konvertiert werden, um dem von `pow` zurückgegebenen Typ zu entsprechen.

- Schränken Sie das Ergebnis von `pow` auf `complex<float>` ein, indem Sie `complex<float>{pow(ARG, ARG)}` angeben. Anschließend ist eine Multiplikation mit einem **`float`** -Wert möglich.

- Übergeben Sie **`float`** anstelle von **`int`** an `pow`. Dieser Vorgang ist möglicherweise langsamer.

- In einigen Fällen können Sie `pow` vollständig vermeiden. Beispielsweise kann `pow(cf, -1)` durch eine Division ersetzt werden.

### <a name="switch-related-warnings-for-c"></a>Schalterbezogene Warnungen für C

Ab Visual Studio 2019 Version 16.6 implementiert der Compiler einige bereits vorhandene C++-Warnungen für Code, der als C kompiliert wird. Die folgenden Warnungen sind nun auf unterschiedlichen Ebenen aktiviert: C4060, C4061, C4062, C4063, C4064, C4065, C4808 und C4809. Die Warnungen C4065 und C4060 sind in C standardmäßig deaktiviert.

Sie werden bei fehlenden **`case`** -Anweisungen, nicht definierten **`enum`** -Elementen und nicht korrekten **`bool`** -Schaltern (Schalter mit zu vielen case-Angaben) ausgelöst. Zum Beispiel:

```c
#include <stdbool.h>

int main() {
    bool b = true;
    switch (b) {
        case true: break;
        case false: break;
        default: break; // C4809: switch statement has redundant 'default' label;
                        // all possible 'case' labels are given
    }
}
```

Entfernen Sie den redundanten **`default`** -Fall, um dieses Problem zu beheben:

```c
#include <stdbool.h>

int main() {
    bool b = true;
    switch (b) {
        case true: break;
        case false: break;
    }
}
```

### <a name="unnamed-classes-in-typedef-declarations"></a>Unbenannte Klassen in `typedef`-Deklarationen

Ab Visual Studio 2019, Version 16.6, wurde das Verhalten von **`typedef`** -Deklarationen so beschränkt, dass es [P1766R1](https://wg21.link/P1766R1) entspricht. Durch dieses Update können unbenannte Klassen innerhalb einer **`typedef`** -Deklaration keine anderen Member enthalten als die folgenden:

- nicht statische Datenmember
- Memberklassen
- Memberenumerationen
- Standardmemberinitialisierer

Dieselben Einschränkungen gelten rekursiv für alle geschachtelten Klassen. Durch diese Einschränkung soll die Einfachheit von Strukturen mit **`typedef`** -Namen zu Bindungszwecken sichergestellt werden. Diese müssen so einfach sein, dass keine Bindungsberechnungen erforderlich sind, bevor der Compiler den **`typedef`** -Namen für die Bindung erreicht.

Diese Änderung wirkt sich auf alle Standardmodi des Compilers aus. Bei der Standardeinstellung ( **`/std:c++14`** ) und den **`/std:c++17`** -Modi gibt der Compiler bei nicht konformem Code die Warnung C5208 aus. Wenn **`/permissive-`** angegeben wird, gibt der Compiler die Warnung C5208 als Fehler bei Verwendung von **`/std:c++14`** und Fehler C7626 bei Verwendung von **`/std:c++17`** aus. Der Compiler gibt den Fehler C7626 für nicht konformen Code aus, wenn **`/std:c++latest`** angegeben wird.

Das folgende Beispiel zeigt die Konstrukte, die in unbenannten Strukturen nicht länger zulässig sind. Abhängig vom angegebenen Standardmodus werden die Fehler oder Warnungen C5208 bzw. C7626 ausgegeben:

```cpp
struct B { };
typedef struct : B { // inheriting from 'B'; ill-formed
    void f(); // ill-formed
    static int i; // ill-formed
    struct U {
        void f(); // nested class has non-data member; ill-formed
    };
    int j = 10; // default member initializer; ill-formed
} S;
```

Der obige Code kann korrigiert werden, indem Sie der unbenannten Klasse einen Namen zuweisen:

```cpp
struct B { };
typedef struct S_ : B {
    void f();
    static int i;
    struct U {
        void f();
    };
    int j = 10;
} S;
```

### <a name="default-argument-import-in-ccli"></a>Importieren von Standardargumenten in C++/CLI

Eine zunehmende Anzahl von APIs hat in .NET Core Standardargumente. Aus diesem Grund unterstützen wir nun den Import von Standardargumenten in C++/CLI. Durch diese Änderung kann es bei vorhandenem Code, in dem mehrere Überladungen deklariert sind, zu Fehlern kommen, wie im folgenden Beispiel gezeigt:

```cpp
public class R {
    public void Func(string s) {}   // overload 1
    public void Func(string s, string s2 = "") {} // overload 2;
}
```

Wenn diese Klasse in C++/CLI importiert wird, tritt beim Aufruf einer der Überladungen ein Fehler auf:

```cpp
    (gcnew R)->Func("abc"); // error C2668: 'R::Func' ambiguous call to overloaded function
```

Der Compiler gibt den Fehler C2668 aus, weil beide Überladungen dieser Argumentliste entsprechen. In der zweiten Überladung wird das zweite Argument vom Standardargument gefüllt. Um dieses Problem zu umgehen, können Sie die redundante Überladung (1) löschen. Alternativ verwenden Sie die vollständige Argumentliste und geben die Standardargumente explizit an.

## <a name="conformance-improvements-in-visual-studio-2019-version-167"></a><a name="improvements_167"></a> Verbesserungen der Konformität in Visual Studio 2019, Version 16.7

### <a name="definition-of-is-trivially-copyable"></a>Definition von *ist trivial kopierbar*

In C++20 wurde die Definition von *ist trivial kopierbar* geändert. Wenn eine Klasse einen nicht statischen Datenmember mit als mit **`volatile`** qualifiziertem Typ hat, bedeutet dies nicht mehr, dass ein vom Compiler generierter Kopier- oder Verschiebekonstruktor oder ein Kopier- oder Verschiebezuweisungsoperator nicht trivial ist. Der Ausschuss für den C++-Standard hat diese Änderung rückwirkend als Fehlerbericht angewendet. In MSVC ändert sich das Compilerverhalten in verschiedenen Sprachmodi, wie z. B. **`/std:c++14`** oder **`/std:c++latest`** , nicht.

Es folgt ein Beispiel des neuen Verhaltens:

```cpp
#include <type_traits>

struct S
{
    volatile int m;
};

static_assert(std::is_trivially_copyable_v<S>, "Meow!");
```

Dieser Code lässt sich nicht in Versionen von MSVC vor Visual Studio 2019, Version 16.7 kompilieren. Es gibt eine standardmäßige Compilerwarnung, die Sie verwenden können, um diese Änderung zu erkennen. Wenn Sie den obigen Code mithilfe von **`cl /W4 /w45220`** kompilieren, wird die folgende Warnung angezeigt:

Warnung C5220: `'S::m': a non-static data member with a volatile qualified type no longer implies that compiler generated copy/move constructors and copy/move assignment operators are non trivial`

### <a name="pointer-to-member-and-string-literal-conversions-to-bool-are-narrowing"></a>Konvertierungen von Pointer-to-Member-Funktionen und Zeichenfolgenliteralen in `bool` sind einschränkend.

Der Ausschuss für den C++-Standard hat vor Kurzem den Fehlerbericht [P1957R2](https://wg21.link/p1957r2) akzeptiert, der `T*` ->  **`bool`** als einschränkende Konvertierung einstuft. In MSVC wurde ein Fehler in seiner Implementierung behoben, der zuvor `T*` ->  **`bool`** als einschränkend diagnostiziert hatte, aber nicht die Konvertierung eines Zeichenfolgenliterals in **`bool`** oder einer Pointer-to-Member-Funktion in **`bool`** erkannte.

Das folgende Programm ist in Visual Studio 2019, Version 16.7 fehlerhaft formatiert:

```cpp
struct X { bool b; };
void f(X);

int main() {
    f(X { "whoops?" }); // error: conversion from 'const char [8]' to 'bool' requires a narrowing conversion

    int (X::* p) = nullptr;
    f(X { p }); // error: conversion from 'int X::*' to 'bool' requires a narrowing conversion
}
```

Um diesen Code zu korrigieren, fügen Sie entweder **`nullptr`** explizite Vergleiche hinzu, oder vermeiden Sie Kontexte, in denen einschränkende Konvertierungen fehlerhaft formatiert sind:

```cpp
struct X { bool b; };
void f(X);

int main() {
    f(X { "whoops?" != nullptr }); // Absurd, but OK

    int (X::* p) = nullptr;
    f(X { p != nullptr }); // OK
}
```

### <a name="nullptr_t-is-only-convertible-to-bool-as-a-direct-initialization"></a>`nullptr_t` kann nur als direkte Initialisierung in `bool` konvertiert werden

In C++11 ist **`nullptr`** nur als eine *direkte Konvertierung* in **`bool`** konvertierbar, z. B. wenn Sie eine **`bool`** mithilfe einer Initialisierungsliste in geschweiften Klammern initialisieren. Diese Einschränkung wurde von MSVC nie erzwungen. MSVC implementiert die Regel nun gemäß [`/permissive-`](../build/reference/permissive-standards-conformance.md). Implizite Konvertierungen werden nun als fehlerhaft formatiert diagnostiziert. Eine kontextabhängige Konvertierung in **`bool`** ist weiterhin zulässig, da die direkte Initialisierung `bool b(nullptr)` gültig ist.

In den meisten Fällen können Sie den Fehler beheben, indem Sie, wie im folgenden Beispiel gezeigt, **`nullptr`** durch **`false`** ersetzen:

```cpp
struct S { bool b; };
void g(bool);
bool h() { return nullptr; } // error, should be 'return false;'

int main() {
    bool b1 = nullptr; // error: cannot convert from 'nullptr' to 'bool'
    S s { nullptr }; // error: cannot convert from 'nullptr' to 'bool'
    g(nullptr); // error: cannot convert argument 1 from 'nullptr' to 'bool'

    bool b2 { nullptr }; // OK: Direct-initialization
    if (!nullptr) {} // OK: Contextual conversion to bool
}
```

### <a name="conforming-initialization-behavior-for-array-initializations-with-missing-initializers"></a>Konformes Initialisierungsverhalten für Arrayinitialisierungen mit fehlenden Initialisierern

Bislang zeigte MSVC ein nicht konformes Verhalten für Arrayinitialisierungen mit fehlenden Initialisierern. MSVC rief stets den Standardkonstruktor für jedes Arrayelement ohne Initialisierer auf. Das Standardverhalten besteht darin, jedes Element mit einer leeren Initialisierungsliste in geschweiften Klammern zu initialisieren ( **`{}`** ). Der Initialisierungskontext für eine leere Initialisierungsliste in geschweiften Klammern ist die Kopierinitialisierung, die keine Aufrufe an explizite Konstruktoren erlaubt. Es kann auch Laufzeitunterschiede geben, weil die Verwendung von `{}` zur Initialisierung einen Konstruktor aufrufen kann, der anstelle des Standardkonstruktors `std::initializer_list` verwendet. Das konforme Verhalten wird gemäß [`/permissive-`](../build/reference/permissive-standards-conformance.md) aktiviert.

Es folgt ein Beispiel des geänderten Verhaltens:

```cpp
struct B {
    explicit B() {}
};

void f() {
    B b1[1]{}; // Error in /permissive-, because aggregate init calls explicit ctor
    B b2[1]; // OK: calls default ctor for each array element
}
```

## <a name="bug-fixes-and-behavior-changes-in-visual-studio-2019"></a><a name="update_160"></a> Fehlerbehebungen und Verhaltensänderungen in Visual Studio 2019

### <a name="reinterpret_cast-in-a-constexpr-function"></a>`reinterpret_cast` in einer `constexpr`-Funktion

**`reinterpret_cast`** ist in einer **`constexpr`** -Funktion nicht zulässig. Der Microsoft-C++-Compiler lehnte **`reinterpret_cast`** früher nur bei Verwendung in einem **`constexpr`** -Kontext ab. In Visual Studio 2019 diagnostiziert der Compiler im Modus für alle Sprachstandards **`reinterpret_cast`** ordnungsgemäß in der Definition einer **`constexpr`** -Funktion. Mit dem folgenden Code wird nun „C3615: `constexpr function 'f' cannot result in a constant expression`“ ausgelöst.

```cpp
long long i = 0;
constexpr void f() {
    int* a = reinterpret_cast<int*>(i);
}
```

Entfernen Sie den Modifizierer **`constexpr`** aus der Funktionsdeklaration, um den Fehler zu vermeiden.

### <a name="correct-diagnostics-for-basic_string-range-constructor"></a>Richtige Diagnose für den Bereichskonstruktor „basic_string“

In Visual Studio 2019 unterdrückt der `basic_string`-Bereichskonstruktor nicht mehr die Compilerdiagnose mit **`static_cast`** . Der folgende Code wird in Visual Studio 2017 ohne Warnungen kompiliert, obwohl bei der Konvertierung von **`wchar_t`** in **`char`** ein Datenverlust auftreten kann, wenn `out` initialisiert wird:

```cpp
std::wstring ws = /* … */;
std::string out(ws.begin(), ws.end());
```

Visual Studio 2019 löst ordnungsgemäß die Warnung „C4244: `'argument': conversion from 'wchar_t' to 'const _Elem', possible loss of data`“ aus. Sie können std::string wie im folgenden Beispiel initialisieren, um die Warnung zu vermeiden:

```cpp
std::wstring ws = L"Hello world";
std::string out;
for (wchar_t ch : ws)
{
    out.push_back(static_cast<char>(ch));
}
```

### <a name="incorrect-calls-to--and---under-clr-or-zw-are-now-correctly-detected"></a>Fehlerhafte Aufrufe von `+=` und `-=` unter `/clr` und `/ZW` werden nun ordnungsgemäß erkannt

In Visual Studio 2017 wurde ein Fehler eingeführt, durch den der Compiler Fehler stillschweigend ignoriert und keinen Code für ungültige Aufrufe von **`+=`** und **`-=`** unter **`/clr`** oder **`/ZW`** generiert hat. Der folgende Code wird in Visual Studio 2017 fehlerfrei kompiliert, löst in Visual Studio 2019 jedoch ordnungsgemäß den Fehler „C2845: `'System::String ^': pointer arithmetic not allowed on this type`“ aus:

```cpp
public enum class E { e };

void f(System::String ^s)
{
    s += E::e; // C2845 in VS2019
}
```

Um den Fehler in diesem Beispiel zu vermeiden, verwenden Sie den Operator **`+=`** mit der Methode `ToString()`: `s += E::e.ToString();`.

### <a name="initializers-for-inline-static-data-members"></a>Initialisierer für statische Inline-Datenmember

Ungültiger Memberzugriff innerhalb der Initialisierer **`inline`** und **`static constexpr`** wird nun ordnungsgemäß erkannt. Der folgende Beispielcode wird in Visual Studio 2017 fehlerfrei kompiliert, in Visual Studio 2019 wird im **`/std:c++17`** -Modus jedoch der Fehler „C2248: `cannot access private member declared in class 'X'`“ ausgelöst.

```cpp
struct X
{
    private:
        static inline const int c = 1000;
};

struct Y : X
{
    static inline int d = c; // C2248 in Visual Studio 2019
};
```

Deklarieren Sie den Member `X::c` als geschützt, um diesen Fehler zu vermeiden:

```cpp
struct X
{
    protected:
        static inline const int c = 1000;
};
```

### <a name="c4800-reinstated"></a>Wiederherstellung der Warnung C4800

MSVC verwendete bisher die Leistungswarnung C4800 bei einer impliziten Konvertierung in **`bool`** . Sie war zu störend und konnte nicht unterdrückt werden, sodass wir sie in Visual Studio 2017 entfernt haben. Allerdings gab es während des Lebenszyklus von Visual Studio 2017 viel Feedback zu den nützlichen Fällen, die dank dieser Warnung behoben werden konnten. Daher haben wir die Warnung C4800 sorgfältig angepasst und bieten sie in Visual Studio 2019 zusammen mit einer erläuternden C4165 wieder an. Beide Warnungen können problemlos unterdrückt werden: entweder durch eine explizite Umwandlung oder durch den Vergleich mit 0 des entsprechenden Typs. Die Warnung C4800 ist eine standardmäßig deaktivierte Warnung der Stufe 4, und die Warnung C4165 ist eine standardmäßig deaktivierte Warnung der Stufe 3. Beide können mithilfe der Compileroption **`/Wall`** gefunden werden.

Im folgenden Beispiel werden die Warnungen C4800 und C4165 in **`/Wall`** ausgelöst:

```cpp
bool test(IUnknown* p)
{
    bool valid = p; // warning C4800: Implicit conversion from 'IUnknown*' to bool. Possible information loss
    IDispatch* d = nullptr;
    HRESULT hr = p->QueryInterface(__uuidof(IDispatch), reinterpret_cast<void**>(&d));
    return hr; // warning C4165: 'HRESULT' is being converted to 'bool'; are you sure this is what you want?
}
```

Sie können den Code folgendermaßen schreiben, um die Warnungen im vorherigen Beispiel zu vermeiden:

```cpp
bool test(IUnknown* p)
{
    bool valid = p != nullptr; // OK
    IDispatch* d = nullptr;
    HRESULT hr = p->QueryInterface(__uuidof(IDispatch), reinterpret_cast<void**>(&d));
    return SUCCEEDED(hr);  // OK
}
```

### <a name="local-class-member-function-doesnt-have-a-body"></a>Lokale Klassenmemberfunktion enthält keinen Text

In Visual Studio 2017 wird die Warnung „C4822: `Local class member function doesn't have a body`“ nur ausgelöst, wenn die Compileroption **`/w14822`** explizit festgelegt ist. Bei Verwendung von **`/Wall`** wird sie nicht angezeigt. In Visual Studio 2019 ist die Warnung C4822 standardmäßig deaktiviert und in **`/Wall`** auffindbar, ohne dass **`/w14822`** explizit festgelegt sein muss.

```cpp
void example()
{
    struct A
        {
            int boo(); // warning C4822
        };
}
```

### <a name="function-template-bodies-containing-if-constexpr-statements"></a>Funktionsvorlagentexte, die `if constexpr`-Anweisungen enthalten

Für Funktionsvorlagentexte, die **`if constexpr`** -Anweisungen enthalten, sind einige auf die Analyse bezogene [`/permissive-`](../build/reference/permissive-standards-conformance.md)-Überprüfungen aktiviert. Der folgende Code löst in Visual Studio 2017 z. B. nur dann „C7510: `'Type': use of dependent type name must be prefixed with 'typename'`“ aus, wenn die Option **`/permissive-`** nicht festgelegt ist. Der gleiche Code löst in Visual Studio 2019 selbst dann Fehler aus, wenn die Option **`/permissive-`** festgelegt ist:

```cpp
template <typename T>

int f()
{
    T::Type a; // error C7510

    if constexpr (T::val)
    {
        return 1;
    }
    else
    {
        return 2;
    }
}

struct X
{
    using Type = X;
    constexpr static int val = 1;
};

int main()
{
    return f<X>();
}
```

Fügen Sie das Schlüsselwort **`typename`** zur Deklaration von `a` hinzu, um den Fehler zu vermeiden: `typename T::Type a;`.

### <a name="inline-assembly-code-isnt-supported-in-a-lambda-expression"></a>Inlineassemblycode wird in Lambdaausdrücken nicht unterstützt

Das Microsoft C++-Team wurde vor Kurzem auf ein Sicherheitsproblem hingewiesen, durch das die Verwendung von Inlineassemblern innerhalb eines Lambdaausdrucks bei der Ausführung zur Beschädigung von `ebp` (das Register für Rückgabeadressen) führen kann. Ein böswilliger Angreifer könnte sich dieses Szenario zunutze machen. Der Inlineassembler wird nur bei x86 unterstützt, und zwischen dem Inlineassembler und den übrigen Elementen des Compilers findet keine zufriedenstellende Interaktion statt. Aufgrund dieser Tatsachen und der Art des Problems bestand die sicherste Lösung darin, den Inlineassembler innerhalb eines Lambdaausdrucks nicht zuzulassen.

Die einzige Verwendung eines Inlineassemblers innerhalb eines Lambdaausdrucks, die in der Praxis gefunden wurde, war das Erfassen der Rückgabeadresse. In diesem Szenario können Sie die Rückgabeadresse auf allen Plattformen erfassen, indem Sie einfach die intrinsische Compilerfunktion `_ReturnAddress()` verwenden.

Der folgende Code erzeugt sowohl in Visual Studio 2017 15.9 als auch in Visual Studio 2019 den Fehler „C7552: `inline assembler is not supported in a lambda`“:

```cpp
#include <cstdio>

int f()
{
    int y = 1724;
    int x = 0xdeadbeef;

    auto lambda = [&]
    {
        __asm {

            mov eax, x
            mov y, eax
        }
    };

    lambda();
    return y;
}
```

Verschieben Sie den Assemblycode wie im folgenden Beispiel gezeigt in eine benannte Funktion, um diesen Fehler zu vermeiden:

```cpp
#include <cstdio>

void g(int& x, int& y)
{
    __asm {
        mov eax, x
        mov y, eax
    }
}

int f()
{
    int y = 1724;
    int x = 0xdeadbeef;
    auto lambda = [&]
    {
        g(x, y);
    };
    lambda();
    return y;
}

int main()
{
    std::printf("%d\n", f());
}
```

### <a name="iterator-debugging-and-stdmove_iterator"></a>Iteratordebuggen und `std::move_iterator`

Das Feature für das Iteratordebuggen kann `std::move_iterator` nun ordnungsgemäß entpacken. Beispielsweise kann `std::copy(std::move_iterator<std::vector<int>::iterator>, std::move_iterator<std::vector<int>::iterator>, int*)` nun den schnellen Pfad `memcpy` binden.

### <a name="fixes-for-xkeycheckh-keyword-enforcement"></a>Fehlerbehebung der Schlüsselworterzwingung \<xkeycheck.h>

Die Erzwingung der Standardbibliothek in \<xkeycheck.h> für Makros, die ein Schlüsselwort ersetzen, wurde korrigiert. Die Bibliothek gibt nun das tatsächlich erkannte problematische Schlüsselwort statt einer allgemeinen Meldung aus. C++20-Schlüsselwörter werden ebenfalls unterstützt, und es wird vermieden, dass IntelliSense zufällige Schlüsselwörter als Makros erkennt.

### <a name="allocator-types-no-longer-deprecated"></a>Zuweisungstypen sind nicht mehr als veraltet markiert.

`std::allocator<void>`, `std::allocator::size_type` und `std::allocator::difference_type` sind nicht mehr als veraltet markiert.

### <a name="correct-warning-for-narrowing-string-conversions"></a>Richtige Warnungen für einschränkende Zeichenfolgenkonvertierungen

Ein nicht beabsichtigter **`static_cast`** von `std::string`, der für den Standard nicht erforderlich ist und versehentlich C4244-Warnungen unterdrückt hat, wurde entfernt. Beim Versuch, `std::string::string(const wchar_t*, const wchar_t*)` aufzurufen, wird nun ordnungsgemäß die Warnung „C4244 `narrowing a wchar_t into a char`“ ausgelöst.

### <a name="various-fixes-for-filesystem-correctness"></a>Verschiedene Korrekturen für die Richtigkeit von \<filesystem>

- Das Fehlschlagen von `std::filesystem::last_write_time` beim Versuch, den letzten Schreibzugriff eines Verzeichnisses zu ändern, wurde behoben.
- Der Konstruktor `std::filesystem::directory_entry` speichert nun ein fehlgeschlagenes Ergebnis, anstatt eine Ausnahme auszulösen, wenn ein nicht vorhandener Zielpfad angegeben wird.
- Die Version von `std::filesystem::create_directory` mit zwei Parametern wurde geändert, sodass nun die Version mit einem Parameter aufgerufen wird, da die zugrundeliegende `CreateDirectoryExW`-Funktion `copy_symlink` verwenden würde, wenn `existing_p` eine symbolische Verknüpfung ist.
- `std::filesystem::directory_iterator` schlägt nicht mehr fehl, wenn eine fehlerhafte symbolische Verknüpfung festgestellt wird.
- `std::filesystem::space` akzeptiert jetzt relative Pfade.
- `std::filesystem::path::lexically_relative` wird nicht mehr durch nachstehende Schrägstriche behindert (siehe [LWG 3096](https://cplusplus.github.io/LWG/issue3096)).
- Das Ablehnen von Pfaden mit umgekehrten Schrägstrichen von `CreateSymbolicLinkW` in `std::filesystem::create_symlink` wurde behoben.
- Es wurde ein Problem behoben, bei dem die `delete`-Funktion des POSIX-Löschmodus unter Windows 10 LTSB 1609 zwar vorhanden war, aber keine Dateien löschen konnte.
- Die Kopierkonstruktoren und Kopierzuweisungsoperatoren von `std::boyer_moore_searcher` und `std::boyer_moore_horspool_searcher` sind nun in der Lage, Kopiervorgänge tatsächlich durchzuführen.

### <a name="parallel-algorithms-on-windows-8-and-later"></a>Parallele Algorithmen unter Windows 8 und höher

Die Bibliothek mit parallelen Algorithmen verwendet unter Windows 8 und höher nun ordnungsgemäß die echte `WaitOnAddress`-Familie, anstatt immer die gefälschten Versionen von Windows 7 und früher zu verwenden.

### <a name="stdsystem_categorymessage-whitespace"></a>`std::system_category::message()` Leerzeichen

`std::system_category::message()` schneidet nachstehenden Leerraum von der zurückgegebenen Meldung nun ab.

### <a name="stdlinear_congruential_engine-divide-by-zero"></a>`std::linear_congruential_engine` Division durch 0

Einige Bedingungen wurden behoben, die dazu führten, dass `std::linear_congruential_engine` eine Division durch 0 (null) durchführte.

### <a name="fixes-for-iterator-unwrapping"></a>Fehlerbehebungen für das Entpacken von Iteratoren

In Visual Studio 2017, Version 15.8 wurde erstmalig eine Funktion zum Entpacken von Iteratoren für Programmierer zur Verfügung gestellt, wie im C++-Teamblogartikel [STL Features and Fixes in VS 2017 15.8](https://devblogs.microsoft.com/cppblog/stl-features-and-fixes-in-vs-2017-15-8/) (STL-Funktionen und Fehlerbehebungen in VS 2017 15.8) beschrieben. Mit dieser Funktion werden Iteratoren, die von Standardbibliotheksiteratoren abgeleitet wurden, nicht mehr entpackt. Ein Benutzer, der beispielsweise von `std::vector<int>::iterator` abgeleitet wird und versucht, das Verhalten anzupassen, erhält nun das angepasste Verhalten, wenn er Algorithmen der Standardbibliothek aufruft, anstelle des Verhaltens eines Zeigers.

Die `reserve`-Funktion für ungeordnete Container reserviert N-Elemente nun tatsächlich (siehe [LWG 2156](https://cplusplus.github.io/LWG/issue2156)).

### <a name="time-handling"></a>Behandlung von Zeit

- Zuvor führten einige Zeitwerte, die an die Parallelitätsbibliothek übergeben wurden, zu einem Überlauf, z. B. `condition_variable::wait_for(seconds::max())`. Diese mittlerweile behobenen Überläufe haben das Verhalten in einem scheinbar willkürlichen 29-tägigen Zyklus geändert (wenn von den zugrundeliegenden Win32-APIs akzeptierte uint32_t Millisekunden zu einem Überlauf führten).

- Der \<ctime>-Header deklariert `timespec` und `timespec_get` jetzt im Namespace `std` und auch im globalen Namespace ordnungsgemäß.

### <a name="various-fixes-for-containers"></a>Verschiedene Fehlerbehebungen für Container

- Viele interne Containerfunktionen der Standardbibliothek sind nun privat, um die Funktionsweise von IntelliSense zu verbessern. In zukünftigen Releases von MSVC sind weitere Fehlerbehebungen zu erwarten, die Member als privat kennzeichnen.

- Probleme bei der Richtigkeit der Ausnahmesicherheit, durch die knotenbasierte Container wie `list`, `map` und `unordered_map` beschädigt wurden, wurden behoben. Während einem `propagate_on_container_copy_assignment`- oder `propagate_on_container_move_assignment`-Neuzuweisungsvorgang würden Sie den Sentinelknoten des Containers mit der alten Zuweisung freistellen, die alte Zuweisung mit der POCCA/POCMA-Zuweisung überschreiben und dann versuchen, den Sentinelknoten der neuen Zuweisung abzurufen. Wenn diese Zuteilung fehlschlug, wurde der Container beschädigt. Er konnte nicht einmal zerstört werden, da der Besitz eines Sentinelknotens eine feste Datenstrukturinvariante darstellt. Dieser Code wurde so korrigiert, dass der neue Sentinelknoten unter Verwendung des Zuteilers des Quellcontainers erstellt wurde, bevor der bestehende Sentinelknoten zerstört wurde.

- Die Container wurden behoben, sodass sie Zuweisungen immer in `propagate_on_container_copy_assignment`, `propagate_on_container_move_assignment` und `propagate_on_container_swap` kopieren/verschieben/tauschen. Dies gilt auch für Zuweisungen mit einer Deklaration von `is_always_equal`.

- Es wurden die Überladungen für Funktionen zum Zusammenführen und Extrahieren von Membern hinzugefügt, die rvalue-Container akzeptieren. Weitere Informationen finden Sie unter [P0083 „Splicing Maps and Sets“](https://wg21.link/p0083r3).

### <a name="stdbasic_istreamread-processing-of-rn--n"></a>`std::basic_istream::read`-Verarbeitung von `\r\n`` => `\n`

`std::basic_istream::read` wurde so korrigiert, dass bei der Verarbeitung von `\r\n` => `\n` nicht temporär in den angegebenen Puffer geschrieben wird. Durch diese Änderung entfällt ein Teil des Leistungsvorteils, der in Visual Studio 2017 15.8 für Lesezugriffe größer als 4K erzielt wurde. Es gibt jedoch weiterhin Effizienzsteigerungen durch die Vermeidung von drei virtuellen Aufrufen pro Zeichen.

### <a name="stdbitset-constructor"></a>`std::bitset`-Konstruktor

Der Konstruktor von `std::bitset` liest die Einsen und Nullen von großen Bitsets nicht mehr in umgekehrter Reihenfolge.

### <a name="stdpairoperator-regression"></a>`std::pair::operator=`-Regression

Eine Regression im Zuweisungsoperator von `std::pair` wurde behoben, die bei der Implementierung von [LWG 2729 "Missing SFINAE on std::pair::operator="; (SFINAE für std::pair::operator= fehlt)](https://cplusplus.github.io/LWG/issue2729) eingeführt wurde. Typen, die in `std::pair` konvertiert werden können, werden nun wieder ordnungsgemäß akzeptiert.

### <a name="non-deduced-contexts-for-add_const_t"></a>Nicht abgeleitete Kontexte für `add_const_t`

Ein kleiner Fehler bei Typmerkmalen wurde behoben, bei dem `add_const_t` und zugehörige Funktionen einem nicht abgeleiteten Kontext entsprechen sollten. Das heißt, `add_const_t` sollte ein Alias für `typename add_const<T>::type` sein, nicht für `const T`.

## <a name="bug-fixes-and-behavior-changes-in-162"></a><a name="update_162"></a> Fehlerbehebungen und Verhaltensänderungen in 16.2

### <a name="const-comparators-for-associative-containers"></a>Const-Vergleichsoperatoren für assoziative Container

Der Code für die Suche und das Einfügen in [Menge](../standard-library/set-class.md), [Zuordnung](../standard-library/map-class.md), [Multimenge](../standard-library/multiset-class.md), und [Mehrfachzuordnung](../standard-library/multimap-class.md) wurde zusammengeführt, um die Codegröße zu reduzieren. Auf die gleiche Weise wie früher bei Suchvorgängen rufen Einfügevorgänge nun den „Kleiner als“-Vergleich in einem **`const`** -Vergleichsfunktor auf. Der folgende Code wird in Visual Studio 2019 Version 16.1 und früher kompiliert, erzeugt jedoch C3848 in Visual Studio 2019 Version 16.2:

```cpp
#include <iostream>
#include <map>

using namespace std;

struct K
{
   int a;
   string b = "label";
};

struct Comparer  {
   bool operator() (K a, K b) {
      return a.a < b.a;
   }
};

map<K, double, Comparer> m;

K const s1{1};
K const s2{2};
K const s3{3};

int main() {

   m.emplace(s1, 1.08);
   m.emplace(s2, 3.14);
   m.emplace(s3, 5.21);

}
```

Legen Sie den Vergleichsoperator als **`const`** fest, um den Fehler zu vermeiden:

```cpp
struct Comparer  {
   bool operator() (K a, K b) const {
      return a.a < b.a;
   }
};

```

## <a name="bug-fixes-and-behavior-changes-in-visual-studio-2019-version-167"></a><a name="updates_167"></a> Fehlerbehebungen und Verhaltensänderungen in Visual Studio 2019, Version 16.7

### <a name="initialization-of-class-members-with-overloaded-names-is-correctly-sequenced"></a>Initialisierung von Klassenmembern mit überladenen Namen wird richtig sequenziert

Wir haben einen Fehler in der internen Darstellung von Klassendatenmembern festgestellt, wenn ein Typname auch als Name eines Datenmembers überladen wird. Dieser Fehler führte zu Inkonsistenzen bei der Aggregatinitialisierung und der Initialisierungsreihenfolge der Member. Der generierte Initialisierungscode ist nun korrekt. Diese Änderung kann jedoch zu Fehlern oder Warnungen in der Quelle führen, die wie in diesem Beispiel versehentlich auf die falsch geordneten Member zurückgriffen:

```cpp
// Compiling with /w15038 now gives:
// warning C5038: data member 'Outer::Inner' will be initialized after data member 'Outer::v'
struct Outer {
    Outer(int i, int j) : Inner{ i }, v{ j } {}

    struct Inner { int x; };
    int v;
    Inner Inner; // 'Inner' is both a type name and data member name in the same scope
};
```

In früheren Versionen hat der Konstruktor den Datenmember `Inner` fälschlicherweise vor dem Datenmember `v` initialisiert. (Der C++-Standard erfordert eine Initialisierungsreihenfolge, die mit der Deklarationsreihenfolge der Member übereinstimmt.) Nun, da der generierte Code dem Standard folgt, ist die Memberinitialisierungsliste nicht in der richtigen Reihenfolge. Der Compiler generiert eine Warnung für dieses Beispiel. Um dies zu korrigieren, ordnen Sie die Memberinitialisierungsliste so an, dass sie die Deklarationsreihenfolge widerspiegelt.

### <a name="overload-resolution-involving-integral-overloads-and-long-arguments"></a>Überladungsauflösung mit integralen Überladungen und `long`-Argumenten

Der C++-Standard erfordert als Standardkonvertierung eine Konvertierung von **`long`** in **`int`** . Frühere MSVC-Compiler stufen sie fälschlicherweise als integrale Höherstufung ein, die für die Überladungsauflösung einen höheren Rang einnimmt. Diese Rangfolge kann bewirken, dass die Überladungsauflösung erfolgreich erfolgt, wenn Sie als nicht eindeutig eingestuft wird.

Der Compiler berücksichtigt nun im Modus [`/permissive-`](../build/reference/permissive-standards-conformance.md) den Rang ordnungsgemäß. Ungültiger Code wird wie in diesem Beispiel ordnungsgemäß diagnostiziert:

```cpp
void f(long long);
void f(int);

int main() {
    long x {};
    f(x); // error: 'f': ambiguous call to overloaded function
    f(static_cast<int>(x)); // OK
}
```

Sie können dieses Problem auf verschiedene Arten beheben:

- Ändern Sie in der Aufrufsite den Typ des übergebenen Arguments in **`int`** . Sie können entweder den Variablentyp ändern oder ihn umwandeln.

- Wenn es viele Aufrufsites gibt, können Sie eine weitere Überladung hinzufügen, die ein **`long`** -Argument verwendet. In dieser Funktion wandeln Sie das Argument um und leiten es an die **`int`** -Überladung weiter.

### <a name="use-of-undefined-variable-with-internal-linkage"></a>Verwendung einer nicht definierten Variablen mit interner Bindung

Versionen von MSVC vor Visual Studio 2019, Version 16.7 akzeptierten die Verwendung der deklarierten Variablen **`extern`** , die eine interne Bindung hatte und nicht definiert war. Solche Variablen können in keiner anderen Übersetzungseinheit definiert werden und kein gültiges Programm bilden. Der Compiler diagnostiziert diesen Fall nun zur Kompilierzeit. Der Fehler ähnelt dem Fehler für nicht definierte statische Funktionen.

```cpp
namespace {
    extern int x; // Not a definition, but has internal linkage because of the anonymous namespace
}

int main()
{
    return x; // Use of 'x' that no other translation unit can possibly define.
}
```

Dieses Programm wurde zuvor falsch kompiliert und verknüpft, gibt nun aber Folgendes aus:

Fehler C7631: `'anonymous-namespace'::x': variable with internal linkage declared but not defined`

Solche Variablen müssen in derselben Übersetzungseinheit definiert werden, in der sie verwendet werden. Beispielsweise können Sie einen expliziten Initialisierer oder eine separate Definition bereitstellen.

### <a name="type-completeness-and-derived-to-base-pointer-conversions"></a>Typvollständigkeit und von Basisklasse abgeleitete Zeigerkonvertierungen

In C++-Standards vor C++20 erforderte eine Konvertierung von einer abgeleiteten Klasse in eine Basisklasse nicht, dass die abgeleitete Klasse ein vollständiger Klassentyp sein musste. Der Ausschuss für den C++-Standard hat eine rückwirkende Änderung des Fehlerberichts genehmigt, die für alle Versionen der Sprache C++ gilt. Durch diese Änderung wird der Konvertierungsprozess an Typmerkmale, wie z. B. `std::is_base_of`, angeglichen, die erfordern, dass die abgeleitete Klasse ein vollständiger Klassentyp ist.

Hier sehen Sie ein Beispiel:

```cpp
template<typename A, typename B>
struct check_derived_from
{
    static A a;
    static constexpr B* p = &a;
};

struct W { };
struct X { };
struct Y { };

// With this change this code will fail as Z1 is not a complete class type
struct Z1 : X, check_derived_from<Z1, X>
{
};

// This code failed before and it will still fail after this change
struct Z2 : check_derived_from<Z2, Y>, Y
{
};

// With this change this code will fail as Z3 is not a complete class type
struct Z3 : W
{
    check_derived_from<Z3, W> cdf;
};
```

Diese Behavior Change gilt für alle C++-Sprachmodi von MSVC, nicht nur für **`/std:c++latest`** .

### <a name="narrowing-conversions-are-more-consistently-diagnosed"></a>Einschränkende Konvertierungen werden einheitlicher diagnostiziert

MSVC gibt eine Warnung für einschränkende Konvertierungen in einem Listeninitialisierer in geschweiften Klammern aus. Bisher diagnostizierte der Compiler keine einschränkenden Konvertierungen von größeren zugrunde liegenden **`enum`** -Typen in einschränkendere integrale Typen. (Der Compiler betrachtete sie fälschlicherweise als integrale Höherstufung statt als Konvertierung.) Wenn die einschränkende Konvertierung beabsichtigt ist, können Sie die Warnung vermeiden, indem Sie für das Initialisiererargument **`static_cast`** verwenden. Oder wählen Sie einen größeren integralen Zieltyp aus.

Hier ist ein Beispiel für die Verwendung einer expliziten **`static_cast`** , um auf die Warnung zu reagieren:

```cpp
enum E : long long { e1 };
struct S { int i; };

void f(E e) {
    S s = { e }; // warning: conversion from 'E' to 'int' requires a narrowing conversion
    S s1 = { static_cast<int>(e) }; // Suppress warning with explicit conversion
}
```

::: moniker-end

::: moniker range="vs-2017"

## <a name="conformance-improvements-in-visual-studio-2017-rtw-version-150"></a><a name="improvements_150"></a> Verbesserungen der Konformität in Visual Studio 2017 RTW (Version 15.0)

Mit der Unterstützung für generalisierte **`constexpr`** -Elemente und der Initialisierung für nicht statische Datenelemente (Non-Static Data Member Initialization, NSDMI) für Aggregate ist der Microsoft-C++-Compiler in Visual Studio 2017 für Features, die im C++14-Standard hinzugefügt wurden, jetzt vollständig. Dem Compiler fehlen jedoch noch einige Funktionen der C++11- und C++98-Standards. Eine Tabelle mit dem aktuellen Compilerstatus finden Sie unter [Microsoft C++-Sprachkonformität: Tabelle](../visual-cpp-language-conformance.md).

### <a name="c11-expression-sfinae-support-in-more-libraries"></a>C++11: Unterstützung für SFINAE für Ausdrücke in mehr Bibliotheken

Die Unterstützung für den SFINAE-Ausdruck wird im Compiler weiterhin verbessert. Dies ist für die Vorlagenargumentableitung und -ersetzung erforderlich, bei der die Ausdrücke **`decltype`** und **`constexpr`** möglicherweise als Vorlagenparameter angezeigt werden. Weitere Informationen finden Sie unter [Expression SFINAE improvements in Visual Studio 2017 RC (Verbesserungen der SFINAE für Ausdrücke in Visual Studio 2017)](https://devblogs.microsoft.com/cppblog/expression-sfinae-improvements-in-vs-2015-update-3/).

### <a name="c14-nsdmi-for-aggregates"></a>C++14: NSDMI für Aggregate

Ein Aggregat ist ein Array oder eine Klasse, die Folgendes aufweist: keinen vom Benutzer bereitgestellten Konstruktor, keine nicht statischen Datenmember, die privat oder geschützt sind, keine Basisklassen und keine virtuellen Funktionen. Ab C++14 können Aggregate Memberinitialisierer enthalten. Weitere Informationen finden Sie unter [Member initializers and aggregates (Memberinitialisierer und Aggregate)](https://wg21.link/n3605).

### <a name="c14-extended-constexpr"></a>C++14: Erweiterte `constexpr`

Als **`constexpr`** deklarierte Ausdrücke dürfen jetzt bestimmte Arten von Deklarationen, IF- und SWITCH-Anweisungen, Schleifenanweisungen und Mutationen von Objekten enthalten, deren Lebensdauer in der Auswertung von **`constexpr`** -Ausdrücken begonnen hat. Darüber hinaus ist es nicht mehr erforderlich, dass eine nicht statische Memberfunktion von **`constexpr`** implizit **`const`** ist. Weitere Informationen finden Sie unter [Relaxing constraints on `constexpr` functions (Lockerung der Einschränkungen für constexpr-Funktionen)](https://wg21.link/n3652).

### <a name="c17-terse-static_assert"></a>C++17: Nicht ausführliche `static_assert`

Der Meldungsparameter für **`static_assert`** ist optional. Weitere Informationen finden Sie unter [Extending static_assert, v2 (Erweitern des static_assert, v2)](https://wg21.link/n3928).

### <a name="c17-fallthrough-attribute"></a>C++17: `[[fallthrough]]`-Attribut

Im **`/std:c++17`** -Modus kann das `[[fallthrough]]`-Attribut im Kontext von switch-Anweisungen als Hinweis für den Compiler verwendet werden, dass das Fall-Through-Verhalten vorgesehen ist. Dieses Attribut verhindert, dass der Compiler in solchen Fällen Warnungen ausgeben kann. Weitere Informationen finden Sie unter [Wording for `[[fallthrough]]` attribute](https://wg21.link/p0188r0) (Worlaut für [[fallthrough]]-Attribut).

### <a name="generalized-range-based-for-loops"></a>Verallgemeinerte bereichsbasierte for-Schleifen

Bereichsbezogene for-Schleifen erfordern nicht mehr, dass `begin()` und `end()` Objekte des gleichen Typs zurückgeben. Diese Änderung ermöglicht `end()` die Rückgabe eines Sentinels wie von Bereichen in [range-v3](https://github.com/ericniebler/range-v3) verwendet und die Einhaltung der abgeschlossenen, jedoch noch nicht ganz veröffentlichten technische Spezifikation zu Bereichen. Weitere Informationen finden Sie unter [Generalizing the Range-Based `for` Loop (Generalisieren einer bereichsbasierten FOR-Schleife)](https://wg21.link/p0184r0).

## <a name="conformance-improvements-in-153"></a><a name="improvements_153"></a> Verbesserungen der Konformität in 15.3

### <a name="constexpr-lambdas"></a>`constexpr`-Lambdas

Lambdaausdrücke können jetzt in konstanten Ausdrücken verwendet werden. Weitere Informationen finden Sie unter [`constexpr`-Lambdaausdrücke in C++](../cpp/lambda-expressions-constexpr.md).

### <a name="if-constexpr-in-function-templates"></a>`if constexpr` in Funktionsvorlagen

Eine Funktionsvorlage kann **`if constexpr`** -Anweisungen enthalten, um das Branchen zur Kompilierzeit zu unterstützen. Weitere Informationen finden Sie unter [`if constexpr`-Anweisungen](../cpp/if-else-statement-cpp.md#if_constexpr).

### <a name="selection-statements-with-initializers"></a>Auswahlanweisungen mit Initialisierern

Eine **`if`** -Anweisung kann einen Initialisierer enthalten, der innerhalb der Anweisung selbst im Blockbereich eine Variable einführt. Weitere Informationen finden Sie unter [`if`-Anweisungen mit Initialisierer](../cpp/if-else-statement-cpp.md#if_with_init).

### <a name="maybe_unused-and-nodiscard-attributes"></a>`[[maybe_unused]]`- und `[[nodiscard]]`-Attribute

Ein neues `[[maybe_unused]]`-Attribut schaltet Warnungen aus, wenn eine Entität nicht verwendet wird. Das `[[nodiscard]]`-Attribut generiert eine Warnung, wenn der Rückgabewert eines Funktionsaufrufs verworfen wird. Weitere Informationen finden Sie unter [Attribute in C++](../cpp/attributes.md).

### <a name="using-attribute-namespaces-without-repetition"></a>Verwenden von Attributnamespaces ohne Wiederholung

Neue Syntax, um nur einen einzigen Namespacebezeichner in einer Attributliste zu erlauben. Weitere Informationen finden Sie unter [Attribute in C++](../cpp/attributes.md).

### <a name="structured-bindings"></a>Strukturierte Bindungen

Es ist jetzt möglich, einen Wert mit individuellen Namen für die verschiedenen Komponenten in einer einzigen Anweisung zu speichern. Dies gilt, wenn der Wert ein Array, `std::tuple` oder `std::pair` ist oder nur öffentliche, nicht statische Datenmember enthält. Weitere Informationen finden Sie unter [Structured Bindings (Strukturierte Bindungen)](https://wg21.link/p0144r0) und [Returning multiple values from a function (Zurückgeben von mehreren Werten aus einer Funktion)](../cpp/functions-cpp.md#multi_val).

### <a name="construction-rules-for-enum-class-values"></a>Erstellungsregeln für `enum class`-Klassenwerte

Es gibt nun eine implizite Konvertierung für Enumerationen mit eigenem Gültigkeitsbereich, die nicht einschränkend ist. Es erfolgt eine Konvertierung vom zugrunde liegenden Typ einer Enumeration mit eigenem Gültigkeitsbereich in die Enumeration selbst. Diese Konvertierung ist verfügbar, wenn in der Definition kein Enumerator eingeführt wird und in der Quelle eine Listeninitialisierungsyntax verwendet wird. Weitere Informationen finden Sie unter [Construction Rules for enum class Values (Erstellungsregeln für enum-Klassenwerte)](https://wg21.link/p0138r2) und [Enumerations (Enumerationen)](../cpp/enumerations-cpp.md#no_enumerators).

### <a name="capturing-this-by-value"></a>Erfassen von `*this` nach Wert

Das **`*this`** -Objekt in einem Lambdaausdruck kann jetzt anhand des Werts erfasst werden. Diese Änderung ermöglicht Szenarios in denen der Lambdaausdruck in parallelen und asynchronen Vorgängen aufgerufen wird, insbesondere in neueren Computerarchitekturen. Weitere Informationen finden Sie unter L[Lambda Capture of \*this by Value as \[=,\*this\]](https://wg21.link/p0018r3) (Lambdaerfassung von „*this“ anhand des Werts als =,this).

### <a name="removing-operator-for-bool"></a>Entfernen von `operator++` für `bool`

`operator++` wird für **`bool`** -Typen nicht mehr unterstützt. Weitere Informationen finden Sie unter [Remove Deprecated operator++(bool)](https://wg21.link/p0002r1) (Veralteten „operator++(bool)“ entfernen).

### <a name="removing-deprecated-register-keyword"></a>Entfernen des veralteten Schlüsselworts `register`

Das Schlüsselwort **`register`** , das als veraltet gekennzeichnet und vom Compiler ignoriert wurde, wurde jetzt aus der Sprache entfernt. Weitere Informationen finden Sie unter [Remove Deprecated Use of the `register`Keyword](https://wg21.link/p0001r1) (Entfernen der Verwendung des veralteten Schlüsselworts „register“).

## <a name="conformance-improvements-in-155"></a><a name="improvements_155"></a> Verbesserungen der Konformität in 15.5

Funktionen, die mit \[14] markiert sind, stehen selbst im **`/std:c++14`** -Modus ohne Bedingungen zur Verfügung.

### <a name="new-compiler-switch-for-extern-constexpr"></a>Neue Compilerschalter für `extern constexpr`

In früheren Versionen von Visual Studio hat der Compiler immer eine interne **`constexpr`** -Variablenbindung ausgegeben, selbst wenn die Variable als **`extern`** markiert wurde. In Visual Studio 2017 Version 15.5 ermöglicht ein neuer Compilerschalter ([`/Zc:externConstexpr`](../build/reference/zc-externconstexpr.md)) das richtige standardkonforme Verhalten. Weitere Informationen finden Sie unter [Externe constexpr-Verknüpfung](#extern_linkage).

### <a name="removing-dynamic-exception-specifications"></a>Entfernen dynamischer Ausnahmespezifikationen

[P0003R5](https://wg21.link/p0003r5) Dynamische Ausnahmespezifikationen sind in C++11 veraltet. Das Feature wird aus C ++ 17 entfernt, aber die (immer noch) veraltete `throw()`-Spezifikation wird strikt als Alias für `noexcept(true)` beibehalten. Weitere Informationen dazu finden Sie unter [Entfernen der dynamischen Ausnahmespezifikation und noexcept](#noexcept_removal).

### `not_fn()`

[P0005R4](https://wg21.link/p0005r4) `not_fn` ersetzt `not1` und `not2`.

### <a name="rewording-enable_shared_from_this"></a>Umformulieren von `enable_shared_from_this`

[P0033R1](https://wg21.link/p0033r1) `enable_shared_from_this` wurde in C++11 hinzugefügt. Der C++17-Standard aktualisiert die Spezifikation, um bestimmte Ausnahmefälle besser zu verarbeiten. \[14]

### <a name="splicing-maps-and-sets"></a>Splice-Zuordnungen und -Sätze

[P0083R3](https://wg21.link/p0083r3) Dieses Feature ermöglicht das Extrahieren von Knoten aus assoziativen Containern (z.B. `map`, `set`, `unordered_map`, `unordered_set`), die dann geändert und wieder in den gleichen Container oder einen anderen Container eingefügt werden können, der den gleichen Knotentyp verwendet. (Ein häufiger Anwendungsfall besteht darin, einen Knoten aus einer `std::map` zu extrahieren, den Schlüssel zu ändern und ihn dann erneut einzufügen.)

### <a name="deprecating-vestigial-library-parts"></a>Veraltete rudimentäre Bibliotheksteile

[P0174R2](https://wg21.link/p0174r2) Einige Features der C++-Standardbibliothek wurden im Laufe der Jahre durch neuere Features ersetzt, oder es hat sich herausgestellt, dass sie nicht sehr nützlich oder sogar problematisch sind. Diese Funktionen werden sind in C++17 offiziell als veraltet eingestuft.

### <a name="removing-allocator-support-in-stdfunction"></a>Entfernen der Zuweisungsunterstützung in `std::function`

[P0302R1](https://wg21.link/p0302r1) Vor C++17 besaß die Klassenvorlage `std::function` mehrere Konstruktoren, die ein Zuweisungsargument angenommen haben. Allerdings war die Verwendung von Zuweisungen in diesem Kontext problematisch, und die Semantik war unklar. Die problematischen Konstruktoren wurden entfernt.

### <a name="fixes-for-not_fn"></a>Korrekturen für `not_fn()`

[P0358R1](https://wg21.link/p0358r1) Neue Formulierungen für `std::not_fn` bieten Unterstützung für die Weitergabe der Wertkategorie bei einem Wrapperaufruf.

### <a name="shared_ptrt-shared_ptrtn"></a>`shared_ptr<T[]>`, `shared_ptr<T[N]>`

[P0414R2](https://wg21.link/p0414r2) Zusammenführen von `shared_ptr`-Änderungen aus Library Fundamentals in C++17. \[14]

### <a name="fixing-shared_ptr-for-arrays"></a>Korrigieren von `shared_ptr` für Arrays

[P0497R0](https://wg21.link/p0497r0) Korrekturen an der shared_ptr-Unterstützung für Arrays. \[14]

### <a name="clarifying-insert_return_type"></a>Erklärung zu `insert_return_type`

[P0508R0](https://wg21.link/p0508r0) Die assoziativen Container mit eindeutigen Schlüsseln und die ungeordneten Container mit eindeutigen Schlüsseln besitzen die Memberfunktion `insert`, die einen geschachtelten `insert_return_type`-Typ zurückgibt. Dieser Rückgabetyp ist nun als Spezialisierung eines Typs definiert, der für den Iterator und NodeType des Containers parametrisiert ist.

### <a name="inline-variables-for-the-standard-library"></a>Inlinevariablen für die Standardbibliothek

[P0607R0](https://wg21.link/p0607r0)

### <a name="annex-d-features-deprecated"></a>Veraltete Features aus Anhang D

Anhang D des C++-Standards enthält alle Features, die veraltet sind. Dazu gehören auch `shared_ptr::unique()`, `<codecvt>` und `namespace std::tr1`. Wenn der Compilerschalter **`/std:c++17`** festgelegt wird, werden fast alle Features der Standardbibliothek in Anhang D als veraltet markiert. Weitere Informationen finden Sie unter [Features der Standardbibliothek in Anhang D sind als veraltet markiert](#annex_d).

Der `std::tr2::sys`-Namespace in `<experimental/filesystem>` gibt bei Verwendung von **`/std:c++14`** jetzt standardmäßig eine Warnung zu veralteten Features aus und wird bei Verwendung von **`/std:c++17`** standardmäßig entfernt.

Verbesserte Konformität in `<iostream>` durch Vermeidung einer nicht standardmäßigen Erweiterung (explizite Spezialisierungen in der Klasse).

Die Standardbibliothek verwendet jetzt intern Variablenvorlagen.

Die Standardbibliothek wurde aufgrund von C++17-Compileränderungen aktualisiert. Dabei wurde u. a. **`noexcept`** im Typsystem hinzugefügt. Außerdem wurden dynamische Ausnahmespezifikationen entfernt.

## <a name="conformance-improvements-in-156"></a><a name="improvements_156"></a> Verbesserungen der Konformität in 15.6

### <a name="c17-library-fundamentals-v1"></a>C++17-Bibliotheksgrundlagen V1

[P0220R1](https://wg21.link/p0220r1) integriert die technische Spezifikation der Bibliotheksgrundlagen für C++17 in die Standardbibliothek. Enthält Updates zu \<experimental/tuple>, \<experimental/optional>, \<experimental/functional>, \<experimental/any>, \<experimental/string_view>, \<experimental/memory>, \<experimental/memory_resource>, und \<experimental/algorithm>.

### <a name="c17-improving-class-template-argument-deduction-for-the-standard-library"></a>C++17: Verbessern der Vorlagenargumentableitung für die Standardvorlagenbibliothek

[P0739R0](https://wg21.link/p0739r0) Verschieben Sie `adopt_lock_t` für `scoped_lock` an den Anfang der Parameterliste, um die konsistente Verwendung von `scoped_lock` zu ermöglichen. Lassen Sie zu, dass der Konstruktor `std::variant` in mehreren Fällen Teil einer Überladungsauflösung ist, um die Kopierzuweisung zu ermöglichen.

## <a name="conformance-improvements-in-157"></a><a name="improvements_157"></a> Verbesserungen der Konformität in 15.7

### <a name="c17-rewording-inheriting-constructors"></a>C++17: Umformulierung der Konstruktorvererbung

[P0136R1](https://wg21.link/p0136r1) gibt an, dass eine **`using`** -Deklaration, die einen Konstruktor benennt, jetzt die zugehörigen Basisklassenkonstruktoren für Initialisierungen der abgeleiteten Klasse sichtbar macht, anstatt die zusätzlichen abgeleiteten Klassenkonstruktoren zu deklarieren. Diese Umformulierung ist eine Änderung gegenüber C++14. In Visual Studio 2017 Version 15.7 und höher kann Code, der im **`/std:c++17`** -Modus in C++14 gültig ist und die Konstruktorvererbung verwendet, ungültig sein oder über eine andere Semantik verfügen.

Im folgenden Beispiel ist das Verhalten von C++14 dargestellt:

```cpp
struct A {
    template<typename T>
    A(T, typename T::type = 0);
    A(int);
};

struct B : A {
    using A::A;
    B(int n) = delete; // Error C2280
};

B b(42L); // Calls B<long>(long), which calls A(int)
          //  due to substitution failure in A<long>(long).
```

Das folgende Beispiel zeigt das Verhalten bei Verwendung von **`/std:c++17`** in Visual Studio 15.7:

```cpp
struct A {
    template<typename T>
    A(T, typename T::type = 0);
    A(int);
};

struct B : A {
    using A::A;
    B(int n)
    {
        //do something
    }
};

B b(42L); // now calls B(int)
```

Weitere Informationen finden Sie unter [Konstruktoren](../cpp/constructors-cpp.md#inheriting_constructors).

### <a name="c17-extended-aggregate-initialization"></a>C++17: Erweiterte Aggregatinitialisierung

[P0017R1](https://wg21.link/p0017r1)

Wenn der Konstruktor einer Basisklasse zwar nicht öffentlich, aber für eine abgeleitete Klasse verfügbar ist, können Sie im **`/std:c++17`** -Modus in Visual Studio Version 2017 Version 15.7 nicht länger leere Klammern zum Initialisieren eines Objekts des abgeleiteten Typs verwenden.
Im folgenden Beispiel ist das konforme Verhalten von C++14 dargestellt:

```cpp
struct Derived;
struct Base {
    friend struct Derived;
private:
    Base() {}
};

struct Derived : Base {};
Derived d1; // OK. No aggregate init involved.
Derived d2 {}; // OK in C++14: Calls Derived::Derived()
               // which can call Base ctor.
```

In C++17 gilt `Derived` nun als Aggregattyp. Das bedeutet, dass die Initialisierung von `Base` über den privaten Standardkonstruktor direkt als Teil der erweiterten Aggregatinitialisierungsregel erfolgt. Zuvor wurde der private Konstruktor `Base` über den `Derived`-Konstruktor aufgrund der Friend-Deklaration erfolgreich aufgerufen.
Das folgende Beispiel zeigt das C++17-Verhalten im **`/std:c++17`** -Modus in Visual Studio Version 15.7:

```cpp
struct Derived;
struct Base {
    friend struct Derived;
private:
    Base() {}
};
struct Derived : Base {
    Derived() {} // add user-defined constructor
                 // to call with {} initialization
};
Derived d1; // OK. No aggregate init involved.
Derived d2 {}; // error C2248: 'Base::Base': cannot access
               // private member declared in class 'Base'
```

### <a name="c17-declaring-non-type-template-parameters-with-auto"></a>C++17: Deklarieren von Nichttyp-Vorlagenparameter mit „auto“

[P0127R2](https://wg21.link/p0127r2)

Im **`/std:c++17`** -Modus kann der Compiler jetzt den Typ eines mit **`auto`** deklarierten Vorlagenarguments ohne Typ ableiten:

```cpp
template <auto x> constexpr auto constant = x;

auto v1 = constant<5>;      // v1 == 5, decltype(v1) is int
auto v2 = constant<true>;   // v2 == true, decltype(v2) is bool
auto v3 = constant<'a'>;    // v3 == 'a', decltype(v3) is char
```

Eine Auswirkung dieses neuen Features ist, dass gültiger C++14-Code womöglich ungültig sein oder über eine andere Semantik verfügen kann. Beispielsweise sind einige Überladungen, die zuvor ungültig waren, nun gültig. Das folgende Beispiel zeigt den C++14-Code, der kompiliert wird, weil der Aufruf an `example(p)` an `example(void*);` gebunden ist. In Visual Studio 2017 Version 15.7 stellt die `example`-Funktionsvorlage im **`/std:c++17`** -Modus die beste Übereinstimmung dar.

```cpp
template <int N> struct A;
template <typename T, T N> int example(A<N>*) = delete;

void example(void *);

void sample(A<0> *p)
{
    example(p); // OK in C++14
}
```

Das folgende Beispiel zeigt den C++17-Code im **`/std:c++17`** -Modus in Visual Studio 15.7:

```cpp
template <int N> struct A;
template <typename T, T N> int example(A<N>*);

void example(void *);

void sample(A<0> *p)
{
    example(p); // C2280: 'int example<int,0>(A<0>*)': attempting to reference a deleted function
}
```

### <a name="c17-elementary-string-conversions-partial"></a>C++17: Elementare Zeichenfolgenkonvertierungen (partiell)

[P0067R5](https://wg21.link/p0067r5) Gebietsschemaunabhängige Funktionen auf niedriger Ebene für Wechsel zwischen ganzen Zahlen und Zeichenfolgen und zwischen Gleitkommazahlen und Zeichenfolgen.

### <a name="c20-avoiding-unnecessary-decay-partial"></a>C++20: Vermeiden der unnötigen decay-Eigenschaft (partiell)

[P0777R1](https://wg21.link/p0777r1) Fügt Differenzierung zwischen dem Konzept von „decay“ und der einfachen Entfernung von Konstanten- oder Verweisqualifizierern hinzu.  Die neue Typeigenschaft `remove_reference_t` ersetzt in einigen Kontexten `decay_t`. Die Unterstützung für `remove_cvref_t` ist in Visual Studio 2019 implementiert.

### <a name="c17-parallel-algorithms"></a>C++17: Parallele Algorithmen

[P0024R2](https://wg21.link/p0024r2) Die technische Spezifikation zur Parallelität ist mit nur wenigen Änderungen im Standard eingeschlossen.

### <a name="c17-hypotx-y-z"></a>C++17: `hypot(x, y, z)`

[P0030R1](https://wg21.link/p0030r1) Für die Typen **`float`** , **`double`** und **`long double`** werden drei neue Überladungen zu `std::hypot` hinzugefügt. Jeder dieser Typen verfügt über drei Eingabeparameter.

### <a name="c17-filesystem"></a>C++17: \<filesystem>

[P0218R1](https://wg21.link/p0218r1) Übernimmt die Dateisystem-TS in die Standardversion, mit ein paar Veränderungen in der Formulierung.

### <a name="c17-mathematical-special-functions"></a>C++17: Mathematische spezielle Funktionen

[P0226R1](https://wg21.link/p0220r1) Übernimmt die vorherige technische Spezifikation für die mathematischen speziellen Funktionen in den Standardheader \<cmath>.

### <a name="c17-deduction-guides-for-the-standard-library"></a>C++17: Herleitungsregelwerk für die Standardbibliothek

[P0433R2](https://wg21.link/p0433r2) Updates auf STL, um von der Nutzung von C++17 von [P0091R3](https://wg21.link/p0091r3) zu profitieren, was Unterstützung für die Klassenvorlagenargumentableitung hinzufügt.

### <a name="c17-repairing-elementary-string-conversions"></a>C++17: Elementare Zeichenfolgenkonvertierungen

[P0682R1](https://wg21.link/p0682r1) Verschieben Sie die elementaren Funktionen für die Zeichenfolgenkonvertierung von P0067R5 in einen neuen Header, \<charconv>, und führen Sie andere Verbesserungen durch, einschließlich der Fehlerbehandlung zur Verwendung von `std::errc` anstelle von `std::error_code`.

### <a name="c17-constexpr-for-char_traits-partial"></a>C ++ 17: `constexpr` für `char_traits` (partiell)

[P0426R1](https://wg21.link/p0426r1) Änderungen an den `std::traits_type`-Memberfunktionen `length`, `compare` und `find`, damit `std::string_view` in konstanten Ausdrücken verfügbar wird. (In Visual Studio 2017 Version 15.6 wird dies nur für Clang/LLVM unterstützt. In Version 15.7 Preview 2 ist die Unterstützung für CIXX ebenso fast vollständig.)

## <a name="conformance-improvements-in-159"></a><a name="improvements_159"></a> Verbesserungen der Konformität in 15.9

### <a name="left-to-right-evaluation-order-for-operators-----and-"></a>Auswertungsreihenfolge von links nach rechts für die Operatoren `->*`, `[]`, `>>` und `<<`

Ab C++17 müssen die Operanden der Operatoren `->*`, `[]`, `>>` und `<<` in der Reihenfolge von links nach rechts ausgewertet werden. Es gibt zwei Fälle, in denen der Compiler diese Reihenfolge nicht sicherstellen kann:

- wenn es sich bei einem der Operandenausdrücke um ein nach Wert übergebenes Objekt handelt oder er ein nach Wert übergebenes Objekt enthält oder

- wenn er mithilfe von **`/clr`** kompiliert wird und einer der Operanden ein Feld eines Objekts oder ein Arrayelement ist.

Der Compiler gibt die Warnung [C4866](../error-messages/compiler-warnings/c4866.md) aus, wenn er die Auswertung von links nach rechts nicht sicherstellen kann. Diese Warnung wird vom Compiler nur generiert, wenn **`/std:c++17`** oder höher angegeben ist, da die Anforderung der Auswertungsreihenfolge von links nach rechts für diese Operatoren in C++17 eingeführt wurde.

Um diese Warnung zu vermeiden, sollten Sie zunächst überprüfen, ob die Auswertung von links nach rechts für die Operanden erforderlich ist. Dies kann beispielsweise erforderlich sein, wenn durch die Auswertung der Operanden reihenfolgenabhängige Nebenwirkungen auftreten. In vielen Fällen hat die Reihenfolge, in der Operanden ausgewertet werden, keinen beobachtbaren Effekt. Wenn die Auswertungsreihenfolge von links nach rechts sein muss, überlegen Sie, ob Sie die Operanden stattdessen als const-Verweis übergeben können. Diese Änderung entfernt die Warnung im folgenden Codebeispiel:

```cpp
// C4866.cpp
// compile with: /w14866 /std:c++17

class HasCopyConstructor
{
public:
    int x;

    HasCopyConstructor(int x) : x(x) {}
    HasCopyConstructor(const HasCopyConstructor& h) : x(h.x) { }
};

int operator>>(HasCopyConstructor a, HasCopyConstructor b) { return a.x >> b.x; }

// This version of operator>> does not trigger the warning:
// int operator>>(const HasCopyConstructor& a, const HasCopyConstructor& b) { return a.x >> b.x; }

int main()
{
    HasCopyConstructor a{ 1 };
    HasCopyConstructor b{ 2 };

    a>>b;        // C4866 for call to operator>>
};
```

## <a name="bug-fixes-in-visual-studio-2017-rtw-version-150"></a><a name="update_150"></a> Fehlerbehebungen in Visual Studio 2017 RTW Version 15.0

### <a name="copy-list-initialization"></a>copy-list-Initialisierung

In Visual Studio 2017 werden ordnungsgemäß Compilerfehler im Zusammenhang mit der Objekterstellung bei Verwendung von Initialisiererlisten erzeugt. Diese Fehler wurden in Visual Studio 2015 nicht erfasst und konnten zu Abstürzen oder einem nicht definierten Laufzeitverhalten führen. Laut N4594 13.3.1.7p1 muss der Compiler in der copy-list-Initialisierung einen expliziten Konstruktor für die Überladungsauflösung berücksichtigen, aber einen Fehler auslösen, wenn diese Überladung tatsächlich gewählt wird. Er muss jedoch einen Fehler auslösen, wenn diese bestimmte Überladung ausgewählt wird.

Die folgenden beiden Beispiele kompilieren in Visual Studio 2015, aber nicht in Visual Studio 2017.

```cpp
struct A
{
    explicit A(int) {}
    A(double) {}
};

int main()
{
    A a1 = { 1 }; // error C3445: copy-list-initialization of 'A' cannot use an explicit constructor
    const A& a2 = { 1 }; // error C2440: 'initializing': cannot convert from 'int' to 'const A &'

}
```

Verwenden Sie direkte Initialisierung, um den Fehler zu korrigieren:

```cpp
A a1{ 1 };
const A& a2{ 1 };
```

In Visual Studio 2015 behandelt der Compiler fälschlicherweise eine copy-list-Initialisierung auf die gleiche Weise wie eine normale Kopierinitialisierung. Er konvertiert nur die Konstruktoren für die Überladungsauflösung. Im folgenden Beispiel wählt Visual Studio 2015 `MyInt(23)`. Visual Studio 2017 löst den Fehler ordnungsgemäß aus.

```cpp
// From http://www.open-std.org/jtc1/sc22/wg21/docs/cwg_closed.html#1228
struct MyStore {
    explicit MyStore(int initialCapacity);
};

struct MyInt {
    MyInt(int i);
};

struct Printer {
    void operator()(MyStore const& s);
    void operator()(MyInt const& i);
};

void f() {
    Printer p;
    p({ 23 }); // C3066: there are multiple ways that an object of this type can be called with these arguments
}
```

Dieses Beispiel ähnelt dem vorherigen Beispiel, löst jedoch einen anderen Fehler aus. Es ist in Visual Studio 2015 erfolgreich, und in Visual Studio 2017 mit C2668 schlägt es fehl.

```cpp
struct A {
    explicit A(int) {}
};

struct B {
    B(int) {}
};

void f(const A&) {}
void f(const B&) {}

int main()
{
    f({ 1 }); // error C2668: 'f': ambiguous call to overloaded function
}
```

### <a name="deprecated-typedefs"></a>Veraltete TypeDefs

Visual Studio 2017 gibt jetzt die richtige Warnung für veraltete TypeDefs aus, die in einer Klasse oder Struktur deklariert sind. In Visual Studio 2015 wird das folgende Beispiel ohne Warnungen kompiliert. In Visual Studio 2017 erzeugt es C4996.

```cpp
struct A
{
    // also for __declspec(deprecated)
    [[deprecated]] typedef int inttype;
};

int main()
{
    A::inttype a = 0; // C4996 'A::inttype': was declared deprecated
}
```

### `constexpr`

Visual Studio 2017 löst ordnungsgemäß einen Fehler aus, wenn der linke Operand eines bedingten Auswertungsvorgangs in einem constexpr-Kontext ungültig ist. Der folgende Code wird in Visual Studio 2015 kompiliert, in Visual Studio 2017 jedoch nicht. Stattdessen wird „C3615 `constexpr function 'f' cannot result in a constant expression`“ ausgelöst:

```cpp
template<int N>
struct array
{
    int size() const { return N; }
};

constexpr bool f(const array<1> &arr)
{
    return arr.size() == 10 || arr.size() == 11; // C3615
}
```

Deklarieren Sie die Funktion `array::size()` als **`constexpr`** , oder entfernen Sie den **`constexpr`** -Qualifizierer aus `f`, um den Fehler zu beheben.

### <a name="class-types-passed-to-variadic-functions"></a>Klassentypen, die an variadic-Funktionen übergeben werden

In Visual Studio 2017 müssen Klassen oder Strukturen, die an eine variadic-Funktion übergeben werden (z. B `printf`), einfach kopierbar sein. Wenn solche Objekte übergeben werden, macht der Compiler einfach eine bitweise Kopie und ruft keinen Konstruktor oder Destruktor auf.

```cpp
#include <atomic>
#include <memory>
#include <stdio.h>

int main()
{
    std::atomic<int> i(0);
    printf("%i\n", i); // error C4839: non-standard use of class 'std::atomic<int>'
                        // as an argument to a variadic function.
                        // note: the constructor and destructor will not be called;
                        // a bitwise copy of the class will be passed as the argument
                        // error C2280: 'std::atomic<int>::atomic(const std::atomic<int> &)':
                        // attempting to reference a deleted function

    struct S {
        S(int i) : i(i) {}
        S(const S& other) : i(other.i) {}
        operator int() { return i; }
    private:
        int i;
    } s(0);
    printf("%i\n", s); // warning C4840 : non-portable use of class 'main::S'
                      // as an argument to a variadic function
}
```

Sie können eine Memberfunktion aufrufen, die einen einfachen kopierbaren Typ zurückgibt, um den Fehler zu beheben,

```cpp
    std::atomic<int> i(0);
    printf("%i\n", i.load());
```

oder Sie verwenden eine statische Umwandlung, um das Objekt zu konvertieren, bevor es übergeben wird:

```cpp
    struct S {/* as before */} s(0);
    printf("%i\n", static_cast<int>(s))
```

Für mit `CString` erstellte und verwaltete Zeichenfolgen sollte der bereitgestellte `operator LPCTSTR()` verwendet werden, um ein `CString`-Objekt in einen C-Zeiger umzuwandeln, der von der Formatzeichenfolge erwartet wird.

```cpp
CString str1;
CString str2 = _T("hello!");
str1.Format(_T("%s"), static_cast<LPCTSTR>(str2));
```

### <a name="cv-qualifiers-in-class-construction"></a>CV-Qualifizierer in der Klassenkonstruktion

In Visual Studio 2015 ignoriert der Compiler beim Generieren eines Klassenobjekts über einen Konstruktoraufruf manchmal fälschlicherweise die CV-Qualifizierer. Dieses Problem kann potenziell zu einem Absturz oder zu unerwartetem Laufzeitverhalten führen. Das folgende Beispiel kompiliert in Visual Studio 2015, aber löst einen Compilerfehler in Visual Studio 2017 aus:

```cpp
struct S
{
    S(int);
    operator int();
};

int i = (const S)0; // error C2440
```

Deklarieren Sie `operator int()` als **`const`** , um den Fehler zu beheben.

### <a name="access-checking-on-qualified-names-in-templates"></a>Zugriff auf qualifizierte Namen in Vorlagen überprüfen

In früheren Versionen des Compilers wurde der Zugriff auf qualifizierte Namen in bestimmten Kontexten von Vorlagen nicht überprüft. Dieses Problem kann das erwartete SFINAE-Verhalten behindern, bei dem die Ersetzung aufgrund der Nichterreichbarkeit des Namens erwartungsgemäß fehlschlägt. Dies konnte potenziell einen Absturz oder unerwartetes Verhalten zur Laufzeit auslösen, da der Compiler die falsche Überladung des Operators aufgerufen hat. In Visual Studio 2017 wird ein Compilerfehler ausgelöst. Welcher Fehler angezeigt wird, kann variieren, üblicherweise ist es jedoch „C2672 `no matching overloaded function found`“. Der folgende Code kompiliert in Visual Studio 2015, aber löst in Visual Studio 2017 einen Fehler aus:

```cpp
#include <type_traits>

template <class T> class S {
    typedef typename T type;
};

template <class T, std::enable_if<std::is_integral<typename S<T>::type>::value, T> * = 0>
bool f(T x);

int main()
{
    f(10); // C2672: No matching overloaded function found.
}
```

### <a name="missing-template-argument-lists"></a>Fehlende Vorlagenargumentlisten

Bis Visual Studio 2015 wurde vom Compiler keine Diagnose für fehlende Vorlagenargumentlisten durchgeführt. Es wurde nicht bemerkt, wenn die fehlende Vorlage in einer Vorlagenparameterliste enthalten war, z. B. wenn ein Teil eines Standardvorlagenarguments oder ein Nichttyp-Vorlagenparameter fehlte. Dieses Problem kann zu unvorhersehbarem Verhalten führen, einschließlich des Absturzes des Compilers oder unerwartetem Laufzeitverhalten. Der folgende Code kompiliert in Visual Studio 2015, aber erzeugt in Visual Studio 2017 einen Fehler.

```cpp
template <class T> class ListNode;
template <class T> using ListNodeMember = ListNode<T> T::*;
template <class T, ListNodeMember M> class ListHead; // C2955: 'ListNodeMember': use of alias
                                                     // template requires template argument list

// correct:  template <class T, ListNodeMember<T> M> class ListHead;
```

### <a name="expression-sfinae"></a>SFINAE für Ausdrücke

Um SFINAE für Ausdrücke zu unterstützen, analysiert der Compiler jetzt **`decltype`** -Argumente, wenn die Vorlagen deklariert statt instanziiert werden. Wenn also eine nicht abhängige Spezialisierung im decltype-Argument gefunden wird, wird sie nicht auf die Instanziierungerungszeit zurückgestellt. Es wird sofort verarbeitet, und alle daraus resultierenden Fehler werden sofort diagnostiziert.

Das folgende Beispiel zeigt einen solchen Compilerfehler, der zum Zeitpunkt der Deklaration ausgelöst wird:

```cpp
#include <utility>
template <class T, class ReturnT, class... ArgsT>
class IsCallable
{
public:
    struct BadType {};

    template <class U>
    static decltype(std::declval<T>()(std::declval<ArgsT>()...)) Test(int); //C2064. Should be declval<U>

    template <class U>
    static BadType Test(...);

    static constexpr bool value = std::is_convertible<decltype(Test<T>(0)), ReturnT>::value;
};

constexpr bool test1 = IsCallable<int(), int>::value;
static_assert(test1, "PASS1");
constexpr bool test2 = !IsCallable<int*, int>::value;
static_assert(test2, "PASS2");
```

### <a name="classes-declared-in-anonymous-namespaces"></a>In anonymen Namespaces deklarierte Klassen

Entsprechend dem C++-Standard verfügt eine Klasse, die innerhalb eines anonymen Namespace deklariert wird, über interne Verknüpfungen und kann daher nicht exportiert werden. In Visual Studio 2015 und früheren Versionen wurde diese Regel nicht durchgesetzt. In Visual Studio 2017 wird die Regel teilweise durchgesetzt. In Visual Studio 2017 löst das folgende Beispiel den Fehler „C2201: `const anonymous namespace::S1::vftable: must have external linkage in order to be exported/imported.`“ aus

```cpp
struct __declspec(dllexport) S1 { virtual void f() {} }; //C2201
```

### <a name="default-initializers-for-value-class-members-ccli"></a>Standardinitialisierer für Wertklassenmember (C++/CLI)

In Visual Studio 2015 und früher, ließ der Compiler einen Standardmember-Initialisierer für einen Member einer Wertklasse zu, ignorierte diesen aber. Standardinitialisierung einer Wertklasse initialisiert die Elemente immer auf null. Ein Standardkonstruktor ist nicht zulässig. In Visual Studio 2017 lösen Standardmember-Initialisierer einen Compilerfehler aus, wie im folgenden Beispiel gezeigt:

```cpp
value struct V
{
    int i = 0; // error C3446: 'V::i': a default member initializer
               // isn't allowed for a member of a value class
};
```

### <a name="default-indexers-ccli"></a>Standardindexer (C++/CLI)

In Visual Studio 2015 und früher hat der Compiler in einigen Fällen fälschlicherweise eine Standardeigenschaft als einen Standardindexer kategorisiert. Das Problem konnte umgangen werden, indem der Bezeichner **`default`** für den Zugriff auf die Eigenschaft verwendet wurde. Diese Problemumgehung wurde selbst wiederum problematisch, nachdem **`default`** als Schlüsselwort in C++11 eingeführt wurde. In Visual Studio 2017 wurden die Fehler, für die eine Problemumgehung erforderlich war, behoben. Der Compiler löst jetzt einen Fehler aus, wenn für den Zugriff auf die Standardeigenschaft für eine Klasse **`default`** verwendet wird.

```cpp
//class1.cs

using System.Reflection;
using System.Runtime.InteropServices;

namespace ClassLibrary1
{
    [DefaultMember("Value")]
    public class Class1
    {
        public int Value
        {
            // using attribute on the return type triggers the compiler bug
            [return: MarshalAs(UnmanagedType.I4)]
            get;
        }
    }
    [DefaultMember("Value")]
    public class Class2
    {
        public int Value
        {
            get;
        }
    }
}

// code.cpp
#using "class1.dll"

void f(ClassLibrary1::Class1 ^r1, ClassLibrary1::Class2 ^r2)
{
       r1->Value; // error
       r1->default;
       r2->Value;
       r2->default; // error
}
```

In Visual Studio 2017 können Sie anhand ihres Namens auf beide Eigenschaften zugreifen:

```cpp
#using "class1.dll"

void f(ClassLibrary1::Class1 ^r1, ClassLibrary1::Class2 ^r2)
{
       r1->Value;
       r2->Value;
}
```

## <a name="bug-fixes-in-153"></a><a name="update_153"></a> Fehlerbehebungen in 15.3

### <a name="calls-to-deleted-member-templates"></a>Aufrufe gelöschter Membervorlagen

In früheren Versionen von Visual Studio gab der Compiler mitunter keine Fehlermeldung bei falsch formatierten Aufrufen einer gelöschten Membervorlage zurück. Durch diese Aufrufe wurden zur Laufzeit möglicherweise Abstürze verursacht. Mit dem folgenden Code wird jetzt „C2280, `'int S<int>::f<int>(void)': attempting to reference a deleted function`“ ausgelöst:

```cpp
template<typename T>
struct S {
   template<typename U> static int f() = delete;
};

void g()
{
   decltype(S<int>::f<int>()) i; // this should fail
}
```

Um den Fehler zu beheben, deklarieren Sie `i` als **`int`** .

### <a name="pre-condition-checks-for-type-traits"></a>Voraussetzungsprüfungen für Typmerkmale

Visual Studio 2017 Version 15.3 verbessert Voraussetzungsprüfungen für Typmerkmale so, dass der Standard strenger befolgt wird. Eine solche Prüfung erfolgt für „assignable“. Mit dem folgenden Code wird C2139 in Visual Studio 2017 Version 15.3 generiert:

```cpp
struct S;
enum E;

static_assert(!__is_assignable(S, S), "fail"); // C2139 in 15.3
static_assert(__is_convertible_to(E, E), "fail"); // C2139 in 15.3
```

### <a name="new-compiler-warning-and-runtime-checks-on-native-to-managed-marshaling"></a>Neue Compilerwarnung und CLR-Prüfungen für Marshalling von nativ zu verwaltet

Aufrufe nativer Funktionen aus verwalteten Funktionen erfordern Marshalling. Die CLR führt das Marshalling aus, versteht aber nicht die C++-Semantik. Wenn Sie ein natives Objekt nach Wert übergeben, ruft die CLR entweder den Kopierkonstruktor des Objekts auf oder verwendet `BitBlt`, was zu einem nicht definiertem Verhalten zur Laufzeit führt.

Jetzt gibt der Compiler eine Warnung aus, wenn er diesen Fehler zur Kompilierzeit findet. Ein natives Objekt mit gelöschtem Kopierkonstruktor wird zwischen einer nativen und einer verwalteten Grenze nach Wert übergeben. In den Fällen, in denen dem Compiler zur Kompilierzeit keine Informationen vorliegen, fügt er eine Laufzeitprüfung hinzu, sodass das Programm sofort `std::terminate` aufruft, sobald ein falsch formatiertes Marshalling erfolgt. Mit dem folgenden Code wird in Version 15.3 von Visual Studio 2017 die Warnung „C4606 `'A': passing argument by value across native and managed boundary requires valid copy constructor. Otherwise, the runtime behavior is undefined.`“ generiert

```cpp
class A
{
public:
   A() : p_(new int) {}
   ~A() { delete p_; }

   A(A const &) = delete;
   A(A &&rhs) {
   p_ = rhs.p_;
}

private:
   int *p_;
};

#pragma unmanaged

void f(A a)
{
}

#pragma managed

int main()
{
    f(A()); // This call from managed to native requires marshaling. The CLR doesn't understand C++ and uses BitBlt, which results in a double-free later.
}
```

Um den Fehler zu beheben, entfernen Sie die Direktive `#pragma managed`, um den Aufrufer als nativ zu markieren und Marshalling zu vermeiden.

### <a name="experimental-api-warning-for-winrt"></a>Warnung zu experimenteller API für WinRT

WinRT-APIs, die zu Experimentier- und Feedbackzwecken veröffentlicht werden, werden mit `Windows.Foundation.Metadata.ExperimentalAttribute` versehen. In Visual Studio 2017 Version 15.3 generiert der Compiler die Warnung C4698 für dieses Attribut. Einige APIs in früheren Versionen des Windows SDK wurden bereits mit dem Attribut markiert, sodass Aufrufe dieser APIs jetzt diese Compilerwarnung auslösen. In neueren Windows SDKs wurde das Attribut in allen ausgelieferten Typen entfernt. Wenn Sie ein älteres SDK verwenden, müssen Sie diese Warnungen für alle Aufrufe an ausgelieferte Typen unterdrücken.

Mit dem folgenden Code wird die Warnung „C4698: `'Windows::Storage::IApplicationDataStatics2::GetForUserAsync' is for evaluation purposes only and is subject to change or removal in future updates`“ generiert:

```cpp
Windows::Storage::IApplicationDataStatics2::GetForUserAsync(); //C4698
```

Fügen Sie #pragma hinzu, um die Warnung zu deaktivieren:

```cpp
#pragma warning(push)
#pragma warning(disable:4698)

Windows::Storage::IApplicationDataStatics2::GetForUserAsync();

#pragma warning(pop)
```

### <a name="out-of-line-definition-of-a-template-member-function"></a>Out-of-Line-Definition einer Vorlagenmemberfunktion

Visual Studio 2017 Version 15.3 generiert einen Fehler für Out-of-Line-Definitionen einer Vorlagenmemberfunktion, die in der Klasse nicht deklariert wurde. Mit dem folgenden Code wird jetzt der Fehler „C2039: `'f': is not a member of 'S'`“ generiert:

```cpp
struct S {};

template <typename T>
void S::f(T t) {} //C2039: 'f': is not a member of 'S'
```

Um den Fehler zu beheben, fügen Sie der Klasse eine Deklaration hinzu:

```cpp
struct S {
    template <typename T>
    void f(T t);
};
template <typename T>
void S::f(T t) {}
```

### <a name="attempting-to-take-the-address-of-this-pointer"></a>Es wird versucht, die Adresse eines `this`-Zeigers zu verwenden

In C++ ist **`this`** ein prvalue des Typzeigers auf X. Sie können nicht die Adresse von **`this`** verwenden oder sie an einen lvalue-Verweis binden. In früheren Versionen von Visual Studio konnte es Ihnen der Compiler ermöglichen, diese Einschränkung mithilfe einer Umwandlung zu umgehen. In Visual Studio 2017 Version 15.3 generiert der Compiler Fehler C2664.

### <a name="conversion-to-an-inaccessible-base-class"></a>Konvertierung in eine Basisklasse, auf die nicht zugegriffen werden kann

Visual Studio 2017 Version 15.3 generiert einen Fehler, wenn Sie versuchen, einen Typ in eine Basisklasse zu konvertieren, auf die nicht zugegriffen werden kann. Der Compiler löst jetzt den Fehler „C2243: `'type cast': conversion from 'D *' to 'B *' exists, but is inaccessible`“ aus. Der folgende Code ist falsch formatiert und kann möglicherweise einen Absturz während der Laufzeit verursachen. Der Compiler generiert nun C2243, wenn er Code wie diesen erkennt:

```cpp
#include <memory>

class B { };
class D : B { }; // C2243. should be public B { };

void f()
{
   std::unique_ptr<B>(new D());
}
```

### <a name="default-arguments-arent-allowed-on-out-of-line-definitions-of-member-functions"></a>Standardargumente sind in Out-of-Line-Definitionen von Memberfunktionen nicht zulässig

Standardargumente sind in Out-of-Line-Definitionen von Memberfunktionen in Vorlagenklassen nicht zulässig. Der Compiler gibt bei Verwendung von **`/permissive`** eine Warnung und unter [`/permissive-`](../build/reference/permissive-standards-conformance.md) einen schwerwiegenden Fehler aus.

In früheren Versionen von Visual Studio konnte der folgende falsch formatierte Code einen Absturz zur Laufzeit verursachen. In Visual Studio 2017 Version 15.3 wird die Warnung „C5034: `'A\<T>::f': an out-of-line definition of a member of a class template cannot have default arguments`“ generiert:

```cpp
template <typename T>
struct A {
    T f(T t, bool b = false);
};

template <typename T>
T A<T>::f(T t, bool b = false) // C5034
{
    // ...
}
```

Entfernen Sie das Standardargument `= false`, um den Fehler zu beheben.

### <a name="use-of-offsetof-with-compound-member-designator"></a>Verwenden von `offsetof` mit zusammengesetztem Memberkennzeichner

In Visual Studio 2017 Version 15.3 führt das Verwenden von `offsetof(T, m)`, wobei *m* ein zusammengesetzter Memberkennzeichner ist, zu einer Warnung, wenn die Kompilierung mit der Option **`/Wall`** erfolgt. Der folgende Code ist falsch formatiert und kann möglicherweise zur Laufzeit einen Absturz verursachen. In Version 15.3 von Visual Studio 2017 wird die Warnung „C4841: `non-standard extension used: compound member designator in offsetof`“ generiert:

```cpp
struct A {
   int arr[10];
};

// warning C4841: non-standard extension used: compound member designator in offsetof
constexpr auto off = offsetof(A, arr[2]);
```

Um den Code zu korrigieren, deaktivieren Sie die Warnung mit einem Pragma, oder ändern Sie den Code so, dass `offsetof` nicht verwendet wird:

```cpp
#pragma warning(push)
#pragma warning(disable: 4841)
constexpr auto off = offsetof(A, arr[2]);
#pragma warning(pop)
```

### <a name="using-offsetof-with-static-data-member-or-member-function"></a>Verwenden von `offsetof` mit statischem Datenmember oder mit Memberfunktion

In Visual Studio 2017 Version 15.3 führt das Verwenden von `offsetof(T, m)` zu einem Fehler, wenn *m* ein statischer Datenmember oder eine Memberfunktion ist. Mit dem folgenden Code werden die Fehler „C4597: `undefined behavior: offsetof applied to member function 'example'`“ und „C4597: `undefined behavior: offsetof applied to static data member 'sample'`“ generiert:

```cpp
#include <cstddef>

struct A {
   int ten() { return 10; }
   static constexpr int two = 2;
};

constexpr auto off = offsetof(A, ten);
constexpr auto off2 = offsetof(A, two);
```

Dieser Code ist falsch formatiert und kann möglicherweise zur Laufzeit einen Absturz verursachen. Um den Fehler zu beheben, ändern Sie den Code so, dass das nicht definierte Verhalten nicht mehr aufgerufen wird. Dies ist nicht portierbarer Code, der vom C++-Standard nicht zugelassen ist.

### <a name="new-warning-on-__declspec-attributes"></a><a name="declspec"></a> Neue Warnung zu `__declspec`-Attributen

In Visual Studio 2017 Version 15.3 ignoriert der Compiler Attribute nicht mehr, wenn `__declspec(...)` vor der externen Verknüpfungsspezifikation `extern "C"` angewendet wird. Zuvor hat der Compiler das Attribut ignoriert, was zu Problemen zur Laufzeit führen konnte. Bei Festlegung der Optionen **`/Wall`** und **`/WX`** wird mit dem folgenden Code die Warnung „C4768: `__declspec attributes before linkage specification are ignored`“ generiert:

```cpp
__declspec(noinline) extern "C" HRESULT __stdcall //C4768
```

Um die Warnung zu korrigieren, fügen Sie zuerst `extern "C"` hinzu:

```cpp
extern "C" __declspec(noinline) HRESULT __stdcall
```

Diese Warnung ist in Version 15.3 standardmäßig deaktiviert (standardmäßig aktiviert in Version 15.5) und wirkt sich nur auf den mit **`/Wall`** **`/WX`** kompilierten Code aus.

### <a name="decltype-and-calls-to-deleted-destructors"></a>`decltype` und Aufrufe gelöschter Destruktoren

In früheren Versionen von Visual Studio erkannte der Compiler nicht, wenn im Kontext des Ausdrucks, der **`decltype`** zugeordnet war, ein gelöschter Destruktor aufgerufen wurde. Mit dem folgenden Code wird in Version 15.3 von Visual Studio 2017 der Fehler „C2280: `'A<T>::~A(void)': attempting to reference a deleted function`“ generiert:

```cpp
template<typename T>
struct A
{
   ~A() = delete;
};

template<typename T>
auto f() -> A<T>;

template<typename T>
auto g(T) -> decltype((f<T>()));

void h()
{
   g(42);
}
```

### <a name="uninitialized-const-variables"></a>Nicht initialisierte „const“-Variablen

Das Visual Studio 2017 RTW-Release wies eine Regression auf, bei der der C++-Compiler keine Diagnose für eine nicht initialisierte **`const`** -Variable ausgab. Diese Regression wurde in Visual Studio 2017 Version 15.3 behoben. Mit dem folgenden Code wird die Warnung „C4132: `'Value': const object should be initialized`“ generiert:

```cpp
const int Value; //C4132
```

Um den Fehler zu beheben, weisen Sie `Value` einen Wert zu.

### <a name="empty-declarations"></a>Leere Deklarationen

Visual Studio 2017 Version 15.3 warnt bei leeren Deklarationen jetzt für alle Typen und nicht nur für integrierte Typen. Der folgende Code führt jetzt zur Warnung C4091, Stufe 2 für alle vier Deklarationen:

```cpp
struct A {};
template <typename> struct B {};
enum C { c1, c2, c3 };

int;    // warning C4091 : '' : ignored on left of 'int' when no variable is declared
A;      // warning C4091 : '' : ignored on left of 'main::A' when no variable is declared
B<int>; // warning C4091 : '' : ignored on left of 'B<int>' when no variable is declared
C;      // warning C4091 : '' : ignored on left of 'C' when no variable is declared
```

Um die Warnungen zu entfernen, können Sie die leeren Deklarationen auskommentieren oder entfernen. In Fällen, in denen das nicht benannte Objekt einen Nebeneffekt haben soll (z. B. RAII), sollte es mit einem Namen versehen werden.

Die Warnung wird bei Verwendung von **`/Wv:18`** ausgeschlossen und ist auf der Warnstufe W2 standardmäßig aktiviert.

### <a name="stdis_convertible-for-array-types"></a>`std::is_convertible` für Arraytypen

Frühere Versionen des Compilers haben zu falschen Ergebnissen für [std::is_convertible](../standard-library/is-convertible-class.md) für Arraytypen geführt. Daher mussten Bibliotheksautoren bei der Verwendung der Typeigenschaft `std::is_convertible<...>` besondere Schreibweisen für den Microsoft C++-Compiler anwenden. Im folgenden Beispiel sind die statischen Assertionen in früheren Versionen von Visual Studio erfolgreich, jedoch nicht in Visual Studio 2017 Version 15.3:

```cpp
#include <type_traits>

using Array = char[1];

static_assert(std::is_convertible<Array, Array>::value);
static_assert(std::is_convertible<const Array, const Array>::value, "");
static_assert(std::is_convertible<Array&, Array>::value, "");
static_assert(std::is_convertible<Array, Array&>::value, "");
```

`std::is_convertible<From, To>` wird berechnet, indem überprüft wird, ob eine imaginäre Funktionsdefinition wohlgeformt ist:

```cpp
   To test() { return std::declval<From>(); }
```

### <a name="private-destructors-and-stdis_constructible"></a>Private Destruktoren und `std::is_constructible`

Frühere Versionen des Compilers ignorieren, ob ein Destruktor privat war, wenn über das Ergebnis von [std::is_constructible](../standard-library/is-constructible-class.md) entschieden wird. Dies wird nun berücksichtigt. Im folgenden Beispiel sind die statischen Assertionen in früheren Versionen von Visual Studio erfolgreich, jedoch nicht in Visual Studio 2017 Version 15.3:

```cpp
#include <type_traits>

class PrivateDtor {
   PrivateDtor(int) { }
private:
   ~PrivateDtor() { }
};

// This assertion used to succeed. It now correctly fails.
static_assert(std::is_constructible<PrivateDtor, int>::value);
```

Private Destruktoren führen dazu, dass ein Typ nicht konstruierbar ist. `std::is_constructible<T, Args...>` wird berechnet, als würde die folgende Deklaration geschrieben:

```cpp
   T obj(std::declval<Args>()...)
```

Dieser Aufruf impliziert einen Destruktoraufruf.

### <a name="c2668-ambiguous-overload-resolution"></a>C2668: Mehrdeutige Überladungsauflösung

Frühere Versionen des Compilers konnten manchmal keine Mehrdeutigkeiten erkennen, wenn durch die Verwendung von sowohl Deklarationen als auch argumentabhängigen Lookups mehrere Kandidaten gefunden wurden. Dieser Fehler kann zum Auswählen der falschen Überladung und zu unerwartetem Laufzeitverhalten führen. Im folgenden Beispiel löst Visual Studio 2017 Version 15.3 ordnungsgemäß „C2668 `'f': ambiguous call to overloaded function`“ aus:

```cpp
namespace N {
   template<class T>
   void f(T&, T&);

   template<class T>
   void f();
}

template<class T>
void f(T&, T&);

struct S {};
void f()
{
   using N::f;

   S s1, s2;
   f(s1, s2); // C2668
}
```

Um den Code zu korrigieren, entfernen Sie die Anweisung `N::f`, wenn Sie `::f()` aufrufen wollten.

### <a name="c2660-local-function-declarations-and-argument-dependent-lookup"></a>C2660: Lokale Funktionsdeklarationen und argumentabhängiges Lookup

Lokale Funktionsdeklarationen verbergen die Funktitonsdeklaration im umschließenden Bereich und deaktivieren das argumentabhängige Lookup. In früheren Versionen des Compilers wurde in diesem Fall jedoch stets eine argumentabhängige Suche durchgeführt. Dies könnte zum Auswählen der falschen Überladung und zu unerwartetem Laufzeitverhalten führen. Der Fehler liegt in der Regel in einer falschen Signatur der lokalen Funktionsdeklaration. Im folgenden Beispiel löst Visual Studio 2017 Version 15.3 ordnungsgemäß „C2660 `'f': function does not take two arguments`“ aus:

```cpp
struct S {};
void f(S, int);

void g()
{
   void f(S); // C2660 'f': function does not take 2 arguments:
   // or void f(S, int);
   S s;
   f(s, 0);
}
```

Um das Problem zu beheben, ändern Sie entweder die Signatur `f(S)`, oder entfernen Sie diese.

### <a name="c5038-order-of-initialization-in-initializer-lists"></a>C5038: Reihenfolge der Initialisierung in Initialisiererlisten

Klassenmember werden in der Reihenfolge initialisiert, in der sie deklariert sind, nicht in der Reihenfolge, in der Sie in Initialisiererlisten angezeigt werden. Frühere Versionen des Compilers haben keine Warnung ausgegeben, wenn sich die Reihenfolge der Initialisiererliste von der Deklarationsreihenfolge unterschied. Dieses Problem konnte zu undefiniertem Laufzeitverhalten führen, wenn die Initialisierung eines Members von einem anderen Member in der Liste abhing, der bereits initialisiert wurde. Im folgenden Beispiel löst Visual Studio 2017 Version 15.3 (mit **`/Wall`** ) ordnungsgemäß die Warnung „C5038 `data member 'A::y' will be initialized after data member 'A::x'`“ aus:

```cpp
struct A
{
    A(int a) : y(a), x(y) {} // Initialized in reverse, y reused
    int x;
    int y;
};
```

Um das Problem zu beheben, ordnen Sie die Initialisiererliste so an, dass die Reihenfolge mit der Reihenfolge der Deklarationen übereinstimmt. Eine ähnliche Warnung wird ausgelöst, wenn ein oder beide Initialisierer auf Member der Basisklasse verweisen.

Diese Warnung ist standardmäßig deaktiviert und wirkt sich nur auf mit **`/Wall`** kompilierten Code aus.

## <a name="bug-fixes-and-other-behavior-changes-in-155"></a><a name="update_155"></a> Fehlerbehebungen und andere Verhaltensänderungen in 15.5

### <a name="partial-ordering-change"></a>Teilweise Änderung der Reihenfolge

Der Compiler weist nun den folgenden Code ordnungsgemäß zurück und gibt die richtige Fehlermeldung aus:

```cpp
template<typename... T>
int f(T* ...)
{
    return 1;
}

template<typename T>
int f(const T&)
{
    return 2;
}

int main()
{
    int i = 0;
    f(&i);    // C2668
}
```

```Output
t161.cpp
t161.cpp(16): error C2668: 'f': ambiguous call to overloaded function
t161.cpp(8): note: could be 'int f<int*>(const T &)'
        with
        [
            T=int*
        ]
t161.cpp(2): note: or       'int f<int>(int*)'
t161.cpp(16): note: while trying to match the argument list '(int*)'
```

Das Problem im Beispiel oben ist, dass es zwei Unterschiede in den Typen gibt (const im Vergleich zu non-const und pack im Vergleich zu non-pack). Um den Compilerfehler zu beseitigen, entfernen Sie einen der Unterschiede. Dies ermöglicht es dem Compiler, die Funktionen eindeutig zu sortieren.

```cpp
template<typename... T>
int f(T* ...)
{
    return 1;
}

template<typename T>
int f(T&)
{
    return 2;
}

int main()
{
    int i = 0;
    f(&i);
}
```

### <a name="exception-handlers"></a>Ausnahmehandler

Handler, die auf ein Array oder einen Funktionstyp verweisen, stimmen niemals mit einem Ausnahmeobjekt überein. Der Compiler hält sich nun ordnungsgemäß an diese Regel und gibt eine Warnung der Stufe 4 aus. Auch werden Handler von `char*` oder `wchar_t*` nicht mehr einem Zeichenfolgenliteral zugeordnet, wenn **`/Zc:strictStrings`** verwendet wird.

```cpp
int main()
{
    try {
        throw "";
    }
    catch (int (&)[1]) {} // C4843 (This should always be dead code.)
    catch (void (&)()) {} // C4843 (This should always be dead code.)
    catch (char*) {} // This should not be a match under /Zc:strictStrings
}
```

```Output
warning C4843: 'int (&)[1]': An exception handler of reference to array or function type is unreachable, use 'int*' instead
warning C4843: 'void (__cdecl &)(void)': An exception handler of reference to array or function type is unreachable, use 'void (__cdecl*)(void)' instead
```

Mit dem folgenden Code wird der Fehler vermieden:

```cpp
catch (int (*)[1]) {}
```

### <a name="stdtr1-namespace-is-deprecated"></a><a name="tr1"></a> Der `std::tr1`-Namespace ist veraltet.

Der `std::tr1`-Namespace, der nicht dem Standard entspricht, ist nun sowohl im C++14- als auch im C++17-Modus als veraltet markiert. In Visual Studio-2017 Version 15.5 löst der folgende Code C4996 aus:

```cpp
#include <functional>
#include <iostream>
using namespace std;

int main() {
    std::tr1::function<int (int, int)> f = std::plus<int>(); //C4996
    cout << f(3, 5) << std::endl;
    f = std::multiplies<int>();
    cout << f(3, 5) << std::endl;
}
```

```Output
warning C4996: 'std::tr1': warning STL4002: The non-standard std::tr1 namespace and TR1-only machinery are deprecated and will be REMOVED. You can define _SILENCE_TR1_NAMESPACE_DEPRECATION_WARNING to acknowledge that you have received this warning.
```

Um den Fehler zu beheben, entfernen Sie den Verweis auf den `tr1`-Namespace:

```cpp
#include <functional>
#include <iostream>
using namespace std;

int main() {
    std::function<int (int, int)> f = std::plus<int>();
    cout << f(3, 5) << std::endl;
    f = std::multiplies<int>();
    cout << f(3, 5) << std::endl;
}
```

### <a name="standard-library-features-in-annex-d-are-marked-as-deprecated"></a><a name="annex_d"></a> Features der Standardbibliothek in Anhang D sind als veraltet markiert

Wenn der Compilerschalter im **`/std:c++17`** -Modus festgelegt ist, werden fast alle Features der Standardbibliothek in Anhang D als veraltet markiert.

In Visual Studio-2017 Version 15.5 löst der folgende Code C4996 aus:

```cpp
#include <iterator>

class MyIter : public std::iterator<std::random_access_iterator_tag, int> {
public:
    // ... other members ...
};

#include <type_traits>

static_assert(std::is_same<MyIter::pointer, int*>::value, "BOOM");
```

```Output
warning C4996: 'std::iterator<std::random_access_iterator_tag,int,ptrdiff_t,_Ty*,_Ty &>::pointer': warning STL4015: The std::iterator class template (used as a base class to provide typedefs) is deprecated in C++17. (The <iterator> header is NOT deprecated.) The C++ standard has never required user-defined iterators to derive from std::iterator. To fix this warning, stop deriving from std::iterator and start providing publicly accessible typedefs named iterator_category, value_type, difference_type, pointer, and reference. Note that value_type is required to be non-const, even for constant iterators. You can define _SILENCE_CXX17_ITERATOR_BASE_CLASS_DEPRECATION_WARNING or _SILENCE_ALL_CXX17_DEPRECATION_WARNINGS to acknowledge that you have received this warning.
```

Um den Fehler zu beheben, befolgen Sie die Anweisungen im Text der Warnung, wie im folgenden Code gezeigt:

```cpp
#include <iterator>

class MyIter {
public:
    typedef std::random_access_iterator_tag iterator_category;
    typedef int value_type;
    typedef ptrdiff_t difference_type;
    typedef int* pointer;
    typedef int& reference;

    // ... other members ...
};

#include <type_traits>

static_assert(std::is_same<MyIter::pointer, int*>::value, "BOOM");
```

### <a name="unreferenced-local-variables"></a>Unreferenzierte lokale Variablen

In Visual Studio 15.5 wird die Warnung C4189 in den meisten Fällen ausgegeben, wie im folgenden Code gezeigt:

```cpp
void f() {
    char s[2] = {0}; // C4189. Either use the variable or remove it.
}
```

```Output
warning C4189: 's': local variable is initialized but not referenced
```

Um den Fehler zu beheben, entfernen Sie die nicht verwendete Variable.

### <a name="single-line-comments"></a>Einzeilige Kommentare

In Visual Studio 2017 Version 15.5 werden die Warnungen C4001 und C4179 nicht mehr vom C-Compiler ausgegeben. Zuvor wurden sie nur bei Verwendung des Compilerschalters **`/Za`** ausgegeben.  Die Warnungen werden nicht mehr benötigt, weil einzeilige Kommentare seit C99 Teil des C-Standards sind.

```cpp
/* C only */
#pragma warning(disable:4001) //C4619
#pragma warning(disable:4179)
// single line comment
//* single line comment */
```

```Output
warning C4619: #pragma warning: there is no warning number '4001'
```

Wenn der Code nicht abwärtskompatibel sein muss, können Sie die Warnung vermeiden, indem Sie die C4001/C4179-Unterdrückung entfernen. Wenn der Code abwärts kompatibel sein muss, unterdrücken Sie nur C4619.

```C

/* C only */

#pragma warning(disable:4619)
#pragma warning(disable:4001)
#pragma warning(disable:4179)

// single line comment
/* single line comment */
```

### <a name="__declspec-attributes-with-extern-c-linkage"></a>`__declspec`-Attribute mit `extern "C"`-Verknüpfung

In früheren Versionen von Visual Studio hat der Compiler `__declspec(...)`-Attribute ignoriert, wenn `__declspec(...)` vor der `extern "C"`-Verknüpfungsspezifikation angewendet wurde. Dieses Verhalten führte dazu, dass Code generiert wurde, den der Benutzer nicht beabsichtigt hatte (mit möglichen Auswirkungen auf die Laufzeit). Die Warnung wurde in Visual Studio Version 15.3 hinzugefügt, war aber standardmäßig deaktiviert. In Visual Studio 2017 Version 15.5 ist die Warnung standardmäßig aktiviert.

```cpp
__declspec(noinline) extern "C" HRESULT __stdcall //C4768
```

```Output
warning C4768: __declspec attributes before linkage specification are ignored
```

Um den Fehler zu beheben, platzieren Sie die Verknüpfungsspezifikation vor dem Attribut __declspec:

```cpp
extern "C" __declspec(noinline) HRESULT __stdcall
```

Diese neue Warnung C4768 wird für einige Windows SDK-Header ausgegeben, die mit Visual Studio 2017 15.3 oder älter ausgeliefert wurden (Beispiel: Version 10.0.15063.0, auch bekannt als RS2 SDK). Spätere Versionen von Windows SDK-Headern (speziell ShlObj.h und ShlObj_core.h) wurden jedoch so korrigiert, dass sie diese Warnung nicht ausgeben. Wenn Sie sehen, dass diese Warnung von Windows SDK-Headern ausgegeben wird, können Sie diese Aktionen ausführen:

1. Wechseln Sie zum neuesten Windows SDK, das mit Visual Studio 2017 Version 15.5 ausgeliefert wurde.

1. Deaktivieren Sie die Warnung um den #include-Teil der Windows SDK-Headeranweisung:

```cpp
   #pragma warning (push)
   #pragma warning(disable:4768)
   #include <shlobj.h>
   #pragma warning (pop)
   ```

### <a name="extern-constexpr-linkage"></a><a name="extern_linkage"></a> `extern constexpr`-Bindung

In früheren Versionen von Visual Studio gab der Compiler immer eine interne **`constexpr`** -Variablenverknüpfung aus, selbst wenn die Variable als **`extern`** markiert wurde. In Visual Studio 2017 Version 15.5 ermöglicht ein neuer Compilerschalter ( **`/Zc:externConstexpr`** ) das richtige, standardkonforme Verhalten. Letztendlich wird dieses Verhalten die Standardeinstellung sein.

```cpp
extern constexpr int x = 10;
```

```Output
error LNK2005: "int const x" already defined
```

Wenn eine Headerdatei eine Variable enthält, die als **`extern constexpr`** deklariert ist, muss sie als `__declspec(selectany)` markiert werden, damit ihre doppelten Deklarationen richtig kombiniert werden:

```cpp
extern constexpr __declspec(selectany) int x = 10;
```

### <a name="typeid-cant-be-used-on-incomplete-class-type"></a>`typeid` kann nicht für einen unvollständigen Klassentyp verwendet werden

In früheren Versionen von Visual Studio ließ der Compiler fälschlicherweise den folgenden Code zu, was zu potenziell falschen Typinformationen führte. In Visual Studio 2017 Version 15.5 löst der Compiler ordnungsgemäß einen Fehler aus:

```cpp
#include <typeinfo>

struct S;

void f() { typeid(S); } //C2027 in 15.5
```

```Output
error C2027: use of undefined type 'S'
```

### <a name="stdis_convertible-target-type"></a>`std::is_convertible`-Zieltyp

`std::is_convertible` erfordert, dass der Zieltyp ein gültiger Rückgabetyp ist. In früheren Versionen von Visual Studio ließ der Compiler fälschlicherweise abstrakte Typen zu, was zu falscher Überladungsauflösung und unbeabsichtigtem Laufzeitverhalten führen konnte.  Der folgende Code löst jetzt ordnungsgemäß c2338 aus:

```cpp
#include <type_traits>

struct B { virtual ~B() = 0; };
struct D : public B { virtual ~D(); };

static_assert(std::is_convertible<D, B>::value, "fail"); // C2338 in 15.5
```

Um den Fehler zu vermeiden, sollten Sie bei der Verwendung von `is_convertible` Zeigertypen vergleichen, da ein Vergleich ohne Zeigertyp möglicherweise zu einem Fehler führt, wenn ein Typ abstrakt ist:

```cpp
#include <type_traits>

struct B { virtual ~B() = 0; };
struct D : public B { virtual ~D(); };

static_assert(std::is_convertible<D *, B *>::value, "fail");
```

### <a name="dynamic-exception-specification-removal-and-noexcept"></a><a name="noexcept_removal"></a> Entfernen der dynamischen Ausnahmespezifikation und `noexcept`

In C++17 ist `throw()` ein Alias für **`noexcept`** . `throw(<type list>)` und `throw(...)` werden entfernt, und bestimmte Typen können **`noexcept`** enthalten. Diese Änderung kann zu Quellkompatibilitätsproblemen mit Code führen, der mit C++14 oder früher konform ist. Die Option **`/Zc:noexceptTypes-`** kann verwendet werden, um zur C++14-Version von **`noexcept`** zurückzukehren, während generell der C++17-Modus verwendet wird. Dies ermöglicht es Ihnen, Ihren Quellcode zu aktualisieren, um ihn an C++17 anzupassen, ohne dass Sie Ihren gesamten `throw()`-Code zur gleichen Zeit neu schreiben müssen.

Der Compiler diagnostiziert nun auch eine größere Anzahl nicht übereinstimmender Ausnahmespezifikationen in Deklarationen im C++17-Modus oder mit [`/permissive-`](../build/reference/permissive-standards-conformance.md) mit der neuen Warnung C5043.

Der folgende Code generiert C5043 und C5040 in Visual Studio 2017 Version 15.5, wenn der Schalter **`/std:c++17`** verwendet wird:

```cpp
void f() throw(); // equivalent to void f() noexcept;
void f() {} // warning C5043
void g() throw(); // warning C5040

struct A {
    virtual void f() throw();
};

struct B : A {
    virtual void f() { } // error C2694
};
```

Sie können die Fehler entfernen, während Sie weiterhin **`/std:c++17`** verwenden, indem Sie entweder die Option **`/Zc:noexceptTypes-`** zur Befehlszeile hinzufügen oder Ihren Code aktualisieren, um wie im folgenden Beispiel gezeigt **`noexcept`** zu verwenden:

```cpp
void f() noexcept;
void f() noexcept { }
void g() noexcept(false);

struct A {
    virtual void f() noexcept;
};

struct B : A {
    virtual void f() noexcept { }
};
```

### <a name="inline-variables"></a>Inlinevariablen

Statische **`constexpr`** -Datenmember sind nun implizit **`inline`** . Ihre Deklaration innerhalb einer Klasse ist nun also ihre Definition. Die Verwendung einer Out-of-Line-Definition für einen statischen **`static constexpr`** -Datenmember ist redundant und nun veraltet. Wenn in Visual Studio 2017 Version 15,5 der Schalter **`/std:c++17`** verwendet wird, generiert der folgende Code nun die Warnung „C5041 `'size': out-of-line definition for constexpr static data member is not needed and is deprecated in C++17`“:

```cpp
struct X {
    static constexpr int size = 3;
};
const int X::size; // C5041
```

### <a name="extern-c-__declspec-warning-c4768-now-on-by-default"></a>`extern "C" __declspec(...)` Warnung C4768 jetzt standardmäßig aktiviert

Die Warnung wurde in Visual Studio Version 2017 Version 15.3 hinzugefügt, war aber standardmäßig deaktiviert. In Visual Studio 2017 Version 15.5 ist die Warnung standardmäßig aktiviert. Weitere Informationen finden Sie unter [Neue Warnung zu \_\_-Attributen](#declspec).

### <a name="defaulted-functions-and-__declspecnothrow"></a>Standardfunktionen und `__declspec(nothrow)`

Der Compiler erlaubte es bisher, Standardfunktionen mit `__declspec(nothrow)` zu deklarieren, wenn die entsprechenden Basis-/Memberfunktionen Ausnahmen zuließen. Dieses Verhalten steht im Widerspruch zum C++-Standard und kann zur Laufzeit zu undefiniertem Verhalten führen. Der Standard verlangt, dass solche Funktionen als gelöscht definiert werden, wenn es eine Abweichung von der Ausnahmespezifikation gibt.  Bei Verwendung von **`/std:c++17`** löst der folgende Code nun „C2280 `attempting to reference a deleted function. Function was implicitly deleted because the explicit exception specification is incompatible with that of the implicit declaration.`“ aus

```cpp
struct A {
    A& operator=(const A& other) { // No exception specification; this function may throw.
        ...
    }
};

struct B : public A {
    __declspec(nothrow) B& operator=(const B& other) = default;
};

int main()
{
    B b1, b2;
    b2 = b1; // error C2280
}
```

Um diesen Code zu korrigieren, entfernen Sie entweder __declspec(nothrow) aus der Standardfunktion, oder entfernen Sie `= default`, und geben Sie eine Definition für die Funktion zusammen mit der erforderlichen Ausnahmebehandlung an:

```cpp
struct A {
    A& operator=(const A& other) {
        // ...
    }
};

struct B : public A {
    B& operator=(const B& other) = default;
};

int main()
{
    B b1, b2;
    b2 = b1;
}
```

### <a name="noexcept-and-partial-specializations"></a>`noexcept` und Teilspezialisierungen

Mit **`noexcept`** im Typsystem können Teilspezialisierungen für den Abgleich bestimmter aufrufbarer Typen möglicherweise nicht kompiliert werden oder nicht die primäre Vorlage auswählen. Der Grund hierfür ist eine fehlende Teilspezialisierung für Zeiger auf noexcept-Funktionen.

In solchen Fällen kann es erforderlich sein, zusätzliche Teilspezialisierungen hinzuzufügen, um die **`noexcept`** -Funktionszeiger und die **`noexcept`** -Zeiger auf Memberfunktionen zu verarbeiten. Diese Überladungen sind nur im **`/std:c++17`** -Modus zulässig. Wenn die Abwärtskompatibilität mit C++14 aufrechterhalten werden muss und Sie Code schreiben, den andere nutzen, sollten Sie diese neuen Überladungen innerhalb von `#ifdef`-Anweisungen schützen. Wenn Sie in einem eigenständigen Modul arbeiten, können Sie anstelle von `#ifdef`-Wächtern einfach den Schalter **`/Zc:noexceptTypes-`** für die Kompilierung verwenden.

Der folgende Code wird bei Verwendung von **`/std:c++14`** kompiliert, bei Verwendung von **`/std:c++17`** mit `error C2027: use of undefined type 'A<T>'` tritt jedoch ein Fehler auf:

```cpp
template <typename T> struct A;

template <>
struct A<void(*)()>
{
    static const bool value = true;
};

template <typename T>
bool g(T t)
{
    return A<T>::value;
}

void f() noexcept {}

int main()
{
    return g(&f) ? 0 : 1; // C2027
}
```

Der folgende Code ist bei Verwendung von **`/std:c++17`** erfolgreich, da der Compiler die neue Teilspezialisierung `A<void (*)() noexcept>` auswählt:

```cpp
template <typename T> struct A;

template <>
struct A<void(*)()>
{
    static const bool value = true;
};

template <>
struct A<void(*)() noexcept>
{
    static const bool value = true;
};

template <typename T>
bool g(T t)
{
    return A<T>::value;
}

void f() noexcept {}

int main()
{
    return g(&f) ? 0 : 1; // OK
}
```

## <a name="bug-fixes-and-other-behavior-changes-in-157"></a><a name="update_157"></a> Fehlerbehebungen und andere Verhaltensänderungen in 15.7

### <a name="c17-default-argument-in-the-primary-class-template"></a>C++17: Standardargument in der primären Klassenvorlage

Diese Verhaltensänderung ist eine Vorbedingung für [Vorlagenargumentableitung für Klassenvorlagen – P0091R3](https://wg21.link/p0091r3).

Zuvor hat der Compiler das Standardargument in der primären Klassenvorlage ignoriert:

```cpp
template<typename T>
struct S {
    void f(int = 0);
};

template<typename T>
void S<T>::f(int = 0) {} // Re-definition necessary
```

Im **`/std:c++17`** -Modus in Visual Studio 2017 Version 15.7 wird das Standardargument nicht ignoriert:

```cpp
template<typename T>
struct S {
    void f(int = 0);
};

template<typename T>
void S<T>::f(int) {} // Default argument is used
```

### <a name="dependent-name-resolution"></a>Abhängige Namensauflösung

Diese Verhaltensänderung ist eine Vorbedingung für [Vorlagenargumentableitung für Klassenvorlagen – P0091R3](https://wg21.link/p0091r3).

Im folgenden Beispiel löst der Compiler in Visual Studio 15.6 und früher `D::type` zu `B<T>::type` in der primären Klassenvorlage auf.

```cpp
template<typename T>
struct B {
    using type = T;
};

template<typename T>
struct D : B<T*> {
    using type = B<T*>::type;
};
```

Für Version 15.7 von Visual Studio 2017 im Modus **`/std:c++17`** ist das **`typename`** -Schlüsselwort in der **`using`** -Anweisung von D erforderlich. Wenn **`typename`** nicht vorhanden ist, löst der Compiler die Warnung C4346 (`'B<T*>::type': dependent name is not a type`) und den Fehler C2061 (`syntax error: identifier 'type'`) aus:

```cpp
template<typename T>
struct B {
    using type = T;
};

template<typename T>
struct D : B<T*> {
    using type = typename B<T*>::type;
};
```

### <a name="c17-nodiscard-attribute---warning-level-increase"></a>C++17 `[[nodiscard]]`-Attribute: Anstieg der Warnstufe

In Visual Studio 2017 Version 15.7 wurde im **`/std:c++17`** -Modus die Warnstufe von „C4834 `discarding return value of function with 'nodiscard' attribute`“ von W3 in W1 erhöht. Sie können die Warnung mit einer Umwandlung zu **`void`** oder durch Übergabe von **`/wd:4834`** an den Compiler deaktivieren.

```cpp
[[nodiscard]] int f() { return 0; }

int main() {
    f(); // warning: discarding return value
         // of function with 'nodiscard'
}
```

### <a name="variadic-template-constructor-base-class-initialization-list"></a>Initialisierungsliste für Basisklassen für variadic-Vorlagenkonstruktoren

In früheren Editionen von Visual Studio war eine Initialisierungsliste für Basisklassen für variadic-Vorlagenkonstruktoren, in der Vorlagenargumente fehlten, fälschlicherweise ohne Fehler zulässig. In Visual Studio 2017 Version 15.7 wird ein Compilerfehler ausgelöst.

Das folgende Codebeispiel in Version 15.7 von Visual Studio 2017 löst den Fehler „C2614: `D<int>: illegal member initialization: 'B' is not a base or member`“ aus.

```cpp
template<typename T>
struct B {};

template<typename T>
struct D : B<T>
{

    template<typename ...C>
    D() : B() {} // C2614. Missing template arguments to B.
};

D<int> d;
```

Ändern Sie den B()-Ausdruck zu „B\<T>T>()“, um den Fehler zu beheben.

### <a name="constexpr-aggregate-initialization"></a>`constexpr`-Aggregatinitialisierung

In früheren Versionen des C++-Compilers wurde die **`constexpr`** -Aggregatinitialisierung falsch behandelt. Der Compiler hat ungültigen Code akzeptiert, in dem die Aggregatinitialisierungsliste über zu viele Elemente verfügte und eine ungültige Codegenerierung erzeugte. Ein Beispiel für einen solchen Code wird im Folgenden gezeigt:

```cpp
#include <array>
struct X {
    unsigned short a;
    unsigned char b;
};

int main() {
    constexpr std::array<X, 2> xs = {
        { 1, 2 },
        { 3, 4 }
    };
    return 0;
}
```

In Visual Studio 2017 Version 15.7 Update 3 und höher löst das vorherige Beispiel jetzt „C2078 `too many initializers`“ aus. Im unten stehenden Codebeispiel wird veranschaulicht, wie der Code behoben wird. Beim Initialisieren eines `std::array` mit geschachtelten „brace-init-list“-Objekten weisen Sie dem inneren Array selbst ein „braced-list“ zu:

```cpp
#include <array>
struct X {
    unsigned short a;
    unsigned char b;
};

int main() {
    constexpr std::array<X, 2> xs = {{ // note double braces
        { 1, 2 },
        { 3, 4 }
    }}; // note double braces
    return 0;
}
```

## <a name="bug-fixes-and-behavior-changes-in-158"></a><a name="update_158"></a> Fehlerbehebungen und Verhaltensänderungen in 15.8

Bei sämtlichen Compileränderungen in Visual Studio 2017 Version 15.8 handelt es sich um Fehlerbehebungen und Verhaltensänderungen. Sie sind im Folgenden aufgeführt:

### <a name="typename-on-unqualified-identifiers"></a>`typename` für nicht qualifizierte Bezeichner

Im Modus [`/permissive-`](../build/reference/permissive-standards-conformance.md) werden falsche **`typename`** -Schlüsselwörter für nicht qualifizierte Bezeichner in Definitionen von Aliasvorlagen vom Compiler nicht mehr akzeptiert. Mit dem folgenden Code wird nun „C7511 `'T': 'typename' keyword must be followed by a qualified name`“ generiert.

```cpp
template <typename T>
using  X = typename T;
```

Ändern Sie die zweite Zeile in `using  X = T;`, um den Fehler zu beheben.

### <a name="__declspec-on-right-side-of-alias-template-definitions"></a>`__declspec()` auf der rechten Seite der Definitionen von Aliasvorlagen

[__declspec](../cpp/declspec.md) ist auf der rechten Seite einer Aliasvorlagendefinition nicht mehr zulässig. Zuvor hat der Compiler diesen Code akzeptiert, jedoch ignoriert. Bei Verwendung des Alias wurde keine Warnung zu veralteten Features generiert.

Das C++-Standardattribut [\[\[deprecated\]\]](../cpp/attributes.md) kann stattdessen verwendet werden und wird ab Visual Studio 2017 Version 15.6 eingehalten. Mit dem folgenden Code wird nun „C2760 `syntax error: unexpected token '__declspec', expected 'type specifier'`“ generiert:

```cpp
template <typename T>
using X = __declspec(deprecated("msg")) T;
```

Ersetzen Sie den Code mit dem Folgenden (mit den Attributen vor dem „=“ der Aliasdefinition), um den Fehler zu beheben:

```cpp
template <typename T>
using  X [[deprecated("msg")]] = T;
```

### <a name="two-phase-name-lookup-diagnostics"></a>Diagnose der Zweiphasennamenssuche

Die Zweiphasennamenssuche erfordert, dass nicht abhängige Namen in Vorlagentexten zum Zeitpunkt der Definition für die Vorlage sichtbar sind. Zuvor hätte der Microsoft C++-Compiler einen nicht gefundenen Namen bis zu den Instanziierungszeitpunkten nicht gesucht. Nun müssen nicht abhängige Namen im Vorlagentext gebunden sein.

Dies kann sich beispielsweise ergeben, wenn in abhängigen Basisklassen gesucht wird. Zuvor war im Compiler die Verwendung von Namen zulässig, die in abhängigen Basisklassen definiert sind. Der Grund dafür ist, dass diese Namen bei der Instanziierung ermittelt wurden, wenn alle Typen aufgelöst werden. Nun wird dieser Code als Fehler behandelt. In diesen Fällen können Sie erzwingen, dass nach der Variable zum Instanziierungszeitpunkt gesucht wird, indem Sie sie mit dem Basisklassentyp qualifizieren oder anderweitig abhängig machen, indem Sie beispielsweise einen `this->`-Pointer hinzufügen.

Im Modus [`/permissive-`](../build/reference/permissive-standards-conformance.md) erzeugt der folgende Code nun „C3861: `'base_value': identifier not found`“:

```cpp
template <class T>
struct Base {
    int base_value = 42;
};

template <class T>
struct S : Base<T> {
    int f() {
        return base_value;
    }
};
```

Ändern Sie die Anweisung **`return`** in `return this->base_value;`, um den Fehler zu beheben.

**Hinweis**: In der Boost-Python-Bibliothek ist eine MSVC-spezifische Problemumgehung für eine Vorlagenvorwärtsdeklaration in [unwind_type.hpp](https://github.com/boostorg/python/blame/develop/include/boost/python/detail/unwind_type.hpp) vorhanden. Im [`/permissive-`](../build/reference/permissive-standards-conformance.md)-Modus ab Visual Studio 2017 Version 15.8 (\_MSC\_VER=1915) führt der MSVC-Compiler die argumentabhängige Namenssuche ordnungsgemäß aus. Das Verhalten entspricht jetzt dem Verhalten anderer Compiler, sodass diese Problemumgehung nicht mehr erforderlich ist. Um den Fehler „C3861: `'unwind_type': identifier not found`“ zu vermeiden, finden Sie unter [PR 229](https://github.com/boostorg/python/pull/229) im Boost-Repository Informationen zum Aktualisieren der Headerdatei. Das Boost-Paket [vcpkg](../build/vcpkg.md) wurde bereits gepatcht. Wenn Sie also Ihre Boost-Quellen aus vcpkg abrufen oder aktualisieren möchten, müssen Sie den Patch nicht separat anwenden.

### <a name="forward-declarations-and-definitions-in-namespace-std"></a>Vorwärtsdeklarationen und -definitionen im Namespace `std`

Standardmäßig ist es in C++ nicht zulässig, dem Namespace `std` Vorwärtsdeklarationen oder -definitionen hinzuzufügen. Das Hinzufügen von Deklarationen oder Definitionen in den Namespace `std` oder einen Namespace im Namespace `std` resultiert nun in nicht definiertem Verhalten.

Der Ort, an dem einige Standardbibliothekstypen definiert werden, soll zu einem zukünftigen Zeitpunkt verschoben werden. Durch diese Änderung wird vorhandener Code, der dem Namespace `std` Vorwärtsdeklarationen hinzufügt, unterbrochen. Eine neue Warnung (C4643) hilft beim Identifizieren solcher Probleme mit der Quelle. Im **`/default`** -Modus ist die Warnung aktiviert, standardmäßig ist sie deaktiviert. Dies wirkt sich auf Programme aus, die mit **`/Wall`** oder **`/WX`** kompiliert werden.

Mit dem folgenden Code wird jetzt „C4643: `Forward declaring 'vector' in namespace std is not permitted by the C++ Standard`“ ausgelöst.

```cpp
namespace std {
    template<typename T> class vector;
}
```

Verwenden Sie anstelle einer Vorwärtsdeklaration eine **include**-Anweisung, um den Fehler zu beheben:

```cpp
#include <vector>
```

### <a name="constructors-that-delegate-to-themselves"></a>Auf sich selbst verweisende Konstruktoren

Der C++-Standard schlägt vor, dass ein Compiler eine Diagnose ausgeben soll, wenn ein delegierender Konstruktor an sich selbst delegiert. Der Microsoft C++-Compiler in den Modi [`/std:c++17`](../build/reference/std-specify-language-standard-version.md) und [`/std:c++latest`](../build/reference/std-specify-language-standard-version.md) löst nun „C7535: `'X::X': delegating constructor calls itself`„ aus.

Ohne diese Fehlermeldung wird das folgende Programm kompiliert, jedoch wird eine Endlosschleife erstellt:

```cpp
class X {
public:
    X(int, int);
    X(int v) : X(v){}
};
```

Delegieren Sie an einen anderen Konstruktor, um die Endlosschleife zu vermeiden:

```cpp
class X {
public:

    X(int, int);
    X(int v) : X(v, 0) {}
};
```

### <a name="offsetof-with-constant-expressions"></a>`offsetof` mit konstanten Ausdrücken

[offsetof](../c-runtime-library/reference/offsetof-macro.md) wurde bisher mithilfe eines Makros implementiert, das [reinterpret_cast](../cpp/reinterpret-cast-operator.md) erfordert. Die Verwendung ist in Kontexten nicht zulässig, die einen konstanten Ausdruck erfordern, jedoch war es bisher im Microsoft C++-Compiler gültig. Das `offsetof`-Makro, das im Rahmen der Standardbibliothek enthalten ist, verwendet eine intrinsische Compiler-Funktion ( **__builtin_offsetof**), jedoch haben viele Personen den Makro-Trick verwendet, um `offsetof` selbst zu definieren.

In Visual Studio 2017, Version 15.8, beschränkt der Compiler die Bereiche, in denen diese **`reinterpret_cast`** -Operatoren im Standardmodus auftreten können, damit der Code dem Standardverhalten von C++ besser entspricht. Im Modus [`/permissive-`](../build/reference/permissive-standards-conformance.md) sind die Einschränkungen sogar strenger. Wenn ein `offsetof`-Ergebnis an Stellen verwendet wird, an denen konstante Ausdrücke erforderlich sind, löst der Code möglicherweise die Warnung „C4644 `usage of the macro-based offsetof pattern in constant expressions is non-standard; use offsetof defined in the C++ standard library instead`“ oder „C2975 `invalid template argument, expected compile-time constant expression`“ aus.

Der folgende Code löst in den Modi **`/default`** und **`/std:c++17`** C4644 und im Modus [`/permissive-`](../build/reference/permissive-standards-conformance.md) C2975 aus:

```cpp
struct Data {
    int x;
};

// Common pattern of user-defined offsetof
#define MY_OFFSET(T, m) (unsigned long long)(&(((T*)nullptr)->m))

int main()

{
    switch (0) {
    case MY_OFFSET(Data, x): return 0;
    default: return 1;
    }
}
```

Verwenden Sie `offsetof` wie über \<cstddef> definiert, um den Fehler zu beheben:

```cpp
#include <cstddef>

struct Data {
    int x;
};

int main()
{
    switch (0) {
    case offsetof(Data, x): return 0;
    default: return 1;
    }
}
```

### <a name="cv-qualifiers-on-base-classes-subject-to-pack-expansion"></a>CV-Qualifizierer auf Basisklassen, die einer Paketerweiterung unterliegen

Vorherige Versionen des Microsoft C++-Compilers haben nicht erkannt, dass Basisklassen über CV-Qualifizierer verfügen, wenn sie ebenfalls Paketerweiterungen unterliegen.

In Visual Studio 2017, Version 15.8 löst der folgende Code im Modus [`/permissive-`](../build/reference/permissive-standards-conformance.md) die Warnung „C3770: `'const S': is not a valid base class`“ aus:

```cpp
template<typename... T>
class X : public T... { };

class S { };

int main()
{
    X<const S> x;
}
```

### <a name="template-keyword-and-nested-name-specifiers"></a>`template`-Schlüsselwort und geschachtelte Namensspezifizierer

Im Modus [`/permissive-`](../build/reference/permissive-standards-conformance.md) erfordert der Compiler nun das Schlüsselwort **`template`** , das einem Vorlagennamen vorangestellt wird, wenn dieser hinter einem abhängigen geschachtelten Namensspezifizierer steht.

Im Modus [`/permissive-`](../build/reference/permissive-standards-conformance.md) erzeugt der folgende Code nun „C7510: `'example': use of dependent template name must be prefixed with 'template'. note: see reference to class template instantiation 'X<T>' being compiled`“:

```cpp
template<typename T> struct Base
{
    template<class U> void example() {}
};

template<typename T>
struct X : Base<T>
{
    void example()
    {
        Base<T>::example<int>();
    }
};
```

Fügen Sie der Anweisung `Base<T>::example<int>();` das Schlüsselwort **`template`** wie im folgenden Beispiel gezeigt hinzu, um den Fehler zu beheben:

```cpp
template<typename T> struct Base
{
    template<class U> void example() {}
};

template<typename T>
struct X : Base<T>
{
    void example()
    {
        // Add template keyword here:
        Base<T>::template example<int>();
    }
};
```

## <a name="bug-fixes-and-behavior-changes-in-159"></a><a name="update_159"></a> Fehlerbehebungen und Verhaltensänderungen in 15.9

### <a name="identifiers-in-member-alias-templates"></a>Bezeichner in Memberaliasvorlagen

Ein Bezeichner, der in einer Memberalias-Vorlagendefinition verwendet wird, muss vor der Verwendung deklariert werden.

In vorherigen Compilerversionen war der folgende Code zulässig:

```cpp
template <typename... Ts>
struct A
{
  public:
    template <typename U>
    using from_template_t = decltype(from_template(A<U>{}));

  private:
    template <template <typename...> typename Type, typename... Args>
    static constexpr A<Args...> from_template(A<Type<Args...>>);
};

A<>::from_template_t<A<int>> a;
```

In Visual Studio 2017 Version 15.9 löst der Compiler im [`/permissive-`](../build/reference/permissive-standards-conformance.md)-Modus „C3861: `'from_template': identifier not found`“ aus.

Um den Fehler zu beheben, deklarieren Sie `from_template_t` vor `from_template`.

### <a name="modules-changes"></a>Moduländerungen

In Visual Studio 2017, Version 15.9 löst der Compiler immer dann den Fehler C5050 aus, wenn die Befehlszeilenoptionen für Module zwischen Modulerstellung und Modulverwendung nicht konsistent sind. Im folgenden Beispiel liegen zwei Probleme vor:

- Auf der Verbraucherseite (main.cpp) ist die Option **`/EHsc`** nicht angegeben.

- Die C++-Version lautet auf der Erstellerseite **`/std:c++17`** und auf der Verbraucherseite **`/std:c++14`** .

```cmd
cl /EHsc /std:c++17 m.ixx /experimental:module
cl /experimental:module /module:reference m.ifc main.cpp /std:c++14
```

Der Compiler löst in beiden Fällen die Warnung C5050 aus: `warning C5050: Possible incompatible environment while importing module 'm': mismatched C++ versions.  Current "201402" module version "201703"`.

Darüber hinaus löst der Compiler immer dann einen C7536-Fehler aus, wenn die IFC-Datei geändert wurde. Der Header der Modulschnittstelle enthält einen SHA2-Hash der darunter befindlichen Inhalte. Beim Import wird die IFC-Datei gehasht und dann mit dem im Header angegebenen Hash verglichen. Wenn diese nicht übereinstimmen, wird der Fehler C7536 ausgelöst: `ifc failed integrity checks.  Expected SHA2: '66d5c8154df0c71d4cab7665bab4a125c7ce5cb9a401a4d8b461b706ddd771c6'`.

### <a name="partial-ordering-involving-aliases-and-non-deduced-contexts"></a>Teilsortierung im Zusammenhang mit Aliasen und nicht abgeleiteten Kontexten

Es besteht ein Implementierungsunterschied bei den Regeln für die Teilsortierung im Zusammenhang mit Aliasen in nicht abgeleiteten Kontexten. Im folgenden Beispiel lösen GCC und der Microsoft C++-Compiler (im Modus [`/permissive-`](../build/reference/permissive-standards-conformance.md)) einen Fehler aus, während Clang den Code akzeptiert.

```cpp
#include <utility>
using size_t = std::size_t;

template <typename T>
struct A {};
template <size_t, size_t>
struct AlignedBuffer {};
template <size_t len>
using AlignedStorage = AlignedBuffer<len, 4>;

template <class T, class Alloc>
int f(Alloc &alloc, const AlignedStorage<T::size> &buffer)
{
    return 1;
}

template <class T, class Alloc>
int f(A<Alloc> &alloc, const AlignedStorage<T::size> &buffer)
{
    return 2;
}

struct Alloc
{
    static constexpr size_t size = 10;
};

int main()
{
    A<void> a;
    AlignedStorage<Alloc::size> buf;
    if (f<Alloc>(a, buf) != 2)
    {
        return 1;
    }

    return 0;
}
```

Das vorherige Beispiel löst C2668 aus:

```Output
partial_alias.cpp(32): error C2668: 'f': ambiguous call to overloaded function
partial_alias.cpp(18): note: could be 'int f<Alloc,void>(A<void> &,const AlignedBuffer<10,4> &)'
partial_alias.cpp(12): note: or       'int f<Alloc,A<void>>(Alloc &,const AlignedBuffer<10,4> &)'
        with
        [
            Alloc=A<void>
        ]
partial_alias.cpp(32): note: while trying to match the argument list '(A<void>, AlignedBuffer<10,4>)'
```

Der Grund für den Implementierungsunterschied ist eine Regression in der C++-Standardformulierung. Bei der Lösung des Kernproblems 2235 wurde Text entfernt, der erlauben würde, dass diese Überladungen sortiert werden können. Der aktuelle C++-Standard bietet keinen Mechanismus für eine Teilsortierung dieser Funktionen, deshalb können sie als nicht eindeutig betrachtet werden.

Als Problemumgehung wird empfohlen, sich nicht auf die Teilsortierung zum Lösen dieses Problems zu verlassen. Verwenden Sie stattdessen SFINAE zum Entfernen von bestimmter Überladungen. Im folgenden Beispiel wird eine Hilfsklasse `IsA` verwendet, um die erste Überladung zu entfernen, wenn `Alloc` eine Spezialisierung von `A` ist:

```cpp
#include <utility>
using size_t = std::size_t;

template <typename T>
struct A {};
template <size_t, size_t>
struct AlignedBuffer {};
template <size_t len>
using AlignedStorage = AlignedBuffer<len, 4>;

template <typename T> struct IsA : std::false_type {};
template <typename T> struct IsA<A<T>> : std::true_type {};

template <class T, class Alloc, typename = std::enable_if_t<!IsA<Alloc>::value>>
int f(Alloc &alloc, const AlignedStorage<T::size> &buffer)
{
    return 1;
}

template <class T, class Alloc>
int f(A<Alloc> &alloc, const AlignedStorage<T::size> &buffer)
{
    return 2;
}

struct Alloc
{
    static constexpr size_t size = 10;
};

int main()
{
    A<void> a;
    AlignedStorage<Alloc::size> buf;
    if (f<Alloc>(a, buf) != 2)
    {
        return 1;
    }

    return 0;
}
```

### <a name="illegal-expressions-and-non-literal-types-in-templated-function-definitions"></a>Ungültige Ausdrücke und Nichtliteraltypen in Definitionen von Vorlagenfunktionen

Ungültige Ausdrücke und Nichtliteraltypen werden nun richtig in Definitionen von Vorlagenfunktionen diagnostiziert, die explizit spezialisiert werden. Bisher wurden solche Fehler nicht für die Funktionsdefinition ausgegeben. Der ungültige Ausdruck oder Nichtliteraltyp wurde aber trotzdem diagnostiziert, wenn er als Teil eines konstanten Ausdrucks ausgewertet wurde.

In früheren Versionen von Visual Studio wird der folgende Code ohne Warnung kompiliert:

```cpp
void g();

template<typename T>
struct S
{
    constexpr void f();
};

template<>
constexpr void S<int>::f()
{
    g(); // C3615 in 15.9
}
```

In Visual Studio 2017 Version 15.9 führt der Code zu diesem Fehler:

```Output
error C3615: constexpr function 'S<int>::f' cannot result in a constant expression.
note: failure was caused by call of undefined function or one not declared 'constexpr'
note: see usage of 'g'.
```

Entfernen Sie den Qualifizierer **`constexpr`** aus der expliziten Instanziierung der Funktion `f()`, um diesen Fehler zu vermeiden.

::: moniker-end

::: moniker range="vs-2015"

## <a name="c-conformance-improvements-in-visual-studio-2015"></a>Verbesserungen der C++-Konformität in Visual Studio 2015

Es ist eine vollständige Liste der Konformitätsverbesserungen bis Visual Studio 2015 Update 3 verfügbar. Weitere Informationen finden Sie unter [Visual C++: Neuerungen 2003 bis 2015](/cpp/porting/visual-cpp-what-s-new-2003-through-2015).

::: moniker-end

## <a name="see-also"></a>Siehe auch

[Microsoft C++-Sprachkonformität: Tabelle](visual-cpp-language-conformance.md)
