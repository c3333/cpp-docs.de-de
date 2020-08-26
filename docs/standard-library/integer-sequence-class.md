---
title: integer_sequence-Klasse
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::index_sequence
- type_traits/std::make_index_sequence
- type_traits/std::integer_sequence
- type_traits/std::make_integer_sequence
- type_traits/std::index_sequence_for
helpviewer_keywords:
- std::index_sequence
- std::make_index_sequence
- std::integer_sequence
- std::make_integer_sequence
- std::index_sequence_for
ms.assetid: 2cfdddee-819d-478e-bb78-c8a9c2696803
ms.openlocfilehash: 4d927be4fdd41ab75ca78a0e0e7ab0282e4fbf6a
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88843871"
---
# <a name="integer_sequence-class"></a>integer_sequence-Klasse

Stellt eine Ganzzahlsequenz dar. Kann zum ableiten und Erweitern von Parameter Paketen in Variadic-Typen wie "Std:: Tuple" verwendet werden \<T...> , die als Argumente an eine Funktion übergeben werden.

## <a name="syntax"></a>Syntax

```cpp
template <class T, T... Vals>
struct integer_sequence
```

### <a name="parameters"></a>Parameter

*Bund*\
Der Typ von Werten; muss sich um einen integralen Typ handeln: „bool“, „char“, „char16_t“, „char32_t“, „wchar_t“ oder signierte oder nicht signierte Ganzzahltypen.

*Veranstaltungen*\
Ein typenloses Parameterpaket, das eine Sequenz von Werten des integralen Typs T darstellt.

## <a name="members"></a>Member

|Name|Beschreibung|
|-|-|
|`static size_t size() noexcept`|Die Anzahl der Elemente in der Sequenz.|
|`typedef T value_type`|Der Typ jedes Elements in der Sequenz. Muss ein ganzzahliger Typ sein.|

## <a name="remarks"></a>Bemerkungen

Ein Parameterpaket, das direkt an eine Funktion weitergegeben wird, kann ohne spezielle Bibliothekshilfsprogramme entpackt werden. Wenn ein Parameterpaket Bestandteil eines an eine Funktion weitergegebenen Typs ist und Sie Indizes für den Zugriff auf Elemente benötigen, besteht die einfachste Möglichkeit es zu entpacken darin, `integer_sequence` und die zugehörigen Typaliase `make_integer_sequence`, `index_sequence`, `make_index_sequence` und `index_sequence_for` zu verwenden.

## <a name="example"></a>Beispiel

Das folgende Beispiel beruht auf dem ursprünglichen Vorschlag [N3658](https://wg21.link/n3658). Darin wird die Verwendung von `integer_sequence` zum Erstellen von `std::tuple` aus `std::array<T,N>` und die Verwendung von `integer_sequence` für den Abruf bei Tupel-Membern gezeigt.

In der Funktion `a2t` ist `index_sequence` ein Alias von `integer_sequence` auf Grundlage des integralen Typs `size_t`. `make_index_sequence` ist ein Alias, der zum Zeitpunkt der Kompilierung eine nullbasierte `index_sequence` mit der gleichen Anzahl an Elementen wie das Array erstellt, das durch den Aufrufer weitergegeben wird. `a2t` übergibt `index_sequence` nach Wert an `a2t_`, wo der Ausdruck `a[I]...` entpackt`I` wird. Dann werden die Elemente an `make_tuple` übergeben, wo sie als einzelne Argumente verwendet werden. Wenn Sie Sequenz beispielsweise drei Elemente enthält, wird `make_tuple` als „make_tuple(a[0], a[1], a[2])“ aufgerufen. Die Arrayelemente an sich können von einem beliebigen Typ sein.

Die Apply-Funktion akzeptiert ein [Std:: Tuple](../standard-library/tuple-class.md)und erzeugt `integer_sequence` mithilfe der- `tuple_size` Hilfsklasse einen. Beachten Sie, dass [Std::d ecay_t](../standard-library/decay-class.md) erforderlich ist, da [tuple_size](../standard-library/tuple-size-class-tuple.md) nicht mit Verweis Typen funktioniert. Mithilfe der `apply_`-Funktion werden Tupel-Member entpackt und als getrennte Argumente an einen Funktionsaufruf weitergeleitet. In diesem Beispiel ist die Funktion ein einfacher Lambdaausdruck, der die Werte ausgibt.

```cpp
#include <stddef.h>
#include <iostream>
#include <tuple>
#include <utility>
#include <array>
#include <string>

using namespace std;

// Create a tuple from the array and the index_sequence
template<typename Array, size_t... I>
auto a2t_(const Array& a, index_sequence<I...>)
{
    return make_tuple(a[I]...);
}

// Create an index sequence for the array, and pass it to the
// implementation function a2t_
template<typename T, size_t N>
auto a2t(const array<T, N>& a)
{
    return a2t_(a, make_index_sequence<N>());
}

// Call function F with the tuple members as separate arguments.
template<typename F, typename Tuple = tuple<T...>, size_t... I>
decltype(auto) apply_(F&& f, Tuple&& args, index_sequence<I...>)
{
    return forward<F>(f)(get<I>(forward<Tuple>(args))...);
}

// Create an index_sequence for the tuple, and pass it with the
// function object and the tuple to the implementation function apply_
template<typename F, typename Tuple = tuple<T...>>
decltype(auto) apply(F&& f, Tuple&& args)
{
    using Indices = make_index_sequence<tuple_size<decay_t<Tuple>>::value >;
    return apply_(forward<F>(f), forward<Tuple>(args), Indices());
}

int main()
{
    const array<string, 3> arr { "Hello", "from", "C++14" };

    //Create a tuple given a array
    auto tup = a2t(arr);

    // Extract the tuple elements
    apply([](const string& a, const string& b, const string& c) {cout << a << " " << b << " " << c << endl; }, tup);

    char c;
    cin >> c;
}
```

Um einen `index_sequence` für ein Parameter Paket zu erstellen, verwenden Sie `index_sequence_for` \<T...> einen Alias für.`make_index_sequence`\<sizeof...(T)>

## <a name="requirements"></a>Requirements (Anforderungen)

Header: \<type_traits\>

Namepace: std

## <a name="see-also"></a>Weitere Informationen

[Auslassungs Zeichen-und Variadic-Vorlagen](../cpp/ellipses-and-variadic-templates.md)
