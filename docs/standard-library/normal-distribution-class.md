---
title: normal_distribution-Klasse
ms.date: 11/04/2016
f1_keywords:
- random/std::normal_distribution
- random/std::normal_distribution::reset
- random/std::normal_distribution::mean
- random/std::normal_distribution::stddev
- random/std::normal_distribution::param
- random/std::normal_distribution::min
- random/std::normal_distribution::max
- random/std::normal_distribution::operator()
- random/std::normal_distribution::param_type
- random/std::normal_distribution::param_type::mean
- random/std::normal_distribution::param_type::stddev
- random/std::normal_distribution::param_type::operator==
- random/std::normal_distribution::param_type::operator!=
helpviewer_keywords:
- std::normal_distribution [C++]
- std::normal_distribution [C++], reset
- std::normal_distribution [C++], mean
- std::normal_distribution [C++], stddev
- std::normal_distribution [C++], param
- std::normal_distribution [C++], min
- std::normal_distribution [C++], max
- std::normal_distribution [C++], param_type
- std::normal_distribution [C++], param_type
ms.assetid: bf92cdbd-bc72-4d4a-b588-173d748f0d7d
ms.openlocfilehash: 138011ec4ccf6c010f002d61cdb8ae8b0bac1796
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212149"
---
# <a name="normal_distribution-class"></a>normal_distribution-Klasse

Generiert eine Normalverteilung.

## <a name="syntax"></a>Syntax

```cpp
template<class RealType = double>
class normal_distribution
   {
public:
   // types
   typedef RealType result_type;
   struct param_type;

   // constructors and reset functions
   explicit normal_distribution(result_type mean = 0.0, result_type stddev = 1.0);
   explicit normal_distribution(const param_type& parm);
   void reset();

   // generating functions
   template <class URNG>
   result_type operator()(URNG& gen);
   template <class URNG>
   result_type operator()(URNG& gen, const param_type& parm);

   // property functions
   result_type mean() const;
   result_type stddev() const;
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

Die Klassen Vorlage beschreibt eine Verteilung, die Werte eines benutzerdefinierten ganzzahligen Typs produziert **`double`** . Wenn kein entsprechend der normal Verteilung verteilter Wert bereitgestellt wird, geben Sie ein. Die folgende Tabelle ist mit Artikeln über einzelne Member verknüpft.

||||
|-|-|-|
|[normal_distribution](#normal_distribution)|`normal_distribution::mean`|`normal_distribution::param`|
|`normal_distribution::operator()`|`normal_distribution::stddev`|[param_type](#param_type)|

Die Eigenschafts Funktionen `mean()` und `stddev()` geben die Werte für die gespeicherten Verteilungsparameter *Mean* bzw. *StdDev* zurück.

Das Eigenschaftsmember `param()` gibt das aktuell gespeicherte Verteilungspaket `param_type` zurück oder legt es fest.

Die `min()`- und `max()`-Memberfunktion gibt das jeweils kleinst- und größtmögliche Ergebnis zurück.

Die `reset()`-Memberfunktion verwirft alle zwischengespeicherten Werte, damit das Ergebnis des folgenden Aufrufs von `operator()` nicht von Werten abhängig ist, die vor dem Aufruf aus der Engine bezogen wurden.

Die `operator()`-Memberfunktionen geben den nächsten generierten Wert von entweder dem aktuellen oder dem spezifizierten Parameterpaket zurück, das auf der URNG-Engine basiert.

Weitere Informationen zu Verteilungs Klassen und ihren Membern finden Sie unter [\<random>](../standard-library/random.md) .

Ausführliche Informationen zur Normalverteilung finden Sie im Artikel [Normal Distribution (Normalverteilung)](https://go.microsoft.com/fwlink/p/?linkid=400924) auf WolframMathWorld.com.

## <a name="example"></a>Beispiel

```cpp
// compile with: /EHsc /W4
#include <random>
#include <iostream>
#include <iomanip>
#include <string>
#include <map>

using namespace std;

void test(const double m, const double s, const int samples) {

    // uncomment to use a non-deterministic seed
    //    random_device gen;
    //    mt19937 gen(rd());
    mt19937 gen(1701);

    normal_distribution<> distr(m, s);

    cout << endl;
    cout << "min() == " << distr.min() << endl;
    cout << "max() == " << distr.max() << endl;
    cout << "m() == " << fixed << setw(11) << setprecision(10) << distr.mean() << endl;
    cout << "s() == " << fixed << setw(11) << setprecision(10) << distr.stddev() << endl;

    // generate the distribution as a histogram
    map<double, int> histogram;
    for (int i = 0; i < samples; ++i) {
        ++histogram[distr(gen)];
    }

    // print results
    cout << "Distribution for " << samples << " samples:" << endl;
    int counter = 0;
    for (const auto& elem : histogram) {
        cout << fixed << setw(11) << ++counter << ": "
            << setw(14) << setprecision(10) << elem.first << endl;
    }
    cout << endl;
}

int main()
{
    double m_dist = 1;
    double s_dist = 1;
    int samples = 10;

    cout << "Use CTRL-Z to bypass data entry and run using default values." << endl;
    cout << "Enter a floating point value for the 'mean' distribution parameter: ";
    cin >> m_dist;
    cout << "Enter a floating point value for the 'stddev' distribution parameter (must be greater than zero): ";
    cin >> s_dist;
    cout << "Enter an integer value for the sample count: ";
    cin >> samples;

    test(m_dist, s_dist, samples);
}
```

```Output
Use CTRL-Z to bypass data entry and run using default values.
Enter a floating point value for the 'mean' distribution parameter: 0
Enter a floating point value for the 'stddev' distribution parameter (must be greater than zero): 1
Enter an integer value for the sample count: 10

min() == -1.79769e+308
max() == 1.79769e+308
m() == 0.0000000000
s() == 1.0000000000
Distribution for 10 samples:
    1: -0.8845823965
    2: -0.1995761116
    3: -0.1162665130
    4: -0.0685154932
    5: 0.0403741461
    6: 0.1591327792
    7: 1.0414389924
    8: 1.5876269426
    9: 1.6362637713
    10: 2.7821317338
```

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<random>

**Namespace:** std

## <a name="normal_distributionnormal_distribution"></a><a name="normal_distribution"></a>normal_distribution:: normal_distribution

Erstellt die Verteilung.

```cpp
explicit normal_distribution(result_type mean = 0.0, result_type stddev = 1.0);
explicit normal_distribution(const param_type& parm);
```

### <a name="parameters"></a>Parameter

*bedeutete*\
Der `mean`-Verteilungsparameter.

*STDDEV*\
Der `stddev`-Verteilungsparameter.

*parm*\
Die für die Erstellung der Verteilung verwendete Parameterstruktur.

### <a name="remarks"></a>Bemerkungen

**Vorbedingung:**`0.0 < stddev`

Mit dem ersten Konstruktor wird ein Objekt erstellt, dessen gespeicherter `mean`-Wert den Wert *mean* und dessen gespeicherter `stddev`-Wert den Wert *stddev* enthält.

Mit dem zweiten Konstruktor wird ein Objekt erstellt, dessen gespeicherte Parameter aus *parm* initialisiert werden. Sie können die aktuellen Parameter einer vorhandenen Verteilung abrufen und festlegen, indem Sie die Memberfunktion `param()` aufrufen.

## <a name="normal_distributionparam_type"></a><a name="param_type"></a>normal_distribution::p aram_type

Speichert die Parameter der Verteilung.

```cpp
struct param_type {
   typedef normal_distribution<result_type> distribution_type;
   param_type(result_type mean = 0.0, result_type stddev = 1.0);
   result_type mean() const;
   result_type stddev() const;

   bool operator==(const param_type& right) const;
   bool operator!=(const param_type& right) const;
   };
```

### <a name="parameters"></a>Parameter

*bedeutete*\
Der `mean`-Verteilungsparameter.

*STDDEV*\
Der `stddev`-Verteilungsparameter.

*Richting*\
Die `param_type`-Struktur, mit der verglichen wird.

### <a name="remarks"></a>Bemerkungen

**Vorbedingung:**`0.0 < stddev`

Diese Struktur kann bei der Instanziierung an den Klassenkonstruktor des Verteilers, an die Memberfunktion `param()` (zur Festlegung der gespeicherten Parameter einer vorhandenen Verteilung) und an `operator()` (zur Verwendung anstelle der gespeicherten Parameter) übergeben werden.

## <a name="see-also"></a>Weitere Informationen

[\<random>](../standard-library/random.md)
