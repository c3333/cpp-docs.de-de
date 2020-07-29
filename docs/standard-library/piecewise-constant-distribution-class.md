---
title: piecewise_constant_distribution-Klasse
ms.date: 11/04/2016
f1_keywords:
- random/std::piecewise_constant_distribution
- random/std::piecewise_constant_distribution::reset
- random/std::piecewise_constant_distribution::intervals
- random/std::piecewise_constant_distribution::densities
- random/std::piecewise_constant_distribution::param
- random/std::piecewise_constant_distribution::min
- random/std::piecewise_constant_distribution::max
- random/std::piecewise_constant_distribution::operator()
- random/std::piecewise_constant_distribution::param_type
- random/std::piecewise_constant_distribution::param_type::intervals
- random/std::piecewise_constant_distribution::param_type::densities
- random/std::piecewise_constant_distribution::param_type::operator==
- random/std::piecewise_constant_distribution::param_type::operator!=
helpviewer_keywords:
- std::piecewise_constant_distribution [C++]
- std::piecewise_constant_distribution [C++], reset
- std::piecewise_constant_distribution [C++], intervals
- std::piecewise_constant_distribution [C++], densities
- std::piecewise_constant_distribution [C++], param
- std::piecewise_constant_distribution [C++], min
- std::piecewise_constant_distribution [C++], max
- std::piecewise_constant_distribution [C++], param_type
- std::piecewise_constant_distribution [C++], param_type
ms.assetid: 2c9a21fa-623e-4d63-b827-3f1556b6dedb
ms.openlocfilehash: 6764e37b994ed76d27f88e3bdc8ec137d5e2f600
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232988"
---
# <a name="piecewise_constant_distribution-class"></a>piecewise_constant_distribution-Klasse

Generiert eine stückweise konstante Verteilung mit Intervallen von variierender Weite und in jedem Intervall eindeutiger Wahrscheinlichkeit.

## <a name="syntax"></a>Syntax

```cpp
template<class RealType = double>
class piecewise_constant_distribution
   {
public:
   // types
   typedef RealType result_type;
   struct param_type;

   // constructor and reset functions
   piecewise_constant_distribution();
   template <class InputIteratorI, class InputIteratorW>
   piecewise_constant_distribution(
       InputIteratorI firstI, InputIteratorI lastI, InputIteratorW firstW);
   template <class UnaryOperation>
   piecewise_constant_distribution(
      initializer_list<result_type> intervals, UnaryOperation weightfunc);
   template <class UnaryOperation>
   piecewise_constant_distribution(
      size_t count, result_type xmin, result_type xmax, UnaryOperation weightfunc);
   explicit piecewise_constant_distribution(const param_type& parm);
   void reset();

   // generating functions
   template <class URNG>
   result_type operator()(URNG& gen);
   template <class URNG>
   result_type operator()(URNG& gen, const param_type& parm);

   // property functions
   vector<result_type> intervals() const;
   vector<result_type> densities() const;
   param_type param() const;
   void param(const param_type& parm);
   result_type min() const;
   result_type max() const;
   };
```

### <a name="parameters"></a>Parameter

*RealType*\
Der Gleit Komma Ergebnistyp. der Standardwert ist **`double`** . Informationen zu möglichen Typen finden Sie unter [\<random>](../standard-library/random.md) .

## <a name="remarks"></a>Bemerkungen

Die Sampling-Verteilung weist Intervalle von variierender Breite und in jedem Intervall eindeutiger Wahrscheinlichkeit auf. Informationen über weitere Sampling-Verteilungen erhalten Sie unter [piecewise_linear_distribution-Klasse](../standard-library/piecewise-linear-distribution-class.md) und [discrete_distribution](../standard-library/discrete-distribution-class.md).

Die folgende Tabelle ist mit Artikeln über einzelne Member verknüpft:

||||
|-|-|-|
|[piecewise_constant_distribution](#piecewise_constant_distribution)|`piecewise_constant_distribution::intervals`|`piecewise_constant_distribution::param`|
|`piecewise_constant_distribution::operator()`|`piecewise_constant_distribution::densities`|[param_type](#param_type)|

Die Eigenschaftsfunktion `intervals()` gibt einen `vector<result_type>` mit dem Satz gespeicherter Intervalle der Verteilung zurück.

Die Eigenschaftsfunktion `densities()` gibt einen `vector<result_type>` mit den für jeden Intervallsatz gespeicherten Dichten zurück, die entsprechend den in den Konstruktorparametern genannten Gewichten berechnet werden.

Das Eigenschaftsmember `param()` gibt das aktuell gespeicherte Verteilungspaket `param_type` zurück oder legt es fest.

Die `min()`- und `max()`-Memberfunktion gibt das jeweils kleinst- und größtmögliche Ergebnis zurück.

Die `reset()`-Memberfunktion verwirft alle zwischengespeicherten Werte, damit das Ergebnis des folgenden Aufrufs von `operator()` nicht von Werten abhängig ist, die vor dem Aufruf aus der Engine bezogen wurden.

Die `operator()`-Memberfunktionen geben den nächsten generierten Wert von entweder dem aktuellen oder dem spezifizierten Parameterpaket zurück, das auf der URNG-Engine basiert.

Weitere Informationen zu Verteilungs Klassen und ihren Membern finden Sie unter [\<random>](../standard-library/random.md) .

## <a name="example"></a>Beispiel

```cpp
// compile with: /EHsc /W4
#include <random>
#include <iostream>
#include <iomanip>
#include <string>
#include <map>

using namespace std;

void test(const int s) {

    // uncomment to use a non-deterministic generator
    // random_device rd;
    // mt19937 gen(rd());
    mt19937 gen(1701);

    // Three intervals, non-uniform: 0 to 1, 1 to 6, and 6 to 15
    vector<double> intervals{ 0, 1, 6, 15 };
    // weights determine the densities used by the distribution
    vector<double> weights{ 1, 5, 10 };

    piecewise_constant_distribution<double> distr(intervals.begin(), intervals.end(), weights.begin());

    cout << endl;
    cout << "min() == " << distr.min() << endl;
    cout << "max() == " << distr.max() << endl;
    cout << "intervals (index: interval):" << endl;
    vector<double> i = distr.intervals();
    int counter = 0;
    for (const auto& n : i) {
        cout << fixed << setw(11) << counter << ": " << setw(14) << setprecision(10) << n << endl;
        ++counter;
    }
    cout << endl;
    cout << "densities (index: density):" << endl;
    vector<double> d = distr.densities();
    counter = 0;
    for (const auto& n : d) {
        cout << fixed << setw(11) << counter << ": " << setw(14) << setprecision(10) << n << endl;
        ++counter;
    }
    cout << endl;

    // generate the distribution as a histogram
    map<int, int> histogram;
    for (int i = 0; i < s; ++i) {
        ++histogram[distr(gen)];
    }

    // print results
    cout << "Distribution for " << s << " samples:" << endl;
    for (const auto& elem : histogram) {
        cout << setw(5) << elem.first << '-' << elem.first+1 << ' ' << string(elem.second, ':') << endl;
    }
    cout << endl;
}

int main()
{
    int samples = 100;

    cout << "Use CTRL-Z to bypass data entry and run using default values." << endl;
    cout << "Enter an integer value for the sample count: ";
    cin >> samples;

    test(samples);
}
```

```Output
Use CTRL-Z to bypass data entry and run using default values.
Enter an integer value for the sample count: 100
min() == 0
max() == 15
intervals (index: interval):
          0:   0.0000000000
          1:   1.0000000000
          2:   6.0000000000
          3:  15.0000000000
densities (index: density):
          0:   0.0625000000
          1:   0.0625000000
          2:   0.0694444444
Distribution for 100 samples:
    0-1 :::::::
    1-2 ::::::
    2-3 :::::
    3-4 ::::::
    4-5 :::::::
    5-6 ::::::
    6-7 :::
    7-8 ::::::::::
    8-9 ::::::
    9-10 ::::::::::::
    10-11 :::::
    11-12 ::::::
    12-13 :::::::::
    13-14 ::::
    14-15 ::::::::
```

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<random>

**Namespace:** std

## <a name="piecewise_constant_distributionpiecewise_constant_distribution"></a><a name="piecewise_constant_distribution"></a>piecewise_constant_distribution::p iecewise_constant_distribution

Erstellt die Verteilung.

```cpp
// default constructor
piecewise_constant_distribution();

// constructs using a range of intervals, [firstI, lastI), with
// matching weights starting at firstW
template <class InputIteratorI, class InputIteratorW>
piecewise_constant_distribution(InputIteratorI firstI, InputIteratorI lastI, InputIteratorW firstW);

// constructs using an initializer list for range of intervals,
// with weights generated by function weightfunc
template <class UnaryOperation>
piecewise_constant_distribution(initializer_list<RealType>
intervals, UnaryOperation weightfunc);

// constructs using an initializer list for range of count intervals,
// distributed uniformly over [xmin,xmax] with weights generated by function weightfunc
template <class UnaryOperation>
piecewise_constant_distribution(size_t count, RealType xmin, RealType xmax, UnaryOperation weightfunc);

// constructs from an existing param_type structure
explicit piecewise_constant_distribution(const param_type& parm);
```

### <a name="parameters"></a>Parameter

*firsti*\
Ein Eingabeiterator für das erste Element im Verteilungsbereich.

*lasti*\
Ein Eingabeiterator für das letzte Element im Verteilungsbereich.

*firstW*\
Ein Eingabeiterator für das erste Element im Gewichtsbereich.

*Abstände*\
Ein [initializer_list](../cpp/initializers.md) mit den Verteilungsintervallen.

*Countdown*\
Die Anzahl von Elementen im Verteilungsbereich.

*xmin*\
Der niedrigste Wert im Verteilungsbereich.

*xmax*\
Der höchste Wert im Verteilungsbereich. Muss größer als *xmin* sein.

*weightfunc*\
Das Objekt, das die Wahrscheinlichkeitsfunktion für die Verteilung darstellt. Sowohl der-Parameter als auch der Rückgabewert müssen in konvertierbar sein **`double`** .

*parm*\
Die für die Erstellung der Verteilung verwendete Parameterstruktur.

### <a name="remarks"></a>Bemerkungen

Der Standardkonstruktor legt die gespeicherten Parameter so fest, dass es nur ein Intervall, 0 bis 1, mit einer Wahrscheinlichkeitsdichte von 1 gibt.

Der Iteratorbereichskonstruktor

```cpp
template <class InputIteratorI, class InputIteratorW>
piecewise_constant_distribution(InputIteratorI firstI, InputIteratorI lastI,
    InputIteratorW firstW);
```

erstellt ein Verteilungsobjekt mit Intervallen von Iteratoren über die Sequenz [`firstI`, `lastI`) und einer passenden Gewichtssequenz, die mit `firstW` beginnt.

Der Initialisiererlistenkonstruktor

```cpp
template <class UnaryOperation>
piecewise_constant_distribution(initializer_list<result_type>
intervals,
    UnaryOperation weightfunc);
```

erstellt ein Verteilungs Objekt mit Intervallen aus den initialisiererlistenintervallen und Gewichtungen, die aus der Funktion " *weightfunc*" generiert werden. *intervals*

Der als

```cpp
template <class UnaryOperation>
piecewise_constant_distribution(size_t count, result_type xmin, result_type xmax,
    UnaryOperation weightfunc);
```

erstellt ein Verteilungs Objekt mit gleichmäßig über [] verteilten *Zähl* Intervallen und `xmin,xmax` weist jedem Intervall Gewichtungs Gewichtungen entsprechend der *weightfunc*-Funktion zu. *weightfunc* muss einen Parameter akzeptieren und einen Rückgabewert aufweisen, der beide in konvertierbar sind **`double`** . **Vorbedingung:**`xmin < xmax`

Der als

```cpp
explicit piecewise_constant_distribution(const param_type& parm);
```

erstellt ein Verteilungs *Objekt mit einem* Parameter als gespeicherte Parameter Struktur.

## <a name="piecewise_constant_distributionparam_type"></a><a name="param_type"></a>piecewise_constant_distribution::p aram_type

Speichert alle Parameter der Verteilung.

```cpp
struct param_type {
   typedef piecewise_constant_distribution<result_type> distribution_type;
   param_type();
   template <class IterI, class IterW>
   param_type(IterI firstI, IterI lastI, IterW firstW);
   template <class UnaryOperation>
   param_type(size_t count, result_type xmin, result_type xmax, UnaryOperation weightfunc);
   std::vector<result_type> densities() const;
   std::vector<result_type> intervals() const;

   bool operator==(const param_type& right) const;
   bool operator!=(const param_type& right) const;
   };
```

### <a name="parameters"></a>Parameter

Siehe Konstruktorparameter für [piecewise_constant_distribution](#piecewise_constant_distribution).

### <a name="remarks"></a>Bemerkungen

**Vorbedingung:**`xmin < xmax`

Diese Struktur kann bei der Instanziierung an den Klassenkonstruktor des Verteilers, an die Memberfunktion `param()` (zur Festlegung der gespeicherten Parameter einer vorhandenen Verteilung) und an `operator()` (zur Verwendung anstelle der gespeicherten Parameter) übergeben werden.

## <a name="see-also"></a>Siehe auch

[\<random>](../standard-library/random.md)\
[piecewise_linear_distribution](../standard-library/piecewise-linear-distribution-class.md)
