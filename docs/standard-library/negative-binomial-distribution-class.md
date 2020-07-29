---
title: negative_binomial_distribution-Klasse
ms.date: 11/04/2016
f1_keywords:
- random/std::negative_binomial_distribution
- random/std::negative_binomial_distribution::reset
- random/std::negative_binomial_distribution::k
- random/std::negative_binomial_distribution::p
- random/std::negative_binomial_distribution::param
- random/std::negative_binomial_distribution::min
- random/std::negative_binomial_distribution::max
- random/std::negative_binomial_distribution::operator()
- random/std::negative_binomial_distribution::param_type
- random/std::negative_binomial_distribution::param_type::k
- random/std::negative_binomial_distribution::param_type::p
- random/std::negative_binomial_distribution::param_type::operator==
- random/std::negative_binomial_distribution::param_type::operator!=
helpviewer_keywords:
- std::negative_binomial_distribution [C++]
- std::negative_binomial_distribution [C++], reset
- std::negative_binomial_distribution [C++], k
- std::negative_binomial_distribution [C++], p
- std::negative_binomial_distribution [C++], param
- std::negative_binomial_distribution [C++], min
- std::negative_binomial_distribution [C++], max
- std::negative_binomial_distribution [C++], param_type
- std::negative_binomial_distribution [C++], param_type
ms.assetid: 7f5f0967-7fdd-4578-99d4-88f292b4fe9c
ms.openlocfilehash: 5168bd054d045f624a970b177113203179e1fb8a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212201"
---
# <a name="negative_binomial_distribution-class"></a>negative_binomial_distribution-Klasse

Generiert eine negative binomiale Verteilung.

## <a name="syntax"></a>Syntax

```
template<class IntType = int>
class negative_binomial_distribution
{
public:
    // types
    typedef IntType result_type;
    struct param_type;

    // constructor and reset functions
    explicit negative_binomial_distribution(result_type k = 1, double p = 0.5);
    explicit negative_binomial_distribution(const param_type& parm);
    void reset();

    // generating functions
    template `<`class URNG>
    result_type operator()(URNG& gen);
    template `<`class URNG>
    result_type operator()(URNG& gen, const param_type& parm);

    // property functions
    result_type k() const;
    double p() const;
    param_type param() const;
    void param(const param_type& parm);
    result_type min() const;
    result_type max() const;
};
```

### <a name="parameters"></a>Parameter

*Inttype*\
Der Integer-Ergebnistyp, der Standardwert ist **`int`** . Informationen zu möglichen Typen finden Sie unter [\<random>](../standard-library/random.md) .

## <a name="remarks"></a>Bemerkungen

Die Klassen Vorlage beschreibt eine Verteilung, die Werte eines benutzerdefinierten ganzzahligen Typs produziert **`int`** . Wenn kein entsprechend der diskreten Wahrscheinlichkeitsfunktion der negativen binomialen Verteilung verteilter Wert bereitgestellt wird, geben Sie ein. Die folgende Tabelle ist mit Artikeln über einzelne Member verknüpft.

||||
|-|-|-|
|[negative_binomial_distribution](#negative_binomial_distribution)|`negative_binomial_distribution::k`|`negative_binomial_distribution::param`|
|`negative_binomial_distribution::operator()`|`negative_binomial_distribution::p`|[param_type](#param_type)|

Die Eigenschaftenmember `k()` und `p()` geben die aktuell gespeicherten Verteilungsparameter Werte *k* bzw. *p* zurück.

Das Eigenschaftsmember `param()` gibt das aktuell gespeicherte Verteilungspaket `param_type` zurück oder legt es fest.

Die `min()`- und `max()`-Memberfunktion gibt das jeweils kleinst- und größtmögliche Ergebnis zurück.

Die `reset()`-Memberfunktion verwirft alle zwischengespeicherten Werte, damit das Ergebnis des folgenden Aufrufs von `operator()` nicht von Werten abhängig ist, die vor dem Aufruf aus der Engine bezogen wurden.

Die `operator()`-Memberfunktionen geben den nächsten generierten Wert von entweder dem aktuellen oder dem spezifizierten Parameterpaket zurück, das auf der URNG-Engine basiert.

Weitere Informationen zu Verteilungs Klassen und ihren Membern finden Sie unter [\<random>](../standard-library/random.md) .

Ausführliche Informationen über die diskrete Wahrscheinlichkeitsfunktion zur negativen binomialen Verteilung finden Sie im Wolfram MathWorld-Artikel [Negative Binomial Distribution](https://go.microsoft.com/fwlink/p/?linkid=400516).

## <a name="example"></a>Beispiel

```cpp
// compile with: /EHsc /W4
#include <random>
#include <iostream>
#include <iomanip>
#include <string>
#include <map>

void test(const int k, const double p, const int& s) {

    // uncomment to use a non-deterministic seed
    //    std::random_device rd;
    //    std::mt19937 gen(rd());
    std::mt19937 gen(1729);

    std::negative_binomial_distribution<> distr(k, p);

    std::cout << std::endl;
    std::cout << "k == " << distr.k() << std::endl;
    std::cout << "p == " << distr.p() << std::endl;

    // generate the distribution as a histogram
    std::map<int, int> histogram;
    for (int i = 0; i < s; ++i) {
        ++histogram[distr(gen)];
    }

    // print results
    std::cout << "Histogram for " << s << " samples:" << std::endl;
    for (const auto& elem : histogram) {
        std::cout << std::setw(5) << elem.first << ' ' << std::string(elem.second, ':') << std::endl;
    }
    std::cout << std::endl;
}

int main()
{
    int    k_dist = 1;
    double p_dist = 0.5;
    int    samples = 100;

    std::cout << "Use CTRL-Z to bypass data entry and run using default values." << std::endl;
    std::cout << "Enter an integer value for k distribution (where 0 < k): ";
    std::cin >> k_dist;
    std::cout << "Enter a double value for p distribution (where 0.0 < p <= 1.0): ";
    std::cin >> p_dist;
    std::cout << "Enter an integer value for a sample count: ";
    std::cin >> samples;

    test(k_dist, p_dist, samples);
}
```

Erste Ausführung:

```Output
Use CTRL-Z to bypass data entry and run using default values.
Enter an integer value for k distribution (where 0 `<` k): 1
Enter a double value for p distribution (where 0.0 `<`p `<`= 1.0): .5
Enter an integer value for a sample count: 100

k == 1
p == 0.5
Histogram for 100 samples:
    0 :::::::::::::::::::::::::::::::::::::::::::
    1 ::::::::::::::::::::::::::::::::
    2 ::::::::::::
    3 :::::::
    4 ::::
    5 ::
```

Zweite Ausführung:

```Output
Use CTRL-Z to bypass data entry and run using default values.
Enter an integer value for k distribution (where 0 `<` k): 100
Enter a double value for p distribution (where 0.0 `<` p <= 1.0): .667
Enter an integer value for a sample count: 100

k == 100
p == 0.667
Histogram for 100 samples:
    31 ::
    32 :
    33 ::
    34 :
    35 ::
    37 ::
    38 :
    39 :
    40 ::
    41 :::
    42 :::
    43 :::::
    44 :::::
    45 ::::
    46 ::::::
    47 ::::::::
    48 :::
    49 :::
    50 :::::::::
    51 :::::::
    52 ::
    53 :::
    54 :::::
    56 ::::
    58 :
    59 :::::
    60 ::
    61 :
    62 ::
    64 :
    69 ::::
```

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<random>

**Namespace:** std

## <a name="negative_binomial_distributionnegative_binomial_distribution"></a><a name="negative_binomial_distribution"></a>negative_binomial_distribution:: negative_binomial_distribution

Erstellt die Verteilung.

```cpp
explicit negative_binomial_distribution(result_type k = 1, double p = 0.5);
explicit negative_binomial_distribution(const param_type& parm);
```

### <a name="parameters"></a>Parameter

*km*\
Der `k`-Verteilungsparameter.

*cker*\
Der `p`-Verteilungsparameter.

*parm*\
Die für die Erstellung der Verteilung verwendete Parameterstruktur.

### <a name="remarks"></a>Bemerkungen

**Vorbedingung:** `0.0 < k` und `0.0 < p ≤ 1.0`

Mit dem ersten Konstruktor wird ein Objekt erstellt, dessen gespeicherter `p`-Wert den Wert *p* und dessen gespeicherter `k`-Wert den Wert *k* enthält.

Mit dem zweiten Konstruktor wird ein Objekt erstellt, dessen gespeicherte Parameter aus *parm* initialisiert werden. Sie können die aktuellen Parameter einer vorhandenen Verteilung abrufen und festlegen, indem Sie die Memberfunktion `param()` aufrufen.

## <a name="negative_binomial_distributionparam_type"></a><a name="param_type"></a>negative_binomial_distribution::p aram_type

Speichert die Parameter der Verteilung.

Struktur param_type {typedef negative_binomial_distribution `<` result_type> distribution_type; param_type (result_type k = 1, Double p = 0,5); result_type k () Konstanten; Double p () Konstanten;

   bool operator==(const param_type& right) const; bool operator!=(const param_type& right) const; };

### <a name="parameters"></a>Parameter

*km*\
Der `k`-Verteilungsparameter.

*cker*\
Der `p`-Verteilungsparameter.

*Richting*\
Die `param_type`-Struktur, mit der verglichen wird.

### <a name="remarks"></a>Bemerkungen

**Vorbedingung:** `0.0 < k` und `0.0 < p ≤ 1.0`

Diese Struktur kann bei der Instanziierung an den Klassenkonstruktor des Verteilers, an die Memberfunktion `param()` (zur Festlegung der gespeicherten Parameter einer vorhandenen Verteilung) und an `operator()` (zur Verwendung anstelle der gespeicherten Parameter) übergeben werden.

## <a name="see-also"></a>Weitere Informationen

[\<random>](../standard-library/random.md)
