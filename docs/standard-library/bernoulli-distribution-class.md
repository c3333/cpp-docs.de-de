---
title: bernoulli_distribution-Klasse
ms.date: 11/04/2016
f1_keywords:
- random/std::bernoulli_distribution
- random/std::bernoulli_distribution::reset
- random/std::bernoulli_distribution::p
- random/std::bernoulli_distribution::param
- random/std::bernoulli_distribution::min
- random/std::bernoulli_distribution::max
- random/std::bernoulli_distribution::operator()
- random/std::bernoulli_distribution::param_type
- random/std::bernoulli_distribution::param_type::p
- random/std::bernoulli_distribution::param_type::operator==
- random/std::bernoulli_distribution::param_type::operator!=
helpviewer_keywords:
- std::bernoulli_distribution [C++]
- std::bernoulli_distribution [C++], reset
- std::bernoulli_distribution [C++], p
- std::bernoulli_distribution [C++], param
- std::bernoulli_distribution [C++], min
- std::bernoulli_distribution [C++], max
- std::bernoulli_distribution [C++], param_type
- std::bernoulli_distribution [C++], param_type
ms.assetid: 586bcde1-95ca-411a-bf17-4aaf19482f34
ms.openlocfilehash: 6a53707d823ced7316604f75691194dc6e05545e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364860"
---
# <a name="bernoulli_distribution-class"></a>bernoulli_distribution-Klasse

Generiert eine Bernoulli-Verteilung.

## <a name="syntax"></a>Syntax

```cpp
class bernoulli_distribution
   {
public:
   // types
   typedef bool result_type;
   struct param_type;

   // constructors and reset functions
   explicit bernoulli_distribution(double p = 0.5);
   explicit bernoulli_distribution(const param_type& parm);
   void reset();

   // generating functions
   template <class URNG>
   result_type operator()(URNG& gen);
   template <class URNG>
   result_type operator()(URNG& gen, const param_type& parm);

   // property functions
   double p() const;
   param_type param() const;
   void param(const param_type& parm);
   result_type min() const;
   result_type max() const;
   };
```

### <a name="parameters"></a>Parameter

*URNG*\
Die einheitliche Zufallszahlengenerator-Engine. Mögliche Typen finden Sie unter [ \<zufällige>](../standard-library/random.md).

## <a name="remarks"></a>Bemerkungen

Die Klasse beschreibt eine Verteilung, die Werte des Typs **bool**erzeugt, die gemäß der diskreten Wahrscheinlichkeitsfunktion Bernoulli-Verteilung verteilt werden. Die folgende Tabelle ist mit Artikeln über einzelne Member verknüpft.

||||
|-|-|-|
|[bernoulli_distribution](#bernoulli_distribution)|`bernoulli_distribution::p`|`bernoulli_distribution::param`|
|`bernoulli_distribution::operator()`||[param_type](#param_type)|

Das Eigenschaftsmember `p()` gibt den aktuell gespeicherten Verteilungsparameterwert `p` zurück.

Das Eigenschaftsmember `param()` gibt das aktuell gespeicherte Verteilungspaket `param_type` zurück oder legt es fest.

Die `min()`- und `max()`-Memberfunktion gibt das jeweils kleinst- und größtmögliche Ergebnis zurück.

Die `reset()`-Memberfunktion verwirft alle zwischengespeicherten Werte, damit das Ergebnis des folgenden Aufrufs von `operator()` nicht von Werten abhängig ist, die vor dem Aufruf aus der Engine bezogen wurden.

Die `operator()`-Memberfunktionen geben den nächsten generierten Wert von entweder dem aktuellen oder dem spezifizierten Parameterpaket zurück, das auf der URNG-Engine basiert.

Weitere Informationen zu Verteilungsklassen und deren Mitgliedern finden Sie unter [ \<zufällige>](../standard-library/random.md).

Ausführliche Informationen über die diskrete Wahrscheinlichkeitsfunktion zur Bernoulli-Verteilung finden Sie im Wolfram MathWorld-Artikel [Bernoulli Distribution](https://go.microsoft.com/fwlink/p/?linkid=398467).

## <a name="example"></a>Beispiel

```cpp
// compile with: /EHsc /W4
#include <random>
#include <iostream>
#include <iomanip>
#include <string>
#include <map>

void test(const double p, const int s) {

    // uncomment to use a non-deterministic seed
    //    std::random_device rd;
    //    std::mt19937 gen(rd());
    std::mt19937 gen(1729);

    std::bernoulli_distribution distr(p);

    std::cout << "p == " << distr.p() << std::endl;

    // generate the distribution as a histogram
    std::map<bool, int> histogram;
    for (int i = 0; i < s; ++i) {
        ++histogram[distr(gen)];
    }

    // print results
    std::cout << "Histogram for " << s << " samples:" << std::endl;
    for (const auto& elem : histogram) {
        std::cout << std::boolalpha << std::setw(5) << elem.first << ' ' << std::string(elem.second, ':') << std::endl;
    }
    std::cout << std::endl;
}

int main()
{
    double p_dist = 0.5;
    int samples = 100;

    std::cout << "Use CTRL-Z to bypass data entry and run using default values." << std::endl;
    std::cout << "Enter a double value for p distribution (where 0.0 <= p <= 1.0): ";
    std::cin >> p_dist;
    std::cout << "Enter an integer value for a sample count: ";
    std::cin >> samples;

    test(p_dist, samples);
}
```

```Output
Use CTRL-Z to bypass data entry and run using default values.
Enter a double value for p distribution (where 0.0 <= p <= 1.0): .45
Enter an integer value for a sample count: 100
p == 0.45
Histogram for 100 samples:
false :::::::::::::::::::::::::::::::::::::::::::::::::::::::::::
true :::::::::::::::::::::::::::::::::::::::::
```

## <a name="requirements"></a>Anforderungen

**Header:** \<random>

**Namespace:** std

## <a name="bernoulli_distributionbernoulli_distribution"></a><a name="bernoulli_distribution"></a>bernoulli_distribution::bernoulli_distribution

Erstellt die Verteilung.

```cpp
explicit bernoulli_distribution(double p = 0.5);
explicit bernoulli_distribution(const param_type& parm);
```

### <a name="parameters"></a>Parameter

*P*\
Der gespeicherte `p`-Verteilungsparameter.

*Parm*\
Die für die Erstellung der Verteilung verwendete `param_type`-Struktur.

### <a name="remarks"></a>Bemerkungen

**Voraussetzung:**`0.0 ≤ p ≤ 1.0`

Der erste Konstruktor konstruiert ein Objekt, dessen gespeicherter `p`-Wert den Wert *p* enthält.

Mit dem zweiten Konstruktor wird ein Objekt erstellt, dessen gespeicherte Parameter aus *parm* initialisiert werden. Sie können die aktuellen Parameter einer vorhandenen Verteilung abrufen und festlegen, indem Sie die Memberfunktion `param()` aufrufen.

## <a name="bernoulli_distributionparam_type"></a><a name="param_type"></a>bernoulli_distribution::param_type

Enthält die Parameter der Verteilung.

struct param_type ' typedef bernoulli_distribution distribution_type; param_type(double p = 0.5); double p() const;

   bool operator==(const param_type& right) const; bool operator!=(const param_type& right) const; };

### <a name="parameters"></a>Parameter

*P*\
Der gespeicherte `p`-Verteilungsparameter.

### <a name="remarks"></a>Bemerkungen

**Voraussetzung:**`0.0 ≤ p ≤ 1.0`

Diese Struktur kann bei der Instanziierung an den Klassenkonstruktor des Verteilers, an die Memberfunktion `param()` (zur Festlegung der gespeicherten Parameter einer vorhandenen Verteilung) und an `operator()` (zur Verwendung anstelle der gespeicherten Parameter) übergeben werden.

## <a name="see-also"></a>Siehe auch

[\<zufällige>](../standard-library/random.md)
