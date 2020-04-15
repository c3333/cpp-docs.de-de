---
title: extreme_value_distribution-Klasse
ms.date: 11/04/2016
f1_keywords:
- random/std::extreme_value_distribution
- random/std::extreme_value_distribution::reset
- random/std::extreme_value_distribution::a
- random/std::extreme_value_distribution::b
- random/std::extreme_value_distribution::param
- random/std::extreme_value_distribution::min
- random/std::extreme_value_distribution::max
- random/std::extreme_value_distribution::operator()
- random/std::extreme_value_distribution::param_type
- random/std::extreme_value_distribution::param_type::a
- random/std::extreme_value_distribution::param_type::b
- random/std::extreme_value_distribution::param_type::operator==
- random/std::extreme_value_distribution::param_type::operator!=
helpviewer_keywords:
- std::extreme_value_distribution [C++]
- std::extreme_value_distribution [C++], reset
- std::extreme_value_distribution [C++], a
- std::extreme_value_distribution [C++], b
- std::extreme_value_distribution [C++], param
- std::extreme_value_distribution [C++], min
- std::extreme_value_distribution [C++], max
- std::extreme_value_distribution [C++], param_type
- std::extreme_value_distribution [C++], param_type
ms.assetid: a0cd8370-0a54-4e26-9388-8b9678fb57da
ms.openlocfilehash: f72401d7bdc4a61a8e986c10cdbd4fad732e41ce
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368449"
---
# <a name="extreme_value_distribution-class"></a>extreme_value_distribution-Klasse

Generiert eine Extremwertverteilung.

## <a name="syntax"></a>Syntax

```cpp
template<class RealType = double>
class extreme_value_distribution
   {
public:
   // types
   typedef RealType result_type;
   struct param_type;

   // constructor and reset functions
   explicit extreme_value_distribution(result_type a = 0.0, result_type b = 1.0);
   explicit extreme_value_distribution(const param_type& parm);
   void reset();

   // generating functions
   template <class URNG>
   result_type operator()(URNG& gen);
   template <class URNG>
   result_type operator()(URNG& gen, const param_type& parm);

   // property functions
   result_type a() const;
   result_type b() const;
   param_type param() const;
   void param(const param_type& parm);
   result_type min() const;
   result_type max() const;
   };
```

### <a name="parameters"></a>Parameter

*RealType*\
Der Gleitkomma-Ergebnistyp wird standardmäßig **verdoppelt.** Mögliche Typen finden Sie unter [ \<zufällige>](../standard-library/random.md).

*URNG*\
Die Zufallszahlengenerator-Engine. Mögliche Typen finden Sie unter [ \<zufällige>](../standard-library/random.md).

## <a name="remarks"></a>Bemerkungen

Die Klassenvorlage beschreibt eine Verteilung, die Werte eines benutzerdefinierten Gleitkommatyps erzeugt, oder typ **doppelt,** wenn keine bereitgestellt wird, verteilt gemäß der Extremwertverteilung. Die folgende Tabelle ist mit Artikeln über einzelne Member verknüpft.

||||
|-|-|-|
|[extreme_value_distribution](#extreme_value_distribution)|`extreme_value_distribution::a`|`extreme_value_distribution::param`|
|`extreme_value_distribution::operator()`|`extreme_value_distribution::b`|[param_type](#param_type)|

Die Eigenschaftsfunktionen `a()` und `b()` geben ihre entsprechenden Werte für die gespeicherten Verteilungsparameter `a` und `b` zurück.

Weitere Informationen zu Verteilungsklassen und deren Mitgliedern finden Sie unter [ \<zufällige>](../standard-library/random.md).

Ausführliche Informationen über die Extremwertverteilung finden Sie im Wolfram MathWorld-Artikel [Extreme Value Distribution](https://go.microsoft.com/fwlink/p/?linkid=401110).

## <a name="example"></a>Beispiel

```cpp
// compile with: /EHsc /W4
#include <random>
#include <iostream>
#include <iomanip>
#include <string>
#include <map>

void test(const double a, const double b, const int s) {

    // uncomment to use a non-deterministic generator
    //    std::random_device gen;

    std::mt19937 gen(1701);

    std::extreme_value_distribution<> distr(a, b);

    std::cout << std::endl;
    std::cout << "min() == " << distr.min() << std::endl;
    std::cout << "max() == " << distr.max() << std::endl;
    std::cout << "a() == " << std::fixed << std::setw(11) << std::setprecision(10) << distr.a() << std::endl;
    std::cout << "b() == " << std::fixed << std::setw(11) << std::setprecision(10) << distr.b() << std::endl;

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
    double a_dist = 0.0;
    double b_dist = 1;

    int samples = 10;

    std::cout << "Use CTRL-Z to bypass data entry and run using default values." << std::endl;
    std::cout << "Enter a floating point value for the \'a\' distribution parameter: ";
    std::cin >> a_dist;
    std::cout << "Enter a floating point value for the \'b\' distribution parameter (must be greater than zero): ";
    std::cin >> b_dist;
    std::cout << "Enter an integer value for the sample count: ";
    std::cin >> samples;

    test(a_dist, b_dist, samples);
}
```

```Output
Use CTRL-Z to bypass data entry and run using default values.
Enter a floating point value for the 'a' distribution parameter: 0
Enter a floating point value for the 'b' distribution parameter (must be greater than zero): 1
Enter an integer value for the sample count: 10

min() == -1.79769e+308
max() == 1.79769e+308
a() == 0.0000000000
b() == 1.0000000000
Distribution for 10 samples:
    1: -0.8813940331
    2: -0.7698972281
    3: 0.2951258007
    4: 0.3110450734
    5: 0.4210546820
    6: 0.4210688771
    7: 0.4598857960
    8: 1.3155194200
    9: 1.5379170046
    10: 2.0568757061
```

## <a name="requirements"></a>Anforderungen

**Header:** \<random>

**Namespace:** std

## <a name="extreme_value_distributionextreme_value_distribution"></a><a name="extreme_value_distribution"></a>extreme_value_distribution::extreme_value_distribution

Erstellt die Verteilung.

```cpp
explicit extreme_value_distribution(result_type a_value = 0.0, result_type b_value = 1.0);
explicit extreme_value_distribution(const param_type& parm);
```

### <a name="parameters"></a>Parameter

*a_value*\
Der `a`-Verteilungsparameter.

*b_value*\
Der `b`-Verteilungsparameter.

*Parm*\
Die für die Erstellung der Verteilung verwendete `param_type`-Struktur.

### <a name="remarks"></a>Bemerkungen

**Voraussetzung:**`0.0 < b`

Mit dem ersten Konstruktor wird ein Objekt erstellt, in dessen gespeichertem `a`-Wert der Wert *a_value* enthalten ist und dessen gespeicherter `b`-Wert den Wert *b_value* enthält.

Mit dem zweiten Konstruktor wird ein Objekt erstellt, dessen gespeicherte Parameter aus *parm* initialisiert werden. Sie können die aktuellen Parameter einer vorhandenen Verteilung abrufen und festlegen, indem Sie die Memberfunktion `param()` aufrufen.

## <a name="extreme_value_distributionparam_type"></a><a name="param_type"></a>extreme_value_distribution::param_type

Speichert die Parameter der Verteilung.

```cpp
struct param_type {
   typedef extreme_value_distribution<result_type> distribution_type;
   param_type(result_type a_value = 0.0, result_type b_value = 1.0);
   result_type a() const;
   result_type b() const;

   bool operator==(const param_type& right) const;
   bool operator!=(const param_type& right) const;
   };
```

### <a name="parameters"></a>Parameter

*a_value*\
Der `a`-Verteilungsparameter.

*b_value*\
Der `b`-Verteilungsparameter.

*Richting*\
Das mit diesem `param_type`-Objekt zu vergleichende Objekt.

### <a name="remarks"></a>Bemerkungen

**Voraussetzung:**`0.0 < b`

Diese Struktur kann bei der Instanziierung an den Klassenkonstruktor des Verteilers, an die Memberfunktion `param()` (zur Festlegung der gespeicherten Parameter einer vorhandenen Verteilung) und an `operator()` (zur Verwendung anstelle der gespeicherten Parameter) übergeben werden.

## <a name="see-also"></a>Siehe auch

[\<zufällige>](../standard-library/random.md)
