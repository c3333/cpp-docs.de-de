---
title: uniform_real_distribution-Klasse
ms.date: 11/04/2016
f1_keywords:
- random/std::uniform_real_distribution
- random/std::uniform_real_distribution::reset
- random/std::uniform_real_distribution::a
- random/std::uniform_real_distribution::b
- random/std::uniform_real_distribution::param
- random/std::uniform_real_distribution::min
- random/std::uniform_real_distribution::max
- random/std::uniform_real_distribution::operator()
- random/std::uniform_real_distribution::param_type
- random/std::uniform_real_distribution::param_type::a
- random/std::uniform_real_distribution::param_type::b
- random/std::uniform_real_distribution::param_type::operator==
- random/std::uniform_real_distribution::param_type::operator!=
helpviewer_keywords:
- std::uniform_real_distribution [C++]
- std::uniform_real_distribution [C++], reset
- std::uniform_real_distribution [C++], a
- std::uniform_real_distribution [C++], b
- std::uniform_real_distribution [C++], param
- std::uniform_real_distribution [C++], min
- std::uniform_real_distribution [C++], max
- std::uniform_real_distribution [C++], param_type
- std::uniform_real_distribution [C++], param_type
ms.assetid: 5cf906fd-0319-4984-b21b-98425cd7532d
ms.openlocfilehash: ba2ec419e524ca571120fe82c7cbf63c1a97eaaa
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88839594"
---
# <a name="uniform_real_distribution-class"></a>uniform_real_distribution-Klasse

Generiert eine einheitliche (jeder Wert ist gleichermaßen wahrscheinlich) Gleitkommaverteilung innerhalb eines Ausgabebereichs, der inklusive-exklusive ist.

## <a name="syntax"></a>Syntax

```cpp
template<class RealType = double>
   class uniform_real_distribution {
public:
   // types
   typedef RealType result_type;
   struct param_type;

   // constructors and reset functions
   explicit uniform_real_distribution(
      result_type a = 0.0, result_type b = 1.0);
   explicit uniform_real_distribution(const param_type& parm);
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
Der Gleit Komma Ergebnistyp. der Standardwert ist **`double`** . Informationen zu möglichen Typen finden Sie unter [\<random>](../standard-library/random.md) .

## <a name="remarks"></a>Bemerkungen

Die Klassen Vorlage beschreibt eine inklusiv-exklusive Verteilung, die Werte eines vom Benutzer angegebenen ganzzahligen Gleit Komma Typs mit einer Verteilung erzeugt, damit jeder Wert gleichermaßen wahrscheinlich ist. Die folgende Tabelle ist mit Artikeln über einzelne Member verknüpft.

[uniform_real_distribution](#uniform_real_distribution)\
[param_type](#param_type)|

Das Eigenschaftsmember `a()` gibt die aktuell gespeicherte Untergrenze der Verteilung zurück, während `b()` die aktuell gespeicherte Obergrenze zurückgibt. Für diese Verteilungs Klasse sind diese Mindest-und Maximalwerte identisch mit denen, die von den allgemeinen Eigenschafts Funktionen zurückgegeben `min()` und `max()` im Thema beschrieben werden [\<random>](../standard-library/random.md) .

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

void test(const double a, const double b, const int s) {

    // uncomment to use a non-deterministic seed
    //    std::random_device rd;
    //    std::mt19937 gen(rd());
    std::mt19937 gen(1729);

    std::uniform_real_distribution<> distr(a,b);

    std::cout << "lower bound == " << distr.a() << std::endl;
    std::cout << "upper bound == " << distr.b() << std::endl;

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
            << std::setprecision(10) << elem.first << std::endl;
    }
    std::cout << std::endl;
}

int main()
{
    double a_dist = 1.0;
    double b_dist = 1.5;

    int samples = 10;

    std::cout << "Use CTRL-Z to bypass data entry and run using default values." << std::endl;
    std::cout << "Enter a floating point value for the lower bound of the distribution: ";
    std::cin >> a_dist;
    std::cout << "Enter a floating point value for the upper bound of the distribution: ";
    std::cin >> b_dist;
    std::cout << "Enter an integer value for the sample count: ";
    std::cin >> samples;

    test(a_dist, b_dist, samples);
}
```

```Output
Use CTRL-Z to bypass data entry and run using default values.
Enter a floating point value for the lower bound of the distribution: 0
Enter a floating point value for the upper bound of the distribution: 1
Enter an integer value for the sample count: 10
lower bound == 0
upper bound == 1
Distribution for 10 samples:
          1: 0.0288609485
          2: 0.2007994386
          3: 0.3027480117
          4: 0.4124758695
          5: 0.4413777133
          6: 0.4846447405
          7: 0.6225745916
          8: 0.6880935217
          9: 0.7541936723
         10: 0.8795716566
```

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<random>

**Namespace:** std

## <a name="uniform_real_distributionuniform_real_distribution"></a><a name="uniform_real_distribution"></a> uniform_real_distribution:: uniform_real_distribution

Erstellt die Verteilung.

```cpp
explicit uniform_real_distribution(result_type a = 0.0, result_type b = 1.0);
explicit uniform_real_distribution(const param_type& parm);
```

### <a name="parameters"></a>Parameter

*ein*\
Die Untergrenze (einschließend) für Zufallswerte.

*b*\
Die Obergrenze (ausschließend) für Zufallswerte.

*parm*\
Die für die Erstellung der Verteilung verwendete `param_type`-Struktur.

### <a name="remarks"></a>Bemerkungen

**Vorbedingung:**`a < b`

Der erste Konstruktor konstruiert ein Objekt, dessen *gespeicherter-Wert den* Wert *a* enthält und dessen gespeicherter *b* -Wert den Wert *b*enthält.

Mit dem zweiten Konstruktor wird ein Objekt erstellt, dessen gespeicherte Parameter aus *parm* initialisiert werden. Sie können die aktuellen Parameter einer vorhandenen Verteilung abrufen und festlegen, indem Sie die Memberfunktion `param()` aufrufen.

## <a name="uniform_real_distributionparam_type"></a><a name="param_type"></a> uniform_real_distribution::p aram_type

Speichert alle Parameter der Verteilung.

```cpp
struct param_type {
   typedef uniform_real_distribution<result_type> distribution_type;
   param_type(result_type a = 0.0, result_type b = 1.0);
   result_type a() const;
   result_type b() const;

   bool operator==(const param_type& right) const;
   bool operator!=(const param_type& right) const;
   };
```

### <a name="parameters"></a>Parameter

*ein*\
Die Untergrenze (einschließend) für Zufallswerte.

*b*\
Die Obergrenze (ausschließend) für Zufallswerte.

*Richting*\
Das mit diesem `param_type`-Objekt zu vergleichende Objekt.

### <a name="remarks"></a>Bemerkungen

**Vorbedingung:**`a < b`

Diese Struktur kann bei der Instanziierung an den Klassenkonstruktor des Verteilers, an die Memberfunktion `param()` (zur Festlegung der gespeicherten Parameter einer vorhandenen Verteilung) und an `operator()` (zur Verwendung anstelle der gespeicherten Parameter) übergeben werden.

## <a name="see-also"></a>Weitere Informationen

[\<random>](../standard-library/random.md)
