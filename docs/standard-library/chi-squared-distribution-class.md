---
title: chi_squared_distribution-Klasse
ms.date: 11/04/2016
f1_keywords:
- random/std::chi_squared_distribution
- random/std::chi_squared_distribution::reset
- random/std::chi_squared_distribution::n
- random/std::chi_squared_distribution::param
- random/std::chi_squared_distribution::min
- random/std::chi_squared_distribution::max
- random/std::chi_squared_distribution::operator()
- random/std::chi_squared_distribution::param_type
- random/std::chi_squared_distribution::param_type::n
- random/std::chi_squared_distribution::param_type::operator==
- random/std::chi_squared_distribution::param_type::operator!=
helpviewer_keywords:
- std::chi_squared_distribution [C++]
- std::chi_squared_distribution [C++], reset
- std::chi_squared_distribution [C++], n
- std::chi_squared_distribution [C++], param
- std::chi_squared_distribution [C++], min
- std::chi_squared_distribution [C++], max
- std::chi_squared_distribution [C++], param_type
- std::chi_squared_distribution [C++], param_type
ms.assetid: 9b603fbe-cafd-4a92-b8c5-a434d60b8122
ms.openlocfilehash: 5d7a7e2ba3c962a1ef63b14fed5d4bfb67c38b44
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88845678"
---
# <a name="chi_squared_distribution-class"></a>chi_squared_distribution-Klasse

Generiert eine Chi-Quadrat-Verteilung.

## <a name="syntax"></a>Syntax

```cpp
template<class RealType = double>
class chi_squared_distribution {
public:
    // types
    typedef RealType result_type;
    struct param_type;

    // constructor and reset functions
    explicit chi_squared_distribution(RealType n = 1);
    explicit chi_squared_distribution(const param_type& parm);
    void reset();

    // generating functions
    template <class URNG>
    result_type operator()(URNG& gen);
    template <class URNG>
    result_type operator()(URNG& gen, const param_type& parm);

    // property functions
    RealType n() const;
    param_type param() const;
    void param(const param_type& parm);
    result_type min() const;
    result_type max() const;
};
```

### <a name="parameters"></a>Parameter

*RealType*\
Der Gleit Komma Ergebnistyp. der Standardwert ist **`double`** . Informationen zu möglichen Typen finden Sie unter [\<random>](../standard-library/random.md) .

*URNG*\
Die einheitliche Zufallszahlengenerator-Engine. Informationen zu möglichen Typen finden Sie unter [\<random>](../standard-library/random.md) .

## <a name="remarks"></a>Bemerkungen

Die Klassen Vorlage beschreibt eine Verteilung, die Werte eines benutzerdefinierten Gleit Komma Typs produziert **`double`** . Wenn kein entsprechend der Chi-Quadrat-Verteilung verteilter Wert bereitgestellt wird, geben Sie ein. Die folgende Tabelle ist mit Artikeln über einzelne Member verknüpft.

[chi_squared_distribution](../standard-library/chi-squared-distribution-class.md)\
[param_type](#param_type)

Die Eigenschaftsfunktion `n()` gibt den Wert für den gespeicherten Verteilungsparameter `n` zurück.

Das Eigenschaftsmember `param()` gibt das aktuell gespeicherte Verteilungspaket `param_type` zurück oder legt es fest.

Die `min()`- und `max()`-Memberfunktion gibt das jeweils kleinst- und größtmögliche Ergebnis zurück.

Die `reset()`-Memberfunktion verwirft alle zwischengespeicherten Werte, damit das Ergebnis des folgenden Aufrufs von `operator()` nicht von Werten abhängig ist, die vor dem Aufruf aus der Engine bezogen wurden.

Die `operator()`-Memberfunktionen geben den nächsten generierten Wert von entweder dem aktuellen oder dem spezifizierten Parameterpaket zurück, das auf der URNG-Engine basiert.

Weitere Informationen zu Verteilungs Klassen und ihren Membern finden Sie unter [\<random>](../standard-library/random.md) .

Ausführliche Informationen über die Chi-Quadrat-Verteilung finden Sie im Wolfram MathWorld-Artikel [Chi-Squared Distribution (Chi-Quadrat-Verteilung)](https://go.microsoft.com/fwlink/p/?linkid=400528).

## <a name="example"></a>Beispiel

```cpp
// compile with: /EHsc /W4
#include <random>
#include <iostream>
#include <iomanip>
#include <string>
#include <map>

void test(const double n, const int s) {

    // uncomment to use a non-deterministic generator
    //    std::random_device gen;
    std::mt19937 gen(1701);

    std::chi_squared_distribution<> distr(n);

    std::cout << std::endl;
    std::cout << "min() == " << distr.min() << std::endl;
    std::cout << "max() == " << distr.max() << std::endl;
    std::cout << "n() == " << std::fixed << std::setw(11) << std::setprecision(10) << distr.n() << std::endl;

    // generate the distribution as a histogram
    std::map<double, int> histogram;
    for (int i = 0; i < s; ++i) {
        ++histogram[distr(gen)];
    }

    // print results
    std::cout << "Distribution for " << s << " samples:" << std::endl;
    int counter = 0;
    for (const auto& elem : histogram) {
        std::cout << std::fixed << std::setw(11) << ++counter << ": "
            << std::setw(14) << std::setprecision(10) << elem.first << std::endl;
    }
    std::cout << std::endl;
}

int main()
{
    double n_dist = 0.5;
    int samples = 10;

    std::cout << "Use CTRL-Z to bypass data entry and run using default values." << std::endl;
    std::cout << "Enter a floating point value for the \'n\' distribution parameter (must be greater than zero): ";
    std::cin >> n_dist;
    std::cout << "Enter an integer value for the sample count: ";
    std::cin >> samples;

    test(n_dist, samples);
}
```

Erste Ausführung:

```Output
Use CTRL-Z to bypass data entry and run using default values.
Enter a floating point value for the 'n' distribution parameter (must be greater than zero): .5
Enter an integer value for the sample count: 10

min() == 4.94066e-324
max() == 1.79769e+308
n() == 0.5000000000
Distribution for 10 samples:
    1: 0.0007625595
    2: 0.0016895062
    3: 0.0058683478
    4: 0.0189647765
    5: 0.0556619371
    6: 0.1448191353
    7: 0.1448245325
    8: 0.1903494379
    9: 0.9267525768
    10: 1.5429743723
```

Zweite Ausführung:

```Output
Use CTRL-Z to bypass data entry and run using default values.
Enter a floating point value for the 'n' distribution parameter (must be greater than zero): .3333
Enter an integer value for the sample count: 10

min() == 4.94066e-324
max() == 1.79769e+308
n() == 0.3333000000
Distribution for 10 samples:
    1: 0.0000148725
    2: 0.0000490528
    3: 0.0003175988
    4: 0.0018454535
    5: 0.0092808795
    6: 0.0389540735
    7: 0.0389562514
    8: 0.0587028468
    9: 0.6183666639
    10: 1.3552086624
```

Dritte Ausführung:

```Output
Use CTRL-Z to bypass data entry and run using default values.
Enter a floating point value for the 'n' distribution parameter (must be greater than zero): 1000
Enter an integer value for the sample count: 10

min() == 4.94066e-324
max() == 1.79769e+308
n() == 1000.0000000000
Distribution for 10 samples:
    1: 958.5284624473
    2: 958.7882787809
    3: 963.0667684792
    4: 987.9638091514
    5: 1016.2433493745
    6: 1021.9337111110
    7: 1021.9723046240
    8: 1035.7622110505
    9: 1043.8725156645
    10: 1054.7051509381
```

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<random>

**Namespace:** std

## <a name="chi_squared_distributionchi_squared_distribution"></a><a name="chi_squared_distribution"></a> chi_squared_distribution:: chi_squared_distribution

Erstellt die Verteilung.

```cpp
explicit chi_squared_distribution(result_type n = 1.0);
explicit chi_squared_distribution(const param_type& parm);
```

### <a name="parameters"></a>Parameter

*Nr*\
Der `n`-Verteilungsparameter.

*parm*\
Die für die Erstellung der Verteilung verwendete Parameterstruktur.

### <a name="remarks"></a>Bemerkungen

**Vorbedingung:**`0.0 < n`

Der erste Konstruktor konstruiert ein Objekt, dessen gespeicherter `n`-Wert den Wert *n* enthält.

Mit dem zweiten Konstruktor wird ein Objekt erstellt, dessen gespeicherte Parameter aus *parm* initialisiert werden. Sie können die aktuellen Parameter einer vorhandenen Verteilung abrufen und festlegen, indem Sie die Memberfunktion `param()` aufrufen.

## <a name="chi_squared_distributionparam_type"></a><a name="param_type"></a> chi_squared_distribution::p aram_type

Speichert die Parameter der Verteilung.

```cpp
struct param_type {
   typedef chi_squared_distribution<result_type> distribution_type;
   param_type(result_type n = 1.0);
   result_type n() const;

   bool operator==(const param_type& right) const;
   bool operator!=(const param_type& right) const;
   };
```

### <a name="parameters"></a>Parameter

*Nr*\
Der `n`-Verteilungsparameter.

*Richting*\
Das mit diesem `param_type`-Objekt zu vergleichende Objekt.

### <a name="remarks"></a>Bemerkungen

**Vorbedingung:**`0.0 < n`

Diese Struktur kann bei der Instanziierung an den Klassenkonstruktor des Verteilers, an die Memberfunktion `param()` (zur Festlegung der gespeicherten Parameter einer vorhandenen Verteilung) und an `operator()` (zur Verwendung anstelle der gespeicherten Parameter) übergeben werden.

## <a name="see-also"></a>Weitere Informationen

[\<random>](../standard-library/random.md)
